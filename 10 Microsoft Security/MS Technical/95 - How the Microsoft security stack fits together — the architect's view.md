---
title: "How the Microsoft security stack fits together — the architect's view"
product: "Security Architecture"
day: 95
published: 2026-09-07
source: https://lnkd.in/p/eiwEcSU5
impressions: 914
tags:
  - architecture
  - zero-trust
  - identity
  - secops
  - ai-security
  - synthesis
  - moc
---

# How the Microsoft security stack fits together — the architect's view

## Summary
The synthesis note: the whole stack as layers, not a product list. Zero Trust (strategy) → identity (control plane) → devices/data/apps/network (pillars) → SecOps (connective layer) → AI across everything. The architecture is the lines between the boxes.

## Key facts
- Strategy on top: Zero Trust (verify explicitly, least privilege, assume breach).
- Identity as control plane: Entra (Conditional Access, PIM, Identity Protection, Governance, Agent ID).
- Protected assets: devices (Intune/MDE), data (Purview), apps & cloud (Defender for Cloud/MDCA), network (GSA).
- Connective layer (unified SecOps in the Defender portal): Exposure Management, Defender XDR + attack disruption, Sentinel (SIEM/SOAR), Security Copilot.
- AI runs across every layer: secure AI (Agent ID, Purview, Defender) and AI that secures (Copilot agents).

## Licensing & prerequisites
- Correlation/coverage depends on the products licensed, deployed and connected.

## Practitioner notes / gotchas
- The value is in the connections, not the individual products — most orgs own the stack but in silos.
- Recurring thread of the whole series: the clever layer on top only pays off if the foundations underneath are done properly.

## Microsoft Learn references
- [Zero Trust overview](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview)
- [Zero Trust security in Azure](https://learn.microsoft.com/en-us/azure/security/fundamentals/zero-trust)
- [What is Microsoft Entra Agent ID?](https://learn.microsoft.com/en-us/entra/agent-id/what-is-microsoft-entra-agent-id)
- [DSPM deployment guidance](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-step1)
- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
- [Unified security operations in the Defender portal](https://learn.microsoft.com/en-us/unified-secops/overview-unified-security)

## Related
- [[74 - Zero Trust foundations — three principles, seven pillars]]
- [[91 - Microsoft Defender XDR — unified incidents & automatic attack disruption]]
- [[89 - Microsoft Security Exposure Management]]
- [[98 - Where Microsoft security is heading — the agentic SOC]]

## Source
LinkedIn (Day 95): https://lnkd.in/p/eiwEcSU5
