# Day 28 — LinkedIn Content Package
**Topic:** Intune device compliance — what your Conditional Access policy is actually enforcing
**Category:** Endpoint Security
**Format:** Technical article
**Note:** Builds on Day 8 (CA on but not controlling access) and Day 3 (Defender for Endpoint config gaps). Endpoint thread: Day 3 + Day 28.

---

## LinkedIn Article

Your Conditional Access policy says "require device to be marked as compliant."

Most organisations ticked that box months ago. What they rarely check is what the compliance policy behind it actually evaluates.

A device marked compliant in Intune is only as secure as the settings you chose to enforce. If you left most of the compliance policy at its defaults, you may have CA gating access on a signal that does not mean what you think it means.

The two-part setup organisations often get half right

Intune device compliance is a two-step process. First, you create a compliance policy in Intune that defines what a compliant device looks like. Second, you create a Conditional Access policy in Entra ID with the grant control "Require device to be marked as compliant."

Both steps are necessary. Microsoft is explicit on this: without a compliance policy created in Intune, that Conditional Access grant control will not function as intended. The CA policy is checking a compliance signal, and if there is no policy producing that signal, the control does not do what you expect.

There is also a tenant-level setting that catches teams out. In the Intune admin centre, under Devices > Compliance > Compliance policy settings, there is a default that determines how to treat devices with no compliance policy assigned. Out of the box, that default is set to Compliant. Any device not covered by a compliance policy passes the CA check automatically.

If your compliance policy is scoped to a specific group and you have devices sitting outside that assignment, they are getting through unevaluated.

What the settings actually check — and what they do not

Open a Windows compliance policy in Intune and most settings will be at "Not configured." Intune does not enforce anything it has not been explicitly told to evaluate.

Two settings are worth paying particular attention to.

The "Encryption of data storage on device" setting performs a basic OS drive check. The "Require BitLocker" setting is different. It uses Device Health Attestation at the TPM level, which provides a stronger and more tamper-resistant verification. If your policy uses the basic encryption check, you are not getting the same assurance as the BitLocker option. The difference matters, particularly on devices that could have had encryption bypassed before enrolment.

Secure Boot works on the same Device Health Attestation mechanism. It requires a device with TPM 1.2 or later.

Firewall status, Microsoft Defender Antimalware, and real-time protection are all "Not configured" by default. If you want compliance to evaluate those, you need to turn them on explicitly.

Security baselines are not a replacement for compliance policies

Intune includes security baselines under Endpoint security > Security baselines. These push configuration to devices. The current version for Windows is version 25H2. A baseline can enable BitLocker for removable drives, enforce password requirements, disable basic authentication, and apply dozens of other hardening settings.

But a security baseline and a compliance policy do different things.

A baseline configures the device. A compliance policy evaluates the device's current state and tells Entra ID whether it meets your requirements. CA then acts on that signal.

You need both. The baseline gets the device into the right state. The compliance policy confirms it is in that state and reports accordingly.

Practitioner take

When I review customer Intune environments, the pattern I see most often is a compliance policy configured quickly during a deployment project, with most settings left at "Not configured." The CA policy is in place, devices are showing as compliant, and the team is confident the control is working.

What they have is a CA policy that gates access on a signal that is not checking the things they assumed it was.

The other gap I see is scope. A compliance policy that targets one group of devices is not a compliance policy for the whole organisation. Understanding what is and is not covered by your policy assignment is as important as what the policy itself contains.

Where to look today

Open the Intune admin centre and go to Devices > Compliance > Policies. Select your Windows compliance policy and check which settings are configured versus left as "Not configured."

Look specifically at whether the BitLocker setting uses Device Health Attestation or the basic encryption check.

Then go to Devices > Compliance > Compliance policy settings and check the default for devices with no policy assigned.

Those three checks will tell you whether your compliant device signal is doing what you expect it to do.

I wrote about the broader Conditional Access gap back on Day 8. Compliance policy enforcement is often where that gap sits.

What does your Windows compliance policy actually check? Have you reviewed it recently, or is it set up the way it was on day one?

---

## Microsoft Learn References

- [Device compliance policies overview — Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/device-compliance-get-started)
- [Windows compliance settings — Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/compliance-policy-create-windows)
- [Require compliant device — Conditional Access grant control](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-grant#require-device-to-be-marked-as-compliant)
- [Use security baselines to configure Windows devices — Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/security-baselines)
- [Monitor Intune device compliance policies](https://learn.microsoft.com/intune/device-security/compliance/monitor-policy)

---

## Suggested Image Concept

Dashboard view of Intune compliance policy settings, showing most settings as "Not configured" — with the BitLocker row highlighted. Simple, factual, makes the point immediately.

---

## Three Alternative Discussion Questions

1. When did you last audit what your Intune compliance policies are actually checking versus what you assumed they were checking?
2. Have you deployed Intune security baselines alongside your compliance policies, or are you using one without the other?
3. Do you know what happens in your tenant when a device has no compliance policy assigned — does it default to compliant or noncompliant?

---

## Hashtags

#MicrosoftIntune #ConditionalAccess #MicrosoftSecurity #EndpointSecurity #MicrosoftEntra
