# 🧽 Hardware: The Scrubber-Mouse

The whole submission hinges on one object: a dish scrubber that is secretly a computer mouse. Here's the concept.

## The core idea

A standard optical mouse already measures exactly what we need: fine-grained X/Y movement at a high sample rate. Dishwashing already produces exactly that movement — short, fast, repeated back-and-forth strokes across a surface. The hardware side of this project is just about getting a mouse's guts to survive that environment and report the motion we care about.

## Build concept

```
   ┌─────────────────────────────────┐
   │     Scrubber housing (outer)     │
   │  ┌─────────────────────────────┐ │
   │  │  Sealed inner chamber        │ │
   │  │   - optical sensor module    │ │
   │  │   - MCU (motion → signal)    │ │
   │  │   - battery or tethered USB  │ │
   │  └──────────────┬───────────────┘ │
   │                 │ sealed cable     │
   └─────────────────┼─────────────────┘
                      │
              USB / Bluetooth → computer
```

- **Sensor**: the optical/laser tracking module from a standard mouse, repositioned to face into the scrubbing motion rather than down at a desk.
- **Enclosure**: the sensor and its PCB sit in a sealed, waterproofed inner chamber inside the scrubber body — the scouring pad stays on the *outside*, doing its actual dish-cleaning job, while the sensor stays dry on the inside.
- **Signal path**: raw X-axis motion feeds steering (lean the scrubber left/right across the sink). Stroke velocity — how fast the back-and-forth motion reverses direction — feeds throttle, using the same stroke-detection logic as the software's mouse controller.
- **Connectivity**: USB for the prototype; Bluetooth HID is the obvious next step so there's no cable dangling over a sink full of water (see Roadmap in the README — we know, we know).

## Why this works

A mouse doesn't care what's moving it. It just reports delta-X and delta-Y. Our software's control scheme (in `game/index.html`) was deliberately built around *two different readings of the same motion stream* — raw position for steering, rate-of-direction-change for power — specifically so that any device that behaves like a mouse, scrubber included, can drive it without any game-side changes.

## Known issues (a.k.a. things we'd fix with more time)

- Water + electronics is a genuinely bad combination and our seal is "hackathon-grade," not "IP67-certified."
- Soap suds reduce optical tracking contrast on certain plate colors. White plates, surprisingly, are the hardest.
- The scrubber occasionally registers a "stroke" when it's just sitting in the dish rack, which we are choosing to call a feature (idle regen).
