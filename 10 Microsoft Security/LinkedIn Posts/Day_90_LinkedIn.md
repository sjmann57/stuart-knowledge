# Day 90 — LinkedIn Content Package
**Topic:** Microsoft Defender for Identity — watching the part of your identity estate attackers still love
**Category:** Identity Security / Defender for Identity / ITDR
**Week theme:** Week 13 — SecOps posture (Days 89–91)
**Date:** 2026-09-02 (Wednesday)
**Format:** Technical article — Week 13 Day 3
**LinkedIn URL:** https://lnkd.in/p/ejUPm7Ub

---

## LinkedIn Article (published — 2026-09-02)

Microsoft Defender for Identity: watching the ground attackers still love

One of my favourite and not often talked about subjects.

Yesterday I wrote about Microsoft Security Exposure Management and how Microsoft says 61% of attack paths lead to sensitive user accounts.

That is a good place to pick up today.

Because one of the important sources of identity context feeding Microsoft's wider security platform is:

Microsoft Defender for Identity.

And one of the environments it protects is something that sometimes gets less attention in 2026:

On-premises Active Directory.

The blind spot nobody likes to talk about

Much of today's identity conversation is about cloud identity.

* Entra ID.
* Conditional Access.
* Passkeys.
* Workload identities.
* Agent identities.

All important, and I have written about all of them.

But many organisations still depend heavily on on-premises Active Directory.

And AD remains a major target.

Why?

* Because it has often existed for years.
* Configurations accumulate.
* Legacy protocols remain enabled.
* Service accounts gain permissions nobody remembers granting.
* Groups grow.
* Applications develop dependencies.
* Normally poorly documented and fully understood.
* And sometimes everyone becomes nervous about changing any of it because nobody quite knows what will break.

Microsoft's own security research makes the problem clear.

Microsoft says most identity attacks use common Active Directory misconfigurations and continued use of legacy components, such as NTLMv1, to compromise identities and breach organisations.

An attacker doesn't necessarily need to begin with Domain Admin.

They can start with an ordinary identity.

The problem begins when they can steal credentials, escalate privileges and move laterally towards more sensitive identities and infrastructure.

Eventually, that path can lead towards the domain itself.

Conditional Access remains an important control for cloud access.

But it isn't designed to detect an attacker performing lateral movement inside Active Directory.

That requires visibility into what is happening inside your identity infrastructure.

What Defender for Identity is

Microsoft Defender for Identity, or MDI, is Microsoft's identity threat detection and response capability for on-premises, cloud and hybrid identity environments.

Microsoft describes it as helping organisations:

detect, investigate and respond to identity-based attacks across on-premises, cloud and hybrid environments.

It monitors identity signals from:

* On-premises Active Directory
* Microsoft Entra ID
* Supported IAM solutions such as Okta

It then uses behavioural analytics, threat intelligence and known attack patterns to identify suspicious activity.

Those signals don't stay isolated inside Defender for Identity.

They flow into the Microsoft Defender portal, where Microsoft can correlate them with signals from endpoints, email, SaaS applications, cloud workloads and other security sources.

That is important.

An identity alert may only tell you part of the story.

Combine it with the compromised endpoint, suspicious email, cloud activity and lateral movement, and suddenly you can see the attack rather than a collection of separate alerts.

Identity Security is becoming broader

There is another change worth understanding.

Microsoft increasingly describes Defender for Identity as part of its wider Identity Security capability.

That extends beyond traditional AD users.

Microsoft's current identity inventory includes human and non-human identities.

Non-human identities can include:

* Active Directory service accounts
* Microsoft Entra service principals
* OAuth applications
* Identities from supported SaaS platforms

Microsoft has also started adding visibility into service principals used by AI agents, currently in preview.

This connects with something I have written about repeatedly over the last few weeks.

Identity security isn't simply about employees anymore.

* Users.
* Administrators.
* Service accounts.
* Applications.
* Workloads.
* AI agents.

They can all have access.

They can all have permissions.

And they can all become part of an attack path.

Two things Defender for Identity does that are easy to conflate

