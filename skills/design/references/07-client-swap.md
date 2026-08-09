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

**8. Empty the images folder and write a fresh `images.md`.** Both, in that order, and no
shortcuts on either.

```bash
# From the new project root. The old client's photos do not travel.
rm -rf images && mkdir images
rm images.md
```

Then write `images.md` from scratch off `templates/images.md`, with the prompts rewritten for
the new business. Rewritten, not edited. The prompt is built from the new trade's
`Buys This Result` and `Proof Asset` and the new style row's `Imagery Direction`, so a
detailer's dark bay and hard light has no business in a plumber's manifest. The hero law
applies again from zero: the new hero shows the new result, never the new provider working.

Slot count changes too. The section order changed in step 6, so the number of slots changed
with it. Recount the `figure.slot` elements and match the table to them.

Check before you move on:

```bash
ls images/          # empty, or only files generated for THIS client
grep -c "figure class=\"slot\"" index.html   # matches the row count in images.md
```

A single leftover photo from the last client is the fastest way to lose a contract. It is
also the easiest thing in the world to miss, because the page still renders and still looks
full. Delete the folder. Do not audit it.

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
| Every photo file | `images/`, deleted and recreated empty |
| Every image prompt | `images.md`, rewritten from the new trade and style rows |
| Every alt text | The markup and `images.md`, matching each other |
| Slot file names | `images/NN-slot-subject.webp`, renumbered to the new section order |
| Every review and name | `client.md` proof block |
| Form recipient address | Environment config, not the code |
| Booking or calendar link | `client.md` |
| Analytics property | Environment config |
| Favicon and Open Graph image | `public/` |
| Licence and insurance numbers | `client.md`, footer |

## What can stay

- The component library. Buttons, cards, inputs, section shells.
- The slot component. The `figure.slot` markup and its CSS are structure, so they stay. The
  ratios, the file names, the alt text and the prompts inside them do not.
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
| Slots and a fresh `images.md` | 5 min |
| Invisible stuff and deploy | 5 min |

Forty minutes to a page that ships with every slot placed, sized and prompted. Filling the
slots is the operator's next hour, or the client's next day, and it happens against
`images.md` instead of against a blank page. The shoot list still goes out during the brief,
not in phase 4, because client photos are the only part nobody can generate.

## The trap

The temptation on swap three is to stop asking the seven questions and stop offering three
directions, because you already know what a plumber's site looks like. That is when every
site starts looking the same, the operator becomes a template vendor, and the price falls.

Keep the gate. It is ten minutes and it is what the client is actually paying for.
