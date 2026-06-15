---
hide:
  - navigation
title: Start Here
description: The first 30 minutes on the Arizona mesh. A single, in-order guide that takes you from an unboxed radio to sending your first message and seeing it acknowledged.
---

# Start Here: Your First 30 Minutes

New to the Arizona mesh? This is the page to get going. Follow the steps **in order, top to bottom** (don't skip ahead). By the end you'll have a working node, the right Arizona settings, and proof that the mesh can hear you. Once you're connected and want to fine-tune your node, the deeper settings reference (roles, broadcast intervals, MQTT) lives on [Additional Settings](/docs/additional-settings.html).

!!! info "What you need before you begin"
    - A Meshtastic radio. Don't have one? See [Recommended Hardware](/docs/recommended-hardware.html). You can get on the mesh for about $30.
    - The Meshtastic app on your phone (links in Step 2).
    - About 30 minutes. Most of it is waiting for firmware to flash.
    - Our Discord, which is where the Arizona radio settings live (link in Step 3).

[:fontawesome-brands-discord: Join the Arizona Meshtastic Discord](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }

---

## Step 1: Flash the latest firmware

1. Open the [**Meshtastic Web Flasher**](https://flasher.meshtastic.org) in **Google Chrome** (other browsers often fail to connect to the serial port).
2. Select your device, click **Flash**, and follow the prompts.

!!! warning "Leave \"Install Meshtastic UI\" UNCHECKED on most devices"
    The web flasher may offer an **"Install Meshtastic UI"** option. **Meshtastic UI (MUI)** is a separate on-device interface built for **color touchscreen** devices like the LilyGO T-Deck and SenseCAP Indicator. It is **not** meant for the small OLED screens on common boards like the **Heltec V3/V4** or RAK handhelds, and installing it there can leave you with a blank screen or a boot loop. Unless you have a touchscreen device and specifically want the on-device UI, leave this **unchecked** and use the phone app for the interface. If your screen is already stuck or blank, re-flash with it off. See [FAQ → Flashing problems](/docs/faq.html#flashing-gotchas).

!!! danger "Never transmit without an antenna attached"
    Powering on or sending with the antenna disconnected can permanently damage the radio. Always screw the antenna on first.

!!! tip "Back up your keys before re-flashing"
    Flashing can wipe your settings, including your node's identity keys. Export/back up your configuration from the Meshtastic app first, so you don't reappear as a brand-new node.

---

## Step 2: Install the app and pair over Bluetooth

| Platform | Link |
|:---------|:-----|
| **Android** | [Google Play Store](https://play.google.com/store/apps/details?id=com.geeksville.mesh) |
| **iOS** | [Apple App Store](https://apps.apple.com/us/app/meshtastic/id1586432531) |

1. Turn on your radio.
2. Open the app, tap **+**, and select your device to pair over Bluetooth.
3. If prompted for a pairing code, the default is usually printed on your device or in its documentation.
4. You should now see your node in the app.

---

## Step 3: Get the Arizona radio settings from Discord

This is where most new nodes go wrong, and it's why this step points you to Discord.

To join the Arizona mesh you need the community-specific **region, preset, and frequency slot**. We keep those values in our [Discord server](https://discord.gg/HrKtyuFEQk) so they stay coordinated and current, then you enter them in the app.

In your Meshtastic app, open **Settings → LoRa (Radio Configuration)** and set these:

<div class="azmsh-locked">
  <div class="azmsh-settings">
    <p class="azmsh-group-title">Arizona LoRa settings</p>
    <div class="azmsh-row"><span class="azmsh-label">1. Region:</span> <span class="azmsh-value">US</span></div>
    <div class="azmsh-row"><span class="azmsh-label">2. Preset:</span> <span class="azmsh-value">ExamplePreset_AZ</span></div>
    <div class="azmsh-row"><span class="azmsh-label">3. Frequency Slot:</span> <span class="azmsh-value">00</span></div>
  </div>
  <div class="azmsh-overlay">
    <span class="azmsh-overlay-text">🔒 Arizona radio settings are shared in Discord</span>
    <a class="md-button md-button--primary" href="https://discord.gg/HrKtyuFEQk">Join The Discord</a>
  </div>
</div>

!!! warning "The Frequency Slot is the #1 missed setting"
    Lots of people set the preset correctly but leave the **Frequency Slot** at `0`/auto, so they land on the wrong frequency and can't hear anyone. Set it to the exact slot listed in Discord.

    **iOS gotcha:** the Slot field is text entry. **Double-tap the existing value** to select it, then type the correct slot. Leave **Frequency Override** blank or `0`; entering a value there *locks* the Slot field. "Override" and "Slot" are different fields.

---

## Step 4: Set up your primary channel

Open **Settings → Channels** and configure the **primary** channel (index 0) using the values from Discord.

<div class="azmsh-locked">
  <div class="azmsh-settings">
    <p class="azmsh-group-title">Primary channel (index 0)</p>
    <div class="azmsh-row"><span class="azmsh-label">Name:</span> <span class="azmsh-value">ExampleName</span></div>
    <div class="azmsh-row"><span class="azmsh-label">Key (PSK):</span> <span class="azmsh-value">ExampleKey==</span></div>
  </div>
  <div class="azmsh-overlay">
    <span class="azmsh-overlay-text">🔒 Primary channel name + key are shared in Discord</span>
    <a class="md-button md-button--primary" href="https://discord.gg/HrKtyuFEQk">Join The Discord</a>
  </div>
</div>

!!! danger "Do NOT rename your primary channel"
    Renaming the primary channel to "AZ Mesh", "azmsh", or anything custom puts you on a *different* channel and you fall off the mesh entirely. Use exactly the name and key listed in Discord.

Want the extra Arizona community channels (azmsh, Weather, Traffic, Trivia)? Those are public and live on the [Suggested Channels](/docs/suggested_channels.html) page. Add them as **secondary** channels; they don't replace your primary.

---

## Step 5: (Optional) Turn on MQTT for the map

MQTT puts your node on the community map and shares diagnostics. It does **not** carry your text messages. The full MQTT walkthrough, including the broker details, is on [Additional Settings → MQTT](/docs/additional-settings.html#mqtt).

---

## Step 6: Self-test (prove the mesh can hear you)

This is the moment of truth.

1. Go to the **Messages** tab and open your **primary** channel.
2. Send the message: **`test`** (send it as many times as you want).
3. Wait up to a minute, then watch for **emoji tapbacks** on your message. Many Arizona nodes run an auto-responder that reacts with a number:
    - :one: :two: :three: … = how many hops away that node was when it heard you
    - :asterisk: = a direct hit, no hops

**You got tapbacks?** :tada: You're on the Arizona mesh. Head to [How To Test](/docs/how-to-test.html) to claim your node and explore the map.

**No tapbacks after a few tries?** That's almost always physical placement, not a settings bug. Keep reading.

!!! tip "If you can RECEIVE any messages, your settings are correct"
    Seeing *other people's* messages come in means your radio, preset, slot, and channel are all right. If you can hear them but they can't hear you, it's an RF/placement problem, not a configuration problem. Go to [FAQ → I can receive, but I can't send](/docs/faq.html#cant-send).

---

## Where to go next

- :material-test-tube: **Test your setup / see yourself on the map** → [How To Test](/docs/how-to-test.html)
- :material-help-circle: **Can't send / no acks / "Max Transmission Reached"?** → [FAQ → I can receive, but I can't send](/docs/faq.html#cant-send)
- :material-radio-tower: **Add community channels** → [Suggested Channels](/docs/suggested_channels.html)
- :material-tune: **Tune your node (roles, intervals, MQTT)** → [Additional Settings](/docs/additional-settings.html)
- :material-frequently-asked-questions: **Site says "Forbidden", node won't claim, flashing problems** → [FAQ & Troubleshooting](/docs/faq.html)

---

## Want to go deeper?

Everything above gets you on the Arizona mesh. Once you're connected and want to fine-tune your node (node roles, broadcast intervals, Neighbor Info, the full MQTT walkthrough), head to the **[Additional Settings](/docs/additional-settings.html)** reference. It's laid out in the same order as the Meshtastic app, with iOS vs Android name differences noted.

[:material-tune: Open Additional Settings](/docs/additional-settings.html){ .md-button }
