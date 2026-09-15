# Day 76 — LinkedIn Content Package
**Topic:** Zero Trust for identity — the most foundational pillar
**Category:** Zero Trust / Identity Security / Microsoft Entra ID
**Week theme:** Zero Trust — principles, assessment, identity, and adoption (Days 74–77)
**Date:** 2026-08-19 (Wednesday)
**Format:** Technical article — Week 11 Day 3
**LinkedIn URL:** https://www.linkedin.com/pulse/zero-trust-identity-most-foundational-pillar-stuart-mann-d5wte
**LinkedIn post (shortlink):** https://lnkd.in/p/eTF8hmc5

---

## LinkedIn Article (published — 2026-08-19)

Zero Trust for identity: the most foundational pillar

In a world without a traditional perimeter, identity becomes one of your primary security control planes.

Not just the network edge. Not just the firewall.

Identity.

That shift has significant implications for what identity security needs to do, and for how mature your identity controls actually need to be.

Yesterday I looked at the Microsoft Zero Trust Assessment and how it gives you a baseline view of your tenant's current security posture.

Today I want to explain why identity is so foundational, and what the identity pillar in Zero Trust actually requires.

Why identity is foundational

Think about how access works today.

A user accesses email.

A workload calls an API.

An AI agent retrieves a document.

Each involves an identity requesting access to a resource, and that access needs to be authenticated and authorised appropriately.

Devices are slightly different. They have their own identities and provide signals that can influence access decisions made for users and applications.

If your identity controls are weak, the other Zero Trust pillars have to compensate.

You configure strong data controls; the challenge is that a legitimate user with sanctioned access gets compromised and your data is exposed.

Time spent defining and building good network segmentation becomes less effective if an over-privileged identity has access across multiple segments.

Device compliance alone doesn't prove that the person using the device can be trusted.

Identity is foundational because it sits at the centre of so many access decisions.

Microsoft's Zero Trust guidance reflects the need for strong identity controls and protection. Before an identity accesses a resource, Microsoft recommends verifying it with strong authentication, checking that the access is compliant and typical for that identity, and applying least privilege.

What the identity pillar requires

Microsoft structures its Zero Trust identity guidance around six deployment objectives.

The first is cloud identity integration with on-premises identity systems.

For organisations with hybrid identity, on-premises identities can be integrated with Microsoft Entra ID using technologies such as Microsoft Entra Connect Sync or Microsoft Entra Cloud Sync.

The terminology here is worth understanding.

Microsoft's Zero Trust deployment objective says that cloud identity federates with on-premises identity systems, but that does not mean every organisation needs to deploy a federated authentication service such as AD FS.

Microsoft's current direction is to move applications and authentication away from AD FS where appropriate, towards Microsoft Entra ID and cloud authentication.

Password Hash Synchronisation, Pass-through Authentication and federation are different authentication approaches.

What matters from a Zero Trust perspective is creating a strong identity control plane that can apply authentication, access and risk controls consistently.

And the configuration details matter.

Synchronisation scope, authentication methods, privileged accounts and hybrid identity architecture can all introduce risk if they aren't managed correctly.

Conditional Access

The second objective is Conditional Access policies that gate access and provide remediation activities.

Conditional Access is Microsoft's Zero Trust policy engine for access decisions.

It brings together signals such as:

* Identity
* Device
* Location
* Application or resource
* User and sign-in risk
* Authentication context
* Session information

Based on those signals, Conditional Access can block access or require controls such as stronger authentication, compliant devices or approved authentication strengths.

But there is an important distinction here.

Conditional Access isn't simply one policy covering every type of identity.

Users, workload identities and AI agent identities have different authentication patterns and different Conditional Access capabilities.

Conditional Access for workload identities can protect service principals.

Microsoft Entra Agent ID now provides specific Conditional Access capabilities for AI agents. AI agent capabilities will continue to expand within Conditional Access.

So when reviewing Conditional Access coverage, the question used to be:

"Do we have Conditional Access?"

It should now be more of:

"Which identities and resources are actually covered by our Conditional Access policies?"

That is a very different question, particularly as Microsoft expands Conditional Access beyond traditional user identities.

Analytics and visibility

The third objective is analytics and visibility.

You cannot manage what you cannot see.

Sign-in logs, audit logs, risk detections and identity-related reporting give you visibility into what is happening across your identity infrastructure.

Microsoft Entra workbooks can help analyse identity activity, while integration with Microsoft Sentinel and Defender XDR brings identity signals into your wider security operations.

This matters because Zero Trust is not simply about controlling access.

You also need to understand what happens after access is granted.

Identity governance

The fourth objective is identity governance.

This includes capabilities such as Privileged Identity Management (PIM), entitlement management, lifecycle workflows and access reviews.

PIM is worth calling out directly.

Applying the principle of least privilege to administrators means reducing unnecessary standing privileged access.

PIM supports eligible, time-bound role assignments, activation controls, approval, justification and other controls around privileged access.

If your Global Administrators, Security Administrators and other privileged roles are permanently assigned when they don't need to be, that is an area I would review.

Microsoft identifies roles containing privileged permissions as privileged roles. I would start by identifying which users hold those roles, then reviewing which assignments genuinely need to remain permanently active.

Entitlement management and access reviews then help address another common problem:

Access accumulates.

* People change jobs.
* People move teams.
* Projects finish.
* External users remain.
* Group memberships grow.
* Applications and identities retain permissions that nobody remembers granting.

