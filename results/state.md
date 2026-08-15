# Fetch-health state
<!-- Contract (see CLAUDE.md "Memory files" + "Fetch rules"): read before
     any network call; update at end of run. Craigslist is probed every
     run; other blocked domains get ONE recovery probe per week. -->

## Egress status
- EGRESS_BLOCKED at the network proxy (not site bot-detection) observed
  2026-08-14 for ALL listing domains: craigslist, zumper, redfin, zillow,
  hotpads, apartments.com, and every PM site attempted. Flagged to owner —
  fix is in the claude.ai cloud environment's network allowlist
  (env_01X8mXvPBM7u6pBz3odWEPi4): allow sfbay.craigslist.org,
  www.craigslist.org, www.zumper.com, and the PM-site domains.
- Until the probe succeeds, scheduled runs operate in SEARCH-ONLY mode.

## Never direct-fetch (bot-block 403s even when egress is open)
- zillow.com (403: 2026-08-10, 08-14 ×2)
- redfin.com (403: 2026-08-10, 08-14 ×2)
- hotpads.com (403: 2026-08-10, 08-14)
- apartments.com (403: 2026-08-14 ×2)

## Probe log
- 2026-08-14: sfbay.craigslist.org → EGRESS_BLOCKED (scheduled-run network)
- 2026-08-15 15:07 UTC: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled 8am-window run). Whole run ran search-only per Fetch rules. Blocker persists 2 days running — still needs the network-allowlist fix flagged 08-14.
