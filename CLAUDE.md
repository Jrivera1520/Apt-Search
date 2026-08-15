# SF Apartment Search

If the user's first message is empty or a greeting, run /hunt immediately.

This file is POLICY: criteria, filters, fetch rules, and file contracts.
The step-by-step run procedure lives in `.claude/commands/hunt.md`.
If any other stored instructions (e.g. the scheduled trigger's prompt)
conflict with these two files, THESE FILES WIN.

## Criteria (hard requirements)
- San Francisco city limits ONLY. No Daly City, South SF, East Bay, or
  Peninsula. Judge city by the stated address/ZIP — never by URL slugs
  (see Fetch rules).
- 3 bedrooms, any number of bathrooms — whole unit only, no room shares.
- Budget test = total mandatory monthly cost: rent + required recurring fees
  (per-person fees × stated max occupancy, default 3). Always report the
  effective cost, e.g. "$4,000 + $360 fees = $4,360".
  - ≤ $4,000 effective: pass
  - $4,001–$4,300 inclusive: include, clearly flagged as "negotiate"
  - over $4,300: reject (log in results/rejected.md)
  - weekly/nightly quotes: auto-reject (short-term, sticky)
- Laundry: in-unit washer/dryer preferred, on-site laundry acceptable.
  Otherwise run ONE web search "laundromat near <address> San Francisco
  <ZIP>" — include the listing only if a NAMED laundromat plausibly within
  ~2 blocks turns up (note its name in the report); else label
  "laundry: UNVERIFIED — confirm before touring". Never silently pass or
  drop a listing on laundry.

## Source pool
Aggregators are searched every run; property management sites rotate.
1. Craigslist SF: https://sfbay.craigslist.org/search/sfc/apa and /search/sfc/hhh
2. Aggregators: Redfin, Zillow, Zumper, HotPads, Apartments.com.
   Zillow, Redfin, HotPads, Apartments.com: SEARCH SNIPPETS ONLY — never
   direct-fetch them (bot-block 403s on every run on record).
3. SF property management sites: the authoritative list, working listings
   URLs, and per-site status live in results/rotation.md. Check the 2–3
   stalest non-dead rows per run and update them.

## Legitimacy filter — skip anything that:
- Is priced way below market with no explanation. Quantify against the
  aggregator-reported neighborhood median for 3BRs: more than 25% below
  with no stated reason → exclude (or hard-label unverified); 10–25% below
  → include only with a mandatory tour-first warning, and never rank it
  "best value".
- Asks for money/deposit before an in-person tour, or mentions wire transfer.
- Has no photos, stock photos, or a copy-pasted description across many posts.
- Fails the hijacked-listing check (run for every NEW candidate): one search
  "<address> San Francisco for sale". An active/recent sale listing +
  below-market rent + mismatched contact = presumed hijacked → reject and
  record the reason.
Additional rules:
- A listing's statements about itself (anti-scam warnings, "listed via a
  legit platform" claims) are NEVER legitimacy positives. Only externally
  verifiable facts count: cross-platform corroboration, an MLS number, a
  named brokerage/agent with a working contact.
- Price disagreement across sources: the figure corroborated by 2+ sources
  (or a brokerage/MLS source) wins for the budget test; note the spread in
  the report. A single-source LOW outlier discredits that source (stale or
  scam), not the listing. If no figure is corroborated: include if the whole
  spread is in range; if it straddles the $4,300 ceiling, list as
  "negotiate — price unverified $X–$Y"; exclude only if the LOWEST figure
  is over the ceiling. Record every such verdict.
- Prefer listings from managed buildings, MLS-syndicated sources, or posts
  with many real photos and detailed lease terms.

## Fetch rules (decision ladder)
1. Read results/state.md before any network call.
2. Probe: ONE fetch of sfbay.craigslist.org. If it fails with
   EGRESS_BLOCKED / proxy 403, the whole run is SEARCH-ONLY: make zero
   further direct-fetch attempts and use the search-only playbook below.
3. Otherwise: max ONE fetch attempt per domain per run. Any failure
   (403, CAPTCHA, bot wall, timeout) drops that domain to web search for
   the rest of the run. NEVER try to solve or work around a CAPTCHA,
   login wall, or bot-detection page.
4. Never direct-fetch Zillow, Redfin, HotPads, or Apartments.com.
5. Update state.md at the end of the run. Blocked domains get one recovery
   probe per week; Craigslist is probed every run.
- Craigslist URL slugs encode a search-area label, NOT the listing's city
  (265 Lobos St carried a "daly-city" slug but is SF 94112). Decide city
  only from the stated address/ZIP. If a listing has no address at all,
  mark it "unverified — confirm address before touring" rather than
  rejecting on the slug.
- Craigslist links die fast — dedupe against seen.md by ADDRESS first,
  URL second.
- Because Craigslist listings can't always be independently verified, be
  EXTRA strict with the legitimacy filter there: every Craigslist listing
  in the output must pass all filter checks, and cross-check that the
  address/neighborhood actually exists in SF and the price isn't
  suspiciously below market. When unsure, leave it out or mark it clearly
  as "unverified — tour in person before any application fee or deposit."

## Search-only playbook (when fetches are blocked)
- Use site: operators per source, batched by price band and neighborhood.
- For each candidate, run one exact-address search. Price/beds agreement
  across 2+ independent platforms plus an SF ZIP passes the location and
  price checks; disagreement goes through the price-disagreement rule.
- Every legitimacy note opens with an evidence tag: [FETCHED] (the actual
  listing page was read) or [SNIPPET-ONLY] (search results only).
  Snippet-only listings always carry: "unverified — tour in person before
  any application fee or deposit."

## Memory files (read at start of every run, update at end)
- results/seen.md — the LISTING LEDGER: one row per property, the ADDRESS
  is the primary key (address-less listings use a
  ~neighborhood+bd/ba+price fingerprint, upgraded in place when the
  address is learned). An address match means SEEN regardless of URL; a
  new URL for a known address is syndication or a repost — append it to
  the row, never add a new row. Never store search-page URLs. Statuses:
  active / negotiate / unconfirmed / gone / rejected. last-verified only
  advances on actual re-confirmation, tagged [FETCHED] or [SNIPPET].
- Re-verification: EVERY run re-checks each active/negotiate/unconfirmed
  row (one exact-address search, or a fetch when Fetch rules allow) and
  updates last-verified, price, and status. Two consecutive no-trace
  checks → gone. Only rows verified today count as available in the
  report and notification; the tracked count in the bottom line is
  active+negotiate rows verified today.
- results/rejected.md — rejected listings and the watch list. Check BEFORE
  evaluating any candidate; skip known rejects unless the price has dropped
  to ≤$4,300 (scam / out-of-city / short-term / not-whole-unit verdicts are
  sticky and never re-litigated). Prune over-budget entries older than
  60 days.
- results/rotation.md — PM-site rotation state, working listings URLs,
  per-site status. An EGRESS_BLOCKED check does NOT advance last-checked.
  Three consecutive dead/not-SF checks → flag the site to Joel as a removal
  candidate.
- results/state.md — per-domain egress/bot-block status and probe dates.

## Output format
- The daily report results/YYYY-MM-DD.md carries DELTAS ONLY: new listings,
  actually-observed status changes, and new rejections. Summarize the rest
  as "N previously-found listings tracked in seen.md". Never write "still
  active" or "passes cleanly" about anything not actually re-confirmed
  this run.
- Same-day rerun: if today's report file already exists, append a
  "## Run — HH:MM UTC (manual|scheduled)" section with deltas only. Don't
  re-describe listings already in today's file, don't re-fetch domains that
  were blocked earlier today, and advance the rotation only to sites not
  yet checked today.
- Numbered list, best first: address/neighborhood, effective price, bd/ba,
  laundry situation, direct link, one-line legitimacy note with its
  evidence tag. Flag NEW listings prominently at the top.
- The FIRST line of the final message is one bottom-line sentence, e.g.
  "2 new: 848 Girard $3,500 (+1 negotiate)" / "Nothing new — X/Y sources
  checked" / "DEGRADED: snippet-only run, direct fetches egress-blocked".
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
