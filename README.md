# Goals (stand-alone PWA)

A static, offline-capable web app for logging S / AD / M entries. All data lives in the browser's localStorage on the device (key `goals.entries.v1`). On first run it shows a welcome card: Import backup or Start fresh.

## Files
- `index.html`: the whole app (inline CSS and JS, no external libraries)
- `manifest.webmanifest`: install metadata (standalone, start_url/scope `./`)
- `sw.js`: service worker. Network-first, with a cache fallback for offline use.
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`

## Run locally
    python3 -m http.server 8000   # then open http://localhost:8000/

## Deploy (GitHub Pages)
Push these files to a repo and enable Pages. Relative paths mean it works under `/<repo>/`. HTTPS is required for install and offline use.

## Install on Pixel
Open the URL in Chrome, then tap ⋮ and choose "Install app" or "Add to Home screen".

## Features
Log (S/AD/M, date defaults to the local date, optional note), filter All/S/AD/M, days-since counter, stat tiles, yearly totals, monthly stacked bars with a year toggle, gap histogram, the last 5 entries, delete latest (with confirm) plus Undo, Export JSON/CSV, Import JSON/CSV (merges and skips exact date+type+note duplicates).

## Caveats
- Data is per-browser and per-device. Clearing Chrome site data or uninstalling deletes it, so export backups regularly.
- Undo only works until the next log or a page reload.
- After an update, bump `CACHE` in sw.js. Network-first means online users get new files right away anyway.
