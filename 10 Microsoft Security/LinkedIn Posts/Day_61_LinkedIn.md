# Day 61 — LinkedIn Content Package
**Topic:** Microsoft Defender for Servers — Plan 1, Plan 2, and the controls most organisations haven't turned on
**Category:** Cloud Security / Endpoint Security
**Week theme:** Microsoft Defender for Cloud (Days 60–63)
**Date:** 2026-08-05 (Tuesday)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft hook):**
The most common finding when I review an Azure environment is open management ports.
RDP or SSH. Exposed to the internet. Open all the time.
Not because anyone decided that was acceptable.
Because nobody ever changed the default.

**Hook 2:**
Virtual machines are still the most common workload in enterprise Azure environments.
They are also one of the most frequently under-protected.
Defender for Servers is designed to change that.

**Hook 3:**
Enabling Defender for Servers is not the same as configuring it.
Most organisations enable the plan, see the Secure Score recommendation disappear, and move on.
The controls that make the biggest difference are not always on by default.

---

## LinkedIn Article (published — 2026-08-05)

Microsoft Defender for Servers: the two plans and the controls most organisations haven't turned on

A team builds a new set of servers, "just for testing", they say, but accidentally deploys them into a production subscription. No one reviews Secure Score or Defender for Cloud recommendations. When I later review the environment, I find the management ports are open.

RDP or SSH.

Exposed to the internet.

Open all the time.

Not because anyone decided that was acceptable.

Because nobody ever checked and changed the default, and there is a lack of process.

Microsoft Defender for Servers is the Microsoft Defender for Cloud plan designed to protect Windows and Linux servers running in Azure, AWS, Google Cloud Platform and on-premises environments.

It is one of the most valuable Defender Plans available and also one of the most consistently under-configured.

Today I want to look at what Defender for Servers actually provides, the difference between Plan 1 and Plan 2, and the controls worth reviewing and enabling as soon as the plan is in place.

Two plans

Microsoft Defender for Servers is available in two plans.

Plan 1 provides the core protection layer.

It includes integration with Microsoft Defender for Endpoint, endpoint detection and response (EDR), security recommendations, software inventory, core vulnerability assessment capabilities powered by Microsoft Defender Vulnerability Management, security alerts and attack detection.

When enabled, Defender for Servers automatically provisions Microsoft Defender for Endpoint on supported Azure virtual machines. For AWS, Google Cloud Platform and on-premises servers, onboarding depends on the connected environment and Azure Arc where applicable.

Plan 2 includes everything in Plan 1 and adds a much broader set of cloud security capabilities.

These include:

- Agentless machine scanning
- Just-in-time VM access
- File Integrity Monitoring
- Premium Microsoft Defender Vulnerability Management capabilities
- Agentless malware scanning
- Secrets scanning
- Sensitive data discovery
- OS configuration assessment
- Attack path context through Defender CSPM

For most organisations, Plan 2 delivers the capabilities that significantly reduce attack surface rather than simply detecting attacks.

Microsoft Defender for Endpoint integration

Microsoft Defender for Endpoint forms the foundation of both plans.

Once onboarded, servers appear alongside workstations and other endpoints in the Microsoft Defender portal, allowing security teams to investigate incidents across identities, endpoints, email and cloud workloads from a single incident queue.

Modern deployments rely primarily on Microsoft Defender for Endpoint, complemented by agentless machine scanning where supported.

However, some Defender for Cloud capabilities continue to use Azure Monitor Agent and Log Analytics workspaces where appropriate, including features such as File Integrity Monitoring. Older Log Analytics Agent deployments are being retired and should no longer be used for new deployments.

If you are reviewing older documentation, you will often see references to the Log Analytics Agent. Microsoft now recommends Microsoft Defender for Endpoint and Azure Monitor Agent depending on the capability being used.

Just-in-time VM access

Just-in-time VM access remains one of the highest-value controls in Defender for Servers Plan 2.

Management ports such as RDP (3389) and SSH (22) are frequently left permanently open to simplify administration.

That convenience creates a permanent attack surface.

Just-in-time access reverses the model.

Management ports remain closed until authorised users request access.

Access is approved for a limited period, can be restricted to specific source IP addresses and is automatically removed when the approved window expires.

For many organisations this is one of the quickest ways to reduce internet-facing attack surface without affecting day-to-day administration.

I would also be looking at Azure Bastion to remove direct RDP and SSH exposure altogether, but that is a topic for another day.

Just-in-Time VM Access and Azure Bastion complement each other. One limits when management ports can be used; the other removes the need to expose them to the internet in the first place.

Vulnerability assessment

Both plans provide vulnerability assessment through Microsoft Defender Vulnerability Management.

Plan 2 extends this by adding agentless machine scanning, allowing operating systems, installed software and security posture to be assessed without requiring additional software to be deployed to the machine.

