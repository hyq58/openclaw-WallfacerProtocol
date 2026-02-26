# Signing Rules / 电子凭证规则

> How we prove that a document was reviewed, approved, and hasn't been tampered with.

---

## Why Signing Matters

AI agents can modify files. Humans can modify files. Without a verification mechanism, you can't tell if the policy you're reading is the one that was approved, or a drift from it.

Signing is our answer to that problem. It's lightweight, auditable, and doesn't require a PKI to get started.

---

## The Two-Level System

### Level 1 — Content Hash (Required for all policies)

Every policy document carries a SHA-256 hash of its content in a YAML front matter block:

```yaml
---
doc_id: POL-006
version: "1.0"
status: approved
content_sha256: "sha256:abc123..."
approved_by: "Owner"
approved_at: "2026-02-26"
---
```

The hash covers the document body *excluding* the front matter. This means you can update metadata (e.g., `reviewed_at`) without invalidating the content hash.

To verify: `sha256sum <file>` and compare against `content_sha256`.

### Level 2 — Release Attestation (Required for Charter amendments)

Major releases use a detached signature file stored in `07-SIGNATURES/attestations/`:

```
attestations/
  POL-001-v1.0.sig    # GPG or SSH signature over the PDF export
  POL-001-v1.0.sha256 # Hash file that was signed
```

Release log is maintained in `07-SIGNATURES/policy_release_log.csv`.

---

## Signing Workflow

```
1. Author completes document
2. Generate hash: sha256sum document.md > document.sha256
3. Update front matter with hash
4. PR is reviewed and approved
5. On merge: CI workflow (verify_sign.yml) validates hash
6. For Charter: Owner signs the PDF export
7. Store attestation in 07-SIGNATURES/attestations/
```

---

## Hash Invalidation Policy

If a document's hash doesn't match:
1. The document is flagged as `UNVERIFIED`
2. Moon is notified
3. Earth investigates the cause
4. Sun decides: re-approve with new hash, or rollback

An unverified policy is not enforceable until re-signed.
