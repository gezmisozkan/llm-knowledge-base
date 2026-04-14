# Dual Knowledge Base Router

## Purpose
This repository is a reusable template for two separate knowledge bases that can live side by side:

- `daily-kb/` for long-lived personal and reusable knowledge
- `repo-kb/` for knowledge about the current repository

These scopes are intentionally separate. They have different folders, different indexes, and different `CLAUDE.md` contracts.

---

## Required Startup Behavior For Any Agent
At the start of a session in this repo:
1. Read this file first.
2. Choose the correct scope.
3. Read the scoped contract:
   - `daily-kb/CLAUDE.md`, or
   - `repo-kb/CLAUDE.md`
4. Read that scope's `wiki/INDEX.md`.
5. Check the relevant `_index.md` before creating anything new.

---

## Scope Routing

### Use `repo-kb/` when the task is about
- the current repository's codebase
- architecture, components, workflows, setup, decisions, or debugging
- implementation-specific notes, incidents, or project commands
- requests such as "explore the codebase", "document this repo", or "save this repo knowledge"

### Use `daily-kb/` when the task is about
- general technical knowledge that outlives this repo
- personal preferences, rules, checklists, and recurring lessons
- reusable concepts not tied to the current repository
- requests such as "add this to the KB" when the content is broad rather than repo-specific

### If ambiguous
- default to `repo-kb/` if the conversation directly references files or behavior in this repository
- default to `daily-kb/` if the content is not dependent on this repository

### Promotion rule
If repo-specific work produces a lesson that is durable outside this repository:
- keep the concrete detail in `repo-kb/`
- promote only the reusable abstraction into `daily-kb/`

---

## Non-Negotiables
- Do not mix daily and repo knowledge in the same folder tree.
- Do not treat the repository root as a KB root.
- Do not save repo documentation into `daily-kb/` unless it has been deliberately generalized.
- Do not save personal or general knowledge into `repo-kb/` unless it is truly about this repository.
- Each KB must maintain its own `raw/`, `wiki/`, `outputs/`, and indexes.

---

## Quick Command Interpretation
- "explore the codebase and add it to the KB" -> use `repo-kb/`
- "document this repository" -> use `repo-kb/`
- "save this lesson/preference/concept" -> use `daily-kb/`
- "promote this" -> move a reusable abstraction from `repo-kb/` to `daily-kb/` when justified
- "answer from the KB" -> answer from the relevant scope, not both by default
