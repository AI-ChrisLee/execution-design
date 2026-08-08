# Phase 4. Imagery

Photos decide whether a local business site is believed. Type and colour can be perfect and
one stock handshake undoes all of it.

## The order

1. **A real photo of this business.** Their work, their people, their van, their room.
2. **A generated image, prompted carefully, of a thing rather than a person.** A texture, a
   surface, a background. Never a fake customer, never a fake team.
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
in these trades spot it.

## Generated images

Allowed for surfaces, textures, backgrounds, and abstract slots. Not allowed for people who
are supposed to be this business, and not allowed for the work itself. A generated roof is a
lie about a roof.

If you generate:

- Prompt for the phone-camera look: natural daylight, slight grain, one light source. Never
  ask for a phone in the frame, a phone screen, or a status bar.
- One subject per image. Front-load the subject in the prompt. Thirty to a hundred words.
- Describe positive states, what you want present, not what you want removed.
- Check hands, text, logos and reflections before you use it. Any garbled text kills it.
- Never a collage reference. One reference image at a time.

## Technical

| Slot | Size | Format | Weight |
|---|---|---|---|
| Hero | 1920x1080 desktop, 828x1104 mobile | AVIF with WebP fallback | Under 200KB |
| Gallery item | 1200x900 | WebP | Under 120KB |
| Card thumbnail | 800x600 | WebP | Under 80KB |
| Portrait | 1000x1250 | WebP | Under 120KB |
| Open Graph | 1200x630 | JPEG or PNG | Under 300KB |
| Favicon | 512x512 source, plus 32x32 ico | PNG and ICO | Under 20KB |

Rules:

- Set explicit `width` and `height` on every image so nothing jumps while it loads.
- `loading="lazy"` on everything below the fold. Never on the hero.
- `object-fit: cover` with a chosen `object-position`. Faces do not belong at the crop edge.
- Serve a separate mobile crop for the hero. Cropping a landscape hero to a phone gives you
  a strip of sky.

## Alt text

Written for a person using a screen reader, and it happens to help search too.

```
NO   alt="image1"
NO   alt="roofing services in Vancouver roofing contractor best roofer"
YES  alt="Finished asphalt shingle roof on a two storey house in East Vancouver"
```

Decorative background images get `alt=""`. Never leave the attribute off.

## The gate

No slot ships with a placeholder. If a real image is missing, replace the slot with type or
a plain block and put the missing photo on the blocker list. A grey box that says
"image coming" is how a site sits at 90 percent for two weeks.

Next: `05-polish.md`.
