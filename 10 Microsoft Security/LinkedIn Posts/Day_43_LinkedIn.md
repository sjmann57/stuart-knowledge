# Day 43 — LinkedIn Content Package
**Topic:** Microsoft Entra Workload ID — the credential problem nobody is managing
**Category:** Identity / Security
**Date:** 2026-07-16 (scheduled)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
There is a client secret in your tenant that expires in eleven days.
Nobody knows which application it belongs to. Nobody knows who created it. And nobody will know it expired until something breaks.

**Hook 2:**
Most organisations have a governance process for human identity credentials.
Access reviews, password policies, MFA enforcement. There is a plan.
For application credentials — client secrets, certificates, managed identities — the plan is usually to fix it after the outage.

**Hook 3:**
Your pipelines, your APIs, your integrations — they all authenticate to Azure using credentials.
The question is whether those credentials are managed, rotated, and monitored. Or whether they are sitting in a key vault that nobody opened since the project went live.

---

## LinkedIn Article (Stuart's version — published 2026-07-16)
**Note:** Key changes from draft: expanded app registration/service principal distinction (application object vs service principal per-tenant); added explicit "Microsoft's recommendation" framing for eliminating long-lived credentials; licensing nuance added — "Premium capabilities are not assigned directly to service principals, organisations should purchase licences to cover the workload identities that use Premium functionality" (removes "one licence unlocks all" oversimplification); Access Reviews licensing clarified as "Workload ID Premium plus Entra ID P2 or Entra ID Governance for reviewers"; close adjusted to "Human identities are governed because organisations have mature processes for users. Workload identities rarely receive the same attention, despite often having privileged access to production systems and data."; discussion question simplified to "Does your organisation have a documented owner for every production service principal?"

