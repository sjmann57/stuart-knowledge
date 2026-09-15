# Day 6 — LinkedIn Content Package
**Topic:** Entra ID Privileged Identity Management — licenced, but not working
**Category:** Identity and Access
**Framework:** Microsoft Guidance vs Real-World Implementation
**Format:** Research-backed article (Day 6+ format)
**Status:** Stuart's rewrite — fact-checked

---

## 1. Title

PIM is licensed. Does that mean it is working?

---

## 2. LinkedIn Post — Full Version (Stuart's, ~600 words)

*(Full version — use as LinkedIn Article or trim to short version below)*

PIM is licensed. Does that mean it is working?

There is a question I ask in almost every security assessment I run. Who has Global Administrator role rights right now? Not who is assigned the role. Who has it active right now, and why?

The answer is usually the same. Several people. Permanently. Because it was easier to leave it that way.

Leaving your front door open is convenient; you don't need a key to get in, but it's easy access for everyone else as well.

Microsoft Entra Privileged Identity Management, PIM for short, was designed to address that problem.

Microsoft Learn defines it as: "Privileged Identity Management (PIM) is a service in Microsoft Entra ID that enables you to manage, control, and monitor access to important resources in your organisation. These resources include resources in Microsoft Entra ID, Azure, and other Microsoft Online Services such as Microsoft 365 or Microsoft Intune."

No unnecessary standing access and no forgotten admin accounts sitting with a permanent Global Administrator.

The concept is straightforward. The reality of deployment is another thing entirely.

Microsoft's guidance on PIM is clear. Highly privileged roles such as Global Administrator should be managed through just-in-time access to meet zero-trust requirements, with emergency access accounts retained for break-glass scenarios. I would recommend that highly privileged accounts be activated for no more than 1 hour. Security Administrator and other high-privilege roles should follow the same pattern. Access reviews should run regularly to catch eligible assignments that are no longer needed. The audit history covering the last 30 days should be reviewed weekly.

That is what the documentation says. What I often find when I arrive somewhere is one of three things.

The first is that PIM is licensed because it comes with Microsoft Entra ID P2 and has never been configured. The privileged roles are still on permanent active assignments. The intention to deploy PIM exists; it simply hasn't happened yet, usually because there is always something more urgent, or you tested it and it felt too inhibiting to use.

The second is that PIM has been partially deployed. The lower-privilege roles are eligible. The Global Administrator and Security Administrator accounts remain permanently active because activating them through PIM felt too disruptive. This is, of course, the wrong way around. Those are precisely the roles PIM was designed to protect first.

The third, and the one that looks fine until you look more carefully, is that PIM is deployed correctly for the roles, but access reviews are not running. Eligible assignments accumulate over time. People change roles, leave the organisation, or no longer need access, but without a structured review process, eligible assignments remain. Eventually, you have a list of eligible users for sensitive roles who haven't been checked in for 2 years.

I have seen a real mix of the above scenarios, and a few more I could talk about. The majority get stuck at the first stage; they have licences, but never get beyond a bit of testing. I have worked with organisations that have experienced security breaches, and suddenly there is an urgent need to enable PIM. Having a strategy that meets your business and team's needs makes PIM far easier to deploy and more likely to succeed.

The fix for all three is not complicated, but it does require proper prioritisation.

The licence is already in place for most organisations with Entra ID P2 bundled into their licensing. What it does require is someone making the decision that standing privileged access is a risk worth addressing, and then actually doing it.

Is PIM deployed across your privileged roles?

Or are you relying on trust, permanent assignments, and the hope that nobody ever compromises an admin account?

---

## 3. LinkedIn Post — Short Version (~300 words)

*(Trimmed for a standard LinkedIn post. All key points kept; the three patterns compressed.)*

PIM is licensed. Does that mean it is working?

There is a question I ask in almost every security assessment I run. Who has Global Administrator role rights right now? Not who is assigned the role. Who has it active right now, and why?

The answer is usually the same. Several people. Permanently. Because it was easier to leave it that way.

Leaving your front door open is convenient; you don't need a key to get in, but it's easy access for everyone else as well.

Microsoft Entra Privileged Identity Management was designed to address that problem. Just-in-time access, approval workflows, time-limited activation, access reviews. The licence is already in place for most organisations with Entra ID P2 bundled into their Microsoft 365 licensing.

The concept is straightforward. The deployment reality is another thing entirely.

What I find when I arrive somewhere falls into one of three patterns. PIM is licensed but never configured, because there was always something more urgent. PIM has been partially deployed, but the Global Administrator and Security Administrator accounts are still permanently active, because activating them through PIM felt too disruptive; those are, of course, exactly the roles PIM was designed to protect first. Or PIM is configured correctly for the roles, but access reviews are not running, and eligible assignments have been accumulating for two years without anyone checking them.

The majority get stuck at the first stage. They have licences, but never get beyond a bit of testing. Having a strategy that meets your business and team's needs makes PIM far easier to deploy and more likely to succeed.

The fix is not complicated. It requires someone making the decision that standing privileged access is a risk worth addressing, and then actually doing it.

Is PIM deployed across your privileged roles?

Or are you relying on trust, permanent assignments, and the hope that nobody ever compromises an admin account?

---

## 3. Microsoft Learn References

- What is Privileged Identity Management: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure
- Plan a PIM deployment: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-deployment-plan
- PIM for Groups: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/concept-pim-for-groups

---

## 4. Suggested Image Concept

Clean graphic, dark background. Large text: "Who has Global Admin right now?" Below it, in smaller text: "Not who is assigned it. Who has it active, right now, and why?" Small Microsoft Entra ID logo bottom-right.

Alternative: A simple two-column visual. Left: "Permanently Active — no justification, no expiry, no audit trail." Right: "Eligible + JIT — MFA required, approval required, one-hour window, full audit."

---

## 5. Alternative Discussion Questions

1. Is PIM deployed across your privileged roles, or is it still on the backlog?
2. What was the reason PIM deployment kept getting delayed in your organisation?
3. Have you run an access review recently and found eligible assignments that should no longer be there?

---

## 6. Hashtags

#MicrosoftEntra #PrivilegedIdentityManagement #ZeroTrust #MicrosoftSecurity #SecurityArchitect

---

## Day 6 Checklist

- [ ] Consider adding attribution to the Microsoft quote (see fact-check notes)
- [ ] Post with graphic or personal photo
- [ ] Add follow-up comment within 30 minutes
- [ ] Engage with any comments on Days 4 and 5 before posting

