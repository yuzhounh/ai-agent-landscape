# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Added NVIDIA NIM free tier (100+ open models, low rate limit, no SLA) to the vendor plan table.

### Changed

- Enriched the plan table from the awesome-coding-plan value comparison: tier names and quota mechanics for Zhipu, Kimi, MiMo, Codex and Claude Code memberships, DeepSeek API characteristics, Bailian Lite discontinuation, Ark daily limited stock, and OpenCode Go / Ollama model coverage; noted IDE/plugin plan billing models (usage-based vs quota-based) and the Gemini CLI / Code Assist subscription entry change; added free-tier and subscription notes for OpenRouter and Fireworks AI.
- Refreshed the plan table and domestic platform table from the 2026-08-16 third-party comparison: updated purchase availability and model coverage for Zhipu, Model Studio, Tencent Cloud, Ark, Qianfan, Kimi, MiniMax, DeepSeek, Codex, Claude Code, OpenCode, and Ollama; added Huawei Cloud, JD Cloud, iFlytek Spark, China Unicom Cloud, China Mobile Cloud, StepFun, SenseTime SenseNova, and Moore Threads to domestic platforms.

## [0.2.0] - 2026-08-19

### Added

- Added Cursor Origin (agent-native code hosting with repos, PRs, and GitHub sync; early beta) to the repository-native agent table.

### Changed

- Expanded the README from a representative shortlist into a broader ecosystem directory covering additional IDE, CLI, cloud, repository-native, work, personal, computer-use, framework, plan, router, and model products.
- Added product-family mapping to clarify how models, harnesses, surfaces, cloud execution, and plans relate across major vendors.
- Corrected DeepSeek Harness to reflect its official developer-preview release and open-source repository.
- Added clearer status, evidence, compatibility, security, and maintenance guidance.
- Simplified product naming across tables and removed the disproportionate DeepSeek Harness standalone section.
- Enriched the plan table based on a third-party Coding Plan comparison: added Xiaomi MiMo Token Plan, Codex, and Claude Code quota rows, and refreshed tier and availability notes for Zhipu, Model Studio, Ark, Kimi, MiniMax, OpenCode, and Ollama.
- Updated the last-verified badge to 2026-08-19 and re-aligned all README table padding to consistent CJK-aware display widths.
- Added third-party Coding Plan comparison references, moved CC.SWITCH into the plan compatibility notes as a config-switching tool, added 共绩算力 and 优云智算 to domestic platforms, and renamed platform entries (硅基流动 SiliconFlow, 阿里云百炼, 腾讯云).

## [0.1.0] - 2026-08-15

### Added

- Initial public release of the AI Agent ecosystem landscape.
- Classification framework based on interface, execution location, work object, and autonomy.
- Coverage of AI IDEs, terminal agents, cloud/background agents, repository-native agents, work/desktop agents, always-on agents, and computer/browser-use agents.
- Separate maps for Coding Plan, Token Plan, API routers, foundation models, and chat products.
- Clarifications for cross-category product families and the distinction between models, harnesses, surfaces, and plans.

[Unreleased]: https://github.com/yuzhounh/ai-agent-landscape/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/yuzhounh/ai-agent-landscape/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/yuzhounh/ai-agent-landscape/releases/tag/v0.1.0
