# Day 49 — LinkedIn Content Package
**Topic:** Microsoft Security Copilot — the AI layer that compresses the analyst timeline
**Category:** SecOps / AI Security
**Date:** 2026-07-24
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
An incident arrives in Microsoft Defender XDR. It has 23 alerts, across 4 devices, with 6 affected users.
An experienced analyst takes around 45 minutes to read the alerts, correlate the entities, check the threat intelligence, and understand what happened. A junior analyst takes longer — and may miss connections an experienced analyst would catch.
Security Copilot produces the summary in under a minute.

**Hook 2:**
Microsoft's Phishing Triage Agent identifies 6.5 times more malicious alerts than human analysts working alone.
Not because human analysts are poor at their jobs. Because the volume of phishing submissions arriving in a typical SOC exceeds what any team can review thoroughly at the pace attacks move.

**Hook 3:**
The constraint in most security operations is not intelligence.
Microsoft's security platform generates enormous signal across email, endpoints, cloud apps, and identity.
The constraint is the time it takes an analyst to read that signal, connect the dots, and decide what to do next.

---

## LinkedIn Article (Stuart's version — published 2026-07-25)
**Note:** Key changes from draft: portal URL corrected to securitycopilot.microsoft.com (not security.copilot.microsoft.com); connected products listed explicitly (Defender XDR, Sentinel, Entra, Intune, MDCA); MDTI framed as "where licensed" (separate licensing consideration); script analysis caveat added — "Analysts should still validate the findings before taking action" (responsible AI framing); KQL: "generates and explains" + "refined if needed"; agents section simplified — removed specific GA/Preview status labels for individual agents and 6.5x stat, replaced with "some generally available and others in preview depending on the capability"; week arc section includes actual LinkedIn article links for Days 46-47-48; licensing section significantly simplified — removed specific E5/E7 SCU numbers (400 SCUs per 1,000 users), kept broader framing "organisations should review the current licensing guidance before deployment"; embedded vs standalone distinction: "Embedded Security Copilot experiences continue to expand...while the standalone Security Copilot service uses provisioned SCU capacity"; close changed "signal" to "telemetry"; discussion question simplified to two short questions.

Microsoft Security Copilot, the AI layer that compresses the analyst timeline

An incident arrives in Microsoft Defender XDR. It has 23 alerts across four devices, with six affected users.

An experienced analyst might spend 45 minutes reading the alerts, correlating the affected entities, checking relevant threat intelligence and understanding the full scope of what happened. A junior analyst may take longer and miss connections an experienced colleague would spot.

Microsoft Security Copilot can produce an incident summary in under a minute.

That is not the whole story.

But it is the part that matters most for understanding what Microsoft Security Copilot is, and what it is not.

This week I have covered Microsoft Defender for Office 365, Defender for Cloud Apps and Defender Vulnerability Management.

Security Copilot is the AI layer that works across those products, helping analysts understand and respond to security incidents faster.

What Security Copilot actually is

Microsoft Security Copilot is a generative AI security solution designed to help security professionals investigate, respond to and understand threats more quickly.

It is not a general-purpose AI assistant.

It works with your Microsoft security data, including incidents and alerts from Microsoft Defender XDR, Microsoft Sentinel, Microsoft Entra, Microsoft Intune, Microsoft Defender for Cloud Apps and other connected Microsoft security products and supported plugins.

Where licensed, it can also incorporate Microsoft Defender Threat Intelligence.

The result is that when you ask Copilot to summarise an incident, it is analysing the incident in your own tenant rather than generating a generic response.

Security Copilot is available through the standalone portal at securitycopilot.microsoft.com, and through embedded experiences across Microsoft security products. Most analysts will first encounter it in Microsoft Defender XDR.

Core capabilities

Four capabilities provide immediate value for most security teams.

Incident summarisation is the most obvious.

From a Defender XDR incident, Security Copilot generates a natural-language summary describing what happened, when it happened, which entities were involved, and how the attack progressed. Analysts can use that as the starting point for an investigation rather than spending significant time manually building the picture.

Script analysis addresses one of the more time-consuming parts of incident response.

When a suspicious PowerShell, Bash or batch script appears in an alert, Security Copilot explains what the script is doing in plain language and highlights potentially malicious behaviour. Analysts should still validate the findings before taking action, but the time taken to understand unfamiliar scripts is significantly reduced.

KQL generation helps analysts build Advanced Hunting queries using natural language.

Rather than remembering every table and operator, analysts can describe what they are trying to investigate, and Security Copilot generates and explains a Kusto Query Language (KQL) query that can then be refined if needed.

Executive reporting produces incident summaries written for non-technical audiences.

Instead of writing board updates from scratch, analysts can generate an executive summary from the incident and then review and tailor it before distribution.

Agents: moving from assistance to automation

Microsoft has introduced Security Copilot agents that perform specific security tasks with minimal analyst interaction.

