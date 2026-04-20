---
name: lint
description: Perform low-risk knowledge base maintenance. Check placement, linking, terminology drift, duplicates, and stale placeholders. Trigger with /lint [scope].
user-invocable: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
---

# /lint - Knowledge Base Maintenance

Use this skill to inspect the vault for structural drift and apply incremental fixes.

Arguments passed: `$ARGUMENTS`

## Goal

Keep `Knowledge/` and user-requested areas of `Outputs/` tidy, navigable, and consistent without large reorganisations.

## Workflow

1. Determine scope.
   - If `$ARGUMENTS` names a folder or note, limit checks to that scope.
   - Otherwise scan the relevant `Knowledge/` sections.

2. Check note placement.
   - Look for notes stored in the wrong top-level section or wrong taxonomy branch.

3. Check links.
   - Look for missing or weak cross-links.
   - Improve discoverability by adding a small number of meaningful links where appropriate.

4. Check terminology drift.
   - Compare note language with `Knowledge/glossary.md`.
   - Normalize terms when the canonical wording is clear.

5. Check duplicates.
   - Flag or consolidate notes that clearly cover the same idea.
   - Prefer minimal fixes over structural churn.

6. Check placeholders and stale content.
   - Expand or remove empty placeholders when safe.
   - If the user asked for maintenance in `Outputs/`, check for stale deliverables there too.

## Rules

- Keep fixes incremental and low-risk.
- Prefer improving placement, links, and terminology over renaming or deleting files.
- Do not delete meaningful notes without clear justification.
- Treat `Research/` as read-only unless the user explicitly requests edits.
