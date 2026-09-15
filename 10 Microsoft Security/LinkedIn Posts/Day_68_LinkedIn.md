# Day 68 — LinkedIn Content Package
**Topic:** Microsoft Entra Agent ID — giving AI agents an identity your policies can actually enforce
**Category:** AI Security / Identity / Microsoft Entra
**Week theme:** Microsoft Agent 365 — AI agent governance (Days 67–70)
**Date:** 2026-08-12 (Tuesday)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (used in published):**
You have Conditional Access policies for your users.

You probably have policies covering your service accounts and workload identities.

Do you have policies for your AI agents?

**Hook 2:**
Your organisation's AI agents are accessing SharePoint, email, and APIs.

In most cases, those agents have no identity in Microsoft Entra.

No identity means no policy. No policy means no control.

**Hook 3:**
When a user accesses a corporate resource, Conditional Access evaluates that request.

When an AI agent accesses the same resource, most organisations have nothing in place.

Microsoft Entra Agent ID is built to close that gap.

---

## LinkedIn Article (published — 2026-08-12)

Microsoft Entra Agent ID: Giving AI agents an identity your policies can actually enforce

You have Conditional Access policies for your users.
You probably have policies covering your service accounts and workload identities.
Do you have policies for your AI agents?

Yesterday I introduced Microsoft Agent 365 as the control plane for observing, governing and securing agents across the organisation.
Today I want to go deeper into one of the most important parts of that picture: identity.

Because one of the biggest security gaps with AI agents is an agent operating without an identity your security controls can govern.

What is Microsoft Entra Agent ID?

Microsoft Entra Agent ID provides identity, access management and governance capabilities designed specifically for AI agents.

Agent identities are distinct identity objects within Microsoft Entra ID that give AI agents their own identification and authentication capabilities.

Microsoft Entra Agent ID provides the identity foundation for AI agents within Microsoft environments, but extending capabilities such as Conditional Access, Identity Protection and network controls to agents has additional licensing requirements.

Organisations should treat Agent ID and agent security controls as related but separately licensed capabilities.

Unlike human user identities or traditional workload identities, agent identities are designed around the way AI agents operate: autonomously, on behalf of users, and increasingly as digital workers interacting with enterprise systems.

The platform uses established identity standards, including OAuth 2.0, while also supporting agent protocols such as MCP and A2A.

Most importantly for security teams, Microsoft is extending the controls we already use in Entra to agents.

That includes Conditional Access.

How agents access resources

Before you build identity and access policies for agents, you need to understand how the agent operates.

There are three scenarios worth separating.

The first is an agent acting on behalf of a user.

The agent accesses resources using delegated permissions associated with the signed-in user. An agent accessing Microsoft Graph, SharePoint or another API on behalf of someone is an example.

The user's identity remains part of the authorisation chain. Existing user Conditional Access policies continue to protect the user's sign-in and delegated access.

Agent-based Conditional Access policies, however, apply when agents access resources using their own identity rather than when acting on behalf of a user.

The second is an autonomous agent.

Here, the agent operates without an interactive user and uses its own agent identity to request access to resources.

This could be an agent executing scheduled tasks, generating reports, processing events or interacting with APIs in the background.

For autonomous agent identities, the Conditional Access grant control currently available is Block access.

Because there is no interactive user session, controls such as MFA or device-compliance requirements cannot be satisfied directly by the agent.

This makes the policy model different from Conditional Access for human users.

The third is an agent's user account.

Microsoft supports agents that operate through user-like identities. These might represent digital workers that need access to resources normally associated with users.

Conditional Access treats these separately from agent identities and provides targeting for agent users.

That distinction matters.

A Conditional Access policy targeting an agent identity does not automatically apply to its associated agent user account.

Each access model needs to be understood when you design the policy.

Licensing reality check

Before you get too excited about agent Conditional Access, there is an important licensing consideration.

Microsoft Entra Agent ID itself is available to Microsoft Entra customers. Extending Entra security capabilities to those agents requires additional licensing.

Microsoft 365 E7 includes Microsoft Agent 365 and Microsoft Entra Suite. Microsoft 365 E5 customers can pair E5 with Microsoft Agent 365.

