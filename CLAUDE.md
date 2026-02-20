# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML recruitment pages for **AMS Corporation's AI Task Force (AI TF 1기)** — 2026 internal recruitment campaign. All content is in Korean.

No build system, no package manager, no dependencies. Each file is a self-contained single HTML file with inline CSS and JavaScript.

## File Variants

The files represent different design iterations of the same content:

| File | Style | Notes |
|------|-------|-------|
| `ams_ai_tf.html` | Full-page scrolling, desktop | Original version with nav, sections, email form |
| `ams_ai_tf_v2.html` | Full-page scrolling, desktop | V2 refinement |
| `ams_ai_tf_terminal.html` | Terminal/CRT aesthetic | Scanline overlay, typewriter animations, full-height app shell |
| `ams_tf_v3_mobile.html` | Mobile-first terminal | Command-based navigation (`H['cmd']` JS handlers), menu overlay |

## Architecture Patterns

**CSS custom properties** define the entire color system at `:root`. All files use a dark theme with IBM Plex Mono (monospace) and Noto Sans KR (Korean sans-serif) from Google Fonts.

**Terminal-style files** (`_terminal`, `v3`) use a full-viewport app shell (`height:100vh; overflow:hidden`) with a scrollable `#main` content area. Navigation is JS-driven via command handlers rather than anchor links.

**v3 command system**: Content is rendered by calling `H['command-name']()` functions that write HTML via `pOut()`. The menu overlay appears above a fixed bottom input bar, positioned dynamically by JS.

**Desktop scroll files** (`ams_ai_tf.html`, `v2`) use conventional section-based layout with a fixed nav, fade-in scroll animations, and an email `<form>` or mailto link for applications.

## Content Sections (consistent across variants)

1. Hero / intro
2. What is the TF (`about`)
3. Why join (`why`)
4. Benefits — AI tool budget (월 최대 10만원), learning budget (최대 20만원), HR review reflection
5. Department breakdown (`depts`) — per-team AI use cases
6. Recruitment schedule (`schedule`)
7. How to apply (`apply`) — email to `joonsung.lee@amslighting.co.kr`
8. FAQ

## Development

Open any `.html` file directly in a browser — no server required.

To preview on mobile: use browser DevTools device emulation, or serve locally with any static server:
```
npx serve .
# or
python -m http.server 8080
```
