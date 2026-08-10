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
- The accent appears on the money action and at most one other decorative place. Focus
  rings, error states and inline text links are functional and do not count against that.
- Body text against its surface clears 4.5:1. Large headings clear 3:1.
- Text on the accent uses the `Text On Accent` value from `data/palettes.csv`.

OPEN when:
- There are six or more colours, or a gradient nobody decided on.
- Grey text sits on a grey card at 3:1 and calls itself subtle.
- The button is a different blue than the link.
- Dark mode was added without checking a single contrast pair.

Check: list every hex value used in the build. Five palette values, plus one error colour if
a form needs one, and that is the ceiling. A seventh hex opens box 3.

Then count the accent. Grep for `var(--accent)` and list what each hit is doing. Stars, tags,
bullets, badges and asterisks are decoration. Three or more decorative hits opens box 3, and
"I disclosed it" is not a reason to close it. The disclosure is the finding.

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

Every slot placed and sized from build one. Real files in all of them before this closes.

This is the box that stays open longest, and the one most often graded as closed because the
page "looks finished". It does not close on placeholders. It closes on files.

CLOSED when:
- `images.md` exists at the project root and every row reads `filled`.
- Not one placeholder is left on the page. Not one.
- Every image shows this business, its work, its people, or its place, or is a generated
  image that follows the hero law in `04-imagery.md`: the result the buyer gets, never the
  provider working.
- Before and after pairs are real photos, same subject, same angle, same light.
- No generated faces, no generated logos, no generated readable text anywhere.
- Images are cropped for the slot, not squashed into it.

OPEN when:
- Any slot is still a placeholder. One hatched box in the footer opens the box.
- `images.md` is missing, or its `Filled` count does not match what is on the page.
- There are no image slots at all. A trade site with no photograph of the work is a template,
  whatever the type and colour are doing.
- A stock handshake, a stock team meeting, or a smiling model in scrubs is on the page.
- A generated image has six fingers, melted text, or a logo that says nothing.
- The hero is a person working instead of the finished result.
- The hero is a before and after pair, so nothing on the page can be filled without the
  client. Slot 01 reads CLIENT PHOTO in `images.md`. The hero is one finished frame and it
  is always `generate`.
- Every row in `images.md` reads CLIENT PHOTO. The operator can fill nothing today, and the
  spec site he sends a prospect is all hatched boxes.
- An empty slot renders as a flat block instead of a hatched, captioned box. Load the page
  and screenshot the whole page without scrolling first. Every empty slot shows its hatch and
  its caption in that screenshot, or box 5 is open. A placeholder that only appears after the
  reader scrolls to it is a broken image for everyone who sees it first.
- The hero image is a 4MB JPEG straight off a phone.

Check: open `images.md`, read the `Filled` count, then count the `figure.slot` elements in
the markup. The two numbers have to match, and both have to be the full count. Then name the
source of every image on the page. Any answer of "a stock site" opens box 5.

Say it out loud in the handover, with the count:

```
OPEN 5 Imagery: 11 slots, 0 filled. Prompts are in images.md.
```

That is a finished build with an honest open box, and it gets the photos back in a day.
"Imagery done" while a hatched slot sits in the hero is the version the client finds out
about on the call.

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
- The form shows a success message without sending anything. That is not an open box, that
  is a defect. Rip the fake confirmation out before you hand the page to anyone.
- A visible button or link points at `#` and does nothing.

Check: be the buyer. Start at the top of the page and try to give the business money. If you
get stuck or bored, box 9 is open. Then open the network tab, submit the form, and watch for
the request. No request means no buyer, whatever the page said back to you.

## Reporting

Report like this:

```
Nine boxes: 7 closed, 2 open.
OPEN 5 Imagery: 11 slots, 0 filled. Prompts are in images.md. Slots 04 to 09 are the before
and after pairs and need the client's photos, not generated ones.
OPEN 8 Invisible: quote form posts nowhere. Blocked on the client's email address.
```

Name what is open, why, and what unblocks it. Never round up.

A build that ships with every slot placed, sized and prompted, and reports box 5 open, is
doing its job. A build that reports seven of nine when the honest score is three is worse
than a bad build, because nobody goes back to fix a build that was called finished.
