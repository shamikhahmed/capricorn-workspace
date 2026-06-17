# Capricorn Systems — Workspace Audit
*Generated 2026-06-12 · Phase 1 of the workspace upgrade*

## Inventory

| Project | Type | Stack | Size (app code) | Git |
|---|---|---|---|---|
| shamikhahmed.github.io | Company hub | Static HTML + vanilla JS/CSS | 3.7k lines | clean |
| VaultCap | Encrypted life vault PWA | Vanilla JS + Capacitor | ~1.1 MB JS, 47 files | clean |
| PulseCap | Performance OS PWA | Vanilla JS + Capacitor | ~1.0 MB JS, 39 files | clean |
| PrismCap | 38-game party hub PWA | Vanilla JS + Capacitor (Vite in devDeps, unused) | 456 KB JS | clean |
| SteadyCap | Recovery OS PWA | Vanilla JS + Capacitor | 260 KB JS | clean |
| LedgerCap | Wealth OS PWA | Vanilla JS + Capacitor | 212 KB JS | clean |
| DeePonyCap | MLP collector PWA | Vanilla JS + Capacitor | 60 KB JS, inline CSS | clean |
| ScentCap | Fragrance wardrobe | React 19 + Vite + Tailwind 4 + framer-motion | 44 src files | clean |
| AuraCap | Apple ecosystem studio | React 19 + Vite + Tailwind 4 + framer-motion | 54 src files | clean |
| CarApp | Reserved placeholder | — | empty | n/a |

All repos have clean working trees. TypeScript builds pass for ScentCap and AuraCap. Existing `truth-audit.mjs` reports 2 doc-naming issues (legacy "VaultOS" reference in VaultCap/memory, "AI Coach" naming note in PulseCap docs).

## Security

- ✅ No exposed secrets/API keys found (scanned for key patterns across all source).
- ✅ VaultCap ships a CSP meta tag; LLM calls go through a Cloudflare Worker proxy (no key in client).
- ⚠️ Only VaultCap has a CSP. The other five apps + hub have none.
- ⚠️ Hub renders product data via `innerHTML` from local JS data files — safe today (no user input) but fragile if data ever becomes remote.

## Accessibility (workspace-wide)

| Issue | Where | Severity |
|---|---|---|
| `user-scalable=no, maximum-scale=1` blocks pinch zoom (WCAG 1.4.4 fail) | VaultCap, PulseCap, DeePonyCap | High |
| No `:focus-visible` styles (keyboard users get no focus ring) | All except VaultCap (1 rule) | High |
| No `prefers-reduced-motion` handling | LedgerCap, DeePonyCap | Medium |
| Sparse ARIA on app shells (nav landmarks, tab roles) | All six Capricorn apps | Medium |

## SEO & metadata

- ❌ **No Open Graph / Twitter card tags anywhere** — sharing any product URL renders a bare link.
- ❌ **No JSON-LD structured data anywhere** (Organization, SoftwareApplication).
- ❌ Missing `<meta name="description">`: VaultCap, PulseCap, PrismCap, LedgerCap, DeePonyCap app shells.
- ❌ No canonical URLs, no sitemap.xml, no robots.txt on the hub.
- ⚠️ Bare `<title>` tags ("PrismCap", "PulseCap") — no descriptive suffix.

## Performance

- ⚠️ **Render-blocking Google Fonts** on every entry page (no `font-display` control beyond `display=swap`, no preload, two-host round trip before first paint).
- ⚠️ Hub starfield canvas runs `requestAnimationFrame` continuously — even when tab is idle or canvas is offscreen (static stars redrawn ~60fps; pure battery drain).
- ⚠️ PulseCap ships `Cache-Control: no-cache` **meta http-equiv tags** that fight its own service worker strategy.
- ⚠️ PrismCap carries Vite + TypeScript in devDependencies but is plain JS — dead tooling.
- ⚠️ No `loading="lazy"` discipline audit done per-image yet (hub carousel loads all product screenshots eagerly).
- ✅ All apps are SW-cached offline-first with versioned caches (v24–v27) — solid foundation.

## Code quality & architecture

- 🔴 **VaultCap `js/app.js` is 5,505 lines**; `ui.js` 2,382 — monolith risk for the flagship.
- 🟡 PulseCap better factored (modules/) but `workout.js` at 1,708 lines.
- 🟡 DeePonyCap has all CSS inline in `index.html` (~large `<style>` block) — no caching of styles.
- 🟡 Hub has two CSS files (`capricorn.css` used, `site.css` 608 lines — verify dead).
- 🟡 No shared anything: each app re-implements toasts, modals, focus traps, reveal observers. Intentional per-brand visuals, but primitives (motion curves, spacing scale, a11y helpers) should be shared.
- 🟡 `ScentCap/dist` and `AuraCap/dist` contain macOS `" 2"` duplicate artifacts (e.g. `index 2.html`, `sw 2.js`) — stale build output.

## UX & design observations

- Hub: strong identity (dark + gold, Bricolage Grotesque) and existing reveal/carousel system. Missing: scroll-storytelling depth, magnetic/hover physics, kinetic type, view-transitions between pages, and any 3D moment. The "By the numbers" and principles sections are static cards.
- Apps each have a deliberate distinct identity (this is a stated brand principle — preserve it).
- Micro-interaction coverage uneven: skeleton/empty/success states not consistently present in the vanilla apps.

## Priority fix list (maps to upgrade phases)

1. **A11y blockers**: remove `user-scalable=no`; add `:focus-visible` + reduced-motion everywhere.
2. **SEO layer**: descriptions, OG/Twitter, JSON-LD, canonical, sitemap/robots on hub.
3. **Perf**: font loading strategy, starfield idle behavior, PulseCap cache-meta removal, lazy media.
4. **Design system**: `/shared/design-system` tokens + motion + a11y primitives, consumed opt-in per app (per-app accents preserved).
5. **Hub**: award-level pass — WebGL constellation hero, scroll storytelling, magnetic CTAs, kinetic type.
6. **Apps**: CSS-first motion polish, state coverage (empty/loading/success), responsive sweep 320→2560.
7. **Cleanup**: dist `" 2"` artifacts, PrismCap dead devDeps, `site.css` dead-check, truth-audit naming fixes.
