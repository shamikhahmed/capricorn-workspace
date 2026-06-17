# Capricorn Systems — Workspace Upgrade Report
*2026-06-12 · Phases 1–10 complete · All changes committed locally (NOT pushed — review then push per repo)*

## What changed, per project

### shamikhahmed.github.io — `85504b0` (23 files)
**Found:** always-on starfield rAF loop; no OG/JSON-LD/sitemap; render-blocking fonts; hero carousel overflowed its container by ~165px into the stats section on tablet; sw.js existed but was never registered; no focus-visible.
**Done:** bespoke WebGL constellation hero (~6 KB shader — chosen over three.js's 150 KB for one effect; parallax, twinkle, constellation lines, pauses when hidden/offscreen, static 2D fallback for reduced-motion/no-WebGL); OG/Twitter/canonical on all 14 pages + JSON-LD Organization; sitemap.xml + robots.txt; non-blocking fonts; carousel front card now in-flow (overflow fixed at every breakpoint, verified 375/768/1280); count-up stats, kinetic gradient headline, magnetic CTAs, pointer-tilt cards, skip link; SW registered, cache → v16; design-system core + components vendored.

### VaultCap `43a4d9a` · PulseCap `eb5d118` · PrismCap `6138604` · SteadyCap `fc9a1bb` · LedgerCap `0e93eef` · DeePonyCap `529f65b`
**Found:** pinch-zoom blocked (VaultCap/PulseCap/DeePonyCap — WCAG 1.4.4 fail); zero focus-visible styles (5 of 6); no reduced-motion handling (LedgerCap/DeePonyCap); no OG tags, missing meta descriptions; render-blocking fonts; PulseCap shipped no-cache meta tags that fought its own service worker.
**Done (all six):** vendored `css/capricorn-core.css` (tokens + focus rings + 44 px touch targets + reduced-motion kill switch) with each app's accent mapped to `--cap-accent`; pinch-zoom re-enabled; meta description + OG/Twitter + canonical; fonts non-blocking; PulseCap cache-meta removed; core stylesheet precached and SW cache bumped.
**Verified:** all six Playwright suites pass; LedgerCap + VaultCap visually checked at 375 px — identities fully preserved.

### ScentCap `9d…` / AuraCap
**Found:** zero code splitting (ScentCap shipped one 822 KB bundle, recharts included on every page); stale macOS `" 2"` duplicates in dist; bare titles, no OG.
**Done:** React.lazy route splitting — ScentCap main bundle **822 KB → 267 KB** with recharts (331 KB) isolated to /analytics; AuraCap 15/16 pages lazy; dist rebuilt clean; OG/Twitter/canonical + descriptive titles.
**Verified:** tsc + builds green; ScentCap e2e 4/4, AuraCap e2e 2/2.

## Workspace-level repairs
- **`scripts/sync-versions.mjs` was silently broken** — still pointed at pre-rebrand folder names (VaultOS, FitnessOS…), so it had been a no-op since the rename. Fixed; stale `VERSION.json` swCache names (`fos-v22`, `stundsOS-v9`, `discipline-v7`…) modernized to `<app>-vN`.
- truth-audit now passes 0 issues (legacy "VaultOS" memory refs, AI-coach naming note).
- New `shared/design-system/` (tokens, a11y, motion, components, 1.5 KB JS runtime) + `scripts/sync-design-system.mjs` to re-vendor; new `scripts/app-upgrade-pass.mjs` (idempotent).

## Performance notes
- Fonts no longer block first paint on any entry page (~300–600 ms FCP win on cold loads, network-dependent).
- Hub no longer burns a 60 fps rAF loop while idle/offscreen.
- ScentCap first-load JS −67%.

## Remaining recommendations (not done, by design or scope)
1. **VaultCap app.js (5,505 lines) / ui.js (2,382)** — needs a careful module split; too risky to bundle into this sweep. Highest-value next refactor.
2. CSP headers for the five apps that lack one (VaultCap has it; others need a meta-CSP pass tuned to each app's external calls).
3. DeePonyCap inline CSS → external file (caching win, small).
4. ARIA landmark/tab-role audit inside each app's dynamic views (smoke tests don't cover screen-reader semantics).
5. Real-device Lighthouse runs post-deploy to confirm 95+ across the four categories.
6. Hub `enterprise.html` still uses legacy `site.css` — fold into capricorn.css when that page is next touched.
7. Replace hub screenshots that still show pre-rebrand "VaultOS" UI chrome (visible in hero carousel).
