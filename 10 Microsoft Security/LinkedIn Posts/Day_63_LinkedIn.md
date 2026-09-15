# Day 63 — LinkedIn Content Package
**Topic:** Microsoft Defender for DevOps — finding security issues in code before they become cloud problems
**Category:** Cloud Security / DevSecOps
**Week theme:** Microsoft Defender for Cloud (Days 60–63) — Week 9 close
**Date:** 2026-08-06 (Thursday)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (used in draft):**
By the time a vulnerability shows up in a running workload, it has already passed through several stages.

It was written into code.

Reviewed in a pull request.

Built into an image.

Deployed to a server or a cluster.

Defender for DevOps is designed to find it earlier — before any of that happens.

**Hook 2:**
A misconfigured storage account is far cheaper to fix in a Terraform template than after it has been deployed to production.

Most organisations discover it after deployment.

Defender for DevOps is built to surface it before the template ever runs.

**Hook 3:**
Every misconfiguration that reaches a running cloud environment started somewhere.

It started in code.

Defender for DevOps is the part of Microsoft Defender for Cloud that works at that stage.

---

## LinkedIn Article (published — 2026-08-07)

Microsoft Defender for DevOps: finding security issues in code before they become cloud problems

By the time a vulnerability shows up in a running workload, it has already passed through several stages.

It was written into code.

Reviewed in a pull request.

Built into an image.

Deployed to a server or a Kubernetes cluster.

Microsoft Defender for DevOps is designed to find many of those problems earlier, before they reach production.

This is the final article in my week covering Microsoft Defender for Cloud.

This week I have covered the architecture (Monday), Defender for Servers (Tuesday), and Defender for Containers (Wednesday).

Today I want to finish with Microsoft Defender for DevOps, the capability that helps shift security left by identifying risks during software development rather than after workloads are deployed.

I'm not a developer. Like many people working in security, I've often found myself looking in from the outside. The inner workings of software development can sometimes feel like a different world.

Should that, in itself, be a blocker?

My answer is no.

Like many things in security, it starts with conversations, good processes and the right frameworks.

We often talk about Secure by Design. Microsoft Defender for DevOps is part of making that happen.

What is Microsoft Defender for DevOps?

Microsoft Defender for DevOps extends Microsoft Defender for Cloud into the software development lifecycle.

Rather than protecting running infrastructure, it connects to the environments where applications are written, reviewed and built, providing security visibility across development pipelines and source code repositories.

Microsoft Defender for DevOps integrates natively with GitHub and Azure DevOps, providing a centralised view of security findings from connected development environments.

Instead of developers, security teams and cloud teams working from separate tools, Defender for DevOps brings those findings together inside Microsoft Defender for Cloud.

Three capabilities

Microsoft Defender for DevOps focuses on three areas.

The first is DevOps security posture management. Security teams gain visibility across connected repositories, pipelines and organisations, identifying exposed secrets, insecure service connections, excessive permissions and configuration weaknesses.

The second is Infrastructure as Code security. Infrastructure templates are scanned before deployment, allowing security issues to be identified before cloud resources are created.

The third is code-to-cloud correlation. Defender for Cloud connects findings discovered during development with the cloud resources eventually deployed from that code, giving security teams the context needed to prioritise remediation.

Infrastructure as Code scanning

Infrastructure as Code (IaC) scanning is one of the most practical capabilities Defender for DevOps provides.

Modern cloud environments are increasingly built using code rather than manual configuration.

Terraform, Bicep, ARM templates, Kubernetes manifests, Helm charts, Dockerfiles and AWS CloudFormation templates all define infrastructure that can be deployed repeatedly.

If a security misconfiguration exists inside one of those templates, every future deployment inherits the same weakness.

Microsoft Security DevOps (MSDO) integrates into Azure DevOps and GitHub workflows to scan Infrastructure as Code during the development pipeline.

Defender for DevOps then centralises those findings inside Microsoft Defender for Cloud alongside other cloud security recommendations.

Instead of discovering insecure storage accounts, permissive network security groups or publicly exposed Kubernetes services after deployment, teams can identify these issues while the code is still being reviewed. That becomes even more valuable as AI-generated code becomes increasingly common in software development.

Pull request annotations

One of the most useful capabilities for development teams is pull request annotations.

When Microsoft Security DevOps identifies an Infrastructure as Code issue during a pull request, the finding can be surfaced directly within the pull request itself.

Developers see the security recommendation in the same workflow they are already using, alongside the affected code.

That removes one of the biggest challenges in application security.

The finding appears where the developer is already working instead of in a separate dashboard that we know may never be checked.

DevOps security posture

Defender for DevOps also assesses the security posture of the development environment itself.

This includes repositories, pipelines, organisations, service connections, variable groups and secrets.

Modern software supply chains have become attractive attack targets.

Compromised service connections, exposed credentials, excessive permissions and insecure pipeline configurations have all featured in real-world attacks.

Rather than only scanning the code, Defender for DevOps also assesses the environment responsible for building and deploying that code.

Connecting code to cloud

This is where Defender for DevOps becomes particularly valuable.

When used alongside Defender CSPM and the wider Defender for Cloud platform, security findings discovered during development can be linked to deployed cloud resources.

Security teams can see that a Terraform template contains a misconfiguration. Still, they can also see that the workload deployed from that template is internet-facing, contains sensitive data or forms part of an attack path.

