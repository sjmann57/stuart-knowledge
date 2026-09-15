# Day 34 — LinkedIn Content Package
**Topic:** Microsoft Purview DSPM — the data security check most organisations skip before deploying Copilot
**Category:** Compliance / Security Strategy
**Date:** 2026-07-07
**Format:** Technical article

---

## Three Alternative Hooks (draft uses Hook 2)

**Hook 1:**
Your Copilot licence is live. Your SharePoint permissions were too broad before you turned it on.

**Hook 2 (draft uses this):**
Copilot does not create your data security problem. It reveals the one you already have.

**Hook 3:**
Before you deployed Microsoft 365 Copilot, did you check what it would be able to surface?

---

## LinkedIn Article (Stuart's version — published)
**Note:** Stuart's key changes from draft: classic DSPM retirement date added (September 30, 2026); custom assessment timing corrected to "48 hours, no auto-update" (not 30 days); licensing section made more cautious ("complex and confusing") rather than specific E3/E5 split; shadow AI section softened to "limited" visibility rather than "cannot see"; "grown over the years" (draft: "grown over years").

Copilot does not create your data security problem. It reveals the one you already have.
When I review customer environments ahead of a Microsoft 365 Copilot deployment, the same issue comes up. SharePoint permissions have grown over the years. Documents are shared broadly across the organisation. Sensitivity labels have not been applied. Nobody has audited what Copilot will be able to surface because nobody has audited what users can already access.
Copilot respects the permissions it is given. If a user has access to a document, Copilot can surface it. That is not a product defect. It is the data estate working as configured, which is often not how the organisation intended.
What DSPM actually tells you
Microsoft Purview Data Security Posture Management, DSPM for short, gives you a central view of your data security posture and guided actions to answer four practical questions about your data: what sensitive data you have, where it is stored, who can access it, and how it is protected.
It brings together posture insights, policy coverage, activity signals, investigations, and recommended actions from across Microsoft Purview. Instead of navigating each solution separately, DSPM lets you see data risks, control gaps, and remediation options from a single place.
Navigate there from the Microsoft Purview portal: Solutions > DSPM. If you see "Data Security Posture Management (classic)" or "DSPM for AI (classic)" listed separately, those are previous versions. Use the current DSPM experience for new work.
Data Security Posture Management (classic) and Data Security Posture Management for AI (classic) will be retired on September 30, 2026. All features from the classic solutions, along with your data, are now available in the new DSPM.
The oversharing assessment most organisations have not run.
DSPM automatically runs a weekly default data risk assessment. It scans the top 100 SharePoint sites in your organisation by usage.
What it looks for: items accessible to anyone with a link, items shared externally, and sensitive content without a label applied. The results tell you where your data governance exposure sits before Copilot makes it easier to find.
The limitation worth knowing: 100 sites. If your oversharing risk sits outside the highest-usage sites, the default assessment will not find it.
Custom assessments let you target specific sites, users, or Fabric workspaces. Microsoft states that custom assessment results take at least 48 hours to appear and do not update again. If you need a fresh view, you need to run a new assessment.
I wrote about DLP policies stuck in simulation mode. DSPM makes DLP policy coverage gaps visible from a single place, without having to navigate to the DLP solution separately. It is a useful way to see whether the controls you configured are actually applying to the data at risk.
Licensing and the part people miss
DSPM requires Microsoft 365 E5 or Microsoft Purview Suite. Do not assume it is available just because you have Microsoft 365 E3. What I can add is that Microsoft Licensing for Purview can be complex and confusing, and your own validation is required within your tenant.
Microsoft Purview Audit must also be enabled for DSPM to collect interaction data. For new tenants, audit is usually enabled by default, but it is still worth confirming.
DSPM can help you review AI usage, Microsoft 365 Copilot interactions, and data security risks, but some guided actions rely on other Purview capabilities. Communication Compliance, Insider Risk Management, Data Security Investigations, Network Data Security, and some AI-related controls may have their own licensing and configuration requirements.
Check licensing before assuming the full set of DSPM recommendations, one-click policies, investigations, and remediation actions are available in your tenant.
Shadow AI requires extra steps.
DSPM provides clearer visibility into Microsoft 365 Copilot and Microsoft Copilot interactions from within the Microsoft 365 ecosystem.
For third-party AI sites such as ChatGPT, Google Gemini, DeepSeek, and others supported by Microsoft Purview, extra steps are needed.
Devices must be onboarded to Microsoft Purview. The process uses the same deployment methods and tooling as Microsoft Defender for Endpoint onboarding. The Microsoft Purview browser extension must also be deployed to Windows users.
Without those pieces in place, your visibility into third-party AI usage will be limited. You may know that users are visiting AI sites, but you will not have the same level of insight into what data they are putting into them.
Where to look today
Open the Microsoft Purview portal > Solutions > DSPM.
Check whether the setup tasks are complete. Confirm that Purview Audit is enabled. Look at the default data risk assessment under Discover > Data risk assessments. Note the date of the last results and how many sites were scanned.
Then review the security objective "Prevent data exposure in Microsoft 365 Copilot and Microsoft Copilot interactions" to see your current posture gap.
If Copilot is already deployed in your tenant and you have not reviewed the oversharing assessment, that is the place to start.
Copilot surfaces what users can access. If that list is longer than it should be, the problem is the permissions, not the AI.
Have you run a DSPM data risk assessment before or after deploying Microsoft 365 Copilot, and what did the results show?

---

## Microsoft Learn References

- [Learn about Data Security Posture Management](https://learn.microsoft.com/purview/data-security-posture-management-learn-about)
- [Prevent oversharing with data risk assessments from Data Security Posture Management](https://learn.microsoft.com/purview/data-security-posture-management-oversharing)
- [Learn about Data Security Posture Management for AI (classic)](https://learn.microsoft.com/purview/dspm-for-ai)
- [Microsoft 365 E3 vs E5 DSPM for AI feature comparison](https://learn.microsoft.com/microsoft-365/copilot/microsoft-365-copilot-license-feature-overview#microsoft-365-e3-vs-e5-vs-e7-license-features)
- [Use Microsoft Purview to manage data security and compliance for other AI apps](https://learn.microsoft.com/purview/ai-other-apps)

---

## Suggested Image Concept

Microsoft Purview portal DSPM screen showing the "Prevent oversharing of sensitive data" objective with a high-risk count — ideally showing sites with broad sharing links alongside unlabelled sensitive content. Makes the Copilot risk visible without a word.

---

## Three Alternative Discussion Questions

1. Have you run a DSPM data risk assessment before or after deploying Microsoft 365 Copilot, and what did the results show?
2. Did your organisation audit SharePoint permissions before deploying Copilot, or did the deployment happen first?
3. Which part of the DSPM picture is hardest to fix in practice — unlabelled data, overshared sites, or missing policies?

---

## Hashtags

#MicrosoftPurview #MicrosoftCopilot #DataSecurity #MicrosoftSecurity #MicrosoftCompliance
