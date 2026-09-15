---
title: "Microsoft Purview becomes the data-security hub"
product: "Microsoft Purview"
day: 83
published: 2026-08-26
source: https://www.linkedin.com/pulse/microsoft-purview-becomes-data-security-hub-dlp-protecting-mann-lo12e/
impressions: 
tags:
  - purview
  - dlp
  - data-security
  - ai-security
  - consolidation
---

# Microsoft Purview becomes the data-security hub

## Summary
Purview is consolidating as the single data-security hub: DLP moving out of Defender for Cloud Apps into Purview, and DLP extended into browser, network and AI-prompt paths — protecting the ways data actually leaves today.

## Key facts
- Defender for Cloud Apps file policies retire 6 Jan 2027 — migrate to Purview DLP / auto-labelling.
- Browser Data Security (Edge for Business) inspects typed/pasted content in real time (no device onboarding for Edge integration).
- Network Data Security extends inspection to non-Microsoft browsers/apps/APIs (HTTP/HTTPS, preview).
- AI-prompt controls block sensitive info in Copilot prompts and into consumer AI (ChatGPT, Gemini, DeepSeek); default Copilot DLP policy starts in simulation mode.
- DSPM for AI is the front door; new DSPM vs DSPM (classic) split.

## Licensing & prerequisites
- Some browser/network features are pay-as-you-go, not bundled E5; Network Data Security with GSA can require Microsoft 365 E7 or Purview E5 + Entra Internet Access. Several capabilities in preview.

## Practitioner notes / gotchas
- Diarise 6 Jan 2027 for the DfCA file-policy migration.
- The default Copilot DLP policy in simulation mode won't block anything until moved to enforce — 'visible ≠ protected'.

## Microsoft Learn references
- [Learn about Microsoft Purview](https://learn.microsoft.com/purview/purview)
- [Learn about data loss prevention](https://learn.microsoft.com/purview/dlp-learn-about-dlp)
- [Learn about using Microsoft Purview DLP to protect interactions with Microsoft 365 Copilot and Copilot Chat](https://learn.microsoft.com/purview/dlp-microsoft365-copilot-location-learn-about)
- [Migrate file policies to Microsoft Purview (Defender for Cloud Apps)](https://learn.microsoft.com/defender-cloud-apps/migrate-file-policies-to-purview)
- [Microsoft Purview data security and compliance for AI](https://learn.microsoft.com/purview/ai-microsoft-purview)

## Related
- [[33 - Microsoft Purview DLP — simulation mode that never gets turned on]]
- [[47 - Microsoft Defender for Cloud Apps]]
- [[69 - Microsoft Purview & AI agent data security]]

## Source
LinkedIn (Day 83): https://www.linkedin.com/pulse/microsoft-purview-becomes-data-security-hub-dlp-protecting-mann-lo12e/
