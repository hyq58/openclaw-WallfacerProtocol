# Security Policy / 安全策略

---

## Reporting a Vulnerability

If you find a security issue in this framework or the systems built on it, please **do not open a public issue**. Instead, email the maintainer directly (see `SECURITY.md` in the repo root).

We aim to respond within 48 hours.

---

## System Boundaries / 系统禁区

The following paths and operations are off-limits to all agents:

| Boundary | Reason |
|----------|--------|
| Platform configuration files (e.g., `openclaw.json`) | System integrity |
| LaunchAgent plists in `~/Library/LaunchAgents/` | Persistence control |
| Guard directories | Tamper detection |
| Token / API key files | Credential protection |
| Any file outside the declared workspace root | Scope control |

Agents that attempt to access these paths must self-halt and report to Sun.

---

## Data Handling

1. **No exfiltration.** Agent outputs may not contain private data (API keys, personal identifiers, credentials).
2. **Logs are sanitized.** Audit receipts strip sensitive fields before writing.
3. **PDFs are verified.** Exported documents are hashed before publication.

---

## Incident Response

If a security violation is detected:

```
1. Agent that detects it halts all operations
2. Files incident report in 06-AUDIT/incidents/
3. Notifies Sun via mailbox (priority: 🔴)
4. Sun notifies Owner
5. Owner decides: patch, rollback, or emergency stop
```

No agent self-remedies a security violation without Owner authorization.
