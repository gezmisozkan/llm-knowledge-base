# Starter Prompts for Your Knowledge Base

## 1. Scrape a Web Source

To add a web article or page:

> Scrape [URL] into `raw/web/`. Extract the main content and save it as a markdown file with a descriptive filename. Preserve important headings, lists, tables, and code snippets where possible. Do not summarize yet.

## 2. Compile Or Update The Wiki

After adding sources to `raw/`, run:

> Read everything in `raw/`. Then compile or update the wiki in `wiki/` following the rules in `CLAUDE.md`. Create or update `wiki/INDEX.md` first, then update existing topic pages when possible, and create new pages only when needed. Link related topics. Summarize durable knowledge, not just source text.

## 3. Ask Questions Against The KB

Once `wiki/` has useful coverage, try prompts like:

> Based on everything in `wiki/`, what are the three biggest gaps in my understanding of [topic]?

> Compare what source A says about [concept] vs what source B says. Where do they disagree?

> Write me a 500-word briefing on [topic] using only this knowledge base.

Save generated answers to `outputs/` or promote durable parts into `wiki/`.

## 4. Add New Knowledge Quickly

Use this when you paste notes, lessons, or copied material:

> Inspect the existing knowledge base and decide whether this belongs in `raw/`, `wiki/`, or `outputs/`. Update an existing wiki page if one already fits. Otherwise create the smallest correct new file. If the material is incomplete, save it in `raw/` first and note likely promotion targets.

## 5. Monthly Health Check

Run this periodically:

> Review the entire `wiki/` directory. Flag contradictions, duplicate pages, orphan pages, claims not backed by `raw/`, and topics mentioned but never explained. Suggest missing pages that would improve coverage and identify outputs that should be promoted into `wiki/`.
