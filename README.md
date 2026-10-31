# REA Group

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

REA Group Limited is an ASX-listed (ASX:REA) digital real estate advertising business headquartered in Melbourne, Australia and majority-owned by News Corp. It operates realestate.com.au and realcommercial.com.au, the property data and analytics brand PropTrack, the Mortgage Choice broking network, and REA India (Housing.com, PropTiger, and Makaan). REA Group's public developer surface is delivered through PropTrack, whose developer portal publishes nine OpenAPI 3.1 documents covering 32 operations - OAuth token issuance, address matching and suggestion, property summary, attributes, planning, tenure, listings and transactions, automated valuations (AVM Sale, Rent, Plus and Pro), PDF valuation and property reports, suburb-level market history, supply and demand, auction results and demographics, plus a Disclaimers API that serves the attribution text PropTrack contractually requires alongside its data. Every service also publishes a live, unauthenticated Stoplight mock server, so the contract can be exercised before a commercial agreement is signed. The APIs are documented publicly but are partner-gated - access requires a commercial agreement arranged through an Account Manager, and calls are authenticated with OAuth 2.0 client credentials exchanged for a one-hour JWT bearer token at data.proptrack.com. Alongside PropTrack, REA Group runs the realestate.com.au Partner Portal (partner.realestate.com.au), the integration surface for real estate agencies and their CRM / software providers to publish for-sale and for-rent listings onto realestate.com.au and realcommercial.com.au and to receive buyer and renter enquiries. Listing distribution uses REAXML, REA's long-standing industry-standard XML property feed (schema published at reaxml.realestate.com.au), which the majority of Australian agency CRMs implement, with partner onboarding, API credentials (Client ID + secret) and enquiry delivery managed through the partner portal.

**Areas:** Real Estate · Property Data · Valuation · AVM · Market Insights · Listings · Transaction · Address Matching · REAXML · Partner Portal · PropTech · Australia

## REA Group on APIs.io

