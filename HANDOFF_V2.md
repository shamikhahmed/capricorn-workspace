# Capricorn — AI Handoff v2
*2026-06-12. All repos live at `~/Desktop/Projects/`. Rule for every task: commit locally per repo, never push — user reviews and pushes.*

---

## Master task list

| # | Task | Impact | Effort | Status |
|---|------|--------|--------|--------|
| 1 | Inner page redesign (about/sovereignty/solutions) | High | Medium | TODO |
| 2 | Re-capture stale product screenshots | High | Low (mechanical) | TODO |
| 3 | Nav active state (highlight current page) | Medium | Low | TODO |
| 4 | Custom 404 page | Medium | Low | TODO |
| 5 | In-app branding sweep (8 apps) | Medium | Medium | TODO |
| 6 | Page transitions (fade between pages) | Medium | Low | TODO |
| 7 | Scroll progress bar track | Low | Low | TODO |
| 8 | Principle cards — add small SVG icons | Low | Low | TODO |
| 9 | Footer — add Twitter/X + contact email | Low | Low | TODO |
| 10 | Higgsfield hero video | High | Manual (user only) | WAITING |
| 11 | VaultCap monolith split (js/app.js, 5505 lines) | Medium | High | TODO |
| 12 | Lighthouse audit (verify perf post-Three.js) | Info | Low | TODO |

---

## Workspace conventions (read before doing anything)

- **Never push** — commit locally only. User reviews and pushes.
- Design system source: `shared/design-system/` — never edit the vendored `capricorn-core.css` files inside each app. Run `node scripts/sync-design-system.mjs` to compile.
- SW cache versions: bump `const CACHE = 'capricorn-vN'` in `sw.js` whenever you change CSS/JS in the hub. Apps have their own `sw.js`.
- Hub pages use two CSS files: `css/capricorn.css` (all inner pages + product pages) and `css/home.css` (homepage only).
- Product page content is generated from `js/products-data.js` by `js/product-page.js`. Never edit the HTML of product pages directly.
- React apps (ScentCap, AuraCap) use Vite. Run `npm run build` after editing src files.
- Vanilla apps (VaultCap, PulseCap, PrismCap, SteadyCap, LedgerCap, DeePonyCap) have no build step — edit files directly.

---

## Task 1 — Inner page redesign
**Files:** `about.html`, `sovereignty.html`, `solutions.html`, `enterprise.html` in `shamikhahmed.github.io/`

**Context:** The homepage was fully rebuilt with GSAP+Lenis+Three.js. Inner pages use `css/capricorn.css` and `js/capricorn.js`. They have a floating pill nav (just fixed) but the page content is unstyled — no scroll reveal animations, weak typography hierarchy, no visual interest.

**What to do:**
1. Read `about.html`, `sovereignty.html`, `solutions.html` in full.
2. Add `data-reveal` attributes to section headings and lead paragraphs — the IntersectionObserver in `js/capricorn-motion.js` picks these up automatically (already loaded on all pages).
3. Add `class="cap-reveal"` to cards and list items where appropriate.
4. Rewrite the text content on each page to match the human, direct voice of the homepage — no corporate jargon. Short sentences. Same rules as the homepage copy.
5. For `about.html`: add a proper founder section with Shamikh Ahmed's name and the one-person company story.
6. For `sovereignty.html`: make the Device Sovereignty manifesto feel dramatic — large typography, each principle on its own row.
7. For `solutions.html`: clean up the investor/team pitch — bullet points of what Capricorn is, link to each product's pitch deck.
8. Do NOT change the nav HTML, footer HTML, or any `<link>`/`<script>` tags.
9. Bump `const CACHE` in `sw.js` by 1 after changes.

**Verify:** Open each page in a browser at 375px and 1280px. No horizontal overflow, text readable, reveals fire on scroll.

---

## Task 2 — Re-capture product screenshots
**Files:** `shamikhahmed.github.io/assets/screenshots/` (currently shows pre-rebrand "VaultOS"/"DisciplineOS" UI)

**Context:** The hub product showcase shows 8 screenshots. They're stale — wrong app names, wrong branding. Each app runs locally via a `serve` script.

**What to do:**
1. Read `scripts/capture-screenshots.mjs` to understand the capture flow.
2. For each app in `{VaultCap, PulseCap, PrismCap, SteadyCap, LedgerCap, DeePonyCap}`:
   - Run `npm run serve` (or check `package.json` for the serve command) in the app directory to start it locally.
   - Run the capture script against it.
   - Verify the resulting PNG shows the new app name (e.g. "VaultCap" not "VaultOS").
3. ScentCap and AuraCap: run `npm run dev` (Vite) then capture.
4. Copy new PNGs to `shamikhahmed.github.io/assets/screenshots/`.
5. Commit hub repo only.

