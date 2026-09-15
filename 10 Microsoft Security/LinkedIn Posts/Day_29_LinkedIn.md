# Day 29 — LinkedIn Content Package
**Topic:** Microsoft Defender for Identity — the identity detection tool most organisations have but haven't deployed
**Category:** Security Operations / Identity
**Format:** Technical article
**Note:** Stuart's published version. Builds on Day 7 (Entra ID Identity Protection), Day 8 (Conditional Access), Day 26 (threat hunting). Key Stuart changes: softened DCSync claim to "potentially exposing" rather than "have every hash"; reordered kill chain (Lateral movement first, then Reconnaissance, then Domain dominance); portal path corrected to System > Settings > Identities > Sensors; v3.x prerequisites clarified (March 2026 cumulative update + Defender for Endpoint); Secure Score section uses general posture assessment language rather than naming specific assessment.

---

## LinkedIn Article (Stuart's version — published)

Entra ID Identity Protection is enabled. That is not the same as monitoring your Active Directory for attacks.
Identity Protection watches cloud sign-in risk. It detects leaked credentials, anonymous IP sign-ins, and impossible travel. It requires Entra ID P2 and is primarily focused on Entra sign-in and user risk.
Microsoft Defender for Identity does something different. It watches what is happening inside your Active Directory, the Kerberos traffic, NTLM authentication, DNS queries, Windows events and replication requests going to and from your domain controllers. It is looking for the attacks that happen after an attacker is already inside your network.
Most organisations running Microsoft 365 E5 have both products licensed. Many have not deployed Defender for Identity at all.
What Defender for Identity actually covers
Defender for Identity installs a lightweight sensor directly on your domain controllers. No port mirroring, no dedicated server, no complex network changes. The sensor parses network traffic and Windows events locally and sends the relevant signals to the Defender portal for analysis.
What it is looking for covers the full kill chain of an AD-focused attack:
Lateral movement: Pass-the-Hash and Pass-the-Ticket attacks, in which a stolen NTLM hash or Kerberos ticket is replayed on another machine to move laterally through the environment without requiring a plaintext password.
Reconnaissance: An attacker enumerating users, groups, and machines across the domain before they decide where to move.
Domain dominance: DCSync attacks, where an attacker uses directory replication service calls to extract password hashes directly from Active Directory, potentially exposing password hashes for many accounts in the domain, including privileged accounts. Golden Ticket activity, where a compromised KRBTGT account is used to forge authentication tickets with arbitrary lifetimes and permissions.
If an attacker has reached the DCSync stage, they have the hash for every account in your domain, including all your privileged accounts. Defender for Identity detection is strongest when sensors are deployed across all domain controllers, because the sensors need visibility into the domain controller activity involved.
The deployment gap most organisations have
This is the practical issue I see repeatedly. Either Defender for Identity was never deployed because the project was treated as optional during the M365 E5 rollout, or sensors were installed on two or three domain controllers during a pilot and coverage was never completed.
Defender for Identity should have sensors on all your domain controllers, including read-only domain controllers (RODCs). If a sensor is missing from even one DC, there is a gap in your detection coverage. An attacker targeting that specific domain controller may not generate the Defender for Identity alerts you expect from that DC.
For domain controllers running Windows Server 2019 or later, you deploy the v3.x sensor. v3.x requires Windows Server 2019+, the March 2026 cumulative update or later, and Defender for Endpoint onboarded on that server. For older domain controllers and for AD FS, AD CS, or Microsoft Entra Connect servers that are not domain controllers, you use the v2.x sensor. Both are installed from the Microsoft Defender portal under Settings > Identities > Sensors.
How to check your coverage in two minutes
Microsoft Secure Score and Defender for Identity posture assessments can highlight unmonitored identity infrastructure. These assessments can help identify identity infrastructure that is not monitored, including domain controllers without a Defender for Identity sensor. If you have not looked at it recently, it is worth checking now.
You can also go directly to the Microsoft Defender portal > System > Settings > Identities > Sensors and count the sensors listed against the number of domain controllers in your environment. The gap will be obvious if it exists.
What you get when it is deployed
Defender for Identity alerts flow into unified incidents in the Microsoft Defender portal, alongside alerts from Defender for Endpoint, Defender for Office 365, and Defender for Cloud Apps. An attack that starts with a phishing email, moves to endpoint credential theft, and then progresses to lateral movement through Active Directory will appear as a single incident, with the full attack chain visible.
Identity security posture assessments from Defender for Identity also appear in Microsoft Secure Score, covering AD misconfigurations, unconstrained Kerberos delegation, weak protocol usage, and Group Policy gaps that attackers commonly exploit before they even need to perform lateral movement.
I covered threat hunting in Sentinel and Defender XDR on Day 26. Defender for Identity feeds directly into Advanced Hunting via the identity tables, so if you are hunting for lateral movement or authentication abuse, these signals are part of the dataset.
Practitioner take
The pattern I see most often is Identity Protection enabled, some Conditional Access risk policies in place, and the team satisfied that identity threat detection is covered. Defender for Identity is licensed under the same Microsoft 365 E5 agreement. It was just never deployed.
The distinction matters because the attacks that lead to full domain compromise, DCSync, Golden Ticket, and Pass-the-Ticket, are not cloud sign-in events. Identity Protection will not see them. Defender for Identity is specifically built to catch them, but only if the sensors are on the domain controllers where those attacks happen.
Where to start today
Go to the Microsoft Defender portal > System > Settings > Identities > Sensors.
If you see a handful of sensors when you have dozens of domain controllers, that is your starting point.
If you see no sensors at all, you have the product licensed but not deployed, and your on-premises Active Directory is going unmonitored for the attacks most likely to result in domain compromise.
Have you deployed Defender for Identity sensors on all your domain controllers, or is it one of those products that is licensed but sitting unused?

---

## Microsoft Learn References

- [Microsoft Defender for Identity overview](https://learn.microsoft.com/en-us/defender-for-identity/what-is)
- [Pilot and deploy Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-xdr/pilot-deploy-defender-identity)
- [Deploy the Defender for Identity sensor v3.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3)
- [Defender for Identity sensor v2.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2)
- [Identity infrastructure security assessments — Unmonitored domain controllers](https://learn.microsoft.com/en-us/defender-for-identity/security-posture-assessments/identity-infrastructure)
- [Microsoft Defender for Identity alerts in Microsoft Defender format](https://learn.microsoft.com/en-us/defender-for-identity/alerts-xdr)

---

## Suggested Image Concept

Microsoft Defender portal Sensors page showing a handful of deployed sensors against a long list of domain controllers — making the coverage gap immediately visible. Simple, factual, makes the point without a word.

---

## Three Alternative Discussion Questions

1. If someone asked you right now how many of your domain controllers have Defender for Identity sensors, could you answer without logging in to check?
2. Does your team treat Defender for Identity and Entra ID Identity Protection as covering the same ground, or do you have both deliberately deployed?
3. What is your biggest barrier to deploying Defender for Identity sensors across all domain controllers — licensing, operational complexity, or something else?

---

## Hashtags

#MicrosoftDefender #ActiveDirectory #MicrosoftSecurity #IdentitySecurity #MicrosoftMVP
