# REA Group (rea-group)

REA Group Limited is an ASX-listed (ASX:REA) digital real estate advertising business headquartered in Melbourne, Australia and majority-owned by News Corp. It operates realestate.com.au and realcommercial.com.au, the property data and analytics brand PropTrack, the Mortgage Choice broking network, and REA India (Housing.com, PropTiger, and Makaan). REA Group's public developer surface is delivered through PropTrack, whose developer portal publishes **nine OpenAPI 3.1 service documents covering 32 operations** — address matching, property attributes and history, listings, sold transactions, automated valuations (AVM), PDF reports and suburb-level market analytics for Australia.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/rea-group/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/rea-group/refs/heads/main/apis.yml)

## Tags

- Real Estate
- Property Data
- Valuations
- AVM
- Market Insights
- Listings
- Transactions
- Address Matching
- Geospatial
- REAXML
- Partner Portal
- PropTech
- Australia

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-27

## Access

The PropTrack developer portal ([developer.proptrack.com.au](https://developer.proptrack.com.au/)) is publicly readable and fully specified, but the underlying data APIs are **partner-gated**: `https://data.proptrack.com` returns HTTP 403 without credentials. Authentication is OAuth 2.0 client credentials — an `api_key` and `api_secret` issued by an Account Manager under a commercial agreement, Base64-encoded as HTTP Basic on `POST /oauth2/token`, exchanged for a JWT bearer token with a 3600 second TTL. There is no self-serve signup.

What makes this provider unusual for a gated API: **every service also publishes a live, unauthenticated Stoplight mock server** that serves the documented response examples — including the real error envelopes. The contract is testable before a commercial agreement is signed. See [`sandbox/`](sandbox/rea-group-sandbox.yml).

A quota- and expiry-bounded trial programme is documented, with honest disclosure of its data restrictions (reduced attribute coverage and withheld Valuer-General transactions for Victorian properties). See [`plans/`](plans/rea-group-plans.yml).

## APIs

| Service | Operations | Spec | Mock |
|---|---|---|---|
| [OAuth 2.0 Token](https://developer.proptrack.com.au/docs/apis/how-to-authenticate) | 1 | [oauth](openapi/rea-group-oauth-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/70243931) |
| [Address](https://developer.proptrack.com.au/docs/apis/address) | 2 | [address](openapi/rea-group-address-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/67669714) |
| [Properties](https://developer.proptrack.com.au/docs/apis/properties) | 15 | [properties](openapi/rea-group-properties-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/67669715) |
| [Listings](https://developer.proptrack.com.au/docs/apis/listings) | 3 | [listings](openapi/rea-group-listings-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/160758630) |
| [Transactions](https://developer.proptrack.com.au/docs/apis/transactions) | 2 | [transactions](openapi/rea-group-transactions-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/205281044) |
| [Market](https://developer.proptrack.com.au/docs/apis/market) | 5 | [market](openapi/rea-group-market-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/99896681) |
| [Reports](https://developer.proptrack.com.au/docs/apis/reports) | 2 | [reports](openapi/rea-group-reports-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/181515791) |
| [Disclaimers](https://developer.proptrack.com.au/docs/apis/disclaimersbranding) | 1 | [disclaimers](openapi/rea-group-disclaimers-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/723134185) |
| [Upcoming (Schools)](https://developer.proptrack.com.au/docs/apis/coming-soon) | 1 | [coming-soon](openapi/rea-group-coming-soon-openapi.yml) | [mock](https://stoplight.io/mocks/proptrack/apis/639882521) |

Plus the [realestate.com.au Partner Portal](https://partner.realestate.com.au/) and the **REAXML** listing feed ([propertyList DTD](https://reaxml.realestate.com.au/propertyList.dtd)) — REA Group's own XML schema, implemented by the majority of Australian agency CRMs. Australia has no MLS and no RESO mandate; REAXML is the structural substitute.

## The shape of the surface

The spine is `address → propertyId → everything`. Resolve a free-text address with `address.match`, then fan out on the returned `propertyId` for attributes, listings, transactions, planning, tenure and valuations. The Market API is the one branch that does *not* join to `propertyId` — it is keyed by suburb geography and returns aggregates. See [`data-model/`](data-model/rea-group-data-model.yml).

## Artifacts

| Artifact | What it holds |
|---|---|
| [`openapi/`](openapi/) | 9 provider-published OpenAPI 3.1.0 documents, 32 operations, 189 named examples |
| [`authentication/`](authentication/rea-group-authentication.yml) | OAuth 2.0 client credentials profile, token URL, TTL, error codes |
| [`conventions/`](conventions/rea-group-conventions.yml) | Cursor pagination, error envelope, `X-Transaction-Id` tracing, concurrent v1/v2 |
| [`errors/`](errors/rea-group-error-codes.yml) | 18 numbered error codes (7xxx validation, 9xxx platform) with per-endpoint applicability |
| [`rate-limits/`](rate-limits/rea-group-rate-limits.yml) | 16 published per-endpoint limits plus the quota model |
| [`plans/`](plans/rea-group-plans.yml) | Trial quota/expiry, Victoria data restrictions, contract pricing |
| [`sandbox/`](sandbox/rea-group-sandbox.yml) | 9 live unauthenticated mock servers, verified |
| [`examples/`](examples/rea-group-examples.yml) | 189 named response examples indexed per operation |
| [`data-model/`](data-model/rea-group-data-model.yml) | Entity graph reconstructed from inline response schemas |
| [`skills/`](skills/_index.yml) | 3 agent skills — resolve an address, order a valuation, search listings and market |
| [`agentic-access/`](agentic-access/rea-group-agentic-access.yml) | Recommended `x-agentic-access` contracts for all 32 operations |
| [`overlays/`](overlays/rea-group-security-overlay.yaml) | Our enhancements — the missing security scheme, contact block, spec findings |
| [`mcp/`](mcp/rea-group-mcp.yml) | Candidate tool surface. **PropTrack publishes no MCP server.** |
| [`conformance/`](conformance/rea-group-conformance.yml) | 13 standards assessed, including why RESO does not apply |
| [`lifecycle/`](lifecycle/rea-group-lifecycle.yml) | Versioning, roadmap, and the verified absence of a status page |

## Known gaps in the provider's contract

Recorded in full in [`review.yml`](review.yml) and [`overlays/`](overlays/rea-group-security-overlay.yaml):

- **No `securitySchemes`** in any of the nine documents, despite OAuth 2.0 being required. Generated clients read the API as unauthenticated.
- **Six invalid path templates** in the Properties document — query strings and prose embedded in path keys, e.g. `/api/v1/properties/valuations/sale ~ Pro`.
- **No idempotency** on three billable, side-effecting POST operations that document 504 timeouts. A retried timeout may be a second paid valuation.
- **Empty `info.version`** in all nine documents.
- **No `components.schemas`** — everything inlined, inflating the Properties document to 591KB.
- **No rate-limit response headers**, no status page, no deprecation policy, no changelog, no SDKs, no MCP server.

## Common Properties

- [Website](https://www.rea-group.com/)
- [Documentation](https://developer.proptrack.com.au/docs/apis/home)
- [Developer Portal](https://developer.proptrack.com.au/)
- [API Reference](https://developer.proptrack.com.au/docs/apis/guide)
- [Getting Started](https://developer.proptrack.com.au/docs/apis/how-to-authenticate)
- [Partner Portal](https://partner.realestate.com.au/)
- [Terms of Use](https://developer.proptrack.com.au/docs/apis/terms-of-use)
- [FAQ](https://developer.proptrack.com.au/docs/apis/faqs)
- [GitHub Organization](https://github.com/realestate-com-au)
- [LinkedIn](https://www.linkedin.com/company/rea-group/)
- [X](https://twitter.com/REA_Group)
- [YouTube](https://www.youtube.com/channel/UCfLcFXAN3pjad2aCzUNhUaA)
- [Blog](https://www.rea-group.com/about-us/news-and-insights/)
- [Support](https://www.proptrack.com.au/support/contact-support/)
- [Privacy Policy](https://www.rea-group.com/privacy/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
