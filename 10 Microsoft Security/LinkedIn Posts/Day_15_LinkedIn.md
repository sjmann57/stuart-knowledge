# Day 15 — LinkedIn Content Package
**Topic:** What's new in Microsoft Entra Identity Security — June 2026
**Category:** Identity and Access / News
**Format:** Current awareness post — research-backed from Microsoft Tech Community
**Sources:** Microsoft Entra Blog June 2026, Microsoft Entra ID security updates post (June 8, 2026)

---

## 1. Title

Microsoft Entra — what changed this month, and what you need to do before July 6.

---

## 2. LinkedIn Post (Draft — for Stuart's review)

Microsoft Entra — what changed this month, and what you need to do before July 6.

Microsoft does not slow down. June 2026 has brought a set of Entra updates worth knowing about, and two of them have deadlines that are closer than most people realise.

**What is new this month**

Phishing-resistant MFA has been extended to Linux. Ubuntu 24.04 and 26.04, RHEL 8, 9 and 10 now support passkey and certificate-based authentication on the desktop. If you have been using Linux as a reason to delay phishing-resistant MFA rollout, that reason has gone.

Registration Campaigns in Entra now support passkeys. Administrators can configure nudges to prompt users to register a passkey during sign-in, without forcing a hard cutover. This is one of the more practical tools for driving passkey adoption at scale without a big bang migration.

The Entra Security Operator role has been extended. SOC analysts can now take identity response actions directly from the Microsoft Defender unified portal — disable accounts, revoke sessions, mark users as compromised, force password resets, delete specific authentication methods — without needing elevated Entra roles. Fewer people with standing privileged access to take remediation actions. This is exactly what the principle of least privilege looks like in a SOC context.

**What needs action before July 6**

Starting July 6, Conditional Access policies scoped to the Register security information user action will be evaluated and enforced during credential registration. If you have these policies sitting in report-only mode, they will start enforcing in under three weeks. Users who cannot satisfy the policy controls — MFA, device compliance — will be blocked from registering new authentication methods.

That might be exactly what you want. Or it might break your helpdesk registration workflow if you have not reviewed it. Either way, the time to check is now, not after users start calling.

A second change is coming on September 7. Entra Self-Service Password Reset will only accept authentication methods that users have explicitly registered. Any fallback to unregistered methods stops working from that date.

**The pattern**

Microsoft is tightening enforcement across credential registration, SSPR, and identity response. The controls have existed for a while. The difference now is that enforcement is being switched on, with or without your intervention.

If you are not reviewing these changes before they hit, you are letting Microsoft set your security configuration for you.

When did you last check your Conditional Access policies scoped to security information registration?

---

## 3. Sources

- What's New in Microsoft Entra: June 2026: https://techcommunity.microsoft.com/blog/microsoft-entra-blog/whats-new-in-microsoft-entra-june-2026/4517885
- Microsoft Entra ID security updates — what organisations need to do now: https://techcommunity.microsoft.com/blog/microsoft-entra-blog/microsoft-entra-id-security-updates-what-organizations-need-to-do-now/4522024

---

## 4. Suggested Image Concept

Dark background, clean text. Large text: "July 6." Below it: "Your Conditional Access credential registration policies start enforcing." Small Microsoft Entra logo bottom-right. Urgency without alarm.

Alternative: A simple three-item list graphic. "Phishing-resistant MFA — now on Linux. Passkey registration campaigns — now available. CA credential registration enforcement — July 6." Clean, no stock photos.

---

## 5. Alternative Discussion Questions

1. Have you reviewed your Conditional Access policies scoped to security information registration ahead of the July 6 enforcement change?
2. Have you used Registration Campaigns to drive passkey adoption, or are you still relying on user-led registration?
3. Does your SOC have the Entra Security Operator role configured, or do analysts still need elevated Entra roles to take identity remediation actions?

---

## 6. Hashtags

#MicrosoftEntra #IdentitySecurity #ConditionalAccess #Passwordless #SecurityArchitect

---

## Day 15 Checklist

- [ ] The July 6 deadline is the hook — it is 19 days away as of today (17 June). Lead with urgency, not features
- [ ] The Security Operator role extension ties directly to least privilege — worth a personal observation if you have seen SOC teams with over-privileged Entra roles
- [ ] "Letting Microsoft set your security configuration for you" is a strong close — keep or adjust to your voice
- [ ] This is a current awareness post — no need to add personal experience beyond the practitioner framing
- [ ] Post with graphic or personal photo
- [ ] Add follow-up comment within 30 minutes — consider linking directly to the Microsoft blog posts for readers who want the full detail
