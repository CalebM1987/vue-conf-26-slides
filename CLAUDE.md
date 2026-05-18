# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A [Slidev](https://sli.dev) presentation for **VueConf 2026**. Slidev is a Markdown-driven, Vite + Vue based slidedeck tool — slides live in `slides.md`, separated by `---`, with per-slide frontmatter and HTML-comment presenter notes.

## Current state

The project is **not yet scaffolded**. Only the Slidev agent skill is installed (see `skills-lock.json` and `.agents/skills/slidev/`). There is no `package.json`, `slides.md`, or `node_modules` yet. The first task in this repo is almost certainly bootstrapping the Slidev project itself.

To scaffold, prefer initializing in-place rather than running `pnpm create slidev` (which creates a subdirectory). Create `package.json` with `@slidev/cli` + the desired theme, plus the standard scripts (`dev`, `build`, `export`), then a starter `slides.md`.

## Working with Slidev — use the bundled skill

The `.agents/skills/slidev/` directory is a comprehensive, pre-installed reference for Slidev. **Consult it before searching the web or guessing syntax.**

- `.agents/skills/slidev/SKILL.md` — index of every feature with a one-line usage hint and a pointer to the detailed reference
- `.agents/skills/slidev/references/*.md` — ~50 focused reference docs (one per feature: `code-magic-move.md`, `core-animations.md`, `layout-slots.md`, etc.)

Workflow: scan `SKILL.md` for the feature, then read the matching `references/<topic>.md` file for the full syntax and gotchas.

## Common commands (once scaffolded)

```bash
pnpm install
pnpm run dev          # dev server at http://localhost:3030
pnpm run build        # static SPA in dist/
pnpm run export       # PDF export (requires `pnpm add -D playwright-chromium`)
```

## Browser collaboration via playwright-skill

`.claude/skills/playwright-skill/` is a ported skill for driving the Slidev dev server in a real Chromium window. Use it to navigate slides, click through animations, screenshot a layout, or capture console errors while iterating. See its `SKILL.md` for the agent-facing instructions.

Quick start (with the Slidev dev server running on :3030):

```bash
.claude/skills/playwright-skill/bin/open --headed
playwright-cli -s=presentation goto http://localhost:3030/
playwright-cli -s=presentation screenshot
.claude/skills/playwright-skill/bin/close   # when done
```

Project config: `.claude/skills/playwright-skill/skill/worktrees.json` (the `presentation` worktree maps to `http://localhost:3030`). No auth is required — Slidev runs as an open local server.

## Notes for editing slides

- First frontmatter block in `slides.md` is the **headmatter** (deck-wide config: theme, title, fonts, drawings, seoMeta, etc.). Subsequent frontmatter blocks configure individual slides.
- `---` separates slides; HTML comments inside a slide are presenter notes.
- Layouts (`layout: two-cols`, `cover`, `center`, `section`, `image-right`, `iframe`, `quote`, …) are set per-slide via frontmatter; multi-slot layouts use `::right::` / `::default::` markers.
- For animated reveals use `v-click` / `<v-clicks>`; for code transitions use `````md magic-move` blocks; for type-aware code samples use `` ```ts twoslash ``.
