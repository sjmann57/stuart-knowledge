# Day 41 — LinkedIn Content Package
**Topic:** CIEM: the product changed, the problem did not
**Category:** Identity / Cloud Security
**Date:** 2026-07-14
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Microsoft Entra Permissions Management was retired on 1 October 2025.
If your organisation had it on the evaluation backlog, that decision has been made for you.
The problem it was designed to solve has not gone away.

**Hook 2:**
Every cloud environment I review has the same pattern.
Access gets granted for a project and never removed. Service principals accumulate permissions nobody reviews. Managed identities hold Contributor rights at subscription level from a deployment three years ago.
This is the problem CIEM solves. The product moved. The gap did not.

**Hook 3:**
Your organisation probably has overprovisioned identities across Azure, AWS, and GCP right now.
You may not be able to see them. That is the problem cloud infrastructure entitlement management was built to address.

---

## LinkedIn Article (Stuart's version — published 2026-07-14)
**Note:** Key changes from draft: retirement date changed to "1 November 2025" (draft said 1 October 2025 per Microsoft Learn docs — Stuart may have verified an extended date; flag for future reference); expanded description of how permissions accumulate ("testing that ends up in production, or from access granted to make it work in a hurry under pressure"); added explicit note that paid Defender CSPM is required; prose refinements throughout; close aphorism adjusted to "after everything else has failed" (not "blocked").

Microsoft Entra Permissions Management was retired on 1 November 2025.
If your organisation had it on the evaluation backlog, that decision has been made for you. If you were already using it, Microsoft ended support at the same time. Microsoft partnered with Delinea to provide an alternative standalone product for customers who still need dedicated cloud infrastructure entitlement management outside the Microsoft security platform.
But the problem CIEM was designed to solve has not gone away. In most multicloud environments I review, it has grown.

What CIEM addresses

The pattern I see across almost every organisation with Azure, AWS, or GCP in scope is the same.

Users and workload identities accumulate permissions over time: from testing that ends up in production, or from access granted to make it work in a hurry under pressure and never removed. Service principals are deployed with Owner-level rights during a migration and left there. Managed identities hold Contributor assignments at the subscription level that have not been reviewed for a considerable amount of time.

In a single-cloud Azure environment, this is difficult enough to manage. Across Azure, AWS, and GCP, the scale of overprovisioned access becomes significant.

The question is not whether overprivileged identities exist in your environment.
They almost certainly do.
The question is whether you can see them.

Where the CIEM capability lives today

Microsoft Defender for Cloud provides native Cloud Infrastructure Entitlement Management (CIEM) capabilities as part of the Defender CSPM plan.

If your organisation already has Defender CSPM enabled, CIEM is available as an extension that can be enabled within the Defender CSPM settings. It does not require a separate standalone CIEM product, although it does require the paid Defender CSPM plan to be enabled for the cloud environments you want to assess.

Defender for Cloud CIEM supports Azure, AWS, and GCP.

It analyses both human and workload identities, including Microsoft Entra users, groups, service principals, managed identities, AWS IAM users, groups and roles, and Google Cloud IAM users, groups and service accounts.

The key outputs are effective permission analysis, identity risk recommendations, and integration with Cloud Security Explorer and attack path analysis.

Recommendations commonly surfaced include:

* Overprovisioned identities should have only the permissions they actually need.
* Permissions assigned to inactive identities should be removed.

The attack path integration is where this becomes valuable from a security perspective.

An overprivileged service principal with access to a storage account containing sensitive data is not simply another recommendation. Where that identity forms part of a viable attack path, Defender for Cloud correlates it with attack path analysis, helping security teams prioritise the issues that genuinely increase organisational risk.

The gap most teams miss: workload identities

Human identities receive some governance attention.

Users have access reviews, Privileged Identity Management for privileged roles, and usually some form of joiner, mover and leaver process.

Workload identities often receive none of that.

Service principals, managed identities, app registrations, and their associated role assignments accumulate over time with little or no lifecycle management. A service principal created for a deployment pipeline three years ago may still have permissions nobody has reviewed. A managed identity assigned the Contributor role at the subscription level during an initial deployment may still have that role long after the original requirement has disappeared.

In almost every multicloud environment reviewed, workload identities are among the largest and least-governed parts of the attack surface.

How to enable CIEM in Defender for Cloud

The CIEM extension is not enabled automatically, even when Defender CSPM is active.

For Azure, open Microsoft Defender for Cloud, go to Environment settings, select the subscription, open the Defender CSPM plan settings, and enable the Permissions Management (CIEM) extension.

Recommendations typically begin appearing within a few hours.

For AWS and GCP, onboard the cloud environment into Microsoft Defender for Cloud first, then enable the CIEM extension within the Defender CSPM settings.

AWS onboarding uses the supplied CloudFormation template.
GCP onboarding supports Cloud Shell or Terraform deployment, depending on your preferred deployment method.

One change from the standalone Entra Permissions Management product is worth noting.

The Permissions Creep Index metric has been deprecated and no longer appears in Defender for Cloud CIEM recommendations.

Where to look today

Open Microsoft Defender for Cloud and navigate to Environment settings.

For each Azure subscription, AWS account, or GCP project that is protected by Defender CSPM, open the plan settings and confirm that Permissions Management (CIEM) is enabled.

If CIEM is already enabled, open Recommendations, filter on Identity and Access, and review the overprovisioned and inactive identity recommendations.

Then review Attack Path Analysis to determine whether any of those identities contribute to a viable attack path.

If CIEM is not enabled and Defender CSPM is already deployed, that is the logical place to start.

The permission nobody is using is rarely harmless.
It is often the permission an attacker uses after everything else has failed.

Does your organisation have a consistent review process for workload identity permissions, or is service principal governance still a gap?

---

## Microsoft Learn References

- [Cloud infrastructure entitlement management (CIEM) in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/permissions-management)
- [Enable cloud infrastructure entitlement management (CIEM)](https://learn.microsoft.com/azure/defender-for-cloud/enable-permissions-management)
- [Microsoft Entra Permissions Management retirement announcement](https://learn.microsoft.com/entra/fundamentals/whats-new-archive#march-2025)
- [What is Microsoft Defender for Cloud CSPM?](https://learn.microsoft.com/azure/defender-for-cloud/concept-cloud-security-posture-management)
- [Attack path analysis in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/how-to-manage-attack-path)

---

## Suggested Image Concept

Microsoft Defender for Cloud Environment settings page showing the Defender CSPM plan with the Permissions Management (CIEM) toggle visible in the settings panel. Demonstrates that CIEM is now a switch within an existing plan, not a separate product to evaluate and procure.

---

## Three Alternative Discussion Questions

1. Does your organisation have a consistent review process for workload identity permissions, or is service principal governance still a gap?
2. Has the retirement of Entra Permissions Management changed your approach to CIEM, or was it never part of your roadmap?
3. In your multicloud environments, which cloud has the worst overprovisioned identity problem — Azure, AWS, or GCP?

---

## Hashtags

#MicrosoftEntra #CIEM #CloudSecurity #MicrosoftDefender #IdentitySecurity