I find it easier to think about Defender for Identity as doing two related jobs.

The first is posture

Before an attack happens, Defender for Identity can assess your identity environment and tell you where weaknesses exist.

Microsoft calls these identity security posture assessments.

They appear in Microsoft Secure Score and identify exploitable configurations and weaknesses, with remediation recommendations.

Current assessments cover areas including:

* Privileged service accounts
* DCSync permissions
* Kerberos delegation
* Dormant or insecure accounts
* Risky privileged group membership
* Hybrid identity configuration
* Legacy configurations and protocols

One example I particularly like is looking for service accounts sitting in privileged groups.

* These accounts are often long-lived.
* They may run applications or scheduled tasks.
* Nobody logs onto them every morning.
* And because they aren't associated with one person, ownership can become unclear.

Microsoft's current assessment guidance specifically highlights service accounts that are members of privileged groups such as Domain Admins and Enterprise Admins.

That is exactly the type of identity I would want to find before an attacker does.

The second is detection and response

* Posture tells you where the weaknesses are.
* Detection tells you when someone may be exploiting them.
* Defender for Identity analyses identity behaviour across the stages of an attack.

Microsoft's current architecture documentation describes stages including:

Reconnaissance

An attacker starts learning about the environment:

* Users.
* Groups.
* Resources.
* IP addresses.

Compromised credentials

Attempts to obtain or misuse credentials, including brute-force activity, repeated authentication failures and suspicious group membership changes.

Lateral movement

The attacker tries to expand their control across systems and identities.

And eventually:

AD domain dominance.

Microsoft associates this stage with behaviour including remote code execution against domain controllers, DCShadow, malicious domain-controller replication and Golden Ticket activity.

That last stage is clearly serious.

But I wouldn't wait until then.

A credible credential compromise or lateral movement alert involving a privileged identity may already represent a significant incident.

The earlier you identify the attack chain, the more opportunity you have to stop it.

This is where the real environments matter

This is one of those technologies where the architecture diagram and the customer environment can look very different.

A lot of security investment understandably goes into cloud identity.

* MFA.
* Conditional Access.
* PIM.
* Identity Protection.
* Passkeys.

But then you look behind it and find an Active Directory environment that has been running for ten, fifteen or twenty years plus.

* Old service accounts.
* Legacy authentication.
* Nested privileged groups.
* Servers nobody wants to touch.
* Accounts that nobody is quite sure who owns.
* And that matters because hybrid identity connects these environments.

Cloud security controls can be well designed, but the route to them begins somewhere much older.

For me, that is one of the strongest reasons for deploying Defender for Identity.

You need visibility on both sides of hybrid identity.

How it works, briefly

Defender for Identity uses lightweight sensors on your on-premises identity infrastructure.

The sensors capture and analyse relevant network traffic and Windows events locally, then send the required signals to Microsoft's cloud service for analysis.

Microsoft currently has two sensor generations:

v2.x and v3.x.

And this is an area where Microsoft's deployment guidance has changed significantly during 2026.

Sensor v3.x

For eligible domain controllers running Windows Server 2019 or later, Microsoft recommends sensor v3.x.

This includes eligible domain controllers that also run:

* AD FS
* AD CS
* Microsoft Entra Connect

Sensor v3.x requires Microsoft Defender for Endpoint to be onboarded on the server and has additional operating system and update prerequisites.

Sensor v2.x

Sensor v2.x remains required for several scenarios.

That includes:

* Older supported domain controllers
* Standalone AD FS servers
* Standalone AD CS servers
* Standalone Microsoft Entra Connect servers

In other words, don't simply assume v3 has replaced v2 everywhere.

Microsoft supports mixed deployments where v2 and v3 sensors report into the same Defender for Identity environment.

Microsoft also offers a migration experience for eligible v2.x domain-controller sensors.

Where the prerequisites are met, you can migrate directly through the Microsoft Defender portal.

The v2 sensor continues monitoring until v3 is ready, allowing Microsoft to switch over without monitoring downtime or duplicated data.

