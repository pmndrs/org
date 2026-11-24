# AI policy

**Status: Draft**

## Our position

**AI tools are welcome. The person who submits the work is responsible for it.** We follow the [OpenJS Foundation AI Coding Assistants Policy](https://ai-coding-assistants-policy.openjsf.org), which covers Node.js and our wider JS ecosystem, and is in the same spirit as the Linux kernel's. This page adds the few rules specific to Poimandres.

We don't ban AI. We don't accept code nobody understands.

## Rules for contributors

1. **Understand what you submit.** You've read every line and can explain why it's there. If a reviewer asks and you can't answer, the PR waits until you can.
2. **Same quality bar.** No discount for AI-written code: no repetition where a helper belongs, follow the project's style, and write TSDoc on public APIs that says something the code doesn't.
3. **Disclose with an `Assisted-by:` trailer** when an AI tool wrote any part of the change. Autocomplete doesn't count. This is the format the Linux kernel, Node.js, OpenSSL and Fedora use.
   ```
   Assisted-by: claude-code
   ```
4. **Dependency changes need a reason.** Any change to `package.json` or a lockfile must say what's being added and why, in your own words. "The AI suggested it" isn't a reason. Unexplained or look-alike packages get blocked.
5. **A human opens and owns every PR.** Agents can do the work, but a person submits it, answers review, and is accountable. PRs opened by an agent with no human behind them are closed.
6. **Write your own PR descriptions and comments.** AI is fine for translation or grammar. Don't paste AI summaries of your diff, or AI replies to reviewers.
7. **Never paste secrets into an AI tool.** No tokens, passwords, or vault contents, whatever the tool promises about data handling.
8. **Credit recognizable code.** If an AI hands you something clearly copied from another project, find the source, check the license is compatible, and credit it, just as you would if you'd copied it yourself.
9. **Only use tools whose terms don't restrict their output.** If a tool claims ownership of what it generates, don't use it for contributions.

## Stricter areas

- **Security-sensitive code** (auth, crypto, credentials, CI workflows with secrets): disclosure is required and the Security & Infrastructure team must sign off.
- **Human-written only:** security advisories, incident updates, governance changes, and anything legal or sponsor-facing. AI can help with research and drafts, but a person writes the final text and signs it.

## Rules for maintainers

- AI can help with triage, summaries, and drafting replies. A human reads it before anything is sent.
- **No AI merges and no AI-only approvals.** Every merge needs a human who read the change.
- **Use GitHub's limits.** Core and Maintained repos turn on the open-PR limit for people without write access. Any repo being flooded can restrict PRs to collaborators for a while. These are normal tools, not drastic ones.

## AI-found security reports

More and more real bugs are being found with AI help, so we don't dismiss a report because AI was involved.

- **A verified report with a reproducer** gets the normal 72-hour acknowledgement, however it was found.
- **An unverified report** (code that doesn't exist, no reproducer, obvious boilerplate) gets a short templated reply explaining what's missing, and is closed.
- **Repeated unverified reports** from the same source may be filtered.

## AGENTS.md

AGENTS.md is now a stable standard under the Linux Foundation's Agentic AI Foundation, and most coding agents read it. **Core repos should have one** that points agents to this policy, the commit format, and the project's conventions. It's optional everywhere else.

## Review

The Steering Committee reviews this page every quarter, and sooner if the OpenJS policy changes, a major incident happens, or a relevant court ruling comes out.

## Where others stand (Nov 2026)

**Similar to us:** [Linux kernel](https://docs.kernel.org/process/coding-assistants.html) (formal policy since Linux 7.0), [OpenJS Foundation](https://ai-coding-assistants-policy.openjsf.org) / Node.js, [OpenSSL](https://openssl-library.org/post/2026-06-18-ai-policy/), Fedora, and the [Linux Foundation](https://www.linuxfoundation.org/legal/generative-ai) baseline.

**Stricter, and deliberately not our approach:** [OpenJDK](https://openjdk.org/legal/ai) (interim ban since April 2026, with a full policy promised), Godot (bans substantial AI code and agents, since June 2026), Codeberg (won't host projects built mostly with AI, since July 2026), Gentoo and NetBSD (bans since 2024).

**Undecided:** FreeBSD (working group, report expected Q4 2026).

**Recommended reading:** *Securing Open Source in the Age of AI*, OpenSSF + CNCF, v1.0, May 2026.
