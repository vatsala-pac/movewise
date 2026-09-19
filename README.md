# MoveWise ♿🚇

### Your journey shouldn't break just because the network does.

**MoveWise** is a smart, accessibility-first commuter companion built for the **LTA NEBULA X Hackathon — Problem Statement 2: Smart Commuter Companion**.

MoveWise does more than tell commuters that something has gone wrong.

It understands **who is travelling, what they need, what has changed, and what they should do next.**

When a disruption, lift outage, crowding or weather condition affects a journey, MoveWise proactively recommends an alternative route tailored to the commuter — including the walking, bus and MRT legs needed to actually complete the journey.

# 🌐 Live Demo

**Live application:**
`https://storage.googleapis.com/qwiklabs-gcp-03-b6b8c6bf731e-movewise/index.html`
---

## 👤 Meet Ginie

> **"I don't need another app to tell me there's a problem. I need to know what I'm supposed to do now."**

**Ginie, 20**, is a polytechnic student rushing to her first real job — her internship.

She's active, constantly moving around Singapore and rarely plans her day around transport disruptions. Between school, activities, friends and her internship, she depends heavily on Singapore's public transport network.

But being active also means injuries happen.

A sprained ankle.

A sore knee.

A minor injury that makes stairs painful.

A day when walking further than usual simply isn't realistic.

For Ginie, accessibility isn't always a permanent characteristic. **Her mobility needs can change depending on the day.**

That's where MoveWise comes in.

### Ginie's journey

On a normal day:

**Home → MRT → Internship**

Simple.

But imagine she is rushing to her internship with an injured ankle.

She selects:

> ♿ **I need step-free access**

MoveWise adapts her journey around that requirement.

Then, halfway through her trip, something changes:

> ⚠️ **Pioneer MRT lift is unavailable.**

A conventional journey planner might simply show the disruption.

MoveWise asks:

**"How does this affect Ginie?"**

It recognises that a lift outage is significantly more important to someone who requires step-free access.

Instead of leaving Ginie to figure it out herself, MoveWise searches for another way.

For example:

**MRT → accessible bus connection → nearby station → functioning lift → destination**

The exact alternative is determined from available transport data rather than forcing every commuter onto the same route.

### The result

Ginie doesn't have to stand on a platform searching through multiple apps while already running late.

She gets:

* What happened
* Why her original route no longer works for her
* An accessible alternative
* Step-by-step instructions
* Additional travel time
* Walking distance
* Accessibility score
* The reason the alternative was selected

**MoveWise turns a disruption into a decision.**

---

# 🚨 The Problem

Singapore's public transport network works extremely well on an ordinary day.

The difficult journey is the one that isn't ordinary.

A signal fault.

A train disruption.

A station exit closure.

A broken lift.

A sudden downpour.

A crowded platform.

A commuter with an injury.

The information may already exist — but the commuter is still left to answer:

> **"What am I supposed to do now?"**

The challenge brief asks for a commuter companion that is **proactive, provides decision support, handles planned and unplanned events, and is tailored to the individual commuter.**

MoveWise is built around exactly that idea.

---

# 💡 Our Solution

MoveWise moves from:

**Reactive information**

> "There is a disruption on the EWL."

to:

**Proactive decision support**

> "Your route is affected. Take this alternative instead. It adds 11 minutes and still meets your accessibility requirements."

The difference is simple:

### We don't just tell you what happened.

### We tell you what to do next.

---

# ✨ Key Features

## 🗺️ Personalised Multi-Modal Routing

MoveWise plans journeys from **door to door**, rather than simply from station to station.

Routes can combine:

* 🚶 Walking
* 🚌 Bus
* 🚇 MRT
* 🚲 Cycling

The route adapts to the commuter's selected preferences and current network conditions.

The hackathon requires actual journey planning and revised routes when conditions change, including the walking legs at both ends of the journey.

---

## ♿ Accessibility-Aware Routing

Accessibility is not treated as a separate feature.

It changes the route itself.

Users can specify needs such as:

* Wheelchair
* Lift-only access
* Minimal walking
* Fewer stairs
* Step-free access

MoveWise then considers these requirements when evaluating routes.

### Example

A normal route may be:

**MRT → Pioneer MRT → destination**

But if the required Pioneer MRT lift is unavailable:

**❌ Normal route — inaccessible**

MoveWise can instead search for an alternative involving:

**🚌 Bus → accessible MRT station → functioning lift → destination**

The route's accessibility score changes accordingly.

### Accessibility principle

> **The fastest route isn't always the most usable route.**

For someone who requires a lift, a route with a functioning lift can be more valuable than a shorter route that depends on a broken one.

---

# 🧪 Lift Breakdown Simulation

