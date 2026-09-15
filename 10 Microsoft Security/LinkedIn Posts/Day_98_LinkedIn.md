# Day 98 — LinkedIn Content Package
**Topic:** Where Microsoft security is heading — the agentic SOC
**Category:** AI Security / SecOps / Future direction
**Week theme:** Week 14 — the closing arc (Days 95–100)
**Date:** 2026-09-10 (Thursday)
**Format:** Forward-looking / opinion piece
**LinkedIn URL:** https://lnkd.in/p/ei8SDsSK

---

## LinkedIn Article (final — scheduled, 2026-09-10)

Where Microsoft security is heading: the agentic SOC

For most of this challenge, I have written about where Microsoft security is today.

Today, I want to look forward.

Because if you step back from the individual products and look at Microsoft's direction of travel, it is remarkably consistent.

Microsoft has even given it a name.

The agentic SOC.

What "agentic SOC" actually means

The idea is straightforward, even if the technology behind it isn't.

Autonomous defences handle more high-confidence threats at machine speed.

AI agents take on more repetitive investigation, triage, and correlation.

Human defenders move towards judgement, strategy, governance and the difficult decisions that genuinely need a person.

Microsoft describes the agentic SOC as an operating model that combines a security platform capable of increasingly defending itself with AI agents working alongside people.

There is an important distinction here.

Autonomous defence and AI agents aren't the same thing.

Microsoft describes the underlying autonomous defence layer as deterministic and policy-bound.

When the platform identifies a threat with sufficiently high confidence, it can take predefined action without waiting for an analyst.

The agent layer sits above that.

Agents reason over evidence, coordinate investigations, help prioritise work and increasingly orchestrate response across security domains.

Then humans provide something different again. They provide Intent, Judgement, and Accountability, and that distinction matters, because the agentic SOC isn't simply:

"Give AI control of the SOC."

It is about deciding which decisions machines can safely make, which tasks agents can accelerate, and which decisions still need a person.

Some of this is already happening

This isn't all a slide of future promises.

Automatic attack disruption has already been operating within Microsoft Defender for several years.

Defender XDR correlates signals to identify active attacks with high confidence and can automatically contain compromised assets to limit lateral movement and reduce impact. Current actions include isolating devices, disabling or containing users and revoking sessions, depending on the identity and services involved.

And Microsoft published an interesting number in April.

According to its agentic SOC research and operational data:

Attacks such as ransomware are being disrupted in an average of three minutes.

Microsoft says tens of thousands of attacks are contained every month with a 99.99% confidence rating for these autonomous disruption actions.

Think about that for a moment.

* Three minutes.
* A human analyst might still be opening the incident.
* The platform is already trying to stop the attacker from moving any further.
* That is machine-speed defence operating today.

Everything I wrote about this year was pointing here

What struck me when I started pulling this series together was that none of this should really be a surprise.

Look at the individual pieces.

Microsoft Sentinel is now positioned by Microsoft as the agentic defence platform, bringing together security data and context for defenders and agents.

Its data lake expands the amount and types of security data available for investigation.

Its graph capabilities add relationships and context.

And its MCP server provides a structured way for supported AI tools and agents to interact with Sentinel data, including natural-language exploration of data lake and graph context.

Then came Security Copilot agents.

Agents across Defender, Entra, Intune and Purview are taking on tasks including alert triage, threat hunting, Conditional Access optimisation, identity risk investigation and vulnerability remediation.

Then Microsoft Entra Agent ID.

AI agents increasingly need identities of their own.

Agent ID introduces purpose-built identity constructs so supported AI agents can be authenticated, authorised, governed and protected using Microsoft Entra capabilities.

And Agent 365 builds on that identity foundation to help organisations discover, manage and govern agents at scale.

Then Microsoft Security Exposure Management.

It automatically generates attack paths from data collected across assets and workloads, helping defenders understand how exploitable weaknesses could provide routes towards critical assets.

It can also identify choke points where multiple attack paths converge, helping teams prioritise remediation where it will have the greatest effect.

Then Defender XDR.

Signals from different security domains become correlated incidents.

