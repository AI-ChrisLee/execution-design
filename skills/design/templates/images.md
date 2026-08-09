# images.md

Copy this file to the project root as `images.md`. The build writes it during phase 3, at
the same time it puts the slots in the markup. It is the operator's work order for photos.

One row per slot. Never a slot on the page that is missing here, and never a row here with
no slot on the page.

## The header the operator reads

Keep this block at the top of every generated `images.md`, filled for the project.

```
Site: Acme Detailing, Burnaby
Style: Detail Gloss   Palette: P03   Slots: 11   Filled: 0

HOW TO FILL A SLOT
1. Copy the prompt for the slot.
2. Paste it into fal.ai, Higgsfield, or ChatGPT. Any of the three. Same prompt, no rewrite.
3. Generate at the pixel size in the row, or larger. Never upscale a small one.
4. Save the file in images/ with the exact File name below. Do not rename it.
5. Reload the page. The placeholder is gone and nothing moved.

Rows marked CLIENT PHOTO are not generated. Ask the client for them. A generated before and
after is fraud, and a generated face is a lie the client has to defend.

Box 5 stays OPEN until Filled matches Slots.
```

Three tools, one prompt. fal.ai, Higgsfield and ChatGPT are interchangeable here. Use
whichever one the operator already pays for. Do not write tool-specific parameter flags into
a prompt, because that breaks the other two.

## The summary table

```markdown
| # | File | Pixels | Ratio | Where it appears | Source | Status |
|---|---|---|---|---|---|---|
| 01 | 01-hero-black-suv-after.webp | 1920x1080 | 16 / 9 | Hero, full bleed | generate | empty |
| 01m | 01-hero-black-suv-after-mobile.webp | 828x1104 | 3 / 4 | Hero under 640px | generate | empty |
| 02 | 02-bay-interior.webp | 1200x900 | 4 / 3 | How it works, step 1 | generate | empty |
| 03 | 03-owner-portrait.webp | 1000x1250 | 4 / 5 | Owner section | CLIENT PHOTO | empty |
| 04 | 04-before-silver-sedan.webp | 1200x900 | 4 / 3 | The work, pair 1 left | CLIENT PHOTO | empty |
| 05 | 05-after-silver-sedan.webp | 1200x900 | 4 / 3 | The work, pair 1 right | CLIENT PHOTO | empty |
| 10 | 10-open-graph.webp | 1200x630 | 40 / 21 | Link preview | generate | empty |
| 11 | 11-favicon.png | 512x512 | 1 / 1 | Browser tab | CLIENT LOGO | empty |
```

Status is `empty` or `filled`. Nothing else. No "in progress", no "pending", because both of
those mean empty and read as done.

## The per-slot block

The table is the map. Each slot then gets its own block, because a prompt inside a table
cell wraps into something nobody can copy. Fenced block for the prompt, so it copies in one
click.

### Worked example, filled

Below is exactly what the build should write. This is the standard for how specific each
field has to be.

---

**01. Hero**

File `images/01-hero-black-suv-after.webp` and `images/01-hero-black-suv-after-mobile.webp`
Size 1920x1080 desktop, 828x1104 mobile
Ratio 16 / 9 desktop, 3 / 4 under 640px
Where Hero, full bleed, behind the headline and the call button
Alt `Black SUV parked outside the bay after a full detail, paint reflecting the sky`
Source generate
Status empty

```
A freshly detailed black SUV parked inside a dark concrete garage bay, one hard overhead
light directly above the roof, the hood and doors holding a clean unbroken reflection of the
light strip, water beads still sitting on the rear quarter panel, damp floor under the
tires, wheels clean and dry, evening light in the open bay door behind it. Shot on a phone,
single light source, deep shadows, slight grain. No people in the frame, no signage or
lettering.
```

For the mobile crop, run the same prompt and add: `Vertical frame, the car filling the lower
two thirds.` Do not crop the desktop file down. A cropped landscape hero on a phone is a
strip of sky.

---

