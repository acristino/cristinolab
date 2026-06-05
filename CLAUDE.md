# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Static multi-page website for the Cristino Lab (Neurogenomics and Systems Biology Laboratory, Institute for Biomedicine and Glycomics, Griffith University). Styles live in `assets/css/style.css`. No build system, no bundler, no dependencies.

Deployment: pushes to `main` auto-deploy to Cloudflare Pages.

## Previewing

Open any HTML file directly in a browser. No server needed — it's fully static.

```bash
# or serve locally for accurate font loading
python3 -m http.server 8080
```

## Architecture

The site is organised as separate HTML pages, each importing `assets/css/style.css`:

| File | Description |
|---|---|
| `index.html` | Home — hero, image gallery, lab overview teaser |
| `about.html` | PI profile, biography, grants & funding |
| `research.html` | Research areas grouped as Basic and Medical |
| `team.html` | Current members with photos, alumni supervision list |
| `publications.html` | All 49 publications with syntheses and word cloud |
| `collaborations.html` | IBG/Griffith, Australian, international partners |
| `resources.html` | Resources placeholder (coming soon) |
| `tools.html` | Bioinformatics tools placeholder (coming soon) |
| `contact.html` | Contact details and opportunities |

## Design system (CSS custom properties)

All colours are defined as variables at `:root` in `assets/css/style.css`. The palette is light/white with blue accents:

- `--accent` / `--accent-dim`: primary blue (`#1460c8`)
- `--teal` / `--teal-dim`: secondary green (`#0a7a60`)
- `--text`, `--text-secondary`, `--text-muted`: text hierarchy
- `--border`, `--border-subtle`: dividers and card outlines

Typography uses three Google Fonts families:
- `--serif` (DM Serif Display): headings
- `--sans` (DM Sans): body copy and team card names
- `--mono` (DM Mono): labels, section tags, navigation links, metadata

## Adding content

**New team member (current)** — add a `.team-card` div in the relevant group in `team.html`. Place photo in `assets/img/` and replace the `[ Photo ]` placeholder with `<img src="assets/img/FILENAME" alt="Name">`.

**New publication** — prepend a `.pub-item` div in `publications.html`. Follow the existing pattern: `.pub-year` + `.pub-content` with `.authors`, `.journal` link, and `.pub-synthesis` paragraph.

**New research area** — add a `.research-card` to the appropriate `.research-grid` in `research.html`.

**New collaborator** — add a `.collab-card` div to the relevant section in `collaborations.html`.

**New grant** — prepend a `.grant-item` div in the grants section of `about.html`.

## Nav active state

Each page sets `class="active"` on its own nav link. Update this when copying the nav block to a new page.

## Assets

- `assets/css/style.css` — shared stylesheet (edit here, not inline)
- `assets/img/` — all photos and images
- `assets/js/` — scripts (future; contact form submission, etc.)
