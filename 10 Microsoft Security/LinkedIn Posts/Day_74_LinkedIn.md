# Day 74 — LinkedIn Content Package
**Topic:** Zero Trust foundations — three principles, seven pillars, and why it matters
**Category:** Zero Trust / Microsoft Security
**Week theme:** Zero Trust — principles, assessment, identity, and adoption (Days 74–77)
**Date:** 2026-08-17 (Monday)
**Format:** Technical article — Week 11 Day 1
**LinkedIn URL:** https://www.linkedin.com/pulse/zero-trust-foundations-three-principles-seven-pillars-stuart-mann-y9nhe

---

## LinkedIn Article (published — 2026-08-17)

Zero Trust foundations: three principles, seven pillars, and why it matters

Zero Trust is one of the most overused terms in security.

Every vendor claims their product delivers it.

Most organisations say they are on a Zero Trust journey.

Very few can explain what that actually means.

So this week I am going to cover it, starting with the foundations today, running through the Microsoft Zero Trust Assessment tomorrow, and then going deeper into specific pillars later in the week.

What Zero Trust actually is

Zero Trust is a security strategy.

It is not a product you can buy, a feature you can enable, or a certification you can achieve. It is an architectural approach that changes how you think about access, trust and risk.

The traditional security model relied heavily on network boundaries and assumed that assets inside the perimeter were safer than those outside.

That model does not work anymore.

Users access resources from anywhere. Applications live across cloud and on-premises environments. Devices are not always managed. Modern attacks use identity compromise, phishing and session hijacking and no longer depend on network location.

Zero Trust replaces that trust-by-default model with a simple idea:

Never trust, always verify.

And importantly, verification doesn't happen once. Trust needs to be continuously evaluated as conditions and risk change.

The three principles

Microsoft's Zero Trust model is built on three guiding principles.

The first is verify explicitly.

Every access request should be authenticated and authorised using all available signals. Not just username and password. And where possible, passwords should be replaced with phishing-resistant authentication methods, such as passkeys.

Identity, device health, location, behaviour, the resource being accessed, data classification, anomalies and risk can all contribute to the decision.

Trust is not assumed because someone is on the corporate network or because they authenticated successfully yesterday.

The second is to use least privilege access.

Users and workloads get only the access they need, for the shortest time required.

This means approaches such as just-in-time and just-enough access, scoped permissions, risk-based adaptive policies and controls that reduce unnecessary standing privilege.

The third is assume breach.

This is the one that changes how you architect everything else.

If you design your environment assuming that an attacker might already be operating inside it, you stop relying on an impenetrable perimeter and start focusing on limiting the blast radius.

Segment access.

Encrypt communications.

Monitor activity.

Build detection and response into the environment so that when something does happen, you can contain it quickly.

We have been talking about these three principles for years, yet in many organisations, only one or two are really being put into practice.

The seven pillars

Microsoft applies Zero Trust across seven core technology areas.

Identity covers human and non-human identities and the controls used to authenticate and authorise them. Microsoft Entra provides many of these capabilities, including Conditional Access, Identity Protection and identity governance.

Endpoints cover the devices accessing your resources. Access decisions can take into account device management, compliance, configuration and risk. A user might have valid credentials, but if their device is unmanaged or compromised, that should change the access decision.

Data protects the asset itself. Classification, labelling, encryption, access controls and data loss prevention help protect sensitive information throughout its lifecycle. Microsoft Purview provides many of these capabilities.

Applications cover how applications and APIs authenticate, receive permissions and access resources. Zero Trust principles also need to be built into application development rather than relying on the network perimeter to protect the application.

Infrastructure covers the workloads and platforms running the organisation, including servers, virtual machines, containers and cloud services across on-premises, hybrid and multicloud environments.

Networks control connectivity between users, devices, applications and resources. Segmentation and micro-segmentation help restrict lateral movement; traffic should be protected and monitored, and access should be explicitly authorised rather than trusted because it originates from an internal network. Microsoft Entra Global Secure Access is one Microsoft technology that can contribute here.

The seventh area is Visibility, automation and orchestration.

This brings signals from across the other pillars together so security teams can detect, investigate and respond to threats. Microsoft Defender XDR and Microsoft Sentinel are major parts of Microsoft's approach here.

And what about AI?

Another area we need to consider is AI.

Microsoft's current Zero Trust guidance applies the same principles to AI workloads, applications, agents and data.

Microsoft has also introduced AI security checks into the Zero Trust Assessment, including guidance around Microsoft Entra agent identities.

I covered some of this during last week's series on Microsoft Agent 365.

I would not describe AI as simply replacing the established seven-pillar Zero Trust model with an eight-pillar model.

Instead, AI is becoming another major security scenario where the same Zero Trust principles apply.

As AI agents increasingly act on behalf of users and organisations, identity, permissions, data access and continuous monitoring become even more important.

Why this matters in practice

Zero Trust is worth understanding properly, rather than treating it as a marketing term, because it gives you a consistent framework for making security decisions.

When someone asks why you are implementing Conditional Access, why you require compliant devices for sensitive applications, why privileged access is time-limited, or why you are segmenting your network, the answer comes back to the same principles.

Verify explicitly.

Use least privilege.

Assume breach.

That consistency makes it easier to explain security decisions to stakeholders, prioritise investment and identify gaps across your environment.

And importantly, Zero Trust is not something you finish.

Microsoft describes adoption as a gradual, long-term effort. Different organisations start from different levels of maturity, technology and risk.

So before deciding where to invest next, you need to understand where you are today.

Tomorrow I will look at the Microsoft Zero Trust Assessment. This open-source PowerShell-based assessment uses read-only permissions to examine your Microsoft environment against Microsoft's current security recommendations.

Rather than asking whether you have Zero Trust, it gives you something much more useful:

Where are the gaps?

What is your organisation's starting point with Zero Trust? Do you have the foundations in place, or are you still working through the principles?

---

## Microsoft Learn References

- [Zero Trust overview — guiding principles](https://learn.microsoft.com/security/zero-trust/zero-trust-overview)
- [Technology pillars overview](https://learn.microsoft.com/security/zero-trust/deploy/overview)
- [Zero Trust adoption framework overview](https://learn.microsoft.com/security/zero-trust/adopt/zero-trust-adoption-overview)

---

## Hashtags

#ZeroTrust #MicrosoftSecurity #SecurityArchitecture #MicrosoftEntra #ZeroTrustStrategy #Cybersecurity #InfoSec #MicrosoftMVP

---

## Notes

- Day 74 published post — Week 11 opener.
- Stuart's version expanded the AI section significantly vs draft: not treating AI as an eighth pillar but as a major security scenario where ZT principles apply.
- Passkeys/phishing-resistant auth added to Verify Explicitly section.
- "Zero Trust is not something you finish" point added — good stakeholder framing.
- Closing sets up Day 75 (Assessment article, scheduled for Tuesday 2026-08-18).
- Metrics check due: 2026-09-17
