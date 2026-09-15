# Data dictionary

## Common conventions

Snapshot date is the folder name. An `observedAt`, `retrievedAt`, `snapshotAt`, `quoteAt`, or source-specific date refines it where the source recorded one. Times are preserved from the source; a date-only value does not imply a precise time. JSON null and blank CSV values are missing. JSON booleans use true/false; CSV arrays/objects are JSON strings.

Restaurant catalog IDs (`wing-*` and census IDs) share one namespace. ATL 10 IDs such as `local` form a separate namespace. `jonId` in reviewer visits is a provisional association to the original catalog, not verified branch identity. `sourceRow` and `rows` identify original spreadsheet rows; arrays of aliases/cities retain ambiguity rather than implying separate verified branches.

## Restaurant and reviewer fields

| File/field | Meaning |
| --- | --- |
| census: id, name, state, city, market | Stored identity; state is a postal code, including DC |
| locationStatus, evidenceStatus | Branch verification and evidence status |
| samEntryId, suggestionRows, suggestedCities | Reviewer entry link and source-row/city hints |
| seed-identities | Original 50 identity records; a subset of the catalog |
| census-sources | Restaurant ID and source label/URL objects |
| visits: id, sourceRow, name, state, region | Original reviewer visit identity and source row |
| rank, rankText, total | Reviewer’s reported rank and total out of 50; N/A remains unscored |
| appearance, meatiness, texture, sauce, experience | Reviewer’s five reported category scores, each out of 10 |
| videoOrder, wingsEaten, videoUrl | Source video sequence, reported quantity, supporting video |
| jonId, matchNote | Provisional catalog association and qualifications |
| suggestions: id, name, city, state, rows, aliases | Normalized suggestion group and all source-row references; not verified reviews |
| state-representatives | Source rank, entryId, state and sourceRow |
| regional-winners | Source region, restaurant name, state, score and sourceRow |
| heat-challenges | Source rank, sauce, name, city, state and sourceRow |

## Wingonomics inputs

| File/field | Meaning |
| --- | --- |
| menu: restaurantId, amount, quantity | Catalog restaurant, USD order total, menu-listed pieces |
| scope, unit, url, observedAt | Branch/menu scope, unit qualification, evidence and date |
| state-economics: rpp, population | Regional price parity, US=100; resident population count |
| rppYear, populationYear | Separate statistical vintages |
| equities: symbol, name, price | Source-listed security identity and USD per share |
| change, changePercent | Source-reported USD change and percentage change, not fractions |
| snapshotAt, quoteTime | Retrieval time and source quote time (unknown in this equity snapshot) |
| crypto: id, name, symbol, rank | CoinGecko ID and source market-cap rank |
| price, marketCap | USD per asset unit and circulating market cap in USD |
| change, changePercent, quoteAt, source | 24-hour price change, percent change, source quote timestamp and asset URL |
| CPIAUCNS | Monthly all-items CPI-U, not seasonally adjusted; index base 1982–84=100 |
| CUUR0000SEFV | Monthly food-away-from-home CPI, not seasonally adjusted; index base 1982–84=100 |
| annual: year, cpi, restaurantIndex | Stored annual averages used as inputs, not raw monthly observations |
| months, missingMonths | Count and explicit missing months used for the annual input |

The original FRED CSVs retain their original date field and missing-value representation. Historical national wing prices are estimates produced elsewhere from the restaurant CPI proxy; this repository does not represent them as observed prices.

## ATL 10 evidence

| File/field | Meaning |
| --- | --- |
| restaurants: id, name, area, address | Reference Atlanta identity, with qualifications in source records |
| editorial: infatuationRank, eaterIncluded | Source rank (missing if absent) and unranked-list inclusion |
| reviews: platform, stars, reviewCount | Aggregate listing rating out of 5 and source review count |
| sourceUrls, retrievalKind, observedAt | Evidence links, direct/indexed access distinction, date |
| reddit: recordId, thread, participantId | Coded record and thread-local substitute identifier; original usernames excluded |
| positive, negative | Arrays of restaurant keys supported or criticized; names outside the 19 may remain as context |
| keyword: restaurant, keyword, avgMonthlySearches, sourceRow | Assigned contender, exact supplied spelling, reported national monthly average, original workbook row |
| social: restaurant, platform, query, queryUrl | Contender, channel, exact query and search URL |
| status, sampled, results | Observed/blocked; number of sampled headings; accepted source links |
| results.position, results.url | Original result position and evidence URL; arrays can omit rejected headings |
| audit | Retained heading decisions (position, URL, title, decision, reason) where supplied |
| reportedMatchedUnits | Collector-reported accepted-unit count, where supplied; not a platform total |
| batchId, observedAt, provider, personalization, searchLocation | Per-query conditions; missing values inherit disclosed snapshot/batch metadata where applicable |
| notes, qualityFlags | Collection limitations and matching exceptions |

Google/news units are deduplicated by publisher domain, YouTube by video ID, and X by post ID. `results.length` need not equal distinct accepted units. Original and team batches differ in location and personalization confirmation. Blocked observations are not zeros. Social visibility is a bounded sample, not search demand; keyword data is a separate supplied national average. Do not add aliases or platform audiences together.

## Analyst annotations

`seed-assessments.json` preserves `features` (including crisp, juicy, heat, acclaim and any additional stored traits) with `featureStatus`, evidence notes, review-sample gaps, negative-theme research summaries and location corrections. Feature values are provisional 0–100 model coding, not measured customer scores. These records cannot establish measured national rank.

`atl10-culture.csv` holds continuity and contribution rubric codes (0–2 each), the recorded history band and supporting source IDs. It also retains `redditBranchFactor`, a branch-association model assumption. Culture coding measures documented history, not a representative sample of offline Atlantans.

## Provenance and integrity

`*-source.json`, `sources.json`, and reviewer `source.json` hold retrieval dates, providers, source links, collection conditions and limitations. Keyword provenance includes the original workbook name, sheet and SHA-256; the private workbook itself is not included. Unscored sources remain unscored. The manifest classifies each file and records its byte hash. No credentials or production connection settings are needed to use these data.
