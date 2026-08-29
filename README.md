# MoveWise — Smart Travel Companion

An interactive click-through prototype of **MoveWise**, a Smart Travel Companion app built for LTA's NEBULA X Hackathon ("Problem Statement 02 — Smart Travel Companion").

**[Live demo →](https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/)** *(update this link once GitHub Pages is live — see setup steps below)*

## What's in this repo

- `index.html` — the entire app. A single self-contained HTML/CSS/JS file: a phone-frame mockup you click and type into right in the browser. No build step, no backend, no dependencies to install.

## Running it locally

Just open `index.html` in any modern browser — double-click the file, or run a tiny local server if you prefer:

```
python3 -m http.server 8000
```

then visit `http://localhost:8000`.

## Deploying with GitHub Pages

This repo is set up to be served directly by GitHub Pages from the root of the default branch. In the repo's **Settings → Pages**, set the source to your default branch and the `/ (root)` folder — GitHub will publish `index.html` automatically.

## Opening it on your phone

Once GitHub Pages is live, the link at the top of this file works exactly the same on a phone browser as on desktop — just open it in Safari (iOS) or Chrome (Android). It's a normal responsive web page, not an app-store app, so there's nothing to install.

For an app-like icon on your home screen (optional):
- **iOS (Safari):** open the link → tap the Share icon → **Add to Home Screen**.
- **Android (Chrome):** open the link → tap the ⋮ menu → **Add to Home screen** (or **Install app**, depending on your Chrome version).

Either way it still just opens the same web page full-screen — there's no offline mode or native functionality, since this is a click-through design prototype.

## Features

- Real 181-station MRT/LRT network graph with genuine shortest-path routing
- Accessibility-aware trip planning (wheelchair/stroller/low-walking/minimal-stairs constraints)
- **Comfort Mode** — a Journey Comfort Score, Fastest-vs-Most-Comfortable route comparison, and comfort-biased missed-transfer recovery, built around Singapore's "May I Have A Seat, Please?" sticker initiative
- Live-style platform crowding, crowd forecasting, and "Near me" geolocation views
- Missed-transfer / disruption recovery engine, with a "Simulate NSL disruption" control (in the Demo controls panel beside the phone) for demoing it
- "Find my exit" destination-aware MRT exit recommendation
- EZ-Link → eWallet linking UI (mock)
- Two accessibility/appearance modes — Standard and Simple & Large (larger text, bigger tap targets, extra contrast) — each with its own Light/Dark theme
- Minimalist black-and-white design system throughout, with color reserved only for real information (MRT line colors, service-status states)
