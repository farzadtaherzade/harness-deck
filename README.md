# هرنس — Harness: از مدل زبانی تا ایجنت

A 23-slide, presenter-led **Farsi (RTL) talk deck** about agent harnesses — built as a single self-contained HTML file with a persistent Three.js car, live offline agent simulations, and QR showcases.

**Open `harness.html` in any browser. That's the whole install.**

## What's inside

| File | What it is |
|---|---|
| `harness.html` | The deck — zero dependencies, all CSS/JS/Three.js inline, fixed 1920×1080 stage |
| `troll-calculator/index.html` | A calculator with a face that dodges your cursor and demands a subscription for `1+1` |
| `script.md` | The full presenter script (Farsi) with per-slide timings (≈25:30) |
| `PRODUCT.md` / `DESIGN.md` | Durable product + design-system records |
| `.frontend-slides/src/` | Deck sources (`deck.part1.html` + `three.min.js` + `qrcode.min.js` + `deck.part2.html`) and the one-line assemble step |

## Rebuild after editing sources

```bash
node -e "const fs=require('fs');const d='.frontend-slides/src/';fs.writeFileSync('harness.html',Buffer.concat([fs.readFileSync(d+'deck.part1.html'),fs.readFileSync(d+'three.min.js'),fs.readFileSync(d+'qrcode.min.js'),fs.readFileSync(d+'deck.part2.html')]))"
```

## Deck controls

- **Next / Prev:** `←` / `→` (RTL-mirrored), Space, wheel, swipe, or the on-screen buttons
- **Slide 7:** drag to rotate the car, button explodes it into labeled parts
- **Slides 8–9:** play/pause/step the offline agent simulation; the audience picks its task
- **Inline editing:** hover the top-left corner or press `E`, `Ctrl+S` to save
- **Deep links:** `?slide=7`, `?slide=6&explode=1`

## Featured projects (QR slides)

- [huehunch.vercel.app](https://huehunch.vercel.app) — color-guessing party game
- [neon-arena-r5zh.vercel.app](https://neon-arena-r5zh.vercel.app/) — 3D wave-survival shooter
- [raid-night.vercel.app](https://raid-night.vercel.app/) — group voice-room

## Notes

- Fonts load from Google Fonts (Lalezar / Vazirmatn / JetBrains Mono); everything else is offline.
- The simulations are deterministic and clearly labeled — no real LLM calls, no fabricated data.
