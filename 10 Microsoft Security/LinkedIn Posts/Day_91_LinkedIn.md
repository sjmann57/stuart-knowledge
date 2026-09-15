# Day 91 — LinkedIn Content Package
**Topic:** Microsoft Defender XDR — where the separate products stop being separate
**Category:** SecOps / Defender XDR / Threat Response
**Week theme:** Week 13 — SecOps posture (Days 89–91), series close
**Date:** 2026-09-03 (Thursday)
**Format:** Technical article — Week 13 Day 4 (close)
**LinkedIn URL:** https://lnkd.in/p/eSMrri5v

---

## LinkedIn Article (published — 2026-09-03)

Microsoft Defender XDR: where the separate products stop being separate

This is the last technical article in a run that has covered a lot of ground.

Sentinel becoming a platform.

What is new in Entra, Purview and Security Copilot agents.

Then Exposure Management and Defender for Identity this week.

Every one of those has been a piece.

Today is about the capability that helps turn those pieces into a whole.

Microsoft Defender XDR.

Because owning the products isn't the same as having them working together.

And XDR is where that starts to happen.

The problem it solves

Most organisations don't have a shortage of security tools.

They have a shortage of connection between them.

An attacker rarely stays in one place.

* They might phish a user.
* Land on an endpoint.
* Steal credentials.
* Move laterally through identity.
* Access SaaS applications.
* Reach cloud resources.

Along the way, different security products see different parts of the attack.

* Defender for Office 365 might detect the malicious email.
* Defender for Endpoint might detect malicious activity on the device.
* Defender for Identity might identify suspicious identity behaviour or lateral movement.
* Defender for Cloud might identify activity affecting a cloud workload.

Potentially four alerts.

Four different parts of the environment.

One attack.

And without correlation, a SOC analyst has to work out, under time pressure, that they are all part of the same story.

That correlation problem is one of the things Defender XDR exists to solve.

From alerts to incidents

The core idea in Defender XDR is the difference between an alert and an incident.

An alert tells you that something malicious or suspicious may have happened.

An incident brings related alerts together to tell the wider story of an attack.

Microsoft Defender automatically aggregates and correlates related alerts and security signals into incidents.

It then continues monitoring how those incidents develop and can merge incidents where further evidence shows they belong together.

That changes the analyst experience.

Instead of investigating:

Alert 1 > then Alert 2 > then Alert 3

And eventually discovering they are connected, the analyst gets a correlated incident containing the evidence Microsoft believes belongs to the same attack.

That can include:

* Alerts
* Users
* Devices
* Mailboxes
* Applications
* Evidence
* Attack timelines
* Relationships between affected assets

The incident graph then helps the analyst understand how those entities and alerts relate to each other.

That is the difference between investigating individual security events and investigating an attack story.

The products behind it

Defender XDR is Microsoft's extended detection and response capability that brings together signals across Microsoft security products.

The Microsoft Defender portal provides unified experiences for incidents and alerts, hunting, actions and submissions, and threat analytics.

Depending on what you have licensed and deployed, that can bring together signals and capabilities from products including:

* Microsoft Defender for Endpoint
* Microsoft Defender for Office 365
* Microsoft Defender for Identity
* Microsoft Defender for Cloud Apps

and other Microsoft security services integrated into the Defender portal.

Then you have the wider unified security operations platform.

Microsoft Sentinel adds SIEM capabilities, third-party data and broader security analytics.

Defender for Cloud adds cloud workload protection and cloud security context.

Security Exposure Management adds exposure relationships, critical assets and attack paths.

Microsoft Entra adds identity risk and access context.

The important point is this:

You only see the security capabilities your subscriptions provide.

Which brings me back to the theme running through this whole series.

The quality of the correlated security picture depends on the security signals and capabilities you have actually deployed.

Owning Microsoft 365 E5 doesn't magically create a mature XDR deployment.

The products still need configuring.

* Endpoints need onboarding.
* Identity sensors need deploying.
* Email protection needs configuring.
* Cloud applications need connecting.
* And the SOC still needs processes for investigating what the platform finds.

Attack disruption: the part that changes the conversation

This is the capability I would most want people to understand.

Automatic attack disruption doesn't simply detect an attack and generate another alert.

It can automatically contain an attack while it is still happening.

And importantly, it works at the incident level.

Microsoft describes automatic attack disruption as using XDR signals to evaluate the entire attack rather than relying on a single indicator of compromise.

The process has three broad stages.

* Microsoft Defender correlates signals from different sources into a high-confidence incident.
* It identifies assets the attacker controls or uses to spread the attack.
* Then it automatically takes response actions through the relevant Microsoft security products to contain those assets.

Those actions can now include things such as:

