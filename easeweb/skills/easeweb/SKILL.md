---
name: easeweb
description: >-
  Use this skill whenever the user wants to create, edit, translate, review,
  preview, export, or organize interactive web presentations or courses on
  EaseWeb (easeweb.host), including decks with interactive slide-link buttons,
  tables, images, or runnable SQL, Python, Bash, MongoDB, Redis, and ClickHouse
  code blocks.
---

# EaseWeb Presentations Workflow

EaseWeb (`https://easeweb.host`) is a web presentation and interactive course
platform connected via the `easeweb` MCP server (`https://easeweb.host/mcp/`).

## Before Making Changes

1. **Inspect existing context first**:
   - Call `list_presentations` and `list_projects` when working on an existing
     deck or course so you know the exact slugs, themes, and project structure.
   - Call `get_format` if you need the exact list of block types, themes, fonts,
     or prop limits before building a complex deck.
   - Call `read_presentation` for a fast text-only overview of a deck; use
     `get_slides` when you need exact coordinates and block IDs to edit.

2. **Respect authentication and permissions**:
   - Every change is recorded in the presentation's revision history
     (`list_history` / `restore_version`).
   - If a presentation is private or read-only, use `request_access` instead of
     retrying failed writes.

## Building High-Quality Decks

1. **Build the full deck in one call when possible**:
   - Use `create_presentation` with all slides and objects defined cleanly on
     the `1280x720` canvas.
   - Pick a cohesive theme (`light`, `dark`, `paper`, `midnight`, `forest`,
     `sunset`) so defaults match automatically.
   - Use `table` blocks for structured comparisons, `code` blocks with
     `runnable: true` for interactive SQL / Python / Bash / MongoDB / Redis /
     ClickHouse examples, and `button` blocks with `link: {"kind": "slide", "slide_number": N}`
     for interactive agendas and branching flows.

2. **Keep layout clean and legible**:
   - Leave generous margins (`x >= 60`, `y >= 48`, width `<= 1160`) and avoid
     overlapping text blocks.
   - Keep each slide focused on one clear idea; put detailed talking points in
     speaker `notes`.

3. **Include translations when appropriate**:
   - Set `lang` (`"ru"` or `"en"`) to match the primary text language.
   - Populate `title_tr`, `name_tr`, and block `props.tr` for the other site
     language whenever the user wants a bilingual presentation; check
     `missing_translations` in tool responses.

## Verification

1. **Check runnable code**:
   - Whenever a presentation contains runnable code blocks and `database` setup
     scripts, call `check_code` to verify that every runnable block executes
     cleanly and matches its expected output.
2. **Visual inspection**:
   - Call `preview_slides` on newly created or heavily edited slides to inspect
     the rendered output and fix any text overflow, overlap, or contrast issues.
3. **Share the result**:
   - Always return the clickable presentation URL (`https://easeweb.host/movie/<slug>/`)
     and summarize what was created or changed.
