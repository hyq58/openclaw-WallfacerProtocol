# SOP S1: Backup / 备份

> Make it reversible before making it different.

**When:** After S0 (Probe), before any write operations.

---

## Procedure

1. **Copy the target** to a timestamped backup location.
   ```bash
   cp -r /path/to/target /path/to/backup/target.$(date +%Y%m%d_%H%M%S).bak
   ```
2. **Verify the backup** — confirm it's readable and complete.
3. **Record the backup path** in the task's execution receipt.
4. **Write the rollback command** — the exact command that restores from this backup.

## Rules

- Backup must be outside the directory being modified
- Backup filename must include a timestamp
- Rollback command must be tested (at minimum, dry-run)

## Exit Criteria

- [ ] Backup exists and is verified
- [ ] Rollback command is written and confirmed executable
- [ ] Backup path recorded in execution receipt
