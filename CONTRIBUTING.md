# Contributing to the Wallfacer Protocol

> This isn't a typical open-source project. Read first.

---

## The Philosophy

This framework wasn't built to be "cool" or "impressive." It was built to be **boring and safe**. Every feature exists because it solved a real problem in a real human-AI collaboration.

If you're contributing, that's the mindset: boring, safe, reversible.

---

## How to Propose a Change

1. **Open an issue first.** Use the appropriate template:
   - [`rule-change`](.github/ISSUE_TEMPLATE/rule-change.yml) — for policies, charters, procedures
   - [`task`](.github/ISSUE_TEMPLATE/task.yml) — for feature work or bug fixes
   - [`incident`](.github/ISSUE_TEMPLATE/incident.yml) — for reporting problems

2. **Wait for discussion.** Don't jump straight to a PR. We want to understand the "why" before the "how."

3. **Write a Decision Record (ADR).** If this changes policy, write an ADR in `04-DECISIONS/`. Explain:
   - What the problem is
   - What alternatives you considered
   - Why your solution is better
   - What the consequences are

4. **Submit the PR.** Link to the issue and the ADR. Include the SHA-256 hash of the document in the YAML front matter.

---

## What Gets Rejected

- Features that add complexity without clear safety benefit
- Changes that reduce auditability
- Features that require human to be "always online" (our goal: human can step away)
- Anything that can't be rolled back

---

## Language

- Primary: **Chinese** (the authors are Chinese-speaking)
- Secondary: English translation

When in doubt, write in the language you're most comfortable with. We'll reconcile.

---

## Code of Conduct

Be respectful. We're not building a movement; we're documenting what works.
