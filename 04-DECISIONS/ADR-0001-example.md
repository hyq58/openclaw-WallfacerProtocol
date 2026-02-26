# ADR-0001: Three-Agent Architecture

**Status:** Accepted  
**Date:** 2026-02-25  
**Deciders:** Owner + Sun

---

## Context

We needed a way to deploy AI agents with meaningful autonomy while keeping human oversight practical — not requiring the human to review every action, but ensuring the human could intervene at any point.

The naive approach (one agent, full access, human reviews everything) doesn't scale. The opposite extreme (agents fully autonomous, no oversight) isn't safe.

## Decision

We adopted a three-role separation:

- **Scheduler (Sun):** Owns priority. Doesn't execute.
- **Executor (Earth):** Executes. Doesn't self-assign.
- **Auditor (Moon):** Reviews. Doesn't execute.

This mirrors patterns from human organizations: a project manager, an engineer, and a QA reviewer. Each has a clear lane. No lane-crossing.

## Consequences

**Positive:**
- Clear accountability — every failure can be traced to a role
- Reduced blast radius — no single agent can both approve and execute
- Auditor independence — Moon's value comes from not being involved in execution

**Negative:**
- Slower throughput — WIP=1 means no parallelism
- More overhead — every task needs dispatch, execution, and audit steps

## Why WIP=1

Multiple concurrent tasks create ambiguous state. When two things are "in progress," it's never clear which one takes priority when a conflict arises. Enforcing WIP=1 forces explicit priority decisions before they become emergencies.

## Alternatives Considered

- **Two-agent (Scheduler + Executor):** Rejected — no independent audit layer
- **Full parallel execution:** Rejected — too much state to track, ownership ambiguous
- **Human-in-the-loop for every step:** Rejected — defeats the purpose of automation
