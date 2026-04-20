---
name: query
description: Answer a question from the curated Knowledge base first, then optionally file reusable insights back into Knowledge. Trigger with /query <question>.
user-invocable: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
---

# /query - Knowledge Base Query

Use this skill when the user asks a question about the vault and the output should result in a new document. The answer should come from curated notes first.

Arguments passed: `$ARGUMENTS`

## Goal

Answer from `Knowledge/` before improvising, then store genuinely reusable synthesis back into the knowledge base when appropriate.

## Workflow

1. Parse the question from `$ARGUMENTS`.
   - If no question is provided, ask the user what they want to know.

2. Search `Knowledge/` first.
   - Start with `Knowledge/glossary.md` when terminology matters.
   - Search the relevant subfolders for matching notes.

3. Read the relevant notes and synthesize across them.
   - Prefer the vault's existing language and framing.
   - If the vault is incomplete, say so clearly.

4. Answer the user directly.
   - Lead with the answer.
   - Reference supporting notes with wiki-links when helpful.
   - Distinguish clearly between note-backed statements and gaps.

5. File reusable insights back only when warranted.
   - Update an existing note if the synthesis belongs there.
   - Create a new note only if the answer produced a durable frame that will likely be reused.
   - Update `Knowledge/glossary.md` if a term needs to be added or tightened.

## Rules

- Consult `Knowledge/` before improvising.
- Do not invent note content or citations.
- Prefer updating existing notes over creating new ones.
- Keep any file changes concise and durable.