For organisations using standalone Entra licensing with Microsoft Agent 365:

* Conditional Access for agents requires Microsoft Entra ID P1.
* Identity Protection for agents requires Microsoft Entra ID P2.
* ID Governance for agents requires Microsoft Entra ID P1.
* Network controls require Microsoft Entra Internet Access.

Microsoft currently states that enforcement of the Microsoft Agent 365 licensing requirement for Conditional Access for agents is coming soon. In my test tenant, I was already blocked while the licensing warning was displayed.

That last point is important because this is a fast-moving area of the Microsoft platform.

In other words, validate the current licensing model before designing agent security controls around features you may not be licensed to enforce. For planning purposes, assume you will need Microsoft 365 E7 or Microsoft Agent 365 alongside the appropriate Entra licensing.

Scaling governance with attributes

Managing individual agent identities inside Conditional Access policies will quickly become difficult as organisations deploy hundreds or potentially thousands of agents.

This is where custom security attributes become useful, but there is an important distinction to understand.

Custom security attributes help determine which agent identities a Conditional Access policy targets. They are not additional Conditional Access conditions.

For example, Microsoft Entra allows you to classify agent identities using attributes such as:

* Environment
* Department
* DataSensitivity

You might assign an agent:
Environment = Production
Department = Finance
DataSensitivity = Confidential

You can then use those attributes when selecting the agent identities that a Conditional Access policy applies to.

Instead of manually selecting fifty production agents, for example, you could target agent identities classified as Environment = Production. New agent identities given the same classification can then fall within the scope of the policy without administrators continually adding them individually.

The distinction between targeting and conditions is important.

For an autonomous agent identity, Conditional Access currently has a much more limited set of controls than it does for a human user. Once you have selected which agent identities the policy applies to, Agent risk is currently the agent-specific condition available, and Block access is the available grant control.

So a policy could effectively say:
Target: Agent identities where Environment = Production
Condition: Agent risk = High
Control: Block access

Agent users are different.

An agent user is a user-like identity associated with an agent. Conditional Access provides additional conditions for agent users, including Agent execution environments, Device platforms, Filters for devices, and Agent risk.

A Conditional Access policy targeting an agent identity does not automatically apply to its associated agent user account. The two need to be considered separately when designing your policies.

Agent identity blueprints provide another way to scale policy targeting.

Conditional Access can target an agent identity blueprint, automatically covering the agent identities created from that blueprint, including new identities created later.

So there are effectively two ways to avoid managing agents individually:

Attributes classify agent identities and allow policies to target agents matching those classifications.

Blueprints allow a policy to cover the family of agent identities created from that blueprint.

The important point is scale.

You need a governance model that continues to work when you have hundreds or thousands of agents rather than twenty.

That moves agent security away from individual administration and towards policy-driven governance.

Agents using API keys can sit outside this control.

This is an important boundary to understand.

Conditional Access protects resources secured by Microsoft Entra ID.

If an agent accesses a resource using an API key instead, that authentication does not go through the Microsoft Entra token issuance process.

Conditional Access therefore does not apply to that access.

That matters because many agents connect to third-party APIs, custom applications, SaaS platforms and other services using credentials that Microsoft Entra does not control.

The agent may still have an Entra Agent ID for other purposes, but that does not magically bring every API call the agent makes under Conditional Access.

You need to understand the authentication method used for each resource the agent accesses.

Agent identity is only useful as a security boundary when the resource participates in that identity model.

Agent lifecycle and ownership

Identity is also about accountability.

Before looking at ownership, it is useful to understand where agent identity blueprints fit.

In Microsoft Entra ID, an agent identity blueprint acts as the parent definition from which individual agent identities can be created.

You can see these under:
Entra ID → Agents → Agent blueprints

A blueprint can have multiple agent identities linked to it, giving you a way to group agents built for a common purpose and manage aspects of their identity consistently.

For example:
Security Reporting Blueprint
→ Security Reporting Agent 01
→ Security Reporting Agent 02
→ Security Reporting Agent 03

This relationship also becomes part of the governance model.

Microsoft Entra Agent ID introduces several administrative relationships around agents and their blueprints.

Owners handle technical administration.

Sponsors provide business accountability for the agent's purpose and lifecycle decisions.

