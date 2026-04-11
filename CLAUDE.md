# Knowledge Base Operating Contract

## Purpose
This repository is a universal, markdown-first second brain for all personal knowledge — technical, creative, and lifestyle. Engineering notes, ML experiments, fashion choices, tool configs, and daily lessons all live here as equals.

The repository root is the knowledge base root.

Core folders:
- `raw/` stores incoming source material and rough captures.
- `wiki/` stores curated canonical knowledge, organized by domain.
- `outputs/` stores generated answers, reports, and temporary artifacts.

---

## Required Startup Behavior For Any Agent
At the start of a session in this repo:
1. Read this file first.
2. Read `wiki/INDEX.md`.
3. Check the relevant domain `_index.md` before creating anything new.
4. Prefer updating existing pages over creating duplicates.

---

## Domain Routing — Where To File Things

`wiki/` uses domain-first organization. Each domain is a folder. Use this table to file pages:

| Domain | File here | Not here |
|---|---|---|
| `linux/` | bash, shell builtins, coreutils (sed, awk, grep, find), WSL, file system, permissions, processes, signals | Git workflows (→ `git/`), Python scripts |
| `python/` | language syntax, stdlib, packaging (pip, venv, poetry), typing, testing (pytest), common patterns | ML/DL libraries (→ `ml/` or `dl/`) |
| `ml/` | sklearn, classical algorithms (SVM, trees, regression), feature engineering, evaluation metrics, data pipelines | Neural nets, PyTorch, training loops (→ `dl/`) |
| `dl/` | PyTorch, training loops, optimizers, schedulers, loss functions, debugging DL, datasets, dataloaders | Classical ML algorithms (→ `ml/`) |
| `git/` | branching strategies, rebase, tags, workflows, hooks, config | `.gitattributes` (→ `linux/`) |
| `tools/` | VS Code, tmux, docker, conda, curl, jq, cloud drives, system configs, any utility tool | Things clearly belonging to a language domain |
| `style/` | clothing, dress codes, outfit combinations, color theory, smart casual rules, seasonal choices | — |
| `daily/` | patterns and lessons that genuinely span multiple domains | Anything with a clear single domain |

**Adding a new domain:** If something doesn't fit any existing domain, create a new folder with an `_index.md` — no other structural changes needed. Examples: `health/`, `finance/`, `books/`, `cooking/`.

**Do not force topics into `daily/` to avoid a filing decision.** If it belongs to a domain, file it there.

---

## Passive Capture Rules — When To Write Without Being Asked

After every substantive exchange, evaluate this decision tree:

```
Did we discuss something factual, procedural, or conceptual?
├─ YES: Already in wiki/?
│       ├─ YES, new detail or correction → update existing page at session end
│       └─ NO: Is it durable? (still true next week?)
│               ├─ YES → create new wiki page at session end
│               └─ NO  → save to raw/inbox/ with a brief note
└─ NO: Was there a raw source (error output, pasted text, URL, screenshot)?
        ├─ YES → save to raw/ immediately (no confirmation needed)
        └─ NO  → nothing to do
```

A fact is **durable** if it is:
- A command, flag, or syntax pattern that works consistently
- A concept explaining WHY something behaves a certain way
- A decision the user made with reasoning
- A checklist that will be reused
- A preference or rule the user has settled on (technical or personal)

A fact is **not durable** if it is:
- Specific to a single run or experiment → save to `raw/` instead
- Pure speculation not confirmed by the user
- Conversational context with no lasting value

---

## Session-End Capture Protocol

At natural session end (user says "thanks", "ok", "done", or stops), propose a capture summary:

```
Session capture ready:
1. wiki/linux/bash-redirects.md (NEW) — bash redirect semantics
2. wiki/linux/line-endings.md (UPDATE) — add VS Code status bar tip
3. raw/inbox/experiment-notes.md (NEW) — raw training run output

Proceed? (or "skip" to skip all)
```

Rules:
- Raw source captures (`raw/`) happen **immediately without confirmation** — `raw/` is always safe.
- Wiki writes are **batched to session end** — do not interrupt mid-conversation.
- If the user says "capture this" or "save this" mid-session, execute immediately.
- After writing, update the domain `_index.md` and the Recent additions section of `wiki/INDEX.md`.

---

## Default Behavior When The User Says "Add This To The KB"

1. If the user gives rough notes, pasted text, copied material, links, screenshots, transcripts, or incomplete thoughts:
   - save it to the appropriate place in `raw/` first
   - preserve the source faithfully
   - update `wiki/` only if durable knowledge can be extracted safely

2. If the user gives a stable concept, lesson, system detail, checklist item, policy, or decision:
   - search for the most relevant existing page in the correct domain folder
   - update that page if it exists
   - create a new page only if no good existing page fits
   - file under the correct domain using the Domain Routing table above

3. If the user asks a question:
   - answer from `wiki/` first
   - use `raw/` only to verify claims or fill missing context
   - save the response in `outputs/answers/` if it is a generated answer rather than canonical knowledge
   - promote durable parts back into `wiki/` when justified

4. If the information is uncertain, incomplete, or contradictory:
   - state that clearly
   - do not invent certainty
   - preserve unresolved ambiguity when needed

