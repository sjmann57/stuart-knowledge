# Day 67 — LinkedIn Content Package
**Topic:** Microsoft Agent 365 — the control plane for observing, governing and securing AI agents at scale
**Category:** AI Security / AI Governance / Microsoft Security
**Week theme:** Microsoft Agent 365 — AI agent governance (Days 67–70)
**Date:** 2026-08-11 (Monday — Week 10 opener)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (used in draft):**
Your organisation may already have dozens of AI agents running.

Some were deployed by IT. Some were built by business users. Some arrived via third-party platforms.

How many do you actually know about?

**Hook 2:**
AI agents are proliferating inside enterprise environments faster than most IT teams can track.

The question is no longer whether your organisation has agents.

It is whether you have visibility and control over the ones that are already there.

**Hook 3:**
There is a difference between allowing AI agents in your organisation and governing them.

Most organisations right now are doing the first.

Microsoft Agent 365 exists to help with the second.

---

## LinkedIn Article (published — 2026-08-11)
**LinkedIn URL:** https://lnkd.in/p/eFSKzuKm

Microsoft Agent 365: the control plane for observing, governing and securing AI agents at scale

Your organisation may already have dozens of AI agents running.

Some were deployed by IT. Some were built by business users using Copilot Studio or Agent Builder. Some arrived as part of third-party platforms that teams connected without involving IT at all.

How many do you actually know about?

This week I am starting a new series. After spending last week in Microsoft Defender for Cloud, I want to look at a product that I think is going to become one of the most significant conversations in enterprise security over the next twelve months.

Microsoft Agent 365.

Before I go any further, I want to be clear about what this is, because the name causes genuine confusion.

Microsoft Agent 365 is not a tool for building AI agents.

It is the control plane for IT and security leaders to observe, secure, and govern agents across the organisation.

Those are very different things.

What problem does it solve?

The organisations I speak with are at different stages of the AI agent journey. Some have deployed Microsoft 365 Copilot and are starting to see users build and publish agents. Others are still assessing the governance implications before opening things up. Most are somewhere in the middle.

What almost all of them share is this: they do not have a complete view of every AI agent operating inside their environment.

Microsoft calls this agent sprawl. Agents created in Copilot Studio. Agents built by individual users with Agent Builder. Agents published from SharePoint. Agents running on Microsoft Foundry. And increasingly, agents arriving via non-Microsoft platforms that have been connected by teams working independently of IT.

Each of those agents is operating with access to data, tools and services inside your organisation.

Without centralised visibility, you cannot govern what you cannot see.

Microsoft Agent 365 is the product built to address that.

Three pillars: Observe, Govern, Secure

Microsoft describes Microsoft Agent 365 around three pillars, and they are the right framework for understanding what the product does.

Observe.

The Agent overview in the Microsoft 365 admin centre, accessed at admin.cloud.microsoft under Agents, gives administrators a centralised view of all agents operating in the tenant.

The dashboard provides a snapshot of agent activity across the last thirty days, an agent registry broken down by source and platform, usage trends, and governance signals requiring attention.

The platform breakdown is where this becomes immediately relevant for security teams. The registry surfaces agents built on Copilot Studio, Agent Builder, the Agents Toolkit, SharePoint and Microsoft Foundry. It also covers connected non-Microsoft platforms.

If agents have arrived in your environment via third-party routes that IT did not approve, this is where they will appear.

Key governance signals in the dashboard include agents without assigned owners, agents flagged as at risk by connected security platforms, pending approval requests, and agents generating errors.

That last category matters in a way that practitioners will recognise immediately. An agent without an owner carries the same governance risk as a service account without an owner. When the person who built it leaves the organisation, nobody is accountable for what it continues to do.

Govern.

Microsoft Agent 365 is designed to bring agents under IT oversight from the point of onboarding, rather than retrospectively after sprawl has already occurred.

