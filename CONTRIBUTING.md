# Contributing

This repository is a public, forkable starting point for building a foundational part of a compounding organisation: its knowledge engine. Contribute only when the result improves the repo's structure, operating rules, or reusable scaffolding.

## What this repository is for

Contributions should strengthen one or more of these outcomes:

1. Make the repository easier to understand, fork, and extend.
2. Improve the repo's operating surface: skills, agent instructions, templates, examples, and structure.
3. Clarify how the system is maintained and how new material should be shaped.
4. Keep the repository easy to trim, adapt, and keep consistent over time.

## What belongs

Good contributions are usually one of these:

- updates to `README.md`, `AGENTS.md`, or other repo-level guidance
- new or improved skills, agent descriptions, or workflow instructions
- reusable templates, prompts, canvases, or contribution forms
- worked examples that show how the repository should be structured or used
- folder, naming, or placement conventions that make the vault easier to navigate
- small automation, validation, or linting improvements that keep the repo consistent

## What does not belong

Do not use this repository for:

- private notes, personal notes, or people profiles
- raw transcripts, raw call notes, or unredacted source material
- client-specific, employer-specific, or relationship-specific context
- CRM-style records such as contacts, accounts, deal histories, activity logs, or account plans
- system-of-record data that changes frequently and is already owned by another tool
- routine knowledge-note edits that do not change the repo's structure, workflows, or conventions
- idea fragments that depend on private context to make sense
- generic productivity advice or a broad digital garden of loosely related thoughts
- speculative templates or examples that do not solve a clear problem in the repository

When in doubt, exclude first.

## Why these exclusions exist

This repository is meant to stay public-safe, forkable, and structurally reusable.

- Relationship-specific history belongs in the relevant system of record, not in a reusable repository template.
- Volatile operational state creates maintenance noise and weakens the durability of the knowledge base.
- The repository should capture reusable learning, not duplicate records that already belong to CRM, support, finance, HR, or project tools.

In practice, this means customer transcripts and notes may inform examples, workflows, and structural guidance, but the repository should not become the place where someone checks the latest state of a contact, account, or deal.

## Before opening an issue or PR

1. Read the README, `AGENTS.md`, and the relevant nearby docs or skills.
2. Check whether the change improves the repo's structure or maintainability, not just a single note.
3. Keep the scope narrow. Small, coherent changes are preferred.
4. If the change adds a new file type, skill, agent pattern, or structural convention, open an issue first.

## Issues

Use issues to propose:

- a new template, example, or workflow
- a new skill or agent instruction pattern
- a folder, naming, or placement convention
- a repo-level automation or validation improvement
- a structural improvement that keeps the repository more forkable

Please include:

- the structural problem to solve
- who the change helps
- why the current repo shape is not enough
- the smallest useful change

## Pull requests

All changes to this repository must be made through a pull request. PRs should be focused, explain the why clearly, and use the template below.

## PR template

```md
## What?
## Why?
## How?
## Testing?
## Anything Else? (optional)
```

Use the template to describe the repo-structure impact clearly:

1. **What?** - which structural files changed
2. **Why?** - why the change improves the repo's workflows, templates, or maintainability
3. **How?** - how the structure, links, instructions, or examples were updated
4. **Testing?** - what you checked for consistency, formatting, links, placement, or behavior
6. **Anything Else? (optional)** - follow-up work, context, or open questions

Preferred PR characteristics:

- one logical change per PR
- concise writing and minimal duplication
- no broad folder reshuffles without prior discussion

## Editing scope

This contribution guide is for changes that shape the repository itself.

- Use the normal knowledge workflows for day-to-day note creation and curation.
- Use PRs here when the change affects structure, skills, agent instructions, examples, templates, or repo-level conventions.
- If a note edit only changes content inside the knowledge base and does not alter the system around it, it probably does not belong in a repo-structure PR.

## File placement

Use the repository structure deliberately:

- `docs/` for narrative and explanatory documents about how the system works
- `.claude/skills/` for skills and their workflows
- `examples/` for worked examples and reference patterns
- `templates/` for reusable authoring or contribution templates
- `Knowledge/` for structural conventions, folder guidance, and system-level reference pages

For example:

- guidance on integrating this engine with CRM or other operational tools belongs in `docs/`
- actual CRM records or account histories do not belong in the repository

If a contribution does not clearly fit one of those purposes, it probably does not belong yet.

## Licensing

This repository currently uses the MIT License. By contributing, you agree that your contribution will be released under that license unless maintainers state otherwise.

## Maintainer review criteria

Maintainers will favor contributions that are:

- public-safe
- evidence-based
- reusable
- small in scope
- aligned with the repository thesis

Contributions may be declined if they increase maintenance burden, duplicate existing material, or push the repository toward a generic digital garden.
