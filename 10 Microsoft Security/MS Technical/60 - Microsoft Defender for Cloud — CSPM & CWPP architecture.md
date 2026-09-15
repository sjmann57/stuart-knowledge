---
title: "Microsoft Defender for Cloud — CSPM & CWPP architecture"
product: "Microsoft Defender for Cloud"
day: 60
published: 2026-08-04
source: https://lnkd.in/p/e4PMCsed
impressions: 501
tags:
  - defender-for-cloud
  - cspm
  - cwpp
  - cloud-security
  - architecture
---

# Microsoft Defender for Cloud — CSPM & CWPP architecture

## Summary
The two halves of Defender for Cloud: CSPM (posture — find and fix misconfigurations and risky attack paths before an attack) and CWPP (workload protection — runtime threat detection for servers, containers, databases, storage and more).

## Key facts
- CSPM: Secure Score, recommendations, attack path analysis, agentless scanning, data-aware security posture, cloud security graph.
- CWPP: per-resource Defender plans providing runtime protection and threat detection.
- Cloud security graph + attack paths feed Exposure Management.
- Multicloud (Azure/AWS/GCP) and hybrid.

## Licensing & prerequisites
- Defender CSPM plan for advanced posture; separate workload plans (Servers, Containers, Databases, Storage, etc.) for CWPP.

## Practitioner notes / gotchas
- Posture (prevent) and workload protection (detect) are different jobs — design for both.
- Attack-path analysis here is the cloud-native cousin of Exposure Management's cross-workload paths.

## Microsoft Learn references
- [What is Microsoft Defender for Cloud?](https://learn.microsoft.com/azure/defender-for-cloud/defender-for-cloud-introduction)
- [What is Cloud Security Posture Management (CSPM)?](https://learn.microsoft.com/azure/defender-for-cloud/concept-cloud-security-posture-management)
- [Secure score in Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/secure-score-security-controls)
- [Security explorer and attack paths in Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/concept-attack-path)
- [Plan multicloud security with Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/plan-multicloud-security-get-started)

## Related
- [[61 - Microsoft Defender for Servers]]
- [[62 - Microsoft Defender for Containers]]
- [[89 - Microsoft Security Exposure Management]]

## Source
LinkedIn (Day 60): https://lnkd.in/p/e4PMCsed
