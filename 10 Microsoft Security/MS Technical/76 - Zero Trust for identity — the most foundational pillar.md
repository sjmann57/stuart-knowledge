---
title: "Zero Trust for identity — the most foundational pillar"
product: "Zero Trust"
day: 76
published: 2026-08-19
source: https://www.linkedin.com/pulse/zero-trust-identity-most-foundational-pillar-stuart-mann-d5wte
impressions: 151
tags:
  - zero-trust
  - identity
  - entra
  - deployment-objectives
  - pillar
---

# Zero Trust for identity — the most foundational pillar

## Summary
Identity is the primary Zero Trust control plane. Microsoft structures the identity pillar around six deployment objectives — where the most significant findings usually sit.

## Key facts
- Six objectives: cloud/on-prem identity integration; Conditional Access gating all resources; analytics & visibility; identity governance (PIM, entitlement mgmt, access reviews, passwordless); real-time risk analysis; threat-signal integration.
- Conditional Access reframed: 'which identities are covered?' (users, workload IDs, agent IDs) not 'do we have CA?'.
- Passwordless nuance: a passwordless experience may not mean the directory account has no password.
- AI agents now part of the identity architecture (Agent ID).

## Licensing & prerequisites
- Spans Entra P1/P2, Entra ID Governance, Defender for Identity depending on objective.

## Practitioner notes / gotchas
- If identity is weak, every other pillar has to compensate — get it right first.
- Ask an org for its agreed list of critical identities — the answer is rarely as clear as expected.

## Microsoft Learn references
- [Zero Trust identity pillar deployment objectives](https://learn.microsoft.com/en-us/security/zero-trust/deploy/identity)
- [Zero Trust technology pillars overview](https://learn.microsoft.com/en-us/security/zero-trust/deploy/overview)
- [What is Privileged Identity Management?](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure)
- [What is Microsoft Entra ID Protection?](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)

## Related
- [[06 - Entra ID Privileged Identity Management (PIM)]]
- [[08 - Conditional Access]]
- [[74 - Zero Trust foundations — three principles, seven pillars]]
- [[90 - Microsoft Defender for Identity (ITDR for on-prem AD)]]

## Source
LinkedIn (Day 76): https://www.linkedin.com/pulse/zero-trust-identity-most-foundational-pillar-stuart-mann-d5wte
