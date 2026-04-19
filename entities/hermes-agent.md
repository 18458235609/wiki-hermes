# Hermes Agent

## Overview

Hermes Agent is an open-source AI agent framework by [Nous Research](https://github.com/NousResearch). It runs in the terminal, messaging platforms (Telegram, Discord, Slack, etc.), and IDEs. It belongs to the same category as Claude Code, Codex, and OpenClaw — autonomous coding and task-execution agents.

**GitHub:** ~30k stars (as of 2026-04)
**License:** MIT
**Repository:** nousresearch/hermes-agent

## Key Features

- **Self-improving through skills** — learns from experience by saving reusable procedures as skill documents
- **Persistent memory** — cross-session memory of user preferences, environment, lessons learned
- **Multi-platform gateway** — Telegram, Discord, Slack, WhatsApp, Signal, Matrix, Email, WeChat, and more
- **Provider-agnostic** — works with OpenRouter, Anthropic, OpenAI, DeepSeek, local models, 20+ providers
- **Profiles** — multiple independent instances with isolated configs and memory
- **Extensible** — plugins, MCP servers, custom tools, webhooks, cron scheduling

## Architecture

```
Hermes Agent
├── CLI (interactive terminal chat)
├── Gateway (messaging platforms)
├── AIAgent (core conversation loop)
├── Toolsets (terminal, file, web, browser, delegation, etc.)
├── Skill System (74 skills installed in this environment)
├── Memory System (cross-session persistence)
└── Session Store (SQLite-based conversation storage)
```

## Config

- `~/.hermes/config.yaml` — main configuration
- `~/.hermes/.env` — API keys and secrets
- `~/.hermes/skills/` — installed skills
- `~/.hermes/sessions/` — session transcripts
- `~/.hermes/logs/` — gateway and error logs

## Relationship to Other Entities

- [[hermes-agent]] (this wiki) documents the methods Hermes uses to evolve
- [[claude-code]] — similar agent from Anthropic; Hermes can delegate to Claude Code
- [[codex]] — OpenAI's coding agent
- [[opencode]] — OpenCode CLI agent
- [[autogen]] — Microsoft's multi-agent framework (different approach: conversation-based)
- [[metagpt]] — multi-agent framework with SOP pipeline

## External Links

- Docs: https://hermes-agent.nousresearch.com/docs/
- GitHub: https://github.com/NousResearch/hermes-agent
