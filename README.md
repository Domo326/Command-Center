# Command Center

A single-file, offline-first tour management app for field and tour managers in experiential marketing. Track your route, giveaway inventory, daily event recaps, and a 3D print queue from one installable web app.

Built as a companion to [Premium Tracker](https://github.com/Domo326/Premium-Tracker-Verizon) and sharing the same architecture: one HTML file, no build step, no backend, no account.

## What it does

**Home** - A dashboard showing your current or next event with a countdown, automatic weather for the event city, low-stock alerts, and quick stats across every section of the app.

**Tour** - Your route as a list of stops. Each stop holds the event name, city, venue, start and end dates, hotel plus confirmation number, truck parking notes, and free-form notes. Weather is pulled automatically per stop (forecast for upcoming dates, archive data for past ones). Stops are split into "Up next" and past events.

**Inventory** - Giveaway (premium) tracking. Add items with a starting quantity and a low-stock threshold. Log batches given out or restocks using quick-tap amounts or a custom number. Each item shows a remaining-stock progress bar, and the Inventory tab icon shows a red dot whenever anything falls to or below its threshold. Item names are matched to an icon automatically (typing "bottle" or "tote" picks the right one), and you can override it.

**Recap** - A structured form for end-of-day event reporting: attendance estimate, consumer interactions, QR scans, premiums distributed, weather, highlights, issues, and staff. Generating a recap formats everything into a clean text block and copies it to your clipboard, ready to paste into an email or report within the 24-hour reporting window. All past recaps are saved and viewable.

**PrintNest** - A lightweight queue for a 3D printing side business. Capture ideas on the road and move each job through Idea, Queued, Printing, and Done. Jobs can be tagged with a printer (H2D, X1C, P1S, A1, A1 Mini, Resin) and notes.

## How it works

- Single `index.html` file. React 18 and Babel Standalone load from CDN and compile the JSX in the browser. Tailwind CSS via CDN for utility classes. No build step, no dependencies to install.
- All data persists in `localStorage` under the `command:` namespace. Nothing leaves the device; the app works fully offline once loaded.
- Weather comes from the free Open-Meteo geocoding, forecast, and archive APIs. No API key required. Geocoding results are cached for 60 days, past-date weather forever, and future-date weather for 6 hours to keep requests minimal.
- Three themes (Dark by default, Light, Ocean) cycle from the theme button. Layout is responsive: a sidebar on tablets, foldables, and desktop; a bottom tab bar on phones.

## Running it

Open `index.html` in any modern browser. That is the whole deployment.

To host it, push this repo to Vercel (or GitHub Pages, Netlify, etc.) with no build configuration - it is a static file.

To install on a phone, open the hosted URL and use "Add to Home Screen" (Safari) or the install prompt (Chrome/Android).

## Data and privacy

Everything is stored locally in the browser. Clearing site data clears the app. There is no sync, no analytics, and no server.

## Roadmap ideas

- manifest.json and icon set for full standalone PWA install
- Export and import of all data as JSON for backups and device transfers
- CSV export of inventory and recap history
- End-of-tour summary with stats and shareable image export
