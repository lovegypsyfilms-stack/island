# Handoff: ISLAND — Documentary Feature Site

## Overview
A single-page, cinematic marketing site for **ISLAND** (Love Gypsy Films) — a documentary feature about two friends living homeless in the Hawaiian wilds, shot over eleven years. The site is a dark, full-bleed, scroll-driven page: hero (key art) → logline chapter → the story (synopsis + portrait) → contact/press footer.

## About the Design Files
The files in this bundle are **design references created in HTML** — prototypes showing intended look and behavior, not production code to copy directly. The task is to **recreate this design in the target codebase's existing environment** (React, Vue, plain HTML/CSS, etc.) using its established patterns and libraries. If no environment exists yet, a static site (plain HTML/CSS/JS, or Astro/Next static export) is the most appropriate choice — this is a single marketing page with no backend requirements.

`ISLAND.dc.html` is authored in a proprietary component format; read the markup inside `<x-dc>` for the exact structure and inline styles, and the `class Component` script for behavior (scroll reveals, data). `image-slot.js` is a prototype-only placeholder widget — in production, replace each `<image-slot>` with a real `<img>`/`background-image` supplied by the filmmaker.

## Fidelity
**High-fidelity.** Colors, typography, spacing, and copy are final unless noted. Recreate pixel-perfectly. The only placeholders are: the "Watch the trailer" link target (no URL yet) and the story portrait image (drag-and-drop slot in the prototype).

## Screens / Views

### 1. Fixed Nav
- Fixed to top, full-width, z-index above all content; padding 26px 48px; background `linear-gradient(to bottom, rgba(10,9,8,.85), rgba(10,9,8,0))`.
- Left: "LOVE GYPSY FILMS" — Archivo 700, 13px, letter-spacing .4em, color #e8e2d8, links to top.
- Right: links "THE STORY" and "CONTACT" — Archivo 600, 11px, letter-spacing .28em, color rgba(232,226,216,.75), hover #eab97e; flex row, gap 36px.

### 2. Hero (100vh, min 640px)
- Background: the full key-art poster (`assets/poster.png`), `background: #0a0908 url(...) center 38% / contain no-repeat`. The whole poster must fit on screen (contain, not cover) — the title/tagline are baked into the artwork, so there is NO HTML title.
- Entrance: slow settle animation on the poster layer — `scale(1.06) → scale(1)` over 6s ease-out, once.
- Overlay gradient: `linear-gradient(to bottom, rgba(10,9,8,.35) 0%, transparent 35%–55%, rgba(10,9,8,.92) 92%, #0a0908 100%)`.
- Bottom-center (bottom: 7vh): outlined button "▶  WATCH THE TRAILER" — Archivo 600, 11px, letter-spacing .3em, color #e8e2d8, 1px border rgba(232,226,216,.35), padding 15px 34px, square corners. Hover: border #d89a5c, background rgba(216,154,92,.08), text #eab97e, .3s transition. **Href is a placeholder — trailer URL to be supplied.**
- Scroll cue: 1px × 44px vertical gradient line, bottom-center, gentle bob loop (translateY 0→8px, opacity .7→.3, 2.4s ease-in-out infinite).

### 3. Logline Chapter (min-height 70vh, centered column, text-center, padding 100px 24px)
- Kicker: "A DOCUMENTARY OF SURVIVAL AND MADNESS" — Archivo 600, 11px, letter-spacing .5em, accent color, margin-bottom 44px.
- Logline: "Outcast and homeless in Hawaii - two friends confront the depths of their existence - only to awaken ancient forces obsessed with their total destruction." — Source Serif 4, weight 300, clamp(26px, 3.4vw, 44px), line-height 1.5, max-width 880px, color #e8e2d8. (Hyphens are intentionally plain "-", not em-dashes.)
- Below (margin-top 56px): "SHOT OVER ELEVEN YEARS" — 12px, letter-spacing .32em, color rgba(232,226,216,.5), flanked by two 48px × 1px rules in rgba(216,154,92,.5), gap 20px.

