# Run and ship

## Previewing it locally

There's no build step. Any static file server pointed at the project folder works — the repo's `.claude/launch.json` already has one configured (`npx serve -l 5500 .`), served at `http://localhost:5500/index.html`.

You cannot just double-click `index.html` and get a fully correct preview in every browser — some browsers restrict relative image loading from a bare `file://` path. Always preview through an actual local server, not by opening the file directly, to see it exactly as a visitor would.

## What shipping this actually requires

This is a single static HTML file with a folder of images sitting next to it — there is no framework, no `npm run build`, nothing to compile. "Deploying" it is copying `index.html` plus every image/video file it references to wherever `billiontests.com` is hosted (or a new static host — Netlify, Vercel, GitHub Pages, or a plain web server all work with zero changes to the code).

**Nothing in this project folder shows where or how the site is actually hosted today** — no hosting config, no CI/CD file, no deploy script. Confirm with whoever owns `billiontests.com` infrastructure before assuming this is already live there, or how to push an update once it is.

## Before it goes fully public

Cross-check against `03-known-gaps.md` — at minimum, the fake QR codes and the missing mobile navigation are the two gaps most likely to actively cost visitors (a broken "download the app" promise, and zero navigation for anyone on a phone, which is most of the intended audience). Everything else in that doc is a completeness/polish gap, not a broken-experience gap.

## Sharing the file itself (not the live link)

If you ever need to hand someone the raw file instead of a live URL — email, WhatsApp, a USB drive — zip the whole folder, not just `index.html`. Every photo is referenced by relative filename; the HTML file alone renders with every image broken.
