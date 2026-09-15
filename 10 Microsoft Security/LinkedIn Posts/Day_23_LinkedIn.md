# Day 23 — LinkedIn Content Package
**Topic:** Token theft — the attack that happens after MFA
**Category:** Identity and Access / Security Operations
**Format:** Technical article
**Note:** Natural extension of Day 9 (Authentication Strengths / AiTM) and Day 16 (Passkeys vs FIDO keys). Angle is distinct: MFA strength protects the authentication event; Token Protection protects what comes after it.

---

## 1. Title

Your users completed MFA. The token still got stolen.

---

## 2. LinkedIn Article (Stuart's version — published)

Your users completed MFA. The token still got stolen.

A few weeks ago, I wrote about AiTM attacks — adversary-in-the-middle phishing that bypasses SMS and push notification MFA by sitting between the user and the login page, capturing the session token in real time. Several people asked me a reasonable follow-up question: if we deploy phishing-resistant MFA, are we protected?

Largely, yes. But not from everything.

A token replay attack can occur after authentication completes. The user proves their identity, completes MFA, and receives a session token. That token is then stolen and replayed from a different device. Without additional controls, Microsoft Entra ID accept a valid session token even when authentication requirements have already been satisfied. In endpoint compromise scenarios, the attacker never touched a password or an MFA prompt.

This is token theft and an attack vector you need to protect against.

Why the session token is valuable

When a user signs in on a managed Windows device, Entra ID issues a Primary Refresh Token (PRT). The PRT enables seamless single sign-on across Microsoft 365 applications. It supports single sign-on and can be used to obtain access tokens for supported applications, which makes it highly valuable to an attacker. If it can be extracted from a device, through a compromised endpoint, a malicious extension, or a memory injection technique, it can be replayed elsewhere to access Exchange, SharePoint, Teams, and more.

On Apple platforms, unmanaged iOS and macOS devices are not supported, and Apple's native Mail and Calendar apps do not support Token Protection.

The key point: phishing-resistant MFA protects the authentication event. It does not protect the token that is issued afterwards.

What Token Protection does

Token Protection is a Conditional Access session control that binds the PRT cryptographically to the device that registered it. When a supported application requests access, Entra ID checks that the token being presented came from the specific device it was issued to. A stolen token, replayed from a different machine, fails that check.

It does not stop the token from being stolen. It stops the stolen token from working anywhere else.

Where things stand today

Token Protection on Windows is generally available. iOS, iPadOS, and macOS are in preview. It currently supports only native applications; browser-based apps are not yet supported. The resources you can protect today are Exchange Online, SharePoint Online, and Microsoft Teams, with Azure Virtual Desktop and Windows 365 also supported on Windows.

Microsoft Entra ID P1 is included in Microsoft 365 Business Premium and many Enterprise plans, but licensing should still be checked before rollout.

How to start

The risk with Token Protection is compatibility. Some older native clients and device configurations will not support it, and if you enforce it without checking first, you will block legitimate users.

With Conditional Access policies, adjust policies to ensure token protection is used, and start in report-only mode. Review both interactive and non-interactive sign-in logs. Look at what would have been blocked. Fix the gaps; typically, older clients, devices not properly registered with Entra ID, or hybrid join issues you already suspected were there. Add a pilot group, watch the logs, and expand from there.

Microsoft Entra ID Protection also provides detection signals worth enabling if you have not already: anomalous token detection flags tokens with atypical characteristics or tokens used from unfamiliar locations, and unfamiliar sign-in properties catch non-interactive sign-ins that fall outside normal behaviour. Both are indicators of a token replay attempt.

The pattern I keep seeing.

Organisations invest in phishing-resistant MFA, rightly. Then they treat the identity work as done. Token theft is a reminder that authentication is not a single gate. It is a chain, and attackers are working every link in it.

Protecting the authentication event and protecting what comes after it are two separate problems that both need an answer.

What is your current approach to detecting and containing token theft? Are you using Identity Protection risk signals, Sentinel, or something else?

---

## 3. Microsoft Learn References

- [Token Protection in Microsoft Entra Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-token-protection)
- [Protecting Tokens in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/devices/protecting-tokens-microsoft-entra-id)
- [Token Protection Deployment Guide — Windows](https://learn.microsoft.com/en-us/entra/identity/conditional-access/deployment-guide-token-protection-windows)
- [Token theft playbook](https://learn.microsoft.com/en-us/security/operations/token-theft-playbook)
- [What is a Primary Refresh Token?](https://learn.microsoft.com/en-us/entra/identity/devices/concept-primary-refresh-token)

---

## 4. Suggested Image Concept

Clean dark graphic. Left side: "MFA Completed ✓" in green. Right side: "Token stolen" in red. Below: "Token Protection — Conditional Access." Simple, stark contrast. No stock photography.

---

## 5. Alternative Discussion Questions

- "We talk a lot about MFA. How often do you talk about what happens to the session token after authentication?"
- "Token Protection is GA on Windows. Has anyone deployed it in production yet — what did report-only mode reveal?"
- "Identity Protection anomalous token detection is a good early signal. Is anyone acting on it automatically, or is it still manual triage?"

---

## 6. Hashtags

#MicrosoftSecurity #EntraID #ZeroTrust #IdentitySecurity #SecurityArchitect

---

## Fact-Check Notes

- Token Protection Windows GA confirmed on MS Learn (updated March 2026). iOS/macOS in preview. ✓
- Supported resources: Exchange Online, SharePoint Online, Microsoft Teams, Azure Virtual Desktop, Windows 365 (Windows only for last two). ✓
- Native apps only — browser not yet supported. ✓
- Entra ID P1 required. ✓
- PRT is cryptographically bound to the device at registration. ✓
- Token theft playbook: attacker replays token post-MFA, Entra sees valid token and grants access. ✓
- Anomalous token detection and unfamiliar sign-in properties are Identity Protection signals for token replay. ✓
- Deploy in report-only mode first — confirmed in MS Learn deployment guidance. ✓

**Note on AiTM vs token theft:** AiTM (Day 9) captures the session cookie in transit during authentication. Token theft (Day 23) is broader — can happen via endpoint compromise, PRT extraction, malicious extension, etc. Both result in stolen session tokens but through different means. Article keeps this clear without overcomplicating it.

**Substack note:** This topic could support a longer Substack article — full token theft investigation playbook, KQL detection queries, containment steps. Good candidate if Stuart wants to go deeper.
