# Presidential Black Car - Context

**Client:** Presidential Black Car (Chicago black car service, presidentialblackcar.com)
**Status:** GMG pitch pilot in progress. Not yet a signed client.
**Owner / orchestrator:** Dwayne Crump (Ghetto Media Group / GMG)
**Code:** `~/Developer/presidential-black-car/` on Dwayne's Mac. Not pushed to a remote yet.

## What's being built

An inherited starter codebase (Expo for iOS/Android/web + Supabase Postgres/Auth/Edge Functions + Stripe + Google Maps) that will become Presidential Black Car's booking app. Dwayne is preparing a **pitch pilot** (web-only demo on GMG infrastructure) to show the actual owner this week. If owner signs, the full M1-M6 engagement fires at **$7,000 total**.

## Pitch pilot deliverable

A working web demo at a public URL that the owner can click through:
- Rider signs in with an email magic code
- Books a ride, sees prices for Premium SUV ($25 base + $4.25/mi + $0.65/min, $85 min) and Sprinter Van ($75 base + $6.50/mi + $1.00/min, $175 min)
- Dispatch (owner) sees the request and confirms with a vehicle + driver
- Rider sees "Confirmed"

Not needed for pitch: real Stripe payments, iOS/Android builds, push notifications. Those come in paid milestones.

## Stack

- Expo SDK 57, React Native 0.86, Expo Router, TypeScript 6
- Supabase (cloud project `pbc-pitch` at `xmqclhfzvsmraefglgkb.supabase.co`, us-east-1, Postgres 17)
- Stripe (not needed for pitch)
- Google Maps (Places API + Routes API, not yet enabled)
- Cloudflare Pages (planned demo host, under GMG CF account)

## What's done

- Local verification: 149/149 tests passing (79 core + 50 DB + 20 Deno)
- Git init, initial commit `86ecbc7 Starter from handoff`
- Supabase project created, linked, migration pushed
- `apps/mobile/.env` configured with publishable key

## What's next

- Start Expo web dev server (in progress right now)
- Open in browser via Chrome MCP so Dwayne can sign in
- Run `supabase/snippets/first-time-setup.sql` after Dwayne's account exists
- Seed demo data (fictional drivers, sample bookings)
- Enable Google Places + Routes APIs
- Deploy to Cloudflare Pages at a `pbc-demo` URL
- Hand Dwayne the demo URL + talking points
