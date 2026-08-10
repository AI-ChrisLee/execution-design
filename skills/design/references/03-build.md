# Phase 3. Build

Tokens first, sections second, copy last. In that order, because copy written before the
layout exists always turns out too long.

## Step 1. Tokens

Write the whole design system as variables before you write a single section. Copy the hex
values from the palette row and the font values from the pairing row. Do not retype them
from memory.

```css
@import url('<Google Fonts Import from fonts.csv>');

:root {
  /* Colour: five values, from palettes.csv. No sixth. */
  --surface:  #F4F1EC;
  --raised:   #E5E0D6;
  --ink:      #14161A;
  --muted:    #5E6269;
  --accent:   #F2A20C;
  --on-accent:#14161A;

  /* Type: from fonts.csv */
  --font-display: 'Archivo Black', 'Arial Black', sans-serif;
  --font-body:    'Archivo', system-ui, sans-serif;

  /* Space: one scale, no arbitrary values */
  --s1: 0.25rem; --s2: 0.5rem;  --s3: 0.75rem; --s4: 1rem;
  --s5: 1.5rem;  --s6: 2rem;    --s7: 3rem;    --s8: 4rem;
  --s9: 6rem;    --s10: 8rem;

  /* Shape: from the style row */
  --radius: 0px;
  --line: 1px solid color-mix(in srgb, var(--ink) 12%, transparent);

  /* Motion: from the style row */
  --t-fast: 150ms;
  --t-slow: 250ms;
  --ease: cubic-bezier(0.2, 0, 0, 1);
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

Rules on tokens:

- Every colour in the build references a variable. A raw hex anywhere in a component is a bug.
- Section padding is `var(--s9)` on desktop, `var(--s7)` on mobile. Pick once, use everywhere.
- Shadows are optional and usually wrong. If you use one, use one: `0 1px 2px rgba(0,0,0,.06)`.
  Layered coloured shadows are an AI tell.
- Borders beat shadows for separating things on a light surface.

## Step 2. Sections

Take the `Section Order` string from the style row in `styles.csv` and build it in that
order. Do not reorder it because a section feels more interesting. The order was set by what
a buyer in that trade needs to see and when.

Section rules that hold across every style:

- One idea per section. If a section has two headings, it is two sections.
- Every section that makes a claim is followed by something that proves it.
- The money action appears in the hero, in the middle, and at the end. Three times, same
  wording, same colour.
- Maximum width for reading is 68 characters. Full-bleed is for images, not paragraphs.
- Nothing between the hero and the first proof element. Proof comes second, always.

Standard component specs:

| Component | Spec |
|---|---|
| Primary button | `--accent` background, `--on-accent` text, 52px tall, 24px horizontal padding, `--radius`, weight 600, hover darkens 8 percent over `--t-fast` |
| Secondary button | Transparent, 1px `--ink` border, `--ink` text, same height |
| Card | `--raised` background, `--line` border, `--s5` padding, `--radius`. No shadow unless the style says so |
| Input | 52px tall, 1px `--muted` border, 16px text minimum so iOS does not zoom, visible focus ring in `--accent` |
| Link | `--accent`, underline on hover, never a colour that is not the accent |
| Proof strip | `--raised` band, one row, four items maximum, `--muted` labels and `--ink` values |

Only one primary button per screen height. That is what makes it primary. A sticky mobile
bar counts as a button on every screen, so the header CTA comes out when the bar goes in.

### Where the accent is allowed

The accent is the scarcest thing in the build. Two decorative homes, and that is the whole
budget: the money action, and one supporting element you name out loud in the handover.
Everything else uses `--ink` or `--muted`.

Functional states do not spend the budget, because a buyer reads them as feedback and not
as decoration: the focus ring, the error colour, a text link inside a paragraph. Those are
free. Star ratings, list bullets, badges, tags, card borders, required-field asterisks and
section rules are not. Those are the ten small places an accent leaks into and the reason a
page ends up looking like a theme.

Before you leave this step, list every selector that touches `var(--accent)`. If more than
two are decorative, cut back to two.

## Step 3. Image slots

Hard rule. Every image slot goes into the markup while you are building sections, not after.
A page that ships with no image slots is not a page waiting for photos, it is a page that
forgot photos. A detailer's site with no car on it reads as a template.

The slot is a real element from build one. It holds the exact size the real photo will take,
it carries the alt text that photo will need, and it points at the file path that photo will
live at. When the operator drops the file in, nothing on the page moves and no markup gets
edited.

### The markup

This is the standard. Copy it. Do not invent a second pattern.

```html
<figure class="slot" style="--slot-ratio: 16 / 9; --slot-focus: 50% 45%">
  <img src="images/01-hero-black-suv-after.webp"
       alt="Black SUV parked outside the bay after a full detail, paint reflecting the sky"
       width="1920" height="1080" decoding="async" fetchpriority="high"
       onerror="this.remove()">
  <figcaption>Photo slot 01. Save as images/01-hero-black-suv-after.webp, 1920x1080.
    Prompt 01 in images.md.</figcaption>
