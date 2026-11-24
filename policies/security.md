# Security

**Status: Draft**

People build on our code because they trust it. Here's how we protect that trust. The specifics live in [Security standards](./security-standards.md).

## What we commit to

- A **Security & Infrastructure team** of at least 2 people looks after credentials and responds to incidents.
- Security reports are **acknowledged within 72 hours**.
- After any incident, we publish **what went wrong and what we changed**.

## The rules

1. **No single holder.** Every critical account (GitHub org, npm org, domains, password vault, fiscal host) has **at least two** people who can access it.
2. **Roles, not people.** Access comes with a role and ends when the role ends (see [Who holds access](#who-holds-access) below).
3. **Everything shared lives in the password manager** (1Password), split into vaults by role. Nothing in personal password managers, notes, or chat.
4. **People join with their own accounts; the org owns anything that can't have members.**
   - **Your personal account is fine** for GitHub, npm, Vercel, Cloudflare, Notion and anything else that supports members or teams. The org grants you a role, and removing the role removes your access.
   - **Single-login services use a role email** such as `domains@` or `social@`, with the password in 1Password. Examples: the domain registrar, social media accounts, and anything else where only one person can log in. These should never live on one person's own login.
   - **Billing is moving off personal cards.** Where a personal card pays for an org service, that's a known single point of failure until we have an org payment method (fiscal host card or our own entity). We keep a list of each one, so it's visible.
5. **Prefer short-lived credentials.** Publish from CI with npm Trusted Publishing where possible, not long-lived tokens.
6. **Rotate** shared credentials on a schedule, and always when someone with access leaves.

## Who holds access

Access comes with a role, never with a person or their history.

- **GitHub org Owner:** held by active Steering Committee members and the Security & Infrastructure team. At least 3 at all times. It isn't a title of honor or a reward for past work. It's custody of the org's keys.
- **Repo admin / write:** held by the repo's current maintainers.
- **npm publish, domains, vaults, fiscal host:** held by whoever is responsible for that system right now. Always at least 2 people.

When someone's role ends, whether they step down, go inactive, or are removed for cause (see [Membership](./membership.md#how-a-role-ends)), their access is removed. That applies to everyone equally, and it says nothing about trust. A dormant account with Owner rights is one of the most common ways open-source projects get compromised, and removing those accounts is ordinary security hygiene.

**Offboarding:** access is removed within 7 days, and every shared credential the person knew is rotated within 14. If removing someone would leave a system with a single holder, a backup is added first.

## Two-factor authentication

Every account tied to Poimandres has 2FA. **SMS is never accepted.**

| Account | Required now | Recommended |
| --- | --- | --- |
| npm org Owner | Passkey or hardware key (npm enforces this) | Hardware key + a backup |
| GitHub org Owner, domain registrar, 1Password, fiscal host admin | Authenticator app (TOTP) at minimum | **Hardware security key** (YubiKey etc.) or passkey |
| Core-tier repo maintainers | Authenticator app (TOTP) at minimum | **Hardware security key** or passkey |
| Everyone else | Authenticator app (TOTP) | Passkey |

**Why we recommend hardware keys:** passkeys and hardware keys can't be phished, while authenticator-app codes can be relayed by a fake login page. A hardware key also isn't tied to a phone or a synced cloud account. **The org reimburses hardware keys** for anyone holding a critical role. Get two, and register the second as a backup.

Keep recovery codes for Owner-level accounts in the right role vault, not just on your own device.

## If something goes wrong

- **Report it:** security issues go to the security address listed in each repo's `SECURITY.md`, never public issues.
- **During an incident** the Security & Infrastructure team can rotate any credential, remove any access, or take down a package or repo **without waiting for approval**, including suspending someone's access. A suspension during an incident isn't a judgment of the person. A written account goes to the Steering Committee within a week. Anyone acting in good faith in their role has the collective behind them.

## Volunteers

Everyone here is a volunteer. We ask for good faith and judgment, not heroics or on-call availability nobody is paid for. If something you're asked to do feels like it puts you personally at legal or financial risk, stop and escalate.
