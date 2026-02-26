# Task Workflow / 任务流转流程

> From proposal to archive — how work moves through the system.

---

## The Lifecycle

```
[Idea / Request]
       │
       ▼
   [PROPOSED] ──► Owner/Sun reviews
       │
  ┌────┴────┐
  │         │
[TODO]   [REJECTED]
  │
  ▼ (Sun dispatches)
[IN_PROGRESS] ── WIP=1 enforced
  │
  ├──► Earth executes
  │       │
  │    [BLOCKED] ──► Sun resolves ──► [IN_PROGRESS]
  │
  ▼
[PENDING_REVIEW] ── Moon audits
  │
  ├──► Fail ──► [IN_PROGRESS] (fix) or [ROLLBACK]
  │
  ▼
[DONE] ──► moved to 05-TASKS/done/
```

---

## State Definitions

| State | Meaning |
|-------|---------|
| `TODO` | Queued, not started. Priority assigned. |
| `IN_PROGRESS` | Exactly one task at a time. Earth is working. |
| `BLOCKED` | Earth cannot proceed without input. Sun must resolve. |
| `PENDING_REVIEW` | Earth complete, Moon reviewing. |
| `DONE` | Accepted by Moon, confirmed by Sun. |
| `ROLLBACK` | Change reversed. Incident filed in `06-AUDIT/incidents/`. |
| `REJECTED` | Task will not be done. Reason recorded. |

---

## Policy Change Workflow

Policy changes (anything in `00-CHARTER/`, `01-GOVERNANCE/`, `02-POLICIES/`) follow a stricter path:

1. **Propose** — Open a `rule-change` issue with the draft text
2. **Review** — 24-hour minimum open discussion
3. **Decision Record** — Write an ADR in `04-DECISIONS/`
4. **Owner Approval** — Explicit sign-off required
5. **Publish** — Merge PR, update `POLICY_INDEX.md`, export PDF
6. **Attest** — Sign the release in `07-SIGNATURES/attestations/`

Charter changes additionally require: old version archived in `99-ARCHIVE/`.

---

## NEXT_ACTION Discipline

Every agent output must end with exactly one `NEXT_ACTION` block:

```
NEXT_ACTION:
  TYPE: EXECUTE | WAIT_OWNER | TERMINATE
  TARGET: <role that acts next>
  TASK: <one sentence>
  ACCEPTANCE: <how we know it's done>
  ROLLBACK: <how we undo it>
```

Outputs without a valid `NEXT_ACTION` are rejected by Sun and must be resubmitted.
