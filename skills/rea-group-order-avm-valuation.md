---
name: Order a PropTrack AVM valuation and retrieve the report
description: >-
  Order an automated valuation (sale, rent, AVM Plus or AVM Pro) from PropTrack's
  Automated Valuation Model for an address or a propertyId, and download the
  resulting PDF valuation report.
api: openapi/rea-group-properties-openapi.yml
operations:
- auth-token
- address.match
- v1-properties-valuation-sale
- avm-propertyId
- avm-propertyId-enquiry
- v1-properties-valuation-sale-plus
- avm-propertyId-plus
- v1-properties-valuation-sale-pro
- avm-propertyId-pro
- reports-valuations-pdf
- reports-property-report
---

# Order an AVM valuation and retrieve the report

PropTrack's AVM is the product banks, brokers and valuers actually buy. This is
the **billable, side-effecting** part of the API — treat it differently from the
read surface.

> **These are ordering operations, not lookups.** Each call orders a valuation.
> There is no idempotency key, no request de-duplication and no documented
> safe-retry contract. A retried POST is a second order. Never retry blind — see
> "Retry discipline" below.

## Step 1 — token

`POST /oauth2/token` (`auth-token`), client credentials, as in
`rea-group-resolve-address-to-property.md`. Bearer token, 3600s TTL.

## Step 2 — pick your entry point

Two ways in, and the choice matters:

**By address string** — `POST /api/v1/properties/valuations/sale`
(`v1-properties-valuation-sale`). Use when you only have text and do not need the
property resolved first.

**By propertyId** — `GET /api/v1/properties/{propertyId}/valuations/sale`
(`avm-propertyId`). Use when you already resolved the address via
`address.match`. Preferred: resolution is explicit and you can inspect
`matchScore` before spending a valuation.

## Step 3 — choose the request type

`requestType` is the pricing and purpose dimension. Get it right the first time —
the wrong one is a wasted billable call.

| requestType | Meaning |
|---|---|
| `enquiry` | Indicative valuation, for research and enquiry-stage use |
| `origination` | Valuation intended to support loan origination |

And three product tiers, each with an address-string POST and a propertyId GET:

| Tier | Covers | Operations |
|---|---|---|
| Sale | Sale valuation only | `v1-properties-valuation-sale`, `avm-propertyId` |
| Rent | Rental valuation | `avm-propertyId-enquiry` (`.../valuations/rent`) |
| AVM Plus | Sale **and** rental in one request | `v1-properties-valuation-sale-plus`, `avm-propertyId-plus` |
| AVM Pro | Sale, rental **and** environmental hazards in one request | `v1-properties-valuation-sale-pro`, `avm-propertyId-pro` |

Prefer Plus/Pro over multiple single calls when you need more than one figure —
that is what they exist for, and it is one billable order instead of two or three.

Read the confidence range on the response, not just the point estimate. An AVM
figure without its range is not a usable answer for an origination decision.

## Step 4 — retrieve the report

`GET /api/v1/reports/valuations/{valuationId}/pdf` (`reports-valuations-pdf`)
renders a completed valuation as a PDF. `valuationId` comes from the valuation
response — persist it, it is your only handle on that order.

For a standalone property report (not tied to a valuation), use
`POST /api/v1/reports/property` (`reports-property-report`), which returns `201`.

## Step 5 — disclaimers are mandatory

Fetch `GET /api/v1/disclaimers` and display the returned text with any valuation
figure you surface. Attribution is a contractual requirement, and valuations are
exactly the output where it matters.

## Rules specific to this surface

- **Rate limit is 25 requests/second**, half the read surface. Applies to both the
  valuation endpoints and the report endpoints.
- **`504` is real here.** The valuation and report operations are the only ones in
  the catalogue that document a Gateway Timeout response — the model takes real
  time. Budget a long client timeout.
- **Retry discipline.** On `504` or `500` you do not know whether the order
  landed. Do not immediately re-POST. Where you hold a `valuationId`, poll the
  report endpoint instead. Where you do not, escalate rather than double-order —
  quote the `X-Transaction-Id` to support. This is the sharpest edge in the whole
  PropTrack surface and the absence of an idempotency key is why.
- **Trial restrictions.** On a trial agreement, Victorian properties have reduced
  attribute coverage and withheld Valuer-General transactions, which is upstream
  of the model. Do not benchmark AVM accuracy in Victoria on trial credentials.
- **Errors.** `9003` access denied means your agreement does not include this
  endpoint — valuation access is licensed separately from property data. Full
  registry in `errors/rea-group-error-codes.yml`.
