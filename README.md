<a id="readme-top"></a>

# MoveWise — Smart Travel Companion

An interactive click-through prototype of **MoveWise**, a Smart Travel Companion app built for LTA's NEBULA X Hackathon ("Problem Statement 02 — Smart Travel Companion").

**[Live demo →](https://vatsala-pac.github.io/movewise/)** 
## About The Project

**MoveWise** is a Smart Travel Companion app built for **LTA's NEBULA X Hackathon** — a direct response to Problem Statement 02, which calls for proactive, personalized decision support for Singapore's commuters instead of one-size-fits-all routing.

Most transport apps stop at telling you what's already happening: a train is delayed, a platform is crowded, a lift is out. By the time you see that, you're already stuck. MoveWise is built around a different premise — that a transit app should behave like it knows the network is *alive*, and knows *you*:

- **It sees the whole system, not just your route.** [Transit Map](#features) renders every MRT/LRT line as a live animated digital twin — real stations in genuine sequence order, colored live by real crowd data, with disruptions visibly propagating across the network the moment they happen, not buried in a status list.
- **It adapts to how you're feeling today, not a fixed profile.** [Comfort Mode](#features) computes a live Journey Comfort Score and offers a Fastest-vs-Most-Comfortable route choice, built around Singapore's own "May I Have A Seat, Please?" initiative — a rider states a need ("I may need to sit," "fewer transfers"), never a diagnosis.
- **It never treats a disruption as a dead end.** A graph-based recovery engine finds a genuine alternate interchange, and a **Smart bus bridge** grounds the fallback in a real LTA bus service, a real stop, and a real walking distance — not a single hard-coded "take bus 66" message.
- **It watches your stop even if you can't.** The "Notify me at my stop" alert (on the Route Details screen) arms a real countdown from your actual route, then fires a full-screen "This is your stop!" takeover, a phone vibration, an audible chime, and a browser notification when your stop is reached — so dozing off on a long ride doesn't mean missing it. A status bar showing stops remaining stays visible across every tab while it's armed.

Every one of those claims is backed by real LTA data, not mocked placeholders: a genuine 181-station MRT/LRT network graph with real shortest-path routing, all 5,205 of LTA's official bus stops (92% with their real published names), 27,324 real stop-service records covering 509 real bus services, and a live lift/escalator outage feed that actually re-scores accessibility routing when a station's lift goes down. Where LTA's public export runs out — roughly the remaining 8% of stops — MoveWise says so plainly rather than quietly guessing, because a hackathon judge (or a real rider) should never have to wonder which numbers on screen are real.

The whole thing ships as a single self-contained HTML file: no build step, no backend, no dependencies to install — open it in a browser, or add it to a phone's home screen for a true full-screen "installed app" feel with zero browser chrome. That was a deliberate choice, not a limitation: it keeps the entire prototype inspectable, forkable, and demo-able from a single link, which matters when judges only get a few minutes with your project.

Design-wise, MoveWise commits to one clean, minimalist black-and-white system with color spent only where it carries real meaning — MRT line colors, live status states, crowd levels — rather than decoration. Every icon across the app (tab bar, map pins, settings, accessibility, wallet, and more) is a real Lucide line icon for one consistent visual identity from the first screen to the last, in Standard and Simple & Large accessibility modes, each with its own Light/Dark theme — built so the same app genuinely works for an elderly commuter who needs a seat and a student sprinting for a train, without maintaining two separate experiences.

**Built for the "Most Unique" and "Best Aesthetics" categories** — a live network digital twin nobody else in the room will have built, disruption recovery that's honest about real vs. illustrative data, and an accessibility story that's actually wired into routing logic rather than a settings toggle that does nothing.

([back to top](#readme-top))

## What's in this repo

- `index.html` — the entire app. A single self-contained HTML/CSS/JS file: a phone-frame mockup you click and type into right in the browser. No build step, no backend, no dependencies to install.
- `manifest.webmanifest` + `icon.png` — makes "Add to Home Screen" launch the app full-screen with no browser address bar, like a real installed app (see below). Upload these alongside `index.html`, at the repo root.

## Running it locally

Just open `index.html` in any modern browser — double-click the file, or run a tiny local server if you prefer:

```
python3 -m http.server 8000
```

then visit `http://localhost:8000`.

([back to top](#readme-top))

## Deploying with GitHub Pages

This repo is set up to be served directly by GitHub Pages from the root of the default branch. In the repo's **Settings → Pages**, set the source to your default branch and the `/ (root)` folder — GitHub will publish `index.html` automatically.

## Opening it on your phone

Once GitHub Pages is live, the link at the top of this file works exactly the same on a phone browser as on desktop — just open it in Safari (iOS) or Chrome (Android). It's a normal responsive web page, not an app-store app, so there's nothing to install.

### Getting the "just the app" look (no webpage chrome)

By default the link shows the full demo page — masthead, mode/theme switcher, the phone mockup with a bezel, the Demo controls panel. Two ways to skip straight to just the app screen, filling the whole browser viewport:

- **Quick way:** open the link with `?app=1` on the end, e.g. `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/?app=1` — this strips every bit of outer page chrome immediately, no bezel, no page background, just the app filling the screen.
- **Add to Home Screen (recommended):** this makes it launch in true "app mode" automatically — full-screen, no browser address bar at all, exactly like tapping a real installed app icon:
  - **iOS (Safari):** open the link → tap the Share icon → **Add to Home Screen**.
  - **Android (Chrome):** open the link → tap the ⋮ menu → **Add to Home screen** (or **Install app**, depending on your Chrome version).
  - Once added, tap the new home screen icon (not the browser) to open it — the manifest and viewport-detection script automatically switch it into app-only mode, so you don't even need the `?app=1` link for this path.

Either way it's still the same web page under the hood — there's no offline mode or native functionality, since this is a click-through design prototype — but visually and interaction-wise it reads as a standalone app, not a website.

([back to top](#readme-top))

<a id="features"></a>

## Features

- **Plan from where you are** — an interactive live map (OpenStreetMap via Leaflet) centred on your real location, showing the nearest MRT/LRT station and bus stop with real walking distances, plus a walking-route line to whichever one you pick. Bus stops are LTA's real, complete stop locations (5,205 stops network-wide, from LTA's official bus stop dataset), and 4,771 of them (92%) show their real name — e.g. "West Grove Pr Sch" — from LTA's official BusStop shapefile, rather than a small hand-picked sample or a generic "Bus Stop [code]" label everywhere
- Bus services shown per stop are grounded in real data at network scale: LTA's official Bus Routes export (27,324 real stop-service records) grounds 4,790 of the app's 5,205 bus stops (92%) with their genuine service list — the stop screen stays clean and focused on arrivals, with no "verified" badges or data-provenance disclosures cluttering the interface
- Multi-modal routing — when your real location is used as the starting point, route options can combine a walk, a bus leg, and the MRT/LRT network, not just walk-to-station; every plan (multi-modal or not) now honestly includes the real walking time from your location to the boarding station, and choosing the nearest bus stop as your starting point (instead of the nearest station) is fully respected
- Real 181-station MRT/LRT network graph with genuine shortest-path routing
- Accessibility-aware trip planning (wheelchair/stroller/low-walking/minimal-stairs constraints)
- **Comfort Mode** — a Journey Comfort Score, Fastest-vs-Most-Comfortable route comparison, and comfort-biased missed-transfer recovery, built around Singapore's "May I Have A Seat, Please?" sticker initiative
- **MRT Live** and **Bus Live** as two distinct taskbar tabs — train line status, accessibility advisories, platform crowding and crowd forecast live under MRT Live; bus stop search, per-stop services and arrivals live under Bus Live — so each mode has its own clear, uncluttered home instead of one combined "Live" screen
- **Transit Map** — a taskbar tab (sitting right beside MRT Live) showing a live animated digital twin of the whole system: every main line drawn as a schematic track with its real stations in genuine sequence order, a moving train indicator per line, and every station dot colored live by the same crowd data used everywhere else in the app; tap any station for its forecast. Flip "Simulate NSL disruption" and watch the affected line turn red/dashed and its stations visibly pulse in real time, right alongside MRT Live and Home
- **Wallet** as the last taskbar tab — a stored-value transit card balance, top up by amount or custom entry, and link/unlink an eWallet (PayNow, GrabPay, Apple Pay) for instant top-ups; once an eWallet is linked, an auto top-up option (below a threshold) appears right underneath it — kept out of sight until there's actually something for it to draw from; a card-balance widget on Home jumps straight into it; a successful top-up shows a brief on-screen confirmation before the balance settles
- Taskbar icons are custom line-art SVGs (house, folded map, train, bus, people-network, card wallet) instead of emoji — crisp at any size, recolor automatically for Light/Dark theme and the active-tab state via `currentColor`
- Every other icon throughout the app — map pins, settings, star/save, bell alerts, wheelchair accessibility, drag handles, edit/delete, wallet, sun/moon theme switch, and more — is a real Lucide (open-source, MIT licensed) line icon rather than an emoji, for one consistent minimalist visual identity across the whole app, not just the tab bar
- **Smart bus bridge** — when a simulated line disruption is active, the recovery plan now includes a genuinely data-grounded bus bridge: the real nearest bus stop to the disrupted stretch (from real station coordinates), a real LTA bus service out of it, real walking distances to and from the bus stops, and an honest label for whether that service is confirmed to serve both ends of the bridge or just the closest real option out of the boarding stop
- Home screen layout: settings gear sits top-right, a personalized greeting ("Hi, [name]" when signed in, "Hi" otherwise) sits right below it, the card balance widget and the Plan a trip/Find my exit buttons come first, with any proactive alert (disruptions, heavy crowding, predicted crowding) below them
- **Bus status** on Home — star a bus stop from Bus Live, or add/remove stops right on Home via an "Edit" toggle with an inline search box, to see next arrivals + live crowd level for each without leaving Home; tapping a saved stop takes you straight into Bus Live for it
- Bus Live's per-stop arrivals use an SG Bus Timing–style always-visible 3-column grid — next 3 buses per service, bold minutes-to-arrival (or "Arr" in green once essentially at the stop) with a deck-type label underneath — instead of needing to expand each service to see its wait times
- Bus Live itself now shows your favourite stops right at the top of the Stops list (tap the star on any stop to save it), plus its own "Allow location access" prompt that lists the real bus stops nearest to you once granted — no need to go via Plan first, and granting it here is shared with Plan's own map card automatically
- 509 real bus services have a genuine LTA-published stop sequence (one real direction each) grounding exactly which stops they serve
- **Bus Route Info** — inside Bus Live, look up any bus number and see every stop it serves in order, with distance along the route and an estimated wait per stop; a clean, uncluttered list with no inline "verified" or data-source messaging
- Live-style platform crowding, crowd forecasting, and "Near me" geolocation views
- Missed-transfer / disruption recovery engine, with a "Simulate NSL disruption" control (in the Demo controls panel beside the phone) for demoing it
- "Find my exit" destination-aware MRT exit recommendation
- **"Notify me at my stop" alert** — arm it on the Route Details screen and it counts down in real time, then fires a full-screen "This is your stop!" takeover, a phone vibration pattern, an audible chime, and a browser notification once your stop is reached; a persistent status bar shows stops remaining on every tab while it's armed — built for anyone who might doze off on a longer ride
- Two accessibility/appearance modes — Standard and Simple & Large (larger text, bigger tap targets, extra contrast) — each with its own Light/Dark theme
- Minimalist black-and-white design system throughout, with color reserved only for real information (MRT line colors, service-status states)

([back to top](#readme-top))
