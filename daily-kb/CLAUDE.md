# Daily Knowledge Base Operating Contract

## Purpose
`daily-kb/` is a universal, markdown-first second brain for long-lived personal and reusable knowledge. Technical notes, tool habits, style preferences, recurring checklists, and cross-project lessons all live here as durable knowledge.

The knowledge base root for this scope is `daily-kb/`.

Core folders:
- `raw/` stores incoming source material and rough captures.
- `wiki/` stores curated canonical knowledge, organized by domain.
- `outputs/` stores generated answers, reports, and temporary artifacts.

---

## Required Startup Behavior For Any Agent
At the start of work in this scope:
1. Read this file first.
2. Read `daily-kb/wiki/INDEX.md`.
3. Check the relevant domain `_index.md` before creating anything new.
4. Prefer updating existing pages over creating duplicates.

---

## Domain Routing — Where To File Things

`daily-kb/wiki/` uses domain-first organization. Each domain is a folder. Use this table to file pages:

| Domain | File here | Not here |
|---|---|---|
| `linux/` | bash, shell builtins, coreutils, WSL, file system, permissions, processes, signals | Git workflows, Python scripts |
| `python/` | language syntax, stdlib, packaging, typing, testing, common patterns | ML and DL libraries |
| `ml/` | sklearn, classical algorithms, feature engineering, evaluation metrics, data pipelines | Neural nets and training loops |
| `dl/` | PyTorch, optimizers, schedulers, loss functions, training loops, datasets | Classical ML algorithms |
| `git/` | branching strategies, rebase, tags, workflows, hooks, config | `.gitattributes` |
| `tools/` | VS Code, tmux, docker, conda, curl, jq, cloud drives, system configs | Topics that clearly belong to another domain |
| `style/` | clothing, dress codes, outfit combinations, color theory, seasonal choices | - |
| `daily/` | cross-domain patterns and lessons that genuinely span multiple areas | Anything with a clear single domain |

If something does not fit any existing domain, create a new folder with an `_index.md`.

Do not force topics into `daily/` to avoid a filing decision.

---

## Passive Capture Rules — When To Write Without Being Asked

After every substantive exchange, evaluate this decision tree:

```text
Did we discuss something factual, procedural, or conceptual?
|- YES: Already in daily-kb/wiki/?
|       |- YES, new detail or correction -> update existing page at session end
|       `- NO: Is it durable? (still true next week?)
|               |- YES -> create new wiki page at session end
|               `- NO  -> save to daily-kb/raw/inbox/ with a brief note
`- NO: Was there a raw source (error output, pasted text, URL, screenshot)?
        |- YES -> save to daily-kb/raw/ immediately
        `- NO  -> nothing to do
```

Durable knowledge includes:
- commands, flags, and syntax patterns that work consistently
- concepts that explain why something behaves a certain way
- stable decisions, preferences, and reusable checklists
- lessons that will still matter outside this repository

Not durable:
- one-off run details or experiment logs
- unconfirmed speculation
- transient conversation context with no reusable value

---

## Session-End Capture Protocol

At natural session end, propose a capture summary such as:

```text
Session capture ready:
1. daily-kb/wiki/linux/bash-redirects.md (NEW) - bash redirect semantics
2. daily-kb/wiki/tools/vscode-status-bar.md (UPDATE) - add status bar tip
3. daily-kb/raw/inbox/experiment-notes.md (NEW) - rough notes

Proceed? (or "skip" to skip all)
```

Rules:
- Raw captures in `daily-kb/raw/` happen immediately without confirmation.
- Wiki writes are batched to session end unless the user explicitly asks to save now.
- After adding a page, update the domain `_index.md` and `daily-kb/wiki/INDEX.md`.

---

## Default Behavior When The User Says "Add This To The KB"

1. If the material is rough, partial, pasted, copied, or source-like:
   - save it to the appropriate place in `daily-kb/raw/` first
   - preserve it faithfully
   - update `daily-kb/wiki/` only if durable knowledge can be extracted safely

2. If the material is a stable concept, lesson, checklist, policy, or preference:
   - search for the most relevant existing page in the correct domain
   - update it if it exists
   - create a new page only if no good existing page fits

3. If the user asks a question:
   - answer from `daily-kb/wiki/` first
   - use `daily-kb/raw/` only to verify claims or fill gaps
   - save generated answers in `daily-kb/outputs/answers/` when useful

4. If the information is uncertain:
   - state that clearly
   - do not invent certainty
   - preserve ambiguity when needed

---

## Folder Contract

### `daily-kb/raw/`
Use for unprocessed or minimally processed material.

Subfolders:
- `raw/inbox/`
- `raw/web/`
- `raw/notes/`
- `raw/docs/`
- `raw/screenshots/`

Rules:
- Never overwrite raw source material with polished summaries.
- Favor faithful capture over cleanup.

### `daily-kb/wiki/`
Use for durable, canonical, linked knowledge.

Rules:
- Prefer small, atomic pages.
- Every important page begins with frontmatter and a short summary.
- Link related pages with `[[page-name]]` syntax.
- Update the relevant `_index.md` and `daily-kb/wiki/INDEX.md` after changes.

### `daily-kb/outputs/`
Use for generated answers, briefings, reports, and health checks.

Outputs are not canonical by default. Promote stable parts into `daily-kb/wiki/` when justified.

---

## Frontmatter Standard For Durable Wiki Notes

```yaml
---
title: Note Title
type: concept
status: canonical
source_type: derived
sources: []
tags: []
domain: linux
created: 2026-04-14
updated: 2026-04-14
aliases: []
confidence: medium
---
```

---

## Naming And Linking Rules
- Use lowercase kebab-case filenames.
- Keep names short and explicit.
- Prefer one topic per page.
- Playbooks use the prefix `playbook-`.
- Decisions use the prefix `decision-`.
- Every domain folder must have an `_index.md`.

---

## Non-Negotiables
- Do not create duplicate pages for the same topic.
- Do not overwrite raw source material with polished summaries.
- Do not hide ambiguity.
- Do not put repo-specific documentation in `daily-kb/` unless it has been deliberately generalized.
- After every substantive session, run the passive capture evaluation.
