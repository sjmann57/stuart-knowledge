# Day 46 — LinkedIn Content Package
**Topic:** Microsoft Defender for Office 365 — the email security gap hiding in your M365 licence
**Category:** SecOps / Email Security
**Date:** 2026-07-21
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
A finance manager receives an email from the CEO. Urgent payment request, new supplier, needs processing today. The display name is right. The email passed the spam filter. Nothing looked unusual.
It was not from the CEO.

**Hook 2:**
Most organisations tell me they have email security in place.
They mean they have Microsoft 365. That includes Exchange Online Protection, which handles spam and known malware.
Exchange Online Protection is not Microsoft Defender for Office 365. The gap between them is where a significant proportion of successful phishing attacks land.

**Hook 3:**
Safe Links is on. Safe Attachments is configured. Anti-phishing policies are in place.
I know this because the tenant has Microsoft Defender for Office 365 Plan 2 and the built-in protection preset policy is enabled.
What it does not have is impersonation protection for the CEO, the CFO, or the five external domains that send the organisation its invoices.

---

## LinkedIn Article (Stuart's version — published 2026-07-21)
**Note:** Key changes from draft: EOP description expanded to include SPF/DKIM/DMARC email authentication checks; Safe Links explanation added in-line ("rewrites supported URLs and checks them again when the user clicks them, helping protect against malicious destinations that may have become unsafe after delivery"); licensing clarified to include G3/G5/A5; custom policies framing softened ("Custom policies remain an option, but they bring extra complexity and maintenance that, if not done right, often deliver little extra value"); key real-world human insight added: "Often, the people that need protection the most do not want it, and this is where we need to make security and protection as invisible as we can for our end users"; AIR nuance: "Depending on how automation is configured, remediation actions may require analyst approval" (more accurate than binary "requires approval"); close teaser added: "There is much more to talk about, such as whitelists and other elements, something for another post"; discussion question reworded to focus on "exactly which priority accounts are protected by impersonation detection".

A finance manager receives an email from the CEO

