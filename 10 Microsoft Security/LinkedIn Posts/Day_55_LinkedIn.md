# Day 55 — LinkedIn Content Package
**Topic:** Microsoft Entra Internet Access — the identity-centric secure web gateway
**Category:** Network Security / Zero Trust
**Week theme:** The network access layer (Days 53–56)
**Date:** 2026-07-30
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Most organisations already have a web proxy or secure web gateway.
It knows the URL being requested.
It does not know who is requesting it.

**Hook 2:**
Web filtering is a solved problem. Every proxy vendor offers it. The question is not whether you can filter web traffic. It is whether your filtering policies know who is making the request and what they are authorised to do.

**Hook 3:**
Your web proxy has been blocking gambling and social media sites for years. It has one policy for everyone. The CEO gets the same filtering rules as the new contractor who joined yesterday. Microsoft Entra Internet Access is built around a different assumption.

---

## LinkedIn Article (published — 2026-07-30)

Microsoft Entra Internet Access, the identity-centric secure web gateway

Most organisations already have a web proxy or secure web gateway.

It knows the URL being requested.

It does not always know who is requesting it.

Microsoft Entra Internet Access is built on a different model. It is Microsoft's cloud-delivered Secure Web Gateway, and the difference is that every filtering decision is identity-aware.

This week I have been covering Microsoft Global Secure Access. On Monday I introduced the three traffic profiles. Yesterday I covered Microsoft Entra Private Access and replacing the VPN. Today I am looking at Microsoft Entra Internet Access, the internet and SaaS traffic layer.

What is Microsoft Entra Internet Access?

Microsoft Entra Internet Access is Microsoft's identity-centric Secure Web Gateway (SWG) for internet and SaaS traffic.

It is generally available and is managed through the Microsoft Entra admin centre.

Rather than relying on a standalone web proxy with its own user database and policy engine, Microsoft Entra Internet Access integrates directly with Microsoft Entra ID and Microsoft Global Secure Access. User identity, device compliance, sign-in risk, and Conditional Access can all contribute to decisions about internet access.

That integration is the core design difference from a traditional proxy.

How filtering works

The building blocks are web content filtering policies, security profiles, and Conditional Access.

A web content filtering policy defines what to block or allow, using web categories, fully qualified domain names (FQDNs), or URL destinations.

Those filtering policies are assigned to security profiles.

Security profiles are then associated with users and devices through Microsoft Entra Internet Access and Global Secure Access. Conditional Access provides identity context and may require traffic to pass through Global Secure Access before access is granted to supported applications.

This allows different users to receive different internet access policies based on identity, group membership, device compliance and other Microsoft Entra signals, without maintaining separate identity stores or policy engines.

The baseline security profile

One useful feature is the Baseline security profile.

The Baseline profile provides minimal protection to internet traffic routed through Microsoft Entra Internet Access, even if no custom security profiles have been assigned yet.

It provides a sensible starting point for organisations beginning their deployment by applying default protections before more granular policies are introduced.

From there, organisations can build additional security profiles for different user groups or business requirements.

Threat intelligence

Microsoft Entra Internet Access can block access to known malicious internet destinations using Microsoft's threat intelligence.

Threat intelligence policies automatically block connections to known malicious destinations without requiring administrators to maintain manual block lists.

This complements web content filtering rather than replacing it.

Threat intelligence blocks destinations known to be malicious.

Web content filtering controls access based on organisational policy and acceptable use.

Together they address different aspects of internet security.

TLS inspection

For encrypted HTTPS traffic, Microsoft Entra Internet Access can identify destinations using Server Name Indication (SNI) without decrypting traffic.

Where deeper inspection is required, organisations can enable TLS inspection.

TLS inspection allows the service to decrypt, inspect, and re-encrypt supported HTTPS traffic after a trusted certificate is deployed to managed devices.

This enables more granular inspection and policy enforcement than hostname-based filtering alone.

As with any TLS inspection deployment, organisations should consider privacy, regulatory and application compatibility requirements before enabling inspection broadly. Many cloud-based solutions now detect TLS inspection and treat it as a man-in-the-middle attack.

AI traffic visibility

Generative AI has quickly become one of the fastest-growing categories of internet traffic.

Microsoft Entra Internet Access can identify AI services using Microsoft's AI web categorisation capabilities.

This allows organisations to understand which AI services are being accessed and apply web content filtering policies consistently across those services.

Microsoft continues to expand AI-specific controls within Global Secure Access, with new capabilities introduced as the platform evolves.

Where to look today

Open the Microsoft Entra admin centre and navigate to:

Global Secure Access > Secure > Web content filtering policy

Version 2 of the policy configuration is now the default; if you notice it appears differently.

If you are starting your deployment, begin with the Baseline security profile to establish a minimum level of protection for all internet traffic routed through Microsoft Entra Internet Access.

From there, create additional security profiles and assign web filtering policies appropriate to different user groups.

Review the traffic logs to understand which web categories are accessed, which destinations are blocked, and which users and devices generate that traffic.

Traditional web filtering tells you what was blocked.

Microsoft Entra Internet Access tells you who was blocked, from which device, under which security policy, and alongside the same identity context used throughout Microsoft Entra.

This week I have covered the three layers of Microsoft Global Secure Access.

Tomorrow I will bring them together to look at how Microsoft Traffic, Microsoft Entra Private Access, and Microsoft Entra Internet Access work alongside Conditional Access and Microsoft Defender for Cloud Apps to deliver a consistent Zero Trust access model across identity, network, and applications.

What does your organisation currently use for internet traffic filtering, and have you explored how closely it integrates with your identity platform?

---

## Microsoft Learn References

- [Learn about Microsoft Entra Internet Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-internet-access)
- [How to configure Global Secure Access web content filtering](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering)
- [How to configure Global Secure Access threat intelligence](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-threat-intelligence)
- [Configure Transport Layer Security Inspection Policies](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-transport-layer-security)
- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)

---

## Suggested Image Concept

Microsoft Entra admin centre showing the Web content filtering policy configuration with a security profile linked to a Conditional Access policy — illustrating the identity-aware filtering model where policies are scoped to users and groups rather than applied universally.

---

## Three Alternative Discussion Questions

1. What does your organisation currently use for internet traffic filtering, and have you explored whether it integrates with your identity platform?
2. Does your current web gateway give you per-user visibility into what was blocked and why, or does it report at a network level without identity context?
3. Has your security team discussed how to govern access to AI tools and services at the network layer, separate from application-level controls?

---

## Hashtags

#MicrosoftEntra #GlobalSecureAccess #ZeroTrust #SecureWebGateway #MicrosoftSecurity #NetworkSecurity

---

## Accuracy Notes (for future articles)

- UDP/QUIC not supported in Internet Access (consistent with Day 54 — TCP only)
- Source traffic type filtering (Agent/Browser/Application/Unknown) = **Preview**
- HTTP method request filtering = **Preview** — requires TLS inspection for HTTPS
- Baseline security profile applies to all traffic even without a CA policy — useful deployment detail
- TLS inspection needed for full URL path visibility; SNI-only without it
- "Shadow AI discovery" term and "prompt injection protection" both avoided — per Day 53 published correction; "AI traffic visibility" framing used instead with cautious language about evolving capabilities
- Policy changes via CA can take up to 60–90 minutes to propagate; security profile config changes < 5 minutes
