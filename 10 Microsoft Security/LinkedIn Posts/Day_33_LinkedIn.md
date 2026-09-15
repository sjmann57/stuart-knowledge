# Day 33 — LinkedIn Content Package
**Topic:** Microsoft Purview DLP — policies in simulation mode that never get turned on
**Category:** Security Strategy / Compliance
**Format:** Technical article
**Note:** Stuart's published version. First Purview article. Key Stuart changes: Copilot/Copilot Chat added to locations (some GA, some preview); E3 clarified to include Teams files (stored in SharePoint/OneDrive) but not chat/channel messages; endpoint onboarding corrected to "via Microsoft Defender for Endpoint" (not Purview); "obvious business complexities" caveat added to policy tips section; removed "most common" → "a common state".

---

## LinkedIn Article (Stuart's version — published)

Your DLP policies are in simulation mode. There they will stay, unless someone makes a decision.
This is a common state I find Microsoft Purview Data Loss Prevention in when I review customer environments. Policies exist, simulation results were reviewed once, someone spotted too many false positives, and the move to enforcement got deferred. Months later, the policies are still watching without acting.
A policy in simulation mode does not block anything. It observes, generates data, and then that data expires after 30 days.
What DLP actually protects, and what it does not
Microsoft Purview DLP can cover a wide range of locations: Exchange email, SharePoint sites, OneDrive, Teams chat and channel messages, Windows and macOS endpoint devices, and Microsoft 365 Copilot and Copilot Chat interactions. However, some Copilot DLP controls are generally available, while others remain in preview.
Here is the part many teams miss when it comes to licensing.
Microsoft 365 E3 covers DLP for Exchange, SharePoint, and OneDrive, including files shared through Teams because Teams stores files in SharePoint and OneDrive. Teams chat and channel message DLP require Microsoft 365 E5. Endpoint DLP, which monitors what users do with sensitive files on their Windows and macOS devices, also requires Microsoft 365 E5 or an equivalent Microsoft Purview compliance add-on.
If you are utilising only E3 licences and DLP policies that include Teams chat, Teams channel messages, or endpoint devices, those locations require Microsoft 365 E5 or the appropriate compliance add-on. The policy exists, but those workloads are outside your licence entitlement.
The simulation mode trap
DLP simulation mode is the right place to start. Microsoft designed it specifically for tuning policies before enforcement; you can see what the policy would have caught without impacting users. The problem is not that you use simulation mode. The problem is that policies remain in simulation mode.
When a policy runs in simulation mode, the results are available for 30 days. After that, the data expires. If the team does not review the results within that window and make a decision, the data will be lost. The policy continues running in simulation mode, generating a fresh 30 days of data that will also expire unreviewed.
The typical reason enforcement gets deferred: false positives. A policy that detects credit card numbers will fire on finance teams processing payments, HR handling employee data, and customer service reviewing account information, all of which are legitimate use cases. Seeing the volume of matches in simulation mode, without a plan for handling overrides, leads to paralysis.
The policy design problem underneath
There are two common approaches for most false positives.
The first is policies that are too broad. Flagging any document or email containing a credit card number, without context or thresholds, catches too much legitimate activity. DLP uses deep content analysis; you can set thresholds, require specific counts, and add conditions based on the recipient or whether the content is being shared externally, but many default templates remain unconfigured.
The second is enforcement being positioned as the only alternative to simulation. It is not.
Policy tips are a middle step that is consistently underused. Before blocking, you can show users a pop-up notification explaining what the policy detected and why the action is restricted. Users can acknowledge the tip and provide a business justification for an override. This changes behaviour without creating a blocking incident, and it gives your team real data on how often users genuinely need to do the thing the policy is flagging.
The recommended path: simulation mode first, then policy tips visible, then enforcement. Each stage gives you data to tune the policy before the next one. The obvious business complexities should never be underestimated as well.
Endpoint DLP, the extra step most teams skip.
Endpoint DLP extends coverage to Windows 10, Windows 11, and the three most recent macOS versions. It monitors what users do with sensitive files on their devices: copying to USB drives, uploading via browsers to cloud services, copying to the clipboard, printing, and other supported activities.
To use Endpoint DLP, devices need to be onboarded via Microsoft Defender for Endpoint. Although managed from Microsoft Purview, onboarding uses the same deployment methods and tooling as Defender for Endpoint. If devices are not onboarded, the Devices location in your DLP policy does nothing.
Once an Endpoint DLP policy is updated, it typically takes about 1 hour to synchronise with managed devices before it takes effect.
Where to look today
Open the Microsoft Purview portal > Data loss prevention > Policies.
Look at how many of your policies are in simulation mode versus in enforcement mode. Look at when the simulation was last reviewed. Check whether your Teams chat, Teams channel messages, and endpoint locations are covered by the licences your users actually have.
If the list shows mostly simulation mode with review dates from months ago, that is the gap.
DLP without enforcement is a monitoring tool. Monitoring without action is a log nobody acts on.
Have you moved your DLP policies from simulation mode to enforcement, or is that decision still pending?

---

## Microsoft Learn References

- [Learn about data loss prevention — Microsoft Purview](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp)
- [Learn about data loss prevention simulation mode](https://learn.microsoft.com/en-us/purview/dlp-simulation-mode-learn)
- [Create and deploy data loss prevention policies](https://learn.microsoft.com/en-us/purview/dlp-create-deploy-policy)
- [Learn about Endpoint data loss prevention](https://learn.microsoft.com/en-us/purview/endpoint-dlp-learn-about)
- [Data loss prevention and Microsoft Teams](https://learn.microsoft.com/en-us/purview/dlp-microsoft-teams)

---

## Suggested Image Concept

Microsoft Purview portal DLP Policies page showing multiple policies all in "Simulation" state — with a column showing last reviewed dates from several months ago. Makes the point without a word.

---

## Three Alternative Discussion Questions

1. What made you finally move your DLP policies from simulation mode to enforcement — and what convinced the business it was the right time?
2. Have you used DLP policy tips as a middle step before blocking, or did you go straight from simulation to enforcement?
3. Does your team know which DLP workloads your current licence actually covers — specifically whether Teams and endpoint devices are included?

---

## Hashtags

#MicrosoftPurview #DataLossPrevention #MicrosoftSecurity #InformationProtection #MicrosoftCompliance
