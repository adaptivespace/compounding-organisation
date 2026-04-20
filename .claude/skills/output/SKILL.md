---
name: output
description: Produce a polished deliverable in Outputs from existing Knowledge and relevant Research when the user asks for one. Trigger with /output <deliverable request>.
user-invocable: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
---

# /output - Polished Deliverable

Use this skill when the user wants a memo, guide, or report written into `Outputs/`.

Arguments passed: `$ARGUMENTS`

## Goal

Create a polished deliverable grounded in the curated vault, using `Research/` only as supporting source material when necessary.

## Workflow

1. Parse the requested deliverable and determine the target folder.
   - Guides go in `Outputs/Guides/`
   - Memos go in `Outputs/Memos/`
   - Reports go in `Outputs/Reports/`

2. Read the relevant notes in `Knowledge/` first.

3. Read source material in `Research/` only if needed to fill gaps or verify details.

4. Draft the deliverable.
   - Follow any applicable instructions in `Context/`.
   - Keep the output consistent with the repository's terminology.
   - Link back to relevant notes when useful for navigation.

5. If the drafting process reveals durable knowledge that belongs in `Knowledge/`, update the relevant notes before or alongside the deliverable.

## Rules

- Create deliverables in `Outputs/` only when explicitly requested.
- Prefer grounding the piece in curated `Knowledge/` before returning to raw `Research/`.
- Keep changes focused on the requested deliverable and any directly supporting knowledge updates.
