# Phase 6. Mobile and ship

Most buyers of a local service see the page on a phone, one-handed, outdoors, in a hurry.
Build for that person and the desktop version takes care of itself.

## Step 1. The 375px pass

Set the viewport to 375 wide and walk the whole page.

- No horizontal scroll at 320, 375 and 414. Check all three. One overflowing element breaks
  the whole page.
- Body text 16px minimum. Inputs 16px minimum, or iOS zooms on focus and the layout jumps.
- Tap targets 44x44 minimum with 8px between them.
- The primary action sits in the lower two thirds of the screen where a thumb reaches.
- The h1 wraps to three lines maximum. If it wraps to five, the clamp is wrong.
- Tables reflow into stacked rows. Menus become real text, never a sideways scroll.
- The sticky header is 56px or less. It should not eat a third of the screen.

## Step 2. The phone bar for local service

Any trade that gets called in an emergency gets a pinned call bar on mobile.

- Fixed to the bottom, full width, `--accent` background, `--on-accent` text.
- `<a href="tel:...">` with the number formatted the way a local reads it.
- 56px tall. Add matching bottom padding to the page so it never covers the footer.
- One action only. A call bar with a call button and a book button is neither.

For clinics, salons and restaurants, the same bar says Book or Order instead.

## Step 3. The one-thumb test

Start at the top of the page and try to give the business money, using one thumb, without
zooming. Time it. On a local service page it should be under fifteen seconds.

If you had to use two hands, pinch, or hunt, box 7 is still open.

## Step 4. The invisible stuff

Work through this list. Every item, every time.

**Head**
- `<title>` written for this business. Format: `Trade in City | Business Name`.
- Meta description under 155 characters, with the city and the offer in it.
- `<meta name="viewport" content="width=device-width, initial-scale=1">`.
- Canonical URL set.
- Open Graph title, description and image. Paste the link into a chat and look at it.
- Favicon at 32x32 and a 512x512 source. Not the framework default.
- `lang` attribute set on `<html>`.

**Structured data for local service sites**
- `LocalBusiness` JSON-LD with name, address, phone, hours, area served and URL.
- Every value read from `client.md`, so the swap in phase 7 updates it too.

**Forms**
- Submit a real test and confirm the message arrived somewhere the client can read.
- The client's address is the recipient, not the agency's.
- Success state tells the buyer what happens next and when.
- Basic spam protection: a honeypot field, or a rate limit. Not a puzzle that costs leads.

**Speed**
- Largest image under 300KB.
- Fonts preloaded and `font-display: swap`.
- No render-blocking script that is not needed for the first screen.
- Page interactive in under 2.5 seconds on a throttled 4G profile.
- Run Lighthouse on mobile. Performance and accessibility both 90 or better.

**Accessibility**
- Every image has real alt text.
- Headings run h1, h2, h3 in order with no skips.
- The keyboard reaches every action and the focus ring is visible.
- `prefers-reduced-motion` is honoured.

**Pages**
- 404 exists, matches the design, and links home.
- Privacy page if any form collects an email.
- Footer carries phone, address, hours, licence number where the trade needs one.

## Step 5. Deploy

1. Build locally and confirm no errors and no console warnings.
2. Deploy to a preview URL first. Send that to the client, not the live domain.
3. Point the domain only after the client has approved the preview in writing.
4. Set up redirects from the old site's URLs if one exists. A dead old URL loses the search
   traffic they already had.
5. Add analytics and confirm the first event fires.
6. Confirm the form fires from the live domain too. It behaves differently there.

## Step 6. Handover

Give the client three things and nothing else:

1. The live URL.
2. A one-page note on what changes without a developer: hours, prices, photos, and where
   `client.md` lives.
3. What the monthly covers. Photos, review requests, offer swaps, seasonal hero changes.

The install is the first payment. The monthly is the business. Say what it buys in plain
language on handover day, not in a follow-up nobody reads.

## Step 7. Post-launch check, day seven

- Did any lead come through, and did the client answer it?
- Does the page show up when you search the business name?
- Any console errors from real traffic?
- Any device where the layout broke?

Fix those, then go to `07-client-swap.md` and rebuild for the next business.
