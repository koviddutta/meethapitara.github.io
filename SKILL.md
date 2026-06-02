# MeethaPitara — Agent Skill

Use this design system when building any Meetha Pitara artifact — marketing site, packaging, deck, social post, product label.

## Load the tokens

Every HTML artifact must start by linking the single source of truth:

```html
<link rel="stylesheet" href="colors_and_type.css">
```

Paths are relative to the artifact's folder. From `ui_kits/web/` or `slides/` it becomes `../colors_and_type.css`.

## Non-negotiables

1. **Cream is the canvas, not white.** `--mp-cream` `#F5EFE6` is the default page background. White is only for cards / product surfaces.
2. **Three typefaces only:** Bebas Neue (display/eyebrow, UPPERCASE), Ezra (serif headings + italics), Avenir Book (body + UI). Never introduce a fourth.
3. **Hindi loanwords stay in english script**, italicised on first appearance: *dadi*, *mithai*, *ghee*, *pitara*, *kulfi*. Never use Devanagari glyphs as decoration unless the user asks.
4. **No emoji. No stock iconography beyond Lucide.** The brand motif is the `i`-with-heart (bindi) from `assets/logos/logomark-*.png`.
5. **Warm, soft shadows only** (`--sh-1` to `--sh-4`). Never sharp drop-shadows or neon glows.
6. **Editorial whitespace.** Desktop sections 96–128px vertical. Never cram.
7. **Buttons:** pill shape (`border-radius: 999px`) for primary CTAs. Terracotta or maroon fill. Always include a trailing `→` for navigational CTAs.
8. **Imagery:** real food photography or a single brand-color block. No stock photos. No generated SVG illustrations of sweets.

## Recipes

### A full-bleed section on a colored panel

```html
<section style="background: var(--mp-maroon); color: var(--mp-cream); padding: 120px 80px;">
  <p class="eyebrow">Our story</p>
  <h2>We don't make ice cream. We make <em>the memory of it.</em></h2>
</section>
```

### A flavour card

Use `preview/cards-product.html` or `ui_kits/web/FlavourCard.jsx` as the template. Product cards must show: **eyebrow** (category · weight), **flavour name in Ezra italic-adjacent**, one-line *evocative* blurb, and price in Bebas Neue.

### A pattern-border decoration

```html
<div style="height: 60px; background: url(assets/patterns/pattern-diagonal-blue-terracotta.png) repeat-x;"></div>
```

Use at the very top or bottom edge of a section. Never scatter across content.

### A slide deck

Always via the `<deck-stage>` web component — see `slides/index.html` for the canonical setup (1920×1080, speaker-notes JSON, per-slide chrome with slide number + logo + hairline rule at the bottom).

## Voice rules for copy

- Lead with feeling, not features.
- Short sentences. Then one longer one that lands.
- Em-dashes are our signature punctuation.
- Use *we* and *you*. Never "the customer" or "users".
- Price formatted `₹320`; weights formatted `500 ml` (space).
- Never "disrupt", "mission", "innovative", or "AI-powered". This brand pre-dates those words.

## Font substitution flags

All three brand faces are now live: **Bebas Neue** (Google Fonts), **Ezra** (self-hosted, full family 300–900 + italics) and **Avenir Book** (self-hosted, single 'Book' weight — bold is synthesized). All are wired in `colors_and_type.css`; `Nunito Sans` remains only as a body fallback. No substitutions remain.

## What NOT to do

- Don't invent new brand colors. The palette is six core hues plus cream neutrals. That's it.
- Don't rebuild the logo. All lockups exist in `assets/logos/`.
- Don't use a gradient as a page background.
- Don't use a left-border accent card.
- Don't use emoji or ironic ALL-CAPS.
- Don't design an icon that uses the heart from the logo — reserve it for the wordmark.