That additional context helps prioritise remediation based on real business risk rather than treating every finding equally.

Where to look today

Open Microsoft Defender for Cloud and navigate to DevOps security.

If you have not connected any development environments, start by connecting your Azure DevOps or GitHub organisation.

Once connected, review the inventory to understand what repositories, pipelines and organisations have been discovered.

I would focus on two areas first:

- Infrastructure as Code findings — identify high- or critical-severity misconfigurations before they are deployed.
- DevOps security posture — review service connections, repositories, pipelines and secrets for excessive permissions or exposed credentials.

These are often the quickest improvements to make in environments that have not previously assessed their software supply chain.

Closing the week

This week I have worked through Microsoft Defender for Cloud from the architecture outwards.

Defender for Cloud protects cloud environments throughout their lifecycle.

Defender for Servers and Defender for Containers protect workloads after deployment.

Microsoft Defender for DevOps helps identify risks while applications are still being designed, written and reviewed, before those workloads ever reach production.

Both layers are needed.

Protecting running infrastructure while ignoring development pipelines means new risks continue to be introduced with every deployment.

Scanning code without protecting running workloads leaves you blind to threats that only appear after deployment.

The strength of Microsoft Defender for Cloud is that it connects both.

From the developer writing code, to the administrator deploying infrastructure, to the security analyst responding to incidents, the same platform provides a connected view of risk.

From the code being written today…

…to the workload running tomorrow.

Thank you to everyone who has followed this week's series.

Next week I'll move into another area of the Microsoft security platform and continue building on the same architectural approach.

Which part of Microsoft Defender for Cloud delivers the most value in your organisation: posture management, workload protection or securing the software development lifecycle?

---

## Microsoft Learn References

- [Overview of Microsoft Defender for Cloud DevOps security](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-devops-introduction)
- [Improve DevOps environment security posture](https://learn.microsoft.com/azure/defender-for-cloud/concept-devops-environment-posture-management-overview)
- [Enable pull request annotations in GitHub and Azure DevOps](https://learn.microsoft.com/azure/defender-for-cloud/enable-pull-request-annotations)
- [Scan your connected GitHub repository or Azure DevOps project](https://learn.microsoft.com/azure/defender-for-cloud/iac-vulnerabilities)
- [Support and prerequisites: DevOps security](https://learn.microsoft.com/azure/defender-for-cloud/devops-support)

---

## Hashtags

#MicrosoftDefender #DefenderForCloud #DevSecOps #CloudSecurity #AzureSecurity #MicrosoftSecurity #DevOps #InfrastructureAsCode

---

## Accuracy Notes (for future articles)

- **Stuart's "not a developer" disclosure:** Continues the authenticity theme from Day 62. Stuart explicitly acknowledged he looks in from the outside on software development. This is genuine and builds trust. Carry this honest framing into any future DevSecOps content.
- **"Shift security left" used:** Stuart used this term in the published version ("helps shift security left by identifying risks during software development"). Draft deliberately avoided it as jargon; Stuart chose to use it. He is comfortable with the terminology.
- **"Secure by Design" referenced:** Linked Defender for DevOps to the Secure by Design principle. Strong grounding for future articles on DevSecOps topics.
- **Platforms named:** GitHub and Azure DevOps (GitLab omitted from this article — Stuart simplified). Don't assume GitLab is absent when describing the product more fully; it is supported, but Stuart chose not to name it here.
- **Three capabilities (Stuart's version):** DevOps security posture management / Infrastructure as Code security / Code-to-cloud correlation. Use this exact framing in future references.
- **MSDO named:** "Microsoft Security DevOps (MSDO)" — the Azure DevOps extension / GitHub Action that integrates scanning into pipelines. First time named explicitly in this series.
- **IaC types confirmed:** Terraform, Bicep, ARM, Kubernetes manifests, Helm charts, Dockerfiles, AWS CloudFormation. Use all of these when listing IaC support.
- **AI-generated code angle added:** "That becomes even more valuable as AI-generated code becomes increasingly common in software development." — Stuart added this. Smart topical link. Reuse when discussing why IaC scanning matters more now.
- **PR annotations framing:** "The finding appears where the developer is already working instead of in a separate dashboard that we know may never be checked." — excellent practitioner insight about dashboard fatigue. Strong reuse candidate.
- **Software supply chain named as attack surface:** "Compromised service connections, exposed credentials, excessive permissions and insecure pipeline configurations have all featured in real-world attacks." — accurate and grounded.
- **Code-to-cloud context:** "the workload deployed from that template is internet-facing, contains sensitive data or forms part of an attack path" — connects Defender for DevOps findings directly to Defender CSPM attack path analysis from Day 60.
- **Closing framing (strong reuse candidate):** "From the developer writing code, to the administrator deploying infrastructure, to the security analyst responding to incidents, the same platform provides a connected view of risk. From the code being written today… …to the workload running tomorrow." — best closing in the Week 9 series.
- **Licensing note removed in published version:** Stuart did not call out Defender CSPM requirement for PR annotations or code-to-cloud. He mentioned "Defender CSPM and the wider Defender for Cloud platform" in the code-to-cloud section without specifying it as a separate paid plan. Maintain this softer framing in future articles unless licensing is the specific focus.
- **Week 9 series complete:** Days 60–63 now fully published: architecture → Servers → Containers → DevOps. Week 10 topic not yet confirmed.
