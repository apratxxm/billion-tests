# What's here

The whole site is one file: `index.html`. No React, no build tool, no npm install — open it in a browser or point any static file server at the folder and it runs. Styling is Tailwind loaded from a CDN `<script>` tag plus a small hand-written `<style>` block for animations and a few colours Tailwind's default palette doesn't have. Icons are Lucide, also loaded from a CDN. There is no backend, no database, no form that submits anywhere.

## The page, section by section

1. **Nav + hero** — sticky nav with a scroll-progress bar, the headline, a 4-stat row (98%+ accuracy, 20s, 10+ parameters, 30+ strip types), two CTA buttons, and a scrolling logo/credibility marquee.
2. **How it works** — "Dip. Scan. Interpret." Three cards, each with a real photo now (a urine-cup-and-strip shot, a phone-scanning-the-BT-Card shot, a results-report shot).
3. **The BT Card™** — the calibration-card innovation explained, with a real photo of the actual reference card, plus a stat block (training images, samples validated, parameters, "TRL 9").
4. **The crisis** — the "1.4M+" preventable-deaths statistic, full-bleed, with a breakdown table by condition (diabetes, CKD, UTI, liver).
5. **Why us** — a four-row comparison: legacy lab-bound approach on the left, BillionTests' answer on the right.
6. **No cold chain / no wait** — four value-prop tiles contrasting urine screening with blood-based diagnostics.
7. **What it reveals** — a 9-row list of every parameter the strip reads (glucose, protein, leukocytes, etc.) and what each one can flag.
8. **Two ways to deploy** — App-only vs. the plug-and-play Edge Device, side by side.
9. **Credibility** — a pull-quote stat, the full team grid (12 people — 2 with photos and bios, 3 more with photos only, 7 with name only), a "proven AI" pedigree row (Checko.ai, Upjao.ai, Tracksure), and a row of institutional credibility marks.
10. **Demo + Partners** — one section split in two: left half books a demo (phone number, CBO title), right half recruits partners (strip manufacturers, hospitals, diagnostic centres, foundations) with a "Want to join us?" mailto button.
11. **Footer** — big wordmark, tagline, social icons, a link column, a five-address contact column, a "scan to download" QR block, and copyright.

## What's real vs. placeholder

**Real and live:** all copy, all stats, the BT Card photo, the three how-it-works photos, Maninder's and Pramod's photos+bios, four more team photos (Sahil, Pranav, Ritu, plus Sethi/Pramod already counted), the phone number, five contact email addresses, the domain link.

**Present in the project folder but not on the page:** `how-to-use-demo.mp4` — a real ~1.3MB product demo video recovered from the pitch deck — is sitting unused; nothing on the page links to or embeds it. `three-step-composite.jpeg` (a polished single-image version of the how-it-works steps) and `karan-bahuguna.jpeg` (a team photo for a "Product Leader" not currently in the team grid) are also unused.

**Decorative, not functional:** both "scan to download" QR graphics (the floating widget and the footer one) are a CSS checkerboard pattern, not an actual encoded QR code — see `03-known-gaps.md`.

See `03-known-gaps.md` for the full list of what's missing, broken, or still an open decision.
