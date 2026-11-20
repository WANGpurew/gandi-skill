---
name: cli-authoring
description: |
  当用户要让 AI/CLI 读写、批量修改或验证 Gandi 3.0 作品，或用积木文本(DSL)写积木时调用。
  核心: gandi up 一次授权(只连本机)→pull 作品为文件夹→按 DSL 改文件→逐文件 check 带 base-rev 防冲突→ push 写回→run --frames 后台运行→view 截图/--text→state 读变量→assert 断言；出错看 JSON code/hint， doctor 排障，history/undo 找回。
  不适用于: 在编辑器里手动做作品、Gandi 2.0/原版 Scratch、远程主机。
  Triggers: CLI/ pull/ push/ DSL/ 积木文本/ assert/ 后台运行/ AI做作品/ gandi up/ E_CONFLICT
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.capability-id: cap.gandi.cli-ai-workflow
  cangjie.capability-revision: 1
  cangjie.bundle-id: bundle.gandi-guide
  cangjie.source-title: Gandi 3.0 功能文档
  cangjie.tags: cli, ai, dsl, automation
---
<!-- capability_id: cap.gandi.cli-ai-workflow | revision: 1 | status: active -->

# 用 CLI/AI 读写与验证作品（含 DSL）

## R — 原文 (Reading)

> "gandi pull game     # 把整个作品导出到 game/；# ……用普通的编辑工具改 game/ 里的文件……；gandi push game     # 把改动写回编辑器"
>
> — Gandi 3.0 功能文档·CLI 与 AI 分组·用 CLI 做作品 / slug: cli-workflow（源：summary-part1 §二；candidates/framework.md f20、case.md c01）

> "写入带着读到的版本号，期间有人改过就报 E_CONFLICT，需要重新读一遍再改。"
>
> — Gandi 3.0 功能文档·用 CLI 做作品·逐个文件改 / slug: cli-workflow（源：candidates/principle.md p20、case.md c02）

> "gandi run --frames 120   # 在后台舞台上跑 120 帧；gandi view --output shot.png   # 舞台截图；看不了图片时 --text 输出字符画；gandi state   # 变量、角色状态；--engine 读物理和光照"
>
> — Gandi 3.0 功能文档·用 CLI 做作品·运行和检查 / slug: cli-workflow（源：candidates/case.md c03）

## I — 方法论骨架 (Interpretation)

把"让 AI 做 Gandi 作品"从一次性的手工操作，落成一条可复现、可回滚的工程闭环：
① **先授权**——装 Node≥20 + gandi-cli，首次 `gandi up` 由人在编辑器里点"连接 CLI"授权一次；CLI 只连同一台电脑上的编辑器，不支持远程/云端；
② **把作品当文件夹**——`gandi pull` 导出为本地文件夹（积木页是 `.js`、角色是 `sprite.json`），用普通编辑工具按 DSL 改文件，再 `gandi push` 分批写回；
③ **逐文件安全编辑**——只改单个文件时走 `read` 拿 rev → `check` → `write --base-rev`，版本变了报 E_CONFLICT 就必须重读再写，绝不静默覆盖；
④ **后台按帧验证**——`run --frames` 在看不见的后台舞台按帧跑（可复现、可模拟键鼠），`view` 截图（无图用 `--text` 字符画）、`state` 读变量、`assert` 断言，用例固化到 `/自动化/tests/名字.json` 用 `gandi test` 回归；
⑤ **出错可找回**——错误 JSON 带 `code`/`hint` 与退出码 2，`doctor` 排障、`turn undo` 撤一轮、`history list/show/save/restore` 找回、`export` 导出 .sb3；
⑥ **DSL 是积木的另一种写法**——文本编回积木结构一致，但与 JS 有差异（序号从 1、`===` 不比类型、变量+变量按数字相加），高级数据结构须先确认装了哪个扩展版本再写。
核心洞察：pull→改→push→run/view/state/assert 是主线，base-rev 是并发安全锁，doctor/history 是安全网。

## A1 — 书中的应用 (Past Application)

