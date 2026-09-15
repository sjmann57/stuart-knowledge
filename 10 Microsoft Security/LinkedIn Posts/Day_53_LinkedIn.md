# Day 53 — LinkedIn Content Package
**Topic:** Microsoft Global Secure Access — Microsoft's Security Service Edge solution
**Category:** Network Security / Zero Trust
**Week theme:** The network access layer (Days 53–56)
**Date:** 2026-07-28
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Remote access via VPN was designed for a world where your applications lived in a data centre and your users sat in an office.
Neither of those things is consistently true anymore.

**Hook 2:**
Your VPN grants access to the network. Once connected, users can reach any resource on that network segment. Security controls happen at the edge. Inside, movement is relatively unconstrained.
That is not how Zero Trust is supposed to work.

**Hook 3:**
Most organisations I review have built half a Zero Trust architecture. The identity layer is well developed. Conditional Access is in place. MFA is enforced.
The network access layer is still a VPN from 2015.

---

## LinkedIn Article (published — 2026-07-28)

Microsoft Global Secure Access, moving beyond the VPN

Remote access via VPN was designed for a world where your applications lived in a data centre, and your users sat in an office.

Neither of those things is consistently true anymore.

Applications are in Microsoft 365, Azure, third-party SaaS, and on-premises systems that have not yet moved. Users connect from home, cafes, train clients' client sites, mobile devices on public networks, and occasionally from an office. The network perimeter that VPN was built to protect either no longer exists or no longer encompasses the resources users actually need.

This is the problem Microsoft's Security Service Edge (SSE) solution is designed to address.

That solution is called Microsoft Global Secure Access.

What is Security Service Edge?

Security Service Edge (SSE) is the network security component of a Zero Trust architecture. Rather than securing access at a fixed network perimeter, SSE follows the user and device, applying access controls based on identity, device state, location and risk, regardless of where the user is or which network they are connected to.

Microsoft Global Secure Access is Microsoft's SSE solution. It is managed through the Microsoft Entra admin centre and brings together two products:

* Microsoft Entra Private Access, which provides Zero Trust Network Access (ZTNA) to private corporate resources.
* Microsoft Entra Internet Access provides secure access to the internet and SaaS applications through Microsoft's cloud-delivered secure web gateway.

Both services are generally available.

Three traffic profiles

Global Secure Access manages traffic through three forwarding profiles, each covering a different type of network traffic.

Microsoft traffic profile

The Microsoft traffic profile routes Microsoft 365 and other Microsoft service traffic across Microsoft's global network.

Rather than sending Microsoft 365 traffic through a corporate VPN or proxy before returning to Microsoft's services, traffic follows Microsoft's optimised network path from the user's device.

Organisations with Microsoft Entra ID P1 or P2 can enable the Microsoft traffic profile without purchasing Microsoft Entra Internet Access or Microsoft Entra Private Access licences. For many organisations, this is the logical first step when adopting Global Secure Access.

Private Access traffic profile

The Private Access traffic profile provides Zero Trust Network Access to private applications running on-premises, in Azure or in other cloud environments.

Instead of connecting users to an entire network through a VPN, users are granted access only to the specific applications they are authorised to use. Microsoft Entra Conditional Access policies continue to enforce identity, device compliance and authentication requirements before access is granted.

I will cover Microsoft Entra Private Access in more detail in a future article.

Internet Access traffic profile

The Internet Access traffic profile routes internet traffic through Microsoft's cloud-delivered secure web gateway.

It applies web filtering, threat protection and internet access policies while working alongside Microsoft Entra Conditional Access for supported identity-aware applications.

We will look at Microsoft Entra Internet Access in more detail in another article.

NOTE: The Private Access and Internet Access traffic profiles require either standalone Microsoft Entra Private Access or Microsoft Entra Internet Access licences, or Microsoft Entra Suite. Microsoft Entra ID P1 or P2 is also required.

What makes it different from a traditional proxy or VPN?

