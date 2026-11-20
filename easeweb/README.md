# EaseWeb Plugin for Google Antigravity

Connect your Antigravity agent directly to **[EaseWeb](https://easeweb.host)** — an interactive web presentation and course platform.

## What You Can Do

- **Create complete presentations in one step** from notes, outlines, or lesson plans on a `1280×720` canvas with text, shapes, tables, images, and branching navigation buttons.
- **Embed live runnable code** in slides — PostgreSQL, MongoDB, Redis, ClickHouse, Python (with `numpy`, `pandas`, `matplotlib`), and Bash — and automatically verify every code block with `check_code`.
- **Edit and visually review decks** — update individual blocks, reorder slides, inspect rendered slide previews (`preview_slides`), and leave structured review notes that authors see right in the viewer.
- **Organize courses into projects** with cross-presentation links and shared access controls.
- **Safe collaboration** — OAuth 2.1 authentication (read-only or read-and-write), full revision history with one-click restore, and zero silent data loss.

## Installation

### From GitHub (via Antigravity CLI)

```bash
agy plugin install https://github.com/svyatoslavoh/gospel
```

### Local Validation & Testing

```bash
agy plugin validate --strict ./plugins/easeweb
agy plugin install ./plugins/easeweb
```

## Authentication

When you first use an EaseWeb tool, Antigravity connects to `https://easeweb.host/mcp/` using **OAuth 2.1** (PKCE + Dynamic Client Registration / Client ID Metadata Document). Sign in with Google, Apple, or Yandex (free) and choose either **Read only** or **Read and write** access. You can revoke access at any time at `https://easeweb.host/agents/`.

## Links

- Website: https://easeweb.host
- MCP Documentation: https://easeweb.host/docs/mcp/
- Privacy Policy: https://easeweb.host/privacy/
- Terms of Service: https://easeweb.host/terms/
