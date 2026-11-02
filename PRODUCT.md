# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

delegated: zero-dependency, single-file HTML — the user's explicit choice of the `/frontend-slides` skill fixes the stack (one self-contained HTML file per deck, inline CSS/JS, no npm, no build tools).

## Users

The user and their immediate team. They build and present the web slide decks themselves; there is no external customer audience for the tooling.

## Product Purpose

Web-based presentations: animation-rich HTML slide decks that run entirely in the browser as a single self-contained file. The immediate content focus is decks about agent harnesses and agents (the AI-agent ecosystem). Success is a deck that presents live in the browser, looks custom-crafted rather than template-generic, and stays reusable across talks.

## Positioning

Unlike PowerPoint/Google Slides exports, each deck is a zero-dependency HTML file with a fixed 1920×1080 stage and a bespoke per-deck design — nothing to install, nothing to build, opens anywhere.

## Operating Context

- Decks are produced through the `/frontend-slides` skill's pipeline: content discovery → style discovery via three visual single-slide previews the user picks from → full deck generation → live presenting.
- Primary consumption is presenting live from the HTML file (arrow-key/space navigation, touch/swipe when enabled). Deployed URLs, PDF export, and .pptx conversion were deliberately not selected as workflows.
- Inline text editing is a post-draft affordance (press E, click text, Ctrl+S to save) unless a deck is explicitly locked.
- This workspace is greenfield: each deck lands as its own HTML file here.

## Capabilities and Constraints

Binding constraints inherited from the frontend-slides skill (must hold for every deck):
- Fixed 1920×1080 stage scaled uniformly to the viewport; 16:9 preserved on every screen; no responsive re-layout of slide content.
- Zero dependencies: single HTML file, all CSS/JS inline; fonts from Fontshare or Google Fonts (never system defaults).
- Slide switching via `.active`/`.visible` with `visibility`/`opacity`/`pointer-events` (never `display: none`); include the skill's `viewport-base.css` in full.
- `prefers-reduced-motion` support; no scrolling, overflow, or overlapping panels; no text below comfortable reading size.
- Distinctive per-deck aesthetics; avoid generic "AI slop" (Inter/Roboto/Arial defaults, purple-gradient-on-white, cookie-cutter layouts).

Deliberately undecided (recorded, not invented): typical deck length; density mode is chosen per deck (speaker-led vs reading-first) via the skill's Phase 1 interview; whether .pptx conversion, URL deployment, or PDF export will ever be needed.

## Brand Commitments

None — confirmed "no fixed brand": each deck is free to choose its own aesthetic; no house style to respect.

## Evidence on Hand

None yet. The workspace is empty: no existing decks, logos, content, data, or testimonials. Future decks use only content the user provides per deck; nothing may be fabricated.

## Product Principles

1. The deck is the artifact: self-contained and portable — it presents live in any browser with zero installs.
2. Every deck earns its own committed aesthetic; never converge on a house look or generic defaults.
3. Density is a decision: speaker-led or reading-first is chosen deliberately per deck, never by accident.
4. Design inside the stage: the fixed 16:9 canvas is the medium, not a constraint to fight.
5. Only real content: slides carry what the user actually supplies; nothing invented to fill space.

## Accessibility & Inclusion

Baseline inherited from the skill: `prefers-reduced-motion` support and comfortable reading sizes at stage scale. No WCAG target or other product-specific requirement established.
