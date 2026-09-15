---
title: "Microsoft Defender for Identity (introduction)"
product: "Microsoft Defender for Identity"
day: 29
published: 
source: https://www.linkedin.com/pulse/entra-id-identity-protection-enabled-same-monitoring-your-stuart-mann-y5hwe
impressions: 662
tags:
  - identity
  - defender-for-identity
  - itdr
  - active-directory
---

# Microsoft Defender for Identity (introduction)

## Summary
Early introduction to Defender for Identity — the ITDR tool many organisations own (via E5/EMS) but haven't deployed. Monitors on-premises Active Directory and hybrid identity for attack behaviour. (Expanded in the Day 90 note.)

## Key facts
- Detects reconnaissance, compromised credentials, lateral movement and domain-dominance behaviour in AD.
- Lightweight sensors on domain controllers (and AD FS/AD CS/Entra Connect) feed the Defender portal.
- Feeds identity signals into Defender XDR and the unified identity risk score.
- Identity security posture assessments surface in Microsoft Secure Score.

## Licensing & prerequisites
- Per-user licence; included in EMS E5, Microsoft 365 E5 and the Defender suites.

## Practitioner notes / gotchas
- 'Licensed but not deployed' is the common state — coverage (a sensor on every DC) is the first job.
- See the fuller Day 90 note for sensor v2.x/v3.x detail and the Entra Connect (MSOL_) assessments.

## Microsoft Learn references
- [Microsoft Defender for Identity overview](https://learn.microsoft.com/en-us/defender-for-identity/what-is)
- [Pilot and deploy Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-xdr/pilot-deploy-defender-identity)
- [Deploy the Defender for Identity sensor v3.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3)
- [Defender for Identity sensor v2.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2)
- [Identity infrastructure security assessments — Unmonitored domain controllers](https://learn.microsoft.com/en-us/defender-for-identity/security-posture-assessments/identity-infrastructure)
- [Microsoft Defender for Identity alerts in Microsoft Defender format](https://learn.microsoft.com/en-us/defender-for-identity/alerts-xdr)

## Related
- [[90 - Microsoft Defender for Identity (ITDR for on-prem AD)]]
- [[07 - Entra ID Identity Protection]]

## Source
LinkedIn (Day 29): https://www.linkedin.com/pulse/entra-id-identity-protection-enabled-same-monitoring-your-stuart-mann-y5hwe
