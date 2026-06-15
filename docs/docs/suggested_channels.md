---
title: Suggested Channels
---

# Suggested Channels

Channels are how Meshtastic groups conversations on the mesh. Every node listens on a
**primary** channel plus any **secondary** channels you add, and each channel has its own
name and encryption key so the right messages reach the right people.

Adding the channels below lets you join the wider **azmsh.net** community. Chat on the
Arizona channel, watch the weather roll in from rooftop stations, keep an eye on traffic, and
even play a little trivia. The channel names and keys are shared with the community in our
[Discord server](https://discord.gg/HrKtyuFEQk) so they stay coordinated.

!!! tip "Two things to get right"

    - **Channel names are case-sensitive.** `Weather` and `weather` are *not* the same channel.
    - **Keys must match exactly.** Copy each key from Discord character-for-character.
      They're short, pre-shared keys (PSKs). That's by design for community channels.

---

## 📲 How to Add a Channel

Pick your platform below. The flow is the same idea everywhere: open the Meshtastic app,
find the **Channels** editor, add a channel, and enter the **Name** and **Key** from the
[table further down](#the-channels) exactly as written.

???+ note "Android"

    1. Open the **Meshtastic** app and make sure your node is connected over Bluetooth.
    2. Tap the **Settings** tab, then open **Channels**.
    3. Tap the **+** (add) button to create a new channel.
    4. Enter the **Channel Name** exactly as shown in the table. Remember it's
       **case-sensitive**.
    5. Enter the **Key** (PSK) from the table. On Android the key size is taken from the
       key you paste, so just paste it in exactly as written.
    6. Leave **Uplink/Downlink** at their defaults unless you have a reason to change them.
    7. Tap **Save** / the send button to write the channel to your node.

    > To use the default preset as your primary channel, you can leave the primary channel's
    > name **blank**. An empty primary name is the `default` channel.

??? note "iOS / iPadOS / macOS"

    1. Open the **Meshtastic** app and connect to your node.
    2. Go to **Settings → Radio Configuration → Channels**.
    3. Tap **Add Channel** (the **+** button).
    4. Enter the **Channel Name** exactly as shown in the table. It's **case-sensitive**.
    5. Set the **Key Size** to match the **Size** column in the table:
        - `Default` → leave the size at **Default (1 byte)**.
        - `1-byte` → choose the **1 byte** size.
    6. Enter the **Key** (PSK) from the table exactly as written.
    7. Tap **Save**, then make sure you **send the configuration** back to your node.

    > To use the default preset as your primary channel, you can leave the primary channel's
    > name **blank**. An empty primary name is the `default` channel.

??? note "Other (Web Client / Apple Watch / CLI)"

    **Web Client ([client.meshtastic.org](https://client.meshtastic.org))**

    1. Connect to your node over Bluetooth, Serial, or HTTP.
    2. Open **Config → Channels** and add a new channel.
    3. Enter the **Name** and **Key** from the table exactly, then save and send.

    **Apple Watch**

    The Watch app mirrors the channels already configured on your paired node. Add channels
    on your iPhone first (see the iOS steps above) and they'll sync to the Watch.

    **Meshtastic CLI**

    If you have the [Meshtastic CLI](https://meshtastic.org/docs/software/python/cli/installation/)
    installed, you can add a secondary channel directly. For example, to add **azmsh**:

    ```
    meshtastic --ch-add azmsh
    meshtastic --ch-index 1 --ch-set psk base64:<KEY_FROM_DISCORD> --ch-set name azmsh
    ```

    Adjust the `--ch-index` and values for each channel you want. Use the exact names and keys
    shared in [Discord](https://discord.gg/HrKtyuFEQk). Names are case-sensitive.

---

## The Channels

Each Arizona community channel has a **name** and a **key (PSK)**. The keys are shared with
the community in our [Discord server](https://discord.gg/HrKtyuFEQk) so they stay coordinated.
Join, grab the exact name + key for each channel, and add them as described above. The names
below tell you what each channel is for; the keys are behind the Discord gate.

<div class="azmsh-locked">
  <div class="azmsh-settings">
    <p class="azmsh-group-title">Primary (default) — leave the name blank, Default key size</p>
    <div class="azmsh-row"><span class="azmsh-label">Key (PSK):</span> <span class="azmsh-value">ExampleKey==</span></div>
    <p class="azmsh-group-title">azmsh — Arizona chatter + tests, Default key size</p>
    <div class="azmsh-row"><span class="azmsh-label">Key (PSK):</span> <span class="azmsh-value">ExampleKey==</span></div>
    <p class="azmsh-group-title">Weather — rooftop weather stations, 1-byte key size</p>
    <div class="azmsh-row"><span class="azmsh-label">Key (PSK):</span> <span class="azmsh-value">ExampleKey==</span></div>
    <p class="azmsh-group-title">Traffic — local traffic reports + waypoints, 1-byte key size</p>
    <div class="azmsh-row"><span class="azmsh-label">Key (PSK):</span> <span class="azmsh-value">ExampleKey==</span></div>
    <p class="azmsh-group-title">Trivia — play trivia (type !help in-channel), 1-byte key size</p>
    <div class="azmsh-row"><span class="azmsh-label">Key (PSK):</span> <span class="azmsh-value">ExampleKey==</span></div>
  </div>
  <div class="azmsh-overlay">
    <span class="azmsh-overlay-text">🔒 Channel names + keys are shared in Discord</span>
    <a class="md-button md-button--primary" href="https://discord.gg/HrKtyuFEQk">Join The Discord</a>
  </div>
</div>

!!! question "Need a hand?"

    Stuck getting a channel to show up? Hop into our [Discord](https://discord.gg/HrKtyuFEQk)
    or [reach out](../reach_out.md). Someone in the community is always happy to help.
