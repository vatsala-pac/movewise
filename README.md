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

([back to top](#readme-top))


## Deploying with GitHub Pages

This repo is set up to be served directly by GitHub Pages from the root of the default branch. In the repo's **Settings → Pages**, set the source to your default branch and the `/ (root)` folder — GitHub will publish `index.html` automatically.

- **Quick way:** open the link with `?app=1` on the end, e.g. `https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/?app=1` — this strips every bit of outer page chrome immediately, no bezel, no page background, just the app filling the screen.
- **Add to Home Screen (recommended):** this makes it launch in true "app mode" automatically — full-screen, no browser address bar at all, exactly like tapping a real installed app icon:
  - **iOS (Safari):** open the link → tap the Share icon → **Add to Home Screen**.
  - **Android (Chrome):** open the link → tap the ⋮ menu → **Add to Home screen** (or **Install app**, depending on your Chrome version).
  - Once added, tap the new home screen icon (not the browser) to open it — the manifest and viewport-detection script automatically switch it into app-only mode, so you don't even need the `?app=1` link for this path.

Either way it's still the same web page under the hood — there's no offline mode or native functionality, since this is a click-through design prototype — but visually and interaction-wise it reads as a standalone app, not a website.

([back to top](#readme-top))

<a id="features"></a>

## Features
- **Plan from where you are** — an interactive live map centred on your real location, showing the nearest MRT/LRT station and bus stop with real walking distances, plus a walking-route line to whichever one you pick. Bus stops are LTA's real, complete stop locations and show their real name — e.g. "West Grove Pr Sch" — from LTA's official BusStop shapefile
- Bus services shown per stop are grounded in real data at network scale: LTA's official Bus Routes export (27,324 real stop-service records) 
- Multi-modal routing — when your real location is used as the starting point, route options can combine a walk, a bus leg, and the MRT/LRT network, not just walk-to-station; every plan (multi-modal or not) now honestly includes the real walking time from your location to the boarding station, and choosing the nearest bus stop as your starting point (instead of the nearest station) is fully respected
- Real 181-station MRT/LRT network graph with genuine shortest-path routing
- Accessibility-aware trip planning (wheelchair/stroller/low-walking/minimal-stairs constraints)
- **Comfort Mode** — a Journey Comfort Score, Fastest-vs-Most-Comfortable route comparison, and comfort-biased missed-transfer recovery, built around Singapore's "May I Have A Seat, Please?" sticker initiative
- **MRT Live** and **Bus Live** as two distinct taskbar tabs — train line status, accessibility advisories, platform crowding and crowd forecast live under MRT Live; bus stop search, per-stop services and arrivals live under Bus Live — so each mode has its own clear, uncluttered home instead of one combined "Live" screen
- **Transit Map** — shows a live animated digital twin of the whole system: every main line drawn as a schematic track with its real stations in genuine sequence order, a moving train indicator per line, and every station dot colored live by the same crowd data used everywhere else in the app; tap any station for its forecast. Flip "Simulate NSL disruption" and watch the affected line turn red/dashed and its stations visibly pulse in real time, right alongside MRT Live and Home
- **Wallet** as the last taskbar tab — a stored-value transit card balance, top up by amount or custom entry, and link/unlink an eWallet (PayNow, GrabPay, Apple Pay) for instant top-ups; once an eWallet is linked, an auto top-up option (below a threshold) appears right underneath it — kept out of sight until there's actually something for it to draw from; a card-balance widget on Home jumps straight into it; a successful top-up shows a brief on-screen confirmation before the balance settles
- **Smart bus bridge** — when a simulated line disruption is active, the recovery plan now includes a genuinely data-grounded bus bridge: the real nearest bus stop to the disrupted stretch (from real station coordinates), a real LTA bus service out of it, real walking distances to and from the bus stops, and an honest label for whether that service is confirmed to serve both ends of the bridge or just the closest real option out of the boarding stop
- **Bus status** on Home — star a bus stop from Bus Live, or add/remove stops right on Home via an "Edit" toggle with an inline search box, to see next arrivals + live crowd level for each without leaving Home; tapping a saved stop takes you straight into Bus Live for it
- Bus Live's per-stop arrivals use an SG Bus Timing–style always-visible 3-column grid — next 3 buses per service, bold minutes-to-arrival (or "Arr" in green once essentially at the stop) with a deck-type label underneath
- Bus Live itself now shows your favourite stops right at the top of the Stops list (tap the star on any stop to save it), plus its own "Allow location access" prompt that lists the real bus stops nearest to you once granted — no need to go via Plan first, and granting it here is shared with Plan's own map card automatically
- Live-style platform crowding, crowd forecasting, and "Near me" geolocation views
- "Find my exit" destination-aware MRT exit recommendation
- **"Notify me at my stop" alert** — arm it on the Route Details screen and it counts down in real time, then fires a full-screen "This is your stop!" takeover, a phone vibration pattern, an audible chime, and a browser notification once your stop is reached; a persistent status bar shows stops remaining on every tab while it's armed — built for anyone who might doze off on a longer ride
- Two accessibility/appearance modes — Standard and Simple & Large (larger text, bigger tap targets, extra contrast) — each with its own Light/Dark theme
- Minimalist black-and-white design system throughout, with color reserved only for real information (MRT line colors, service-status states)

([back to top](#readme-top))
