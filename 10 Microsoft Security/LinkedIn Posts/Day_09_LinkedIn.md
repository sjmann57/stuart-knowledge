# Day 9 — LinkedIn Content Package
**Topic:** Authentication Strengths — MFA is on, but not all MFA is equal
**Category:** Identity and Access
**Framework:** Microsoft Guidance vs Real-World Implementation
**Format:** Research-backed article (Day 6+ format)
**Builds on:** Day 8 (Conditional Access referenced "authentication strength") and Day 6 (PIM requires MFA to activate roles — but which MFA?)

---

## 1. Title

MFA is on. That does not mean your accounts cannot be phished.

---

## 2. LinkedIn Post (Stuart's version — published)

MFA is on. That does not mean your accounts cannot be phished.

Over the last few posts, I have covered PIM, Identity Protection, and Conditional Access. Each one surfaces a version of the same problem. The control exists. The licence is in place. But the configuration does not do what people think it does.

Authentication strength is one of the clearest examples of this.

Most organisations have MFA enabled. They consider that done. But there is a significant difference between MFA that can be intercepted and MFA that cannot; for example, SMS-based authentication remains vulnerable to attacks such as SIM swapping, social engineering, and credential phishing.

Push notifications remain vulnerable to MFA fatigue attacks, where users approve prompts they did not initiate, such as when a tired user just wants to get back to work or carry on with an evening out. The use of number matching, however, has reduced this risk. Adversary-in-the-middle attacks specifically target these methods by relaying credentials in real time after a user completes MFA. The MFA event happens, and the attacker still gets in.

So what options are there to protect you? The answer is to move to Phishing-resistant MFA. Methods such as FIDO2 security keys, Windows Hello for Business, and Microsoft Entra certificate-based authentication use strong cryptographic authentication methods that are significantly more resistant to phishing than traditional MFA methods. For phishing-resistant methods, authentication is tied to cryptographic trust that an attacker cannot simply relay to a phishing site they control. There is no password to steal, no code to intercept, no notification to approve.

Microsoft Entra Conditional Access has three built-in authentication strengths. MFA strength covers the broad set of methods that satisfy an MFA requirement, including SMS and push notifications. Passwordless MFA limits authentication to passwordless methods such as Windows Hello for Business and FIDO2 security keys. Phishing-resistant MFA strength narrows it further still, allowing only Microsoft-defined phishing-resistant authentication methods.

I am sure you already know you can enforce authentication strength as a Conditional Access grant control. That means you can require phishing-resistant MFA for your most sensitive resources, your privileged roles, your highest-risk sign-ins, without forcing it on every user for every application from day one.

In practice, I find that authentication strength still allows SMS, because "it has always been that way for our users". MFA is on. It satisfies the Conditional Access grant control for MFA. Nobody has asked whether the type of MFA matters. For most organisations, we have moved authentication to push notification MFA, and it is a reasonable trade-off between security and user experience. For a Global Administrator activating a role through PIM, it is not. Microsoft specifically supports Authentication Strengths in Conditional Access policies, allowing organisations to require phishing-resistant MFA for privileged role activation. Microsoft also recommends phishing-resistant MFA for administrator accounts through its Secure Future Initiative and Zero Trust guidance.

I would recommend moving users towards phishing-resistant MFA wherever practical, prioritising privileged access, administrators, and high-risk applications first.

The question today is not whether MFA is enabled. The question is what type of MFA is protecting your most sensitive access, and whether your Conditional Access policies are actually enforcing the right level.

Are you enforcing phishing-resistant MFA on your privileged roles and sensitive applications?

Or are you relying on MFA that an attacker with the right tools can still bypass?

---

## 3. Microsoft Learn References

- Conditional Access authentication strengths: https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths
- Passkeys (FIDO2) in Microsoft Entra ID: https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless
- Create and manage custom authentication strengths: https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strength-advanced-options
- Plan a phishing-resistant MFA deployment: https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-plan-prerequisites-phishing-resistant-passwordless-authentication

---

## 4. Suggested Image Concept

Dark background, clean text. Large text: "MFA is on." Below it, in a different weight or colour: "That does not mean your accounts cannot be phished." Small Microsoft Entra ID logo bottom-right.

Alternative: A simple three-tier visual showing the three built-in authentication strengths as a ladder. Bottom: "MFA Strength — SMS, push notification, password + something." Middle: "Passwordless MFA Strength — no password required." Top: "Phishing-Resistant MFA — cannot be intercepted or replayed." Each step labelled with examples (FIDO2, Windows Hello for Business, CBA at the top tier). Clean, no stock photos.

---

## 5. Alternative Discussion Questions

1. Have you configured authentication strength in Conditional Access, or are all MFA methods treated as equal?
2. Do your privileged role activations through PIM require phishing-resistant MFA, or will any MFA method satisfy the requirement?
3. Have you seen adversary-in-the-middle attacks bypass MFA in your organisation or in organisations you have worked with?

---

## 6. Hashtags

#MicrosoftEntra #AuthenticationStrength #ZeroTrust #MicrosoftSecurity #SecurityArchitect

---

## Day 9 Checklist

- [ ] Review draft — the AiTM (adversary-in-the-middle) observation is the sharpest practitioner point; add your own version if you have seen this in a real engagement or a customer breach post-mortem
- [ ] Consider referencing the four-post identity thread explicitly (PIM → Identity Protection → Conditional Access → Authentication Strength) or letting it stand alone
- [ ] The "tired user approving push notifications" line is relatable — keep or adjust to match your voice
- [ ] Post with graphic or personal photo
- [ ] Add follow-up comment within 30 minutes — consider noting that authentication strength can be applied to Conditional Access policies gradually, starting with the most sensitive resources
- [ ] Engage with any comments on Day 8 before posting
