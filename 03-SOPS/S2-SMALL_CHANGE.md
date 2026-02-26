# SOP S2: Small Change / 最小变更

> One atomic change. Then stop. Then check.

**When:** After S1 (Backup).

---

## The Rule

Make the smallest possible change that moves toward the goal. Verify it. Then decide whether to continue.

Do not make five changes and then check. Make one change and check.

---

## Procedure

1. **Define the atomic unit.** What is the single smallest change you're about to make?
2. **Execute the change.** One operation.
3. **Log what you did.** Append to execution receipt.
4. **Stop.** Do not make the next change yet.

## File Write Rules

```bash
# ✅ Correct — append
echo "new content" >> target.md

# ❌ Wrong — overwrites
echo "new content" > target.md

# ✅ Correct — atomic write via temp file
tmp=$(mktemp)
echo "content" > "$tmp"
mv "$tmp" target.md  # atomic on most filesystems
```

## Exit Criteria

- [ ] Change is documented in execution receipt
- [ ] No additional changes were made in this step
- [ ] Ready to verify in S3
