# Migraine Diary

A private, single-page migraine tracker (PWA). All data lives in the phone's
browser storage: no server, no account, nothing leaves the device. The hosted
code is fully generic; tap the app title on the phone to personalise the name
(stored locally alongside the entries).

## Files

- `index.html` - the whole app (log, history, charts, insights, CSV export)
- `manifest.webmanifest`, `sw.js`, `icon.svg`, `icon-192.png`, `icon-512.png` - PWA install + offline support

## Getting it onto a phone

The app needs to be served over HTTPS once for "Add to Home Screen" and offline
mode to work. Two easy options:

1. **GitHub Pages (free, simplest).** Push this folder to a repo, enable Pages.
   She visits the URL in Chrome once, taps menu > "Add to Home screen", done.
   It works offline afterwards. The repo can be private data-wise: the app is
   just code, her entries never leave her phone.
2. **Existing web server.** Copy the folder to any HTTPS-served path
   (e.g. `https://yourserver/diary/`) and open that URL on the phone.

## Day to day

- Log from the home screen icon; entries take ~10 seconds (chips, no typing).
- Trends tab: insights, monthly chart, severity, triggers, time-of-day.
- "CSV report" exports a spreadsheet for the neurologist.
- "Backup" / "Restore" moves all data between phones as a JSON file. Do a
  backup occasionally: clearing Chrome's site data would erase the diary.

## Local preview (dev)

`python -m http.server 8377 --directory .` then http://localhost:8377
(service worker is skipped on plain HTTP; everything else works).
