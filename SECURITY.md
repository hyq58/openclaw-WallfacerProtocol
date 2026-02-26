# Security Policy / 安全策略

---

## Reporting Security Issues

**Do NOT open a public issue for security vulnerabilities.**

Email the maintainer directly: the owner's email is on their GitHub profile.

We aim to respond within 48 hours.

---

## Scope

This framework governs AI agent behavior. The security model assumes:
- The AI agents have filesystem access within a defined workspace
- The human owner retains the ability to stop, pause, or terminate agents at any time
- Agents cannot self-replicate or persist without human authorization

---

## What We Consider a Security Issue

- Privilege escalation (agent gaining permissions it shouldn't have)
- Data exfiltration (sensitive data leaving the workspace)
- Persistence bypass (agent creating unauthorized startup items)
- Audit tampering (modifying logs after the fact)

---

## Response Timeline

| Severity | Response Time | Resolution Target |
|----------|---------------|-------------------|
| Critical | 24 hours | 7 days |
| High | 48 hours | 14 days |
| Medium | 1 week | 30 days |
| Low | 1 month | 90 days |
