# SF Apartment Search

If the user's first message is empty or a greeting, run /hunt immediately.

## Criteria (hard requirements)
- San Francisco city limits ONLY. No Daly City, South SF, East Bay, or Peninsula.
- 3 bedrooms, any number of bathrooms
- $4,000/month or under (flag anything up to $4,300 as a "negotiate" option)
- Laundry: in-unit washer/dryer preferred, on-site laundry acceptable,
  otherwise must be within ~2 blocks of a laundromat (verify on the map)

## Sources to check every run
1. Craigslist SF: https://sfbay.craigslist.org/search/sfc/apa and /search/sfc/hhh
2. Redfin SF 3BR rentals, Zillow, Zumper, HotPads, Apartments.com
3. These SF property management sites: Rentals in SF, Rent SF Now, Jwavro,
   Relisto, Gaetani Real Estate, SF Bay Rental Co, Show Mojo, Chandler
   Properties, Mosser, RNB, Cybus Management, Luminor SF, Key Opp, Golden Gate
   Properties, Progressive, West Coast Property Management, ZipRent, Amsires,
   BanCal, Brick + Timber, RMC, Leading SF, Rental Source, HSM, Gateway
   Management, Utopia Management, Trinity, GoFiveStarPM

## Legitimacy filter — skip anything that:
- Is priced way below market (e.g. a $1,500 3BR) with no explanation
- Asks for money/deposit before an in-person tour, or mentions wire transfer
- Has no photos, stock photos, or a copy-pasted description across many posts
- Prefer listings from managed buildings, MLS-syndicated sources, or posts
  with many real photos and detailed lease terms

## Output format
- Numbered list, best first: address/neighborhood, price, bd/ba, laundry
  situation, direct link, one-line legitimacy note
- Compare against results/seen.md and mark anything NEW prominently
- Append new listing URLs to results/seen.md, save the full run to
  results/YYYY-MM-DD.md
- Be blunt if nothing new exists. Don't pad the list with over-budget or
  out-of-city listings unless flagged as "negotiate" options.

## Notifications (scheduled runs)
- At the end of EVERY scheduled/unattended run, send a push notification with
  the PushNotification tool — Joel wants a phone reminder every morning run,
  including empty ones. Never end a scheduled run silently.
- Found something new: lead with the best listing (address, price, link).
- Nothing new: one line, e.g. "Morning apartment sweep done — nothing new
  today, N listings still tracked."
- Run failed or sources blocked: say exactly that in the notification instead
  of skipping it.

## Fetch notes
- Craigslist links die fast; trust results/seen.md for dedupe so you don't
  chase ghosts.
- Zillow and Mosser sometimes block automated fetching — when a fetch
  bounces, lean on web search results instead of retrying.
- If a site shows a CAPTCHA, login wall, or bot-detection page: do NOT try
  to solve or work around it. Drop that source for this run, note it in the
  output ("Zillow blocked this run"), and shift the effort to Craigslist and
  the property management sites instead.
- Because Craigslist is the fallback, be EXTRA strict with the legitimacy
  filter there: every Craigslist listing in the output must pass all the
  filter checks, and cross-check that the address/neighborhood actually
  exists in SF and the price isn't suspiciously below market. When unsure,
  leave it out or mark it clearly as "unverified — tour in person before
  any application fee or deposit."
