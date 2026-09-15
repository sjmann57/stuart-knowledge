---
title: "Intune device compliance"
product: "Microsoft Intune"
day: 28
published: 
source: https://www.linkedin.com/pulse/your-conditional-access-policy-says-require-device-marked-stuart-mann-jcc7e
impressions: 183
tags:
  - intune
  - device-compliance
  - conditional-access
  - endpoint
  - zero-trust
---

# Intune device compliance

## Summary
What a Conditional Access 'require compliant device' control is actually enforcing depends entirely on the Intune compliance policy behind it — the policy defines what 'compliant' means.

## Key facts
- Compliance policies define rules: encryption, OS version, jailbreak/root, threat level, firewall, etc.
- Device compliance state is a Conditional Access signal (require compliant / hybrid-joined device).
- Defender for Endpoint feeds device risk into compliance (risk-based conditional access).
- Non-compliant devices can be blocked from resources or given remediation.

## Licensing & prerequisites
- Microsoft Intune (Microsoft 365 E3/E5, EMS); Defender for Endpoint for risk-based compliance.

## Practitioner notes / gotchas
- 'Require compliant device' is only as strong as the compliance policy's rules — an empty policy protects nothing.
- Identity + device context beats identity alone (ties to Conditional Access, Day 8).

## Microsoft Learn references
- [Device compliance policies overview — Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/device-compliance-get-started)
- [Windows compliance settings — Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/compliance-policy-create-windows)
- [Require compliant device — Conditional Access grant control](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-grant#require-device-to-be-marked-as-compliant)
- [Use security baselines to configure Windows devices — Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/security-baselines)
- [Monitor Intune device compliance policies](https://learn.microsoft.com/intune/device-security/compliance/monitor-policy)

## Related
- [[08 - Conditional Access]]
- [[90 - Microsoft Defender for Identity (ITDR for on-prem AD)]]

## Source
LinkedIn (Day 28): https://www.linkedin.com/pulse/your-conditional-access-policy-says-require-device-marked-stuart-mann-jcc7e
