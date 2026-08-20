# BillionTests™ website — complete documentation

For the founders, not the engineers. What this site is, what's on it, how it's built, what's still missing, and every change made to it since day one.

This folder used to be split across 5 separate files. It's now two: this one (everything about the current state of the site) and [`CHANGELOG.md`](CHANGELOG.md) (every change ever made, in order). Read this one first.

---

## 1. What this is, in one paragraph

A marketing website for **BillionTests™**, VisionExcl Technologies' urine-strip AI diagnostics platform. It is **4 static HTML files** — `index.html` (the main page), `contact.html`, `news.html`, `articles.html` — sitting in one folder next to their images and one video. There is no framework, no build step, no server-side code, no database, and **no backend of any kind**. "Deploying" this site means copying these files and their images to wherever `billiontests.ai` / `billiontests.com` is hosted. Nothing in this folder controls that hosting — see §6.

## 2. The 4 pages

| Page | Purpose |
|---|---|
| `index.html` | The main site — hero, product explanation, team, CTA. Everything else links back to it. |
| `contact.html` | A form (name/email/phone/org/reason/message) that opens the visitor's email client via a `mailto:` link — **it does not submit anywhere itself**, there is no form backend. |
| `news.html` | Two real press clippings (Dainik Jagran, one English outlet) about Pranav Asthana's IIT Kanpur urine analyzer work. |
| `articles.html` | Placeholder "coming soon" page for future long-form content. |

## 3. `index.html`, section by section (top to bottom)

1. **Nav + hero** — sticky nav, scroll-progress bar, headline, 4-stat row, two CTA buttons, scrolling logo/credibility marquee. Below the desktop breakpoint, a hamburger button toggles a mobile nav panel with the same links.
2. **How it works** — "Dip. Scan. Interpret." Three cards with real product photos.
3. **The BTCardX™** — the calibration-card innovation, a real photo of the physical card (shrunk to 300px per founder feedback), a real demo video (`how-to-use-demo.mp4`, capped to `max-w-sm`), and a "trained & proven" stat row.
4. **The crisis** — the "1.4M+" preventable-deaths statistic, full-bleed, with a per-condition breakdown table (diabetes, CKD, UTI, liver).
5. **Why us** — legacy lab-bound approach vs. BillionTests' answer, four-row comparison.
6. **No cold chain / no wait** — four value tiles contrasting urine screening with blood-based diagnostics.
7. **What it reveals** — 9-row list of every parameter the strip reads and what each flags.
8. **Two ways to deploy** — App-only vs. plug-and-play Edge Device.
9. **Credibility / team** — a pull-quote stat, then four tiers: **Founders** (4, all with photo + bio), **Development Team** (4, with bios pulled from visotonics.com), **Advisors & Mentors** (8), plus institutional credibility marks.
10. **Demo + Partners** — combined section: left half books a demo (phone + `mpsethi@billiontests.ai`), right half recruits partners (manufacturers, hospitals, diagnostic centres, foundations).
11. **Footer** — wordmark, tagline, social icons (unlinked, see §5), link columns, contact column (email/phone/city list), a Google Play badge (decorative, see §5 — no App Store badge, see below), QR code (real, scannable), copyright.

## 4. How to edit content

There is no CMS — every word, number, and email is hardcoded in the HTML. Editing is a text edit, then a browser refresh. No rebuild step, ever.

