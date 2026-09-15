---
title: "Microsoft Sentinel — the agentic defence platform"
product: "Microsoft Sentinel"
day: 81
published: 2026-08-24
source: https://www.linkedin.com/pulse/microsoft-sentinel-longer-just-siem-evolving-agentic-defence-mann-ixfae
impressions: 54052
tags:
  - sentinel
  - siem
  - agentic
  - data-lake
  - mcp
  - graph
  - ai-security
---

# Microsoft Sentinel — the agentic defence platform

## Summary
Sentinel has evolved from a SIEM into a SIEM and platform for agentic defence — a data-first foundation that turns telemetry into a security graph, standardises how AI agents access it, and coordinates response, with humans in command.

## Key facts
- Data lake (GA): analytics tier for real-time + data-lake tier for low-cost long-term retention (up to 12 years); analytics data mirrored to lake; direct-to-lake ingestion for secondary data.
- Sentinel graph (preview): models relationships for pre/post-breach reasoning; custom graphs + Graph Query Language (preview).
- MCP server (preview): natural-language querying of lake/graph; works with Security Copilot, Copilot Studio, Foundry, VS Code, ChatGPT, Claude.
- Defender portal is the long-term home; Azure portal retires 31 Mar 2027.

## Licensing & prerequisites
- Consumption-priced by tier; MCP interface at no extra cost (pay for KQL/graph queries). GA in Defender portal without E5.

## Practitioner notes / gotchas
- Reframe the mental model: logs→rules→alerts becomes data→context→AI reasoning→response.
- Graph and MCP are preview — test before building operational dependencies; the data lake is the clearest immediate value.

## Microsoft Learn references
- [What is Microsoft Sentinel?](https://learn.microsoft.com/azure/sentinel/sentinel-overview)
- [What's new in Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/whats-new)
- [Microsoft Sentinel in the Microsoft Defender portal](https://learn.microsoft.com/azure/sentinel/microsoft-sentinel-defender-portal)
- [What is Microsoft Sentinel data lake?](https://learn.microsoft.com/azure/sentinel/datalake/sentinel-lake-overview)
- [What is Microsoft Sentinel's support for Model Context Protocol (MCP)?](https://learn.microsoft.com/azure/sentinel/datalake/sentinel-mcp-overview)

## Related
- [[19 - Microsoft Sentinel — licence vs running threat detection]]
- [[26 - Threat hunting in Microsoft Sentinel & Defender XDR]]
- [[91 - Microsoft Defender XDR — unified incidents & automatic attack disruption]]
- [[98 - Where Microsoft security is heading — the agentic SOC]]

## Source
LinkedIn (Day 81): https://www.linkedin.com/pulse/microsoft-sentinel-longer-just-siem-evolving-agentic-defence-mann-ixfae
