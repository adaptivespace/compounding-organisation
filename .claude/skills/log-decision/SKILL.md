---
name: log-decision
description: Capture a decision record by guiding the user through the decision template or by ingesting a meeting transcript, then update related decision records when the new one complements or supersedes them. Trigger with /log-decision [decision topic or transcript source].
user-invocable: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
---

# /log-decision - Decision Logging

Use this skill when the user wants to record a decision in `Knowledge/Operating System/Decision Records/`.

Arguments passed: `$ARGUMENTS`

## Goal

Create a durable decision record that follows the repository template, ensure the decision is complete enough to be useful later, and maintain links to earlier decisions when the new record complements or supersedes them.

## Target Format

Decision records should use the frontmatter and body pattern from `Templates/Knowledge/Decision Record.md`. The filename for the decision record should follow the format `<YYYY-MM-DD> - <Short title based on the decision content>.md`.

Required body fields:

- `**context:**`
- `**facing:**`
- `**we decided for:**`
- `**and neglected:**`
- `**to achieve:**`
- `**accepting that:**`

## Workflow

1. Determine the input mode.
   - If `$ARGUMENTS` is a transcript path or refers to meeting notes, read the transcript and extract the decision.
   - Otherwise treat this as a guided decision-capture workflow.

2. Gather the missing decision content.
   - If working from a transcript, extract the six required fields and identify any missing or ambiguous parts.
   - If working interactively, ask only for the fields that are still missing.
   - Do not create the record until all six body fields are materially answered.

3. Search for related decision records.
   - Search `Knowledge/Operating System/Decision Records/` for related topics, prior versions, and adjacent decisions.
   - Determine whether the new decision:
     - complements an earlier decision
     - supersedes an earlier decision
     - is independent

4. Create the new decision record.
   - Place it in `Knowledge/Operating System/Decision Records/`.
   - Use Title Case for the file name.
   - Fill in frontmatter, including `status`.
   - Use `status: accepted` unless the user clearly indicates the decision is still proposed.
   - Add `supersedes` when applicable.
   - Add `## Related` links to adjacent concepts, strategies, playbooks, or earlier decisions.
   - Add `## Sources` with transcript or supporting source references when applicable.

5. Update earlier decisions when linked.
   - If the new decision complements an earlier one, add reciprocal `## Related` links where helpful.
   - If the new decision supersedes an earlier one:
     - update the older decision's frontmatter to `status: superseded`
     - set `superseded_by: [[New Decision Title]]`
     - add a visible note near the top of the old record stating that it was superseded by `[[New Decision Title]]`
   - Do not mark an earlier decision as superseded unless the relationship is clear from the user's instructions or the transcript.

6. Validate completeness.
   - Check that all six required body fields are present.
   - Check that any supersession links are two-way.
   - Check that the decision can stand alone without needing the original conversation to be understood.

7. Update the decision log in `/Knowledge/Operating System/Decision Records/README.md`.

## Rules

- Keep decision records concise and durable.
- Preserve the user's actual decision, not a cleaner but different one.
- Prefer minimal edits to earlier decisions unless supersession is explicit.
- If the transcript contains multiple decisions, either create separate records or ask the user which one to log first.
- Treat transcripts in `Research/` as read-only unless the user explicitly asks for edits there.