</figure>
```

```css
.slot {
  position: relative;
  margin: 0;
  box-sizing: border-box;      /* the placeholder border must not grow the box */
  aspect-ratio: var(--slot-ratio);
  background: var(--raised);
  border-radius: var(--radius);
  overflow: hidden;
}

/* The placeholder is painted by the figure itself, on the first frame, always.
   It never waits for a request to fail. */
.slot::before {
  content: "";
  position: absolute;
  inset: 0;
  z-index: 0;
  background: repeating-linear-gradient(135deg,
    transparent 0 20px,
    color-mix(in srgb, var(--ink) 5%, transparent) 20px 21px);
  box-shadow: inset 0 0 0 1px color-mix(in srgb, var(--ink) 12%, transparent);
}

.slot figcaption {
  position: absolute;
  z-index: 0;
  left: 0; right: 0; bottom: 0;
  padding: var(--s3) var(--s4);
  font-family: var(--font-body);
  font-size: 12px;
  line-height: 1.4;
  letter-spacing: 0.04em;
  color: var(--muted);
  background: color-mix(in srgb, var(--surface) 88%, transparent);
}

/* The photo sits on top and covers the placeholder the moment it decodes. */
.slot img, .slot picture { position: absolute; inset: 0; z-index: 1; }

.slot img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: var(--slot-focus, 50% 50%);
}
```

How it behaves. The figure paints its own placeholder: the raised fill, a hairline inset, a
faint diagonal hatch, and a small muted caption naming the file. That happens on the first
frame, before any image request goes out, so the slot reads as a measured reserved box from
the moment the page appears. The photo is stacked on top. The day the operator saves the real
file at that path, it covers the hatch and the caption and both are gone. No markup edit, no
layout shift, no broken image icon.

Do not wire the placeholder to `:not(:has(img))` and an `onerror` that removes the failed
image. That version looks correct on the hero and is wrong everywhere else. Every slot below
the fold carries `loading="lazy"`, so the request never goes out until the reader scrolls
near it, so the error never fires, so the placeholder never turns on. A real build shipped
this way screenshotted with seven of its eight slots as flat dead rectangles. A placeholder
that depends on a request failing is a placeholder that is not there yet. Paint it first,
cover it later.

`onerror="this.remove()"` stays on the image, but only to strip the browser's broken-image
glyph. Nothing about the placeholder depends on it any more.

The `box-sizing` line stays. The hairline is an inset shadow, so it costs no layout in either
state, and empty and full measure the same to the decimal.

With JavaScript off and the file still missing, the browser draws its own broken-image mark
over the slot. The measured box and the hatch underneath are both still there, so it is still
sized and still reads as a slot. Say that in the handover if anyone asks.

The hero gets a second crop, so it gets `<picture>`. Same wrapper, same behaviour. The
`picture` element is positioned with the image, so an empty one takes no space over the
placeholder.

```html
<figure class="slot slot--hero" style="--slot-ratio: 16 / 9">
  <picture>
    <source media="(max-width: 640px)" srcset="images/01-hero-black-suv-after-mobile.webp">
    <img src="images/01-hero-black-suv-after.webp"
         alt="Black SUV parked outside the bay after a full detail, paint reflecting the sky"
         width="1920" height="1080" fetchpriority="high" onerror="this.remove()">
  </picture>
  <figcaption>Photo slot 01. Two files, desktop and mobile. Prompt 01 in images.md.</figcaption>
</figure>

<style>
  @media (max-width: 640px) { .slot--hero { --slot-ratio: 3 / 4; } }
</style>
```

### The rules on slots

1. **Ratio is locked on the wrapper.** `aspect-ratio` on the figure, `width` and `height` on
   the image. The box is the same size empty and full.
2. **File paths live under `images/` at the project root.** Create the folder during the
   build, even empty. Name every file `NN-slot-subject.webp`, lowercase, hyphens, where `NN`
   matches the row number in `images.md`. `01-hero-black-suv-after.webp`,
   `04-before-silver-sedan.webp`, `07-owner-portrait.webp`. A mobile crop adds `-mobile`.
3. **Alt text is written for the real photo**, present tense, describing what the photo will
   show. Never the word placeholder, never the file name, never a keyword list. Decorative
   slots get `alt=""` and no figcaption.
4. **The placeholder never looks broken, and it is there on the first frame.** No broken
   image icon, no red X, no "image coming soon" in 24px type across the hero. Neutral fill,
   hairline, small caption, all of it painted by CSS. A slot must never need a failed request
   to look like a slot, because every slot below the fold is lazy and that request has not
   happened yet.
5. **Never a stock photo, not even for the demo.** The stock photo you drop in to make the
   demo look full is the one that ships. An honest empty slot beats it every time.
6. **The build writes `images.md` at the project root.** One row per slot, with the prompt.
   Template and format in `templates/images.md`, recipe in `04-imagery.md`. A slot that is
   not in `images.md` does not exist as far as the operator is concerned.
7. **Say box 5 is OPEN out loud** in the handover, with the count. "12 slots, 0 filled" is a
   finished build with an open box. "Imagery done" with a hatched hero is a lie.

### How many slots

Take them from the `Section Order` in the style row and the `Proof Asset` in the trade row.
A local service home page normally lands between eight and fourteen. If your page has three,
you skipped the proof section that sells the job.

### Look at the empty slots before you move on

Reading the CSS is not the check. Open the page with `images/` still empty and take one
screenshot of the whole thing, without scrolling first. Every empty slot has to show its
hatch and its caption in that one screenshot, the last one in the footer included.

A flat block in that screenshot means the placeholder is wired to something that has not
happened yet. Fix the CSS, do not scroll until it appears. The prospect opening the spec site
sees the same flat block you just saw, and a flat block is what a broken image looks like.

No browser in this environment? Then say in the handover that the empty slots were not
rendered, in those words, and put it on the blocker list. Never grade it as checked.

## Step 4. Copy

Copy is where a good-looking page dies. Four rules.

### Rule 1. Sell the result

Read the `Buys This Result` and `Never Sell This` cells for the trade before writing a word.

```
NO   Premium ceramic coating using 9H nano-technology, applied by certified installers.
YES  Your paint still beads water in 2029. Booked in one visit.

