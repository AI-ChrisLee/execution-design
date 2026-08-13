---
name: design
description: Design and build client-facing sites for local service businesses, content brands, and ad landing pages. Use this when asked to design or build a website, a landing page, a homepage, or a brand page. Use this when asked to pick a style direction, a colour palette, or a font pairing for a real business. Use this when asked to review, grade, or fix a page against a quality bar. Use this when asked to rebuild an existing site for a different business from a client.md file. Carries 16 curated style directions, the nine-box conversion checklist, and the anti-default laws.
license: MIT. Full terms in LICENSE, including the notice for the forked work.
---

# Execution Design

A design system for pages somebody pays for. Three shapes only: local service business
sites, content brand pages, ad landing pages. Everything here exists to make the second
site faster than the first.

## When to use this

Any time the output is a page a stranger will judge in three seconds. Building a new site,
rebuilding an old one, picking a direction, fixing a page that looks AI-made, or grading a
build before it goes to the client.

## Skip it for

Backend work, database schemas, API design, scripts, internal tools nobody sells. If the
task does not change how something looks, reads, or gets clicked, this skill adds nothing.

## The nine boxes

This is the bar, and it is graded on selling, not on pretty. Nobody pays for fonts. An
owner pays for one thing: more customers. A build is done when all nine are closed. Grade
honestly and name the open boxes out loud. Full grading criteria live in `checklist.md`.

| # | Box | Closed looks like | Open looks like |
|---|---|---|---|
| 1 | One goal | One money action the whole page pushes, plus one honest reason to act now | Competing actions, generic copy, no reason to move this week |
| 2 | Type that signals money | A real pairing, sized on a scale, readable at 375px | Default system font, one size, Inter body |
| 3 | Minimal colour | Five values, one loud, on the money action | Six-plus colours, gradient soup, random accents |
| 4 | The three second test | Who, where, and the button, before any scrolling | Everything the same weight, nothing leads |
| 5 | Imagery that sells the result | The result the buyer gets, a real file in every slot | A placeholder still on the page, or the provider working |
| 6 | Motion that feels expensive, not busy | Zero or one intentional move, under 250ms | Scroll reveals on every section, counters, parallax |
| 7 | Built for the phone | Built at 375px first, thumb reaches every action | Desktop shrunk down, tiny tap targets, side scroll |
| 8 | Nothing leaks | Fast, found on Google, every lead lands in a list | Broken form, leads firing into the void, 4MB hero |
| 9 | A buyer | One money action per screen, and it works | Pretty page with no way to pay, call, or book |

Box nine is the one every design tool forgets. A page without a buyer is a portfolio piece.

## The laws

These are not preferences. Break one and the build gets rejected.

1. **Sell the result, never the tool.** A roofer sells a dry house. A gym sells the body in
   twelve weeks. Nobody buys the shingle brand or the equipment list. `trades.csv` has the
   result for every trade in the `Buys This Result` column and the trap in `Never Sell This`.
2. **Ask before you build.** Run the questions in `references/01-brief-and-questions.md`,
   then offer exactly three style directions and stop. No building until the operator picks.
3. **Inter is banned as the body font.** So are the system defaults, unset. Inter is what
   every AI-made page defaults to and buyers now read it as fake. Pick a pairing from
   `fonts.csv`. If a client brand guide demands Inter, say so out loud in the handover and
   pair it with a display face that is not Inter.
4. **Five colours, one loud.** Surface, Raised, Ink, Muted, Accent. That is the whole system.
   One accent, used for the money action and almost nothing else.
5. **Every image slot ships in the markup, sized, named and prompted.** The page never goes
   out with zero photographs and no place for one. Each slot locks its final ratio, carries
   the alt text the real photo will need, points at a file path under `images/`, and shows a
   neutral placeholder that reads as a reserved slot instead of a broken image. That
   placeholder is painted by CSS on the first frame, never wired to a failed image request,
   because every slot below the fold is lazy and its request has not happened yet. The build
   writes `images.md` at the project root with the exact prompt for every slot, so the
   operator can paste it into fal.ai, Higgsfield or ChatGPT and be done. Never a stock photo,
   not even for a demo. Markup in `references/03-build.md`, prompts in
   `references/04-imagery.md`.
6. **The hero shows the result the buyer gets, never the provider working.** A detailer's
   hero is the finished car, not a person polishing it. A realtor's hero is the property that
   sold. A gym's hero is the room and real members, not a trainer posing. This is a law.
   The hero is ONE finished frame carrying a generate prompt. Never a before and after pair.
   Before and after is proof, it lives in the gallery, and it is always a real client photo,
   so a hero built as a pair is a hero nobody can fill. Test every build: at least the hero
   and one section image must be fillable today, by the operator, with no photo from the
   client. A page where every slot says CLIENT PHOTO is a page of empty boxes on the day it
   gets sent to a prospect, which is the day it has to sell.
7. **Box 5 stays open until real files replace every placeholder**, and the build says so out
   loud with a count. A real photo beats a generated one. A generated one beats an empty
   slot. Stock loses to all three.
8. **Delete the AI words and see what survives.** Write the copy, strip every adjective
   stack and every filler word, then read what is left. If nothing is left, the claim was
   empty. No em dashes anywhere on the page, ever. Grep the markup for the character before
   grading. Copy rules in `references/03-build.md`.
9. **The page never fakes a send.** No simulated form submit, no success message when
   nothing left the browser, no working-looking button behind a placeholder endpoint. If
   there is no live destination yet, disable the button, say so on the page, and let the
   phone number carry the money action. Procedure in `references/03-build.md`.
