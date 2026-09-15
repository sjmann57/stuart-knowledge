# Day 47 — LinkedIn Content Package
**Topic:** Microsoft Defender for Cloud Apps — the cloud app security layer most organisations haven't switched on
**Category:** SecOps / Cloud Security
**Date:** 2026-07-22
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Someone on your sales team uploaded your latest pricing proposal to their personal Dropbox before flying to a customer meeting. The document contained margin information not shared outside the organisation.
Your security team had no visibility. There was no alert. It happened on a personal laptop via a browser.
This is not an edge case.

**Hook 2:**
Your organisation has approved a list of cloud applications. Microsoft 365, Salesforce, ServiceNow, maybe a few others.
Your users are accessing significantly more than that. The question is how many, which ones, and what data is going into them.

**Hook 3:**
Three years ago a developer approved a third-party app integration. It requested read access to all organisational email to enable a reporting feature.
That developer left eighteen months ago. The app is still running. Nobody has reviewed its permissions since.

---

## LinkedIn Article (draft — 2026-07-22)

Someone on your sales team uploaded your latest pricing proposal to their personal Dropbox before flying to a customer meeting. The document contained margin information not shared outside the organisation.

Your security team had no visibility. There was no alert. It happened on a personal laptop, in a browser, on a public Wi-Fi network.

This is not an edge case.

In every organisation I have reviewed with a substantial remote or hybrid workforce, users are regularly moving data through cloud applications that the security team has no visibility of. Microsoft Defender for Cloud Apps is the control that addresses this. And in most Microsoft 365 E5 organisations, it is already licensed and largely unconfigured.

What Microsoft Defender for Cloud Apps does

Microsoft Defender for Cloud Apps delivers protection across four areas: cloud access security broker capabilities including shadow IT discovery, SaaS security posture management, threat protection as part of the Defender XDR stack, and app-to-app protection covering OAuth-enabled applications.

This article focuses on the two capabilities most organisations have neither enabled nor reviewed: Cloud Discovery and Conditional Access App Control.

Cloud Discovery: what your users are actually using

Cloud Discovery analyses network traffic against a catalogue of over 31,000 cloud applications. Each app is assessed against more than 90 risk factors covering security practices, compliance certifications, data protection policies, and legal exposure. The output is a risk score and a visibility report showing which apps are in use, how much data is flowing through them, and which users are accessing them.

The most straightforward way to enable Cloud Discovery for an organisation already using Microsoft Defender for Endpoint is through the native integration. Defender for Endpoint forwards cloud app networking activity to Defender for Cloud Apps automatically, providing continuous visibility across managed devices without any additional agent deployment or log collector configuration.

For devices outside MDE management, or where you want visibility across network traffic rather than per-device, Defender for Cloud Apps supports log upload from a wide range of firewall and proxy vendors, and integration with secure web gateways including Zscaler.

What organisations typically find when they first enable Cloud Discovery is that the number of cloud applications in active use is significantly higher than IT expects. The sanctioned list covers a subset of what users are actually doing. The rest is shadow IT.

Discovery alone changes the conversation, because it gives you specific data to work with rather than assumptions.

Conditional Access App Control

Knowing which apps are in use is the starting point. Controlling what happens within those sessions is the next step.

Conditional Access App Control routes sessions through Defender for Cloud Apps as a proxy, after Microsoft Entra ID has evaluated and passed the relevant Conditional Access policies. This requires Microsoft Entra ID P1 and the relevant Conditional Access policy to be configured to route the session.

Two types of policy are available.

Access policies control whether a user can access an application at all, based on user identity, device compliance state, location, and risk. They allow or block access before the session begins.

Session policies apply controls within an active session. A user on an unmanaged device can be permitted to access Salesforce, but blocked from downloading any record. A user uploading a file classified as confidential by a Microsoft Purview sensitivity label can be blocked or prompted to justify the action. Documents opened in browser sessions can be watermarked. Pasting sensitive content from a monitored application can be blocked.

