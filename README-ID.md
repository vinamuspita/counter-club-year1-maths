# Counter Club: Year 1 Maths — Offline PWA

This package wraps the supplied HTML app as an installable Progressive Web App (PWA). The learning content and application logic are preserved. Google Fonts loading was removed so the app does not depend on an online font; offline devices will use the built-in system font fallback instead.

## Important

A PWA service worker **cannot be installed directly from a `file://` HTML file**. To install it on iPad and phones, publish this folder to a static HTTPS host once (for example GitHub Pages or Netlify). Open the hosted URL online at least once so the app shell is cached, then it can be opened offline from its Home Screen icon. No account or server is needed for local progress storage; progress is stored separately on each device/browser.

## Install on iPad (Safari)

1. Publish the folder to an HTTPS website and open its URL in Safari while online.
2. Wait for the page to finish loading, then tap **Share**.
3. Choose **Add to Home Screen**. If shown, enable **Open as Web App**, then tap **Add**.
4. Open Counter Club from the new Home Screen icon once while online. Keep it open briefly to let the offline files cache.
5. Test by turning on Airplane Mode and opening the Home Screen app.

## Install on Android (Chrome)

1. Open the hosted HTTPS URL in Chrome while online.
2. Open the browser menu and choose **Install app** or **Add to Home screen**.
3. Open the installed app once while online and wait for it to finish loading.
4. Test offline by enabling Airplane Mode and opening the app icon.

## Publish using GitHub Pages (one free option)

1. Create a GitHub repository and upload **all contents of this folder** (not just `index.html`).
2. In the repository, open **Settings → Pages**.
3. Choose deployment from the `main` branch and the repository root, then save.
4. Wait for the Pages URL, open it on iPad/phone while online, and follow the install steps above.

A static host such as Netlify can also publish the whole folder by drag-and-drop. Keep `index.html`, `manifest.webmanifest`, `service-worker.js`, and the `icons` folder together.

## Local progress and limitations

- Learner profiles, stars, badges, settings, and progress use browser `localStorage` when the optional hosted database integration is unavailable.
- Local progress is not shared between iPad and phone. Browser/site data clearing can erase it, so avoid clearing website data if you need to retain progress.
- Sound uses the browser/device speech engine; speech availability and voices may vary by device and offline language packs.
- The original app has an optional integration with `window.claude` if supplied by a host environment. In ordinary static hosting it falls back to local storage, which is the intended per-device offline mode.
- After publishing an updated version, the service worker cache version may need to be incremented in `service-worker.js` (`counter-club-year1-v1`) so installed devices download the new version.

## Files

- `index.html` — application
- `manifest.webmanifest` — install metadata
- `service-worker.js` — offline app-shell cache
- `icons/` — app icons
