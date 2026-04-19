# Claude Code

## Overview

Claude Code is Anthropic's autonomous coding agent CLI. It reads files, writes code, runs shell commands, manages git workflows, and spawns subagents autonomously.

**Publisher:** Anthropic
**CLI:** `@anthropic-ai/claude-code` (npm)
**Version:** v2.x required
**Auth:** Browser OAuth (Pro/Max), API key billing, SSO for Enterprise

## Key Modes

### Print Mode (`-p`) — Non-Interactive (Preferred)
```
claude -p 'Add error handling to all API calls in src/' \
  --allowedTools 'Read,Edit' \
  --max-turns 10
```
One-shot task, returns result, exits. No PTY needed.

### Interactive PTY Mode
```
tmux new-session -d -s claude-work
tmux send-keys -t claude-work 'claude' Enter
```
Full conversational REPL. Requires tmux orchestration.

## Hermes Integration

Hermes can delegate to Claude Code via terminal:
```python
terminal(command="claude -p '...'", workdir="/path")
```

Or via PTY + tmux for interactive sessions.

Comparison with Hermes:
- Claude Code is purpose-built for coding
- Hermes is broader (any task) with coding as one domain
- Hermes can orchestrate Claude Code as a specialized subagent

## Key Capabilities

- Read, edit, search files
- Run shell commands
- Git operations (commit, branch, merge)
- Spawn subagents
- Multi-turn conversation in interactive mode
- Tool use with allowlist (`--allowedTools`)

## Relationship to Other Entities

- [[hermes-agent]] — Hermes can delegate tasks to Claude Code
- [[codex]] — similar agent from OpenAI
- [[opencode]] — open-source alternative

## External Links

- Docs: https://code.claude.com/docs/en/cli-reference
