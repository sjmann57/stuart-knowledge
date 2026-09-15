# Day 8 — LinkedIn Content Package
**Topic:** Conditional Access — on, but not controlling access
**Category:** Identity and Access
**Framework:** Microsoft Guidance vs Real-World Implementation
**Format:** Research-backed article (Day 6+ format)
**Builds on:** Day 6 (PIM) and Day 7 (Identity Protection) — completing the identity thread

---

## 1. Title

Conditional Access is on. That does not mean access is conditional.

---

## 2. LinkedIn Post (Stuart's version — fact-checked, ready to publish)

Conditional Access is on. That does not mean access is conditional.

Over the last two posts, I wrote about PIM and Identity Protection, protecting privileged access and detecting compromised identities. Conditional Access is the policy layer that sits across both of them. It is also the one where I most often find the gap between what an organisation thinks is in place and what is actually enforced.

Microsoft Entra Conditional Access works as an if-then statement. If a user meets these conditions, then grant or block access. It can evaluate sign-in risk and user risk from Identity Protection, device compliance from Intune, network location, authentication strength and sign-in context. When it is working properly, it is one of the most effective access controls available in the Microsoft stack.

The problem I find in practice falls into a few consistent patterns.

The first is that legacy authentication has not been blocked.

Legacy protocols such as IMAP, POP, and SMTP AUTH are commonly encountered during reviews and should be carefully assessed.

Legacy authentication cannot satisfy modern authentication requirements such as MFA and device-based Conditional Access controls. Where legacy authentication remains enabled, it can create paths around the protections organisations believe they have implemented. Blocking it is one of the most impactful single actions you can take.

The second is exclusion groups. Every policy has them; they are necessary. But the break-glass exclusion group, which started with two accounts, now has 30. Nobody has reviewed it in a year. The accounts in that group bypass every policy that references it. More worryingly, I often find that many of the organisation's Global Admins are in the exclusions too. What is in your exclusions?

The third connects directly back to Tuesday's post. Identity Protection is generating risk signals. But if Conditional Access risk-based policies have not been configured, those signals do nothing. The connection between detection and enforcement is missing. Have you already allowed that bad actor in?

The fourth is report-only mode. The policy exists, the design has been approved, and the dashboard shows no major issues. Yet six months later the policy is still not enforcing anything.

Core Conditional Access capabilities require Entra ID P1, while risk-based Conditional Access policies that integrate with Identity Protection require Entra ID P2. Most organisations have Entra ID P1, but definitely should be seriously moving to P2; whether they have it configured to do what they think it does is a different question.

Do you know what your Conditional Access exclusions actually contain?

Or has the list grown quietly while nobody was checking?

---

## 3. Microsoft Learn References

- Build a Conditional Access policy: https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policies
- Conditional Access conditions: https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-conditions
- Block legacy authentication: https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-block-legacy-authentication
- Common Conditional Access policies: https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common

---

## 4. Suggested Image Concept

Dark background, clean text. Large text: "Conditional Access is on." Below it, in different weight or colour: "That does not mean access is conditional." Microsoft Entra logo bottom-right.

Alternative: Three-panel sequence showing the thread across Days 6, 7 and 8. Panel 1: "PIM — who gets privileged access?" Panel 2: "Identity Protection — are those accounts compromised?" Panel 3: "Conditional Access — is any of it enforced?" Clean, no stock photos.

---

## 5. Alternative Discussion Questions

1. When did you last audit what accounts are in your Conditional Access exclusion groups?
2. Have you blocked legacy authentication across your tenant, or are there still exceptions keeping it alive?
3. Are your Identity Protection risk signals connected to Conditional Access, or are they informational only?

---

## 6. Hashtags

#MicrosoftEntra #ConditionalAccess #ZeroTrust #MicrosoftSecurity #SecurityArchitect

---

## Day 8 Checklist

- [ ] Review draft — the exclusion group observation is the sharpest practitioner point; add your own version if you have a specific example (e.g. a number of accounts or a sector where you see this most)
- [ ] Consider whether to reference the three-part identity thread explicitly in the opening or keep it implicit
- [ ] Post with graphic or personal photo
- [ ] Add follow-up comment within 30 minutes — consider noting that legacy authentication blocking is the single highest-impact Conditional Access action for most organisations
- [ ] Engage with any comments on Day 7 before posting

