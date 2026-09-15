# WingMath data

Data behind WingMath’s **wing science** (restaurant evidence) and **wingonomics** (prices and economic comparisons).

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
