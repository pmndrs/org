# Security standards

**Status: Draft**

What "secure" means for Poimandres right now. Each rule is either **required now** or a **target** we're working toward. Owned by the Security & Infrastructure team and changed by lazy consensus. The principles behind them are on the [Security](./security.md) page.

## 1. Signing in

The goal is **phishing-resistant sign-in**, meaning a passkey or hardware key, on the accounts that can do the most damage. Authenticator-app codes (TOTP) can be phished. SMS is never accepted.

| Account | Required now | Target |
| --- | --- | --- |
| npm org Owner | Passkey or hardware key (npm enforces it) | — |
| GitHub org Owner, domain registrar, 1Password, fiscal host admin | Authenticator app | Passkey or hardware key |
| Everyone else | Authenticator app | — |

- **Register a backup.** Owners keep a second passkey or key, so losing one device doesn't lock them out.
- **Recovery codes** for Owner accounts go in the `Security-Infra` vault, never only on your own device.
- **GitHub can't enforce passkey-only sign-in** at the org level, so for GitHub Owners it's a rule people follow. Until the target is met, authenticator apps on these accounts are an accepted risk.

## 2. Passwords and secrets

Shared secrets live in **1Password Business**. We need Business rather than Teams because it keeps the access logs that break-glass reviews and audits rely on.

| Vault | Who | What's in it |
| --- | --- | --- |
| `Steering` | Steering Committee | Fiscal host, treasury, billing and root logins for cloud accounts, read-only registrar |
| `Security-Infra` | Security & Infrastructure team | Registrar, DNS, GitHub and npm recovery codes, CI admin, monitoring |
| `Project-<name>` | Team Lead + named maintainers | Project tokens, deploy secrets, third-party API keys |
| `Shared-Tools` | All members | Non-sensitive shared seats |
| `Break-Glass` | Steering + Security & Infra | Master recovery codes. Every use is logged and reviewed within a week |

**Rotation**

- **Prefer short-lived credentials** (OIDC / Trusted Publishing). They don't need rotating at all.
- **Long-lived API tokens and non-OIDC CI secrets:** every quarter.
- **Registrar password and recovery codes:** once a year, and whenever someone with access leaves.
- **Anything you think is compromised:** immediately, before anything else.

**Access** to a vault is granted by the Security & Infrastructure team with Steering approval. It ends when the role ends.

## 3. Per system

**GitHub**

- 3+ Owners: at least 2 from the Steering Committee and at least 1 from Security & Infra.
- 2FA required for every org member.
- Default branch: changes need a PR reviewed by a maintainer, and force-pushes are blocked. Signed commits are up to each project.
- Org-level secrets are managed by Security & Infra. Repo secrets are kept to a minimum and owned by the Team Lead.

**npm**

- 2+ Owners.
- **Trusted Publishing (OIDC) for every package that supports it.** This is the single most valuable control we have: it removes the human publish path, so a stolen Owner account can't push a malicious release.
- Where it isn't supported, use an automation token stored in GitHub Actions secrets, rotated quarterly.
- Publishing by hand needs Team Lead approval and a note in the release.
- Every package requires 2FA to publish, and ships with provenance where the toolchain supports it.

**Domains and DNS**

- Registry lock on, where the registrar supports it.
- DNSSEC is a target.
- DNS changes need approval from one Security & Infra member and one Steering member.

**CI**

- In workflows that publish, deploy or touch secrets, pin third-party actions to a commit SHA, not a tag.
- Changes to those workflows need a second maintainer's review.
- No self-hosted runners on repos that publish to npm.

**Hosting and cloud** (Vercel, Cloudflare, and similar)

- Members use their own accounts with a team role.
- Any root or single-login account uses a role email.
- Day-to-day work uses scoped access, never the root login.

## 4. Dependencies

- Dependabot security alerts on, with open alerts reviewed monthly by each project.
- **Before adding a new production dependency,** check who maintains it, its recent history, and its download numbers. Watch for look-alike names.
- Lockfiles are committed, and CI installs from them (`npm ci`, `pnpm install --frozen-lockfile`).
- Read the install scripts of any new dependency before adopting it.
