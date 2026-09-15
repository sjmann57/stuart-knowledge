---
title: "Token theft — the attack after MFA"
product: "Microsoft Defender XDR"
day: 23
published: 
source: https://www.linkedin.com/pulse/your-users-completed-mfa-token-still-got-stolen-stuart-mann-w6oue
impressions: 
tags:
  - identity
  - token-theft
  - aitm
  - conditional-access
  - token-protection
---

# Token theft — the attack after MFA

## Summary
MFA stops password-only attacks but not token theft: an adversary-in-the-middle or malware can steal the session token issued after a successful MFA and replay it, bypassing the MFA the user just completed.

## Key facts
- Attack vectors: AiTM phishing proxies, infostealer malware lifting browser session cookies.
- Defences: token protection (bind token to device), Conditional Access continuous access evaluation (CAE), compliant-device requirements, phishing-resistant auth.
- Signals surface in Entra ID Protection (anomalous token) and Defender XDR.
- Shortening session lifetime and requiring managed/compliant devices reduces replay window.

## Licensing & prerequisites
- Token protection / CAE require appropriate Entra ID P1/P2 and supported clients.

## Practitioner notes / gotchas
- The dangerous misconception: 'we have MFA so we're covered'. The token is the new target.
- Phishing-resistant methods + device binding are what actually blunt AiTM.

## Microsoft Learn references
- [Token Protection in Microsoft Entra Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-token-protection)
- [Protecting Tokens in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/devices/protecting-tokens-microsoft-entra-id)
- [Token Protection Deployment Guide — Windows](https://learn.microsoft.com/en-us/entra/identity/conditional-access/deployment-guide-token-protection-windows)
- [Token theft playbook](https://learn.microsoft.com/en-us/security/operations/token-theft-playbook)
- [What is a Primary Refresh Token?](https://learn.microsoft.com/en-us/entra/identity/devices/concept-primary-refresh-token)

## Related
- [[07 - Entra ID Identity Protection]]
- [[08 - Conditional Access]]
- [[09 - Authentication Strengths (phishing-resistant MFA)]]

## Source
LinkedIn (Day 23): https://www.linkedin.com/pulse/your-users-completed-mfa-token-still-got-stolen-stuart-mann-w6oue
