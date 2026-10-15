# graiphdeals-content

Guides (`guides/<slug>.md`) and manual deals (`manual-deals.yaml`) for graiphdeals.

## Publishing

Open a PR against `main`. Once the `content-lint` check is enabled, it runs the
API's own `python -m graiphdeals_api.authoring check --guides-dir guides --manual-file manual-deals.yaml`
inside the deployed API image and must pass. Merge to `main`. The next ingest run
(daily, or an ad hoc ingest Job) reads `main` HEAD. No app release is needed.

## Contract

The frontmatter contract and editorial rules live in
[graiphd/graiphdeals](https://github.com/graiphd/graiphdeals):
`apps/api/content/README.md` and the `guide.schema.json` it publishes.

- The filename stem must equal the frontmatter `slug`.
- No prices, discounts or merchant links in guide bodies.
- New frontmatter keys can only be used once every environment runs an API
  release that accepts them (the parser rejects unknown keys).
- Only real, page-verified content belongs here. This repository is public.
