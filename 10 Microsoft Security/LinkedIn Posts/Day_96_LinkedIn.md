# Day 96 — LinkedIn Content Package
**Topic:** Explaining security to the board — the business lens
**Category:** Security Leadership / Business of Security
**Week theme:** Week 14 — the closing arc (Days 95–100)
**Date:** 2026-09-08 (Tuesday)
**Format:** Business / leadership perspective post
**LinkedIn URL:** https://lnkd.in/p/e9wKiwuz

---

## LinkedIn Article (final — ready to post, 2026-09-08)

Explaining security to the board

Yesterday I wrote about how the Microsoft security stack fits together as an architecture.

Today I want to change register completely, because the technical architecture is only half the job.

The other half is explaining it to people who don't care about any of it.

Not because they aren't interested in security.

Because they are interested in the business, and security becomes relevant when you connect it to something the business already cares about.

That translation is one of the most valuable and least practised skills in our field.

The language gap

Security teams talk about controls, products, CVEs and configurations.

Boards and executives generally need a different language.

* Revenue.
* Cost.
* Risk.
* Reputation.
* Regulation.
* Growth.
* Continuity.

When those two languages meet in a room, the result can be a security leader explaining Conditional Access and multifactor authentication to a group of people quietly wondering what any of it has to do with the business.

The technology isn't necessarily the problem.

The translation is.

Microsoft's current Security Adoption Framework makes exactly this connection. It describes business scenarios to connect business risk to security outcomes and provide a common language between business and technical stakeholders.

What a board actually wants to know

Strip away the detail, and most leadership conversations come down to a handful of things.

* Are we going to end up on the front page?
* If something goes wrong, can we keep operating?
* Are we spending the right amount, not too little and not too much?
* Are we meeting our legal and regulatory obligations?

And increasingly:

* Can we adopt AI without creating a new class of risk?

Those aren't really technical questions. They are business questions with a security dimension. Your job is to answer them in the language they were asked in.

Start with the business, not the technology

This is something Microsoft's current Security Adoption Framework gets right.

It starts with business scenarios, rather than individual security products.

Microsoft's current scenarios include:

* Rapidly and securely adopt AI, including protecting data.
* Enable people to work securely from anywhere.
* Minimise business damage from security incidents.
* Identify and protect critical business assets.
* Continuously improve security posture and compliance.

Those are outcomes a business leader can understand.

Microsoft then maps those outcomes through security disciplines and technology pillars before getting down to technical solutions.

I wrote about that framework a few weeks ago, and it stuck with me because it reverses how many technical people present security.

We tend to start at the bottom:

* Here is the control. Here is what it does.

The board starts at the top:

* Here is the outcome we care about.

The skill is meeting them at the top and working down, rather than starting at the bottom and hoping they follow you up.

"We need another Conditional Access policy" is a technical statement.

"We need to reduce the likelihood that a compromised identity can reach our critical business systems, and limit the impact if one does" is the business risk we are trying to address.

Conditional Access might then be one of the controls that helps us achieve it.

Same technology.

Very different conversation.

Microsoft's own guidance now describes business scenarios as a mechanism for making decisions about investment, priorities, trade-offs and resource allocation without requiring business leaders to work through deep technical detail.

Risk, not Fear

There is a wrong way to do this, and I have seen it plenty of times.

Fear.

* The breach headlines.
* The scary statistics.
* The implication that disaster is one click away unless the budget gets approved.
* It might get attention.

But repeatedly using fear instead of evidence can quickly damage your credibility.

The better conversation is about risk.

* What could happen?
* How likely is it?
* What would the impact be?
* Which parts of the business would be affected?
* What controls do we already have?
* What gaps remain?
* What does the proposed investment change?

Not:

* "We might get breached."

But:

* "Here is our exposure. Here is what we are doing about it. Here is the residual risk. And here is the decision we need the business to make."

That last part matters.

Mature security isn't about promising to eliminate risk. You can't.

It is about understanding risk and making informed decisions about how you respond to it.

* Avoid it.
* Reduce it.
* Transfer it.
* Or consciously accept it.

That also means the security team doesn't own every business risk decision.

Our job is to make the risk understandable so the people with the right accountability can make an informed decision.

