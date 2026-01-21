<a href="https://github.com/VoltAgent/voltagent">
<img width="1500" height="500" alt="claude-skills" src="https://github.com/user-attachments/assets/39c54dfd-129e-4b43-8b92-20824a56e069" />
</a>

<br/>
<br/>

<div align="center">
    <strong>Claude 技能精选合集，包含官方和社区构建的优质资源。
    </strong>
    <br />
    <br />

</div>

<div align="center">

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
![Last Update](https://img.shields.io/github/last-commit/VoltAgent/awesome-claude-skills?label=Last%20update&style=flat-square)
[![Discord](https://img.shields.io/discord/1361559153780195478.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2)](https://s.voltagent.dev/discord)
[![GitHub forks](https://img.shields.io/github/forks/VoltAgent/awesome-claude-skills?style=social)](https://github.com/VoltAgent/awesome-claude-skills/network/members)

</div>

# Awesome Claude Skills

Claude Skills（Claude 技能）是包含指令、脚本和资源的文件夹，用于教导 Claude 执行特定任务。技能可以包含可执行代码，并且仅在需要时加载，这使得你可以维护数百个技能而不会影响性能。多个技能可以同时运行以完成复杂任务，如文档创建、代码测试和数据分析。

**注意：** Claude Skills 现已成为被多个 AI 编码助手采用的 **Agent Skills** 标准。这意味着此处列出的技能也可以在 Codex、Gemini CLI 和其他兼容工具中使用。请参阅下表了解路径和文档。

### 一个基本技能是什么样的？

```YAML
---
name: api-tester
description: Test REST APIs and validate responses
---

# API Tester

Test HTTP endpoints and validate response structures.

## When to Use This Skill

Use this skill when you need to test API endpoints and verify response data.

## Instructions

When testing an API:

1. Send a request to the specified endpoint
2. Check the response status code
3. Validate the response body structure
4. Report any errors or unexpected results

## Response Validation

- Verify required fields exist
- Check data types match expected values
- Confirm nested objects have correct structure
```

查看 [官方仓库](https://github.com/anthropics/skills) 和 [创建指南](https://support.claude.com/en/articles/12512198-how-to-create-custom-skills) 了解更多详情。

### 其他 AI 编码助手的技能路径

| 工具 | 项目路径 | 全局路径 | 官方文档 |
|------|-------------|-------------|---------------|
| Antigravity | `.agent/skills/` | `~/.gemini/antigravity/skills/` | [Antigravity Skills](https://antigravity.google/docs/skills) |
| Claude Code | `.claude/skills/` | `~/.claude/skills/` | [Claude Code Skills](https://docs.anthropic.com/en/docs/claude-code/skills) |
| Codex | `.codex/skills/` | `~/.codex/skills/` | [Codex Skills](https://developers.openai.com/codex/skills) |
| Cursor | `.cursor/skills/` | `~/.cursor/skills/` | [Cursor Skills](https://cursor.com/docs/context/skills) |
| Gemini CLI | `.gemini/skills/` | `~/.gemini/skills/` | [Gemini CLI Skills](https://geminicli.com/docs/cli/skills/) |
| GitHub Copilot | `.github/skills/` | `~/.copilot/skills/` | [Copilot Skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) |
| OpenCode | `.opencode/skills/` | `~/.config/opencode/skills/` | [OpenCode Skills](https://opencode.ai/docs/skills) |
| Windsurf | `.windsurf/skills/` | `~/.codeium/windsurf/skills/` | [Windsurf Cascade Skills](https://docs.windsurf.com/windsurf/cascade/skills) |

### 在 Trae 和 Qoder 中使用

虽然 **Trae** 和 **Qoder** 主要使用“规则 (Rules)”系统，而不是基于目录的“技能 (Skills)”标准，但你仍然可以利用这些资源：

- **Trae**: Trae 使用 `.rules` 文件来管理上下文。你可以通过将技能的指令（即 `SKILL.md` 的内容）复制到 `.trae/project_rules.md`（用于项目特定技能）或 `user_rules.md`（用于全局技能）来适配技能。可以通过 **Settings > Rules** 进行配置。
- **Qoder**: Qoder 使用 `.qoder/rules` 来优化模型行为。你可以将技能的指令放入 `.qoder/rules/` 中的规则文件里，或者利用 **Repo Wiki** 功能让 Agent 能够访问技能的文档。

<br/>

<a href="https://github.com/VoltAgent/voltagent">
<img width="3082" height="592" alt="cta" src="https://github.com/user-attachments/assets/74dbaad4-8285-420b-95df-245948c766c8" />
</a>

<br/>

## 官方 Claude 技能

### 文档创建

- **[anthropics/docx](https://github.com/anthropics/skills/tree/main/skills/docx)** - 创建、编辑和分析 Word 文档
- **[anthropics/doc-coauthoring](https://github.com/anthropics/skills/tree/main/skills/doc-coauthoring)** - 协作文档编辑和共同创作
- **[anthropics/pptx](https://github.com/anthropics/skills/tree/main/skills/pptx)** - 创建、编辑和分析 PowerPoint 演示文稿
- **[anthropics/xlsx](https://github.com/anthropics/skills/tree/main/skills/xlsx)** - 创建、编辑和分析 Excel 电子表格
- **[anthropics/pdf](https://github.com/anthropics/skills/tree/main/skills/pdf)** - 提取文本、创建 PDF 和处理表单

### 创意与设计

- **[anthropics/algorithmic-art](https://github.com/anthropics/skills/tree/main/skills/algorithmic-art)** - 使用带有随机种子的 p5.js 创建生成艺术
- **[anthropics/canvas-design](https://github.com/anthropics/skills/tree/main/skills/canvas-design)** - 设计 PNG 和 PDF 格式的视觉艺术
- **[anthropics/frontend-design](https://github.com/anthropics/skills/tree/main/skills/frontend-design)** - 前端设计和 UI/UX 开发工具
- **[anthropics/slack-gif-creator](https://github.com/anthropics/skills/tree/main/skills/slack-gif-creator)** - 创建针对 Slack 尺寸限制优化的动画 GIF
- **[anthropics/theme-factory](https://github.com/anthropics/skills/tree/main/skills/theme-factory)** - 使用专业主题样式化产物或生成自定义主题

### 开发

- **[anthropics/web-artifacts-builder](https://github.com/anthropics/skills/tree/main/skills/web-artifacts-builder)** - 使用 React 和 Tailwind 构建复杂的 claude.ai HTML 产物
- **[anthropics/mcp-builder](https://github.com/anthropics/skills/tree/main/skills/mcp-builder)** - 创建 MCP 服务器以集成外部 API 和服务
- **[anthropics/webapp-testing](https://github.com/anthropics/skills/tree/main/skills/webapp-testing)** - 使用 Playwright 测试本地 Web 应用程序

### 品牌与沟通

- **[anthropics/brand-guidelines](https://github.com/anthropics/skills/tree/main/skills/brand-guidelines)** - 将 Anthropic 的品牌颜色和排版应用于产物
- **[anthropics/internal-comms](https://github.com/anthropics/skills/tree/main/skills/internal-comms)** - 撰写状态报告、新闻通讯和常见问题解答 (FAQ)

### 元技能 (Meta)

- **[anthropics/skill-creator](https://github.com/anthropics/skills/tree/main/skills/skill-creator)** - 创建扩展 Claude 能力的技能指南
- **[anthropics/template](https://github.com/anthropics/skills/tree/main/template)** - 用于创建新技能的基本模板

## Vercel 工程团队的技能

- **[vercel-labs/react-best-practices](https://github.com/vercel-labs/agent-skills/tree/main/skills/react-best-practices)** - React 最佳实践和模式
- **[vercel-labs/vercel-deploy-claimable](https://github.com/vercel-labs/agent-skills/tree/main/skills/claude.ai/vercel-deploy-claimable)** - 将项目部署到 Vercel
- **[vercel-labs/web-design-guidelines](https://github.com/vercel-labs/agent-skills/tree/main/skills/web-design-guidelines)** - Web 设计指南和标准

## Trail of Bits 团队的安全技能

- **[trailofbits/ask-questions-if-underspecified](https://github.com/trailofbits/skills/tree/main/plugins/ask-questions-if-underspecified)** - 对模棱两可的需求提示进行澄清
- **[trailofbits/audit-context-building](https://github.com/trailofbits/skills/tree/main/plugins/audit-context-building)** - 通过超细粒度代码分析构建深度架构上下文
- **[trailofbits/building-secure-contracts](https://github.com/trailofbits/skills/tree/main/plugins/building-secure-contracts)** - 包含 6 个区块链漏洞扫描器的智能合约安全工具包
- **[trailofbits/burpsuite-project-parser](https://github.com/trailofbits/skills/tree/main/plugins/burpsuite-project-parser)** - 搜索并提取 Burp Suite 项目文件中的数据
- **[trailofbits/constant-time-analysis](https://github.com/trailofbits/skills/tree/main/plugins/constant-time-analysis)** - 检测加密代码中编译器引起的时间侧信道
- **[trailofbits/culture-index](https://github.com/trailofbits/skills/tree/main/plugins/culture-index)** - 索引和搜索文化文档
- **[trailofbits/differential-review](https://github.com/trailofbits/skills/tree/main/plugins/differential-review)** - 带有 git 历史分析的以安全为重点的差异审查
- **[trailofbits/dwarf-expert](https://github.com/trailofbits/skills/tree/main/plugins/dwarf-expert)** - DWARF 调试格式专家
- **[trailofbits/entry-point-analyzer](https://github.com/trailofbits/skills/tree/main/plugins/entry-point-analyzer)** - 识别智能合约中改变状态的入口点
- **[trailofbits/fix-review](https://github.com/trailofbits/skills/tree/main/plugins/fix-review)** - 验证修复提交是否解决了审计发现的问题且没有引入新错误
- **[trailofbits/property-based-testing](https://github.com/trailofbits/skills/tree/main/plugins/property-based-testing)** - 针对多种语言和智能合约的基于属性的测试
- **[trailofbits/semgrep-rule-creator](https://github.com/trailofbits/skills/tree/main/plugins/semgrep-rule-creator)** - 创建和优化用于漏洞检测的 Semgrep 规则
- **[trailofbits/sharp-edges](https://github.com/trailofbits/skills/tree/main/plugins/sharp-edges)** - 识别容易出错的 API 和危险配置
- **[trailofbits/spec-to-code-compliance](https://github.com/trailofbits/skills/tree/main/plugins/spec-to-code-compliance)** - 用于区块链审计的规范到代码合规性检查器
- **[trailofbits/static-analysis](https://github.com/trailofbits/skills/tree/main/plugins/static-analysis)** - 包含 CodeQL、Semgrep 和 SARIF 的静态分析工具包
- **[trailofbits/testing-handbook-skills](https://github.com/trailofbits/skills/tree/main/plugins/testing-handbook-skills)** - 测试手册技能：模糊测试器、静态分析、清理器
- **[trailofbits/variant-analysis](https://github.com/trailofbits/skills/tree/main/plugins/variant-analysis)** - 通过基于模式的分析查找类似漏洞

## Sentry 团队为其开发团队提供的技能

- **[getsentry/agents-md](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/agents-md)** - 生成和管理 AGENTS.md 文件
- **[getsentry/claude-settings-audit](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/claude-settings-audit)** - 审计 Claude 设置配置
- **[getsentry/code-review](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/code-review)** - 执行代码审查
- **[getsentry/commit](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/commit)** - 使用最佳实践创建提交
- **[getsentry/create-pr](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/create-pr)** - 创建拉取请求 (PR)
- **[getsentry/deslop](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/deslop)** - 清理草率的代码
- **[getsentry/find-bugs](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/find-bugs)** - 查找并识别代码中的错误
- **[getsentry/iterate-pr](https://github.com/getsentry/skills/tree/main/plugins/sentry-skills/skills/iterate-pr)** - 迭代拉取请求反馈

## Cloudflare 工程师的技能

- **[dmmulroy/cloudflare-skill](https://github.com/dmmulroy/cloudflare-skill/tree/main/skill/cloudflare)** - 供 AI/LLM 使用的综合 Cloudflare 平台参考文档。涵盖 Workers、Pages、存储 (KV, D1, R2)、AI (Workers AI, Vectorize, Agents SDK)、网络、安全和基础设施即代码。

## Hugging Face 团队的技能

Hugging Face 团队为 ML 工作流提供的官方 AI agent 技能。

- **[huggingface/hugging-face-cli](https://github.com/huggingface/skills/tree/main/skills/hugging-face-cli)** - 用于模型、数据集、仓库和计算任务的 HF Hub CLI
- **[huggingface/hugging-face-datasets](https://github.com/huggingface/skills/tree/main/skills/hugging-face-datasets)** - 使用配置和 SQL 查询创建和管理数据集
- **[huggingface/hugging-face-evaluation](https://github.com/huggingface/skills/tree/main/skills/hugging-face-evaluation)** - 使用 vLLM/lighteval 和评估表进行模型评估
- **[huggingface/hugging-face-jobs](https://github.com/huggingface/skills/tree/main/skills/hugging-face-jobs)** - 在 HF 基础设施上运行计算任务和 Python 脚本
- **[huggingface/hugging-face-model-trainer](https://github.com/huggingface/skills/tree/main/skills/hugging-face-model-trainer)** - 使用 TRL 训练模型：SFT、DPO、GRPO、GGUF 转换
- **[huggingface/hugging-face-paper-publisher](https://github.com/huggingface/skills/tree/main/skills/hugging-face-paper-publisher)** - 在 HF Hub 上发布带有模型/数据集链接的论文
- **[huggingface/hugging-face-tool-builder](https://github.com/huggingface/skills/tree/main/skills/hugging-face-tool-builder)** - 为 HF API 操作构建可重用的脚本
- **[huggingface/hugging-face-trackio](https://github.com/huggingface/skills/tree/main/skills/hugging-face-trackio)** - 使用实时仪表板跟踪 ML 实验

## Expo 团队的技能

Expo 团队为构建、部署和调试 Expo 应用程序提供的官方 AI agent 技能。

- **[expo/expo-app-design](https://github.com/expo/skills/tree/main/plugins/expo-app-design)** - 设计和构建 Expo 应用程序
- **[expo/expo-deployment](https://github.com/expo/skills/tree/main/plugins/expo-deployment)** - 将 Expo 应用程序部署到生产环境
- **[expo/upgrading-expo](https://github.com/expo/skills/tree/main/plugins/upgrading-expo)** - 升级 Expo SDK 版本

## 社区技能

### 生产力和协作

- **[notiondevs/Notion Skills for Claude](https://www.notion.so/notiondevs/Notion-Skills-for-Claude-28da4445d27180c7af1df7d8615723d0)** - 与 Notion 协作的技能
- **[op7418/NanoBanana-PPT-Skills](https://github.com/op7418/NanoBanana-PPT-Skills)** - AI 驱动的 PPT 生成，具有文档分析、样式化图像和可选视频过渡功能
- **[PleasePrompto/notebooklm-skill](https://github.com/PleasePrompto/notebooklm-skill)** - 与 NotebookLM 交互以进行基于文档的对话
- **[obra/superpowers-lab](https://github.com/obra/superpowers-lab)** - Claude 超能力的实验室环境
- **[obra/brainstorming](https://github.com/obra/superpowers/blob/main/skills/brainstorming/SKILL.md)** - 生成和探索想法
- **[obra/writing-plans](https://github.com/obra/superpowers/blob/main/skills/writing-plans/SKILL.md)** - 创建战略文档
- **[obra/executing-plans](https://github.com/obra/superpowers/blob/main/skills/executing-plans/SKILL.md)** - 实施和运行战略计划
- **[obra/dispatching-parallel-agents](https://github.com/obra/superpowers/blob/main/skills/dispatching-parallel-agents/SKILL.md)** - 协调多个并行 agent
- **[obra/sharing-skills](https://github.com/obra/superpowers/blob/main/skills/sharing-skills/SKILL.md)** - 分发和交流能力
- **[obra/using-superpowers](https://github.com/obra/superpowers/blob/main/skills/using-superpowers/SKILL.md)** - 利用核心平台能力
- **[ComposioHQ/content-research-writer](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/content-research-writer)** - 通过研究增强写作
- **[ComposioHQ/meeting-insights-analyzer](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/meeting-insights-analyzer)** - 分析会议沟通模式
- **[ComposioHQ/competitive-ads-extractor](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/competitive-ads-extractor)** - 分析竞争对手广告
- **[ComposioHQ/image-enhancer](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/image-enhancer)** - 提高图像质量
- **[wrsmith108/linear-claude-skill](https://github.com/wrsmith108/linear-claude-skill)** - 使用 MCP 工具、SDK 脚本和 GraphQL 回退管理 Linear 问题、项目和团队
- **[wshuyi/x-article-publisher-skill](https://github.com/wshuyi/x-article-publisher-skill)** - 将文章发布到 X/Twitter

### 开发与测试

- **[antonbabenko/terraform-skill](https://github.com/antonbabenko/terraform-skill)** - Terraform 基础设施即代码最佳实践
- **[zxkane/aws-skills](https://github.com/zxkane/aws-skills)** - 具有基础设施自动化和云架构模式的 AWS 开发
- **[conorluddy/ios-simulator-skill](https://github.com/conorluddy/ios-simulator-skill)** - 控制 iOS 模拟器
- **[sanjay3290/postgres](https://github.com/sanjay3290/ai-skills/tree/main/skills/postgres)** - 针对 PostgreSQL 数据库执行安全只读 SQL 查询，支持多连接
- **[sanjay3290/deep-research](https://github.com/sanjay3290/ai-skills/tree/main/skills/deep-research)** - 使用 Gemini Deep Research Agent 执行自主多步研究，用于市场分析和文献综述
- **[jthack/ffuf-claude-skill](https://github.com/jthack/ffuf_claude_skill)** - 使用 ffuf 进行 Web 模糊测试
- **[lackeyjb/playwright-skill](https://github.com/lackeyjb/playwright-skill)** - 使用 Playwright 进行浏览器自动化
- **[ibelick/ui-skills](https://github.com/ibelick/ui-skills)** - 固执己见的、不断发展的约束，用于指导 agent 构建界面
- **[nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill)** - UI/UX 设计模式和最佳实践
- **[scarletkc/vexor](https://github.com/scarletkc/vexor)** - 由向量驱动的 CLI，用于语义文件搜索，带有 Claude/Codex 技能
- **[obra/test-driven-development](https://github.com/obra/superpowers/blob/main/skills/test-driven-development/SKILL.md)** - 在实现代码之前编写测试
- **[ComposioHQ/changelog-generator](https://github.com/ComposioHQ/awesome-claude-skills/tree/master/changelog-generator)** - 将 git 提交转换为发布说明
- **[obra/subagent-driven-development](https://github.com/obra/superpowers/blob/main/skills/subagent-driven-development/SKILL.md)** - 使用多个子 agent 进行开发
- **[obra/systematic-debugging](https://github.com/obra/superpowers/blob/main/skills/systematic-debugging/SKILL.md)** - 代码中有条理的问题解决方法
- **[obra/root-cause-tracing](https://github.com/obra/superpowers/blob/main/skills/root-cause-tracing/SKILL.md)** - 调查并确定根本问题
- **[obra/testing-skills-with-subagents](https://github.com/obra/superpowers/blob/main/skills/testing-skills-with-subagents/SKILL.md)** - 协作测试方法
- **[obra/testing-anti-patterns](https://github.com/obra/superpowers/blob/main/skills/testing-anti-patterns/SKILL.md)** - 识别无效的测试实践
- **[obra/finishing-a-development-branch](https://github.com/obra/superpowers/blob/main/skills/finishing-a-development-branch/SKILL.md)** - 完成 Git 代码分支
- **[obra/requesting-code-review](https://github.com/obra/superpowers/blob/main/skills/requesting-code-review/SKILL.md)** - 发起代码审查流程
- **[obra/receiving-code-review](https://github.com/obra/superpowers/blob/main/skills/receiving-code-review/SKILL.md)** - 处理并整合代码反馈
- **[obra/using-git-worktrees](https://github.com/obra/superpowers/blob/main/skills/using-git-worktrees/SKILL.md)** - 管理多个 Git 工作树
- **[obra/verification-before-completion](https://github.com/obra/superpowers/blob/main/skills/verification-before-completion/SKILL.md)** - 在完成之前验证工作
- **[obra/condition-based-waiting](https://github.com/obra/superpowers/blob/main/skills/condition-based-waiting/SKILL.md)** - 管理条件暂停或延迟
- **[obra/commands](https://github.com/obra/superpowers/tree/main/skills/commands)** - 创建和管理命令结构
- **[obra/writing-skills](https://github.com/obra/superpowers/blob/main/skills/writing-skills/SKILL.md)** - 开发和记录能力
- **[fvadicamo/dev-agent-skills](https://github.com/fvadicamo/dev-agent-skills)** - Git 和 GitHub 工作流技能：git-commit（约定式提交）、github-pr-creation、github-pr-merge、github-pr-review，以及 creating-skills 指南
- **[omkamal/pypict-skill](https://github.com/omkamal/pypict-claude-skill/blob/main/SKILL.md)** - 成对测试生成
- **[alinaqi/claude-bootstrap](https://github.com/alinaqi/claude-bootstrap)** - 固执己见的项目初始化，带有安全第一的护栏、规范驱动的原子 todos、LLM 测试模式和 CLI 工具编排 (gh, vercel, supabase)
- **[ZhangHanDong/makepad-skills](https://github.com/ZhangHanDong/makepad-skills)** - Rust 应用程序的 Makepad UI 开发技能：设置、模式、着色器、打包和故障排除。
- **[callstackincubator/react-native-best-practices](https://github.com/callstackincubator/agent-skills/blob/main/skills/react-native-best-practices/SKILL.md)** - 来自 Callstack 的 React Native 应用程序性能优化

### 上下文工程

- **[muratcankoylan/context-fundamentals](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/context-fundamentals)** - 了解什么是上下文，为什么它很重要，以及 agent 系统中上下文的剖析
- **[muratcankoylan/context-degradation](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/context-degradation)** - 识别上下文失败的模式：迷失在中间、中毒、分心和冲突
- **[muratcankoylan/context-compression](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/context-compression)** - 设计和评估长期会话的压缩策略
- **[muratcankoylan/context-optimization](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/context-optimization)** - 应用压缩、屏蔽和缓存策略
- **[muratcankoylan/multi-agent-patterns](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/multi-agent-patterns)** - 掌握编排器、点对点和分层多 agent 架构
- **[muratcankoylan/memory-systems](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/memory-systems)** - 设计短期、长期和基于图的记忆架构
- **[muratcankoylan/tool-design](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/tool-design)** - 构建 agent 可以有效使用的工具，包括架构简化模式
- **[muratcankoylan/evaluation](https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering/tree/main/skills/evaluation)** - 构建 agent 系统的评估框架

### 专业领域

- **[K-Dense-AI/claude-scientific-skills](https://github.com/K-Dense-AI/claude-scientific-skills)** - 科学研究和分析技能
- **[NotMyself/claude-win11-speckit-update-skill](https://github.com/NotMyself/claude-win11-speckit-update-skill)** - Windows 11 系统管理
- **[sanjay3290/imagen](https://github.com/sanjay3290/ai-skills/tree/main/skills/imagen)** - 使用 Google Gemini 的 API 生成图像，用于 UI 原型、图标和视觉资产
- **[jeffersonwarrior/claudisms](https://github.com/jeffersonwarrior/claudisms)** - SMS 消息集成
- **[SHADOWPR0/security-bluebook-builder](https://github.com/SHADOWPR0/security-bluebook-builder)** - 为敏感应用程序构建简明、规范的安全蓝皮书（威胁模型、数据分类、身份验证/会话、日志记录/审计、保留、IR、安全门）
- **[obra/defense-in-depth](https://github.com/obra/superpowers/blob/main/skills/defense-in-depth/SKILL.md)** - 多层安全方法
- **[huifer/Claude-Ally-Health](https://github.com/huifer/Claude-Ally-Health)** - 用于医疗信息分析、症状跟踪和健康指导的健康助手技能
- **[frmoretto/clarity-gate](https://github.com/frmoretto/clarity-gate)** - RAG 系统中认知质量的预摄入验证，具有 9 点验证和两轮 HITL 工作流

### n8n 自动化

- **[czlonkowski/n8n-code-javascript](https://github.com/czlonkowski/n8n-skills/tree/main/skills/n8n-code-javascript)** - n8n Code 节点中的 JavaScript，带有数据访问模式
- **[czlonkowski/n8n-code-python](https://github.com/czlonkowski/n8n-skills/tree/main/skills/n8n-code-python)** - n8n Code 节点中的 Python 编码，有限制
- **[czlonkowski/n8n-expression-syntax](https://github.com/czlonkowski/n8n-skills/tree/main/skills/n8n-expression-syntax)** - 带有 {{}} 和 $json/$node 变量的 n8n 表达式语法
- **[czlonkowski/n8n-mcp-tools-expert](https://github.com/czlonkowski/n8n-skills/tree/main/skills/n8n-mcp-tools-expert)** - MCP 工具指南，包含工具选择和节点格式
- **[czlonkowski/n8n-node-configuration](https://github.com/czlonkowski/n8n-skills/tree/main/skills/n8n-node-configuration)** - 带有依赖规则和 AI 连接的节点配置
- **[czlonkowski/n8n-validation-expert](https://github.com/czlonkowski/n8n-skills/tree/main/skills/n8n-validation-expert)** - 使用错误目录修复 n8n 验证错误
- **[czlonkowski/n8n-workflow-patterns](https://github.com/czlonkowski/n8n-skills/tree/main/skills/n8n-workflow-patterns)** - Webhook、HTTP、数据库和 AI 任务的工作流模式

### 其他

- **[materials-simulation-skills](https://github.com/HeshamFS/materials-simulation-skills)** - 计算材料科学的 agent 技能：数值稳定性、时间步进、线性求解器、网格生成、模拟验证、参数优化和后处理
- **[wrsmith108/varlock-claude-skill](https://github.com/wrsmith108/varlock-claude-skill)** - 安全的环境变量管理，确保机密永远不会暴露在 Claude 会话、终端、日志或 git 提交中
- **[SHADOWPR0/beautiful_prose](https://github.com/SHADOWPR0/beautiful_prose)** - 永恒、有力的英语散文的硬性写作风格契约，没有 AI 的怪癖

## 🤝 贡献

我们欢迎贡献！请参阅 [CONTRIBUTING.md](CONTRIBUTING.md) 了解准则。

- 通过 PR 提交新技能
- 改进现有定义
- 添加新文档、视频和文章

**注意：** 请不要提交你 3 小时前创建的技能。我们现在专注于社区采用的技能，特别是那些由开发团队发布并在实际使用中得到验证的技能。质量重于数量。

* 这是一个精选列表。我们不审计、认可或保证所列项目的安全性或正确性。
