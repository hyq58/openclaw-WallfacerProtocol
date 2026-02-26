# SOP S5: Watchman Wake / 守夜人唤醒

> When the guardian service goes silent, this is how you bring it back.

---

## What is the Watchman?

The Watchman is the background service that monitors agent health, triggers scheduled tasks, and ensures the event-driven architecture stays alive. If it stops, agents go dark.

## Detection

Signs the Watchman has stopped:
- Agent heartbeats missing for >30 minutes
- Trigger files (`*.trigger`) not being processed
- Mailbox messages going unanswered

## Wake Procedure

```bash
# 1. Check current state
openclaw gateway status

# 2. If stopped, restart
openclaw gateway restart

# 3. Verify agents are responsive
touch ~/.openclaw/agents/sun/agent/.trigger
# Expect: response in mailbox within 60 seconds

# 4. If restart fails, escalate to Owner
```

## Escalation

If the Watchman cannot be restarted:
1. Log the failure in `06-AUDIT/incidents/`
2. Notify Owner via alternative channel (e.g., direct message)
3. Do not attempt further automated fixes — wait for human intervention
