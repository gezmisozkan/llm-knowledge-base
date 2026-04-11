---
name: llm-knowledge-base
description: Maintain a universal markdown-first second brain covering all personal knowledge — technical (Linux, Python, ML, DL, Git, tools) and personal (style, daily lessons, etc). Use when working inside this repository to capture sources, update canonical notes, answer from the KB, and promote durable knowledge.
compatibility: Works with repo-aware coding agents that can read and write local files.
---

# LLM Knowledge Base Workflow

This repository is a universal second brain. All domains — technical or personal — are treated equally.

## First Steps
1. Read `CLAUDE.md` — the full operating contract.
2. Read `wiki/INDEX.md` — the domain map.
3. Check the relevant domain `_index.md` before creating anything new.

## Operating Rules
- Put rough or source-like material into `raw/` first.
- Put durable canonical knowledge into `wiki/` under the correct **domain folder**.
- Put generated answers and reports into `outputs/`.
- Prefer updating existing wiki pages over creating duplicates.
- Preserve uncertainty when the source is incomplete.
- After every substantive session, run the passive capture evaluation (see CLAUDE.md).

## Domain Folders
`wiki/` uses domain-first organization. Current domains:

| Domain | Scope |
|---|---|
| `linux/` | bash, shell, WSL, coreutils, text processing |
| `python/` | language, stdlib, packaging, testing |
| `ml/` | classical ML, sklearn, features, metrics |
| `dl/` | PyTorch, training, optimizers, architectures |
| `git/` | workflows, branching, config, hooks |
| `tools/` | editors, docker, cloud drives, env management |
| `style/` | clothing, dress codes, color theory, outfit combinations |
| `daily/` | cross-domain patterns and lessons |

To add a new domain: create the folder with an `_index.md` — no other structural changes needed.

## Typical Commands
- Add source: save it to `raw/web/`, `raw/docs/`, `raw/notes/`, or `raw/inbox/`
- Add knowledge: find the right domain folder, update the best existing page or create a new one
- Answer a question: read `wiki/` first, then save the result to `outputs/answers/` if appropriate
- Promote stable knowledge: move durable parts from `raw/` or `outputs/` into `wiki/`
- After adding a page: update the domain `_index.md` and `wiki/INDEX.md` Recent additions
