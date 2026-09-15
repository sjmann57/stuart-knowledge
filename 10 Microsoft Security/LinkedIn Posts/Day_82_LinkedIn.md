# Day 82 — LinkedIn Content Package
**Topic:** What's new in Microsoft Entra — passkeys by default, Tenant Governance, and Backup and Recovery
**Category:** Identity Security / Microsoft Entra ID
**Week theme:** What's new in Microsoft Security (Days 81–84)
**Date:** 2026-08-25 (Tuesday)
**Format:** Technical article — Week 12 Day 2
**LinkedIn URL:** pending

---

## LinkedIn Article (published — 2026-08-25)

What's new in Microsoft Entra: passkeys by default, Tenant Governance, and Backup and Recovery

Yesterday I looked at how Microsoft Sentinel is changing.

Today it is Microsoft Entra, where three additions are worth understanding: two have dates you need to know, and one addresses a gap that has worried identity teams for years.

Passkeys are becoming the default.

This is the big one, and it has firm dates. There are many great articles that you may also want to look up about passkeys.

Microsoft Entra ID is making passkeys the default authentication experience.

Microsoft's reasoning is stated plainly in the documentation: to help enterprises adopt AI at scale, users need to move from phishable authentication methods towards phishing-resistant authentication methods such as passkeys.

Microsoft no longer positions SMS and voice as secure authentication methods, and it is retiring Microsoft-provided SMS and voice authentication from Entra ID.

The timeline matters.

1 September 2026

From 1 September 2026, users who are enabled for SMS or voice in the Entra Authentication Methods Policy or legacy MFA settings will automatically be enabled for passkeys.

Microsoft will also set the Registration Campaign to Microsoft Managed for these users.

When those users next sign in and complete MFA, eligible users will be guided to register a passkey.

By default, users can snooze that registration prompt.

A temporary opt-out is also available for the automatic September migration if your organisation needs more time.

But that only buys you time until February.

1 February 2027

From 1 February 2027, Microsoft-provided SMS and voice delivery will be retired in Microsoft Entra ID.

If you haven't configured a customer-managed telecom provider, users will no longer be able to use Microsoft's SMS or voice service for MFA.

After that date, users whose only available MFA method is SMS or voice will be required to register a passkey during sign-in before they can continue accessing their account.

That prompt is blocking.

And Microsoft is explicit (for now):

There is no opt-out from the February behaviour.

If your organisation has a genuine business, regulatory or operational requirement to retain SMS or voice authentication, Microsoft is providing the option to use a customer-managed telecom provider through the Microsoft Security Store.

Microsoft still recommends moving users to passkeys wherever possible.

Synced passkeys

There is good news alongside this.

Microsoft Entra now supports synced passkeys, alongside device-bound passkeys.

A synced passkey is stored through a passkey provider such as:

* Apple iCloud Keychain
* Google Password Manager
* Supported third-party passkey providers

The encrypted credential can then synchronise across the user's devices through that provider.

Microsoft distinguishes between two broad passkey models.

Synced passkeys provide convenience and easier recovery for most users.

Device-bound passkeys, such as FIDO2 security keys and passkeys in Microsoft Authenticator, keep the credential tied to a specific authenticator or device.

Microsoft recommends considering device-bound passkeys for administrators, highly privileged users and scenarios requiring tighter device control.

Other phishing-resistant Microsoft authentication methods, including Windows Hello for Business and certificate-based authentication, remain important parts of the wider authentication strategy.

So this isn't simply about replacing SMS with another MFA prompt.

It is about moving users away from phishable authentication.

What I would do now

Find out who in your tenant still relies on SMS or voice.

Microsoft provides a PowerShell script specifically to identify those users.

Then plan the migration rather than waiting for Microsoft to do it for you.

Enable passkeys.

Pilot them.

Run the registration campaign.

Communicate with your users.

Deal with exceptions.

And work out what you are going to do with privileged users.

The September change is automatic unless you temporarily opt out.

The February deadline isn't.

Tenant Governance

The second addition addresses a problem most large organisations have and few can see clearly:

Tenant sprawl.

Mergers.

