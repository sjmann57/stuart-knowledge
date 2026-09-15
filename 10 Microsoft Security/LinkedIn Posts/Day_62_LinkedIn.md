# Day 62 — LinkedIn Content Package
**Topic:** Microsoft Defender for Containers — registry scanning, runtime protection, and the gap between the two
**Category:** Cloud Security / Container Security
**Week theme:** Microsoft Defender for Cloud (Days 60–63)
**Date:** 2026-08-05 (Wednesday)
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft hook):**
A vulnerability scan checks the image.

It does not check what runs inside the container after it is deployed.

Those are two different things.

Many organisations treat them as the same.

**Hook 2:**
Container security has two layers.

The first is what the image contains before it runs.

The second is what happens inside the cluster after it does.

Most organisations have one. Far fewer have both.

**Hook 3:**
A clean container image does not mean a secure running workload.

It means the image had no known vulnerabilities when it was scanned.

What happens after deployment is a different question entirely.

---

## LinkedIn Article (published — 2026-08-06)

Microsoft Defender for Containers: what registry scanning doesn't tell you about your running cluster

A vulnerability scan checks the image.

It does not check what happens after the container starts running.

Those are two different things.

Many organisations treat them as the same.

Microsoft Defender for Containers is the Microsoft Defender for Cloud plan designed to protect containerised workloads across Kubernetes environments and container registries throughout the application lifecycle.

Yesterday I covered Defender for Servers.

Today's article covers what is, in my experience, one of the fastest-growing areas of cloud security, with the growth of containerisation.

What does Defender for Containers cover?

Before looking at the technology, it helps to understand two terms that appear throughout this article. In my roles, I spend a minimal amount of time on this subject, so explaining it helps. I have also been asked questions on this subject recently, and this will help those who asked.

A container image is a packaged application. It contains the application itself together with everything it needs to run, including its operating system components, runtime, libraries and configuration. Think of it as a sealed software package that is ready to be deployed.

A container registry is where those images are stored before they are deployed. You can think of it as a secure software warehouse that holds approved application images ready for use.

Once an image is deployed, it becomes one or more running containers inside a Kubernetes cluster. Kubernetes is the platform that deploys, runs and manages containers across one or more servers, allowing applications to scale automatically and recover if a server fails.

Microsoft Defender for Containers protects each stage of that lifecycle.

The plan combines four areas of protection:

- Cloud Security Posture Management
- Vulnerability assessment
- Runtime threat protection
- Kubernetes security

Understanding the difference between vulnerability assessment and runtime protection is the most important takeaway from this article.

Container registry scanning

Registry scanning assesses container images before they are deployed.

When Defender for Containers is enabled with registry access configured, Azure Container Registry images are scanned automatically.

Scanning occurs when images are pushed to the registry, when images are imported, and through regular rescans of recently used images and images currently deployed into monitored Kubernetes environments.

Vulnerability findings are powered by Microsoft Defender Vulnerability Management together with Microsoft threat intelligence. The scanning covers operating system packages together with supported application language packages.

Defender for Containers also supports scanning images stored in supported external registries.

Registry scanning tells you whether an image contains known vulnerabilities before deployment.

It does not tell you what the application is doing after it starts running.

Runtime protection with the Defender sensor

Once a container is running, a different set of risks appears.

An attacker may exploit a vulnerability in the application, execute malicious code, create privileged Kubernetes roles, move laterally between workloads or install cryptocurrency miners. None of these activities changes the original image, so registry scanning alone will never detect them.

This is where the Defender sensor comes in.

The Defender sensor provides runtime protection.

It is deployed automatically to every server, known as a node, within the Kubernetes cluster using a Kubernetes feature called a DaemonSet. A DaemonSet ensures one copy of the Defender sensor runs on every node in the cluster.

The sensor watches what running containers are actually doing. It collects runtime telemetry from the cluster, including Kubernetes activity, process execution and workload behaviour, before securely sending those signals to Defender for Cloud for analysis.

For Azure Kubernetes Service (AKS), the sensor is deployed through the AKS Security Profile.

No inbound connectivity is required.

Kubernetes audit logs are collected through Azure-managed infrastructure, so administrators do not need to configure auditing separately.

Runtime protection combines behavioural analytics with Kubernetes-aware detections mapped to the MITRE ATT&CK framework for Containers.

Examples include:

- Exposed Kubernetes dashboards
- Creation of high-privilege Kubernetes roles
- Suspicious process execution
- Binary drift, where software running inside a container differs from the original image
- Lateral movement between workloads
- Cryptocurrency mining
- Malware execution

Alerts generated by runtime detections integrate directly into Microsoft Defender XDR, allowing security teams to investigate container threats alongside identity, endpoint and email incidents from a single investigation experience.

Two layers, not one

This is the point many organisations miss.

Think of it like buying a new car.

A factory inspection tells you the car left production in good condition.

It tells you nothing about how it will be driven once it reaches the road.

Container image scanning checks the application before deployment.

Runtime protection watches what actually happens afterwards.

A clean image can still become a compromised workload.

