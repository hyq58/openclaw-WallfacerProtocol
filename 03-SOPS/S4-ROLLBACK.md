# SOP S4: Rollback / 回滚

> When things go wrong, this is what you do.

---

## When to Roll Back

- Acceptance test fails
- Unexpected side effects detected
- Sun or Owner instructs rollback
- Moon flags a violation

## Procedure

1. **Execute the rollback command** defined in S1.
   ```bash
   cp /path/to/backup/target.20260226_153000.bak /path/to/target
   ```
2. **Verify rollback success.** Confirm target is in pre-change state.
3. **Log the rollback** in execution receipt with timestamp and reason.
4. **File an incident report** in `06-AUDIT/incidents/` if the rollback was unplanned.
5. **Notify Sun** with a summary of what happened.

## Rules

- ❌ No "partial rollbacks" — either fully rolled back or fully applied
- ❌ No modifying the backup after rollback to cover up the failure
- ✅ Document the root cause even if you don't have time to fix it
