# PR #28, split into seven

PR #28 was one 21-file, +1143/−657 change. It is now seven, four of which are
under a minute to review. Every branch is pushed to `rancur/azmsh-site` and has a
rendered preview.

**Preview index (start here): <https://rancur.github.io/azmsh-site/preview/>**

I could not open the pull requests myself — this session's GitHub access is
scoped to the fork, not to `ArizonaMeshtasticCommunity`. Each section below has
a "Create PR" link plus the exact title and body to paste. Same for closing #28:
the comment is drafted at the bottom.

## Merge order

```
Logan's #30  →  1, 2, 3, 4  (any order, any time)  →  5  →  6  →  7
```

1–4 are independent. 5, 6 and 7 build on each other, so **open 6 only once 5 has
merged, and 7 once 6 has merged** — GitHub can't chain cross-fork PRs, so an
early-opened 6 would show 5's commits too. Each branch is already based on
current `main` (`f4b01e5`); the later ones just need `git rebase origin/main`
once their predecessor lands.

## Verified before pushing

- `mkdocs build --strict` passes on **every branch standing alone**, merged onto
  upstream `main` by itself. (Same install list as `.github/workflows/deploy.yml`.)
- **All seven merge cleanly on top of Logan's #30**, tested by applying `#30.diff`
  to `main` and merging each branch into it. Details below.
- All seven merge cleanly with each other, and the union builds `--strict`.
- No absolute `/docs/*.html` link survives anywhere in the union.

---

## 1 · Footer links resolve at any base path

