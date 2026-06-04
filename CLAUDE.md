# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static homepage for the Cristino Lab (Neurogenomics and Systems Biology Laboratory, GRIDD, Griffith University). The entire site lives in a single `index.html` with all CSS inlined in a `<style>` block — no build system, no bundler, no dependencies.

Deployment: pushes to `main` auto-deploy to GoDaddy via GitHub Actions.

## Previewing

Open `index.html` directly in a browser. No server needed — it's fully static.

```bash
# Linux
xdg-open index.html

# or serve locally for accurate font loading
python3 -m http.server 8080
```

## Architecture

All markup, styles, and (future) scripts live in `index.html`. The page is organized into sequential `<section id="...">` blocks:

| Section | ID | Description |
|---|---|---|
| Hero | `#hero` | Full-viewport intro with logo, heading, CTAs |
| Stats bar | — | Key lab metrics (not a `<section>`) |
| About | `#about` | Two-column: text + institute card |
| Research | `#research` | 6-card grid of research areas |
| Team | `#team` | Card grid; placeholder photos until real ones arrive |
| Publications | `#publications` | Chronological list with year, authors, journal |
| News | `#news` | Card grid with date, tag, title, excerpt |
| Contact | `#contact` | Two-column: details + static form (no backend yet) |

## Design system (CSS custom properties)

All colours are defined as variables at `:root`. The palette is light/white with blue accents:

- `--accent` / `--accent-dim`: primary blue (`#1460c8`)
- `--teal` / `--teal-dim`: secondary green (`#0a7a60`)
- `--text`, `--text-secondary`, `--text-muted`: text hierarchy
- `--border`, `--border-subtle`: dividers and card outlines

Typography uses three Google Fonts families applied consistently:
- `--serif` (DM Serif Display): all `h1`/`h2`/`h3` headings
- `--sans` (DM Sans): body copy and team card names
- `--mono` (DM Mono): labels, section tags, navigation links, stats, metadata

## Adding content

**New team member** — duplicate a `.team-card` div in `#team`. The `.team-photo` div should be replaced with an `<img>` once a photo is available; the comment in the CSS explains this.

**New publication** — prepend a `.pub-item` div in `#publications`. Follow the existing pattern: `.pub-year` + `.pub-content` with `.authors` and `.journal` link.

**New news item** — prepend a `.news-card` div in `#news`. Use one of the existing tag styles (Grant, Publication, Position).

**New research area** — add a `.research-card` to `.research-grid` in `#research`. The grid is `auto-fit minmax(280px, 1fr)` so it reflows automatically.

## Planned but not yet created

- `assets/css/` — future external stylesheet
- `assets/js/` — future scripts (contact form submission, etc.)
- The contact form `<button>` has no `action` or JS handler yet
