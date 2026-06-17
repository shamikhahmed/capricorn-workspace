# Capricorn Systems — Comprehensive Handoff Document

**Prepared for:** Passing to another AI to write detailed implementation prompts  
**Workspace:** portable folder (see root `README.md`; scripts use `scripts/lib/workspace-root.mjs`)  
**Transcript source:** [3615aa31-6370-4654-b3ad-da98cfe3349b](3615aa31-6370-4654-b3ad-da98cfe3349b)  
**Date context:** June 10–12, 2026 (last updated June 12)  
**Founder:** Shamikh Ahmed (`shamikh73@gmail.com`)

---

## 0. CURRENT STATUS (June 12, 2026)

### Cap suite (operator tools — not on GitHub yet)

| Product | Folder | Package | Role |
|---------|--------|---------|------|
| **Cap · DevRoom** | `Cap-DevRoom/` | `cap-devroom` | Engineering office — AI agents, CEO command, sandboxes for 8 Cap apps |
| **Cap · Markroom** | `Cap-Markroom/` | `cap-markroom` | Marketing / company ops monorepo (Turborepo) |
| **Capricorn Hub** | `shamikhahmed.github.io/` | — | Public investor site |

Former names **Jarvis OS** → **Meridian Office** → **Cap DevRoom** (folders `jarvis-os` / `meridian-office` removed). Run DevRoom: `cd Cap-DevRoom && npm run dev`. See `Cap-DevRoom/docs/CAP-SUITE.md`.

## 0b. PORTFOLIO STATUS (June 11, 2026 — evening)

**Portfolio complete for 8 Cap apps** (6 Capricorn + ScentCap + AuraCap). All listed on the hub with README, pitch, presentation, landing, privacy, icons, screenshots, and live GitHub Pages deploys. **CarApp** is intentionally deferred (empty placeholder).

| Repo | Latest `main` commit |
|------|----------------------|
| shamikhahmed.github.io | `91859dd` |
| ScentCap | `9716f49` |
| AuraCap | `49b6542` |
| VaultCap | `ecc9f4c` |
| PulseCap, PrismCap, SteadyCap, LedgerCap, DeePonyCap | synced with `origin/main` |

**Hub URLs added:** `scentcap.html`, `auracap.html` · Live apps: `/ScentCap/`, `/AuraCap/`  
**SPA deep links:** ScentCap + AuraCap use `404.html` + `index.html` redirect (GitHub Pages pattern).  
**iPhone layout:** Hero used `min-height: 100vh` + vertical centering, which caused large blank gaps above content on small screens — fixed in `capricorn.css` (mobile: `min-height: auto`, `justify-content: flex-start`, tighter hero/carousel padding).

---

## 1. PROJECT OVERVIEW

**Capricorn Systems** is a company-first portfolio of **eight** offline-first Progressive Web Apps (PWAs) — six Capricorn products plus standalone **ScentCap** and **AuraCap** — unified under **Device Sovereignty**: software that lives on the user's device, not in a mandatory cloud.

