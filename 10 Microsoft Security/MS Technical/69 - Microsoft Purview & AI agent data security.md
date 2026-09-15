---
title: "Microsoft Purview & AI agent data security"
product: "Microsoft Purview"
day: 69
published: 2026-08-13
source: https://lnkd.in/p/ewWfSg_p
impressions: 2038
tags:
  - purview
  - ai-security
  - agents
  - copilot
  - dspm
  - data-security
---

# Microsoft Purview & AI agent data security

## Summary
What Purview protects automatically for AI agents/Copilot versus what you must configure — and where the gaps are. Existing controls (labels, permissions) carry into AI, but the strongest protections need deliberate setup.

## Key facts
- Sensitivity labels and permissions are honoured by AI apps automatically (users can't get data via AI they can't otherwise access).
- DLP for M365 Copilot can block processing of sensitive prompts, block sensitive labelled files/emails as grounding, and block external web grounding.
- DSPM for AI provides visibility, risk and one-click policies for AI interactions.
- Insider Risk Management 'risky AI usage' detects prompt injection and protected-material access.

## Licensing & prerequisites
- Microsoft 365 E5 / E5 Compliance; some AI/prompt controls in preview and rolling out.

## Practitioner notes / gotchas
- 'Automatic' covers inheritance of labels/permissions; the blocking controls are opt-in and need configuring.
- Weak classification underneath = weak AI protection on top (high-reach post: 1,211).

## Microsoft Learn references
- [Use Microsoft Purview to manage data security & compliance for Microsoft Agent 365](https://learn.microsoft.com/en-us/purview/ai-agent-365)
- [Data Security Posture Management](https://learn.microsoft.com/en-us/purview/data-security-posture-management-learn-about)
- [Insider Risk Management — Risky AI usage policy template](https://learn.microsoft.com/en-us/purview/insider-risk-management-policy-templates#risky-ai-usage)
- [Audit logs for Copilot and AI activities](https://learn.microsoft.com/en-us/purview/audit-copilot)

## Related
- [[34 - Microsoft Purview DSPM (Data Security Posture Management)]]
- [[37 - Microsoft Purview Sensitivity Labels]]
- [[83 - Microsoft Purview becomes the data-security hub]]
- [[70 - Microsoft Defender threat protection for AI agents]]

## Source
LinkedIn (Day 69): https://lnkd.in/p/ewWfSg_p
