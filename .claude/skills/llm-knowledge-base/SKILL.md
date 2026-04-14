---
name: llm-knowledge-base
description: Maintain a reusable dual-scope knowledge base with separate daily and repo-specific roots. Use when working inside this repository to route captures to the correct KB, update canonical notes, answer from the right scope, and promote durable knowledge across scopes when justified.
compatibility: Works with repo-aware coding agents that can read and write local files.
---

# LLM Knowledge Base Workflow

This repository contains two separate knowledge bases:

- `daily-kb/` for long-lived personal and reusable knowledge
- `repo-kb/` for knowledge about the current repository

## First Steps
1. Read root `CLAUDE.md` to choose the right KB.
2. Read the scoped contract: `daily-kb/CLAUDE.md` or `repo-kb/CLAUDE.md`.
3. Read that scope's `wiki/INDEX.md`.
4. Check the relevant scoped `_index.md` before creating anything new.

## Routing Defaults
- If the task is about this codebase, architecture, setup, workflows, bugs, or design decisions, use `repo-kb/`.
- If the task is a general concept, reusable lesson, personal preference, or cross-repo knowledge, use `daily-kb/`.
- If repo-specific knowledge becomes broadly reusable, keep the detailed version in `repo-kb/` and promote a distilled version to `daily-kb/`.

## Operating Rules
- Keep the two KBs separate; do not mix files across scopes.
- Put rough or source-like material into the chosen scope's `raw/` first.
- Put durable canonical knowledge into the chosen scope's `wiki/`.
- Put generated answers and reports into the chosen scope's `outputs/`.
- Prefer updating existing scoped pages over creating duplicates.
- Preserve uncertainty when the source is incomplete.

## Typical Commands
- Explore a repo and capture findings -> `repo-kb/`
- Save a reusable concept or personal rule -> `daily-kb/`
- Answer from one KB -> read that scope's `wiki/` first
- Promote reusable lessons -> distill from `repo-kb/` into `daily-kb/` when justified
