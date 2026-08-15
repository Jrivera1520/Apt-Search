# PM-site rotation state
<!-- Contract (see CLAUDE.md "Memory files"): each run checks the 2-3
     STALEST non-dead rows (never-checked sort first), then updates
     last-checked + status + note. EGRESS_BLOCKED does NOT advance
     last-checked. 3 consecutive dead/not-SF checks -> flag to Joel as a
     removal candidate. Statuses: never-checked / ok / 0-inventory /
     luxury-only / no-3br / dead-url / js-only / wrong-company / not-SF -->

| site | listings URL | last checked | status | note |
|---|---|---|---|---|
| Show Mojo | (find via search) | — | never-checked | |
| RNB | (find via search) | — | never-checked | |
| Luminor SF | (find via search) | — | never-checked | |
| Progressive | (find via search) | — | never-checked | |
| West Coast Property Management | (find via search) | — | never-checked | |
| BanCal | (find via search) | — | never-checked | |
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
