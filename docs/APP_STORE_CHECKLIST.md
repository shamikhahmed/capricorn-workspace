# App Store Readiness Checklist — OS Portfolio

**Phase 4** · June 10, 2026

| Item | Status |
|------|--------|
| Portfolio hub live `shamikhahmed.github.io` | ✅ |
| Capacitor config + npm scripts per app | ✅ |
| `icon-1024.png` per app | ✅ |
| `docs/APP_STORE.md` + `docs/IOS_INFO_PLIST.md` per app | ✅ |
| Privacy policy URLs (`privacy.html` hosted) | ✅ |
| Playwright smoke ×6 | ✅ |
| `npx cap add ios` + Xcode archive | ⬜ After Xcode install |
| Apple Developer account + TestFlight | ⬜ User action |
| App Store Connect metadata + screenshots | ⬜ User action |

### Xcode path (no Swift Playgrounds needed)

1. Install **Xcode** from Mac App Store (not Swift Playgrounds).
2. In each app: `npm install && npm run cap:init`
3. `npm run cap:ios` → set signing team → Archive → TestFlight.
