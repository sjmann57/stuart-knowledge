---
title: "Microsoft Global Secure Access (Security Service Edge)"
product: "Microsoft Entra / GSA"
day: 53
published: 2026-07-28
source: https://www.linkedin.com/pulse/microsoft-global-secure-access-moving-beyond-vpn-stuart-mann-c3kme/
impressions: 
tags:
  - gsa
  - sse
  - ztna
  - network-security
  - secure-access
---

# Microsoft Global Secure Access (Security Service Edge)

## Summary
Global Secure Access (GSA) is Microsoft's Security Service Edge — the umbrella over Entra Internet Access and Entra Private Access, delivering identity-centric secure access to internet, SaaS and private resources.

## Key facts
- Umbrella for Entra Internet Access (SWG) and Entra Private Access (ZTNA).
- Identity-aware: access decisions tied to Entra identity and Conditional Access rather than network location.
- Client and per-app connectors route traffic through Microsoft's edge.
- Universal tenant restrictions and source-IP restoration are notable capabilities.

## Licensing & prerequisites
- Licensing via Global Secure Access / Entra Suite; Internet and Private Access have their own SKUs.

## Practitioner notes / gotchas
- SSE reframes 'access' around identity, not the perimeter — the network-pillar expression of Zero Trust.
- See Days 54–56 for the two halves and the unified access model.

## Microsoft Learn references
- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
- [Global Secure Access traffic forwarding profiles](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-forwarding)
- [Learn about Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-private-access)
- [Universal Tenant Restrictions](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-universal-tenant-restrictions)
- [Compliant Network check in Conditional Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-compliant-network)
- [Shadow AI discovery](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-shadow-ai-discovery)
- [Quickstart: Access the Global Secure Access area of the Microsoft Entra admin centre](https://learn.microsoft.com/en-us/entra/global-secure-access/quickstart-access-admin-center)

## Related
- [[54 - Microsoft Entra Private Access (ZTNA - VPN replacement)]]
- [[55 - Microsoft Entra Internet Access (identity-centric SWG)]]
- [[56 - Global Secure Access + Conditional Access + Defender for Cloud Apps]]

## Source
LinkedIn (Day 53): https://www.linkedin.com/pulse/microsoft-global-secure-access-moving-beyond-vpn-stuart-mann-c3kme/
