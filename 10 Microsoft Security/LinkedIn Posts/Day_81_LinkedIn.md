# Day 81 — LinkedIn Content Package
**Topic:** Microsoft Sentinel is no longer just a SIEM — the shift to an agentic defense platform
**Category:** SecOps / Microsoft Sentinel / AI Security
**Week theme:** What's new in Microsoft Security (Days 81–84)
**Date:** 2026-08-24 (Monday)
**Format:** Technical article — Week 12 Day 1
**LinkedIn URL:** pending

---

## LinkedIn Article (published — 2026-08-24)

Microsoft Sentinel is no longer just a SIEM: it is evolving into an agentic defence platform.

Microsoft Sentinel is no longer just a SIEM.

For years, most conversations about Microsoft Sentinel started with one word:

SIEM.

That description is still correct, but it no longer captures everything Microsoft is building Sentinel to be.

Microsoft now describes Sentinel as both the SIEM and the platform for agentic defence.

And the change is bigger than a marketing line; it changes how the rest of this conversation should be read.

This week, I am covering what Microsoft has recently added across the security stack, starting with Sentinel, because this change could significantly affect how a SOC works day to day.

From SIEM to SIEM and platform

A traditional SIEM collects security data, analyses it and generates alerts that security teams investigate.

Sentinel still does all of that.

Analytics rules.

Threat hunting.

Incidents.

Automation.

Playbooks.

But Microsoft is extending Sentinel beyond that traditional SIEM model into what it describes as an AI-ready, data-first foundation for security operations.

The idea is to bring security telemetry together in a common data foundation, add graph-based context around how entities relate to each other, standardise how AI agents access security data through MCP, and enable more agentic security workflows.

Microsoft describes this as evolving Sentinel into:

"both the SIEM and the platform for agentic defence."

That last part matters.

Agentic defence doesn't mean removing analysts from the SOC.

Microsoft's stated direction is AI and automation operating at greater speed and scale, while people remain in command of strategy and high-impact investigations.

Three additions help explain where Sentinel is heading.

The data lake

Microsoft Sentinel data lake is now generally available.

It is a fully managed data lake designed for security operations, providing cost-effective retention and analysis of large volumes of security data.

It brings together logs from Microsoft 365, Defender, Azure, Microsoft Entra, Microsoft Purview and Microsoft Intune, alongside third-party sources through more than 350 connectors, including AWS and GCP.

One important architectural change is separating the data you need for real-time analytics from the data you want to retain for longer-term investigation, hunting, compliance, or analysis.

Sentinel now has two main data tiers.

The analytics tier is designed for data that needs high-performance querying and Sentinel capabilities such as analytics rules, alerting, hunting and workbooks.

The data lake tier provides lower-cost long-term storage for large volumes of security data.

Data stored in the analytics tier is mirrored into the data lake for the configured retention period.

But you can also configure supported data to be ingested directly into the data lake tier when you don't need the full real-time analytics capabilities of the analytics tier.

Data in the lake remains queryable through capabilities including KQL jobs, scheduled analytics and notebooks, although it doesn't provide all the real-time features available against analytics-tier data.

And retention can extend to 12 years.

For anyone who has watched Sentinel ingestion and retention costs climb, this changes some of the conversations we have when designing Sentinel.

Instead of asking:

"Can we afford to ingest this data?"

we can have a more useful conversation:

"How quickly do we need to analyse it, and which tier should it live in?"

That is an important architectural change.

The graph

Then there is Microsoft Sentinel graph.

This one needs a little nuance because the capability is developing quickly.

Microsoft Sentinel graph provides graph analytics across Microsoft's security ecosystem, allowing security teams and AI agents to reason over relationships between assets, identities, activities and threat intelligence.

Instead of looking at security events only as rows in tables, you can look at the relationships between them.

Microsoft describes this as spanning both pre-breach and post-breach security scenarios.

Think about the difference between asking:

"What happened to this device?"

and:

"What paths connect this compromised identity to my critical assets?"

That is where graph-based security becomes interesting.

Microsoft also supports custom graphs, which are currently in preview.

These allow you to build graphs using Sentinel data lake and non-Microsoft data, define nodes and relationships, materialise the graph and query it using Graph Query Language.

The interactive graph experience in Sentinel is also currently in preview.

For analysts, that provides another way of understanding an attack.

For AI agents, it provides context that is difficult to get from individual events in isolation.

The MCP server

This is the one I would pay attention to: it makes Sentinel easier to use directly from AI tools.

Microsoft Sentinel now provides a hosted Model Context Protocol (MCP) server that connects AI clients to Sentinel tools and data.

MCP is an open protocol that defines how AI applications interact with external tools, data, memory and context.

Sentinel's implementation provides a Microsoft-hosted interface that uses Microsoft Entra for identity and allows compatible AI clients and agents to work with security data and security tools.

The data exploration tools can:

* Find relevant Sentinel data lake tables.
* Understand table schemas.
* Execute KQL queries.
* Analyse entities.
* Work with supported Sentinel graph capabilities.

That means an analyst can ask natural-language questions about security data and use Sentinel tools without first knowing which table contains the information or manually constructing a well-formed KQL query.

And it doesn't stop with one Microsoft AI interface.

Microsoft currently documents Sentinel MCP integrations with:

* Microsoft Security Copilot
* Microsoft Copilot Studio
* Microsoft Foundry
* Visual Studio Code

Microsoft also now documents connectors for ChatGPT and Claude, although those integrations are currently in preview.