Managers can represent responsibility for agents within the organisational hierarchy and support governance processes such as requesting access packages for agents that report to them.

Microsoft requires at least one sponsor for each agent identity and agent identity blueprint.

That gives us something we have struggled with for years with service accounts:

Who actually owns this identity?

Microsoft Entra ID Governance can then extend that model with capabilities including access packages and lifecycle workflows.

For me, this is an important part of Agent ID.

Creating an agent identity is only the start.

You also need a way to decide who is accountable for it, what it can access, how that access is reviewed and what happens when the agent is no longer required.

Otherwise, we risk repeating the same problem we already have with old service accounts and workload identities.

They get created.
They get permissions.
The original project finishes.
Nobody removes them.
Three years later, nobody knows why they still exist.

We should not repeat that model with AI agents.

Identity Protection for agents

Microsoft has also extended Entra ID Protection capabilities to agent identities.

Identity Protection evaluates agent activity for indicators of compromise and raises risk detections that can be reviewed through the Risky Agents experience.

Security teams can investigate risky agents and respond by confirming an agent as compromised, confirming it as safe, dismissing the risk or disabling the agent.

You can then combine agent risk with Conditional Access.

For example:
If Agent Risk = High → Block access.

That starts to make agent identity part of the same Zero Trust decision process we already apply to human identities.

It is worth remembering that Conditional Access for agent identities is currently more limited than Conditional Access for human users.

You should think of it primarily as a mechanism for restricting or blocking autonomous agent access rather than expecting full feature parity with user-based Conditional Access.

And licensing matters here as well.

Conditional Access for agents requires Microsoft Entra ID P1 alongside the applicable Agent 365 licensing.
Identity Protection for agents requires Microsoft Entra ID P2 alongside the applicable Agent 365 licensing.

These capabilities are developing quickly, so licensing and feature status should be checked against the current Microsoft documentation when designing your architecture.

Where to look today

Start in the Microsoft Entra admin centre.

Go to:
Entra ID → Agents → Agent identities

From there, you can review agent identities in your tenant and examine information such as their status, owners, sponsors, permissions and sign-in activity.

But do not confuse this with the old Entra Agent Registry.

Microsoft retired the Agent Registry and Agent Collections blades from the Entra admin centre on 1 May 2026.

Microsoft Agent 365 is now the unified agent registry and control plane, with the wider agent inventory available through the All agents experience in the Microsoft 365 admin centre.

That separation is useful to understand:

Microsoft Agent 365 gives you the wider control plane and inventory.
Microsoft Entra Agent ID provides the identity foundation.

Then review your Conditional Access design.

Ask:

* Which agents act on behalf of users?
* Which operate autonomously?
* Which use agent user accounts?
* Which agents have dedicated Conditional Access policies?
* Could agent identity blueprints or attributes simplify your policies?
* Which agents use API keys or authentication outside Entra?
* Who owns and sponsors each agent identity?
* What happens when an agent becomes high risk?
* What happens when the agent is retired?

This is infrastructure work, not a policy toggle.

And it is worth addressing before the number of agents in your organisation starts growing faster than your ability to govern them.

Tomorrow I will look at the data security side of Microsoft Agent 365. How Microsoft Purview helps govern the data agents interact with, how activity can be audited, and where the security boundaries sit.

Does your organisation currently have a plan for governing AI agent identities, or are agents still operating largely outside your identity and access management processes?

---

## Microsoft Learn References

