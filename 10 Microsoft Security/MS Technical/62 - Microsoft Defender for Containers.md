---
title: "Microsoft Defender for Containers"
product: "Microsoft Defender for Cloud"
day: 62
published: 2026-08-05
source: https://www.linkedin.com/feed/update/urn:li:activity:7490798800639401985/
impressions: 724
tags:
  - defender-for-cloud
  - containers
  - kubernetes
  - cwpp
  - registry-scanning
---

# Microsoft Defender for Containers

## Summary
Defender for Containers secures the container lifecycle: registry/image vulnerability scanning (shift-left) and runtime threat protection for Kubernetes — with a real gap between the two if only one is in place.

## Key facts
- Image scanning of registries and (agentless) running images for vulnerabilities.
- Runtime protection via a sensor/DaemonSet detecting suspicious Kubernetes and container activity.
- Kubernetes posture: misconfiguration recommendations and hardening.
- Covers AKS plus EKS/GKE and Arc-enabled clusters.

## Licensing & prerequisites
- Single Defender for Containers plan; priced per vCore/resource.

## Practitioner notes / gotchas
- Scanning a clean image at build time doesn't protect it at runtime — you need both halves.
- Foundational concepts (images, registries, Kubernetes) matter because many teams manage containers without deep security context.

## Microsoft Learn references
- [Introduction to Microsoft Defender for Containers](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-introduction)
- [Defender for Containers architecture](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-architecture)
- [Defender for Containers deployment overview](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-deployment-overview)
- [Enable Defender for Containers in Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-containers-enable-plan)
- [Vulnerability management for containers](https://learn.microsoft.com/azure/defender-for-cloud/agentless-vulnerability-assessment-azure)

## Related
- [[61 - Microsoft Defender for Servers]]
- [[63 - Microsoft Defender for DevOps (Defender for Cloud – DevOps security)]]

## Source
LinkedIn (Day 62): https://www.linkedin.com/feed/update/urn:li:activity:7490798800639401985/
