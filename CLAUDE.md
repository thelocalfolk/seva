# Seva — Website Build (The Local Folk)

Project brief and working rules for the Seva Shopify build. Read this at the start of every session before touching any code.

---

## The project

- **Client:** Seva
- **Store:** `0qty0z-ey.myshopify.com`
- **Theme:** Broadcast — working/staging theme is **`seva/main`** (unpublished, **GitHub-connected** to `thelocalfolk/seva` branch `main`). This is the single source of truth: a `git push` to `main` auto-syncs into `seva/main`. The old "Good Manners – Sandpit" theme (id `148165886102`) is **retired** — do not push to it. Neither is the live/published theme.
- **GitHub repo:** `https://github.com/thelocalfolk/seva` (branch `main`)
- **Figma:** Seva | Website — https://www.figma.com/design/oFg9tSu6NxNa4I39nGpfuu/Seva-%7C-Website (file key `oFg9tSu6NxNa4I39nGpfuu`)

---

## The golden rule — deployment

**GitHub `main` auto-syncs to the unpublished dev/staging theme `seva/main` ONLY. It is NEVER connected to the live/published theme.**

- The deploy flow is: edit local files → `git commit`/`push` to `main` (with approval) → `seva/main` updates automatically. **No manual `shopify theme push` needed** (and don't push to the retired Sandpit theme).
- Never run `shopify theme push` to the **live/published** theme, and never connect this repo/branch to the published theme via an auto-sync integration.
- **Publishing `seva/main` → live is Eliza's manual step**, done herself through Shopify. Claude never publishes.
- Never commit or push to GitHub without showing Eliza the changed files and the commit message first, and getting approval.
- Git commands need Eliza's logins/network; Claude can stage + commit locally, but pushes go through her machine.

---

## Broadcast theme notes

Seva is on **Broadcast**, not Horizon — so the Horizon typography-snippet rules from the Bacii project do NOT apply here. Broadcast-specific things to remember (from the shopify-section-development skill):

- **Free shipping bar** is a snippet (`snippets/free-shipping.liquid`) rendered from `sections/cart-drawer.liquid`, passing `show_progress_bar` and `is_cart_drawer`. CSS for shared snippets lives in the matching CSS file (e.g. `free-shipping.css`) — add custom styles at the bottom.
- **Colour schemes** are applied via `block.settings.color_scheme` and can override custom backgrounds. To confirm CSS is loading, use `!important` temporarily then trace the conflict.
- **Cart re-renders** fire `cart:refresh` and `cart:updated` events on `document` — listen to both to re-init JS after the cart drawer updates. Confirm exact event names in `assets/cart.js`.
- Common Broadcast classes: `.drawer__message`, `.cart__message`, `.free-shipping`, `.free-shipping__progress-bar`.

Always read the actual theme file before assuming — Broadcast gets heavily customised.

---

## Working conventions

- **Read before writing.** Read the relevant theme files (`config/settings_schema.json`, a similar existing section, the main CSS file, related snippets) before generating any code. Match the theme's existing class-naming, CSS variables, and conventions — don't impose a generic style.
- **Schema-driven everything** — all copy, colours, images, spacing exposed as schema settings; nothing hardcoded. Every section needs a preset.
- **Scope all CSS** to the section with `#section-{{ section.id }}` or a unique class.
- **Mobile-first**, breakpoint typically `@media (max-width: 768px)`.
- **Australian English** everywhere: colour, customise, optimisation, behaviour.
- **Plain English** in chat, explain before doing, ask when unsure, no walls of bullet points.
- Kebab-case filenames; Title Case section names in schema.

---

## Git workflow

- Always tell Eliza which files changed before staging.
- Commit messages in plain English describing what changed and why.
- Show the commit message and wait for approval before pushing.
- Never push directly to GitHub without confirmation. Never run destructive commands without approval.

---

## Build status

**➡️ Current progress + how to resume: read `BUILD-NOTES.md` first (has a "RESUME HERE" section).**

- [x] Theme pulled from Seva store (Good Manners – Sandpit)
- [x] Git + GitHub repo connected (thelocalfolk/seva)
- [x] Figma design mapped (see `Figma-Node-Map.md`)
- [x] Homepage built to Figma (`templates/index.json`, 15 sections) + custom sections in `sections/`
- [x] About page built (`templates/page.about.json`, `/pages/about`)
- [x] Ingredients, FAQ, Contact pages built + Figma loop-checked
- [x] Privacy Policy + Terms of Service pages built (Figma-verbatim copy)
- [x] Product (Hair Oil, `product.hair-oil.json`) + Collection (Best Sellers, `collection.best-sellers.json`) templates built + loop-checked
- [x] All 9 designed pages loop-checked to Figma — see `BUILD-NOTES.md` (☀️ MORNING REPORT at top)
- [ ] Blog + Article — designed in Figma, deferred (Eliza handling); also a "The Blog" band on Homepage + About still to build
- [ ] Nothing pushed to GitHub/store yet — awaiting Eliza's review + her manual push
