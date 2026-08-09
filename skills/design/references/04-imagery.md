# Phase 4. Imagery

Photos decide whether a local business site is believed. Type and colour can be perfect and
one stock handshake undoes all of it.

Phase 3 already put every slot on the page, sized and named. This phase fills them. Two
routes: real photos from the client, or generated images that follow the law below.

## The order

1. **A real photo of this business.** Their work, their people, their van, their room.
2. **A generated image, prompted carefully, of the result rather than the provider.** The
   finished car, the empty room, the sold house, the surface. Never a fake customer, never a
   fake team.
3. **Nothing.** Type on a coloured block, a big number, a quote set large. Honest and fast.
4. **Stock.** Last. Usually never.

Most AI-built sites run this order backwards. That is why they look the same.

## Getting real photos

The client already has more than they think. Ask in this order:

- Their phone camera roll from the last three jobs.
- Their Google Business profile photos.
- Their Instagram or Facebook page.
- The manufacturer's product photos, if they install a branded product.

Then give them a shoot list. Specific, five to twelve shots, shot on a phone. Most clients
will do it the same day if the list is concrete.

Shoot list template for a local service business:

```
1. The van or truck with the logo, parked outside a real job. Landscape.
2. The owner, outdoors, in work clothes, looking at the camera. Waist up.
3. Three finished jobs, wide. Stand in the same spot for the before and after.
4. One close crop of the detail you are proud of.
5. The team, if there is one. Outdoors, not in a line.
6. The workspace, shop, or room, with the lights on.

Shot on a phone, in daylight, no filter, landscape unless noted.
Send the originals, not the compressed versions from a messaging app.
```

For a clinic, salon, or restaurant, swap the van for the room, and add the front door from
the street so the buyer recognises the place when they arrive.

## Before and after

The most persuasive image in local service work, and the easiest to ruin.

- Same subject. The same car, the same roof, the same yard.
- Same angle. Stand in the same spot. Mark it if the jobs are days apart.
- Same light. Both shots at the same time of day, or both indoors under the same lights.
- No filter on either. A graded after next to an ungraded before reads as a lie.
- Label them. "Before" and "After" in `--muted`, small, not a badge.

If the client only has an after, use only the after. A fabricated before is fraud and buyers
in these trades spot it. A generated before or after is the same fraud with extra steps.
Before and after pairs are always real photos. There is no exception to this one.

## The manifest

The build writes `images.md` at the project root. One row per slot: the file name, the pixel
size, the ratio, where it appears, the alt text, and the exact prompt.

Format and worked example in `templates/images.md`. The operator's whole job is: open the
file, copy a prompt, generate it, save the file under the given name in `images/`, reload.

**fal.ai, Higgsfield and ChatGPT are interchangeable for this.** Same prompt, all three, no
rewrite. Chris uses fal.ai. Other operators use Higgsfield or ChatGPT. Write the prompt so
it works in any of them, which means plain English and no tool-specific parameter flags.

## The hero law

**The hero shows the result the buyer gets. Never the provider working.**

This is a law, not a preference. It is the same law as "sell the result, never the tool",
applied to pictures, and it is the single fix that separates a commissioned build from a
template.

| Trade | The hero shows | Never |
|---|---|---|
| Auto detailing | The finished car, gleaming, done | A person polishing a panel |
| Real estate | The property that sold | The agent with folded arms |
| Gym | The room and real members mid-set | A trainer posing with a clipboard |
| Roofing | The finished roof on the finished house | A crew on a ladder |
| Dental | The treatment room, calm and clean | A model in scrubs smiling |
| Restaurant | The plate on the real table | A chef staring at a pan |
| Landscaping | The yard, done, from the street | Someone holding a trimmer |

The buyer is not shopping for a worker. They are shopping for the state their car, house,
body, or yard will be in on Friday. Show them Friday.

The one place the provider belongs is a portrait section, once, and that portrait is a real
photo of a real person. Never generated. See the two failure modes below.

## The prompt recipe

Build every prompt from three inputs, in this order:

