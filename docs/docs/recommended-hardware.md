---
hide:
  - navigation
title: Recommended Hardware
---

# :material-radio-handheld: Recommended Hardware

New to Meshtastic? Here's what to buy. No monthly fees, no subscriptions. Just a one-time purchase and you're on the mesh.

!!! tip "You need two things"
    **1. A handheld radio.** Carry it with you. It pairs with your phone over Bluetooth<br>
    **2. A node up high.** On your roof or in your attic, to keep you connected from home

    That's it. Buy these two things, follow our [How to Connect](/docs/how-to-connect.html) guide, and you're on the mesh.

---

## :material-star: Start Here

Don't want to read the whole page? Buy these two.

<div class="grid cards" markdown>

-   :material-cellphone:{ .lg .middle } __1. Handheld: RAK WisMesh Pocket V2__

    ---

    The best all-around handheld for Arizona. GPS, huge 3200 mAh battery (3+ days), IP66 waterproof. Pairs with your phone over Bluetooth. Open the Meshtastic app and start messaging.

    **~$89-99.** Also budget the ~$12 antenna upgrade below. It's the best money you'll spend.

    [:material-cart: RAK Store (~$89)](https://store.rakwireless.com/products/wismesh-pocket) · [Rokland (~$99)](https://store.rokland.com/products/wismesh-pocket)

-   :material-home-roof:{ .lg .middle } __2. Rooftop: PeakMesh 1W__

    ---

    Fully assembled and solar powered, with a **1 watt** radio and several mounting styles. Nothing to build, nothing to solder, no power to run. Turn it on, get it up high, done.

    **~$115-120.** Our default answer to "I'm new, what do I buy?"

    [:material-cart: PeakMesh 1W nodes on Etsy](https://www.etsy.com/shop/PeakMesh?search_query=1w)

</div>

!!! warning "Don't skip the rooftop node"
    **This is the #1 mistake new users make.** A handheld on its own struggles indoors and at any real distance. Put a node up high and the difference is night and day.

---

## :material-cellphone: 1. Your Handheld

These pair with your phone over Bluetooth, so you type messages on your phone screen.

!!! tip "What to expect from a handheld"
    A handheld does best when there's a rooftop node within range. That's especially true of the **card-style trackers**, which have sealed internal antennas you can't upgrade. Handhelds with an **external antenna** do noticeably better and are often heard well outdoors.

| Device | Chip | Battery | Battery Life | Screen | Price | Best For |
|---|---|---|---|---|---|---|
| **Wio Tracker L1** | nRF52840 | 800 mAh | ~2-3 days | 0.96" OLED | ~$30 | :material-star: Budget pick |
| **Wio Tracker L1 Pro** | nRF52840 | 2000 mAh | ~2.5 days | 1.3" OLED | ~$43 | Budget, with solar |
| **LILYGO T-Echo** | nRF52840 | 850 mAh | ~5-7 days | 1.54" E-Ink | ~$60-68 | Readable in full sun |
| **RAK WisMesh Pocket V2** | nRF52840 | 3200 mAh | ~3+ days | 1.3" OLED | ~$89-99 | :material-trophy: Best overall |
| **LILYGO T-Deck Plus** | ESP32-S3 | 2000 mAh | ~1-2 days | 2.8" Touch | ~$77-87 | Keyboard, no phone needed |

!!! info "nRF52840 or ESP32? Here's all you need to know"
    Those are the two chips Meshtastic devices are built on, and the only difference that really matters to you is battery versus WiFi.

    | | **nRF52840** | **ESP32 / ESP32-S3** |
    |---|---|---|
    | **Battery life** | :material-battery-high: Great (days to weeks) | :material-battery-medium: OK (1-2 days) |
    | **WiFi** | :material-close: No | :material-check: Yes |
    | **Bluetooth** | :material-check: Yes | :material-check: Yes |

    **Simple rule:** carrying it in your pocket? Get **nRF52840**. Plugging it into the wall? **ESP32** is fine, and you get WiFi.

!!! success "Upgrade your antenna. The best $12 you'll spend"
    **Most handhelds ship with a weak stock antenna.** The stubby one in the box wastes roughly a third of your signal as heat instead of putting it on the air.

    **Get the [Muziworks 17cm Whip](https://muzi.works/products/whip-antenna-17cm) (~$12).** SMA male, 915 MHz tuned, and the community consistently reports much better range than stock. Also sold as a [4-pack (~$36)](https://muzi.works/products/4-pack-whip-antenna-17cm-915mhz) or on [Amazon](https://www.amazon.com/muzi-%E1%B4%A1%E1%B4%8F%CA%80%E1%B4%8B%EA%9C%B1-915Mhz-Antenna-Meshtastic/dp/B0D7D6866W).

    **Fits:** WisMesh Pocket, T-Echo, T-Deck Plus, T-Beam, and most handhelds with an SMA connector.<br>
    **Doesn't apply to:** card-style trackers. Their antennas are sealed inside.

---

#### :material-star-outline: Budget Pick: Seeed Wio Tracker L1 (~$30)

The best value in Meshtastic right now. For about $30 you get a radio, GPS, screen, and battery, ready to go.

The **L1 Pro** (~$43) is worth the extra $13: bigger screen, joystick, solar charging, a 2000 mAh battery, and an antenna connector so you can upgrade.

:material-cart: [Seeed Studio L1 ($29.90)](https://www.seeedstudio.com/Wio-Tracker-L1-p-6453.html) | [L1 Pro ($42.90)](https://www.seeedstudio.com/Wio-Tracker-L1-Pro-p-6454.html) | [Amazon (L1 Pro)](https://www.amazon.com/seeed-studio-L1-Pro-Tracker/dp/B0FNCS5ST1)

---

#### :material-white-balance-sunny: Best in Sunlight: LILYGO T-Echo (~$60-68)

The e-ink screen works like a Kindle: perfectly readable in direct Arizona sun, and it barely touches the battery. One of the longest-lasting handhelds you can buy.

!!! warning "Attach the antenna before powering it on"
    The T-Echo's radio can be permanently damaged if it transmits with no antenna connected.

:material-cart: [LILYGO Store (~$60)](https://lilygo.cc/products/t-echo-meshtastic) | [Rokland (~$68)](https://store.rokland.com/products/lilygo-ttgo-meshtastic-t-echo-white-lora-sx1262-wireless-module-915mhz-nrf52840-gps-for-arduino)

---

#### :material-trophy: Best Overall: RAK WisMesh Pocket V2 (~$89-99)

The grab-and-go handheld. It works out of the box, no flashing and no tinkering: 3200 mAh battery, IP66 waterproof, solar connector, and an external SMA antenna connector for the upgrade above.

:material-cart: [RAK Store (~$89)](https://store.rakwireless.com/products/wismesh-pocket) | [Rokland (~$99)](https://store.rokland.com/products/wismesh-pocket) | [Atlavox](https://atlavox.com/products/rak-wismesh-pocket)

---

#### :material-keyboard: No Phone Needed: LILYGO T-Deck Plus (~$77-87)

A tiny standalone messenger with a full physical keyboard, trackball, and touchscreen. Leave your phone in your pocket. Uses ESP32-S3, so you get WiFi but shorter battery life.

:material-cart: [LILYGO Store (~$77)](https://lilygo.cc/products/t-deck-plus-meshtastic) | [Amazon](https://www.amazon.com/LILYGO-ESP32-S3-LORA-89-2-8-inch-Development/dp/B0FBGX1VP5)

---

#### :material-map-marker: Card-Style Trackers

Credit-card-sized, no screen and no buttons. Toss one in a backpack, clip it to a collar, leave it in a vehicle. It reports its location to the mesh on its own. All three transmit at the same 22 dBm.

**Our pick: RAK WisMesh Tag (~$39)**. 1000 mAh (5-6 days typical), IP66, accelerometer.

:material-cart: [RAK Store (~$39)](https://store.rakwireless.com/products/wismesh-tag-meshtastic-gps-lora-tracker-ip66) | [Rokland (~$50)](https://store.rokland.com/products/wismesh-tag-from-rakwireless-mokosmart-meshtastic-compatible-card-sized-node-us915-mhz)

**Best for handing to someone else: SenseCAP MeshTracker X1 (~$50)**

A bit thicker and heavier than the others (8 mm, 45 g), and better at nearly everything else. It charges with a **normal USB-C cable**, which matters more than it sounds: there's no proprietary puck to lose. Bigger 1100 mAh battery (~5 days), newer radio, dual-band L1+L5 GPS, IP66.

This is the one to give **someone who just needs to keep it charged and nothing else**. A family member, a kid, a hiking partner.

:material-cart: [Seeed Studio ($49.90)](https://www.seeedstudio.com/sensecap-meshtracker-x1-meshtastic-gps-tracker-p-6935.html)

**Also fine: SenseCAP T-1000e (~$39)**. The original, and still perfectly good. It has the smallest battery of the three (700 mAh) and charges from a proprietary magnetic puck rather than USB-C.

!!! warning "Buy the T-1000**e**"
    The "e" is the Meshtastic version. Other T-1000 models won't work.

:material-cart: [Seeed Studio](https://www.seeedstudio.com/SenseCAP-Card-Tracker-T1000-E-for-Meshtastic-p-5913.html) | [Amazon](https://www.amazon.com/SenseCAP-Card-Tracker-T1000-Meshtastic/dp/B0DJ6KGXKB)

---

## :material-home-roof: 2. Your Rooftop Node

This is the node that stays home, up high, and keeps you on the mesh. It matters more than your handheld does.

!!! tip "Height beats everything else"
    **How high it is matters more than how good it is.** A basic node at 30 feet will beat an expensive one at 6 feet, every time.

!!! info "Set it to CLIENT"
    **CLIENT** is the right role for a home rooftop node. Leave it there. See [Recommended Settings](/docs/recommended-settings.html) for the rest of your configuration.

    ??? warning "Thinking about Router or Router Late? Read this first"
        **Router** and **Router Late** are for high-elevation sites with real line-of-sight, not typical homes. Setting them on a house node adds congestion and causes routing problems for everyone on the shared mesh. Ask on Discord before you change it.

        [:fontawesome-brands-discord: Ask the Community on Discord](https://discord.gg/HrKtyuFEQk){ .md-button .md-button--primary }

### :material-flash: Get at least 1 watt { #why-1-watt }

**The short version: for a node that lives on your roof, don't buy anything under 1 watt (30 dBm).**

Most ready-made solar nodes transmit at 22 dBm. That sounds close to 30. It isn't, because dBm is a logarithmic scale:

| TX power | In watts | |
|---|---|---|
| 22 dBm | 0.16 W | Most handhelds and most ready-made solar nodes |
| 28 dBm | 0.63 W | Amplified boards |
| **30 dBm** | **1.0 W** | **Everything we recommend below** |

That's roughly **6x the transmit power**, worth something like **1.5-1.8x the distance** at which people can hear you. It's the clearest hardware difference between a node that sometimes gets through and one that's simply always there.

!!! warning "What 1 watt does, and what it doesn't"
    Transmit power only changes **how far you are heard**. It does nothing for **what you can hear**. That comes from **height, a good antenna, and a spot away from electrical noise**.

    Most people who put a 1W node on the roof also raise and upgrade the antenna at the same time, which is why everything seems to improve at once. Both halves are doing work.

    **Get it high, put a good antenna on it, and make it 1 watt. In that order.**

??? info "The legal bit: FCC power limits"
    On US 915 MHz you're allowed up to **30 dBm** out of the radio with an antenna up to **6 dBi**. Above 6 dBi of antenna gain you have to turn the radio down to match.

    - **30 dBm plus the 5 to 5.8 dBi antennas we recommend is about 35 to 35.8 dBm EIRP.** Under the limit.
    - The **RAK 1W Booster Kit** (used in the builds below) is FCC certified at **~24.5 dBm** and ships set there. The hardware will do 30 dBm; turning it up is your call and your responsibility.
    - The **Station G3** can physically exceed the limit. It defaults to 30 dBm. Leave it there.

!!! note "Be a good neighbor"
    1 watt is a lot of power. If your local mesh is already healthy and people hear you fine, running full power mostly adds noise for everyone else. Start where your node ships, confirm you're heard, and turn it up only if you need to.

---

### :material-cart: Buy one ready to go

#### :material-trophy: PeakMesh 1W (~$115-120) { #peakmesh-1w }

**Not sure what to get? Get this.** It arrives assembled, tested, and flashed. You turn it on and mount it.

PeakMesh is a one-person shop in Florida with a 5.0 rating across roughly 1,100 reviews and a long track record in the community. In September 2026 they released 1 watt versions of their four best-selling enclosures.

Every 1W model includes:

- A **1 watt radio** (RAK 1W Booster Kit, nRF52840)
- **Two solar panels** and **two 5000 mAh cells**, rated for a month or more with no sun
- A genuine **ALFA 5 dBi outdoor antenna**
- A UV-resistant enclosure in several colors, with an illuminated power switch so you can see it's on from the ground

| Model | Mount style | Price |
|---|---|---|
| [**Ultimate**](https://www.etsy.com/listing/4552505343/new-1-watt-peakmesh-ultimate-wall-pole) | Wall, pole, or gutter. **The right pick for most houses** | ~$115 |
| [**Altitude**](https://www.etsy.com/listing/4552515778/new-1-watt-peakmesh-altitude-tree) | Hangs from a tree branch | ~$120 |
| [**Magnet Climber**](https://www.etsy.com/listing/4552520488/new-1-watt-peakmesh-magnet-climber) | Magnet mount, vertical surfaces | ~$120 |
| [**Magnet Mover**](https://www.etsy.com/listing/4552519074/new-1-watt-peakmesh-magnet-mover-magnet) | Magnet mount, horizontal surfaces | ~$120 |

Putting a node on a house? **Buy the Ultimate.** Gutter and pole mounts are sold separately in the shop's Accessories section.

!!! warning "Check availability before you order"
    Each listing sells two ways: **with** the 1W radio, or **"DIY No Radio Version"** without it. RAK's 1W kits have been hard to source, so the complete version is often sold out. If it is, message PeakMesh (they reply fast), or buy the DIY version and add a [RAK 1W Booster Kit (~$39)](https://store.rakwireless.com/products/meshtastic-1w-lora-booster-kit-rak3401) yourself. The enclosure is built around that exact board.

:material-cart: **[Browse PeakMesh 1W nodes](https://www.etsy.com/shop/PeakMesh?search_query=1w)**

---

### :material-tools: Or build your own

Two good builds. The first is solar and beginner-friendly. The second is for maximum performance where you have power.

#### A. WisMesh Repeater Mini 1W, the solar build (~$125-150) { #repeater-mini-1w }

A community build that drops a RAK 1W Booster Kit into the WisMesh Repeater Mini's solar enclosure. **No soldering**, and the board fits the existing mounting holes without modification. The result is a 1 watt solar node that runs itself off the sun.

Designed and field-tested by **prayingmedic**, a member of this community, who has run one on a mast through extended testing with the battery holding steady.

| Part | Price |
|---|---|
| [RAK 1W LoRa Booster Kit (RAK3401)](https://store.rakwireless.com/products/meshtastic-1w-lora-booster-kit-rak3401) | ~$39 |
| [WisMesh Repeater Mini](https://store.rokland.com/products/wismesh-repeater-mini-reliable-coverage-expansion-for-smart-networks) (the solar enclosure) | ~$50-70 |
| [Meshnology 5Ah battery](https://www.amazon.com/Meshnology-Rechargeable-955565-Protection-Development/dp/B0FFM9MDPR/?th=1) | ~$20 |
| [Alfa 5.8 dBi whip antenna](https://store.rokland.com/collections/802-11ah-wi-fi-halow/products/alfa-network-ars-9096rp-5-dbi-indoor-antenna-for-helium-hotspots) | ~$12 |

Plus lever nuts, foam tape, M3 screws, and hose clamps. Two optional 3D-printed parts, a mast bracket and a battery spacer, are linked in the guide.

!!! tip "Point the solar panel at the sky"
    The enclosure wasn't originally designed for this build, and the panel does best facing **up** rather than out. Get that right and it holds charge fine. Get it wrong and it may not keep up, especially on a busy mesh where the node transmits more. The guide covers mounting.

:material-cart: **[Full Build Guide → WisMesh Repeater Mini 1W](/docs/wismesh-repeater-mini-1w.html){ .md-button .md-button--primary }**

#### B. Station G3, the high-performance build (~$109) { #station-g3 }

The most capable Meshtastic radio you can buy, and the successor to the long-running Station G2. Worth it if you want the best possible receive performance, or a WiFi/MQTT gateway.

- **1 watt** by default, on an ESP32-S3 with WiFi and Bluetooth
- An **adaptive low-noise amplifier**, which is the real upgrade over the G2. It handles interference and strong nearby signals far better, so it can still pick out weak, distant nodes on a busy band
- **Modular**, so a future radio or MCU upgrade doesn't mean buying a whole new device

**We call this a build because you have to solve power yourself.** It needs 9-19 V, so a USB phone charger won't run it. Three ways people handle that:

1. **Indoors or in a garage**, plugged into the wall. The simplest option
2. **In the attic**, with coax running up to a roof-mounted antenna. Keep the run to 10 feet or less of LMR-240 or better
3. **Solar**, built around a 12 V LiFePO4 battery and a charge controller. Completely doable, just physically larger than the all-in-one nodes above

!!! info "Sold in batches"
    BQ Voyage produces the G3 in batches and they sell out quickly. Check the shop for the current run.

:material-cart: [BQ Voyage Shop](https://store.bqvoy.com/product/mesh-device-station-edition/) | [Station G3 wiki](https://wiki.bqvoy.com/en/devkits/station-g3)

!!! tip "Starting from a bare board instead?"
    For a true 1 watt node, build around the **[RAK 1W Booster Kit](https://store.rakwireless.com/products/meshtastic-1w-lora-booster-kit-rak3401) (~$39)**, the same board both builds above use.

    If you want something smaller and can accept a little less power, the **[Heltec Mesh Node T096](https://heltec.org/project/t096/) (~$30-34)** is the best cheap board right now: nRF52840, an **amplified radio at 28 dBm**, dual-band GPS, and a solar connector onboard. It replaces the T114 as our bare-board pick, since the T114's radio is only 21 dBm at the same price.

    A bare board is not a node. You still supply the battery, antenna, and enclosure.

---

## :material-antenna: Antennas

Your antenna affects range more than your radio does.

**For a rooftop node, get a 5-6 dBi omnidirectional antenna.** That's the sweet spot for a house in a neighborhood. Higher gain is not automatically better: an 8-10 dBi antenna squeezes your signal into a narrow horizontal band, which is great on flat ground and bad if you're anywhere near hills.

| Antenna | Gain | Price | Best For |
|---|---|---|---|
| [**Rokland 5.8 dBi Fiberglass**](https://store.rokland.com/products/5-8-dbi-n-male-omni-outdoor-915-mhz-antenna-large-profile-32-height-for-helium-rak-miner-2-nebra-indoor-bobcat) | 5.8 dBi | ~$30-40 | :material-star: All-around rooftop (32" tall) |
| [**ALFA AOA-915-5ACM**](https://store.rokland.com/products/alfa-aoa-915-5acm-5-dbi-omni-outdoor-915mhz-802-11ah-mini-antenna-for-lora-halow-application) | 5 dBi | ~$25-35 | Compact outdoor (7" tall) |
| [**Rokland 8 dBi Low Profile**](https://store.rokland.com/products/8-dbi-omni-outdoor-915mhz-fiberglass-antenna-for-lora-halow-application) | 8 dBi | ~$50 | Flat terrain only |
| [**Muziworks 17cm Whip**](https://muzi.works/products/whip-antenna-17cm) | n/a | ~$12 | :material-star: Handheld upgrade (SMA) |
| [**MESHTAC 4 dBi Gooseneck**](https://store.rokland.com/products/meshtac-gooseneck-tactical-antenna-4-dbi-gain-sma-male-915-mhz-flexible-for-meshtastic-lora) | 4 dBi | ~$20-25 | Handheld upgrade (SMA) |

!!! tip "Keep the cable short"
    Every foot of coax costs you signal. Use **LMR-240 or better** and keep the run to **10 feet or less**.

---

## :material-link-variant: Where to Buy

| Retailer | Notes |
|---|---|
| [**PeakMesh**](https://www.etsy.com/shop/PeakMesh?search_query=1w) | Our rooftop pick. Pre-built 1W solar nodes, excellent reviews, ships from FL |
| [**Rokland**](https://store.rokland.com/) | US-based, fast shipping, great antenna selection |
| [**RAK Wireless**](https://store.rakwireless.com/collections/meshtastic) | WisMesh Pocket, Tag, and the 1W Booster Kit |
| [**BQ Voyage**](https://store.bqvoy.com/) | Station G3. Serious RF engineering. Sells in batches |
| [**Seeed Studio**](https://www.seeedstudio.com/) | Wio Tracker L1, SenseCAP card trackers |
| [**Muziworks**](https://muzi.works/) | Antennas and cases, assembled in the USA |
| [**Atlavox**](https://atlavox.com/) | Meshtastic hardware and accessories |

!!! danger "Watch out for fakes on Amazon"
    There are **a lot** of knockoff Meshtastic devices and antennas on Amazon, and a badly made antenna can leave you worse off than the stock one. Buy from the retailers above when you can. If you do buy on Amazon, check that the seller is the official brand store.

---

#### Next Steps

- [How to Connect](/docs/how-to-connect.html). Set up your new radio and join the Arizona mesh
- [Recommended Settings](/docs/recommended-settings.html). Configure your node for our network
- [Official Meshtastic Hardware List](https://meshtastic.org/docs/hardware/devices/)

---

*Prices are estimates and may vary. Check the retailer links for current pricing and stock.*
