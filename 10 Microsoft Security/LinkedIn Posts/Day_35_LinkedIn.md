# Day 35 — LinkedIn Content Package
**Topic:** Microsoft Purview Insider Risk Management — behavioural signals DLP cannot see
**Category:** Compliance / Security Operations
**Date:** 2026-07-08
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Your DLP policy flagged the download. It did not flag the 500 downloads that happened in the three days before a user resigned.

**Hook 2:**
DLP watches what data moves. Insider Risk Management watches who is moving it, and whether the pattern makes sense.

**Hook 3:**
You have Microsoft Purview Insider Risk Management licenced. In most tenants, zero policies are active.

---

## LinkedIn Article (Stuart's version — published)
**Note:** Key changes from draft: hook softened from "500 downloads" to "hundreds of downloads" (avoids inventing a specific statistic); expanded DLP description to include sharing/copying/emailing/uploading; IRM capabilities listed as bullets; added detail on auditing of de-anonymisation actions; prerequisites section expanded for Data leaks template (HR connector for connected systems, not account deletion trigger); Adaptive Protection section expanded with tiered enforcement example (Low/Moderate/Elevated); specific 72hr figure removed ("allow sufficient time"); close aphorism expanded to "DLP tells you what happened. Insider Risk Management helps explain why it happened and whether the pattern of behaviour represents a genuine insider risk."

Your DLP policy flagged the download.
It did not flag the hundreds of downloads that happened over the previous days before the employee resigned.
That is the difference between content-based detection and behavioural detection.
Microsoft Purview Data Loss Prevention (DLP) focuses on protecting sensitive information during user activities such as sharing, copying, emailing or uploading content. Microsoft Purview Insider Risk Management (IRM) looks at patterns of behaviour over time. In many organisations I review, IRM is already licensed but has never been configured.

What IRM sees that DLP does not

Microsoft Purview Data Loss Prevention detects sensitive content during supported user activities. It can identify when someone emails a document containing sensitive information, copies regulated data to a USB device, uploads files to cloud services, or performs other monitored actions that match DLP conditions.

Microsoft Purview Insider Risk Management takes a different approach.

Instead of looking at a single event, it correlates behavioural signals across Microsoft 365 together with organisational context and, where configured, information from connected HR systems and Microsoft Defender. It builds a picture of how a user is behaving over time.

It can identify patterns such as:

* large numbers of file downloads
* repeated printing of sensitive documents
* unusual access to SharePoint or OneDrive content
* copying files to removable media
* sending data outside the organisation

On their own, none of these activities necessarily indicate malicious intent.
Combined over several days, and viewed alongside indicators such as an employee leaving the business or a high-confidence security alert, they can represent a genuine insider risk.

Privacy by design, not privacy by accident

The first question I hear when organisations consider enabling Insider Risk Management is usually about privacy.

Microsoft designed the platform with privacy built in.

User identities are pseudonymised by default. Analysts investigating alerts see anonymised identifiers rather than employee names. Access to reveal identities requires a separate permission, and every de-anonymisation action is audited.

Role separation is equally important.

The people who configure policies do not have to be the same people investigating alerts. Microsoft provides separate role groups for administrators, analysts, investigators and auditors.

HR and Legal should be involved before policies are enabled, not after the first alert is generated.

The prerequisites most teams skip

Every Insider Risk Management policy starts from a template.

Many of those templates depend on prerequisites that organisations have never configured.

The Data theft by departing users template relies on Microsoft 365 HR connectors to import resignation or termination information from supported HR systems. Without those signals, the policy cannot identify users who are leaving the organisation.

The Data leaks template depends on Microsoft Purview DLP generating high-severity incident reports. If your DLP policies are only running in simulation mode, or your rules never generate high-severity incidents, Insider Risk Management has nothing to use as a trigger.

The Security policy violations template requires Microsoft Defender for Endpoint integration to enable security alerts to contribute to insider risk scoring.

One setting catches organisations out more than any other.

Policy indicators are disabled globally by default.

Even after creating policies, no alerts will be generated until the required indicators have been enabled in Insider Risk Management settings.

Adaptive Protection: behavioural signals driving policy decisions

One of the most useful integrations is Adaptive Protection.

Adaptive Protection allows Microsoft Purview DLP and Microsoft Entra Conditional Access to use the insider risk level assigned by Insider Risk Management.

As a user's risk level changes, organisations can apply different controls for different users.

For example:

* Low-risk users may simply receive a policy tip.
* Moderate-risk users may be required to provide a business justification.
* Elevated-risk users can be blocked from performing the same action altogether.

As risk levels decrease, additional controls can also be automatically relaxed.

Adaptive Protection also creates a retention policy that preserves deleted Exchange Online, SharePoint Online and OneDrive content created by elevated-risk users for 120 days, supporting later investigations if required.

Like many Microsoft security services, analytics take time to build. Allow sufficient time after enabling Insider Risk Management and Adaptive Protection before expecting meaningful behavioural insights.

Where to look today

Open the Microsoft Purview portal and navigate to Insider Risk Management.

Check:

* Are any Insider Risk Management policies configured?
* Are they reporting a healthy status?
* Have the required policy indicators been enabled?
* If you're using the Data leaks template, are your DLP policies generating high-severity incident reports?

Without those foundations, Insider Risk Management cannot produce meaningful alerts.

Insider Risk Management does not replace DLP.
DLP tells you what happened.
Insider Risk Management helps explain why it happened and whether the pattern of behaviour represents a genuine insider risk.

Have you enabled Insider Risk Management in your organisation?
If so, which policy templates have provided the most value?

---

## Microsoft Learn References

- [Learn about Insider Risk Management](https://learn.microsoft.com/purview/insider-risk-management)
- [Learn about Insider Risk Management policy templates](https://learn.microsoft.com/purview/insider-risk-management-policy-templates)
- [Microsoft Purview Insider Risk Management and Communication Compliance privacy guide](https://learn.microsoft.com/purview/insider-risk-solution-privacy)
- [Help dynamically mitigate risks with Adaptive Protection](https://learn.microsoft.com/purview/insider-risk-management-adaptive-protection)
- [Configure policy indicators in Insider Risk Management](https://learn.microsoft.com/purview/insider-risk-management-settings-policy-indicators)

---

## Suggested Image Concept

Microsoft Purview Insider Risk Management alert dashboard showing a user's risk activity timeline, with multiple download and print events clustered in a short window. The pattern is visible in the chart; no single event would have triggered a DLP alert alone. Shows what "behavioural detection" means in practice.

---

## Three Alternative Discussion Questions

1. Have you enabled Insider Risk Management policies in your organisation, and if so, which templates have been most useful?
2. How did your organisation handle the privacy and employment law questions when enabling Insider Risk Management?
3. Is Adaptive Protection something your organisation has configured, or is the IRM-to-DLP integration still on the roadmap?

---

## Hashtags

#MicrosoftPurview #InsiderRisk #MicrosoftSecurity #DataSecurity #MicrosoftCompliance
