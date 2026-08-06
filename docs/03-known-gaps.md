# Known gaps — what's broken, missing, or still undecided

Checked directly against the live `index.html`. For prioritizing what to fix before this goes out further than internal review.

## Functional bugs

- **Both "download the app" QR codes are fake.** The floating widget (bottom-right on every page load) and the footer's "Scan to download" block are both a plain CSS checkerboard pattern (`repeating-conic-gradient`), not a real encoded QR code. Scanning either with a phone does nothing. There is no app store link anywhere on the page to generate a real one from yet.
- **No mobile navigation.** The nav's link list (`How it works`, `BT Card™`, `The crisis`, etc.) is set to `hidden` below the `lg` breakpoint (1024px) with no hamburger menu or any alternative. On a phone or tablet — which is the primary device this whole product is designed around — a visitor sees only the logo and the "Book a demo" button. There is currently no way to jump to a section from a small screen except scrolling manually.
- **Social icons go nowhere.** LinkedIn, Facebook, Instagram, and X icons in the footer are all `href="#"`. No real profile URLs have been provided yet.
- **No page preview when shared.** There's no `<meta name="description">`, no Open Graph tags, no Twitter Card tags, and no favicon. Since this link is being shared over WhatsApp, pasting it into a chat currently shows no title, no image, and no blurb — just a bare URL.
- **"Book a demo" doesn't book anything.** Both buttons in the demo section (`Book a demo →` and the phone number itself) just trigger a `tel:` dial to the same number. There's no calendar link, no form. Two buttons doing the identical action is also mildly redundant.
- **No legal links.** No Privacy Policy or Terms of Service anywhere in the footer, despite the product handling personal health data and the page actively courting hospitals/foundations/CSR partners who will look for this.

## Missing content

- **7 of 12 team members have name only** — no photo, no title/role, no contact link: Abhishek, Alok, Mohini Behera, Amitabha Bandyopadhyay, Ravi Vedururu, Sandeep, Neeraj Garg. (Sandeep does at least show "IIT Bombay" underneath.) The other 5 (Maninder, Pramod, Sahil, Pranav, Ritu) have at least a photo; only Maninder and Pramod have a bio line. Titles/roles (Co-founder, Advisor, etc.) that existed on these people in earlier drafts were dropped when the grid was simplified — right now there's no way to tell from the page who's a founder, an advisor, or a team member.
- **A real demo video exists and isn't used.** `how-to-use-demo.mp4` (~1.3MB) was recovered from the pitch deck and is sitting in the project folder, unreferenced anywhere in `index.html`. The "See how it works" button just scrolls to the static three-card section.
- **Two more unused assets**: `three-step-composite.jpeg` (a single polished graphic covering all three how-it-works steps) and `karan-bahuguna.jpeg` (a photo for a "Product Leader" who isn't in the team grid at all).
- **Partner logos** — the partner section deliberately shows category icons instead of real logos, since there are no signed partners yet. That's intentional, not a bug, but worth remembering to swap in real logos the moment there's a first partner to show.

## Open decisions, not yet resolved

- **Which email address is "the" contact address is unclear.** The footer lists all five (`info@`, `sales@`, `collaboration@`, `partnership@`, `mpsethi@billiontests.com`) with no guidance on which to use for what. A separate, individual-name email scheme (`abhishek@`, `sahil@`, `pranav@`, `cbo@` for collaboration+partnerships) was proposed at one point but never reconciled with what's actually live — right now the site reflects the older role-based scheme only.
- **No real app store link exists yet** for either iOS or Android, which blocks fixing the fake-QR issue above.