- **Stats that count up on scroll** (98%+, 20s, 1.4M+, etc.) are `<span data-count="98">` elements — change the number in `data-count`, the animation picks it up automatically. `data-dec="1"` marks the one stat that shows a decimal place.
- **Contact info** appears in three places that must be kept in sync by hand: the Demo+Partners section, the footer's Contact column, and `contact.html`'s left column. There is no single source of truth for this — a search-and-replace across all `.html` files is the safest way to change an email or phone number.
- **Primary contact email** is `mpsethi@billiontests.ai` (Maninder's own address). The footer's Contact column was trimmed to just **two** addresses — `mpsethi@billiontests.ai` and `partnership@billiontests.ai` — per direct founder instruction; the earlier `sales@` and `collaboration@` addresses were removed, not just hidden.
- **Nav spacing at laptop widths (1024–1279px)** — the desktop nav's link gap and font size step down (`gap-4`/`text-[13px]`) below the 1280px breakpoint and back up (`gap-8`/`text-[15px]`) above it, so the links never sit flush against the logo or the "Book a demo" button. If more nav links are ever added, re-check this range first — it's the tightest fit on the page.
- **Mobile nav** — on `index.html`, `news.html`, and `articles.html`, a hamburger button (`id="menu-toggle"` on the smaller pages, a similarly-named button on `index.html`) toggles a `<nav id="mobile-nav">` panel between `hidden` and `flex` via a few lines of vanilla JS at the bottom of each file. Adding or renaming a nav link means editing it in **both** the desktop `<nav>` and the mobile `#mobile-nav` panel — they're two separate lists of links, not one shared component. `contact.html` has no nav links to begin with (just a "back to site" link), so it has no hamburger.
- **Team grid** — each tier (Founders / Development Team / Advisors & Mentors) is a CSS grid of `<div>` cells. To add someone with a photo, copy an existing photo-cell's markup as a template. Every founder-tier cell now follows the same pattern: photo + name/title row, then a bio paragraph below.
- **Nav and footer links** are anchor links (`#how`, `#card`, `#crisis`, etc.) pointing at `id=` attributes further down the same page. Renaming a section's `id` silently breaks every link pointing at it — no error, the link just stops scrolling anywhere.
- **Images** are referenced by plain relative filename (`abhishek.jpeg`, `qr.jpeg`, etc.) sitting next to the HTML. This means **the HTML files can't be shared on their own** — email or WhatsApp-ing just `index.html` breaks every photo. Zip the whole folder, or share a hosted link, to keep images intact.

## 5. What's real vs. placeholder right now

**Real and live:** all copy and stats, the BTCardX™ photo, three how-it-works photos, all 4 founder photos+bios, 4 development-team photos+bios, 8 advisor entries, the real demo video (embedded), the real scannable QR code, phone number, primary + secondary emails, a favicon (`favicon.svg`, a "B" monogram in the site's own palette, linked from all 4 pages).

**Decorative / not functional — flagged, not hidden:**
- **The Google Play badge** in the footer is an image only, not a link — no real Play Store listing exists yet. There is deliberately **no App Store badge** — it was removed on request since the app isn't iOS-ready yet; re-add `badge-appstore.png` (still in the folder, just unreferenced) once an iOS build exists.
- **Social icons** (LinkedIn, Facebook, Instagram, X) in the footer all point to `#` — no real profile URLs have been provided.
- **`contact.html`'s form** doesn't submit to any server — it opens the visitor's email client pre-filled via `mailto:`. This works but depends on the visitor having a configured email client, and produces no record on your end unless the email actually gets sent.

**Known gaps, not yet addressed:**
- **Priyanka Priyadarshini has no bio line** — her founder-grid cell shows photo/name/title only. No bio text has been supplied for her at any point.
- **No page-preview metadata.** No `<meta name="description">`, no Open Graph tags — sharing the site link in WhatsApp or elsewhere currently shows a bare URL with no title/image/blurb. (A favicon now exists — see above — but that's the browser-tab icon, not the link-preview card.)
- **No legal pages.** No Privacy Policy or Terms of Service, despite the product handling personal health data and actively courting hospital/CSR partners who will look for this.
- **Non-website materials untouched.** The letterhead, brochure, pitch deck, and visiting card in this folder (see §7) have never been edited as part of this work — only the 4 website pages have been. If founder feedback says "update everywhere," it has only ever been applied to the site.

## 6. Hosting, deployment, and backend — the honest answer

**There is no backend.** No server code, no database, no API, no user accounts, no credentials of any kind belong to this project. Every page is a static file that a browser renders entirely on its own, pulling Tailwind CSS and Google Fonts from public CDNs at load time. There is nothing to secure, patch, or provision beyond wherever the static files are hosted.

**Nothing in this folder says where the site is actually hosted today.** No hosting config, no CI/CD file, no deploy script, no DNS notes. Before assuming `billiontests.ai` already serves this exact folder, or before trying to push an update, confirm with whoever currently owns that domain/hosting account. This is the one piece of infrastructure knowledge that lives outside this folder entirely and needs to be captured from whoever set it up.

**To preview locally:** any static file server pointed at this folder works. This repo's `.claude/launch.json` already has one configured (`npx serve -l 5500 .`), served at `http://localhost:5500/index.html`. Do not just double-click `index.html` — some browsers block relative image loading from a bare `file://` path, so it won't render correctly outside a real server.

**To ship an update:** copy the changed `.html` file(s) plus every image/video they reference to wherever the live site is hosted. Any static host — Netlify, Vercel, GitHub Pages, or a plain web server — works with zero code changes.

**To hand someone the raw files** instead of a live link (email, WhatsApp, USB): zip the whole folder, not just the HTML. Every photo is a relative filename reference; the HTML alone renders with every image broken.

## 7. Supporting files in this folder

These are the source materials the site's copy, photos, and bios were pulled from — kept in the repo for traceability, not referenced by any HTML file:

| File | What it is |
|---|---|
| `BT_march26 (1).pptx`, `BT_march26_Original PPT.pptx`, `BT_march26_Changes suggested.pptx`, `BT_version_V3_12_08_2026.pptx` | Successive versions of the company pitch deck |
| `BillionTests Brochure .pdf` | Print/digital brochure — **not edited as part of this work** |
| `BillionTests_BCKIC_Proposal_v3.docx` | An earlier grant/incubation proposal document |
| `WEBSITE CHANGES 13_08_26.docx`, `PPT ChangesUpdated (1).docx`, `BillionTests_Website_points_16-08-2026.docx`, `BillionTests_WEBSITE_CHANGES_18_08_26.docx` | Four rounds of written, founder-provided change requests — the authoritative source for most branding/content decisions logged in `CHANGELOG.md` |
| `CityImaging Certificate.pdf`, `sample report from app.pdf` | Reference/supporting documents, not currently used on the site |
| `qr.jpeg` | The real, live QR code shown on the site |
| `how-to-use-demo.mp4` | The real product demo video embedded in the BTCardX™ section |
| `favicon.svg` | The site's favicon — referenced by all 4 pages |
| `badge-appstore.png` | The App Store badge image — still in the folder but currently unreferenced by any page (see §5) |
| `three-step-composite.jpeg`, `karan-bahuguna.jpeg`, `team-photo-unconfirmed-1/2.jpeg`, `sahil-reddy.jpeg`, `maninder.png`, `pramod.png` | Orphaned photos — superseded by newer versions or people removed from the final roster. Safe to ignore; kept rather than deleted in case they're needed again. |

## 8. Design system, in brief

- **One accent colour** — Tailwind token `teal`, hex `#1E69D2`, defined once in the `tailwind.config` block at the top of each HTML file. Every blue element on every page — links, buttons, stat numbers, borders — pulls from this single token. Changing that one hex value re-colours the entire site at once.
- **Fonts** — Fraunces (serif, display/headlines) + Inter (sans, body text and uppercase labels), both loaded from Google Fonts.
- **Theme** — dark only, throughout (`ink` #0A1930 background, `paper` #F3F7FC text, `mist` #122A4D card surfaces, `stone` #A9B9D6 muted text). No light-mode section anywhere.
- **Motion** — scroll-reveal fades, a count-up animation on stat numbers, a scroll-progress bar, all built with vanilla `IntersectionObserver` and respecting `prefers-reduced-motion` (disabled entirely for visitors who've asked their OS for reduced motion).

## 9. The 5 old doc files, for reference

`01-whats-here.md`, `02-content-and-editing.md`, `03-known-gaps.md`, `04-design-language.md`, and `05-run-and-ship.md` have been merged into this single file and deleted. Everything they covered is now in §3–§8 above. `CHANGELOG.md` is new — it didn't exist before this pass.
