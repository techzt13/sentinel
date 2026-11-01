# Pitch — Cardputer "Flipper-Style" Build

## Lead angle: the smart-home guardian

### The problem

The average home now has 20+ connected devices — and the owner has no idea what's
actually on their network, whether their WiFi password would survive ten minutes of
attack, or why the internet dies every evening. Meanwhile, every gadget ships with its
own remote and its own app.

### The product

One palm-sized device, ~$80, that answers the three questions every homeowner has:

1. **"What's on my network?"** — full LAN + port scan finds every device, including
   the forgotten smart plug with a wide-open port. A channel-congestion scan explains
   the 8pm slowdown.
2. **"Is my network actually secure?"** — it attacks *your own* network the way a real
   attacker would: captures the handshake, tries to crack the password, tests deauth
   resistance. If your own device can break in, you know to fix it *before* someone
   else tries.
3. **"Can I get rid of this pile of remotes?"** — captures and replays 433 MHz outlets,
   fans, and LED strips, plus IR TV/AC. One device becomes the universal remote for the
   whole apartment. Custom NFC tags by the door: tap to join guest WiFi, tap for
   lights-off mode.

### The kicker

No subscription, no cloud service, no account, no data leaves your home. It works
entirely offline — which, for a *security* product, is the point.

### Taglines

- *"A security audit and a universal remote in your pocket — for less than a nice dinner out."*
- *"Your smart home is talking. This lets you finally listen."*
- *"Find the holes in your own network before someone else does."*

### The demo (what wins the room)

Plug it in, scan **your own hotspot** — the device list appears live. Then race the
"crack my own WiFi" demo against a deliberately weak password like `homerouter123`.
It cracks in seconds. Then: *"That could be your parents' router. Now you know why it
matters."*

---

## Secondary audiences

### The curious student / young hacker

Wants hands-on cybersecurity, but a Flipper Zero is $170+ and courses are theory.

> *"A Flipper Zero teaches you to press buttons. This teaches you how the buttons work."*

### The IT student / junior pentester

Needs a portable audit kit for coursework, CTFs, and homelab practice.

> *"The cheapest way to put 'hands-on wireless security experience' on a resume — and actually mean it."*

### The educator / club leader

Slides don't teach 'don't trust public WiFi'. One live captive-portal demo on a test
router does. Class sets are affordable at ~$80/unit.

> *"The most persuasive cybersecurity lesson is watching your own password appear on the attacker's screen."*

### The maker

A weekend hardware project that's actually useful afterward: no soldering,
off-the-shelf parts, two large open-source communities, endless room to mod.

---

## Elevator pitch

*"A pocket-sized, multi-radio security research device for ~$80 — half the price of a
Flipper Zero — that audits WiFi networks, reads and emulates NFC cards, captures
sub-GHz remotes, and blasts IR, all from a keyboard-driven computer that fits in your
palm. It dual-boots two open-source firmwares, and every part is off-the-shelf with no
soldering."*

## One-line value proposition

*"Flipper-Zero-class capability at half the price — but unlike a Flipper, you built it,
you can modify every line of its firmware, and owning it means you actually understand
it."*

## Anticipated Q&A

- **"Isn't this just a hacking tool?"** — It's a security *auditing* tool. Every demo
  runs against my own lab network; the repo has an explicit rules page. The same
  features power defensive use: deauth detection, skimmer detection, rogue-AP hunting.
- **"Why not just buy a Flipper?"** — Cost, a real keyboard, better WiFi capability,
  and the build itself is the learning. A Flipper is a product; this is a project.
- **"What's the weakness?"** — No 125 kHz RFID, single radio means one band at a time,
  and there's a known firmware bug on the Cap's config persistence. I can name them
  because I actually built it.