1. **The result**, from `Buys This Result` in the trade row. This is the subject.
2. **The proof shape**, from `Proof Asset` in the trade row. This is what the image has to
   prove.
3. **The look**, from `Imagery Direction` in the style row. This is the light, the setting
   and the texture.

That third one is why two detailers get different pictures. Pull the clause straight from
the row instead of writing a generic prompt.

| Style row says | The clause it becomes |
|---|---|
| Detail Gloss: dark garage, one hard light source, reflections on paint | "inside a dark concrete bay, one hard overhead light, an unbroken reflection along the hood" |
| Iron Room: sweat, chalk, real members mid-set, shot from low | "chalk dust on black rubber floor, shot from floor height near the rack" |
| Front Desk: real property photos and one strong portrait | "shot from the sidewalk at mid morning, the whole front of the house in frame" |
| Clinic Calm: real room photos in natural light | "daylight from one window on the right, everything clean and put away" |

### The rules

- **30 to 100 words.** Under 30 and the model invents the missing half. Over 100 and it
  starts dropping clauses.
- **Front-load the subject.** First six words name the thing. "A freshly detailed black SUV
  parked inside..." not "A photograph in a moody style depicting..."
- **Positive present states only.** Say what is there, not what to remove. "Wheels clean and
  dry" beats "no dirt on the wheels". The one exception is the two failure modes below,
  where a short negative tail is allowed and needed.
- **One reference image at most. Never a collage.** Feeding four photos in a grid gets you an
  average of four photos.
- **Natural phone camera grade.** Real daylight or one named light source, slight grain.
  Write it like the client shot it on their phone, because that is what the buyer believes.
- **Never write these:** "flat colour range", "auto HDR", "colour graded". Every one of them
  pulls the output toward the plastic stock look the whole plugin exists to avoid. Skip
  "cinematic", "8k" and "hyperrealistic" for the same reason.

### The two failure modes

AI images fail at two things, over and over: people, and text that has to be readable. Both
of them are avoidable at the planning stage, which is the point.

**People.** Hands, teeth, eyes and the fifth person in the background. Any generated human
who is supposed to be this business is also a lie the client has to defend. So do not need
them. The empty room at opening, the finished car with nobody in it, the plated food, the
finished yard from the street. Every one of those sells harder than a fake person anyway.
When a face is genuinely required, it is a real photo of the real owner, from the shoot
list, or the slot goes to type instead.

**Text.** Signs, logos, plate numbers, price boards, phone numbers on a van. Generated text
melts. Plan the frame so no text needs to be readable: turn the sign away from the camera,
crop above the lettering, shoot the van from the wheel side, park the car with the plate out
of frame. Then close the prompt with one short clause naming what is absent.

Close every prompt with the same tail: `No people in the frame, no signage or lettering.`
Drop the first half when a person is deliberately in shot.

### Four real prompts

Copy the shape of these. They are the standard.

**Auto detailing, hero, Detail Gloss.** Trade result is paint that still looks wet two years
from now. Proof asset is same-car before and after.

```
A freshly detailed black SUV parked inside a dark concrete garage bay, one hard overhead
light directly above the roof, the hood and doors holding a clean unbroken reflection of the
light strip, water beads still sitting on the rear quarter panel, damp floor under the
tires, wheels clean and dry, evening light in the open bay door behind it. Shot on a phone,
single light source, deep shadows, slight grain. No people in the frame, no signage or
lettering.
```

**Real estate, hero, Front Desk.** Trade result is a sale at a number. Proof asset is recent
sales with price and days on market. The sign is turned so nothing has to be legible.

```
A two storey craftsman house on a quiet residential street at mid morning, front lawn cut,
porch light on, curtains open, a small yard sign at the edge of the grass angled away from
the camera, parked cars further down the block, bare maple branches overhead. Shot on a
phone from the sidewalk, flat overcast daylight, slight grain. No people in the frame, no
readable lettering.
```

**Gym, room shot, Iron Room.** The members and their results are real photos. What gets
generated is the room, empty, at opening.