* Containing or isolating a device
* Containing a user at the endpoint layer
* Disabling an Active Directory user
* Revoking an Entra user session
* Suspending a user in Entra ID
* Taking protective action against a compromised OAuth application
* Containing an IP address

Microsoft also has preview attack disruption integrations for Okta and AWS, using Microsoft Sentinel integrations.

That is quite a shift.

We have moved from:

"Something bad happened. Here is an alert."

towards:

"Something bad is happening. We have enough confidence to start containing it."

One detection can trigger a response somewhere else

Microsoft gives a good example of why cross-product response matters.

Imagine Defender for Endpoint identifies a malicious file on an endpoint.

Defender XDR can instruct Defender for Office 365 to scan for and remove that file from email messages across the organisation.

Think about what is happening there.

The detection starts on the endpoint.

The response reaches into email.

That is XDR.

The boundary between the individual products becomes less important because the platform understands that the endpoint and the mailbox are part of the same attack.

Why speed matters

This matters because attackers don't work at SOC speed.

An attacker can move through an environment in minutes.

A human analyst needs time.

Time to receive the alert.

Time to investigate.

Time to correlate the evidence.

Time to understand what has happened.

Time to decide what action is safe.

Time to contain it.

Automatic attack disruption is designed to reduce that gap.

Microsoft uses correlated telemetry, threat intelligence, historical incident information and multiple AI and machine-learning approaches to establish sufficient confidence before taking disruption actions.

That confidence threshold matters.

Because automatically disabling an identity or isolating a device is very different from simply raising an alert.

The callback to yesterday matters here

Yesterday I wrote about Defender for Identity.

There is a direct connection.

Automatic attack disruption can take action against compromised on-premises Active Directory identities.

But there are prerequisites.

Defender for Identity requires the appropriate domain controller auditing, sensors and remediation permissions for those actions to work.

There is also an important 2026 sensor nuance.

With Defender for Identity sensor v3.x, remediation actions use the domain controller's LocalSystem account.

If you are using v2.x sensors, Defender for Identity can use LocalSystem by default or an appropriately configured gMSA action account where required.

The v3.x sensor does not use the gMSA action accounts configured for v2.x.

That is another example of why the foundations matter.

Attack disruption cannot magically act on infrastructure that hasn't been correctly integrated with the platform.

The clever capability at the top still depends on the deployment underneath it.

Would you actually let it disable an account?

This is where I think the technology becomes interesting from an architecture point of view.

It is easy to look at automatic attack disruption in a demo and think:

Of course I want that turned on.

Then you put yourself in the client's position.

Would you let a security platform automatically disable an identity?

* What if it is an executive?
* A service account?
* A critical administrator?
* Would you let it isolate a production device?
* And what happens if the detection is wrong?
* These are reasonable questions.
* But there is another side to the conversation.
* What happens if you don't?

If an attacker is actively moving through the environment, how long does it take your SOC to identify the attack, correlate everything and contain it manually?

* Five minutes?
* Twenty minutes?
* An hour?
* Longer?

That is the balance.

Machine-speed containment versus the operational risk of automated action.

For me, the answer isn't simply to turn automation off.

It is to understand how it works, configure it properly, protect the genuine exceptions and make sure the SOC knows how to investigate and reverse actions when required.

The controls that keep humans involved

Microsoft has deliberately built visibility and control around attack disruption.

When automatic attack disruption takes action, Defender can show:

* An Attack Disruption tag on the incident
* A banner showing that automatic action occurred
* The containment status of affected assets in the incident graph
* Actions in the Action center
* Attack disruption information through APIs

Security teams remain responsible for investigation, remediation and returning assets to service.

Microsoft also allows you to create exclusion policies that prevent specific assets or actions from being automatically disrupted.

For example, you might exclude a critical server from automatic isolation or prevent a particular critical identity from being automatically disabled.

But this needs discipline.

Microsoft explicitly recommends keeping exclusions limited.

And that makes sense.

If you exclude everything you are worried about disrupting, you risk excluding exactly the assets an attacker would most like to compromise.

The question shouldn't be:

"How do we stop automation touching anything important?"

It should be:

"Which exceptions are genuinely necessary, and what compensating response do we have for them?"

That is a much better security conversation.

Where Sentinel fits

For completeness, because I started this series talking about Sentinel, this is where the pieces come together.

Microsoft Sentinel and Defender XDR now form part of Microsoft's unified security operations platform in the Microsoft Defender portal.

Sentinel adds the SIEM capability.

* Third-party data.
* Analytics.
* Hunting.
* Automation.

Longer-term security data and investigation capabilities.

Defender XDR brings deep correlation and response across Microsoft's Defender security products.

When Sentinel is connected to the Defender portal, alerts from both Microsoft and non-Microsoft sources can participate in the unified incident experience.

