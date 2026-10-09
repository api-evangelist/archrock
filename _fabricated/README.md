# Quarantined — API Evangelist authored, NOT published by Archrock

Everything in this directory was **written by API Evangelist tooling**, not harvested from
Archrock. It is kept for audit history and deliberately held outside the artifact directories
so it can never be indexed, scored, or read as a provider-published contract. Moved here
2026-09-26 (roadmap#725, Kin's decision 14 of 2026-09-26).

## What it is

`openapi/_original/archrock-investor-relations-api.yaml` is an OpenAPI 3.0.3 "Archrock Investor
Relations API" (5 operations: quarterly financials, fleet statistics, equipment, operational
metrics, SEC filings) written by the 2026-05-04 bulk scaffold pass. The refine pass later split it
into four per-tag files (Financials, Fleet, Operations, SEC Filings), and `apis.yml` listed each as
an Archrock API. Every other file here was generated from that spec:

- `collections/` — Postman and OpenCollection files (derived from the per-tag specs)
- `examples/`, `json-schema/`, `json-structure/`, `json-ld/` — the spec's invented schemas and examples
- `rules/` — Spectral rulesets "measured from this provider's own OpenAPI conventions"
- `vocabulary/`, `capabilities/` — vocabulary and capability edges read off the invented operations
- `agentic-access/`, `authentication/` — already self-labelled "SCAFFOLD-DERIVED, NOT PUBLISHED"

## Verification that no Archrock API exists

| Check | Result (2026-09-26) |
|---|---|
| `api.archrock.com` (the spec's only server) | NXDOMAIN, no DNS record |
| `https://www.archrock.com/sitemap.xml` | 200, 41 URLs, none a developer, API or docs page |
| `https://www.archrock.com/aroc-investor-relations/` | 200, an investor-relations web page, no endpoints |

See `../apis.yml` -> `x-fabrication` and `x-coverage`.

The real programmatic source of Archrock data is the SEC: `https://data.sec.gov/submissions/CIK0001389050.json`
returned 200 JSON for "Archrock, Inc." (AROC). It is listed in `apis.yml` as a third-party
government API.

**Do not restore these files.** If Archrock ever publishes a real API, harvest it verbatim.
