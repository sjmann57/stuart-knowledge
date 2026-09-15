---
title: "Security Copilot agents across Defender, Entra, Intune & Purview"
product: "Microsoft Security Copilot"
day: 84
published: 2026-08-27
source: https://www.linkedin.com/pulse/security-copilot-agents-across-defender-entra-intune-purview-mann-cqv5e
impressions: 
tags:
  - security-copilot
  - agents
  - ai-security
  - secops
  - automation
---

# Security Copilot agents across Defender, Entra, Intune & Purview

## Summary
The agentic layer: ~12 Microsoft-built Security Copilot agents embedded across Defender, Entra, Intune and Purview (plus partner agents), doing triage, optimisation and investigation with administrator oversight — and now included for eligible E5/E7.

## Key facts
- Defender: Phishing/Security Alert Triage Agent, Threat Intelligence Briefing, Threat Hunting Assistant, Security Analyst, Dynamic Threat Detection.
- Entra: Conditional Access Optimization Agent (GA), Identity Risk Management Agent.
- Intune: Vulnerability Remediation Agent (Device Offboarding removed Jun 2026; Policy Config & Change Review retired after 31 Aug 2026).
- Purview: DLP Triage, Insider Risk Triage, DSPM & Data Security Investigations posture agents (preview).
- Governance: agent identity (often via Entra Agent ID), RBAC per agent, human oversight; monitoring group needs equal/higher permissions.

## Licensing & prerequisites
- Included for eligible Microsoft 365 E5/E7 (SCU allocation); agents consume SCUs; several agents in preview and the portfolio changes quickly.

## Practitioner notes / gotchas
- Provisioning Security Copilot doesn't auto-enable agents — you set up the ones you want.
- Ask five questions per agent: what identity, what permissions, what data, what actions, who's accountable (Zero Trust for agents).

## Microsoft Learn references
- [Microsoft Security Copilot agents](https://learn.microsoft.com/copilot/security/agents-security-copilot)
- [Security Copilot for Microsoft 365 E5 and E7 included customers](https://learn.microsoft.com/copilot/security/security-copilot-inclusion)
- [Deploy AI agents in Microsoft Defender](https://learn.microsoft.com/defender-xdr/security-copilot-agents-defender)
- [Security Copilot agents in Intune overview](https://learn.microsoft.com/intune/copilot/agents/)
- [Microsoft Security Copilot Security Compute Units and capacity](https://learn.microsoft.com/copilot/security/security-compute-units-capacity)

## Related
- [[49 - Microsoft Security Copilot]]
- [[68 - Microsoft Entra Agent ID]]
- [[98 - Where Microsoft security is heading — the agentic SOC]]

## Source
LinkedIn (Day 84): https://www.linkedin.com/pulse/security-copilot-agents-across-defender-entra-intune-purview-mann-cqv5e
