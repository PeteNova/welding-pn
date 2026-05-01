# Changelog — Nowakowski TIG Welding Website

All notable changes to the site ([github.com/PeteNova/welding-pn](https://github.com/PeteNova/welding-pn)).

Format: [Keep a Changelog](https://keepachangelog.com/). Versioned by session date.

---

## [2026-05-01] — Session #1

First major iteration. Started from the GD Autocentre kit template, refactored
into Nowakowski TIG Welding identity, added i18n + Advisory section, removed
the Tweaks panel, and pushed initial repo to GitHub.

### Added
- PL / EN / DE language switcher in header — localStorage-backed (`welding-lang` key), default EN, native attribute-based i18n via `data-i18n` and `data-i18n-attr` keys with hierarchical lookup (`split('.').reduce(...)`).
- New `<section id="advisory">` block — 4 tiles (Consulting & Audits, Training & Mentoring, WPS Documentation, Welder Hire) in 4×1 grid with own H2 + intro, distinct background (`var(--bg-2)`), placed after Services. Adds `nav.advisory` link in header + footer.
- Tooltip on rate-banner phrase ("fixed fee locally" / "stała opłata" / "lokale Pauschale") — uses existing `[data-tip]` system, dotted underline + `cursor: help` indicator, content explains local zone covers Gloucester + Gloucestershire with exact amount agreed at quote stage.
- 8 hands-on welding services tiles in main `#services` grid: TIG — Aluminium / Stainless / Mild Steel, Custom Fabrication, Repairs & Restoration, Mobile Callout, Motorsport & Performance, Bespoke Metalwork.
- GitHub repo at [github.com/PeteNova/welding-pn](https://github.com/PeteNova/welding-pn) — public, `main` branch, `.gitignore` covering `.DS_Store`, `node_modules/`, `.vercel/`, IDE folders.

### Changed
- Hero headline: from "Quality Welds. / In Expert Hands." to **"TIG Expert. / Steel · Stainless · Aluminium."** — italic-em on the brand word "Expert", smaller second line (font-size 0.55em) for materials list.
- About section heading: from "Honest welds. / Honest quotes." to **"Fachowość i / zdrowy rozsądek."** (PL) / **"Expertise and / common sense."** (EN) / **"Können und / Verstand."** (DE) — italic-em on second line.
- Services H2: italic emphasis moved to first line — **"Spoiny estetyczne / i konstrukcyjne."** (PL) / **"Show-quality / and structural welds."** (EN) / **"Ästhetisch / und tragend."** (DE).
- Hero background image swapped to TIG-specific welding photo (Pexels 9130189 — welder with TIG torch in dimly lit workshop, blue arc, minimal sparks). Replaces generic MIG-style spark photo.
- Brand SVG (header + footer): from "GD AUTOCENTRE / EST · 2015 · GLOUCESTER" to **"NOWAKOWSKI WELDING / TIG · ALU · STAINLESS · MILD STEEL"**. Wider viewBox (200→240) to accommodate longer text.
- Section numbering renumbered after Advisory insertion: Services 01, Advisory 02, Process 03, About 04, Pricing 05, Reviews 06, Location 07, Contact 08 — applied across all 3 languages.
- Default theme set to `dark` (was `auto`) — guarantees the white accent shows on first load.
- Light/dark accent locked via CSS: `--accent: #f5f5f2` (near-white) in dark mode, `--accent: #1a1b1c` (dark gray) in light mode. `--accent-contrast` flipped accordingly.
- Pricing rows: from "Interim Service / Full Service" (car-shop terms) to **"Minimum job / Hourly rate"** (welding-shop terms).
- Trust strip badges: from "10+ Years / 71+ Reviews / Female-Friendly / Performance" to **"TIG Specialist / Honest Quotes / Mobile Service / Clean Finish"**.
- Hero subtitle expanded: now mentions consulting (audits, equipment selection, weld-process optimization) alongside hands-on welding.
- Service form `<select>` options localized to TIG categories (TIG Alu / Stainless / Mild Steel / Custom Fab / Repair / Mobile / Motorsport / Bespoke / Other).
- Reviews section copy marked as placeholder (5 reviews with "TBA · Google Review" bylines) — flagged for replacement before launch in intro paragraph.
- Map iframe: from `153a Bristol Road, Gloucester GL1 5SY (GD Autocentre)` to `Gloucester UK (Nowakowski TIG Welding)` — neutral pending workshop address confirmation.
- Rate-banner copy clarified into three plain sentences: hourly rate / materials separately on invoice / mobile callout zones (fixed fee locally + per-mile by Google Maps beyond). All three languages.

### Fixed
- PL typo in services description: "fabryków" → "zakładów przemysłowych" (proper genitive plural + better B2B framing).

### Removed
- `editorial` and `cyber` theme variants — all CSS rules with `[data-variant="editorial"]` and `[data-variant="cyber"]` selectors stripped via Python script (109 blocks, 282 lines). `industrial` is the sole variant.
- Tweaks panel completely removed: gear-icon toggle button, settings panel HTML (variant/accent/density pickers), CSS for `.tweaks-toggle`, `#tweaks`, `.tw-*` classes including responsive overrides, JS module (`TWEAK_DEFAULTS`, `getTweaks`, `setTweaks`, `applyTweaks`, `toggleTweaks`, button handlers, edit-mode protocol postMessage), event listener on `#tweaksToggle`, and `tweaks.*` translation keys in all three languages.
- Static GD-specific identity strings throughout (`GD Autocentre Ltd`, `Gintaras Druskis`, `Gin`, `01452 422 405`, `+447894550082`, `info@gdautocentre.com`, `153a Bristol Road`, `GL1 5SY`, `Company No. 12205703`, `https://gd-autocentre.vercel.app`, Facebook URL `GDAutocentreLtd`) — replaced with Nowakowski TIG Welding equivalents or `TBA` placeholders.

### Internal
- i18n architecture (vanilla JS, no library): `TRANSLATIONS` object with `en` / `pl` / `de` blocks (~600 keys total), `setLang()` function iterating `[data-i18n]` and `[data-i18n-attr]` elements, hierarchical key lookup, HTML-aware (`innerHTML` if value contains `<`, else `textContent`). `<html lang>` and `body[data-lang]` updated on switch.
- localStorage keys: `welding-lang` (i18n) and `welding-tweaks-v2` (legacy, no longer written after Tweaks removal).
- Folder structure: `Welding-PN/Welding-PN-Website/` (public, in git) + `Welding-PN/data/` (private — growth-tracker, competitors, content-calendar, seo-audit, quote-templates, quote-log — never committed to public repo).
- Skill ecosystem (`~/.claude/skills/`): `welding-pn` (growth manager), `welding-pn-deploy` (GitHub + Vercel + Web3Forms + domain wizard), `welding-pn-automation` (Gmail draft + WhatsApp quote response), `welding-pn-update` (this finalizer skill — created in Session #1).
- Helper Python script `strip-variants.py` used to mechanically remove all `[data-variant="editorial|cyber"]` CSS rules with brace-balanced block detection (cleaned up after run).