Traditional VPNs and proxies make decisions primarily based on IP addresses, ports, and network rules.

They have little understanding of who the user is, the user's current sign-in risk, or whether the user's device complies with your security policies.

Global Secure Access integrates directly with Microsoft Entra ID and Conditional Access.

That means the same Conditional Access policies you already use for applications, requiring compliant devices, enforcing authentication strength or responding to sign-in risk, can also influence how network access is granted.

Two capabilities demonstrate this particularly well.

Universal Tenant Restrictions

Universal Tenant Restrictions prevent managed users from authenticating to external Microsoft Entra tenants or personal Microsoft accounts through the managed network.

For example, a user cannot simply sign in to a personal OneDrive account or another organisation's Microsoft 365 tenant from a managed device if your organisation's policy blocks that behaviour.

Compliant Network

Compliant Network is a Conditional Access signal that verifies that traffic flows through Global Secure Access before access is granted.

This gives organisations a trusted network signal directly within Conditional Access, something that traditionally required third-party network access control solutions.

AI traffic visibility

As organisations adopt generative AI services, visibility becomes increasingly important.

Microsoft Entra Internet Access can identify AI applications being accessed across your organisation using Microsoft's AI web categorisation capabilities. This helps security teams understand which AI services are in use, even if they have never been formally approved.

Microsoft continues to expand AI-aware security controls within Internet Access, including capabilities designed to help inspect and govern interactions with supported AI services as these features become generally available.

Where to look today

Open the Microsoft Entra admin centre and navigate to Global Secure Access.

If your organisation has Microsoft Entra ID P1 or P2, consider enabling the Microsoft traffic profile as a first step. It provides Microsoft 365 traffic optimisation, richer traffic visibility, and features such as Universal Tenant Restrictions.

Review the dashboards and traffic reports to understand how users, devices, and applications communicate through your environment.

For many organisations, this is the first time network activity has been viewed alongside identity context.

VPN solved the right problem for the era in which it was built.

For many organisations, that is no longer the primary access model.

Access decisions increasingly need to follow the identity, device, and application rather than the corporate network.

This week I am covering each layer of Global Secure Access in more detail:

* Tomorrow: Microsoft Entra Private Access and VPN replacement.
* Wednesday: Microsoft Entra Internet Access and Microsoft's secure web gateway.
* Thursday: How Global Secure Access integrates with Conditional Access and Defender for Cloud Apps to deliver consistent Zero Trust access policies.

Does your organisation still rely primarily on VPN for remote access, or has Zero Trust Network Access become part of your roadmap?

---

## Microsoft Learn References

- [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access)
- [Global Secure Access traffic forwarding profiles](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-traffic-forwarding)
- [Learn about Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-private-access)
- [Universal Tenant Restrictions](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-universal-tenant-restrictions)
- [Compliant Network check in Conditional Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-compliant-network)
- [Shadow AI discovery](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-shadow-ai-discovery)
- [Quickstart: Access the Global Secure Access area of the Microsoft Entra admin centre](https://learn.microsoft.com/en-us/entra/global-secure-access/quickstart-access-admin-center)

---

## Suggested Image Concept

Microsoft Entra admin centre showing the Global Secure Access dashboard with the three traffic forwarding profiles (Microsoft traffic, Private Access, Internet Access) and the traffic logs panel, illustrating the unified view across all three network layers.

---

## Three Alternative Discussion Questions

1. Does your organisation's remote access model still rely primarily on VPN, and if so, has Zero Trust Network Access been on your roadmap?
2. Has your organisation activated the Microsoft traffic forwarding profile in Global Secure Access, and if so, what was the first thing you noticed in the traffic logs?
3. Are you aware of which AI tools your users are accessing through your network, and would a Shadow AI discovery report change any decisions your security team would make?

---

## Hashtags

#MicrosoftEntra #GlobalSecureAccess #ZeroTrust #SecurityServiceEdge #MicrosoftSecurity