Closing the thread

Two weeks ago I started writing about what is changing across the Microsoft security stack.

* Sentinel.
* Entra.
* Purview.
* Security Copilot agents.

Then this week:

* Security Exposure Management.
* Defender for Identity.
* And now Defender XDR.

Pull it together, and the shape becomes clearer.

* Exposure Management shows where you are exposed before an attack.
* Defender products detect activity across identities, endpoints, email, applications and other parts of the environment.
* Defender XDR correlates those signals into incidents and gives the SOC the attack story.
* Automatic attack disruption can then take containment actions against high-confidence attacks while the security team investigates.
* Sentinel extends that security operations model with SIEM, third-party data, analytics and automation.

That is the model Microsoft is building.

Not simply a collection of security products.

A coordinated security operations platform where information from one part of the environment can change how another part responds.

But the same warning applies to everything I have written about during this series.

The coordination is only as good as the foundations underneath it.

* The products need deploying.
* The sensors need to be there.
* The endpoints need onboarding.
* The identity infrastructure needs monitoring.
* The integrations need configuring.
* The permissions need to be right.
* The SOC needs to know what happens when automation acts.

Buying the licence doesn't do any of that for you.

The platform can correlate, investigate and increasingly disrupt attacks at machine speed.

But it still rewards the organisations that did the unglamorous work underneath it.

Are your Microsoft security products actually working as one coordinated defence, or are they still separate tools raising separate alerts that nobody has time to connect?

---

## Microsoft Learn References

- [What is Microsoft Defender XDR?](https://learn.microsoft.com/defender-xdr/microsoft-365-defender)
- [Incidents and alerts in the Microsoft Defender portal](https://learn.microsoft.com/defender-xdr/incidents-overview)
- [Automatic attack disruption in Microsoft Defender](https://learn.microsoft.com/defender-xdr/automatic-attack-disruption)
- [Configure automatic attack disruption in Microsoft Defender XDR](https://learn.microsoft.com/defender-xdr/configure-attack-disruption)
- [Microsoft Defender XDR integration with Microsoft Sentinel](https://learn.microsoft.com/azure/sentinel/microsoft-365-defender-sentinel-integration)

---

## Hashtags

#DefenderXDR #XDR #SecOps #MicrosoftSecurity #MicrosoftDefender #AttackDisruption #ThreatResponse #Cybersecurity

---

## Accuracy Notes

- **Defender XDR definition:** unified pre- and post-breach suite coordinating detection/prevention/investigation/response across endpoints, identities, email, apps (+ cloud, SaaS) — confirmed verbatim.
- **Products correlated:** Defender for Endpoint, Defender for Office 365, Defender for Identity, Defender for Cloud Apps, Defender Vulnerability Management, Defender for Cloud, Entra ID Protection, Purview DLP, App Governance, Purview IRM, Security Exposure Management — confirmed from overview.
- **"Correlates signals from products you have licensed and provisioned"** — confirmed verbatim (foundations theme).
- **Alerts vs incidents:** alert = single detection; incident = container of related alerts = full attack story; AI correlation engine auto-aggregates and keeps adding evidence — confirmed. External alerts via Sentinel + Defender for Cloud — confirmed. Incident contents (timeline, tactics, entities, graph, AIR logs, evidence, summary) — confirmed.
- **Automatic attack disruption:** contains in-progress attacks at incident level (not single IOC); 3 stages (correlate → identify attacker-controlled assets → auto response); high-confidence signals + Microsoft security research + AI — confirmed. Malicious-file-to-all-mailboxes example verbatim.
- **Response scope:** disable accounts, isolate/contain devices, contain tokens/sessions/apps; Entra ID + AD actions; PREVIEW for Okta + AWS via Sentinel — confirmed. Automatic device isolation in preview.
- **MDI prerequisites for disruption:** DC auditing + action accounts (default LocalSystem impersonation); sensor must be on the DC where the account is disabled — confirmed. This is the Day 90 callback.
- **Human control:** Attack Disruption tag, yellow banner, incident graph status, Action center, full logging, release/enable actions, exclusion policies (not recommended broadly) — confirmed.
- **Device group remediation levels:** Full / Semi automation; Semi allows disruption without manual approval — confirmed (not heavily used in article to keep it readable).
- **Sentinel integration:** bi-directional sync; post-July-2025 onboarding auto-onboards workspace to Defender portal for unified SecOps — confirmed.
- **Cross-product hunting:** 30 days historic raw signals — confirmed (not central to article).
- **All GA/preview statuses verified this session (Sep 2026).** Okta/AWS disruption + automatic device isolation still preview — re-check before publishing.
- One [STUART'S PERSPECTIVE] slot left (human trust / exclusions).
- Metrics check due: 2026-10-03
