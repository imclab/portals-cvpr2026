# Portals CVPR 2026 Poster — v6 spec

**Created:** 2026-05-27
**Author:** James + Claude (frontend-design skill)
**Supersedes:** `H3M_Portals_CVPR_Poster_84x42_100ppi_5.jpg` (v5)
**Files:** `poster.html` · `poster.css`

---

## Physical

- 84″ W × 42″ H landscape (CVPR 2026 spec)
- 100 ppi → 8400 × 4200 px @ 1:1
- 1 px CSS = 1 pt print
- Bleed: none; safe inset = `48px` (frame hairline)

## Aesthetic direction (frontend-design skill applied)

**Industrial-utilitarian × editorial.** Pure-black canvas (Portals brand SSOT `src/theme/brandColors.ts`) + single Iris-glow accent `#F7FFA8` + monospace-annotation pairing (Satoshi display / JetBrains Mono caption). Generous whitespace, hairline separators only, zero decorative borders, one accent color used as scream-only signal.

**Differentiation thesis:** in a workshop where ~95% of posters are white background + sans-serif + black text + small QR + math density, the Portals poster is the only **dark, product-shipping** poster. Visible across the workshop floor. Carries through to a TestFlight CTA — visitors can try the product on their phone before they finish reading.

## Grid

```
┌──────────────────────────────────────────────────────────────────────────┐
│  TOP STRIP                                                                │
│  [h3m] [IMC LAB]                       [CVPR 2026 · Denver · 4DWM]      │
│  ─────────────────────────────────────────────────────────────────────  │
│  Portals.                              <— 320pt display                 │
│  Persistent, Editable 4D Spatial …     <— 92pt sub                       │
│  From stateless scenes to stateful worlds…  <— 56pt thesis             │
│  Tunick · Brant · Pennock · Kasowski   ¹H3M  ²IMC Lab                   │
├──────────────────────────────────────────────────────────────────────────┤
│  HERO BAND                                                                │
│  ┃ 2.7–4.1× LOD       ┃ 60 fps                ┃ 360+ VFX                │
│    speed-up · iPhone     sustained on             one 5-property         │
│    14 Pro                commodity mobile          shared contract       │
├──────────────────────────────────────────────────────────────────────────┤
│  4-COLUMN BODY                                                            │
│  01 Why 4D?      02 Edge runtime    03 Persistence    04 Creator         │
│  - lede          - lede              - lede            - lede             │
│  - GOAL box      - contract diagram  - schema list     - 4 screenshots    │
│  - use cases     - perf table        - perf table      - UV-mux quadrant  │
├──────────────────────────────────────────────────────────────────────────┤
│  BOTTOM STRIP — 5 cells                                                   │
│  axes(4) │ LIMITS │ 3 QR │ refs(8) │ contact + acks                      │
└──────────────────────────────────────────────────────────────────────────┘
```

## Borrowed patterns (from `_ref/` reference posters)

| Pattern | Source ref poster | Where in v6 |
|---|---|---|
| Numbered sections | RayGS (8 sections) | `01–04` mono-set sec-num |
| GOAL pull-quote | CUT3R | `.goal` block in col 01 |
| TL;DR / honesty callout | GenFusion (red TL;DR) | `.limits` red-left-border block |
| 3-row Goal/Challenges/Solution | MegaSaM | col 01 lede → goal → use-cases |
| Method diagram center | all 4 | `.contract` diagram col 02 |
| Quantitative table on right | all 4 | `.perf` tables cols 02 + 03 |
| Large org logo top | RayGS (Meta) | `.logo-h3m` 140pt |
| Author + affiliation strip | all 4 | `.authors` row |
| Rotated axis labels (idea) | GenFusion | not adopted — saved for v7 if rev grids land |

## Net-new patterns (no ref poster has)

- **Dark substrate** — single-poster differentiation across the workshop floor
- **Hero numerics band @ 280pt** — 3 stats above-the-fold, no other 4DWM poster does this
- **Product screenshots column** — only deployed-shipping product at workshop
- **5-property contract diagram** — visualizes the paper's clearest systems contribution
- **MetavidoVFX UV-mux quadrant** — Keijiro attribution + record→edit→replay loop
- **Limitations / honesty box** — earns trust w/ Schwarz / Wang / Dai-tier readers; mirrors paper §8.4 + reviewer-driven honesty pass
- **3 QR codes** w/ TestFlight CTA — captures walk-bys

## Type system

- Display: **Satoshi** 900 / 700 / 500 — variable letter-spacing `-0.055em` (huge) → `-0.005em` (body). Stylistic sets ss01, ss02.
- Mono: **JetBrains Mono** 700 / 500 / 400 — used for section numbers, captions, labels, technical annotation.
- Scale: 320 (title) · 280 (hero num) · 92 (subtitle) · 64 (sec title) · 56 (thesis) · 30 (lede) · 24 (body) · 22 (mono labels) · 18 (mono fine-print) · 14 (acks).
- Reading distance @ 6 ft → all body type ≥ 20pt. Verified.

## Color

| Token | Hex | Role |
|---|---|---|
| `--bg` | `#000000` | sheet canvas (Portals SSOT) |
| `--fg` | `#FFFFFF` | primary text |
| `--fg-dim` | `#C8C8C8` | secondary text |
| `--muted` | `#6a6a6a` | tertiary / acks |
| `--accent` | `#F7FFA8` | Iris glow — sec-num, hero suffix, GOAL, contract shader, table highlights, QR captions |
| `--accent-soft` | `rgba(247,255,168,0.10)` | GOAL bg, contract-prop chips |
| `--accent-glow` | `rgba(247,255,168,0.35)` | text-shadow halos (sparingly) |
| `--edge` | `#e74c3c` | limitations callout — ONLY used here |
| `--hair` | `rgba(255,255,255,0.10)` | separators |
| `--hair-strong` | `rgba(255,255,255,0.22)` | emphasized separators |

One accent rule: yellow is the ONLY positive accent. Red `--edge` reserved exclusively for the limitations box (one usage). No other colors.

## QR payloads (to generate before print)

| QR | URL | Notes |
|---|---|---|
| Paper | `https://imclab.github.io/portals-cvpr2026/` | Project + paper PDF |
| Try on iPhone | TestFlight invite link | Auto-redeem; consumer-readable |
| Project + XRAI | `https://h3m.ai/portals` | Studio + XRAI spec |

Generate at 1024×1024 PNG, paste into the `.qr-box` divs as `<img>`. Use a high-error-correction QR (H tier = ~30%) so the booth lighting + camera glare doesn't break it. Keep quiet zone ≥ 4 modules.

## Open production tasks

- [ ] Replace 4 `.shot .ph` placeholders with real iPhone screenshots (use v5 source PNGs from `src/features/figment/res/`)
- [ ] Generate + drop 3 QR PNGs into `qr-box` divs
- [ ] Add real H3M logo SVG (currently typographic `h3m` placeholder)
- [ ] Verify Satoshi loads from Fontshare CDN at print resolution; fallback embedded if booth wifi unreliable
- [ ] Print test: render w/ Chrome `Print → Save as PDF`, A0 landscape; visually inspect at 25% zoom for legibility, gradient banding, accent contrast
- [ ] Color-proof on actual booth print stock if vendor allows
- [ ] After review: tag as v6.0, snapshot PNG to `_ref/v6_final.png` for handoff

## Trust tier
**T2 partially-validated** — design system applied, brand-locked, structure complete. Promotes to T1 after live test print + visual review.

## Honest limits of this design

1. Placeholder QR squares — not real codes
2. Placeholder screenshot tiles — not real iPhone captures yet
3. No real H3M SVG logo
4. Browser print fidelity to A0 unverified at this resolution; may need Illustrator round-trip for production
5. Single column of body text in `.col p` may need tighter ragging once real content lands
6. UV-mux quadrant uses CSS gradients to *suggest* the mux pattern — not an accurate visualization of the Keijiro layout
