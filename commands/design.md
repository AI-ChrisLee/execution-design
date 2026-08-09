---
description: Build or restyle a client-facing site with the Execution Design system. Pass the brief after the command.
---

Use the `design` skill in this plugin for everything below. Read its SKILL.md, its checklist.md,
and the reference for the phase you are in before you write any code.

The operator's brief follows. If it is empty, ask for it.

$ARGUMENTS

Run the phases in order:

1. **Brief and questions** (references/01-brief-and-questions.md). Do not build yet. Ask the
   clarifying questions, then offer exactly three style directions pulled from data/styles.csv,
   matched to the trade in data/trades.csv. Stop and wait for the pick.
2. **Style pick** (references/02-style-pick.md). Lock the style, the palette from
   data/palettes.csv, and the font pairing from data/fonts.csv. Never use Inter.
3. **Build** (references/03-build.md). Write the page. Sell the result, never the tool. Put
   every image slot in the markup while you build the sections, at its final ratio, with real
   alt text and a file path under images/.
4. **Imagery** (references/04-imagery.md), **Polish** (references/05-polish.md),
   **Mobile and deploy** (references/06-mobile-deploy.md) as the work reaches them.

Write images.md at the project root, from templates/images.md, with one row and one finished
prompt per slot. The prompts have to run as they are in fal.ai, Higgsfield or ChatGPT.

Grade against the nine boxes in checklist.md whenever asked, and say which boxes are still open.
Box five is imagery, and it stays open with a count until a real file sits in every slot. Box
nine is a buyer, and it stays open until somebody pays.