Microsoft Entra provides authentication to the hosted MCP interface.

For Sentinel's MCP tool collections, a Security Reader role is sufficient to list and invoke many tools, although individual tool collections and actions may require additional permissions.

The graph tools, for example, require Sentinel data lake and graph access, with at least read-only access to Microsoft Security Exposure Management for graph data.

The reason this matters is accessibility.

An analyst who isn't fluent in KQL can use natural language to explore security data and start an investigation.

That doesn't make KQL irrelevant.

For advanced hunting, detection engineering and understanding exactly what your queries are doing, I still want people in the SOC who understand KQL.

But MCP lowers the barrier to getting useful information from the data.

And that changes who can perform meaningful investigation work.

The portal change you cannot ignore

All of this also connects to Microsoft's move towards the Microsoft Defender portal.

Microsoft Sentinel is generally available in the Defender portal, including for customers without Microsoft Defender XDR or a Microsoft 365 E5 licence.

Microsoft describes the Defender portal as the primary innovation surface for Sentinel, with new Sentinel experiences landing there first.

And there is now a firm deadline.

After 31 March 2027, Microsoft will no longer support Microsoft Sentinel in the Azure portal.

Customers still using Sentinel through the Azure portal will be redirected to the Defender portal.

If you are running Sentinel in the Azure portal today, planning that transition is not a 2027 problem.

The data lake onboarding and graph experiences are already centred on the Defender portal.

Microsoft's direction is clear.

The Defender portal is the long-term home for Sentinel.

What this means in practice

A few observations from me.

First, the data lake is the capability with the clearest immediate architectural value.

Cost-effective long-term retention addresses a real problem that has shaped Sentinel designs for years.

You don't necessarily need every piece of security telemetry sitting in an expensive analytics tier waiting for a real-time query.

Some data needs immediate detection.

Some needs hunting.

Some needs investigation months later.

Some simply needs retaining.

Those are different requirements, and Sentinel can now treat them differently.

Second, parts of the graph and MCP story are still in preview.

The direction is interesting, but I would test preview capabilities in a controlled way before building critical SOC processes around them.

Preview means it can change.

Third, the agentic framing is not simply marketing, but we shouldn't interpret it as handing the SOC over to autonomous AI agents.

Microsoft is building the data, graph, MCP and agent capabilities that allow AI to take a much bigger role in security operations.

But humans still need to govern what those agents can access, what they can do and where approval is required.

I would treat AI-generated security actions much like automation or code introduced into any security environment:

Understand it. Test it. Control its permissions. Monitor it.

Then decide what you are comfortable automating.

Sentinel is changing

For me, this is one of the most significant architectural changes to Microsoft Sentinel since it launched.

Sentinel is still a SIEM.

But if your mental model of Sentinel is still:

Logs → rules → alerts → incidents

it is time to expand it.

The emerging model is closer to:

Data → context → AI reasoning → investigation → response

with the SIEM capabilities still sitting underneath it.

That is what Microsoft means when it talks about Sentinel becoming the platform for agentic defence.

The question for SOC teams now is not simply:

"Are we using Sentinel?"

It is:

"Are we designing Sentinel for where Microsoft is taking it?"

Have you started moving your Sentinel operations into the Defender portal, or are you still running them in the Azure portal?

---

## Microsoft Learn References

- [What is Microsoft Sentinel?](https://learn.microsoft.com/azure/sentinel/sentinel-overview)
- [What's new in Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/whats-new)
- [Microsoft Sentinel in the Microsoft Defender portal](https://learn.microsoft.com/azure/sentinel/microsoft-sentinel-defender-portal)
- [What is Microsoft Sentinel data lake?](https://learn.microsoft.com/azure/sentinel/datalake/sentinel-lake-overview)
- [What is Microsoft Sentinel's support for Model Context Protocol (MCP)?](https://learn.microsoft.com/azure/sentinel/datalake/sentinel-mcp-overview)

---

## Hashtags

#MicrosoftSentinel #SecOps #SIEM #AISecurity #MicrosoftSecurity #MicrosoftDefender #ThreatHunting #Cybersecurity

---

## Accuracy Notes

- **Repositioning confirmed:** Sentinel is officially "a cloud-native SIEM and unified security platform for agentic defense" — direct from the overview and application card pages.
- **Data lake: GA** — confirmed from What's new (Sept 2025) and overview. Analytics tier vs data lake tier; analytics data auto-mirrored to lake. Up to 12 years retention (from MCP application card).
- **Graph: Preview** — confirmed. Attack-path example ("which vulnerable paths from a compromised entity to a critical asset") is Microsoft's own.
- **MCP server: Preview** — confirmed. Entra for identity; clients include VS Code, Security Copilot, Copilot Studio, Foundry, ChatGPT, Claude. Roles: Security Reader/Operator/Administrator minimum; graph tools need Exposure Management read access.
- **Azure portal retirement: 31 March 2027** — confirmed from Defender portal page. Defender portal is long-term home and primary innovation surface.
- **350+ connectors, including AWS/GCP** — confirmed from overview.
- **E5 note:** Sentinel GA in Defender portal for customers with or without Defender XDR / E5 — confirmed.
- **Agentic = assisted, not autonomous:** "humans remain responsible for decisions and actions" — verbatim framing from the application card. Playbook peer-review analogy drawn from the application card best-practices section.
- **All GA/preview statuses verified this session (Aug 2026).** Graph + MCP still preview at time of writing — worth a re-check before publishing.
- Metrics check due: 2026-09-24
