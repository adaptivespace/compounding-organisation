---
name: ask
description: Answer directly from the curated Knowledge base without updating files. Read-only fast path for questions. Trigger with /ask <question>.
user-invocable: true
allowed-tools:
  - Read
  - Glob
  - Grep
---

# /ask - Direct Knowledge Answer

Use this skill when the user wants a direct answer from the vault but does not want note maintenance as part of the task.

Arguments passed: `$ARGUMENTS`

## Goal

Answer quickly from `Knowledge/` without changing any files.

## Workflow

1. Parse the question.
2. Search `Knowledge/` for relevant notes.
3. Read the minimum set of notes needed to answer well.
4. Answer directly and clearly.
5. State gaps if the vault does not cover the topic.

## Rules

- This skill is read-only.
- Consult `Knowledge/` before improvising.
- Do not write notes, update glossary entries, or create outputs.