One important limitation:

The current direct migration process applies to eligible domain controllers without additional identity roles.

So again, check the current prerequisites before planning your migration.

The new Identity Security view

Microsoft is also building a broader Identity Security dashboard, currently in preview and gradually rolling out.

It brings together information across areas including:

* Identity providers
* SaaS applications
* On-premises identities
* PAM and IGA integrations
* Human identities
* Non-human identities
* Agentic identities, currently in preview

The dashboard also provides identity coverage information and Secure Score posture information.

There is also a separate Coverage and maturity experience, currently in preview.

This helps you understand how complete your identity security coverage is across on-premises, cloud, SaaS and supported partner environments.

Microsoft currently defines maturity levels as:

Connected → Protected → Fortified → Resilient.

I like this direction.

It isn't enough to say:

"We own Defender for Identity."

The better question is:

"How much of our identity environment is actually being monitored?"

Coverage matters

This brings me back to something I keep writing about.

Foundations.

Defender for Identity is a good example of a security control whose value depends heavily on coverage.

Microsoft's current deployment guidance says to install Defender for Identity sensors on all domain controllers, including read-only domain controllers.

If you have AD FS, AD CS or Entra Connect servers that aren't domain controllers, those should also be covered using the appropriate v2 sensor where supported.

An unmonitored domain controller is a gap in your identity visibility.

Microsoft's new Coverage and maturity experience now makes this easier to see.

The on-premises identities card shows active sensors against discovered servers and identifies servers without Defender for Identity sensor coverage.

That is where I would start.

Not with the alerts.

With coverage.

Where it fits with Exposure Management

This is also where yesterday's Microsoft Security Exposure Management article connects.

Exposure Management can show attack paths across identities, devices and cloud resources.

But those attack paths depend on security data.

Defender for Identity provides identity context around Active Directory, identities, relationships, security posture and attacker movement.

That context contributes to Microsoft's wider Defender and exposure-management view.

Take away that visibility and your understanding of the on-premises identity part of the attack surface becomes weaker.

Again:

The clever capability at the top depends on getting the foundations underneath it right.

What about Entra ID Protection?

This relationship has changed enough that I wouldn't describe it simply as:

MDI protects AD | Identity Protection protects Entra.

That used to be a useful shorthand.

It is becoming too simplistic.

Microsoft Defender for Identity now monitors identity signals across Active Directory, Microsoft Entra ID and supported external identity providers.

Microsoft Entra ID Protection remains focused on detecting, investigating and remediating identity-based risk in Microsoft Entra ID, including risky users and sign-ins.

The products remain complementary.

But Microsoft's current Identity Security direction increasingly brings those signals together.

For example, the Identity Security dashboard can display identity-related incidents containing alerts from Defender for Identity and Microsoft Entra ID Protection.

That gives the SOC a much more useful question than:

"Was this an on-premises or cloud identity attack?"

The question becomes:

"What happened to this identity across the whole environment?"

And one housekeeping point

If anyone reading this is still running Advanced Threat Analytics (ATA), this needs attention.

ATA 1.x reached the end of extended support on:

14 January 2026.

It no longer has Microsoft support.

Defender for Identity is Microsoft's cloud-based successor for protecting on-premises Active Directory identity signals.

If ATA is still sitting somewhere in your environment, it's time to migrate, urgently.

Where I would start

If you have Defender for Identity licensing and haven't looked at the deployment recently, I would start with coverage:

* Check every domain controller.
* Including the read-only ones.
* Check AD FS.
* Check AD CS.
* Check Entra Connect, including active and staging servers where applicable.

Then check which sensor version each server should actually be running.

Don't assume everything should be v3.

After that, look at the identity security posture assessments.

I would pay particular attention to:

* Privileged service accounts
* Replication permissions
* Delegation
* Privileged group membership
* Legacy authentication
* Hybrid identity weaknesses

Then look at your detection and response processes.

If Defender for Identity raises a credible credential compromise, lateral movement or domain dominance alert, who investigates it?

