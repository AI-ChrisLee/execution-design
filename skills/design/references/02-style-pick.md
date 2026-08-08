# Phase 2. Style pick

Three directions, named, with real values. The operator picks one. Then you build.

## Why three

One option is a demand. Five options is a survey. Three is a decision the client can make in
a minute, and it makes the direction theirs, which is what stops the rebuild later.

## The lookup

Three reads, in this order. Never skip the trade row.

1. Read `data/trades.csv`. Find the row matching the client's trade. Take the
   `Style Shortlist`, `Buys This Result`, `Never Sell This`, `Proof Asset`, `Local Signals`
   and `Watch Out`.
2. Read `data/styles.csv`. Pull the shortlisted style rows plus one deliberate outsider that
   fits the shape. That outsider is what makes three feel like a real choice.
3. Read `data/palettes.csv` and `data/fonts.csv` using the `Palette ID` and
   `Font Pairing ID` from each style row. Copy the hex values and the import line exactly.

If the trade is not in `trades.csv`, match by shape instead of by industry. Mobile dog
grooming behaves like house cleaning: recurring, at the customer's address, booked by trust.
Say which row you borrowed and why.

## Which shape

| Shape | Use it when | Pages |
|---|---|---|
| `local-service` | A business serves a geographic area and gets called, booked, or quoted | 1 to 5 |
| `content-brand` | A person or publication wants subscribers, viewers, or readers | 1 to 2 |
| `ad-landing` | One ad points at one offer and nothing else | 1, no nav |

An ad landing page can also borrow a trade style. Take the trade's palette and fonts, then
use the `Direct Response` section order and strip the nav. That keeps the ad, the page and
the eventual site looking like one business.

## How to present the three

Each direction gets a name, a sentence, the palette, the pairing, and what it is wrong for.
Keep the whole thing under a page. Show the swatches as hex, and if you can render, show
them as blocks.

Template:

```
DIRECTION A. Trade Bold
Heavy and plain-spoken. Built for buyers who want to see the crew and the machine.

Palette (Amber Yard)   Surface #F4F1EC   Raised #E5E0D6   Ink #14161A
                       Muted #5E6269     Accent #F2A20C
Type                   Archivo Black over Archivo
Motion                 Hover only. Nothing animates on scroll.
Wrong for              Anything sold on softness or calm.

DIRECTION B. ...
DIRECTION C. ...
```

Then one line: "Pick A, B, or C, or tell me what is off and I will adjust one of them."

## Then stop

This is a hard stop. Do not build any of the three "to show them". Do not build a hybrid.
Wait for the pick.

If the operator picks nothing and asks you to choose, choose the first shortlisted style
from the trade row, say why in one sentence, and note that they can change it in phase 5
before imagery goes in. After imagery, a direction change costs a rebuild.

## After the pick

Write the pick into `client.md` under `style`:

```
style: Trade Bold
palette_id: P01
font_pairing_id: F01
```

Those three lines are what the client swap in phase 7 reads. Nothing downstream should look
up the style any other way.

## The anti-default check

Before you move to build, confirm all four:

- Body font is not Inter and is not an unset system stack.
- Exactly five colours are defined, one of them loud.
- The section order came from the style row, not from habit.
- The motion budget from the style row is written down.

If any of those is not true, the direction is not picked yet.

Next: `03-build.md`.
