---
hide:
  - navigation
title: Receive Works, Can't Send
description: You can see other people's messages but yours never get acknowledged, or you see "Max Transmission Reached". This is the most common issue on the mesh — and it's almost always physical placement, not a settings bug.
---

# I Can Receive, But I Can't Send

This is by far the most common issue people bring to the community — "I see everyone else's messages, but mine never get acknowledged," or "I keep getting **Max Transmission Reached**."

!!! success "If you receive ANY messages, your settings are already correct"
    Receiving other people's traffic proves your **region, preset, frequency slot, and primary channel** are all set right — the radio is decoding the mesh. So this is **not** a settings problem. It's an **asymmetric RF link**: you can hear a strong, high-up node, but your lower-power signal can't make the trip back. The fix is physical, not in the app.

If you have *never* received a single message, that's a different problem — recheck your settings on [Start Here, Step 3](/docs/start-here.html#step-3-set-the-arizona-lora-radio-settings) (most likely a wrong Frequency Slot or a renamed primary channel).

---

## What "Max Transmission Reached" / no acks actually means

When you send on the primary channel, your node waits to hear the message relayed back (an implicit acknowledgement). If it never hears the relay after several attempts, it reports **Max Transmission Reached** or shows no acknowledgement. It means your packet isn't reaching a node that can repeat it — your *transmit* path is weak, even though your *receive* path is fine. Big rooftop nodes transmit at several watts from high up; a handheld indoors might be a fraction of a watt behind a wall.

---

## Fix it, in order of impact

### 1. Get outside

Walls, roofs, stucco with metal lath, and Low-E windows all crush a 915 MHz signal. Step **completely outside** and send `test` again. Even a 30-second outdoor test tells you whether your building is the problem.

### 2. Get high — height is might

Elevation beats almost everything else.

- Move to a **second floor, balcony, or rooftop**.
- For a fixed home node, put the antenna in the **attic or on the roof**, not on a desk.
- A basic antenna up high will out-perform an expensive antenna down low, every time.

### 3. Upgrade the antenna

Most handhelds ship with a weak stock antenna (often ~69% efficient). A good whip is the single cheapest range upgrade you can make.

- Handheld: the [Muziworks 17cm whip (~$12)](https://muzi.works/products/whip-antenna-17cm) is the community favorite.
- See the full [Antenna Guide](/docs/recommended-hardware.html#antenna-guide) for rooftop options.

!!! danger "Never transmit with the antenna disconnected"
    Sending without an antenna can fry the radio. Always attach the antenna before powering on or transmitting.

### 4. Add a rooftop relay node

If you live in a dead spot, the real fix is a permanent node up high that relays for you. A [Station G2 or a solar rooftop node](/docs/recommended-hardware.html#rooftop-base-station-nodes) on your roof anchors coverage for your whole area — and it relays *your* handheld back into the mesh. This is the #1 long-term fix.

### 5. Check power, then time of day

- Solar/battery nodes often transmit at very low power (**0.05W–0.5W**). If you've maxed out placement and antenna, a [higher-power node (1W+)](/docs/recommended-hardware.html#rooftop-base-station-nodes) may be the answer.
- The mesh ebbs and flows. If nobody's on when you test, you'll hear nothing. Try again at a busier time.

---

## Still stuck?

Bring it to the community. A quick thread in **#i-need-help** on Discord — with your hardware, antenna, and where you tested from — usually gets you sorted fast.

[:fontawesome-brands-discord: Ask in #i-need-help](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }
