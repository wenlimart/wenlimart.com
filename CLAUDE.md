# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A static HTML website hosted on GitHub Pages at wenlimart.com. It is an open catalog of AI-generated media samples ("Try this first.") — showing prompts, model settings, and results across different generation types (text→video, text→audio, text→image, etc.).

No build system, no package manager, no framework. Pure HTML + CSS + vanilla JS.

## Site structure

Each page follows an identical layout pattern: `header → hero/content → nav → gallery → footer`. The nav links to these pages (several are planned but not yet created):

- `index.html` — text → video (exists)
- `text-audio.html` — text → audio (stub)
- `text-image.html` — text → image (stub)
- `image-video.html` — image → video (stub)
- `video-video.html` — video → video (stub)
- `outtakes.html` — outtakes (stub)
- `from-you.html` — community submissions (stub)
- `contact.html` — contact page (exists)

## Design system

All styles are inlined per-page (no shared stylesheet). When creating new pages, copy the CSS variables and base styles from an existing page:

- **Fonts**: `DM Mono` (monospace, for UI chrome) and `Noto Sans JP` (body text), both loaded from Google Fonts
- **Color tokens**: `--bg`, `--fg`, `--accent`, `--muted`, `--muted2`, `--border`, `--tag-bg`, `--card-bg`, `--prompt-bg`
- **Animation**: Cards and hero sections use `fadeUp` keyframe (`opacity: 0 → 1`, `translateY(10px → 0)`)
- **Responsive**: Single breakpoint at `max-width: 600px` adjusting padding

## Card anatomy

Each gallery card contains three zones:
1. `.card-video` — 16:9 video embed or placeholder text
2. `.card-prompt-wrap` — the generation prompt, truncated to 3 lines with expand toggle
3. `.card-details-wrap` — model/settings metadata, truncated to 1 line with expand toggle

The JS `toggleEl(btn, id)` function handles expand/collapse. On DOMContentLoaded, buttons are hidden if content doesn't overflow.

## Gallery sections

Each `.section-block` has a `.section-title` row that can show either a descriptive label (`.section-title-text`) or just a date (`.section-date`), flanked by horizontal rules (`.section-title-line`).

## Deployment

Pushing to `main` on GitHub auto-deploys via GitHub Pages. The `CNAME` file sets the custom domain to `wenlimart.com`.
