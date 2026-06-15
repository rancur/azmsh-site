---
hide:
  - navigation
title: Flashing & Recovery
description: Avoid the common flashing mistakes (boot loops, blank screens, and bricked nodes) and recover a node that won't boot using DFU / bootloader mode.
---

# Flashing & Recovery

Most "bricked" nodes aren't actually dead. They're just stuck after a flash, or were flashed with an option that doesn't suit the hardware. Here's how to avoid the common traps and recover a node that won't boot.

---

## Before you flash

Use the official [**Meshtastic Web Flasher**](https://flasher.meshtastic.org) in **Google Chrome** (other browsers frequently fail to connect to the serial port).

!!! warning "UNCHECK \"Install Meshtastic UI\" (the #1 flashing mistake)"
    Many devices, **especially the Heltec V3 and V4**, will boot-loop or show a **blank/black screen** if you flash with the on-device "Meshtastic UI" (InkHUD) option enabled. Unless you specifically want and have confirmed support for the on-device UI, leave that checkbox **unchecked**. You can always use the phone app for the interface.

!!! danger "Never power on or transmit without an antenna"
    The radio's power amplifier can be permanently damaged if it transmits with no antenna attached. Screw the antenna on **before** powering the device or sending anything.

!!! tip "Back up your keys first"
    Flashing can wipe your settings, including your node's identity keys. Export/back up your configuration from the Meshtastic app before updating, so you don't reappear as a brand-new node.

---

## My screen is blank or it's boot-looping after a flash

1. Re-open the [Web Flasher](https://flasher.meshtastic.org) in Chrome.
2. Re-flash the **same firmware version**, but this time make sure **"Install Meshtastic UI" is UNCHECKED**.
3. Let it complete and reboot. The screen issue is almost always that UI option on Heltec V3/V4.

---

## My node is completely dead / the flasher can't see it

The device probably needs to be put into **DFU (bootloader) mode** so the flasher can talk to it.

- **How to enter DFU varies by device.** It usually means **holding a button (often BOOT/USR) while plugging in USB or pressing reset**. Check your specific device's documentation for the exact button combo.
- nRF52 devices (RAK, T-Echo, etc.) typically expose a **USB drive** when in bootloader mode. You can drag a firmware file onto it, or use the Web Flasher.
- ESP32 devices (Heltec, Station G2, T-Deck) enter download mode via the **BOOT button**; the Web Flasher will then detect the serial port.

Once the device is in DFU/bootloader mode, the Web Flasher should detect it. Re-flash current firmware (UI option unchecked) and it should come back to life.

---

## Still stuck?

Post your device model and what happens at power-on in **#i-need-help** on Discord. Someone has almost certainly recovered the same board.

[:fontawesome-brands-discord: Ask in #i-need-help](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }
