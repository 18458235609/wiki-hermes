# Wiki Index

> 内容目录。每个 wiki 页面按类型列出并附一句话摘要。
> 阅读此文件定位相关页面。
> Last updated: 2026-04-19 | Total pages: 33

## Entities
- [[hermes-agent]] — Nous Research 开源 Agent 框架（~30k stars），自带 skill 系统和记忆
- [[claude-code]] — Anthropic 的编程 Agent CLI，支持 print 模式和交互模式
- [[metagpt]] — 多 Agent 软件开发框架，ICLR 2024 Oral，SOP 驱动
- [[autogen]] — Microsoft 的对话式多 Agent 框架，消息传递模式
- [[crewai]] — 角色驱动多 Agent，支持顺序/层级流程
- [[langgraph]] — LangChain 上的图式工作流引擎，支持状态/循环/人机交互

## Concepts
- [[self-reflection]] — 自我反思：Agent 对自身输出的二次评价能力
- [[error-recovery]] — 错误恢复：检测失败并调整策略继续的能力
- [[agent-memory]] — Agent 记忆系统：跨会话持久化信息的能力
- [[feedback-loop]] — 反馈回路：输出反馈为输入实现自我纠正
- [[skill-acquisition]] — 技能获取：Agent 发展新能力的过程
- [[learning-from-mistakes]] — 错误中学习：将错误转化为未来行为改变
- [[skill]] — 技能系统：可复用文档化知识模块（74个已安装）
- [[skill-management]] — 技能管理：创建、维护、更新、审核、归档
- [[skill-loading]] — 技能加载：运行时将 skill 注入 agent 上下文
- [[skill-vetting]] — 技能审核：加载前检查安全性、准确性、质量
- [[skill-creation]] — 技能创建：将过程性知识编码为 SKILL.md
- [[prompting]] — 提示工程：CoT、Few-shot、Role-playing 等技巧
- [[delegation]] — 任务委托：父 agent 向子 agent 分发子任务
- [[subagent]] — 子代理：独立执行子任务的隔离 agent
- [[multi-agent]] — 多代理系统：多个 agent 协作的系统架构
- [[orchestration]] — 编排：协调多个 subagent 的控制平面
- [[workflow]] — 工作流：完成目标的定义步骤序列
- [[task-planning]] — 任务规划：分解复杂目标为可执行步骤
- [[chain-of-thought]] — 思维链：显式生成推理步骤提升复杂任务准确率
- [[few-shot]] — Few-shot：用示例展示模式而非直接指令
- [[role-playing]] — 角色扮演：赋予 agent 特定身份/专业视角
- [[output-formatting]] — 输出格式控制：JSON/表格/代码块等结构化约束
- [[system-prompt]] — 系统提示：定义 agent 身份/能力/约束的基础层

## Comparisons
- [[multi-agent-frameworks]] — MetaGPT/AutoGen/CrewAI/LangGraph/Hermes 五大框架对比
- [[knowledge-compilation]] — 知识持久化方法对比：skill/fine-tune/RAG/prompting
- [[delegation-patterns]] — delegate_task vs spawn hermes process 对比

## Queries
- [[when-multi-agent]] — 何时用多 Agent vs 单 Agent
- [[when-create-skill]] — 何时建 skill vs 改进 prompting
- [[self-improving-loop]] — Agent 自我提升飞轮：经验→反思→学习→应用

## Summaries
<!-- 综合摘要 -->