Plan 2 also introduces agentless malware scanning and secrets scanning, helping identify exposed credentials, certificates, connection strings and other sensitive information stored on disks.

These capabilities complement Microsoft Defender for Endpoint rather than replacing it.

File Integrity Monitoring

File Integrity Monitoring is included with Defender for Servers Plan 2.

It monitors changes to critical operating system files, Windows Registry keys and selected Linux system files that may indicate unauthorised activity or compromise.

Microsoft has modernised File Integrity Monitoring.

New deployments use Microsoft Defender for Endpoint together with Azure Monitor Agent rather than the legacy Log Analytics Agent.

The feature still requires a Log Analytics workspace because change data is stored and processed there.

File Integrity Monitoring is not enabled automatically.

If compliance frameworks such as PCI DSS require file monitoring, it should be reviewed and enabled as part of the initial Defender for Servers deployment.

On-premises and multicloud

Defender for Servers supports Azure, AWS, Google Cloud Platform and on-premises servers.

For non-Azure servers, Azure Arc provides the management plane that enables Defender for Cloud to deliver the full Defender for Servers experience.

Servers connected through Azure Arc can receive the same Defender for Servers capabilities as Azure virtual machines, subject to the features supported by the connected environment.

Simply installing Microsoft Defender for Endpoint on an on-premises server does not provide the full Defender for Servers capability set.

Azure Arc remains the recommended approach. Also consider whether management groups, subscriptions and Azure Policy align with your security boundaries.

Where to look today

Open Microsoft Defender for Cloud and navigate to Environment settings.

Review which subscriptions have Defender for Servers enabled and confirm whether they are using Plan 1 or Plan 2.

Then review the Defender for Servers settings and confirm which optional capabilities have been enabled.

I would focus on four areas first:

- Just-in-time VM access: identify internet-facing management ports that remain permanently open.
- Agentless machine scanning: confirm it is enabled where supported.
- Vulnerability assessment: review the highest-priority recommendations generated through Microsoft Defender Vulnerability Management.
- File Integrity Monitoring: if your organisation has compliance requirements, confirm it has been configured rather than simply enabled.

Tomorrow I will look at Microsoft Defender for Containers, the Defender Plan that protects Kubernetes environments and container registries, and one of the fastest-growing areas of cloud security.

Defender for Servers does far more than onboard Microsoft Defender for Endpoint.

Many of the controls that make the biggest difference to reducing attack surface are optional, and in my experience they are the ones most organisations have never enabled.

Does your organisation use Defender for Servers Plan 1 or Plan 2, and how many of these controls are actually active today?

---

## Microsoft Learn References

- [Overview of Microsoft Defender for Servers](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-servers-overview)
- [Select a Defender for Servers plan](https://learn.microsoft.com/azure/defender-for-cloud/plan-defender-for-servers-select-plan)
- [Just-in-time VM access overview](https://learn.microsoft.com/azure/defender-for-cloud/just-in-time-access-overview)
- [File integrity monitoring in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/file-integrity-monitoring-overview)
- [Agentless machine scanning in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/concept-agentless-data-collection)

---

## Hashtags

#MicrosoftDefender #DefenderForCloud #CloudSecurity #AzureSecurity #MicrosoftSecurity #ZeroTrust #VulnerabilityManagement

---

## Accuracy Notes (for future articles)

- **Agent model nuance (important):** AMA is NOT fully retired from Defender for Servers — FIM specifically still uses MDE + AMA; Log Analytics Agent (MMA) is retired for new deployments. Stuart's framing: "Modern deployments rely primarily on MDE, complemented by agentless. Some capabilities continue to use AMA and Log Analytics workspaces." Do NOT say AMA is deprecated — it still has a role.
- **FIM requires Log Analytics workspace** — change data stored/processed there; enabling FIM in the portal without configuring the workspace won't fully work. Stuart's key distinction: "configured rather than simply enabled" — use this phrasing in future compliance-related articles.
- **Plan 2 list Stuart added:** Sensitive data discovery, OS configuration assessment, Attack path context through Defender CSPM — these were not in the draft. Include in future Plan 2 references.
- **Azure Bastion** flagged as complementary to JIT — Stuart noted "a topic for another day." Potential future article topic.
- **JIT + Bastion framing:** "One limits when management ports can be used; the other removes the need to expose them to the internet in the first place." — strong paired framing, reuse.
- **On-prem without Arc:** "Simply installing MDE on an on-premises server does not provide the full Defender for Servers capability set." — correct; Arc is the recommended path for full capability.
- **Management groups + Azure Policy alignment** flagged as important consideration for non-Azure servers — worth noting in future architecture articles.
- **"Configured rather than simply enabled"** — key practitioner distinction for any feature that requires post-activation configuration (FIM, JIT, etc.).
- Hook used: real-world scenario of test servers accidentally in production, no process to review recommendations.