**02. The bay**

File `images/02-bay-interior.webp`
Size 1200x900
Ratio 4 / 3
Where How it works, step one, left column
Alt `The detailing bay with the doors open and the lights on, floor clear and ready`
Source generate
Status empty

```
An empty detailing bay with the roller door open to the street, polished concrete floor
still damp in one corner, a rolling tool cart parked against the wall, coiled hoses on a
wall hook, one work light overhead and daylight coming in through the open door. Shot on a
phone from just inside the door, slight grain. No people in the frame, no signage or
lettering.
```

---

**03. Owner portrait**

File `images/03-owner-portrait.webp`
Size 1000x1250
Ratio 4 / 5
Where Owner section, right column, next to the years and the review count
Alt `Marco, the owner, standing in the bay doorway in work clothes`
Source CLIENT PHOTO. Do not generate.
Status empty

```
Not a prompt. Ask the client for this shot:
Stand in the open bay door, work clothes on, waist up, phone held at chest height, daylight
behind the person taking it. One take, no filter, send the original.
A generated face on an owner section is the fastest way to lose the contract.
```

---

**04 and 05. Before and after, pair one**

File `images/04-before-silver-sedan.webp`, `images/05-after-silver-sedan.webp`
Size 1200x900 each
Ratio 4 / 3
Where The work, first pair, left and right
Alt `Silver sedan before the detail, swirl marks visible on the hood` and
`The same silver sedan after the detail, hood reflecting the ceiling light cleanly`
Source CLIENT PHOTO. Do not generate.
Status empty

```
Not a prompt. Same car, same spot on the floor, same light, both shots.
Mark the floor with tape if the two shots are days apart.
If only the after exists, use only the after and delete the before slot.
```

---

**10. Open Graph**

File `images/10-open-graph.webp`
Size 1200x630
Ratio 40 / 21
Where Link preview when the page is pasted into a message
Alt Not used. Set the same description in the meta tag.
Source generate
Status empty

```
A freshly detailed black SUV shot from the front three quarter angle inside a dark bay, one
hard overhead light, wide empty space on the left half of the frame for text. Shot on a
phone, deep shadows, slight grain. No people in the frame, no signage or lettering.
```

Leave the left half quiet. The business name and the city get set as real text over it in
the build, never generated into the picture.

---

**11. Favicon**

File `images/11-favicon.png` plus `favicon.ico` at 32x32
Size 512x512 source
Ratio 1 / 1
Where Browser tab
Alt Not used.
Source CLIENT LOGO. Do not generate.
Status empty

```
Not a prompt. Take the client's mark from client.md.
If there is no mark, set the first letter in the display face on the accent colour and say
so in the handover. A generated logo is a trademark problem, not a design choice.
```

---

## Rules for writing this file

1. **Every slot on the page has a row.** Run through the markup and count the `figure.slot`
   elements. The counts have to match.
2. **The prompt is finished, not a template.** No `[trade]`, no `[colour]`, no blanks. The
   operator pastes it as it is. A prompt with a blank in it is a task, not a work order.
3. **Prompts come from the recipe in `04-imagery.md`.** Result from the trade row, proof
   shape from the trade row, look from the style row. 30 to 100 words, subject first,
   positive states, phone-camera grade, the negative tail for people and lettering.
4. **The hero prompt shows the result the buyer gets.** Never the provider working. That law
   is in `04-imagery.md` and it is checked here.
5. **Mark real-photo slots clearly.** Before and after pairs, faces, logos, and any shot that
   claims to be this business's actual work. Those say CLIENT PHOTO and carry the shot
   instruction instead of a prompt.
6. **Alt text matches the markup exactly.** Same sentence in both places, written for the
   real photo.
7. **Update Filled as files land.** The number at the top is what the nine-box grade reads.

## What this file is not

Not a mood board. Not a list of ideas. Not "we could add photos here". It is a list of files
that do not exist yet, each with the exact instruction that creates it, at the exact size
the page is already holding open.
