# Day 95 — LinkedIn Content Package
**Topic:** How the Microsoft security stack actually fits together — the architect's view
**Category:** Security Architecture / Microsoft Security (synthesis)
**Week theme:** Week 14 — the closing arc (Days 95–100)
**Date:** 2026-09-07 (Monday)
**Format:** Technical / architectural synthesis post
**LinkedIn URL:** https://lnkd.in/p/eiwEcSU5

---

## LinkedIn Article (final — ready to post, 2026-09-07)

How the Microsoft security stack actually fits together

* Over the last few months, I have written in detail about a long list of Microsoft security products.
* Entra.
* Purview.
* Defender in all its forms.
* Sentinel.
* Security Exposure Management.
* Security Copilot.
* And more recently, the AI agent security stack.

Each article looked at one piece.

As I come towards the end of this challenge, I want to step back and answer the question none of those individual articles really did:

How does it all fit together?

Because a list of products isn't an architecture.

An architecture is what you get when you understand how the pieces connect, what each layer is responsible for, and how information moves between them.

Here is how I hold it in my head.

The strategy sits on top: Zero Trust

Zero Trust isn't a product.

It is the security strategy everything underneath should support.

Microsoft defines it around three principles:

* Verify explicitly.
* Use least privilege access.
* Assume breach.

Those principles matter because they give you something to test your architecture against.

* Why are we implementing this control?
* What risk does it address?
* Does it help us verify access?
* Reduce privilege?
* Limit the impact of compromise?
* Improve our ability to detect and respond when something goes wrong?

That is the top of my model.

Not another security product.

The principles that decide what good looks like.

Identity is a control plane

If Zero Trust is the strategy, identity is one of the most important control planes underneath it.

* The old security model relied heavily on location:
* Inside the network meant trusted.
* Outside meant untrusted.

That doesn't work particularly well anymore.

* Users work from anywhere.
* Applications run across multiple clouds.
* Devices move between networks.
* Workloads communicate with other workloads.
* And now AI agents can act on behalf of users and organisations.

Identity therefore becomes one of the strongest signals behind modern access decisions.

Microsoft Entra sits here.

* Conditional Access evaluates signals and applies access policies.
* Privileged Identity Management helps reduce standing privileged access through just-in-time and time-bound activation.
* Identity Protection provides identity-risk signals.
* Identity Governance helps manage identity and access lifecycles.

And now:

Microsoft Entra Agent ID.

Agent ID extends Microsoft Entra identity capabilities to AI agents, providing dedicated identity constructs that can be authenticated, authorised, governed and protected.

That last part matters.

We are moving from thinking about identity as:

People.

Then:

People and workloads.

Towards:

People, workloads and AI agents.

But identity isn't acting alone.

Zero Trust access decisions can also use device health, location, workload, data and risk signals.

That interaction between signals is where the architecture starts becoming interesting.

Then the things you are protecting

Underneath that sit the things the organisation actually cares about.

* Devices.
* Applications.
* Data.
* Infrastructure.
* Networks.
* And increasingly AI.

Different Microsoft security products provide controls around each part.

Devices

Microsoft Intune manages device configuration and compliance.

Microsoft Defender for Endpoint provides prevention, detection, investigation and response.

Those device signals can then inform access decisions.

Having the correct password shouldn't automatically mean a user's device should be trusted.

Identity plus device context gives you a better decision than identity alone.

Data

Then there is Microsoft Purview.

This is where classification, information protection, DLP, Insider Risk Management, DSPM and other data-security capabilities come together.

One correction I think is important here:

Sensitivity labels are extremely useful, but they aren't the foundation of every Purview capability.

Microsoft's current DSPM guidance, for example, says a sensitivity labelling schema isn't required for DSPM, although it significantly improves context, reporting and recommendations.

The broader foundation is understanding the data.

* What is sensitive?
* Where is it?
* Who can access it?
* How is it being used?
* Where is it exposed?

Purview DSPM increasingly brings those questions together into a central data-security posture view.

Applications and cloud workloads

Applications introduce another set of controls.

Microsoft Defender for Cloud Apps provides visibility and protection around SaaS applications and cloud app usage.

Microsoft Defender for Cloud addresses multicloud security posture and workload protection across Azure, AWS, GCP, and hybrid environments.

Those aren't the same problem.

But the signals can contribute to the same security picture.

Network and access

Then there is Microsoft Entra Global Secure Access.

Global Secure Access is the umbrella for: Microsoft Entra Internet Access and Microsoft Entra Private Access.

Private Access is particularly interesting architecturally because it provides identity-centric Zero Trust Network Access to private resources.

Instead of giving someone broad network-level access through a traditional VPN, you can provide granular access to the applications and resources they actually need.

Microsoft explicitly positions this as modernising traditional VPN scenarios with identity-aware ZTNA.

Again: Least privilege.

The same Zero Trust principle, applied somewhere different.

Then comes the connective layer: security operations

This is where the separate security controls start becoming a platform.

Microsoft now describes the Defender portal as providing unified security operations.

It brings together capabilities including:

* XDR
* SIEM and SOAR
* Exposure management
* Cloud security
* Threat intelligence
* Generative AI

This is where the connections between the products become important.

Microsoft Security Exposure Management helps you understand where you are exposed before an attacker gets there.

It brings assets, identities, workloads and relationships together through the enterprise exposure graph and can identify attack paths towards critical assets.

Microsoft Defender XDR correlates security signals across endpoints, identities, email, Microsoft 365 services and SaaS applications.

Instead of investigating separate alerts, the SOC can investigate the wider incident.

And, as I wrote last week, automatic attack disruption can take containment action against high-confidence attacks.

Microsoft Sentinel adds the SIEM and SOAR capability.

