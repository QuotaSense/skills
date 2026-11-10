## QuotaSense agent log

When you start or finish a long task, switch model, or stop to wait on a usage limit, write one line to the QuotaSense Log:

```
quotasense log --kind milestone "started: refactor of the test suite"
quotasense log --kind switch "gpt-5 to gpt-5-mini for the small fixes"
quotasense log "waiting on the 5h limit"
```

Kinds: `note` (default), `milestone`, `switch`. At most 80 characters. Never include secrets, prompt text, replies, file contents or project names. Do not log routine steps (20 lines per machine per hour at most; extras are dropped). The command exits 0 even when the log is off, so never retry it.