NO   Comprehensive dental care for the whole family in a state-of-the-art facility.
YES  A cleaning that does not hurt, and the price before we start.

NO   We deliver quality landscaping solutions tailored to your needs.
YES  Your yard stays done. One price, April to October.
```

### Rule 2. Delete the AI words and see what survives

Write the line. Then strip these and read what is left. If the sentence is gone, the claim
was empty and you have to find a real one.

Banned outright: delve, tapestry, elevate, robust, seamless, cutting-edge, best-in-class,
state-of-the-art, world-class, unparalleled, bespoke, curated experience, holistic, tailored
to your needs, solutions, unlock, harness, embark, journey, passionate about, dedicated to
excellence, we pride ourselves.

Also banned: "your trusted partner", "quality you can count on", "we go above and beyond",
"customer satisfaction is our top priority", "with years of experience".

Every one of those is a claim with no evidence. Replace it with a number, a name, or a date.

```
NO   With years of experience, we take pride in delivering quality workmanship.
YES  Nineteen years. 412 Google reviews. Same crew on every job.
```

### Rule 3. No em dashes on the page

Zero. Not in the headline, not in a card, not in the FAQ, not in a meta description. The long
dash is the loudest tell that a machine wrote the line, and buyers read it that way now.

Use a period, a comma, brackets, or split the sentence.

```
NO   Paint correction, ceramic coating and full interiors — booked at the bay.
YES  Paint correction, ceramic coating and full interiors. Booked at the bay.

NO   Nineteen years in the same town — same crew on every job.
YES  Nineteen years in the same town. Same crew on every job.
```

Grep the finished markup for the character before you grade box 5. One hit is a fail.

### Rule 4. No adjective stacking, short restrained lines

One adjective per noun, and only if it earns its place. Two adjectives in a row is a tell.

```
NO   A beautiful, modern, fully responsive website built with cutting-edge technology.
YES  A site that loads in a second and books jobs from a phone.
```

Line length by slot:

| Slot | Limit |
|---|---|
| H1 | 12 words |
| Subhead | 20 words |
| Button | 4 words, a verb first |
| Section heading | 8 words |
| Body paragraph | 3 sentences |
| Card body | 25 words |

Vary sentence length on purpose. A page of 18-word sentences reads as machine-written even
when every sentence is fine.

Write "you" and "we". Never "our clients" or "the customer". You are talking to one person.

### Button copy

The button says what happens next, in the buyer's words.

```
NO    Learn more.    Get started.    Submit.    Contact us.
YES   Call now.      Book Tuesday.   Get my quote.    Send the photos.
```

## Step 5. States

Build these before you call a section done. They are half the "invisible stuff" box.

- Hover and focus on every interactive element. Focus must be visible with a keyboard.
- Empty state for any list that could be empty.
- Loading state on the form button, and it must disable on submit.
- Error state on every field, with the message next to the field, not at the top.
- Success state after submit that tells the buyer what happens next and when.

### Never fake the send

A success message that appears when nothing left the browser is the worst thing you can
ship. The operator demos it, it looks like it works, the client puts it on a real domain,
and the leads go nowhere for a month before anybody notices. A broken form gets fixed on
day one. A lying form does not.

So: no `setTimeout` that pretends, no `preventDefault` with a fake confirmation, no
placeholder endpoint sitting behind a working-looking button.

If the real endpoint is not known yet, do this instead:

1. Leave the form's `action` empty and the submit button `disabled`, with a line under it
   that reads `Booking goes live when the client's email is connected.`
2. Put the phone number in the form's place as the working money action, so the page still
   converts.
3. Put the endpoint at the top of the blocker list and say box 8 and box 9 are OPEN.

The page never claims something happened that did not happen. That rule outranks the
success state above.

## What not to build

- A hero carousel. Nobody sees slide two.
- A pop-up on load. It costs more than it collects on a local service site.
- A chat widget nobody staffs.
- An animated hero background.
- A page of icons where photos should be.
- A blog nobody will write.

Next: `04-imagery.md`.
