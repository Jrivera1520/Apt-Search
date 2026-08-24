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
- 2026-08-16: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 3 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied.
- 2026-08-17: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 4 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied.
- 2026-08-18: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 5 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied.
- 2026-08-19: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 6 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied.
- 2026-08-20: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 7 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied. NOTE: despite egress block, search-only surfaced 2 strong NEW verified finds this run (225-227 Chenery St $3,950, 775 Post St #403 $4,000).
- 2026-08-21: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 8 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied. NOTE: search-only surfaced 1 NEW verified find (32 Coso Ave, Bernal Heights, $3,850, MLS-corroborated + Brown & Patki brokerage).
- 2026-08-22: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 9 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied. Also confirmed EGRESS_BLOCKED this run: keyopp.managebuilding.com, brickandmortarsf.com, app.tenantturner.com. NOTE: no new fully-verified listing this run; one unpriced KeyOpp lead (251 27th Ave) added unconfirmed; 3 tracked rows got first-time no-trace/off-market signals (775 Post St #403, 3624 San Bruno Ave, 215 Upper Terrace); a candidate address for the long-tracked address-less Bayview $3,600 post ("300 Klamath St") was investigated and ruled out — that address resolves to Brisbane, CA 94005, not SF.
- 2026-08-23: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 10 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied. NOTE: 2 new verified/partially-verified listings added (59 Dorado Terrace $3,850 unconfirmed, 1830 Alemany Blvd #301 $4,150 negotiate — verified via Atlas Property Group); the two prior no-trace flags on 775 Post St #403 and 3624 San Bruno Ave both cleared on re-check (both re-surfaced normally); 215 Upper Terrace hit its 2nd consecutive no-fresh-price signal and was marked gone (building itself still operating, just this quoted rate unconfirmed).
- 2026-08-24: sfbay.craigslist.org → EGRESS_BLOCKED again (scheduled run). Whole run ran search-only per Fetch rules. Blocker persists 11 days running — network-allowlist fix (env_01X8mXvPBM7u6pBz3odWEPi4) still not applied. NOTE: 2 new verified listings added (813 Meade Ave, Bayview, $4,000 unconfirmed; 135 Maddux Ave, Silver Terrace, $4,200 negotiate — verified via Corcoran brokerage); 2420 Taraval St #2's long-unresolved price finally isolated at $3,495, but its MLS listing now shows status "Closed" — first no-trace/off-market signal logged; re-verified all 19 active/negotiate/unconfirmed ledger rows via exact-address search, all still present with no other material changes; 3 PM sites spot-checked (SF Bay Rental Co, Amsires, BanCal) — Amsires' cheapest 3BR now $4,995 (824 Brazil Ave, rejected), others unchanged; 3 candidate leads (Mission furnished 3BR $3,900, Ingleside/CCSF $4,200, 418 Athens St) could not be verified to a confirmed address/unit and were logged in rejected.md as insufficient-data rather than added to the ledger.
