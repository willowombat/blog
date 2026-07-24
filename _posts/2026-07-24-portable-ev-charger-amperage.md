---
layout: post
title: "Changing the amperage on a touch-button portable EV charger"
date: 2026-07-24
categories: home
tags: [ev, home, howto]
---

Got a 32A portable Level 1/2 EV charger for the house (J1772, NEMA 14-50 with a 5-15 adapter for regular outlets). The unit doesn't have physical buttons — just a single touch-sensitive spot on the display — so the amperage adjustment isn't obvious the first time.




Here's the sequence that actually works:

1. Unplug the connector from the vehicle first. The button won't respond to amperage changes while it's connected.
2. Long-press the touch button (about 2-4 seconds) until the display enters adjustment mode — the amperage number starts blinking.
3. Tap the button repeatedly to step through the available currents: 6A, 8A, 10A, 13A, 16A, 20A, 24A, 32A, looping back around.
4. Once the number you want is showing, long-press again to confirm and save.
5. If you sit on the adjustment screen too long without pressing anything (4-10 seconds), it times out and drops back without saving — just start over.

Plug the connector into the car after that and it charges at whatever you set.

Filing this here mostly so future-me doesn't have to relearn it from scratch next time the setting needs to change.
