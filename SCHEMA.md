# Wiki Schema

## Domain
Hermes Agent 进化学习方法论 — Agent 自我提升、skill 系统、任务委托、工作流、prompting 技巧

## Conventions
- 文件名：小写、中划线、无空格（如 `self-reflection-methods.md`）
- 每个 wiki 页面以 YAML frontmatter 开头（见下方）
- 使用 `[[wikilinks]]` 链接其他页面，每页至少 2 个出站链接
- 更新页面时同步更新 `updated` 日期
- 新页面必须添加到 `index.md` 对应板块
- 所有操作追加到 `log.md`

## Frontmatter
```yaml
---
title: 页面标题
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [tag1, tag2]
sources: [raw/articles/source-name.md]
---
```

## Tag Taxonomy
**Agent 自我提升**
- self-improvement | self-reflection | error-recovery | memory | learning-from-mistakes | feedback-loop | skill-acquisition

**Skill 系统**
- skill | skill-management | skill-vetting | skill-loading | skill-creation | prompting | hermes-agent

**任务委托/调度**
- delegation | subagent | orchestration | multi-agent | task-planning | autonomous-agent | workflow

**Prompting 技巧**
- prompting | few-shot | chain-of-thought | cot | system-prompt | role-playing | constraints | output-formatting

**工程实践**
- debugging | testing | iteration | measurement | benchmark | evaluation

**Meta**
- comparison | timeline | opinion | meta | hermes-internal（Hermes 内部实现）
- case-study | experiment（实战案例/实验记录）

## Page Thresholds
- **创建页面：** 实体/概念在 2+ 来源中出现，或在一个来源中处于核心地位
- **追加到现有页：** 来源提到已覆盖的内容
- **不创建页面：** 路过一提的词、细小细节、或超出领域的内容
- **拆分页面：** 超过 ~200 行时拆分为子主题并交叉链接
- **归档页面：** 内容完全被取代时移到 `_archive/`，从 index 移除

## Entity Pages
每个 notable 实体一页，包括：
- 概述 / 是什么
- 关键事实和日期
- 与其他实体的关系（[[wikilinks]]）
- 来源引用

## Concept Pages
每个概念/主题一页，包括：
- 定义 / 解释
- 当前认知状态
- 开放问题或争议
- 相关概念（[[wikilinks]]）

## Comparison Pages
对比分析页，包括：
- 对比对象和对比原因
- 对比维度（表格格式优先）
- 结论或综合判断
- 来源

## Update Policy
新信息与现有内容冲突时：
1. 检查日期 — 新来源通常取代旧来源
2. 真正矛盾时，保留双方立场并注明日期和来源
3. 在 frontmatter 标记：`contradictions: [page-name]`
4. 在 lint 报告中标记待用户审查