It brings broader data collection, third-party security data, analytics, hunting and automation into the same security operations model.

And then:

Microsoft Security Copilot.

Copilot adds AI-assisted investigation and security operations capabilities across this environment.

Microsoft now explicitly brings Defender XDR, Sentinel, Security Exposure Management and Security Copilot together through the Defender portal.

That is an important change in how I think about the Microsoft security stack.

We aren't simply connecting individual security products anymore. Microsoft is building a common operational layer above them.

And running through all of it now: AI

AI security doesn't fit neatly into one box; it cuts across the architecture.

An AI agent may need an identity. Microsoft Entra Agent ID can provide that identity foundation and apply identity-driven controls to supported agents.

The data an AI application or agent accesses needs protecting.

Microsoft Purview can apply information protection and data-security controls across supported Copilot and AI scenarios. Sensitivity labels can affect how protected content is handled, including checking usage rights where label encryption applies.

AI agents also need security monitoring and threat protection.

Their identities and relationships increasingly appear in security and exposure-management experiences.

And then AI sits on the other side of the equation.

It is increasingly helping do the defending.

* Security Copilot.
* Security Copilot agents.
* AI-assisted investigations.
* Automated triage.
* Natural-language hunting.
* Security recommendations.

That has been one of the biggest themes running through this series:

AI is becoming something we need to secure and something we use to secure everything else.

The point most product demos miss

Any one of these products demos well on its own.

* Conditional Access looks good.
* Defender XDR looks good.
* Purview looks good.
* Exposure Management looks good.
* Sentinel looks good.

That's not where the biggest value sits.

It is in the connections.

* Identity risk influencing Conditional Access.
* Device compliance influencing an access decision.
* Defender for Identity providing context that contributes to your wider exposure picture.
* Security signals becoming correlated incidents in Defender XDR.
* Sentinel bringing third-party signals into unified security operations.
* Purview classifications and policies influencing how sensitive data is handled in supported AI experiences.

The architecture isn't simply the boxes.

It is the lines between the boxes.

And this is what I see in real environments

This is probably the biggest lesson I have learned working as an architect.

Most organisations don't need me to tell them Microsoft has another security product.

Many already own a significant part of this stack.

The challenge is that they often own it in silos.

* One team looks after Entra.
* Another handles Intune.
* Defender is somewhere else.
* Sentinel belongs to the SOC.
* Purview sits with compliance or data governance.
* Networking has its own team.
* And now AI arrives and touches nearly all of them.

The technology might integrate.

The organisation doesn't always integrate with it.

That is where architecture matters.

Not:

"Which product should we buy next?"

But:

"What are we trying to protect, what capabilities do we already own, what is actually deployed, and how should those capabilities work together?"

Because owning the licence isn't the difficult bit; getting the architecture, people, processes and technology working together is.

And the thread through everything

If there is one message I would take from this whole series, it is this:

The clever capability at the top only pays off when the foundations underneath it are done properly.

* Attack disruption can't act effectively on infrastructure that hasn't been onboarded and configured correctly.
* Exposure Management can't build a complete view from signals it doesn't have.
* Conditional Access can't make a good device-based decision if device posture isn't available.
* DSPM gets better context when your data-classification and protection foundations are in place.
* And Copilot doesn't magically fix poor information protection.

It works with the permissions and protection controls you have configured.

That is why the same word has appeared again and again throughout these articles.

Foundations.

The platform rewards organisations that do the unglamorous groundwork.

Owning the licence is the start. Architecture is the job.

If you look at the Microsoft security stack and it feels like a hundred separate products, I understand why.

* There are a lot of names.
* A lot of portals.
* A lot of licences.
* And they keep changing.

The shift happens when you stop looking at the individual product names and start looking at the layers.

Strategy.

* Identity and access.
* Devices, data, applications, infrastructure and network.
* Exposure management.
* Detection and response.
* SIEM and security operations.
* AI across all of it.

Different capabilities. Different teams.

But all serving the same security strategy, and all becoming increasingly connected.

For me, that is what a security architect is really there to do.

Not simply to know what each box does.

Understand the lines between them.

When you look at your own environment, do you see a coordinated security architecture, or a collection of products that happen to share a portal?

---

## Microsoft Learn References

- [Zero Trust overview](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview)
- [Zero Trust security in Azure](https://learn.microsoft.com/en-us/azure/security/fundamentals/zero-trust)
- [What is Microsoft Entra Agent ID?](https://learn.microsoft.com/en-us/entra/agent-id/what-is-microsoft-entra-agent-id)
- [DSPM deployment guidance](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-step1)
- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
- [Unified security operations in the Defender portal](https://learn.microsoft.com/en-us/unified-secops/overview-unified-security)

---

## Hashtags

#MicrosoftSecurity #SecurityArchitecture #ZeroTrust #DefenderXDR #MicrosoftEntra #MicrosoftPurview #IdentitySecurity #Cybersecurity

---

## Notes

- Day 95 — Week 14 opener, the closing arc. Synthesis piece: no new product, ties the whole series into one architecture.
- Structure = the architect's mental model, top to bottom: Zero Trust (strategy) → identity (control plane) → devices/data/apps/network (pillars) → SecOps (connective layer: Exposure Mgmt, XDR, Sentinel, Copilot) → AI woven across → the foundations thread.
- Deliberately positions Stuart as a strategic architect, not a feature explainer — the differentiator for the finale week.
- Reuses and references the whole 100-day body of work; pairs naturally with the 100_Day_Post_Index.
- One [STUART'S PERSPECTIVE] slot — the "owned in silos, the work is connecting it" practitioner view.
- Closing question invites the reader to assess their own estate — good comment driver.
- Metrics check due: 2026-10-07
