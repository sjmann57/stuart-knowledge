# Day 83 — LinkedIn Content Package
**Topic:** Microsoft Purview becomes the data-security hub — DLP consolidation and protecting AI prompts
**Category:** Data Security / Microsoft Purview / AI Security
**Week theme:** What's new in Microsoft Security (Days 81–84)
**Date:** 2026-08-26 (Wednesday)
**Format:** Technical article — Week 12 Day 3
**LinkedIn URL:** pending

---

## LinkedIn Article (published — 2026-08-26)

Microsoft Purview becomes the data-security hub: DLP consolidation and protecting AI prompts.

So far this week I have covered Sentinel and Entra.

Today it is Microsoft Purview, where two changes matter.

File-based data protection is consolidating into Purview, and DLP is being extended to do something increasingly necessary:

Protect what your users type into AI.

This is a very relevant topic for me today, as I have been looking at these controls and the questions they raise for clients I work with. The complexity increases as the technology users are driving has greater reach within organisations.

Purview as the data-security hub

Microsoft positions Purview as a set of solutions to govern, protect and manage data, including data being used with AI.

That matters because data protection in the Microsoft stack has historically had more than one home.

You could configure DLP controls in Microsoft Purview.

You could also configure file policies in Microsoft Defender for Cloud Apps.

Two places.

Overlapping capabilities.

And a reasonable amount of confusion about which one you should use for what.

Microsoft is now changing that model.

File policies in Defender for Cloud Apps retire on 6 January 2027.

Microsoft's guidance is to recreate those policies using Microsoft Purview DLP or auto-labelling policies before that date.

This doesn't mean Defender for Cloud Apps is disappearing.

It continues to provide capabilities including SaaS app discovery, posture management and threat detection.

But Microsoft is explicitly moving file-based data protection to Purview.

If you have file policies running in Defender for Cloud Apps today, that is a migration to plan now.

Not in January 2027.

The move from Defender for Cloud Apps to Purview is a good change, but I now have to rewire some more of my thinking when designing solutions, as the landscape changes.

DLP is no longer just about email and SharePoint

Purview DLP already protects data across locations including Exchange, SharePoint, OneDrive, Teams and endpoints.

But the interesting change for me is where Microsoft is extending that protection.

Because data doesn't only leave an organisation through an email attachment anymore.

It can leave through a browser.

An application.

An API.

Or increasingly:

An AI prompt.

Microsoft is extending Purview into those paths through several different controls.

Browser Data Security

Browser Data Security, using Microsoft Edge for Business, extends Purview DLP into browser interactions with cloud applications.

This allows Purview to inspect sensitive information being shared to and from cloud apps through Edge for Business and apply policy controls.

And importantly:

You don't need to onboard the device into Microsoft Purview for this Edge for Business integration.

That creates another way of protecting sensitive information being entered directly into a browser session.

There is a licensing distinction worth understanding.

Some scenarios involving Microsoft Entra-registered managed applications are covered by Microsoft 365 E5 or equivalent licensing.

Protecting data shared from a managed device to an unmanaged application in Edge for Business is a pay-as-you-go capability. Pay-as-you-go capabilities are increasing across the Microsoft Purview landscape.

So don't assume that because you have E5, every Browser Data Security scenario is automatically covered.

Network Data Security

Then there is Microsoft Purview Network Data Security.

This extends visibility and data inspection beyond Microsoft Edge.

Network Data Security can inspect supported network traffic to websites, cloud applications and generative AI services.

That means Purview can start seeing data moving through paths including non-Microsoft browsers, applications and APIs rather than relying entirely on endpoint or browser controls.

Microsoft currently supports HTTP and HTTPS inspection in preview for Network Data Security.

The licensing here also needs checking carefully.

For example, Network Data Security with Microsoft Entra Global Secure Access requires supported licence combinations that include Microsoft 365 E7, or Purview E5 or equivalent together with Entra Internet Access or equivalent.

Integrations with supported non-Microsoft SASE and secure-browser solutions require Purview E5 or equivalent and Purview pay-as-you-go billing.

This is not simply another feature that everybody with E5 automatically gets.

Protecting what users put into AI

This is the part I would pay closest attention to.

Microsoft Purview DLP now provides controls specifically for interactions with Microsoft 365 Copilot and Microsoft 365 Copilot Chat.

You can create DLP policies to do several things.

Block sensitive information in prompts