---

## Task 3 — Nav active state
**Files:** `css/capricorn.css`, `js/capricorn.js`

**Context:** The floating pill nav has no visual indicator for the current page. All links look the same whether you're on about.html or sovereignty.html.

**What to do:**
1. In `js/capricorn.js`, after the nav scroll listener, add logic to match `window.location.pathname` to nav link `href` values and add class `is-current` to the matching `<a>`.
2. In `css/capricorn.css`, style `.nav-links a.is-current`: `opacity: 1; color: var(--gold);` — nothing heavy, just visible.
3. Same for `css/home.css` on the homepage (homepage nav links are Products, Principles, Sovereignty, About, Solutions — match against pathname).
4. Commit hub repo.

---

## Task 4 — Custom 404 page
**Files:** Create `shamikhahmed.github.io/404.html`

**Context:** GitHub Pages serves a generic error page on bad URLs. The site has a Three.js galaxy and premium branding — a custom 404 fits.

**What to do:**
1. Create `404.html` that reuses the hub's nav and footer HTML (copy from `index.html` lines 51–65 for nav, lines 197–210 for footer).
2. Link `css/capricorn-core.css` and `css/capricorn.css` (not home.css — no Three.js needed here).
3. Main content: big "404" in the footer-giant style (outlined text), a one-line message ("This page doesn't exist."), and a single CTA button back to `index.html`.
4. Add `js/capricorn.js` and `js/capricorn-motion.js` so nav toggle and reveals work.
5. Do NOT add Three.js or GSAP — keep it lightweight.
6. Commit hub repo.

---

## Task 5 — In-app branding sweep
**Scope:** 6 vanilla apps: VaultCap, PulseCap, PrismCap, SteadyCap, LedgerCap, DeePonyCap

**Context:** Each app received a new geometric mark (`icon.svg` in the app root). But in-app splash screens, About pages, and Settings screens still reference old emoji or the old logo path.

**What to do (per app):**
1. `grep -r "logo\|emoji\|🔐\|💪\|🎮\|🌿\|📊\|♡" --include="*.html" --include="*.js" <AppDir>/` to find old references.
2. Replace any `<img src="...logo...">` or emoji used as app icon with `<img src="icon.svg" alt="" width="48" height="48">` (adjust path depth as needed).
3. Do not change gameplay logic, data structures, or CSS variables.
4. Commit that app's repo only.

**Do one app at a time. Start with VaultCap.**

---

## Task 6 — Page transitions
**Files:** `js/capricorn.js`, `css/capricorn.css`

**Context:** Clicking between hub pages is a hard cut. A simple GSAP fade-out/in would feel premium.

**What to do:**
1. GSAP is already loaded on every hub page via `<script src="js/vendor/gsap.min.js">`.
2. In `js/capricorn.js`, add a click listener on all internal `<a>` tags that:
   - Calls `e.preventDefault()`
   - Runs `gsap.to(document.body, { opacity: 0, duration: 0.22, onComplete: () => location.href = href })`
3. On page load, fade in: `gsap.from(document.body, { opacity: 0, duration: 0.28, ease: 'power2.out' })`
4. Skip the transition for `target="_blank"`, hash-only links, and the current page.
5. In `css/capricorn.css`: add `body { opacity: 1; }` so there's no flash before GSAP runs.
6. Commit hub repo.

---

## Task 10 (manual — user only) — Higgsfield hero video
1. Log in to higgsfield.ai with your account.
2. Use the prompt in `shamikhahmed.github.io/docs/HIGGSFIELD.md`.
3. Download the result and compress: `ffmpeg -i input.mp4 -vcodec libx264 -crf 28 -vf scale=1920:-2 -an assets/video/hero-loop.mp4`
4. The homepage auto-detects the file and fades it in as a background layer behind the galaxy.

---

## State at handoff

- Hub homepage: Three.js galaxy + GSAP scroll story + Lenis — all working
- Floating pill nav: live on all 14 hub pages (home.css + capricorn.css)
- Design system: compiled to `capricorn-core.css` in all 9 repos (v26 cache)
- All copy: humanised — no more "operating system", "holographic", "PBKDF2 310k iterations"
- Marks: geometric SVG marks for all 9 entities, rasterised to PNG icons
- SW cache: hub at v19, apps at v26
- React apps: ScentCap + AuraCap have route-level code splitting

## What NOT to touch
- `js/home-experience.js` — Three.js + GSAP story, fragile, don't change without reading first
- `css/home.css` — homepage only, not shared
- `shared/design-system/` source files — run sync script after any change
- `js/products-data.js` — single source of truth for all product pages, structure must not change
- Any `capricorn-core.css` file inside an app — those are compiled, not authored
