# Day 69 — LinkedIn Content Package
**Topic:** Microsoft Purview and AI agent data security — what's automatic, what isn't, and where the gaps are
**Category:** AI Security / Data Security / Microsoft Purview
**Week theme:** Microsoft Agent 365 — AI agent governance (Days 67–70)
**Date:** 2026-08-13 (Thursday)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (used in published):**
Your organisation has Purview policies in place.

Sensitivity labels. DLP rules. Retention policies.

When your AI agents interact with data covered by those policies, do you know which controls actually apply?

**Hook 2:**
When you deploy a new AI agent, three data security controls are enabled automatically.

Everything else needs to be configured manually.

Most organisations have not done that configuration.

**Hook 3:**
A data loss prevention policy that protects your users from sharing sensitive data does not automatically extend to your AI agents.

Unless you have explicitly included the agent in the policy, the control does not apply.

---

## LinkedIn Article (published — 2026-08-13)

Microsoft Purview and AI agent data security: what's automatic, what isn't, and where the gaps are

Your organisation has Purview policies in place.
Sensitivity labels. DLP rules. Retention policies.
When your AI agents interact with data covered by those policies, do you know which controls actually apply?

Yesterday I looked at how Microsoft Entra Agent ID provides the identity foundation for AI agents, and how Conditional Access can be extended to agent identities.
Today I want to look at the data side.
Because your data governance posture is now also part of your AI governance posture.
But only if your policies actually cover your agents.
And many of those controls are not automatically enabled for agent instances and must be explicitly configured.

What is automatic

When you create an agent instance in Microsoft Agent 365, Microsoft automatically enables three Purview capabilities for it.

The first is audit.

Prompts and responses are captured in the Microsoft Purview unified audit log. Audit events can include when interactions occurred, which Microsoft 365 service was involved, references to Microsoft 365 files accessed during the interaction and any sensitivity labels applied to those files.

Microsoft also states that interaction types captured for Agent 365 include agent-to-human, human-to-agent, agent-to-tools and agent-to-agent interactions.

The information can be surfaced through Activity Explorer and searched through the Audit solution in the Microsoft Purview portal.

From a forensic and compliance investigation perspective, that gives you a useful audit trail from the start.

The second is data classification.

Agent instances are automatically enabled for sensitive-data detection using Microsoft Purview data classification.

That gives you visibility into sensitive information being used through agent interactions before you start extending additional Purview policies to those agents.

The third is Compliance Manager.

Agent instances are automatically included in assessments for AI regulations in Compliance Manager, giving you a starting point for assessing compliance requirements around AI use.

Those are the three capabilities Microsoft currently enables automatically for Agent 365 agent instances.

For other Purview capabilities, you need to consider the agent instance in your policy configuration.

Sensitivity labels and agent access

Sensitivity labels are one of the most important data protection controls in the Microsoft environment, and agents interact with labelled content in ways that are worth understanding.

First, an Agent 365 agent instance doesn't automatically gain access to a file simply because it exists within Microsoft 365.

For an agent instance to access a file, the file must be explicitly shared with it.

Then we need to consider encryption.

If a sensitivity label applies encryption, the encryption configuration must explicitly grant the agent instance the VIEW and EXTRACT usage rights.

This is where there is an important difference.

A sensitivity label configured to grant access broadly across your organisation shouldn't be assumed to provide access for an Agent 365 agent instance. Microsoft documents that the agent instance should be explicitly included in the encryption configuration and granted the required VIEW and EXTRACT rights.

That means if you have encrypted files that agents need to work with, checking the label alone isn't enough.

You need to check the encryption permissions behind that label as well.

There is a second sensitivity-label gap worth knowing.

When Agent 365 creates new content, that content does not automatically inherit the sensitivity label from the source items.

An agent summarising a document marked Confidential does not automatically produce a summary marked Confidential.

The newly created content isn't automatically labelled or encrypted simply because its source was.

If data protection coverage of agent-generated content matters in your organisation, you need to decide how that new content will be classified and protected.

Data Loss Prevention and the silent block problem

Microsoft Purview DLP can also be extended to Agent 365 agent instances.

You can explicitly specify an agent instance in the DLP policy as you would a user, or use a security group that contains agent instances.

Microsoft currently documents support for blocking or auditing:
* agent-to-human interactions
* human-to-agent interactions

