---
hide:
  - navigation
title: Start Here
description: The first 30 minutes on the Arizona mesh — a single, in-order checklist that takes you from an unboxed radio to sending your first message and seeing it acknowledged.
---

# Start Here: Your First 30 Minutes

New to the Arizona mesh? Start on this page. Follow the steps **in order, top to bottom** — don't skip ahead. By the end you'll have a working node, the right Arizona settings, and proof that the mesh can hear you.

!!! info "What you need before you begin"
    - A Meshtastic radio. Don't have one? See [Recommended Hardware](/docs/recommended-hardware.html) — you can get on the mesh for about $30.
    - The Meshtastic app on your phone (links in Step 2).
    - About 30 minutes. Most of it is waiting for firmware to flash.

---

## Step 1: Flash the latest firmware

1. Open the [**Meshtastic Web Flasher**](https://flasher.meshtastic.org) in **Google Chrome** (other browsers often fail).
2. Select your device, click **Flash**, and follow the prompts.

!!! warning "UNCHECK \"Install Meshtastic UI\" when flashing"
    On many devices (especially Heltec V3/V4), leaving the "Meshtastic UI" / "InkHUD" option checked causes boot loops or a blank screen. If you don't specifically want the on-device UI, leave it **unchecked**. If your screen is already stuck or blank, re-flash with it off. See [Flashing & Recovery](/docs/flashing-gotchas.html).

!!! danger "Never transmit without an antenna attached"
    Powering on or sending with the antenna disconnected can permanently damage the radio. Always screw the antenna on first.

---

## Step 2: Install the app and pair over Bluetooth

| Platform | Link |
|:---------|:-----|
| **Android** | [Google Play Store](https://play.google.com/store/apps/details?id=com.geeksville.mesh) |
| **iOS** | [Apple App Store](https://apps.apple.com/us/app/meshtastic/id1586432531) |

1. Turn on your radio.
2. Open the app, tap **+**, and select your device to pair over Bluetooth.
3. You should now see your node in the app.

---

## Step 3: Set the Arizona LoRa radio settings

This is where most new nodes go wrong. In the app, open **Settings → LoRa (Radio Configuration)** and set:

| Setting | Value | Why |
|:--------|:------|:----|
| **Region** | `US` | Required for legal 915 MHz operation. |
| **Preset / Modem** | **MediumFast** | The standard Arizona preset. Not MediumSlow, not LongFast. |
| **Frequency Slot** | **18** (906.375 MHz) | The single most-missed setting. See the iOS note below. |
| **OK to MQTT** | **On** | Lets your node share map/diagnostics (not your messages). |

!!! warning "Set Frequency Slot to 18 — this is the #1 missed setting"
    Lots of people pick **MediumFast** but leave the **Frequency Slot** at `0`/auto, so they land on the wrong channel and can't hear anyone. Set it to **18**.

    **iOS gotcha:** the Slot field is text entry — **double-tap the `0`** to select it, then type `18`. Leave **Frequency Override** blank or `0`; if you put a value in Override, the Slot field locks. "Override" and "Slot" are *not* the same field.

---

## Step 4: Set the primary channel (leave the name BLANK)

Open **Settings → Channels** and look at the **primary** channel (index 0):

- **Name:** leave it **BLANK** (preferred). A blank primary name *is* the standard `MediumFast` channel.
- **Pre-shared key:** `AQ==`

!!! danger "Do NOT rename your primary channel to \"AZ Mesh\" or \"azmsh\""
    Renaming the primary channel to anything custom (a common mistake) puts you on a *different* channel and you fall off the mesh entirely. Leave it blank, or set it to exactly `MediumFast` with key `AQ==`.

Want the extra Arizona community channels (azmsh, Weather, Traffic, Trivia)? Add them as **secondary** channels from the [Suggested Channels](/docs/suggested_channels.html) page — they don't replace your primary.

---

## Step 5: (Optional) Turn on MQTT for the map

MQTT puts your node on the community map and shares diagnostics. It does **not** carry your text messages.

The live broker server, username, and password are shared in Discord (we keep them off the public site). Once you have them, see [Recommended Settings → MQTT](/docs/recommended-settings.html#mqtt) for the exact toggles.

[:fontawesome-brands-discord: Join the Discord for the broker settings](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }

---

## Step 6: Self-test — prove the mesh can hear you

This is the moment of truth.

1. Go to the **Messages** tab and open your **primary** channel.
2. Send the message: **`test`**
3. Wait up to a minute, then watch for **emoji tapbacks** on your message. Many Arizona nodes run an auto-responder that reacts with a number:
    - :one: :two: :three: … = how many hops away that node was when it heard you
    - :asterisk: = a direct hit, no hops

**You got tapbacks?** :tada: You're on the Arizona mesh. Head to [What Now?](/docs/what-now.html) to claim your node and explore the map.

**No tapbacks after a few tries?** That's almost always physical placement, not a settings bug — keep reading.

!!! tip "If you can RECEIVE any messages, your settings are correct"
    Seeing *other people's* messages come in means your radio, preset, slot, and channel are right. If you can hear them but they can't hear you, it's an RF/placement problem, not a configuration problem. Go to [Receive works, can't send](/docs/cant-transmit.html).

---

## Where to go next

- :material-help-circle: **Can't send / no acks / "Max Transmission Reached"?** → [Receive works, can't send](/docs/cant-transmit.html)
- :material-tune: **Full settings reference** (roles, broadcast intervals, MQTT) → [Recommended Settings](/docs/recommended-settings.html)
- :material-radio-tower: **Add community channels** → [Suggested Channels](/docs/suggested_channels.html)
- :material-map: **Claim your node + see yourself on the map** → [What Now?](/docs/what-now.html)
- :material-frequently-asked-questions: **Site says "Forbidden", node won't claim, flashing problems** → [FAQ & Troubleshooting](/docs/faq.html)
