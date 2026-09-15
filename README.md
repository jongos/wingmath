# WingMath data

**Tracking the Wingconomy. Economics, Extra Sauce.**

For centuries, civilization attempted to understand itself through gold, oil and the gross domestic product. An understandable detour. None of those things comes with blue cheese.

[WingMath](https://wingmath.com) is a database-backed research project exploring chicken wings through restaurant evidence, customizable rankings, menu prices and economic comparisons. It began with Jon’s wing experiment: a provisional shortlist, a methodology and an appetite that had become administratively complicated. It has grown into a shared collection of observations, sources and assumptions that anyone can inspect and help improve.

> One wing, indivisible. A ten piece for all!

## Saucy Wing Science, Jumbo Data

**Wing science** powers customizable national rankings, state exploration and ATL 10. It brings together restaurant and reviewer evidence, editorial coverage, cultural history, social visibility and search demand, while letting visitors choose their own priorities. The goal is to make the evidence—and the role of personal taste—visible.

**Wingonomics** uses the chicken wing as a unit for exploring prices and purchasing power. The Wing Index establishes an experimental price-per-wing benchmark from an expanded menu sample, with equal weight for each eligible restaurant. That shared denominator powers comparisons across stocks, Crispy Crypto and Wingflation, alongside restaurant-price research.

Our founding proposition is audacious: a wing can be both delicious and divisible. Divide its menu price by its count and a unit price emerges. Divide again by a regional price index and the napkin becomes a research instrument. Put the result in a serif typeface and the institution is essentially complete.

The humor is deliberate; the distinctions in the data matter. Missing evidence remains missing. Uncollected reviews do not become praise. Unobserved prices do not become zero. Model-coded taste signals are labeled provisional. A broader menu sample does not mean we have measured every American restaurant.

Good wings deserve attention. Big claims deserve evidence. We intend to consume a concerning amount of the former while steadily improving the latter.

Explore the [website](https://wingmath.com), read [About WingMath](https://wingmath.com/about), or inspect [how the methods work](https://wingmath.com/how-it-works).

## What this repository contains

This repository contains dated CSV and JSON data snapshots, research annotations, source references, and data documentation. The website, application code, deployment configuration, database credentials, assets, and website Git history are maintained separately. This is an open-data project; the website software is not licensed by this repository.

## Initial edition: 2026-09-15

| Dataset | Coverage |
| --- | --- |
| Restaurant catalog | 1,380 candidates, plus the original 50 identities |
| Reviewer evidence | 89 visits; 87 scored and 2 N/A; 1,403 suggestion groups |
| Menu observations | 6 order prices, with quantities and branch notes |
| State economics | Regional price parities and population for 50 states + DC |
| Equity quotes | 502 dated stock observations |
| Crispy Crypto | 25 source-ranked crypto assets |
| Inflation inputs | Original monthly CPI files and 47 annual inputs, 1979–2025 |
| ATL 10 | 19 contenders, editorial/review evidence, and 42 coded discussion records |
| Social visibility | 76 searches: 64 observed, 12 blocked; 14 complete restaurants |
| Search demand | 50 keywords: 39 supplied averages, 11 missing |

Start with [data/2026-09-15](data/2026-09-15), the [data dictionary](DATA_DICTIONARY.md), and the [manifest](manifest.json). The manifest records file counts, hashes, source links, and the distinction between observations, normalized identities, aggregates, and analyst annotations.

## Using the data

- CSV files use UTF-8 and a header row. Empty cells and JSON `null` mean missing, never zero. Arrays in CSV cells use JSON encoding.
- Values preserve their recorded units and numeric precision. Dollar market quotes are included as inputs; calculated wing conversions and final WingMath rankings are excluded.
- `restaurants/` is a normalized catalog rather than a verified branch directory. Preserve IDs and branch qualifications when joining records.
- `annotations/` contains provisional analyst coding, not measured restaurant quality. Social attention, reviews, cultural documentation, and search demand measure different things.
- Snapshots are dated observations, not live feeds. This initial edition was extracted from the saved dataset artifacts used to populate WingMath’s database, not a fresh crawl or a live SQL backup.
- Source retrieval times and quote/observation times are different. A missing timestamp remains missing. The displayed crypto source ranks and reviewer ranks are original source fields, not generated WingMath rankings.

## Reuse and contributions

WingMath’s original contributions are available under [CC BY 4.0](LICENSE.md), with third-party materials identified separately. Cite WingMath, the snapshot date, this repository, and the original sources relevant to your use.

See [CONTRIBUTING.md](CONTRIBUTING.md) to submit corrected or newly collected data. This repository is a versioned research snapshot; committing data here does not automatically update the production database.

## Expanded menu edition and database mirror

The expanded menu edition contains **29 eligible restaurant prices across 25 states and D.C.**, plus three excluded quotes. See [expanded-menu.json](data/2026-09-15/prices/expanded-menu.json) for the source prices and eligibility decisions. The original six-price snapshot remains unchanged.

The [database synchronization workflow](.github/workflows/sync-data.yml) checks for curated public-data changes once daily at 12:00 UTC (8 a.m. Eastern daylight time / 7 a.m. Eastern standard time). Its latest successful output is stored under `data/current/`; Git history preserves earlier snapshots. See [SYNC.md](SYNC.md) for the field allowlist, privacy exclusions, timing limits and failure behavior. Website source is not included.