10. **One goal per page, and one honest reason to act now.** Decide the money action before
    the first section is written: book, call, or quote. Every section points at it. Then
    give the buyer one true reason to move this week: a seasonal offer, this month's slots,
    a first-visit price. Real constraints only. Fake countdowns and invented scarcity are
    banned; there is always a real constraint, find it and name it.
11. **Every lead lands in a list.** The booking form is not decoration, it is the thing the
    owner is paying for. Wire it so every request lands somewhere the client can read: a
    database table, a sheet, an inbox that gets checked. Test it with a real submission
    before handover, every time. A lead that leaks is a refund waiting to happen.

## The data

Four CSV files live in `data/`, next to this file. Read them with the Read tool, or from a
shell:

```bash
cat "$CLAUDE_PLUGIN_ROOT/skills/design/data/trades.csv"
cat "$CLAUDE_PLUGIN_ROOT/skills/design/data/styles.csv"
cat "$CLAUDE_PLUGIN_ROOT/skills/design/data/palettes.csv"
cat "$CLAUDE_PLUGIN_ROOT/skills/design/data/fonts.csv"
```

If `$CLAUDE_PLUGIN_ROOT` is empty, the files are in the `data/` folder that sits beside this
SKILL.md. Use that absolute path. Never guess at values that are in the file.

| File | Rows | What it answers |
|---|---|---|
| `trades.csv` | 54 | For this trade: which styles fit, what the buyer actually buys, what never to sell, the proof asset to gather, the money band, the trust signals, the trap. Covers all three shapes: 42 local service, 8 content brand, 4 ad landing |
| `styles.csv` | 16 | The style direction: mood, section order, radius, motion budget, imagery direction, copy angle, what it is wrong for |
| `palettes.csv` | 16 | The five hex values with roles, the text colour that goes on the accent, and the rule for using it |
| `fonts.csv` | 16 | Display and body pairing, weights, the Google Fonts import line, the CSS variables, the type scale, the trap |

How they join:

- `trades.csv` → `Style Shortlist` names match the `Style` column in `styles.csv`.
- `styles.csv` → `Palette ID` matches `Palette ID` in `palettes.csv`.
- `styles.csv` → `Font Pairing ID` matches `Font Pairing ID` in `fonts.csv`.

So one trade name gets you the full spec in three lookups. Read the trade row first, always.

## The workflow

Seven phases. Each one has a reference file. Read the file for the phase you are in, not all
of them at once.

| Phase | Read this | You leave with |
|---|---|---|
| 1. Brief | `references/01-brief-and-questions.md` | A filled `client.md` and answers to the seven questions |
| 2. Style pick | `references/02-style-pick.md` | Three named directions offered, one picked by the operator |
| 3. Build | `references/03-build.md` | Tokens, sections in order, image slots, real copy |
| 4. Imagery | `references/04-imagery.md` | `images.md` written, a prompt per slot, real files where they exist |
| 5. Polish | `references/05-polish.md` | Nine boxes graded, open ones closed |
| 6. Mobile and ship | `references/06-mobile-deploy.md` | 375px pass, the invisible stuff, live URL |
| 7. Client swap | `references/07-client-swap.md` | The same build running for the next business |

Do not skip phase 2. Building before the operator picks a direction is how a site gets
rebuilt three times for free.

## Starting a project

1. Copy `templates/client.md` to the project root as `client.md`.
2. Ask the seven questions from phase 1 and fill it in. Leave nothing as a guess. If a fact
   is unknown, write `UNKNOWN` and ask for it before build.
3. Look up the trade row in `trades.csv`.
4. Offer three directions with names, palettes and fonts. Stop and wait.
5. Build. `client.md` is the only place business facts live. No name, phone, city or colour
   gets hard-coded anywhere else.
6. Create `images/` at the project root and write `images.md` beside `client.md`, from
   `templates/images.md`, with one row and one finished prompt per slot on the page.

## If the data has no match

The lookup either hits or it does not. Say which.

1. Retry once with a broader trade name. "Mobile dog grooming" is not in `trades.csv`, but
   the shape is the same as "House cleaning": a recurring visit at the customer's address.
2. If it still misses, pick the closest row by shape, not by industry, and say out loud
   which row you borrowed and why.
3. If nothing is close, design from the laws and the nine boxes, and say plainly that no
   row matched. Never present a made-up palette or font as if it came from the data.

A guessed hex value that looks like data is worse than an honest gap.

## The client swap

This is the reuse engine and the reason the second site takes forty minutes instead of an
hour. Every business fact lives in `client.md` at the project root. Nothing else in the
build knows the client's name.

To rebuild the whole site for the next business:

1. Copy the finished project folder.
2. Replace `client.md` with the new business.
3. Run the swap: read the new `client.md`, look up the new trade in `trades.csv`, apply the
   new palette and fonts, regenerate copy and section order, empty `images/`, and write a
   fresh `images.md` with prompts rewritten for the new business.
4. Grade the nine boxes again. A swap is not done because it renders.

Full procedure, including what must change and what must not, is in
`references/07-client-swap.md`.

## Before you hand it over

Grade all nine boxes in `checklist.md` and report the score honestly. Name every open box.
A build with three open boxes handed over as finished is how a client stops paying the
monthly.

Box 5 gets a count, not an adjective. "11 slots, 0 filled, prompts in images.md" is the
report. "Imagery done" while a placeholder sits in the hero is not.
