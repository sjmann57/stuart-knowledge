# Day 19 — LinkedIn Content Package
**Topic:** Microsoft Sentinel — licence vs. running threat detection, and the Azure portal retirement
**Category:** Security Operations
**Framework:** Microsoft Guidance vs Real-World Implementation
**Format:** Research-backed article (Day 6+ format)
**Builds on:** Day 14 (Defender XDR) — completes the Security Operations picture

---

## 1. Title

Sentinel is in your licence. That does not mean threat detection is running.

---

## 2. LinkedIn Post (Stuart's version — published)

A couple of weeks ago, I wrote about Defender XDR and the gap between having five security products and having a security platform. Sentinel sits alongside that conversation, and the same pattern appears.

Microsoft Sentinel is a cloud-native SIEM. It collects data across users, devices, applications, and infrastructure, on-premises and across multiple clouds. It detects threats using analytics rules, maps coverage to the MITRE ATT&CK framework, and automates response through playbooks built on Azure Logic Apps. When it is working properly, it is one of the most capable security operations platforms available.

Most organisations I work with have Sentinel in their stack. Few have it working as efficiently as possible.

What I find in practice falls into a few consistent patterns.

I often find organisations collecting far more data than they actively use. Data collection should follow detection requirements, not the other way around. Data connectors have been deployed, data is being ingested, and basic analytics are enabled. The out-of-the-box analytic rules exist for a reason. They cover common attack patterns, anomalous sign-ins, lateral movement, and persistence techniques. Enabling them can be done quickly. Many organisations either haven't enabled the relevant rules, or they haven't tuned them, leaving noise and missed detections. The workspace has data, but what value is it giving?

The second pattern is SOAR. Sentinel supports automation through playbooks, which are Logic Apps workflows that can trigger on an alert or incident and take action automatically. Notify a team. Isolate a device. Revoke a session. Open a ticket in ServiceNow. The capability is there. In practice, I rarely find it configured beyond the most basic alert notification.

The third thing worth knowing right now is that the Azure portal experience for Sentinel is being retired. After March 31, 2027, Sentinel will only be available through the Microsoft Defender portal. Microsoft has had Sentinel available in the Defender portal for some time now, and the unified experience is better; your Sentinel incidents, Defender XDR alerts, and identity signals all in the same view. But if your team is still working in the Azure portal, the clock is ticking. Planning that transition now, rather than in Q1 2027, is the sensible approach.

There are many articles here on LinkedIn and in Microsoft Learn to help you get the most from Microsoft Sentinel. Before you go down a rabbit hole, think about what you want to detect, the data sources available to you, and which signals give you value.

A few top tips to help

What are you trying to protect and detect? Spend some time thinking about what the solution is to achieve, and have defined outcomes.

Ensure you are ingesting high-value security logs, and review retention policies so older data is moved to lower-cost storage where appropriate without affecting investigation requirements.

If using the out-of-the-box analytics, spend time tuning them and making them useful, tuning out false positives. Watchlists can help enrich detections and reduce noise when used alongside rule tuning and suppression logic.

For SOAR, what do you do regularly? Document it and then automate it with playbooks.

---

## 3. Microsoft Learn References

- What is Microsoft Sentinel: https://learn.microsoft.com/en-us/azure/sentinel/overview
- Detect threats with built-in analytics: https://learn.microsoft.com/en-us/azure/sentinel/detect-threats-built-in
- Automate threat response with playbooks: https://learn.microsoft.com/en-us/azure/sentinel/automate-responses-with-playbooks
- Microsoft Sentinel in the Microsoft Defender portal: https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-defender-portal

---

## 4. Suggested Image Concept

Dark background, clean text. Large text: "Sentinel is ingesting your logs." Below it: "That is not the same as detecting threats." Microsoft Sentinel logo bottom-right.

Alternative: Quote card — "The licence is not the security posture."

---

## 5. Alternative Discussion Questions

1. Have you enabled the out-of-the-box Sentinel analytic rules, or is your workspace relying on default configuration?
2. Have you built any SOAR playbooks in Sentinel, or is your incident response still manual?
3. Is your Sentinel environment in the Azure portal or the Defender portal, and have you planned for the March 2027 migration?

---

## 6. Hashtags

#MicrosoftSentinel #SecurityOperations #SIEM #ZeroTrust #SecurityArchitect

---

## Day 19 Checklist

- [ ] The "incident queue is empty — that is not a good sign" observation is the sharpest line; add your own example if you have seen this in an engagement
- [ ] The March 2027 Defender portal retirement is timely and most people won't know about it — worth a follow-up comment linking to the Microsoft blog on the migration
- [ ] "The licence is not the security posture" — this runs through the whole series and lands well as a closing image
- [ ] Post with graphic or personal photo
- [ ] Add follow-up comment within 30 minutes
