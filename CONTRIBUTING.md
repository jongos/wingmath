# Contributing data

Submit a pull request with CSV or JSON observations and source metadata. Include the collection date, source URL, units, restaurant/branch identity, and the method used to obtain the value. Use a new dated snapshot for a new observation period. Record corrections explicitly instead of silently changing historical observations.

Keep stable restaurant IDs where identity is established. Flag uncertain branches and aliases. Use null/empty for missing data and preserve blocked/unavailable statuses. Keep measured observations separate from analyst assessments, estimates, and aggregate inputs. Preserve source values before deriving any new measure.

Update manifest file hashes, record counts, and the data dictionary when fields change. For CSV, count data rows excluding the header; for JSON arrays count top-level records. Metadata objects have a null record count. Hash the complete UTF-8 file bytes using SHA-256.

Contribute only data you are authorized to share. Include source attribution and identify any third-party rights. Original contributions are submitted under the license in LICENSE.md.

Keep website code, HTML/CSS/JavaScript, generated rankings, media, credentials, account identifiers, private conversation links, database backups, and deployment configuration out of this repository. Please do not include reviewer usernames or full comment text. The repository allowlist is an aid, not a replacement for reviewing every changed file.
