---
title: "Microsoft Defender XDR — unified incidents & automatic attack disruption"
product: "Microsoft Defender XDR"
day: 91
published: 2026-09-03
source: https://lnkd.in/p/eSMrri5v
impressions: 480
tags:
  - defender
  - xdr
  - secops
  - attack-disruption
  - incidents
  - unified-secops
---

# Microsoft Defender XDR — unified incidents & automatic attack disruption

## Summary
Defender XDR is the correlation layer that turns separate alerts from identity, endpoint, email and cloud into a single attack story — and automatic attack disruption can contain a high-confidence attack in progress, at the incident level, while analysts catch up.

## Key facts
- Alert = single detection; incident = container of correlated alerts telling the full attack story (AI correlation engine).
- Correlates Defender for Endpoint/Office 365/Identity/Cloud Apps, MDVM, Defender for Cloud, Entra ID Protection, Purview DLP/IRM, Exposure Management — plus external via Sentinel & Defender for Cloud.
- Automatic attack disruption: correlate to a high-confidence incident → identify attacker-controlled assets → auto-contain (isolate device, disable/contain user, revoke session, contain token/IP/OAuth app).
- Response scope includes Entra ID + AD actions; preview for Okta and AWS via Sentinel.
- Human control preserved: Attack Disruption tag, Action center, full logging, release/re-enable, exclusion policies (kept minimal).

## Licensing & prerequisites
- Correlates only licensed/provisioned products. MDI-based disruption needs DC auditing + action accounts (v3.x uses LocalSystem; v2.x can use gMSA).

## Practitioner notes / gotchas
- Attack disruption's ~3-minute ransomware containment is real but depends on the underlying products being deployed — it can't disable an account on a DC with no sensor.
- Exclusion discipline: ask 'which exceptions are genuinely necessary and what compensating response do we have', not 'how do we stop automation touching anything'.

## Microsoft Learn references
- [What is Microsoft Defender XDR?](https://learn.microsoft.com/defender-xdr/microsoft-365-defender)
- [Incidents and alerts in the Microsoft Defender portal](https://learn.microsoft.com/defender-xdr/incidents-overview)
- [Automatic attack disruption in Microsoft Defender](https://learn.microsoft.com/defender-xdr/automatic-attack-disruption)
- [Configure automatic attack disruption in Microsoft Defender XDR](https://learn.microsoft.com/defender-xdr/configure-attack-disruption)
- [Microsoft Defender XDR integration with Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/microsoft-365-defender-sentinel-integration)

## Related
- [[90 - Microsoft Defender for Identity (ITDR for on-prem AD)]]
- [[89 - Microsoft Security Exposure Management]]
- [[81 - Microsoft Sentinel — the agentic defence platform]]
- [[98 - Where Microsoft security is heading — the agentic SOC]]

## Source
LinkedIn (Day 91): https://lnkd.in/p/eSMrri5v
