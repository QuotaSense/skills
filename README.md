# QuotaSense skills

Agent skills and hooks for [QuotaSense](https://quotasense.com), the app that shows your AI coding usage and limits across machines.

## agent-log

Lets coding agents write one short line to the Log card in the QuotaSense app: when a long task starts or ends, when they switch model, or when they stop to wait on a usage limit.

Needs QuotaSense installed, with `"agent_log": true` in its `config.json`. When it is off, the command does nothing.

- **Claude Code skill:** copy `agent-log/SKILL.md` to `~/.claude/skills/agent-log/SKILL.md`.
- **Claude Code hooks:** merge `agent-log/hooks.json` into the `hooks` section of `~/.claude/settings.json`. They log "context compacted" and "session ended, N tokens".
- **Other agents (Codex and others):** add the text of `agent-log/AGENTS.md` to your `AGENTS.md`.

The log never holds prompt text, replies, file contents, secrets or project names. Lines are at most 80 characters.

## Licence

MIT. See `LICENSE`.
