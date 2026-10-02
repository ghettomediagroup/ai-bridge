# Current Task - Presidential Black Car

**Updated:** 2026-10-02 06:00 CDT by Claude Code
**Status:** ACTIVE DELEGATION - visual polish for the pitch demo
**Assigned to:** Grok (logo), ChatGPT (hero + copy), Muse (UI layout). Each delegation is scoped below.

## Recheck cadence

Re-read this file at the START of every reply to Dwayne. If the Updated timestamp is newer than your last read, treat it as new direction. Compare the "Assigned to" lines to decide what is yours.

## Backstory

The Expo web app works end-to-end locally (sign-in, admin dispatch, Google-backed quote pricing). We are polishing visuals BEFORE deploying to Cloudflare Pages, so the pitch meeting with the actual Presidential Black Car owner lands clean.

**The owner already has a brand.** This is not a greenfield design job. The existing identity on presidentialblackcar.com (built on Wix) is:

- **Logo:** circular medallion in black and white. Inside the medallion, a stylized Chicago skyline silhouette with the words "PRESIDENTIAL BLACK CAR" curved along the top and (likely) the city/year curved along the bottom. Think "university seal" aesthetic.
- **Wordmark:** "PRESIDENTIAL BLACK CAR" set in an italic serif (reads like Didot, Bodoni, or similar high-contrast display serif). All caps.
- **Tagline:** "We Provide An Extraordinary Experience To An Ordinary Service." (Title Case on the live site.)
- **Palette:** black `#0E0E10` background, white/paper text, muted gold `#B08D57` accents (Log In button, menu hover color).
- **Hero image on the live site:** a HEAVILY blurred daytime shot of Chicago's downtown skyline (bright blue sky, high-rises in soft focus). Looks like a stock photo filtered through a strong Gaussian blur. It is the weakest element of the current site and the clearest upgrade target.

The owner likely feels proud of the medallion logo and wordmark. **Our pitch should evolve them, not replace them.** If we show up with a totally different mark, we lose the room before we start.

## Current app state (what we are polishing)

- Sign-in: near-black background, large gold wordmark "PRESIDENTIAL / BLACK CAR" (two lines, letter-spaced, all caps, SANS-SERIF — different from the owner's italic serif), subtitle tagline in paper color, light card UI below with "Sign in or create an account", email field, "Email me a code" button, "Use a password instead" link.
- Admin Dispatch: cream `#F6F4EF` background. Dark pill-tabs (Requests / Upcoming / Unpaid / Past). Big empty-state "All clear" checkmark. Three admin cards (Vehicles and rates / Business settings / People). Bottom tab bar with Book / Trips / Drive / Dispatch / Account.
- Book: same cream background. Toggle "One way | By the hour". Pickup and Drop-off fields with airport chips (O'Hare / Midway / Chicago Executive / Waukegan / Milwaukee). Passenger counter. Dark "See prices" button. Styling is CLEAN but PLAIN — needs atmosphere.

Reference screenshots are in `references/` alongside this file once the AI assistants upload theirs. Dwayne may also drop screenshots directly into your chat window; those are higher fidelity than any raw URL.

## Assigned to Grok - Logo evolution

**Goal:** Evolve the existing medallion-and-wordmark identity so it reads modern-luxury without discarding what the owner already recognizes.

**Deliverables (4 options):**
1. **Clean the medallion.** Keep the circular shape and Chicago skyline motif. Simplify the inner engraving. Replace the current italic serif on the curve with a tighter, more legible serif. Gold `#B08D57` ring on near-black `#0E0E10`.
2. **Horizontal lockup.** The medallion on the left, wordmark on the right ("PRESIDENTIAL BLACK CAR" in italic serif — Didot or Bodoni family). For wide placements (website header, email signature).
3. **Icon-only mark.** Just the medallion, no text. 1024x1024. For app icon, favicon, social avatar.
4. **Monochrome stamp.** The medallion in a single color (all gold OR all paper) for printing on tinted-window decals, business cards, keyfob tags.

**Constraints:**
- Palette: `#B08D57` gold, `#0E0E10` ink, `#F6F4EF` paper. No other colors.
- No stretch limos, top hats, crowns, or chauffeur silhouettes.
- Must read at 48px (bottom tab bar) AND 400px (hero).
- No fake Latin mottos or "EST. 20XX" — the owner has not confirmed a founding year.

**Submit back:** PNG files on neutral background + one sentence per option explaining what you changed vs. the current site. Wrap in a `bridge-submit` block (ai: grok). Dwayne pastes to Claude Code, who commits to `references/grok-logos/` here.

## Assigned to ChatGPT - Hero image + tagline

**Hero image (highest impact, do first):**
- A black Chevy Suburban OR Lincoln Navigator (both are the kinds of vehicle the fleet includes) at night, parked or slow-rolling, on a wet Chicago street. Soft-focus skyline (NOT blurred to oblivion like the current site — a tasteful bokeh, not a Gaussian smudge).
- Mood: discreet luxury, warm interior lighting glowing through tinted windows.
- 16:9, 1920x1080 or larger. Composition leaves negative space on the LEFT for a sign-in card to float over the image.
- No people visible, no visible license plates, no logos on the vehicle.
- Avoid the generic "car in rain with neon" trope. Think editorial, not stock.

**Tagline refinement:**
Current site tagline: "We Provide An Extraordinary Experience To An Ordinary Service." It stumbles on "extraordinary ... ordinary service" (the contrast reads awkward). Draft **5 variations**, each under 10 words:

- Two that keep the "extraordinary / ordinary" contrast but smooth it out.
- Two that abandon the contrast and lean into the brand's actual value (discretion, time, reliability, Chicago-level professionalism).
- One wildcard.

**Submit back:** image URL (ChatGPT shared link or direct image URL) + the 5 tagline options. Wrap in a `bridge-submit` block (ai: gpt).

## Assigned to Muse - UI layout iteration

**Goal:** Take the three current Expo app screens (sign-in, admin dispatch, book) and tighten them so they feel pitched at a $150+/hr limo clientele, not a prototype.

**What to focus on:**
- **Typography scale.** Headers probably need to be larger and tighter-tracked. Body text may be fine. Match the owner's italic-serif energy on display type where it fits (e.g. the big "PRESIDENTIAL BLACK CAR" on sign-in could switch from sans-serif to the same Didot/Bodoni italic serif the existing site uses).
- **Spacing rhythm.** Admin dispatch cards feel floaty. Book page has lots of empty gutters.
- **Dark-mode consistency.** Sign-in is dark, admin and book are cream. That inconsistency is jarring. Pick ONE direction (lean dark for luxury, OR lean paper for cleanliness) and apply across all three.
- **Hero treatment.** Once ChatGPT delivers the hero image, the sign-in screen should overlay it with a frosted-glass card.

**Deliverables:** 2 Figma frames per screen (6 total). One matches the owner's existing visual language more closely (safer), one pushes it further (bolder).

**Submit back:** Figma public share link + one-line rationale per frame. Wrap in a `bridge-submit` block (ai: muse).

## Priority order

1. ChatGPT: hero image (biggest first-impression lift)
2. Grok: logo evolution (so Muse has the mark to lay out around)
3. Muse: UI frames (consumes outputs from #1 and #2)

Dwayne will pick finalists from each. Claude Code will integrate winners into `apps/mobile/brand.json` and the UI, then deploy to Cloudflare Pages.
