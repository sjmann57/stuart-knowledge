# Day 42 — LinkedIn Content Package
**Topic:** Entra ID Governance Lifecycle Workflows — automating the gaps your HR system leaves behind
**Category:** Identity / Governance
**Date:** 2026-07-15
**Format:** Technical article

---

## Three Alternative Hooks

**Hook 1 (draft uses this):**
A new employee joins on Monday. By Thursday they still do not have the right group memberships, their manager has sent three emails to IT, and they logged in for the first time using a temporary password someone read out over Teams.
That is the Joiner problem. Most organisations with Microsoft Entra ID Governance have a solution for it that has never been switched on.

**Hook 2:**
Someone handed in their notice on a Friday. They left on the following Friday. Their Microsoft 365 account was still active the Monday after that.
That gap is where insider risk begins. Microsoft Entra ID Governance Lifecycle Workflows can close it automatically.

**Hook 3:**
Every organisation I review manages joiners, movers, and leavers the same way.
Manually. With emails. And a shared IT inbox that nobody owns.

---

## LinkedIn Article (Stuart's version — published 2026-07-15)
**Note:** Key changes from draft: added "identity-driven" framing vs traditional provisioning scripts; TAP delivery reframed as "organisation delivers using its approved secure process" (more enterprise-neutral, removes direct manager-email dependency assumption); group limitation clarified as "assigned cloud-only security groups"; leaver gap expanded with realistic scenario (resign Friday/leaving date changes/IT not informed); Mover section strengthened with specific Finance group example; TAP gotcha simplified to "confirm TAP authentication is enabled" (removed nuanced user-must-have-no-auth-methods detail); close aphorism adjusted to "It usually fails during the days between someone joining or leaving the organisation and their identity being updated to reflect reality."

A new employee joins on Monday.
By Thursday, they still do not have the correct group memberships; their licence has been assigned manually; and their manager has sent three emails to IT asking what is happening. They set up their first sign-in using a temporary password, which someone read aloud over Teams.
That is not an edge case.
It is what identity lifecycle management looks like in many organisations before Microsoft Entra Lifecycle Workflows is configured.

What Lifecycle Workflows does

Lifecycle Workflows automate the tasks your organisation currently performs manually across the three phases of a user's identity lifecycle: Joiner, Mover and Leaver.

Unlike traditional provisioning scripts, Lifecycle Workflows are identity-driven. They respond to changes in Microsoft Entra user attributes rather than relying on an administrator to manually start the process.

A workflow is made up of execution conditions and tasks.

The execution conditions define who is in scope, for example, all new hires in the UK office, and when the workflow runs, such as two days before the employeeHireDate attribute.

The tasks are the actions that are performed automatically when those conditions are met.

Workflows can run on a schedule against users whose attributes match the defined scope, or they can be started on demand.

The Joiner gap: day one access without manual steps

For new hires, one of the most valuable workflow combinations I see organisations missing is generating a Temporary Access Pass before the user's first day and notifying the hiring manager that onboarding is ready.

The organisation can then deliver the Temporary Access Pass using its approved secure process.

The new starter uses the Temporary Access Pass to register a passwordless or phishing-resistant authentication method on day one, rather than relying on a temporary password. For many organisations, this becomes the first practical step towards passwordless authentication.

Beyond authentication, Lifecycle Workflows can add new starters to Microsoft 365 groups and assigned cloud-only security groups, assign licences, add users to Microsoft Teams, and initiate access package assignment requests before the employee starts work.

There is one important limitation on group tasks.

Lifecycle Workflows support Microsoft 365 groups and assigned cloud-only security groups.
They do not support mail-enabled security groups, distribution lists, dynamic groups or role-assignable groups.

If your access model relies heavily on those group types, that affects what can be automated.

The Leaver gap: the risk of manual offboarding

The security case for automating leaver workflows is straightforward.

Manual offboarding depends on the right information reaching the right people at the right time.

In practice, there is almost always a gap.

Someone resigns on a Friday. Their leaving date changes. HR updates one system, but IT is not informed. The account remains active. Access to SharePoint, Teams and Exchange Online continues longer than intended.

