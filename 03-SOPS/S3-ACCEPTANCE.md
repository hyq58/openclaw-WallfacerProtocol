# SOP S3: Acceptance Test / 验收测试

> Prove it works. Don't assume.

---

## Procedure

1. **Run the acceptance test** defined in the task's ACCEPTANCE criteria.
2. **Capture the output.** Paste relevant output into the execution receipt.
3. **Compare against criteria.** Does the output match what was specified?
4. **Submit for Moon review** if the task requires audit sign-off.

## What "Works" Means

- The specific ACCEPTANCE criterion from the task definition is met
- No regressions observed in dependent systems
- Rollback is still possible (S4)

## Failure Handling

If the test fails:
1. Do NOT attempt another change
2. Log the failure in the execution receipt
3. Execute rollback (S4)
4. Report to Sun with: what was tried, what the output was, what was expected
