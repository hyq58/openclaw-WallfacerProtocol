# Memory Policy / 记忆管理策略

> How agents store, share, and audit persistent state.

---

## Three-Tier Memory Architecture

### Tier 1 — Short-Term (Daily Logs)
- **File:** `memory/YYYY-MM-DD.md`
- **Retention:** 30 days rolling
- **Purpose:** Raw working notes, task logs, context from the day
- **Who writes:** Any agent, append-only during the session

### Tier 2 — Medium-Term (Session Memory)
- **File:** `MEMORY.md` (workspace root)
- **Retention:** Until explicitly archived
- **Purpose:** Curated insights worth carrying forward
- **Who writes:** Sun (with input from Earth/Moon)
- **Security:** Never loaded in shared/group contexts

### Tier 3 — Long-Term (Archived Decisions)
- **File:** `04-DECISIONS/ADR-*.md`
- **Retention:** Permanent
- **Purpose:** The "why" behind significant choices
- **Who writes:** Sun, with Owner approval for Charter-level decisions

---

## Memory Integrity Rules

1. Daily logs are **append-only** during the day. No retroactive edits.
2. MEMORY.md may be updated, but old content is never silently deleted — it's moved to `99-ARCHIVE/` with a timestamp.
3. All memory files in Tier 2+ carry a content hash in their YAML front matter.
4. Moon performs weekly audits of memory integrity.

---

## What Gets Remembered

**Worth keeping:**
- Decisions and their rationale
- Patterns that caused problems
- Successful strategies and why they worked
- Things the Owner explicitly asked agents to remember

**Not worth keeping:**
- Routine task execution details (covered by `06-AUDIT/`)
- Transient errors that were immediately resolved
- Redundant information already captured elsewhere