Everything profiled for REA Group is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/rea-group/](https://apis.io/providers/rea-group/)** — or go straight to one of the APIs or properties below.

### APIs (49)

- [realestate.com.au Listing Feed (REAXML)](https://apis.io/apis/rea-group/realestate-listing-feed-reaxml/) — REA Group's REAXML listing feed - the long-standing industry-standard XML property schema used by Australian agency CRMs to publish residential and…
- [realestate.com.au Partner Portal](https://apis.io/apis/rea-group/realestate-partner-portal/) — The realestate.com.au Partner Portal is REA Group's integration surface for agencies and their software / CRM providers - covering partner onboarding, API…
- [REA Group Attributes API](https://apis.io/apis/rea-group/rea-group-attributes-api/) — Property Attributes
- [REA Group Auction Results API](https://apis.io/apis/rea-group/rea-group-auction-results-api/) — The Auction Results API from REA Group — 1 operation(s) for auction results.
- [REA Group AVM API](https://apis.io/apis/rea-group/rea-group-avm-api/) — AVM
- [REA Group AVM Report API](https://apis.io/apis/rea-group/rea-group-avm-report-api/) — The AVM Report API from REA Group — 1 operation(s) for avm report.
- [REA Group Demographics API](https://apis.io/apis/rea-group/rea-group-demographics-api/) — The Demographics API from REA Group — 1 operation(s) for demographics.
- [REA Group Disclaimers API](https://apis.io/apis/rea-group/rea-group-disclaimers-api/) — The Disclaimers API from REA Group — 1 operation(s) for disclaimers.
- [REA Group Listing by listingId API](https://apis.io/apis/rea-group/rea-group-listing-by-listingid-api/) — The Listing by listingId API from REA Group — 1 operation(s) for listing by listingid.
- [REA Group Listings API](https://apis.io/apis/rea-group/rea-group-listings-api/) — Property Listings
- [REA Group Match API](https://apis.io/apis/rea-group/rea-group-match-api/) — The Match API from REA Group — 1 operation(s) for match.
- [REA Group Planning API](https://apis.io/apis/rea-group/rea-group-planning-api/) — Property Planning Overlays
- [REA Group Point & Radius Search API](https://apis.io/apis/rea-group/rea-group-point-radius-search-api/) — The Point & Radius Search API from REA Group — 2 operation(s) for point & radius search.
- [REA Group Property Report API](https://apis.io/apis/rea-group/rea-group-property-report-api/) — The Property Report API from REA Group — 1 operation(s) for property report.
- [REA Group Rent History API](https://apis.io/apis/rea-group/rea-group-rent-history-api/) — The Rent History API from REA Group — 1 operation(s) for rent history.
- [REA Group Sale History API](https://apis.io/apis/rea-group/rea-group-sale-history-api/) — The Sale History API from REA Group — 1 operation(s) for sale history.
- [REA Group Schools API](https://apis.io/apis/rea-group/rea-group-schools-api/) — The Schools API from REA Group — 1 operation(s) for schools.
- [REA Group Search API](https://apis.io/apis/rea-group/rea-group-search-api/) — Property Search
- [REA Group Suburb & Postcode Search API](https://apis.io/apis/rea-group/rea-group-suburb-postcode-search-api/) — The Suburb & Postcode Search API from REA Group — 2 operation(s) for suburb & postcode search.
- [REA Group Suggest API](https://apis.io/apis/rea-group/rea-group-suggest-api/) — The Suggest API from REA Group — 1 operation(s) for suggest.
- [REA Group Summary API](https://apis.io/apis/rea-group/rea-group-summary-api/) — Property Summary
- [REA Group Supply & Demand API](https://apis.io/apis/rea-group/rea-group-supply-demand-api/) — The Supply & Demand API from REA Group — 1 operation(s) for supply & demand.
- [REA Group Tenure Type API](https://apis.io/apis/rea-group/rea-group-tenure-type-api/) — Property Tenure Type History
- [REA Group Transactions API](https://apis.io/apis/rea-group/rea-group-transactions-api/) — Property Transactions
- [REA Group Oauth2 API](https://apis.io/apis/rea-group/rea-group-oauth2-api/) — The Oauth2 API from REA Group — 1 operation(s) for oauth2.
- [REA Group Agencies stats API](https://apis.io/apis/rea-group/rea-group-agencies-stats-api/) — The Agencies stats API from REA Group — 1 operation(s) for agencies stats.
- [REA Group Agency ratings reviews API](https://apis.io/apis/rea-group/rea-group-agency-ratings-reviews-api/) — The Agency ratings reviews API from REA Group — 1 operation(s) for agency ratings reviews.
- [REA Group Agent ratings reviews API](https://apis.io/apis/rea-group/rea-group-agent-ratings-reviews-api/) — The Agent ratings reviews API from REA Group — 1 operation(s) for agent ratings reviews.
- [REA Group Agents stats API](https://apis.io/apis/rea-group/rea-group-agents-stats-api/) — The Agents stats API from REA Group — 1 operation(s) for agents stats.
- [REA Group Campaign API](https://apis.io/apis/rea-group/rea-group-campaign-api/) — The Campaign API from REA Group — 3 operation(s) for campaign.
- [REA Group Connection Leads API](https://apis.io/apis/rea-group/rea-group-connection-leads-api-api/) — The Connection Leads API API from REA Group — 2 operation(s) for connection leads api.
- [REA Group Creative API](https://apis.io/apis/rea-group/rea-group-creative-api/) — The Creative API from REA Group — 1 operation(s) for creative.
- [REA Group Customer V1 API](https://apis.io/apis/rea-group/rea-group-customerv1-api/) — The customerV1 API from REA Group — 7 operation(s) for customerv1.
- [REA Group Diagnostic API](https://apis.io/apis/rea-group/rea-group-diagnostic-api/) — The diagnostic API from REA Group — 1 operation(s) for diagnostic.
- [REA Group eDM Performance API](https://apis.io/apis/rea-group/rea-group-edm-performance-api/) — The eDM Performance API from REA Group — 1 operation(s) for edm performance.
- [REA Group Enquiries API](https://apis.io/apis/rea-group/rea-group-enquiries-api/) — The Enquiries API from REA Group — 3 operation(s) for enquiries.
- [REA Group Enrichments API](https://apis.io/apis/rea-group/rea-group-enrichments-api/) — The Enrichments API from REA Group — 2 operation(s) for enrichments.
- [REA Group Flight API](https://apis.io/apis/rea-group/rea-group-flight-api/) — The Flight API from REA Group — 1 operation(s) for flight.
- [REA Group Integrations API](https://apis.io/apis/rea-group/rea-group-integrations-api/) — The Integrations API from REA Group — 2 operation(s) for integrations.
- [REA Group Listing Performance API](https://apis.io/apis/rea-group/rea-group-listing-performance-api/) — The Listing Performance API from REA Group — 2 operation(s) for listing performance.
- [REA Group Listings Export API](https://apis.io/apis/rea-group/rea-group-listings-export-api/) — The listings-export API from REA Group — 3 operation(s) for listings-export.
- [REA Group Prices API](https://apis.io/apis/rea-group/rea-group-prices-api/) — The Prices API from REA Group — 2 operation(s) for prices.
- [REA Group Project Performance API](https://apis.io/apis/rea-group/rea-group-project-performance-api/) — The Project Performance API from REA Group — 2 operation(s) for project performance.
- [REA Group Report API](https://apis.io/apis/rea-group/rea-group-report-api/) — The Report API from REA Group — 2 operation(s) for report.
- [REA Group Seller Leads API](https://apis.io/apis/rea-group/rea-group-seller-leads-api/) — The Seller Leads API from REA Group — 2 operation(s) for seller leads.
- [REA Group Successful Applicant API](https://apis.io/apis/rea-group/rea-group-successful-applicant-api-api/) — The Successful Applicant API API from REA Group — 2 operation(s) for successful applicant api.
- [REA Group Tenant Selection API](https://apis.io/apis/rea-group/rea-group-tenant-selection-api-api/) — The Tenant Selection API API from REA Group — 3 operation(s) for tenant selection api.
- [REA Group Upload API](https://apis.io/apis/rea-group/rea-group-upload-api/) — The Upload API from REA Group — 1 operation(s) for upload.
- [REA Group Webhooks API](https://apis.io/apis/rea-group/rea-group-webhooks-api/) — The Webhooks API from REA Group — 5 operation(s) for webhooks.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Rea Group Agentic Access](https://apis.io/agentic-access/rea-group/rea-group-agentic-access/)

#### JSON Schema (38)

The data models the API reads and writes.

- [AffiliatedAgency](https://apis.io/schemas/rea-group/rea-group-affiliated-agencies/)
- [AgenciesStats](https://apis.io/schemas/rea-group/rea-group-agencies-stats/)
- [AgentsStats](https://apis.io/schemas/rea-group/rea-group-agents-stats/)
- [CampaignListResponse](https://apis.io/schemas/rea-group/rea-group-campaign-list-response/)
- [CampaignResponse](https://apis.io/schemas/rea-group/rea-group-campaign-response/)
- [ConnectionLeads](https://apis.io/schemas/rea-group/rea-group-connection-leads/)
- [CreativeResponse](https://apis.io/schemas/rea-group/rea-group-creative-response/)
- [DeliveryResponse](https://apis.io/schemas/rea-group/rea-group-delivery-response/)
- [EdmPerformanceItems](https://apis.io/schemas/rea-group/rea-group-edm-performance-items/)
- [Enquiries](https://apis.io/schemas/rea-group/rea-group-enquiries/)
- [Enquiry](https://apis.io/schemas/rea-group/rea-group-enquiry/)
- [Enrichment](https://apis.io/schemas/rea-group/rea-group-enrichment/)
- [Enrichments](https://apis.io/schemas/rea-group/rea-group-enrichments/)
- [FlightResponse](https://apis.io/schemas/rea-group/rea-group-flight-response/)
- [int](https://apis.io/schemas/rea-group/rea-group-int/)
- [Integration](https://apis.io/schemas/rea-group/rea-group-integration/)
- [Integrations](https://apis.io/schemas/rea-group/rea-group-integrations/)
- [ListingPerformance](https://apis.io/schemas/rea-group/rea-group-listing-performance/)
- [ListingPerformanceItems](https://apis.io/schemas/rea-group/rea-group-listing-performance-items/)
- [nonEmptyString](https://apis.io/schemas/rea-group/rea-group-non-empty-string/)
- [ProjectPerformance](https://apis.io/schemas/rea-group/rea-group-project-performance/)
- [ProjectPerformanceItemsForAgency](https://apis.io/schemas/rea-group/rea-group-project-performance-items-for-agency/)
- [PublishedApplicationItem](https://apis.io/schemas/rea-group/rea-group-published-application-item/)
- [RatingsReviews](https://apis.io/schemas/rea-group/rea-group-ratings-reviews/)
- [realcommercial_products](https://apis.io/schemas/rea-group/rea-group-realcommercial-products/)
- …and 13 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Rea Group Context](https://apis.io/jsonld/rea-group/rea-group-context/)

#### Collections (9)

Postman and Open Collection request collections.

- [Address API](https://apis.io/collections/rea-group/open-rea-group-address/)
- [Coming Soon](https://apis.io/collections/rea-group/open-rea-group-coming-soon/)
- [Disclaimers API](https://apis.io/collections/rea-group/open-rea-group-disclaimers/)
- [Listings API](https://apis.io/collections/rea-group/open-rea-group-listings/)
- [Market](https://apis.io/collections/rea-group/open-rea-group-market/)
- [OAuth 2.0](https://apis.io/collections/rea-group/open-rea-group-oauth/)
- [Properties API](https://apis.io/collections/rea-group/open-rea-group-properties/)
- [Reports](https://apis.io/collections/rea-group/open-rea-group-reports/)
- [Transactions](https://apis.io/collections/rea-group/open-rea-group-transactions/)

#### Overlays (47)

OpenAPI overlays, including conversational phrasing for each operation.

- [Rea Group Agencies Stats Api Overlay](https://apis.io/overlays/rea-group/rea-group-agencies-stats-api-overlay/)
- [Rea Group Agency Ratings Reviews Api Overlay](https://apis.io/overlays/rea-group/rea-group-agency-ratings-reviews-api-overlay/)
- [Rea Group Agent Ratings Reviews Api Overlay](https://apis.io/overlays/rea-group/rea-group-agent-ratings-reviews-api-overlay/)
- [Rea Group Agents Stats Api Overlay](https://apis.io/overlays/rea-group/rea-group-agents-stats-api-overlay/)
- [Rea Group Attributes Api Overlay](https://apis.io/overlays/rea-group/rea-group-attributes-api-overlay/)
- [Rea Group Auction Results Api Overlay](https://apis.io/overlays/rea-group/rea-group-auction-results-api-overlay/)
- [Rea Group Avm Api Overlay](https://apis.io/overlays/rea-group/rea-group-avm-api-overlay/)
- [Rea Group Avm Report Api Overlay](https://apis.io/overlays/rea-group/rea-group-avm-report-api-overlay/)
- [Rea Group Campaign Api Overlay](https://apis.io/overlays/rea-group/rea-group-campaign-api-overlay/)
- [Rea Group Connection Leads Api Api Overlay](https://apis.io/overlays/rea-group/rea-group-connection-leads-api-api-overlay/)
- [Rea Group Creative Api Overlay](https://apis.io/overlays/rea-group/rea-group-creative-api-overlay/)
- [Rea Group Customerv1 Api Overlay](https://apis.io/overlays/rea-group/rea-group-customerv1-api-overlay/)
- [Rea Group Demographics Api Overlay](https://apis.io/overlays/rea-group/rea-group-demographics-api-overlay/)
- [Rea Group Diagnostic Api Overlay](https://apis.io/overlays/rea-group/rea-group-diagnostic-api-overlay/)
- [Rea Group Disclaimers Api Overlay](https://apis.io/overlays/rea-group/rea-group-disclaimers-api-overlay/)
- [Rea Group Edm Performance Api Overlay](https://apis.io/overlays/rea-group/rea-group-edm-performance-api-overlay/)
- [Rea Group Enquiries Api Overlay](https://apis.io/overlays/rea-group/rea-group-enquiries-api-overlay/)
- [Rea Group Enrichments Api Overlay](https://apis.io/overlays/rea-group/rea-group-enrichments-api-overlay/)
- [Rea Group Flight Api Overlay](https://apis.io/overlays/rea-group/rea-group-flight-api-overlay/)
- [Rea Group Integrations Api Overlay](https://apis.io/overlays/rea-group/rea-group-integrations-api-overlay/)
- [Rea Group Listing By Listingid Api Overlay](https://apis.io/overlays/rea-group/rea-group-listing-by-listingid-api-overlay/)
- [Rea Group Listing Performance Api Overlay](https://apis.io/overlays/rea-group/rea-group-listing-performance-api-overlay/)
- [Rea Group Listings Api Overlay](https://apis.io/overlays/rea-group/rea-group-listings-api-overlay/)
- [Rea Group Listings Export Api Overlay](https://apis.io/overlays/rea-group/rea-group-listings-export-api-overlay/)
- [Rea Group Match Api Overlay](https://apis.io/overlays/rea-group/rea-group-match-api-overlay/)
- …and 22 more published on APIs.io

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [REA Group API Rules](https://apis.io/rules/rea-group/rea-group-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Rea Group Authentication](https://apis.io/security/rea-group/rea-group-authentication/)
- [Rea Group Domain Security](https://apis.io/security/rea-group/rea-group-domain-security/)
- [Rea Group Vulnerability Disclosure](https://apis.io/security/rea-group/rea-group-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Rea Group Scopes](https://apis.io/scopes/rea-group/rea-group-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Rea Group Plans](https://apis.io/plans/rea-group/rea-group-plans/)

#### Rate limits (1)

Published request limits.

- [Rea Group Rate Limits](https://apis.io/rate-limits/rea-group/rea-group-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.rea-group.com/)
- [Documentation](https://developer.proptrack.com.au/docs/apis/home)
- [Getting started](https://developer.proptrack.com.au/docs/apis/how-to-authenticate)
- [API reference](https://developer.proptrack.com.au/docs/apis/guide)
- [Pricing](https://developer.proptrack.com.au/docs/apis/api-trials)
- [Sign up](https://www.proptrack.com.au/contact-us)
- [Support](https://www.proptrack.com.au/support/contact-support/)
- [Blog](https://www.rea-group.com/about-us/news-and-insights/)
- [Security](https://www.rea-group.com/security)
- [Terms of service](https://developer.proptrack.com.au/docs/apis/terms-of-use)
- [Privacy policy](https://www.rea-group.com/privacy/)
- [GitHub](https://github.com/realestate-com-au)

## API Evangelist rating

**Kin Score 53.8** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 52.2 |
| Contract governance | 4.5 |
| Operational transparency | 50.0 |
| Developer ergonomics | 62.5 |
| Access clarity | 60.5 |

**Agent readiness 29.1** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 28.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/rea-group/](https://apis.io/providers/rea-group/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for REA Group: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/rea-group/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
