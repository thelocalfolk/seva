# Seva — Figma Node Map

Reference for pulling design context per page/section. Use with `get_design_context` in Claude Code (load the `figma-design-to-code` skill first).

- **File:** Seva | Website
- **File key:** `oFg9tSu6NxNa4I39nGpfuu`
- **URL:** https://www.figma.com/design/oFg9tSu6NxNa4I39nGpfuu/Seva-%7C-Website
- **Canvas:** `171:2` (name "Final") — holds every page frame, desktop + mobile, laid out side by side.

---

## Design system (from Figma variables)

**Type**
- **Headings — "Cyan"** (serif display), weight 400, line-height 1.15:
  - H1 50px · H2 30px · H3 20px · H4 15px
- **Body — "DM Sans"**, weight 400, line-height 1.5:
  - P1 12px · P2 10px

**Colour**
- Named token **"Teddy" `#928076`** (warm taupe — likely body text / muted accents).
- The rest of the palette is carried by imagery, not variables: cream / off-white backgrounds, blush pink panels, deep botanical red (the "For Your Ritual" banner), natural greens. Pull exact fills per section via `get_design_context` when building.

**Fonts note:** "Cyan" is the display serif — confirm the licensed webfont name and how it's loaded (Shopify font_picker vs custom @font-face) before building type. DM Sans is a Google font.

---

## Page frames (top-level nodes on canvas `171:2`)

| Page | Desktop node | Mobile node |
|------|--------------|-------------|
| Homepage | `171:6914` (1440×9544) | `171:7141` (393×10114) |
| About | `171:7586` (1440×7931) | `171:7704` (393×9580) |
| Ingredients | `171:7828` (1440×6766) | — |
| Collection | `171:10093` (1440×3287) | `171:10326` (393×3620) · `171:7941` (393×7414) |
| Product | `171:9416` (1440×9585) | `171:9770` (393×9735) |
| Blog | `171:10646` (1440×4093) | `171:10864` (393×6422) |
| Article / Single | `171:10572` (1440×3929) | `171:10958` (393×5738) |
| FAQ | `171:10732` (1440×4886) | `171:11044` (393×5389) |
| Contact | `171:14815` (1440×3174) | `171:14885` (393×3181) |
| Privacy / Policy | `171:14614`, `171:14702` (desktop) | `171:14966`, `171:15062` (mobile) |

---

## Homepage section bands (desktop `171:6914`, top → bottom)

Layer names in this file are auto-generated placeholders ("Hero 1 | Left", "Group 21") and the text-layer names are lorem — so **do not trust layer names for copy**. Read each band visually and pull real content with `get_design_context` on the band. Approx. y positions within the 9544px-tall frame:

1. **Header / nav** — transparent over hero (y 0–50).
2. **Hero** — full-bleed image, centred wordmark (y 50–843). Node cluster around `171:6921`.
3. **Marquee strip** — thin running-text band (y ~843, node `171:6919`).
4. **Intro statement** — centred serif paragraph (y ~976–1135).
5. **Image + text panel** — portrait image beside a blush text panel (y ~1180–1862).
6. **Two-image band** — two square image tiles side by side (y ~1993–2712).
7. **Editorial block + CTA** — text with vertical divider rules, square image, button (y ~2812–3345).
8. **"For Your Ritual" feature banner** — deep-red/floral full-bleed, overlay heading + CTA, gold jewellery (y ~4016–4559).
9. **Full-width image band** — single wide image (y ~5354, node `171:7083`).
10. **3-column feature row** — icon + heading + short text ×3 (y ~4642–5178).
11. **Editorial block + image** — text beside image (y ~5591–6413).
12. **Product / gallery grid** — multiple square image tiles (y ~6073–6792).
13. **Large image + caption** — full-bleed lifestyle image with small text (y ~7779).
14. **Newsletter / pre-footer** — sign-up band (y ~8555–8960).
15. **Footer** — nav links, social icons (Instagram/Facebook/TikTok), newsletter (y ~8960–9544).

> The y ranges are a guide from metadata; confirm exact band boundaries visually in Figma when building each one.
