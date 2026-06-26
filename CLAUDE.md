# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MD Viewer is a **zero-dependency, single-file HTML app** hosted on GitHub Pages. Everything — HTML structure, CSS, and JavaScript — lives in `index.html`. There is no build step, no package manager, no bundler.

**Live URL**: https://nvalettepro-sudo.github.io/markdown_viewer/

## Development

Open `index.html` directly in a browser, or serve it locally:

```bash
python3 -m http.server 8080
```

No install, no build. Changes to `index.html` are immediately testable by refreshing the browser.

## Architecture

The app is a split-pane Markdown editor with a live preview. All logic is in a single `<script>` block at the bottom of `index.html`.

**Key sections (marked with `══` comments in source):**

| Section | Responsibility |
|---|---|
| CSS variables / `[data-theme]` | Dark/light theme via CSS custom properties |
| `parseFrontmatter` / `frontmatterToHTML` | Parses YAML-like frontmatter (`---` block) and renders it as a metadata table |
| `render()` | Debounced (150ms) Markdown → HTML via marked.js + highlight.js |
| `convertPDF()` | Two-pass PDF text extraction via PDF.js: calibrate font sizes → infer heading levels → emit Markdown |
| `fetchURL()` | CORS proxy cascade (corsproxy.io → allorigins.win × 2) with 12s timeout per proxy |
| `htmlToMarkdown()` | DOM-based HTML-to-Markdown converter: strips nav/footer/ads, finds `<main>`/`<article>`, converts nodes recursively |
| `exportHTML()` | Generates a self-contained standalone HTML file with inlined CSS |
| Divider resize | Drag-to-resize the editor/preview split via `mousedown`/`mousemove`/`mouseup` |

**External CDN dependencies** (no local copies — all loaded from cdnjs.cloudflare.com):
- `marked` 9.1.6 — Markdown parsing
- `highlight.js` 11.9.0 — Syntax highlighting
- `pdf.js` 3.11.174 — PDF text extraction (with web worker)
- Google Fonts — JetBrains Mono + Crimson Pro

## Constraints

- **No frameworks, no npm** — keep it a single deployable HTML file.
- **CORS limitation**: URL import relies on public proxies; it will fail for sites that block them. The proxy cascade is the intended workaround.
- **PDF heuristics**: Heading detection in `convertPDF()` is font-size based (median × multipliers). It's approximate by design.
- **GitHub Pages deployment**: push to `main` — Pages serves `index.html` at the repo root automatically.
