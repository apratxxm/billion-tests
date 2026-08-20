# Changelog — every change, start to now

A complete, chronological log of everything done on the BillionTests™ website, from the very first design brief to the most recent commit. Grouped by phase, in order. Git commit hashes are given where the change was committed; earlier design-iteration work (wireframes, variant rounds) predates commits and is logged from the working history instead.

For what the site looks like *today* (not how it got there), see [`README.md`](README.md).

---

## Phase 1 — Design brief and rejection of first drafts

- Three existing reference HTML files were reviewed against the founder's brief and **rejected outright** as looking too generic/AI-generated. Goals set instead: strong visual hierarchy, real negative space, bento-style layouts, subtle motion, a footer with real design intent — not a template.
- Full wireframes were built and reviewed **before** any polished mockup, at the founder's explicit request ("show me wireframes completely fleshed out before making the website").
- For each major section, **3 layout variants** were produced varying axis of design (spacing, layout, shape, information density, visual hierarchy), explicitly modeled on awwwards-style reference sites rather than generic SaaS templates.
- Per-section variant feedback was collected and actioned round by round — e.g. the hero headline was iterated 3 times before landing on "INDIA'S FIRST UNIVERSAL VISION-AI DIAGNOSTICS PLATFORM"; "How it works" settled on variant C; the health-crisis section merged elements of variants B and C per direct instruction.

## Phase 2 — Initial build and theme conversion

- `index.html` was assembled as a single static file: Tailwind CDN + custom config, Fraunces/Inter via Google Fonts, Lucide icons via CDN, vanilla-JS scroll-reveal / count-up / scroll-progress-bar, all respecting `prefers-reduced-motion`.
- The site was converted from an original light/dark alternating-section theme to **fully dark, throughout** — no light-mode sections left anywhere.
- The colour system went through several full palette swaps before settling: initial editorial palette → full dark-blue/sky-blue palette → a **single unified accent colour** (`teal`) used for every blue element site-wide, replacing what had been several different one-off blue hex values scattered through the file.
- **`72ad27e`** — Initial commit.
- **`34834c6`** (2026-08-03) — Accent blue set to `#1E69D2`; step-card stagger spacing fixed; CBO name added to the demo section.

## Phase 3 — Design-critique loop, contact page, real bios