- [What is the Microsoft agent identity platform](https://learn.microsoft.com/en-us/entra/agent-id/what-is-agent-id-platform)
- [Conditional Access for agent identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/agent-id)
- [Protect agent identities with Microsoft Entra](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/capabilities-entra)

---

## Hashtags

#MicrosoftEntra #AgentIdentity #ConditionalAccess #AIGovernance #ZeroTrust #MicrosoftSecurity #MicrosoftAgent365 #IdentityAndAccess

---

## Accuracy Notes (for future articles)

- **Microsoft Entra Agent ID vs Microsoft Agent 365 licensing (critical):** Entra Agent ID itself is available to all Microsoft Entra customers. Extending security capabilities (CA, ID Protection, Governance) to agents requires additional licensing. Do not conflate the two.
  - M365 E7 = includes Agent 365 + Entra Suite
  - M365 E5 = can pair with Microsoft Agent 365 as add-on
  - Conditional Access for agents = requires Entra ID P1 + Agent 365
  - Identity Protection for agents = requires Entra ID P2 + Agent 365
  - ID Governance for agents = requires Entra ID P1 + Agent 365
  - Network controls = requires Entra Internet Access + Agent 365
  - Enforcement of Agent 365 licensing for CA "coming soon" per Microsoft — Stuart was already blocked in test tenant with licensing warning displayed. Validate before designing.
- **Three access patterns (clarified from published version):**
  1. On-behalf-of user (OBO/delegated) — CA evaluated against user; existing user CA policies provide some protection; agent-specific CA applies when agent uses own identity, NOT in OBO flow
  2. Autonomous agent (application-only) — CA evaluated against agent identity; BLOCK ACCESS is the only available grant control (no interactive user to satisfy MFA/device compliance)
  3. Agent user account (digital worker) — Conditional Access provides additional conditions vs autonomous agents: Agent execution environments, Device platforms, Filters for devices, Agent risk; CA targeting agent identity ≠ automatically covers agent user account
- **Custom security attributes = targeting, NOT conditions:** Stuart's key clarification. Attributes (Environment, Department, DataSensitivity) are used to SELECT which agent identities a policy targets. They are NOT additional CA conditions. Example attributes confirmed: Environment, Department, DataSensitivity.
- **Agent identity blueprint (confirmed structure):**
  - Navigation: Entra ID → Agents → Agent blueprints
  - Blueprint = parent definition; agent identities = instances derived from it
  - Example: Security Reporting Blueprint → Agent 01 / Agent 02 / Agent 03
  - CA targeting a blueprint automatically covers all derived agent identities including future ones
- **Two scaling mechanisms for CA:** (1) Attributes — classify agents, target policies by classification; (2) Blueprints — target the blueprint, covers all derived agent identities
- **Agent lifecycle governance — three roles:**
  - Owners = technical administration
  - Sponsors = business accountability (Microsoft REQUIRES at least one sponsor per agent identity AND per blueprint)
  - Managers = organisational hierarchy / access package requests
  - Entra ID Governance: access packages + lifecycle workflows for agents
  - Stuart's service account parallel: "They get created. They get permissions. The original project finishes. Nobody removes them. Three years later, nobody knows why they still exist." — strong reuse framing.
- **Risky Agents experience:** Named explicitly. ID Protection raises detections reviewable in "Risky Agents." Response options: confirm compromised / confirm safe / dismiss risk / disable agent. Can combine with CA: Agent Risk = High → Block access.
- **Agent Registry retirement (critical accuracy note):** Microsoft retired the Agent Registry and Agent Collections blades from the Entra admin centre on 1 May 2026. Navigation for agent identities is now: Entra ID → Agents → Agent identities. Microsoft Agent 365 (Microsoft 365 admin centre → All agents) is the unified inventory and registry.
- **API key bypass:** Confirmed and framed precisely. "The agent may still have an Entra Agent ID for other purposes, but that does not magically bring every API call the agent makes under Conditional Access." — practitioner-level framing. Good reuse candidate.
- **MCP and A2A protocols:** Named explicitly as agent-specific protocols alongside OAuth 2.0. Both confirmed supported by the platform.
- **CA feature parity caveat:** "Conditional Access for agent identities is currently more limited than Conditional Access for human users. Think of it primarily as a mechanism for restricting or blocking autonomous agent access rather than expecting full feature parity." — important for practitioners who assume parity.
- **Stuart tested in own tenant:** He personally tested agent CA in his tenant and confirmed being blocked with licensing warning. Authentic practitioner insight — real-world validation.
- **Navigation confirmed (Entra):** Entra ID → Agents → Agent identities (for agent identities); Entra ID → Agents → Agent blueprints (for blueprints)
- **Week 10 arc:** Day 67 (overview) → Day 68 (identity/Entra, published) → Day 69 (data/Purview) → Day 70 (threats/Defender). Day 68 previews Day 69 explicitly.
- **No MVP tracker entry yet** — will add when confirmed.
