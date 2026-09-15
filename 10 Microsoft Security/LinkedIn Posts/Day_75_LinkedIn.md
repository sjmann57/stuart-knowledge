# Day 75 — LinkedIn Content Package
**Topic:** Microsoft Zero Trust Assessment — testing your tenant against hundreds of security configuration checks
**Category:** Zero Trust / Microsoft Security / Security Assessment
**Week theme:** Zero Trust — principles, assessment, identity, and adoption (Days 74–77)
**Date:** 2026-08-18 (Tuesday) — SCHEDULED
**Format:** Technical article
**LinkedIn URL:** https://www.linkedin.com/pulse/microsoft-zero-trust-assessment-testing-your-tenant-against-mann-lwjde

---

## Three Alternative Hooks

**Hook 1 (used in draft):**
There is a free tool that tests your Microsoft tenant against hundreds of security configuration checks, produces a report showing where you align with best practice and where you do not, and gives you prioritised remediation steps.

Many organisations have never run it.

**Hook 2:**
Most security reviews start with a spreadsheet and a list of questions.

The Microsoft Zero Trust Assessment starts with PowerShell and your actual tenant configuration.

The difference is significant.

**Hook 3:**
It is one thing to know the Zero Trust framework.

It is another to know where your tenant currently sits within it.

The Microsoft Zero Trust Assessment closes that gap.

---

## LinkedIn Article (draft — for Stuart's review)

Microsoft Zero Trust Assessment: testing your tenant against hundreds of security configuration checks

There is a free tool that tests your Microsoft tenant against hundreds of security configuration checks, produces a report showing where you align with best practice and where you do not, and gives you prioritised remediation steps.

Many organisations have never run it.

The Microsoft Zero Trust Assessment is an open-source PowerShell module, published by Microsoft on GitHub. It reads your actual tenant configuration, tests it against checks grounded in Zero Trust principles, the Secure Future Initiative, and external frameworks including NIST, CISA, and CIS, and produces an HTML report you can use to understand your current baseline and prioritise what to address first.

It does not make any changes to your environment.

Everything it does is read-only.

What it checks

The assessment tests across seven Zero Trust pillars: identity, devices, network, data, infrastructure, security operations, and AI.

The AI pillar is a recent addition. For those who followed last week's series on Microsoft Agent 365, the assessment now tests your posture against AI-specific Zero Trust controls — which makes it a natural follow-on to the work of understanding what agent governance controls you have in place.

For each pillar, the assessment runs a series of checks against your tenant configuration. Each check has a risk level and a result status. The results tell you what was tested, what was found, and what remediation actions are recommended.

The sources behind those checks include Microsoft's own internal security baselines and real-world deployment insights, alongside NIST, CISA, and CIS guidance. The code is public and can be reviewed at github.com/microsoft/zerotrustassessment.

That transparency matters. You can see exactly what the tool is testing and why.

What you need before you run it

The assessment requires PowerShell 7.

For the first run, you need a Global Administrator account. This is to provide consent for the permissions the Microsoft Graph PowerShell module requests. After the initial consent, subsequent runs can be performed with a combination of Global Reader, Security Reader, Exchange Administrator, and SharePoint Administrator roles.

If your organisation does not use Microsoft Azure, the assessment can still run. The Azure sign-in checks for audit and sign-in log export configuration. If you close the Azure sign-in window without signing in, the assessment skips the checks that depend on it and continues with the rest.

The permissions the tool requests through Microsoft Graph cover areas including audit logs, device management, directory information, Conditional Access policies, identity risk events, entitlement management, and privileged access. You can review the full permissions list in the get-started documentation and in the open-source code before running.

How to run it

Open PowerShell 7 and install the module:

Install-Module ZeroTrustAssessment -Scope CurrentUser

Then connect to the required services:

Connect-ZtAssessment

This opens sign-in prompts for Microsoft Graph, Microsoft Azure, Microsoft Exchange, Microsoft SharePoint, and Azure Information Protection. Sign in to each with the appropriate account.

Then run the assessment:

Invoke-ZtAssessment

The assessment saves its output to a folder called ZeroTrustReport in your current working directory, as an HTML file called ZeroTrustAssessmentReport.html. When the run completes, the report opens automatically in your default browser.

One practical note on timing: for large tenants, the assessment can take more than 24 hours to complete. If you start it, leave it running. Stopping it mid-run means starting again.

Reading the output

The report opens to a revamped Overview tab that gives you a high-level view of your tenant's Zero Trust posture across all seven pillars.

The Identity, Devices, Network, Data, Infrastructure, Security Operations, and AI tabs then show the individual check results, each with a risk level and a status.

Select any individual result and the report shows you what was tested, what was found, and the specific remediation actions recommended.

