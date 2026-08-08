# Phase 5. Polish

The build renders. That is not done. This phase is where a page stops looking AI-made.

## Step 1. Grade the nine boxes

Open `checklist.md` and grade every box, honestly, in writing. Report the score with the
open boxes named. Do not fix anything until the whole grade is written down, because fixing
as you go means you never see the pattern.

## Step 2. The AI-made pass

Look for these, in this order. Every one of them is a signal a buyer reads as "a machine
made this and nobody checked".

**Type tells**
- Inter, or a system stack that fell back to Inter.
- Every heading the same size.
- Letter spacing untouched on a display face set at 64px. Big type needs tighter tracking.
- Widows: a single word alone on the last line of a heading. Fix with a non-breaking space.

**Colour tells**
- A purple to blue gradient anywhere.
- A gradient on text.
- Six or more colours in the build.
- Grey text at 3:1 that was meant to look calm.
- The same blue every AI page uses. If the accent came from a default and not from
  `palettes.csv`, replace it.

**Layout tells**
- Three feature cards with an icon, a two-word heading, and one sentence. The single most
  common AI-built section on the internet.
- Icons where photographs belong.
- Perfectly even padding everywhere, so nothing groups and nothing leads.
- A section that says "Why choose us" with three generic reasons.

**Copy tells**
- Any word from the banned list in `03-build.md`.
- Every sentence between 15 and 25 words.
- A rule of three in every heading.
- Adjective stacks.

**Motion tells**
- Fade-up on every section.
- Counting numbers.
- Parallax.
- A custom cursor.

Fix them. Then look again.

## Step 3. The specificity pass

Go line by line and ask one question of every sentence: could a competitor down the street
say this word for word? If yes, it is filler. Replace it with a number, a name, a place, a
date, or delete it.

```
BEFORE  We serve customers across the region with a commitment to quality.
AFTER   Burnaby, New West and East Van. Same crew since 2011.
```

Count how many concrete facts are on the page: numbers, place names, dates, prices, named
people. A local service home page should carry at least twelve. If it carries three, the
page is not finished, it is decorated.

## Step 4. The squint test

Blur the page until you cannot read words.

- The strongest shape should be the promise.
- The second strongest should be the money button.
- If the nav or a card grid wins, the hierarchy is wrong.

Then do it again at 375px.

## Step 5. The read-aloud test

Read the hero and the first proof section out loud. If you run out of breath, the sentence
is too long. If you feel embarrassed saying it, the claim is inflated and the client will
feel it too.

## Step 6. Contrast

Check every text-on-background pair with a real contrast tool, not by eye.

- Body text: 4.5:1 minimum.
- Text at 24px or larger, or 19px bold: 3:1 minimum.
- Text on the accent uses the `Text On Accent` value from `palettes.csv`. Do not improvise.
- Text over an image needs a solid scrim, not a blur. A 60 percent `--ink` overlay is the
  safe default.
- Focus rings need 3:1 against what is behind them.

## Step 7. Cut

The last pass is subtraction. Find:

- One section that repeats a section above it. Delete it.
- One paragraph that explains something the photo already showed. Delete it.
- Every button that is not the money action or a real navigation step. Delete it.
- Any badge, pill, or gradient that arrived without a decision. Delete it.

A page gets better by losing things far more often than by gaining them.

## Step 8. Regrade

Run `checklist.md` again from a blank sheet. Report the new score. If a box is still open,
say why and what unblocks it.

Next: `06-mobile-deploy.md`.
