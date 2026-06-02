# MeethaPitara — Design System

> **"A pitara full of nostalgia."**
>
> मीठा पिटारा — "sweet treasure box." A premium modern Indian dessert brand that bottles childhood mithai memories into a contemporary, editorial, investor-ready consumer product.

---

## About MeethaPitara

**Meetha Pitara** (literally "sweet treasure chest" in Hindi) is a premium modern Indian dessert brand — gelato, mithai and sweet experiences — anchored in nostalgia. The brand name itself recalls the painted tin *pitaras* grandparents used to keep sweets in, so every touchpoint is a small act of remembering: a familiar flavour, an old pattern, a warm colour, the rounded letterforms of a childhood sign-painter.

The brand voice is **playful but professional, emotionally warm, heritage-meets-modern**. Visuals lean editorial and polished — think Indian sweet shop re-imagined as a premium boutique — rather than loud or startup-y.

**Products implied by the source materials:**
- `gelato` — the flagship SKU line (hence `Patterns_gelato.pdf`)
- `packaging` — tins, sleeves, takeaway boxes (strongly implied by logo suite variations)
- `marketing site / e-commerce` — a DTC storefront
- `investor / pitch deck` — the brief specifically calls for a premium investor deck

No live codebase or Figma was attached — only the brand book + logo PNG suite + pattern/graphics PDFs. Everything visual in this system is lifted from those source materials directly (logos, colours, pattern swatches) or documented as the closest faithful extension of them.

---

## Sources (provided by the user)

| Source | Path | Status |
|---|---|---|
| Brand guideline sheet | `uploads/Brand Guideline Sheet 2.pdf` | ✅ read, parsed |
| Logos & graphics (38 pages of logo suite) | `uploads/Logos and graphics.pdf` + mirror in `Branding/Meetha Pitara x Janvi/Logos and graphics.pdf` | ✅ logos extracted to `assets/logos/` |
| Patterns — gelato | `uploads/Patterns_gelato.pdf` | ⚠️ PDF too dense for runtime rasterisation; pattern samples lifted from LOGOS suite instead (`assets/patterns/`) |
| Logo PNG suite (38 files) | `Branding/Meetha Pitara x Janvi/PNG/LOGOS-01..38.png` | ✅ mirrored and renamed to `assets/logos/` |
| `LOGOS.ai`, `VD 2B.pdf` | `Branding/Meetha Pitara x Janvi/` | Not parsed — AI file needs Illustrator; VD 2B is a brand deck PDF the guideline sheet already summarised |

**Credit:** brand identity designed by **Janvi Mehta**.

---

## Index — what lives where

```
/
├── README.md                     ← you are here
├── SKILL.md                      ← Claude Code / agent skill manifest
├── colors_and_type.css           ← CSS variables: colors, type, spacing, shadows, motion
├── assets/
│   ├── logos/                    ← primary / secondary / submark / logomark / badge, in up to 6 colorways
│   └── patterns/                 ← diagonal bead + vine borders (brand swatches)
├── preview/                      ← design-system preview cards (Design System tab)
├── ui_kits/
│   ├── packaging/                ← mithai-box / gelato-tub packaging mocks
│   └── web/                      ← marketing site components (hero, product card, nav)
├── slides/                       ← investor-deck sample slides (Title, Quote, Product, Stats, Market)
```

---

## Visual Foundations

### Palette

The guideline sheet locks in a tight, warm, earthy palette. It's **six colours total** — that restraint is a feature, not a limitation.

| Token | Hex | Role |
|---|---|---|
| `--mp-white` | `#FFFFFF` | paper, packaging base |
| `--mp-ink` | `#231F20` | body ink, headline black |
| `--mp-blue` | `#0D0195` | deep cobalt — the "unexpected" brand anchor, heritage feel |
| `--mp-terracotta` | `#CC6B46` | warm clay — the hero brand colour, used on logo & packaging |
| `--mp-peach` | `#D59282` | dusty peach — soft accent, kulfi / rose flavours |
| `--mp-maroon` | `#8F2A28` | deep mithai-box red — premium accent, foil-stamp feel |

Extended neutrals (`--mp-cream`, `--mp-sand`, `--mp-oat`) are harmonious extensions used as page surfaces. `--mp-forest` `#2D4A36` appears in the pattern swatches as a green foil accent.

### Backgrounds

- **Cream/paper is the default canvas**, not white. `--mp-cream` (`#F5EFE6`) feels like unbleached card stock and is warmer than white — it's the "page" for most surfaces.
- **Solid deep colour full-bleed** is the second background mode — a maroon, cobalt, or terracotta panel used for section breaks, hero banners, or pack-shots. Never gradient blends.
- **Pattern borders** (see `assets/patterns/`) sit at the very top or bottom edge of a layout as a decorative rule, diagonal or horizontal. They are never scattered over content.
- No stock photography energy, no "gradient mesh" backgrounds, no noise textures.

