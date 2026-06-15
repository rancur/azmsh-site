---
hide:
  - navigation
title: Additional Settings
description: The deeper Meshtastic settings reference for Arizona operators, laid out in the same section order as the iOS Meshtastic app (Radio Configuration, Device Configuration, Module Configuration), with Android name differences noted where they help.
---

# Additional Settings

This is the deeper settings reference for your node: node roles, broadcast intervals, Neighbor Info, MQTT, and more. It's laid out in the **same section order as the iOS Meshtastic app**, grouped under **Radio Configuration**, **Device Configuration**, and **Module Configuration**, so you can read down this page with the app open and follow along section by section.

!!! tip "New here? Start with the Start Here guide first"
    If you just unboxed a radio, **don't start on this page.** Go to **[Start Here](/docs/start-here.html)** first; it walks you in order from flashing firmware to sending your first acknowledged message, and it already includes everything you need to get on the Arizona mesh. Come back here once you're connected and want to fine-tune your node.

    [:material-rocket-launch: Go to Start Here](/docs/start-here.html){ .md-button .md-button--primary }

!!! info "The Arizona-specific values aren't repeated here"
    Your **region, preset, frequency slot, primary channel name + key, and MQTT broker** are shared in [Discord](https://discord.gg/HrKtyuFEQk) so the whole mesh stays coordinated. Get those from Discord (see [Start Here → Step 3](/docs/start-here.html#step-3-get-the-arizona-radio-settings-from-discord)). Everything on this page is general guidance that's the same for any operator.

!!! note "Names on this page follow the iOS app; Android differences are noted"
    This page uses the **iOS / iPadOS / macOS** section names and setting names, in the order the iOS app lists them. Where Android uses a different word for the same setting, we note it in parentheses, like **Modem Presets (Android: Presets)**. The path to reach the settings also differs slightly:

    - **iOS / iPadOS / macOS:** **Settings → Radio Configuration / Device Configuration / Module Configuration →** the section name (e.g. **LoRa**).
    - **Android:** **Settings** tab → the section name (e.g. **LoRa**). Modules appear further down the same list.

    After changing anything on iOS, remember to **Save / send the configuration** back to your node.

---

# Radio Configuration

In the iOS app, **Radio Configuration** holds **LoRa, Channels, and Security**, in that order. These are the radio-level settings that put you on the Arizona mesh.

## LoRa { #lora }

The **LoRa** section is the most important radio section: it's where **Region, Modem Preset, and Frequency Slot** live. Getting these exactly right is what puts you on the Arizona mesh.

!!! note "Name differences in this section"
    - **Region** is called **Region** on both apps (iOS may show it as **Set LoRa Region**).
    - The preset is **Modem Presets (iOS) / Presets (Android)**.
    - **Frequency Slot** and **Frequency Override** are named the same on both.
    - The hop setting is **Hop Limit (iOS) / Number of Hops (Android)**.

The Arizona **Region, Modem Preset, and Frequency Slot** values are shared in Discord. Set them exactly as listed; they are covered in [Start Here → Step 3](/docs/start-here.html#step-3-get-the-arizona-radio-settings-from-discord).

<div class="azmsh-locked">
  <div class="azmsh-settings">
    <p class="azmsh-group-title">Arizona LoRa settings</p>
    <div class="azmsh-row"><span class="azmsh-label">Region:</span> <span class="azmsh-value">US</span></div>
    <div class="azmsh-row"><span class="azmsh-label">Modem Preset / Preset:</span> <span class="azmsh-value">ExamplePreset_AZ</span></div>
    <div class="azmsh-row"><span class="azmsh-label">Frequency Slot:</span> <span class="azmsh-value">00</span></div>
  </div>
  <div class="azmsh-overlay">
    <span class="azmsh-overlay-text">🔒 Arizona radio settings are shared in Discord</span>
    <a class="md-button md-button--primary" href="https://discord.gg/HrKtyuFEQk">Join The Discord</a>
  </div>
</div>

!!! warning "The Frequency Slot is the #1 missed setting"
    Lots of people set the preset correctly but leave the **Frequency Slot** at `0`/auto, so they land on the wrong frequency and can't hear anyone. Set it to the exact slot listed in Discord.

    **iOS gotcha:** the Slot field is text entry. **Double-tap the existing value** to select it, then type the correct slot. Leave **Frequency Override** blank or `0`; entering a value there *locks* the Slot field. "Frequency Override" and "Frequency Slot" are different fields.

!!! info "Hop Limit (iOS) / Number of Hops (Android)"
    Leave this at the default (**3**) unless the community advises otherwise. Cranking up the hop count floods the mesh and rarely helps; more hops is not more range.

The **"OK to MQTT"** toggle also lives in the LoRa section. See the [MQTT](#mqtt) section below for how it works with the MQTT module.

---

## Channels { #channels }

The **Channels** section is where you set your **primary** channel and add **secondary** channels.

- Your **primary channel** (index 0) must match the Arizona settings exactly. Setting it up is covered in [Start Here → Step 4](/docs/start-here.html#step-4-set-up-your-primary-channel).
- **Do not rename your primary channel.** Renaming it to "AZ Mesh", "azmsh", or anything custom puts you on a *different* channel and you fall off the mesh.
- Community channels (azmsh, Weather, Traffic, Trivia) are added here as **secondary** channels. The names, keys, and per-platform steps live on the [Suggested Channels](/docs/suggested_channels.html) page.

The fields are labeled **Channel Name** and **PSK** (the key) on both apps.

---

## Security { #security }

The **Security** section holds your node's **identity keys**. These are what let other nodes verify it's really you and what make direct messages private.

!!! tip "Back up your keys before re-flashing"
    Flashing can wipe your settings, including your node's identity keys. Export/back up your configuration from the Meshtastic app first, so you don't reappear as a brand-new node and trigger impersonation warnings for others.

- If you ever see a **"possible impersonation"** warning about another node, or your own node is flagged, it usually means weak/duplicate keys from very old firmware. The fix is to regenerate keys on the affected node. See [FAQ → DM "No Channel" / impersonation](/docs/faq.html#dm-no-channel).

---

# Device Configuration

In the iOS app, **Device Configuration** holds **User, Bluetooth, Device, Display, Network, Position, and Power**, in that order. These set how your node identifies itself, how it behaves, and how it connects.

## User { #user }

The **User** section is where you set how your node identifies itself on the mesh.

- **Long Name:** your node's full name (e.g. "Will's Rooftop"). Shows up in everyone's node list.
- **Short Name:** up to 4 characters, shown on small screens and maps. Make it recognizable.
- **Licensed Operator (iOS) / Licensed amateur radio (Android):** **leave this OFF** unless you're a licensed ham operator running under Part 97. Turning it on disables encryption and changes how your node transmits. The Arizona community mesh uses the standard encrypted ISM-band setup, so almost everyone leaves this off.

---

## Bluetooth { #bluetooth }

The **Bluetooth** section controls how your phone pairs with the node.

- **Pairing Mode:** most devices default to a fixed PIN or a random PIN shown on screen. If you have no screen, the PIN is usually `123456` or printed in the device docs.
- If pairing fails or keeps dropping, see [FAQ → Bluetooth won't pair or keeps dropping](/docs/faq.html#bluetooth).

---

## Device { #device }

The **Device** section holds your node's **role** and rebroadcast behavior. Picking the right role is the single most important choice here, because it affects the whole mesh, not just you.

The field is labeled **Device Role** on both apps.

### Node Roles

Choosing the right role for your device keeps the network clean and efficient.

#### Client Mute

**Use for: anything mobile** (backpacks, vehicles, pocket nodes).

Client Mute nodes can send and receive messages but do **not** rebroadcast other people's traffic. This is the best choice for devices that move around, since mobile rebroadcasters create unpredictable routing and extra congestion.

#### Client

**Use for: stationary home or rooftop nodes.**

Client is the standard role. Your node will participate in the mesh by rebroadcasting messages, which helps extend coverage for your neighbors.

!!! tip "When in doubt, client it out"
    Not sure which role to pick? Set your device to **Client Mute** and talk to a community member in Discord. You can always change it later.

#### Router and Router Late

!!! warning "Understand Router roles before switching"
    **Router** and **Router Late** are designed for nodes at **high elevation, permanent fixed locations with good line-of-sight** (hilltops, towers, or mountain repeater sites). They aggressively rebroadcast traffic and are optimized to extend the mesh across long distances.

    Used in the wrong context (a home, an apartment, or a mobile node), these roles can cause increased congestion, routing loops, and degraded performance for everyone on the mesh. Meshtastic's own guidance is to use these roles only where they genuinely improve coverage for the wider network, not just your own reach.

    **Before switching to Router or Router Late, make sure you understand the implications.** If you're unsure whether your location and setup are a good fit, ask the community on Discord. We're happy to help.

    [:fontawesome-brands-discord: Ask the Community on Discord](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }

### Node Info Broadcast Interval

Your node periodically broadcasts its name and details so others can see it. This rarely needs to change.

| Setting | Value | Notes |
|:--------|:------|:------|
| **Node Info Broadcast Interval** | `43200` sec (12 hours) | Your node info rarely changes, so there's no need to broadcast it often. Same value for mobile and stationary nodes. |

On iOS this setting lives on the Device screen with the broadcast interval expressed in seconds. On Android it is labeled **Node Info Broadcast Interval**.

---

## Display { #display }

The **Display** section controls the on-device screen (brightness, screen timeout, units, orientation). These are personal-preference settings and don't affect the mesh.

- Set **Display Units** to your preference (the community generally uses imperial in Arizona).
- A shorter **Screen Timeout** saves battery on handhelds.

---

## Network { #network }

The **Network** section is for **WiFi and Ethernet**, and only applies to **ESP32-based** nodes (Heltec, Station G2, T-Deck). Bluetooth-only nRF52 nodes (most handhelds and solar nodes) don't have this.

- Enter your **WiFi SSID and password** here if your rooftop ESP32 node will reach the community MQTT server over your home internet.
- A WiFi connection is what lets an ESP32 node uplink to MQTT **without** proxying through your phone.

---

## Position { #position }

The **Position** section controls how often your node shares its GPS location and how often it reads its own GPS. Tuning these correctly reduces channel congestion and saves battery.

!!! note "Name differences in this section"
    - **Smart Position** is called the same on both apps (sometimes shown as **Smart Position Enabled**).
    - The GPS read interval is **Update Interval (iOS) / GPS Polling Interval (Android)**.

### Mobile Nodes

For devices that move around (in your car, backpack, pocket, etc.):

| Setting | Value | Notes |
|:--------|:------|:------|
| **Smart Position** | **ON** | Automatically sends position updates when you move. |
| Smart Position Min Distance | `100` meters | Only broadcasts after moving at least 100 m. |
| Smart Position Min Interval | `60` seconds | No more than one smart broadcast per minute. |
| **Position Broadcast Interval** | `3600` sec (1 hour) | Fallback interval if GPS is enabled. |
| **Update Interval (iOS) / GPS Polling Interval (Android)** | `300` sec (5 minutes) | How often the device checks its own GPS. |

### Stationary Nodes

For devices that stay in one place (rooftop, home base, solar nodes):

| Setting | Value | Notes |
|:--------|:------|:------|
| **Smart Position** | **OFF** | Your node is not moving, so smart positioning is not needed. |
| **Position Broadcast Interval** | `43200` sec (12 hours) | Only if GPS is enabled. Your position is fixed. |
| **Update Interval (iOS) / GPS Polling Interval (Android)** | `21600` sec (6 hours) | Minimal GPS checks since the node does not move. |

!!! tip "No GPS? Set a fixed position instead"
    Rooftop and indoor nodes often have no GPS fix. Enable **Fixed Position** and set your coordinates manually so your node still shows up in the right place on the map.

---

## Power { #power }

The **Power** section controls sleep and battery behavior. Most operators can leave this at defaults.

- Plugged-in rooftop nodes: leave power-saving **off** so the node stays fully awake.
- Battery and solar nodes: power-saving can extend runtime, but it also delays responses. Only enable it once your node is otherwise working, and test afterward.

---

# Module Configuration

Modules are optional add-ons. In the iOS app they appear under **Module Configuration** (Android lists them further down the **Settings** list). The full iOS list is alphabetical (Ambient Lighting, Canned Messages, Detection Sensor, External Notification, MQTT, Neighbor Info, Range Test, Ringtone, Serial, Store & Forward, TAK Server, Telemetry). Below are the modules Arizona operators use most.

## MQTT { #mqtt }

MQTT lets your node upload diagnostic data to a shared server, which helps us monitor network health and see all nodes on the map. It does **not** send your personal messages or private data, only metadata like position, telemetry, and node info.

!!! danger "MQTT does NOT send your messages (map + diagnostics only)"
    A common misconception is that MQTT carries your text messages over the internet. It does **not**. MQTT shares only **map position, telemetry, and node info** for the community map and monitoring tools. Your text messages always travel over the LoRa radio mesh, encrypted, and are never uplinked.

!!! info "The three toggles that make MQTT work"
    - **"OK to MQTT"** (in the **LoRa** section, same name on both apps): **ON**. Lets your node's data be uplinked at all.
    - **Channel Uplink** (per channel): **ON**. Sends *that channel's* node/telemetry data to the server. Labeled **Uplink Enabled** on both apps.
    - **Connect to MQTT via Proxy (iOS) / Proxy to client enabled (Android):** turn **ON only if the node has no WiFi of its own.** It then relays MQTT through your phone's connection. If the node is on WiFi (most rooftop ESP32 nodes), leave it **OFF**.

**How to Enable MQTT**

To enable MQTT uplink, you will need the community broker settings (server address, username, and password). We keep these in Discord.

[:fontawesome-brands-discord: Join the Discord for MQTT broker settings](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }

Once you have the broker details:

1. **LoRa section:** enable **"OK to MQTT"**. This allows your node's data to be uplinked.
2. **MQTT module:** enter the broker settings provided in Discord. The fields are **Server**, **Username**, **Password**, and **Root topic** on both apps.

    <div class="azmsh-locked">
      <div class="azmsh-settings">
        <div class="azmsh-row"><span class="azmsh-label">Server:</span> <span class="azmsh-value">broker.example.net:1883</span></div>
        <div class="azmsh-row"><span class="azmsh-label">Username:</span> <span class="azmsh-value">example_uplink_user</span></div>
        <div class="azmsh-row"><span class="azmsh-label">Password:</span> <span class="azmsh-value">example_password</span></div>
        <div class="azmsh-row"><span class="azmsh-label">Root topic:</span> <span class="azmsh-value">msh/REGION/EXAMPLE</span></div>
      </div>
      <div class="azmsh-overlay">
        <span class="azmsh-overlay-text">🔒 Broker settings are shared in Discord</span>
        <a class="md-button md-button--primary" href="https://discord.gg/HrKtyuFEQk">Join The Discord</a>
      </div>
    </div>

3. **Channel settings** (for each channel you want to uplink):
    - **Uplink (Uplink Enabled):** **ON**. Sends your node's data to the MQTT server.
    - **Downlink (Downlink Enabled):** **OFF**. Prevents MQTT messages from being injected back into the radio mesh.

!!! warning "Always keep Downlink OFF"
    Downlinking from MQTT into the primary channel floods the radio mesh with traffic from the internet. Keep downlink disabled unless you have a specific reason and have discussed it with the community.

---

## Neighbor Info { #neighbor-info }

Neighbor Info is a module that periodically broadcasts a list of your node's direct neighbors along with the signal quality (SNR) of each link. When enabled across multiple nodes, the community can build a real picture of how the mesh is connected, which helps identify coverage gaps, optimize node placement, and understand how traffic actually flows through the network.

In the iOS Module Configuration list, **Neighbor Info** appears alphabetically just after MQTT. Neighbor Info packets are small and infrequent, so the channel congestion impact is very low.

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

## Where to go next

- :material-rocket-launch: **Not set up yet?** → [Start Here](/docs/start-here.html)
- :material-test-tube: **Confirm the mesh can hear you** → [How To Test](/docs/how-to-test.html)
- :material-frequently-asked-questions: **Something's not working** → [FAQ & Troubleshooting](/docs/faq.html)
- :material-radio-tower: **Add community channels** → [Suggested Channels](/docs/suggested_channels.html)
- :material-radio-handheld: **Need better hardware** → [Recommended Hardware](/docs/recommended-hardware.html)
