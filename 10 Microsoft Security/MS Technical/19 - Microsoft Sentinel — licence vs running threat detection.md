---
title: "Microsoft Sentinel — licence vs running threat detection"
product: "Microsoft Sentinel"
day: 19
published: 
source: https://www.linkedin.com/pulse/sentinel-your-stack-you-simply-paying-store-logs-stuart-mann-pr7fe
impressions: 
tags:
  - sentinel
  - siem
  - secops
  - detection
  - cost
---

# Microsoft Sentinel — licence vs running threat detection

## Summary
Owning Sentinel is not the same as running detection with it. Ingesting logs into a workspace is storage; value comes from analytics rules, hunting, automation and a team acting on incidents. Also flags the Azure-portal retirement.

## Key facts
- Sentinel is a cloud-native SIEM/SOAR; paying for ingestion alone just stores logs.
- Value = analytics rules, UEBA, hunting, playbooks/automation, and an operating SOC.
- Data connectors (350+) and table/tier management shape cost.
- Azure portal for Sentinel retires 31 Mar 2027 — future is the Defender portal (unified SecOps).

## Licensing & prerequisites
- Sentinel is consumption-priced (ingestion + retention); commitment tiers reduce cost. GA in the Defender portal even without E5.

## Practitioner notes / gotchas
- 'We have Sentinel' often means 'we store logs' — detection engineering and response are the actual work.
- Plan the Defender-portal transition now (see Day 81).

## Microsoft Learn references
- (see LinkedIn source)

## Related
- [[81 - Microsoft Sentinel — the agentic defence platform]]
- [[26 - Threat hunting in Microsoft Sentinel & Defender XDR]]
- [[91 - Microsoft Defender XDR — unified incidents & automatic attack disruption]]

## Source
LinkedIn (Day 19): https://www.linkedin.com/pulse/sentinel-your-stack-you-simply-paying-store-logs-stuart-mann-pr7fe
