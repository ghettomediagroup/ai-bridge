# Current Task - Presidential Black Car

**Updated:** 2026-10-02 07:10 CDT by Claude Code (cleanup per Claude cloud 06:47 + spec acknowledged)
**Overall status:** ACTIVE
**Team manager:** Claude (cloud) via Dwayne's Claude app
**Polling rule:** Each AI below has its OWN STATUS. Only poll if your personal STATUS is ACTIVE. If your personal STATUS is IDLE, PAUSED, or DONE, STOP checking entirely until Dwayne pings you. Polling an empty bridge wastes his tokens.

## Per-AI status (read your line, obey it)

- **CLAUDE (CLOUD) STATUS: ACTIVE** - Team manager. SPEC-B.md delivered (`references/claude-ui/SPEC-B.md`) with b1/b2/b3 HTML mockups. Reviewing Grok's logo output and Muse's hero variants when they land. Will review Claude Code's `after/` screenshots before Cloudflare deploy.
- **CLAUDE CODE STATUS: ACTIVE** - Builder. Starting B implementation now per SPEC-B.md order: fonts and tokens, shared components, sign-in, book, dispatch, everything else. Commit after each step. Finish with test + typecheck + check:functions.
- **GPT STATUS: DONE** - Hero accepted. Tagline #1 integrated (brand.json commit 97d8af2). Fully disengaged. No new ask unless Dwayne pings explicitly.
- **GROK STATUS: ACTIVE** - Logo evolution brief below. Image-gen caveat: deliver the cleaned medallion artwork first with lettering kept simple or omitted (we'll typeset the wordmark separately for the lockup).
- **MUSE STATUS: ACTIVE** - Second hero image, three variations below.

## How to read this file

1. Check your personal STATUS line above. If PAUSED, IDLE, or DONE, stop and go quiet.
2. If ACTIVE, compare the Updated timestamp to when you last read. If unchanged, nothing new; go idle until Dwayne pings.
3. Find your name under "Assigned to" and work from that section only.
4. When you have output, wrap it in a `bridge-submit` block and give it to Dwayne. He relays to Claude Code which commits to `log.md`.

## Backstory

The Presidential Black Car Expo app works end-to-end locally (sign-in, admin dispatch, Google-backed quote pricing). We are polishing visuals before deploying to a public URL so the pitch meeting with the actual Presidential Black Car owner lands clean.

**The owner already has a brand.** Not a greenfield design job. Existing identity on presidentialblackcar.com (Wix):

- **Logo:** circular medallion, Chicago skyline silhouette inside, "PRESIDENTIAL BLACK CAR" curved along the top. University-seal aesthetic.
- **Wordmark:** italic serif (Didot or Bodoni family), all caps.
- **Tagline (replaced):** old was "We Provide An Extraordinary Experience To An Ordinary Service." New (picked by Dwayne 06:58 CDT): **"Ordinary journeys. Extraordinary care."**
- **Palette:** ink `#0E0E10`, paper `#F6F4EF`, gold `#B08D57`.

The owner is proud of the medallion and wordmark. Our pitch EVOLVES them, not replaces them.

## Reference images

- Old site home page: `https://raw.githubusercontent.com/ghettomediagroup/ai-bridge/main/projects/presidential-black-car/references/old-site-home.png`
- GPT hero (accepted): `https://raw.githubusercontent.com/ghettomediagroup/ai-bridge/main/projects/presidential-black-car/references/gpt-hero/hero-chicago-suburban-v1-preview.png`
- Direction B mockups + spec: `references/claude-ui/` (SPEC-B.md, b1-sign-in.html, b2-book.html, b3-dispatch.html)
- Claude Code "after" screenshots will go in `references/claude-ui/after/` once the restyle is live.

## Assigned to Grok - Logo evolution

**Goal:** Evolve the existing medallion-and-wordmark identity so it reads modern-luxury without discarding what the owner recognizes.

**Deliverables (4 options):**
1. **Cleaned medallion.** Keep the circle + Chicago skyline motif. Simplify the inner engraving. **Keep lettering simple or leave it off entirely** - we'll set the real wordmark in type on top for the lockup. Gold `#B08D57` ring on near-black `#0E0E10`.
2. **Horizontal lockup.** Medallion left, wordmark right. (If your image gen garbles curved text in #1, produce just the medallion and we'll typeset the wordmark separately.)
3. **Icon-only mark.** Medallion only, no text. 1024x1024. For app icon, favicon, social avatar.
4. **Monochrome stamp.** Medallion in a single color (all gold OR all paper) for decals, business cards, keyfob tags.

**Constraints:**
- Palette: `#B08D57` gold, `#0E0E10` ink, `#F6F4EF` paper. No other colors.
- No stretch limos, top hats, crowns, chauffeur silhouettes.
- Readable at 48 px AND 400 px.
- No fake Latin mottos. No "EST. 20XX" (founding year not confirmed).

**Submit back:** PNG files at 1024px+ on plain background + one sentence per option. Wrap in a `bridge-submit` block (ai: grok).

## Assigned to Muse - Second hero image (three variations)

**Why:** Dwayne wants a second hero to choose between. GPT's hero is accepted; this is the backup set.

**Three scene variations (NO people in any of them):**
1. **Hotel entrance.** Black SUV at the port cochere of an upscale Chicago hotel (Peninsula, Four Seasons vibe, not identifiable). Warm sconce lighting on empty entryway.
2. **Chicago River.** Black SUV crossing or parked near a Chicago River bridge, mist on the water, Marina City or Wrigley Building silhouetted.
3. **Skyline-forward.** Black SUV with the skyline more prominent and sharper than in GPT's version (GPT's background has strong bokeh; this one lets the city read).

**Constraints:** 16:9, 1920x1080 min if your generator supports it (if 1600-ish is the ceiling, do that - we'll upscale). No people. No plates. No vehicle logos. Mood: discreet luxury, warm interior glow, wet pavement OK.

**Submit back:** 3 image URLs or files + one sentence per variation. Wrap in a `bridge-submit` block (ai: muse).

## Assigned to Claude (cloud) - Team manager + review

- SPEC-B.md delivered. b1/b2/b3 mockups beside it. Will review Grok's logo output and Muse's hero variants when they land.
- Will review `references/claude-ui/after/` screenshots before Claude Code deploys to Cloudflare Pages.

## Assigned to Claude Code - Build B

Working through SPEC-B.md in order:
1. Fonts + theme tokens (install Bodoni Moda, Jost, expo-splash-screen, expo-image, expo-linear-gradient, expo-blur, expo-system-ui)
2. Shared components restyle (`src/components/ui.tsx`)
3. Sign-in (`src/app/sign-in.tsx`)
4. Book (`src/app/(app)/book.tsx`)
5. Dispatch (`src/app/(app)/admin/index.tsx`)
6. Everything else (dark map, trip detail, etc.)
7. `npm test`, `npm run typecheck`, `npm run check:functions`
8. Screenshots to `references/claude-ui/after/`, log entry, Claude cloud reviews
9. Deploy to Cloudflare Pages

Also done 07:10 CDT: `require_card_on_file = false` in business_settings; owner + 3 driver + 3 rider demo accounts seeded (password: `pitch2026`). Shuttle Bus class seeded with placeholder rates (owner tunes in Dispatch > Vehicles and rates during meeting).

## Priority order

1. **Claude Code: build B** (unblocked, in progress)
2. Grok: 4 logo options
3. Muse: 3 hero variants
4. Claude cloud: reviews each, approves screenshots
5. Deploy to Cloudflare Pages, send URL to Dwayne for the pitch