Administrators can require agents to go through an IT-controlled approval workflow before they are made available to the wider organisation. Policy templates can be applied at onboarding, enforcing governance and compliance requirements consistently across every agent regardless of where it was built.

Access control is central to the governance model. The principle of least privilege applies to agents in exactly the same way it applies to users and service accounts. Agents should only have access to the resources, data and tools they genuinely require. Controlling that from the start is significantly easier than trying to restrict access after an agent has already been deployed and is being actively used.

The audit capability is also worth calling out directly. If your organisation is subject to regulatory requirements around AI systems, the ability to demonstrate that agents are governed, monitored and subject to compliance controls will become a requirement rather than a recommendation.

Secure.

The security layer within Microsoft Agent 365 extends existing infrastructure to agents. That is the key framing.

Rather than introducing a separate security stack, Microsoft Entra, Microsoft Defender and Microsoft Purview have each been extended with purpose-built controls for agents.

Entra gives administrators visibility into agent identities. Agents can be assigned an Entra Agent ID, bringing them under the same identity and access management infrastructure used for users and service accounts. Conditional Access policies can be extended to agents, enforcing access decisions based on agent context, risk level and resource sensitivity.

Agents without an Entra Agent ID are effectively shadow agents. They may be running, accessing data and performing actions inside your environment without the identity controls you would normally apply.

Microsoft Defender now includes purpose-built agent controls: security posture management for agents, detection of suspicious agent activity, real-time blocking of malicious tool invocations, and threat investigation and hunting across agent activity logs. This is surfaced inside the Microsoft Defender portal, not a separate product.

Microsoft Purview extends data security controls to agent interactions. Sensitivity labels are inherited and honoured by agents, data loss prevention policies apply to what agents can access and share, and all agent activity can be audited for compliance and forensic investigation.

The framing I find most useful here is this: Microsoft Agent 365 does not introduce a new security stack for agents. It extends the security infrastructure many organisations have already built, and applies it to a new category of identity that most have not yet brought under control.

Where to look today

Open the Microsoft 365 admin centre at admin.cloud.microsoft and navigate to Agents, then Overview.

Access to the full Agent 365 dashboard depends on your organisation's licensing. Microsoft Agent 365 is available as a standalone licence and is also included in Microsoft 365 E7.

Start with two questions.

First, what is actually there? Review the agent registry and understand which platforms are represented. Look particularly for agents from sources that IT did not provision directly.

Second, what are the governance gaps? Agents without owners and agents flagged as at risk are the most immediate signals requiring action. Pending approval requests indicate that agents are being published without going through an IT-controlled flow.

Knowing the controls exist is not the same as having them configured.

The week ahead

This week I will continue looking at Microsoft Agent 365, including how the identity, data security and threat protection capabilities work in practice.

AI agent governance is one of the fastest-moving areas of the Microsoft security platform right now. The Entra, Defender and Purview integrations each deserve a closer look, and I will cover them through the week.

The organisations that establish centralised visibility and governance over agents early will be in a significantly stronger position than those that wait until agent sprawl has already created a problem they are trying to manage retrospectively.

Does your organisation currently have a centralised view of the AI agents operating in your tenant, or is that still a gap?

---

## Microsoft Learn References

