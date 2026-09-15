# Day 16 — LinkedIn Content Package
**Topic:** Passkeys vs physical FIDO keys — not the same strategy
**Category:** Identity and Access
**Format:** Technical opinion post
**Status:** Rewritten to Stuart's voice — for review

---

## 1. Title

Passkeys vs physical FIDO keys: they're not the same strategy, and your privileged users prove it.

---

## 2. LinkedIn Post (Voice rewrite — for Stuart's review)

Passkeys vs physical FIDO keys: they're not the same strategy, and your privileged users prove it.

I'm seeing a lot of confusion in security teams right now. "We're moving to passwordless" often means "we're rolling out passkeys everywhere." That's not the full picture.

The real answer: it depends on the user tier and the threat model.

**Why passkeys work for standard users**

Passkeys improve the security posture for your entire user base. They eliminate password reuse, which is the root cause of most breaches, they're resistant to phishing, and they're frictionless enough that users actually adopt them. A 95% adoption rate with passkeys beats a 30% adoption rate with hardware tokens. That is the reality of security programmes; if users won't use the tool, the tool doesn't work.

Passkeys sync across devices via your cloud account, whether that's iCloud or Google. That convenience is the point. For someone checking email and accessing cloud apps, it's a significant step up from "Password123!" on a Post-it note.

Entra ID handles this well with Windows Hello and passwordless phone sign-in. You get Conditional Access and device compliance checks, and you're gradually moving away from passwords entirely.

**Why physical FIDO keys are the right choice for privileged users**

Now flip to your admins. Your service account operators. Your security team. Your finance team with access to banking systems.

A passkey lives on your device. If that device is compromised, through malware, a supply chain attack, or a stolen laptop, the passkey goes with it. An attacker who controls your machine can intercept the passkey at the moment it is used.

A physical FIDO key is fundamentally different. It's an isolated cryptographic processor. The private key never leaves the device. An attacker cannot steal it, cannot phish it, and cannot intercept it in transit because it doesn't pass through any other systems except the authentication protocol itself.

For privileged access, that isolation matters. You're protecting against sophisticated adversaries, determined insider threats, and advanced ransomware operators. A passkey doesn't cut it at that level.

**The threat model is the decider**

Standard users are low-risk targets. Phishing is the primary threat. Passkeys solve that.

Privileged users are high-value targets. You're dealing with APT-level sophistication, domain controller access, and financial wire authority. You need defence in depth: physical possession of the key, a PIN, and cryptographic binding to the specific service.

**Practical implementation**

Your Entra ID Conditional Access policy should enforce this separation:

* Standard users: passwordless phone sign-in or passkey, risk-based
* Privileged users: MFA plus a physical FIDO key, no exceptions

Yes, this means your privileged users carry hardware. Yes, there's a recovery process if they lose it. But you're protecting crown jewels. The friction is worth it.

I've also seen organisations require FIDO keys only for critical paths, Privileged Access Workstations and resource admin consoles, and allow passkeys for secondary access. That's a reasonable middle ground.

**The adoption reality**

Rolling this out requires clear messaging: standard users get convenience, privileged users get security. Most people understand that once it's explained. The ones who push back are usually the ones who should be asking themselves whether they actually need privileged access in the first place.

Budget for: FIDO key cost (£20 to £60 per key), replacement tokens, MDM integration, user training, and support overhead. For a 100-person organisation with 15 privileged users, you're looking at a couple of hundred pounds and a week of rollout work. Scale that up accordingly.

**Where I see this go wrong**

1. All passkeys, no physical keys: you've improved the baseline but left your crown jewels exposed.
2. All physical keys everywhere: you've created so much friction that users circumvent the system.
3. FIDO2 without Conditional Access: you have the hardware but no policy enforcement. Users forget to use it.
4. Recovery not planned: a user loses their key on day two. What happens next?

**The question I'd ask you**

What's your current privileged access story? Are you enforcing MFA on admin accounts? If you are, are you enforcing strong MFA, hardware-based rather than SMS? And if you're not, what's holding you back?

---

## 3. Microsoft Learn References

- Passkeys (FIDO2) in Microsoft Entra ID: https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless
- Conditional Access authentication strengths: https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths
- Plan a phishing-resistant MFA deployment: https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-plan-prerequisites-phishing-resistant-passwordless-authentication

---

## 4. Suggested Image Concept

Two-column graphic, dark background. Left: "Standard users — passkey, convenience, 95% adoption." Right: "Privileged users — physical FIDO key, isolation, no exceptions." Clean, no stock photos.

Alternative: Quote card — "If users won't use the tool, the tool doesn't work."

---

## 5. Hashtags

#MicrosoftEntra #Passwordless #FIDO2 #ZeroTrust #SecurityArchitect

---

## Day 16 Changes Made
- Removed "genuinely" (AI telltale)
- Removed "beautifully" (marketing language)
- Removed all m-dashes; restructured sentences to use commas
- "non-negotiable" removed (appeared twice in original)
- "organisations" not "organizations" throughout
- "cannot" as one word throughout
- "That's incomplete thinking" softened to "That's not the full picture"
- "defence in depth" UK spelling
- Tightened the threat model section
- Kept numbered list for "where it goes wrong" — matches Day 13 Eisenhower format