### 4. The Story (padding 140px 0 160px; background `linear-gradient(to bottom, #0a0908, #12100c 30%, #12100c 70%, #0a0908)`)
- Section header: "02" (11px, 600, .4em tracking, accent) + "THE STORY" (Archivo 700, clamp(28px, 3.4vw, 46px), letter-spacing .22em, #f2ede4), baseline-aligned, gap 24px, bottom border 1px rgba(232,226,216,.14), padding-bottom 26px, margin-bottom 80px. Content max-width 1240px, side padding 48px.
- Two-column grid 5fr / 7fr, gap 72px, align start:
  - Left: portrait image, 4:5 aspect ratio (prototype uses a drop-slot; production: real photo of the filmmaker in the field).
  - Right: three paragraphs — Source Serif 4, weight 300, 19px, line-height 1.85, color rgba(232,226,216,.8), gap 28px. First letter of paragraph one is an enlarged initial (32px, accent color). Exact copy:
    1. "Two strangers from different corners of the world, Ben and Anthony, travel to Hawaii - one to heal a broken heart, the other to find himself by stepping away from society. They end up living homeless in the wilds, documenting a journey that will consume them both."
    2. "Years pass and Ben descends into an outlaw existence, battling addiction while embracing the life of a tormented mystic. Convinced he is the embodiment of Satan, he becomes the target of territorial locals and is eventually jailed following a near-fatal altercation."
    3. "Meanwhile, Anthony struggles to complete the now out-of-control documentary. Spending everything he has, enduring declining health, homelessness and an increasingly volatile co-star, he searches for meaning in a journey that has taken everything from him."

### 5. Contact / Press Footer (top border 1px rgba(232,226,216,.12), padding 110px 48px 60px)
- Grid 1fr / auto, gap 64px, align end, max-width 1240px centered.
- Left: kicker "CONTACT & PRESS" (11px, 600, .5em, accent); email `contact@lovegypsyfilms.com` as a large link (Archivo 600, clamp(22px, 3vw, 40px), #f2ede4, hover #eab97e); sub-line "For press, festival and distribution enquiries. Screeners available on request." (Source Serif 4, 300, 16px, rgba(232,226,216,.55), max-width 480px).
- Right (right-aligned column, gap 10px): "ISLAND" (700, 13px, .5em, #e8e2d8) / "LOVE GYPSY FILMS PRESENTS" (10px, .32em, rgba(232,226,216,.4)) / "© 2026 LOVE GYPSY FILMS" (10px, .2em, rgba(232,226,216,.3)).

### Film-grain overlay (whole page)
Fixed, full-viewport, pointer-events none, above content: tiled 160px SVG `feTurbulence` fractal noise (baseFrequency 0.9, 2 octaves, rect opacity 0.28), layer opacity .5, `mix-blend-mode: overlay`. Toggleable — ship on by default.

## Interactions & Behavior
- **Scroll reveals**: every element marked for reveal starts at opacity 0 / translateY(28px) and transitions to visible (1.1s ease, both properties) when it enters the viewport (IntersectionObserver, threshold 0.15, one-shot). Applied to: hero button, logline kicker/text/rule line, story header/portrait/text, footer blocks.
- **Smooth scrolling** for in-page anchor nav (`scroll-behavior: smooth`).
- Nav/footer link hovers as specified above; no other interactive states.
- No forms, no loading/error states.
- Responsive: type scales via clamp(); the story grid and footer grid should stack to one column below ~820px (prototype does not implement this breakpoint — add it in production).

## State Management
None required. Static page. (The prototype exposes two design tweaks — accent color and grain on/off — which need not ship.)

## Design Tokens
- Colors: background #0a0908; raised background #12100c; text #e8e2d8; bright headings #f2ede4; accent (firelight) #d89a5c; accent hover #eab97e; hairlines rgba(232,226,216,.08–.14); muted text rgba(232,226,216,.4–.75).
- Type: **Archivo** (Google Fonts; 400–800) for all UI/headings — always uppercase with wide tracking (.22em–.5em); **Source Serif 4** (300/400 + italics) for narrative prose.
- Spacing: section padding 100–160px vertical, 48px gutters; content max-width 1240px; prose max-width 880px.
- Radius: 0 everywhere (square corners). 
- Shadows: none on UI; selection color #d89a5c on #0a0908.

## Assets
- `assets/poster.png` — ISLAND key art (supplied by filmmaker; contains title, tagline, credits baked in).
- Google Fonts: Archivo, Source Serif 4.
- Grain: generated SVG noise data-URI (in the HTML file, self-contained).
- Still needed from the filmmaker: trailer URL, portrait photo.

## Files
- `ISLAND.dc.html` — the full design (markup inside `<x-dc>`, behavior in the `Component` class script).
- `assets/poster.png` — hero key art.
- `image-slot.js` — prototype-only placeholder widget; do not ship.