- [Microsoft Agent 365 documentation overview](https://learn.microsoft.com/en-us/microsoft-agent-365/)
- [Agent management in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-365-overview)
- [Secure AI agents at scale using Microsoft Agent 365](https://learn.microsoft.com/en-us/security/security-for-ai/agent-365-security)

---

## Hashtags

#MicrosoftAgent365 #AIGovernance #MicrosoftSecurity #AgentSecurity #AIAgents #MicrosoftEntra #ZeroTrust #MicrosoftDefender

---

## Accuracy Notes (for future articles)

- **Product name:** "Microsoft Agent 365" — NOT "agents for Microsoft 365 Copilot." These are entirely different products. Agent 365 is the IT/security control plane; "agents for M365 Copilot" is about building agents. Do not shorten to "Agent 365" in article prose — use "Microsoft Agent 365" in full.
- **Three pillars:** Observe / Govern / Secure. This is the official Microsoft framing confirmed in the MS Learn documentation.
- **Portal path:** admin.cloud.microsoft → Agents → Overview. The "Agent workload" is described as "the grounding control plane for all agents managed at your organisation."
- **Agent registry platforms confirmed:** Copilot Studio, Agent Builder (Teams/Copilot Studio Legacy), Agents Toolkit, SharePoint, Microsoft Foundry V2. Non-Microsoft platforms can also appear via Registry sync — examples named in docs include Manus and Genspark.
- **Agents without owners:** Named as a specific governance risk category in the dashboard. Surfaced as "Agents without owners" — admins assign ownership. Risk: accountability gap when the original builder leaves.
- **Agents at risk:** Defined as "aggregated high severity risks across Microsoft security platforms such as Microsoft Entra, Microsoft Defender, and Microsoft Purview." Surfaced in the dashboard governance card.
- **Entra Agent ID:** Agents can be assigned an Entra Agent ID. Those without one are effectively shadow agents — running without identity governance controls.
- **Shadow agents framing:** Confirmed terminology — the Entra security page references "shadow agents" as agents without proper Entra identity registration. Parallel to shadow IT is accurate and useful.
- **Conditional Access extended to agents:** Confirmed — "Extend conditional access and identity protection policies from users to agents." This is significant for practitioners who already work with CA.
- **SASE for agents:** Entra Global Secure Access can monitor and block malicious/non-compliant network traffic from agents running on user devices, including Copilot Studio agents.
- **Defender — what is covered:** Agent security posture management (misconfigurations, attack paths), threat detection and blocking (suspicious activity, real-time blocking of malicious tool invocations), threat investigation and hunting (unified agent observability logs). All surfaced in Microsoft Defender XDR portal.
- **Purview — what is covered:** Data security posture management, sensitivity labels (agents inherit and honour them), DLP, insider risk management, communication compliance, auditing, data lifecycle management, eDiscovery, Compliance Manager for AI regulation assessments.
- **Licensing:** Microsoft Agent 365 is a standalone licence. Also included in Microsoft 365 E7. Some capabilities may require Frontier program access (Microsoft's early access programme for emerging M365 capabilities) — caveat where needed in future precision articles.
- **What the admin centre article says about draft agents:** Currently, only draft agents from Copilot Studio are visible in the registry. Other platforms (Agent Builder, Foundry, SharePoint) do not surface draft/unpublished agents yet. Do not claim full draft visibility.
- **Agent types in the registry:** MCS DA (declarative), MCS CEA (custom engine), MCS BP (business process), Foundry LOB, Foundry non-LOB, Foundry hosted, Agent Builder, SharePoint, Agent Toolkit, Agent instance (Agent 365 SDK). If listing agent types, use these official names.
- **Governance actions in dashboard:** Approve pending agent requests / Assign ownership to agents without owners / Investigate and remediate agents at risk / Review agents with exceptions. Only AI Administrator or Global Administrator roles can take these actions (not just view).
- **Metrics timing note:** Active users, agent run-time, and agents with exceptions metrics only begin from Agent 365 licence activation — early after activation, less than 30 days of data will be visible.
- **Week 10 arc:** Days 67–70 covering Microsoft Agent 365. Day 67 = control plane overview (this article). Days 68–70 TBD — candidates: Entra Agent ID and Conditional Access for agents / Purview data security for agents / Defender threat protection for agents.
- **No MVP tracker entry yet** — will add when article is confirmed for publication.
- **Week 10 theme updated:** Previous plan was "Microsoft 365 Copilot and AI agents" — corrected to "Microsoft Agent 365 — AI agent governance." The original Day 67 draft (about building agents with M365 Copilot) is now superseded. That content may be useful for a different day, but Day 67 is definitively about Microsoft Agent 365.
