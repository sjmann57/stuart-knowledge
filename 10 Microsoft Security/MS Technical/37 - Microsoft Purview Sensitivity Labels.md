---
title: "Microsoft Purview Sensitivity Labels"
product: "Microsoft Purview"
day: 37
published: 2026-07-09
source: https://www.linkedin.com/posts/stuartmann_microsoftpurview-sensitivitylabels-informationprotection-activity-7481362334150586368-HT5S
impressions: 2212
tags:
  - purview
  - sensitivity-labels
  - information-protection
  - classification
  - encryption
  - top-performer
---

# Microsoft Purview Sensitivity Labels

## Summary
Sensitivity labels classify and protect content (markings, encryption, access control) and the label travels with the data. A strong foundation for much of Purview — though, importantly, not a hard prerequisite for every capability. (High-reach article: 2,199.)

## Key facts
- Labels apply visual markings, encryption and usage rights that persist with the file/email.
- Auto-labelling (client and service-side) classifies at scale using SITs/trainable classifiers.
- Labels drive DLP conditions and are honoured by Copilot/AI apps (EXTRACT usage right needed for labelled+encrypted content).
- Label priority determines the effective label on inherited/combined content.

## Licensing & prerequisites
- Microsoft 365 E5 / E5 Compliance (or Information Protection & Governance).

## Practitioner notes / gotchas
- Nuance: labels are extremely useful but not the foundation of every Purview capability (e.g. DSPM doesn't require a labelling schema).
- Enable labels for SharePoint/OneDrive so encrypted files are processable by services and Copilot.

## Microsoft Learn references
- [Learn about sensitivity labels](https://learn.microsoft.com/purview/sensitivity-labels)
- [Get started with sensitivity labels](https://learn.microsoft.com/purview/get-started-with-sensitivity-labels)
- [Automatically apply a sensitivity label to Microsoft 365 data](https://learn.microsoft.com/purview/apply-sensitivity-label-automatically)
- [Default sensitivity labels and policies to protect your data](https://learn.microsoft.com/purview/default-sensitivity-labels-policies)
- [Microsoft Purview service description — sensitivity labelling licensing](https://learn.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description#microsoft-purview-information-protection-sensitivity-labeling)

## Related
- [[33 - Microsoft Purview DLP — simulation mode that never gets turned on]]
- [[34 - Microsoft Purview DSPM (Data Security Posture Management)]]
- [[69 - Microsoft Purview & AI agent data security]]

## Source
LinkedIn (Day 37): https://www.linkedin.com/posts/stuartmann_microsoftpurview-sensitivitylabels-informationprotection-activity-7481362334150586368-HT5S
