# Day 60 — LinkedIn Content Package
**Topic:** Microsoft Defender for Cloud — CSPM and CWPP architecture
**Category:** Cloud Security / Zero Trust
**Week theme:** Microsoft Defender for Cloud (Days 60–63)
**Date:** 2026-08-04 (Monday)
**Format:** Technical article — Week 9 opener

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Your Azure subscription already has a security score.
Most organisations have never looked at it properly.

**Hook 2:**
Cloud security tends to get complicated fast.
Which tool covers which workload. Which alert matters. Which score reflects your actual posture.
Microsoft Defender for Cloud is designed to answer all of those questions from one place.

**Hook 3:**
Most organisations I work with have Microsoft Defender for Cloud enabled.
Far fewer have connected it to the workloads it is designed to protect.
The gap between enabled and configured is where most cloud security risk lives.

---

## LinkedIn Article (published — 2026-08-04)

Microsoft Defender for Cloud: posture management, workload protection, and why most organisations are only using half of it

Your Azure subscription already has a security score.

Most organisations have never looked at it properly, or not looked for months.

This week I am covering Microsoft Defender for Cloud.

Today I want to explain the architecture because it is frequently misunderstood.

Most organisations I speak with have enabled Defender for Cloud but treat it as a single product when it is actually multiple capabilities working together.

What is Microsoft Defender for Cloud?

Microsoft Defender for Cloud is Microsoft's Cloud-Native Application Protection Platform (CNAPP).

It is administered primarily through the Azure portal, with an increasing number of cloud security experiences also available through the Microsoft Defender portal.

Microsoft positions Defender for Cloud around three core capabilities:

- Foundational Cloud Security Posture Management (Foundational CSPM)
- Defender CSPM
- Defender Plans, which provide Cloud Workload Protection Platform (CWPP) capabilities

Understanding the distinction between posture management and workload protection is the foundation for understanding the rest of the platform.

Cloud Security Posture Management

Cloud Security Posture Management (CSPM) focuses on configuration.

Defender for Cloud continuously assesses cloud resources against the Microsoft Cloud Security Benchmark, raising recommendations whenever resources do not align with Microsoft's recommended security controls.

Each recommendation explains what the issue is, why it matters and how to remediate it.

Those recommendations contribute to your Secure Score, which provides an overall measure of your cloud security posture.

As recommendations are remediated, your Secure Score improves.

The Azure portal displays the traditional Secure Score.

The Microsoft Defender portal also provides Cloud Secure Score, which introduces additional cloud-focused risk context.

Although related, the two scores are calculated differently, so it is important to understand which one you are viewing.

Remember, Secure Score does not always mean secure or compliant; you must understand your workloads and think beyond Secure Score.

Foundational CSPM

Foundational CSPM is included with Defender for Cloud.

It provides Secure Score, security recommendations and foundational posture assessment across your cloud resources.

When AWS and Google Cloud Platform environments are connected, Defender for Cloud can also assess posture across those environments.

Defender CSPM

The paid Defender CSPM plan extends those capabilities considerably.

Two capabilities stand out.

Attack Path Analysis builds a graph of your cloud environment and identifies realistic attack paths between internet-exposed resources and sensitive assets.

Rather than presenting hundreds of unrelated recommendations, it highlights combinations of weaknesses that an attacker could realistically chain together.

Cloud Security Explorer allows security teams to query that same graph.

Questions such as:

"Which internet-facing virtual machines have known vulnerabilities and can access sensitive storage accounts?"

become straightforward to answer.

That context changes how organisations prioritise remediation.

Cloud Workload Protection

Where CSPM focuses on configuration, Cloud Workload Protection Platform (CWPP) focuses on active threats.

Defender for Cloud provides workload-specific Defender Plans, each protecting a different resource type.

These include:

- Defender for Servers
- Defender for Containers
- Defender for Storage
- Defender for Databases
- Defender for App Service
- Defender for Key Vault
- Defender for APIs
- and several others.

Each Defender Plan provides workload-specific threat detection, alerting and security recommendations.

Defender for Servers protects Windows and Linux servers running in Azure, AWS, Google Cloud Platform and on-premises environments.