Purview can detect sensitive information types in prompts.

That includes Microsoft-provided sensitive information types such as credit card numbers and passport numbers, as well as custom sensitive information types you create.

When configured to enforce the block action, Copilot doesn't return a response to a prompt containing the sensitive information.

It also prevents that sensitive prompt data from being used for internal or external web searches.

There is an important configuration point here.

Microsoft provides a default policy called:

Default DLP policy - Protect sensitive M365 Copilot interactions

But it initially runs in simulation mode.

That means it logs the event rather than blocking it.

If you actually want to prevent Copilot from processing the prompt, you need to move the policy into enforcement mode.

Having the policy visible doesn't necessarily mean you are protected.

Block sensitive data from web grounding

Purview DLP can also stop Microsoft 365 Copilot and Copilot Chat from using external web search when a prompt contains sensitive information.

Instead, Copilot can continue generating a response using permitted internal Microsoft 365 data.

The sensitive information isn't sent to external web services for grounding.

That is a useful distinction.

You don't necessarily have to block the entire Copilot interaction.

You can stop the sensitive information leaving the Microsoft 365 data boundary through external web grounding.

Block labelled files and emails

Purview DLP can also restrict Microsoft 365 Copilot and Copilot Chat from processing files and emails carrying specified sensitivity labels.

This gives you another control over what organisational data Copilot can use as grounding information.

Again, this comes back to classification.

If your organisation doesn't know which information is sensitive, it becomes considerably harder to tell AI what it should and shouldn't use.

Block external email from grounding

Another interesting control is currently in preview.

You can prevent Microsoft 365 Copilot and Copilot Chat from using emails received from external domains as grounding data.

Copilot excludes those external emails while continuing to use permitted internal Microsoft 365 data.

Microsoft specifically calls out reducing prompt injection and untrusted data influence as reasons for this control.

This one is worth watching.

An attacker doesn't necessarily need to compromise the AI itself.

They may be able to influence what the AI does by manipulating the information it consumes.

What about ChatGPT, Gemini and other AI tools?

Microsoft 365 Copilot isn't the only concern.

Your users can open a browser and use:

ChatGPT.

Google Gemini.

DeepSeek.

Consumer Microsoft Copilot.

And then paste corporate information straight into the prompt.

Purview provides several ways to address this.

On devices onboarded into Microsoft Purview, Endpoint DLP can warn or block users from sharing sensitive information with third-party generative AI sites.

Microsoft gives the example of preventing a user from pasting credit card numbers into ChatGPT, or presenting a warning that the user can override depending on your policy configuration.

Purview can also use Browser Data Security in Edge to control sensitive information entered into AI prompts.

Microsoft specifically documents controls for consumer AI applications including:

* ChatGPT
* Microsoft Copilot consumer
* DeepSeek
* Google Gemini

This addresses a gap that has quietly widened over the last few years.

Sensitive data leaving through a browser tab rather than through corporate email.

DSPM is the front door

This is another area where Microsoft has made a significant change.

The current strategic experience is Microsoft Purview Data Security Posture Management (DSPM).

Microsoft previously had DSPM for AI and Data Security Posture Management as separate experiences.

Those versions now remain available as:

DSPM for AI (classic)

and

Data Security Posture Management (classic).

Microsoft says most new functionality will be added to the current DSPM experience.

The new DSPM brings together data-security insights and guided workflows across Microsoft Purview.

It gives you areas including:

* Posture
* Security objectives
* AI observability
* Asset explorer
* Reports
* Setup tasks

AI observability gives you visibility into AI apps and agents being used across the organisation, including sensitive interactions and risk information.

Security objectives provide remediation plans that can include recommended actions and one-click policies.

For me, if you are starting to understand your AI data-security posture, this is where I would begin.

Rather than immediately creating individual DLP policies, first understand:

What AI is actually being used?

Where is sensitive information going?

Which applications and agents are interacting with it?

Where are the biggest risks?

Then build the controls around what the data tells you.

A few honest notes

First, licensing.

This isn't one simple licence question.

Some Purview capabilities are included in Microsoft 365 E5 or equivalent licensing.

Some browser and network scenarios require pay-as-you-go.

Network Data Security has additional licence requirements depending on how you integrate it.

And individual AI platforms can have their own requirements.

Check the capability and use case you are actually deploying before assuming you have coverage.

Second, preview.

Not everything described here has the same release status.

