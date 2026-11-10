---
name: agent-log
description: Write one short line to the QuotaSense Log (Insights tab) when you start a long task, switch model, or stop to wait on a usage limit. Use `quotasense log`. Never put secrets, prompt text, file contents or project names in it.
---

# QuotaSense agent log

`quotasense log` adds one line to the Log card on the QuotaSense phone app. The owner reads it to see what the agents on each machine did and when. It is off unless the owner set `"agent_log": true` in QuotaSense's config.json. When it is off, the command prints one note and exits 0. Do not try to turn it on.

## When to log

- You start a long task (many steps, or longer than about 15 minutes): `--kind milestone`.
- You finish that long task: `--kind milestone`.
- You switch model or provider, or hand work to another agent: `--kind switch`.
- You stop to wait for a 5-hour or weekly limit to reset: `--kind note`.

Do not log routine steps, every tool call, or every reply. The command keeps at most 20 lines per machine per hour and drops the rest.

## Command

```
quotasense log --kind milestone "started: migrate billing tests"
quotasense log --kind switch "opus to sonnet for the test fixes"
quotasense log "waiting on the weekly limit, resets Thu 15:48"
```

If `quotasense` is not on PATH, run `python3 -m quotasense log ...` from the QuotaSense checkout.

## Rules

- 80 characters at most. Longer text is cut. Whitespace is collapsed to single spaces.
- Never include secrets, keys, tokens, passwords, URLs with credentials or e-mail addresses.
- Never include the user's prompt text, your replies, file contents, code or diffs.
- Never include project, repository, customer or person names. The Log already shows the machine.
- Describe the kind of work in a few plain words, for example "started: refactor of the test suite".
- The command never fails a task. Do not retry it and do not report its output to the user.
