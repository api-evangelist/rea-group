---
name: Search PropTrack listings, sold transactions and suburb market trends
description: >-
  Run geospatial and suburb/postcode searches across for-sale and sold listings on
  realestate.com.au data, and pull suburb-level market statistics - sale and rent
  history, supply and demand, auction results and demographics.
api: openapi/rea-group-listings-openapi.yml
operations:
- auth-token
- listings-point-and-radius-search
- get-api-v2-listings-search-suburb-and-postcode
- listings
- get-transactions-propertyId
- get-transactions-propertyId-suburb
- get-api-v2-properties-summaries-search
- get-api-v2-properties-geopoints-pins
- market.sale-history
- market.rent-history
- market.supply-and-demand
- get-api-v2-market-auctions
- /api/v2/market/demographics
---

# Search listings, transactions and market trends

Two different query models live here, and mixing them up is the most common
mistake:

- **Listings and transactions** are keyed by **geography or id** and return
  individual records.
- **Market** is keyed by **suburb geography only** and returns aggregate metrics.
  It does not join to `propertyId`.

## Step 1 — token

`POST /oauth2/token` (`auth-token`). Bearer, 3600s.

## Step 2 — search listings

**Point and radius** — `GET /api/v2/listings/search/point-and-radius`
(`listings-point-and-radius-search`). Latitude, longitude and a radius. Use for
"what is for sale near here".

**Suburb and postcode** — `GET /api/v2/listings/search/suburb-and-postcode`
(`get-api-v2-listings-search-suburb-and-postcode`). Use for administrative
boundaries rather than a circle.

**By id** — `GET /api/v2/listings/{listingId}` (`listings`) for a single listing.

Sold transactions mirror the same two shapes:
`GET /api/v2/transactions/search/point-and-radius`
(`get-transactions-propertyId`) and
`GET /api/v2/transactions/search/suburb-and-postcode`
(`get-transactions-propertyId-suburb`).

For property records rather than listings, use
`GET /api/v2/properties/summaries/search` (`get-api-v2-properties-summaries-search`)
or `GET /api/v2/properties/geopoints/search`
(`get-api-v2-properties-geopoints-pins`) for map pins.

## Step 3 — paginate properly

Every search here is cursor-paginated:

- `pageSize` — default 25, **maximum 200**. Ask for 200 when sweeping; the rate
  limit is per request, not per record, so larger pages are strictly cheaper.
- `afterPageCursor` / `beforePageCursor` — opaque bidirectional cursors. **Never
  send both** — that is error `7015` (conflicting criteria).
- `numberOfResults` is the **total matching the criteria**, not the page count.
  Use it to size the sweep before you start, not to detect the last page.

Stop when a page returns no forward cursor. Do not compute page counts from
`numberOfResults` — the cursor is the contract.

## Step 4 — read the market

All suburb-keyed, all requiring `searchType` plus `state` and `postcode`/`suburb`
(omitting them is error `7004`):

| Question | Operation |
|---|---|
| Sale price history for a suburb | `GET /api/v2/market/sale/historic/{metric}` (`market.sale-history`) |
| Rent history for a suburb | `GET /api/v2/market/rent/historic/{metric}` (`market.rent-history`) |
| Supply and demand balance | `GET /api/v2/market/supply-and-demand/{metric}` (`market.supply-and-demand`) |
| Auction results | `GET /api/v2/market/auctions` (`get-api-v2-market-auctions`) |
| Suburb demographics | `GET /api/v2/market/demographics` (`/api/v2/market/demographics`) |

`{metric}` is a path parameter — the specific measure (median price, days on
market and so on). Check the enum in the spec; an unlisted value is error `7007`.

Date ranges come back in a `dateRanges` block. Respect it rather than assuming a
window — coverage differs by metric and suburb.

## Rules that apply throughout

- **Rate limit** is 50 requests/second per endpoint here, rolling one-second
  window, no headers to observe it. Sweeping many suburbs is exactly where you
  will hit `429` / `9011` — pace and back off.
- **Quota counts failures.** A tight retry loop against a validation error burns
  paid quota. Fix `7xxx` before retrying.
- **Trial gap.** On a trial agreement, `Market/Sale History` returns **no data at
  all** for Victoria, and Victorian Valuer-General transactions are withheld from
  the transaction endpoints. Response schemas are unchanged, so an empty result on
  a trial is not evidence of an empty market.
- **Date ranges.** An invalid start/end combination is error `7014`.
- **Disclaimers.** `GET /api/v1/disclaimers` — required wherever you display this
  data.
