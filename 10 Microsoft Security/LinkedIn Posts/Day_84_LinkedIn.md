# Day 84 — LinkedIn Content Package
**Topic:** Security Copilot agents across Defender, Entra, Intune and Purview — the agentic layer arrives
**Category:** AI Security / Microsoft Security Copilot / SecOps
**Week theme:** What's new in Microsoft Security (Days 81–84)
**Date:** 2026-08-27 (Thursday)
**Format:** Technical article — Week 12 Day 4 (series close)
**LinkedIn URL:** https://www.linkedin.com/pulse/security-copilot-agents-across-defender-entra-intune-purview-mann-cqv5e

---

## LinkedIn Article (published — 2026-08-27)

Security Copilot agents across Defender, Entra, Intune and Purview

All week I have written about parts of the Microsoft security stack becoming more agentic.

Sentinel becoming a platform for agentic defence.

Entra and Purview adding AI-aware controls.

Today is the layer that starts tying much of it together:

Microsoft Security Copilot agents.

Agents are now being built directly into security workflows across Microsoft Defender, Microsoft Entra, Microsoft Intune and Microsoft Purview.

What was announced

At Ignite 2025, Microsoft announced a dozen new Microsoft-built Security Copilot agents across Defender, Entra, Intune and Purview, alongside more than 30 partner-built agents.

That put the announced ecosystem at more than 40 Microsoft and partner agents.

Two things make this more than another AI feature release.

First, the agents are embedded.

Rather than living only in the standalone Security Copilot portal, agents can appear directly inside Microsoft Defender, Entra, Intune and Purview.

That matters because this is where the security work already happens.

Second, the commercial model changed.

Microsoft Security Copilot is now included for eligible Microsoft 365 E5 and E7 customers.

Rollout started on 18 November 2025 for existing Security Copilot customers with Microsoft 365 E5 and has continued through a phased rollout to eligible E5 and E7 customers.

When inclusion reaches an eligible tenant, Security Copilot is automatically provisioned. There is no separate Azure setup or manual SCU provisioning required for that included capacity.

But there is an important distinction:

Provisioning Security Copilot does not automatically enable all agents.

You still need to set up the agents you want to use.

The included capacity is also now clear.

Microsoft 365 E5 and E7 customers receive:

400 Security Compute Units per month for every 1,000 paid user licences

up to a maximum of: 10,000 SCUs per month.

The allocation scales with licence count.

For example, 400 eligible licences provide 160 SCUs per month, while 4,000 provide 1,600 SCUs.

If you have E5 or E7, this is worth checking.

You may already have Security Copilot provisioned and not have looked at which agents you can deploy.

What the agents actually do

The concrete examples are much more useful than the concept.

Microsoft Defender

The Phishing Triage Agent tackles one of the most repetitive jobs in many SOCs:

User-reported phishing.

It analyses user-reported suspicious emails and uses AI-driven reasoning to classify them, providing analysts with the reasoning behind its verdict.

There is an important update here too.

The Security Alert Triage Agent is the same agent as the Phishing Triage Agent, with its capabilities extended to a broader set of supported Defender alerts.

Email and collaboration alert triage is generally available, while the expanded cloud and identity alert capabilities are currently in preview.

Microsoft Defender also now includes agents such as:

* Threat Intelligence Briefing Agent
* Threat Hunting Assistant
* Security Analyst Agent
* Dynamic Threat Detection Agent

The Threat Hunting Assistant lets analysts investigate threats using natural language.

The Security Analyst Agent analyses security data from sources including Defender XDR, Sentinel Log Analytics and Sentinel data lake.

And the Dynamic Threat Detection Agent works continuously in the background, correlating alerts, events, anomalies and threat intelligence to identify threats that existing detections may have missed.

This is where the agent model starts making sense.

Don't create one AI that tries to do everything.

Give individual agents defined security tasks.

You wouldn't give every job to one person.

Microsoft Entra

In Entra, one agent I find particularly interesting is the Conditional Access Optimization Agent.

It analyses your Conditional Access environment looking for areas including:

* Unprotected users
* Unprotected applications
* Agent identities
* Policy gaps
* Overlapping policies

It can recommend new policies, suggest changes to existing policies and identify policies that could potentially be consolidated.

It can also propose changes that administrators can review and apply, including creating or updating Conditional Access policies.

That matters.

The agent can do the analysis and make the recommendation.

You remain responsible for the decision.

Microsoft provides reasoning and policy information with its suggestions so you can review what the agent found before taking action.

This is a good example of where agentic security has real value.

Conditional Access environments become complicated.

* Policies accumulate.
* Exceptions appear.
* Applications change.
* Users change.
* Agent identities appear.
* And gaps develop.

Having an agent looking for those gaps is very different from asking someone to perform a Conditional Access review once a year.

Microsoft Intune

