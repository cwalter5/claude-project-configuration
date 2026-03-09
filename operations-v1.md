# Operations

## Critical review

When the user calls for a critical review, cover: contradictions or tensions between rules, actionability failures, redundancy within each file and across files, devil's advocate challenges to each rule, performance concerns (rules likely to be ignored or misapplied), efficiency concerns (rules that could be simplified or collapsed), whether simpler or more native approaches exist for anything built that could have been achieved with less, cross-file overlap between `profile-instructions.md` and `project-instructions.md` (any rule in both is redundant and should be removed from project), and any other issues that are actionable and relevant. Work through each file in scope systematically.

## Compression

When producing dist files, generate compressed versions automatically. Apply these rules:

- Collapse redundant or overlapping rules into single statements
- Strip prose explanations; keep the instruction only
- Convert enumerations to compact inline lists
- Remove section headers where content is self-evident
- Preserve all behavioral instructions — fidelity over brevity when in conflict

## Creating a new template

1. Create a source file: `[template-name].md`
2. Draft the template content following the rules in `project-instructions.md`
3. Review for ambiguity, redundancy, and executability before staging
4. Produce a compressed dist: `dist-[template-name].md` using the compression rules above
5. Record the new file in `inventory.md`

## Updating an existing template

1. Edit the source file only
2. Increment the version in the filename or header
3. Regenerate the dist — never edit dist files directly
4. Show a diff in chat for changes of 5 lines or fewer; summarize larger changes

## Package project

Triggered by "package project". Before packaging, run the following checks and surface any warnings — all are advisory, not blocking:

1. Verify the loaded rules appear complete — check that all major sections are present and active
2. Verify every file in `inventory.md` is present in outputs — flag any missing
3. Flag any files in outputs not listed in `inventory.md`
4. Verify all files are routed correctly — behavioral and formatting rules in `profile-instructions.md`; workflow rules in `project-instructions.md`; architectural decisions in `architecture.md`; inventory in `inventory.md`; universal flag labels not isolated to `project-instructions.md`
5. Verify high-stakes rules appear early in each file — flag any critical rules buried in the middle
6. Flag any unresolved tensions or open questions from the current session

Then ask whether dists need to be regenerated. Then zip the current snapshot — latest versioned source files and reference files — and present for download. Latest versioned file is identified by the highest version number in the filename (e.g. `v3` over `v2`). Where no version number exists, the file is included as-is. Superseded versions and dist files are excluded unless explicitly requested. Then remind the user to follow the installation steps in `README-v1.md` to update project files, project instructions, and profile instructions.