### Imagery

- Cinematic, warmly-lit still life of mithai and gelato — the light is warm (3200K-ish), shadows soft, grain minimal.
- Food is always **centre-stage and uncluttered**: one hero sweet, one tin, one scoop. No flat-lay collages with fifty elements.
- When imagery isn't available, use cream paper + a single brand-colour block or pattern border instead of stock.

### Corner radii

- Packaging / cards / image frames: **16–24px** (`--r-md`..`--r-lg`). Warm, hand-held feel, never sharp corners.
- Buttons: `--r-pill` (fully rounded) or `--r-md` for rectangular "tin-label" buttons.
- Never use only a left-border accent card — that's a startup trope, not this brand.

### Shadows

Shadow system is **soft, warm, and low-contrast** — closer to "object on paper" than "UI material":

```
--sh-1:  subtle pop (list items, chips)
--sh-2:  standard card rest state
--sh-3:  hovered / featured card
--sh-4:  hero module (tinted with maroon for warmth)
```

No hard drop shadows, no neon glows, no inner shadows on inputs (inputs use a hairline instead).

### Borders

`1px solid var(--line)` (`#E2D6C2`) — a warm oat hairline, **not** cool grey. Used sparingly — mostly for input fields, list dividers, and card edges when no shadow is present.

### Hover / press

- **Hover** — translate-Y `-2px`, bump to `--sh-3`, subtle `scale(1.01)` on photography thumbs.
- **Press** — shrink to `scale(0.98)`, shadow collapses to `--sh-1`, colour deepens one step (terracotta → maroon).
- Never a "darken filter" hover. Always a directional physical cue.

### Animation

- **Philosophy:** everything is unhurried, warm, and confident — this is premium, not jumpy.
- Easing: `--ease-soft` `cubic-bezier(.22,.61,.36,1)` for most transitions; `--ease-out` for entries.
- Durations: 160ms for micro (hover), 260ms for UI, 480ms for content reveals.
- Fades + subtle Y-shifts. No bounces, no parallax hero, no flashy scroll effects.

### Transparency + blur

- Rarely used. The brand favours flat printed surfaces. Blur shows up only on sticky nav-on-scroll (`backdrop-filter: blur(14px)` over `rgba(245,239,230,.85)`) and on modal scrims.

### Layout

- Editorial whitespace is non-negotiable. Section padding is **96–128px vertical** (`--sp-9/10`) on desktop, 48–64px on mobile.
- Grid: 12-column, max-width 1280px; gutters 24–32px.
- Left-aligned text is the default. Centred text is saved for heroes and quotes.
- Headlines on cream sit on **2–3 lines max** with generous margin.

### Fixed elements

- Top nav is fixed on scroll with cream-tinted blur background.
- Logo mark (`i` with bindi dot) is used as a compact favicon / app-icon / social-profile cue.

---

## Content Fundamentals

### Tone of voice

Playful but professional. Emotionally warm. Heritage-meets-modern. We write like a grandmother who also happens to be a food critic — affectionate, specific, and never precious.

**Do:**
- Use English with comfortable Hindi/Urdu loanwords: *pitara, mithai, ghee, elaichi, kulfi, khoya, bindi*.
- Lead with memory and feeling, not ingredients or specs.
- Speak in short, warm declaratives. Short sentences. Then one longer one that lands like a spoonful.
- Use **we** (as the brand) and **you** (as the reader / customer). Friendly, not formal.

**Don't:**
- Don't use startup-voice (*"We're on a mission to disrupt…"*). We're not disrupting anything; we're remembering.
- Don't use emoji. Unicode characters like `—` and `·` are fine as typographic punctuation.
- Don't use exclamation marks stacked or ironic all-caps.
- Don't over-explain. Let the food, the word "pitara", and the photography do the work.

### Casing

- Headlines: **sentence case** in Ezra (serif). Occasional **ALL CAPS** in Bebas Neue for eyebrow labels, price tags, stamps.
- Buttons & nav: **Title Case** ("Shop the pitara"). Never sentence case buttons.
- Small labels / section eyebrows: **ALL CAPS** + wide tracking (`--tr-caps` 0.16em).

### Punctuation + rhythm

- Em-dashes (—) are the signature punctuation; they do what commas can't.
- One-word sentences earn their place: *"Remember?"*
- Hindi words italicised **only** when first introduced on a page; thereafter set roman.
- Prices: `₹120` (no space). Weights: `80 g`, `1 kg` (with space).