Automatic attack disruption can then contain high-confidence attacks while they are still happening.

Each one is a piece.

Put them together and Microsoft's direction becomes much clearer.

A security operation where machines do more of the repetitive execution, agents do more of the investigation and reasoning, and people spend more time making the decisions that matter.

The two-sided AI story

The part I find most interesting is that AI now sits on both sides of the security equation.

On one side:

AI is something we have to secure.

* AI agents introduce identities.
* Permissions.
* Data access.
* New attack paths.
* New governance questions.
* New opportunities for attackers.

That was a whole part of this series.

* Agent 365.
* Agent ID.
* Purview protecting data used by supported AI applications and agents.
* Defender capabilities protecting the AI estate.

Microsoft itself now talks about security being woven into and around every layer of that AI estate.

But on the other side:

AI is increasingly helping to do the securing.

* Security Alert Triage Agent.
* Threat Hunting Assistant.
* Conditional Access Optimisation Agent.
* Identity Risk Management Agent.
* Vulnerability Remediation Agent.
* And other Security Copilot agents across Microsoft's security products.

Then underneath them sits autonomous defence.

* Attack disruption.
* Containment.
* Predictive protection.
* Machine-speed response.

So we are doing two things simultaneously.

Securing AI.

And:

Using AI to secure everything else.

The dual role is one of the defining changes happening in security right now.

But here are the questions we need to ask

I am optimistic about this direction.

We need to be sensible about it.

Because automation is easy to demonstrate, especially when everything works, the harder conversation is:

What happens when it doesn't?

* If a security system can automatically disable an account or isolate a device, who owns the consequences if the wrong asset gets affected?
* Who decides the confidence threshold?
* Which systems should never be isolated automatically?
* Which accounts require additional safeguards?
* Who reviews what the agents are doing?
* Where does automation stop?
* Where must a human make the decision?

Those aren't arguments against an agentic SOC.

They are part of building one properly.

Interestingly, Microsoft's own agentic SOC model reaches much the same conclusion.

Microsoft describes people as providing intent, judgement and accountability, while autonomous defence and agents handle increasing amounts of execution, context and coordination.

For me, that is the important bit.

* Machine speed where machine speed makes sense.
* Human judgement where the consequence requires it.

Are organisations actually ready for this?

This is where I think the architecture conversation becomes more interesting than the marketing.

Technically, some of this is already here.

Operationally, I think many organisations have some work to do.

I still see environments where basic security capabilities have been configured and onboarded but aren't fully deployed as they should be.

* Critical sensors are missing.
* Identity controls only partially implemented.
* Security products and teams are operating in silos.
* Data not properly understood or controlled.
* SOC processes still heavily manual.
* Ownership split across teams that rarely talk to each other.

Then we start talking about autonomous security.

My view is that most organisations shouldn't jump from manual operations straight to full autonomy, and Microsoft doesn't suggest that either.

Its agentic SOC maturity model describes three stages:

* SOC I: Unify the platform foundation.
* SOC II: Accelerate operations with generative AI and task agents.
* SOC III: Deploy agentic automation.

That progression makes sense to me.

* Get the foundations working.
* Introduce AI into bounded, high-volume tasks.
* Build confidence.
* Put governance around it.
* Understand where it works.
* Understand where it doesn't.
* Then expand the level of autonomy.

That feels much more realistic than simply switching on agents and calling yourself an agentic SOC.

And then there is the people question

There is another part of this we shouldn't ignore.

How do people learn the craft?

A junior analyst traditionally learns by doing a lot of the work that AI agents are now becoming good at.

* Reading alerts.
* Looking at evidence.
* Writing queries.
* Triaging phishing.
* Following incidents.
* Making mistakes.
* Learning what normal looks like.

If agents increasingly take that work away, we need to think about how the next generation develops that experience. This is exactly the conversation I was having last week.

The future is that analysts will move from actively triaging alerts and incidents to supervising outcomes. Engineering teams and threat hunters will increasingly tune, govern, and oversee the autonomous capabilities.

In a way, I am seeing this coming to life now, but we shouldn't assume that removing repetitive work automatically creates experienced security people.

