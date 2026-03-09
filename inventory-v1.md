# Inventory

## File map

| File | Type | Description |
|------|------|-------------|
| `README.md` | Reference | Project orientation, purpose, and efficiency rationale |
| `architecture-v1.md` | Reference | How files load and interact, decisions |
| `inventory-v1.md` | Reference | This file — file map and current snapshot |
| `operations-v1.md` | Reference | On-demand operations: critical review, compression, templates, package project |
| `continuous-improvement-v1.md` | Reference | Research template for periodic improvement reviews |
| `project-instructions-v3.md` | Source | Session-level rules and triggers — compiled to dist for project context |
| `profile-instructions-v2.md` | Source | Behavioral rules — compiled to dist for Claude user preferences |
| `dist-project-instructions.md` | Dist | Compressed project instructions for upload to project context |
| `dist-profile-instructions.md` | Dist | Compressed profile instructions for upload to Claude user preferences |
| `session-review-YYYY-MM-DD.md` | Output | Session review artifact — not a project file, not versioned |

Never edit dist files directly — regenerate from source.

## Current snapshot

Latest files for project update:

- `project-instructions-v3.md` → compile to `dist-project-instructions.md`, upload to project context
- `profile-instructions-v2.md` → compile to `dist-profile-instructions.md`, upload to Claude user preferences
- `operations-v1.md`
- `architecture-v1.md`
- `inventory-v1.md`
- `README.md`
- `continuous-improvement-v1.md`
