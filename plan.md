# Church On The Hill — Implementation Plan

## Product approach

Build a full React/Express church website with a public editorial experience and a small secure content layer for event registrations and prayer requests. The public site uses a central, typed church-content module so dates, streams, links, satellite data, ministry activity and sermon metadata can be updated in one place. The server will persist only the information needed for forms, with explicit consent language and a private staff view gated behind the starter's authenticated admin role. A COTH site owner can expand the staff permission allowlist after the initial handoff.

The site will not manufacture operational facts. Published public evidence confirms the COTH International identity, its founders, its 40th-anniversary milestone and ten satellite community names. Satellite data fields will show verified facts where available; pages with no verified public address, leader or service time will direct visitors to the official COTH channel rather than display invented details. The main public contact used is `info@coth.co.za`, as published by COTH-Mbombela. Giving will take visitors to the official COTH web address pending a separately verified destination.

## Information architecture

The route system provides dedicated, shareable pages for Home, About, Our Story, What We Believe, Leadership, Satellites, each satellite, Ministries, each ministry, Events, Media, Watch Live, Sunday Services, Sermon Series, Podcasts, Connect, Contact, Give and Privacy. A small staff route supports attendee lookup and safe attendance-status updates. The main navigation remains compact: About, Satellites, Ministries, Media, Connect and Give; other pages surface through contextual links and the footer.

Public content data is organized into typed domain objects for satellites, ministries, service cards, streams, sermons, podcasts, events and belief statements. The events interface validates attendee registration client-side and server-side, confirms submissions, and exposes only the submitting attendee's confirmation code. The prayer form avoids requiring sensitive narrative details and is presented as private; forms do not collect unnecessary data.

## Design direction

**Design Movement**: A sunlit editorial revival—raw church print culture interpreted through COTH's own purple and orange identity.

**Core Principles**: Monumental ideas with human-scale details; purposeful whitespace over ornamental decoration; truth-first content; photographs treated as moments of testimony.

**Color Philosophy**: Charcoal gives the message gravity; off-white creates a calm paper-like field; purple carries COTH's identity; orange acts as a warm signal for invitations, live moments and small points of delight.

**Layout Paradigm**: An asymmetric editorial canvas with vertical guide rules, numbered chapters, split media cards and shifting blocks of text rather than a conventional centered marketing grid.

**Signature Elements**: A slim purple “hill line” rising through sections; orange parenthesis-style CTA marks; two-digit editorial chapter numbers.

**Interaction Philosophy**: Interactions should feel deliberate and tactile—underlines draw in, cards lift slightly and media play controls respond without turning the site into a spectacle.

**Animation**: Headlines reveal by word in a short stagger. Images use a clipped upward reveal. Section content fades and rises when entering view. Background guide lines have gentle parallax only on devices without reduced-motion preferences. Animation durations stay within 350–800ms with no looping decorative motion.

**Typography System**: Use Helvetica Now when installed, then Helvetica Neue/Arial as system fallbacks. Headlines are uppercase, compact and high contrast. Reading copy uses a more open regular weight, with small orange or purple labels for navigation cues.

**Brand Essence**: A kingdom family becoming brighter, better and bigger through God's Word. The personality is bold, faith-filled and hospitable.

**Brand Voice**: Direct, confident and invitational. “Come as you are. Leave carrying light.” “One church family. Many places. One bright calling.”

**Wordmark & Logo**: Preserve supplied marks when available. Until the official artwork is supplied to the project, use a restrained typographic COTH lockup with a rising line motif—not a replacement logo.

**Signature Brand Color**: COTH Purple `#662D91`.

## Technology and content handling

The starter's React, Wouter, Tailwind and Framer Motion stack serves the responsive public app. Express/tRPC and Drizzle provide controlled registration, prayer-request and attendance operations. Database rows are additive and scoped to the form's intended purpose. Frontend form validation uses Zod patterns and accessible error states. No third-party data or a private prayer message is rendered on public routes.

All public photography uses the downloaded Unsplash editorial images collected for this implementation. Image treatment uses CSS overlays, monochrome framing and crop-safe layout rather than generating portraits or a fabricated representation of COTH people.

## Project structure

- `client/src/data/church.ts`: typed editable public content, verified/source-aware satellite facts and all page copy.
- `client/src/components/coth/`: shared header, footer, buttons, media blocks, animated headings, data cards, forms and staff utilities.
- `client/src/pages/`: page templates and dynamic detail pages for satellites, ministries, sermons and events.
- `client/src/index.css`: COTH design tokens, responsive editorial layout and reduced-motion handling.
- `server/routers.ts`: event, attendance and prayer tRPC procedures with validation and access control.
- `server/db.ts`, `drizzle/schema.ts`, `drizzle/migrations/`: database queries and additive form-data schema.
- `client/public/assets/`: served church photography and route manifest.

