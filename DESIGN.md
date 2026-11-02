---
name: هرنس — Harness Deck System
description: Acid-yellow engineering-blueprint world for Farsi agent-harness talks; fixed 1920×1080 stage, one persistent Three.js car.
colors:
  near-black: "#1C1C1C"
  acid: "#F5D200"
  acid-60: "rgba(245, 210, 0, 0.6)"
  acid-38: "rgba(245, 210, 0, 0.38)"
  acid-16: "rgba(245, 210, 0, 0.16)"
  acid-08: "rgba(245, 210, 0, 0.08)"
  ink-dark: "#1C1C1C"
  tire-dark: "#141414"
  headlight: "#fff6c9"
typography:
  display:
    fontFamily: "Lalezar, Vazirmatn, sans-serif"
    fontSize: "320px"
    fontWeight: 400
    lineHeight: 0.86
    letterSpacing: "0em"
  headline:
    fontFamily: "Lalezar, Vazirmatn, sans-serif"
    fontSize: "128px"
    fontWeight: 400
    lineHeight: 1.02
  body:
    fontFamily: "Vazirmatn, sans-serif"
    fontSize: "31px"
    fontWeight: 400
    lineHeight: 1.65
  label:
    fontFamily: "JetBrains Mono, monospace"
    fontSize: "20px"
    fontWeight: 400
    letterSpacing: "0.08em"
rounded:
  none: "0px"
spacing:
  slide-x: "104px"
  slide-y: "84px"
  gap: "22px"
components:
  button-primary:
    backgroundColor: "transparent"
    textColor: "{colors.acid}"
    rounded: "{rounded.none}"
    padding: "16px 38px"
  button-primary-hover:
    backgroundColor: "{colors.acid}"
    textColor: "{colors.ink-dark}"
  chip:
    backgroundColor: "transparent"
    textColor: "{colors.acid-60}"
    rounded: "{rounded.none}"
    padding: "8px 18px"
---

# Design System: هرنس — Harness Deck System

## Overview

**Creative North Star: "The Living Blueprint"** — a drafting sheet that stands up and drives.

Every slide is an engineering drawing sheet: a faint acid grid on near-black, registration crosses in the corners, drafting callouts with leader lines, and one persistent 3D car rendered as a technical object — acid faces, near-black ink edges, a drafting grid for a floor. The binary palette is absolute: near-black field, acid type, nothing else. Farsi is the voice; Latin appears only as technical chrome (mono labels like `LLM`, `MCP PORT`, terminal output). The deck speaks RTL; the car drives leftward, the direction of reading.