The Phishing Triage Agent helps classify user-reported phishing submissions, reducing the volume of routine manual investigations.

The Threat Intelligence Briefing Agent produces structured threat intelligence summaries based on current intelligence.

Additional agents continue to be introduced across Microsoft security products, with some generally available and others in preview depending on the capability.

These agents are not replacing analysts.

They reduce the time spent on repetitive work, allowing analysts to focus on investigations that require human judgement.

Connecting back to this week

Security Copilot becomes more valuable as more Microsoft security products are connected.

The phishing email we covered on Monday generates alerts in Defender for Office 365: [Microsoft Defender for Office](https://www.linkedin.com/pulse/finance-manager-receives-email-from-ceo-stuart-mann-cvb7e/)
Security Copilot can summarise the incident, identify affected users and suggest investigation and remediation steps.

The cloud application activity from Tuesday appears in Defender for Cloud Apps: [Microsoft Defender for Cloud Apps](https://www.linkedin.com/pulse/microsoft-defender-cloud-apps-security-layer-most-havent-stuart-mann-e9g8f/)
Security Copilot correlates those events with endpoint, identity and email activity to provide a broader incident view.

The vulnerability we discussed on Wednesday appears in Defender Vulnerability Management: [Microsoft Defender Vulnerability Management](https://www.linkedin.com/pulse/microsoft-defender-vulnerability-management-knowing-your-stuart-mann-jlc2e/)
Security Copilot can explain the vulnerability, identify affected assets and help prepare remediation guidance.

Each Microsoft security product generates valuable signals.

Security Copilot helps analysts understand those signals faster.

Licensing and capacity

Security Copilot uses Security Compute Units (SCUs), which provide the processing capacity required to run prompts and AI workloads.

Unlike traditional per-user licensing, organisations provision SCU capacity based on expected usage.

Embedded Security Copilot experiences continue to expand across Microsoft security products, while the standalone Security Copilot service uses provisioned SCU capacity.

Microsoft continues to evolve both the licensing model and embedded experiences, so organisations should review the current licensing guidance before deployment.

Where to look today

Open Microsoft Defender and navigate to an active incident.

If Security Copilot is available, generate an incident summary and compare it with your normal investigation process.

Review the available Security Copilot agents within the Microsoft Defender portal and determine which are enabled in your environment.

If you have standalone Security Copilot, visit securitycopilot.microsoft.com and review the plugins associated with your Microsoft security estate.

The biggest constraint in most SOCs is not a lack of telemetry.

It is the time it takes analysts to turn that telemetry into understanding and action.

That is the problem Microsoft Security Copilot is trying to solve.

Is your organisation using Microsoft Security Copilot today?
If so, which capability has made the biggest difference to your investigations?

---

## Microsoft Learn References

- [What is Microsoft Security Copilot?](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot)
- [Microsoft Security Copilot Security Compute Units and capacity](https://learn.microsoft.com/en-us/copilot/security/security-compute-units-capacity)
- [Security Copilot inclusion for Microsoft 365 E5 and E7 customers](https://learn.microsoft.com/en-us/copilot/security/security-copilot-inclusion)
- [Microsoft Security Copilot and Chat in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-in-microsoft-365-defender)
- [Summarize incidents with Microsoft Copilot in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-m365d-incident-summary)
- [Investigate an incident's malicious script](https://learn.microsoft.com/en-us/copilot/security/investigate-incident-malicious-script)
- [Use promptbooks in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/using-promptbooks)
- [Microsoft Security Copilot Phishing Triage Agent in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/phishing-triage-agent)
- [Microsoft Security Copilot Security Alert Triage Agent in Microsoft Defender (Preview)](https://learn.microsoft.com/en-us/defender-xdr/security-alert-triage-agent)
- [Deploy AI agents in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-agents-defender)

---

## Suggested Image Concept

Microsoft Defender XDR incident page showing the Copilot incident summary panel open alongside a complex incident with multiple alerts and affected entities — demonstrating the AI-generated natural language summary produced from real tenant data.

---

## Three Alternative Discussion Questions

1. Is your organisation using Security Copilot today, and if so, which capability has had the most practical impact on your team's day-to-day investigations?
2. Has your organisation enabled the Phishing Triage Agent, and if so, have you reviewed what percentage of submissions it is classifying versus escalating to analyst review?
3. For organisations with M365 E5 licences that have not yet explored Security Copilot — what has been the barrier: awareness, trust in AI output, or something else?

---

## Week Theme Close — Completing the Defender XDR Picture

Day 46: Defender for Office 365 — the email attack that passes the spam filter
Day 47: Defender for Cloud Apps — the data that leaves via a personal Dropbox
Day 48: Defender Vulnerability Management — the 3,847 findings and which 40 matter
Day 49: Security Copilot — the AI layer that turns signal into action faster

---

## Hashtags

#MicrosoftSecurity #SecurityCopilot #DefenderXDR #AIinSecurity #MicrosoftSecurity365
