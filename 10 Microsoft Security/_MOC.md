---
title: Microsoft Security KB — Map of Content
tags:
  - moc
  - microsoft-security
---

# Microsoft Security — Knowledge Base (MOC)

Distilled knowledge notes from the 100-day Microsoft Security writing programme. Each note: summary, key facts, licensing/prerequisites, practitioner gotchas, Microsoft Learn references, related notes and the LinkedIn source.

**50 technical notes** across 17 areas.

> [!tip] Start here
> New to the vault? Read **[[95 - How the Microsoft security stack actually fits together — the architect's view]]** for the layered map, then **[[74 - Zero Trust foundations — three principles, seven pillars]]** for the strategy.

## By area

### Zero Trust
- [[74 - Zero Trust foundations — three principles, seven pillars]]
- [[75 - Microsoft Zero Trust Assessment]]
- [[76 - Zero Trust for identity — the most foundational pillar]]
- [[77 - Zero Trust implementation — from assessment to action]]

### Microsoft Entra
- [[06 - Entra ID Privileged Identity Management (PIM)]]
- [[07 - Entra ID Identity Protection]]
- [[08 - Conditional Access]]
- [[09 - Authentication Strengths (phishing-resistant MFA)]]
- [[15 - What's new in Microsoft Entra — June 2026]]
- [[16 - Passkeys vs physical FIDO keys]]
- [[41 - CIEM — Entra Permissions Management]]
- [[42 - Entra ID Governance — Lifecycle Workflows]]
- [[43 - Microsoft Entra Workload ID]]
- [[82 - What's new in Microsoft Entra — passkeys by default, Tenant Governance, Backup & Recovery]]

### Microsoft Entra / GSA
- [[53 - Microsoft Global Secure Access (Security Service Edge)]]
- [[54 - Microsoft Entra Private Access (ZTNA - VPN replacement)]]
- [[55 - Microsoft Entra Internet Access (identity-centric SWG)]]
- [[56 - Global Secure Access + Conditional Access + Defender for Cloud Apps]]

### Microsoft Defender for Identity
- [[29 - Microsoft Defender for Identity (introduction)]]
- [[90 - Microsoft Defender for Identity (ITDR for on-prem AD)]]

### Microsoft Defender XDR
- [[14 - Microsoft Defender XDR — five products, not yet a platform]]
- [[23 - Token theft — the attack after MFA]]
- [[91 - Microsoft Defender XDR — unified incidents & automatic attack disruption]]

### Microsoft Defender for Cloud
- [[20 - Microsoft Defender for Cloud — Secure Score, CSPM & the cloud gap]]
- [[60 - Microsoft Defender for Cloud — CSPM & CWPP architecture]]
- [[61 - Microsoft Defender for Servers]]
- [[62 - Microsoft Defender for Containers]]
- [[63 - Microsoft Defender for DevOps (Defender for Cloud – DevOps security)]]

### Microsoft Defender for Office 365
- [[46 - Microsoft Defender for Office 365]]

### Microsoft Defender for Cloud Apps
- [[47 - Microsoft Defender for Cloud Apps]]

### Microsoft Defender Vulnerability Management
- [[48 - Microsoft Defender Vulnerability Management]]

### Microsoft Intune
- [[28 - Intune device compliance]]

### Microsoft Purview
- [[33 - Microsoft Purview DLP — simulation mode that never gets turned on]]
- [[34 - Microsoft Purview DSPM (Data Security Posture Management)]]
- [[35 - Microsoft Purview Insider Risk Management]]
- [[36 - Microsoft Purview Communication Compliance]]
- [[37 - Microsoft Purview Sensitivity Labels]]
- [[69 - Microsoft Purview & AI agent data security]]
- [[83 - Microsoft Purview becomes the data-security hub]]

### Microsoft Sentinel
- [[19 - Microsoft Sentinel — licence vs running threat detection]]
- [[26 - Threat hunting in Microsoft Sentinel & Defender XDR]]
- [[81 - Microsoft Sentinel — the agentic defence platform]]

### Microsoft Security Exposure Management
- [[89 - Microsoft Security Exposure Management]]

### Microsoft Security Copilot
- [[49 - Microsoft Security Copilot]]
- [[84 - Security Copilot agents across Defender, Entra, Intune & Purview]]

### AI Agent Security
- [[67 - Microsoft Agent 365 — control plane for AI agents]]
- [[68 - Microsoft Entra Agent ID]]
- [[70 - Microsoft Defender threat protection for AI agents]]

### Security Architecture
- [[95 - How the Microsoft security stack fits together — the architect's view]]

### Security direction
- [[98 - Where Microsoft security is heading — the agentic SOC]]

## Recurring threads

- **Foundations first** — the clever capability on top only pays off when sensors/identities/data/integrations underneath are done properly.
- **Identity is the control plane** — most of Zero Trust is enforced here; workload and agent identities now included.
- **Licence ≠ deployed** — owning E5 isn't the same as configuring and operating the controls.
- **AI is two-sided** — something to secure (Agent 365 / Agent ID / Purview / Defender) and something that secures (Security Copilot agents, autonomous defence).
- **The agentic SOC** — machine speed for containment, human judgement for consequence.