Because major disruptions may not occur during judging, MoveWise includes a clearly labelled demonstration mode.

### Pioneer MRT Lift Breakdown

Toggle:

**OFF → Pioneer MRT operating normally**

**ON → Pioneer MRT lift unavailable**

When the simulation is enabled, MoveWise treats the Pioneer MRT lift as unavailable and recalculates affected journeys.

For wheelchair/lift-dependent users, the app searches for an alternative rather than simply displaying an outage notice.

This allows judges to experience the accessibility-routing logic immediately.

The hackathon brief explicitly allows replay/injected test data for demonstrating disruption scenarios, provided the simulation is clearly labelled.

---

# 🔔 Proactive Disruption Alerts

MoveWise doesn't wait for commuters to discover a disruption themselves.

When an active journey is affected, MoveWise can notify the commuter and provide a revised route.

### Instead of:

> ⚠️ EWL disruption

MoveWise provides:

> ⚠️ **Your journey has been affected**
>
> The route you planned is no longer suitable.
>
> **We've found an alternative for you.**
>
> 🚌 Take Bus 193
> 🚇 Continue from Pioneer MRT
> ♿ Use the accessible entrance
>
> **+12 min**
>
> **Accessibility: 94/100**

The exact route and information are generated from the available transport data.

---

# 🧠 Personalised Decision Support

The same disruption can have completely different consequences for different commuters.

For example:

### Commuter A

No accessibility requirements.

A lift outage may be a minor inconvenience.

### Commuter B

Requires a wheelchair-accessible route.

The same lift outage could make the station unusable.

MoveWise therefore evaluates disruptions against the **individual commuter**, rather than treating every user the same.

---

# 📊 Route Scoring

MoveWise evaluates routes using multiple factors rather than simply choosing the shortest journey.

Depending on the commuter's preferences, the route can consider:

| Factor            | Why it matters                                             |
| ----------------- | ---------------------------------------------------------- |
| Accessibility     | Can the commuter physically use the route?                 |
| Walking distance  | Important for injured or mobility-constrained users        |
| Stairs            | Avoided when required                                      |
| Lift availability | Critical for step-free users                               |
| Transfers         | Fewer transfers can reduce complexity                      |
| Travel time       | Helps commuters make time-sensitive decisions              |
| Bus availability  | Provides alternatives during rail disruptions              |
| Crowding          | Helps commuters avoid uncomfortable or difficult transfers |
| Weather           | Can influence walking and cycling decisions                |

The result is a route that is optimised for **the commuter**, not simply the map.

---

# 📍 Data & Technology

MoveWise is built around real Singapore transport and geospatial data.

### LTA DataMall

Relevant datasets include:

* `TrainServiceAlerts`
* `BusArrival`
* `BusServices`
* `BusRoutes`
* `BusStops`
* `PCDRealTime`
* `PCDForecast`
* `v2/FacilitiesMaintenance`
* `TrainStation`
* `TrainStationExit`
* `BusStopLocation`
* `CoveredLinkWay`
* `CyclingPath`
* `Footpath`

The hackathon specifically identifies `TrainServiceAlerts` as the official structured train disruption feed and `FacilitiesMaintenance` as the source for MRT lift maintenance information.

Bus arrival data also provides useful accessibility and crowding information, including wheelchair-accessible vehicle information and passenger load.

### OpenStreetMap

OpenStreetMap provides the geospatial foundation for:

* Footpaths
* Crossings
* Stairs
* Lifts
* Covered walkways
* Cycling paths
* Pedestrian infrastructure

OpenStreetMap is required as the geospatial base for this problem statement.

**© OpenStreetMap contributors**

### OneMap

Singapore's official mapping service can support:

* Geocoding
* Reverse geocoding
* Walking routes
* Cycling routes
* Public transport routing

### Weather

Weather conditions can influence the walking portion of a journey.

MoveWise can use Singapore's open government weather data to account for changing conditions.

---

# 🏗️ Architecture

```text
                    ┌──────────────────────┐
                    │       MoveWise       │
                    │   Mobile Web App     │
                    └──────────┬───────────┘
                               │
                    ┌──────────▼───────────┐
                    │   Routing Engine     │
                    │                      │
                    │ Personal preferences │
                    │ Accessibility        │
                    │ Travel time          │
                    │ Walking              │
                    │ Transfers            │
                    └──────────┬───────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
       ┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
       │ LTA DataMall│ │ OpenStreetMap│ │   OneMap    │
       │             │ │              │ │             │
       │ Disruptions │ │ Footpaths    │ │ Geocoding   │
       │ Bus data    │ │ Accessibility│ │ Routing     │
       │ Lift data   │ │ Walkways     │ │             │
       └─────────────┘ └──────────────┘ └─────────────┘
                               │
                    ┌──────────▼───────────┐
                    │   Decision Support   │
                    │                      │
                    │ "What changed?"      │
                    │ "Does it affect me?" │
                    │ "What should I do?"  │
                    └──────────────────────┘
```

