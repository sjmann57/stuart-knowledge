# Day 7 — LinkedIn Content Package
**Topic:** Entra ID Identity Protection — signals nobody is reading
**Category:** Identity and Access
**Framework:** Microsoft Guidance vs Real-World Implementation
**Format:** Research-backed article (Day 6+ format)
**Builds on:** Day 6 (PIM — protecting privileged access)

---

## 1. Title

Your identities are being attacked right now. Are you reading the signals?

---

## 2. LinkedIn Post (Stuart's version)

Your identities are being attacked right now. Are you reading the signals?

Yesterday I wrote about PIM and protecting privileged access. That is the right conversation to have. But a question sits underneath it. What happens when the accounts you are trying to protect are already compromised?

Microsoft analyses 78 trillion security signals every day. According to the Microsoft Digital Defence Report 2024, Microsoft reports more than 600 million identity attacks per day, and a 2.75x increase in ransomware-linked encounters. These are not abstract statistics; they are the environment in which your identities operate right now.

Microsoft Entra ID Protection was designed to surface that risk. It monitors sign-ins and user accounts for patterns that indicate compromise, including leaked credentials in breach databases, password spray attempts, sign-ins from anonymous IP addresses, impossible travel, and more. It assigns a risk level to each sign-in and user account, and can automatically trigger remediation via risk-based Conditional Access policies.

The licence is the same Entra ID P2 you are already using for PIM. The signals may already be available in your tenant, but they only reduce risk when someone reviews them or uses them in Conditional Access.

In practice, I find that reports are not being reviewed, and policies that could provide automated protection are not configured to protect your environment. All this leaves you vulnerable to security breaches and may put your business at risk. I know passwords are bad, and there are many options for users not to use them; many larger organisations have already taken steps to secure their identities, but have you?

Taking time to revisit what you may have configured months or even years ago is key to maintaining good security practices. The same principle also applies to workload identities, service principals, automation accounts, and AI-enabled applications and Agents. They need to be monitored and protected too; the landscape is becoming more than just what your users are doing.

Take time to review what is showing in Identity Protection and have a look at your Conditional Access. Reviewing the Identity Dashboard and Risk Policy impact analysis is a good start, along with Conditional review for risk users and sign-ins.

There are many Microsoft documents that provide good guidance on what good looks like, and for some, they are an ideal place to start. The difficulty comes in more complex environments, where good hygiene and documentation may not be as you hoped. If unsure, reach out for some help and guidance.

The signals are there. The question is whether anyone is reading them.

Are you reviewing your Identity Protection reports regularly?

Or are the signals accumulating while something waits to use them?

---

## 3. Microsoft Learn References

- What is Microsoft Entra ID Protection: https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection
- What is risk in ID Protection: https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-risks
- Configure risk-based Conditional Access policies: https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-configure-risk-policies
- How to investigate risk: https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-investigate-risk

---

## 4. Suggested Image Concept

Dark background, clean text. Large number: "600 million" — below it: "attacks on Microsoft customers. Every day." Small Microsoft Entra ID Protection logo bottom-right. No stock photos, no clip art.

Alternative: Quote card using the line: "The signals are there. The question is whether anyone is reading them."

---

## 5. Alternative Discussion Questions

1. When did you last review your Identity Protection risky users report?
2. Have you configured risk-based Conditional Access policies, or are your Identity Protection detections informational only?
3. Have you ever found a leaked credential detection that had been sitting unactioned in your tenant?

---

## 6. Hashtags

#MicrosoftEntra #IdentityProtection #ZeroTrust #MicrosoftSecurity #SecurityArchitect

---

## Day 7 Checklist

- [ ] Review draft — the leaked credential observation is strong; add your own version of this if you have seen it in an engagement
- [ ] The Microsoft Digital Defence Report stats are accurate as of the 2024 report — worth keeping as they land well with CISOs
- [ ] Post with graphic or personal photo
- [ ] Add follow-up comment within 30 minutes — consider referencing the link between PIM (Day 6) and Identity Protection as a natural security thread
- [ ] Engage with any comments on Day 6 before posting

