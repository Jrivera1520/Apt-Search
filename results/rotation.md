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
| RNB | (find via search) | 2026-08-15 | no-3br | rnbrentals.com is primarily Marin/San Mateo/Sacramento-focused; no distinct current SF 3BR listings surfaced via search (site itself didn't rank). Recommend a direct fetch of rnbrentals.com/bay-area-rentals.php next time egress allows, before concluding 0-inventory |
| Luminor SF | luminorsf.com/availability | 2026-08-15 | no-3br | real SF PM company (1792 26th Ave); availability page has bed-count filters but current results surfaced were studios/rooms only (e.g. 5826 Geary Blvd #6, 0bd room) — no 3BR found this check |
| Progressive | progressivesf.com/availability | 2026-08-16 | 0-inventory | search-only check (site:progressivesf.com) found 0 3BR results on availability page; other current listings are studios/1BR/2BR in SF and Marin |
| West Coast Property Management | wcpm.com | 2026-08-16 | js-only | search-only check surfaced no site-specific listings (site: query returned generic aggregator results) — likely JS-rendered listings page; needs a direct fetch once egress recovers before concluding inventory |
| BanCal | bancalsf.com/availability | 2026-08-16 | no-3br | one 3BR found: 348 Hyde St, Unit 11, 94109, 3bd/2.5ba, $4,500/mo — over the $4,300 ceiling, rejected (see rejected.md) |
| RMC | (find via search) | — | never-checked | |
| Leading SF | (find via search) | — | never-checked | |
| Rental Source | (find via search) | — | never-checked | |
| HSM | (find via search) | — | never-checked | |
| Gateway Management | (find via search) | — | never-checked | |
| Utopia Management | (find via search) | — | never-checked | |
| GoFiveStarPM | (find via search) | — | never-checked | |
| Trinity | trinitysf.com | — | never-checked | 08-14 check hit a Central Valley namesake, not the SF company — audit against trinitysf.com |
| Relisto | relisto.com | 2026-08-10 | no-3br | in-budget options were out-of-city; SF ones $7,600+ |
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
