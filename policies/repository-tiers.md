# Repository tiers

**Status: Draft**

Not every repo under `pmndrs/` gets the same promise from the org, and users deserve to know which is which before they depend on one. Every repo has a **tier**. The tier describes what we commit to. It says nothing about how good the code is, and repos move up and down tiers as normal.

### Adopted: the org has taken responsibility. Can't be transferred out.

| Tier | Name | What the org promises | Maintainers needed | Who sets direction |
| --- | --- | --- | --- | --- |
| **0** | **Core** | Long-term maintenance, full security response, regular releases | 3+ active and a Team Lead | Maintainers day to day. Breaking redesigns, renames, deprecation, or moving out of the org need the Steering Committee (and a member vote for the biggest) |
| **1** | **Maintained** | Actively developed and released | 2+ active | Maintainers. Renaming or deprecating needs Steering sign-off |
| **2** | **Supported** | Kept alive even if the original maintainer leaves: security fixes, critical bugs, ecosystem updates. Possibly slow | 1 named org caretaker | Caretaker. Deprecation needs Steering sign-off |

### Hosted: still the maintainer's or owner's. Can be moved out at any time.

| Tier | Name | What the org promises | Maintainers needed | Who sets direction |
| --- | --- | --- | --- | --- |
| **3** | **Hosted** | Hosting, visibility, security reports routed. Best effort only | 1 active (usually the author) | The maintainer |
| **4** | **Experimental** | Showcased, not for production, no promises. Reviewed periodically | Whoever's working on it | Whoever's working on it |
| **S** | **Stewarded** | Held for safekeeping at the owner's request. Kept online, security reports passed to the owner. Never an org project | The owner, if anyone | The owner |

**Tier 5, Archived:** read-only, kept for reference. An archived repo stays on whichever side it was on: an archived adopted repo is still the org's, and an archived hosted repo is still the maintainer's.

## Who can take a repo out: the adoption line

There are two kinds of repo in the org:

- **Hosted (Tiers 3–4):** the repo is still the maintainer's, living in the org. The maintainer can move it back out **at any time**. Tell the Steering Committee and we'll do the transfer. No vote, no justification needed.
- **Adopted (Tiers 0–2):** the org has taken responsibility for keeping it alive, and users depend on that promise. **Adopted repos aren't transferred out of the org, by anyone.** They can still be demoted or archived under the normal rules, but the repo stays in `pmndrs/`.

**Adoption is a one-way door, and it happens once, on purpose.** A repo is adopted when it first moves to Tier 2 or higher. There are two ways in:

1. **With the maintainer's consent (the normal path).** The Steering Committee proposes adoption and the maintainer agrees in writing.
2. **When the maintainer has disappeared.** Sometimes a hosted repo that people depend on is left behind. If the maintainer has had no activity for **6+ months** and hasn't replied to a notice sent through GitHub and any known contact, with **30 days** to respond, the Steering Committee can put adoption to a **member vote** (7 days, simple majority). If the vote passes, the org takes responsibility so users aren't stranded. If the maintainer comes back before the vote closes, it stops and their consent is needed again.

**Once adopted, always adopted.** Demoting or archiving an adopted repo doesn't hand it back. If anyone, including the original author, wants to carry an archived project on elsewhere, they fork it.

**Forking is always allowed, for every tier, for everyone.** The code is open source. You can fork any pmndrs repo at any time and take it in any direction. The fork lives outside the org under its own name. What you can't take is an adopted repo itself: its issues, stars and history in place, its org-scoped npm package, or its users' trust in the org's promise.

**Stewarded repos** are on the hosted side of the line, permanently. Sometimes someone asks us to look after a repo they're stepping away from. We give it a safe home in `pmndrs/` so it isn't lost or squatted, but it was never ours and doesn't become ours by sitting here. The owner can take it back any time, archive or unarchive it, or hand it to someone else. We don't promote, adopt, or change it without the owner's consent, except to act on a security problem. If the owner later wants the org to take it on, it goes through normal adoption with their consent.

**Existing repos:** the first tier classification decides this. Anything placed at Tier 2 or higher is adopted from that point on.

## The rules that matter

- **Repos in the org follow the org's policies.** Bringing a repo into `pmndrs/` gets you visibility, infrastructure, security help, and continuity. In exchange you give up unilateral control of its direction.
- **Original authorship isn't a permanent veto.** If you step away and others carry a project, the people doing the work decide where it goes. Your credit stays. (See [Ownership](./ownership.md).)
- **Every README shows its tier** in a short header at the top.
- **Tiers change.** A repo moves **up** when it gains users and maintainers (Steering sign-off, plus member lazy consensus to reach Core). It moves **down** when maintainers go quiet for 6+ months or drop below the tier minimum (Steering decision). Moving down isn't a punishment.

## Bringing a repo in

1. Short proposal: what it is, its license, the proposed tier, who maintains it.
2. The Steering Committee reviews within 2 weeks.
3. **The maintainer confirms in writing** that the repo will follow pmndrs policies and tier rules while it's here. Repos usually come in as Hosted and stay the maintainer's to take back out until they're adopted. If a repo comes in directly at Tier 2 or higher, this written confirmation is the adoption consent, and the repo can't be moved out later.
4. Setup: README tier header, credentials into the vault, npm scope if needed.

## Moving a repo out

- **Hosted or Stewarded, never adopted:** the maintainer or owner asks and we transfer the repo. For npm:
  - **Unscoped package names** (e.g. `some-lib`) can move with the repo, and we hand over publish rights.
  - **Org-scoped names** (`@pmndrs/...`) stay with the org. We either keep the name or deprecate it with a pointer to the new location, whichever is less disruptive for users.
- **Adopted (ever Tier 2+):** not transferable. Fork instead.

## Archiving

Mark it archived on GitHub, add a README notice pointing to alternatives, deprecate the npm package, and retire its secrets. Anyone can propose unarchiving it if they'll take it on.
