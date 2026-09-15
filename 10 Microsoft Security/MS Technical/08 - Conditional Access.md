---
title: "Conditional Access"
product: "Microsoft Entra"
day: 8
published: 2026-06-11
source: https://www.linkedin.com/posts/stuartmann_conditional-access-is-on-that-does-not-mean-activity-7470498969807405056-Au85
impressions: 183
tags:
  - identity
  - entra
  - conditional-access
  - zero-trust
  - policy-engine
---

# Conditional Access

## Summary
Conditional Access is the Zero Trust policy engine: it evaluates signals (user, device, location, app, risk, session) on each access request and applies controls such as MFA, compliant device or block. Being 'on' is not the same as controlling access.

## Key facts
- Signals in: user/group, device compliance/state, sign-in & user risk, location/named locations, application, authentication context, session.
- Controls out: require MFA, require compliant/hybrid-joined device, require approved app, require authentication strength, block, session controls.
- Coverage is the real question: which identities and resources are actually in scope — users, workload identities and now agent identities differ.
- Report-only mode lets you validate a policy before enforcing.

## Licensing & prerequisites
- Baseline needs Microsoft Entra ID P1; risk-based conditions need P2.

## Practitioner notes / gotchas
- 'Do we have Conditional Access?' is the wrong question — 'which identities and resources are covered?' is the right one.
- Gaps: legacy auth not blocked, service principals/workload identities uncovered, exclusions never reviewed.

## Microsoft Learn references
- [What is Conditional Access?](https://learn.microsoft.com/entra/identity/conditional-access/overview)

## Related
- [[07 - Entra ID Identity Protection]]
- [[09 - Authentication Strengths (phishing-resistant MFA)]]
- [[28 - Intune device compliance]]
- [[76 - Zero Trust for identity — the most foundational pillar]]

## Source
LinkedIn (Day 8): https://www.linkedin.com/posts/stuartmann_conditional-access-is-on-that-does-not-mean-activity-7470498969807405056-Au85