That is often where identity governance starts to break down.

Lifecycle Workflows can trigger tasks using the employeeLeaveDateTime attribute, including revoking sign-in sessions, disabling the account, removing supported group memberships, removing licence assignments and scheduling account deletion after a defined period.

These actions can be staged over time.

You might revoke sign-in sessions on the employee's last day, disable the account immediately afterwards, remove licences several days later, and schedule account deletion after thirty days to allow time for mailbox handover where required.

One limitation is worth remembering.

The disable user and delete user tasks do not support users with active Microsoft Entra role assignments or membership of role-assignable groups.

Those privileged accounts require additional governance before those workflow tasks can complete successfully.

The Mover gap: the most overlooked part of identity governance

Most organisations have thought about joiners and leavers.

Movers are where I consistently find the biggest governance gap.

When someone changes department, manager or business unit, their access should change with them.

In many organisations, it does not.

Group memberships from previous roles accumulate.
Licences remain assigned for applications the user no longer needs.
Nobody notices that someone who left the Finance department two years ago still belongs to three Finance security groups.

Lifecycle Workflows can be triggered by attribute changes, such as department or job title.

They can notify a manager, remove configured group memberships associated with the previous role, initiate new access package assignments and perform other tasks appropriate for the user's new position.

Licensing

Lifecycle Workflows require Microsoft Entra ID Governance, either as the standalone product or as part of Microsoft Entra Suite.

This capability is separate from Microsoft Entra ID P1 and P2 licensing.

If you plan to use the Temporary Access Pass as part of onboarding, confirm that Temporary Access Pass authentication is enabled before configuring the workflow.

Without it, Temporary Access Pass generation cannot complete successfully.

Where to look today

Open the Microsoft Entra admin centre and navigate to:

Identity Governance > Lifecycle Workflows

If no workflows exist, that is your starting point.

Review the built-in templates for pre-hire onboarding, new-hire onboarding, and leaver offboarding.

They provide an excellent starting point that can be customised rather than building every workflow from scratch.

Then review the attributes your workflows depend on.

Lifecycle Workflows are triggered by attributes such as employeeHireDate and employeeLeaveDateTime.

If those values are not populated from your HR system, the workflows cannot trigger automatically.

Identity governance rarely fails during design.
It usually fails during the days between someone joining or leaving the organisation and their identity being updated to reflect reality.

How long does it typically take your organisation to fully provision a new starter or revoke a leaver's access on their final day?

---

## Microsoft Learn References

- [What are lifecycle workflows?](https://learn.microsoft.com/entra/id-governance/what-are-lifecycle-workflows)
- [Lifecycle Workflow built-in tasks](https://learn.microsoft.com/entra/id-governance/lifecycle-workflow-tasks)
- [Microsoft Entra ID Governance deployment guide for employee lifecycle automation](https://learn.microsoft.com/entra/architecture/governance-deployment-employee-lifecycle)
- [Manage inactive users using Lifecycle Workflows](https://learn.microsoft.com/entra/id-governance/lifecycle-workflow-inactive-users)
- [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/entra/id-governance/licensing-fundamentals)

---

## Suggested Image Concept

Microsoft Entra admin center showing the Lifecycle Workflows page with two or three workflow templates visible — "Onboard new hire employee" and "Offboard an employee" — with their trigger conditions shown. Demonstrates that the built-in templates exist and are ready to configure, not build from scratch.

---

## Three Alternative Discussion Questions

1. How long does it typically take your organisation to fully provision a new starter or revoke a leaver's access on their final day?
2. Has your organisation automated any part of the Joiner, Mover, or Leaver process with Lifecycle Workflows, and which phase delivered the most immediate value?
3. What is the biggest barrier to automating your leaver process — the HR attribute data not being in Entra ID, the licence requirement, or the internal process to get sign-off on automation?

---

## Hashtags

#MicrosoftEntra #IdentityGovernance #LifecycleWorkflows #MicrosoftSecurity #ZeroTrust