Intune is interesting for a different reason because it shows just how quickly this area is changing.

Microsoft announced several Security Copilot agents for Intune, including:

* Policy Configuration Agent
* Device Offboarding Agent
* Change Review Agent
* Vulnerability Remediation Agent

But the portfolio has already changed.

Microsoft removed the Device Offboarding Agent on 1 June 2026.

And Microsoft has announced that the Policy Configuration Agent and Change Review Agent will no longer be available in the Intune admin centre after 31 August 2026.

Microsoft specifically recommends avoiding new workflows or dependencies on those agents.

That leaves the Vulnerability Remediation Agent as the Intune agent I would pay closest attention to from this original group.

It uses Microsoft Defender Vulnerability Management data to help identify and prioritise vulnerabilities affecting managed devices and support remediation through Intune.

This is also a useful reminder:

Agentic security is moving quickly.

An agent announced at Ignite isn't necessarily an agent you should build an operational process around a year later.

Check the current status before adopting it.

Microsoft Purview

Purview now has specialised Security Copilot agents supporting data-security workflows.

Microsoft currently documents:

* DLP Triage Agent
* Insider Risk Management Triage Agent
* Data Security Posture Management Posture Agent, in preview
* Data Security Investigations Posture Agent, in preview

The DLP Triage Agent evaluates areas including content risk, exfiltration risk and policy risk to prioritise alerts.

The Insider Risk Management Triage Agent evaluates activity and user risk.

The Data Security Posture Agent takes a different approach, helping security teams search for sensitive data across Microsoft 365 using natural language and providing risk analysis around what it finds.

This connects directly to the Purview article I wrote yesterday.

We are moving from simply having policies that generate events towards agents that can help analyse, prioritise and investigate what those controls find.

The part I would not skip: governing the agents

Here is where my week comes full circle.

Two weeks ago I wrote about AI agents as a new class of identity and about Microsoft Entra Agent ID giving agents an identity that can be governed.

That principle becomes very relevant here.

Security Copilot agents can operate inside some of the most sensitive areas of your Microsoft environment.

Conditional Access.

Security alerts.

Endpoint configuration.

Identity risk.

Data security.

So their identity and permissions matter.

Microsoft's current Security Copilot agent setup model allows an agent, depending on the agent, to use a newly created agent identity or an existing user account.

Microsoft recommends creating an agent identity where that option is supported.

The implementation can still differ between agents.

For example, the Conditional Access Optimization Agent can use Microsoft Entra Agent ID for authorisation.

So rather than assuming every agent works in exactly the same way, I would ask five questions:

* What identity is this agent using?
* What permissions does it have?
* What data can it access?
* What actions can it take?
* Who is accountable for reviewing what it does?

That is Zero Trust applied to agents.

Human oversight still matters!

The reassuring part of Microsoft's current design is that human oversight remains part of the model.

And this is an important point in the wider AI conversation.

The Conditional Access Optimization Agent provides reasoning behind its recommendations and administrators retain control over policy changes.

The Security Alert Triage Agent similarly provides transparent rationale for its classifications, including the supporting evidence, and analysts can provide feedback on the agent's verdict.

The point isn't simply:

"The AI made the decision."

You should be able to understand:

* What did it find?
* Why does it think this is a problem?
* What evidence did it use?
* What does it recommend?
* What happens if I approve it?

That is the difference between useful automation and blind trust.

How often are you checking what you are presented with?

Who is making the decisions?

Are they still human-led choices?

And are you validating the actions?

A few notes

First, status.

Not every Security Copilot agent has the same release status.

Some of the Security Alert Triage Agent's expanded capabilities are currently in preview.

The Vulnerability Remediation Agent is currently in public preview.

The Purview DSPM and Data Security Investigations Posture Agents are also documented as preview capabilities.

And, as the Intune changes show, some agents can be retired while the wider agent strategy continues.

Check the status of the specific agent before building an operational dependency around it.

Second, capacity.

Agents consume Security Compute Units.

Under the Microsoft 365 E5 and E7 inclusion model, customers receive 400 SCUs per month for every 1,000 paid licences, up to 10,000 SCUs.

That allocation resets monthly.

Unused SCUs do not roll over.

Microsoft currently says that usage beyond the included allocation will be throttled at a future date, and customers will then have the option to scale beyond it at $6 USD per SCU on a pay-as-you-go basis.

So I wouldn't assume today that every E5 or E7 customer can exceed their allocation and automatically move to PAYG.

Monitor consumption through the Security Copilot usage dashboard.

Third, prerequisites.

Agents aren't magic sitting on top of an empty tenant.

The Security Alert Triage Agent requires different underlying licences depending on the alerts you want it to triage.

Email and collaboration alerts require Microsoft Defender for Office 365 Plan 2.

Cloud alerts require the applicable Microsoft Defender for Cloud protection.