Microsoft Entra Workload ID: the credential problem nobody is managing
There is a client secret in your tenant that expires in eleven days.
Nobody knows which application it belongs to. Nobody knows who created it. And nobody will know it has expired until something breaks at an inconvenient moment.
This is not an unusual situation.
In almost every Microsoft Entra tenant I review, application credentials are the least-governed part of the identity estate.
Two weeks ago I wrote about overprovisioned permissions on workload identities, where CIEM in Microsoft Defender for Cloud surfaces the access that service principals and managed identities have accumulated over time.
The credential side of the problem is separate and just as common.
What are workload identities?
Workload identities are the non-human identities in your Microsoft Entra tenant.
They include application registrations, service principals, and managed identities.
An application registration creates an application object in Microsoft Entra ID. That application can then be represented by a service principal within a tenant, and the service principal is the identity that authenticates and receives permissions or role assignments.
Managed identities are a different type of workload identity. They are created and managed automatically by Azure, scoped to a specific Azure resource such as a virtual machine, App Service, Function App or Logic App, and they eliminate the need for you to create or manage credentials.
The credential problem sits primarily with application registrations.
Client secrets and the outage you have not had yet
A client secret is a shared secret that an application presents to Microsoft Entra ID when requesting an access token.
Client secrets are convenient.
They are also the source of a predictable set of problems.
Secrets get created for a deployment and then forgotten.
They get hardcoded into configuration files, CI/CD pipelines, or application settings where they accumulate.
They have expiry dates that nobody is monitoring.
When they expire, they cause outages.
When they are compromised through an exposed repository, leaked configuration, or poor credential management, they are often not discovered until an audit or security incident.
Certificates are more secure than client secrets, but they introduce their own operational burden: certificate renewal, private key protection, rotation schedules, and lifecycle management, all of which can easily be overlooked.
Microsoft's recommendation, wherever the scenario supports it, is to eliminate long-lived credentials altogether.
The modern alternative: Workload Identity Federation
Workload Identity Federation removes the need to store credentials for supported scenarios.
Instead of creating a client secret or certificate, you configure a federated identity credential on an application registration.
The workload, for example, a GitHub Actions workflow, an Azure DevOps pipeline, or a Kubernetes workload, authenticates using a short-lived token issued by its own trusted identity provider.
Microsoft Entra ID validates that token and exchanges it for a Microsoft Entra access token.
The result is that there is no client secret or certificate to expire, leak, rotate, or forget in a configuration file.
GitHub Actions is the implementation I see most often.
Rather than storing a service principal secret as a GitHub repository secret, you configure OpenID Connect federation. GitHub presents a short-lived token to Microsoft Entra ID, which then issues an access token to the workflow. No Azure credential is stored in GitHub.
Azure DevOps service connections also support Workload Identity Federation, allowing Azure authentication without storing service principal secrets.
Where client secrets cannot yet be replaced, for example with older applications, third-party integrations, or software that does not support OpenID Connect, the focus shifts to governance: monitoring expiry dates, enforcing shorter lifetimes, and treating application credentials with the same discipline as privileged human credentials.
What Microsoft Entra Workload ID Premium adds
Microsoft Entra Workload ID includes Free and Premium capabilities.
The Free capability includes application registrations, service principal management, managed identities, and Workload Identity Federation. It is available with Microsoft Entra tenants.
The Premium capability adds governance and security features that become increasingly valuable as the number of workload identities grows.
Unlike user licences, Premium capabilities are not assigned directly to service principals. Organisations should purchase licences to cover the workload identities that use Premium functionality.
Three capabilities stand out in practice.
Conditional Access for workload identities allows policies to target service principals rather than users. You can restrict authentication to trusted named network locations or approved public IP address ranges, reducing the opportunity for a compromised workload identity to authenticate from unexpected locations.
Identity Protection for workload identities analyses authentication behaviour for service principals and detects suspicious sign-in activity and anomalous authentication patterns. These detections help identify compromised workload identities that may otherwise go unnoticed.
Access Reviews allow periodic review of privileged service principal assignments. This requires Microsoft Entra Workload ID Premium, along with Microsoft Entra ID P2 or Microsoft Entra ID Governance, for the reviewers conducting the reviews.
Where to look today
Open the Microsoft Entra admin centre and navigate to:
Identity > Applications > App registrations
Review the Certificates & secrets page for applications that still use client secrets.
Look at the expiry dates.
Any secret approaching expiry without a documented owner represents both an operational and security risk.
Then look at how old those secrets are.
A client secret that has existed for two or three years without rotation is often a sign that the application has not been reviewed since it was first deployed.
For any CI/CD pipeline still using a service principal secret, Workload Identity Federation should be your first migration target.
GitHub Actions and Azure DevOps both provide well-documented migration paths.
If your organisation has Microsoft Entra Workload ID Premium, review the sign-in logs for high-value service principals.
Look for authentication from unexpected IP ranges or unusual authentication patterns.
That is often where the first evidence of a compromised application credential appears.
Human identities are governed because organisations have mature processes for users.
Workload identities rarely receive the same attention, despite often having privileged access to production systems and data.
Does your organisation have a documented owner for every production service principal?
#MicrosoftEntra #WorkloadIdentity #IdentitySecurity #MicrosoftSecurity #ZeroTrust

---

## Microsoft Learn References

- [Workload Identity Federation](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation)
- [Workload identities overview](https://learn.microsoft.com/en-us/entra/workload-id/workload-identities-overview)
- [Workload Identities Premium FAQ](https://learn.microsoft.com/en-us/entra/workload-id/workload-identities-faqs)
- [Securing workload identities with Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/concept-workload-identity-risk)
- [Conditional Access for workload identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/workload-identity)
- [Migrate applications away from secret-based authentication](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/migrate-applications-from-secrets)
- [Add and manage app credentials in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials)

---

## Suggested Image Concept

Microsoft Entra admin centre showing the App registrations blade with the Certificates & secrets tab open, displaying a mix of expired and near-expiry client secrets with no clear owner. Demonstrates the practical credential hygiene problem rather than a clean "everything is configured correctly" screenshot.

---

## Three Alternative Discussion Questions

1. Does your organisation have a documented owner for each service principal with production access, and when were the credentials on those app registrations last reviewed?
2. Has your team migrated any CI/CD pipelines from service principal secrets to Workload Identity Federation, and what drove the decision to prioritise it?
3. Client secrets, certificates, or Workload Identity Federation — which credential type is most common in your environment for pipeline authentication, and is that the result of a conscious decision or just how it evolved?

---

## Hashtags

#MicrosoftEntra #WorkloadIdentity #IdentitySecurity #MicrosoftSecurity #ZeroTrust
