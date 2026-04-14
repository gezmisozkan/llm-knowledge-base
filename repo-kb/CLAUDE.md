# Repository Knowledge Base Operating Contract

## Purpose
`repo-kb/` is a markdown-first knowledge base for the current repository. It captures durable facts about this codebase: architecture, components, setup, workflows, decisions, debugging notes, and repository-specific lessons.

The knowledge base root for this scope is `repo-kb/`.

Core folders:
- `raw/` stores raw exploration notes, copied docs, logs, errors, and source material.
- `wiki/` stores curated canonical knowledge about the repository.
- `outputs/` stores generated briefings, answers, and reports.

---

## Required Startup Behavior For Any Agent
At the start of work in this scope:
1. Read this file first.
2. Read `repo-kb/wiki/INDEX.md`.
3. Check the relevant repo-specific `_index.md` before creating anything new.
4. Prefer updating existing pages over creating duplicates.

---

## Repo Routing — Where To File Things

`repo-kb/wiki/` uses project-first organization. Use this table to file pages:

| Domain | File here | Not here |
|---|---|---|
| `architecture/` | system structure, main modules, data flow, boundaries, diagrams-in-words | implementation notes for a single component |
| `components/` | individual modules, services, packages, features, interfaces | global architectural decisions |
| `workflows/` | build, test, release, local dev, CI, operational playbooks | durable general knowledge not tied to this repo |
| `decisions/` | repository-specific design choices, tradeoffs, migrations, policy choices | generic best practices |
| `debugging/` | incidents, failure modes, troubleshooting, recurring bugs, gotchas | one-off noisy logs with no durable value |
| `setup/` | environment setup, prerequisites, install steps, credentials locations, bootstrapping | general tool usage that is not repo-specific |

If something does not fit, create a new folder with an `_index.md` inside `repo-kb/wiki/`.

---

## Passive Capture Rules — When To Write Without Being Asked

After every substantive repo-focused exchange, evaluate this decision tree:

```text
Did we learn something durable about this repository?
|- YES: Already in repo-kb/wiki/?
|       |- YES, new detail or correction -> update existing page at session end
|       `- NO: Is it likely useful next time someone explores this repo?
|               |- YES -> create a new repo wiki page at session end
|               `- NO  -> save to repo-kb/raw/inbox/ if the source may still help later
`- NO: Was there a raw source (log, command output, pasted doc, screenshot)?
        |- YES -> save to repo-kb/raw/ immediately
        `- NO  -> nothing to do
```

Durable repo knowledge includes:
- architecture facts and component responsibilities
- setup steps and environment expectations
- recurring debugging patterns and failure signs
- repository-specific commands and workflows
- decisions with context and tradeoffs

Not durable:
- noisy one-off command output with no future value
- speculation not verified against the codebase or user input
- general knowledge that belongs in `daily-kb/`

---

## Session-End Capture Protocol

At natural session end, propose a capture summary such as:

```text
Session capture ready:
1. repo-kb/wiki/architecture/system-overview.md (NEW) - main repository structure
2. repo-kb/wiki/debugging/playbook-fix-local-setup.md (UPDATE) - add failure signs
3. repo-kb/raw/inbox/test-run-log.md (NEW) - raw command output

Proceed? (or "skip" to skip all)
```

Rules:
- Raw captures in `repo-kb/raw/` happen immediately without confirmation.
- Wiki writes are batched to session end unless the user asks to save immediately.
- After adding a page, update the relevant `_index.md` and `repo-kb/wiki/INDEX.md`.

---

## Default Behavior When The User Says "Add This To The KB"

1. If the material is an error log, command output, copied doc, or rough exploration note:
   - save it to the appropriate place in `repo-kb/raw/` first
   - preserve the source faithfully
   - promote to `repo-kb/wiki/` only if durable knowledge can be extracted safely

2. If the material is a stable repo fact, workflow, decision, setup rule, or debugging lesson:
   - search the most relevant existing page in `repo-kb/wiki/`
   - update it if it exists
   - create a new page only if no good existing page fits

3. If the user asks a question about this repository:
   - answer from `repo-kb/wiki/` first
   - use `repo-kb/raw/` only to verify or fill gaps
   - save generated answers in `repo-kb/outputs/answers/` when useful

4. If a lesson becomes reusable beyond this repo:
   - keep the repo-specific version here
   - promote the generalized version into `daily-kb/`

---

## Folder Contract

### `repo-kb/raw/`
Use for unprocessed or minimally processed repository material.

Subfolders:
- `raw/inbox/`
- `raw/web/`
- `raw/notes/`
- `raw/docs/`
- `raw/screenshots/`

Rules:
- Never overwrite raw source material with polished summaries.
- Keep enough source context to retrace a repo claim.

### `repo-kb/wiki/`
Use for durable, canonical, linked repository knowledge.

Rules:
- Prefer small pages with one main concern.
- Link related pages with `[[page-name]]` syntax.
- Update the relevant `_index.md` and `repo-kb/wiki/INDEX.md` after changes.

### `repo-kb/outputs/`
Use for generated repo answers, briefings, reports, and health checks.

Outputs are not canonical by default. Promote stable parts into `repo-kb/wiki/` when justified.

---

## Frontmatter Standard For Durable Wiki Notes

```yaml
---
title: Note Title
type: system
status: canonical
source_type: derived
sources: []
tags: []
domain: architecture
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
- Do not mix repo knowledge with `daily-kb/` by default.
- Do not store general evergreen knowledge here unless it is tied to this repository.
- Do not create duplicate pages for the same repo topic.
- Do not overwrite raw source material with polished summaries.
- Do not hide ambiguity.
- After every substantive repo session, run the passive capture evaluation.
