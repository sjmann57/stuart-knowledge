# Day 36 — LinkedIn Content Package
**Topic:** Microsoft Purview Communication Compliance — the conversations your DLP policy cannot see
**Category:** Compliance / Regulatory
**Date:** 2026-07-08
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Your DLP policy prevents an employee from emailing a file containing credit card numbers. It does not monitor what that same employee typed into Microsoft 365 Copilot ten minutes earlier.

**Hook 2:**
Global Administrators do not have access to Microsoft Purview Communication Compliance by default. That is not a typo. It is documented, and it catches almost every organisation the first time.

**Hook 3:**
Microsoft Purview Communication Compliance monitors Teams, Exchange, Viva Engage, and Copilot prompts and responses. In most regulated tenants I review, it is licensed and not configured.

---

## LinkedIn Article (Stuart's version — published, going out 2026-07-09)
**Note:** Key changes from draft: Hook expanded to cover Copilot AND inappropriate/non-compliant communications (broader than Copilot alone); Global Admin gotcha softened — draft said "Global Admins have NO access by default" but Stuart's version says "Although Global Administrators can access and configure Communication Compliance, Microsoft recommends using dedicated role groups" (note: Microsoft Learn docs state "By default, Global Administrators don't have access" — Stuart verified/softened this claim in his tenant context); review percentage framing changed to "matched communications" (more precise); Copilot pay-as-you-go section expanded with specific product names (Security Copilot, Copilot Studio, Fabric Copilot, third-party AI); close aphorism expanded to three lines distinguishing DLP vs CC.

Your DLP policy prevented an employee from emailing a file containing credit card numbers.
It does not tell you whether that same employee spent the previous ten minutes asking Microsoft 365 Copilot questions about customer data, or whether their conversations contained threatening, inappropriate, or non-compliant communications.
That is the gap Microsoft Purview Communication Compliance fills. In most tenants I review with a Microsoft 365 E5 licence, it is included, and nobody has configured it.

What Communication Compliance monitors

Microsoft Purview Data Loss Prevention protects sensitive information during supported user activities such as sharing, emailing, copying or uploading content.
Microsoft Purview Communication Compliance watches the communications themselves.

It monitors messages in Microsoft Teams channels and private chats, Exchange Online email, Viva Engage, and prompts and responses entered into Microsoft 365 Copilot and Microsoft 365 Copilot Chat. Coverage can also be extended to supported third-party communication sources through connectors.

For organisations in financial services, healthcare, or any regulated sector where supervisory review of communications is a regulatory requirement, this is not optional. It is part of the compliance programme.

The first gotcha most teams hit

One of the first things that catches organisations out is permissions.

Although Global Administrators can access and configure Communication Compliance, Microsoft recommends using dedicated Communication Compliance role groups that separate administration from investigations.

Communication Compliance provides dedicated role groups including Communication Compliance Administrators, Analysts, Investigators and Viewers. In most organisations, the people configuring policies should not be the same people reviewing or investigating alerts.

After assigning role groups, allow up to 30 minutes for permissions to propagate before expecting access to the solution.

Policy templates and the review percentage most teams do not notice.

Communication Compliance provides predefined templates for the most common scenarios.

The Detect inappropriate text template covers harassment, discrimination, threats and profanity across Teams, Exchange Online and Viva Engage.

The Detect financial regulatory compliance template covers customer complaints, gifts and entertainment, money laundering, stock manipulation and other regulatory classifiers.

What I see organisations miss is the review percentage.

The inappropriate text template defaults to reviewing 100% of matched communications.

The financial regulatory compliance template defaults to reviewing 10%.

If your organisation is in financial services and relies on the regulatory compliance template, you are reviewing one in ten matched communications by default. Whether that satisfies your regulatory obligations depends on your own supervisory requirements, so it is worth confirming before your next audit.

Channel coverage is not automatic.

Communication Compliance supports Exchange Online and Microsoft Teams once the required permissions, auditing and policies have been configured.

Viva Engage requires your tenant to be running in Native Mode before private messages and community conversations can be monitored. Without Native Mode, those communications are outside the policy scope.

Microsoft 365 Copilot and Microsoft 365 Copilot Chat prompts and responses can be monitored without additional pay-as-you-go billing.

For other AI services, including Microsoft Security Copilot, Microsoft Copilot Studio, Microsoft Fabric Copilot and supported third-party AI applications, Microsoft currently requires pay-as-you-go billing in addition to the appropriate licensing.

One timing point is worth knowing.

Exchange Online email can take up to approximately 24 hours before appearing in Communication Compliance.
Microsoft Teams communications can take up to approximately 48 hours.
Other supported sources have their own ingestion schedules, so newly created policies should always be given time before assuming they are not working.

One more point that surprises people.

Communication Compliance policies cannot currently be created or managed with PowerShell. Configuration is performed through the Microsoft Purview portal.

Connection to Insider Risk Management

Communication Compliance integrates with Microsoft Purview Insider Risk Management.

Depending on the policy configuration, Communication Compliance signals can contribute additional context to Insider Risk investigations alongside file activity, security alerts and other behavioural indicators.

If a user generates Communication Compliance alerts while also exhibiting unusual file access patterns or endpoint security events, investigators have a much richer picture than either solution alone provides.

I covered how Insider Risk Management builds that behavioural picture in a previous post.

Where to look today

Open the Microsoft Purview portal and navigate to Communication Compliance.

If the solution is not visible, start by checking your role assignment.

If policies already exist, review the default review percentage for each policy. Confirm whether Viva Engage is included where required and whether your tenant is running in Native Mode.

Review whether Microsoft 365 Copilot interactions are included in your monitoring strategy.

If the policy list is empty, there is a good chance the licence is already available.
The configuration simply has not been completed.

Communication Compliance does not replace DLP.
DLP protects sensitive information.
Communication Compliance helps you understand the conversations surrounding that information.

For organisations with supervisory review obligations, those are two different audit trails.

Have you configured Communication Compliance policies in your organisation, and how are you managing the review workflow for investigators?

---

## Microsoft Learn References

- [Learn about Communication Compliance](https://learn.microsoft.com/purview/communication-compliance)
- [Get started with Communication Compliance](https://learn.microsoft.com/purview/communication-compliance-configure)
- [Create and manage Communication Compliance policies](https://learn.microsoft.com/purview/communication-compliance-policies)
- [Plan for Communication Compliance](https://learn.microsoft.com/purview/communication-compliance-plan)
- [Configure a Communication Compliance policy to detect generative AI interactions](https://learn.microsoft.com/purview/communication-compliance-copilot)

---

## Suggested Image Concept

Microsoft Purview Communication Compliance alert dashboard showing a flagged Teams message with a classifier match highlighted. The policy name visible at the top, the review workflow showing the message pending triage. Demonstrates what "watching the conversation" looks like in practice.

---

## Three Alternative Discussion Questions

1. Have you configured Communication Compliance policies in your organisation, and how are you handling the review workflow for alerts?
2. For those in regulated industries — are you using Communication Compliance to meet supervisory review requirements such as FINRA Rule 3110, and how do you manage the reviewer workload?
3. Has your organisation started using Communication Compliance to monitor Microsoft 365 Copilot prompts and responses, and what prompted that decision?

---

## Hashtags

#MicrosoftPurview #CommunicationCompliance #MicrosoftSecurity #MicrosoftCompliance #MicrosoftCopilot