- An Opus-model design-critique pass was run twice (critique → fix → re-verify), explicitly scoped to **only** colour/contrast/visual-hierarchy/negative-space — not content or copy. It caught and fixed two real misses: a gradient panel that only matched the target accent colour at one edge, and a hero stat number sized large enough to read as a different visual weight than the rest of the accent usage.
- Section vertical rhythm was standardized through one shared `.sec` class; two sections that had bespoke padding values were brought back in line with it.
- `contact.html` was built: a form (name/email/phone/org/reason/message) that opens the visitor's email client via `mailto:` — no server-side submission, by design (no backend exists in this project).
- The team grid was reorganized into tiers and given real bios for Pranav Asthana, Ritu Mishra, and Mohini Behera, sourced by cross-referencing `visotonics.com/company/about` (same founding team runs both ventures).
- Two team members — Karan Bahuguna and Shreyan Awasthi — were added at this stage based on a photo-to-name match in source pptx slide XML (Shreyan's match was only medium-confidence). Both were fully removed later, in Phase 5, once an authoritative document confirmed the final roster excludes them.
- Project documentation (`docs/`) was created for the first time, modeled on the structure of `Visotonics/new/visotonics/docs` (not copied from it, per explicit instruction).
- **`ed7fed0`** (2026-08-06) — Add contact form, unify team grid with real bios, and project docs.

## Phase 4 — Real QR code, BTCardX layout iteration

- The two "scan to download" QR graphics (floating widget + footer) were **fake** — a CSS checkerboard pattern, not an encoded QR code. Replaced with a real, scannable QR image (`qr.jpeg`).
- **`c8bad98`** (2026-08-08) — Replace fake QR placeholders with real scannable app-download code.
- **`90c8e49`** (2026-08-08) — Updated `qr.jpeg` to a corrected version.
- The BTCardX™ section (photo + demo video + stats) went through **4 rounds of layout iteration** in a single week, each a direct response to founder feedback on how it read visually:
  - **`0852914`** (2026-08-12) — First embed of the real demo video alongside the reference-card photo, heading above, description below, as part of a larger batch of changes (see Phase 5 below — same commit).
  - **`04c8c1d`** (2026-08-12) — Reworked to equal-width photo/video columns; stats moved below into a horizontal 4-up row instead of a vertical list.
  - **`f194ebd`** (2026-08-12) — Photo centered and width-constrained on its own row; video moved below the stats table, spanning full width with a centered label.
  - **`61b94bf`** (2026-08-12) — Photo widened to near-full width with a slight inset on both sides.
  - (Later, in Phase 6, the photo was **shrunk back down** to 300px and the video capped to `max-w-sm` — direct founder feedback that both had become too large.)

## Phase 5 — First rebrand round: BTCardX, address, news pages

Committed together in **`0852914`** (2026-08-12), driven by a large WhatsApp feedback dump plus new founder photos and 3 attached source documents:

- Renamed "BT Card" → **"BTCardX"** across the site; added a trademark line (at this point still "BillionTests.ai" branding).
- Replaced the street address with a city list: Mumbai, Ahmedabad, Lucknow, Bhubaneshwar, Mohali, Washington DC.
- Removed an unsupported "30+ strip types" claim; replaced with a note on CDSCO-licensed strip compatibility.
- Restructured the team grid into 4 tiers: Founders / Development Team / Team / Advisors & Mentors, matching an updated org chart.
- Restored `pramod.png`, which had been accidentally deleted in an earlier edit.
- Added `news.html` and `articles.html`, with real press coverage on the News page, linked from nav and footer on every page.
- Embedded the real product demo video in the BTCardX section for the first time.

## Phase 6 — Second rebrand round: BillionTests.AI, 8-person founder roster

Driven by a second large WhatsApp dump: 5 new founder photos (Maninder in a turban, Priyanka, Abhishek in a brown suit, Alok in a green suit) plus 3 new source documents (`WEBSITE CHANGES 13_08_26.docx`, `PPT ChangesUpdated (1).docx`, `BT_version_V3_12_08_2026.pptx`).

- **`b556c58`** (2026-08-16):
  - Rebranded to **"BillionTests.AI"** throughout (nav, page `<title>`, footer, copyright) — superseding the plain "BillionTests" name used until this point. `BTCardX™` trademark treatment kept consistent alongside it.
  - Replaced Sahil Reddy with **Priyanka Priyadarshini** (Co-founder & CGO) in the founder roster.
  - Added **Alok Kulshrestha** (Co-founder & COO) and **Abhishek Chaturvedi** (Co-founder & CPO) with real photos, titles, and bios, finalizing the roster at **8 founders/leadership**.
  - Updated Maninder's photo and formalized his title as **Co-founder & CBO**.
  - **Removed Karan Bahuguna and Shreyan Awasthi** entirely — confirmed by the authoritative PPT-changes document as not part of the final roster.
  - Removed the "Proven AI, already deployed at national scale" pedigree section (Checko.ai / Upjao.ai / Tracksure references), per the same document.
  - Fixed British spelling: "analyzer" → "analyser" in the why-us headline.
  - Corrected the footer address to the right city list and order.
  - Removed a "CDSCO prep" line from the footer trust column.
  - Added the source reference docs (V3 deck, PPT/website change lists) to the repo for traceability.
- A full mobile-responsiveness audit was run at this point (an initial regex-based pass produced false positives from a flawed exclusion pattern; redone by manually inspecting the actual class strings). Result: layout is responsive down to phone width **except** the nav, which has no small-screen alternative — logged as the top open gap.

## Phase 7 — Third rebrand round: trademark symbol, final content polish

Driven by a third document, `BillionTests™_Website points_16-08-2026.docx`, shared via a WhatsApp Desktop local file transfer — extracted for both its 11 text feedback points and 12 embedded reference images.

- **`c02c9a1`** (2026-08-17):
  - **Reversed the previous ".AI" branding decision** — switched from "BillionTests.AI" to **"BillionTests™"** (trademark symbol, not a domain-style suffix) across all 4 pages, per this newest and most authoritative instruction. This is the branding as it stands today.
  - Added missing founder introduction/bio lines for Maninder, Alok, and Abhishek (their cards previously showed photo/name/title only); fixed "AI enabled and Lab Testing" wording to "AI enabled Lab Testing Solution."
  - Shrunk the oversized BTCardX reference-card photo (to 300px) and demo video (`max-w-sm`) — both had grown too large across the Phase 4 layout iterations.
  - Replaced the unused `info@billiontests.ai` address with **`mpsethi@billiontests.ai`** as the primary contact address, in the footer, `contact.html`, and `news.html`.
  - Added Google Play / App Store badge images to the footer's app-download block — cropped from an image embedded in the source docx. **Not linked to a real store listing** — decorative only, since no store URLs exist yet.
  - Renamed the Demo+Partners CTA button from "Book a demo" to **"Contact for demo & Partnership"**, and added Maninder's email alongside the phone number in that section's credit line.
  - Fixed `contact.html`'s city list ("Bombay" instead of "Mumbai," matching the footer and the source document's spelling) and balanced the two news-page card image heights, which had been cropping to different aspect ratios.

## Phase 8 — Documentation consolidation

- **2026-08-17.** The original 5-file `docs/` structure (`README.md`, `01-whats-here.md`, `02-content-and-editing.md`, `03-known-gaps.md`, `04-design-language.md`, `05-run-and-ship.md`) was consolidated into **two files**: a single comprehensive `README.md` covering site structure, content editing, real-vs-placeholder status, hosting/backend, supporting files, and the design system; and this file, `CHANGELOG.md`, logging every change made from the first design brief onward. Requested directly by the founder for knowledge-transfer purposes — readable without engineering background, no unnecessary technical depth.