Acquisitions.

Test environments.

Business units doing their own thing.

And user-created shadow IT tenants.

Microsoft's own documentation acknowledges that many organisations have tenants that central IT doesn't administer and sometimes doesn't even know exist.

Each of those relationships can introduce security and compliance risk.

Microsoft Entra Tenant Governance lets organisations identify related tenants, establish governance relationships, centrally administer governed tenants, and monitor configuration.

Two parts stand out for me.

Related tenants

Related tenants help identify other tenants connected to yours using discovery signals.

Microsoft currently documents three main signals.

B2B relationships identify inbound and outbound B2B access, registration and administrative relationships.

Multitenant applications identify tenants with multitenant applications that have permissions in your tenant, or tenants that your multitenant applications can access.

Billing relationships identify tenants sharing billing accounts.

That last one could surface tenants that security teams did not realise existed.

There is an important distinction, though.

A related tenant does not mean you own or control that tenant.

It means Microsoft has identified evidence of a relationship between the tenants.

You then need to understand what that relationship is and decide if any governance action is required.

Cross-tenant delegated administration

The other capability I would pay attention to is cross-tenant delegated administration.

It uses Granular Delegated Admin Privileges (GDAP) technology.

Administrators in a governing tenant can manage governed tenants using credentials from their home tenant.

They don't need a local administrator account or B2B guest account in every governed tenant.

Roles and permissions are defined through governance relationships and governance policy templates, allowing you to apply least-privilege administrative access across tenant boundaries.

For an organisation with multiple Microsoft Entra tenants, that could make administration considerably easier to control.

Rather than asking:

"Who has an admin account in that tenant?"

you can start asking:

"Who has delegated access from our governing tenant, and why?"

That is a much better governance conversation.

Tenant Governance licensing

There is some nuance around licensing.

Microsoft describes Tenant Governance as having Basic and Premium service levels, but individual capabilities map to different Entra licences.

For example:

* Secure creation of new governed tenants has capabilities available with Microsoft Entra Free.
* Cross-tenant delegated administration is available with Entra ID P1, P2 or Entra ID Governance for the administrators configuring governance relationships.
* Related tenant discovery requires Microsoft Entra ID Governance.
* Premium configuration-management capacity is provided through Microsoft Entra ID Governance licensing.

So don't assume that because you can see Tenant Governance, every capability is included in your existing licence.

Check the feature you actually intend to use.

Backup and Recovery

The third addition is the one I suspect will get the quiet nods from anyone who has lived through a bad identity change.

Microsoft Entra Backup and Recovery is currently in public preview.

It is a built-in service designed to help restore supported Microsoft Entra directory objects to a previously known good state after accidental changes or security compromise.

And importantly:

It is always on by default.

Microsoft automatically backs up supported directory objects.

Current supported objects include:

* Users
* Groups
* Applications
* Service principals
* Conditional Access policies
* Named locations
* Authentication method policy
* Authorisation policy
* OAuth2 permission grants
* App role assignments

Agent identities associated with supported user, application or service principal objects are also supported.

How the backups work

Microsoft automatically creates one backup each day.

Each backup is retained for up to seven days.

The backups cannot be modified or deleted.

Microsoft Entra ID P1 or P2 is currently a prerequisite for using Backup and Recovery.

That design matters.

The backup itself isn't another object sitting in the tenant that an administrator can edit or delete after compromising an account.

That's exactly the type of scenario identity recovery needs to consider.

Recovery

The workflow also gives you a useful safety step before making changes.

You can select a backup and create a difference report comparing the backed-up state with the current state.

That lets you see what changed before starting recovery.

You can scope that comparison to all supported objects, an object type, or specific object IDs.

Then you can recover from the selected backup or difference report.

Microsoft has also introduced two specific roles:

Microsoft Entra Backup Reader: for viewing backup information and difference reports.

Microsoft Entra Backup Administrator: for creating difference reports and running recovery operations.

Global Administrator also carries the required permissions, but the dedicated roles give you a much better least-privilege option.

The caveats

There are a few.

First:

It is in preview.

I would test it and understand exactly what it recovers before treating it as part of a production recovery strategy.

