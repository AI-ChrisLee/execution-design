# The nine boxes

The grading sheet. Run it before any handover, and run it again after a client swap.

Score each box CLOSED or OPEN. There is no partial credit and there is no average. Report
the open ones by name. "Seven of nine, boxes 5 and 8 open" is a real answer. "Looks good" is
not.

## Box 1. Point of view

The page has an opinion about who it is for and what it sells.

CLOSED when:
- One sentence in the hero names the buyer and the result.
- Swapping the business name would break the copy, because the copy is specific.
- There is something on the page the competition would not say.

OPEN when:
- The hero could belong to any business in the trade.
- The copy leads with "quality service" or "years of experience" or "your trusted partner".
- Three services get equal weight because nobody decided which one sells.

Check: cover the logo. Can you tell which business this is? If not, box 1 is open.

## Box 2. Typography

A real pairing, sized on a scale, readable on a phone.

CLOSED when:
- Display and body come from a pairing in `data/fonts.csv`, imported and applied.
- Body copy is 16px minimum, 17px preferred, line height 1.6 or looser.
- The heading scale uses clamp, so nothing overflows at 375px or looks tiny at 1440px.
- Line length in body sections sits between 60 and 75 characters.

OPEN when:
- Inter is the body font.
- The font never got imported and the browser fell back to a system face.
- Every heading is the same size, or the h1 wraps to five lines on a phone.
- Body text is 14px anywhere a buyer has to read a sentence.

Check: open the page at 375px and read a full paragraph without zooming.

## Box 3. Colour

Five values, one loud, applied the same way every time.

CLOSED when:
- Surface, Raised, Ink, Muted, Accent are set as CSS variables and used by name.
- The accent appears on the money action and at most one other place.
- Body text against its surface clears 4.5:1. Large headings clear 3:1.
- Text on the accent uses the `Text On Accent` value from `data/palettes.csv`.

OPEN when:
- There are six or more colours, or a gradient nobody decided on.
- Grey text sits on a grey card at 3:1 and calls itself subtle.
- The button is a different blue than the link.
- Dark mode was added without checking a single contrast pair.

Check: list every hex value used in the build. More than five means box 3 is open.

## Box 4. Hierarchy

The eye lands where the money is.

CLOSED when:
- Squinting at the hero, the promise reads first and the button reads second.
- Section headings are visibly heavier than body text and lighter than the h1.
- Whitespace groups related things and separates unrelated ones.
- Only one thing per screen is loud.

OPEN when:
- Everything is bold, so nothing is.
- The nav is heavier than the hero headline.
- Cards, badges and pills compete on the same row.
- Padding is the same everywhere, so nothing groups.

Check: blur the screenshot until text is unreadable. The shape you still see should be the
promise and the button.

## Box 5. Imagery

Real photos of the real business, or honest empty space.

CLOSED when:
- Every image shows this business, its work, its people, or its place.
- Before and after pairs are the same subject, same angle, same light.
- Images are cropped for the slot, not squashed into it.
- Where no real photo exists, the slot is replaced by type or a plain block, on purpose.

OPEN when:
- A stock handshake, a stock team meeting, or a smiling model in scrubs is on the page.
- A generated image has six fingers, melted text, or a logo that says nothing.
- The hero image is a 4MB JPEG straight off a phone.
- The gallery is a placeholder grid nobody replaced.

Check: name the source of every image on the page. Any answer of "a stock site" opens box 5.

## Box 6. Motion

Zero or one intentional move.

CLOSED when:
- The motion budget from the style row is respected and nothing extra crept in.
- Hovers are 120ms to 200ms. Section reveals, if any, are 200ms to 300ms.
- `prefers-reduced-motion` is honoured.
- Nothing moves on the hero except a video the client paid for.

OPEN when:
- Every section fades up on scroll.
- Numbers count up.
- There is parallax.
- A custom cursor exists.

Check: load the page and scroll once. Count the moving things. More than one opens box 6.

## Box 7. Mobile

Built at 375px first.

CLOSED when:
- The layout was designed at 375px and grew from there.
- Tap targets are 44px minimum and the primary action sits in thumb reach.
- No horizontal scroll at 320px, 375px, or 414px.
- The phone number is tappable and pinned or reachable on a local service site.
- Tables and menus reflow instead of scrolling sideways.

OPEN when:
- The desktop layout got shrunk and the text is now 11px.
- Something pushes the page 20px wider than the viewport.
- The sticky header eats a third of the screen.
- The form fields are too small to tap without zooming.

Check: 375px wide, one thumb, book the appointment. If it takes two hands, box 7 is open.

## Box 8. The invisible stuff

The part nobody sees until it is broken.

CLOSED when:
- Title tag and meta description are written for this business, not left as the template.
- Favicon exists and is not the framework default.
- Open Graph image renders when the link gets pasted into a message.
- Every image has real alt text.
- The form actually sends, and a test message arrived somewhere the client can read.
- Largest image under 300KB. Fonts preloaded. Page interactive in under 2.5 seconds on 4G.
- 404 page exists and links home.
- Phone, email and address in the footer match `client.md` exactly.

OPEN when:
- The title tag still says the framework name.
- The form posts nowhere and nobody tested it.
- Google cannot see the business name, city or trade anywhere in the markup.
- The page weighs 6MB.

Check: submit the form yourself and confirm the message arrived. Every time.

## Box 9. A buyer

The page asks for money, a call, or a booking, and the path works end to end.

CLOSED when:
- Every screen height has one money action visible or one scroll away.
- The action matches the trade: call for emergency trades, book for clinics and salons,
  form for quotes, subscribe for content brands.
- The path works: click, fill, send, confirmation, and the client gets notified.
- The money section repeats at the bottom of the page.
- Money terms are stated, at least as a band. Hidden pricing is not mystery, it is friction.

OPEN when:
- The only contact route is an email address in the footer.
- The button says "Learn more" and goes to a page with another "Learn more".
- The booking link is broken, or points at the agency's calendar instead of the client's.
- Nobody tested a real submission.

Check: be the buyer. Start at the top of the page and try to give the business money. If you
get stuck or bored, box 9 is open.

## Reporting

Report like this:

```
Nine boxes: 7 closed, 2 open.
OPEN 5 Imagery: three service cards still use stock photos. Need shoot list from client.
OPEN 8 Invisible: quote form posts nowhere. Blocked on the client's email address.
```

Name what is open, why, and what unblocks it. Never round up.
