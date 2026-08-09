# Execution Design

A Claude Code plugin for building pages somebody pays for.

Three shapes only. Local service business sites, content brand pages, and ad landing pages.
It carries 16 curated style directions with real palettes and font pairings, a nine-box
quality bar, a set of anti-default laws, and a client swap that rebuilds a whole site for
the next business from one file.

## Install

```
/plugin marketplace add AI-ChrisLee/execution-design
/plugin install execution-design@execution-design
```

If the install summary says to run `/reload-plugins`, run it.

Then use it:

```
/execution-design:design
```

Or just describe the job. "Build a site for a detailer in Burnaby" triggers it.

## What it does

Seven phases, in order, each with its own reference file the model reads on demand.

| Phase | What happens |
|---|---|
| 1. Brief | Seven questions to the operator, then `client.md` gets filled |
| 2. Style pick | Three named directions offered with real hex values and fonts, then a hard stop |
| 3. Build | Tokens, section order from the style row, copy written to the laws |
| 4. Imagery | Every slot placed and sized, `images.md` written with a real prompt per slot |
| 5. Polish | Nine boxes graded, then the pass that removes every AI tell |
| 6. Mobile and ship | 375px pass, the invisible stuff, deploy, handover |
| 7. Client swap | The same build running for the next business in forty minutes |

## What makes it different

Most design plugins are a general database. This one is narrow on purpose, and it carries
rules a database cannot.

**Curated for three shapes, not for everything.** 16 style directions instead of 84. Each
one is tied to real trades: detailers, dentists, gyms, contractors, salons, restaurants,
accountants, agents. `data/trades.csv` maps 54 trades to the styles that fit, the result the
buyer actually wants, the thing you must never sell them, the proof asset to gather, and the
trap in that trade.

**It carries the laws.**

- Sell the result, never the tool. A roofer sells a dry house, not a shingle brand.
- Ask before you build. Seven questions, then three directions, then a hard stop.
- Inter is banned as the body font. It is what every AI-made page defaults to.
- Five colours, one loud. Surface, Raised, Ink, Muted, Accent. No sixth.
- Every image slot ships in the markup, sized, named and prompted. Never a stock photo.
- The hero shows the result the buyer gets, never the provider working.
- Delete the AI words and see what survives. If nothing survives, the claim was empty.

**The image placeholder system.** The page ships with every image slot already in place, at
the final aspect ratio, with the alt text the real photo will need and a file path under
`images/`. The empty state is a neutral measured slot, never a broken image icon and never a
stock photo. Alongside it the build writes `images.md`: one row per slot with the file name,
the pixel size, the ratio, where it appears, the alt text, and the exact prompt. Paste a
prompt into fal.ai, Higgsfield or ChatGPT, save the file under the given name, reload. The
page is done and nothing moved. Box 5 stays open, out loud, with a count, until every
placeholder has a real file behind it.

**The nine boxes.** Point of view, typography, colour, hierarchy, imagery, motion, mobile,
the invisible stuff, and box nine, a buyer. Box nine is the one every design tool forgets. A
page with no way to call, book, or pay is a portfolio piece. The plugin grades a build
against all nine and reports which are open, by name, with no rounding up.

**The client swap.** Every business fact lives in `client.md` at the project root. Name,
city, trade, colours, photos, links, tone, proof. Replace that one file, look up the new
trade, apply the new palette, and the whole site regenerates for the next business. First
site an hour. Second site forty minutes.

## Layout

```
execution-design/
├── LICENSE
├── README.md
├── .claude-plugin/
│   ├── marketplace.json
│   └── plugin.json
└── skills/
    └── design/
        ├── SKILL.md
        ├── checklist.md              the nine boxes, with grading criteria
        ├── data/
        │   ├── styles.csv            16 style directions
        │   ├── palettes.csv          16 palettes, 5 hex values each
        │   ├── fonts.csv             16 pairings with import lines and scales
        │   └── trades.csv            54 trades mapped to styles and results
        ├── references/
        │   ├── 01-brief-and-questions.md
        │   ├── 02-style-pick.md
        │   ├── 03-build.md
        │   ├── 04-imagery.md
        │   ├── 05-polish.md
        │   ├── 06-mobile-deploy.md
        │   └── 07-client-swap.md
        └── templates/
            ├── client.md            every business fact, the swap reads this
            └── images.md            the image manifest, one prompt per slot
```

## The data

Four CSV files. Read the trade row first, then join.

- `trades.csv` `Style Shortlist` matches `styles.csv` `Style`
- `styles.csv` `Palette ID` matches `palettes.csv` `Palette ID`
- `styles.csv` `Font Pairing ID` matches `fonts.csv` `Font Pairing ID`

One trade name gets you the full spec in three lookups. Every font is a real Google Font
with a working import line. Every palette has been checked for contrast, and the text colour
that goes on the accent is stored next to it.

## Verify a change

From this directory:

```bash
claude plugin validate .
claude plugin validate . --strict
claude --plugin-dir .
```

## Attribution

This plugin is a fork of [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill),
released under the MIT License, copyright (c) 2024 Next Level Builder.

What we took from it: the plugin and marketplace manifest shape, the idea of a skill backed
by CSV data instead of prose, the progressive-disclosure split between a short SKILL.md and
reference files loaded on demand, the priority-table-as-centrepiece structure, the paired
positive and negative columns in every data table, and the rule that the tool must say out
loud when a lookup returned nothing rather than inventing a value.

What is ours: all of the data, all of the references, the nine boxes, the laws, the seven
questions, the three-direction gate, and the client swap. No code was copied.

The original is a general design database covering 84 styles across every product type. This
is a narrow fork for one job: sites that local service businesses, content brands, and ad
buyers actually pay for.

The name `ui-ux-pro-max` and the `uupm.cc` domain belong to Next Level Builder and are not
used here.

## License

MIT. See `LICENSE`, which carries both the original copyright notice and ours.
