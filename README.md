# Dual Knowledge Base Template

A markdown-first knowledge base template with two independent scopes:

- `daily-kb/` for personal and reusable knowledge
- `repo-kb/` for knowledge about the current repository

This split is intentional. A copied version of this template should work both as a daily second brain and as a repo documentation system without mixing the two.

## Why two KBs?

Many KB setups become messy because one folder tree tries to serve two jobs at once:

- long-lived personal knowledge
- repository-specific exploration and documentation

This template separates them completely. Each scope has its own:

- `CLAUDE.md`
- `raw/`
- `wiki/`
- `outputs/`
- indexes and filing rules

The root `CLAUDE.md` is only a router.

## Folder structure

```text
.
├── CLAUDE.md
├── daily-kb/
│   ├── CLAUDE.md
│   ├── raw/
│   ├── wiki/
│   └── outputs/
├── repo-kb/
│   ├── CLAUDE.md
│   ├── raw/
│   ├── wiki/
│   └── outputs/
└── starter-prompts.md
```

## How routing works

- Use `repo-kb/` for codebase exploration, architecture notes, setup, debugging, workflows, and decisions.
- Use `daily-kb/` for reusable concepts, personal preferences, stable playbooks, and lessons that outlive one repo.
- If repo-specific work produces a general lesson, keep the detailed version in `repo-kb/` and promote the reusable abstraction into `daily-kb/`.

## `daily-kb/`

`daily-kb/` is a universal second brain. It uses a domain-first wiki with folders such as `linux/`, `python/`, `git/`, `tools/`, `style/`, and `daily/`.

Use it for:

- technical concepts that apply across projects
- personal rules and preferences
- reusable workflows and checklists
- cross-domain lessons

## `repo-kb/`

`repo-kb/` is a repo documentation system. It uses a project-first wiki with folders such as `architecture/`, `components/`, `workflows/`, `decisions/`, `debugging/`, and `setup/`.

Use it for:

- codebase structure and architecture
- component behavior and interfaces
- setup steps and environment notes
- debugging patterns and incidents
- repository-specific decisions and workflows

## Getting started

1. Open the repo in your agent.
2. The agent reads root `CLAUDE.md` first.
3. The agent routes into `daily-kb/` or `repo-kb/`.
4. Work inside the chosen scope only.

If you copy this template into another repository, `repo-kb/` becomes that repository's KB, while `daily-kb/` remains your broader reusable knowledge store.

## License

MIT - see `LICENSE`.
