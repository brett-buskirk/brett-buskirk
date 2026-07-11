# Agentic Engineering Practices

*The craft layer of how I work with AI coding agents — the working method beneath the guardrails.*

This is a companion to the governance docs, not a replacement:

- **[AI Agent Working Agreement](AI-AGENT-WORKING-AGREEMENT.md)** — the non-negotiable *floor* I bring
  to any repo (a human merges, no direct-to-main, no secrets, tests as part of the change).
  *What I promise.*
- **`/etc/claude-code/CLAUDE.md`** (managed policy) — the enforced version of that floor on my machine.
- **This file** — the *craft*: the day-to-day disciplines that make agent-driven work reliable.
  *How I actually engineer.*

These are distilled from reviewing a mature power-user Claude Code setup and keeping only what's
**scale-independent** — practices that pay off on a 5,000-line project as much as a 100,000-line one,
without the heavy infrastructure (knowledge graphs, session-journaling hooks, persistent-observation
servers) that only earns its keep on a large, long-running monolith.

Each practice: what it is, why, and **how to make it stick**.

## 1. Verify in tiers, after every change

Don't call a change done until it's been checked in order — cheapest, fastest checks first:

1. **Syntax / compile** — the file parses and type-checks.
2. **Tests** — run the suite (or the nearest subset). If none exist, that's a gap to close, not skip.
3. **Call-site check** — on any signature/interface change, grep every consumer and confirm they hold.
4. **Integration / runtime** — for anything deployed or cross-module, actually run it and confirm the
   behavior consumers expect is unchanged.

Three hard-won refinements worth stealing:
- **Clear stale build/bytecode caches before integration testing** (`__pycache__`, `dist/`, etc.). A
  stale artifact shows old line numbers in tracebacks and hides the real error.
- **Pessimistic arbitration.** If one pass says PASS and a second says FAIL, the FAIL wins. "It worked
  when I ran it" is not passing.
- **Assert the real failure mode.** When testing that a guard *doesn't* over-block, assert the
  downstream error you'd get if it did (e.g. an `AttributeError`) rather than mocking everything — the
  failure mode is the test oracle.

**Make it stick:** put a 3-line version of this ladder in each project's `CLAUDE.md` so it auto-loads,
and treat "climbed the ladder" as the definition of done before opening a PR.

## 2. Two-failure abort

If the same edit fails twice on the same target, **stop.** Don't try a third time — write down what
you observed and reassess or ask. Repeated failed attempts pollute context and usually mean the mental
model is wrong, not the syntax.

**Make it stick:** name the pattern out loud ("that's two — stopping"). Formalizing it prevents the
thrash spiral.

## 3. No-op by default for risky changes

Land behavior that could break something behind a switch that **defaults to off (or log-only)**. Ship
it observing — log what it *would* have done — then flip it on deliberately once the logs look right.

This matters most where a merge deploys immediately (no staging gap): observing in production before
acting is the safety margin.

**Make it stick:** for anything touching production behavior, the default diff is flag-guarded and
inert; a second, tiny change flips the flag once you've watched it. Track live flags in the project doc.

## 4. Context hygiene

- **`/clear` between unrelated tasks** — don't carry one subsystem's context into another; it causes
  subtle cross-contamination.
- **`/compact` around 50–60% usage**, and state explicitly what must survive before you trigger it.
- **Delegate exploration to sub-agents** — reading/searching fills context fastest; hand it off and keep
  the main thread for judgment and edits.

**Make it stick:** treat context like a budget, not an infinite scroll.

## 5. Numbered bug classes (institutional memory)

When a bug turns out to be an instance of a *pattern*, give the pattern a number and a one-line fix, and
record it. Then it's referenceable ("that's BC#7") instead of re-explained each time.

**Make it stick:** keep the top handful in the project `CLAUDE.md`, the long tail in a memory ref file.
Promote a pattern only when it's (a) general, (b) actually bit you, and (c) not already covered — and
promote it deliberately, never auto-append.

## 6. Keep the instruction file lean

A project's `CLAUDE.md` is rules + pointers, not an encyclopedia. Heavy detail lives in ref files it
points to, loaded on demand. Prune it to *current state*, not history. Only promote a rule when it's
general and high-severity.

**Make it stick:** when `CLAUDE.md` starts feeling like a dumping ground, move detail to
`memory/ref/*.md` and leave a pointer.

---

*Adopt incrementally — one habit at a time until it's automatic, then the next. The floor (the working
agreement) is non-negotiable from day one; these are the craft that makes operating inside that floor
fast and reliable.*
