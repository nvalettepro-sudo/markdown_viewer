# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Users

Primary user (confirmed): the owner, for personal and professional use. They convert and clean up documents (PDFs, web pages, HTML files, scanned images) into Markdown for their own work. Other audiences (colleagues, a public community) were not confirmed as targets; the app is nevertheless hosted publicly on GitHub Pages.

## Product Purpose

MD Viewer turns messy sources into clean, structured Markdown. Conversion is the main job (confirmed); the editor and live preview exist to check and correct the result, not as the headline feature. Success means a source (PDF, URL, HTML file, image via OCR) ends up as Markdown whose structure is right: headings, tables, a table of contents, with no silent loss of content.

## Positioning

Undecided; not discussed. Repository evidence only: one self-contained HTML file with no install, no account, and no build, that handles PDF, web page, HTML file and image (OCR) import in one place.

## Operating Context

- Import paths: `.md/.txt` file, PDF (text extraction, OCR fallback for scanned PDFs), URL (through public CORS proxies), local `.html` file, image (OCR, French and English).
- Typical source: web pages and documents whose structure is lost on import (tables, heading levels). Pages that block automated access (anti-bot protection) can only be imported by saving the HTML locally, via PDF, or by copy-paste.
- Post-import structuring: Auto-titres (heading detection with a preview to validate or correct levels before applying) and a dynamic table of contents (`<!-- TOC -->` marker, always rebuilt from the real headings).
- Output: `.md` file or standalone `.html` export.

## Capabilities and Constraints

Confirmed by the user:
- The interface is in French.
- The visible version number and date in the status bar are updated with every change.
- The app must be usable across different browsers and on iPhone and iPad. Not yet verified: the current layout is a desktop split-pane editor/preview.

Documented in the repository (CLAUDE.md):
- A single `index.html`, with no framework, no npm and no build; deployed from `main` on GitHub Pages.
- Libraries load from CDNs (marked, highlight.js, PDF.js, Tesseract.js, Google Fonts).
- URL import depends on public CORS proxies and fails on sites that block them.
- PDF heading detection is heuristic (font-size based) and approximate by design.

## Brand Commitments

Name: MD Viewer (header wordmark "MD.VIEWER"). Voice: French, direct, instructive. Error messages explain the cause, then list alternatives ranked from most to least complete, with the limits of each (the owner asked for this explicitly).

## Evidence on Hand

No testimonials, usage data, customer evidence or screenshots are on file. Do not fabricate any. Sample documents used while building features were supplied in conversation and are not stored in the repository.

## Product Principles

1. **Conversion first.** Any change is judged by whether it improves the Markdown produced from a messy source; the editor serves that goal.
2. **Never fail silently.** When a conversion is incomplete or an import is blocked, say so, say why, and offer the alternatives with their limits.
3. **Propose, then apply.** Automatic restructuring (Auto-titres) shows what it will do and lets the user correct it first; everything applied stays undoable with Ctrl+Z.
4. **Always in sync.** Derived content, such as the table of contents, reflects the document's real state however it was changed.
5. **Everything in one file.** Features must fit the zero-dependency single-file constraint.

## Accessibility & Inclusion

No product-specific accessibility requirement was established. The confirmed cross-device requirement (different browsers, iPhone, iPad) is recorded under Capabilities and Constraints.
