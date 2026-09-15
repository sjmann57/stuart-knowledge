# Day 77 — LinkedIn Content Package
**Topic:** Zero Trust implementation — from assessment to action
**Category:** Zero Trust / Security Architecture / Microsoft Security
**Week theme:** Zero Trust — principles, assessment, identity, and adoption (Days 74–77) — Week 11 close
**Date:** 2026-08-20 (Thursday)
**Format:** Technical article — Week 11 Day 4
**LinkedIn URL:** https://www.linkedin.com/pulse/zero-trust-implementation-from-assessment-action-stuart-mann-zfhre
**LinkedIn post (shortlink):** https://lnkd.in/p/eJjfGVNM

---

## LinkedIn Article (published — 2026-08-20)

Zero Trust implementation: from assessment to action

Running the Zero Trust Assessment gives you a baseline.

It tells you where you are.

The question that follows is how you turn that into a plan that actually gets executed.

I want to use this article to look at the part of Zero Trust that gets the least attention:

Not the technology, but the implementation model.

The technology problem and the programme problem

Most organisations that struggle with Zero Trust do not struggle because the technology is unavailable.

* The controls exist.
* The licences are often in place.
* The documentation is detailed.

What is often missing is a structured way to move from assessment output to prioritised, funded and sequenced work.

And then a way to sustain that work over the time it takes.

Zero Trust is not a project where you reach an end date, tick the box and move on.

It requires continuous improvement.

The three principles:

* Verify explicitly
* Use least privilege
* Assume breach

are not conditions you achieve once and then maintain passively.

They require ongoing configuration, monitoring, policy review and adaptation as your organisation, technology and threats change.

Microsoft describes security transformation and Zero Trust adoption as a long-term effort, with organisations continually improving controls as their business requirements, technology and threats change.

Microsoft's security adoption model for Zero Trust

Microsoft provides a structured model for moving security strategy into implementation.

The current security adoption model has three core components:

Business scenarios → Security disciplines → Technology pillars

Microsoft then provides technical solutions that connect those requirements to implementation guidance.

There is an important distinction between them.

Business scenarios define why you are investing.

Security disciplines define what security capabilities and organisational responsibilities are required.

Technology pillars define where those controls are applied.

Technical solutions describe how you implement them.

That distinction makes the model much more useful than simply starting with a list of Microsoft products.

Start with the business scenario

Rather than starting with technology, Microsoft's current security adoption model starts with business outcomes and risks that security and business leaders can understand.

The five current business scenarios are:

* Rapidly and securely adopt AI.
* Enable people to do their job securely from anywhere.
* Minimise business damage from security incidents.
* Identify and protect critical business assets.
* Continuously improve security posture and compliance.

This changes the conversation.

Instead of starting with:

"We need to deploy another Conditional Access policy."

You might start with:

"We need to reduce the business impact of compromised identities."

You can then work backwards into the security disciplines, controls and technologies needed to achieve that outcome.

That gives the technical work a business reason.

And importantly, it gives somebody a reason to fund it, often the most difficult part in many security projects.

Security disciplines

The next layer is security disciplines.

Terminology matters here.

Security disciplines are not simply another name for the seven Zero Trust technology pillars.

Microsoft uses disciplines to define areas of security ownership, accountability and capability needed to deliver business outcomes.

They cover the strategy, architecture, processes, controls and operational responsibilities needed to achieve the required security outcome.

Microsoft groups these disciplines across areas including planning and oversight, technical strategy and security operations.

This is the what.

What capabilities do we need to achieve the business outcome?

It also introduces something that can easily get missed in a technology-led Zero Trust programme:

Who owns it?

A control without ownership, review, and accountability can quickly become another configuration implemented once and then forgotten.

Technology pillars

Then we get to the technology pillars.

Microsoft's current security adoption model structures these around:

* Identities
* Endpoints
* Data
* Apps
* Infrastructure
* Network
* SecOps

These provide the technical boundaries where Zero Trust controls are applied.

This is the where.

Where in our environment do those security capabilities need to be implemented?

Microsoft Entra, Intune, Purview, Defender XDR, Defender for Cloud, Global Secure Access and Microsoft Sentinel can all provide technologies that implement parts of that architecture.

But this is an important point:

The product should come after the requirement, not before it.

You identify the business outcome.

You identify the security capability required.

You identify where the control needs to operate.

Then you decide which technology implements it.

That is a much stronger architecture discussion than starting with a Microsoft licence and asking what features we haven't switched on yet.

Technical solutions

The final layer brings this into implementation.

Microsoft's technical solutions provide detailed guidance for implementing controls across the technology pillars.

This is the how.

The distinction is useful:

Business scenario: Why?

Security discipline: What?

Technology pillar: Where?

Technical solution: How?

That gives you a route from a business requirement to technical implementation.

And for me, that is the important part.

You are no longer implementing a technology because it is available in your licence.

You are implementing a control because you can trace it back to a security capability and ultimately to a business requirement or risk.

The Zero Trust Workshop

Alongside the automated Zero Trust Assessment, Microsoft provides the Zero Trust Workshop.

The two are complementary.

The Assessment measures your current posture and identifies configuration gaps.

The Workshop helps you document progress and develop an actionable roadmap for Zero Trust implementation.

Microsoft describes the Workshop as a single-page application, supported by written workshop guidance for facilitators and participants.

