# Capricorn Systems — Product Portfolio

Six offline-first applications built as device-sovereign software. **Capricorn rebrand completed June 10, 2026** — company site live, repos renamed, in-app branding updated.

**Company site:** [shamikhahmed.github.io](https://shamikhahmed.github.io/) — Capricorn Systems hub with product pages, sovereignty, and solutions.

**Investor one-liner:** Capricorn Systems ships six premium offline-first apps — encrypted life vault, performance training, 38-game party hub, recovery OS, Pakistani wealth ledger, and child-safe MLP collector — all PWAs with local data, Playwright-verified quality, and Capacitor/TestFlight paths to App Store.

---

## Products

| Product | Tagline | Version | Live |
|---------|---------|---------|------|
| **VaultCap** | Encrypted life vault — finance, identity, documents (PK/UK/UAE) | 4.1.0 | [Open](https://shamikhahmed.github.io/VaultCap/) |
| **PulseCap** | Performance OS — 300+ exercises, Smart Coach, body map | 4.5.1 | [Open](https://shamikhahmed.github.io/PulseCap/) |
| **PrismCap** | 38 offline games — Pass & Play | 4.0.0 | [Open](https://shamikhahmed.github.io/PrismCap/) |
| **SteadyCap** | Recovery OS — routines, medicines, habits, SOS | 2.0.0 | [Open](https://shamikhahmed.github.io/SteadyCap/) |
| **LedgerCap** | Wealth OS — PSX, Meezan funds, Zakat, net worth | 2.3.0 | [Open](https://shamikhahmed.github.io/LedgerCap/) |
| **DeePonyCap** | MLP collection tracker — child-friendly | 2.2.0 | [Open](https://shamikhahmed.github.io/DeePonyCap/) |

### Standalone Cap apps (not Capricorn)

| Product | Tagline | Live |
|---------|---------|------|
| **ScentCap** | Fragrance wardrobe — daily picks, DNA-style scoring | [Open](https://shamikhahmed.github.io/ScentCap/) |
| **AuraCap** | Apple ecosystem studio — import apps, design layouts | [Open](https://shamikhahmed.github.io/AuraCap/) |

---

## Repositories

| Product | GitHub |
|---------|--------|
| VaultCap | [shamikhahmed/VaultCap](https://github.com/shamikhahmed/VaultCap) |
| PulseCap | [shamikhahmed/PulseCap](https://github.com/shamikhahmed/PulseCap) |
| PrismCap | [shamikhahmed/PrismCap](https://github.com/shamikhahmed/PrismCap) |
| SteadyCap | [shamikhahmed/SteadyCap](https://github.com/shamikhahmed/SteadyCap) |
| LedgerCap | [shamikhahmed/LedgerCap](https://github.com/shamikhahmed/LedgerCap) |
| DeePonyCap | [shamikhahmed/DeePonyCap](https://github.com/shamikhahmed/DeePonyCap) |
| Company hub | [shamikhahmed/shamikhahmed.github.io](https://github.com/shamikhahmed/shamikhahmed.github.io) |
| ScentCap | [shamikhahmed/ScentCap](https://github.com/shamikhahmed/ScentCap) |
| AuraCap | [shamikhahmed/AuraCap](https://github.com/shamikhahmed/AuraCap) |

---

## Phase status (0→4)

| Phase | Scope | Status |
|-------|-------|--------|
| **0 Truth** | Docs ↔ code alignment, Smart Parser/Coach naming, 38 games, journal triggers | ✅ |
| **1 PWA** | SW cache bust, PNG maskable icons, deck precache, DeePonyCap IndexedDB photos | ✅ |
| **2 Quality** | Playwright smoke ×6, PRIVACY/SECURITY/CHANGELOG truth, pitch expansion, landing footers | ✅ |
| **3 Enterprise** | Seed UI ×6, SECURITY.md, ENTERPRISE.md, trigger forecast, VERSION sync | ✅ |
| **4 App Store** | Portfolio hub, Capacitor scaffolds, icon-1024, APP_STORE + IOS_INFO_PLIST | ✅ |
| **5 Capricorn** | Company rebrand, repo rename, in-app + marketing pages, desktop polish (VaultCap) | ✅ |

---

## Security notes

- **VaultCap LLM:** Bundled proxy in `js/config/llm-bundled.js` → Cloudflare Worker at `https://vaultos-llm-proxy.shamikhahmed.workers.dev`. Smart Parser remains offline default.
- Each app: `PRIVACY.md`, `SECURITY.md`, `privacy.html`, `changelog.html`, `.env` in `.gitignore`.

---

## Documentation per product

| Product | Guide | Pitch | Presentation | Privacy | Changelog |
|---------|-------|-------|--------------|---------|-----------|
| VaultCap | [GUIDE](VaultCap/docs/GUIDE.md) | [pitch](VaultCap/pitch.html) | [slides](VaultCap/presentation.html) | [privacy](VaultCap/privacy.html) | [changelog](VaultCap/changelog.html) |
| PulseCap | [GUIDE](PulseCap/docs/GUIDE.md) | [pitch](PulseCap/pitch.html) | [slides](PulseCap/presentation.html) | [privacy](PulseCap/privacy.html) | [changelog](PulseCap/changelog.html) |
| PrismCap | [GUIDE](PrismCap/docs/GUIDE.md) | [pitch](PrismCap/pitch.html) | [slides](PrismCap/presentation.html) | [privacy](PrismCap/privacy.html) | [changelog](PrismCap/changelog.html) |
| SteadyCap | [GUIDE](SteadyCap/docs/GUIDE.md) | [pitch](SteadyCap/pitch.html) | [slides](SteadyCap/presentation.html) | [privacy](SteadyCap/privacy.html) | [changelog](SteadyCap/changelog.html) |
| LedgerCap | [GUIDE](LedgerCap/docs/GUIDE.md) | [pitch](LedgerCap/pitch.html) | [slides](LedgerCap/presentation.html) | [privacy](LedgerCap/privacy.html) | [changelog](LedgerCap/changelog.html) |
| DeePonyCap | [GUIDE](DeePonyCap/docs/GUIDE.md) | [pitch](DeePonyCap/pitch.html) | [slides](DeePonyCap/presentation.html) | [privacy](DeePonyCap/privacy.html) | [changelog](DeePonyCap/changelog.html) |

---

## Tooling

```bash
# Sync VERSION.json → sw.js, landing badges
node scripts/sync-versions.mjs

# Truth audit (marketing ↔ code)
node scripts/truth-audit.mjs

# Playwright smoke (run inside each app dir)
cd VaultCap    && npx playwright test   # port 8765
cd PulseCap    && npx playwright test   # port 8766
cd PrismCap    && npx playwright test   # port 8770
cd SteadyCap   && npx playwright test   # port 8768
cd LedgerCap   && npx playwright test   # port 8769
cd DeePonyCap  && npx playwright test   # port 8770
```

---

*© 2026 Capricorn Systems · Built by Shamikh Ahmed*
