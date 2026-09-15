---
title: "Entra ID Privileged Identity Management (PIM)"
product: "Microsoft Entra"
day: 6
published: 2026-06-08
source: https://www.linkedin.com/posts/stuartmann_who-has-the-global-administrator-role-rights-activity-7469729015239569408-QJ_v
impressions: 
tags:
  - identity
  - entra
  - pim
  - privileged-access
  - zero-trust
---

# Entra ID Privileged Identity Management (PIM)

## Summary
PIM provides just-in-time, time-bound, approval-gated activation of privileged roles so admins hold standing privilege only when they actually need it. Licensed but not switched on is the common failure state.

## Key facts
- Eligible vs active assignments: eligible roles are activated on demand for a limited window rather than held permanently.
- Activation can require MFA, justification, approval workflow and ticket reference.
- Applies to Entra ID roles, Azure resource roles and PIM for Groups.
- Access reviews and alerts surface standing/over-privileged assignments.
- Core lever for the Zero Trust 'use least privilege' principle applied to administrators.

## Licensing & prerequisites
- Requires Microsoft Entra ID P2 (or equivalent, e.g. Microsoft 365 E5).

## Practitioner notes / gotchas
- Owning the licence isn't the control — Global/Security Admins left permanently assigned is the highest-priority gap to close.
- Start by identifying who holds privileged roles, then move eligible-appropriate ones to JIT.

## Microsoft Learn references
- [What is Privileged Identity Management?](https://learn.microsoft.com/entra/id-governance/privileged-identity-management/pim-configure)

## Related
- [[07 - Entra ID Identity Protection]]
- [[76 - Zero Trust for identity — the most foundational pillar]]
- [[41 - CIEM — Entra Permissions Management]]

## Source
LinkedIn (Day 6): https://www.linkedin.com/posts/stuartmann_who-has-the-global-administrator-role-rights-activity-7469729015239569408-QJ_v
