# Day 26 — LinkedIn Content Package
**Topic:** Threat hunting in Microsoft Sentinel and Defender XDR — proactive vs reactive detection
**Category:** Security Operations
**Format:** Technical article
**Note:** Originally drafted as Day 24. Stuart posted on Day 26. Completes the SecOps thread: Day 14 (Defender XDR), Day 19 (Sentinel), Day 26 (hunting).

---

## LinkedIn Article (Stuart's version — published)

Your Sentinel workspace is generating alerts. That is not the same as hunting for threats.

Analytics rules trigger when a known pattern matches your data. They detect what you expected to see. Threat hunting is different. It starts with a hypothesis and looks for behaviour you did not expect, before an incident exists, before an alert fires and, ideally, before the damage is done.

Many organisations running Microsoft Sentinel rarely perform structured threat hunting unless they have a mature SOC or a managed detection service. The capability has been there for years. The queries already exist, many of which are mapped to MITRE ATT&CK. The question is simple: have you opened the Hunting page?

Why this gap matters

Attackers understand how detection rules work. They adapt their techniques to stay below thresholds or avoid known patterns, particularly when an organisation relies on default analytics rules. Long dwell times, the period between initial access and discovery, often happen because an attacker remained just outside the conditions your detections were designed to identify.

I wrote about the analytics rules gap in an earlier post. Threat hunting sits above that. Instead of waiting for a rule to match, you actively search for behaviour that has not yet been detected.

What Microsoft gives you out of the box

Microsoft Sentinel includes a dedicated Hunting page. In the Microsoft Defender portal, go to Threat management > Hunting > Queries. Many Microsoft and partner solutions installed from Content Hub include hunting queries alongside analytics rules and workbooks, with queries mapped to MITRE ATT&CK tactics and techniques.

You can run all queries or focus on those that support your hunting hypothesis. Sort the results by Result count, Results delta or changes over the previous 24 hours. Sudden increases or decreases often tell a more interesting story than large numbers alone.

Microsoft Defender XDR also includes Advanced Hunting, providing up to 30 days of raw telemetry from Defender for Endpoint, Defender for Identity, Defender for Office 365 and Defender for Cloud Apps. When Microsoft Sentinel is connected to the Defender portal, you can also query Sentinel workspace data from the same interface. As of February 2026, the EntraIdSignInEvents table provides direct access to interactive and non-interactive Entra sign-in events, making identity-based threat hunting much easier.

Both environments use Kusto Query Language (KQL). If you already write analytics rules, you already have the skills to begin hunting.

A workflow that produces results

Threat hunting without a hypothesis is simply browsing.

Start by deciding what you are looking for and why.

Three practical examples:

* A threat intelligence report describes an active campaign abusing OAuth application consent. Search your environment for recently consented applications, unusual permission grants, or suspicious sign-in activity associated with them.
* Your analytics dashboards show an increase in authentication failures, but no alerts have fired. Hunt the underlying events to understand what is driving the change.
* You onboarded a new data source last month. Run the hunting queries supplied with that solution to learn what normal activity looks like before you need to investigate an incident.

When a query returns something suspicious, create a bookmark. Bookmarks preserve the query, your notes, the result set and the associated MITRE ATT&CK mapping. From there you can create an incident directly or convert the hunt into a new analytics rule.

This is how detection engineering improves over time. Every successful hunt should improve your environment. That may mean creating a new analytics rule, refining an existing one, documenting expected behaviour or confirming that unusual activity is actually benign.

Mature SOCs do not only hunt for attackers. They also hunt to validate that their detection coverage still works after infrastructure changes, new applications or emerging attack techniques.

Where to start today

Open the Microsoft Defender portal and go to Microsoft Sentinel > Threat management > Hunting > Queries.

Select Run all queries if you are new to hunting, or choose a small group of queries related to a specific hypothesis.

Sort the results by Results delta.

Look for activity that changed during the last 24 hours but has no corresponding alert.

Some queries will return nothing.
Some will show expected activity.
Occasionally, one will reveal behaviour that has been sitting quietly in your environment for weeks because no detection rule was ever written to find it.

Most hunts do not uncover an active attacker, and that is a good outcome. It tells you your environment behaved as expected or that your existing detections are working. The hunt that does find something unusual often becomes tomorrow's analytics rule.

That is why you hunt.

---

## Microsoft Learn References

- [Threat hunting in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/hunting)
- [Conduct end-to-end proactive threat hunting in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/hunts)
- [Proactively hunt for threats with advanced hunting in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Advanced hunting with Microsoft Sentinel data in Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-microsoft-defender)
- [View MITRE ATT&CK framework coverage in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/mitre-coverage)
- [Keep track of data during hunting with Microsoft Sentinel (Bookmarks)](https://learn.microsoft.com/en-us/azure/sentinel/bookmarks)