### 案例一：把整个作品当文件夹改（worked_example，slug: cli-workflow / c01）
- **问题**：想让 AI 批量改一个作品，要先看清文件结构，又不想在编辑器里逐块点。
- **方法执行**：`gandi pull game` 把整个作品导出到 `game/` → 用普通编辑工具改里面的文件（积木页 `*.js`、角色 `sprite.json`、造型/声音文件）→ `gandi push game` 分批写回（建角色→变量/造型/声音/设置→积木页），编译错报本地文件名与行号、失败批不写。
- **结论**：文档所述效果——作品即一个文件夹，虚拟文件路径短而稳定（如 `主场景/Hero/main.js`，只有同层重名才带 `~id`）；再 pull 只更新本地没改过的文件。

### 案例二：后台舞台按帧验证（worked_example，slug: cli-workflow / c03）
- **问题**：改完文件后，AI 要不占编辑器舞台、按帧可复现地验证运行效果。
- **方法执行**：`gandi run --frames 120` 后台跑 120 帧 → `gandi view --output shot.png`（看不了图片用 `--text`）→ `gandi state` 读变量 → `gandi assert "score >= 3" "Hero.x > 0"`，并可模拟键鼠、按住的键跨多次 run 保持。
- **结论**：文档所述效果——运行在后台舞台，时间按帧推进、结果可复现；assert 不满足即报错，截图只含舞台渲染画面，不含监视器与编辑器界面。

## A2 — 触发场景 (Future Trigger) ★

### 用户会在什么情境下需要这个 skill?
1. 想让 AI/智能体用命令行读写、批量修改一个 Gandi 作品，而不是在界面里手点。
2. 想把作品导出成文件夹，用文本编辑器/脚本批量改积木或素材后再写回。
3. 改完想在无人值守的后台按帧跑一遍，截图或断言验证结果（CI/回归测试）。
4. CLI 报了 E_CONFLICT / E_DEGRADED_WRITE / 编译错，或想撤销一轮、找回旧版本。

### 语言信号
- "让 AI 用 CLI 做作品 / 把作品当文件夹改"
- "pull / push / DSL 写积木 / base-rev 冲突怎么办"
- "后台跑一下截图 / assert 断言 / gandi test 回归"
- "CLI 连不上 / doctor / history 找回 / E_CONFLICT / E_DEGRADED_WRITE"
- "用 CLI 做作品 / AI authoring / headless run / screenshot assert / DSL syntax"

### 与相邻 skill 的区分
- 与 `project-files`（also_read）：本卡用命令行做"改+验证"的工程闭环；project-files 管界面里的打开/保存 .sb3、版本历史、回收站、备份迁移。找回版本时两卡都涉及 `history`，本卡侧重 CLI 命令，后者侧重界面操作与数据保全。
- 与 `run-debug`（also_read）：本卡的 `run/view/state/assert` 是自动化的结果验证；run-debug 是人在调试面板里诊断卡顿、打断点单步。要"查为什么卡"用 run-debug，要"自动跑一遍断言通过没"用本卡。

## E — 可执行步骤 (Execution)

