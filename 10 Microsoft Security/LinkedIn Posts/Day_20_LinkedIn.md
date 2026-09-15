# Day 20 — LinkedIn Content Package
**Topic:** Microsoft Defender for Cloud — Secure Score, CSPM, and the cloud security gap
**Category:** Cloud Security
**Framework:** Microsoft Guidance vs Real-World Implementation
**Format:** Research-backed article (Day 6+ format)
**Opens:** Cloud Security chapter (after Identity thread Days 6-9 and Security Operations Days 14, 19)

---

## 1. Title

Your Azure environment has a security score. Most organisations have never looked at it.

---

## 2. LinkedIn Post (Draft — for Stuart's review)

Your Azure environment has a security score. Most organisations have never looked at it.

Microsoft Defender for Cloud is a cloud-native application protection platform. It covers cloud security posture, workload protection across servers, containers, databases, storage, and APIs, and security embedded into the development lifecycle. It also integrates with generative AI workloads, which is a newer area worth paying attention to as organisations build on top of AI services.

It has three core components. Cloud Security Posture Management, which checks and improves how your cloud resources are configured. Cloud Workload Protection, which defends what is running in your environment. And DevSecOps, which brings security into the code pipeline before anything reaches production.

The part most organisations already have access to, and are not using, is foundational CSPM. It is available on every Azure subscription at no additional cost. It gives you a Secure Score, which is a summary of your security posture based on Microsoft's recommendations across your environment. It maps those recommendations to controls you can act on. It shows you where your configuration drifts from security best practice.

In practice, what I find is that the Secure Score exists and nobody has looked at it beyond the initial setup. Recommendations have been accumulating for months. The score is sitting somewhere between forty and sixty percent and the items that would move it significantly are not being prioritised because nobody has been asked to own them.

The paid Defender CSPM plan adds attack path analysis. This builds a graph of your cloud environment and shows you the routes an attacker could take from a public-facing resource to a sensitive data store or privileged identity. It is one of the more powerful tools I have seen for making the risk conversation concrete with a leadership team. Instead of talking about misconfigured storage accounts in the abstract, you can show the specific path from that misconfiguration to your Azure Key Vault or your SQL database containing customer records. That lands differently.

Beyond CSPM, the workload protection plans cover servers, containers, databases, storage, Key Vault, App Service, APIs, and resource management operations. What I typically find is that some plans have been enabled, usually Defender for Servers, and others have not, creating blind spots in the workload coverage. Defender for Key Vault, for example, detects unusual attempts to access or exploit key vaults, which is the kind of signal that matters when an attacker has already gained a foothold and is moving laterally.

The same pattern I have described across identity and security operations applies here. The platform exists. The free tier is already available. The data is being collected. The recommendations are sitting unreviewed, the attack paths are unmapped, and the workload plans are partially deployed.

What is your Defender for Cloud Secure Score today?

And when did someone last review what it is telling you to fix?

---

## 3. Microsoft Learn References

- What is Microsoft Defender for Cloud: https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction
- Secure Score in Defender for Cloud: https://learn.microsoft.com/en-us/azure/defender-for-cloud/secure-score-security-controls
- Attack path analysis: https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-attack-path
- Cloud Security Posture Management: https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-cloud-security-posture-management

---

## 4. Suggested Image Concept

Dark background. Large number: "47%" — below it: "Your Secure Score. When did you last look at it?" Small Defender for Cloud logo bottom-right. The percentage is illustrative — adjust to whatever a typical mid-market score looks like in your experience.

Alternative: Quote card — "Instead of talking about misconfigured storage accounts in the abstract, you can show the path to your customer database. That lands differently."

---

## 5. Alternative Discussion Questions

1. What is your organisation's Defender for Cloud Secure Score, and who owns improving it?
2. Have you used attack path analysis to show leadership the concrete risk of cloud misconfigurations?
3. Which Defender for Cloud workload protection plans do you have enabled, and do you have gaps in coverage?

---

## 6. Hashtags

#MicrosoftDefender #DefenderForCloud #CloudSecurity #ZeroTrust #SecurityArchitect

---

## Day 20 Checklist

- [ ] The attack path analysis observation is the strongest practitioner point — add your own example if you have used it in a risk conversation with a leadership team
- [ ] "Forty to sixty percent" for Secure Score is a reasonable illustrative range — adjust if your experience differs
- [ ] The AI workload angle (AI SPM) is mentioned briefly — could be expanded into a full Day later given how quickly that space is moving
- [ ] Post with graphic or personal photo
- [ ] Add follow-up comment within 30 minutes — consider linking to the free foundational CSPM getting started guide for readers who want to check their own score
