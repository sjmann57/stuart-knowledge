---
title: "Passkeys vs physical FIDO keys"
product: "Microsoft Entra"
day: 16
published: 2026-06-19
source: https://www.linkedin.com/pulse/passkeys-vs-physical-fido-keys-stuart-mann-fow3e
impressions: 
tags:
  - identity
  - entra
  - passkeys
  - fido2
  - authentication
---

# Passkeys vs physical FIDO keys

## Summary
Passkeys and physical FIDO2 security keys are both phishing-resistant FIDO2 credentials, but they are not the same strategy: synced passkeys prioritise convenience and recovery, device-bound keys prioritise tighter control.

## Key facts
- Synced passkeys live in a platform credential manager (iCloud Keychain, Google Password Manager) and sync across a user's devices.
- Device-bound: FIDO2 hardware security keys, passkeys in Microsoft Authenticator, Windows Hello for Business — the credential stays tied to a device/authenticator.
- Both use cryptographic credentials rather than a shared secret, so both resist phishing, SIM-swap and replay.
- Managed via passkey profiles in the authentication methods policy.

## Licensing & prerequisites
- Requires Entra passkey (FIDO2) method enabled; some scenarios need specific Authenticator/OS versions.

## Practitioner notes / gotchas
- Consider device-bound methods for admins and highly privileged users where tighter device control matters.
- A passwordless user experience does not always mean the directory account has no password.

## Microsoft Learn references
- [Passkeys (FIDO2) in Microsoft Entra ID](https://learn.microsoft.com/entra/identity/authentication/concept-authentication-passkeys-fido2)

## Related
- [[09 - Authentication Strengths (phishing-resistant MFA)]]
- [[82 - What's new in Microsoft Entra — passkeys by default, Tenant Governance, Backup & Recovery]]

## Source
LinkedIn (Day 16): https://www.linkedin.com/pulse/passkeys-vs-physical-fido-keys-stuart-mann-fow3e
