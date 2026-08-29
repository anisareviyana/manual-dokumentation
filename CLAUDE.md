# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Repository Overview

This is a **documentation-only repository** owned by Anisa Reviyana. It contains a collection of standalone HTML files that serve as product/feature manuals written in Bahasa Indonesia. There is no build system, no test suite, no linter, and no package manager — every file is a self-contained HTML document openable directly in a browser.

GitHub remote: `https://github.com/anisareviyana/manual-dokumentation.git`

## Existing Special-Purpose Files

These files already exist and have a specific purpose — **do not overwrite or repurpose them**:

- **`claude.md`** (lowercase) — a custom **persona/role definition** instructing the agent to act as a "Report Architect & Designer" for producing professional reports. This is a prompt-config file, not a Claude Code guidance file. Keep it intact.
- **`agent.md`** — memory/instructions for AI agents (auto-commit and push to GitHub on each HTML change, project conventions). Keep it intact.
- **`index.html`** — landing page that links/frames the documentation collection.

When future Claude instances operate here, they should respect the role defined in `claude.md` and the workflow conventions in `agent.md`.

## Content Layout

Documentation files sit at the repository root, one per feature/topic. Current set:

- `index.html` — landing page
- `manual-flightpayment-document.html` — Manual Book Fitur Flight Payment ALVIS
- `manual-TL-agreement-document.html` — Manual Tour Leader Agreement
- `dokumentasi_tour_leader_agreement.html` — companion/extended TL Agreement docs
- `manual-notification-document.html` and `manual-notification-document-v2.html` — notification feature manual (v2 supersedes v1)
- `dokumentasi-promo-notifikasi.html` — promo notification documentation
- `push-notification-report.html` and `push-notification-report-management.html` — push notification reports

When adding a new manual, drop a new HTML file at the root and update `index.html` if it should appear in the catalog.

## Code Style & Conventions

Documents are **standalone HTML** — no shared CSS/JS files, no templates. Each file is fully self-contained.

- **Language**: `lang="id"` — body content is in Bahasa Indonesia.
- **Typography**: most manuals load **Poppins** from Google Fonts and **Font Awesome** via CDN. Match this when adding new manuals so the look stays consistent.
- **Layout pattern**: the larger manuals (e.g. `manual-flightpayment-document.html`) use a **sidebar + header + content** layout with CSS custom properties for theming at `:root`. Reuse this pattern rather than inventing a new one.
- **Color tokens**: see `--primary`, `--bg`, `--card-bg`, etc. in `manual-flightpayment-document.html` lines ~8–18 as the reference palette. New manuals should expose a similar token set so styling is centralized.
- **Inline CSS in `<style>` blocks** — no external stylesheets. Keep new code in the same spirit: one file, fully self-contained.
- **No JavaScript frameworks** — content is static. If interactivity is needed, use a small inline `<script>` at the bottom of the file.

## Common Commands

There is no build step. The useful workflows are:

- **Preview a document locally** — open the HTML file directly in a browser, or serve the folder:
  ```
  python -m http.server 8000
  ```
  then visit `http://localhost:8000/<file>.html`.
- **Commit changes** — per `agent.md`, HTML changes should be committed and pushed automatically:
  ```
  git add <file>.html
  git commit -m "short description"
  git push
  ```
- **Check status / history** — `git status`, `git log --oneline` (commit messages so far are short Indonesian/English descriptions of the doc edited).

## Adding or Editing Documentation

1. Read the existing manual that covers the same feature (if any) to match tone, palette, and section structure.
2. Keep the file standalone — no shared assets, no external CSS.
3. Match the Bahasa Indonesia voice used elsewhere; preserve heading hierarchy and section numbering style.
4. After editing, commit and push so the GitHub-hosted version stays in sync (per `agent.md`).
5. If a v2 supersedes a v1, leave the older file in place — the project keeps historical versions side by side.

## Things to Avoid

- Do not rename `claude.md` to `CLAUDE.md` or move its contents — that file is a persona definition, not Claude Code guidance.
- Do not introduce a build system, bundler, or package manager unless the user asks — the repo is intentionally plain HTML.
- Do not delete older version files (e.g. `manual-notification-document.html`) when a v2 exists — historical versions are kept.
- Do not add external CSS/JS dependencies beyond Google Fonts and Font Awesome CDN that existing files already use, unless the user requests it.
