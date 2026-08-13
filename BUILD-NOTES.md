# Seva Homepage — Overnight Build Notes

Log of the homepage rebuild to match the Figma design (`171:6914`), done while you were asleep.
**Nothing has been committed or pushed** — all changes are local edits to the sandbox files for your review.

Working rule applied throughout: **implement the brand designer's Figma verbatim** — no creative substitutions.

---

## ☀️ MORNING REPORT — every designed page built + loop-checked (read this first)

While you slept I finished the build and ran a full Figma loop-check on every page. **Nothing pushed — all local for your review.** Every page renders **HTTP 200 with zero Liquid errors** and valid JSON.

### Pages (all 9 designed pages done)

| Page | Template | Preview | Status |
|---|---|---|---|
| Homepage | `index.json` | `/` | ✅ loop-checked |
| About | `page.about.json` | `/pages/about` | ✅ loop-checked |
| Ingredients | `page.ingredients.json` | `/pages/about?view=ingredients` | ✅ loop-checked · images live |
| FAQ | `page.faq.json` | `/pages/faq` | ✅ loop-checked |
| Contact | `page.contact.json` | `/pages/contact` | ✅ loop-checked · images live |
| Privacy Policy | `page.privacy-policy.json` | `/pages/about?view=privacy-policy` | ✅ loop-checked |
| Terms of Service | `page.terms-of-service.json` | `/pages/about?view=terms-of-service` | ✅ loop-checked |
| Product (Hair Oil) | `product.hair-oil.json` | `/products/seva-ayurvedic-modern-hair-oil-50ml-1?view=hair-oil` | ✅ loop-checked |
| Collection (Best Sellers) | `collection.best-sellers.json` | `/collections/all?view=best-sellers` | ✅ loop-checked |

*(Preview links need the `shopify theme dev` server running on `127.0.0.1:9292`, opened on your Mac.)*

### ⚠️ Decisions that need you (in priority order)

