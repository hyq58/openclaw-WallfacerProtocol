# SOP S0: Read-Only Probe / 只读探测

> Before touching anything, understand it.

**When:** This is always the first step. Every task starts here.

---

## Procedure

1. **Identify the target.** What files, services, or state will this task affect?
2. **Read current state.** Use read-only tools: `cat`, `ls`, `grep`, `ps`, `systemctl status`.
3. **Confirm assumptions.** Does the target exist? Is it in the expected state?
4. **Identify dependencies.** What else depends on the target? What does the target depend on?
5. **Document findings.** Write a one-paragraph summary of what you found before proceeding.

## Rules

- ❌ No writes during this step
- ❌ No service restarts
- ❌ No configuration changes
- ✅ All findings logged in the task's execution receipt

## Exit Criteria

You may proceed to S1 (Backup) when:
- [ ] Target state is confirmed and documented
- [ ] Blast radius is understood (what breaks if this goes wrong)
- [ ] Rollback path is identified (even if not yet written up)

If you can't answer "what breaks if this fails," stop and ask Sun.
