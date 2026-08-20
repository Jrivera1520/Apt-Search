# PM-site rotation state
<!-- Contract (see CLAUDE.md "Memory files"): each run checks the 2-3
     STALEST non-dead rows (never-checked sort first), then updates
     last-checked + status + note. EGRESS_BLOCKED does NOT advance
     last-checked. 3 consecutive dead/not-SF checks -> flag to Joel as a
     removal candidate. Statuses: never-checked / ok / 0-inventory /
     luxury-only / no-3br / dead-url / js-only / wrong-company / not-SF -->

| site | listings URL | last checked | status | note |
|---|---|---|---|---|
| Show Mojo | (find via search) | 2026-08-15 | wrong-company? | ShowMojo is leasing/listing-syndication software used by many independent landlords, not a single distinct SF property manager — no SF-specific 3BR inventory found under that name. Flag to Joel: likely a data-entry error, replace with an actual named SF landlord/PM or remove |
| RNB | rnbrentals.com/search-rentals.php | 2026-08-20 | no-3br | re-check 08-20 (search-only): still Sacramento/San Joaquin/Bay Area focus, no distinct SF-city 3BR surfaced. Direct fetch of search-rentals.php still recommended once egress recovers before concluding 0-inventory |
| Luminor SF | luminorsf.com/availability | 2026-08-20 | 0-inventory | re-check 08-20 (search-only): availability page returned 0 results this check — no 3BR. Real SF PM (1792 26th Ave, 415-980-8686) |
| Progressive | progressivesf.appfolio.com/listings | 2026-08-20 | no-3br | re-check 08-20 (search-only): AppFolio listings page shows 2-3BR Noe Valley inventory but no confirmable 3BR price via search; needs a direct fetch of progressivesf.appfolio.com/listings once egress recovers |
| West Coast Property Management | wcpm.com | 2026-08-16 | js-only | search-only check surfaced no site-specific listings (site: query returned generic aggregator results) — likely JS-rendered listings page; needs a direct fetch once egress recovers before concluding inventory |
| BanCal | bancalsf.com/availability | 2026-08-16 | no-3br | one 3BR found: 348 Hyde St, Unit 11, 94109, 3bd/2.5ba, $4,500/mo — over the $4,300 ceiling, rejected (see rejected.md) |
| RMC | rmcsf.com/rentals-1 | 2026-08-17 | no-3br | real SF PM firm (est. 1980, 1234 Castro St, 550+ units) — search-only check of rentals-1 page surfaced no current 3BR listing; needs a direct fetch once egress recovers to confirm inventory |
| Leading SF | leading-sf.com/rental-search/ | 2026-08-17 | js-only | real SF brokerage/PM (1801 Van Ness Ave) — rental-search page is JS-rendered, search snippets returned no listing data |
| Rental Source | rentalsource.com/san-francisco-ca | 2026-08-17 | wrong-company? | rentalsource.com is a nationwide listing aggregator (444 SF rentals, avg 3BR $7,138 = market aggregate, not owned inventory), not a distinct SF property manager — same pattern as ShowMojo. Flag to Joel: likely a data-entry error, replace with an actual named SF landlord/PM or remove |
| HSM | hsmsf.com/projects-8 | 2026-08-18 | no-3br | real SF PM company (600 Haight St, since 1954, 360+ units) — search-only check of rentals page (projects-8) surfaced no current 3BR listing; needs a direct fetch once egress recovers to confirm inventory |
| Gateway Management | gatewaymanagementandrealty.com/rentals/ | 2026-08-18 | no-3br | real SF-focused firm (est. 1980, income-property specialist) — do NOT confuse with "The Gateway" luxury complex at 460 Davis Ct (different company, thegateway.com); search-only check of rentals page surfaced no current 3BR listing, needs direct fetch to confirm |
| Utopia Management | utopiamanagement.com/rental-list/san-francisco-bay-area | 2026-08-18 | not-SF | real regional PM company but SF office is in South San Francisco (611 Gateway Blvd) and current rental-list results were all outside SF proper (Vallejo, Petaluma, Live Oak, Lawndale) — no SF-city inventory surfaced |
| GoFiveStarPM | gofivestarpm.com/san-francisco-property-management | 2026-08-19 | js-only | real Bay Area PM firm managing SF properties (confirmed via 2420 Taraval St listing, 650-435-5906) but no dedicated SF listings/inventory page surfaced via search — likely needs a direct fetch once egress recovers |
| Trinity | trinitysf.com | 2026-08-19 | ok | real SF apartment operator, multiple buildings with 3BR floorplans (215 Upper Terrace/Buena Vista, 1177 Market/SoMa, 1000 Chestnut/Russian Hill, 2000 Broadway/Pac Heights, 6720 Fulton/Richmond) — 215 Upper Terrace shows 3BR "starting at $3,499" (unconfirmed exact unit price), added to seen.md as unconfirmed |
| Relisto | relisto.com | 2026-08-19 | luxury-only | most 3BRs $4,295-$5,895 (Presidio Heights/Pac Heights/SoMa); one lower find, 55 Junior Terrace Dr (Mission Terrace) $4,800, still over ceiling — rejected |
| Mosser | (dead — find new URL) | 2026-08-14 | dead-url | old listings URL 404s since site restructure; needs new URL before next check counts |
| Rentals in SF | rentalsinsf.com | 2026-08-14 | dead-url | listings sub-page 500'd on 08-14; retry, else flag |
| Rent SF Now | rentsfnow.com | 2026-08-14 | js-only | listings behind interactive filters, no static data |
| J. Wavro Associates | jwavro.com | 2026-08-14 | luxury-only | 3BRs at $9k/$12k both checks |
| Gaetani Real Estate | gaetanirealestate.com | 2026-08-14 | 0-inventory | 0 vacancies on both checks |
| Brick + Timber | brickandtimber.com | 2026-08-14 | no-3br | |
| ZipRent | listings.ziprent.com | 2026-08-14 | js-only | inventory lives at listings.ziprent.com, not the marketing site; JS-rendered |
| Golden Gate Properties | (verify) | 2026-08-14 | wrong-company? | resolved to "G2 Properties" ($7,950 Sunset 3BR); verify the intended company |
| SF Bay Rental Co | sfbayrentalco.com/properties/available | 2026-08-14 | luxury-only | 3BRs $11,800+ |
| Chandler Properties | chandlerproperties.appfolio.com/listings | 2026-08-14 | no-3br | |
| Cybus Management | cybus.appfolio.com/listings | 2026-08-14 | 0-inventory | vacancies page showed 0 of 0 |
| Key Opp | keyopp.managebuilding.com | 2026-08-14 | 0-inventory | 0 active listings per Dwellsy |
| Amsires | amsires.appfolio.com/listings | 2026-08-14 | luxury-only | closest 3BR $4,650 (rejected) |
