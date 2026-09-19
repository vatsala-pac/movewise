# MoveWise

## The Problem

Singapore's rail and bus network is one of the most extensive and reliable in the world, but when something does go wrong — such as a signal fault, track fault, or sudden service disruption — commuters are often left to fend for themselves: piecing together information from scattered announcements, operator social media, or word of mouth on a crowded platform, with no clear next step offered to them.

At the same time, with Singapore's ageing population and the everyday range of people riding the network — such as wheelchair and stroller users, someone recovering from a leg injury, or an elderly commuter who simply needs to sit — the "fastest route" is not always the right route for everyone.

Existing transport apps compound both problems: they are often reactive, surfacing a delay only after a commuter is already stuck in it, and one-size-fits-all, applying the same routing logic regardless of who is actually travelling.

## Solution

MoveWise is a personalised public transport companion that helps commuters make informed decisions before and during their journey, turning real-time conditions into actionable recommendations tailored to each person's needs.

Commuters can save **Personalised Accessibility Profiles**, such as wheelchair, stroller, low walking, or minimal stairs preferences, which apply automatically to future trips. **Comfort Mode** lets them adjust needs for a single journey, such as wanting a seat or fewer transfers, without changing their saved profile.

**Crowding Alerts & Forecasts** show current and expected crowd levels before travel, and when disruptions occur, **Smart Disruption Rerouting** offers practical alternatives.

**Smart Bus Bridge** complements this by identifying real alternative bus services, stops, walking distances, and interchange points.

Once on the move, **Find My Exit** recommends the station exit that minimises walking to the commuter's actual destination. **Notify Me at My Stop** automatically alerts commuters as their destination approaches, helping them avoid missing their stop if they fall asleep.

Finally, the **Live Transit Map** visualises the MRT/LRT network and its disruptions through an animated network view.

## Uniqueness of Solution

### Personalised by Default

* Commuters create an accessibility profile once in **Settings** — such as wheelchair, stroller, low walking, or minimal stairs — and it applies automatically to every journey they plan.
* Personalisation stays flexible rather than restrictive.
* **Accessibility for this trip** also allows commuters to temporarily adjust their needs without changing their saved profile.

### From Information to Action

* MoveWise focuses on answering **"What should I do next?"**
* It suggests an alternative route instead of simply reporting a disruption.
* **Find My Exit** picks the exit closest to the commuter's actual destination, rather than showing a static station map.
* **Crowd Forecasts** help commuters anticipate conditions, not just see current crowd levels.

### Proactive Disruption and Crowd Awareness

* Information reaches commuters before they get stuck.
* The **Transit Map** shows the MRT/LRT network as a live animated digital twin, so disruptions are visible across the whole network instead of being buried in a status list.
* **Crowd Forecasting** shows whether a station may become more crowded before the commuter arrives.

### Accessibility and Comfort Beyond Route Planning

* **Comfort Mode** extends LTA's **"May I Have A Seat, Please?"** initiative into a digital experience.
* Users can state a need such as **"I may need to sit"** or **"fewer transfers"**, and MoveWise presents a **Fastest Route** alongside a **More Comfortable Route**.
* Commuters never have to explain why they have those needs.

To ensure that recommended routes are comfortable and accessible, we implemented an **Accessibility Points System**:

1. **Starting Score**

   * Every route starts with **100 points**.
   * Points are deducted based on the accessibility needs selected by the commuter.

2. **Wheelchair & Stroller**

   * If **Wheelchair** or **Stroller** is selected and the route passes through a station with a broken lift:

     * **Wheelchair:** -60 points
     * **Stroller:** -35 points
   * If MoveWise specifically reroutes the commuter around the lift outage, the route receives an **+8 bonus** instead.

3. **Minimal Stairs**

   * If **Minimal Stairs** is selected, the route loses **8 points** for every cross-platform transfer required.

4. **Low Walking**

   * If **Low Walking** is selected, the route loses approximately **1 point for every 10 metres** of walking beyond 300 metres.

5. **Final Score**

   * The final accessibility score is capped between **0 and 100**.
   * If no accessibility needs are selected, no accessibility deductions apply and the route receives a score of **100**.

### Recovery When Journeys Go Wrong

* **Smart Bus Bridge** finds a practical fallback during disruptions, using real bus services, stops, walking distances, and interchange points to turn a dead end into a detour.
* **Notify Me at My Stop** covers commuters who deviate from the plan, such as by falling asleep. It uses the planned route for a live countdown and triggers a full-screen alert, vibration, and chime as the destination approaches.

### Interactive Distance Tracker

* The **My Travel** section includes an interactive distance tracker that records the distance travelled based on the method of transport, such as:

  * 🚌 Public transport
  * 🚶 Walking
  * 🚴 Cycling
* An **Insights** section provides an overall view of weekly travel patterns.
* This feature encourages commuters to consider a combination of public transport, walking, and cycling as part of their everyday journeys.

## Technology Stack

### This Prototype

MoveWise currently uses:

* **[Leaflet.js](https://leafletjs.com/)** for live-location mapping.
* **Lucide** for a consistent line-icon system.
* The browser's **Web Audio, Vibration, and Notification APIs** to power the stop-alert system.
* **MRT/LRT station network, bus stop, bus service, and lift/escalator outage data** to support journey planning and disruption recovery.

### Path to Production

MoveWise can be developed further using:

* **React** for the interactive front-end.
* **Tailwind CSS** for responsive and consistent UI design.
* **Supabase** for backend services, database management, and real-time data handling.
* **Transport APIs** to retrieve live bus/train information, service disruptions, and other transport updates.
* **Mapping and routing APIs** to support route planning and the **Find My Exit** feature.
