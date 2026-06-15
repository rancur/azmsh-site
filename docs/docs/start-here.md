---
hide:
  - navigation
title: Start Here
description: The first 30 minutes on the Arizona mesh. A single, in-order guide that takes you from an unboxed radio to sending your first message and seeing it acknowledged, plus the full settings reference.
---

# Start Here: Your First 30 Minutes

New to the Arizona mesh? This is the only page you need to get going. Follow the steps **in order, top to bottom** (don't skip ahead). By the end you'll have a working node, the right Arizona settings, and proof that the mesh can hear you. The deeper settings reference (roles, broadcast intervals, MQTT) is at the bottom of this page once you're connected.

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

!!! warning "UNCHECK \"Install Meshtastic UI\" when flashing"
    On many devices (especially Heltec V3/V4), leaving the "Meshtastic UI" / "InkHUD" option checked causes boot loops or a blank screen. If you don't specifically want the on-device UI, leave it **unchecked**. If your screen is already stuck or blank, re-flash with it off. See [Flashing & Recovery](/docs/flashing-gotchas.html).

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

MQTT puts your node on the community map and shares diagnostics. It does **not** carry your text messages. The full MQTT walkthrough, including the broker details, is in the [Settings Reference → MQTT](#mqtt) section below.

---

## Step 6: Self-test (prove the mesh can hear you)

This is the moment of truth.

1. Go to the **Messages** tab and open your **primary** channel.
2. Send the message: **`test`** (send it as many times as you want).
3. Wait up to a minute, then watch for **emoji tapbacks** on your message. Many Arizona nodes run an auto-responder that reacts with a number:
    - :one: :two: :three: … = how many hops away that node was when it heard you
    - :asterisk: = a direct hit, no hops

**You got tapbacks?** :tada: You're on the Arizona mesh. Head to [What Now?](/docs/what-now.html) to claim your node and explore the map.

**No tapbacks after a few tries?** That's almost always physical placement, not a settings bug. Keep reading.

!!! tip "If you can RECEIVE any messages, your settings are correct"
    Seeing *other people's* messages come in means your radio, preset, slot, and channel are all right. If you can hear them but they can't hear you, it's an RF/placement problem, not a configuration problem. Go to [Receive works, can't send](/docs/cant-transmit.html).

---

## Where to go next

- :material-help-circle: **Can't send / no acks / "Max Transmission Reached"?** → [Receive works, can't send](/docs/cant-transmit.html)
- :material-radio-tower: **Add community channels** → [Suggested Channels](/docs/suggested_channels.html)
- :material-map: **Claim your node + see yourself on the map** → [What Now?](/docs/what-now.html)
- :material-frequently-asked-questions: **Site says "Forbidden", node won't claim, flashing problems** → [FAQ & Troubleshooting](/docs/faq.html)

---

# Settings Reference

Once you're connected, use this reference to tune your node. The Arizona **region, preset, frequency slot, and primary channel** values are not repeated here. Get those from [Discord](https://discord.gg/HrKtyuFEQk) (see Step 3). Everything below is general guidance that's the same for any operator.

## Node Roles

Choosing the right role for your device keeps the network clean and efficient.

### Client Mute

**Use for: anything mobile** (backpacks, vehicles, pocket nodes).

Client Mute nodes can send and receive messages but do **not** rebroadcast other people's traffic. This is the best choice for devices that move around, since mobile rebroadcasters create unpredictable routing and extra congestion.

### Client

**Use for: stationary home or rooftop nodes.**

Client is the standard role. Your node will participate in the mesh by rebroadcasting messages, which helps extend coverage for your neighbors.

!!! tip "When in doubt, client it out"
    Not sure which role to pick? Set your device to **Client Mute** and talk to a community member in Discord. You can always change it later.

### Router and Router Late

