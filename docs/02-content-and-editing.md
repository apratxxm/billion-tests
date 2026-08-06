# Content and editing

There is no CMS. Every word, every number, every email address is hardcoded inside `index.html`. Changing any of it is a text edit to that one file, followed by a refresh — there is no rebuild step.

## Where things live

- **Stats that count up on scroll** (98%+, 20s, 10+, 30+, 1.4M+, 100K+, 200+, 70K+ etc.) are `<span data-count="98">` elements — change the number in `data-count`, the on-page starting `0` updates itself via the count-up script, no other edit needed. A few use `data-dec="1"` for one decimal place (only the "1.4M+" stat uses this).
- **Contact info** appears in three places that all need updating together if it changes: the "Demo + Partners" section (phone number, CBO title), the footer's Contact column (five email addresses + phone + domain), and the footer's byline ("VisionExcl Technologies Pvt. Ltd. · Lucknow").
- **The five footer email addresses** (`info@`, `sales@`, `collaboration@`, `partnership@`, `mpsethi@`) are all `billiontests.com`. There's no logic behind which one is suggested for what on the page — they're just listed. See `03-known-gaps.md` — this list was never finalized against Maninder's proposed individual-email scheme (`abhishek@`, `sahil@`, `pranav@`, `cbo@`).
- **Team grid** (in the Credibility section) is 12 individual `<div>` cells in one grid. Two cells (Maninder, Pramod) carry a photo + long bio; three more (Sahil, Pranav, Ritu) carry a photo + name only; seven are name-only text with no photo, title, or link. Adding a photo to any name-only cell means swapping that cell's markup to match the photo-cell pattern already used for the other five — copy one of those five as a template.
- **Nav links and footer "Platform"/"Trust" links** are anchor links (`#how`, `#card`, `#crisis`, `#why`, `#reveals`, `#credibility`, `#partners`, `#deploy`, `#top`) pointing at `id=` attributes on sections further down the same page. If a section's `id` is ever renamed, every link pointing at it breaks silently (no 404, the link just scrolls nowhere).

## Images

All images are referenced by plain relative filename (`maninder.png`, `bt-card.jpeg`, `step1-dip-real.jpeg`, etc.) sitting in the same folder as `index.html`. This means:
- The HTML file **cannot be shared on its own** — if you email or WhatsApp just `index.html` to someone, every photo breaks, because the images don't travel with it. Zip the whole folder, or host it somewhere, to share it with images intact.
- Adding a new photo = drop the file in the folder, reference its filename in an `<img src="...">` tag.

## The "single accent colour"

One Tailwind colour token, `teal` (currently `#1E69D2`), is used for every blue accent across the entire page — headline highlights, stat numbers, icons, borders, buttons. It's defined once, in the `tailwind.config` block near the top of the file. Changing that one hex value changes the accent colour everywhere at once. The one deliberate exception is the "TRL 9" badge in the BT Card section, which uses a separate `cyan` token so it reads as a distinct certification-style mark rather than blending into the rest of the page. Full detail in `04-design-language.md`.
