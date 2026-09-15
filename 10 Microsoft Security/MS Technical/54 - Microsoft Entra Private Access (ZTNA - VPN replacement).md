---
title: "Microsoft Entra Private Access (ZTNA / VPN replacement)"
product: "Microsoft Entra / GSA"
day: 54
published: 2026-07-29
source: https://www.linkedin.com/pulse/microsoft-entra-private-access-replacing-vpn-zero-trust-stuart-mann-svrve/
impressions: 151
tags:
  - gsa
  - private-access
  - ztna
  - vpn-replacement
  - zero-trust
---

# Microsoft Entra Private Access (ZTNA / VPN replacement)

## Summary
Entra Private Access provides identity-centric Zero Trust Network Access to private apps and resources — granular per-application access instead of the broad network-level trust a traditional VPN grants.

## Key facts
- Per-app access governed by Conditional Access, not a flat network tunnel.
- Connectors publish private apps without inbound firewall exposure.
- Reduces lateral movement risk versus full-network VPN access.
- Microsoft positions it explicitly as modernising VPN with identity-aware ZTNA.

## Licensing & prerequisites
- Global Secure Access / Entra Private Access licensing; connector infrastructure required.

## Practitioner notes / gotchas
- Least privilege applied to network access — the same Zero Trust principle in a different domain.
- A strong VPN-replacement story where lateral movement is the concern.

## Microsoft Learn references
- [Learn about Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-private-access)
- [Microsoft Entra private network connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-connectors)
- [Tutorial: VPN replacement with Quick Access](https://learn.microsoft.com/en-us/entra/global-secure-access/tutorial-private-access-vpn-replacement)
- [Use Kerberos for single sign-on (SSO) with Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-kerberos-sso)
- [How to configure Quick Access for Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-quick-access)

## Related
- [[53 - Microsoft Global Secure Access (Security Service Edge)]]
- [[55 - Microsoft Entra Internet Access (identity-centric SWG)]]
- [[76 - Zero Trust for identity — the most foundational pillar]]

## Source
LinkedIn (Day 54): https://www.linkedin.com/pulse/microsoft-entra-private-access-replacing-vpn-zero-trust-stuart-mann-svrve/