1. **Warm panel colour — `#EBEBEB` vs `#f2edec`.** You told me to use `#EBEBEB` for the Ingredients panels, so those (and the "Still have questions?" / FAQ-promo CTAs on FAQ/Contact/Privacy/Terms/Product) use `scheme-stone` = `#ebebeb` — **6 templates**. But the Figma actually paints every warm panel/card at `#f2edec`, so the overnight loop-checks used `#f2edec` on About (devotion/conscious), Homepage (ritual + review cards) and Product (Visible Results) — **3 templates**. **Pick one and I'll unify the site in ~2 min:** your `#EBEBEB`, or the Figma's `#f2edec`.
2. **Terms of Service copy artifacts** (from the Figma boilerplate, kept verbatim): a `[NOTE TO MERCHANT: …]` note in Section 9 (should be deleted — it's internal), 4 × `[LINK]` placeholders needing real URLs, and Section 17's heading duplicating Section 16 ("Disclaimer of Warranties" — its body is a Limitation of Liability clause).
3. **Hero subtexts:** Privacy's reads "Please see below for answers to common questions from customers" (FAQ leftover — it IS in the Figma, but wrong for this page); Terms' is a bare "Below is our Terms of Service."
4. **Product Add-to-Cart button** is now an **outline** style (every button in the Figma is outline; only ATC was solid) — deliberate, but eyeball it.
5. **About `@sevabeautyau`** heading should be left-aligned with the "Follow along…" subtitle removed (minor Figma delta).

### 🛠️ Store admin (only you — needs store access)

- **Create Pages + assign templates:** Ingredients → `page.ingredients`, Privacy → `page.privacy-policy`, Terms → `page.terms-of-service`. Assign `product.hair-oil` to the Hair Oil product, and create a **Best Sellers collection** + assign the `best-sellers` template. (About, FAQ, Contact pages already exist & wired.) Point footer nav at them.
- **Upload images:** hero photos for FAQ / Privacy / Terms; the Clean-panel photo + a real Sweet Almond tile (Ingredients); and the 2 product-page marketing images in `figma-exports/product/`. All other slots are pre-wired to filenames — bulk upload auto-populates.
- **Apps:** subscriptions (Subscribe & Save pricing), reviews (star ratings + Reviews band), Afterpay, and an Instagram feed app (the `@sevabeautyau` placeholders sit ready for it).
- **Products/merch:** create the **Golden Kansa Comb** (the "Complete your ritual" upsell) + a **SEVA Ritual Set bundle** (Bundle & Save button target); set up product recommendations ("You may also like"); drive the "Best Seller" badge via a product tag/metafield.
- **Nav menus:** build the footer Housekeeping/Shop/Discover/Follow menus.

### 🚧 Not built (by design)

- **Blog + Article** — designed in the Figma, but you're handling the blog. Heads-up: the Figma also shows a **"The Blog" band on the Homepage and About page** (3 article cards) that isn't built — it needs a Shopify blog + a new blog/article-grid section. Flag when you want it.

### Loop-check fixes applied overnight (summary)
- **Homepage:** hero text `#ffffff`→`#f5f5f5`; ritual/review card fills →`#f2edec`; two paragraph splits; tile height 640→720.
- **About:** devotion/conscious panels →`#f2edec` (scoped CSS); tile height 640→720.
- **Ingredients:** (earlier) panel colours, spacing, 50px headings, centred grid, arch mask, images wired & uploaded.
- **FAQ/Contact:** CTA/FAQ-promo panels →`scheme-stone`; spacing; (galleries reverted to IG placeholders per your call).
- **Privacy:** inter-section spacing brought into rhythm (→40px). **Terms:** already matched.
- **Product:** ATC →outline; Afterpay/sub-note left-aligned; accordion label sizes; removed duplicate "Seva + You" eyebrow; Visible Results card `#f2edec` + gap 12; botanicals header 30→20px; ritual accent →`#e6cfca`.
- **Collection:** card name/price left-aligned to match Figma (higher-specificity scoped CSS).

---

## 🔖 RESUME HERE — session handoff (read first)

**Project:** Seva on Broadcast theme "Good Manners – Sandpit" (id `148165886102`, unpublished dev). See `CLAUDE.md`. Australian English. **Nothing pushed to GitHub or the store — all local.**

**Preview:** `shopify theme dev --store 0qty0z-ey.myshopify.com` → `http://127.0.0.1:9292`. Homepage `/`, About `/pages/about`. If it shows "Upload Errors", **restart the dev server** (Ctrl+C + rerun) — it sticks after any transient error. **Never put `.bak`/temp files in theme folders** (assets/config/layout/sections/snippets/templates) — it breaks the dev server.

**Done & verified:**
- Fonts: Cyan headings (self-hosted `assets/cyan-regular.woff2/.woff`) + DM Sans body; colour schemes `scheme-blush` (#e6cfca) + `scheme-forest` (#182e21). In `config/settings_data.json` + `snippets/head.liquid`.
- Header transparent over hero, logo-left, white wordmark, forest-green free-shipping bar. Footer forest-green, 4 columns + "Return to ritual" newsletter. (`sections/group-header.json` / `group-footer.json`.)
- **Homepage** `templates/index.json` — 15 sections, matches Figma.
- **About** `templates/page.about.json` — 11 bands, renders at `/pages/about` (page's Theme template = `about`).
- Custom sections built: `section-ritual-highlight`, `section-ritual-steps` (pinned-scroll timeline), `section-visible-results`, `section-rooted-ritual` (video slider), `section-collection-tiles`.

**Next up:**
- Build 3 pages — specs in `figma-exports/page-specs.json`: **Formulation/Ingredients, FAQ, Contact** (all "final"). **Collection + Product** are WIP Shopify template pages (need real products/collections — hold).
- ⚠️ CONFIRM with Eliza: is Figma node `171:7828` the **Ingredients** or **Formulation** page? Its hero reads "FORMULATION".
- Images: pull Figma comps into `figma-exports/`; Eliza uploads to Shopify Files. Menus / products / page-template assignments are admin tasks.

**Verify loop:** pull each band from Figma directly (get_screenshot / get_design_context on the node) + inspect the rendered DOM, iterate until it matches. Figma file key `oFg9tSu6NxNa4I39nGpfuu`; node IDs in `Figma-Node-Map.md`.

---

## ✅ Needs you (morning actions)

These are the things I couldn't do without store access. Quick to knock out:

1. **Upload the Figma images** in `figma-exports/` to Shopify (Content → Files), then either pick them in the theme editor or tell me the filenames and I'll wire them in code.
2. **Set the transparent-header logo:** upload `figma-exports/seva-wordmark-white.png`, then in the theme editor → Header → set it as the transparent logo (the "SEVA." wordmark is currently dark and hard to see over the hero). *[see Header below]*
3. **Swap the hero photo:** upload `figma-exports/hero-desktop.png` (the floral-hair shot) and select it in the hero slide, replacing the oil-bottle placeholder.
4. **Confirm hero button links:** Shop → `/collections/all`, Discover Seva → `/pages/about-us-1`. Change if wrong.
5. **Decision — Black Friday announcement bar:** the dark "Black Friday Now Live" bar at the very top is **not in the Figma**. I left it in place rather than delete a live promo. Tell me if you want it removed to match the design.

---

## Changes so far

### Foundations (fonts + colour)
- Body/nav/subheading/buttons → **DM Sans**; headings → **Cyan** (self-hosted `assets/cyan-regular.woff2/.woff`). Letter-spacing zeroed, heading sizes set to the Figma ramp (H1 50 / H2 30 / H3 20 / H4 15).
- Added two colour schemes: **Blush** (`#e6cfca`) and **Forest Green** (`#182e21`).
- Files: `config/settings_data.json`, `snippets/head.liquid`.

### Band 1 — Hero ✅
- Heading → "BEAUTY YOU CAN FEEL IN YOUR BODY." (uppercase, Cyan, XL). Sub-line + two cream **outline** buttons side by side (Shop · Discover Seva) via a `_group-buttons` block. Height set to 750px to match Figma. Kept placeholder photo (real one in `figma-exports/`).

### Band 2 — Marquee ✅
- Scrolling text → "A SACRED ACT OF SELF-CARE" on the light cream scheme.

### Header — transparent ✅ (logo pending)
- `sections/group-header.json`: `transparent_home` → true, so the nav sits transparent over the hero (matches Figma). Nav links/icons already cream. **Wordmark still needs the white version uploaded** (see Needs-you #2).

---

## ⚠️ Important finding — hybrid homepage

The current homepage mixes **real Seva haircare sections** with **leftover jewellery-brand demo sections** that were never replaced. The jewellery leftovers (not in the Figma) are:

- `text-with-products` — "Modern heirlooms elegant treasures"
- `columns` — "Made-To-Order Jewelery / Sculpted Light"
- `double` — "Trends & Tradition"
- `tab-collections` — "Exceptional Pieces"
- `video` — "Behind the Brilliance"
- `press-logos` — jewellery quotes ("Sustainable luxury…jewelry")
- `collections-list-hover`, `section-product` — jewellery-oriented

My plan: keep and Figma-align the Seva sections, **disable** the jewellery leftovers (disabled, not deleted — they stay in the file as backup), and set the final section order to follow the Figma. Anything I'm unsure about I'll flag here rather than guess.

---

## Why the rest is spec'd, not fully built

Almost every remaining Figma band is a **full-bleed photo band** with overlay text (Find Your Ritual, OILS/TOOLS, Make Haircare a Ritual). Those can't be built correctly until the images live in Shopify Files — which only you can upload. And the current sections don't map 1:1 to the Figma, so guessing mappings blind risks a mess. So overnight I: locked in the structural wins, pulled every key image, and wrote the exact per-band spec below. In the morning, once you've uploaded the images, assembling these is fast and accurate.

**Images pulled to `figma-exports/`:** `hero-desktop`, `seva-wordmark-white`, `hair-strengthening-oil`, `make-haircare-a-ritual`, `find-your-ritual-banner`, `oils-tile`, `tools-tile`. Still to pull (trivial, node IDs noted): the intro "back of woman" image (`171:6946`), two-image band (`171:6983`), gallery (`171:6988/6989`), rooted-in-ritual (`171:7018/7019`).

---

## Exact per-band spec (from Figma, verbatim copy)

All heading/body text colour on cream/blush bands is **forest green `#182e21`**. Headings = Cyan; body = DM Sans.

**Band 3 — Intro statement** · centred, cream scheme
> "Rooted in ancestral Indian wisdom and refined for modern self-care, SEVA transforms everyday beauty routines into grounding rituals of restoration."

**Band 4 — The Formulation** · image + text, **blush** scheme, product image = `hair-strengthening-oil.jpg`
- Eyebrow: "The Formulation"
- Heading (H2, uppercase): "The original way to care for your hair, refined for modern routines."
- Body: "The traditions behind our Hair Oil were gifted to us through our founder's ancestral roots in India. We've honoured those ancestral rituals by refining them for modern haircare, creating a lightweight formula that supports stronger hair while bringing a moment of calm into your routine.

Powered by traditional hair-strengthening botanicals and calming ingredients, it nourishes the scalp, leaves hair soft and glossy, and surrounds every ritual with a luxurious scent that lingers."
- Button: "Learn More" (outline)
- Product caption elsewhere: "Hair Strengthening Oil"

**Band — Make Haircare a Ritual** · full green nature image, image = `make-haircare-a-ritual.jpg`
- Heading (H2, uppercase, cream over image): "Make haircare a ritual."

**Band — Find Your Ritual** · full-bleed floral banner, cream overlay text, image = `find-your-ritual-banner.jpg`
- Heading (H1, uppercase): "Find Your Ritual"
- Body: "Your scalp is constantly responding to stress, seasons, lifestyle shifts, and the rhythms of everyday life. This personalized ritual experience helps uncover what your scalp needs most right now, so you can create a more intentional path to nourishment, balance, and restoration."
- Button: "Take the Quiz"

**Band — 3-column feature / reviews** · cream. Heading seen: "Ayurvedic Ingredients. Visible Results." (rest of column copy still to pull → `171:7014`–`7075` cluster)

**Band — OILS / TOOLS split** · two image tiles, cream overlay text
- Tile 1: image `oils-tile.jpg`, label "OILS"
- Tile 2: image `tools-tile.jpg`, label "TOOLS"

**Band — Cultural Sustainability** · already present as `section-rich-text` with correct copy; just needs colour aligned to Figma.

**Bands still to pull copy for:** the "rooted in ritual" 3-image band, the gallery grid, the blog/"The Edit" row, and the Instagram grid + newsletter wording.

---

## Recommended final section order (Figma)

hero → marquee → intro statement → The Formulation → product/two-image → Make Haircare a Ritual → Find Your Ritual → 3-col reviews → gallery → OILS/TOOLS → Cultural Sustainability → The Edit (blog) → Instagram grid + newsletter → footer

The Seva-appropriate existing sections to reuse for these: `custom-content`, `multicolumn`, `rich-text` (Cultural Sustainability), `look` (gallery), `text-row` (Made in India icon row), `rich-text` (Follow us / Instagram). I did **not** overwrite their copy yet, to avoid mis-mapping — we'll place each with you in the morning.

---

## Status at end of night

**Built & verified in the live preview:**
- Hero — verbatim (uppercase Cyan heading, DM Sans sub, two cream outline buttons side by side, 750px, transparent header over it).
- Marquee — "A SACRED ACT OF SELF-CARE" on cream.
- Transparent header — on (wordmark needs the white version, see Needs-you #2).
- Jewellery leftovers — disabled, so the page reads as Seva top to bottom.

**Prepared for the morning (needs your uploads + a couple of confirms):**
- All key band images in `figma-exports/`.
- Exact copy/colour/button spec for every remaining band (above).

**Note:** `figma-exports/` and this `BUILD-NOTES.md` live at the repo root — Shopify ignores them (not theme folders), so they won't touch the theme. A temporary `templates/index.json.bak` I made briefly broke the dev-server sync; I removed it. If the preview ever shows an "Upload Errors" card, it's a stray non-`.liquid` file in a theme folder — tell me and I'll clear it.

## Morning checklist (quick)
1. Upload `figma-exports/*` to Content → Files.
2. Set transparent-header logo = `seva-wordmark-white.png`; set hero image = `hero-desktop.png`.
3. Confirm hero links (Shop, Discover Seva) + decide on the Black Friday bar.
4. Then I'll assemble the remaining bands (The Formulation, Make Haircare a Ritual, Find Your Ritual, OILS/TOOLS, Cultural Sustainability, gallery, newsletter) from the spec — fast, now that images exist.

## Batch 1 (built from Eliza's Figma screenshots, in Figma order)

- **The Formulation** ✅ `section-double`, text-left on cream/greige + floral-braid image right, "Learn More". **Needs `the-formulation.jpg` uploaded to Files** (it's in `figma-exports/`; placeholder until then).
- **Make Haircare a Ritual** ✅ NEW custom section `section-ritual-steps.liquid` — image left + Apply/Ground/Restore timeline + "Explore the Ritual". **Pinned scrollytelling:** the section pins in the viewport and the line fills / dots + text reveal as you scroll through it, then releases. "Scroll length" slider (100–400vh, default 260) controls how long it pins. rAF-throttled; mobile drops the pin; respects `prefers-reduced-motion`. Verified: pins (sticky top 0), progress 0→1, steps activate progressively. Uses `make-haircare-a-ritual.jpg`.
- **Rooted in Ritual** ✅ reconfigured the existing `video-carousel` (kept its 7 real Seva videos) — heading + body + blush background. Note: no eyebrow field for "Seva + You"; swap videos if you want specific ones.
- **Image aspect fix:** Broadcast's `image_tag` fights CSS `aspect-ratio` on `<img>`; fixed by putting the ratio on the media container in both custom sections.

## Batch 2 (Figma order, after Rooted in Ritual)

- **Visible Results** ✅ NEW custom section `section-visible-results.liquid` — heading + 3 review cards (image, ★ rating, quote, name). **Placeholders**: quotes/names are `[…]` and images blank — add real reviews (or wire Judge.me) + before/after images.
- **Find Your Ritual** ✅ full-bleed banner (`section-slideshow-nested`, centred), uses `find-your-ritual-banner.jpg`, heading + scalp copy + "Take the Quiz". **Set the quiz link** (left blank). Note: used AU "personalised" (Figma had US "personalized") per house style — say if you want it verbatim.
- **A Sacred Act of Self-Care (About Seva)** ✅ `section-double`, image left / text right, "Learn More". **Needs `about-seva.jpg`** (the eye/earring shot) — placeholder until uploaded.
- **Cultural Sustainability** ✅ reconfigured the existing rich-text → centred, blush, heading + "Learn More" (removed old background image).

## Batch 3 + QA pass

- **OILS / TOOLS** ✅ NEW custom `section-collection-tiles.liquid` — two image tiles, centred overlay labels, link to collections.
- **Footer** ✅ rebuilt (`sections/group-footer.json`): forest-green (scheme-forest), white SEVA wordmark, 4 columns (Shop / Discover / Housekeeping / Follow), "Return to ritual." newsletter. **Column links need menus** created in admin → Online Store → Navigation (handles `footer-shop`, `footer-discover`, `footer-housekeeping`, `footer-follow`).
- **Marquee fixed** ✅ — was "A Sacred Act…" repeated in Cyan serif; now the bullet-separated taglines (Ritual-Led Self-Care • Scalp-First Haircare • …) in DM Sans 15px, matching Figma.
- **Rooted in Ritual rebuilt** ✅ NEW custom `section-rooted-ritual.liquid` (replaced the reused video-carousel, which couldn't match): blush panel, text-left (Seva + You / heading / body / ‹ › + "1/4"), 2-up video slider right, click-to-play. Verified: 2-col, text-left, slider advances, pagination correct. Keeps the 7 Seva videos.
- **Homepage reconciled to Figma order** — trimmed 9 non-Figma leftovers; now 15 sections. The Formulation moved off the pink blush to soft cream/greige.
- **Blog ("The Edit") intentionally skipped** — Eliza adding later.
- **Gotcha logged:** never leave `.bak` files in theme folders — the dev server rejects them and gets stuck (needs a `shopify theme dev` restart). Backups go to scratchpad only.

## About page (templates/page.about.json) — COMPLETE (11 bands)

Renders at `/pages/about` (page's Theme template = "about"). Bands: hero "ABOUT SEVA" · A Return to Ritual (dove mark) · marquee · Born from Roots (Our Story) · Beauty as an Act of Devotion · Inspired by… Hair Oiling Traditions (4-col icons) · Conscious Ingredients (blush) · Beauty that Restores (blush) · Find Your Ritual · OILS/TOOLS · @sevabeautyau. Blog band skipped (like homepage). Reuses homepage sections. **Images are placeholders** except Find Your Ritual + OILS/TOOLS (reused from Files); dove mark pulled to `figma-exports/seva-mark.png`.
**About needs:** upload ~9 About photos + 4 feature icons + IG images; tune blush shades; real IG grid; set Learn More / Take the Quiz / collection links.

## Parallel analysis workflow (5 pages)
Ran 5 agents → build specs (saved in task output). Status: **Ingredients (final — but hero says "FORMULATION"; confirm page identity), FAQ (final), Contact (final)**; Collection + Product = **wip** (Shopify template pages, depend on product/collection data). Specs list bands, reuse-section map, images + admin per page.

## Band-by-band log

- **Hero image + white wordmark** ✅ wired & verified. Hero photo = `hero-desktop.png`; header `transparent_logo` = `seva-wordmark-white.png`. Wordmark now reads white over the hero. (Hero mobile image still the old launch shot — swap when the mobile crop is ready.)
- **Band 4 — The Ritual (collection highlight)** ✅ built as a NEW custom section `sections/section-ritual-highlight.liquid`. Pickable product cards (badge, price + editable subscription/one-time notes, editable bullets, "Shop the Ritual") + a blush "Complete the Ritual" promo panel. Content verified in DOM. **Products not yet picked** — cards show display names + placeholder images until the two products are selected (or handles wired).
- **My earlier "The Formulation" attempt was wrong** — it was a mis-assembled image+text panel; that band is actually a collection highlight. Deleted the misbuild. The real "The Formulation" band (soft-blush text panel, separate/later in the page) is still TO DO.
- **25-section limit:** deleted the disabled jewellery leftovers (`text-with-products`, `columns`, `double`, `tab-collections`, `video`, `press-logos`, `collections-list-hover`, `product`) — recoverable from git. Homepage now 18 sections.
- **Method change:** building band-by-band from the actual Figma band view (not loose layers), confirming with Eliza before each.
- **Band 3 — Intro statement** ✅ built & verified. New `section-rich-text` ("Intro statement") after the marquee: heading "A SACRED ACT OF SELF-CARE." + paragraph, centred on cream.

## Session — Ingredients, FAQ & Contact pages (built while you slept)

Built all three remaining "final/ready" pages **entirely from existing Broadcast sections** — no new custom section needed (the theme already ships `section-accordion-group`). Everything is schema-driven, Australian English, `scheme-1` cream / `scheme-blush` #e6cfca / `scheme-forest` green for cohesion with the rest of the site. Modelled on the proven `page.about.json` assembly. **Nothing committed or pushed — all local for your review.** All three files validated as clean JSON.

**Files:**
- `templates/page.ingredients.json` — NEW (8 bands): hero "FORMULATION" → intro statement → Beauty panel (cream, text-left/image-right) → Trust panel (blush rose, image-left/text-right) → 11-tile ingredient grid (`section-multicolumn` image blocks, 4-up, buttons off) → Clean panel (cream, text-left/image-right) → "A Sacred Act of Self-Care" About CTA → @sevabeautyau. Panels match the Figma alternation (only Trust is rose). Remaining cosmetic gaps vs Figma: the grid's final row of 3 isn't force-centred, and the Clean image isn't arch-masked (both need custom CSS on shared sections — left for later).
- `templates/page.faq.json` — REWORKED into the 3 Figma categories: hero → **Product & Ritual** (10 Qs) → **Orders & Shipping** (4) → **Returns & Support** (4) → "Still Have Questions?" CTA → @sevabeautyau. Kept your existing hand-written answers where you had them; pulled the new questions' answers **verbatim from Figma** (how to use, how long to leave, overnight, all hair types, non-toxic, damaged order, change/cancel). Category titles are centred `section-rich-text` headings sitting above each accordion (the accordion block heading renders left-aligned). Fixed the Figma typo "Always was thoroughly" → "wash thoroughly", and added real `mailto:` hrefs to the support email links.
- `templates/page.contact.json` — REWORKED to match Figma: hero "CONTACT US" → "WE WOULD LOVE TO HEAR FROM YOU" intro → contact form (Full Name / Email* / Phone Number / Message / Send) → "We may have already answered your question" FAQ promo (`section-double`, links to /pages/faq) → @sevabeautyau. Removed the old placeholder form copy + disabled sections.

**⚠️ Confirm / tweak (quick):**
1. **Ingredients hero says "FORMULATION"** (verbatim from Figma) though you chose the *Ingredients* handle. One-line editor change if you'd rather it read "INGREDIENTS".
2. **FAQ shipping answer** keeps your existing wording ("free standard shipping within Australia"). The Figma's newer version says "standard shipping rates apply" (not free) — left yours per your choice; flag if the free-shipping line is out of date.

**Morning admin (only you can do — needs store access):**
1. Create three Pages in admin (Online Store → Pages) and assign templates: **Ingredients** → `page.ingredients`, **FAQ** → `page.faq`, **Contact** → `page.contact`. Point the footer Discover → Formulation/FAQ links + Contact link at them.
2. Upload page images to Content → Files, then pick them in the theme editor (all image slots left blank/placeholder): Ingredients — hero (dropper on scalp), Beauty (gold sari/lotus), Trust (oil on leaf), Clean (arch-crop parting), About-CTA (lily-pad profile), 11 ingredient squares, IG row; FAQ — hero (palm frond/hand), CTA image, IG row; Contact — hero (ROZ comb), FAQ-promo image, IG row.
3. Instagram rows are heading-only for now (matches About) — wire a real IG grid/app later.
4. Confirm contact-form submissions route to the right inbox (Settings → Notifications).
5. **Not built:** Formulation/Ingredients "arch-masked" image on the Clean panel (would need custom CSS on the shared `section-double` — skipped to avoid touching a global section; note for later). Last row of the ingredient grid isn't force-centred (native wrap left-aligns the final 3 tiles) — cosmetic, flag if you want it centred.
6. Still WIP (need product/collection data): **Collection (Best Sellers)** + **Product (Hair Strengthening Oil)** templates — specs in `figma-exports/page-specs.json`.
