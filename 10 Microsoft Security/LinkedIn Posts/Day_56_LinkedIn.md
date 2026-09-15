# Day 56 — LinkedIn Content Package
**Topic:** Global Secure Access + Conditional Access + Defender for Cloud Apps — the unified Zero Trust access model
**Category:** Network Security / Zero Trust / Identity
**Week theme:** The network access layer (Days 53–56)
**Date:** 2026-07-31
**Format:** Technical article — week synthesis

---

## LinkedIn Article (published — 2026-07-31)

Global Secure Access + Conditional Access + Defender for Cloud Apps: One Zero Trust Access Model

Most security architectures have the same gap.

- The identity platform controls application access.
- The network layer controls connectivity.
- The two do not always work together.

This week I have covered the three layers of Microsoft Global Secure Access:

- The overview on Monday
- Microsoft Entra Private Access on Tuesday
- Microsoft Entra Internet Access on Wednesday

Today I want to bring them together and show how they connect with Microsoft Entra Conditional Access and Microsoft Defender for Cloud Apps to form a single Zero Trust access model.

Not three separate tools.

One policy framework operating across identity, network and applications.

Three layers, one access model

Microsoft positions Global Secure Access together with Microsoft Defender for Cloud Apps as a converged approach to securing access across identities, networks and applications.

That convergence is what makes the architecture different from deploying separate point solutions.

The three layers are identity, network and application.

The identity layer is Microsoft Entra ID together with Conditional Access.

This is where access decisions begin: who the user is, whether their device is compliant, what their sign-in risk is and the conditions under which access should be granted.

The network layer is Microsoft Global Secure Access.

Traffic is routed through the Microsoft Traffic Profile, Microsoft Entra Private Access or Microsoft Entra Internet Access, depending on the destination.

The application layer is Microsoft Defender for Cloud Apps.

For supported applications, Defender for Cloud Apps can apply session controls after authentication, such as preventing downloads on unmanaged devices, watermarking documents or monitoring risky activity within an active session.

Each layer contributes a different control.

Together they form a single Zero Trust access model.

Conditional Access is the common policy layer.

The reason these technologies work together is that Conditional Access provides the common identity policy layer across them.

For application access, Conditional Access determines whether a user can authenticate and under which conditions.

For network access, Compliant Network Grant Control verifies that traffic flows through Microsoft Global Secure Access before access is granted to supported applications.

For application sessions, Conditional Access Session Controls can route supported SaaS sessions through Microsoft Defender for Cloud Apps, enabling real-time monitoring and enforcement within the session.

A user who satisfies identity, device and network requirements experiences seamless access.

A user who fails one of those conditions encounters the appropriate control.

The policy remains consistent because each component is working from the same identity context.

Continuous Access Evaluation

Traditional access decisions happen when a user signs in.

Once an access token has been issued, that token remains valid until it expires unless something intervenes.

Continuous Access Evaluation (CAE) changes that model.

Supported applications can respond rapidly to significant events such as account disablement, password resets or increased user risk without waiting for token expiry.

Global Secure Access integrates with these identity signals so protected access can be re-evaluated as user state changes.

Instead of relying solely on token lifetime, access decisions become much more dynamic.

Unified visibility

One of the practical advantages of the architecture is operational visibility.

Microsoft Global Secure Access provides unified traffic logs across Microsoft Traffic, Private Access and Internet Access.

Rather than correlating VPN logs, proxy logs and identity logs separately, user identity is already associated with network activity.

Security teams can see who accessed a resource, from which device, from which location and which policy applied.

Investigation becomes significantly simpler because identity and network context are already connected.

Where to look today

If you have followed this week's articles and already have Microsoft Global Secure Access deployed, open the Global Secure Access dashboard in the Microsoft Entra admin centre.

Review the traffic dashboards and activity logs across all three traffic profiles.

For Microsoft Defender for Cloud Apps integration, review your Conditional Access Session Controls within Microsoft Entra Conditional Access and confirm which supported applications are routed through Defender for Cloud Apps.

Review the Compliant Network grant control and consider where requiring traffic through Global Secure Access strengthens your Conditional Access policies.

This week I have covered the complete Microsoft Global Secure Access architecture:

- Microsoft Traffic
- Microsoft Entra Private Access
- Microsoft Entra Internet Access
- How they work together with Conditional Access and Microsoft Defender for Cloud Apps

Next week I move into Microsoft Defender for Cloud, beginning with the relationship between Cloud Security Posture Management (CSPM) and Cloud Workload Protection (CWPP).

Identity without network controls leaves gaps.

Network controls without identity leave blind spots.

Zero Trust becomes much stronger when both operate together through a single policy model.

How closely does your organisation's network security integrate with its identity platform, and is Conditional Access already acting as the policy engine that brings them together?

---

## Microsoft Learn References

- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
- [Conditional Access app control — Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/proxy-intro-aad)
- [Compliant network check in Conditional Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-compliant-network)
- [Global Secure Access logs and monitoring](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-global-secure-access-logs-monitoring)
- [Universal Continuous Access Evaluation](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-universal-continuous-access-evaluation)

---

## Suggested Image Concept

A three-layer diagram showing Identity (Entra ID / Conditional Access) at the top, Network (Global Secure Access — Private Access, Internet Access, Microsoft traffic) in the middle, and Application (Defender for Cloud Apps session controls) at the bottom, with Conditional Access shown as the vertical thread connecting all three layers.

---

## Hashtags

#MicrosoftEntra #GlobalSecureAccess #ZeroTrust #ConditionalAccess #MicrosoftSecurity #DefenderForCloudApps

---

## Accuracy Notes (for future articles)

- Microsoft quote from draft removed — published uses "Microsoft positions... as a converged approach" (less prescriptive, avoids quoting a specific doc string that may change)
- "Universal Continuous Access Evaluation" title dropped from section heading — published uses "Continuous Access Evaluation (CAE)" — more cautious framing; avoids claiming simultaneous network revocation
- CAE framing: "can respond rapidly to significant events" rather than "can be revoked in near real time" — softer, avoids over-promising real-time enforcement specifics
- "Compliant Network Grant Control" — capitalisation used in published version (different from draft's "Compliant Network check")
- "Global Secure Access integrates with these identity signals so protected access can be re-evaluated" — deliberate hedge; doesn't claim token revocation happens simultaneously
- No specific portal navigation paths given in "Where to look today" — less prescriptive than draft
- Week summary uses bullet points; discussion question slightly rephrased from draft

---

## Week 8 Arc Summary (for content library)

- Day 53 (Mon): GSA overview — SSE, three traffic profiles, Universal Tenant Restrictions, Compliant Network, AI traffic visibility
- Day 54 (Tue): Entra Private Access — Quick Access migration bridge, Per-App Access destination, Private Network Connector, Kerberos SSO
- Day 55 (Wed): Entra Internet Access — identity-centric SWG, security profiles, Baseline security profile, threat intelligence, TLS inspection
- Day 56 (Thu): Integration — three layers (identity/network/application), CA as common policy layer, Compliant Network Grant Control, CAE, unified traffic logs, MDCA session controls
- Week 9: Defender for Cloud (Days 60–63)