## Phase 9 — Navbar spacing bug fix

- **2026-08-18.** Founder-reported bug: "spacing and margins issue on the navbar." Verified directly against the live layout at multiple window widths — at 1024–1150px (a common laptop screen range, and the exact width where the desktop nav first turns on), the nav links had **zero pixels of gap** to both the logo and the "Book a demo" button, sitting flush against both with no breathing room. Above ~1280px the layout was fine (roughly 52px of gap on each side).
- **Fix:** the nav's link gap and font size now step down (`gap-4`, `text-[13px]`) between 1024px and 1280px, and step back up (`gap-8`, `text-[15px]`) above 1280px via a `xl:` breakpoint. Verified via direct DOM measurement: the gap on each side of the nav went from 0px to 31px at 1024px width, with zero change to the layout at 1280px and above.

## Phase 10 — Fourth feedback round: contact trim, App Store removal, favicon

Driven by a fourth document, `BillionTests_WEBSITE_CHANGES_18_08_26.docx`, shared via WhatsApp Desktop, plus a direct request to add a favicon.

- **2026-08-18** (uncommitted at time of writing — see `git log` for the actual commit once pushed):
  - Fixed "Post Graduate" → "Postgraduate" in Maninder's bio line, matching the spelling style used for the other three founders.
  - Trimmed the footer's Contact column from four email addresses down to **two**, per direct instruction: `mpsethi@billiontests.ai` and `partnership@billiontests.ai`. Removed `sales@` and `collaboration@` entirely, not just hidden.
  - **Removed the Apple App Store badge** from the footer's "get the app" block — the founder noted the app isn't ready for iOS yet, so showing an App Store badge misrepresented availability. The Google Play badge remains as the sole download prompt; `badge-appstore.png` is left in the folder, unreferenced, for whenever an iOS build exists.
  - Added the same hover-lighten treatment used on the founder/team cards (`hover:bg-[#0F3D6E]`) to the five "Any camera / Any lighting / Any strip brand / No expensive hardware / No maintenance" tags in the BTCardX™ section, per the founder's request to make that interaction consistent across the page.
  - **Added a favicon** (`favicon.svg`) — a simple "B" monogram using the site's own `ink` background and `teal` accent colours, linked from all 4 pages. No favicon existed before this.
  - Re-audited all three prior docx rounds against the live code (grepped for leftover `.AI` branding, `info@billiontests` addresses, and "Mumbai" in the address list) — confirmed zero leftovers; everything from Phases 5–7 was already correctly in place.

## Phase 11 — Mobile hamburger nav and responsive overflow fixes

Founder request: fix the navbar spacing/margins issue, then a full mobile-responsiveness pass. This closed out the "no mobile nav" gap that had been flagged as the top-priority open item since Phase 6.

- **`e8bb99e`** (2026-08-18):
  - Added a mobile hamburger menu to `index.html`, `news.html`, and `articles.html` — each gets a toggle button that switches a `<nav id="mobile-nav">` panel between hidden and visible, with the same links as the desktop nav on that page. (`contact.html` has no nav links to toggle, so no hamburger was added there.)
  - Fixed header spacing so the logo, "Book a demo" button, and new hamburger button don't collide at narrow widths.
  - Tightened the crisis-section stats table for mobile to stop it overflowing the viewport.
  - Fixed a `min-width: auto` flexbox bug on the Founders and Development Team cards: a long name (Priyanka Priyadarshini, in particular) could force its card wider than its grid track at tablet width (768px) because the text wrapper had no `min-w-0` to let it shrink and wrap. Applied `min-w-0` to both the card container and the text wrapper across all 8 affected cards.
  - Applied the same `min-w-0` fix to the footer's 6-column link grid, which had the identical bug.
  - Verified zero real horizontal-overflow elements across all 4 pages at both mobile (375px) and tablet (768px) widths, using the browser tool's device-emulation presets (a manual, non-preset resize to exactly 320px was found to desync the tool's own `window.innerWidth` from the real layout viewport mid-audit — a testing-tool artifact, not a site bug; re-confirmed clean with the proper presets).

---

## Still open as of this entry (not yet actioned — see `README.md` §5 for current detail)

- No real App Store / Google Play listing to link the footer's Google Play badge to (and no iOS build yet to justify restoring the App Store badge).
- No real Android app screenshots for the how-it-works cards.
- No event/attendance photography.
- Priyanka Priyadarshini's founder bio line is still blank — never supplied.
- No page-preview metadata (Open Graph / Twitter Card). A favicon now exists (Phase 10) but that's a separate thing from link-preview cards.
- No Privacy Policy or Terms of Service.
- Non-website materials (letterhead, brochure, pitch deck, visiting card) have never been edited as part of this work — only the 4 website HTML pages have.
- Where the live site is actually hosted today is not documented anywhere in this project and needs to be captured from whoever owns the `billiontests.ai`/`.com` domain.
