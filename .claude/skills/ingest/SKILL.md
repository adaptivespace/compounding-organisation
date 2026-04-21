---
name: ingest
description: Ingest material from Research into the curated Knowledge base. Read source material, write synthesized insight notes under Knowledge/Insights, update linked knowledge notes when warranted, update glossary when needed, and place notes in the correct folder. Trigger with /ingest <source>.
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

Turn source material into curated knowledge under `Knowledge/`, writing synthesized insight notes in `Knowledge/Insights/` and updating the appropriate knowledge areas when the insights meaningfully inform them. Keep the flow simple: evidence supports insights, and insights support knowledge. Update existing notes first and only create polished outputs in `Outputs/` when the user explicitly asks.

## Repository Structure

- Source material lives in `Research/`
- Curated notes live in `Knowledge/`
- Deliverables live in `Outputs/`

Knowledge taxonomy:

- Insights: `Knowledge/Insights/Customer/`, `Knowledge/Insights/Market/`, `Knowledge/Insights/Technology/`
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

3. Create or update synthesized insight notes under `Knowledge/Insights/`.
   - Map the source to the matching area: customer material to `Knowledge/Insights/Customer/`, market material to `Knowledge/Insights/Market/`, technology material to `Knowledge/Insights/Technology/`.
   - Capture the main findings, what they may mean, and the supporting source files.
   - Keep these notes close to the evidence, queryable, and useful for current analysis.
   - If the source is under `Research/Customer/Evidence/`, follow the customer discovery extraction workflow in `.claude/skills/extract-customer-insights/SKILL.md`.
   - For customer transcripts and interview notes, explicitly capture:
     - customer context and why now
     - current state and current tools
     - the top 3-4 pain points
     - business impact and workarounds
     - desired outcomes
     - buying context, stakeholders, and timeline when available
     - exact language worth preserving
     - open questions and confidence where the signal is weak

4. Update knowledge notes that should be informed by the insight.
   - Pull out concepts, strategic implications, operating implications, metrics, and repeatable playbooks.
   - Create or update knowledge notes only when the insight meaningfully informs durable understanding, current context, decisions, metrics, or playbooks.
   - For each candidate note, identify: title, target folder, key idea, and which source files or insight notes support it.
   - Prefer linking knowledge notes back to the relevant insight notes so the chain from knowledge to insight to evidence stays visible.

5. Ask clarifying questions if the extracted meaning is ambiguous.
   - Ask only when necessary.
   - Focus on ambiguity around note boundaries, categorisation, or priority.

6. Update existing notes first.
   - Search the relevant `Knowledge/Insights/` and `Knowledge/` folders before creating a new note.
   - Prefer extending an existing insight or knowledge note when the material clearly fits.

7. Create new notes only when needed.
   - Search the relevant `Knowledge/` folders before creating a new note.
   - Use the standard frontmatter from `AGENTS.md` unless the local folder uses an established variation.
   - Keep notes concise and durable.
   - Add `## Related` when cross-links improve navigation.
   - Add `## Sources` when the note is derived from `Research/`.

8. Update `Knowledge/glossary.md` when new terms appear or definitions sharpen.

9. Do not create anything in `Outputs/` unless the user explicitly asked for a polished deliverable.

## Rules

- Treat `Research/` as read-only unless the user explicitly asks for edits there.
- Write synthesized notes under `Knowledge/Insights/` by default.
- Let insight notes be the primary bridge between evidence and the rest of `Knowledge/`.
- Update `Knowledge/Foundations/` or `Knowledge/Operating System/` when an insight meaningfully changes or supports those notes.
- Prefer linking knowledge notes to supporting insight notes rather than treating the relationship as a one-way promotion step.
- For customer evidence, prefer disciplined discovery extraction over generic summarization.
- Edit only under `Knowledge/` and `Outputs/` by default.
- Use wiki-links like `[[Note Name]]`.
- Prefer the smallest correct update.
- Keep terminology consistent with `Knowledge/glossary.md`.