At the time of writing, Microsoft does not document DLP coverage for agent-to-agent interactions.

across:
* Microsoft Teams
* OneDrive
* SharePoint
* email

But there is an operational difference you need to know about.

Agent 365 currently doesn't receive DLP policy violation notifications when content is blocked.

That means the agent owner needs to actively monitor DLP activity and understand how policy enforcement might affect agent workflows.

This matters.

If an agent workflow stops behaving as expected after you introduce DLP controls, don't only troubleshoot the agent.

Check your Purview DLP events as well.

The policy may be doing exactly what you configured it to do.

Insider Risk Management and prompt injection

Microsoft Purview Insider Risk Management can also be extended to Agent 365.

The Risky AI usage policy template helps identify risky AI activity, including indicators associated with prompt injection attempts and attempts to access protected material.

Microsoft describes prompt injection as a scenario where instructions can manipulate an AI system into behaving in ways that weren't intended.

Signals from Risky AI usage can integrate with Microsoft Defender XDR, giving security teams additional context around AI-related risk alongside other security signals.

But again, Agent 365 coverage isn't something you should assume.

You explicitly specify agent instances in the Insider Risk Management policy as you would users.

Microsoft also documents support for built-in trigger events such as data exfiltration.

Purview goes further than DLP and Insider Risk

It's also worth remembering that Purview protection for Agent 365 extends beyond sensitivity labels, DLP and Insider Risk Management.

Microsoft currently documents Agent 365 integration across:
* Audit
* Data Classification
* Sensitivity Labels
* Data Loss Prevention
* Insider Risk Management
* Communication Compliance
* eDiscovery
* Data Lifecycle Management
* Compliance Manager

But only audit, sensitive-data detection through data classification and inclusion in AI regulation assessments in Compliance Manager are automatically enabled when an Agent 365 agent instance is created.

For the other capabilities, you need to look at how your existing policies apply and include agent instances where required.

That distinction matters.

Having Purview configured in your tenant does not automatically mean every Purview control covers every AI agent.

Where to start today

Open the Microsoft Purview portal and navigate to:
Data Security Posture Management → AI observability

One note before you get there.

Microsoft currently has the newer Data Security Posture Management experience and the older Data Security Posture Management (classic) experience.

For Microsoft Agent 365, use the current DSPM experience.

Microsoft specifically states that Data Security Posture Management (classic) doesn't support Agent 365.

AI observability gives you an overview of agent instances in your organisation that have recorded activity during the previous 30 days.

Agents are prioritised using the highest Insider Risk Management risk level associated with that agent.

Access to AI observability and related governance capabilities depends on your Microsoft licensing and the requirements for Agent 365.

From there, you can investigate risky activities including:
* oversharing
* exfiltration
* unethical behaviour

Select an individual agent, and you can see information including:
* Entra-enabled status
* creation date
* owner
* agent user ID
* which agent it is an instance of
* Insider Risk Management risk level
* risky activities detected from agent interactions

Purview can then surface remediation recommendations based on the risks it identifies.

For me, this is the right starting point.

Before building additional policies, understand which agents are active and what they are already doing with your data.

What to ask

Once you have that picture from AI observability, the questions become straightforward.

Which of your agent instances are included in your existing DLP policies?
Which aren't?
Do any agents need access to sensitivity-label-encrypted content?
If so, are those agent instances explicitly granted VIEW and EXTRACT rights in the encryption configuration?
What happens to new content those agents create?
Who is responsible for making sure that content receives the correct classification and protection?
Have you configured the Risky AI usage policy in Insider Risk Management?
Does Communication Compliance need to cover agent interactions?
Do your retention and Data Lifecycle Management requirements cover agent-generated content?
Who is monitoring DLP events where agents are in scope?

And perhaps the most important question:

Do you actually know which AI agents are active in your tenant?

The audit, data classification and Compliance Manager assessment coverage that Microsoft automatically enables gives you a starting point.

The DLP policies, sensitivity-label encryption permissions, Insider Risk Management policies and wider Purview controls protecting that data need your attention.

Knowing your Purview policies exist is not the same as knowing they cover your agents.

Tomorrow I will look at the threat protection side of Microsoft Agent 365, covering how Microsoft Defender extends detection and response capabilities to AI agents and what that means for security operations.