**输入契约**：一台装了 Node≥20 与 npm 的电脑、同一台电脑浏览器打开的 Gandi 编辑器、一个待改作品与明确的改动意图（改哪些积木/变量/素材）；首次需有人在编辑器里授权。
1. **装与授权**：`npm install -g @kukemc/gandi-cli`（或 npx）→ `gandi up` → 编辑器设置→CLI→"连接 CLI"→本机授权页确认。完成标准：`gandi doctor` 能连上编辑器（输出 next 而非排障指引）；判停：Node<20 或想连远程/云端则停止。
2. **导出并改**：选目标编辑器（`gandi editors` / `gandi use`，≤8 标签页）→ `gandi pull <作品>` → 按 DSL 改文件（先 `gandi blocks 关键词` 查写法、`gandi grep` 搜）。完成标准：`gandi check` 通过、无 E_* 错误。
3. **写回（二选一）**：整体改动用 `gandi push`（失败批不写、有冲突不推，`--dry-run` 只检查）；只改单文件走 `gandi files --kind blocks` → `read` 拿 rev → `check --file` → `write --base-rev`。判停：报 E_CONFLICT 必须重读再写；报 E_DEGRADED_WRITE 先装齐扩展重读该页；本地删除加 `--delete`。
4. **后台验证**：`gandi run --frames N` → `gandi view --output shot.png`（或 `--text`）→ `gandi state`（`--engine` 读物理光照）→ `gandi assert "..."`。完成标准：断言全通过；需要回归就把用例存到 `/自动化/tests/名字.json` 用 `gandi test` 逐条跑。
5. **找回/收尾**：出错看错误 JSON 的 `code`/`hint` 与退出码 2，`doctor` 排障；撤一轮 `gandi turn undo`；找回 `gandi history list/show/save/restore`（restore 加 `--confirm`）；导出 `gandi export --output game.sb3`。
**输出契约**：一个已写回并通过 `run/view/state/assert` 验证的作品；可选 .sb3 导出、固化的测试用例文件、排障/回滚记录。

## B — 边界 (Boundary) ★

### 不要在以下情况使用此 skill
- 用户想在界面里手动做作品、画造型、拖积木——走编辑器手动操作或对应独立 skill。
- 目标是 Gandi 2.0 或原版 Scratch——本卡基于 Gandi 3.0 CLI。
- 想通过 CLI 操作远程主机或云端编辑器——CLI 不支持，停止。

### 作者在文档中警告的失败模式
- 只连本机：CLI 只连同一台电脑上的编辑器，远程/云端连不上；换作品或改动丢失需重新 `up`。
- 协作房间不能整份还原：`gandi history restore` 在协作房间不可用；CLI 也不能在进入协作那一刻写入。
- 缺扩展页只读：读到含未装扩展积木的页是只读预览，写入报 E_DEGRADED_WRITE；若在预览上硬写会破坏隐藏结构（mutation、菜单影子、布尔槽空位），必须先装扩展、重读该页再改。
- E_CONFLICT：写入沿用旧 rev、期间有人改过就会冲突；不重读就改会反复失败、改动落不了盘。
- W_GANDI_ONLY：`===`/`!==`/`**`/三元/`break`/`continue` 等专有积木导出到原版 Scratch 打不开（≠ 例外），check 只警告不阻断。
- 高级数据结构对象恒真：`if (o)`、`o != 0` 对对象/列表恒为真，判空要用 `size(o) > 0` / `L.length > 0`。

### 文档的盲点 / 局限
- DSL 与 JS 有差异：序号从 1、`===` 不比类型、`%` 跟除数、变量+变量按数字加（连接用模板串），不支持 `new`/`typeof`/`switch`/`async`；`for...of` 里的 `break` 在编译模式被忽略。
- 代码模式是实验性、默认关，草稿只存本机 IndexedDB、不进作品，清浏览器数据无法找回。
- 截图只含舞台渲染画面，不含监视器和编辑器界面；后台舞台看不到画中画等宿主 UI。

### 容易混淆的邻近方法论
- `blocks-authoring` 管界面里自制/全局积木与作用域；DSL 只是"积木的另一种文本写法"，写的是同一份结构，改 DSL 不等于设计积木架构。
- `project-files` 的 `history` 与本卡 CLI `history` 是同一版本系统，但界面还原能"预览""只取回角色"，CLI 整份还原限制更多。

---

## 相关 skills
- composes-with: `project-files`、`run-debug`、`gandi-guide`（DSL 查积木写法）
- depends-on: 无（授权与 Node≥20 为前置环境，非 skill）

## 审计信息
- 验证通过: V1 ✓ / V2 ✓ / V3 ✓（task-first-v2）
- 来源: summary-part1 §二 CLI 与 AI（core 闭环/逐文件/验证/找回/DSL/高级数据结构/陷阱）；candidates/framework.md f19–f23、principle.md p20、case.md c01–c08、counter-example.md ce07/ce15–ce19/ce23；slug: cli / cli-workflow / dsl-syntax / more-data-types-dsl / code-mode
