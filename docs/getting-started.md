# Getting started

This repository is a ready-to-fork knowledge base structure for building a compounding organisation — one where research, decisions, and operating knowledge accumulate and connect across cycles rather than being lost between them. Fork it, configure a few things, and you can be ingesting material and logging decisions within minutes.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) (or any Claude agent runner such as [OpenCode](https://opencode.ai) that reads `AGENTS.md`)
- A Markdown editor or Obsidian (optional but useful for browsing the vault)

## Setup

**1. Fork or clone the repository.**

```bash
git clone https://github.com/your-org/compounding-organisation.git my-knowledge-base
cd my-knowledge-base
```

**2. Open it in Claude Code.**

```bash
claude
```

Claude will read `CLAUDE.md` automatically and understand its role as knowledge base maintainer.

**3. Populate `Knowledge/glossary.md`.**

The glossary is intentionally empty. Add your organisation's canonical terms before you begin ingesting material — this ensures consistent vocabulary across all notes from the start. Even five to ten terms is enough to begin.

**4. Add business context to `Context/`.**

The `Context/` folder holds information that shapes how the agent writes: your writing style, audience, and any standing constraints. A `styleguide.md` is already included as a starting point. Edit or replace it to reflect your organisation's voice.

## How the knowledge base is structured

Three layers, one direction of flow:

| Layer | Folder | Purpose |
|---|---|---|
| Source material | `Research/` | Raw inputs: transcripts, scans, observations |
| Curated knowledge | `Knowledge/` | Durable, linked notes distilled from Research |
| Polished deliverables | `Outputs/` | Guides, memos, and reports for an audience |

Raw material goes into `Research/`, where it stays as a source of reference. It can then be ingested so that it transforms into atomic notes in `Knowledge/`, and from `Knowledge/` these atomic notes can be synthesised into `Outputs/`. The agent reads the raw material in `Research/` but only edits it when you explicitly ask. Everything in `Knowledge/` and `Outputs/` is fair game.

Within `Knowledge/`, the structure is:

```
Knowledge/
  glossary.md                    Canonical terms — maintain this first
  Foundations/
    Concepts/                    Core conceptual notes
    Strategy/                    Strategic frameworks and principles
  Operating System/
    Active Context/              Current working state and open threads
    Decision Records/            Durable records of key decisions
    Metrics/                     Measures, scorecards, and KPIs
    Playbooks/                   Repeatable operating procedures
```

## The six skills

The agent exposes six slash commands for repeatable workflows. Run them inside a Claude Code session.

| Command | When to use |
|---|---|
| `/ingest <source>` | You have material in `Research/` and want it distilled into `Knowledge/` |
| `/ask <question>` | You want a quick read-only answer — no file changes |
| `/output <request>` | You want a finished memo, analysis, guide, or report in `Outputs/` |
| `/log-decision <topic>` | You want to record a decision with full context and rationale |
| `/lint` | You want the agent to tidy links, fix placement, and flag stale placeholders |

## Your first workflow

A typical first session looks like this:

1. Drop a document, interview transcript, or set of notes into the appropriate `Research/` subfolder — `Customer/`, `Market/`, `Technology/`, or `Signals/`.
2. Run `/ingest Research/Customer/your-file.md`. The agent reads the source, extracts durable notes, updates the glossary if needed, and places notes in the correct `Knowledge/` subfolder.
3. Run `/log-decision` to capture any decision the material informs. The agent guides you through the required fields and links the record to related notes.
4. When you need to share findings, run `/output a memo on X`. The agent drafts from `Knowledge/` first and writes to `Outputs/Memos/`.

## Templates

Reusable templates live in `Templates/`. They are not used directly — copy them as the starting point for new notes when you are working outside of a skill workflow.

```
Templates/
  Knowledge/
    Concept.md           Frontmatter and structure for a concept note
    Decision Record.md   Frontmatter and structure for a decision record
```

## Next steps

- Read `README.md` for the full rationale behind the three-layer architecture.
- Read `AGENTS.md` for the complete operational rules the agent follows.
- Check `CONTRIBUTING.md` before adding anything to the public repository — it sets out what belongs here and what does not.