One important point: Microsoft's Zero Trust material continues to evolve.

The current Workshop application now spans eight pillars, with DevSecOps added as a new pillar.

Microsoft Learn currently provides dedicated Workshop guidance covering Identity, Devices, Data, Networking, Infrastructure, SecOps and AI, while the current Workshop application has expanded that model to include DevSecOps.

That is different from the seven technology pillars in Microsoft's security adoption model.

They are related models used for different purposes, so I would not force them to be the same thing.

Microsoft also has separate detailed guidance for applying Zero Trust principles across DevOps platforms, developer environments and the software development lifecycle.

Assessment and Workshop together

What I like is how these two tools can complement each other.

The Assessment gives you evidence from your environment.

The Workshop helps you turn that understanding into a plan.

So in practice, I see the process as:

Assess where you are.

Understand the gaps.

Decide where you need to go.

Build the roadmap.

Then implement it.

That is much more useful than producing an assessment report that gets reviewed once, saved somewhere and forgotten.

Connecting assessment output to the adoption model

This is where the pieces start becoming useful.

An assessment finding by itself is a technical finding.

It might tell you that an identity control is missing, a device configuration is weak, or a network control needs attention.

But a technical finding doesn't automatically tell the business why it should be funded before something else.

The adoption model gives you another way to look at it.

Ask:

Which business outcome does this gap affect?

Which security capability needs to improve?

Where does the control need to be implemented?

What technical solution closes the gap?

That connection matters.

A finding that creates risk across several important business assets or blocks progress towards a strategic security outcome may deserve attention before another technically interesting finding with much less business impact.

It also gives you a different language for communicating with stakeholders.

A conversation about:

"Reducing the impact of an identity compromise on critical business systems"

lands differently from:

"We have some Conditional Access policy gaps."

They may describe parts of the same problem.

But one explains why the business should care.

The adoption path

Microsoft's current security adoption model gives us a logical way to approach implementation.

Start with the business scenario.

Identify the business outcome or risk that matters most.

Review the security disciplines.

Understand the strategy, architecture, ownership, processes and capabilities required to address it.

Map those requirements to the technology pillars.

Identify where the controls need to operate across identities, endpoints, data, apps, infrastructure, network and SecOps.

Implement through technical solutions.

Use the detailed implementation guidance to deploy the controls needed to support that outcome.

Then review the results and continue improving.

This matters because trying to fix every assessment finding at once is rarely realistic.

* Prioritise.
* Sequence the work.
* Identify dependencies.
* Assign owners.
* Measure progress.
* Then move to the next priority.

Zero Trust becomes a programme of measurable security improvement rather than a huge list of technologies somebody wants deployed.

Closing this week's mini-series

I have covered the Zero Trust foundations, the Zero Trust Assessment and the identity pillar in depth.

Today brings those pieces together into implementation.

Across these articles, the consistent theme is the same one that has run through this week's programme.

Knowing the framework exists is not the same as implementing it.

Having the tools available is not the same as running them.

Running an assessment is not the same as acting on the findings.

And buying the licences is definitely not the same as implementing Zero Trust.

Zero Trust is not a product you deploy.

It is a security strategy and a way of designing, implementing and continuously reviewing controls to reduce unnecessary trust across your environment.

Microsoft Entra, Sentinel, Purview, Defender, Global Secure Access and Agent 365 can all provide parts of that model.

But the products are only part of the answer.

The Assessment helps you understand your current posture.

The security adoption model connects security improvements to business outcomes.

The Workshop can help turn those requirements into an actionable roadmap.

And then comes the part that actually matters:

Doing the work.

If you have worked through a Zero Trust implementation, what was the part of the process that proved harder than expected?

---

## Microsoft Learn References

- [Zero Trust security adoption model](https://learn.microsoft.com/en-us/security/zero-trust/security-adoption-model)
- [Rapidly modernize your security posture for Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/adopt/rapidly-modernize-security-posture)
- [Zero Trust overview](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview)
- [Zero Trust Workshop overview](https://learn.microsoft.com/security/zero-trust/workshop-zero-trust-overview)
- [Zero Trust Assessment overview](https://learn.microsoft.com/en-us/security/zero-trust/assessment/overview)

---

## Hashtags

#ZeroTrust #MicrosoftSecurity #SecurityArchitecture #ZeroTrustAdoption #SecurityTransformation #MicrosoftEntra #Cybersecurity #CISO

---

## Notes

- Day 77 published post — Week 11 close. Zero Trust adoption framework and implementation model.
- Stuart added a fourth layer to the model (Technical solutions: the How), making it Business scenarios → Security disciplines → Technology pillars → Technical solutions.
- Why/What/Where/How framework is Stuart's own framing — very clear and memorable.
- Five current business scenarios confirmed from Microsoft's current security adoption model (different from draft which listed older scenarios).
- Security disciplines explicitly distinguished from technology pillars — ownership and accountability framing is new and strong.
- DevSecOps pillar noted as addition to Workshop application (eight pillars) vs seven in the adoption model — Stuart correctly notes these are different models for different purposes.
- Closing drops the "week 11 of what was a ten-week series" line from the draft — cleaner.
- "And buying the licences is definitely not the same as implementing Zero Trust" — added line, likely to land well.
- Metrics check due: 2026-09-20