We still have to teach them.

* Perhaps the skills change.
* Perhaps junior analysts spend more time understanding why an agent reached a conclusion.
* Perhaps they validate investigations rather than assembling every investigation themselves.
* Perhaps detection engineering and threat hunting become foundational skills earlier in someone's career.

I don't think AI removes the need for security people, but it changes what we need to teach them.

And the same thread, one last time

I have said this in almost every article in this series.

It belongs here too.

None of this removes the need for the foundations.

* An agentic SOC still needs the telemetry.
* The sensors.
* The identities.
* The permissions.
* The data.
* The integrations.
* The policies.
* The governance.

Exposure Management itself makes this clear. Microsoft warns that attack paths might not appear, or might not fully represent the organisation, if the required workload data, licences, or critical-asset definitions aren't available.

Automatic attack disruption has prerequisites too.

The relevant Defender products have to be deployed and configured before the platform can take the corresponding response actions.

The future might be more automated.

It isn't more forgiving of weak foundations.

If anything, automation makes those foundations more important.

Because when you allow technology to act at machine speed, you need to have confidence in the signals, policies and boundaries it is acting on.

Where this leaves us

For those of us working in security, the direction is clear enough to plan around. Some of the value is moving away from manually performing repetitive work.

Towards:

* Designing the systems that perform it.
* Deciding where they are allowed to act.
* Governing them.
* Testing them.
* Challenging their decisions.
* And knowing when a human needs to take control.

Understanding the technology still matters, and I would state it matters even more.

Because you can't properly govern something you don't understand.

But this is the note I wanted to end the technical thread on.

* The tools are becoming agents.
* The defence is becoming more autonomous.
* The strategy hasn't changed.

And the person who understands the technology, the risk and how to use it responsibly becomes more valuable, not less.

So here is the question I am leaving this technical series with:

Are you and your organisation ready to let security act at machine speed, and are you clear where a human still has to make the call?

---

## Microsoft references

- [The agentic SOC — rethinking SecOps for the next decade (Microsoft Security Blog)](https://www.microsoft.com/en-us/security/blog/2026/04/09/the-agentic-soc-rethinking-secops-for-the-next-decade/)
- [Secure agentic AI end-to-end (Microsoft Security Blog)](https://www.microsoft.com/en-us/security/blog/2026/03/20/secure-agentic-ai-end-to-end/)
- [Automatic attack disruption in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption)
- [Configure automatic attack disruption](https://learn.microsoft.com/en-us/defender-xdr/configure-attack-disruption)
- [Work with attack paths (Exposure Management)](https://learn.microsoft.com/en-us/security-exposure-management/work-attack-paths-overview)
- [What is Microsoft Entra Agent ID?](https://learn.microsoft.com/en-us/entra/agent-id/what-is-microsoft-entra-agent-id)

#AgenticSOC #AISecurity #MicrosoftSecurity #SecOps #MicrosoftDefender #SecurityCopilot #Cybersecurity #SecurityArchitecture

---

## Hashtags

#AgenticSOC #AISecurity #MicrosoftSecurity #SecOps #MicrosoftDefender #FutureOfSecurity #Cybersecurity #SecurityArchitecture

---

## Notes

- Day 98 — Week 14, forward-looking piece; last technical-flavoured post before Friday's retrospective.
- Direction confirmed via Sept 2026 web check: Microsoft's "agentic SOC" narrative (RSA 2026 / Security Blog Apr 2026). ~3-min ransomware disruption, tens of thousands contained monthly at high confidence — verify exact figures before publishing.
- Ties the whole series together as having pointed toward this: Sentinel platform, Copilot agents, agent identities, Exposure Management, XDR disruption.
- Two-sided AI framing: securing AI + AI securing (defining feature of the next phase).
- Balanced, not hype: raises accountability, boundaries, and the "how do juniors learn the craft" question honestly.
- Foundations thread reinforced one last time.
- One [STUART'S PERSPECTIVE] slot — client readiness, realistic adoption curve, the human/craft question.
- Sets up Day 99 retrospective explicitly.
- Metrics check due: 2026-10-10