Zero Trust requires us to challenge that access rather than assume that because somebody needed it once, they should keep it forever.

Strong and phishing-resistant authentication

Authentication also deserves its own place in the identity discussion.

Moving away from passwords towards stronger, phishing-resistant authentication significantly reduces one of the most common identity attack surfaces.

Microsoft supports methods including:

* Windows Hello for Business
* Passkeys (FIDO2)
* FIDO2 security keys
* Certificate-based authentication

Microsoft's passwordless strategy matters because passwordless authentication doesn't simply mean adding another factor to a password.

Methods such as Windows Hello for Business and FIDO2 use cryptographic credentials rather than sending a reusable password during authentication.

But there is a nuance.

A passwordless user experience does not necessarily mean that the underlying directory account no longer has a password.

For example, Microsoft's Windows passwordless experience can remove the password credential provider from normal user authentication while the identity directory still retains the password.

The goal is therefore bigger than simply enabling MFA.

Reduce the reliance on passwords and move towards phishing-resistant authentication.

Real-time risk analysis

The fifth deployment objective is real-time analysis of user, device, location and behaviour signals.

Microsoft Entra ID Protection detects identity risk using a range of signals.

Examples include:

* Atypical travel
* Unfamiliar sign-in properties
* Anonymous IP addresses
* Anomalous tokens
* Leaked credentials
* Threat intelligence associated with known threat actors

Some detections occur in real time, while others are calculated offline.

Risk-based Conditional Access can then use user risk and sign-in risk to make access decisions.

This is where Zero Trust becomes adaptive.

Instead of saying:

"This user authenticated successfully, therefore I trust them."

You can say:

"This authentication looks different from what we normally see. I need stronger verification, or I am going to block it."

Defender for Cloud Apps can add another layer by monitoring activity within supported cloud applications, identifying anomalous behaviour and applying session controls in supported Conditional Access scenarios.

Threat signal integration

The sixth objective is integrating threat signals from other security solutions.

Microsoft Defender for Identity monitors identity-related threats across Active Directory and supported identity infrastructure, providing detections and context around attacks involving credentials, privilege and lateral movement.

Microsoft Defender for Endpoint contributes device risk.

For example, Defender for Endpoint can pass device risk to Intune. Device compliance can then be evaluated and used by Conditional Access when deciding if access should be granted.

Defender XDR increasingly brings these identity and endpoint signals together for investigation and response.

Microsoft's current identity security experience combines information from Defender for Identity and Entra ID Protection to help analysts understand identity risk, permissions, relationships and activity.

This is what makes Zero Trust different from a collection of separate security products.

The signals need to work together.

Where AI agents fit

Last week I focused on Microsoft Agent 365 and how AI agents introduce another class of identity that we now need to govern.

The same Zero Trust principles apply.

Verify explicitly.

Use least privilege.

Assume breach.

Microsoft Entra Agent ID provides purpose-built identity constructs for AI agents and extends Entra capabilities into agent authentication, authorisation, governance and protection.

Conditional Access can target agent identities and agent identity blueprints.

Microsoft Entra ID Protection can detect risk associated with agent identities, and Conditional Access can block agents based on that risk.

Identity governance can also be extended to agents, including ownership, sponsorship, lifecycle and access management.

But agents shouldn't simply inherit policies designed for human users.

Microsoft specifically recommends creating agent-specific Conditional Access policies because agents cannot satisfy interactive controls such as MFA in the same way a person can.

This is an important change.

The identity pillar no longer stops with your employees, administrators and service principals.

AI agents now need to be part of your identity architecture as well.

Where to start

If you have run the Zero Trust Assessment from yesterday's article, start with the identity findings.

Look at what the assessment has actually found in your tenant and use the risk information and remediation guidance to help decide what needs attention.

If you haven't run the assessment, there are several areas I would look at first based on what I see in practice:

* Incomplete Conditional Access coverage.
* Permanent privileged role assignments that could use PIM.
* Weak authentication methods where phishing-resistant authentication could be deployed.
* Identity risk being detected but not used effectively for access decisions.
* Workload identities with excessive or poorly reviewed permissions.
* Agent identities operating without appropriate identity governance and access controls.

Start with what the data tells you.

Don't assume a control is working because somebody remembers configuring it.

Test what is actually there.

If you have used Entra ID Protection and risk-based Conditional Access in your organisation, what has been the most effective configuration change you have made to reduce identity risk?

---

## Microsoft Learn References

- [Zero Trust identity pillar deployment objectives](https://learn.microsoft.com/en-us/security/zero-trust/deploy/identity)
- [Zero Trust technology pillars overview](https://learn.microsoft.com/en-us/security/zero-trust/deploy/overview)
- [What is Privileged Identity Management?](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure)
- [What is Microsoft Entra ID Protection?](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)

---

## Hashtags

#ZeroTrust #MicrosoftEntra #IdentitySecurity #ConditionalAccess #PrivilegedIdentityManagement #MicrosoftSecurity #EntraID #Cybersecurity

---

## Notes

- Day 76 published post — Week 11 identity pillar deep dive.
- Stuart expanded the Conditional Access section significantly: the key framing "which identities are covered?" vs "do we have CA?" is new and stronger.
- Authentication moved to its own standalone section with nuance on passwordless user experience vs directory password.
- AI agents section expanded: agent-specific CA policies required because agents can't satisfy interactive MFA.
- "Where to start" list expanded to six areas including agent identities.
- Metrics check due: 2026-09-19