The practical value is the ability to maintain productivity for users on unmanaged devices, personal laptops, or bring-your-own-device scenarios, while preventing data from leaving in a form you cannot control.

The alternative is to block access entirely for unmanaged devices. In many organisations that is the default position because Conditional Access App Control has not been deployed. The result is either a blanket block that generates friction and workarounds, or no control at all.

SaaS Security Posture Management

Defender for Cloud Apps connects to sanctioned applications and surfaces misconfigurations against industry standards including CIS benchmarks and the security recommendations of each application provider.

These findings feed directly into Microsoft Secure Score, giving you a cross-application view of your SaaS security posture alongside your Entra, Defender, and Purview configurations.

For organisations with a significant SaaS footprint, this is often where the most immediate security improvements are found.

App governance and OAuth permissions

The fourth capability worth examining is app governance, which addresses OAuth-enabled applications that have been granted permissions to access Microsoft 365 data on behalf of users.

Third-party integrations accumulate over time. A reporting tool approved by a developer several years ago may still hold read access to all organisational email. A productivity add-in a user installed may have been granted write access to files across SharePoint. Neither may have been reviewed since original approval.

App governance surfaces these permissions, flags unused applications and expired credentials, and allows you to revoke access where it is no longer justified.

Where to look today

Open the Microsoft Defender portal at security.microsoft.com and navigate to:

Cloud apps > Cloud discovery

If no continuous report is configured and your organisation has Defender for Endpoint deployed, enabling the MDE integration is the starting point. You will begin seeing cloud app activity across managed devices within hours.

Review the discovered apps by risk score. Look at the highest-volume unsanctioned apps and assess what data may be flowing through them.

Then navigate to:

Cloud apps > App governance

Review connected apps and their permission scope. Any application with broad permissions, low usage, or no current owner warrants a review.

If Conditional Access App Control is not configured, the starting point is an Entra Conditional Access policy scoped to a specific high-value application, with session controls routing through Defender for Cloud Apps. Salesforce, ServiceNow, and other supported apps can be deployed in monitor-only mode first to understand the session activity before enforcement is applied.

Your organisation almost certainly has users accessing cloud applications your security team has not approved, assessed, or reviewed.
The question is whether you have the visibility to know which ones, and the controls to manage what happens in those sessions.

How many cloud applications do you think your users are actively accessing, and what would your Cloud Discovery report show if you enabled it today?

---

## Microsoft Learn References

- [Microsoft Defender for Cloud Apps overview](https://learn.microsoft.com/en-us/defender-cloud-apps/what-is-defender-for-cloud-apps)
- [Cloud app discovery overview](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery)
- [Discover and manage shadow IT](https://learn.microsoft.com/en-us/defender-cloud-apps/tutorial-shadow-it)
- [Cloud app catalog and risk scores](https://learn.microsoft.com/en-us/defender-cloud-apps/risk-score)
- [Create session policies](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad)
- [Create access policies](https://learn.microsoft.com/en-us/defender-cloud-apps/access-policy-aad)
- [App governance in Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-app-governance)
- [Microsoft Defender for Endpoint integration with Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-cloud-app-security-integration)

---

## Suggested Image Concept

Microsoft Defender portal Cloud Discovery dashboard showing the discovered apps list, with a mix of sanctioned and unsanctioned apps ranked by traffic volume and risk score — illustrating the scale of shadow IT visibility the feature provides compared to the organisation's approved app list.

---

## Three Alternative Discussion Questions

1. How many cloud applications do you think your users are actively accessing, and what would your Cloud Discovery report show if you enabled it today?
2. Has your organisation deployed Conditional Access App Control for any applications, and if so, did the session data change how you thought about unmanaged device access?
3. When did anyone last review which third-party OAuth applications have access to your Microsoft 365 tenant, and do you know which ones still have permissions from employees who have since left?

---

## Hashtags

#MicrosoftDefender #CloudSecurity #DefenderForCloudApps #ShadowIT #MicrosoftSecurity