### Example copywriting

> **Eyebrow:** A PITARA FULL OF NOSTALGIA
>
> **Headline:** The mithai your *dadi* would approve of.
>
> **Body:** Small batches. Pure *ghee*. No shortcuts — and definitely no corn syrup. We make gelato the way our grandmothers made *kulfi*, then we pack it like a treasure.
>
> **CTA:** Open the pitara →

> **Product card:** *Kesar Pista* · A summer afternoon in Lucknow · ₹320 / 500 ml

> **Stat slide:** 47 cities · 12 flavours · one very full pitara.

---

## Typography

### Brand specification (from guideline sheet)

| Role | Font | Usage |
|---|---|---|
| Primary | **Bebas Neue** | Headers, titles, eyebrows, stamps, price tags — uppercase |
| Secondary | **Ezra** | Subheadings, editorial serif moments |
| Supporting | **Avenir Book** | Body copy |

### What this system ships with

All three brand faces are now wired — two self-hosted from client-provided files, one from Google Fonts:

| Brand font | Status | Why | Action needed |
|---|---|---|---|
| Bebas Neue | **Bebas Neue** (Google Fonts) | Same family | ✅ none |
| Ezra | **Ezra** (self-hosted, `fonts/`) | Licensed brand serif provided by client — full family 300–900 + italics, self-hosted | ✅ live |
| Avenir Book | **Avenir Book** (self-hosted, `fonts/`) | Licensed brand sans provided by client — single 'Book' weight; bold is synthesized. `Nunito Sans` kept only as fallback | ✅ live |

All tokens live in `colors_and_type.css` as `--font-display`, `--font-serif`, `--font-body`, `--font-devanagari`.

---

## Iconography

The brand guideline **does not ship an icon set**. It's a print-first identity — logos, patterns, palette, type. That's it.

So this design system takes the following stance on icons:

1. **No bespoke icon font.** The brand doesn't have one, so we don't invent one.
2. **Lucide icons, via CDN,** are used for any UI glyphs (nav, cart, search, social). Lucide's rounded-stroke, 2px-weight aesthetic matches the rounded custom letterforms of the `meetha pitara` wordmark.
   - Load: `<script src="https://unpkg.com/lucide@latest"></script>` and call `lucide.createIcons()`.
3. **The bindi heart** — the drop on the `i` in "pitara" — *is* the brand's native icon motif. It's used as a favicon, social-profile logomark, and occasional inline flourish. Files: `assets/logos/logomark-*.png`.
4. **No emoji.** Ever, in UI or copy.
5. **No unicode-as-icon hacks** (e.g. `♥` or `★`). Always a proper SVG or PNG.
6. **Pattern borders as decoration.** The diagonal bead+vine borders (`assets/patterns/*.png`) take the role icons usually play in ordinary brand systems — they signal section change, decorate a margin, or frame a quote.

### Available brand asset files

**Logos** — 5 lockups in up to 6 colorways, high-res transparent PNG (square masters, ~5625px):
- `primary-*` — full wordmark + tagline, horizontal
- `secondary-*` — stacked wordmark + tagline
- `submark-*` — lowercase `m` only, large and decorative
- `logomark-*` — single `i` with heart-shaped bindi dot (for favicons/app icons)
- `badge-*` — wordmark inside an organic asymmetric blob (for stickers / seals)
- `primary-*-tight` — transparent margins trimmed to the lockup bounds; use these for nav bars / inline placement (the square masters float tiny inside their padding at small sizes)

Colorways: `black`, `white`, `terracotta`, `blue`, `maroon`, `peach`. The full official suite carries all six across primary / secondary / submark / logomark; `peach` and the `white` cuts of secondary/submark/logomark are generated by recolouring the masters (alpha preserved). The `badge` blob ships `black` / `white` / `terracotta` / `blue` / `maroon` (no peach in the official suite).

**Patterns** — two diagonal border motifs in different colorways:
- `pattern-diagonal-blue-terracotta.png`
- `pattern-diagonal-green-maroon.png`

---

## Design System preview cards

Cards live in `preview/` and are registered in the project's asset-review manifest. Open the **Design System tab** to browse them grouped by Type · Colors · Spacing · Components · Brand.

## UI kits

- `ui_kits/web/` — marketing-site components (nav, hero, product card, footer) with a clickable `index.html` demo.
- `ui_kits/packaging/` — physical packaging system mocks (tin label, sleeve, sticker) shown on-surface.

## Slides

`slides/` contains five sample investor-deck slides (Title, Quote, Product, Stats, Market) built on the same tokens. Open `slides/index.html` to flip through them.