If you have started extending Purview policies to cover AI agents, what has been the most complex part of the configuration to get right?

---

## Microsoft Learn References

- [Use Microsoft Purview to manage data security & compliance for Microsoft Agent 365](https://learn.microsoft.com/en-us/purview/ai-agent-365)
- [Data Security Posture Management](https://learn.microsoft.com/en-us/purview/data-security-posture-management-learn-about)
- [Insider Risk Management — Risky AI usage policy template](https://learn.microsoft.com/en-us/purview/insider-risk-management-policy-templates#risky-ai-usage)
- [Audit logs for Copilot and AI activities](https://learn.microsoft.com/en-us/purview/audit-copilot)

---

## Hashtags

#MicrosoftPurview #AIGovernance #DataSecurity #DLP #MicrosoftAgent365 #ZeroTrust #MicrosoftSecurity #SensitivityLabels

---

## Accuracy Notes (for future articles)

- **Three auto-enabled controls (confirmed from MS Learn):** When an agent instance is created in Agent 365, three are enabled automatically: (1) audit, (2) sensitive-data detection via data classification, (3) Compliance Manager AI regulation assessments. For all other Purview capabilities, agent instances must be explicitly included in policies.
- **Full Purview capability list for Agent 365 (confirmed):** Audit / Data Classification / Sensitivity Labels / DLP / Insider Risk Management / Communication Compliance / eDiscovery / Data Lifecycle Management / Compliance Manager. All supported. Three auto-enabled; rest need configuration.
- **Files must be explicitly shared:** Agent instances do not automatically gain access to files in Microsoft 365 — files must be explicitly shared with the agent instance.
- **Sensitivity label encryption gotcha (critical):** Agent instances need explicit VIEW and EXTRACT usage rights in the label's encryption configuration. A label configured to grant broad organisational access should NOT be assumed to extend to agent instances. Check encryption permissions, not just the label.
- **New content inheritance gap (confirmed):** Newly created content from Agent 365 agents does NOT inherit sensitivity labels from source items. An agent summarising a Confidential document produces unlabelled, unencrypted output. Requires explicit process/policy decision.
- **DLP coverage scope (Stuart's precision):** DLP supports blocking/auditing agent-to-human and human-to-agent interactions (Teams, OneDrive, SharePoint, email). At time of writing, agent-to-agent interactions are NOT documented as covered by DLP. Important to caveat.
- **DLP silent block (confirmed):** Agent 365 does not receive DLP policy violation notifications. Agent owner must actively monitor DLP activity. If agent workflow fails unexpectedly after DLP policy introduced, check Purview DLP events — the policy may be the cause.
- **IRM Risky AI usage template:** Detects prompt injection attempts and access to protected materials. Microsoft defines prompt injection as instructions that can manipulate an AI system into unintended behaviour. Signals integrate with Defender XDR.
- **Correct DSPM version (important):** Data Security Posture Management (classic) does NOT support Agent 365. Use the current DSPM version. DSPM → AI observability is the starting point.
- **AI observability detail:** Shows agents with activity in last 30 days, ranked by IRM risk level. Shows per-agent: Entra-enabled status, created date, owner, agent user ID, which agent it's an instance of, IRM risk level, risky activities. Surfaces Purview remediation recommendations.
- **Licensing caveat on observability:** Stuart explicitly noted "Access to AI observability and related governance capabilities depends on your Microsoft licensing and the requirements for Agent 365." — consistent with Week 10 pattern of flagging licensing carefully without claiming specific detail.
- **Risky activities named:** Oversharing, exfiltration, unethical behaviour — confirmed from MS Learn as the three top risky activity categories in AI observability.
- **"Do you actually know which AI agents are active in your tenant?"** — Stuart's strongest closing question in this article. Good reuse candidate as a standalone challenge to practitioners.
- **Key recurring line:** "Knowing your Purview policies exist is not the same as knowing they cover your agents." — adapted from the series' "knowing the controls exist is not the same as having them configured."
- **Week 10 arc:** Day 67 (overview/Agent 365) → Day 68 (identity/Entra, published) → Day 69 (data/Purview, published) → Day 70 (threats/Defender, pending).
- **No MVP tracker entry yet** — add when URL confirmed after publication.
