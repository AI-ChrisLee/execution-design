# Phase 7. The client swap

This is the reuse engine. The first site takes an hour. The second one takes forty minutes,
because everything that made the first one specific lives in one file.

Nothing else in the build knows the client's name.

## The rule

Every business fact lives in `client.md` at the project root. Business name, city, trade,
phone, hours, colours, photos, links, tone, proof. If a fact about the business appears
anywhere else in the codebase, that is a bug and it will cost you time on every swap after
this one.

Check before you call a build done:

```bash
# From the project root. Every hit outside client.md is a bug.
grep -rn "Acme Detailing" --exclude=client.md .
grep -rn "604-555" --exclude=client.md .
grep -rn "Vancouver" --exclude=client.md .
```

Zero hits is the target. If the grep finds the client name in six components, the swap will
take an hour again.

## The swap, step by step

**1. Copy the folder.**

```bash
cp -R sites/acme-detailing sites/northshore-plumbing
cd sites/northshore-plumbing
```

**2. Replace client.md.** Fill it for the new business using the seven questions from
`01-brief-and-questions.md`. Do not edit around the old one. Start from
`templates/client.md` and fill it fresh, or the old business leaks into the new site through
a field nobody re-read.

**3. Look up the new trade.** Read the new trade's row in `data/trades.csv`. The style
shortlist, the result the buyer wants, the trap, the proof asset and the trust signals all
change. Auto detailing and plumbing are both local service and they are not the same page.

**4. Offer three directions again.** The new client picks. Do not reuse the last client's
style because it is already wired up. Two detailers on the same street with the same site is
how a member loses both.

**5. Apply the new tokens.** Swap the palette and the pairing in the token block, from
`palettes.csv` and `fonts.csv`. Five values and one import line. Nothing else in the CSS
should need touching, because everything references a variable.

**6. Reorder the sections.** Take the `Section Order` from the new style row. Sections are
components, so this is reordering, not rebuilding.

**7. Rewrite the copy.** Fresh, from the new `Buys This Result` and the new `client.md`.
Never find-and-replace the old copy. A plumber's page with a detailer's sentence structure
reads exactly as wrong as it is.

**8. Replace every image.** All of them. A single leftover photo from the last client is the
fastest way to lose a contract. Run the shoot list from `04-imagery.md`.

**9. Update the invisible stuff.** Title, meta description, Open Graph image, favicon,
JSON-LD, form recipient, phone links, analytics property. All of it reads from `client.md`
if you built it right. Confirm anyway.

**10. Grade the nine boxes.** From a blank sheet, in `checklist.md`. A swap is not done
because it renders.

## What must change on every swap

Never let one of these survive from the last client.

| Thing | Where |
|---|---|
| Business name, everywhere | `client.md`, title, footer, JSON-LD |
| Phone number and tel links | `client.md`, header, call bar, footer |
| Address, hours, service area | `client.md`, footer, JSON-LD, map |
| Every photo | `public/` or the image directory |
| Every review and name | `client.md` proof block |
| Form recipient address | Environment config, not the code |
| Booking or calendar link | `client.md` |
| Analytics property | Environment config |
| Favicon and Open Graph image | `public/` |
| Licence and insurance numbers | `client.md`, footer |

## What can stay

- The component library. Buttons, cards, inputs, section shells.
- The layout primitives and the space scale.
- The form logic and its validation.
- The build config, deploy setup, and the redirect pattern.
- The nine-box grading sheet.

That split is the whole point. Structure is reusable. Content never is.

## Timing

A realistic second build:

| Step | Time |
|---|---|
| Brief and `client.md` | 10 min |
| Trade lookup and three directions | 5 min |
| Tokens and section order | 5 min |
| Copy | 10 min |
| Images | 5 min if the client sent the shoot list, otherwise blocked |
| Invisible stuff and deploy | 5 min |

Forty minutes, and the only step that can blow up is images. Which is why the shoot list
goes out during the brief, not in phase 4.

## The trap

The temptation on swap three is to stop asking the seven questions and stop offering three
directions, because you already know what a plumber's site looks like. That is when every
site starts looking the same, the operator becomes a template vendor, and the price falls.

Keep the gate. It is ten minutes and it is what the client is actually paying for.