---

# 📱 Designed for Real Commuters

MoveWise is **mobile-first**.

A commuter should be able to use it:

* With one hand
* On a small screen
* While walking
* While standing on a platform
* In bright sunlight
* During a stressful disruption

The challenge explicitly requires the application to be a mobile-first web application and notes that judging takes place on a real phone browser.

The interface therefore prioritises:

**Clear → Immediate → Actionable**

rather than overwhelming the user with information.

---

# 🎯 Our Design Philosophy

### 1. Don't just report.

**Recommend.**

### 2. Don't assume everyone travels the same way.

**Personalise.**

### 3. Don't treat accessibility as an afterthought.

**Build it into routing.**

### 4. Don't wait for commuters to discover problems.

**Be proactive.**

### 5. Don't hide the trade-offs.

**Show the time, distance and accessibility impact.**

---

# 🚀 Example Journey

### Ginie's normal journey

```text
HOME
  │
  ▼
🚶 Walk
  │
  ▼
🚇 MRT
  │
  ▼
🏢 Internship
```

### Something changes

```text
🚨 Pioneer MRT lift unavailable
```

MoveWise detects:

> Ginie requires step-free access.

Instead of continuing with the original route:

```text
❌ Original route
Pioneer MRT
↓
Unavailable lift
↓
Inaccessible
```

MoveWise recalculates:

```text
🚌 Alternative bus
       ↓
🚇 Accessible MRT station
       ↓
♿ Functioning lift
       ↓
🚇 Continue journey
       ↓
🏢 Internship
```

And tells Ginie:

> **Your route has changed because Pioneer MRT's lift is unavailable.**
>
> **We've found an accessible alternative.**
>
> +12 min
> ♿ 94/100 accessibility
> 🚶 450 m walking

The goal isn't to make Ginie understand the transport network.

**The goal is to make her journey understandable.**

---

# 🧪 Demo Flow

For judging, MoveWise can demonstrate the following scenario:

### Step 1

Select:

**♿ Wheelchair / Lift Only**

### Step 2

Plan a journey that involves Pioneer MRT.

### Step 3

Show the normal route.

### Step 4

Enable:

**🧪 Simulate Pioneer MRT Lift Breakdown**

### Step 5

MoveWise identifies:

> 🚨 Pioneer MRT lift unavailable

### Step 6

The original route is downgraded for accessibility.

### Step 7

MoveWise searches for an alternative route using available bus/MRT connections.

### Step 8

The accessible alternative is presented with:

* Route instructions
* Accessibility score
* Travel-time difference
* Walking distance
* Reason for rerouting

### Step 9

Turn the simulation OFF.

The normal route becomes available again.

---

# 🛠️ Getting Started

## Prerequisites

* Node.js
* npm
* A modern web browser

## Installation

```bash
git clone <YOUR_REPOSITORY_URL>

cd MoveWise

npm install
```

## Run locally

```bash
npm run dev
```

Then open the local development URL shown in your terminal.

## Production build

```bash
npm run build
```

# 📚 Data Sources

MoveWise uses official and open data sources wherever possible.

| Source        | Purpose                                                        |
| ------------- | -------------------------------------------------------------- |
| LTA DataMall  | Public transport, disruptions, buses, stations and maintenance |
| OpenStreetMap | Pedestrian and geospatial data                                 |
| OneMap        | Singapore mapping and routing                                  |
| data.gov.sg   | Government open data and weather                               |
| Google Cloud  | Application deployment and cloud infrastructure                |

All third-party data is used according to the relevant terms, licences and attribution requirements.

---

# 🗺️ OpenStreetMap Attribution

Map and geospatial data:

**© OpenStreetMap contributors**

OpenStreetMap data is licensed under the Open Data Commons Open Database License (ODbL).

---

# 🌱 Why MoveWise?

A disruption isn't the same problem for everyone.

A broken lift might be a minor inconvenience for one commuter and a complete barrier for another.

A 10-minute walk might be nothing on one day and impossible on another.

A crowded platform might be acceptable to one person and overwhelming to another.

**MoveWise is built around that difference.**

Instead of asking:

> **"What is the fastest route?"**

we ask:

> **"What is the best route for this commuter, right now, given what is happening?"**

---

# 👥 Team

Built for the **LTA NEBULA X Hackathon**

**Problem Statement 2 — Smart Commuter Companion**

---

## ❤️ MoveWise

### **When the journey changes, MoveWise changes with you.**
