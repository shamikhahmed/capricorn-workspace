# Capricorn — AI Handoff Tasks
*2026-06-12. Each task below is self-contained: paste it into any AI session (Claude, etc.) opened in `~/Desktop/Projects` and it can run cold. Do them in any order. Rule for all tasks: commit locally per repo, push only after I review — except where the task says otherwise.*

---

## 1. Re-capture product screenshots (HIGH impact, mechanical)
> The hub's marketing screenshots in `shamikhahmed.github.io/assets/screenshots/` show pre-rebrand UI (e.g. "DisciplineOS", "VaultOS" chrome). There is a capture script at `shamikhahmed.github.io/scripts/capture-screenshots.mjs` — read it, serve each app locally (each app's package.json has a `serve` script with its port), run the capture, and replace the stale PNGs. Verify by checking 2–3 captures show "SteadyCap"/"VaultCap" branding. Then commit the hub repo.

## 2. Generate the Higgsfield hero video (needs my account, 10 min)
> Manual task for ME, not an AI: log into higgsfield.ai, generate with the prompt in `shamikhahmed.github.io/docs/HIGGSFIELD.md`, compress with the ffmpeg command there, save as `shamikhahmed.github.io/assets/video/hero-loop.mp4`, commit+push. The homepage auto-detects it.

## 3. Long-tail copy polish (cheap, parallelizable)
> In `shamikhahmed.github.io/js/products-data.js`, review every `problems`, `promise`, `features[].d`, `faqs[].a`, and `nameStory` string for all 8 products. Keep the existing voice (short, confident, "your device, your data"), fix anything that reads AI-generic, remove filler adverbs, keep each feature description under 18 words. Do NOT change field names, slugs, URLs, or structure — strings only. Then commit the hub repo.

## 4. Inner-page redesign pass (about/sovereignty/solutions/enterprise)
> The hub homepage (`index.html` + `css/home.css` + `js/home-experience.js`) was rebuilt with GSAP+Lenis; inner pages still use the older `css/capricorn.css` look. Restyle `about.html`, `sovereignty.html`, `solutions.html`, `enterprise.html` to match the homepage's feel: same nav/footer, `.cap-reveal` scroll animations (runtime already loaded via `js/capricorn-motion.js`), tighter typography. Don't add new libraries. Verify each page at 375px and 1280px. Commit the hub repo.

## 5. In-app branding sweep (per app, 8 small tasks)
> For app `<X>` in {VaultCap, PulseCap, PrismCap, SteadyCap, LedgerCap, DeePonyCap, ScentCap, AuraCap}: the app's icon was replaced with a new geometric mark (see `icon.svg` in the app root or assets/icons/ or public/). Find in-app places still showing the OLD logo/emoji branding (splash screens, About/Settings screens, landing.html headers) and swap them to use the new `icon.svg`. Run `npx playwright test` in the app dir afterward; it must pass. Commit that repo only.

## 6. Lighthouse run (verification, no code)
> Run Lighthouse (mobile) against https://shamikhahmed.github.io/ and one product page and one app (e.g. /VaultCap/). Report the four scores each and the top 3 opportunities. Don't change code.

## Context an AI might need
- Workspace conventions: `README.md` at root; design system source in `shared/design-system/` (never edit vendored `capricorn-core.css` copies — run `node scripts/sync-design-system.mjs`).
- Icons regenerate with `node scripts/render-marks.mjs` (marks live in `shared/design-system/marks/`).
- SW cache versions live in each app's `VERSION.json` → `node scripts/sync-versions.mjs`.
- Pushing deploys live (GitHub Pages). PWAs show new versions on the SECOND visit.
