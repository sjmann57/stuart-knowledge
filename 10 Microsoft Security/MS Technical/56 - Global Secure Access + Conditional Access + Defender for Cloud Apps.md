---
title: "Global Secure Access + Conditional Access + Defender for Cloud Apps"
product: "Microsoft Entra / GSA"
day: 56
published: 2026-07-31
source: https://www.linkedin.com/pulse/global-secure-access-conditional-defender-cloud-apps-one-stuart-mann-q7fhe/
impressions: 183
tags:
  - gsa
  - conditional-access
  - mdca
  - zero-trust
  - integration
---

# Global Secure Access + Conditional Access + Defender for Cloud Apps

## Summary
The unified Zero Trust access model: GSA (network edge) + Conditional Access (policy engine) + Defender for Cloud Apps (SaaS visibility and session control) working together so access decisions use identity, device, network and app signals as one.

## Key facts
- GSA routes and secures the traffic; Conditional Access decides; Defender for Cloud Apps controls the session.
- Universal Conditional Access extends CA to network-level access via GSA.
- Conditional Access App Control (from MDCA) enforces in-session controls (block download, monitor).
- Together they close the gap between identity policy and network/SaaS enforcement.

## Licensing & prerequisites
- Combination of Entra P1/P2, Global Secure Access and Defender for Cloud Apps licensing.

## Practitioner notes / gotchas
- Integration is the point — each product is stronger as part of the model than alone.
- A concrete example of 'the architecture is the lines between the boxes' (Day 95).

## Microsoft Learn references
- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
- [Conditional Access app control — Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-intro-aad)
- [Compliant network check in Conditional Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-compliant-network)
- [Global Secure Access logs and monitoring](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-global-secure-access-logs-monitoring)
- [Universal Continuous Access Evaluation](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-universal-continuous-access-evaluation)

## Related
- [[53 - Microsoft Global Secure Access (Security Service Edge)]]
- [[47 - Microsoft Defender for Cloud Apps]]
- [[95 - How the Microsoft security stack fits together — the architect's view]]

## Source
LinkedIn (Day 56): https://www.linkedin.com/pulse/global-secure-access-conditional-defender-cloud-apps-one-stuart-mann-q7fhe/
