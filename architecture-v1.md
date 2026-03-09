# Architecture

## How files load and interact

- `profile-instructions.md` is a source file — it is compiled to a dist and copied manually into Claude user preferences. It is baked into every conversation across all projects as system context.
- `profile-instructions.md` rules are always standalone — they must never defer to, reference, or depend on project instructions. They apply in every context, with or without any project loaded.
- Rules that exist in both `profile-instructions.md` and `project-instructions.md` are redundant — the project version should be removed since profile always loads. Project instructions should only contain rules that are genuinely project-specific.
- `project-instructions.md` is a source file — it is compiled to a dist and uploaded into this project's context. The dist, not the source, is what Claude loads each session.
- All other source files (`operations.md`, `continuous-improvement.md`) are used directly within this project and are not compiled to dist unless being distributed to another project.
- Project instructions are more specific than profile instructions and naturally override them where they conflict. No explicit tiebreaker rule is needed.
- Dist files are compressed outputs. They are never edited directly — always regenerate from source.

## Decisions

- This project is the authoring environment for all Claude project templates
- Compression logic lives here; it need not be duplicated into child templates
- Template output: one dist file per template project
- `project-instructions.md` workflow rules are project-specific — they belong in projects that need them, not in user preferences
- No native inheritance between Claude projects — templates are copied manually into new projects
- All project files are versioned — source, reference, and template files alike. Dist files are not versioned; they are regenerated from source on demand.
- File structure is split by purpose: session rules, on-demand operations, architecture, inventory, and orientation are separate files
