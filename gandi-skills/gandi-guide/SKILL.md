---
name: gandi-guide
description: |
  当用户询问 Gandi 3.0 文档或功能本身(界面/布局/设置/快捷键/术语)，或涉及未独立成 Skill 的主题时调用:
  界面布局与跨设备迁移、整理查找与批量替换、造型动画与声音素材创作、设置二分(通用vs作品)、主题快捷键多语言、 代码文件管理、回收站、注释与颜色选择器、导入导出。
  以下意图优先用同包独立 Skill: CLI/AI做作品→cli-authoring；调试排错→run-debug； 积木脚本组织→blocks-authoring；作品文件版本→project-files；多场景→scenes-assets； 物理光照粒子地图→engine-tools；扩展插件协作→extensions-collab。
  Triggers: Gandi文档/界面/布局/设置/快捷键/素材/造型/声音/查找替换/回收站
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: router
  cangjie.bundle-id: bundle.gandi-guide
  cangjie.capability-count: 10
  cangjie.entrypoint-count: 8
---
# Gandi 3.0 功能文档 — 来源路由入口（compact pack）

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 原版 Scratch 或其它图形化编程工具的具体问题
- Gandi 扩展/插件开发者的 API 签名、注册点、编译管线细节（只作答疑背景）
- 协作服务端部署、环境变量、发布回滚、测试分层等运维内容
- 需要查看用户私有 .sb3 逐行内容的具体调试（本 skill 给方法流程，不看私有工程）

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. Gandi 3.0 是积木编程的互动作品平台：编辑器 + CLI + 引擎 + 协作，作品以 .sb3 保存。
2. 用 CLI 做作品是工程化闭环：gandi up 授权→pull→改文件→push→run/view/state/assert 验证→doctor/history 排障找回。
3. 复杂脚本靠分页+自制/全局积木+作用域三档组织；改变量作用域不可撤销，建时就要选对。
4. 多场景把作品拆成多个小作品，角色可跨场景常驻，场景间带参切换与广播；场景增删改无撤销。
5. 调试走工具链：F3 看状态→录制找卡顿→断点单步→数据面板改值→诊断/静态检查；设断点要临时关编译模式。
6. 速度要与帧率解耦用每秒()，画面要顺用补帧；上限 0.1 秒。
7. 引擎三件套(物理/光照/粒子)+瓦片地图通过装配编辑器给造型挂配置，积木只改本次运行。
8. 协作只同步显式编辑(编辑态)，不同步运行态与个人偏好；撤销只撤自己；关闭协作永久移除。

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 让 AI 用 CLI 做 Gandi 作品；把作品当文件夹批量改；用积木文本语法写积木；后台运行截图断言验证；CLI 冲突或错误码怎么办 | references/capabilities/cli-authoring.md | 已晋级为独立 Skill `cli-authoring`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 作品运行卡顿怎么排查；怎么打断点单步调试；变量值不对怎么查；作品有什么结构错误；速度想与帧率无关 | references/capabilities/run-debug.md | 已晋级为独立 Skill `run-debug`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 怎么组织复杂的积木脚本；怎么做一个带参数的自制积木；多个角色怎么共用一个积木；变量作用域怎么选；怎么给积木写注释 | references/capabilities/blocks-authoring.md | 已晋级为独立 Skill `blocks-authoring`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 怎么打开保存 Gandi 作品；改坏了怎么找回之前版本；误删角色怎么还原；怎么备份迁移作品到另一台电脑；代码文件怎么管理 | references/capabilities/project-files.md | 已晋级为独立 Skill `project-files`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 怎么做一个多场景游戏；角色怎么跨场景常驻；场景之间怎么切换传参；怎么复用素材而不误改 | references/capabilities/scenes-assets.md | 已晋级为独立 Skill `scenes-assets`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 怎么做有重力的平台跳跃；怎么给作品加光照；怎么制作粒子爆炸效果；怎么用瓦片地图做关卡 | references/capabilities/engine-tools.md | 已晋级为独立 Skill `engine-tools`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 怎么安装扩展或插件；怎么和别人同时编辑一个作品；协作里怎么控制权限；为什么运行位置没同步；断线了要重连还是重新进入 | references/capabilities/extensions-collab.md | 已晋级为独立 Skill `extensions-collab`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 怎么摆好面板并保存布局；换电脑怎么迁移界面配置；某个设置是跟人还是跟作品；平板上怎么操作 | references/capabilities/layout-workspace.md | references/capabilities/code-navigation.md |
| 怎么快速找到某个积木；怎么批量替换积木上的值；怎么折叠整理一大堆脚本；怎么用一句话生成一串积木 | references/capabilities/code-navigation.md | references/capabilities/blocks-authoring.md |
| 怎么画造型做动画；怎么给录音降噪；怎么制作逐帧动画并导出视频；怎么用编曲台写曲 | references/capabilities/media-creation.md | references/capabilities/scenes-assets.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- 意图在路由表与能力索引均无法命中 → 明确说明超出文档范围，不硬套。
- 用户问的是 Gandi 2.0 或原版 Scratch → 停止，说明本 skill 基于 Gandi 3.0。
- 涉及暂不可用功能(云变量/作品服务面板等) → 如实说明当前状态，不编造可用流程。
