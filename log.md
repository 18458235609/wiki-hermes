# Wiki Log

> 维基所有操作的时序记录。追加写入。
> 格式：`## [YYYY-MM-DD] action | subject`
> 操作类型：ingest, update, query, lint, create, archive, delete
> 此文件超过 500 条时轮换：重命名为 `log-YYYY.md`，新建空白文件。

## [2026-04-19] create | Wiki initialized
- Domain: Hermes Agent 进化学习方法论
- Structure created with SCHEMA.md, index.md, log.md
- Sub-domains: self-improvement, skill system, delegation, prompting
- Directory: /home/wings/wiki-hermes

## [2026-04-19] ingest | Self-improvement research — arxiv papers + concept pages
- Searched arxiv for: self-reflection, error recovery, agent memory, feedback loops, skill acquisition
- Key papers found: REGREACT, Self-Correcting RAG, Adaptive Memory Crystallization, Persistent Identity in AI Agents, Drawing on Memory
- Raw sources saved: raw/papers/self-reflection-arxiv-2026.md, raw/papers/memory-arxiv-2026.md
- Concept pages: self-reflection, error-recovery, agent-memory, feedback-loop, skill-acquisition, learning-from-mistakes (6 pages)

## [2026-04-19] ingest | Skill system research + concept pages
- Inspected ~/.hermes/skills/ — 74 skills installed, categories: devops, mlops, github, research, media, autonomous-ai-agents, etc.
- Examined skill file structure: SKILL.md with YAML frontmatter, linked files in subdirectories
- Examined hermes-agent skill for skill loading mechanics
- Concept pages created (6):
  - concepts/skill.md — Skill 定义、与其他知识形式对比
  - concepts/skill-management.md — 技能全生命周期管理
  - concepts/skill-loading.md — 运行时加载机制
  - concepts/skill-vetting.md — 审核检查清单
  - concepts/skill-creation.md — 技能创建流程和模板
  - concepts/prompting.md — 提示工程技术（CoT、Few-shot 等）
- index.md updated (Total pages: 12)

## [2026-04-19] ingest | Delegation / orchestration research + concept pages
- Examined subagent-driven-development skill for real delegation patterns (3-role pattern: implementer → spec reviewer → quality reviewer)
- delegation.md — 两种模式：delegate_task（进程内）vs spawn hermes process（进程外）
- subagent.md — 子代理隔离特性、三角色模式
- multi-agent.md — 层级/监督/协作/MoA 四种架构；MetaGPT、ChatDev、AutoGen、CrewAI、LangGraph
- orchestration.md — 五大职责：分解/委托/监控/聚合/恢复；Fan-Out/Pipeline/Supervisor 模式
- workflow.md — 工作流作为 skill；TDD/Subagent-Driven/Cron 等模式
- task-planning.md — 分解策略（线性/并行/层级/条件）；好计划标准
- index.md updated (Total pages: 18)

## [2026-04-19] ingest | Prompting techniques research + concept pages
- chain-of-thought.md — Zero-shot CoT / Few-shot CoT / Self-consistency / Tree-of-Thought
- few-shot.md — 示例模式、用途、局限性（格式/分类/数据抽取）
- role-playing.md — 专家/评审/苏格拉底/角色等模式；风险与约束
- output-formatting.md — JSON/表格/代码块；约束解码 vs 隐式提示 vs 后处理
- system-prompt.md — 系统提示的组成分层；与 skill 注入的关系
- index.md updated (Total pages: 24)

## [2026-04-19] ingest | Entities: frameworks and agents
- hermes-agent.md — Nous Research 开源框架，~30k stars，特性列表，架构组成
- claude-code.md — Anthropic CLI Agent，两种模式（print/PTY），Hermes 集成方式
- metagpt.md — SOP 驱动多 Agent，ICLR 2024 Oral，结构化文档作为 Agent 间通信
- autogen.md — Microsoft 多 Agent，对话模式，User Proxy + Assistant 双 Agent 模式
- crewai.md — 角色 Agent，Sequential/Hierarchical 流程，Role/Task/Crew 抽象
- langgraph.md — 图式工作流，State + Nodes + Edges，支持循环和人机交互
- index.md updated (Total pages: 30)

## [2026-04-19] ingest | Comparisons and Queries
- comparisons/multi-agent-frameworks.md — 五大框架对比（通信模型/自主性/适用场景）
- comparisons/knowledge-compilation.md — 知识持久化方法对比（技能/微调/RAG/prompting）
- comparisons/delegation-patterns.md — delegate_task vs spawn hermes process
- queries/when-multi-agent.md — 何时用多 Agent vs 单 Agent（决策树）
- queries/when-create-skill.md — 何时建 skill vs 改进 prompting（触发检查表）
- queries/self-improving-loop.md — Agent 自我提升飞轮综合分析
- index.md updated (Total pages: 33)

## [2026-04-19] create | Self-Improving Agent Skills
- skills/autonomous-ai-agents/post-task-reflection.md — 任务后结构化复盘，second-order thinking
- skills/autonomous-ai-agents/error-classify-recover.md — 错误分类 + 恢复策略选择
- skills/autonomous-ai-agents/lesson-to-skill.md — 教训提炼为可复用 skill 的完整流程
