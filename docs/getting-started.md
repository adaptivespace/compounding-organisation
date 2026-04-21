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

The glossary is intentionally empty. You can seed it with your organisation's canonical terms if you want to start with a preferred vocabulary, but you do not have to. If you skip this step, `/ingest` will update `Knowledge/glossary.md` automatically when new terms appear or definitions sharpen.

**4. Add business context to `Context/`.**

The `Context/` folder holds information that shapes how the agent writes: your writing style, audience, and any standing constraints. A `styleguide.md` is already included as a starting point. Edit or replace it to reflect your organisation's voice.

## Try The Demo Flow

The fastest way to understand how this repository works is to ingest one of the bundled examples.

Start with the synthetic market report in `Research/Market/Evidence/2026-04-21 - Synthetic Market Report - Knowledge Operations Platforms.md`.

Run:

```bash
/ingest "@Research/Market/Evidence/2026-04-21 - Synthetic Market Report - Knowledge Operations Platforms.md"
```

What to look for after ingest:

- `Knowledge/Insights/Market/` gets a synthesized market insight note based on the report
- `Knowledge/glossary.md` may be updated automatically if the report introduces terms worth canonizing
- linked notes elsewhere in `Knowledge/` may be updated when the insight meaningfully informs them

This is the main demo flow for the repository: evidence in `Research/`, synthesis in `Knowledge/Insights/`, and linked organisational knowledge on top.

After that, ingest the synthetic discovery call in `Research/Customer/Evidence/2026-04-21 - Synthetic Discovery Call - ACME Inc.md`.

Run:

```bash
/ingest "@Research/Customer/Evidence/2026-04-21 - Synthetic Discovery Call - ACME Inc.md"
```

What to look for after ingest:

- `Knowledge/Insights/Customer/` gets a synthesized customer insight note based on the call
- `Knowledge/glossary.md` may be updated automatically if the call introduces terms worth canonizing
- linked notes elsewhere in `Knowledge/` may be updated when the customer insight meaningfully informs them

This gives you a second example of the same pattern using customer discovery evidence.

Once you have both the market and customer examples ingested, try an `/ask` flow that combines them.

Run:

```bash
/ask based on the latest market insights, and customer pain points, what are the key problems in the space and how are different competitors addressing those?
```

What to expect:

- the agent reads from `Knowledge/` first rather than returning to raw research by default
- it should combine the latest notes in `Knowledge/Insights/Market/` and `Knowledge/Insights/Customer/`
- it should synthesize the major problems in the category, compare those to the customer pain points in the discovery call, and summarize the main competitor response patterns

If you want that answer turned into a document, follow it with an `/output` request.

Run:

```bash
/output write a memo on the key problems in the knowledge operations space, how customer pain points map to them, and how different competitors are addressing those problems
```

What to expect:

- the agent uses the curated knowledge created by the earlier ingests
- it writes a memo into `Outputs/Memos/`
- the result is a saved document rather than only an in-chat answer

## How the knowledge base is structured

Three layers, one direction of flow:

| Layer | Folder | Purpose |
|---|---|---|
| Source material | `Research/` | Raw inputs: transcripts, scans, observations |
| Curated knowledge | `Knowledge/` | Synthesized insights plus linked durable knowledge |
| Polished deliverables | `Outputs/` | Guides, memos, and reports for an audience |

Raw material goes into `Research/`, where it stays as a source of reference. It can then be ingested into synthesized insight notes in `Knowledge/Insights/`. Those insights can in turn inform linked notes in the rest of `Knowledge/`, such as concepts, strategy, decisions, metrics, and playbooks. The agent reads the raw material in `Research/` but only edits it when you explicitly ask. Everything in `Knowledge/` and `Outputs/` is fair game.

Within `Knowledge/`, the structure is:

```
Knowledge/
  glossary.md                    Canonical terms — maintain this first
  Insights/
    Customer/                    Customer insight notes derived from evidence
    Market/                      Market insight notes derived from evidence
    Technology/                  Technology insight notes derived from evidence
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
| `/ingest <source>` | You have material in `Research/` and want it distilled into `Knowledge/Insights/` and linked knowledge notes |
| `/ask <question>` | You want a quick read-only answer — no file changes |
| `/output <request>` | You want a finished memo, analysis, guide, or report in `Outputs/` |
| `/log-decision <topic>` | You want to record a decision with full context and rationale |
| `/lint` | You want the agent to tidy links, fix placement, and flag stale placeholders |

## Your first workflow

A typical first session looks like this:

1. Start with one of the example files already in `Research/`, or drop your own source material into the appropriate `Research/` subfolder — `Customer/`, `Market/`, `Technology/`, or `Signals/`.
2. Run `/ingest` on the source. The agent reads the evidence, creates or updates synthesized insight notes in `Knowledge/Insights/`, updates the glossary automatically when needed, and links any affected knowledge notes in the appropriate `Knowledge/` subfolder.
3. For customer discovery calls, inspect the resulting note in `Knowledge/Insights/Customer/` and compare it with the original transcript to see how the evidence was turned into structured insight.
4. Once you have enough ingested material, run `/ask` to query the curated vault across customer, market, and other insight types.
5. If you want the answer captured as a document, follow the query with `/output` and ask for a memo or report. The agent drafts from `Knowledge/` first and writes to `Outputs/`.
6. Run `/log-decision` to capture any decision the material informs. The agent guides you through the required fields and links the record to the relevant insight and knowledge notes.

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
