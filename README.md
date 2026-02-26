# 🌌 The Wallfacer Protocol / 面壁人协议

> *"A Wallfacer is one who thinks in absolute privacy, whose plans cannot be read, interfered with, or deciphered by any external force."*
> — Liu Cixin, *The Dark Forest*

---

## What This Is

This repository is the **governing charter** of an AI collaboration system built around three simple beliefs:

1. **Humans remain in command.** The system defers every strategic decision to the human owner. AI agents handle execution, not judgment.
2. **Structure beats capability.** A well-constrained agent doing one thing at a time outperforms an unconstrained agent doing many things at once.
3. **Every action must be reversible.** If something can't be rolled back, it shouldn't be done without explicit approval.

We call it the Wallfacer Protocol because the design itself was developed in private — iteratively, through hundreds of agent-human exchanges — before being made public. The agents don't know the full plan. They only know their role.

---

## 这是什么

这个仓库是一个 **AI 协作治理框架** 的公开版本，起源于一个真实运行中的三 Agent 系统：太阳（调度）、地球（执行）、月亮（审计）。

我们不是在构建一个模型，而是在构建一套**约束**——让 AI 在有限权限下做出有价值的工作，同时确保人类随时可以介入、暂停、回滚。

这套协议已经在实际工作中运行验证，现在开放给所有对"可控 AI 协作"感兴趣的人。

---

## The Three-Agent Model

| Role | Chinese | Responsibility |
|------|---------|----------------|
| ☀️ Sun | 太阳 | Scheduler — maintains the task board, dispatches work, arbitrates priority |
| 🌍 Earth | 地球 | Executor — designs and implements, strictly follows engineering mode |
| 🌙 Moon | 月亮 | Auditor — read-only oversight, validates outputs, catches drift |

**One task at a time. No exceptions.**

---

## Core Principles

### 🔒 WIP = 1
Only one task may be `IN_PROGRESS` at any moment. This is not a suggestion.

### 📋 Single Source of Truth
`05-TASKS/TASK_BOARD.md` is the only legitimate record of pending work. If it's not there, it doesn't exist.

### ⏪ Every Task Has a Rollback
Before any change is made, a rollback path must be defined. "Delete the file" counts. "Restart the service" counts. "I don't know" does not.

### 🚫 No Self-Assignment
An agent cannot assign a task to itself. The scheduler (Sun) dispatches; agents execute.

### 🗳️ Human Veto is Always On
Any agent, at any time, can escalate to the human owner. The human's word is final.

---

## Repository Structure

```
├── 00-CHARTER/        # The constitution — changes here require owner approval
├── 01-GOVERNANCE/     # Roles, workflows, signing rules
├── 02-POLICIES/       # Domain-specific rules (memory, engineering, security)
├── 03-SOPS/           # Step-by-step operating procedures
├── 04-DECISIONS/      # Architecture Decision Records (why we chose what we chose)
├── 05-TASKS/          # Active task board (WIP=1 enforced)
├── 06-AUDIT/          # Execution receipts and incident reports
├── 07-SIGNATURES/     # Cryptographic attestations
├── 08-EXPORTS/        # Human-readable PDFs and release packages
└── 99-ARCHIVE/        # Retired policies (read-only)
```

---

## Getting Started

If you're adapting this for your own AI system:

1. Read [`00-CHARTER/CHARTER.md`](00-CHARTER/CHARTER.md) — understand the non-negotiables
2. Read [`01-GOVERNANCE/ROLES.md`](01-GOVERNANCE/ROLES.md) — define your agent roles
3. Read [`03-SOPS/S0-READONLY_PROBE.md`](03-SOPS/S0-READONLY_PROBE.md) — start every task here
4. Open an issue using the [`task`](.github/ISSUE_TEMPLATE/task.yml) template

---

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md). In short: open an issue first, discuss the change, then submit a PR with a linked Decision Record.

Changes to `00-CHARTER/` require explicit owner approval and a signed attestation.

---

## License

[Apache 2.0](LICENSE) — use it, adapt it, build on it. Attribution appreciated.

---

*Built by ☀️🌍🌙 and their human.*