That combination of current state and recommended action is what makes the tool useful in practice. It is not just a score. It gives you the information you need to prioritise what to address first.

Important: the report and the export folder contain sensitive information about your tenant's configuration. The assessment documentation specifically flags this. Store the report securely, share it only with people who need it, and delete the local folder once you have completed your review.

Where this fits

The Zero Trust Assessment is a starting point, not a finish line.

It gives you a baseline. It shows you where your current configuration aligns with Zero Trust principles and where it does not. It does not do the remediation for you, and it does not replace a broader security architecture review.

But it does something that many organisations skip entirely: it tests the actual configuration rather than asking people what they think is configured.

There is a gap between what your security policies say and what your tenant is actually doing. The Zero Trust Assessment helps you see that gap.

Tomorrow I will go deeper into the identity pillar, which is typically where the most significant gaps and the most significant opportunity sit.

Has your organisation run the Zero Trust Assessment, or used a similar tool to test your actual tenant configuration against a security baseline?

---

## Microsoft Learn References

- [Zero Trust Assessment overview](https://learn.microsoft.com/en-us/security/zero-trust/assessment/overview)
- [Get started with the Zero Trust Assessment](https://learn.microsoft.com/en-us/security/zero-trust/assessment/get-started)
- [Zero Trust assessment terminology](https://learn.microsoft.com/en-us/security/zero-trust/assessment/glossary)
- [Microsoft Zero Trust Workshop & Assessment (GitHub Pages)](https://microsoft.github.io/zerotrustassessment/)
- [Assessment live demo](https://microsoft.github.io/zerotrustassessment/demo/#/)

---

## Hashtags

#ZeroTrust #MicrosoftSecurity #ZeroTrustAssessment #SecurityBaseline #SecurityArchitecture #PowerShell #MicrosoftEntra #Cybersecurity

---

## Accuracy Notes

- **Tool name:** "Microsoft Zero Trust Assessment" — official name. Published as a PowerShell module. Module name in PowerShell is `ZeroTrustAssessment`.
- **Commands confirmed from MS Learn get-started page:**
  - Install: `Install-Module ZeroTrustAssessment -Scope CurrentUser`
  - Connect: `Connect-ZtAssessment`
  - Run: `Invoke-ZtAssessment`
  - Custom path: `Invoke-ZtAssessment -Path C:\MyAssessment01`
- **First run requires Global Administrator** for consent. Subsequent runs: Global Reader + Security Reader + Exchange Administrator + SharePoint Administrator.
- **Read-only confirmed:** MS Learn explicitly states "The Zero Trust Assessment is read-only."
- **Output location:** `.\ZeroTrustReport\ZeroTrustAssessmentReport.html` in current working directory. Opens automatically after run.
- **Large tenant timing (confirmed):** "For large tenants, the Zero Trust Assessment might take more than 24 hours to run." MS Learn explicitly says don't stop it mid-run.
- **Data sensitivity warning (confirmed from MS Learn):** "The report and the export folder contain sensitive tenant information that threat actors might use to their advantage." MS Learn includes a Caution callout specifically about this.
- **Report tabs (confirmed):** Overview tab + Identity, Devices, Network, Data tabs. Each shows Risk level and Status per test.
- **Source frameworks (confirmed):** NIST, CISA, CIS + Microsoft internal security baselines + real-world insights.
- **Secure Future Initiative (SFI):** Assessment tests against SFI alongside Zero Trust pillars — confirmed from overview page.
- **Open source (confirmed):** Code at github.com/microsoft/zerotrustassessment (specifically /tree/psnext/src/powershell per the FAQ).
- **Azure optional:** If Azure not available, close the window, assessment skips those checks and continues.
- **Permissions list:** 20 Graph permissions requested (AuditLog.Read.All, CrossTenantInformation.ReadBasic.All, DeviceManagement*.Read.All x5, Directory.Read.All, DirectoryRecommendations.Read.All, EntitlementManagement.Read.All, IdentityRisk*.Read.All x3, NetworkAccess.Read.All, Policy.Read.All, Policy.Read.ConditionalAccess, Policy.Read.PermissionGrant, PrivilegedAccess.Read.AzureAD, Reports.Read.All, RoleManagement.Read.All, UserAuthenticationMethod.Read.All). Full list in draft not included for readability.
- **Prerequisite conflict note (from MS Learn):** If you have conflicting versions of Microsoft Graph PowerShell installed, a DLL error may occur — docs recommend using uninstall-graph.merill.net to clean up before reinstalling.
- **VCRedist note (from MS Learn):** On a new Windows installation without Microsoft Office installed, DuckDB DLL error may occur — resolved by installing Microsoft Visual C++ 2015-2022 Redistributable.
- **Support:** Raise issues on the Zero Trust Assessment GitHub repo.
