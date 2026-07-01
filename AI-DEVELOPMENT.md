# AI-Assisted Development — How This Work Is Done Safely

I build with AI coding agents, openly. This document explains **how** — and, more importantly,
the controls that keep that work safe, reviewable, and accountable. If you're evaluating my work
and wondering "how do I know an AI didn't quietly do something reckless," this is the answer.

## The principle

**Agents do the labor. A human keeps the judgment.** Every change an agent makes is treated
exactly like a change from a new contributor: it goes through review and automated gates before it
can land. Nothing merges because a machine felt good about it — it merges because I looked.

## The controls

Every repository I own is set up the same way:

- **No direct commits to `main`.** A branch-protection ruleset makes pull requests the *only* way
  changes reach the default branch. Agents work on branches; they cannot push to `main`.
- **Every PR is gated by an automated review — [AgentGate](https://github.com/brett-buskirk/agent-gate).**
  It inspects each diff for the ways agents commonly go wrong (leaked secrets, out-of-scope edits,
  missing tests, surprise dependencies) and sets a **required, blocking** status check. Leaked
  credentials or dangerous patterns *stop the merge.* It's AI reviewing AI — and it has caught its
  own mistakes.
- **Secrets are scanned at push time.** GitHub secret scanning + push protection is enabled on
  public repos, so a credential is blocked *before* it ever reaches a branch — defense in depth
  alongside AgentGate's own check.
- **Commits are signed.** Commits are cryptographically signed and show as **Verified**, so every
  change has provable authorship — even the ones an agent wrote. A human's signature stands behind
  each one.
- **Dependencies are watched.** Dependabot tracks dependency and GitHub Actions updates; new or
  changed dependencies are flagged for review.
- **Workflow tokens are least-privilege.** CI jobs get only the permissions they need, scoped
  explicitly — never blanket write access.
- **Agents work from a scoped brief.** Each agent operates against a written `CLAUDE.md` that
  defines the task, the architecture, and what is *in* and *out* of scope — bounded context, not a
  blank check.

## Transparency

AI contributions are attributed. Commits an agent helped write carry a `Co-Authored-By` trailer
naming the model. I don't hide that AI is part of the workflow — the point is that it operates
inside a system designed to catch what both a machine *and* a tired human would miss.

## Accountability

I am the sole maintainer. I review and sign off on every merge, and my signature is on the commits.
Using AI doesn't move responsibility onto the tool — it stays with me.
