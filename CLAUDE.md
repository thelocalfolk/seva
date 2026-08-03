# Seva — Website Build (The Local Folk)

Project brief and working rules for the Seva Shopify build. Read this at the start of every session before touching any code.

---

## The project

- **Client:** Seva
- **Store:** `0qty0z-ey.myshopify.com`
- **Theme:** Broadcast — working theme is **"Good Manners – Sandpit"** (theme id `148165886102`, an unpublished dev/sandbox theme)
- **GitHub repo:** `https://github.com/thelocalfolk/seva` (branch `main`)
- **Figma:** Seva | Website — https://www.figma.com/design/oFg9tSu6NxNa4I39nGpfuu/Seva-%7C-Website (file key `oFg9tSu6NxNa4I39nGpfuu`)

---

## The golden rule — deployment

**GitHub is version control and backup ONLY. It is never wired to auto-deploy to the live theme.**

- Never run `shopify theme push` to a live or published theme.
- Never connect this repo to the store's published theme via an auto-sync integration.
- Eliza pushes to the live theme herself, manually, through Shopify.
- Never commit or push to GitHub without showing Eliza the changed files and the commit message first, and getting approval.

Because the Seva store is not connected to Claude via the Shopify MCP, code moves between Shopify and this repo through GitHub and manual `shopify theme pull` / `git` steps that Eliza runs on her Mac (they need her logins + network).

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

- [x] Theme pulled from Seva store (Good Manners – Sandpit)
- [x] Git + GitHub repo connected (thelocalfolk/seva)
- [ ] Figma design mapped (see `Figma-Node-Map.md`)
- [ ] Homepage build plan
- [ ] Section builds
