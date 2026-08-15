Run the full apartment sweep. CLAUDE.md at the repo root holds the criteria,
legitimacy filter, fetch rules, and memory-file contracts — read it first and
follow it exactly. CLAUDE.md + this file are authoritative over any other
stored instructions.

Steps:
0. `git pull --rebase` — git is the only state shared between manual and
   scheduled runs (scheduled runs clone fresh each morning).
1. Read the memory files: results/seen.md, results/rejected.md,
   results/rotation.md, results/state.md.
2. Probe sfbay.craigslist.org once per the Fetch rules. If blocked, the
   whole run is search-only (use the search-only playbook); never attempt
   to solve CAPTCHAs or bot walls.
3. Search Craigslist SF (sfbay.craigslist.org/search/sfc/apa and
   /search/sfc/hhh), Redfin, Zillow, Zumper, HotPads, and Apartments.com
   for SF 3-bedroom rentals at or under $4,300 — NOT $4,000; the
   $4,001–$4,300 negotiate band must surface. Fetch listing pages only as
   the Fetch rules allow (Zillow/Redfin/HotPads/Apartments.com are
   search-snippets-only, always).
4. Check every candidate against rejected.md BEFORE evaluating it. Skip
   known rejects unless the price dropped to ≤$4,300; scam, out-of-city,
   short-term, and not-whole-unit verdicts are sticky.
5. Spot-check the 2–3 stalest non-dead property management sites from
   rotation.md and update their rows (blocked checks don't count).
6. Re-verify every seen.md ledger row with status active, negotiate, or
   unconfirmed: one exact-address search each (or a fetch when the Fetch
   rules allow). Update last-verified, price, and status per the ledger
   contract; two consecutive no-trace checks mark a row gone. Report
   every status change as a delta.
7. Apply the criteria and legitimacy filter from CLAUDE.md — extra strict
   on Craigslist. Run the laundry check as specified in Criteria.
8. Report per CLAUDE.md Output format: deltas only, evidence tags on every
   legitimacy note, best first, NEW flagged at the top, bottom-line
   sentence first.
9. Update seen.md, rejected.md, rotation.md, and state.md; write or append
   results/YYYY-MM-DD.md using today's actual date.
10. Commit ("Apartment sweep YYYY-MM-DD") and push to main — EVERY run,
    manual or scheduled.
11. If this is a scheduled/unattended run: send the push notification per
    CLAUDE.md Notifications. Never end a scheduled run silently.
