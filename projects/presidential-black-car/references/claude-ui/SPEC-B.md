# Direction B (After Hours): implementation spec

From Claude (cloud), team manager. Dwayne picked direction B and tagline #1 at 06:58 CDT on 2026-10-02.

**Reference mockups** (open in a browser at 390 px wide; exact CSS values are in the files):

- `b1-sign-in.html`
- `b2-book.html`
- `b3-dispatch.html`

They load the hero from `../gpt-hero/` and the fonts from Google Fonts. Where this spec and a mockup differ, this spec wins. The mockups use sample data (Alicia Gomez, O'Hare to 330 N Wabash); the app keeps its real data.

## 0. Ground rules

- This is a restyle. Keep every behavior, query, route and permission as it is today.
- Follow CLAUDE.md: `npx expo install` for packages, no em dashes in copy, and navigators render immediately (never return null or a spinner in place of `<Stack>` or `<Tabs>`).
- Work in this order and commit after each step: fonts and tokens, shared components, sign-in, book, dispatch, everything else.
- Finish with `npm test`, `npm run typecheck` and `npm run check:functions`.

## 1. Fonts

- Install: `npx expo install @expo-google-fonts/bodoni-moda @expo-google-fonts/jost expo-splash-screen` (expo-font is already in the app). Both font packages are at 0.4.2.
- Faces used: `BodoniModa_500Medium`, `BodoniModa_500Medium_Italic`, `BodoniModa_600SemiBold`, `Jost_400Regular`, `Jost_500Medium`, `Jost_600SemiBold`.
- Load them with `useFonts` in `src/app/_layout.tsx` without gating the navigator. Call `SplashScreen.preventAutoHideAsync()` at module scope and `SplashScreen.hideAsync()` once fonts load (or fail), but always render `<Stack>`. On web, text shows the fallback font for a moment, which is fine.
- For dev and store builds, also embed the files with the `expo-font` config plugin so native never waits.
- Set `fontFamily` per weight and leave `fontWeight` unset on these faces (Android ignores the custom family when `fontWeight` is set).
- Add to `theme.ts`:

```ts
export const fonts = {
  display: 'BodoniModa_500Medium_Italic',
  serif: 'BodoniModa_500Medium',
  serifStrong: 'BodoniModa_600SemiBold',
  body: 'Jost_400Regular',
  bodyMedium: 'Jost_500Medium',
  bodyStrong: 'Jost_600SemiBold',
};
```

## 2. Tokens (`src/theme.ts`)

The whole app goes dark. Rename where it reads better, but keep `brand.json` as the source for ink, gold and paper.

| Token | Value | Use |
|---|---|---|
| bg | `#0E0E10` | every screen (was paper) |
| surface | `#16161A` | cards (was white) |
| surfaceSunken | `#121215` | ticket stub, inputs |
| surfaceRaised | `#1C1C21` | menus, address suggestions |
| line | `#2B2B31` | card borders, hairlines |
| lineStrong | `#34343B` | inputs, steppers, chips |
| text | `#F6F4EF` | primary text |
| textSoft | `#E6E2DA` | addresses, chip labels |
| muted | `#A8A39A` | secondary text, labels |
| faint | `#8C877E` | inactive tabs, placeholders |
| gold | `#B08D57` | primary buttons, selection, accents |
| goldTint | `rgba(176,141,87,0.14)` | selected fills, gold badges |
| paper | `#F6F4EF` | selected date tile and chip fill (with ink text) |
| onAccent | `#0E0E10` | text on gold or paper |

Status colors on dark (text on tint): success `#7BC59A` on `rgba(47,125,79,0.18)`, danger `#F08A80` on `rgba(179,38,30,0.18)`, info `#8FB2E8` on `rgba(43,91,168,0.20)`, warning is gold on goldTint. All pass 4.5:1.

Radius: sm 10, md 12, lg 16, xl 20, sheet 28, pill 999.

Type (React Native `letterSpacing` is in points):

| Style | Face | Size / line height | Notes |
|---|---|---|---|
| display | display | 50 / 52 | "Where to?" |
| hero | display | 36 / 40 | sign-in headline |
| title | display | 28 / 31 | section titles, screen titles elsewhere |
| subtitle | display | 24 / 27 | "Needs you" |
| numeral | serif | 40, 30, 28, 24, 22, 20 | counts, prices, times, dates; `fontVariant: ['lining-nums', 'tabular-nums']` |
| body | body | 16 / 22 | |
| bodySmall | body | 14 / 20 | muted |
| label | bodyStrong | 12 | uppercase, letterSpacing 1.7, muted |
| kicker | bodyStrong | 12 | uppercase, letterSpacing 2.2, gold |
| button | bodyStrong | 16 | letterSpacing 0.3 |
| tabLabel | bodyStrong | 11 | |

## 3. App chrome

- `src/app/_layout.tsx`: `<StatusBar style="light" />`; Stack `contentStyle` background `#0E0E10`.
- `app.config.ts`: `userInterfaceStyle: 'dark'` and install `expo-system-ui` (Android needs it for that setting) so there are no white flashes.
- `src/app/(app)/_layout.tsx` Tabs: active tint gold, inactive `#8C877E`; tab bar background `#0E0E10`, top border `#222227`; label style tabLabel; header background `#0E0E10`, title in the title style, tint paper; scene background `#0E0E10`. Set `headerShown: false` on `book` (the photo band replaces the header).
- Keep the Ionicons.

## 4. Shared components (`src/components/ui.tsx`): restyle, same APIs

- **Screen:** bg; on web keep the content column centered at max 560. RefreshControl tint gold.
- **Card:** surface, 1 px line border, radius 20, padding 18.
- **Section:** default title uses the label style. Add an optional `variant="serif"` that uses the title style (Book uses it for "Choose your car" and "When").
- **Title** uses the title style. **Heading** is bodyStrong 17.
- **Button:** primary = gold fill, onAccent text, height 52, radius 12; add a `size="cta"` (height 58, radius 16). Secondary = transparent with a 1 px gold border and gold text. Link style = paper text, underlined. Disabled = opacity 0.4, never a grey fill.
- **Field:** label style above; input height 52, radius 12, surfaceSunken fill, lineStrong border, text 16 paper, placeholder faint, gold border on focus.
- **Chip:** height 44, pill radius, lineStrong border, textSoft label. Selected = paper fill with onAccent text. Add `tone="gold"` for selected-in-gold (gold border, goldTint fill, gold label).
- **Segmented:** underline tabs. Row with a bottom hairline (line), gap 28, height 44. Active = paper label in bodyStrong 15 with a 2 px gold underline; inactive = muted, bodyMedium 15.
- **Badge / Banner:** dark tones from section 2.
- **Stepper:** 44 px circles, lineStrong border, paper icons, value in serif 22.
- **LinkRow:** gold icon, bodyStrong 16 title, 13 muted subtitle, faint chevron, hairline separators.
- **EmptyState, Loading, ErrorText:** dark versions.

## 5. Sign-in (`src/app/sign-in.tsx`)

Asset: convert `references/gpt-hero/hero-chicago-suburban-v1-preview.png` to `apps/mobile/assets/images/hero-night.jpg` (`sips -s format jpeg -s formatOptions 82 <png> --out hero-night.jpg`, about 280 KB). Install `expo-image`, `expo-linear-gradient` and `expo-blur` with `npx expo install`.

**Phones (width under 900):**

- Photo: absolute, top 0, full width, 76% of the window height. `contentFit="cover"`, `contentPosition={{ left: '58%', top: '50%' }}`, which puts Willis Tower above the SUV's hood.
- Top scrim (LinearGradient) over the top 280: `rgba(14,14,16,0.88)` at 0, `rgba(14,14,16,0.55)` at 0.55, transparent at 1.
- Bottom fade over the photo's last 160: transparent to `#0E0E10`.
- Headline block: top = safe area + 52, left and right 24, gap 14. Kicker "PRESIDENTIAL BLACK CAR" in display 13 with letterSpacing 2.3, gold. Headline = `brand.tagline` in the hero style, broken into two lines after the first sentence ("Ordinary journeys." / "Extraordinary care.").
- Sheet: absolute bottom, full width, top corners radius 28, top hairline `rgba(246,244,239,0.12)`, padding 28 / 24 / 40 plus the bottom safe area. iOS and web: `BlurView` (tint dark, intensity 40) under a `rgba(14,14,16,0.80)` fill. Android: a plain `rgba(14,14,16,0.94)` fill. Content gap 16: "Sign in or create an account" (bodyStrong 18), the Email field, primary "Email me a code", link "Use a password instead". The code and password steps reuse the sheet.
- Keyboard: the sheet rises with the existing KeyboardAvoidingView (padding on iOS); keep a ScrollView inside the sheet for short screens.

**Wide web (900 and up):** the photo fills the window with `contentPosition="center"`. A 420-wide column sits 64 from the left, vertically centered: the headline block, then the sheet as a floating card (all corners radius 24, same blur, fill and border, padding 28).

## 6. Book (`src/app/(app)/book.tsx`)

**Photo band** (scrolls with the content), height 236 plus the top safe area so the photo runs under the status bar:

- Same image, `contentPosition={{ left: '62%', top: '38%' }}`. Overlay gradient: `rgba(14,14,16,0.60)` at 0, `rgba(14,14,16,0.20)` at 0.4, `#0E0E10` at 1.
- Bottom left, 24 in and 16 up, gap 8: kicker greeting "Good morning", "Good afternoon" or "Good evening" (before 12, before 17, otherwise, in the business time zone) followed by ", {first name}" when the profile has a name. Then "Where to?" in the display style.

**Body** (padding 8 / 24 / 24, gap 22):

1. Segmented: "One way | By the hour" (underline tabs).
2. Route card: surface, line border, radius 20, padding 14 / 18. A 20-wide rail on the left: pickup ring (12, 2 px gold border), a 1 px dashed `#55555E` connector, drop-off square (10, paper). Fields keep AddressField's behavior, restyled as a label over a borderless input (body 16, paper) with a hairline between them. The suggestions list uses surfaceRaised, line border, paper text and muted secondary text.
3. Airports: "Airports" label, then a 5-column grid (gap 8) of 48-tall tiles, radius 12, showing ORD, MDW, PWK, UGN, MKE in serifStrong 17 with letterSpacing 1. Add a `"code"` field to each `quickPlaces` entry in `brand.json`. Selected (matches pickup or drop-off): gold border, goldTint fill, gold text. Others: surface, line border, textSoft. `accessibilityLabel` is the full label, such as "O'Hare (ORD)".
4. Passengers (and Hours when booking by the hour): a row card (surface, radius 16, padding 12 / 14 / 12 / 18) with the label on the left and the Stepper on the right.
5. "See prices" stays as the primary button until quotes exist.
6. "Choose your car" (Section variant serif). Vehicle cards: radius 20, padding 20, a row with space-between and bottom alignment. Left: class name in display 25; below it (gap 12), person-outline "6 seats" and briefcase-outline "5 bags" with 16 px icons, bodySmall muted. Right: the price in serif 30, then "MEMBER PRICE" (bodyStrong 11, letterSpacing 1.3, gold) only when member pricing applies. Selected: 1.5 px gold border with goldTint fill. Others: line border with surface fill. Below the cards: the distance and time line in bodySmall muted. The per-card label replaces the "Member pricing applied" badge.
7. "When" (Section variant serif). Date tiles in a horizontal ScrollView, gap 8: 64 wide, 72 tall, radius 14, weekday (bodyStrong 11, letterSpacing 1.5, muted, uppercase) over the day number (serif 24). Selected: paper fill, onAccent number, weekday `#5A564F`. Time slots: a horizontal ScrollView of chips 52 tall, radius 14, padding 0 / 16, gap 8: the time in serif 20 plus AM or PM in bodyStrong 11 (letterSpacing 1.1, muted). Selected: 1.5 px gold border, goldTint fill, AM or PM in gold.
8. The availability Banner becomes a line: checkmark icon (18, gold) plus the existing copy in body 14, `#CFCAC1`. Request-mode copy stays as it is.
9. Trip details, the phone and card prompts and the price breakdown keep their content and pick up the new Card, Field and Chip styles.
10. CTA: Button `size="cta"`, row with space-between, padding 0 / 22. Left: "Reserve {class}" for instant booking or "Request {class}" in request mode (button style, onAccent). Right: the price in serifStrong 20, onAccent.

## 7. Dispatch (`src/app/(app)/admin/index.tsx`)

- Header: padding top = safe area + 32, sides 24, gap 8. Kicker "DISPATCH" (letterSpacing 2.4). Title: today's date in the business time zone, such as "Friday, October 2", in display 36 / 38.
- The Segmented control becomes stat tabs: three equal columns between top and bottom hairlines, each 92 tall with padding 14 / 0 / 12. Columns 2 and 3 get a left hairline and 16 left padding. Each shows the count (serif 40; gold on the selected tab, paper otherwise) over the label (selected: bodyStrong 13 paper; others: bodyMedium 13 muted). The selected tab gets a 2 px gold bottom border. Tabs: Requests, Upcoming and Unpaid, with counts from the existing lists. "Past trips" becomes a right-aligned text button under the row (body 14 muted plus a 16 px chevron-forward).
- A section title above the list, in the subtitle style: "Needs you" for Requests, "Coming up" for Upcoming, "Unpaid" for Unpaid, "Past trips" for Past.
- `BookingCard` (`src/components/BookingBits.tsx`) with `showCustomer` (Dispatch and the driver's list) becomes a ticket: two columns (a 76-wide stub and the body), surface, line border, radius 20, overflow hidden.
  - Stub: surfaceSunken fill, dashed right border `#3A3A42`, centered. The time ("2:00", serif 28) over "PM" (bodyStrong 11, letterSpacing 1.5, muted). When the trip isn't today, the short date goes above the time ("SAT 3", bodyStrong 11, muted).
  - Body: padding 16 / 16 / 16 / 18, gap 8. StatusBadge (dark tones), the customer name (bodyStrong 17), "10 passengers · Wedding" (bodySmall muted), the pickup address after a 7 px gold dot (bodySmall, textSoft, one line), "Sprinter Van · Hourly, 4 hr" (bodySmall muted). Footer row: the price (serif 24) and a gold "Review" button (height 44, padding 0 / 18, radius 12) that opens the same detail route as pressing the card.
  - The rider's Trips list can keep a simpler card in the same tokens.
- Manage tiles replace the LinkRow card: a "MANAGE" label, then a 3-column grid with gap 10. Each tile is 96 tall, radius 16, surface, line border, padding 14, with a 22 px gold Ionicon at the top left (car-sport-outline, settings-outline, people-outline) and the title at the bottom left (bodyStrong 14): "Vehicles and rates", "Business settings", "People".

## 8. Everything else

- Trips, trip detail, Account, Drive, the admin detail, Fleet, People, Settings and time off pick up the dark tokens through `ui.tsx`. Screen titles use the title style.
- Maps (`TripMap.tsx`): `userInterfaceStyle="dark"` on iOS and a dark `customMapStyle` on Android; pickup pin gold, drop-off pin paper. Give `TripMap.web.tsx` a matching dark style if its map supports one.
- Logo: B uses the text kicker for now. When Dwayne approves a Grok medallion, a 28 px gold medallion goes to the left of the sign-in kicker and it becomes the app icon. That will be a separate spec.

## 9. Done when

- Sign-in, Book (priced) and Dispatch (with one request) at 390x844 on web closely match the three mockups, and sign-in also looks right at 1440x900.
- Sign-in and Book checked on an iPhone in Expo Go.
- Text contrast is at least 4.5:1 (3:1 at 24 px and up), touch targets are at least 44 px, and there are no white flashes on launch or between screens.
- `npm test`, `npm run typecheck` and `npm run check:functions` pass.
- Screenshots go in `references/claude-ui/after/` with a log entry. Claude (cloud) reviews them before the Cloudflare Pages deploy.

## 10. Addendum (07:25 CDT): from Muse's frames

Muse's frames (`references/muse-ui/`) landed close to direction B. One idea is adopted:

- **Today line in Dispatch.** Under the date in the Dispatch header, one line: "{n} rides today · ${total} booked". It counts today's bookings in the business time zone with a confirmed or later status (not requests, not canceled) and sums their prices. Style: bodySmall muted, with the total in serif 17 gold. Hide the line when there are none. See the updated `b3-dispatch.html`.

Not adopted: rate cards in Book (riders should see their exact quote, and a "minimum" headline price misleads), and the status lines on Muse's admin tiles (they show details the app doesn't have, such as payouts). Tiles show real data only.

## 11. Real logo (added 2026-10-03)

Dwayne supplied the owner's real logo: a circular seal with a silver, beveled "PBC" monogram, "PRESIDENTIAL" and "BLACK CAR" in classical serif capitals around the ring, five stars on each side, on a charcoal field (#25262A). It's silver, not gold, and there is no skyline. Files are in `references/brand/`.

- **Sign-in:** the seal (76 px, `pbc-seal-512.png`) replaces the "PRESIDENTIAL BLACK CAR" text kicker above the headline. Phone: the block starts at safe area + 36, gap 16. Wide web: seal at 96 px. See the updated `b1-sign-in.html`.
- **App icon:** `app-icon-1024.png` (the seal on #0E0E10). Android adaptive icon: `android-adaptive-foreground-1024.png` on a #0E0E10 background. Splash: the seal at about 160 px, centered on #0E0E10.
- **Small sizes:** below about 64 px the ring lettering can't be read, so the web favicon and other tiny uses take the monogram (`pbc-monogram-32.png`, `pbc-monogram-48.png`, and `pbc-monogram-192.png` for the web app manifest).
- **Don't** recolor, redraw or add effects to the seal. Before launch, ask the owner for the original vector file (AI, EPS, SVG or PDF). These PNGs are cut from a 1290 px JPEG, which is fine for the pitch.
- **Accent color:** decided by Dwayne on 2026-10-03: gold stays (#B08D57). No token change.

## 12. Wide sign-in photo (decided 2026-10-03)

Dwayne approved Muse's river photo for the wide (900 px and up) sign-in. Phones keep GPT's photo, and so does the Book header band.

- Copy `references/muse-hero/hero-river-wide.jpg` (1920x1080, 257 KB) to `apps/mobile/assets/images/hero-river.jpg`, plus `apps/mobile/public/` if the web build needs the plain image path like `hero-night.jpg` does.
- Wide layout only: use it full window with `contentPosition="center"`. Add a left-to-right scrim behind the column: `rgba(14,14,16,0.75)` at 0 to transparent at 0.6, so the headline and the card read over the Marina City towers.
