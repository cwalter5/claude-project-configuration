# Project Instructions

## Session start

At the start of each session, verify the loaded rules appear complete by checking that all major sections — change workflow, proposed changes handling, triggers, and routing rules — are present and active. Flag any that appear missing or incomplete before proceeding. Do not check for specific filenames — the dist may have been uploaded under any name.

## When changes are discussed and agreed

1. Flag ambiguous or weak phrasing during discussion before it becomes a rule, and verify before staging that each rule is concise, unambiguous, and executable by Claude without additional context or judgment calls. When proposing a rule or change, surface relevant edge cases before asking for agreement — when edge cases could materially affect the decision.
1. State the risk or tradeoff if one exists.
1. When a change is agreed, stage it immediately, present the diff, and flag any issues — issues means non-obvious problems only; don't flag what the diff makes self-evident, but always flag cross-file dependencies and conflicts that may not be visible in the diff alone. Don't ask for confirmation first.
1. Accumulate changes in a versioned artifact.
1. Present the artifact immediately — do not wait to be asked.
1. Note any unresolved tensions or open questions introduced by the change.
1. Do not apply changes that haven't been explicitly agreed — suggest them instead. Incidental fixes (typos, formatting) introduced by a staged change are excepted.
1. After staging a change, generate adversarial test examples for the affected rule. Run them against the previous and new version and present the before/after delta so the impact can be judged.

## File routing

- Before acting on any file, identify its role from the filename or `inventory.md`. Only edit source files — never dist. Route changes to the correct file for their audience: behavioral and formatting rules belong in `profile-instructions.md`; workflow and project-specific rules belong in `project-instructions.md`; architectural decisions belong in `architecture.md`; inventory belongs in `inventory.md`; flag labels that should apply universally must not be added to `project-instructions.md` alone.
- The project should contain only source files and reference files (`README.md`, `architecture.md`, `inventory.md`, `operations.md`). Flag any `dist-` files or unrecognized files found in the project context.

## How to handle proposed changes

- If a change creates contradiction or ambiguity, flag it before applying.
- Keep a changelog at the bottom of `profile-instructions.md` only if the user requests it — otherwise keep the file clean.
- Periodically check that behavior in this conversation matches the rules in `profile-instructions.md`. Flag any drift. If behavioral patterns emerge that aren't covered by existing rules, note them as candidates for session review.
- Don't apply project-specific workarounds as global rules without explicit agreement — changes that should apply universally belong in `profile-instructions.md`.
- Before staging a new version, confirm the previous version is accessible. Never overwrite without incrementing.
- Never review or edit `dist-` files directly — always regenerate from source.

## Triggers

- When the user says "show artifacts", call `present_files` with all current versioned source and dist files in the outputs directory.
- When the user says "package project", follow the package project operation defined in `operations.md`.
- When the user calls for a critical review, follow the critical review rules defined in `operations.md`.
- When producing dist files, follow the compression rules defined in `operations.md`.
