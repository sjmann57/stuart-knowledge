# Day 54 — LinkedIn Content Package
**Topic:** Microsoft Entra Private Access — replacing the VPN with Zero Trust
**Category:** Network Security / Zero Trust
**Week theme:** The network access layer (Days 53–56)
**Date:** 2026-07-29
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
VPN grants access to the network.
Once connected, a user can typically reach anything on that network segment.
That is not application access. That is network access with an authentication step in front of it.

**Hook 2:**
The problem with VPN is not that it stops working. It is what happens when it does work: users get network connectivity, not application access. The difference matters more than most organisations realise.

**Hook 3:**
Most VPN replacement projects I have seen fail for the same reason. The team cannot answer one question: which users need to reach which specific resources? The answer was never required before, because VPN gave everyone access to everything.

---

## LinkedIn Article (published — 2026-07-29)

Microsoft Entra Private Access, replacing the VPN with Zero Trust

VPN grants access to the network.

Once connected, a user can typically reach anything on that network segment.

That is not application access.

That is network access with an authentication step in front of it.

Microsoft Entra Private Access is designed to change that model.

Yesterday I introduced Microsoft Global Secure Access and its three traffic profiles.

Today I want to go deeper into Microsoft Entra Private Access because this is where most organisations will spend the most time during a Zero Trust migration.

What is Microsoft Entra Private Access?

Microsoft Entra Private Access is Microsoft's Zero Trust Network Access (ZTNA) solution.

Rather than connecting users to an entire network, it connects them only to the private applications and resources they are authorised to use.

The same Microsoft Entra Conditional Access policies you already use for Microsoft 365 and SaaS applications can also protect access to on-premises applications, Azure-hosted workloads and other private resources.

Microsoft Entra Private Access is generally available and is managed through the Microsoft Entra admin centre.

How the Private Network Connector works

Microsoft Entra Private Access does not require inbound firewall ports to be opened.

Instead, you deploy the Microsoft Entra Private Network Connector on a Windows Server inside your network.

The connector establishes outbound connections to the Microsoft Global Secure Access service.

When a user connects to a private application, traffic flows from the user's device through the Global Secure Access client, across Microsoft's Security Service Edge, through the Private Network Connector and finally to the internal application.

Connectors can be organised into connector groups that provide high availability and load balancing.

Microsoft recommends deploying multiple connectors within each connector group so connectivity continues if one connector becomes unavailable.

For users, the Global Secure Access client establishes the connection automatically.

If the deployment has been configured correctly, users open the application without manually starting a VPN connection.

Two ways to publish applications

There are two approaches to publishing private resources, and understanding the difference matters.

Quick Access

Quick Access is designed as the fastest way to begin moving away from a traditional VPN.

You publish private resources using IP address ranges, fully qualified domain names (FQDNs), or combinations of both, allowing users to continue accessing resources in much the same way they always have.

Microsoft describes Quick Access as a migration capability rather than the long-term destination.

One of its most useful capabilities is Application Discovery, which shows the private applications and resources users are actually accessing.

For many organisations, this becomes the first accurate inventory of applications still in use across the business.

Per-App Access

Per-App Access is where most organisations ultimately want to end up.

Instead of granting access to broad network ranges, individual private applications are published as Enterprise Applications with their own Conditional Access policies.

A developer accessing a source code repository can have different authentication requirements from a finance user accessing an internal payroll system, even though both applications sit on the same internal network.

That is the capability traditional VPNs cannot provide.

VPN secures a network connection.

Per-App Access secures individual applications.

Microsoft Entra Private Access supports a broad range of TCP-based private applications, making it suitable for far more than traditional web applications.

Kerberos single sign-on

One question always comes up during VPN replacement projects.

How do users continue accessing on-premises applications without repeatedly entering passwords?

Microsoft Entra Private Access supports Kerberos single sign-on for supported on-premises applications.

When correctly configured, users on Microsoft Entra-joined Windows devices can continue to access Kerberos-based applications without additional authentication prompts.

For organisations using Windows Hello for Business, Hybrid Cloud Kerberos Trust enables passwordless authentication while maintaining access to supported on-premises resources.

Getting Kerberos single sign-on working requires planning for DNS, Active Directory connectivity, and authentication configuration, but Microsoft provides detailed implementation guidance, and the capability is fully supported.

Where to look today

Open the Microsoft Entra admin centre and navigate to:

Global Secure Access > Applications

If you are beginning a VPN replacement project, Quick Access is usually the right place to start.

Publish your existing private resources, assign a pilot group and use Application Discovery to understand exactly which applications users are accessing.

Once you understand those traffic patterns, begin moving high-value applications to Per-App Access with application-specific Conditional Access policies.

Both approaches can operate side by side throughout the migration.

The Microsoft Entra Private Network Connector is straightforward to deploy and requires only outbound connectivity to Microsoft's Global Secure Access service.

The biggest challenge I see during VPN replacement projects is rarely the technology.

It is understanding which users genuinely need access to which applications.

Private Access forces that conversation.

That can be uncomfortable at first.

It is also one of the biggest security improvements many organisations make because least-privilege access starts with understanding what access is actually required.

Yesterday I covered Microsoft Global Secure Access and its three traffic profiles.

Tomorrow I will look at Microsoft Entra Internet Access and Microsoft's secure web gateway.

If you have been involved in a VPN replacement project, what was the hardest part of the transition?

---

## Microsoft Learn References

- [Learn about Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-private-access)
- [Microsoft Entra private network connectors](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-connectors)
- [Tutorial: VPN replacement with Quick Access](https://learn.microsoft.com/en-us/entra/global-secure-access/tutorial-private-access-vpn-replacement)
- [Use Kerberos for single sign-on (SSO) with Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-kerberos-sso)
- [How to configure Quick Access for Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-quick-access)

---

## Suggested Image Concept

Microsoft Entra admin centre showing the Quick Access configuration with IP ranges and private DNS suffixes, alongside the Application Discovery report showing traffic to internal resources — illustrating both the migration starting point and the visibility Private Access provides.

---

## Three Alternative Discussion Questions

1. If you have been involved in a VPN replacement project, what was the hardest part of the transition?
2. Does your organisation have a complete inventory of which users need access to which internal applications, or did VPN make that question unnecessary?
3. Have you looked at the Application Discovery report in Global Secure Access — and were there resources in the traffic logs that surprised you?

---

## Hashtags

#MicrosoftEntra #GlobalSecureAccess #ZeroTrust #ZTNA #MicrosoftSecurity #NetworkSecurity
