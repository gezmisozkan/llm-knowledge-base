# LLM Knowledge Base

A markdown-first second brain that grows through AI conversations. Every chat with an LLM agent becomes structured, linked, searchable knowledge — automatically.

## The idea

Most people learn things in conversation with LLMs and then lose them. The chat scrolls away and the insight is gone.

This repo solves that. It defines an **operating contract** ([CLAUDE.md](CLAUDE.md)) that turns your AI agent into an active librarian:

- It **captures** what you discuss — commands, concepts, decisions, even style preferences
- It **files** things into the right domain automatically using a routing table
- It **links** related pages so knowledge compounds over time
- It **proposes** what to save at the end of each session — you approve or skip

You talk. The knowledge base grows.

## How it works

```
You ←→ LLM Agent ←→ Knowledge Base
         │
         ├── raw/       ← captures sources, errors, pasted text faithfully
         ├── wiki/      ← curates durable knowledge by domain
         └── outputs/   ← stores generated answers and reports
```

The agent reads `CLAUDE.md` at the start of every session. That file defines:

1. **Domain routing** — a table mapping topics to folders (Linux stuff → `wiki/linux/`, fashion → `wiki/style/`)
2. **Passive capture rules** — a decision tree for when to write without being asked
3. **Session-end protocol** — batched capture proposal at the end of each conversation
4. **Filing rules** — update before create, link related pages, maintain indexes

## Folder structure

```
├── CLAUDE.md              ← the operating contract (the interesting part)
├── raw/                   ← unprocessed captures
│   ├── inbox/             ← quick unsorted captures
│   ├── web/               ← web pages and articles
│   ├── notes/             ← rough observations
│   ├── docs/              ← copied internal docs
│   └── screenshots/       ← images and visual refs
├── wiki/                  ← canonical knowledge by domain
│   ├── INDEX.md           ← domain map (entry point)
│   ├── linux/             ← bash, shell, WSL, coreutils
│   ├── python/            ← language, stdlib, packaging
│   ├── ml/                ← classical ML, sklearn
│   ├── dl/                ← PyTorch, training, architectures
│   ├── git/               ← workflows, branching, hooks
│   ├── tools/             ← editors, docker, env management
│   ├── style/             ← clothing, dress codes, color theory
│   └── daily/             ← cross-domain patterns
└── outputs/               ← generated answers, reports
    ├── answers/
    ├── briefings/
    ├── health-checks/
    └── reports/
```

Every domain is just a folder. Adding a new one (say `cooking/` or `finance/`) takes one `_index.md` file — no structural changes.

## What makes this different

**Domain-first, not type-first.** Pages are organized by topic (`linux/`, `style/`), not by type (`concepts/`, `playbooks/`). The type lives in frontmatter. This means "show me everything I know about Linux" is a single folder.

**Universal scope.** Technical and personal knowledge are equals. `wiki/style/smart-casual.md` and `wiki/dl/learning-rate.md` follow the same structure, same frontmatter, same linking rules.

**Agent-native.** The entire system is designed for an LLM agent to read and operate. `CLAUDE.md` is not documentation — it is executable instructions. The agent doesn't need you to say "save this." It evaluates every conversation against a capture decision tree and proposes what to keep.

**Obsidian-compatible.** Uses `[[wikilink]]` syntax, frontmatter, and folder structure that Obsidian renders as a navigable, linked graph.

## Getting started

1. Clone this repo
2. Open the folder in [Obsidian](https://obsidian.md/) for browsing
3. Open it in [Claude Code](https://claude.ai/claude-code) (or any agent that reads `CLAUDE.md`)
4. Start talking — the KB grows from there

Customize the domains in `CLAUDE.md` to match your own interests. The starting domains (linux, python, ml, dl, git, tools, style, daily) are a suggestion, not a requirement.

## The operating contract

The core of this system is [CLAUDE.md](CLAUDE.md). Read it. It defines:

- **Domain Routing Table** — where each topic goes
- **Passive Capture Rules** — when the agent writes without being asked
- **Session-End Capture Protocol** — how the agent proposes saves
- **Page Types** — concept, playbook, system, component, decision, glossary
- **Frontmatter Standard** — metadata every page carries
- **Non-Negotiables** — rules the agent must never break

If you change nothing else, customize the domain routing table to match your world.

## License

MIT — see [LICENSE](LICENSE).
