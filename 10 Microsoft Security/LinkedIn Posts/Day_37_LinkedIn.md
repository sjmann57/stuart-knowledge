# Day 37 — LinkedIn Content Package
**Topic:** Microsoft Purview Sensitivity Labels — the foundation the rest of Purview depends on
**Category:** Compliance / Information Protection
**Date:** 2026-07-09
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
I spent the last week writing about DLP, DSPM, Insider Risk Management, and Communication Compliance.
All four of those solutions do less useful work when your data does not have a sensitivity label applied.

**Hook 2:**
DSPM flagged unlabelled content as your biggest data risk. DLP enforces conditions based on label state. IRM uses label context. Communication Compliance scans for sensitive information types that labelling would already have identified.
The missing piece is the label itself.

**Hook 3:**
Your Microsoft 365 tenant has a sensitivity label taxonomy. In most organisations I review, the content does not match it.

---

## LinkedIn Article (Stuart's version — published 2026-07-10)
**Note:** Key changes from draft: Second paragraph softened from negative framing ("do less useful work") to positive ("become significantly more effective"); added detailed paragraph explaining how each Purview solution specifically uses labels (DLP conditions, DSPM unlabelled flag, IRM signals, CC classifiers); Copilot section rewritten to be more precise and grounded ("honours Microsoft Purview Information Protection permissions... same permissions that apply when the user opens the document themselves"); removed the July 2026 specific Copilot rollout claim from web search (replaced with cautious forward-looking statement); container/Teams/Groups label section removed (kept article tighter); service-side scope expanded to include "Exchange Online mailboxes" explicitly; discussion question split into two punchy lines.

I spent the last week writing about DLP, DSPM, Insider Risk Management, and Communication Compliance.
All four of those solutions become significantly more effective when your data has sensitivity labels applied consistently.

Without a well-designed label taxonomy that is actually applied to your data, Microsoft Purview has one hand tied behind its back. DLP conditions target label state. DSPM highlights sensitive content that is unlabelled or insufficiently protected as part of your overall data security posture. Insider Risk Management can use sensitivity labels as one of several contextual signals when evaluating risky activity. Communication Compliance uses many of the same sensitive information types and classifiers that can also be used by auto-labelling.

The thread running through every Purview solution this week is sensitivity labels. And in most tenants I review, the label taxonomy exists, but the label coverage does not.

What a sensitivity label actually does

A sensitivity label from Microsoft Purview Information Protection becomes metadata stored with a document or email. Depending on how the label is configured, it can also apply encryption, usage rights, watermarks, headers, and footers that travel with supported content across Microsoft 365 services and supported applications.

It does more than classify. A label can apply encryption with defined user permissions, add watermarks, headers, and footers, configure privacy and external sharing settings for Microsoft 365 Groups, Microsoft Teams and SharePoint team sites, and Microsoft 365 Copilot respects protection when accessing content.

Specifically on Copilot, Microsoft 365 Copilot honours Microsoft Purview Information Protection permissions. If a user cannot access or decrypt protected content due to permissions enforced by a sensitivity label, Copilot cannot use that content to generate a response. Copilot respects the same permissions that apply when the user opens the document themselves.

Microsoft continues to expand how Microsoft 365 Copilot works alongside Microsoft Purview Information Protection and sensitivity labels as new capabilities are introduced.

Creating labels and publishing them are two different things

The most common setup gap I find is a complete label taxonomy in the Microsoft Purview portal with no publishing policy.

Labels are created in Information Protection. They are not available to users until a label policy publishes them to the required users or groups. Creating a label and publishing a label are two separate actions.

After a publishing policy is created or changed, allow up to 24 hours for labels to appear in users' Microsoft 365 apps.

The licensing split

Manual sensitivity labelling is available with Microsoft 365 E3 and most commercial Microsoft 365 plans. Users see the sensitivity bar in supported Office applications and can apply labels themselves.

Automatic labelling requires Microsoft 365 E5 or an appropriate Microsoft Purview Information Protection and Governance add-on licence.

Auto-labelling has two forms.

Client-side auto-labelling runs inside supported Microsoft 365 apps while users work. It can recommend a label or apply one automatically, depending on how the policy is configured.

Service-side auto-labelling uses policies in Microsoft Purview to scan content already stored in SharePoint Online, OneDrive, and Exchange Online mailboxes. It applies labels to existing content without user interaction, making it one of the most effective ways to address large volumes of historical unlabelled data.

Service-side auto-labelling policies also support simulation mode. Like DLP simulation mode, they show what would happen without making changes. Simulation is the right place to start. Data left in simulation mode remains unlabelled.

Default and mandatory labelling

Within your label policy, two settings have a significant impact on user behaviour.

A default label is automatically applied to new unlabelled documents and emails. Users can change it if appropriate, but they start with a sensible classification instead of no classification at all.

Mandatory labelling requires users to apply a sensitivity label before saving a document or sending an email.

Without a sensible default label, mandatory labelling often results in users simply selecting the first available label to continue working.

Used together, a sensible default with mandatory labelling as a backstop produces much better coverage than either setting on its own.

Where to look today

Open the Microsoft Purview portal and go to Information Protection > Labels.

Count how many labels exist.

Then open Label policies and confirm that a publishing policy covers the users, groups and locations you expect.

Next, open Auto-labelling policies and check whether any policies remain in simulation mode.

If they have been sitting there for weeks or months, it is likely the same backlog of unlabelled sensitive content that DSPM is highlighting as part of your data security posture.

A label taxonomy is not a data protection programme.
The protection comes from the labels that are actually applied to your data.

Have you moved your auto-labelling policies from simulation to enforcement?
If not, what has stopped that final step?

---

## Microsoft Learn References

- [Learn about sensitivity labels](https://learn.microsoft.com/purview/sensitivity-labels)
- [Get started with sensitivity labels](https://learn.microsoft.com/purview/get-started-with-sensitivity-labels)
- [Automatically apply a sensitivity label to Microsoft 365 data](https://learn.microsoft.com/purview/apply-sensitivity-label-automatically)
- [Default sensitivity labels and policies to protect your data](https://learn.microsoft.com/purview/default-sensitivity-labels-policies)
- [Microsoft Purview service description — sensitivity labelling licensing](https://learn.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description#microsoft-purview-information-protection-sensitivity-labeling)

---

## Suggested Image Concept

Microsoft Purview Information Protection page showing the label list with a hierarchy of Personal / Public / General / Confidential labels visible, alongside the Label policies page showing a publishing policy with its scope. Side by side, it illustrates the create-then-publish workflow in practice.

---

## Three Alternative Discussion Questions

1. Have you moved your auto-labelling policies from simulation to enforcement, and what stopped that from happening sooner?
2. What is the biggest practical barrier to achieving meaningful sensitivity label coverage in your organisation — user behaviour, policy configuration, or licensing?
3. Has your organisation used sensitivity labels to restrict Microsoft 365 Copilot access to content, or is that still on the roadmap?

---

## Hashtags

#MicrosoftPurview #SensitivityLabels #InformationProtection #MicrosoftSecurity #MicrosoftCompliance