---

## Folder Contract

### raw/
Use `raw/` for unprocessed or minimally processed material.

Subfolders:
- `raw/inbox/` for quick captures and unsorted inputs
- `raw/web/` for web pages and scraped sources
- `raw/notes/` for rough notes and observations
- `raw/docs/` for internal docs and structured copied material
- `raw/screenshots/` for images and visual references

Rules:
- Never overwrite raw source material with polished summaries.
- Favor faithful capture over cleanup.
- Add minimal source context only when useful.

### wiki/
Use `wiki/` for durable, canonical, linked knowledge.

Structure:
- Domain folders: `linux/`, `python/`, `ml/`, `dl/`, `git/`, `tools/`, `style/`, `daily/`, and any future domains.
- Every domain folder has an `_index.md` listing all pages in that domain.
- `wiki/INDEX.md` is the top-level entry point — a domain table, not a flat page list.

Rules:
- File pages under the correct domain folder. Consult the Domain Routing table.
- Prefer small, atomic pages over long mixed pages.
- Every important page begins with frontmatter and a short summary paragraph.
- Link related pages with `[[page-name]]` syntax.
- After adding any page to a domain, update that domain's `_index.md` and the Recent additions section of `wiki/INDEX.md`.
- Mark uncertainty explicitly.

### outputs/
Use `outputs/` for generated answers, briefings, reports, and health checks.

Rules:
- Outputs are not canonical by default.
- If an output contains durable knowledge, promote the stable parts into `wiki/`.

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
created: 2026-04-10
updated: 2026-04-10
aliases: []
confidence: medium
---
```

Guidance:
- `type`: `concept`, `playbook`, `system`, `component`, `decision`, or `glossary`
- `status`: usually `canonical`, `draft`, or `provisional`
- `source_type`: usually `derived`, `raw-note`, `web`, `internal-doc`, or `output`
- `sources`: list file paths or URLs when available
- `domain`: the domain folder this page lives in (e.g. `linux`, `python`, `style`)
- `confidence`: `high`, `medium`, or `low`

---

## Page Types

### concept
Used for atomic ideas — a tool, a command, a principle, a style rule, anything self-contained.

Recommended sections:
- Summary
- What it is
- Practical defaults
- Failure signs
- Checks
- Related pages

### playbook
Used for actionable workflows — how to do something step by step.

Recommended sections:
- Summary
- Goal
- Checklist
- Defaults
- Common pitfalls
- Related pages

### system
Used for end-to-end system documentation.

Recommended sections:
- Summary
- Goal
- Architecture
- Main flow
- Components
- Inputs / Outputs
- Failure modes
- Related decisions
- Open questions

### component
Used for modules inside systems.

Recommended sections:
- Summary
- Purpose
- Inputs
- Outputs
- Dependencies
- Rules / thresholds
- Failure cases
- Related pages

### decision
Used for architectural or policy choices.

Recommended sections:
- Summary
- Decision
- Context
- Alternatives considered
- Tradeoffs
- Consequences
- Related pages

### glossary
Used for short definitions when a full page is unnecessary.

---

## Naming And Linking Rules
- Use lowercase kebab-case filenames.
- Keep names short and explicit.
- Prefer one topic per page.
- Playbooks use the prefix `playbook-` in the filename (e.g. `playbook-fix-crlf.md`).
- Decisions use the prefix `decision-` in the filename (e.g. `decision-optimizer-choice.md`).
- Concepts need no prefix — the domain folder provides context.
- Systems should link to components.
- Components should link back to systems when relevant.
- Playbooks should link to the concepts they use.
- Decisions should link to the affected systems or components.
- Every domain folder must have an `_index.md`.

---

## Update Policy
When adding new information:
- search for an existing relevant page first
- update before creating
- merge duplicates when safe
- preserve practical defaults, pitfalls, checks, and reasoning
- keep implementation detail that will help future work

---

## Monthly Maintenance Standard
During health checks, look for:
- contradictions between pages
- orphan pages (not linked from any `_index.md`)
- duplicate pages
- weakly sourced claims
- stale decisions
- pages mentioned but not explained
- outputs that should be promoted into `wiki/`
- domain `_index.md` files that are out of date

---

## Quick Command Interpretation
- "add this to the kb" → capture in `raw/` or update `wiki/` using the decision rule above
- "save this source" → save to `raw/`
- "update the wiki" → compile from `raw/` into `wiki/`
- "answer from the kb" → read `wiki/` first and save to `outputs/answers/` when appropriate
- "promote this" → move stable knowledge from `outputs/` or `raw/` into `wiki/`

---

## Non-Negotiables
- Do not create duplicate wiki pages for the same topic.
- Do not overwrite raw source material with polished summaries.
- Do not hide ambiguity.
- Do not file in `daily/` to avoid a domain decision — if it belongs to a specific domain, file it there.
- Do not force topics into existing domains if they don't belong — create a new domain folder instead.
- Do not create a new domain folder for a single page that fits an existing domain.
- Every domain folder must have an `_index.md`. Update it when adding or removing pages.
- After every session with substantive content (technical or personal), run the passive capture evaluation.