Defender for Containers protects containerised workloads across supported Kubernetes environments and container registries throughout the application lifecycle.

Defender for Storage detects malware, suspicious activity and other threats affecting Azure Storage.

Defender for Databases protects Azure SQL, Azure Cosmos DB and supported open-source database platforms.

When threats are detected, Defender for Cloud raises security alerts.

Those alerts integrate with Microsoft Defender XDR and can also be streamed into Microsoft Sentinel for investigation, correlation and response.

One view across multiple clouds

One of the most valuable capabilities of Defender for Cloud is its multicloud architecture.

Azure, AWS and Google Cloud Platform can all be onboarded into a single Defender for Cloud environment.

Once connected, security posture, recommendations and workload alerts are presented together instead of requiring separate security tools and dashboards for each cloud provider.

For organisations operating across multiple cloud platforms, this provides a consistent security view regardless of where workloads are running.

Where to look today

Open Microsoft Defender for Cloud in either the Azure portal or the Microsoft Defender portal.

Start by reviewing your Secure Score (Cloud Security > Secure posture) and identify which recommendations contribute most to improving it.

Then open Recommendations and focus on the actions that will deliver the greatest reduction in risk.

Finally, review Environment settings (Management) and confirm which Defender Plans are enabled for each subscription.

It is common to find subscriptions using Foundational CSPM while workload protection plans remain disabled.

That is often the biggest security gap.

If you have never reviewed your Secure Score, start there.

It tells you where the weaknesses are.

The recommendations tell you how to improve them.

This week I am covering the Defender Plans in more detail.

Tomorrow I will focus on Defender for Servers, the most widely deployed plan and one that usually delivers the quickest security improvements for organisations running virtual machines.

Does your organisation use Microsoft Defender for Cloud today?

And if someone asked you for your current Secure Score, would you know the answer?

---

## Microsoft Learn References

- [What is Microsoft Defender for Cloud?](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-cloud-introduction)
- [What is Cloud Security Posture Management (CSPM)?](https://learn.microsoft.com/azure/defender-for-cloud/concept-cloud-security-posture-management)
- [Secure score in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/secure-score-security-controls)
- [Security explorer and attack paths in Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/concept-attack-path)
- [Plan multicloud security with Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/plan-multicloud-security-get-started)

---

## Suggested Image Concept

The Defender for Cloud Overview dashboard in the Microsoft Defender portal showing the Secure Score tile, active alerts summary, and the Workload protections coverage map — illustrating the single-pane-of-glass view across Azure, AWS, and GCP.

---

## Hashtags

#MicrosoftDefender #DefenderForCloud #CloudSecurity #CSPM #ZeroTrust #MicrosoftSecurity #AzureSecurity

---

## Accuracy Notes (for future articles)

- CNAPP is current official top-level positioning — three components: Foundational CSPM, Defender CSPM, Defender Plans (CWPP). Article uses this exact three-part structure (not the draft's CSPM/DevSecOps/CWPP split).
- "Administered primarily through the Azure portal" — Stuart's framing. Defender portal coverage is growing but Azure portal remains primary admin surface.
- Secure Score caveat added by Stuart: "Secure Score does not always mean secure or compliant; you must understand your workloads and think beyond Secure Score." — key practitioner addition, use in future articles where Secure Score is discussed.
- Two Secure Score models: traditional (Azure portal) vs Cloud Secure Score (Defender portal, additional risk context) — "calculated differently" framing used; do not conflate the two.
- Foundational CSPM: Stuart used "included with Defender for Cloud" not "free" — more durable framing given the Oct 2026 opt-in model change for new subscriptions.
- Defender for Containers framing: "containerised workloads across supported Kubernetes environments and container registries throughout the application lifecycle" — use this phrasing in Day 62.
- Integration: Defender for Cloud alerts integrate with Defender XDR AND can stream to Sentinel — both named.
- Key practitioner insight for the series: "common to find subscriptions using Foundational CSPM while workload protection plans remain disabled — that is often the biggest security gap."
- Portal navigation: Cloud Security > Secure posture (Secure Score); Recommendations; Environment settings (Management) for plan coverage.
- Week 9 preview: Servers (Day 61 tomorrow), Containers (Day 62), DevOps/DevSecOps (Day 63).
