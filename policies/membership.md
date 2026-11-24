# Membership

**Status: Draft**

| Role | What they do | How you get it |
| --- | --- | --- |
| **Contributor** | Anyone opening issues, PRs, discussions | Show up |
| **Maintainer** | Write access on a project's repos; makes technical calls for that project | Invited by the project's maintainers and Team Lead |
| **Team Lead** | One or more per project. Coordinates releases, represents the project, makes sure it doesn't depend on one person, and posts a short monthly update | Chosen by the project's maintainers |
| **Steering Committee** | 3–5 people. Handles money and the fiscal host, approves new projects and archives, appoints the Security & Infra team, resolves disputes, makes emergency calls. Doesn't run day-to-day development | Appointed by the Steering Committee, 1-year renewable terms |
| **Security & Infrastructure team** | 2–5 people who hold the keys: GitHub/npm org settings, domains, password vault, CI. Grants and removes access as decided by the Steering Committee, and can act alone during a security incident | Appointed by the Steering Committee |
| **Emeritus** | Honorary status for people who've stepped back. Credit kept, no access or votes | Stepping down, or 6 months inactive |

**Teams:** each project (or group of related repos, such as R3F, Drei, Zustand, Rendering Tools) is a team with its own maintainers and Team Lead. A new team, or archiving one, needs Steering Committee approval.

## Steering Committee

The Steering Committee is a small group that handles what no single project should handle alone. It serves the members. It doesn't run day-to-day development.

- **Size and terms.** 3–5 people serving one-year terms, which can be renewed. At least 60 days before a term ends, each member says whether they're staying on, so nobody is left guessing who's active.
- **What it handles.** Money and the fiscal host. Approving new projects, initiatives and archives. Appointing the Security & Infrastructure team. Project deadlocks, disputes, and anything touching several projects. Security and legal emergencies.
- **What it doesn't do.** Set project roadmaps, review PRs, or overrule maintainers on technical calls.
- **How it decides.** Lazy consensus within the committee. If someone objects, the committee takes a majority vote. Removing someone for cause needs two-thirds (see [Stepping away and coming back](#stepping-away-and-coming-back)).
- **Accountability.** Every meeting gets a public summary, and any decision can be appealed to the members (see [If you disagree](#if-you-disagree)).

### Meetings

- **Monthly by default.** The committee sets the day and time to suit its time zones. A meeting can be moved, or skipped if there's nothing on the agenda.
- **Open agenda.** Any member can add an item before the meeting.
- **Live or async, both count.** To attend async, post your update on the agenda and answer your action items before the meeting, or reply to the summary within 48 hours.
- **Summary within 72 hours.** It covers decisions, action items with owners, and open threads. Committee members take turns writing it.
- **Missed meetings.** If someone misses three in a row, live or async, another committee member checks in with them privately. It's a check-in, not a penalty. The formal rule is still 6 months of inactivity → Emeritus.

### Team Lead updates

Each Team Lead posts a short monthly update: progress, blockers, and anything the Steering Committee should know. Joining the call is welcome but not required. The written update is what counts.

## Stepping away and coming back

Roles are temporary. People change jobs, have kids, lose interest, and come back years later, and all of that is normal. Here's how it works.

### How a role ends

There are three ways. All of them keep the person's credit.

**a) Stepping down.** You tell us you're stepping back. We thank you, move you to **Emeritus**, and remove access.

**b) Inactivity.** If someone with elevated access (Steering, Team Lead, Security & Infra, GitHub/npm Owner) has had **no activity for 6 months**, they move to Emeritus and their access is removed. Activity means commits, reviews, governance discussion, votes, or meetings. Nobody has to make an awkward call, and life events are expected. It's just keeping the keys current.

**c) For cause.** For a breach of trust, bad faith, or a policy violation, the Steering Committee:

1. writes down the reason and shares it with the person,
2. gives them **14 days to respond**,
3. decides by a **two-thirds vote** of the Steering Committee.

What happens to access afterwards, and emergency suspensions during security incidents, are covered under [Who holds access](./security.md#who-holds-access) on the Security page.

### Emeritus and founders

**Emeritus** is a permanent honorary status for people who built and carried Poimandres. Emeritus members are listed publicly, credited in the projects they shaped, and always welcome in community spaces. They hold no admin access and no votes.

**Founders** are recognized as founders, permanently. Founding the collective or a project earns lasting credit and respect. It doesn't earn standing control of the org, a repo, or its direction. The collective was built on that idea ("stewardship over ownership"), and it protects every project from depending on any one person, founders included.

### Coming back

We want people to come back.

1. **Just start contributing.** Issues, PRs, discussions. You're on the same footing as every other contributor.
2. **Write and maintainer access** come back through the repo's current maintainers, once you're active again, the same way anyone gets it.
3. **Elevated roles** (Team Lead, Steering, Security & Infra, Owner) come back by Steering Committee decision, based on what you're doing now. They're never restored automatically to whatever level you held before.

Who sets a project's direction, and what you can take with you, is on the [Ownership](./ownership.md) page.

## If you disagree

The Steering Committee doesn't get the last word. The members do. Anyone affected by a decision can challenge it, including people who are Emeritus or no longer involved.

**Step 1: Ask the Steering Committee to reconsider.** Write up what you disagree with and why, and post it in the governance channel or a GitHub discussion. The Steering Committee answers in writing within **14 days** and either changes the decision or explains why not. Anyone on the committee who made the original call can't be the only one answering.

**Step 2: Take it to the members.** If you still disagree, ask for a member vote. It needs **3 members to back it**, so a single person can't force endless votes, but a real concern can't be bottled up either. You don't have to be a member yourself to ask.

- The vote is open to all active members (maintainers, Team Leads, Steering, Security & Infra) for **7 days**.
- A **simple majority of votes cast** overturns the decision. Steering members vote as ordinary members, with no extra weight.
- The result is final and recorded publicly.

**While an appeal is open,** the decision stays in effect. That matters most for security: removed access stays removed until the appeal is decided.

Disagreement is welcome. Pressuring individual maintainers, or trying to take repos, packages, or names back unilaterally instead of using this process, is not, and it can lead to removal for cause.