!!! warning "Understand Router roles before switching"
    **Router** and **Router Late** are designed for nodes at **high elevation, permanent fixed locations with good line-of-sight** (hilltops, towers, or mountain repeater sites). They aggressively rebroadcast traffic and are optimized to extend the mesh across long distances.

    Used in the wrong context (a home, an apartment, or a mobile node), these roles can cause increased congestion, routing loops, and degraded performance for everyone on the mesh. Meshtastic's own guidance is to use these roles only where they genuinely improve coverage for the wider network, not just your own reach.

    **Before switching to Router or Router Late, make sure you understand the implications.** If you're unsure whether your location and setup are a good fit, ask the community on Discord. We're happy to help.

    [:fontawesome-brands-discord: Ask the Community on Discord](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }

---

## Broadcast Intervals

Keeping broadcast intervals tuned correctly reduces channel congestion and lets everyone's messages get through reliably.

### Mobile Nodes

For devices that move around (in your car, backpack, pocket, etc.):

| Setting | Value | Notes |
|:--------|:------|:------|
| **Node Info Broadcast** | `43200` sec (12 hours) | Your node info rarely changes. No need to broadcast it often. |
| **Smart Broadcast** | **ON** | Automatically sends position updates when you move. |
| Smart Broadcast Min Distance | `100` meters | Only broadcasts after moving at least 100m. |
| Smart Broadcast Min Interval | `60` seconds | No more than one smart broadcast per minute. |
| **Position Broadcast** | `3600` sec (1 hour) | Fallback interval if GPS is enabled. |
| **GPS Update Interval** | `300` sec (5 minutes) | How often the device checks its own GPS. |
| **Device Metrics** | `3600` sec (1 hour) | Battery, voltage, channel utilization, etc. |
| **Environment Metrics** | `3600` sec (1 hour) | Temperature, humidity, etc. (if sensors attached). |
| **Power Metrics** | `3600` sec (1 hour) | Power monitoring (if sensors attached). |
| **Map Report** | `3600` sec (1 hour) | Sends position to the map server. |

### Stationary Nodes

For devices that stay in one place (rooftop, home base, solar nodes):

| Setting | Value | Notes |
|:--------|:------|:------|
| **Node Info Broadcast** | `43200` sec (12 hours) | Same as mobile. Node info does not change often. |
| **Smart Broadcast** | **OFF** | Your node is not moving, so smart positioning is not needed. |
| **Position Broadcast** | `43200` sec (12 hours) | Only if GPS is enabled. Your position is fixed. |
| **GPS Update Interval** | `21600` sec (6 hours) | Minimal GPS checks since the node does not move. |
| **Device Metrics** | `3600` sec (1 hour) | Still useful for monitoring battery and channel utilization. |
| **Environment Metrics** | `3600` sec (1 hour) | If sensors are attached. |
| **Power Metrics** | `3600` sec (1 hour) | If sensors are attached. |
| **Map Report** | `21600` sec (6 hours) | Less frequent since your position is fixed. |

---

## Neighbor Info

Neighbor Info is a module that periodically broadcasts a list of your node's direct neighbors along with the signal quality (SNR) of each link. When enabled across multiple nodes, the community can build a real picture of how the mesh is connected, which helps identify coverage gaps, optimize node placement, and understand how traffic actually flows through the network.

Neighbor Info packets are small and infrequent, so the channel congestion impact is very low.

**Recommended Update Interval**

| Node type | Interval | Seconds |
|:----------|:---------|:--------|
| **Mobile** | 4 hours | `14400` |
| **Stationary** | 11 hours | `39600` |

4 hours is the minimum the firmware allows. Use the longer interval for stationary nodes since their neighbors rarely change.

??? note "How to Enable on Android"
    Requires Meshtastic app version 2.2.0 or higher.

    1. Open the Meshtastic app and connect to your node.
    2. Tap the **three-dot menu** (vertical ellipsis) in the top-right corner.
    3. Select **Radio Configuration**.
    4. Scroll down and tap **Neighbor Info**.
    5. Toggle **Enabled** to ON.
    6. Set the **Update Interval** to `14400` (mobile) or `39600` (stationary).
    7. Toggle **Transmit Over LoRa** to ON. This sends the neighbor info over the radio mesh and to MQTT.
    8. Tap **Send** to save the settings to your node.

