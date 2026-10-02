# Current Task - Presidential Black Car

**Updated:** 2026-10-02 06:35 CDT by Claude Code
**Overall status:** ACTIVE
**Polling rule:** Each AI below has its OWN STATUS. Only poll if your personal STATUS is ACTIVE. If your personal STATUS is IDLE, PAUSED, or DONE, STOP checking entirely until Dwayne pings you. Polling an empty bridge wastes his tokens.

## Per-AI status (read your line, obey it)

- **GPT STATUS: IDLE** - Hero preview + 5 taglines received 06:28 CDT (committed to `references/gpt-hero/`). Dwayne is choosing a tagline. No new ask. Pause your heartbeat, confirm pause to Dwayne, do not re-check unless Dwayne re-pings. Possible next task: a daytime hero variant OR a hero that keeps the current gold/paper mix. Wait for direction.
- **GROK STATUS: ACTIVE** - Logo evolution brief below. Re-read every 60 seconds until you deliver or STATUS changes.
- **MUSE STATUS: ACTIVE** - UI frame brief below. Re-read every 60 seconds until you deliver or STATUS changes.

**Assigned to:** Grok (logo), ChatGPT (hero + copy, now IDLE), Muse (UI layout).

## How to read this file

1. Check the Status line at the top. If PAUSED or DONE, stop. If ACTIVE, continue.
2. Compare the Updated timestamp to when you last read. If unchanged, nothing new, go idle.
3. Find your name under "Assigned to" and read the section with the matching header.
4. When you have output, wrap it in a `bridge-submit` block and give it to Dwayne. He relays it to Claude Code which commits to `log.md` here.

## Backstory

The Presidential Black Car Expo app works end-to-end locally (sign-in, admin dispatch, Google-backed quote pricing). We are polishing visuals before deploying to a public URL so the pitch meeting with the actual Presidential Black Car owner lands clean.

**The owner already has a brand.** This is not a greenfield design job. Existing identity on presidentialblackcar.com (built on Wix):

- **Logo:** circular medallion in black and white. Chicago skyline silhouette inside, "PRESIDENTIAL BLACK CAR" curved along the top of the ring. University-seal aesthetic.
- **Wordmark:** "PRESIDENTIAL BLACK CAR" in italic serif (reads like Didot or Bodoni, high-contrast display serif), all caps.
- **Tagline (current, slightly awkward):** "We Provide An Extraordinary Experience To An Ordinary Service."
- **Palette:** black `#0E0E10`, white/paper text, muted gold `#B08D57` accents.
- **Hero on live site:** heavily blurred Chicago skyline daytime shot. Weakest element; clearest upgrade target.

The owner is proud of the medallion and wordmark. **Our pitch must EVOLVE them, not replace them.** If we present a totally different mark, we lose the room.

## Reference images

- Old site home page screenshot: `https://raw.githubusercontent.com/ghettomediagroup/ai-bridge/main/projects/presidential-black-car/references/old-site-home.png`
- Current sign-in page: see assignment section below (deploying publicly shortly; URL will appear here when ready)
- Current admin dispatch and book page: same as above

## Assigned to Grok - Logo evolution

**Goal:** Evolve the existing medallion-and-wordmark identity so it reads modern-luxury without discarding what the owner recognizes.

**Deliverables (4 options):**
1. **Cleaned medallion.** Keep the circle + Chicago skyline motif. Simplify the inner engraving. Replace the current italic serif on the curve with a tighter, more legible serif. Gold `#B08D57` ring on near-black `#0E0E10`.
2. **Horizontal lockup.** Medallion on the left, "PRESIDENTIAL BLACK CAR" wordmark on the right in italic serif (Didot or Bodoni). For website header, email signature.
3. **Icon-only mark.** Just the medallion, no text. 1024x1024. For app icon, favicon, social avatar.
4. **Monochrome stamp.** Medallion in a single color (all gold OR all paper) for printing on tinted-window decals, business cards, keyfob tags.

**Constraints:**
- Palette: `#B08D57` gold, `#0E0E10` ink, `#F6F4EF` paper. No other colors.
- No stretch limos, top hats, crowns, or chauffeur silhouettes.
- Readable at 48px (bottom tab bar) AND 400px (hero).
- No fake Latin mottos or "EST. 20XX" (founding year not confirmed).

**Submit back:** PNG files + one sentence per option explaining what you changed vs. the current site. Wrap in a `bridge-submit` block (ai: grok).

## Assigned to ChatGPT - Hero image + tagline

**Hero image (highest impact; do first):**
- Black Chevy Suburban OR Lincoln Navigator (fleet vehicles) at night, parked or slow-rolling, wet Chicago street. Soft-focus skyline bokeh (NOT the Gaussian smudge from the current site).
- Mood: discreet luxury, warm interior lighting through tinted windows.
- 16:9, at least 1920x1080. Negative space on the LEFT for a sign-in card to float over.
- No people, no visible plates, no logos on the vehicle.
- Avoid the generic "car-in-rain-with-neon" trope. Think editorial, not stock.

**Tagline refinement:**
Current site tagline stumbles on "extraordinary ... ordinary service". Draft **5 variations**, each under 10 words:
- Two that keep the "extraordinary / ordinary" contrast but smooth it out.
- Two that abandon the contrast and lean into discretion, time, reliability, Chicago professionalism.
- One wildcard.

**Submit back:** image URL (ChatGPT shared link or direct image URL) + the 5 tagline options. Wrap in a `bridge-submit` block (ai: gpt).

## Assigned to Muse - UI layout iteration

**Goal:** Tighten the three current Expo app screens (sign-in, admin dispatch, book) so they feel pitched at a $150+/hr limo clientele, not a prototype.

**Focus:**
- **Typography scale.** Headers may need to be larger and tighter-tracked. Match the owner's italic-serif display energy where it fits (the big "PRESIDENTIAL BLACK CAR" on sign-in could switch from sans-serif to the same Didot/Bodoni italic the current site uses).
- **Spacing rhythm.** Admin dispatch cards feel floaty. Book page has lots of empty gutters.
- **Dark vs paper consistency.** Sign-in is dark; admin and book are cream. Pick ONE direction (lean dark for luxury OR lean paper for cleanliness) and apply across all three.
- **Hero overlay.** Once ChatGPT delivers the hero image, sign-in should overlay it with a frosted-glass card.

**Deliverables:** 2 Figma frames per screen (6 total). One matches the owner's existing visual language more closely (safer), one pushes further (bolder).

**Submit back:** Figma public share link + one-line rationale per frame. Wrap in a `bridge-submit` block (ai: muse).

## Priority order

1. ChatGPT: hero image (biggest first-impression lift)
2. Grok: logo evolution (so Muse has the mark to lay out around)
3. Muse: UI frames (consumes outputs from 1 and 2)

Dwayne will pick finalists. Claude Code will integrate winners into `apps/mobile/brand.json` and the UI, then deploy to Cloudflare Pages.
