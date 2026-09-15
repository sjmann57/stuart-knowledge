---
title: "Microsoft Purview DLP — simulation mode that never gets turned on"
product: "Microsoft Purview"
day: 33
published: 
source: https://www.linkedin.com/pulse/dlp-policies-simulation-mode-stay-unless-someone-makes-stuart-mann-v4mqe
impressions: 
tags:
  - purview
  - dlp
  - data-security
  - simulation-mode
---

# Microsoft Purview DLP — simulation mode that never gets turned on

## Summary
Purview Data Loss Prevention identifies, monitors and protects sensitive data across M365, endpoints and cloud. A common failure: policies are created in simulation (test) mode to assess impact, and then never moved into enforcement.

## Key facts
- DLP acts on sensitive information types (SITs) and sensitivity labels across Exchange, SharePoint, OneDrive, Teams, endpoints and cloud apps.
- Simulation mode logs matches without enforcing — for tuning before go-live.
- Actions: block, block with override, audit, notify, restrict access.
- Extends to endpoint DLP and (later) browser/network and AI-prompt protection.

## Licensing & prerequisites
- Microsoft 365 E5 / E5 Compliance (or Information Protection & Governance); some browser/network features are pay-as-you-go.

## Practitioner notes / gotchas
- Having a DLP policy visible isn't the same as being protected — simulation mode enforces nothing.
- Tune in simulation, then deliberately move to enforce; second-highest-reach technical post of the series (1,397).

## Microsoft Learn references
- [Learn about data loss prevention — Microsoft Purview](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp)
- [Learn about data loss prevention simulation mode](https://learn.microsoft.com/en-us/purview/dlp-simulation-mode-learn)
- [Create and deploy data loss prevention policies](https://learn.microsoft.com/en-us/purview/dlp-create-deploy-policy)
- [Learn about Endpoint data loss prevention](https://learn.microsoft.com/en-us/purview/endpoint-dlp-learn-about)
- [Data loss prevention and Microsoft Teams](https://learn.microsoft.com/en-us/purview/dlp-microsoft-teams)

## Related
- [[37 - Microsoft Purview Sensitivity Labels]]
- [[34 - Microsoft Purview DSPM (Data Security Posture Management)]]
- [[83 - Microsoft Purview becomes the data-security hub]]

## Source
LinkedIn (Day 33): https://www.linkedin.com/pulse/dlp-policies-simulation-mode-stay-unless-someone-makes-stuart-mann-v4mqe
