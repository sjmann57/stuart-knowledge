---
title: "Microsoft Zero Trust Assessment"
product: "Zero Trust"
day: 75
published: 2026-08-18
source: https://www.linkedin.com/pulse/microsoft-zero-trust-assessment-testing-your-tenant-against-mann-lwjde
impressions: 151
tags:
  - zero-trust
  - assessment
  - posture
  - powershell
  - tooling
---

# Microsoft Zero Trust Assessment

## Summary
A free, open-source, read-only PowerShell tool that tests your Microsoft tenant against hundreds of security-configuration checks aligned to Zero Trust and the Secure Future Initiative, producing an HTML report of gaps and remediation.

## Key facts
- Read-only: reads tenant configuration, makes no changes.
- Install-Module ZeroTrustAssessment → Connect-ZtAssessment → Invoke-ZtAssessment.
- Checks draw on NIST, CISA, CIS and Microsoft internal baselines; results carry risk levels + remediation.
- First run needs Global Administrator consent; report opens on completion.

## Licensing & prerequisites
- Free/open-source; PowerShell 7. First run = Global Admin; subsequent runs lower-privileged (verify current prerequisites). Large tenants can take >24h.

## Practitioner notes / gotchas
- The report/export folder contains sensitive tenant data — store securely, share narrowly, delete when done.
- A baseline and starting point, not a full architecture review — but it tests actual config, not assumptions.

## Microsoft Learn references
- [Zero Trust Assessment overview](https://learn.microsoft.com/en-us/security/zero-trust/assessment/overview)
- [Get started with the Zero Trust Assessment](https://learn.microsoft.com/en-us/security/zero-trust/assessment/get-started)
- [Zero Trust assessment terminology](https://learn.microsoft.com/en-us/security/zero-trust/assessment/glossary)

## Related
- [[74 - Zero Trust foundations — three principles, seven pillars]]
- [[76 - Zero Trust for identity — the most foundational pillar]]
- [[77 - Zero Trust implementation — from assessment to action]]
- [[89 - Microsoft Security Exposure Management]]

## Source
LinkedIn (Day 75): https://www.linkedin.com/pulse/microsoft-zero-trust-assessment-testing-your-tenant-against-mann-lwjde
