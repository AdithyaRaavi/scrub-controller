# 🧽🖱️ Scrub Controller

### A mouse. Inside a scrubber. For science. And for Dave.

> **TL;DR:** We put a mouse inside a dish scrubber so a husband could game and do chores at the exact same time, using the exact same motion. Scrub harder, go faster. His wife never has to know he spent the whole wash cycle in 1st place.

---

## 🍽️ The Origin Story

Meet **Dave**. Every hackathon team needs a cautionary tale, and Dave is ours.

Dave's hobbies, in order of time invested: gaming, thinking about gaming, and explaining to his wife why the sink still looks like a crime scene. Dave's wife, **Priya**, is a senior software engineer. She ships production code before 9am, reviews pull requests on her commute, and has approximately zero tolerance for a sink full of crusty plates when she gets home. Every evening ends the same way — Priya walks in, surveys the kitchen, and Dave receives a performance review so brutal it makes his actual quarterly review look like a thank-you card. No dishes done means no peace in the house. Everyone in the building has heard it. The neighbors have opinions.

One night, mid-boss-fight, Dave heard Priya's key in the door and had approximately four seconds to make a life-altering decision: pause the game and do the dishes like a responsible adult, or don't, and accept his fate.

Dave chose a third option. Dave chose **science**.

What, he wondered, if the dishes *were* the game? What if the exact motion his wife already yells at him to do — scrubbing a plate, back and forth, back and forth — could *also* be the thing driving his car around a circuit at 300 km/h? He wouldn't be skipping chores to play games. He'd be doing chores *by* playing games. Flawless. Un-nagging-able. A loophole so clean it practically does the dishes itself.

So our team built it: a fully working computer mouse, surgically relocated into the body of an ordinary dish scrubber. From the outside, it's just a slightly suspicious yellow-and-green scrubber sitting by the sink. From the inside, it's a precision input device that tracks exactly how fast and how hard you're scrubbing — and turns that straight into throttle.

Steering is just moving the scrubber left and right across the sink, which, conveniently, is also just... washing a plate. Plausible deniability: 100%. Dishes: done. Lap times: also done.

This repository is the fully documented result of that extremely serious, extremely real emergency.

---

## 🏁 What We Actually Built

**The core idea:** one physical motion drives every game.

| Input | Maps to |
|---|---|
| Scrubber **position** (left ↔ right across the sink) | **Steering** |
| How **fast you scrub back and forth** | **Throttle / power** |

Scrub like you mean it and you accelerate. Ease off and you coast to a stop. Steer by leaning the scrubber the way you'd naturally lean while actually cleaning a plate. No keyboard, no joystick, no buttons — just the chore itself.

### 🕹️ Scrub Arcade — the software side

`game/index.html` is a self-contained, browser-playable arcade built to prove the control scheme works, with four fully 3D mini-games sharing the exact same controller:

- **🏎️ Redline Circuit** — 5-lap night circuit race against 4 rivals who actively fight you for position.
- **🚣 River Row Sprint** — out-paddle 3 rivals down a winding river, dodging logs and grabbing buoy boosts.
- **⛷️ Slope Rush** — carve a real downhill run against 2 rival skiers, dodging trees and moguls.
- **🌊 Slalom Jet Ski** — thread 14 buoy gates across open water against 2 rivals.

Every game reads the same mouse-position-and-scrub-speed signal, which is exactly what the physical controller sends — so the software runs identically whether you're testing with a regular mouse or the actual scrubber hardware.

### 🧽 The hardware side

The actual submission is the controller itself — a real optical mouse sealed inside a dish scrubber housing. See [`HARDWARE.md`](./HARDWARE.md) for the build concept, sensor placement, and the waterproofing problem nobody warned us about.

---

## 🎮 Try It

No install, no build step — it's one HTML file.

1. Clone this repo.
2. Open `game/index.html` in any modern browser (or run a tiny local server: `python3 -m http.server`, then visit `http://localhost:8000/game/`).
3. Pick a game, drag your mouse left/right to steer, scrub it back and forth fast to accelerate.
4. Optional but encouraged: do this with an actual wet scrubber in your actual sink, using the actual hardware, while your actual spouse is on their way home.

---

## 🛠️ Tech Stack

- **Three.js** (r128) — real-time 3D rendering, chase cameras, lit scenes
- Vanilla **HTML / CSS / JavaScript** — no framework, no build tooling, one file
- A custom mouse-position + stroke-velocity controller shared across every game
- Hardware: a standard optical mouse module, rehoused — see [`HARDWARE.md`](./HARDWARE.md)

---

## 🏆 Hackathon Submission

| | |
|---|---|
| **Hackathon** | _add your hackathon name here_ |
| **Track / Category** | _e.g. Hardware, Gaming, "Most Unnecessary but Delightful"_ |
| **Team** | _add your team name + members here_ |
| **Problem statement** | Division of household labor is hard to gamify. We fixed that. |
| **One-line pitch** | A mouse inside a scrubber that turns dishwashing into a racing game — the harder you scrub, the faster you go. |

*(Fill in the blanks above before you submit — the judges will want to know who to high-five.)*

---

## 🗺️ Roadmap

- [ ] Waterproof the sensor properly (current prototype is "optimistically sealed")
- [ ] Bluetooth version so Dave doesn't trip over a USB cable mid-race
- [ ] Leaderboard synced to actual dish count, for accountability
- [ ] A companion scrubber for Priya, because competitive multiplayer chores sounds incredible
- [ ] Ask Priya for her honest review of this README

---

## ⚖️ License

MIT — see [`LICENSE`](./LICENSE). Use it, remix it, build your own chore-powered controller. If your spouse asks, tell them it was Dave's idea.
