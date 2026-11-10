# 智光计算 · Meow Optics

把微信小程序 **小黑喵智光计算** 搬进 Android 的版本：本地光学手册 + 公式计算器，外加一个能自己查手册、替你算参数、也能自己长大（加词条／加计算器）的 AI 助手。

- 开发者：小黑喵工作室
- 当前版本：**1.1**（versionCode 2）
- 包名：`com.xiaoheimiao.meowoptics`
- 安装包：见 [Releases](https://github.com/Alice-P197/meow-optics/releases/latest)

## 能做什么

**对话**
- 接自己的大模型：内置 DeepSeek、火山方舟、Kimi、智谱、通义、硅基流动、OpenRouter、OpenAI、Anthropic、Gemini、Ollama、自定义网关
- 一键拉取该服务商的最新模型列表（真实请求 `/models`，过滤掉 embedding／tts 这类非对话模型）
- 流式输出，思考过程单独成块可折叠，工具调用实时卡片，中途停止不会丢已展示的内容

**Key 安全**
- API Key 存进 AndroidKeyStore 的 AES-256-GCM 加密区，磁盘上只有密文
- 不经过前端、不进日志、不随备份导出，界面上只显示 `****后4位`

**光学**
- 对话驱动检索：模型回答光学问题前先查本地手册（BM25 + 中文 bigram），没查到会明说"这是模型知识，不是本地词条"
- 本地手册分类浏览、公式用 KaTeX 离线渲染、词条与计算器互跳
- 计算器按类别分组，参数带单位，出结果给中间量

**自扩展**
- 界面上不写死"多少个计算器／多少篇词条"，数量会变
- 在对话里讲清楚一个手册没有的概念，助手会问"要不要存进手册"，同意就写进去并立刻可检索
- 反复算同一类量，可以让它把公式做成计算器（白名单校验 + 入库前试算，算不出有限数值就不存）
- 设置页「自扩展」可逐条删除

**外观与系统**
- 称呼自己配置（首页问候、引导页、气泡头像首字都跟着变）
- 主题三档：深色 / 浅色 / 跟随系统（跟随系统会实时响应切换）
- 桌面悬浮猫、前台保活、通知／电池／自启动一键跳转
- 历史会话分组、改名、删除；长期记忆、日报记录

**应用内更新**
- 设置页「版本与更新」：填清单地址 → 检查 → 下载（带进度条）→ 拉起系统安装器
- 清单可直接用本仓库的 [update.json](https://alice-p197.github.io/meow-optics/update.json)，也可填 GitHub Release API
- Android 8 以后没有静默安装，首次需手动允许"安装未知应用"

## 安装

1. 下载 [最新安装包](https://github.com/Alice-P197/meow-optics/releases/latest/download/MeowOptics.apk)
2. 点开安装，系统提示"未知来源"时允许文件管理器安装
3. 首启进引导页：填一个服务商的 API Key → 按需开悬浮窗／通知／电池无限制／自启动（小米、红米、华为、荣耀、OPPO、vivo、魅族会跳到对应页面）

## 自更新地址

设置 →「版本与更新」→ 更新清单地址填：

```
https://alice-p197.github.io/meow-optics/update.json
```

每次发版：`versionCode` 加一 → 构建 → 传 Release（资产名保持 `MeowOptics.apk`）→ 改 update.json 的 `versionCode`／`versionName`／`notes`。资产名固定，下载链接就不用改。

## 构建

源码在开发机上（Gradle 8.7 + JDK 17 + Android SDK 34）：

```bash
# 前端核心打包 + 语料索引
node tools/bundle-core.mjs && node tools/build-corpus.cjs
# 出包
gradle :app:assembleRelease
```

产物：`app/build/outputs/apk/release/app-release.apk`

## 仓库说明

- 安装包只走 Releases，不进 git 历史（见 `.gitignore`）
- **签名库、口令、`local.properties`、任何 API Key 都不入这个仓库**；换机器构建时请自备签名库，否则无法覆盖升级（签名不一致只能卸载重装）
- 版权归小黑喵工作室，仓库公开用于分发与后续开发，未授予再分发许可