---
title: "Authentication Strengths (phishing-resistant MFA)"
product: "Microsoft Entra"
day: 9
published: 2026-06-11
source: https://www.linkedin.com/pulse/mfa-does-mean-your-accounts-cannot-phished-stuart-mann-g5ppe
impressions: 
tags:
  - identity
  - entra
  - authentication
  - mfa
  - phishing-resistant
  - passwordless
---

# Authentication Strengths (phishing-resistant MFA)

## Summary
Authentication strengths let Conditional Access require a specific class of credential — not just 'any MFA'. Not all MFA is equal: SMS/voice are phishable, whereas passkeys, FIDO2 keys, Windows Hello for Business and certificate-based auth are phishing-resistant.

## Key facts
- Built-in strengths: MFA, passwordless MFA, phishing-resistant MFA.
- Custom authentication strengths let you define exactly which methods qualify.
- Enforced through Conditional Access grant control ('require authentication strength').
- Phishing-resistant methods: Windows Hello for Business, FIDO2 security keys, passkeys, certificate-based authentication, Platform Credential (macOS).

## Licensing & prerequisites
- Conditional Access grant requires Microsoft Entra ID P1; methods vary by platform/config.

## Practitioner notes / gotchas
- MFA being 'on' does not mean accounts can't be phished — SMS/voice can be intercepted or SIM-swapped.
- Use authentication strengths to force phishing-resistant methods for admins and high-risk apps.

## Microsoft Learn references
- [Authentication strengths](https://learn.microsoft.com/entra/identity/authentication/concept-authentication-strengths)

## Related
- [[08 - Conditional Access]]
- [[16 - Passkeys vs physical FIDO keys]]
- [[82 - What's new in Microsoft Entra — passkeys by default, Tenant Governance, Backup & Recovery]]

## Source
LinkedIn (Day 9): https://www.linkedin.com/pulse/mfa-does-mean-your-accounts-cannot-phished-stuart-mann-g5ppe