**Branch** `claude/split-01-footer-links` · 3 files, +33/−6 · ~1 min
[Create PR](https://github.com/ArizonaMeshtasticCommunity/azmsh-site/compare/main...rancur:azmsh-site:claude/split-01-footer-links?expand=1)
· [Preview](https://rancur.github.io/azmsh-site/preview/split-01-footer-links/)

> **Title:** `fix(footer): resolve Accessibility/Privacy links at any base path`

The Accessibility and Privacy links added in #25 are hardcoded as
`/accessibility.html` and `/privacy.html`. Those resolve on azmsh.net but 404 on
any build served from a sub-path, which is every PR preview — so the two pages
that exist specifically for accessibility compliance are the two you can't reach
when reviewing a change.

Moved out of the `copyright:` string into an override of Material's copyright
partial, which builds them from `{{ base_url }}`. Also relativized the four
`/docs/wismesh-repeater-mini-1w.html` links in Recommended Hardware, which have
the same problem.

**What to look at:** the footer of any page on the preview, then the same page on
the [before build](https://rancur.github.io/azmsh-site/preview/main/) — the links
404 there.

**Not in this PR:** links whose target pages move in PRs 6 and 7.

---

## 2 · Stop hardcoding the default PSK and preset names

**Branch** `claude/split-02-dehardcode-presets` · 2 files, +7/−8 · ~1 min
[Create PR](https://github.com/ArizonaMeshtasticCommunity/azmsh-site/compare/main...rancur:azmsh-site:claude/split-02-dehardcode-presets?expand=1)
· [Preview](https://rancur.github.io/azmsh-site/preview/split-02-dehardcode-presets/)

> **Title:** `docs: stop hardcoding the default PSK and preset names`

The privacy page quotes the default key literally as `AQ==` and names
LongFast/MediumFast, and Suggested Channels lists `MediumFast` as a row in the
community channel table — which reads as an invitation to add your own primary
channel a second time as a secondary. Replaced with the general description in
both places, dropped the row, and collapsed the Android accordion so both
platform sections start the same way.

**What to look at:** Suggested Channels → the table and the two platform
accordions; Privacy Policy → "public-channel data is not private".

**Not in this PR:** the "your primary is separate" callout, which needs the Start
Here page. It ships in PR 6.

---

## 3 · 900 MHz ISM band, not one channel

**Branch** `claude/split-03-host-a-node-band` · 1 file, 2 lines · ~30 sec
[Create PR](https://github.com/ArizonaMeshtasticCommunity/azmsh-site/compare/main...rancur:azmsh-site:claude/split-03-host-a-node-band?expand=1)
· [Preview](https://rancur.github.io/azmsh-site/preview/split-03-host-a-node-band/)

> **Title:** `docs(host-a-node): describe the 900 MHz ISM band, not one channel`

Host a Node tells prospective hosts that Meshtastic "operates on 906.875 MHz".
That's one LongFast slot, not the band — and the same page already says
"902-928 MHz unlicensed band" a few questions further down, so it contradicts
itself. Says "900 MHz ISM band" in both spots now.

**Worth deciding separately:** the site uses three phrasings for this band
("900 MHz ISM" here, "915 MHz ISM limit" in Recommended Hardware, "unlicensed
915 MHz" elsewhere). "902-928 MHz ISM (commonly called 915 MHz)" everywhere would
settle it — happy to do that as a follow-up if you want it.

---

## 4 · Remove two unreachable pages

**Branch** `claude/split-04-remove-orphan-pages` · 2 files, −187 · ~1 min
[Create PR](https://github.com/ArizonaMeshtasticCommunity/azmsh-site/compare/main...rancur:azmsh-site:claude/split-04-remove-orphan-pages?expand=1)
· [Preview](https://rancur.github.io/azmsh-site/preview/split-04-remove-orphan-pages/)

> **Title:** `chore(docs): remove two unreachable pages`

`docs/connect.md` and `docs/recommended_configuration_settings.md` are in neither
`nav` nor `not_in_nav`, and nothing in the repo links to either, so the only way
to reach them is to guess the URL. Both carry stale values — `connect.md`
hardcodes "Hop Count: 3 hops" — and the second says "This page is kept for
reference" in its own body while duplicating Recommended Settings.

**One thing to decide:** `docs/connect.html` did exist as a URL. If you'd rather
keep a redirect stub than delete it outright, say so and I'll add one.

---

## 5 · FAQ & Troubleshooting

**Branch** `claude/split-05-faq-hub` · 4 files, +252/−3 · ~10 min
[Create PR](https://github.com/ArizonaMeshtasticCommunity/azmsh-site/compare/main...rancur:azmsh-site:claude/split-05-faq-hub?expand=1)
· [Preview](https://rancur.github.io/azmsh-site/preview/split-05-faq-hub/docs/faq.html)

> **Title:** `feat(docs): add a single FAQ & Troubleshooting page`

There is nowhere on the site to send someone who is stuck. The answers live in
Discord threads and get retyped every week; the only troubleshooting on the site
is one "Check Your Settings" step buried in What Now?.

One page, ten anchored sections: not receiving · receive-works-can't-send · not
seeing your own messages · Bluetooth · USB not detected · wrong map location ·
403 Forbidden · claiming a node · flashing problems · DM "No Channel". Every
section is deep-linkable, so a helper in #i-need-help can paste one URL.

**What to look at:** the jump list at the top of the preview, then
`#cant-send` and `#forbidden-403` — the two that come up most.

**Note on the links:** this page's links to Start Here / How To Test /
Additional Settings currently point at How to Connect / What Now? / Recommended
Settings, because those are what exists today. PRs 6 and 7 repoint them. That's
why a few lines in this file get rewritten again later.

---

## 6 · Start Here, then How To Test

**Branch** `claude/split-06-start-here` · 12 files, +357/−240 · ~20 min
**Open only after 5 merges.**
[Create PR](https://github.com/ArizonaMeshtasticCommunity/azmsh-site/compare/main...rancur:azmsh-site:claude/split-06-start-here?expand=1)
· [Preview](https://rancur.github.io/azmsh-site/preview/split-06-start-here/docs/start-here.html)

> **Title:** `feat(ia): one linear onboarding path - Start Here, then How To Test`

Today a newcomer lands on Home, clicks "Learn how to connect", and gets a page
that stops at Bluetooth pairing. The Arizona radio settings, the primary
channel, the self-test, and the "did it actually work?" check are on other pages
or not on the site at all.

| Before | After |
|---|---|
| Home → How to Connect → What Now? | Home → **Start Here** → **How To Test** |
| pairing ends the guide | one page: flash → pair → LoRa settings → primary channel → optional MQTT → send `test` |
| Discord link, no context | gated boxes showing *which* settings you need, with the values in Discord |

- **Start Here** is new. It calls out the two things people actually get wrong:
  the Frequency Slot left on auto, and renaming the primary channel.
- **What Now? → How To Test.** Git tracks it as a rename; the real content delta
  is ~30 lines. It fixes the `/node claim` command (now
  `/node action:claim node_identifier:<your-node-id>`), stops hardcoding
  MediumFast, and explains what a tapback is.
- Old URLs keep working: `docs/how-to-connect.html` and `docs/what-now.html`
  become meta-refresh stubs. **Click them on the preview** — worth confirming,
  because mkdocs does not link-check raw HTML, so a typo there would ship green.

**On the Discord-gated boxes** (this is #27's work, rebased in): it's
presentation, not a security control — the real values are never sent to the
browser, the placeholders are fake. I added two things before pushing:
`aria-hidden` on the placeholders plus a screen-reader-only "value shared in
Discord", because otherwise a screen reader reads `ExampleKey==` out as if it
were the real key; and a `min-height` so the overlay can't clip out of the box at
200–400% zoom.

**Logan's #30:** merges clean. This PR rewrites the line directly above where
#30 inserts the affiliate disclosure; I test-merged them and the result keeps
the disclosure intact with the link updated.

---

## 7 · Additional Settings

**Branch** `claude/split-07-additional-settings` · 8 files, +375/−178 · ~20 min
**Open only after 6 merges.**
[Create PR](https://github.com/ArizonaMeshtasticCommunity/azmsh-site/compare/main...rancur:azmsh-site:claude/split-07-additional-settings?expand=1)
· [Preview](https://rancur.github.io/azmsh-site/preview/split-07-additional-settings/docs/additional-settings.html)

> **Title:** `feat(ia): Additional Settings supersedes Recommended Settings`

Recommended Settings is ordered by topic, not by anything you see in the app, so
following it means hunting for each setting. It also stops short of several
settings people ask about (User, Bluetooth, Display, Network, Power).

The new page follows the Meshtastic app's own order — Radio Configuration,
Device Configuration, Module Configuration — so you can read down the page with
the app open next to you. `docs/recommended-settings.html` becomes a redirect
stub.

Two changes from how this page was originally drafted:

- The three section banners were `#` H1s, giving the page four H1s. Demoted, so
  there's one H1 and the table of contents nests properly.
- The MQTT box blurred **Root topic** while the tip three paragraphs below
  publishes the convention in plain text. Root topic isn't a secret, so it now
  shows `msh/US/AZ/{city}` un-blurred; only the broker host, username and
  password stay gated.

**What to look at:** the MQTT section on the preview (that gated box is raw HTML
indented inside a numbered list — the most fragile construct in the whole
change), and `docs/recommended-settings.html` to confirm it redirects.

---

## Three things from #28 I deliberately left out

1. **The `deploy.yml` change.** #28 deletes the entire 52-line pa11y
   accessibility job. That came from a commit labelled "keep deploy.yml matching
   fork main (push-scope workaround)" — a fork-sync artifact, not an intended
   change. `.pa11yci` is still in the repo, so the deletion would orphan it, and
   the gated-settings CSS is exactly the kind of thing that job audits. Dropped.
   The pa11y URL list is updated instead, as pages are added and renamed.
2. **`cant-transmit.md` and `flashing-gotchas.md`.** #28 adds these as redirect
   stubs, but neither URL has ever existed in this repo, so they redirect nothing
   and leave two permanent orphans. Dropped. If those URLs were published
   somewhere I can't see — Discord pins, an old site — tell me and I'll add them.
3. **A `Wi-Fi` → `WiFi` rename** through Host a Node. `Wi-Fi` is the correct
   form; that was a regression riding inside the RF fix. Dropped.

## Worth a look at some point (not fixed here)

- **Raw HTML bypasses `--strict`.** The redirect stubs and the home page's
  `<a href="docs/start-here.html">` aren't link-checked, and they only work
  because the `offline` plugin forces `use_directory_urls: false`. If that
  plugin ever goes, every stub breaks with green CI. I left a comment in each
  stub; setting `use_directory_urls: false` explicitly would make it deliberate.
- **A few claims in the FAQ are unsourced** — stock antennas "often ~69%
  efficient", "Install Meshtastic UI boot-loops Heltec V3/V4". Plausible, but
  someone who knows should confirm before they age badly.

---

## Comment to post when closing #28

> Closing this in favour of seven smaller PRs — same work, reviewable one piece
> at a time, each with a rendered preview.
>
> Merge in any order: #A footer links · #B de-hardcode presets/PSK · #C
> 900 MHz ISM band · #D remove two orphan pages
>
> Then in sequence: #E FAQ & Troubleshooting → #F Start Here + How To Test →
> #G Additional Settings
>
> Previews: https://rancur.github.io/azmsh-site/preview/
>
> Three things from this PR are intentionally **not** in the split: the
> `deploy.yml` change (it deletes the pa11y job — that was a fork-sync artifact,
> not intended), the `cant-transmit` / `flashing-gotchas` redirect stubs (they
> redirect URLs that never existed here), and a `Wi-Fi` → `WiFi` rename.
>
> @logans-stuff's #30 should go in first — all seven were test-merged against it
> and are clean.

*(swap #A–#G for the real numbers once the PRs are open)*
