# `.claude/`

This folder is for project-specific Claude configuration and scaffolding.

## Purpose

Use this directory for Claude-only materials that help agents work on this repository, such as:

- reusable prompts for recurring repository tasks
- project-specific skills or skill scaffolding
- local Claude-oriented configuration notes

## Relationship to `AGENTS.md`

`AGENTS.md` is the canonical cross-agent instruction file for this repository.

- Put shared repository rules in `AGENTS.md`.
- Do **not** duplicate those rules here.
- Keep `CLAUDE.md` as a symlink to `AGENTS.md`.

Use `.claude/` only when something is genuinely Claude-specific.

## Current structure

- `skills/` - placeholder location for project-specific Claude skills

Keep this directory minimal. Add new files only when they support real project workflows.