??? note "How to Enable on Web Client"
    1. Open the Meshtastic Web UI and connect to your node (usually at `meshtastic.local` or via USB serial).
    2. Click **Config** in the left sidebar.
    3. Click **Module Config**.
    4. Click **Neighbor Info**.
    5. Toggle **Enabled** to ON.
    6. Set the **Update Interval** to `14400` (mobile) or `39600` (stationary).
    7. Toggle **Transmit Over LoRa** to ON.
    8. Click **Save** to apply the settings.

??? note "How to Enable via CLI"
    Requires the Meshtastic Python CLI version 2.2.0 or higher (`pip install meshtastic`).

    ```bash
    # Enable the module
    meshtastic --set neighbor_info.enabled true

    # Set update interval (seconds) — 14400 = 4 hours, 39600 = 11 hours
    meshtastic --set neighbor_info.update_interval 14400

    # Enable transmit over LoRa (sends over radio AND MQTT)
    meshtastic --set neighbor_info.transmit_over_lora true

    # Verify your settings
    meshtastic --get neighbor_info
    ```

    Run these commands while connected to your node over USB, Bluetooth, or TCP.

!!! warning "iOS: Neighbor Info not currently supported"
    The iOS Meshtastic app does not currently support enabling the Neighbor Info module. iOS users will need to use the Web client or CLI over a TCP/USB connection to configure this setting on their node.

---

## MQTT

MQTT lets your node upload diagnostic data to a shared server, which helps us monitor network health and see all nodes on the map. It does **not** send your personal messages or private data, only metadata like position, telemetry, and node info.

!!! danger "MQTT does NOT send your messages (map + diagnostics only)"
    A common misconception is that MQTT carries your text messages over the internet. It does **not**. MQTT shares only **map position, telemetry, and node info** for the community map and monitoring tools. Your text messages always travel over the LoRa radio mesh, encrypted, and are never uplinked.

!!! info "The three toggles that make MQTT work"
    - **"OK to MQTT"** (LoRa settings): **ON**, lets your node's data be uplinked at all.
    - **Channel Uplink**: **ON**, sends *that channel's* node/telemetry data to the server.
    - **"Proxy to Client"**: turn **ON only if the node has no WiFi of its own**. It then relays MQTT through your phone's connection. If the node is on WiFi (most rooftop ESP32 nodes), leave it **OFF**.

**How to Enable MQTT**

To enable MQTT uplink, you will need the community broker settings (server address, username, and password). We keep these in Discord.

[:fontawesome-brands-discord: Join the Discord for MQTT broker settings](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }

Once you have the broker details:

1. **LoRa Settings**: Enable **"OK to MQTT"**. This allows your node's data to be uplinked.
2. **MQTT Module**: Enter the broker settings provided in Discord.

    <div class="azmsh-locked">
      <div class="azmsh-settings">
        <div class="azmsh-row"><span class="azmsh-label">Server:</span> <span class="azmsh-value">broker.example.net:1883</span></div>
        <div class="azmsh-row"><span class="azmsh-label">Username:</span> <span class="azmsh-value">example_uplink_user</span></div>
        <div class="azmsh-row"><span class="azmsh-label">Password:</span> <span class="azmsh-value">example_password</span></div>
        <div class="azmsh-row"><span class="azmsh-label">Topic:</span> <span class="azmsh-value">msh/REGION/EXAMPLE</span></div>
      </div>
      <div class="azmsh-overlay">
        <span class="azmsh-overlay-text">🔒 Broker settings are shared in Discord</span>
        <a class="md-button md-button--primary" href="https://discord.gg/HrKtyuFEQk">Join The Discord</a>
      </div>
    </div>

3. **Channel Settings** (for each channel you want to uplink):
    - **Uplink**: **ON**, sends your node's data to the MQTT server.
    - **Downlink**: **OFF**, prevents MQTT messages from being injected back into the radio mesh.

!!! warning "Always keep Downlink OFF"
    Downlinking from MQTT into the primary channel floods the radio mesh with traffic from the internet. Keep downlink disabled unless you have a specific reason and have discussed it with the community.
