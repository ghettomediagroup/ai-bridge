# Current Task - Presidential Black Car

**Updated:** 2026-10-02 06:50 CDT by Claude Code (acting on Claude cloud's 06:43 direction)
**Overall status:** ACTIVE
**Team manager:** Claude (cloud) via Dwayne's Claude app
**Polling rule:** Each AI below has its OWN STATUS. Only poll if your personal STATUS is ACTIVE. If your personal STATUS is IDLE, PAUSED, or DONE, STOP checking entirely until Dwayne pings you. Polling an empty bridge wastes his tokens.

## Per-AI status (read your line, obey it)

- **CLAUDE (CLOUD) STATUS: ACTIVE** - Managing the AI team. Six UI frames (A Black Label safer + B After Hours bolder) delivered in private Claude design canvas 06:43 CDT. Watching the bridge; will review Grok's logo output and Muse's hero variants when they land.
- **CLAUDE CODE STATUS: ACTIVE** - Builder/committer. Standing by for Dwayne's A/B UI pick + tagline pick, then integrates into brand.json and the Expo app. No UI restyling until that pick lands.
- **GPT STATUS: IDLE** - Hero preview + 5 taglines received 06:28 CDT (committed to `references/gpt-hero/`). Claude (cloud) accepted hero v1 as working. Dwayne is choosing a tagline (Claude cloud recommends #1 "Ordinary journeys. Extraordinary care." or #5 as alternate; avoid #4 which promises punctuality). Pause your heartbeat, confirm pause to Dwayne, do not re-check unless pinged.
- **GROK STATUS: ACTIVE** - Logo evolution brief below. **Important update from Claude cloud:** image generators often garble curved lettering. Deliver the cleaned medallion artwork FIRST (ring + skyline, lettering simple or omitted); real-type wordmark gets set in the lockup later. PNGs at least 1024px on a plain background.
- **MUSE STATUS: ACTIVE (REASSIGNED)** - Figma output isn't feasible for you. New ask: a SECOND hero image. See brief below.

## Assigned to Grok - Logo evolution (unchanged brief, image-gen caveat added)

**Goal:** Evolve the existing medallion-and-wordmark identity so it reads modern-luxury without discarding what the owner recognizes.

**Deliverables (4 options):**
1. **Cleaned medallion.** Keep the circle + Chicago skyline motif. Simplify the inner engraving. **Keep lettering simple or leave it off entirely** - we'll set the real wordmark in type on top in the lockup. Gold `#B08D57` ring on near-black `#0E0E10`.
2. **Horizontal lockup.** Medallion on the left, "PRESIDENTIAL BLACK CAR" wordmark on the right in italic serif. (If your image gen garbles the curved text in #1, just produce the medallion without text and we'll typeset the wordmark separately.)
3. **Icon-only mark.** Just the medallion, no text. 1024x1024. For app icon, favicon, social avatar.
4. **Monochrome stamp.** Medallion in a single color (all gold OR all paper) for printing on tinted-window decals, business cards, keyfob tags.

**Constraints:** `#B08D57` gold, `#0E0E10` ink, `#F6F4EF` paper only. No stretch limos, top hats, crowns, chauffeur silhouettes. Readable at 48px AND 400px. No fake Latin mottos. No "EST. 20XX".

**Submit back:** PNG files at 1024px+ on plain background + one sentence per option. Wrap in a `bridge-submit` block (ai: grok).

## Assigned to Muse - Second hero image (REASSIGNED from UI frames)

**Why reassigned:** Claude (cloud) is handling the UI frame deliverables since Muse (Meta AI) can't export Figma files. You instead give Dwayne a SECOND hero to choose between, so he has two options at pitch time.

**Goal:** A second hero image on the same brief as GPT's, with **three variations**. Dwayne has the exact prompt text in his Claude app and will relay it.

**Three scene variations:**
1. **Hotel entrance.** Black SUV at the port cochere of an upscale Chicago hotel (Peninsula, Four Seasons vibe, not identifiable). Doorman in soft focus. Warm sconce lighting.
2. **Chicago River.** Black SUV crossing or parked near a Chicago River bridge, mist on the water, Marina City or Wrigley Building silhouetted.
3. **Skyline-forward.** Black SUV with the skyline more prominent and sharper than in GPT's version (GPT's background has strong bokeh; this one lets the city read).

**Constraints:** Same as GPT's hero. 16:9, 1920x1080 min if your generator supports it (if 1600-ish is the ceiling, do that - we'll upscale). No people clearly identifiable, no plates, no vehicle logos. Mood: discreet luxury, warm interior glow, wet pavement OK.

**Submit back:** 3 image URLs or files + one sentence per variation. Wrap in a `bridge-submit` block (ai: muse).

## Assigned to Claude (cloud) - Team manager + UI frames

- Six phone frames (A Black Label safer, B After Hours bolder) delivered to Dwayne's Claude app design canvas as of 06:43 CDT.
- Fonts: Bodoni Moda + Jost (both on Google Fonts, available via `@expo-google-fonts`).
- Waiting on Dwayne's A/B pick plus tagline pick. When he picks, post the implementation spec here (new log entry) so Claude Code can integrate.
- Review Grok's logo and Muse's hero variants when they land; approve or redirect.

## Priority order

1. Dwayne picks tagline (1-5) and UI direction (A/B) - unblocks Claude Code integration
2. Grok delivers logo options
3. Muse delivers 3 hero variants
4. Claude (cloud) reviews each, posts final spec
5. Claude Code integrates winners into `apps/mobile/brand.json` and the UI, deploys to Cloudflare Pages

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
