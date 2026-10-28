# MCGI Choir Practice App

A free, installable web app (PWA) for choir members to practice their songs. Each listener picks their voice part once, browses events, and opens each song's practice files in built-in players.

**Live app:** https://lesterdc03.github.io/mcgi-choir-practice/

## Features

- **Pick your voice part once:** Soprano, Alto, Tenor, or Bass. It is saved on your device and can be changed any time from the settings button.
- **Browse events:** only published events are shown, newest first, with date and time. A search box helps you find an event.
- **Song lists in the right order:** each event shows its songs in the order set by the encoder. You can search by title and filter by type (Hymnario or Tanging Awit).
- **Practice files for every song:** your own voice part, the minus-one track, the full song, and the choreography video (shown only when there is one).
- **Built-in players:** Google Drive and YouTube files play inside the app.
- **Installs like a native app:** add it to your home screen on Android or iPhone.
- **Works briefly offline:** the last loaded data is cached, so the event list still opens without a connection.

## How to install on your phone

- **Android (Chrome):** open the link, tap the menu (three dots), then **Install app**.
- **iPhone (Safari):** open the link in Safari, tap **Share**, then **Add to Home Screen**.

## How it works

The app is a single static web page with no server and no user accounts. It reads its data from published CSV files of a Google Sheet with three tabs:

| Tab | Purpose |
|---|---|
| Events | Event name, date, status (Draft, Published, Archived), and time |
| Songs | The song library: title, type, and links to each file |
| Playlist | Places songs in events, with an order number |

Only events marked **Published** are shown. Changes to the sheet take a few minutes to appear, because Google caches published sheets.

## Project files

| File | What it does |
|---|---|
| `index.html` | The whole app: page, styles, and code |
| `manifest.json` | Lets the app be installed to the home screen |
| `sw.js` | Service worker: caches files so the app installs and opens offline |
| `icons/` | App icons |

## Run it on your computer

You need Python 3 installed. From this folder, run:

```
python -m http.server 8000
```

Then open http://localhost:8000 in your browser. Opening `index.html` by double-clicking will not work properly, because the service worker only runs over `http://localhost` or `https`.

## Deploy and update

The app is hosted free on GitHub Pages from the `main` branch.

To publish a change:

1. Edit the files.
2. If you changed any app file, update the cache version name in `sw.js`, so phones fetch the new version.
3. Commit and push to `main`. The live site updates in a minute or two.

## Notes

- The published sheet data is public by design, so nothing private should be stored in it.
- Drive files must be shared as **Anyone with the link can view**. YouTube videos must be **Unlisted**, not Private.
- Version 1 supports the four standard voice parts only.

## Credits

Built for the MCGI Music Department choir.
