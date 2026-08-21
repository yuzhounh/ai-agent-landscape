<p align="center">
  <img src="assets/icon.svg" alt="AI Agent Landscape logo" width="128">
</p>

<h1 align="center">AI Agent Landscape</h1>

<p align="center"><strong>AI Agent 产品、运行形态、模型与用量方案的中文生态地图</strong></p>

<p align="center">
  <a href="https://github.com/yuzhounh/ai-agent-landscape/releases/tag/v0.2.0"><img src="https://img.shields.io/badge/version-v0.2.0-blue.svg" alt="Version v0.2.0" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="MIT License" /></a>
  <a href="#信息时效与声明"><img src="https://img.shields.io/badge/last_verified-2026--08--21-2ea44f.svg" alt="Last verified 2026-08-21" /></a>
</p>

AI Agent 已经不再只是聊天框或代码补全插件。一个完整的 Agent 产品，通常由模型、上下文工程、工具、执行环境、权限系统和交付界面共同组成，可以理解需求、拆解任务、调用工具、修改文件、运行代码，并在一定程度上持续工作直至交付结果。

本仓库面向中文读者整理 AI Agent 生态，覆盖 AI 编程、知识工作、桌面与浏览器操作、常驻个人 Agent，以及与其配套的 Coding Plan、Token Plan、API Router、基础模型和 Chat 产品。收录重点是公开可验证的产品形态，不以厂商规模、融资或宣传热度排序。

> [!IMPORTANT]
> 这是一张“地图”，不是排行榜。产品能力、价格、额度、地区可用性和名称都在快速变化；选型前请以链接中的官方页面为准。

## 目录

