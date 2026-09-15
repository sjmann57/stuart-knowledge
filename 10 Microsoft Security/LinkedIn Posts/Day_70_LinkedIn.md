# Day 70 — LinkedIn Content Package
**Topic:** Microsoft Defender threat protection for AI agents — detection, real-time blocking, posture management, and investigation
**Category:** AI Security / Threat Protection / Microsoft Defender XDR
**Week theme:** Microsoft Agent 365 — AI agent governance (Days 67–70) — Week 10 close
**Date:** 2026-08-14 (Thursday)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (used in published):**
A user who clicks on a malicious link makes a decision.

An AI agent that processes malicious content embedded in a file, an email, or a tool response has no choice in the matter; it follows instructions.

**Hook 2:**
Your security operations team knows how to investigate a compromised user account.

Do they know how to investigate a compromised AI agent?

**Hook 3:**
Microsoft Defender can now block a malicious AI agent action before it executes.

Not after the fact. Before.

That is a different kind of control from anything available a year ago.

---

## LinkedIn Article (published — 2026-08-14)

Microsoft Defender threat protection for AI agents: Detection, real-time blocking, posture management, and investigation

A user who clicks on a malicious link makes a decision.
An AI agent that processes malicious content embedded in a file, an email, or a tool response has no choice in the matter; it follows instructions.
It reads the content. It processes the instructions. It may then invoke a tool.
The AI agent, which may now be acting on an attacker's instructions, is part of the threat model that Microsoft Defender is being extended to address.

As the final article in my week series on Microsoft Agent 365 comes to a close, the articles have drawn more questions than others. Also, more questions have been raised that need answers and that I hope will follow in future weeks.

To recap, this week I covered the control plane for AI agent governance on Monday, Identity and Conditional Access on Tuesday, data security and Purview on Wednesday, and today I want to look at threat detection and response.

Before we start, let's look at the minimum licensing needed, as we have done before. Requirements and licensing can change quickly, so always check what is needed for your scenario.

For the Agent 365 security capabilities covered in this article, you need an Agent 365-eligible licence. Since 1 July 2026, Copilot Studio and Microsoft Foundry agent-level discovery and posture, threat protection and Agent 365-powered investigation are no longer covered by Defender for Cloud Apps or Defender for Cloud licences alone.

The AI agent threat landscape

Microsoft describes several threat categories associated with AI agents.

Agent sprawl expands the attack surface. User-created and SaaS agents can accumulate across the organisation, potentially without appropriate authentication or security boundaries.

Over-privileged agents have excessive access to resources. When an agent accumulates permissions beyond what its purpose requires, compromise or misuse of that agent can increase the potential blast radius.

Tool misuse happens when agents are manipulated into abusing tools they have legitimately been authorised to use.

Prompt injection is one of the attack categories associated with AI systems. An attacker can embed malicious instructions inside content that the agent processes, be it in a document, an email, a web page or a tool response, with the intent to manipulate the agent's behaviour.

Indirect prompt injection, also referred to as XPIA, takes this further.

The malicious instructions aren't necessarily in the user's prompt. They can be in content the agent retrieves and processes during its operation.

These aren't simply theoretical attack scenarios.

They are among the threats Microsoft Defender is now being designed to detect, investigate and, for supported scenarios, block before an unsafe action executes.

Agent security posture

The starting point in Microsoft Defender is the AI Agents inventory.

In the Microsoft Defender portal, navigate to:
Assets → AI agents → Agents

This gives you a centralised inventory of agents across your organisation, including agents built with Microsoft Copilot Studio, Microsoft Foundry, Microsoft 365 and supported non-Microsoft platforms.

Local AI agents running on endpoint devices can also be discovered when AI agent runtime protection is configured in Microsoft Defender for Endpoint.

For each agent, Defender can surface:
* Risk level, calculated from active risk indicators
* Risk indicators contributing to that risk level
* Active security recommendations
* Active alerts
* Configuration details
* Identity and authentication information
* Tools
* MCP servers

The agent detail view can also show attack-surface relationships, giving security teams visibility into how an agent relates to other entities and helping them understand the potential impact of a compromise.

There is an important distinction here.
* Security recommendations are calculated separately from the agent's risk level.
* An agent with a lower current risk level can still have open recommendations representing posture gaps.
* Risk level tells you about the agent's overall exposure based on active risk indicators.
* Recommendations tell you what Defender has identified that you can change.

Note: Microsoft currently documents AI agent posture risk in Defender as a preview capability.

Detection: what Defender looks for

Microsoft Defender continuously monitors supported AI agent activity and currently documents detection of threats including:
* Jailbreak attempts.
* Indirect prompt injection (XPIA) attempts.
* Malicious content propagation.
* Secret and credential leakage.
* Evasion techniques.
* Large language model reconnaissance.
* Suspicious user or IP access.

