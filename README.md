# The Compounding Organisation

This repository is a markdown-first knowledge engine for building a compounding organisation.

It is designed to help turn raw research and signals into durable knowledge, connect that knowledge to decisions and operating practice, and produce shared context that can be queried when needed.

## What this is

The repository separates work into three layers:

- `Research/` holds raw source material
- `Knowledge/` holds curated, durable notes
- `Outputs/` holds polished guides, memos, and reports

The goal is to make knowledge reusable over time rather than trapped in one-off notes, chats, or documents.

## What this is not

This repository is not a general-purpose operating system for every kind of organisational data.

- It is not a CRM for managing contacts, accounts, opportunities, activities, or relationship history.
- It is not a system of record for person-level or company-level operational state.
- It is not a safe default location for people profiles, account plans, private customer memory, or relationship-specific context.
- It is not a replacement for project management, ticketing, support, finance, or HR systems.

The rationale is simple: this repository is optimized for compounding knowledge, not for volatile operational state. The question this repository should answer is usually "what are we learning that should remain useful across cycles?" rather than "what happened last with this specific person or account?"

That means customer call transcripts may begin in `Research/` as source material, but the durable output here should be reusable insight such as recurring pains, buying triggers, objections, language patterns, strategic implications, and operating decisions. Relationship memory such as "what was last discussed with person X at company Y?" belongs in the relevant external system of record.

See `docs/connecting-to-systems-of-record.md` for a practical integration model.

## How it works

The core workflow is:

1. Capture source material in `Research/`
2. Distill synthesized insights into `Knowledge/Insights/`
3. Link concepts, strategy, decisions, metrics, and playbooks back to those insights so they are discoverable
4. Produce polished deliverables in `Outputs/` when needed

In practice:

- customer, market, technology, and signal inputs begin in `Research/`
- synthesized customer, market, and technology insights live in `Knowledge/Insights/`
- durable concepts and strategic frames live in `Knowledge/Foundations/`
- decisions, active context, metrics, and playbooks live in `Knowledge/Operating System/`
- outward-facing or polished internal deliverables live in `Outputs/`

The boundary is intentional:

- `Research/` can hold source material that informs learning
- `Knowledge/Insights/` holds the primary synthesis layer that connects evidence to the rest of the vault
- `Knowledge/` should hold reusable patterns, not account-by-account memory
- operational systems should continue to own the current state of relationships, workflows, and transactions

### Powered by agentic workflows
This repository is designed to be curated by agents as well as humans.

The skills in `.claude/skills/` let an agent load a focused workflow only when it is needed, instead of carrying all workflow instructions all the time. That keeps the repository maintainable while still making common tasks reliable and repeatable.

In practice, this means an agent can help with specific jobs such as:

- ingesting source material from `Research/` into synthesized insight notes and linked knowledge notes in `Knowledge/`
- answering questions from the existing knowledge base
- answering directly from the vault without changing files
- linting the vault for placement, linking, terminology, and duplicate-note issues
- producing polished outputs in `Outputs/`
- logging decisions and updating earlier decisions when one supersedes another

Current repository skills:

- `ingest/` - research ingestion and transformation into synthesized insights and linked knowledge
- `ask/` - direct, read-only answers from the curated vault
- `output/` - knowledge-base-first memos, analyses, guides, or reports in `Outputs/`
- `log-decision/` - structured decision capture and supersession handling
- `lint/` - low-risk maintenance of the knowledge base to ensure links are not broken

Available repository workflows include:

- ingesting research into insights and curated knowledge
- querying the vault
- answering directly from the vault without edits
- linting and maintaining the knowledge base
- producing polished outputs
- logging decisions

## Repository structure

```text
Research/
  Customer/
  Market/
  Signals/
  Technology/

Knowledge/
  glossary.md
  Insights/
    Customer/
    Market/
    Technology/
  Foundations/
    Concepts/
    Strategy/
  Operating System/
    Active Context/
    Decision Records/
    Metrics/
    Playbooks/

Outputs/
  Guides/
  Memos/
  Reports/

Context/
Templates/
docs/
```

## What goes where

- `Research/`: raw notes, transcripts, reports, scans, and experiments
- `Knowledge/Insights/`: synthesized customer, market, and technology insights derived from source material in `Research/`
- `Knowledge/Foundations/Concepts/`: durable concepts and mental models
- `Knowledge/Foundations/Strategy/`: enduring strategic choices like ICP, positioning, and long-term bets
- `Knowledge/Operating System/Active Context/`: what is true right now for the current phase, initiative, or period
- `Knowledge/Operating System/Decision Records/`: durable records of important decisions and their rationale
- `Knowledge/Operating System/Metrics/`: metric definitions and measurement logic
- `Knowledge/Operating System/Playbooks/`: repeatable operating procedures
- `Outputs/`: polished deliverables created from the curated knowledge base

Rule of thumb:

- `Research/` is exploratory and source-oriented
- `Knowledge/Insights/` is the synthesized bridge between evidence and the rest of the knowledge base
- `Knowledge/` is curated and durable
- `Outputs/` is polished and audience-ready

Another useful rule of thumb:

- if it is specific to one person, one company, one deal, or one live workflow, it probably belongs in another system
- if it captures a reusable pattern, insight, decision, metric definition, or repeatable practice, it likely belongs here

## Writing conventions

- Use plain markdown
- Use wiki-links like `[[Note Name]]`
- Keep notes concise, durable, and cross-linked
- Follow `Knowledge/glossary.md` for canonical terminology
- Use the templates in `Templates/` when creating common note types

Most curated notes should use frontmatter like:

```yaml
---
title: <page title>
type: insight | concept | strategy | active-context | decision-record | metric | playbook | memo | guide | report
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []
source_authors: []
tags: []
---
```

## Decision logging

Decisions are stored in `Knowledge/Operating System/Decision Records/`.

Decision records are meant to capture:

- context
- the tension or problem being faced
- the chosen path
- the rejected path
- the intended outcome
- the accepted tradeoffs

If a newer decision supersedes an older one, the older decision should be marked as superseded and linked to the newer record.

## Templates and skills

- `Templates/` contains reusable note and output templates
- `.claude/skills/` contains lazy-loaded workflow instructions for repeatable repository tasks
- `AGENTS.md` is the canonical operating manual for maintaining the vault

## If you are working in this repo

Start here:

1. Read `README.md`
2. Read `Knowledge/glossary.md`
3. Inspect the relevant area of `Research/`, `Knowledge/`, or `Outputs/`
4. Use the existing taxonomy before creating new categories

Treat `Research/` as source material by default. Capture synthesis in `Knowledge/Insights/`, update the rest of `Knowledge/` when those insights meaningfully inform it, and create deliverables in `Outputs/` only when needed.
