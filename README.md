# Project README

## Contents

- [Purpose](#purpose)
- [Installation](#installation)
- [Why this exists](#why-this-exists)
- [Open questions](#open-questions)

## Purpose

This is the authoring environment for Claude project templates. It contains the tooling and conventions needed to produce, version, and compress template files for use in other Claude projects.

## Installation

This project produces two files that need to be installed separately.

**1. Profile instructions** — applies to every conversation across all projects.

1. Open [claude.ai](https://claude.ai)
2. Click your initials in the lower left corner
3. Open Settings > Profile (or Personal Preferences)
4. Paste the contents of `dist-profile-instructions.md` into the preferences field
5. Save

**2. Project instructions** — applies only within a specific project. Requires Claude Pro or higher.

1. Open or create a project in Claude.ai
2. Open the project's instructions or context field
3. Paste the contents of `dist-project-instructions.md`
4. Save

**Keeping up to date**

This project manages its own updates. Open it in Claude.ai to review, discuss, and apply changes to both files. When ready, run "package project" to regenerate dists and get a reminder to reinstall. Dist files are always regenerated from source — never edit them directly.

## Why this exists

Out of the box, Claude is optimized for broad appeal — thorough, warm, agreeable, and verbose. That's the right default for casual use. For iterative, task-focused work it creates friction: responses that pad and caveat, positions that soften under pushback, implementations that execute on what was asked rather than what was needed.

This project addresses that gap with a behavioral profile that trades warmth for precision and thoroughness for conciseness.

### What changes in practice

A default Claude session tends to encounter problems around turn 5–10. Responses drift long, corrections pile up, Claude agrees when it should push back, and implementations proceed without checking whether a simpler approach exists. By turn 15–20 in a complex session, a meaningful portion of the exchange is overhead — corrections, clarifications, and rebuilds rather than work.

With the profile applied, the correction cycle shrinks significantly. Rules are flagged before they become ambiguous. Mistakes are surfaced once, concisely. Simpler approaches are proposed before building begins. The session stays on task longer and produces fewer artifacts that need to be undone.

### Estimated efficiency delta

These are reasoned estimates, not measured benchmarks.

| | Default Claude | With profile |
|---|---|---|
| Turns before first correction needed | ~5–10 | ~15–20 |
| Corrective turns per 20-turn session | 4–6 | 1–2 |
| Avg response length (simple queries) | 200–400 tokens | 100–200 tokens |
| Output tokens per 20-turn session | ~6,000–8,000 | ~3,000–4,000 |
| System prompt overhead | 0 | ~800 tokens (recovered by turn 3) |

The token savings are real but secondary. The primary gain is work per session — more decisions made, more tasks completed, fewer cycles spent correcting behavior rather than doing the thing.

### Context limit estimates by session type

At current context window sizes, quality typically begins to degrade before the hard limit is reached — Claude starts losing earlier context, and responses become less coherent or consistent. These estimates reflect the point where a restart becomes advisable, not the hard cutoff.

| Session type | Default Claude | With profile |
|---|---|---|
| Simple Q&A / research | ~60–80 turns | ~80–100 turns |
| Iterative writing or editing | ~30–40 turns | ~50–60 turns |
| Multi-file code or config work | ~20–30 turns | ~35–50 turns |
| Complex multi-file sessions (like this project) | ~15–20 turns | ~30–40 turns |

The gains compound in complex sessions because the profile's terse outputs preserve more usable context per turn. Default Claude's padding fills the context window faster with lower-signal content, meaning the effective working window shrinks sooner.

### The before-acting multiplier

The hardest efficiency gain to quantify is the pre-action check. Default Claude builds what's asked. The profile checks whether what's asked is the right thing to build before starting. A prevented rebuild — or a session that doesn't happen because the right tool was identified upfront — is worth more than any per-turn token saving.

## Open questions

- It is unclear whether project context files are injected once at session start or resent with every message. This affects the token cost tradeoff of file structure — if resent each message, fewer files is more efficient; if injected once, it makes no difference. Clarify before optimizing file structure for token efficiency.
