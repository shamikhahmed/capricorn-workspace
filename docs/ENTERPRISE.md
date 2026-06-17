# Shamikh Ahmed OS Portfolio — Enterprise Demo Guide

**Goal:** Repeatable 30-minute investor/enterprise walkthrough across all 6 apps — seed data via UI, no code edits.

**Last verified:** June 10, 2026 (Phase 3)

---

## Prerequisites (5 min)

1. Mac with Chrome or Safari; stable network for first PWA load.
2. Clone the workspace (any path — e.g. `~/Projects/`) or use GitHub Pages live URLs.
3. One-time Playwright browsers: `npx playwright install chromium` (in any app dir).
4. Optional local serve (faster): from each app folder, `npx serve -l <port> .` (ports 8765–8770).

| App | Local port | Live URL |
|-----|------------|----------|
| VaultCap | 8765 | https://shamikhahmed.github.io/VaultCap/ |
| PulseCap | 8766 | https://shamikhahmed.github.io/PulseCap/ |
| PrismCap | 8767 | https://shamikhahmed.github.io/PrismCap/ |
| SteadyCap | 8768 | https://shamikhahmed.github.io/SteadyCap/ |
| LedgerCap | 8769 | https://shamikhahmed.github.io/LedgerCap/ |
| DeePonyCap | 8770 | https://shamikhahmed.github.io/DeePonyCap/ |

---

## 30-minute demo script

### 1. VaultCap (5 min) — Encrypted life OS

1. Open app → unlock with **demo PIN `123456`** (or create vault, then load demo).
2. **Settings → Load Demo Data (fictional)** — 5 regional profiles (PK/UK/UAE).
3. Show **Banks**, **Documents**, **Smart Import** (offline parser default).
4. **Settings → About** — Enterprise disclaimer, AES-256-GCM, v4.1.0.
5. Mention optional LLM proxy (disabled by default for sensitive demos).

### 2. PulseCap (5 min) — Smart Coach fitness

1. **Settings → Profiles → Try Demo Mode** — 35 workouts, PRs, body stats.
2. Default nav: **Dashboard → Workout → Smart Coach → Recovery → Settings**.
3. Open **Smart Coach** tab — rule-based coaching (not LLM).
4. **Recovery** — readiness sliders; body map via Hub if pinned.
5. Landing shows v4.5.1; offline PWA.

### 3. PrismCap (5 min) — 38 offline games

1. Complete welcome or skip if returning user.
2. **Profile → Load Demo XP Profile** — Level 5+, 42 games, achievements.
3. Launch **Truth Bomb** (Party) — pass-and-play, truth or bomb.
4. Show **Daily challenge** on Arcade; fully offline.
5. v4.0.0 · 38 games (grep-verified in `js/app.js`).

### 4. SteadyCap (5 min) — Recovery OS

1. Complete onboarding or use existing profile.
2. **Profile → Load Demo Recovery Profile** — habits, journal triggers, craving log.
3. **Journal** — trigger chips (Stress, Night, etc.) save to localStorage.
4. **Recovery** tab — TriggerEngine forecast card renders from patterns.
5. **SOS** — 5-phase flow (no placeholders). Medical disclaimer in SECURITY.md.

### 5. LedgerCap (5 min) — Wealth OS

1. **Settings → Load Demo Holdings** — PSX + Meezan ledger.
2. Dashboard net worth, concentration insights.
3. **Settings → Zakat** — nisab, 2.5% estimate, scholar disclaimer.
4. **IPO** — subscribe → mark listed (record-keeping).
5. Not investment advice — SECURITY.md.

### 6. DeePonyCap (5 min) — Child-safe collector

1. **Settings → Load Demo Collection** — 18 ponies G1–G5.
2. Show catalog, generations, wishlist.
3. Photos in **IndexedDB** (not cloud).
4. COPPA-friendly statement in SECURITY.md; v2.2.0.
5. Export backup demo.

---

## Seed data summary

| App | UI path | What loads |
|-----|---------|------------|
| VaultCap | Settings → Load Demo Data | 5 fictional regional profiles |
| PulseCap | Settings → Profiles → Try Demo Mode | 35 workouts, PRs, stats |
| PrismCap | Profile → Load Demo XP Profile | XP, games, wins, achievements |
| SteadyCap | Profile → Load Demo Recovery Profile | Habits, journal, cravings, triggers |
| LedgerCap | Settings → Load Demo Holdings | PSX + Meezan transactions |
| DeePonyCap | Settings → Load Demo Collection | 18 demo ponies |

---

## FAQ (enterprise)

**Is data encrypted?**  
VaultCap: AES-256-GCM with PIN. Other apps: localStorage/IndexedDB on device — protect device passcode and exports.

**Is there telemetry?**  
No analytics SDKs in any of the six apps.

**Medical device?**  
No. SteadyCap supports recovery workflows; SOS is not clinical care.

**Investment advice?**  
No. LedgerCap is a personal ledger; Zakat is estimate-only.

**AI / LLM?**  
VaultCap optional LLM import via proxy. PulseCap Smart Coach is rule-based. Others: no LLM.

**Offline?**  
All six PWAs work offline after first load.

---

## Verification commands

```bash
# Portfolio root
node scripts/truth-audit.mjs
node scripts/generate-doc-pages.mjs
node scripts/sync-versions.mjs

# Playwright per app (from app directory)
cd VaultCap && npx playwright test
cd PulseCap && npx playwright test
# ... etc.
```

See [ENTERPRISE_CHECKLIST.md](./ENTERPRISE_CHECKLIST.md) for sign-off items.