Application vulnerabilities, stolen credentials, privilege escalation and Kubernetes misconfigurations all happen after deployment.

Registry scanning tells you whether an image was vulnerable before deployment.

Runtime protection tells you what is happening after deployment.

They solve different problems.

Enabling registry scanning without the Defender sensor means you cannot see malicious runtime behaviour.

Deploying the Defender sensor without registry scanning means vulnerable images can still reach production.

Neither replaces the other.

Multicloud and on-premises

Azure Kubernetes Service integrates natively with Defender for Containers.

Amazon Elastic Kubernetes Service (EKS), Google Kubernetes Engine (GKE) and supported on-premises Kubernetes environments are onboarded using Azure Arc-enabled Kubernetes.

Once connected, Defender for Cloud provides posture assessment, vulnerability assessment, runtime protection and recommendations across Azure, AWS, Google Cloud Platform and on-premises Kubernetes environments from a single management plane.

Where to look today

Open Microsoft Defender for Cloud and navigate to Environment settings.

Review the Containers plan and confirm which capabilities are enabled.

Do not assume enabling the Defender Plan automatically enables every capability.

I would check four things first:

- Confirm the Defender sensor is deployed to your Kubernetes clusters.
- Confirm registry scanning is enabled for your container registries.
- Confirm Azure Policy for Kubernetes is enabled where appropriate.
- Review container recommendations and identify any high-priority misconfigurations.

Cluster misconfigurations are often some of the quickest security improvements to make before looking at runtime threats.

Tomorrow I will look at Microsoft Defender for DevOps, extending Defender for Cloud into GitHub, Azure DevOps and Infrastructure as Code scanning so vulnerabilities can be identified before they ever reach a container registry.

Container security is not one control.

It starts with the image.

It continues with the cluster.

And it finishes with understanding what your workloads are actually doing at runtime.

Does your organisation currently use registry scanning, runtime protection, or both?

---

## Microsoft Learn References

- [Introduction to Microsoft Defender for Containers](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-introduction)
- [Defender for Containers architecture](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-architecture)
- [Defender for Containers deployment overview](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-deployment-overview)
- [Enable Defender for Containers in Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-enable-plan)
- [Vulnerability management for containers](https://learn.microsoft.com/azure/defender-for-cloud/agentless-vulnerability-assessment-azure)

---

## Hashtags

#MicrosoftDefender #DefenderForCloud #ContainerSecurity #Kubernetes #CloudSecurity #AzureSecurity #MicrosoftSecurity

---

## Accuracy Notes (for future articles)

- **Stuart's acknowledged learning curve on containers:** Stuart explicitly disclosed in the article that containers is not his primary daily area — "In my roles, I spend a minimal amount of time on this subject, so explaining it helps." This is a notable departure from the rest of the series and adds authenticity. The article also originated partly from a question Stuart was asked about Kubernetes/registry. Carry the practitioner framing — honest about depth of experience — into any future container articles.
- **Container/Kubernetes primer included in published version:** Stuart added a plain-English primer explaining container image, container registry, and Kubernetes before the technical sections. This was not in the draft. Use this primer structure (sealed software package / secure software warehouse / orchestration platform) when explaining containers to non-specialist audiences in future.
- **The car analogy:** "Think of it like buying a new car. A factory inspection tells you the car left production in good condition. It tells you nothing about how it will be driven once it reaches the road." — Stuart's addition. Excellent analogy for the image/runtime gap. Reuse for container security explanations.
- **Four capabilities restructured:** Stuart's published version uses: Cloud Security Posture Management / Vulnerability assessment / Runtime threat protection / Kubernetes security — slightly different from the draft's four. Use Stuart's version in future references.
- **Defender sensor = DaemonSet on every node:** eBPF technology, deploys as AKS Security Profile for AKS. No inbound connectivity needed. Audit logs via Azure-managed infrastructure (no separate audit log config in cluster).
- **Binary drift:** explicitly named and explained — "software running inside a container differs from the original image." Keep this phrasing.
- **External registries:** Stuart simplified to "supported external registries" (not named individually). Avoids risk of naming unsupported ones.
- **Multi-cloud:** EKS, GKE, on-premises via Azure Arc-enabled Kubernetes. AKS is native.
- **"Configured rather than simply enabled" pattern continues:** "Do not assume enabling the Defender Plan automatically enables every capability." Stuart uses this for containers same as servers.
- **Four checks in "Where to look":** Defender sensor deployed / registry scanning enabled / Azure Policy for Kubernetes enabled / container recommendations reviewed.
- **Hook change:** Published hook: "It does not check what happens after the container starts running." (Draft had "what runs inside the container after it is deployed.") — subtle but cleaner.
- **Preview Day 63:** Defender for DevOps — GitHub, Azure DevOps, IaC scanning "before they ever reach a container registry." Strong narrative arc linking Day 62 → Day 63.
- **Closing:** "Container security is not one control. It starts with the image. It continues with the cluster. And it finishes with understanding what your workloads are actually doing at runtime." — three-part structure mirrors the article's structure.
