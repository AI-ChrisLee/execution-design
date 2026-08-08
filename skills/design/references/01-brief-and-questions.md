# Phase 1. Brief and questions

The gate. No building happens until this file is done and the operator has answered.

Most bad client sites are not a design failure. They are a briefing failure. The operator
guessed, built for six hours, and the client said "that is not us". Asking seven questions
first costs ten minutes and saves the rebuild.

## The rule

Ask the questions. Wait for real answers. Fill `client.md`. Then offer three directions.
Anything you do before that is your opinion, and nobody is paying for your opinion yet.

If the operator says "just build something", ask anyway. Give them the seven questions as a
list they can answer in two minutes. A short answer beats a guess.

## The seven questions

Ask them in this order. Each one changes the build.

**1. What does this business actually sell, in the customer's words?**

Not the service list. The result. A roofer sells a dry house. A dentist sells a visit that
does not hurt. Look up the trade in `data/trades.csv` and read `Buys This Result` back to
them as a starting point. Ask if it is right.

Follow-up: what does the customer say when they call? Those words go in the hero.

**2. Who is the customer, and where are they?**

City and neighbourhoods, not "everyone". Homeowner or renter, business or consumer, price
shopper or referral. A page for a $200 job and a page for a $20,000 job are different pages.

**3. What is the one action you want a visitor to take?**

One. Call, book, request a quote, order, subscribe. If they name three, make them rank
them, and the top one becomes the money action on every screen.

**4. What proof do you have right now?**

Reviews and how many. Years in business. Licence and insurance. Photos of finished work.
Named results. Anything that already exists beats anything you would have to invent.

Write down what is missing. That becomes the shoot list in phase 4.

**5. What do you have for photos and brand?**

Existing logo, colours, photos, a Google Business profile with images. Ask for the files
now, not in phase 4. If they have nothing, say so plainly and plan the shoot.

**6. Which three sites do you like, and which one do you hate?**

The hated one is more useful than the liked ones. It tells you the direction to avoid, and
it is usually the direction the operator would have picked by default.

**7. What has to be on the page that you would forget to tell me?**

Hours. Service radius. Languages spoken. A deposit policy. A licence number the regulator
requires. Financing. A second location. This question catches the thing that gets discovered
after launch.

## Two more questions for ad landing pages

If the shape is `ad-landing`, add these:

**8. What does the ad say, word for word?**

The H1 repeats the ad hook exactly. Not a paraphrase, not an improvement. Message match is
most of the conversion rate.

**9. What happens after they submit?**

Who gets the lead, how fast do they call back, and what does the thank-you page say. A lead
that nobody calls for two days is a wasted page.

## Filling client.md

Copy `templates/client.md` to the project root. Fill every field. Rules:

- No guessing. If a fact is unknown, write `UNKNOWN` and put it on the blocker list.
- Phone, address and hours get copied exactly as the client writes them, then checked once
  against their Google Business profile.
- Colours go in as hex. If the client gives a logo and no hex, sample the logo and confirm.
- The `never_say` list is as useful as the `sells` line. Fill it.

`client.md` becomes the only place business facts live for the rest of the build. This is
what makes the swap in phase 7 take minutes.

## Blockers

Keep a short list of what you are waiting on. Report it with every progress update. A build
that stalls quietly at 80 percent because nobody chased a phone number is the most common
way a first site takes three weeks.

Format:

```
Blocked on: real photos of two finished jobs, the licence number, the booking link.
Can build without: nothing else.
```

## Then stop

Brief done. Go to `02-style-pick.md`. Do not open a code editor yet.
