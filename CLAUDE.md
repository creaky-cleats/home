# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static microsite for the **Creaky Cleats** slowpitch softball team — a public home and knowledge base for newer team members. Plain hand-written HTML/CSS, **no build step, no framework, no dependencies** (no `package.json`, Makefile, or CI).

## Commands

- **Preview locally:** `python3 -m http.server 8000` then open `http://localhost:8000` (or just open `index.html` directly).
- **Deploy:** push to `main`. GitHub Pages serves the repo root (source: `main` / `/`). No build runs server-side (`.nojekyll` skips Jekyll).
- **Verify live:** `curl -s -o /dev/null -w "%{http_code}\n" https://creaky-cleats.github.io/home/<page>.html`

There are no tests, linters, or build tooling.

## Architecture

Four sibling HTML pages (`index`, `schedule`, `roster`, `handbook`) sharing `style.css`. The structure that spans files:

- **No templating — the header/nav and the inline SVG favicon `<link>` are duplicated verbatim in every page.** Changing the nav (e.g. adding a page) means editing the `<nav>` block in *all four* HTML files plus adding the link. There is no include mechanism; keep these blocks identical by hand.
- **All asset/link paths must be relative** (`style.css`, `roster.html`, `POSITIONS.png`) — never root-absolute (`/style.css`). The repo is `creaky-cleats/home`, not `creaky-cleats.github.io`, so the site is served under the base path **`/home/`**; absolute paths break in production. This is the single easiest way to break the live site.
- **Theming** lives in CSS custom properties under `:root` in `style.css` (`--field`, `--clay`, `--cream`, etc.); component styles reference these tokens. Restyle there, not in per-element rules.
- `POSITIONS.png` is a content asset embedded by `handbook.html` (the 10-position fielding diagram), not a generated/screenshot file — keep it.

## Content state

- `schedule.html` is a **scaffold**: 11 Sunday dates (Jun 21–Aug 30) with `TBD` times/opponents/fields, pending the real schedule. The games are **not** on the connected `jon@n3rd-media.com` Google Calendar — confirm the correct account/calendar before attempting to auto-populate.
- `handbook.html` contains intentional placeholder sections (marked with `.note` callouts) for the team to fill in. The roster in `roster.html` is real.