For example, blocking external email from Copilot grounding is currently preview, and Network Data Security HTTP/HTTPS classification is also documented as preview.

Confirm what has reached your tenant.

Test it.

Then decide where you are comfortable depending on its operational use.

Third, and probably most important from an architecture point of view:

None of this removes the need for the foundations.

DLP for AI relies heavily on controls such as sensitive information types and sensitivity labels.

If your classification is weak, your ability to apply precise AI data controls will be weak too.

Microsoft's own Copilot security guidance starts with identifying sensitive data and applying appropriate sensitivity labels before layering DLP controls over Copilot interactions.

The AI capabilities aren't a shortcut past the data-classification work.

For many organisations, they are another reason to finally do it properly.

The thread through the week

Sentinel is becoming a broader security platform.

Entra is closing identity gaps.

And Purview is becoming Microsoft's central data-security experience, extending protection into browsers, networks and AI interactions.

The common driver behind all three is the same.

The way organisations use technology is changing.

AI is changing where data moves, who or what accesses it, and how quickly it can leave the controls we traditionally relied on.

Microsoft is moving its security controls to follow that change.

But the technology only works if the foundations underneath it work too.

Know your data.

Classify it.

Protect it.

Then control where it can go.

Do you have visibility today into what your users are pasting into AI tools, or is that still a blind spot?

---

## Microsoft Learn References

- [Learn about Microsoft Purview](https://learn.microsoft.com/purview/purview)
- [Learn about data loss prevention](https://learn.microsoft.com/purview/dlp-learn-about-dlp)
- [Learn about using Microsoft Purview DLP to protect interactions with Microsoft 365 Copilot and Copilot Chat](https://learn.microsoft.com/purview/dlp-microsoft365-copilot-location-learn-about)
- [Migrate file policies to Microsoft Purview (Defender for Cloud Apps)](https://learn.microsoft.com/defender-cloud-apps/migrate-file-policies-to-purview)
- [Microsoft Purview data security and compliance for AI](https://learn.microsoft.com/purview/ai-microsoft-purview)

---

## Hashtags

#MicrosoftPurview #DataSecurity #DLP #AISecurity #DataLossPrevention #MicrosoftSecurity #DSPM #Cybersecurity

---

## Accuracy Notes

- **File policies in Defender for Cloud Apps retire 6 January 2027** — confirmed. Guidance: migrate to Purview DLP or auto-labelling. DfCA retains SaaS security / app governance / threat protection; DLP consolidates into Purview.
- **Purview positioning:** "unified... govern, protect, and manage data in the era of AI, wherever your data lives" — verbatim from Learn about Microsoft Purview.
- **DLP locations (traditional):** Exchange, SharePoint, OneDrive, Teams, Office apps, Windows/macOS endpoints, on-prem file shares, Fabric/Power BI, M365 Copilot (preview), managed cloud apps — confirmed.
- **Browser Data Security (Edge for Business):** real-time inspection of typed/pasted content; no device onboarding needed for the Edge integration — confirmed. Pay-as-you-go for managed-device-to-unmanaged-app scenario.
- **Network Data Security:** non-Microsoft browsers/apps/APIs, network-level; 34,000+ cloud apps via DfCA catalog — confirmed. Pay-as-you-go.
- **DLP for M365 Copilot capabilities (all confirmed):** block processing sensitive prompts (SITs); block external web search grounding when SIT present; block processing labelled files/emails; block external email grounding (preview, anti-prompt-injection). "Block SITs in prompts" is PREVIEW, rolling out to M365 Copilot/Copilot Chat incl. Word/Excel/PowerPoint.
- **Consumer AI coverage:** Endpoint DLP + Browser Data Security block paste to ChatGPT, Google Gemini, DeepSeek, consumer Copilot — confirmed. Credit-card-into-ChatGPT example verbatim.
- **DSPM for AI: PREVIEW** — "front door" for AI data security; one-click policies — confirmed. DSPM overall in preview.
- **Dependency on SITs + sensitivity labels:** confirmed throughout — the AI controls act on classification. Architect's framing (foundations first) is Stuart's own, well-grounded.
- **Licensing caveat:** several browser/network features are pay-as-you-go, not bundled E5 — confirmed from service description and billing model pages.
- **All GA/preview statuses verified this session (Aug 2026).** Confirm the block-sensitive-prompts preview has reached the tenant before publishing.
- Metrics check due: 2026-09-26
