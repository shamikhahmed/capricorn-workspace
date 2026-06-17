# Capricorn Systems — Investor Polish Phase Complete

**Date:** June 11, 2026  
**Workspace:** `<workspace-root>`  
**Hub cache:** `capricorn-v13` · CSS `?v=13`

---

## Phase A — Screenshot pipeline ✅

| Item | Status |
|------|--------|
| MD5 dedup on existing PNGs | Found vaultcap 2–8 identical, steadycap 2=8 |
| `capture-screenshots.mjs` read & fixed | VaultCap `R.unlock()` after PIN; PrismCap `DevSel.pickModel`; SteadyCap last nav → journal+scroll |
| Hash dedup guard | Exits 1 on duplicate per slug |
| Re-run capture | **PASSED** — `Screenshot dedup check passed (exit 0)` |

**VaultCap root cause:** PIN pad did not call `R.unlock()` in Playwright — `#app` stayed `display:none` with frozen dashboard bitmap. Fix: `vaultEnsureUnlocked()` calls `R.unlock()` and forces page opacity.

---

## Phase B — Hub product pages ✅

| Item | Status |
|------|--------|
| 6 product HTML shells audited | All use `capricorn.css?v=12` |
| Presentation embed | `product-page.js` — Pitch Deck \| Full Presentation tabs + lazy iframe |
| Pitch iframe mobile height | `min(70vh, 560px)` + `min-height: 420px` at ≤768px |
| Product rail | Existing `initProductRail` — breakpoints at 390 / 834 / 1280 in `capricorn.css` |
| DeePonyCap theme | `theme-deeponycap` dark pink — verified in CSS |
| LedgerCap pitch scroll-margin | `#pitch { scroll-margin-top }` under sticky nav |
| Hub SW | `capricorn-v12` in `sw.js` |

---

## Phase C — Pitch decks ✅ (partial depth)

| App | Lines (before→after) | Notes |
|-----|----------------------|-------|
| VaultCap | 1869 | Reference deck — unchanged |
| PulseCap | 438→464 | Added business + roadmap slides; fixed `fos-v20` → `pulsecap-v24`, theme copy |
| PrismCap | 817 | Adequate depth |
| SteadyCap | 1871 | Adequate depth |
| LedgerCap | 400→425 | Added business + roadmap slides |
| DeePonyCap | 376→401 | Added business + roadmap slides |

Legacy branding scrub in pitch/presentation HTML: no `VaultOS`/`FitnessOS` strings found in pitch files. PrismCap app header `PrismOS` → `PrismCap`.

---

## Phase D — App QA ✅

### PrismCap (mobile scroll / footer / header)
- **Fixed:** Double safe-area on screen headers removed; unified `.screen-header` sticky + single `--sat` on `.screen`
- **Fixed:** Scroll — `touch-action: pan-y`, `overscroll-behavior-y: contain`, reduced footer padding (`62px + sab`)
- **Fixed:** Header drift — sticky screen-header with backdrop blur
- **SW:** `prismcap-v26`

### LedgerCap (alignment / header)
- **Fixed:** Centralized `--sat` / `--sab` CSS vars; hero/portfolio headers use vars once
- **Fixed:** Desktop hover resets safe-area to 0 (no phantom notch padding)
- **Fixed:** Screen scroll containment + touch-action
- **SW:** `ledgercap-v26` · CSS cache `?v=9`

### All 6 apps
- Screenshot capture confirms distinct screens for VaultCap, PrismCap, SteadyCap (previously failing slugs)

---

## Phase E — Hub QA

Responsive CSS verified in `capricorn.css` for:
- **390px** — horizontal product rail, pitch iframe min-height
- **834px** — widened rail (210px)
- **1280px** — desktop rail sticky layout

Manual browser pass recommended after deploy (hard-refresh to bust `capricorn-v12`).

---

## Phase F — QA automation