Detections are surfaced as near-real-time alerts in the Defender portal and can be correlated into incidents using the investigation experience security teams already use for other Microsoft Defender alerts.

This matters operationally.

Security analysts don't need an entirely separate investigation platform for AI agent threats.

Alert triage, incident correlation and Advanced Hunting sit within the existing Defender experience.

One capability worth noting is prompt evidence collection.

When Defender detects suspicious agent activity, it can include snippets from the relevant interaction as evidence in the alert.

Only the portions of user prompts or agent responses identified as suspicious and relevant to the security classification are included. Microsoft states that sensitive data and secrets are redacted, although the remaining conversation content could still itself be sensitive.

Prompt evidence collection is enabled by default and can be controlled at:
Settings → Security for AI → Prompt evidence collection

Being able to see the prompt context associated with a detection can give an analyst valuable information when investigating what caused an alert.

There is one important caveat here.

Microsoft currently lists AI agent detection and investigation in Defender as Public Preview.

That distinction matters when you are considering the capability for production security operations.

Real-time protection: blocking before execution

Detection tells you about suspicious or malicious behaviour.

Real-time protection goes a step further.

Microsoft Defender can inspect agent activity during the agentic loop and block risky actions before they execute.

Coverage depends on the agent platform and how the agent has been integrated.

When you enable real-time protection:
* A built-in Default rule audits all agents.
* It records matching activity as a behaviour without stopping the action.

That gives you visibility before you start enforcing blocking.

Having visibility is always a good step to understand a control before blocking.

Understand what your controls are going to affect before you start preventing agents from performing actions that business processes may depend on.

When you are ready to enforce protection, you can create custom rules that block matching actions and scope those rules to your agents.

Rules can apply to all agents, and you can also exclude specific agents.

When selecting individual agents for exclusion, Microsoft states that only agents with a Microsoft Entra Agent ID appear in the list.

That is an important connection back to the Microsoft Entra Agent ID article on Entra Agent ID.

Identity isn't simply about authentication.

It also gives your security controls something concrete to target.

There is another operational point worth knowing.

When Defender audits or blocks an action, the event is recorded as a behaviour in the BehaviorInfo table.

Microsoft currently states that near-real-time detections continue to generate alerts only while the agent is in audit mode.

When a blocking rule covers an agent, near-real-time alerts aren't generated for that agent through this mechanism.

This is important to understand when you are aligning this to a service you may be operating.

It is especially important for SOC teams when designing their monitoring and hunting processes.

For platform coverage, Microsoft documents different protection mechanisms depending on the agent type.

Rather than assuming that enabling real-time protection covers every agent, check the supported protection model for each agent platform and integration you use.

Coverage depends on the agent platform and integration setup.

Threat investigation and Advanced Hunting

For investigation and threat hunting, Defender gives security teams access to Agent 365 observability data through Advanced Hunting using KQL.

There are six tables particularly relevant to AI agent investigation:
* AgentsInfo: inventory and configuration information for AI agents, including identity, platform, ownership and metadata.
* CloudAppEvents: Agent 365 observability data including agent actions, tool invocations and data access events.
* AlertInfo: alert metadata, including AI agent-related detections.
* AlertEvidence: entities and artefacts associated with alerts, such as agents, users, tools, URLs and resources.
* BehaviorInfo: real-time protection audit and block events recorded as queryable behaviours.
* BehaviorEntities: entities and artefacts associated with those behaviours.

These tables can be queried individually or correlated during an investigation.

For example, you could trace a tool invocation in CloudAppEvents, correlate activity with AlertInfo, and then examine the associated entities through AlertEvidence.

You can also correlate real-time protection behaviour from BehaviorInfo with the agents, users and tools involved.

One note for teams already using Advanced Hunting.

The AgentsInfo table replaces the previous AIAgentsInfo table as part of Microsoft's Agent 365 transition.

If you have existing hunting queries or custom detections based on AIAgentsInfo, review and update them.

Where to start

Start with the AI Agents inventory in the Defender portal:
Assets → AI agents

Understand which agents Defender can see.

Look at:
* Risk levels
* Active risk indicators
* Security recommendations
* Active alerts
* Identity and authentication
* Tools and MCP servers
* Attack-surface relationships

Then review real-time protection under:
Settings → Security for AI → Policies & rules → Real-time protection

Check the built-in Default rule and review the behaviours it is generating.

Understand which of your agent platforms meet Microsoft's current requirements for real-time protection.

Only then would I start moving towards custom blocking rules.

The audit-first approach makes sense.

You want to understand what real-time protection will affect before you start blocking it.

An agent that cannot invoke the tools required to perform its task isn't going to deliver the outcome you created it for.

Closing the week

This week I have worked through Microsoft Agent 365 from the control plane outwards.