Urgent payment request. New supplier. Needs to be processed today before the close of business.
The display name is right. The email address looks correct at a glance. It passed the spam filter without issue.
It was not from the CEO.
Business email compromise is one of the most financially damaging attack types Microsoft Defender for Office 365 is specifically designed to address. And in most tenants I review, the controls that would have caught this are either not configured or are running at settings that would not have stopped it.
The protection ladder
Email protection in Microsoft 365 is not a single product. It is a layered stack.
Exchange Online Protection is included with every Microsoft 365 subscription that includes cloud mailboxes. It provides anti-spam filtering, anti-malware protection, connection filtering, anti-spoofing with spoof intelligence, email authentication checks using SPF, DKIM and DMARC, and quarantine. It is the baseline. It prevents broad, volume-based, known attacks well.
Microsoft Defender for Office 365 Plan 1 adds the controls that matter for targeted attacks: Safe Attachments for email and files stored in SharePoint, OneDrive and Microsoft Teams; Safe Links with time-of-click URL verification in email, Teams and Microsoft 365 apps; and critically, anti-phishing policies with user and domain impersonation protection and mailbox intelligence.
Safe Links rewrites supported URLs and checks them again when the user clicks them, helping protect against malicious destinations that may have become unsafe after the original email was delivered.
Microsoft Defender for Office 365 Plan 2 adds post-breach investigation and response: Threat Explorer for querying email and click data, Attack Simulation Training, Threat Trackers, and Automated Investigation and Response (AIR).
Plan 1 is included in Microsoft 365 Business Premium, Microsoft 365 E3 and Microsoft 365 G3. Plan 2 is included in Microsoft 365 E5, Microsoft 365 G5 and Microsoft 365 A5.
Many organisations I work with have Plan 1 or Plan 2 included in their licence and are functionally running at Exchange Online Protection level because the additional controls have never been configured.
The gap: preset security policies and impersonation protection
Microsoft provides three protection profiles: Built-in protection, Standard, and Strict.
Built-in protection applies basic Safe Links and Safe Attachments to all recipients in any organisation with at least one Defender for Office 365 licence. It is a safety net, not a security posture.
Standard and Strict preset security policies apply Microsoft's recommended settings across anti-spam, anti-malware, anti-phishing, Safe Links and Safe Attachments in one step. Microsoft's own guidance is to start with the Standard preset and apply Strict to priority accounts. Custom policies remain an option, but they bring extra complexity and maintenance that, if not done right, often deliver little extra value.
The most consequential gap I see is that impersonation protection is not configured.
Defender for Office 365 Plan 1 anti-phishing policies can protect specific users and domains from impersonation: your CEO, CFO, and other priority accounts, as well as trusted external supplier domains from which your organisation regularly receives invoices and instructions. Mailbox intelligence takes this further by learning each user's normal messaging behaviours and identifying messages that attempt to impersonate trusted contacts.
None of this is enabled by default in Exchange Online Protection. It requires Defender for Office 365 Plan 1 and deliberate configuration.
Often, the people that need protection the most do not want it, and this is where we need to make security and protection as invisible as we can for our end users.
Safe Attachments for SharePoint, OneDrive and Teams
Safe Attachments scanning for email is widely understood.
Safe Attachments for SharePoint, OneDrive and Microsoft Teams is a separate configuration that many organisations never enable.
When enabled, files uploaded to SharePoint and OneDrive are scanned asynchronously. If a file is later determined to be malicious, Defender for Office 365 blocks users from opening, downloading or sharing it. Files shared through Microsoft Teams receive the same protection.
This matters because many organisations assume that email attachment protection automatically extends to SharePoint and Teams. It does not unless this function has been configured.
Attack Simulation Training
Attack Simulation Training allows organisations to run realistic but harmless phishing simulations targeting their own users.
The value is not the simulation itself.
It is the feedback loop.
You learn which users click, which users report, which business units present the highest risk, and whether your awareness programme is genuinely improving behaviour over time.
Simulation automations allow you to run continuous campaigns instead of isolated exercises, covering multiple phishing and social engineering techniques.
Without that data, security awareness becomes difficult to measure.
Automated Investigation and Response (AIR)
AIR is available in Plan 2 and automatically starts investigations for supported alerts.
It correlates the affected email, determines who else received the same message, checks whether links were clicked, and builds a complete investigation with recommended remediation actions such as removing malicious messages from affected mailboxes.
Depending on how automation is configured, remediation actions may require analyst approval before execution.
I mentioned a few weeks ago that automated remediation in Defender XDR is switched off in many tenants. AIR investigations are often running, but in many environments I review, the investigation queue and recommended actions have not been reviewed for weeks.
Where to look today
Open the Microsoft Defender portal at security.microsoft.com.
Navigate to:
Email & collaboration > Policies & rules > Threat Policies
Review your preset security policies.
If Standard or Strict policies have not been applied, that is your starting point.
Next, review your anti-phishing policies and confirm that user impersonation protection covers your priority accounts and that domain impersonation protection includes the trusted external organisations from which your business regularly receives invoices or payment instructions.
Then review your Safe Attachments policies and confirm that protection for SharePoint, OneDrive and Microsoft Teams has been enabled.
If you are licensed, open Attack Simulation Training and check whether simulations are scheduled.
If none are running, you have no measurable data showing how susceptible your users are to phishing attacks.
Most email attacks do not bypass Microsoft Defender for Office 365.
They bypass the configuration that was never completed.
There is much more to talk about, such as whitelists and other elements, something for another post.
How long has it been since anyone in your organisation reviewed your anti-phishing policies, and do you know exactly which priority accounts are protected by impersonation detection?

---

## Microsoft Learn References

- [Microsoft Defender for Office 365 overview](https://learn.microsoft.com/en-us/defender-office-365/mdo-about)
- [Preset security policies in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies)
- [Safe Attachments in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-about)
- [Safe Attachments for SharePoint, OneDrive, and Microsoft Teams](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-for-spo-odfb-teams-about)
- [Safe Links in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/safe-links-about)
- [Anti-phishing policies in Microsoft 365](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-about)
- [Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started)
- [Automated investigation and response in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/air-about)

---

## Suggested Image Concept

Microsoft Defender portal showing the Preset security policies page with the Standard and Strict preset policies both showing as "Not applied" — demonstrating the common state before deliberate configuration, with the Built-in protection policy as the only active setting.

---

## Three Alternative Discussion Questions

1. How long has it been since anyone in your organisation reviewed the anti-phishing policy configuration, and do you know which users are covered by impersonation protection?
2. Has your organisation run Attack Simulation Training, and if so, which business unit presented the highest phishing susceptibility?
3. When you say your organisation has email security in place, do you mean Exchange Online Protection, Defender for Office 365 Plan 1, or Plan 2 — and does your security posture reflect that distinction?

---

## Hashtags

#MicrosoftDefender #EmailSecurity #DefenderForOffice365 #MicrosoftSecurity #ZeroTrust
