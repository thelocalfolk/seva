# Seva — Homepage Build Plan

Section-by-section plan for the Broadcast homepage (`templates/index.json`), matched to the Figma homepage (`171:6914`). Build in Claude Code, one section at a time: pull the band with `get_design_context`, reuse/customise the matched Broadcast section, then check it in the theme editor.

**Aesthetic:** luxe editorial beauty brand. Serif display (Cyan) + DM Sans body, generous whitespace, full-bleed imagery, cream / blush / botanical-red palette, warm taupe (`#928076`) text. Broadcast's own sections get us most of the way — reuse where the layout is close, build custom only where the design is distinct (marquee, divider-rule editorial block, overlay feature banner).

---

## Build order

Do the structural, reusable sections first (fast wins, establishes the type + colour system), then the custom editorial pieces.

**Phase 1 — foundations**
1. **Global type + colour** — set up the Cyan + DM Sans fonts and the palette in theme settings / CSS before building sections, so everything inherits it. Confirm the Cyan webfont licence/source first.
2. **Header** (`sections/header.liquid`) — nav + wordmark, transparent over hero.
3. **Footer** (`sections/footer.liquid`) — link columns, social icons (Instagram, Facebook, TikTok), newsletter.

**Phase 2 — homepage sections (top → bottom)**

| # | Figma band | Best-fit Broadcast section | Reuse / custom |
|---|-----------|---------------------------|----------------|
| 1 | Hero (full-bleed image + wordmark) | `section-hero.liquid` | Reuse — configure image, overlay, height |
| 2 | Marquee strip (running text) | `section-announcement.liquid` / `ticker.js` | Reuse Broadcast ticker; light custom styling |
| 3 | Intro statement (centred serif) | `section-rich-text.liquid` | Reuse |
| 4 | Image + blush text panel | `section-double.liquid` | Reuse — image one side, text panel other |
| 5 | Two-image band | `section-double.liquid` / `section-products-image.liquid` | Reuse |
| 6 | Editorial block + divider rules + CTA | `section-rich-text.liquid` (custom) | **Custom** — vertical divider rules are bespoke |
| 7 | "For Your Ritual" feature banner | `section-hero.liquid` (overlay) / `section-custom-content.liquid` | **Custom-ish** — full-bleed overlay heading + CTA |
| 8 | Full-width image band | `section-products-image.liquid` / `section-hero.liquid` | Reuse |
| 9 | 3-column feature (icon + heading + text) | `section-multicolumn.liquid` / `section-highlights.liquid` | Reuse |
| 10 | Editorial block + image | `section-double.liquid` | Reuse |
| 11 | Product / gallery grid | `section-collection.liquid` / `section-look.liquid` | Reuse — wire to a collection |
| 12 | Large lifestyle image + caption | `section-double.liquid` / `section-hero.liquid` | Reuse |
| 13 | Newsletter / pre-footer | `section-newsletter.liquid` | Reuse |

---

## Working rules for the build (from the Shopify skills)

- **Audit before editing** any existing Broadcast file (run the `shopify-code-audit` skill) — read the file, check for existing styles/JS, report before writing.
- **Schema-driven everything** — all copy, colours, images, spacing as schema settings; every section gets a preset. Nothing hardcoded.
- **Scope CSS** to `#section-{{ section.id }}`; mobile breakpoint at 768px; check the mobile Figma frames (`171:7141` etc.) for each band.
- **Broadcast gotchas:** colour schemes via `block.settings.color_scheme` can override backgrounds; shared-snippet CSS lives in the matching CSS file; cart re-render fires `cart:refresh` / `cart:updated`.
- **Australian English** in labels, comments, and copy.

## Open questions before / during build

- **Copy is placeholder** in the Figma (lorem "Creative direction is where strategy meets imagination…"). Confirm real homepage copy with the client, or pull final wording from each band as it's designed.
- **"Cyan" font** — need the licensed webfont file/source and how to load it.
- **Products / collections** — which collection feeds the gallery grid (band 11) and any featured-product areas.
- **Marquee content** — what runs in the strip (band 2).