**Key Characteristics:**
- Binary palette: acid (#F5D200) on near-black (#1C1C1C) — every color is this hue at some opacity
- Drafting vocabulary: leader-line callouts, dimension marks, title blocks, corner registration crosses
- One persistent Three.js car that travels between slides (engine alone → assembly → driving → exploded)
- Zero dependencies: one self-contained HTML file, fonts from Google Fonts, Three.js embedded
- Fixed 1920×1080 stage, letterboxed on any viewport, never reflowed

## Colors

A single hue, weaponized. Everything luminous is acid yellow; everything structural is its shadow.

### Primary
- **Acid** (#F5D200): all type, borders, buttons, 3D car faces, route lines, rope fences, wheels' hubs. The only voice on the sheet.

### Neutral
- **Near-black** (#1C1C1C): the field, the stage, terminal backing (via 35% black over it), the ink in 3D edges, tires, 3D dark props.
- **Acid tints** (60% / 38% / 16% / 8%): secondary copy, hairlines, the drafting grid, hover fills. Secondary text is never gray — always this hue dimmed.

### Named Rules
**The Binary Rule.** No third color exists. Code "syntax" in terminals is expressed with weight, strikethrough, and opacity — never red or green.

## Typography

**Display Font:** Lalezar (Vazirmatn fallback) — a compact, tall Persian display face; type-as-graphic-mass at 320–400px.
**Body Font:** Vazirmatn — modern Persian workhorse, weights 300–900.
**Label/Mono Font:** JetBrains Mono — Latin technical chrome and terminal output only, always `direction: ltr`.

**Character:** A Persian engineering poster: Lalezar shouts, Vazirmatn explains, JetBrains Mono annotates. Persian text sets `letter-spacing: 0` and never uses uppercase transforms.

### Hierarchy
- **Display** (Lalezar 400, 320–400px, lh 0.86): the deck title, one word per slide at most.
- **Headline** (Lalezar 400, 88–150px): slide theses.
- **Body** (Vazirmatn 400/700, 31–46px, lh 1.65, max ~30ch): leads and explanations.
- **Label** (JetBrains Mono, 15–21px, +0.08em): mono chrome, counters, terminal lines, callout sub-labels.

## Layout

One fixed 1920×1080 stage scaled uniformly to the viewport; letterbox/pillarbox, no reflow (viewport-base.css inlined in full). Slides compose text in the right 46% (RTL reading starts right) with the 3D subject left; centered layouts only on the interactive and payoff slides. Padding 84px×104px. The drafting grid (80px cells, acid at 8%) and corner registration crosses live on the stage — the sheet persists behind every slide.

## Elevation & Depth

Flat. No box shadows anywhere in the world — depth comes from three sources: the 3D scene's perspective and fog (Fog 0x1C1C1C, 11→26), the acid hairline grid receding on the floor, and the drafting callouts that lift labels off the sheet with 1px leader lines. A soft radial vignette appears only inside the terminal aesthetic when used.

## Shapes

Radius zero everywhere — buttons, panels, pips, blocks are sharp rectangles. Borders are 1–2px acid at 16–60% opacity. The callout is the signature geometry: a 10px square dot, an 84px × 1px leader line, then the label with a small mono sub-label beneath. Pips are 16px squares that fill solid when a simulation step completes.

## Components

### Buttons
- **Shape:** square (0px radius)
- **Primary:** transparent field, 2px acid border, acid Vazirmatn 700 text; padding 16px 38px
- **Hover / Active:** fills acid, text flips near-black; focus ring is a 2px dashed acid outline, offset 3px
- **Small variant:** 21px text, 10px 24px padding (simulation controls)

### Drafting Callout
- **Shape:** dot → 84px leader line → label + mono sub-label, one row, RTL (dot right) or reversed (dot left) depending on which side of the part the dark space is
- **Behavior:** fades in staggered (0.25s steps) when the slide becomes visible; on the exploded slide only, when the explosion state is on

### Terminal (simulation)
- **Shape:** 2px acid-38 border, 35% black fill, JetBrains Mono 21px, `direction: ltr`
- **Content:** `$ ` prompt in acid, output at 60% acid, added lines bold acid, removed lines struck through at 38%; block cursor blinks at 1.1s steps

### Agent Panel (simulation)
- **Shape:** 2px acid border on 8% acid fill, 560px wide, RTL
- **Content:** mono step counter, Lalezar step title, 2px-acid-bordered "thought" line in 60% acid, square pips

### Navigation (deck chrome)
- **Shape:** fixed bottom-center bar outside the stage, near-black with 16% acid border; square 46px buttons with inline SVG chevrons (RTL: next points left); Persian-digit counter between them; 3px acid progress hairline at the very top

## Do's and Don'ts

### Do:
- **Do** keep every color a tint of #F5D200 or #1C1C1C — the Binary Rule has no exceptions.
- **Do** set terminal/code runs `direction: ltr` inside the RTL page; Persian prose stays RTL.
- **Do** earn grid textures: the drafting grid exists because the world IS a drafting sheet.
- **Do** reuse the callout (dot + leader + label) for any part annotation, choosing normal/reversed so text lands on dark space.

### Don't:
- **Don't** add a third hue, rounded corners, or box shadows — flatness and binary color are the world's spine.
- **Don't** reflow slide content per device; the stage letterboxes, period.
- **Don't** switch slides with `display: none` — visibility/opacity via `.active`/`.visible` only.
- **Don't** let body copy sit on acid surfaces or labels sit on the acid car body — text and subject share a hue, so composition must keep them apart.
- **Don't** put internal workflow language (slide numbers as "01/14" are fine; "preview", template names are not) on the sheet.
