# client.md

Copy this file to the project root as `client.md`. It is the only place business facts live.
Fill every field. Where a fact is unknown, write `UNKNOWN` and put it on the blocker list.

Everything below the front matter is read by the build. Nothing in the code should contain
the business name, phone number, city, or brand colours. Only this file does.

```yaml
---
# Identity
name: UNKNOWN                 # exact legal or trading name, spelled the way they spell it
short_name: UNKNOWN           # what people call them, used in the nav and the footer
trade: UNKNOWN                # must match a Trade in data/trades.csv, or the closest one
shape: local-service          # local-service | content-brand | ad-landing
tagline: UNKNOWN              # the result, in the customer's words, 12 words or fewer

# Place
city: UNKNOWN
region: UNKNOWN               # province or state
country: UNKNOWN
address: UNKNOWN              # street address, or NONE if they do not take walk-ins
service_area: UNKNOWN         # neighbourhoods or a radius, as the customer would say it
timezone: UNKNOWN

# Reach
phone: UNKNOWN                # formatted the way a local reads it
phone_tel: UNKNOWN            # E.164 for the tel: link, e.g. +16045551234
email: UNKNOWN                # where the form sends, the client's address not ours
booking_url: UNKNOWN          # their calendar, not the agency's
maps_url: UNKNOWN
hours: UNKNOWN                # e.g. Mon to Fri 7am to 6pm, Sat 8am to 2pm, Sun closed
emergency_hours: NONE         # 24h line if the trade has one

# Money
money_action: UNKNOWN         # call | book | quote | order | subscribe | apply
money_action_label: UNKNOWN   # the button text, verb first, 4 words max
price_display: UNKNOWN        # band | from | exact | none, and the numbers if there are any
deposit_terms: NONE

# Style, filled in phase 2 after the operator picks
style: UNKNOWN                # a Style name from data/styles.csv
palette_id: UNKNOWN           # P01 to P16
font_pairing_id: UNKNOWN      # F01 to F16
brand_colors: NONE            # existing brand hex values, if they have any
logo: NONE                    # path to the logo file, or NONE

# Trust signals, from the Local Signals column for this trade
license_number: UNKNOWN
insured: UNKNOWN
years_in_business: UNKNOWN
review_count: UNKNOWN
review_source: UNKNOWN        # Google, Yelp, Facebook

# Links
website_old: NONE             # the site being replaced, for redirects
google_business: UNKNOWN
instagram: NONE
facebook: NONE
---
```

## Sells

The result the buyer is actually paying for, in one sentence, in their words. Start from the
`Buys This Result` cell for this trade in `data/trades.csv`, then make it specific to this
business.

> UNKNOWN

## Never say

Words and claims that are wrong for this business. Start from the `Never Sell This` cell for
the trade, then add anything the owner hates. This list is as load-bearing as the one above.

- UNKNOWN

## Customer

Who they are, where they live, and what they are worried about when they land on the page.
Two or three sentences. No personas, no invented names.

> UNKNOWN

## Services

Three to six. Each one gets a name the customer would use, a one-line description, and a
price or a band. If pricing is genuinely not possible, write `quote only` and say why.

| Service | What it does for them | Price |
|---|---|---|
| UNKNOWN | UNKNOWN | UNKNOWN |

## Proof

Everything real that already exists. Reviews go in verbatim, with the first name and the
neighbourhood where the client allows it. Never edit a review for grammar.

- Reviews: UNKNOWN
- Years: UNKNOWN
- Named results: UNKNOWN
- Certifications: UNKNOWN
- Recognisable customers: UNKNOWN

## Photos

Every image the build will use, and where it came from. Anything not yet supplied goes on
the blocker list, not into a placeholder.

| Slot | File | Source | Status |
|---|---|---|---|
| Hero | UNKNOWN | UNKNOWN | missing |
| Owner portrait | UNKNOWN | UNKNOWN | missing |
| Work 1 before | UNKNOWN | UNKNOWN | missing |
| Work 1 after | UNKNOWN | UNKNOWN | missing |
| Open Graph | UNKNOWN | UNKNOWN | missing |
| Favicon | UNKNOWN | UNKNOWN | missing |

## Tone

How this business talks. One line, plus two sentences they would say and one they never
would. Take the sentences from a real message, review reply, or voice note if you have one.

> UNKNOWN

## Blockers

What the build is waiting on, and who owes it.

- UNKNOWN

## Worked example

Here is the same file filled for a real shape of business. Use it as the standard for how
specific each field has to be.

```yaml
---
name: North Shore Drain and Plumbing Ltd.
short_name: North Shore Plumbing
trade: Plumbing
shape: local-service
tagline: A working drain today, at a price agreed before we leave.
city: North Vancouver
region: British Columbia
country: Canada
address: 1420 Pemberton Ave, North Vancouver
service_area: North Vancouver, West Vancouver, Lions Bay, Deep Cove
timezone: America/Vancouver
phone: (604) 555-0142
phone_tel: "+16045550142"
email: office@northshoreplumbing.example
booking_url: NONE
maps_url: https://maps.google.com/?cid=EXAMPLE
hours: Mon to Fri 7am to 6pm, Sat 8am to 2pm
emergency_hours: 24 hours for burst pipes and no hot water
money_action: call
money_action_label: Call now
price_display: band
deposit_terms: NONE
style: Local Trust
palette_id: P11
font_pairing_id: F11
brand_colors: NONE
logo: /brand/nsp-logo.svg
license_number: BC TQ 44821
insured: Yes, 2M liability
years_in_business: 19
review_count: 412
review_source: Google
website_old: https://northshoreplumbing.example
google_business: https://g.page/example
instagram: NONE
facebook: NONE
---
```

Sells: a drain that works tonight, quoted before the truck leaves the driveway.

Never say: camera equipment specs, truck stock lists, "your trusted plumbing partner".

Customer: homeowners in North and West Vancouver, most of them over forty, calling because
something is already leaking. They are worried about being charged whatever the plumber
feels like once the work has started.

Tone: short, calm, no upselling. They say "we will tell you the price first" and "we can be
there before noon". They never say "premium" or "solutions".