```
An empty warehouse gym floor early in the morning, four squat racks in a row with loaded
barbells resting on the pins, chalk dust across the black rubber floor, kettlebells lined up
along the wall by size, a wall clock high on the brick, daylight coming through one high
window on the left. Shot on a phone from the doorway, one window as the light source, slight
grain. No people in the frame, no lettering on the walls.
```

**Dental, room shot, Clinic Calm.** The nervous buyer wants to see the room they will sit
in. The practitioner portrait next to it is a real photo, always.

```
A small dental treatment room with the chair reclined and empty, daylight from a window on
the right falling across the headrest, instrument tray closed and clean, a green plant on
the low cabinet, pale wood floor, blinds half open. Shot on a phone from the doorway at
chest height, natural daylight only, slight grain. No people in the frame, no brand names on
the equipment.
```

### Check the output before it goes in

- Count fingers, count legs on the chair, count wheels.
- Read every surface that could carry text. Any garbled lettering kills it, no matter how
  good the rest is.
- Check reflections. A reflection that shows something not in the room is the tell.
- Check it against the trade's `Never Sell This`. A prompt can drift back to selling the
  tool without you noticing.

Two rerolls maximum. If the third one still has melted text, change the framing instead of
the wording.

## Technical

| Slot | Size | Ratio | Format | Weight |
|---|---|---|---|---|
| Hero, desktop | 1920x1080 | 16 / 9 | AVIF with WebP fallback | Under 200KB |
| Hero, mobile | 828x1104 | 3 / 4 | AVIF with WebP fallback | Under 150KB |
| Gallery item | 1200x900 | 4 / 3 | WebP | Under 120KB |
| Before or after | 1200x900 | 4 / 3 | WebP | Under 120KB |
| Card thumbnail | 800x600 | 4 / 3 | WebP | Under 80KB |
| Portrait | 1000x1250 | 4 / 5 | WebP | Under 120KB |
| Open Graph | 1200x630 | 40 / 21 | JPEG or PNG | Under 300KB |
| Favicon | 512x512 source, plus 32x32 ico | 1 / 1 | PNG and ICO | Under 20KB |

The ratio column is what goes in `--slot-ratio`. Set it once in phase 3 and the real file
lands without moving anything.

Rules:

- Set explicit `width` and `height` on every image so nothing jumps while it loads.
- `loading="lazy"` on everything below the fold. Never on the hero.
- `object-fit: cover` with a chosen `object-position`. Faces do not belong at the crop edge.
- Serve a separate mobile crop for the hero. Cropping a landscape hero to a phone gives you
  a strip of sky.
- Generate at the listed pixel size or larger, then compress down. Never upscale a small one.

## Alt text

Written for a person using a screen reader, and it happens to help search too.

```
NO   alt="image1"
NO   alt="roofing services in Vancouver roofing contractor best roofer"
NO   alt="placeholder hero image"
YES  alt="Finished asphalt shingle roof on a two storey house in East Vancouver"
```

The alt text goes in at build time, describing the photo that will exist, and it never
mentions the placeholder. It is the same sentence in `images.md`, so write it once and copy
it into both.

Decorative background images get `alt=""`. Never leave the attribute off.

## The gate

Box 5 closes when a real file sits in every slot. Not when the slots are placed, not when
the prompts are written, not when it looks fine on the demo call.

So the handover reads like this, out loud, every time:

```
OPEN 5 Imagery: 11 slots, 0 filled. Prompts are in images.md.
Slots 04 to 09 are the before and after pairs and need the client's photos, not generated ones.
```

That is a finished build with an open box, which is honest and gets the photos back in a
day. "Imagery done" with a hatched box in the hero is not, and the client finds out on the
call.

The old rule here said never ship a placeholder. The new rule is stricter, not looser: ship
the slot, sized and prompted, and keep box 5 open until the real files land. A grey box that
says "image coming" and nothing else is still banned. A measured slot carrying its own
prompt is a work order.

Next: `05-polish.md`.
