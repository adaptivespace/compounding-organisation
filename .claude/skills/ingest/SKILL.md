---
name: ingest
description: Ingest material from Research into the curated Knowledge base. Read source material, extract durable notes, update glossary when needed, and place notes in the correct folder. Trigger with /ingest <source>.
user-invocable: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
---

# /ingest - Knowledge Base Ingest

Use this skill when the user asks to ingest or process source material from `Research/`.

Arguments passed: `$ARGUMENTS`

## Goal

Turn source material into durable knowledge notes under `Knowledge/`, updating existing notes first and only creating polished outputs in `Outputs/` when the user explicitly asks.

## Repository Structure

- Source material lives in `Research/`
- Curated notes live in `Knowledge/`
- Deliverables live in `Outputs/`

Knowledge taxonomy:

- Concepts: `Knowledge/Foundations/Concepts/`
- Strategy: `Knowledge/Foundations/Strategy/`
- Active context: `Knowledge/Operating System/Active Context/`
- Decision records: `Knowledge/Operating System/Decision Records/`
- Metrics: `Knowledge/Operating System/Metrics/`
- Playbooks: `Knowledge/Operating System/Playbooks/`

## Workflow

1. Resolve the source.
   - If `$ARGUMENTS` is a path under `Research/`, read it.
   - If it is a partial name, search `Research/` for likely matches.
   - If it cannot be found, stop and ask the user to clarify.

2. Read the relevant source material.

3. Extract durable content.
   - Pull out concepts, strategic implications, operating implications, metrics, and repeatable playbooks.
   - For each candidate note, identify: title, target folder, key idea, and which source files support it.

4. Ask clarifying questions if the extracted meaning is ambiguous.
   - Ask only when necessary.
   - Focus on ambiguity around note boundaries, categorisation, or priority.

5. Update existing notes first.
   - Search the relevant `Knowledge/` folders before creating a new note.
   - Prefer extending an existing note when the material clearly fits.

6. Create new notes only when needed.
   - Use the standard frontmatter from `AGENTS.md` unless the local folder uses an established variation.
   - Keep notes concise and durable.
   - Add `## Related` when cross-links improve navigation.
   - Add `## Sources` when the note is derived from `Research/`.

7. Update `Knowledge/glossary.md` when new terms appear or definitions sharpen.

8. Do not create anything in `Outputs/` unless the user explicitly asked for a polished deliverable.

## Rules

- Treat `Research/` as read-only unless the user explicitly asks for edits there.
- Edit only under `Knowledge/` and `Outputs/` by default.
- Use wiki-links like `[[Note Name]]`.
- Prefer the smallest correct update.
- Keep terminology consistent with `Knowledge/glossary.md`.
