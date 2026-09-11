# Shopping List

An installable, offline-capable weekly shopping list for a low FODMAP meal plan.
Tick items as you shop; ticks are saved on the device and survive closing the app.

## Install on a phone

Served over HTTPS via GitHub Pages, then:

- **iPhone** — open the page in **Safari** → Share → *Add to Home Screen*
- **Android** — open in Chrome → accept the install prompt, or ⋮ → *Install app*

It then opens full-screen with no browser bar, and works with no signal.

## Enable GitHub Pages

Repository **Settings → Pages → Source: Deploy from a branch → `main` / `root`**.
The page is then live at `https://pahazavr.github.io/shopping-list/`.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The list — markup, styles and tick-persistence logic, self-contained |
| `manifest.webmanifest` | App name, icons, theme colour, standalone display mode |
| `sw.js` | Service worker; caches assets so the list opens offline |
| `icon-192.png`, `icon-512.png` | App icons (Android, install prompts, maskable) |
| `icon-180.png` | Apple touch icon |
| `.nojekyll` | Stops GitHub Pages running the files through Jekyll |

## Notes

Ticks live in `localStorage`, which is **per device** — two phones keep two
independent lists. Sharing one live list between people would need a backend.

To edit quantities, change the `<li>` rows in `index.html`. After changing any
cached file, bump `CACHE` in `sw.js` (e.g. `fodmap-shop-v2`) so phones that
already installed the app fetch the new version instead of the cached one.
