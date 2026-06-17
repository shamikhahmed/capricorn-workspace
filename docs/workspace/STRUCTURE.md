# Workspace structure conventions

## Moving this folder

Safe to relocate (e.g. `~/Developer/Projects`). Avoid hardcoding `/Users/.../Desktop/Projects` in new code.

Use:

```js
import { WORKSPACE_ROOT, appDir } from '../scripts/lib/workspace-root.mjs';
```

Or from any app: `cd` into workspace root, then `cd VaultCap`.

## Git repos

Each product is its **own git repository**. Do not nest repos under a parent git root unless you intentionally want a monorepo.

## Screenshots

| Location | Purpose |
|----------|---------|
| `shamikhahmed.github.io/assets/screenshots/` | **Canonical** marketing screenshots for the hub site |
| App `src/assets/` | In-app hero/illustration only (not marketing) |

Do not scatter duplicate marketing PNGs inside individual app folders.

## Icons

| Pattern | Apps |
|---------|------|
| Root `icon-192.png`, `icon-512.png` | VaultCap, PulseCap, PrismCap, DeePonyCap, hub |
| `assets/icons/icon-*.png` | SteadyCap, LedgerCap |

Run `node scripts/generate-capricorn-icons.mjs` to regenerate.

## HTML at app root

Files like `pitch.html`, `landing.html`, `privacy.html` must stay at the **repository root** — GitHub Pages serves `https://shamikhahmed.github.io/<RepoName>/pitch.html`.

## Workspace meta docs

| File | Purpose |
|------|---------|
| `docs/workspace/PORTFOLIO.md` | Product table + repo links |
| `docs/workspace/CAPRICORN_HANDOFF.md` | Agent handoff / deep context |
| `docs/workspace/PHASE_COMPLETE.md` | Phase completion log |