On Monday I introduced Agent 365 (https://lnkd.in/p/eFSKzuKm) as the platform for observing, governing and securing AI agents across the organisation.

On Tuesday I looked at how Microsoft Entra Agent ID (https://lnkd.in/p/egVAxyC9) provides identity and Conditional Access for agents.

On Wednesday I looked at how Microsoft Purview (https://lnkd.in/p/ewWfSg_p) governs the data agents interact with.

Today I have looked at how Microsoft Defender extends threat detection, real-time blocking, posture management and investigation to agents.

The thread connecting all four articles is the same one that connects every security architecture conversation I have.

Controls that exist are not the same as controls that are configured.

Controls that are configured are not the same as controls that are understood.

AI agents are a new class of identity and a new attack surface.

The tools to govern and protect them are here, and Microsoft is developing them quickly.

The question is not whether the tools exist.

The question is whether your organisation is using them.

Does your security operations team currently have visibility into AI agent activity in your environment, or are agents still a blind spot in your detection and response capability?

---

## Microsoft Learn References

- [Secure AI agents at scale using Microsoft Agent 365](https://learn.microsoft.com/en-us/security/security-for-ai/agent-365-security)
- [Detect and investigate threats to AI agents using Microsoft Defender (Preview)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-detection-protection)
- [Protect AI agents in real time using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-real-time-protection)
- [Discover AI agents and assess security posture using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-inventory)

---

## LinkedIn URLs (Week 10 arc — confirmed from Day 70 closing)

- Day 67 (Agent 365 overview): https://lnkd.in/p/eFSKzuKm
- Day 68 (Entra Agent ID): https://lnkd.in/p/egVAxyC9
- Day 69 (Purview): https://lnkd.in/p/ewWfSg_p
- Day 70 (Defender): pending

---

## Hashtags

#MicrosoftDefender #AIGovernance #ThreatProtection #MicrosoftAgent365 #DefenderXDR #ZeroTrust #MicrosoftSecurity #PromptInjection

---

## Accuracy Notes (for future articles)

- **CRITICAL LICENSING CHANGE (1 July 2026):** Since 1 July 2026, Copilot Studio and Microsoft Foundry agent-level discovery and posture, threat protection and Agent 365-powered investigation are no longer covered by Defender for Cloud Apps or Defender for Cloud licences alone. Agent 365-eligible licence is required. Stuart established a pattern of leading with licensing reality early in Week 10 articles — carry this forward.
- **Preview status (multiple layers — be precise):**
  - AI agent posture risk in Defender: Stuart flagged as "preview capability" per Microsoft.
  - AI agent detection and investigation in Defender XDR: explicitly listed by Microsoft as Public Preview (page title includes "Preview"). Stuart carried this caveat in the published article.
  - Real-time protection: not flagged as preview in MS docs — more stable capability.
  - Always check current preview status; this area moves fast.
- **Threat categories confirmed from MS Learn:** Jailbreak attempts / Indirect prompt injection (XPIA) / Malicious content propagation / Secret and credential leakage / Evasion techniques / LLM reconnaissance / Suspicious user or IP access.
- **Prompt evidence collection (confirmed detail):** Enabled by default. Only suspicious portions included. Sensitive data and secrets are redacted. Stuart's nuance: "remaining conversation content could still itself be sensitive" — important governance caveat. Navigate: Settings → Security for AI → Prompt evidence collection.
- **BehaviorInfo/alert mode nuance (important for SOC):** When a blocking rule covers an agent, near-real-time alerts are NOT generated for that agent. Only in audit mode do near-real-time alerts surface. SOC teams must account for this when designing monitoring and detection processes.
- **Coverage generalised:** Stuart deliberately avoided naming Work IQ MCP specifically. Use "Coverage depends on the agent platform and integration setup" as the correct practitioner-level framing.
- **Real-time blocking rules:** Default = audit only; Custom rules = block. Only agents with Entra Agent ID appear in exclusion list for individual agent scoping.
- **Six Advanced Hunting tables (confirmed):** AgentsInfo / CloudAppEvents / AlertInfo / AlertEvidence / BehaviorInfo / BehaviorEntities. AgentsInfo replaces previous AIAgentsInfo table — flag this to teams with existing queries.
- **Navigation confirmed:** Assets → AI agents → Agents (inventory); Settings → Security for AI → Policies & rules → Real-time protection (rules).
- **Week 10 arc closing statement (strong reuse candidate):** "Controls that exist are not the same as controls that are configured. Controls that are configured are not the same as controls that are understood." — definitive summary of the Week 10 / AI agent security theme. Reuse in future series closes.
- **Week 10 LinkedIn URLs confirmed:** Day 67 = https://lnkd.in/p/eFSKzuKm; Day 68 = https://lnkd.in/p/egVAxyC9; Day 69 = https://lnkd.in/p/ewWfSg_p; Day 70 = pending.
