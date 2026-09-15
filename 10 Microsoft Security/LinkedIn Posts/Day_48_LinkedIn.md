# Day 48 — LinkedIn Content Package
**Topic:** Microsoft Defender Vulnerability Management — knowing your attack surface before the attacker does
**Category:** SecOps / Vulnerability Management
**Date:** 2026-07-23
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
Your vulnerability scanner returned 3,847 findings this month. Your patch team can realistically action 40 of them before next month's scan.
The question nobody wants to answer is: which 40?

**Hook 2:**
There is a CVE scored 9.8 on your network. It is on a development server with no internet exposure, accessed by two engineers.
There is also a CVE scored 7.2 on your customer portal, actively exploited in the wild, with direct internet exposure.
A raw CVSS list tells you to patch the 9.8 first. That is the wrong answer.

**Hook 3:**
Most organisations know they have unpatched vulnerabilities.
Fewer know which ones are actually being exploited in the wild, which devices carrying them are internet-facing, and which remediation actions would reduce their overall risk exposure the most.
That is the gap between running a vulnerability scanner and running Microsoft Defender Vulnerability Management.

---

## LinkedIn Article (Stuart's version — published 2026-07-23)
**Note:** Key changes from draft: CVSS line strengthened ("never designed"); Exposure Score repositioned as part of Microsoft Security Exposure Management; prioritisation signals expanded to CVSS + EPSS + Microsoft threat intelligence + observed exploit activity + asset context (more comprehensive than draft's CVSS + EPSS + asset context); removed specific 0-29/30-69/70-100 banding; score update timing changed from "recalculates daily / 24hrs" to "updates as Microsoft processes new telemetry"; software inventory EoL example updated to 2010/2022; remediation tasks expanded to include Configuration Manager alongside Intune; Security Baselines framed as "Microsoft security recommendations and supported security baselines" (not specifically CIS); Browser Extensions risk factors: "excessive permissions, poor reputation or outdated versions"; portal path shortened to "Exposure management > Vulnerability management" (no > Overview); discussion question split into two shorter paragraphs.

Microsoft Defender Vulnerability Management: Knowing your attack surface before the attacker does

Your vulnerability scanner returned 3,847 findings this month. Your patch team can realistically action 40 of them before next month's scan.
The question nobody wants to answer is: which 40?

Most organisations approach vulnerability prioritisation using CVSS scores. CVSS measures the theoretical severity of a vulnerability. A 9.8 sounds more urgent than a 6.4. But CVSS was never designed to tell you which vulnerabilities are most likely to be exploited against your specific environment, on your specific devices, this week.

Microsoft Defender Vulnerability Management addresses this directly, and for organisations already running Microsoft Defender for Endpoint Plan 2, the core capability is already included.

Exposure Score: beyond CVSS

Exposure Score is part of Microsoft Security Exposure Management and reflects your organisation's overall security exposure.

What makes it more useful than a raw severity list is the rationale behind Microsoft's prioritisation.

Recommendations are prioritised using multiple signals, including CVSS, EPSS (Exploit Prediction Scoring System), Microsoft's threat intelligence, observed exploit activity and the context of the affected asset. A vulnerability with a moderate CVSS score but active exploitation may be prioritised ahead of a critical vulnerability that currently presents little practical risk.

The affected asset also matters. Internet-facing systems, business-critical devices and highly exposed assets receive greater weighting than low-impact devices.

The result is a prioritised list of security recommendations ordered by the extent to which they reduce your exposure, rather than simply by severity.

As recommendations are remediated, Exposure Score updates as Microsoft processes new telemetry across your environment.

Software inventory and the asset you forgot about

Alongside Exposure Score, Defender Vulnerability Management continuously maintains a software inventory across managed devices: every installed application, its vendor, version, known vulnerabilities affecting that version, and the devices where it is installed.

This matters for two reasons.

First, service shows end-of-life software running in environments where patching was deprioritised years ago by the vendor. The application your finance team has used since 2010, with the vendor stopped support back in 2022, is exactly the finding that scheduled vulnerability scans often miss, but continuous inventory quickly highlights.

Second, it gives security and IT teams a shared view of what is actually installed rather than what they believe is installed. Those two lists are often very different.

Remediation tasks and the Intune integration

Security recommendations in Defender Vulnerability Management can be sent directly as remediation tasks to Microsoft Intune, or to Microsoft Configuration Manager where appropriate.

The task includes the affected software, the recommended action, affected devices and progress tracking.

This closes a gap I see in many organisations. Security identifies the issue. IT receives an email or ticket. Progress is tracked manually.

With remediation management built into Microsoft Defender, both teams work from the same recommendation with shared visibility throughout the remediation process.

Premium capabilities: security baselines and browser extensions

The core Defender Vulnerability Management capabilities are included with Microsoft Defender for Endpoint Plan 2.

Additional premium capabilities are available through the Defender Vulnerability Management add-on or standalone subscription.

Security Baselines Assessment evaluates device configurations against Microsoft security recommendations and supported security baselines. Devices may have no exploitable CVEs but still contain configuration weaknesses that increase risk. This brings configuration posture and vulnerability management together in one place.

Browser Extensions Assessment inventories browser extensions across managed devices and highlights extensions that present elevated risk because of excessive permissions, poor reputation or outdated versions. Browser extensions are an increasingly common attack path, particularly where users install them without IT oversight.

Where to look today

Open the Microsoft Defender portal and navigate to:

Exposure management > Vulnerability management

Review your Exposure Score.

If it sits in the medium or high range, review the highest-priority security recommendations based on potential reduction in exposure.

Review your software inventory for unsupported or end-of-life software.

If you have the premium Defender Vulnerability Management capabilities, review Security Baselines Assessment to identify configuration weaknesses that may be increasing your attack surface.

For recommendations that require software updates or configuration changes, consider creating remediation tasks directly in Intune rather than relying on manual ticketing.

You cannot patch everything.

But you can make sure the 40 things you do patch this month are the ones that reduce your real-world exposure the most, rather than simply the ones with the highest CVSS scores.

What does your vulnerability prioritisation process look like today?
Are you still working from severity scores alone, or are you prioritising based on exploitability, asset context and real-world exposure?

---

## Microsoft Learn References

- [Microsoft Defender Vulnerability Management overview](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)
- [Compare Microsoft Defender Vulnerability Management plans and capabilities](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management-capabilities)
- [Exposure score in Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-exposure-score)
- [Software inventory](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-software-inventory)
- [Security recommendations](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation)
- [Security baselines assessment](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-baselines)
- [Browser extensions assessment](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-browser-extensions)

---

## Suggested Image Concept

Microsoft Defender portal showing the Vulnerability Management overview dashboard with the Endpoint exposure score card, the top security recommendations list sorted by score impact, and the software inventory panel — demonstrating the risk-prioritised view rather than a flat CVE list.

---

## Three Alternative Discussion Questions

1. What does your current vulnerability prioritisation process look like, and are you working from raw CVSS scores or something that incorporates real-world exploitability and asset context?
2. Has your organisation set up the Intune integration for Defender Vulnerability Management remediation tasks, and has it changed how security and IT teams collaborate on patching?
3. When did you last run a software inventory across your endpoint estate, and were there any end-of-life applications that surprised you?

---

## Hashtags

#MicrosoftDefender #VulnerabilityManagement #DefenderXDR #MicrosoftSecurity #CyberSecurity
