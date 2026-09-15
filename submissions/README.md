# Data submissions

Add a dated, descriptive JSON, YAML (.yaml or .yml), or static HTML data-table file to this folder in your fork, then open a pull request. Files here are proposed observations pending review, not accepted or verified research snapshots. Existing curated datasets remain in data/.

Include restaurant_name and branch_address (or the economic asset/series), observed_at, the original value and unit, currency when relevant, source_url or source description, collection method, and limitations. Menu observations should include the order price, wing quantity/type, and tax/fee scope. Use null or blank for missing information; never invent zeros. Retain original scales, source values and branch uncertainty.

Use valid JSON records or arrays; YAML should use spaces for indentation and quoted dates, with no executable tags or custom objects. For HTML, supply only a static table with a caption, headers, one observation per row, source links, and scope notes. Do not include scripts, forms, styling, tracking or a whole webpage. A data table is not a website contribution.

Name files using an observation/collection date and topic, such as YYYY-MM-DD-restaurant-menu.json. For a correction, identify the affected existing file/record and explain the change in the pull request. Include new data documentation as needed; maintainers will reconcile curated snapshot manifests during review.

Do not submit full third-party articles or reviews, personal information, private conversation links, credentials, account exports, or website files. Identify source ownership and contribute only material you can share under the repository's license and third-party scope.

The [WingMath Submit page](https://wingmath.com/submit) has format examples and a document-upload option for CSV, Excel, and text files, plus a public video-link form. These site submissions are held for review and do not automatically appear in this repository.
