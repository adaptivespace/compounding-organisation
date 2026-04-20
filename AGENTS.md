# Knowledge Base Agent Manual (This Repo)

This vault is a markdown-first knowledge base.
This file defines how to ingest material from `Research/`, maintain curated knowledge in `Knowledge/`, and produce polished deliverables in `Outputs/`.

## Role

You are the maintainer of the curated knowledge base.

- You may read source material in `Research/` and distill it into durable notes in `Knowledge/`.
- You keep notes consistent, linked, and discoverable.
- You answer questions by consulting existing notes first, then file reusable insights back into `Knowledge/` when appropriate.

Ownership boundaries:

- Treat `Research/` as source material: read-only unless the user explicitly requests edits.
- You may edit anything under `Knowledge/` and `Outputs/`.
- `Templates/` holds reusable templates and reference scaffolding; update it only when the user asks or the workflow clearly requires it. Otherwise, read-only.
- `Context/` holds business and operational context. This is read-only.
- Ignore repo metadata and helper docs unless they are directly relevant to the task.

## Directory Structure

```
Research/                      Source material and raw inputs
  Customer/                    Customer research and notes
  Market/                      Market research and scans
  Signals/                     Signals, observations, and weak indicators
  Technology/                  Technology research and technical inputs

Knowledge/                     Curated knowledge base
  glossary.md                  Canonical terms and definitions
  Foundations/                 Durable conceptual and strategic knowledge
    Concepts/                  Core concepts
    Strategy/                  Strategic principles and frameworks
  Operating System/            How the organisation operates
    Active Context/            Current context and active working state
    Decision Records/          Durable decisions and rationale
    Metrics/                   Measures, scorecards, and KPIs
    Playbooks/                 Repeatable operating procedures

Outputs/                       Polished deliverables
  Guides/                      How-to and explanatory outputs
  Memos/                       Short-form decision or thinking memos
  Reports/                     Longer-form reports and synthesized output

Context/                       Business & Operational context
Templates/                     Reusable templates
docs/                          Repo-level supporting documentation
```

If a new category becomes necessary, add it under the closest fitting parent folder and update this manual if the structure meaningfully changes.

## Note Types (Where They Live)

- Research source material: `Research/`
- Concept notes: `Knowledge/Foundations/Concepts/`
- Strategy notes: `Knowledge/Foundations/Strategy/`
- Active context notes: `Knowledge/Operating System/Active Context/`
- Decision records: `Knowledge/Operating System/Decision Records/`
- Metrics notes: `Knowledge/Operating System/Metrics/`
- Playbooks: `Knowledge/Operating System/Playbooks/`
- Polished deliverables: `Outputs/Guides/`, `Outputs/Memos/`, `Outputs/Reports/`

Core reference pages:

- `Knowledge/glossary.md` is the canonical vocabulary.
- Folder-level `README.md` files define or introduce a section when present.
- `AGENTS.md` is the operational guide for maintaining the vault.

## Formatting Standards

Default to plain markdown.

For new knowledge notes, follow this pattern unless the surrounding folder uses a different established convention:

```yaml
---
title: <page title>
type: concept | strategy | active-context | decision-record | metric | playbook | memo | guide | report
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: [list of informing research files]
source_authors: [list of authors of source material]
tags: [relevant tags]
---
```

- Start with the key idea in 1-3 lines.
- Keep writing concise and durable.
- Add `## Related` with a short list of relevant wiki-links when cross-links will help navigation.
- Add `## Sources` when the note is derived from one or more documents in `Research/`.

File naming:

- Use Title Case with spaces, matching existing notes.
- Avoid renaming existing notes unless there is a clear benefit.

## Linking Standards

- Use wiki-links: `[[Note Name]]`.
- Prefer linking by note name rather than path unless there is a collision.
- When you create a new note, add meaningful links to adjacent concepts, strategies, decisions, or playbooks.
- Keep terminology consistent with `Knowledge/glossary.md`.

## Skills

Detailed operational workflows are lazy-loaded from `.claude/skills/` instead of being fully embedded here.

Available repository skills:

- `/ingest <source>`: process material from `Research/` into curated notes in `Knowledge/`
- `/query <question>`: answer from `Knowledge/` first, and optionally file reusable synthesis back into the vault
- `/ask <question>`: answer directly from `Knowledge/` without changing files
- `/lint [scope]`: perform low-risk maintenance on `Knowledge/` and, when requested, `Outputs/`
- `/output <request>`: create a polished guide, memo, or report in `Outputs/`
- `/log-decision [topic or transcript]`: capture a decision record and maintain links to earlier decisions, including supersession when applicable

Load these skills only when the task matches the workflow. Keep this file focused on enduring repository rules, taxonomy, and formatting standards.

## Workflow Summary

### Ingest

Trigger: user says `ingest <source>` or asks you to process material from `Research/`.

- Lazy-load and follow `.claude/skills/ingest/SKILL.md`.
- Core expectation: read from `Research/`, update existing notes before creating new ones, update `Knowledge/glossary.md` when needed, and do not create deliverables in `Outputs/` unless explicitly requested.

### Query

- Lazy-load and follow `.claude/skills/query/SKILL.md` for questions that may also produce reusable note updates.
- Use `.claude/skills/ask/SKILL.md` for read-only answers that should not change files.
- Core expectation: consult `Knowledge/` first and answer from the vault rather than improvising.

### Lint / Maintenance

- Lazy-load and follow `.claude/skills/lint/SKILL.md`.
- Core expectation: make incremental, low-risk fixes focused on placement, links, terminology, duplicates, and stale placeholders.

### Polished Outputs

- Lazy-load and follow `.claude/skills/output/SKILL.md` when the user asks for a memo, guide, report, or other polished deliverable.
- Core expectation: ground deliverables in `Knowledge/` first, then use `Research/` as supporting source material when needed.

### Decision Logging

- Lazy-load and follow `.claude/skills/log-decision/SKILL.md` when the user wants to record a decision or extract one from a meeting transcript.
- Core expectation: use the decision record template, ensure all required fields are captured, and update earlier decisions when one is superseded.

## Writing Style

When producing polished prose, follow any instructions in `Context/` if that directory exists for the task at hand.
For knowledge notes, prefer concise, high-signal writing with clear cross-links.

## Session Start Checklist

1. Read `AGENTS.md`.
2. Read `Knowledge/glossary.md`.
3. Inspect the relevant `Knowledge/`, `Research/`, or `Outputs/` subfolder for the task.
4. Identify whether the user wants ingest, query, maintenance, decision logging, or a polished output.

## Observability (Errors)

When an agent hits a blocker (tool failure, command failure, unexpected output), append to `error.log` at repo root.

```
[2026-02-03T15:04:05Z] <1-line summary>
Attempted: <goal, commands, files>
Error: <minimal relevant output>
RCA: <why it happened>
Proposed fix: <actionable next step>
```
