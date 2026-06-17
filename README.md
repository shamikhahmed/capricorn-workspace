# Projects workspace

Portable monorepo-style folder for all Cap apps. **You can move this entire directory** — scripts resolve paths relative to this root, not your Desktop.

## Layout

| Path | What it is |
|------|------------|
| `shamikhahmed.github.io/` | Capricorn company hub (marketing, screenshots, product pages) |
| `VaultCap/` `PulseCap/` `PrismCap/` `SteadyCap/` `LedgerCap/` `DeePonyCap/` | Capricorn product apps (each has its own git repo) |
| `ScentCap/` `AuraCap/` | Standalone Cap apps (separate git repos) |
| `capricorn-tooling/` | Cross-repo tooling ([GitHub](https://github.com/shamikhahmed/capricorn-tooling)) — scripts, design system, agent skills |
| `scripts/` | Symlink → `capricorn-tooling/scripts` |
| `shared/` | Symlink → `capricorn-tooling/shared` |
| `cap-agents/` | Symlink → `capricorn-tooling/cap-agents` |
| `docs/` | Workspace-wide checklists and enterprise docs |
| `docs/workspace/` | Portfolio notes, handoff, phase status |
| `CarApp/` | Reserved — empty placeholder |

## Screenshots (marketing)

All product screenshots live in one place:

`shamikhahmed.github.io/assets/screenshots/`

See `shamikhahmed.github.io/assets/screenshots/README.md` for naming rules.

## Scripts (from workspace root)

```bash
node scripts/truth-audit.mjs
node scripts/generate-capricorn-icons.mjs
node scripts/sync-versions.mjs
cd shamikhahmed.github.io && node scripts/capture-screenshots.mjs
```

## Docs

- [Portfolio status](docs/workspace/PORTFOLIO.md)
- [Capricorn handoff](docs/workspace/CAPRICORN_HANDOFF.md)
- [Phase complete notes](docs/workspace/PHASE_COMPLETE.md)
- [Folder conventions](docs/workspace/STRUCTURE.md)

## Per-app conventions

- **PWA icons:** `icon-192.png` / `icon-512.png` at app root *or* `assets/icons/` (see each app’s `manifest.json`)
- **Deploy HTML** (`index.html`, `pitch.html`, `privacy.html`) stays at app root for GitHub Pages URLs
- **Internal docs** → `docs/` inside each app where applicable
