---
title: "What's new in Microsoft Entra — passkeys by default, Tenant Governance, Backup & Recovery"
product: "Microsoft Entra"
day: 82
published: 2026-08-25
source: https://www.linkedin.com/pulse/whats-new-microsoft-entra-passkeys-default-tenant-governance-mann-ptgee/
impressions: 383
tags:
  - identity
  - entra
  - passkeys
  - tenant-governance
  - backup-recovery
  - whats-new
---

# What's new in Microsoft Entra — passkeys by default, Tenant Governance, Backup & Recovery

## Summary
Three significant Entra additions: passkeys becoming the default sign-in experience (with SMS/voice retirement dates), Tenant Governance for multi-tenant/shadow-IT sprawl, and Entra Backup & Recovery to roll back directory objects after a bad change or compromise.

## Key facts
- Passkeys by default: from 1 Sep 2026 SMS/voice users auto-enabled for passkeys; from 1 Feb 2027 Microsoft-provided SMS/voice retired (blocking passkey registration, no opt-out).
- Customer-managed telecom providers available via the Microsoft Security Store (config from ~30 Oct 2026) for genuine regulatory needs.
- Tenant Governance: related-tenant discovery (B2B, multitenant app, shared billing signals) + cross-tenant delegated administration via GDAP + governance policy templates.
- Backup & Recovery (preview): always-on daily backup of users, groups, apps, service principals, Conditional Access policies, named locations, Agent IDs, auth/authz policy; ~7-day retention; backups can't be disabled/deleted by any admin.

## Licensing & prerequisites
- Passkeys: Entra ID (baseline). Tenant Governance: free/basic capabilities, but cross-tenant delegated admin and related-tenant discovery need P1/P2 or Entra ID Governance. Backup & Recovery: Entra ID P1/P2; workforce tenants only.
- Backup & Recovery is in preview — test before relying on it; does not recover hard-deleted objects.

## Practitioner notes / gotchas
- Two dates to diarise: 1 Sep 2026 and 1 Feb 2027 for the SMS/voice retirement.
- Backups that no admin (even Global Admin) can delete is the right design against an attacker with admin rights.

## Microsoft Learn references
- [Passkeys by default and retirement of Microsoft-provided SMS and voice authentication](https://learn.microsoft.com/entra/identity/authentication/concept-sms-voice-retirement)
- [What is Microsoft Entra Tenant Governance?](https://learn.microsoft.com/entra/id-governance/tenant-governance/overview)
- [Microsoft Entra Backup and Recovery overview (Preview)](https://learn.microsoft.com/entra/backup/overview)
- [Microsoft Entra releases and announcements (What's new)](https://learn.microsoft.com/entra/fundamentals/whats-new)
- [Microsoft Entra authentication overview — phishing-resistant methods](https://learn.microsoft.com/entra/identity/authentication/overview-authentication)

## Related
- [[09 - Authentication Strengths (phishing-resistant MFA)]]
- [[16 - Passkeys vs physical FIDO keys]]
- [[68 - Microsoft Entra Agent ID]]

## Source
LinkedIn (Day 82): https://www.linkedin.com/pulse/whats-new-microsoft-entra-passkeys-default-tenant-governance-mann-ptgee/
