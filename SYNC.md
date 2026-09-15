# Public database synchronization

Public repository: https://github.com/jongos/wingmath
Website source is maintained separately. Never add the public repository as a push destination for the website checkout.

The public repository's `.github/workflows/sync-data.yml` checks `/api/public-data` once daily at 12:00 UTC (8 a.m. Eastern daylight time / 7 a.m. Eastern standard time), with manual dispatch available when needed. It commits a new `data/current/database.json` only when the curated payload changes. Git history preserves previous versions. This is a periodic mirror, not an instantaneous database transaction hook; scheduled jobs can be delayed by GitHub. Changes between checks can be coalesced. A failed download or validation leaves the last good snapshot unchanged and fails the workflow visibly.

The endpoint reads an explicit set of scalar fields in one SQLite statement. Submissions, uploaded files, storage keys, rate-limit buckets, contact details, Reddit account names, free-form JSON blobs, credentials, and website code are excluded. The workflow independently checks the table/column allowlist and rejects common credential patterns. Updating public export fields requires a reviewed schema change in both repositories. Existing source datasets and contribution templates are retained.

`data/current/manifest.json` records the successful retrieval time, counts and SHA-256. The workflow uses GitHub's short-lived GITHUB_TOKEN with repository contents-write permission; no personal token is stored on the website. Contributors' pull requests do not trigger the export workflow. The public repository is an outbound mirror; proposed observations are reviewed before importing into production.

After any authorized research import or database edit, verify the next workflow succeeds and the public manifest reflects the change. Never claim synchronization succeeded based solely on a local fixture. Hosting access controls can block automated retrieval; resolve that through the provider's supported configuration rather than bypassing it or exporting private credentials.