Identity alerts require Entra ID P2, Microsoft Defender for Identity and Microsoft Defender for Cloud Apps.

The Conditional Access Optimization Agent requires at least Microsoft Entra ID P1 and available SCUs.

The agent automates work.

The underlying security product still needs to exist and be configured properly.

And that's the biggest point for me:

Properly configured.

Something many organisations still need to complete, and it's a challenge I'm often asked to help with.

AI accelerates what is already there

A Conditional Access optimisation agent becomes much more useful when your Conditional Access environment has a coherent design.

A phishing triage agent becomes much more useful when Defender for Office 365 and user reporting are configured correctly.

A vulnerability remediation agent becomes much more useful when Defender and Intune have good device visibility.

AI can accelerate good security operations.

It doesn't build the foundations underneath them.

Closing the week

Four days.

Four parts of the Microsoft security stack.

Sentinel becoming a broader platform for security operations and agentic defence.

Entra closing identity, governance and recovery gaps.

Purview extending data security into browsers, networks and AI.

And now Security Copilot agents bringing specialised AI-driven workflows into Defender, Entra, Intune and Purview.

The thread running through all of them is clear.

Microsoft is increasingly building its security portfolio around agentic defence, where AI can take on more repetitive analysis and operational work while people remain responsible for the decisions that matter.

The opportunity is real.

So is the responsibility.

* Agents need identity.
* They need least privilege.
* They need monitoring.
* They need auditability.
* And they need human accountability.

The same security disciplines we already apply to users, administrators, workloads and applications increasingly need to apply to AI agents too.

If you have Microsoft 365 E5 or E7, my suggestion is simple:

Check whether Security Copilot is available in your tenant, and see which agents are currently available in the security products you already use.

And I would emphasise currently available.

Because, as Intune has demonstrated this year, the agent portfolio is changing quickly.

Which Security Copilot agent would take the most repetitive work away from your security team?

---

## Microsoft Learn References

- [Microsoft Security Copilot agents](https://learn.microsoft.com/copilot/security/agents-security-copilot)
- [Security Copilot for Microsoft 365 E5 and E7 included customers](https://learn.microsoft.com/copilot/security/security-copilot-inclusion)
- [Deploy AI agents in Microsoft Defender](https://learn.microsoft.com/defender-xdr/security-copilot-agents-defender)
- [Security Copilot agents in Intune overview](https://learn.microsoft.com/intune/copilot/agents/)
- [Microsoft Security Copilot Security Compute Units and capacity](https://learn.microsoft.com/copilot/security/security-compute-units-capacity)

---

## Hashtags

#SecurityCopilot #AISecurity #MicrosoftSecurity #MicrosoftDefender #MicrosoftEntra #MicrosoftIntune #MicrosoftPurview #Cybersecurity

---

## Accuracy Notes

- **Announced at Ignite 2025:** 12 new Microsoft-built agents across Defender, Entra, Intune, Purview + 30+ partner agents (~40 total) — confirmed from What's New (Nov 2025) and inclusion page.
- **E5/E7 inclusion:** Security Copilot included for eligible M365 E5 and E7; rollout started 18 Nov 2025; auto-provisioned, no Azure setup — confirmed. Inclusion model: 400 SCUs per 1,000 user licenses/month; resets monthly, no rollover; overage $6/SCU pay-as-you-go — confirmed.
- **Defender agents:** Phishing Triage Agent (GA for email; Security Alert Triage Agent = extended version, PREVIEW, adds identity + cloud alerts), Threat Intelligence Briefing Agent, Threat Hunting Assistant, Security Analyst Agent, Dynamic Threat Detection Agent — all confirmed.
- **Entra agents:** Conditional Access Optimization Agent (GA, per July 2025 What's New), Identity Risk Management Agent — confirmed.
- **Intune agents:** Change Review Agent, Device Offboarding Agent, Policy Configuration Agent, Vulnerability Remediation Agent — confirmed from Intune agents overview.
- **Purview agents:** data security agents — confirmed at directory level (copilot-in-purview-agents).
- **Governance model:** agent identity set by admin; RBAC per agent; monitoring user group must have equal-or-higher permissions than the agent — confirmed verbatim from Phishing Triage Agent docs. "Observe, reason, act with oversight" — confirmed. ISO 42001 certified — confirmed from application card.
- **Phishing Triage prerequisites:** Defender for Office 365 Plan 2, URBAC enabled, user-reported settings, SCUs — confirmed.
- **Ties to Days 68 (Entra Agent ID) and Week 10 Agent 365 series** — factual callback, agents-as-identity principle.
- **All GA/preview statuses verified this session (Aug 2026).** Preview items: Security Alert Triage Agent, several E5/E7 rollout agents. Re-check before publishing.
- Metrics check due: 2026-09-27