Second, Backup and Recovery supports specific object types and, for those objects, only supported properties and relationships.

It isn't a complete image of everything in Microsoft Entra.

Third:

Hard-deleted objects cannot be recovered.

Microsoft Entra Backup and Recovery can work with supported objects that have been modified, created or soft-deleted since the selected backup.

Once an object is hard deleted, it is permanently removed, and Backup and Recovery cannot bring it back.

And for hybrid identity, this doesn't remove the need to think about the systems that remain authoritative elsewhere.

If an identity or attribute is still mastered in on-premises Active Directory, Entra Backup and Recovery isn't a replacement for your broader identity recovery strategy.

The thread running through all three

These are not three unrelated features.

Passkeys by default are about moving users away from phishable authentication.

Tenant Governance is about understanding and governing the Microsoft Entra tenant estate you actually have, not simply the one you think you have.

Backup and Recovery is about accepting that mistakes and compromises happen and having a way to return supported identity configuration to a known-good state.

It comes back to the same principles I wrote about last week.

Verify explicitly.

Use least privilege.

Assume breach.

But there is another one I would add from an architect's point of view:

Know what you actually have.

Because you cannot protect an identity, tenant or configuration you don't know exists.

Which of these lands hardest for you: the passkey deadline, tenant sprawl, or finally having a Microsoft-native way to roll back supported Entra configuration after a bad change?

---

## Microsoft Learn References

- [Passkeys by default and retirement of Microsoft-provided SMS and voice authentication](https://learn.microsoft.com/entra/identity/authentication/concept-sms-voice-retirement)
- [What is Microsoft Entra Tenant Governance?](https://learn.microsoft.com/entra/id-governance/tenant-governance/overview)
- [Microsoft Entra Backup and Recovery overview (Preview)](https://learn.microsoft.com/entra/backup/overview)
- [Microsoft Entra releases and announcements (What's new)](https://learn.microsoft.com/entra/fundamentals/whats-new)
- [Microsoft Entra authentication overview — phishing-resistant methods](https://learn.microsoft.com/entra/identity/authentication/overview-authentication)

---

## Hashtags

#MicrosoftEntra #IdentitySecurity #Passkeys #PhishingResistant #TenantGovernance #EntraID #Cybersecurity #MicrosoftSecurity

---

## Accuracy Notes

- **Passkeys default date: 1 September 2026** — confirmed. Auto-enabled for SMS/voice users; registration campaign nudges. Verbatim reasoning "to adopt AI at scale... phishing-resistant."
- **SMS/voice native retirement: 1 February 2027** — confirmed. Blocking passkey registration prompt after this date; explicitly "no opt out."
- **Customer-managed telecom via Security Store:** info from 18 September 2026, configure from 30 October 2026 — confirmed dates.
- **Synced passkeys GA (March 2026)** — confirmed. Device-bound + synced; profiles support both.
- **Phishing-resistant methods list:** Windows Hello for Business, Platform Credential for macOS, synced passkeys, FIDO2 security keys, passkeys in Authenticator, CBA — confirmed.
- **PowerShell script to find SMS/voice users** — confirmed (entra-sms-voice-usage-analyzer). Roles: Global Reader / Auth Policy Admin / Security Reader.
- **Tenant Governance:** Related tenants (B2B, multitenant app, billing signals), cross-tenant delegated admin via GDAP, governance policy templates, secure tenant creation. Free/basic/premium licensing — all confirmed.
- **Backup and Recovery: PREVIEW** — confirmed (public preview March 2026). Always on, daily backup, 7-day retention with P1/P2 (updated from 5 days per June 2026 note — used 7). Covered objects list verbatim incl. Agent IDs, CA policies, named locations. Backups cannot be disabled/deleted by any user incl. Global Admin. Roles: Entra Backup Reader / Entra Backup Administrator. Workforce tenants only; no External ID/B2C; no hard-deleted objects.
- **All GA/preview statuses verified this session (Aug 2026).** Backup and Recovery still preview — re-check before publishing. Confirm the 7-day retention figure hasn't changed again.
- Metrics check due: 2026-09-25