Microsoft's current security adoption guidance similarly puts business leaders into the decision-making process around cybersecurity risk, investment, trade-offs and resource allocation.

Security as an enabler, not just a cost

The other shift is harder, but important.

Security is often presented as a cost.

A tax on doing business.

The department that says no.

The stronger position is security as an enabler.

* The reason the business can adopt AI with confidence.
* The reason it can win a contract that requires particular security or compliance requirements.
* The reason it can operate in a regulated market.
* The reason customers can trust it with their data.
* The reason an incident doesn't have to become a business-ending event.

Microsoft makes a similar argument in its adoption guidance, positioning security as something aligned to business outcomes rather than an isolated technology function. Its current AI scenario specifically focuses on adopting AI quickly while protecting sensitive data and maintaining business resilience.

When security is only seen as a cost, every investment becomes a conversation about reducing spend.

When security helps the organisation achieve something it wants to do, the conversation changes.

That reframing isn't spin.

It is explaining the same work in terms of what it enables, as well as what it prevents.

This is something I've learned as an architect

I've had many conversations where I know the technical answer.

That isn't always enough.

* You can produce a technically excellent design.
* You can explain exactly how the control works.
* You can have all the evidence.

And still lose the room.

Because the people listening aren't necessarily asking:

"How does this technology work?"

They are asking:

* "Why should I care?"
* "What happens if we don't do it?"
* "What does this allow us to do?"
* "Why should I spend money on this rather than something else?"

That has changed the way I approach these conversations.

I still want to understand the technical detail. I think you have to.

But I don't necessarily start there.

If I am talking to a technical team, we can discuss Conditional Access policies, attack paths, DLP rules, Sentinel ingestion or Defender configuration.

If I am talking to a business leader, I need to translate those same controls into:

* Risk.
* Impact.
* Resilience.
* Cost.
* Opportunity.
* Outcome.

The technology hasn't changed.

The audience has.

Recognising that difference is part of being an architect.

Why this matters even if you are technical

You might be reading this thinking:

I'm an engineer, not a CISO. This isn't my job.

I would disagree.

* You don't need to become a salesperson.
* You don't need to turn every technical conversation into a board presentation.
* But you should be able to answer one very simple question:

So what?

* Why does this vulnerability matter?
* Why does this identity need protecting?
* Why does this architecture need changing?
* Why does the organisation need to spend money fixing it?
* What happens if we do nothing?

The ability to explain those things makes your technical knowledge much more useful.

Microsoft's current guidance reflects the same principle. Security disciplines sit between business scenarios and technical implementation specifically to help translate business priorities into measurable security outcomes.

The best architecture in the world doesn't get funded, staffed or prioritised if nobody can explain its value to the people making those decisions.

Knowing the technology is important.

Being able to translate it is what turns technical knowledge into business influence.

So the next time you ask for security investment, think about how you are making the case.

Are you explaining the controls?

Or are you explaining the business outcome those controls are there to protect?

---

## Microsoft Learn References

- [Zero Trust security adoption model](https://learn.microsoft.com/en-us/security/zero-trust/security-adoption-model)
- [Security adoption business scenarios overview](https://learn.microsoft.com/en-us/security/zero-trust/security-adoption-business-scenarios-overview)
- [Zero Trust adoption framework overview](https://learn.microsoft.com/en-us/security/zero-trust/adopt/zero-trust-adoption-overview)

---

## Hashtags

#SecurityLeadership #CISO #Cybersecurity #RiskManagement #SecurityStrategy #MicrosoftSecurity #BoardroomSecurity #BusinessOfSecurity

---

## Notes

- Day 96 — Week 14, the business-lens post. Deliberate register change from Day 95's architecture piece.
- Core argument: translation from technical language to business language (risk, cost, reputation, regulation, enablement) is the differentiating skill.
- Anti-FUD stance: honest risk and accepted-risk framing beats fear-based selling.
- Ties back to Day 77 (Zero Trust adoption framework's business-scenario approach).
- Security-as-enabler reframe is the strategic heart of the post.
- Strongest differentiator of the finale week: shows Stuart can operate at leadership level, not just technical.
- One [STUART'S PERSPECTIVE] slot — a real story of a recommendation landing (or not) based on framing.
- Closing question makes the reader self-assess — good comment driver.
- Metrics check due: 2026-10-08