- [如何理解这张地图](#如何理解这张地图)
- [分层架构](#分层架构)
- [重点产品家族](#重点产品家族)
- [AI IDE / Agent IDE](#ai-ide--agent-ide)
- [CLI / Terminal Coding Agent](#cli--terminal-coding-agent)
- [Cloud / Background Coding Agent](#cloud--background-coding-agent)
- [GitHub / Repository-native Agent](#github--repository-native-agent)
- [通用 Work / Desktop Agent](#通用-work--desktop-agent)
- [Personal / Always-on Agent](#personal--always-on-agent)
- [Computer-Use / Browser-Use Agent](#computer-use--browser-use-agent)
- [Agent Framework / Workflow Platform](#agent-framework--workflow-platform)
- [Coding Plan / Token Plan](#coding-plan--token-plan)
- [API Router / 聚合平台](#api-router--聚合平台)
- [基础模型 / Chat 产品](#基础模型--chat-产品)
- [选型速查](#选型速查)
- [维护与贡献](#维护与贡献)
- [信息时效与声明](#信息时效与声明)

## 如何理解这张地图

### 分类标准

本项目使用四个互相独立的维度，而不是给产品贴一个永久标签：

| 维度                          | 主要问题                         | 常见取值                                                            |
| ----------------------------- | -------------------------------- | ------------------------------------------------------------------- |
| 交&#8288;互&#8288;入&#8288;口                      | 用户在哪里指挥 Agent？           | IDE、终端、网页、桌面应用、GitHub、聊天工具                         |
| 执&#8288;行&#8288;位&#8288;置                      | 任务在哪里运行？                 | 本机、隔离沙箱、云端 VM、CI / GitHub Actions、移动设备              |
| 工&#8288;作&#8288;对&#8288;象                      | Agent 主要操作什么？             | 代码仓库、网页、桌面 GUI、本地文件、文档、表格、演示稿、第三方 SaaS |
| 自&#8288;治&#8288;方&#8288;式                      | Agent 能持续工作多久、如何交付？ | 同步协作、后台异步、定时任务、常驻服务、PR / 文件 / 报告交付        |

### 几个常被混用的概念

- **Model（模型）** 负责理解和生成；
- **Harness（Agent 运行框架）** 负责准备上下文、循环调用模型与工具、处理权限并验证结果；
- **Surface（产品入口）** 是 IDE、CLI、网页、桌面应用、GitHub 或 IM；
- **Plan / API** 决定如何获得模型或产品的使用额度。

可以把它们类比成：模型是发动机，Harness 是整车与驾驶系统，IDE / CLI / Desktop 是驾驶舱，Plan 或 API 则是获得燃料和道路服务的方式。购买某个模型套餐，不等于同时获得任意 Agent 产品；安装一个多模型 Harness，也不等于自动拥有模型额度。

### 为什么产品会跨类

同一产品可能有多个 Surface，同一厂商也可能同时提供模型、Harness、桌面产品和云端服务。例如 Claude Code 同时存在于终端、IDE、桌面应用、网页云任务和 GitHub 工作流中；Kiro 同时有 IDE、CLI 和 Web；Qwen Code 已同时覆盖 CLI、桌面和守护进程模式。

因此：

- 表格中的“主要归类”只表示最典型的使用方式；
- 同一产品可以出现在多个表格中；
- Computer Use 是能力，不一定是独立产品类别；
- Work Agent 可以调用 Browser / Computer Use，Coding Agent 也可以扩展成通用工作 Agent；
- “支持某模型”不等于该工具由模型厂商开发或获得官方背书。

### 状态与证据口径

- **公开服务**：官方已提供公开产品页、下载、注册或文档；
- **Preview / Beta**：官方已发布，但能力、接口、定价或兼容性仍可能发生破坏性变化；
- **开源**：存在官方或项目维护方公开仓库；不代表同时提供托管服务；
- **研究 / 相邻类别**：与 Agent 生态密切相关，但不应与成熟的终端、桌面或云端产品等同。

## 分层架构

~~~mermaid
flowchart TB
    U["用户与团队"] --> S["产品入口 / Surface"]
    S --> H["Agent Harness / 编排层"]
    H --> T["工具与连接层"]
    H --> R["运行环境"]
    H --> M["基础模型"]
    P["订阅 · Coding Plan · Token Plan · 按量 API"] --> S
    P --> M

    S --- S1["IDE · CLI · Web · Desktop · GitHub · IM"]
    H --- H1["规划 · 上下文 · 记忆 · 多 Agent · 验证 · 权限"]
    T --- T1["文件 · Shell · Git · Browser · GUI · MCP · SaaS"]
    R --- R1["本机 · 沙箱 · 云 VM · CI · 常驻主机"]
    M --- M1["GPT · Claude · Gemini · Grok · Qwen · DeepSeek · GLM · Kimi 等"]
~~~

典型调用链可以是：

~~~text
用户
  → IDE / CLI / Desktop / Web / GitHub
  → Agent Harness
  → 文件、Shell、Git、浏览器、MCP、SaaS
  → 本机或云端沙箱
  → 基础模型
  → PR、代码、文档、表格、PPT 或已完成的操作
~~~

## 重点产品家族

这张表用于理解“同一品牌为什么会在多个分类里重复出现”。

| 生态 / 厂商       | 模型与 API                        | 编程入口                                      | 通用工作 / 个人入口                          | 云端或其他形态                     |
| ----------------- | --------------------------------- | --------------------------------------------- | -------------------------------------------- | ---------------------------------- |
| OpenAI            | GPT、OpenAI API                   | Codex CLI、IDE 扩展、Codex Desktop            | ChatGPT、ChatGPT agent                       | Codex cloud、GitHub Action         |
| Anthropic         | Claude、Claude API                | Claude Code CLI、IDE、Desktop                 | Claude、Claude Cowork、Computer Use          | Claude Code on the web、GitHub     |
| Google            | Gemini、Gemini API                | Antigravity、Gemini CLI、Jules                | Gemini                                       | Kiro 由 AWS 提供，不属 Google      |
| AWS               | Bedrock                           | Kiro IDE、Kiro CLI                            | —                                            | Kiro Web / autonomous agent        |
| xAI               | Grok、xAI API                     | Grok Build                                    | Grok                                         | Build 无头 / 自动化形态            |
| Meta              | Llama、Muse                       | Muse Code                                     | Meta AI                                      | 开源权重与开发者生态               |
| 阿里 / Qoder      | 可接入多模型                      | Qoder IDE、Qoder CLI                          | QoderWork、QoderWake                         | Cloud Agents、Mobile               |
| 字节跳动          | 豆包 / Seed、火山方舟             | TRAE IDE、SOLO                                | TRAE Work                                    | Work Web / Mobile、云端任务        |
| 腾讯              | 混元、腾讯云模型服务              | CodeBuddy IDE、CodeBuddy Code                 | WorkBuddy、QClaw、Marvis                     | Token Plan、TokenHub               |
| 智谱              | GLM、BigModel API、Coding Plan    | ZCode                                         | AutoGLM、AutoClaw                            | AutoGLM-OpenClaw 云机              |
| 月之暗面          | Kimi、Moonshot API、Kimi Code API | Kimi Code CLI、VS Code                        | Kimi、Kimi Work、WebBridge                   | 在线 Agent 与会员额度              |
| 阿里 / Qwen       | Qwen、百炼 Model Studio           | Qwen Code、Lingma                             | QwenPaw、Qwen Chat                           | 百炼 Coding Plan、ModelScope       |
| DeepSeek          | DeepSeek 模型与 API               | DeepSeek Harness                              | DeepSeek Chat                                | Harness 当前为开发者预览           |
| MiniMax           | MiniMax 模型与 API                | MiniMax Code                                  | MiniMax 产品入口                             | Token Plan                         |

厂商归属、投资关系和产品运营主体可能发生变化。本表只描述核验时公开可见的产品生态关系，不用于判断法律实体之间的控制关系。

## AI IDE / Agent IDE

这类产品以编辑器或 IDE 扩展为主入口，通常整合代码库索引、补全、对话、文件编辑、终端、调试和 Agent 模式。

| 产品                                                       | 团队 / 地区      | 代表能力                                           | 其他形态                           |
| ---------------------------------------------------------- | ---------------- | -------------------------------------------------- | ---------------------------------- |
| [Cursor](https://www.cursor.com/)                          | Anysphere / 美国 | AI 原生编辑器、代码库理解、Agent                   | Background Agents、CLI、Web/Mobile |
| [Windsurf](https://windsurf.com/)                          | Windsurf / 美国  | Agentic IDE、编辑器内多步开发                      | 插件、企业能力                     |
| [Kiro](https://kiro.dev/)                                  | AWS / 美国       | 规格驱动开发、Agent hooks、steering                | CLI、Web、autonomous agent         |
| [Antigravity](https://antigravity.google/)                 | Google / 美国    | Agent-first 开发平台、多 Agent、浏览器与终端       | CLI、API Agent                     |
| [GitHub Copilot](https://github.com/features/copilot)      | GitHub / 美国    | IDE Agent、Plan、补全、多模型与 GitHub 上下文      | CLI、Coding Agent、Code Review     |
| [Zed Agent Panel](https://zed.dev/docs/ai/agents)          | Zed / 美国       | 原生 Agent、ACP 外部 Agent、终端 Agent 三种路径    | 可接 Claude Code、Codex、OpenCode  |
| [JetBrains Junie](https://www.jetbrains.com/junie/)        | JetBrains        | IDE 内规划、编辑、运行测试与终端命令               | CLI / terminal                     |
| [Qoder IDE](https://qoder.com/)                            | Qoder / 中国     | 自主开发桌面、代码库理解、任务委派                 | CLI、Cloud Agents、Work、Wake      |
| [TRAE IDE](https://www.trae.ai/)                           | 字节跳动 / 中国  | IDE 与 SOLO 协同、端到端软件构建                   | TRAE Work、SOLO Web/Mobile         |
| [CodeBuddy IDE](https://www.codebuddy.ai/)                 | 腾讯 / 中国      | 需求、设计、编码、预览到部署；Craft / Plan 模式    | CLI、WorkBuddy                     |
| [ZCode](https://zcode.z.ai/)                               | 智谱 / 中国      | 面向 GLM 的 Agent IDE、Goal 长任务                 | GLM Coding Plan                    |
| [Comate](https://comate.baidu.com/)                        | 百度 / 中国      | AI IDE、Zulu 编程智能体                            | VS Code / JetBrains 插件           |
| [Lingma](https://lingma.aliyun.com/)                       | 阿里云 / 中国    | IDE、插件、企业代码助手与 Agent 能力               | VS Code / JetBrains                |
| [Cline](https://docs.cline.bot/cline-overview)             | 开源社区         | 编辑器 Agent，可读写文件、运行命令和操作浏览器     | CLI、JetBrains、ACP                |
| [Kilo Code](https://kilo.ai/)                              | Kilo / 开源      | 多模型 IDE Agent、模式与团队工作流                 | CLI、Cloud                         |
| [Roo Code](https://roocode.com/)                           | 开源社区         | VS Code 多模式 Agent、模型与工具可配置             | Cloud / 企业能力                   |

独立 IDE、IDE 扩展和通过 ACP 接入编辑器的外部 Agent 并不是同一种交付方式。评估时应分别检查编辑器兼容性、代码索引位置、扩展权限和 Agent 实际执行环境。

## CLI / Terminal Coding Agent

终端 Agent 直接工作在仓库和工具链旁，适合开发者、服务器环境、自动化脚本和可组合工作流。它们大致可分为“模型厂商主导”与“多模型 / 模型无关”两类。

| 产品                                                                                 | 开发者 / 生态     | 模型关系             | 定位与备注                                                       |
| ------------------------------------------------------------------------------------ | ----------------- | -------------------- | ---------------------------------------------------------------- |
| [Codex CLI](https://developers.openai.com/codex/cli/)                                | OpenAI            | OpenAI 主导          | 开源终端编程 Agent，可读写文件、运行命令并连接 Codex 生态        |
| [Claude Code](https://code.claude.com/docs/en/overview)                              | Anthropic         | Claude 主导          | 终端优先，支持 hooks、skills、MCP、subagents 与多种执行入口      |
| [Gemini CLI](https://github.com/google-gemini/gemini-cli)                            | Google            | Gemini 主导          | 开源终端 Agent，与 Gemini 和 Google 开发生态结合                 |
| [Antigravity](https://antigravity.google/)                                           | Google            | Gemini 生态          | Agent-first 开发产品的终端 / 自动化入口                          |
| [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness)                  | DeepSeek          | DeepSeek 主导        | 官方开源 Agent Harness；开发者预览，插件化、可替换执行组件       |
| [Grok Build](https://docs.x.ai/build/overview)                                       | xAI               | Grok 主导            | 可交互或无头运行的开源 Coding Agent / TUI，支持 ACP              |
| [Muse Code](https://research.meta.ai/blog/introducing-muse-code-and-muse-spark-1-2/) | Meta              | Muse 主导            | 面向 Muse Spark 的终端编程 Agent                                 |
| [Qwen Code](https://qwenlm.github.io/qwen-code-docs/)                                | Qwen / 阿里       | 多协议，Qwen 优化    | 开源 CLI；支持多模型、MCP、subagents、agent teams 与 daemon      |
| [Kimi Code](https://www.kimi.com/code/docs/en/)                                      | 月之暗面          | Kimi 主导            | CLI 与 VS Code；读写代码、运行命令、联网搜索，可接会员 API Key   |
| [Kiro CLI](https://kiro.dev/docs/cli/quick-start/)                                   | AWS               | Kiro 服务            | 终端 Agent、custom agents、steering、MCP 与 subagents            |
| [Qoder CLI](https://docs.qoder.com/cli/quick-start)                                  | Qoder             | 多模型               | 终端编程伙伴与可扩展 Agent 引擎                                  |
| [CodeBuddy Code](https://www.codebuddy.ai/docs/cli/)                                 | 腾讯              | 多模型 / 自有服务    | CLI、Desktop、IDE、ACP、MCP、无头模式与 Dynamic Workflows        |
| [MUSACode](https://docs.mthreads.com/playbook/playbook-doc-online/musacode/)         | 摩尔线程          | 自有与兼容模型       | 通用开发与 MUSA 算子工作流                                       |
| [OpenCode](https://opencode.ai/docs/)                                                | 开源社区          | 模型无关             | 开源终端 / Desktop / IDE Agent，支持多家模型提供方               |
| [Cline CLI](https://docs.cline.bot/)                                                 | 开源社区          | 模型无关             | Cline 的终端入口，与编辑器和任务管理形态衔接                     |
| [Kilo CLI](https://kilo.ai/cli)                                                      | Kilo / 开源       | 模型无关             | 开源终端 Agent，可与 IDE 和 Kilo Cloud 组合                      |
| [Aider](https://aider.chat/docs/)                                                    | 开源社区          | 模型无关             | 经典终端 AI Pair Programming 工具，Git 工作流成熟                |
| [Goose](https://github.com/aaif-goose/goose)                                         | AAIF / 开源       | 模型无关             | 本地通用 Agent，提供 CLI、Desktop、API 与 MCP 扩展               |
| [OpenHands CLI / SDK](https://docs.openhands.dev/sdk/index)                          | OpenHands / 开源  | 模型无关             | 可本地、服务器或云端运行的软件工程 Agent Harness                 |
| [Junie](https://www.jetbrains.com/junie/)                                            | JetBrains         | 服务内模型           | 除 IDE 外提供交互式终端入口                                      |

多模型不等于完全可替换。不同模型在工具调用格式、上下文缓存、推理参数、视觉输入和长任务稳定性方面存在差异；Harness 也可能只对部分模型做过完整适配。

## Cloud / Background Coding Agent

这类 Agent 在远程沙箱、云 VM 或托管执行环境中异步工作。用户可以关闭页面或继续做其他事，稍后审查 diff、提交或 PR。

| 产品                                                                                                              | 典型执行方式                              | 主要交付物                         |
| ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------- | ---------------------------------- |
| [OpenAI Codex cloud](https://developers.openai.com/codex/cloud/)                                                  | OpenAI 托管云环境，可从多入口委派任务     | 代码变更、检查结果、PR             |
| [Claude Code on the web](https://code.claude.com/docs/en/web-quickstart)                                          | Anthropic 托管隔离 VM，可并行后台执行     | 分支、diff、PR、可继续会话         |
| [Cursor Background Agents](https://docs.cursor.com/background-agents)                                             | 云端隔离环境异步工作                      | 分支、diff、PR                     |
| [Kiro Web](https://kiro.dev/docs/web/)                                                                            | 隔离云沙箱；协作、Spec 与 autonomous 模式 | 分支、PR、自动化任务               |
| [GitHub Copilot coding agent](https://docs.github.com/en/copilot/concepts/agents/coding-agent/about-coding-agent) | GitHub Actions 驱动的异步 Agent           | Pull request                       |
| [Devin](https://devin.ai/)                                                                                        | 云端软件工程 Agent                        | 实现、测试、PR、任务记录           |
| [Jules](https://jules.google/)                                                                                    | 克隆仓库到 Google 云 VM，计划并验证       | 分支、diff、PR                     |
| [OpenHands Cloud](https://www.openhands.dev/)                                                                     | 托管沙箱或自建运行时                      | 代码变更、PR、批量工程任务         |
| [Kilo Cloud](https://kilo.ai/)                                                                                    | 与 Kilo IDE / CLI 配套的云端执行          | 后台代码任务与 PR                  |
| [Qoder Cloud Agents](https://qoder.com/)                                                                          | Qoder 平台中的云端 Agent                  | 后台开发任务与可审查结果           |
| [TRAE Work / SOLO Web](https://www.trae.ai/)                                                                      | 云端工作区、多任务并行                    | 代码、应用、文档和结构化成果       |

云端 Agent 的关键差异通常不在聊天界面，而在沙箱初始化、依赖缓存、网络策略、凭据代理、任务并发、日志可审计性、PR 反馈闭环和计费方式。

## GitHub / Repository-native Agent

Repository-native Agent 以 Issue、Pull Request、Review、Actions 或仓库事件为一等任务对象，天然适合异步委派和团队审查。

| 产品                                                                  | 原生入口                                            | 工作闭环                                        |
| --------------------------------------------------------------------- | --------------------------------------------------- | ----------------------------------------------- |
| [GitHub Copilot coding agent](https://github.com/features/ai)         | GitHub Issue、Agents、VS Code                       | Issue → 分支 → Actions → PR → Review            |
| [OpenAI Codex](https://developers.openai.com/codex/)                  | GitHub 连接、云任务、GitHub Action                  | 仓库任务 → 沙箱执行 → Review / PR               |
| [Claude Code](https://code.claude.com/docs/en/platforms)              | GitHub App、Web、Actions                            | Issue / 仓库任务 → 云环境或 Action → PR         |
| [Kiro Web](https://kiro.dev/docs/web/)                                | GitHub / GitLab 仓库、Issue、Web                    | 任务 → 云沙箱 → 分支 → PR / MR                  |
| [Jules](https://jules.google/)                                        | GitHub 仓库、Issue 标签、API                        | 仓库 / Issue → 云 VM → PR                       |
| [Devin](https://devin.ai/)                                            | GitHub 与工单集成                                   | 任务 → 实现与测试 → PR                          |
| [OpenHands](https://www.openhands.dev/)                               | GitHub、平台任务、SDK                               | 任务 → 沙箱或自托管执行 → PR                    |
| [Cursor Background Agents](https://docs.cursor.com/background-agents) | 编辑器、Web / Mobile 与仓库                         | 后台任务 → 分支 → PR                            |
| [Origin](https://cursor.com/cn/changelog/origin-code-hosting)         | Cursor 代码托管、PR 与 GitHub 双向同步（早期 Beta） | 仓库 / PR → Agent 问答、修改与推送 → Review     |
| [CodeRabbit](https://docs.coderabbit.ai/)                             | GitHub、GitLab、Bitbucket、Azure DevOps             | PR Review → 建议 / 修复 → Agent 交接            |
| [Greptile](https://www.greptile.com/docs/introduction)                | GitHub / GitLab App                                 | 全仓索引 → PR Review → 一键交给 Coding Agent    |
| [Qodo Merge / PR-Agent](https://www.qodo.ai/products/qodo-merge/)     | PR、Review、Git 平台                                | PR 分析、摘要、审查、建议与合并辅助             |
| [Sweep](https://github.com/sweepai/sweep)                             | GitHub Issue / PR                                   | Issue → 代码修改 → PR；开源项目形态需按版本核验 |

CodeRabbit、Greptile 和 Qodo 的主定位更接近审查、验证或 PR 编排，而不是独立完成所有开发工作。它们与 Codex、Claude Code、Cursor、Devin 等实现型 Agent 可以互补。

“在 IDE 里知道当前 Git 仓库”并不自动等于 Repository-native；本分类强调 Agent 是否把 Issue、PR、Review、CI 和仓库权限当作一等工作对象。

## 通用 Work / Desktop Agent

Work Agent 的核心不是“什么都能聊”，而是能够处理文件、网页、数据和办公成果，并以文档、表格、演示稿、网页、应用或已完成操作交付。

### 国内代表产品

| 产品                                                                                       | 团队           | 本地与执行特点                                                   | 典型成果                                  |
| ------------------------------------------------------------------------------------------ | -------------- | ---------------------------------------------------------------- | ----------------------------------------- |
| [WorkBuddy](https://cloud.tencent.cn/product/workbuddy)                                    | 腾讯           | 全场景 AI 工作台；办公、代码与设计，本地文件和工具执行           | 文档、数据分析、周报、应用与设计成果      |
| [QoderWork](https://docs.qoder.com/zh/qoderwork/introduction)                              | Qoder          | 本地桌面助手；文件、浏览器、桌面控制、定时任务和 IM              | 文档、表格、PPT、数据和网页流程           |
| [TRAE Work](https://www.trae.ai/)                                                          | 字节跳动       | Desktop / Web / Mobile；Work、Code、Design 等工作入口            | 研究、文档、数据分析、PPT、代码与应用     |
| [Kimi Work](https://www.kimi.com/zh-cn/products/kimi-work)                                 | 月之暗面       | 本地文件、WebBridge、代码执行、Agent 集群与 Cron                 | 报告、表格、PPT、代码和网页任务           |
| [CodeBuddy](https://www.codebuddy.ai/)                                                     | 腾讯           | 从编程入口扩展到研究、文档和多步骤任务                           | 研究、报告、数据与代码                    |
| [AutoClaw](https://autoclaw.zhipuai.cn/)                                                   | 智谱           | 本地桌面应用、Skills、IM、浏览器和办公自动化                     | 文档、数据、网页流程和长任务              |
| [QClaw](https://www.tencent.com/zh-cn/articles/2202318.html)                               | 腾讯           | 基于 OpenClaw，本地运行，连接微信 / WhatsApp / Telegram 等渠道   | 生活与办公自动化、远程电脑任务            |
| [Marvis](https://marvis.qq.com/)                                                           | 腾讯           | 操作系统层级个人助手，面向本地文件、系统与应用                   | 设备管理、文件处理、跨端协作              |
| [Coze](https://www.coze.cn/)                                                               | 字节跳动       | 在线 Agent、工作流、知识库、插件与内容 / 应用创建                | Bot、工作流、网页、内容与办公成果         |

### 海外与全球代表产品

| 产品                                                                                               | 团队          | 执行特点                                                       | 典型成果                                  |
| -------------------------------------------------------------------------------------------------- | ------------- | -------------------------------------------------------------- | ----------------------------------------- |
| [Claude Cowork](https://claude.com/product/cowork)                                                 | Anthropic     | 桌面工作区、受控本地文件、连接器与多步骤知识工作               | 文档、数据、跨应用成果                    |
| [ChatGPT agent](https://openai.com/index/introducing-chatgpt-agent/)                               | OpenAI        | 云端虚拟计算机、浏览器、代码与连接器                           | 研究、表格、演示稿和网页操作              |
| [Manus](https://manus.im/)                                                                         | Manus         | 云端通用 Agent，并提供 Desktop、My Computer 与 Browser         | 研究、网站、数据与多格式成果              |
| [Perplexity Computer](https://www.perplexity.ai/help-center/en/articles/13837784-what-is-computer) | Perplexity    | 云端独立数字工作者、连接器、持久记忆、调度与后台执行           | 研究、应用、邮件、PPT 与跨 SaaS 流程      |
| [Genspark](https://www.genspark.ai/)                                                               | Genspark      | Super Agent、Custom Agent 与一体化 AI Workspace                | Slides、Docs、Sheets、设计、代码与自动化  |

### 直接竞品与相邻产品的边界

- WorkBuddy、QoderWork、TRAE Work、Kimi Work 的共同点，是将 Coding Agent 中的文件、Shell、浏览器、Skills 和长任务能力迁移到普通知识工作；
- AutoClaw、QClaw、QwenPaw、OpenClaw 更强调个人部署、消息渠道、持续记忆和常驻；
- Coze、Dify 一类平台更强调“创建 Agent / Workflow”，不等同于开箱即用的本地桌面员工；
- Manus、ChatGPT agent、Perplexity Computer、Genspark 更偏云端通用执行，是否能操作本机文件或应用要看其桌面桥接方式和授权范围。

## Personal / Always-on Agent

常驻 Agent 强调持续可达、定时或事件触发、长期状态，以及从聊天工具或移动端远程下达任务。它与一次性桌面 Agent 的边界正在快速融合。

| 产品                                                                                                       | 常驻方式                                                       | 适合场景                                      |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | --------------------------------------------- |
| [OpenClaw](https://openclaw.ai/)                                                                           | 自托管 Gateway、消息渠道、Skills、定时与多 Agent 路由          | 私有化、可扩展的个人自动化                    |
| [QwenPaw](https://github.com/agentscope-ai/QwenPaw)                                                        | 本地或云端部署、多渠道、多 Agent、记忆、Skills 与定时          | 开源个人助手、文档和消息自动化                |
| [Hermes Agent](https://hermes-agent.nousresearch.com/docs/)                                                | 自托管、持久记忆、学习循环、消息渠道与 Desktop / CLI           | 长期个人上下文、自改进技能与服务器常驻        |
| [AutoClaw](https://autoclaw.zhipuai.cn/)                                                                   | 一键本地部署、IM、Skills、浏览器与办公自动化                   | 降低个人 Agent 部署门槛                       |
| [AutoGLM-OpenClaw](https://docs.bigmodel.cn/cn/coding-plan/benefits/autoglm-openclaw)                      | 云端个人电脑、24 小时运行、飞书入口                            | 云端简报、提醒、浏览器自动化和跨设备任务      |
| [QClaw](https://www.tencent.com/zh-cn/articles/2202318.html)                                               | 本地运行、移动端消息遥控、安全网关                             | 生活、办公、创作与远程电脑任务                |
| [QoderWake](https://qoder.com/en/blog/qoderwake)                                                           | 面向 7×24 工作的桌面 / 服务器 Agent                            | 持续目标、远程管理与数字员工                  |
| [Kimi Work](https://www.kimi.com/zh-cn/products/kimi-work)                                                 | Cron、Agent 集群、本地后台执行                                 | 定时报表、长周期文件与研究任务                |
| [WorkBuddy](https://cloud.tencent.cn/product/workbuddy)                                                    | 工作台、Skills、企业连接与任务执行                             | 团队办公自动化和可复用工作流                  |
| [Manus My Computer](https://help.manus.im/en/articles/14178443-what-is-the-my-computer-feature-capable-of) | Desktop 与本地 CLI 执行，可从其他设备委派                      | 本地文件、应用开发、远程工作流                |
| [Perplexity Computer](https://www.perplexity.ai/help-center/en/articles/13837784-what-is-computer)         | 云端后台任务、条件触发、定时与连接器                           | 邮件、日历、研究和持续监控                    |
| [Marvis](https://marvis.qq.com/)                                                                           | 操作系统与跨设备入口                                           | 本地设备和个人工作助手                        |

是否“永远在线”取决于设备电源、后台权限、云服务状态、套餐限额和具体版本，不能只根据营销名称判断。常驻 Agent 的权限通常比一次性聊天更高，应使用专门账号、独立工作目录、最小化密钥权限和可审计日志。

## Computer-Use / Browser-Use Agent

Browser Use 通常通过 DOM、无障碍树、截图或浏览器扩展操作网页；Computer Use 进一步覆盖桌面 GUI。它们既可以是模型工具，也可以是独立 Harness 或 Work Agent 的一个能力模块。

| 产品 / 能力                                                                                           | 主要环境                       | 能力边界                                                      |
| ----------------------------------------------------------------------------------------------------- | ------------------------------ | ------------------------------------------------------------- |
| [AutoGLM](https://autoglm.z.ai/)                                                                      | 手机、云手机与设备 Agent       | 视觉理解、点击、滑动、输入和跨 App 任务                       |
| [UI-TARS](https://github.com/bytedance/UI-TARS)                                                       | 桌面与网页 GUI                 | 字节开源 GUI Agent 模型 / 项目，并提供 UI-TARS Desktop        |
| [QoderWork](https://docs.qoder.com/zh/qoderwork/introduction)                                         | 浏览器与桌面应用               | 网页导航、填表、数据提取及桌面点击、输入、滚动                |
| [Kimi WebBridge](https://www.kimi.com/zh-cn/products/kimi-work)                                       | 浏览器                         | 多标签页浏览、点击、滚动、提取和表单任务                      |
| [WorkBuddy](https://cloud.tencent.cn/product/workbuddy)                                               | 本地工作台与浏览器             | 文件、网页和办公流程执行                                      |
| [TRAE Work](https://www.trae.ai/)                                                                     | Web 与工作区                   | 研究、网页任务和跨工具执行                                    |
| [ChatGPT agent](https://openai.com/index/introducing-chatgpt-agent/)                                  | 云端虚拟计算机                 | 浏览器操作、研究、代码和连接器；高影响操作需要确认            |
| [Claude Computer Use](https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/computer-use-tool) | 浏览器 / 桌面执行环境          | 模型输出鼠标键盘动作，客户端负责实际执行与安全控制            |
| [Claude Code in Chrome](https://code.claude.com/docs/en/chrome)                                       | Chrome                         | 测试 Web 应用、调试、填表和提取页面数据                       |
| [Gemini Computer Use](https://ai.google.dev/gemini-api/docs/computer-use)                             | 浏览器、移动与桌面             | 模型生成 GUI 动作，开发者实现客户端执行环境                   |
| [Browser Use](https://docs.browser-use.com/)                                                          | Chromium / 云浏览器            | 开源浏览器 Agent Harness 与托管浏览器任务                     |
| [Perplexity Computer](https://www.perplexity.ai/help-center/en/articles/13837784-what-is-computer)    | 云端沙箱与 SaaS 连接器         | 搜索、工具、连接器、后台与定时执行                            |
| [Manus My Computer / My Browser](https://manus.im/)                                                   | 本机 CLI、浏览器与云端 Agent   | 本地文件、命令、应用与浏览器桥接                              |
| [Antigravity](https://antigravity.google/)                                                            | 开发工作区与浏览器             | 以开发和测试任务为中心的浏览器操作                            |

### 安全基线

- 限定 Agent 可访问的文件夹和网站；
- 使用专门账号与低权限 API Key；
- 转账、购买、发送消息、删除、发布和部署等操作保留人工确认；
- 将网页内容视为不可信输入，防范提示注入；
- 对下载文件、第三方 Skills、MCP Server 和浏览器扩展做来源审查；
- 保留操作日志，并为重要数据建立可恢复备份。

## Agent Framework / Workflow Platform

这一类面向开发者或团队创建自己的 Agent、工作流和产品。它们通常不是现成的“AI 同事”，但构成 Agent 生态的重要编排层。

| 项目 / 平台                                                         | 形态                    | 主要用途                                                    |
| ------------------------------------------------------------------- | ----------------------- | ----------------------------------------------------------- |
| [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) | 开源 Harness / Preview  | 插件化 Agent 运行时、轨迹、模式与二次开发                   |
| [OpenHands SDK](https://docs.openhands.dev/sdk/index)               | 开源 SDK / Runtime      | 构建能读写代码、运行 Shell、浏览网页的软件 Agent            |
| [Qwen-Agent](https://github.com/QwenLM/Qwen-Agent)                  | 开源框架                | Function Calling、MCP、代码解释器、RAG 与 Browser Assistant |
| [AgentScope](https://github.com/agentscope-ai/agentscope)           | 开源多 Agent 框架       | Agent 应用、多 Agent 编排与运行时                           |
| [LangGraph](https://langchain-ai.github.io/langgraph/)              | 开源工作流 / Runtime    | 有状态、可恢复、可人工介入的 Agent 图工作流                 |
| [Microsoft AutoGen](https://microsoft.github.io/autogen/)           | 开源多 Agent 框架       | Agent、工具和多 Agent 对话 / 编排                           |
| [CrewAI](https://www.crewai.com/open-source)                        | 开源框架与平台          | 角色化 Agent 团队与流程自动化                               |
| [Dify](https://dify.ai/)                                            | 开源应用平台            | 可视化工作流、知识库、模型接入、Agent 与应用发布            |
| [Coze](https://www.coze.cn/)                                        | 托管平台                | Bot、Workflow、插件、知识库和多模态应用                     |
| [n8n](https://n8n.io/)                                              | 工作流自动化平台        | 将 LLM / Agent 节点与 SaaS、数据库和企业流程连接            |

如果目标是“直接完成个人工作”，优先看 Work / Personal Agent；如果目标是“开发和运营自己的 Agent”，再重点比较本节的平台、SDK、部署和可观测性。

## Coding Plan / Token Plan

### 先区分五种付费方式

| 类型               | 买到的是什么                                            | 常见限制                                   | 例子                                              |
| ------------------ | ------------------------------------------------------- | ------------------------------------------ | ------------------------------------------------- |
| 产品席位订阅       | 某个 App / IDE / Agent 的使用权                         | 请求数、Agent 次数、并发和高级模型         | ChatGPT、Claude、Cursor、Windsurf、GitHub Copilot |
| 会员内 Coding 权益 | Chat 会员附带的官方 Coding Agent / Key                  | 共享会员额度、指定客户端、滚动窗口         | Claude Code、Kimi Code                            |
| Coding Plan        | 指定编程工具可用的固定月费模型额度                      | 工具白名单、滚动窗口、模型白名单、公平使用 | GLM Coding Plan、百炼 Coding Plan                 |
| Token Plan         | 面向 Coding、OpenClaw 等 Agent 的打包 Token / Credit    | 专用 Key、场景限制、调度优先级             | 腾讯云 Token Plan、MiniMax Token Plan             |
| 按量 API           | 按实际输入、输出、缓存和工具用量计费                    | 余额、速率、区域和模型可用性               | OpenAI API、Anthropic API、DeepSeek API           |

> [!WARNING]
> 产品会员通常不等于通用 API 额度；Coding Plan 的 Key 也通常不能用于自建后端、批量任务或任意 API 调用。接入前必须核对允许的客户端、端点、模型白名单、上下文上限、数据条款和公平使用规则。

### 模型厂商代表方案

| 方案                                 | 提供方      | 类型与特点                                                                  | 官方信息                                                                 |
| ------------------------------------ | ----------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| GLM Coding Plan                      | 智谱        | 官方 Coding Agent 订阅，使用 GLM 系列；新 Token Plan 支持 GLM-5.3，无需抢购 | [快速开始](https://docs.bigmodel.cn/cn/coding-plan/quick-start)          |
| 百炼 Coding Plan                     | 阿里云      | 多模型、专用 Key 与 Endpoint；Coding Plan 限量放量，Token Plan 开放购买     | [官方文档](https://help.aliyun.com/zh/model-studio/coding-plan)          |
| 腾讯云 Token Plan                    | 腾讯云      | Coding Plan 已下线，仅 Token Plan；混元与 GLM、Kimi、MiniMax 接入           | [产品页](https://cloud.tencent.cn/act/pro/tokenplan)                     |
| 火山方舟 Coding Plan / Agent Plan    | 火山引擎    | 已解除限购，开放购买；模型池覆盖 GLM-5.3、DeepSeek-V4、Kimi-K3 等           | [官方文档](https://www.volcengine.com/docs/82379/2165245)                |
| 百度千帆 Coding Plan / Token Plan    | 百度智能云  | Coding Plan 已下线；Token Plan 个人版上线，接入 GLM、DeepSeek、Kimi 等      | [千帆平台](https://cloud.baidu.com/product/codingplan.html)              |
| Kimi Code                            | 月之暗面    | CLI 与 VS Code，可接会员 API Key；Kimi-K3 发布后会员暂停购买                | [官方文档](https://www.kimi.com/code/docs/en/)                           |
| MiniMax Token Plan                   | MiniMax     | Plus / Max / Ultra 三档公开，不限购，全模态额度共享；MiniMax-M3 多模态      | [订阅页](https://platform.minimax.io/subscribe/coding-plan)              |
| 小米 MiMo Token Plan                 | 小米        | Lite / Standard / Pro / Max 四档，无 5 小时硬限                             | [小米 MiMo](https://mimo.xiaomi.com/)                                    |
| Qwen / QwenCloud 相关 Plan           | Qwen / 阿里 | Qwen 生态的 Coding / Token 类订阅；名称与套餐随地区和阶段变化               | [Qwen Code](https://qwenlm.github.io/qwen-code-docs/)                    |
| DeepSeek API                         | DeepSeek    | 按量 API；V4-Pro、V4-Flash 正式版上线，可配官方 Harness                     | [API 文档](https://api-docs.deepseek.com/)                               |
| OpenAI 官方 API                      | OpenAI      | 通用按量 API，与产品席位和 Chat 会员分开                                    | [OpenAI API](https://developers.openai.com/api/)                         |
| Anthropic 官方 API                   | Anthropic   | 通用按量 API，与产品席位和 Chat 会员分开                                    | [Claude API](https://docs.anthropic.com/)                                |
| xAI 官方 API                         | xAI         | 通用按量 API，与产品席位和 Chat 会员分开                                    | [xAI API](https://docs.x.ai/)                                            |
| Codex 会员额度                       | OpenAI      | ChatGPT 订阅附带 Coding Agent 额度；五小时窗口取消，仅周限额；需外币支付    | [定价页](https://openai.com/chatgpt/pricing/)                            |
| Claude Code 会员额度                 | Anthropic   | Pro / Max 订阅附带 Coding Agent 额度，滚动窗口；需境外支付与网络            | [定价页](https://www.anthropic.com/pricing)                              |
| OpenCode Zen / OpenCode Go           | OpenCode    | 精选模型网关与订阅套餐，Go 档聚合 Kimi-K3、GLM-5.3 等最新模型               | [Zen 文档](https://opencode.ai/docs/zen/)                                |
| Ollama Cloud Plan                    | Ollama      | 云端开源模型订阅，按云资源用量计量；即将支持 Kimi-K3；需外币支付            | [Ollama Cloud](https://ollama.com/cloud)                                 |

### 兼容性不是只有“能填 Base URL”

选择 Plan 时至少核对：

1. 是否明确允许目标工具，例如 Claude Code、Codex、OpenCode、Cline、Qwen Code、OpenClaw；
2. 使用 OpenAI、Anthropic、Gemini 还是厂商私有协议；
3. Key 是否只能在交互式编程工具中使用；
4. 模型白名单、上下文、视觉、缓存和工具调用是否完整；
5. 限额按 Token、请求、Credit、五小时窗口、周或月如何计算；
6. 是否允许并发 Agent、后台任务和自动化；
7. 输入输出是否可能用于服务改进；
8. 超额后是停止、降速还是自动转为按量计费。

本仓库刻意不固化价格和精确额度：促销、模型列表、请求窗口和地区政策变化很快，静态数字容易误导。

需要在多个 Plan 或 API 供应商之间频繁切换时，可以用社区配置切换工具统一管理上述配置。例如开源桌面工具 [CC.SWITCH](https://ccswitch.io/)，可在 Claude Code、Codex、OpenCode 等 CLI 之间一键切换 Base URL、Key 与默认模型，避免手改配置文件；项目见 [farion1231/cc-switch](https://github.com/farion1231/cc-switch)，请仅从官方渠道下载。这类工具只做本地配置切换，本身不提供额度或请求代理。

### 第三方对比参考

| 工具                                                                          | 内容                                             | 使用提示                                           |
| ----------------------------------------------------------------------------- | ------------------------------------------------ | -------------------------------------------------- |
| [AI Coding Plan 平台评测与对比](https://vibecoding.dreamfree.space/)          | Coding Plan 平台横评、模型基准与选型文章         | 第三方社区工具，数据和结论请以官方来源交叉核对     |
| [awesome-coding-plan](https://github.com/mahonzhan/awesome-coding-plan)       | 各厂家 Coding Plan 实际价值对比                  | 第三方社区整理，套餐与价格请以官方页面核对         |

以上为社区整理的第三方对比参考，不属于官方信息；套餐、价格和模型列表变化很快，使用前请回到各厂商官方页面核对。

## API Router / 聚合平台

API Router、Inference Provider 和云模型市场提供统一接口、模型目录、账单、路由或托管推理。它们解决“如何接入和运行模型”，但不会自动替代 Agent Harness。

### 全球多模型与推理平台

| 平台                                                                                                               | 覆盖与特点                                                | 更接近哪一层                 |
| ------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------- | ---------------------------- |
| [OpenRouter](https://openrouter.ai/)                                                                               | 多模型统一 API、供应商路由、回退和统一账单                | Router / Marketplace         |
| [Together AI](https://docs.together.ai/docs/inference/overview)                                                    | 大量开放模型，Serverless 与 Dedicated Endpoint            | Inference Provider           |
| [Fireworks AI](https://fireworks.ai/inference)                                                                     | 优化推理、Serverless / Dedicated、OpenAI / Anthropic 兼容 | Inference Provider           |
| [GroqCloud](https://console.groq.com/docs/overview)                                                                | 低延迟推理平台与兼容 API                                  | Inference Provider           |
| [Hugging Face Inference Providers](https://huggingface.co/docs/inference-providers/main/en/index)                  | 一个 HF Token 接入多家推理提供商                          | Router / Provider Aggregator |
| [Replicate](https://replicate.com/docs/topics/models/run-a-model/)                                                 | 通过 Web 或 API 运行文本、图像、音视频等模型              | Model Hosting / API          |
| [Baseten](https://docs.baseten.co/)                                                                                | 专用模型部署、推理与生产基础设施                          | Model Serving                |
| [AWS Bedrock](https://docs.aws.amazon.com/bedrock/)                                                                | 多厂商基础模型、AWS 原生安全与企业服务                    | Hyperscaler Model Platform   |
| [Google Vertex AI Model Garden](https://cloud.google.com/vertex-ai/generative-ai/docs/model-garden/explore-models) | Google 与第三方模型目录、部署和治理                       | Hyperscaler Model Platform   |
| [Microsoft Foundry Models](https://azure.microsoft.com/en-us/products/ai-foundry/models/)                          | 多厂商模型目录、API、部署与企业治理                       | Hyperscaler Model Platform   |

### 国内模型平台与聚合服务

| 平台                                                              | 覆盖与特点                                      | 使用前重点检查                         |
| ----------------------------------------------------------------- | ----------------------------------------------- | -------------------------------------- |
| [硅基流动 SiliconFlow](https://siliconflow.cn/)                   | 国内外开源与商业模型 API、统一推理平台          | 模型版本、地域、速率、数据和发票       |
| [阿里云百炼](https://www.aliyun.com/product/bailian)              | Qwen 及第三方模型、Agent / 应用构建和云能力     | 地域端点、不同产品线 Key、模型白名单   |
| [火山引擎方舟](https://www.volcengine.com/product/ark)            | 豆包与多模型服务、推理和 Agent 工具链           | Endpoint、上下文、并发与套餐边界       |
| [腾讯云](https://cloud.tencent.cn/product/tokenhub)               | 多模型 Token、推理与 Agent 工具适配             | Coding / 通用套餐差异、调度与兼容协议  |
| [百度智能云千帆](https://cloud.baidu.com/doc/qianfan/index.html)  | 文心及多模型平台、Agent 开发与企业服务          | 区域、模型映射、配额和接口差异         |
| [魔搭 ModelScope](https://modelscope.cn/)                         | 模型社区、在线推理、开发和部署生态              | 社区模型许可、托管限制和生产 SLA       |
| [共绩算力](https://suanli.cn/)                                    | Serverless GPU 推理按量，支持 Kimi-K3、GLM-5.3  | 与官方价差、限流、服务稳定性与数据条款 |
| [优云智算](https://www.compshare.cn/)                             | GLM-5.2、DeepSeek-V4-Flash 全档支持，倍率透明   | 套餐档位、倍率折算和并发限流           |
| [华为云](https://www.huaweicloud.com/)                            | Coding Plan 定时放量，覆盖 GLM、Kimi、DeepSeek  | 模型更新节奏、放量时间与额度           |
| [京东云](https://www.jdcloud.com/)                                | Coding Plan 定时放量，接入 Kimi、GLM、DeepSeek  | 模型新旧与额度证据                     |
| [讯飞星火](https://xinghuo.xfyun.cn/)                             | 低价套餐已下架，仅剩高效版与速通版              | 限购、高峰拥挤与套餐条件               |
| [联通云](https://www.cucloud.cn/)                                 | Coding Plan 已下线，仅剩 Token Plan             | 模型覆盖与额度证据                     |
| [移动云](https://ecloud.10086.cn/)                                | 以 MiniMax 系列模型为主，旗舰模型覆盖有限       | 模型覆盖与用量证据                     |
| [阶跃星辰](https://www.stepfun.com/)                              | step 系列自研模型与 step-router 聚合入口        | 第三方模型覆盖与定价                   |
| [商汤日日新](https://www.sensetime.com/cn)                        | SenseNova 自研与 DeepSeek-V4-Flash，仅免费会员  | 编程向模型选择与额度政策               |
| [摩尔线程](https://www.mthreads.com/)                             | 以 GLM-4.7 为主，免费会员、定时放量             | 模型覆盖与放量安排                     |

### 官方平台与非官方中转站

应把以下三类服务分开：

1. 模型厂商官方 API；
2. 有明确运营主体、计费、文档和数据条款的聚合 / 云推理平台；
3. 非官方转售、反向代理、共享账号或来源不透明的中转服务。

第三类可能存在密钥泄露、请求内容留存、模型冒充、余额损失、服务中断、违反上游条款和缺少售后主体等风险。不要向来源不明的端点发送私有代码、客户数据、浏览器凭据或长期有效的高权限密钥。

选择 Router 时不要只比较每百万 Token 单价。还应比较缓存计费、失败重试、上下文裁剪、工具调用、速率、可观测性、数据保留、模型是否被静默替换，以及直接供应商不可用时的回退策略。

## 基础模型 / Chat 产品

Chat 产品、基础模型 / API 和 Agent 产品是三个不同层次。Chat 可能内置 Agent；一个 Agent 也可能允许切换多个模型。

| 体系        | 基础模型 / API                                                    | 面向用户的 Chat 或入口                       | 相关 Agent 产品                             |
| ----------- | ----------------------------------------------------------------- | -------------------------------------------- | ------------------------------------------- |
| OpenAI      | [GPT / OpenAI API](https://developers.openai.com/api/)            | [ChatGPT](https://chatgpt.com/)              | Codex、ChatGPT agent                        |
| Anthropic   | [Claude API](https://docs.anthropic.com/)                         | [Claude](https://claude.ai/)                 | Claude Code、Claude Cowork、Computer Use    |
| Google      | [Gemini API](https://ai.google.dev/)                              | [Gemini](https://gemini.google.com/)         | Antigravity、Gemini CLI、Jules              |
| xAI         | [Grok API](https://docs.x.ai/)                                    | [Grok](https://grok.com/)                    | Grok Build                                  |
| Meta        | [Llama](https://www.llama.com/) · [Muse](https://ai.meta.com/)    | Meta AI                                      | Muse Code                                   |
| Mistral AI  | [Mistral API](https://docs.mistral.ai/)                           | [Le Chat](https://chat.mistral.ai/)          | 可接多模型 Harness                          |
| DeepSeek    | [DeepSeek API](https://api-docs.deepseek.com/)                    | [DeepSeek Chat](https://chat.deepseek.com/)  | DeepSeek Harness                            |
| 阿里 / Qwen | [Qwen / Model Studio](https://www.aliyun.com/product/bailian)     | [Qwen Chat](https://chat.qwen.ai/)           | Qwen Code、Qwen-Agent、QwenPaw、Qoder       |
| 智谱        | [GLM API](https://docs.bigmodel.cn/)                              | [智谱清言 / Z.ai](https://chat.z.ai/)        | ZCode、AutoGLM、AutoClaw                    |
| 月之暗面    | [Kimi API](https://platform.moonshot.cn/)                         | [Kimi](https://www.kimi.com/)                | Kimi Code、Kimi Work、WebBridge             |
| MiniMax     | [MiniMax API](https://platform.minimaxi.com/)                     | [MiniMax](https://www.minimaxi.com/)         | MiniMax Code、Token Plan                    |
| 字节跳动    | [豆包 / Seed / 方舟](https://www.volcengine.com/product/doubao)   | [豆包](https://www.doubao.com/)              | TRAE、TRAE Work、UI-TARS 生态               |
| 腾讯        | [混元](https://cloud.tencent.com/product/hunyuan)                 | [腾讯元宝](https://yuanbao.tencent.com/)     | CodeBuddy、WorkBuddy、QClaw、Marvis         |
| 百度        | [文心 / 千帆](https://cloud.baidu.com/doc/qianfan/index.html)     | [文心一言](https://yiyan.baidu.com/)         | Comate、Zulu、千帆 Agent 平台               |

上表表示同一厂商或生态中的主要关系，不表示某个 Agent 永远只使用自家模型。例如 OpenCode、Cline、Kilo、Aider、Goose、OpenHands 和多个 Work Agent 都可以在一定范围内接入不同模型或 Router。

## 选型速查

| 目标                           | 优先考察的类别                    | 关键问题                                             |
| ------------------------------ | --------------------------------- | ---------------------------------------------------- |
| 在当前项目里边看边改           | AI IDE / CLI Agent                | 大仓理解、测试、权限、diff 和撤销                    |
| 把 Issue 委派出去，回来审 PR   | Cloud / Repository-native Agent   | 沙箱、并发、PR 质量、日志、凭据和成本                |
| 自动审查每个 Pull Request      | Repository-native Review Agent    | 全仓上下文、误报、规则、修复闭环和数据范围           |
| 处理本地文档、表格和 PPT       | Work / Desktop Agent              | 文件保真、隐私、可撤销性和交付质量                   |
| 自动填写网页或跨应用操作       | Browser / Computer Use            | 登录态隔离、确认、失败恢复和提示注入防护             |
| 让个人 Agent 定时或常驻工作    | Personal / Always-on Agent        | 设备在线、远程入口、记忆、密钥、预算和审计           |
| 开发自己的 Agent 或工作流      | Framework / Workflow Platform     | Runtime、状态、工具、部署、观测、人工介入和许可证    |
| 给多个 Agent 统一购买模型额度  | Coding / Token Plan 或 Router     | 客户端白名单、模型、速率、真实成本和数据条款         |
| 需要生产级模型托管与企业治理   | Inference / Hyperscaler Platform  | 区域、SLA、网络、合规、专用部署和可观测性            |

### 一个实用的选型顺序

1. 先确定工作对象：代码、仓库、网页、桌面还是办公文件；
2. 再确定执行位置：本机、云沙箱、CI 还是常驻服务器；
3. 选择 Harness / 产品入口；
4. 最后比较模型和额度方案；
5. 用真实任务测试成功率、人工接管、回滚和总成本，而不是只看模型榜单。

## 维护与贡献

欢迎通过 Issue 或 Pull Request 提交：

- 新产品或已停止服务的产品；
- 官方名称、链接、产品归属或分类修正；
- 官方宣布的能力、地区、平台或套餐变化；
- Preview、Beta、GA、停止维护或重命名状态变化；
- 可复现的能力边界、安全注意事项和兼容性信息。

提交更新时，请尽量提供官方产品页、官方文档、发布公告或官方开源仓库。二手评测可以作为补充，但不应成为“产品存在”或“官方能力”的唯一依据。价格类更新请同时注明地区、币种、税费、日期和套餐条件。

建议新增产品时至少说明：

1. 产品名称与官方链接；
2. 主要 Surface；
3. 执行位置；
4. 工作对象；
5. 典型交付物；
6. 模型关系；
7. 当前状态；
8. 为什么属于该分类。

版本记录见 [CHANGELOG.md](CHANGELOG.md)，贡献指南见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 信息时效与声明

- 当前版本：**v0.2.0**
- 最近系统核验：**2026-08-21**
- 本仓库是独立的社区整理项目，与文中任何厂商均无隶属、授权、赞助或背书关系。
- 产品名称与商标归各自权利人所有；链接优先指向官方来源。
- “支持”表示官方页面在核验时公开描述该能力，不代表所有地区、账号、系统、套餐或灰度版本都可用。
- Preview、Beta、Research Preview 和开源项目可能随时调整接口、能力、许可证、下载方式或停止维护。
- 本项目不提供购买建议、收益承诺或对安全性、可用性、合规性的保证。
- 对本地文件、浏览器登录态、代码仓库和第三方账号授予权限前，请自行完成风险评估并保留备份。
- 若官方页面与本仓库发生冲突，以官方最新说明为准。

## License

[MIT](LICENSE)
