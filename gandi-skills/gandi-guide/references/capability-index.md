# 能力索引（完整版）

| capability_id | 标题 | 重要度 | 意图 | 关键词 | 能力卡 |
|---|---|---|---|---|---|
| cap.gandi.cli-ai-workflow | 用 CLI/AI 读写与验证作品（含 DSL） | critical | 让 AI 用 CLI 做 Gandi 作品；把作品当文件夹批量改；用积木文本语法写积木；后台运行截图断言验证；CLI 冲突或错误码怎么办 | CLI、pull、push、DSL、base-rev、E_CONFLICT、assert、截图、gandi up、AI做作品 | capabilities/cli-authoring.md |
| cap.gandi.run-debug | 运行调试与排错（卡顿/断点/静态检查） | critical | 作品运行卡顿怎么排查；怎么打断点单步调试；变量值不对怎么查；作品有什么结构错误；速度想与帧率无关 | 调试、卡顿、断点、F3、数据面板、诊断、帧间隔、补帧、编译模式 | capabilities/run-debug.md |
| cap.gandi.blocks-authoring | 积木编程与脚本组织 | high | 怎么组织复杂的积木脚本；怎么做一个带参数的自制积木；多个角色怎么共用一个积木；变量作用域怎么选；怎么给积木写注释 | 积木页、自制积木、全局积木、作用域、模块、C形积木、注释 | capabilities/blocks-authoring.md |
| cap.gandi.project-files | 作品文件、版本回滚与数据保全 | high | 怎么打开保存 Gandi 作品；改坏了怎么找回之前版本；误删角色怎么还原；怎么备份迁移作品到另一台电脑；代码文件怎么管理 | 版本历史、还原、回收站、sb3、备份、代码文件、导出 | capabilities/project-files.md |
| cap.gandi.scenes-assets | 多场景架构与素材复用 | high | 怎么做一个多场景游戏；角色怎么跨场景常驻；场景之间怎么切换传参；怎么复用素材而不误改 | 多场景、跨场景角色、场景切换、广播、资源库、独立副本、模块 | capabilities/scenes-assets.md |
| cap.gandi.engine-scene | 引擎搭建：物理/光照/粒子/瓦片地图 | high | 怎么做有重力的平台跳跃；怎么给作品加光照；怎么制作粒子爆炸效果；怎么用瓦片地图做关卡 | 物理、光照、粒子、瓦片地图、装配编辑器、碰撞体、寻路 | capabilities/engine-tools.md |
| cap.gandi.extensions-collab | 扩展插件与多人协作 | medium | 怎么安装扩展或插件；怎么和别人同时编辑一个作品；协作里怎么控制权限；为什么运行位置没同步；断线了要重连还是重新进入 | 扩展、插件、多人协作、权限组、邀请、同步、撤销只撤自己、重新加载 | capabilities/extensions-collab.md |
| cap.gandi.layout-workspace | 界面布局、工作区与设置归属 | medium | 怎么摆好面板并保存布局；换电脑怎么迁移界面配置；某个设置是跟人还是跟作品；平板上怎么操作 | 布局、面板、浮窗、布局锁、设置、平板、触屏 | capabilities/layout-workspace.md |
| cap.gandi.code-navigation | 整理、查找与批量替换积木 | medium | 怎么快速找到某个积木；怎么批量替换积木上的值；怎么折叠整理一大堆脚本；怎么用一句话生成一串积木 | 全局搜索、查找替换、代码框、快捷添加、中键、Ctrl+F、Ctrl+H | capabilities/code-navigation.md |
| cap.gandi.media-creation | 造型、动画与声音素材创作 | medium | 怎么画造型做动画；怎么给录音降噪；怎么制作逐帧动画并导出视频；怎么用编曲台写曲 | 造型编辑器、补间、洋葱皮、逐帧动画、降噪、编曲台、钢琴卷帘、混音台 | capabilities/media-creation.md |