## Delivery boundary

The initial build includes a content-ready, functional front end; private form operations; attendee confirmation and a protected staff-management view. It does not publish unverified leaders, addresses, schedules, livestream states, event dates or a guessed giving provider. Those settings remain deliberately visible as update points in the central content module, rather than being silently invented.

## Focused update — 23 October 2026
Preserve the approved brand, visual language, layouts, existing pages, working features, Facebook information and history. Update the YouTube destination to `https://www.youtube.com/@COTH40YEARS`. Set the worship identity to “Church On The Hill Worship” on Spotify, Apple Music, Deezer and SoundCloud; keep exact artist-page URLs as editable empty fields until COTH supplies them, and do not substitute a search result or guessed artist page. Replace the free-text visit satellite field with a selection backed by the central satellite list, dynamically render that satellite’s verified details or explicit confirmation placeholders, and store visit date and visitor count. Add a dedicated membership page and secure membership registration table, validated form, consent/privacy copy, confirmation and authenticated staff follow-up status without treating submission as official membership. Retain and represent the user-specified 19–22 November 2026 40th-anniversary celebration in Mbombela without inventing an exact venue or timetable. Append database changes only; keep styling within the current form, field, card and responsive conventions.

## Focused update — digital discipleship, worship release and motion
Keep the approved COTH brand and existing pages. Add digital discipleship as text content within Connect, not as a designed poster. Preserve the sequence “God loves you” (John 3:16), “We have all sinned” (Romans 3:23), “Jesus Christ is the answer” (1 Timothy 2:5), and “You must personally accept Jesus Christ” (Revelations 3:20); then include the original Sinner’s Prayer based on Romans 10:9, the exact seven assurances with their references, and the specified next steps. Use the exact salvation-plan, Sinner’s Prayer, seven assurances and next-step wording supplied by COTH on 24 October 2026; transcribe the copy and references verbatim. Link the section at `/connect#digital-discipleship` and make a QR code that uses the visitor-facing page URL. Add a validated, consent-based converts form offering “I am only visiting” and “I want to become a member,” with date, invited by, title, full name, surname, residential address, contact number, email, optional prayer request and age group; protect responses and provide authenticated church-team follow-up. Update worship identity to “Church On The Hill Worship” and feature the newly released “Fortieth Celebration Song” with Spotify, Apple Music, Deezer and SoundCloud labels; exact artist URLs will be added only when supplied, and the already-correct YouTube link stays unchanged. Refine existing Framer Motion reveals into gentle, staggered story transitions around Connect/salvation, Our Story, ministries and anniversary content; preserve reduced-motion support, mobile responsiveness and page performance, without aggressive parallax or long delays.


## Focused update — 25 October 2026: COTH 40th anniversary RSVP
Use the existing `/events/coth-40th-anniversary` event page, central `events` content model, RSVP form, database and authenticated staff attendee workspace. Publish the 19–22 November 2026 program as five gatherings: Thu 19 Nov, 6:00 PM opening service at COTH Headquarters, all black; Fri 20 Nov, 6:00 PM Traditional Night at COTH Headquarters, traditional attire; Sat 21 Nov, 11:00 AM formal celebration/special ceremony and program at COTH Headquarters, daytime formal with black tie encouraged; Sat 21 Nov, 5:00 PM worship night and musical conference/concert at Church On The Hill Mbombela, casual; Sun 22 Nov, 9:00 AM family and togetherness/vow-renewal service at COTH Headquarters, Sunday best. User-confirmed schedule labels are public; any precise street address, guest-speaker name and the Saturday-night featured ministries remain explicitly to be confirmed. Do not infer an individual satellite pastor’s name from “Pastor Elect.”

For the RSVP, retain a low-friction email-only identity (no password or application account), existing attendee/optional phone/party-size fields, explicit event-use consent and generated confirmation code. Normalize the submitted email and enforce a database uniqueness constraint per event so repeated or concurrent submissions cannot create duplicate registrations. A duplicate attempt returns only a neutral already-registered notice, never the existing attendee’s name, party size, confirmation code or contact information. The existing staff-only attendee view remains the sole RSVP-record list and attendance-status workflow. The site does not currently have an outgoing attendee-email provider; confirmations are therefore shown in the browser and must not be represented as sent by email. Keep database changes additive and preserve all existing attendee records.
