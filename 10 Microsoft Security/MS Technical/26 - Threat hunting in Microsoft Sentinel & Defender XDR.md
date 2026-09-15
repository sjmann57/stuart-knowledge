---
title: "Threat hunting in Microsoft Sentinel & Defender XDR"
product: "Microsoft Sentinel"
day: 26
published: 
source: https://www.linkedin.com/pulse/your-sentinel-workspace-generating-alerts-same-hunting-stuart-mann-pdzne
impressions: 
tags:
  - sentinel
  - defender-xdr
  - threat-hunting
  - kql
  - proactive-detection
---

# Threat hunting in Microsoft Sentinel & Defender XDR

## Summary
Proactive threat hunting versus reactive alert-chasing: using KQL and advanced hunting across Sentinel and Defender XDR data to look for compromise the automated detections didn't catch.

## Key facts
- Advanced hunting queries KQL across unified Defender + Sentinel schemas.
- Hunting is hypothesis-driven and proactive, complementing rule-based alerting.
- Findings can be promoted to custom detection rules.
- Sentinel data lake, graph and MCP server extend hunting (natural-language exploration).

## Licensing & prerequisites
- Sentinel + Defender XDR (unified SecOps); Security Copilot can generate KQL.

## Practitioner notes / gotchas
- A workspace generating alerts isn't the same as a team hunting in it.
- KQL fluency still matters even as MCP/Copilot lower the barrier to asking questions of the data.

## Microsoft Learn references
- [Threat hunting in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/hunting)
- [Conduct end-to-end proactive threat hunting in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/hunts)
- [Proactively hunt for threats with advanced hunting in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Advanced hunting with Microsoft Sentinel data in Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-microsoft-defender)
- [View MITRE ATT&CK framework coverage in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/mitre-coverage)
- [Keep track of data during hunting with Microsoft Sentinel (Bookmarks)](https://learn.microsoft.com/en-us/azure/sentinel/bookmarks)

## Related
- [[19 - Microsoft Sentinel — licence vs running threat detection]]
- [[81 - Microsoft Sentinel — the agentic defence platform]]
- [[91 - Microsoft Defender XDR — unified incidents & automatic attack disruption]]

## Source
LinkedIn (Day 26): https://www.linkedin.com/pulse/your-sentinel-workspace-generating-alerts-same-hunting-stuart-mann-pdzne
