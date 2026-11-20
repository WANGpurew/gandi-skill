# 术语词典 (GLOSSARY) — Gandi 3.0

> 全书共享术语，供所有能力卡引用。文档特有用法优先于常识。
> 阶段 3 产出，源自 glossary 提取器（43 条）。

```yaml
- id: g01
  term: 面板 / 组 / 分栏 / 浮窗
  type: term
  source_chapter: 开始使用·面板与布局
  author_definition: |
    "面板（功能区）、组（共享标签条的一叠面板）、分栏（按比例切格）、浮窗（浮于顶层）。"
    工作区/造型/声音/地图每角色一个，舞台/积木栏全局唯一；积木栏随最后点过的工作区。
  key_distinction: |
    ≠ 通用 UI 里的"面板/窗口" — 这四者是编辑器的四种界面容器，有严格的从属关系：
      组=共享一条标签条的一叠面板，分栏=按比例切格，浮窗=浮于顶层的面板。
    = 布局的基本组成单元；"布局"就是这四者的排布方案。
  why_it_matters: |
    下游 layout-workspace 类 skill 谈"摆界面"时指的就是摆这四种容器；
    若把它们当普通窗口，会误导用户去"关闭窗口"而非"停靠/分栏/浮出"。
  tags: [term, ui-container, core-concept]

- id: g02
  term: 布局锁
  type: term
  source_chapter: 开始使用·面板与布局·布局锁
  author_definition: |
    "面板都能拖，代价是到处留着拖放要用的地方：组与组之间的缝、只有一页也要有的标签条、
    浮窗的标题栏和窗口按钮。摆好之后把布局锁上，这些都收掉，地方让给内容。"
    快捷键 Ctrl+Alt+L；锁的状态随布局保存。
  key_distinction: |
    ≠ 常识里"锁定以防误操作" — 这里的主要作用是"收起拖拽占位、把地方让给内容"，
      分隔条/切页/面板开关照常可用。
    ≠ 只在本机生效 — 协作里被跟随者的布局也会"锁住"（跟随锁，同 LAYOUT_LOCKED）。
  why_it_matters: |
    用户说"界面太挤/占地方"时，skill 应提示开布局锁而非关面板；
    协作场景下还要能解释"为什么我的布局拖不动"。
  tags: [term, ui-container, collaboration]

- id: g03
  term: 通用设置 vs 作品设置
  type: term
  source_chapter: 设置·两类设置
  author_definition: |
    "「通用」跟着人（语言/主题/积木栏/声音开关，登录 CCW 连快捷键/插件/布局上云，主题背景图音效只本机）；
    「作品」跟着作品（舞台/帧率/克隆/编译加速，写进作品文件）。改动即时生效无「确定」按钮。"
  key_distinction: |
    ≠ 一般软件的"偏好设置 vs 项目设置"笼统二分 — Gandi 这里归属极严格：
      通用=跟人走、部分上云；作品=写进 .sb3 文件、随作品分发。
    主题"背景图/音效"是例外：归通用但只存本机、不上云。
  why_it_matters: |
    skill 判断"某个设置该在哪改、会不会随作品发给别人"全靠这条归属；
    搞混会导致把舞台帧率当个人偏好、或以为主题会写进作品。
  tags: [term, settings, core-concept]

- id: g04
  term: 扩展 vs 插件
  type: term
  source_chapter: 开发者·扩展与插件（答疑边界）
  author_definition: |
    "扩展给作品加积木、随作品保存；插件改编辑器、装在本机不写作品。"
    外部插件往本机放 {id, name, setup} 的 .js，靠宿主加载；宿主插件由宿主管。
  key_distinction: |
    ≠ 浏览器语境里"扩展=插件"的混用 — 二者作用对象与存放位置相反：
      扩展作用于"作品"（积木数据进 .sb3），插件作用于"编辑器"（只在本机）。
    扩展缺了会让作品出现占位块；插件缺了不影响作品内容。
  why_it_matters: |
    这是用户最常混的一对词。下游 skill 在答疑/选型时必须先分清：
    要"更多积木"装扩展，要"改编辑器行为"装插件；判断分享时也要知道插件不随作品走。
  tags: [term, extension, plugin, core-concept]

- id: g05
  term: 模块
  type: term
  source_chapter: 积木编程·全局积木
  author_definition: |
    "模块＝只放代码的角色，可定义全局积木。"
    仅「模块」可以开「全局积木」；多场景再开「所有场景」时模块可跨场景常驻。
  key_distinction: |
    ≠ 编程里"模块=代码文件/库" — 这里模块是角色栏里的一种"角色"，
      不摆造型、只承载脚本，专门用来放全局积木。
  why_it_matters: |
    用户想"所有角色共用一段积木"时，skill 要知道第一步是建一个模块角色，
    而不是普通角色，否则全局积木入口不出现。
  tags: [term, blocks, role]

- id: g06
  term: 积木页
  type: term
  source_chapter: 积木编程·积木页
  author_definition: |
    "角色脚本分页：根页恒定无行；新建子页右键角色/舞台→新建，F2 重命名、Delete 删（连脚本/注释/框）。
    脚本首块右键「移动到积木页」（≥2 页）。存 .sb3 仍是普通作品。"
  key_distinction: |
    ≠ 代码编辑器里"标签页=打开文件" — 积木页是同一个角色内部脚本的分页，
      不是多文件；分页纯属组织用途，导出后与原版作品无差别。
  why_it_matters: |
    组织复杂脚本（task-03）的核心手段之一。skill 要引导"长脚本按功能分页"，
    并知道删页会连脚本一起删、需先确认。
  tags: [term, blocks, organization]

- id: g07
  term: 全局积木
  type: term
  source_chapter: 积木编程·全局积木
  author_definition: |
    "仅「模块」可定义；开「全局积木」（全作品不重名）、多场景再开「所有场景」（模块跨场景）；
    栏分全局/本角色两档；改定义全作品同步、一步撤销；有角色用时删不掉。"
  key_distinction: |
    ≠ 编程语言里"全局函数" — 它是积木栏里一类带"全作品唯一名字"约束的自制积木，
      且有"两道开关"（全局积木 + 所有场景），只在模块里定义。
    导入/手改造成同名时只认排前的那个，改一个两处都变（陷阱）。
  why_it_matters: |
    skill 指导"跨角色/跨场景复用脚本"时要讲清建模块→开两道开关的顺序，
    并提醒同名冲突与"有引用删不掉"的限制。
  tags: [term, blocks, reuse]

- id: g08
  term: 作用域三档
  type: term
  source_chapter: 积木编程·变量与列表
  author_definition: |
    "变量与列表三档作用域——全局（所有场景）/仅本场景（默认）/仅本角色；
    右键「修改变量」改名字/分类/作用域，改作用域不能撤销（首次 Ctrl+Z 只提示）。"
  key_distinction: |
    ≠ 通用编程的"全局/局部"两档 — Gandi 有中间档"仅本场景（默认）"，
      且默认档不是全局；"分类//名字"只是显示折叠、真名不变。
    最关键差异：作用域一旦改不可撤销。
  why_it_matters: |
    task-03/作用域设计的核心。skill 必须强调"建变量时就选对作用域"，
    因为文档明确改作用域不可撤销，事后补救代价高。
  tags: [term, blocks, variable, core-concept]

- id: g09
  term: 原版增强
  type: term
  source_chapter: 积木编程·补全积木
  author_definition: |
    "「原版增强」是作品级设置，开启后多出一批补全积木：旋转中心偏移、x/y 拉伸、视频、
    带参广播（≤16 按位置对应）、瞬时执行、跳出/跳过循环、画笔增强等；编译原生执行（视频组除外）。"
  key_distinction: |
    ≠ "把作品升级成原版 Scratch 增强版" — 它只是 Gandi 自加的一组积木开关，
      且这些积木存进 .sb3 后用原版 Scratch 打不开（W_GANDI_ONLY，少数例外）。
  why_it_matters: |
    skill 在用户要"旋转中心、带参广播"等能力时要提示先开作品级"原版增强"，
    并提醒导出到原版 Scratch 的兼容性风险。
  tags: [term, blocks, setting]

- id: g10
  term: 代码框
  type: term
  source_chapter: 整理与查找·代码框
  author_definition: |
    "空白右键「创建代码框」或 Ctrl+A 拖矩形（<20×20 不留）；归属靠画框时"碰到"（角压 1/10 也算）；
    折叠真卸下积木减负；选中可拖/改名/换色/锁/导出 SVG；Delete 删连积木一步撤销；
    只属画它那一页，不嵌套。"
  key_distinction: |
    ≠ 图形软件的"框选/画框"临时选中工具 — 代码框是持久的画布分组容器，
      有归属判定、可折叠（折叠会把积木真卸下以减负）、可锁、可导出 SVG。
    ≠ 普通注释框 — 它是整理积木结构的对象，删框会连里面的积木一起删。
  why_it_matters: |
    code-navigation/整理复杂脚本的核心手段。skill 要讲清"折叠减负"与普通隐藏的区别，
    以及没有"只删框留积木"入口（靠 Ctrl+Z）。
  tags: [term, blocks, organization]

- id: g11
  term: 片段
  type: term
  source_chapter: 整理与查找·工作区杂项
  author_definition: |
    "片段是从工作区导出/复用的一段积木文本（DSL）；片段定义不能存——
    自制积木的定义、代码框里的积木都不能存成片段。"
  key_distinction: |
    ≠ 通用编辑器里"snippet=可保存复用的模板" — 这里片段是导出用的临时产物，
      且明确"不能把定义存成片段"，自制的定义、框内积木都被排除。
  why_it_matters: |
    skill 在指导"复用一段积木"时要区分：复用脚本靠全局积木/符号，片段只是临时搬运，
    别误导用户把自制积木定义存进片段。
  tags: [term, blocks, reuse]

- id: g12
  term: 任意①
  type: term
  source_chapter: 整理与查找·查找替换
  author_definition: |
    "查找替换里槽的一种状态：'填什么都算，并且记住'——槽里填着 10 就记住 10，
    槽里插着 x坐标 就记住整块 x坐标；「换成」那边的槽可引用这个记住的值。"
    "「换成」的槽有三态：填死的值、引用 ①、留空（用积木自带的默认值）。"
  key_distinction: |
    ≠ 通配符"*"只做匹配 — 任意①除了"匹配任意"还"记住该值"，
      让替换侧能引用回原值（类似正则捕获组），这是普通"任意值"没有的能力。
  why_it_matters: |
    task-04 批量替换的高级用法。skill 讲"保持原值只改别的槽"时必须用任意①，
    否则会误以为只能整体填死值。
  tags: [term, find-replace, dsl]

- id: g13
  term: pull / push
  type: term
  source_chapter: CLI 与 AI·核心闭环
  author_definition: |
    "gandi pull game → 改文件 → gandi push game：把作品导成文件夹来改。
    pull 只更新未改文件（--force 覆盖）；push 分批写回（建角色→变量/造型/声音/设置→积木页），
    编译错带文件名行号、失败批不写、冲突不推（--force）。"
  key_distinction: |
    ≠ Git 的 pull/push — 这里是"本机编辑器里的作品"与"本地文件夹"之间同步，
      不是与远程仓库；且只连本机编辑器、pull 不覆盖你改过的文件。
  why_it_matters: |
    cli-ai-workflow 主线（task-05）。skill 必须讲清闭环与"pull 不覆盖已改文件、
    push 分批且失败批不写"的安全语义，避免用户当 Git 用而丢改动。
  tags: [term, cli, core-concept]

- id: g14
  term: base-rev
  type: term
  source_chapter: CLI 与 AI·逐文件安全编辑
  author_definition: |
    "gandi write 写入时带上的、从 read 读到的文件版本号：
    '--base-rev 版本号'。写入带着读到的版本号，期间有人改过就报 E_CONFLICT，需要重新读一遍再改。"
  key_distinction: |
    ≠ 一般 REST 的 ETag/乐观锁只是"防覆盖提示" — 这里它是逐文件写入的必带参数，
      与 E_CONFLICT 配套构成"读→改→带 rev 写"的强制安全闭环。
  why_it_matters: |
    task-05 逐文件安全编辑的关键。skill 必须强调"写前先 read 拿 rev、带上 base-rev"，
    否则在协作/多人场景会反复冲突。
  tags: [term, cli, conflict]

- id: g15
  term: E_CONFLICT
  type: term
  source_chapter: CLI 与 AI·逐文件安全编辑
  author_definition: |
    "写入时 base-rev 与当前版本不符（期间有人改过该文件）报的错误：
    '期间有人改过就报 E_CONFLICT，需要重新读一遍再改'；场景在读和写之间改过名也会报 E_CONFLICT。"
  key_distinction: |
    ≠ 泛泛的"冲突" — 它是 CLI 逐文件写回时的具体错误码，
      解法固定为"重读拿新 rev 再改"，不是简单重试覆盖（--force 才强推）。
  why_it_matters: |
    skill 排障时要能把 E_CONFLICT 翻译成"文件被别人改了，重读再改"，
    并区分该文件冲突与场景改名冲突（后者还伴 W_SCENE_RENAMED）。
  tags: [term, cli, error, conflict]

- id: g16
  term: 一轮改动
  type: term
  source_chapter: CLI 与 AI·撤销与历史
  author_definition: |
    "AI 开始一轮工作时，编辑器先存一个版本，然后记下这一轮改过的文件。
    gandi turn undo 或顶栏「CLI 活动」里的「撤销这一轮」撤回这一轮的文件改动；
    之后被人改过的文件跳过并说明。"
  key_distinction: |
    ≠ Ctrl+Z 的"一步撤销" — 一轮改动是 AI 工作粒度的批量快照，
      撤销单位是"这一轮"，且已被人改过的文件会被跳过（不连坐）。
  why_it_matters: |
    cli-ai-workflow 的回退入口。skill 在讲"AI 改坏了怎么退"时要用 turn undo，
    并说明它与普通撤销、与整份 history restore 的粒度差异。
  tags: [term, cli, undo]

- id: g17
  term: 后台舞台
  type: term
  source_chapter: CLI 与 AI·run/view/state/assert
  author_definition: |
    "CLI 跑作品、看舞台、读变量默认在一个看不见的后台舞台上进行，不占编辑器里的舞台。
    '运行默认在一个看不见的后台舞台上……时间按帧推进，计时器、等待、滑行、物理、粒子都跟着帧走，结果可以复现。'"
  key_distinction: |
    ≠ 编辑器里那个可见的舞台 — 后台舞台不可见、按帧推进、可复现，专供自动化验证；
    截图只含舞台内容。协作里在后台舞台跑不算"编辑"，不会同步给别人。
  why_it_matters: |
    task-05 自动化验证的基础。skill 要解释 run/view/state/assert 都作用在后台舞台，
    用户能继续用编辑器，且帧推进保证断言可复现。
  tags: [term, cli, testing]

- id: g18
  term: gandi-dsl
  type: term
  source_chapter: CLI 与 AI·积木文本（DSL） / 积木编程·注释
  author_definition: |
    "积木文本是积木的另一种写法，读写结构一致：声明置顶、if/while/for、Gandi 专有 ===/**/?:/break/continue、
    参数槽=回调形参、define()/call[]；注释用 /** */；错误 E_*/W_* 的 fix 给改法。"
    注释里用 ```gandi-dsl 围栏，拖工作区积木进注释生成 DSL、拖回变真积木（旧 ```blocks 围栏不再识别）。
  key_distinction: |
    ≠ JavaScript — 语法像 JS 但语义不同：序号从 1、=== 不比类型、% 跟除数、
    变量+变量按数字加、不支持 new/typeof/switch/async。
    ≠ 一般"文本格式" — 它是与积木结构一一对应的写法，可往返转换。
  why_it_matters: |
    cli-ai-workflow 与注释示范都依赖它。skill 指导"用文本批量造积木"或"在注释里演示积木"时
    必须用 gandi-dsl，并提醒与 JS 的差异，否则 AI 写出 JS 风格会报错。
  tags: [term, dsl, cli, blocks]

- id: g19
  term: 代码模式
  type: term
  source_chapter: CLI 与 AI·代码模式 / 设置·作品参数
  author_definition: |
    "代码模式（实验、默认关）：设置→通用→实验开启；工作区右上「积木/代码」或 Ctrl+反引号切换；
    停输入 400ms 按段应用；声明区/缺扩展/自检失败时只读；草稿存本机 IndexedDB 不进作品。"
  key_distinction: |
    ≠ "把积木作品变成真代码工程" — 它是实验性编辑视图，积木与代码同源、按段热应用，
      草稿只存本机不写进作品，缺扩展的页只读（写入报 E_DEGRADED_WRITE）。
  why_it_matters: |
    skill 谈"直接用文本改脚本"时要标注实验性、草稿不进作品、需先装扩展重读等边界，
    避免用户以为代码改动会自动保存进 .sb3。
  tags: [term, code-mode, experimental]

- id: g20
  term: 编辑态 vs 运行态
  type: term
  source_chapter: 协作原理·编辑态与运行态（心智模型）
  author_definition: |
    "Y.Doc 只放编辑状态；运行态坐标/克隆体和素材字节都不放（只放 md5）。
    位置/显隐/造型只在显式编辑写文档，变量值只新建/显式编辑写，故「跑完保存当初始位置」不灵。"
    协作只同步显式编辑的变量值与位置，运行时移动/克隆/变量变化不同步。
  key_distinction: |
    ≠ "编辑器里看到的 = 运行时发生的" — Gandi 严格区分：
      协作同步的是"人显式编辑的结果"，不是"作品跑起来后的状态"。
    这条也是"为什么变量值/运行位置不同步"的根因。
  why_it_matters: |
    extensions-collab/协作答疑的核心。skill 要借此解释协作中的同步边界，
    并纠正"跑完保存当初始位置""运行时变量变化会同步"等常见误解。
  tags: [term, collaboration, core-concept, mental-model]

- id: g21
  term: 帧间隔（delta time）
  type: term
  source_chapter: 运行与调试·帧间隔
  author_definition: |
    "「帧间隔(秒)/每秒(n)/实际帧率」：把每帧增量换成「每秒()」（移动 10 步×30 帧＝每秒 300 步），
    上限 0.1 秒；让速度独立于帧率。"
  key_distinction: |
    ≠ 一般动画的"帧率设置" — 帧间隔不是调快慢，而是让运动速度与帧率解耦；
    上限 0.1 秒意味着低于 10 帧时反而变慢动作。
  why_it_matters: |
    run-debug/帧率无关运动改造（task-08）的核心。skill 要引导用"每秒()"替代"每帧移动 N 步"，
    并提醒上限导致的慢动作副作用。
  tags: [term, runtime, delta-time]

- id: g22
  term: 补帧
  type: term
  source_chapter: 运行与调试·帧间隔
  author_definition: |
    "补帧让画面顺、帧间隔让速度独立，两者可同用：补帧补出中间位置让画面顺滑，
    帧间隔保证速度不随帧率变。"
  key_distinction: |
    ≠ 帧间隔 — 补帧作用于"画面平滑度"（插值中间位置），帧间隔作用于"速度独立性"；
    常被误当成同一个设置，实际可同时开启。
  why_it_matters: |
    skill 讲解"卡顿/不流畅"时要分清：速度不稳用每秒()，画面跳用补帧；
    另注意"不限帧率"下动画插值（补帧类机制）失效。
  tags: [term, runtime, animation]

- id: g23
  term: 编译模式
  type: term
  source_chapter: 运行与调试·加速 / 设置·作品参数
  author_definition: |
    "编译模式默认开、随作品保存，数量级提升运行速度；设断点/排查时需临时关闭，
    报错方式与解释模式不同。"
    "编译原生执行（原版增强积木视频组除外）。"
  key_distinction: |
    ≠ 开发里"编译=生成可执行文件" — 这里是把积木编译成原生代码提速的运行时开关，
    默认开；调试（断点只在解释模式生效）时必须临时关。
  why_it_matters: |
    run-debug 的隐藏前提。skill 在讲断点、诊断、报错解读时必须提醒"先关编译模式"，
    否则断点不生效、报错方式对不上。
  tags: [term, runtime, debug, performance]

- id: g24
  term: 监视器
  type: term
  source_chapter: 运行与调试·舞台
  author_definition: |
    "勾选报告的积木会以监视器形式上舞台，可拖动摆放（位置存 .sb3），
    有正常/大字/滑杆三种样式。"
  key_distinction: |
    ≠ 通用"监控面板/仪表盘" — Gandi 监视器是具体某个积木值的可视控件，
    由"报告"类积木生成、贴在舞台上，样式随人设但位置写进作品。
  why_it_matters: |
    run-debug 常用手段。skill 讲"把某个值显示在舞台上观察"时要指向监视器，
    并注意它可拖摆、随作品保存。
  tags: [term, runtime, monitor]

- id: g25
  term: 探针
  type: term
  source_chapter: 运行与调试·调试工作台
  author_definition: |
    "调试用的探针机制：F3 调试信息覆盖舞台不挡操作，可拖积木按频率求值；
    调试工作台/运行调试里作为观测点的统称（另见录制档、日志点）。"
  key_distinction: |
    ≠ 硬件/系统里"探针=侵入式采样工具" — 这里是舞台上的轻量观测手段：
    把某积木挂上去按频率求值显示，属于调试工具链一环，不改作品逻辑。
  why_it_matters: |
    run-debug 工具链的入口之一。skill 要区分探针（实时求值）、F3（状态覆盖层）、
    录制档（事后分析）各自用途，避免混为一谈。
  tags: [term, debug, probe]

- id: g26
  term: 录制档 / .gtrace
  type: term
  source_chapter: 运行与调试·调试工作台
  author_definition: |
    "调试工作台可录制（5 秒档/轻·完整档）一段运行，上限 3600 帧/20 万条，
    导出为 .gtrace，并可「记为基线」用于对比。"
  key_distinction: |
    ≠ 视频录制 — 录制档记的是逐帧执行数据（积木耗时、线程、事件等），不是画面；
    .gtrace 是它导出的分析文件格式，可设基线对比前后性能。
    "自耗时排行"只在完整档才有。
  why_it_matters: |
    task-08 卡顿诊断主线：F3→录制→概览→帧/积木页→跳到积木。
    skill 要讲清录制档的档位差异、.gtrace 导出与基线用法。
  tags: [term, debug, trace, performance]

- id: g27
  term: 自耗时
  type: term
  source_chapter: 运行与调试·调试工作台·积木页
  author_definition: |
    "调试工作台「积木」页给出的自耗时排行（仅完整录制档才有），
    用于定位哪些积木自身耗时间最多。"
  key_distinction: |
    ≠ 积木的总耗时/调用次数 — 自耗时指积木"自身"消耗的时间（不含子积木），
      是找热点帧里具体慢积木的指标，且只有完整档才统计。
  why_it_matters: |
    run-debug 卡顿定位的落点指标。skill 要引导先录完整档再看自耗时排行，
    否则轻量档看不到该页数据。
  tags: [term, debug, performance]

- id: g28
  term: 日志点
  type: term
  source_chapter: 运行与调试·断点单步
  author_definition: |
    "断点的一种变体：'只打不停'——命中时只打印日志、不暂停执行。"
    与条件断点（{变量}>100）、每 N 次停、变量被改/广播/克隆时停并列。
  key_distinction: |
    ≠ 普通断点（命中即暂停） — 日志点只记录不中断，相当于"带条件的可视 log"；
    且所有断点/日志点只在解释模式生效、不写进作品。
  why_it_matters: |
    run-debug 排错手段。skill 要指导"不想打断运行、只想看某处值"时用日志点，
    并提醒需关编译模式、断点不随作品保存。
  tags: [term, debug, breakpoint]

- id: g29
  term: 装配（装配编辑器）
  type: term
  source_chapter: 引擎·装配编辑器
  author_definition: |
    "光照/粒子/物理共用的一套物体配置，由装配编辑器编辑：
    配置挂造型文件夹、各级相加从外到里；克隆体读本体、积木改临时覆盖、停止后清。"
  key_distinction: |
    ≠ 一般"装配=拼装零件" — 这里是给造型挂"物体配置"（碰撞体、灯、发射器等）的专门编辑器，
      配置按造型层级叠加；积木对它的改动是"本次运行的临时覆盖"，不写作品。
  why_it_matters: |
    engine-physics-light（task-09）的公共入口。skill 要先讲清"装配编辑器配持久配置、
    积木只改本次运行"的分工，否则用户会以为积木改了会保存。
  tags: [term, engine, assembly]

- id: g30
  term: 层级覆盖（帧覆盖）
  type: term
  source_chapter: 引擎·装配编辑器
  author_definition: |
    "装配配置挂造型文件夹、各级相加从外到里；「一份」参数须唯一归属，
    通过「设为物体」逐层覆盖。"
  key_distinction: |
    ≠ CSS 那种"就近覆盖" — 这里是沿造型层级从外到里逐级相加、
    某些参数要求"唯一归属"，必须显式「设为物体」来定归属，否则不生效。
  why_it_matters: |
    skill 指导"给造型某层配灯/碰撞体"时要讲清层级叠加与归属规则，
    避免用户在外层配了却看不到效果。
  tags: [term, engine, assembly, override]

- id: g31
  term: 实例覆盖
  type: term
  source_chapter: 引擎·装配编辑器
  author_definition: |
    "克隆体读本体的装配配置；用积木改动的是该实例的临时覆盖，停止运行后被清除、
    不影响本体与作品文件。"
  key_distinction: |
    ≠ 面向对象"实例覆盖原型属性"会持久 — 这里实例覆盖是"运行期临时值"，
      停止即清、不写回作品，本体配置不变。
  why_it_matters: |
    skill 要解释"为什么积木改物理/光照停止后就还原"——因为是实例覆盖；
    想持久改要去装配编辑器改本体配置。
  tags: [term, engine, override]

- id: g32
  term: 规则层
  type: term
  source_chapter: 引擎·瓦片地图
  author_definition: |
    "地图瓦片的一种层：规则层照另一层自动铺（按规则从相邻层推导瓦片）。"
  key_distinction: |
    ≠ 通用"图层" — 规则层的内容不是手画的，而是参照另一层按规则自动生成/自动拼边，
    改参照层会跟着变。
  why_it_matters: |
    地图搭建（task-09）中，skill 讲"自动铺地形/边角"时要指向规则层，
    省去手铺，并提醒它依赖参照层。
  tags: [term, engine, tilemap]

- id: g33
  term: 地形
  type: term
  source_chapter: 引擎·瓦片地图
  author_definition: |
    "地图瓦片绘制中的地形工具：绘制时自动拼边角（相邻瓦片自动匹配边缘）。"
  key_distinction: |
    ≠ 游戏开发里"地形=高度场/地貌系统" — 这里是瓦片地图的画笔模式之一，
      作用是"自动拼接边角"，让相邻瓦片边缘自然衔接。
  why_it_matters: |
    skill 指导画地图时要区分地形（自动拼边）与普通瓦片/图案（手画）；
    后两种方格/等距/交错/六边形里，交错与六边形没有地形。
  tags: [term, engine, tilemap]

- id: g34
  term: 标记
  type: term
  source_chapter: 引擎·瓦片地图
  author_definition: |
    "地图上可摆放的特殊点（如出生点/敌人/宝箱），运行时可据标记摆角色。"
    与瓦片设置里的"标签、属性、寻路代价"并列。
  key_distinction: |
    ≠ 文档标注的"标记" — 它是地图上的语义锚点，供脚本读取来生成角色/事件，
      不是给玩家看的文字标记。
  why_it_matters: |
    寻路/刷怪类玩法搭建时，skill 要引导用标记定位出生点/敌人，
    而非硬编码坐标。
  tags: [term, engine, tilemap]

- id: g35
  term: 占位块
  type: term
  source_chapter: 扩展与插件·缺扩展占位块
  author_definition: |
    "没装上的扩展的积木会变成灰色占位块（数据不改），装上扩展后自动换回真积木。"
  key_distinction: |
    ≠ 开发里的"占位符/TODO" — 占位块保留原积木的数据，只是不能执行/显示异常；
    它是"缺扩展"的可视信号，装上对应扩展即可原地还原，不丢数据。
  why_it_matters: |
    skill 遇到作品打不开/积木变灰时要能判断"缺扩展"，并说明装回扩展会自动还原、
    数据未丢，避免用户误以为作品损坏。
  tags: [term, extension, compatibility]

- id: g36
  term: 移植版 id
  type: term
  source_chapter: 扩展与插件·TurboWarp 兼容
  author_definition: |
    "导入 turbowarp.org 作品时，若扩展库里认得该扩展的移植版（id 认得）就换成库 id，
    否则原样保留；换错 id 会导致整个作品打不开。"
  key_distinction: |
    ≠ 普通"ID 映射" — 它是 TurboWarp 扩展 id 到 Gandi 库 id 的兼容映射，
    只换"库里认得的"，且换错代价极高（作品整体打不开）。
  why_it_matters: |
    task-10 作品迁移时，skill 要提示移植版 id 机制与"换错 id 整个作品打不开"的风险，
    不要盲目替换 id。
  tags: [term, extension, migration, compatibility]

- id: g37
  term: 宿主
  type: term
  source_chapter: 扩展与插件·作品服务 / 开始使用·依赖宿主的功能
  author_definition: |
    "Gandi 可嵌入宿主运行；CLI 标记/云背包/作品服务面板等依赖宿主，网页版没有。
    无宿主时作品服务四面板罩毛玻璃标「开发中」，宿主面板积木无宿主立即关闭、不伪造数据。"
  key_distinction: |
    ≠ 泛称"宿主程序" — 在 Gandi 里"有没有宿主"直接决定若干功能是否可用：
    网页版缺失这些入口；作品服务面板在无宿主时点不动、数据写死。
  why_it_matters: |
    skill 要能解释"为什么我这里找不到导出/CLI 标记/作品服务"——因为在网页版无宿主；
    避免用户反复找不存在的功能。
  tags: [term, host, boundary]

- id: g38
  term: 权限组
  type: term
  source_chapter: 协作与社区·权限组
  author_definition: |
    "默认管理员（改全部内容+管成员，不改组）/编辑者（改全部内容）/旁观者（只读可评论）；
    仅创建者能改组（≤16 组），最多 10 人。权限实时生效，越权改动被服务端撤回需重新进入。"
  key_distinction: |
    ≠ 通用"用户角色/权限" — 这里是邀请协作时的三档权限组，
    且有一条硬规则：改组权限只有创建者有；越权会被服务端撤回而非前端拦截。
  why_it_matters: |
    task-10 协作流程核心。skill 要指导按人分权限组，并说明越权改动会被撤回、
    被移出/改权限后需"重新加载"进入。
  tags: [term, collaboration, permission]

- id: g39
  term: 软锁
  type: term
  source_chapter: 协作原理·三类软锁
  author_definition: |
    "三类软锁（基于 awareness、断线自动释放）：拿着的元素、自制积木定义等；
    自制积木定义同时只允许一人改（签名是定义 + 所有调用块共同的事）。"
  key_distinction: |
    ≠ 数据库"锁"或"软删除" — 它是协作里的"占用声明"：
    谁在编辑某元素/定义就占着，别人只能看；锁随 awareness 走，断线自动释放，
    不是真的锁死、也不会持久化。
  why_it_matters: |
    skill 要借此解释"为什么别人改不了我正在改的自制积木"、"断线后锁为何消失"，
    以及并发编辑的边界。
  tags: [term, collaboration, lock, mental-model]

- id: g40
  term: 换代（generation）
  type: term
  source_chapter: 协作原理·换代
  author_definition: |
    "导入作品和回退历史要整个换掉文档；实时编辑里没法'把文档换成另一份'，所以服务端换的是代：
    存 before-replace、rooms.generation + 1、写新快照，给在线者发关闭码 4410（document replaced），
    双方重新取票据连接。文档格式版本比自己新会拒绝进入。"
  key_distinction: |
    ≠ 软件"版本升级" — 换代是协作文档的整份替换机制，
    在线的人会被强制断开重连；不是增量合并，而是"换一代文档"。
    关闭码 4410 专门表示换代，区别于 4401/4403/4409。
  why_it_matters: |
    skill 排障时要能区分"自动重连"（4400/4408/断网）与"必须重新加载/重进"（4401/4403/4409/4410），
    换代属于后者，且旧数据不删。
  tags: [term, collaboration, error, mental-model]

- id: g41
  term: Y.Doc / CRDT
  type: term
  source_chapter: 协作原理·文档模型
  author_definition: |
    "协作＝每人一份 Yjs CRDT 文档（Y.Doc），增量经服务转发、CRDT 合并；
    服务端只认人/查权限/存。房间内存一份 Y.Doc，只放编辑状态，运行态坐标/克隆体和素材字节都不放（只放 md5）。"
  key_distinction: |
    ≠ 中央数据库文档 — Y.Doc 是每人本地一份、可离线编辑、靠 CRDT 自动合并的文档模型；
    服务端不保存运行态与素材本体，因此"跑完保存当初始位置"不灵。
  why_it_matters: |
    extensions-collab 的底层心智模型（背景）。skill 借此解释"并发编辑为什么不丢、
    撤销为什么只撤自己、什么同步什么不同步"，是协作答疑的根。
  tags: [term, collaboration, mental-model, background]

- id: g42
  term: 定位
  type: term
  source_chapter: 协作与社区·并发处理
  author_definition: |
    "并发时同一参数口只留一块、其余挪到旁边并提示「定位」；
    另有「跳到他那里」（点头像）是跳到别人视角、不改我布局。"
  key_distinction: |
    ≠ 日常"定位=找到位置" — 这里是协作并发冲突后的处理提示：
    被挪开的积木给出「定位」让人去找/处理；与"跳到别人那里"是两个不同动作。
  why_it_matters: |
    skill 解释协作里"我的积木怎么被挪走了"时要指向定位提示，
    并区分"定位（找被挪的块）"与"跳到他那里（换视角）"。
  tags: [term, collaboration, conflict]

- id: g43
  term: 跟随
  type: term
  source_chapter: 协作与社区·看到别人/跟随
  author_definition: |
    "点头像菜单→「跳到他那里」（不改我布局）或「跟随」（我布局临时换成他的并锁住，
    Esc/停止还原）；被跟随者不能反跟随。跟随中布局不可改。"
  key_distinction: |
    ≠ 屏幕共享 — 跟随只把"我的界面布局临时切成对方的并锁住"，
    面板里的内容照常可编辑；且是单向的（被跟随者不能反跟随）。
  why_it_matters: |
    skill 讲"看别人怎么操作"时要讲清跟随的单向性、布局锁定与 Esc/停止还原，
    避免用户以为不能编辑或能互跟。
  tags: [term, collaboration, follow]
```