**Investor-ready goal (user's words):** The user wants to send links to investors and have every product page, app, pitch deck, screenshot, icon, and design feel **100% polished** — "perfect" enough to demo without apology. App Store submission is explicitly **out of scope** for now.

**Who it's for:**

| Audience | What they get |
|----------|---------------|
| **Investors / acquirers** | Company hub, per-product marketing pages, inline pitch decks, multi-device screenshots, sovereignty narrative |
| **Privacy-conscious consumers** | Encrypted vault, offline fitness, offline games, private recovery journal, local wealth ledger, child-safe collector |
| **Diaspora / PK-focused users** | VaultCap (PK/UK/UAE finance), LedgerCap (PSX, Meezan, Zakat) |
| **Families / kids** | PrismCap (offline party games), DeePonyCap (MLP collection) |

**Investor one-liner** (from `PORTFOLIO.md`):

> Capricorn Systems ships six premium offline-first apps — encrypted life vault, performance training, 38-game party hub, recovery OS, Pakistani wealth ledger, and child-safe MLP collector — all PWAs with local data, Playwright-verified quality, and Capacitor/TestFlight paths to App Store.

---

## 2. REPOSITORY STRUCTURE

### Active repos (9 git repos, all on `main` synced with `origin/main`)

| Repo | Path | Contains | Latest commit |
|------|------|----------|---------------|
| **Company hub** | `shamikhahmed.github.io/` | Capricorn marketing site, product pages, screenshots, SW | `fcf8444` |
| **VaultCap** | `VaultCap/` | Encrypted life vault (ex-VaultOS) | `47469ec` |
| **PulseCap** | `PulseCap/` | Performance OS (ex-FitnessOS) | `9045081` |
| **PrismCap** | `PrismCap/` | 38 offline games (ex-PrismOS) | `b308346` |
| **SteadyCap** | `SteadyCap/` | Recovery OS (ex-DisciplineOS) | `11472b9` |
| **LedgerCap** | `LedgerCap/` | Wealth OS (ex-StundsOS) | `aced25f` |
| **DeePonyCap** | `DeePonyCap/` | MLP collector (ex-DeePonyOS) | `40b5743` |
| **ScentCap** | `ScentCap/` | Fragrance wardrobe PWA (standalone Cap app) | `9716f49` |
| **AuraCap** | `AuraCap/` | Apple ecosystem studio PWA (standalone Cap app) | `49b6542` |

### Non-repo local files

| Path | Notes |
|------|-------|
| `PORTFOLIO.md` | Portfolio status doc — **not in any git repo** |
| `scripts/` | Cross-repo tooling (icons, version sync, truth audit) |

### Rebrand mapping (legacy → current)

| Old name | New name | Legacy GitHub Pages path | Current path |
|----------|----------|--------------------------|--------------|
| VaultOS | VaultCap | `/VaultOS/` | `/VaultCap/` |
| FitnessOS | PulseCap | `/FitnessOS/` | `/PulseCap/` |
| PrismOS | PrismCap | `/PrismOS/` | `/PrismCap/` |
| DisciplineOS | SteadyCap | `/DisciplineOS/` | `/SteadyCap/` |
| StundsOS | LedgerCap | `/StundsOS/` | `/LedgerCap/` |
| DeePonyOS | DeePonyCap | `/DeePonyOS/` | `/DeePonyCap/` |

### Live URLs

**Company hub**

- Home: https://shamikhahmed.github.io/
- About: https://shamikhahmed.github.io/about.html
- Sovereignty: https://shamikhahmed.github.io/sovereignty.html
- Solutions: https://shamikhahmed.github.io/solutions.html

**Product marketing pages (hub)**

| Product | Marketing page | Live app | Pitch deck | Presentation |
|---------|------------------|----------|------------|--------------|
| VaultCap | https://shamikhahmed.github.io/vaultcap.html | https://shamikhahmed.github.io/VaultCap/ | https://shamikhahmed.github.io/VaultCap/pitch.html | https://shamikhahmed.github.io/VaultCap/presentation.html |
| PulseCap | https://shamikhahmed.github.io/pulsecap.html | https://shamikhahmed.github.io/PulseCap/ | https://shamikhahmed.github.io/PulseCap/pitch.html | https://shamikhahmed.github.io/PulseCap/presentation.html |
| PrismCap | https://shamikhahmed.github.io/prismcap.html | https://shamikhahmed.github.io/PrismCap/ | https://shamikhahmed.github.io/PrismCap/pitch.html | https://shamikhahmed.github.io/PrismCap/presentation.html |
| SteadyCap | https://shamikhahmed.github.io/steadycap.html | https://shamikhahmed.github.io/SteadyCap/ | https://shamikhahmed.github.io/SteadyCap/pitch.html | https://shamikhahmed.github.io/SteadyCap/presentation.html |
| LedgerCap | https://shamikhahmed.github.io/ledgercap.html | https://shamikhahmed.github.io/LedgerCap/ | https://shamikhahmed.github.io/LedgerCap/pitch.html | https://shamikhahmed.github.io/LedgerCap/presentation.html |
| DeePonyCap | https://shamikhahmed.github.io/deeponycap.html | https://shamikhahmed.github.io/DeePonyCap/ | https://shamikhahmed.github.io/DeePonyCap/pitch.html | https://shamikhahmed.github.io/DeePonyCap/presentation.html |
| ScentCap | https://shamikhahmed.github.io/scentcap.html | https://shamikhahmed.github.io/ScentCap/ | https://shamikhahmed.github.io/ScentCap/pitch.html | https://shamikhahmed.github.io/ScentCap/presentation.html |
| AuraCap | https://shamikhahmed.github.io/auracap.html | https://shamikhahmed.github.io/AuraCap/ | https://shamikhahmed.github.io/AuraCap/pitch.html | https://shamikhahmed.github.io/AuraCap/presentation.html |

**Legacy redirects on hub**

- `product.html?p=vaultos` → `vaultcap.html` (via `LEGACY_SLUG_MAP` in `products-data.js`)
- `app.html?a=fitnessos` → `pulsecap.html`

**GitHub repos**

- https://github.com/shamikhahmed/shamikhahmed.github.io
- https://github.com/shamikhahmed/VaultCap (and PulseCap, PrismCap, SteadyCap, LedgerCap, DeePonyCap)

---

## 3. WHAT WE HAVE BUILT

### Company hub (`shamikhahmed.github.io`)

| Feature | Status | Details |
|---------|--------|---------|
| Capricorn branding | ✅ | Logo, gold constellation aesthetic, Bricolage Grotesque + Inter + IBM Plex Mono |
| Homepage hero | ✅ | Large logo (`clamp(96px, 18vw, 140px)`), stats bar, product grid, spotlights, sovereignty, founder, install, solutions |
| Homepage carousel | ✅ | `#screenshotCarousel` in hero — auto-rotates product device frames every 5s (`initHomeCarousel` in `product-media.js`) |
| Six dedicated product pages | ✅ | `vaultcap.html` … `deeponycap.html` — each loads `product-page.js` |
| Unified Vault-style rail layout | ✅ | Sticky left section nav on all product pages (`product-rail`, `initProductRail`) |
| Pitch embed | ✅ | Inline `<iframe>` to each app's `pitch.html` |
| Screenshot gallery | ✅ | 8 screenshots per product + device showcase (iPhone / iPad / Mac) |
| Naming stories | ✅ | `#name` section per product from `nameStory` in `products-data.js` |
| UX timeline | ✅ | Per-product 4-step install journey (`ux` array + `uxTimeline`) |
| DeePony pink theme | ✅ | `body.theme-deeponycap` — darker pink palette (`bg: #d4a0b8`, text `#2d1235`) |
| Mobile nav | ✅ | Hamburger `nav-toggle` + `initMobileNav` |
| Service worker | ✅ | `capricorn-v11` — precaches HTML, CSS, JS, all 48+ screenshot PNGs |

### Per-app features (post-rebrand)

| App | Version | Key built features |
|-----|---------|-------------------|
| **VaultCap** | 4.1.0 | AES-256-GCM vault, 120+ banks, family profiles, Zakat, smart import, desktop sidebar layout, demo profile unlock for screenshots |
| **PulseCap** | 4.5.1 | 300+ exercises, wger.de sync, 5-tab nav (Home/Train/Explore/Body/Me), body map, Smart Coach (rules-based), recovery readiness |
| **PrismCap** | 4.0.0 | 38 game engines, pass-and-play, XP/achievements, device model picker, `100dvh` shell |
| **SteadyCap** | 2.0.0 | Recovery score, 5-phase SOS, medicines, journal, trigger forecast, `?demo=1` silent demo loader |
| **LedgerCap** | 2.3.0 | PSX holdings, Meezan funds, Zakat, IPO tracker, investment tracker, Cloudflare PSX proxy, `?demo=1` seed data |
| **DeePonyCap** | 2.2.0 | G1–G5 catalog, photo shelves (IndexedDB), wishlist tiers, achievements, `?demo=1` loads 18-pony demo collection |

### Icons (high-res, regenerated)

Script: `scripts/generate-capricorn-icons.mjs`

Generates maskable PNGs at **192, 512, 1024** for Capricorn hub + all 6 apps. Latest app commits: `*-v24` service worker bumps after icon regen.

### Screenshot assets

**60 PNG files** in `shamikhahmed.github.io/assets/screenshots/`:

- Per app: `{slug}.png`, `{slug}-2.png` … `{slug}-8.png`, `{slug}-ipad.png`, `{slug}-mac.png`
- Captured June 10, 2026 via Playwright

### Documentation per app

Each app has: `docs/GUIDE.md`, `pitch.html`, `presentation.html`, `privacy.html`, `changelog.html`, `PRIVACY.md`, `SECURITY.md`, Playwright smoke tests.

---

## 4. TECH STACK & ARCHITECTURE

### Deployment model

```
GitHub Pages (static hosting)
├── shamikhahmed.github.io/     → Company hub (root of user.github.io repo)
├── shamikhahmed.github.io/VaultCap/   → Each app repo deployed as subfolder
├── shamikhahmed.github.io/PulseCap/
└── … (6 app repos)
```

- **No backend** for apps (except optional Cloudflare Workers for LedgerCap PSX proxy and VaultCap LLM proxy)
- **No build step** for hub or apps — vanilla HTML/CSS/JS
- **`.nojekyll`** in app repos for GitHub Pages

### Hub JS module architecture

```
index.html / {product}.html
├── js/products-data.js    → PRODUCTS catalog, LEGACY_SLUG_MAP, COMPANY
├── js/product-media.js    → deviceFrame, screenshotGallery, deviceShowcase, initHomeCarousel
├── js/product-page.js     → Renders all product page sections + rail
└── js/capricorn.js        → Homepage grid, spotlights, carousel, starfield, legacy redirects
```

### App architecture (common pattern)

- Single-page `index.html` + modular `js/` (varies per app)
- `localStorage` / `IndexedDB` for data
- `sw.js` service worker per app with versioned cache (`vaultcap-v24`, etc.)
- `manifest.json` + Apple PWA meta tags
- `css/identity.css` + app-specific layout CSS
- Desktop shell: centered phone/tablet frame at `min-width: 769px` / `1024px` with safe-area reset on Mac browsers

### Screenshot tooling

- `shamikhahmed.github.io/scripts/capture-screenshots.mjs` — Playwright ESM script
- Hub `package.json` exists for Playwright dependency (do not commit `node_modules`)

### Cross-repo scripts (`scripts/`)

| Script | Purpose |
|--------|---------|
| `generate-capricorn-icons.mjs` | High-res maskable icons |
| `generate-icons.mjs` | Older icon generator |
| `sync-versions.mjs` | Sync VERSION.json → sw.js, landing badges |
| `truth-audit.mjs` | Marketing ↔ code alignment grep |
| `create-playwright-smoke.mjs` | Smoke test scaffolding |
| `generate-decks.mjs` | Pitch deck generation helper |
| `rename-capricorn-repos.sh` | Repo rename automation |

---

## 5. DESIGN SYSTEM

### Hub (`capricorn.css`)

| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#0a0e17` | Page background |
| `--gold` | `#c9a227` | Capricorn accent |
| `--font` | Inter | Body |
| `--display` | Bricolage Grotesque | Headings |
| `--mono` | IBM Plex Mono | Pills, stats |
| `--max` | `1120px` | Content width |
| `--safe-t/b` | `env(safe-area-inset-*)` | Notched devices |

### Per-product accent colors (from `products-data.js`)

| Product | Accent | Background | Theme |
|---------|--------|------------|-------|
| VaultCap | `#5b8dee` | `#070b14` | Dark Swiss vault |
| PulseCap | `#00f2ff` | `#0a0a0f` | Kinetic cyan |
| PrismCap | `#c77dff` | `#0a0014` | Neon arcade |
| SteadyCap | `#c9652b` | `#1a110e` | Warm recovery |
| LedgerCap | `#f59e0b` | `#0b0e11` | Gold terminal |
| DeePonyCap | `#c4367a` | `#d4a0b8` | Light pink (`theme-light`, `theme-deeponycap`) |

### Product page layout (unified Vault-style rail)

- `.product-shell` — CSS grid: `196px` sticky left rail + main content
- Rail sections: Overview → The name → Pitch → Screenshots → Experience → Problem → Promise → Features → Compare → Audience → FAQ → Related → Install
- LedgerCap variant: adds ticker marquee + dense feature tables
- Mobile: rail becomes horizontal scroll chips; device showcase stacks to single column

### Breakpoints

| Breakpoint | Behavior |
|------------|----------|
| `≤640px` | Collapsed nav (hamburger), tighter section padding, single-column mocks |
| `≤860px` | Spotlight grid → single column |
| `769px+` (apps) | Desktop centered shell, hide mobile bottom nav padding issues |
| `1024px+` (apps) | `--sat: 0px` safe-area reset on hover/pointer-fine (Mac browsers) |

### Device showcase frames

- iPhone: 390×844, notch
- iPad: 834×1194, `device-shell--ipad`
- Mac: 1280×800 browser frame, `device-shell--mac`

---

## 6. USER'S ORIGINAL REQUESTS (Chronological)

1. **Full engineering audit** of VaultOS (code, security, product, roadmap)
2. **Fix all VaultOS audit issues**, then review other apps in Projects folder
3. **Merge duplicate folders** (FitnessOS2, financial/, Pony-App); rename properly; **complete DeePonyOS rebuild** (magical, child-friendly, NOT dashboard)
4. **Don't delete** renamed repos; DeePonyOS native iPhone PWA polish; then StundsOS
5. **DeePonyOS + StundsOS feature expansion** — user answered detailed questionnaire (onboarding skip/back, backup, collector mode, PSX prices, IPO, keep existing data)
6. **"Do everything and commit and push"** for both apps
7. **Cloudflare Wrangler** setup for StundsOS PSX proxy (cost/safety concerns addressed — free tier)
8. **StundsOS UI overhaul** — footer blank space, wrong prices, settings not saving, investment tracker, IPO → CDC flow
9. **FitnessOS (→ PulseCap) overhaul** — reduce 10+ tabs to 5, wger API, fully offline, fix all screens, "completely perfect"
10. **CTO Phases 0–4** across portfolio — truth, PWA, quality, enterprise, App Store scaffolds (local commits, later pushed)
11. **Capricorn rebrand** — rename all 6 repos, company site, in-app branding, desktop polish
12. **Expand company site** — dedicated product pages, bigger logo, fix Google Fonts 400 error
13. **Add app screenshots + UX journey** to website
14. **Fix DeePony page** — invisible text (font = background); make pink/girlish
15. **Fix "Made for your lock screen"** copy → home screen language
16. **Unique scrolling experience** per product page (later superseded by unified rail)
17. **Cross-device optimization** — Android, iPhone, iPad, Mac for all 6 apps + hub
18. **"Is everything launch ready?"** — honest ~85% assessment
19. **Investor polish pass** — darker DeePony pink, remove homepage screenshot *section* (kept carousel in hero), new high-res icons, fonts/alignment/colors, skip App Store
20. **Add presentation/pitch/carousel back**, more screenshots per product page
21. **Fix Vault page alignment**, Ledger header visibility, enlarge homepage "Capricorn Systems" text, fix auto carousel, improve spotlight visuals
22. **Unify all product pages to Vault-style template** with naming stories, demo data for screenshots, no duplicate screenshots, iPad/Mac device showcase
23. **Fix Vault duplicate screenshots** (show dashboard, family vault, etc.), apply left rail to ALL product pages, fix PrismCap header blank space in app AND screenshots, remove duplicate website content
24. **Fable AI cost estimate** and **$50 budget alternatives**
25. **This handoff document** for another AI to write detailed prompts

---

## 7. PROBLEMS FACED & FIXES APPLIED

| Problem | Fix applied | Where |
|---------|-------------|-------|
| VaultOS security audit issues (decoy PIN, widget leak, XSS, export) | Decoy unlock, encrypted widget, escHtml, unified export, modal prompts | `VaultCap/js/` (pre-rebrand) |
| Duplicate project folders | Removed FitnessOS2, financial/, Pony-App; renamed fitnessos→FitnessOS | Projects root |
| DeePonyOS dashboard feel | Complete magical rebuild; later modularized to DeePonyCap | `DeePonyCap/` |
| DeePony onboarding trap (no skip/back) | Skip/back buttons, onboarding flow | `DeePonyCap/js/app.js` |
| StundsOS footer blank space | Flex nav, `--nav-h`, padding fixes | `LedgerCap/css/app.css` (post-rebrand) |
| StundsOS wrong PSX prices | Cloudflare worker `stunds-psx-proxy.shamikhahmed.workers.dev`, timeseries endpoints | `LedgerCap/js/engines/prices.js` |
| StundsOS settings not saving | Settings persistence fixes | `LedgerCap/js/modules/settings.js` |
| FitnessOS too many tabs | Reduced to 5-tab nav | `PulseCap/` |
| Google Fonts 400 on hub | Removed broken `@import`; valid `<link>` tags | `capricorn.css`, all HTML |
| Product pages too similar (phase 1) | Six distinct scroll layouts | `product-page.js` + CSS (later unified to rail) |
| DeePony invisible text on product page | `theme-deeponycap` light theme with contrast | `capricorn.css`, `products-data.js` |
| "Made for your lock screen" | Changed to "Built to live on your home screen" | `index.html` |
| Screenshots missing | Playwright capture pipeline, 60 PNGs | `assets/screenshots/`, `capture-screenshots.mjs` |
| Subagent work not pushed | Manual commit/push follow-ups | Hub commits `e113088`→`2e7f975` |
| VaultCap Mac sidebar overlap | Sidebar scroll containment, `sb-nav` only scrolls | `VaultCap/css/layout.css` |
| Phantom iPhone notch on Mac | `--sat: 0px` at `1024px+` | All 6 apps' layout CSS |
| PrismCap header blank gap on iPhone | Double safe-area fix | `PrismCap` commit `b308346` |
| DeePony too bright | Darkened pink in app + hub | `DeePonyCap` `c03c02b`, hub `c890354` |
| Homepage carousel broken | `initHomeCarousel` rewrite, dot click handlers | `product-media.js`, `capricorn.js` |
| Vault page alignment off vs others | Unified rail template for all 6 | `a1313cc`, `2e7f975` |
| Ledger pitch section hidden under header | Layout/z-index/padding fixes | `734fbed` |
| Homepage "Capricorn Systems" too small | `.hero-brand`, larger hero logo | `capricorn.css` |
| Spotlight right-side text-only visual | Replaced with real device-framed screenshots | `capricorn.js` |
| SteadyCap empty screenshots | `?demo=1` silent demo loader | `SteadyCap/js/app.js` `11472b9` |
| No naming explanation per product | `nameStory` field + `#name` section | `products-data.js`, `product-page.js` |
| Old branding in apps | Python rebrand sweep across 6 repos | June 10 Capricorn sweep |
| Low-res icons | `generate-capricorn-icons.mjs` → 192/512/1024 maskable | All repos `*-v24` |

---

## 8. KNOWN UNRESOLVED ISSUES

### Critical for investor demo

| Issue | Evidence | Severity |
|-------|----------|----------|
| **VaultCap screenshots 2–8 may still be duplicates** | All `vaultcap-2.png` through `vaultcap-8.png` are exactly **331,280 bytes** on disk — likely same image repeated despite commit `2e7f975` claiming fix | **High** |
| **PrismCap screenshots 2–8 nearly identical** | All ~64KB — nav eval may not be changing screens during capture | **High** |
| **SteadyCap screenshot 8 = screenshot 2** | Both 928,083 bytes | **Medium** |
| **No PDF files anywhere** | `**/*.pdf` search returns 0 files. User asked for "presentation pdf pitch" — only HTML exists | **Medium** |
| **`presentation.html` not embedded on product pages** | Only `pitch.html` is iframe-embedded; `presentation.html` exists per app but not linked from hub product pages | **Medium** |
| **Real device QA not done** | All fixes were code/CSS review + Playwright — no verified pass on physical iPhone, Android, iPad | **High** |
| **Service worker stale cache** | Users/investors may see old site until hard refresh (`Cmd+Shift+R`). Hub at `capricorn-v11` | **Medium** |

### Lower priority / cosmetic

| Issue | Notes |
|-------|-------|
| Internal JS file headers still say `VaultOS` / `FitnessOS` | e.g. `VaultCap/js/core/utils.js` — users don't see this |
| Legacy GitHub Pages URLs (`/VaultOS/`) may 404 | After repo rename; no redirect worker confirmed |
| `PORTFOLIO.md` not versioned | Local only at workspace root |
| LedgerCap live PSX prices | Depends on Cloudflare worker uptime; user reported intermittent SSL/fetch failures |
| Pitch deck depth uneven | VaultCap pitch ~1,870 lines; others thinner |
| User oscillated on homepage carousel | Removed screenshot *section*, kept hero carousel — confirm this matches intent |
| DeePonyCap product page "still very off" per user | May need another visual pass beyond `c890354` |

### Verification needed before telling user "100% done"

1. Open each product page on iPhone Safari, iPad, Mac Chrome — check rail, pitch iframe, gallery swipe
2. Re-run `node shamikhahmed.github.io/scripts/capture-screenshots.mjs` and diff PNG hashes — no duplicates
3. Hard-refresh hub after any deploy and confirm `capricorn-v*` updates
4. Open each live app, add to home screen, verify no header blank gaps (especially PrismCap, DeePonyCap)

---

## 9. SCREENSHOT PIPELINE

### Script location

`shamikhahmed.github.io/scripts/capture-screenshots.mjs`

### How to run

```bash
cd shamikhahmed.github.io
npx playwright install chromium   # first time only
node scripts/capture-screenshots.mjs
```

### Output directory

`shamikhahmed.github.io/assets/screenshots/`

### Naming convention

| File | Content |
|------|---------|
| `{slug}.png` | Landing page (`/App/landing.html`) |
| `{slug}-2.png` | App home after setup |
| `{slug}-3.png` … `{slug}-8.png` | One per navigation step |
| `{slug}-ipad.png` | iPad viewport (834×1194, scale 2) |
| `{slug}-mac.png` | Mac viewport (1280×800) |

### Per-app capture logic

| App | Setup | Navigation |
|-----|-------|------------|
| **VaultCap** | Custom `vaultUnlock()` — demo profile, PIN `123456`, nav via `R.goto()` | landing → dashboard → family → banks → documents → zakat → investments |
| **PulseCap** | `loadDemoMode()` | `go('workout')`, nutrition, recovery, bodymap, progress, profiles |
| **PrismCap** | Seed localStorage `po5`, hide welcome/loader, `Nav.go('home')` | library, arcade, dashboard, profile, home |
| **SteadyCap** | URL `?demo=1` (silent `Profile.loadDemoData`) | recovery, emergency, knowledge, journal, profile, dashboard |
| **LedgerCap** | URL `?demo=1` (silent `Settings.loadSeedData`) | portfolio, transactions, income, settings |
| **DeePonyCap** | URL `?demo=1` (silent `DemoSeed.load`, 18 ponies) | collection, wishlist, shelves, stats, settings, stable |

### Demo mode URLs

- `https://shamikhahmed.github.io/SteadyCap/?demo=1`
- `https://shamikhahmed.github.io/LedgerCap/?demo=1`
- `https://shamikhahmed.github.io/DeePonyCap/?demo=1`

### Known capture bugs to fix in next pass

1. **VaultCap `vaultNav()`** — if PIN/unlock fails on CI, all nav shots repeat same dashboard frame
2. **PrismCap `eval(nav)`** — screens may not switch; verify `Nav.go()` works in Playwright context
3. **Add screenshot hash dedup check** before commit — fail if any two files per slug are identical

### Referenced in `products-data.js`

```javascript
function shotPaths(slug, n = 8) { /* slug.png, slug-2.png … slug-8.png */ }
function deviceShotPaths(slug) { /* slug-2.png, slug-ipad.png, slug-mac.png */ }
```

---

## 10. PITCH DECKS

### Per-app HTML decks (in each app repo)

| App | Pitch (investor) | Presentation (slides) |
|-----|------------------|----------------------|
| VaultCap | `/VaultCap/pitch.html` (~1,870 lines, scrollable slides) | `/VaultCap/presentation.html` |
| PulseCap | `/PulseCap/pitch.html` | `/PulseCap/presentation.html` |
| PrismCap | `/PrismCap/pitch.html` | `/PrismCap/presentation.html` |
| SteadyCap | `/SteadyCap/pitch.html` | `/SteadyCap/presentation.html` |
| LedgerCap | `/LedgerCap/pitch.html` | `/LedgerCap/presentation.html` |
| DeePonyCap | `/DeePonyCap/pitch.html` | `/DeePonyCap/presentation.html` |

### Hub embedding (current)

`product-page.js` → `F.pitch()` section:

- Inline `<iframe src="${p.pitchUrl}">` with "Open deck fullscreen" link
- **No** `presentation.html` embed yet
- **No** PDF download links

### User request not fully done

> "add presentation pdf pitch blah blah in every products page"

**Gap:** Add links/embeds for `presentation.html` and optionally generate PDFs (none exist in repo).

---

## 11. DEPLOYMENT

### GitHub Pages

- Each app repo deploys from its root to `shamikhahmed.github.io/{AppName}/`
- Hub repo deploys to `shamikhahmed.github.io/`
- Push to `main` triggers deploy (1–3 minute propagation)

### Cache busting

| Layer | Mechanism | Current version |
|-------|-----------|-----------------|
| Hub SW | `CACHE = 'capricorn-v11'` in `sw.js` | v11 |
| Hub CSS | `?v=11` on some product HTML (`capricorn.css?v=11`) | v11 |
| App SW | Per-app cache string | `vaultcap-v24`, `pulsecap-v24`, etc. |

**After any hub deploy:** bump `capricorn.css` query param AND `sw.js` CACHE constant, commit, push, tell user to hard-refresh.

### Cloudflare Workers (optional backends)

| Worker | URL | App |
|--------|-----|-----|
| PSX proxy | `https://stunds-psx-proxy.shamikhahmed.workers.dev` | LedgerCap |
| LLM proxy | `https://vaultos-llm-proxy.shamikhahmed.workers.dev` | VaultCap (optional Smart Parser assist) |

### Commit policy

**User rule: do NOT commit unless explicitly asked.** Throughout transcript, user repeatedly asked for push — latest state is fully pushed. Future AI sessions should ask before committing.

---

## 12. BUDGET / COST CONTEXT

### User asked about Claude Fable in Cursor

**Fable pricing (June 2026, from transcript):**
- ~$10 per 1M input tokens
- ~$50 per 1M output tokens (~2× Opus)
- Uses Cursor monthly usage pool

**Cursor plans:**

| Plan | Monthly | Included usage |
|------|---------|----------------|
| Pro | $20 | ~$20 usage |
| Pro+ | $60 | ~$70 usage |
| Ultra | $200 | ~$400 usage |

**Estimated cost for "review everything, fix all, perfect all 7 repos + docs + decks":** ~$250–$1,000+ of agent time if using Fable for monolithic runs.

### $50 budget alternatives (from transcript advice)

1. **Cursor Pro ($20) + Auto mode** — unlimited Auto routing; split into 4–6 focused sessions (~70–85% coverage)
2. **Manual session splitting** — one product per session with specific punch-lists (cheapest effective approach)
3. **Cannot honestly do 100% of scope for ≤$50** in a single Fable marathon

**Recommended for next AI:** Tight scoped prompts per session, not "fix everything."

---

## 13. RECOMMENDED WORK ORDER

### Phase A — Investor blockers (do first)

1. **Re-capture all screenshots** — fix VaultCap nav, PrismCap screen changes, verify no duplicate byte-identical PNGs
2. **Physical device QA** — iPhone Safari, iPad, Mac Chrome, one Android; document punch-list
3. **Hard-refresh verification** — bump hub SW to `capricorn-v12`, confirm live site matches `2e7f975`

### Phase B — Product page completeness

4. Add `presentation.html` link/embed alongside pitch on each product page
5. Fix any remaining DeePonyCap / LedgerCap layout issues user reported
6. Enlarge/adjust homepage hero branding if still too small on user's Mac

### Phase C — Content polish

7. Expand thin pitch decks (PulseCap, PrismCap, SteadyCap, LedgerCap, DeePonyCap) toward VaultCap depth
8. Generate PDF exports of pitch/presentation if user wants downloadable decks
9. Scrub internal `VaultOS`/`FitnessOS` comments in JS headers (optional, low visibility)

### Phase D — Reliability

10. Verify LedgerCap PSX proxy + VaultCap LLM proxy health
11. Run Playwright smoke tests in all 6 app repos
12. Run `node scripts/truth-audit.mjs` and fix marketing mismatches

### Phase E — Only if user asks

13. App Store / Capacitor (explicitly deferred)
14. Commit `PORTFOLIO.md` to a repo if user wants it versioned

---

## 14. FILES TO TOUCH FOR COMMON TASKS

| Task | Primary files |
|------|---------------|
| **Product copy, colors, screenshots, naming stories** | `shamikhahmed.github.io/js/products-data.js` |
| **Product page structure/sections** | `shamikhahmed.github.io/js/product-page.js` |
| **Screenshot gallery, carousel, device frames** | `shamikhahmed.github.io/js/product-media.js` |
| **Homepage grid, spotlights, carousel init** | `shamikhahmed.github.io/js/capricorn.js` |
| **All hub styling, rail, themes, responsive** | `shamikhahmed.github.io/css/capricorn.css` |
| **Homepage HTML** | `shamikhahmed.github.io/index.html` |
| **Per-product HTML shell** | `shamikhahmed.github.io/{vaultcap,pulsecap,prismcap,steadycap,ledgercap,deeponycap}.html` |
| **Hub cache bust** | `shamikhahmed.github.io/sw.js` |
| **Regenerate screenshots** | `shamikhahmed.github.io/scripts/capture-screenshots.mjs` |
| **Regenerate icons** | `scripts/generate-capricorn-icons.mjs` |
| **Portfolio status doc** | `PORTFOLIO.md` (workspace root, not in git) |
| **Sync app versions** | `scripts/sync-versions.mjs` + each app's `VERSION.json` + `sw.js` |
| **VaultCap desktop layout** | `VaultCap/css/layout.css`, `VaultCap/js/app.js` |
| **PrismCap header blank gap** | `PrismCap/css/layout.css`, `PrismCap/index.html` |
| **DeePonyCap app pink/dark** | `DeePonyCap/index.html`, `DeePonyCap/css/`, `DeePonyCap/js/app.js` |
| **Demo seed for screenshots** | `SteadyCap/js/app.js`, `LedgerCap/js/app.js`, `DeePonyCap/js/app.js` |
| **Pitch deck content** | `{App}/pitch.html`, `{App}/presentation.html` |
| **App SW cache bump** | `{App}/sw.js` |
| **Legacy URL redirects** | `shamikhahmed.github.io/js/products-data.js` (`LEGACY_SLUG_MAP`), `app.html`, `product.html` |

---

## 15. SUCCESS CRITERIA

What **"investor ready" / "perfect"** means for this user:

| Criterion | Definition of done |
|-----------|-------------------|
| **Hub** | All pages readable on iPhone, iPad, Mac; no font/alignment issues; carousel works; no duplicate content; hero branding prominent |
| **Product pages** | All 6 use unified Vault-style rail; pitch embedded and visible; 8 unique screenshots + iPad/Mac device frames; naming story present; DeePony readable pink theme |
| **Apps** | Each opens, installs to home screen, no header blank gaps, no footer dead space, desktop shell looks intentional |
| **Screenshots** | No repeated images; show real app states (Vault dashboard + family vault, Ledger portfolio with data, SteadyCap with demo data, etc.) |
| **Icons** | High-res maskable 192/512/1024, per-product visual identity |
| **Decks** | Pitch + presentation accessible from each product page; professional enough to scroll in a boardroom |
| **GitHub** | All 7 repos pushed, `main` clean, Pages live |
| **User sign-off** | User personally clicked every link on phone + Mac and said ready to send to investors |
| **Explicitly NOT required** | App Store submission, TestFlight, Capacitor builds |

---

## 16. CONSTRAINTS

| Constraint | Detail |
|------------|--------|
| **Don't commit unless asked** | User rule — always confirm before `git commit` / `git push` |
| **App Store skipped** | User: "leave app store thing" |
| **No force-push to main** | User git safety rules |
| **Treat as 1M-user SaaS quality** | Reliability > UX > Security > Performance |
| **Smart Coach / Smart Parser** | Rules-based — market as "Smart Assistant", not AI, unless LLM path is clearly optional |
| **API keys** | Never commit `.env`, `crsr_*` keys, or bundled secrets to git |
| **Render/GitHub Pages** | Static hosting only; ephemeral — no server-side writes |
| **Read before modifying** | Workspace rule: read entire relevant codebase before proposing fixes |
| **Minimize scope** | Smallest correct diff; match existing conventions |
| **Real environment** | Must run commands and verify — don't assume |

---

## Quick Reference — Hub Git History (last 10)

```
2e7f975 Fix product rail on all pages, Vault screenshots, and multi-device showcase.
a1313cc Unify product pages on Vault-style rail layout with naming stories.
734fbed Fix Vault/Ledger/DeePony layouts, homepage carousel, and About page.
46a764e Investor product page overhaul: pitch embeds, carousels, 48 screenshots.
c890354 Investor polish: darker DeePony theme, homepage screenshot removal, new icons.
640dd41 Add screenshot gallery styles, DeePony theme polish, and touch-target sizing.
30451a6 Wire product-media.js on homepage and bump service worker to capricorn-v6.
70acf36 Wire homepage screenshot gallery, UX timeline, and mobile nav.
3dc2f51 Bump service worker cache to capricorn-v5 after screenshot gallery rollout.
e113088 Add real app screenshots and UX journey sections across Capricorn site.
```

---

## Suggested First Prompt for the Next AI

> You are polishing Capricorn Systems for an investor demo. Start with Phase A: re-run `shamikhahmed.github.io/scripts/capture-screenshots.mjs`, verify no duplicate PNGs (compare file hashes per slug), fix VaultCap capture to show distinct screens (dashboard, family, banks, documents, zakat, investments), fix PrismCap header blank gap in both the live app and screenshots, then do a browser QA pass on https://shamikhahmed.github.io/vaultcap.html and https://shamikhahmed.github.io/ledgercap.html on iPhone and Mac widths. Bump `sw.js` cache after changes. Do not commit until Shamikh asks.

---

*End of handoff. Paths are relative to the workspace root unless noted as live URLs.*