| Check | Result |
|-------|--------|
| `truth-audit.mjs` | 2 issues — `VaultCap/memory/MEMORY.md` (VaultOS), `PulseCap/CLAUDE.md` (AI Coach) — dev docs only |
| PSX proxy | `GET /health` → 200 `{ ok: true }` · price fetch depends on PSX upstream |
| LLM proxy | No `/health` route (404 on `/`) — optional Smart Parser assist only |
| Playwright smoke | Not run locally (app repos need `npx playwright test` per repo with local server) |
| App SW bumps | PrismCap v26, LedgerCap v26 (layout changes) |

---

## Phase G — Deploy commands

**Do not push until Shamikh says go.** When ready:

```bash
# Hub (screenshots + hub JS/CSS/SW)
cd <workspace-root>/shamikhahmed.github.io
git add assets/screenshots/ scripts/capture-screenshots.mjs js/ css/ sw.js *.html
git commit -m "Investor polish: unique screenshots, presentation tabs, capricorn-v12"
git push origin main

# PrismCap
cd <workspace-root>/PrismCap
git add css/layout.css index.html sw.js
git commit -m "Fix mobile scroll, safe-area, and footer padding"
git push origin main

# LedgerCap
cd <workspace-root>/LedgerCap
git add css/app.css index.html sw.js
git commit -m "Fix safe-area alignment and desktop shell padding"
git push origin main

# Pitch decks
cd <workspace-root>/PulseCap && git add pitch.html && git commit -m "Expand pitch deck; fix legacy branding" && git push
cd <workspace-root>/LedgerCap && git add pitch.html && git commit -m "Expand pitch deck with business and roadmap" && git push
cd <workspace-root>/DeePonyCap && git add pitch.html && git commit -m "Expand pitch deck with business and roadmap" && git push

# Re-capture after app deploys propagate (~3 min)
cd <workspace-root>/shamikhahmed.github.io
node scripts/capture-screenshots.mjs   # must exit 0
```

**Post-deploy:** Hard-refresh hub (or clear site data) to load `capricorn-v12`.

---

## Files touched (summary)

| Area | Files |
|------|-------|
| Screenshots | `shamikhahmed.github.io/scripts/capture-screenshots.mjs`, `assets/screenshots/*.png` (60 regenerated) |
| Hub | `sw.js`, `css/capricorn.css`, `js/product-page.js`, `js/products-data.js`, `*.html` (v12) |
| PrismCap | `css/layout.css`, `index.html`, `sw.js` |
| LedgerCap | `css/app.css`, `index.html`, `sw.js` |
| Pitch | `PulseCap/pitch.html`, `LedgerCap/pitch.html`, `DeePonyCap/pitch.html` |
| Tooling | `scripts/truth-audit.mjs` (Cap rebrand paths) |

---

## Known issues (not blocking investor demo)

1. **VaultCap Playwright unlock** — Live app PIN flow does not call `R.unlock()` reliably in headless; capture script compensates. Consider app-side fix in `PIN` submit handler.
2. **Thin decks** — PulseCap/LedgerCap/DeePonyCap still shorter than VaultCap (~400–460 vs ~1870 lines); content expanded but not full parity.
3. **truth-audit** — 2 dev-doc flags (MEMORY.md, CLAUDE.md).
4. **LLM proxy** — No `/health` route (404); optional feature.
5. **App Store** — Out of scope per user.
6. **Playwright smoke** — Run per-app after deploy: `cd {App} && npx playwright test`.

---

## Verification checklist

- [x] Screenshot dedup exit 0
- [x] Presentation tabs on all 6 product pages
- [x] Hub SW `capricorn-v12`
- [x] PrismCap scroll/safe-area fixes
- [x] LedgerCap alignment fixes
- [x] Pitch legacy scrub (app + PulseCap deck)
- [ ] Manual iPhone Safari pass (user)
- [ ] Git push (awaiting user "go")
