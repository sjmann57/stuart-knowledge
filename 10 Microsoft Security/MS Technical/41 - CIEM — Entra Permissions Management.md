---
title: "CIEM — Entra Permissions Management"
product: "Microsoft Entra"
day: 41
published: 2026-07-14
source: https://www.linkedin.com/posts/stuartmann_microsoftsecurity-microsoftdefenderforcloud-activity-7482911263208030208-y9c-
impressions: 336
tags:
  - identity
  - entra
  - ciem
  - permissions-management
  - cloud-security
  - least-privilege
---

# CIEM — Entra Permissions Management

## Summary
Cloud Infrastructure Entitlement Management (CIEM) discovers and right-sizes the gap between permissions granted and permissions actually used across multicloud identities. The product branding changed, but the permissions-creep problem it solves did not.

## Key facts
- Discovers identities (human and workload) and their effective permissions across Azure, AWS and GCP.
- Permissions Creep Index highlights identities with far more access than they use.
- Right-sizes to least privilege and supports on-demand/just-enough permissions.
- Complements PIM (privileged roles) by covering broad cloud entitlements.

## Licensing & prerequisites
- Check current licensing/packaging — CIEM has moved between standalone and bundled offerings.

## Practitioner notes / gotchas
- Over-permissioned identities are a primary route on attack paths — this is the tool that quantifies and reduces them.
- Multicloud reality: most estates aren't Microsoft-only, so cross-cloud entitlement visibility matters.

## Microsoft Learn references
- [Cloud infrastructure entitlement management (CIEM) in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/permissions-management)
- [Enable cloud infrastructure entitlement management (CIEM)](https://learn.microsoft.com/azure/defender-for-cloud/enable-permissions-management)
- [Microsoft Entra Permissions Management retirement announcement](https://learn.microsoft.com/entra/fundamentals/whats-new-archive#march-2025)
- [What is Microsoft Defender for Cloud CSPM?](https://learn.microsoft.com/azure/defender-for-cloud/concept-cloud-security-posture-management)
- [Attack path analysis in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/how-to-manage-attack-path)

## Related
- [[06 - Entra ID Privileged Identity Management (PIM)]]
- [[89 - Microsoft Security Exposure Management]]
- [[43 - Microsoft Entra Workload ID]]

## Source
LinkedIn (Day 41): https://www.linkedin.com/posts/stuartmann_microsoftsecurity-microsoftdefenderforcloud-activity-7482911263208030208-y9c-
