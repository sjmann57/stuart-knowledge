---
title: "Microsoft Defender for Identity (ITDR for on-prem AD)"
product: "Microsoft Defender for Identity"
day: 90
published: 2026-09-02
source: https://lnkd.in/p/ejUPm7Ub
impressions: 662
tags:
  - identity
  - defender-for-identity
  - itdr
  - active-directory
  - hybrid-identity
  - secops
---

# Microsoft Defender for Identity (ITDR for on-prem AD)

## Summary
Defender for Identity is Microsoft's ITDR for hybrid identity — it watches the on-premises Active Directory ground attackers still target, doing both identity security posture management (ISPM) and detection/response across the attack lifecycle.

## Key facts
- Two jobs: posture assessments (ISPM, surfaced in Secure Score) and detection/response.
- Attack stages detected: reconnaissance, compromised credentials, lateral movement, AD domain dominance (DCShadow, malicious replication, Golden Ticket).
- Lightweight sensors on DCs (incl. RODCs), AD FS, AD CS, Entra Connect; only required signals sent to cloud.
- Sensor v3.x (2026) supports DCs running Entra Connect roles and requires Defender for Endpoint onboarded; v2.x still needed for standalone AD FS/AD CS/Entra Connect servers — mixed deployments supported.
- Hybrid posture assessments flag the Entra Connect connector (MSOL_) account: rotate >90-day password, remove excess replication permissions, no Domain/Enterprise Admin as connector account.
- Feeds Defender XDR + Exposure Management (lateral movement paths); unified identity risk score combines MDI + Entra ID Protection.
- Coverage & maturity model: Connected → Protected → Fortified → Resilient.

## Licensing & prerequisites
- Per-user licence; EMS E5, Microsoft 365 E5, Defender suites. ATA reached end of extended support 14 Jan 2026 — migrate to MDI.

## Practitioner notes / gotchas
- Start with coverage (a sensor on every DC), not the alerts — an unmonitored DC is a blind spot the attack-path tool can't see.
- MDI vs Entra ID Protection: MDI = on-prem + synced accounts; Entra ID Protection = cloud-only Entra accounts (complementary).

## Microsoft Learn references
- [Microsoft Defender for Identity overview](https://learn.microsoft.com/defender-for-identity/what-is)
- [Defender for Identity deployment overview](https://learn.microsoft.com/defender-for-identity/deploy/deploy-defender-identity)
- [Defender for Identity security posture assessments](https://learn.microsoft.com/defender-for-identity/security-assessment)
- [What is Identity Security?](https://learn.microsoft.com/defender-xdr/identity-security/identity-security-overview)
- [What's new in Microsoft Defender for Identity](https://learn.microsoft.com/defender-for-identity/whats-new)

## Related
- [[29 - Microsoft Defender for Identity (introduction)]]
- [[89 - Microsoft Security Exposure Management]]
- [[91 - Microsoft Defender XDR — unified incidents & automatic attack disruption]]

## Source
LinkedIn (Day 90): https://lnkd.in/p/ejUPm7Ub