* How quickly?
* What endpoint context do they have?
* What happens if the identity is privileged?
* And can your SOC follow the attack from the identity into the endpoint, cloud and other affected workloads?

Because simply generating the alert isn't the objective.

Stopping the attacker is.

The ground attackers still love

Cloud identity gets a lot of attention.

And rightly so.

But that doesn't make Active Directory disappear.

Many organisations still have years of identity history sitting inside it.

* Old accounts.
* Old permissions.
* Old protocols.
* Old dependencies.

And somewhere inside all of that may be the route an attacker needs.

Microsoft Defender for Identity gives you the posture, detection and investigation capabilities to understand that part of your identity environment and connect it with the wider Microsoft security platform.

For me, the question is simple:

Is your on-premises Active Directory monitored to the same standard as your cloud identity, or is it the quiet blind spot in your estate?

---

## Microsoft Learn References

- [Microsoft Defender for Identity overview](https://learn.microsoft.com/defender-for-identity/what-is)
- [Defender for Identity deployment overview](https://learn.microsoft.com/defender-for-identity/deploy/deploy-defender-identity)
- [Defender for Identity security posture assessments](https://learn.microsoft.com/defender-for-identity/security-assessment)
- [What is Identity Security?](https://learn.microsoft.com/defender-xdr/identity-security/identity-security-overview)
- [What's new in Microsoft Defender for Identity](https://learn.microsoft.com/defender-for-identity/whats-new)

---

## Hashtags

#DefenderForIdentity #IdentitySecurity #ITDR #ActiveDirectory #MicrosoftSecurity #MicrosoftDefender #HybridIdentity #Cybersecurity

---

## Accuracy Notes

- **MDI definition:** ITDR for hybrid; monitors on-prem AD, Entra ID, other IAM (Okta); behavioural analytics + threat intel; streams into Defender portal for correlated incidents — confirmed.
- **Core component of Microsoft Identity Security**; protects human + NHIs (service accounts, service principals, OAuth apps, agentic identities) — confirmed.
- **Four capabilities:** posture assessments (via Secure Score / ISPM), real-time detection, investigation, remediation — confirmed.
- **Attack stages:** Reconnaissance / Compromised credentials / Lateral movement / AD Domain dominance (RCE on DCs, DCShadow, malicious replication, Golden Ticket) — verbatim from overview.
- **Architecture:** lightweight sensors on DCs (incl RODCs), AD FS, AD CS, Entra Connect; API connectors; cloud analytics; only required signals sent — confirmed. No port mirroring.
- **Sensor v3.x (March 2026):** supports DCs running Entra Connect roles; v2.x→v3.x migration in portal, no downtime (~20 min) — confirmed. (AD FS/AD CS detections on v3.x "coming soon" per docs.)
- **Entra Connect (MSOL_) assessments:** rotate password >90 days; remove unnecessary replication permissions; Enterprise/Domain Admin no longer allowed as AD DS connector account (Entra Connect build 1.4.x+) — confirmed. These require sensor on Entra Connect server.
- **Unmonitored ADCS/ADFS/Entra Connect assessments (July 2025)** — confirmed.
- **Identity Security dashboard: PREVIEW (March 2026)** — summary cards + maturity/coverage score; rolling out gradually — confirmed, flagged as preview.
- **Identity risk score aggregates MDI + Entra ID Protection** — confirmed.
- **MDI vs Entra ID Protection:** MDI = on-prem + synced accounts; Entra ID Protection = cloud-only Entra accounts — confirmed, complementary.
- **Feeds Defender XDR + Exposure Management (lateral movement paths)** — confirmed; ties to Day 89.
- **ATA end of extended support: 13 January 2026** — confirmed; migrate to MDI.
- **Licensing:** per-user; EMS E5/A5, M365 E5/A5/G5, Defender suites, MDI for Users standalone — confirmed.
- **All GA/preview statuses verified this session (Sep 2026).** Identity Security dashboard + some v3.x role detections still preview/coming — re-check before publishing.
- Two [STUART'S PERSPECTIVE] slots left.
- Metrics check due: 2026-10-02
