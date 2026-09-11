# Healify

An installable, offline-capable low FODMAP meal app for two people — the week's
menu and the shopping list for it.

- **Menu** — opens on today automatically, highlights the meal that's due now,
  and remembers which breakfast and snack options you picked. Picks clear
  themselves every Monday.
- **Shopping list** — tick items as you shop; ticks are saved on the device and
  survive closing the app.

## Install on a phone

Served over HTTPS via GitHub Pages, then:

- **iPhone** — open the page in **Safari** → Share → *Add to Home Screen*
- **Android** — open in Chrome → accept the install prompt, or ⋮ → *Install app*

It then opens full-screen with no browser bar, and works with no signal.

## Enable GitHub Pages

Repository **Settings → Pages → Source: Deploy from a branch → `main` / `root`**.
The app is then live at `https://pahazavr.github.io/healify/`.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Shopping list — markup, styles and tick-persistence logic, self-contained |
| `menu.html` | Week menu — day switcher, option picking, current-meal highlight |
| `manifest.webmanifest` | App name, icons, theme colour, standalone display mode |
| `sw.js` | Service worker; caches assets so the app opens offline |
| `icon-192.png`, `icon-512.png` | App icons (Android, install prompts, maskable) |
| `icon-180.png` | Apple touch icon |
| `.nojekyll` | Stops GitHub Pages running the files through Jekyll |

## Notes

Ticks and menu picks live in `localStorage`, which is **per device** — two phones
keep two independent lists. Sharing one live list between people would need a
backend.

To edit quantities, change the `<li>` rows in `index.html`. To change meals, edit
the `BREAKFAST` / `SNACK1` / `SNACK2` / `DAYS` arrays near the top of the script
in `menu.html`.

After changing any cached file, bump `CACHE` in `sw.js` (e.g. `healify-v6`) so
phones that already installed the app fetch the new version instead of the
cached one.
