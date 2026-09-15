---
title: "Entra ID Identity Protection"
product: "Microsoft Entra"
day: 7
published: 2026-06-10
source: https://www.linkedin.com/posts/stuartmann_microsoftentra-identityprotection-zerotrust-activity-7470150989069860864-333p
impressions: 142
tags:
  - identity
  - entra
  - identity-protection
  - risk
  - zero-trust
---

# Entra ID Identity Protection

## Summary
Identity Protection detects identity risk (risky sign-ins and risky users) using Microsoft's signal and threat intelligence, and feeds that risk into Conditional Access for automated response. The signals are only useful if someone is reading and acting on them.

## Key facts
- Sign-in risk (this authentication) vs user risk (the account overall).
- Detections include atypical travel, unfamiliar sign-in properties, anonymous IP, leaked credentials, password spray, anomalous token.
- Risk-based Conditional Access can require MFA/password change or block based on risk level.
- Aggregates into the unified identity risk score alongside Defender for Identity.

## Licensing & prerequisites
- Full risk-based policies and detections require Microsoft Entra ID P2 (or Microsoft 365 E5).

## Practitioner notes / gotchas
- Common gap: risk is detected but no risk-based Conditional Access is enforcing on it — detection without action.
- Tune to blocking/enforce mode deliberately; monitoring-only leaves the value on the table.

## Microsoft Learn references
- [What is Microsoft Entra ID Protection?](https://learn.microsoft.com/entra/id-protection/overview-identity-protection)

## Related
- [[06 - Entra ID Privileged Identity Management (PIM)]]
- [[08 - Conditional Access]]
- [[90 - Microsoft Defender for Identity (ITDR for on-prem AD)]]

## Source
LinkedIn (Day 7): https://www.linkedin.com/posts/stuartmann_microsoftentra-identityprotection-zerotrust-activity-7470150989069860864-333p
