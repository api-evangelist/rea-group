---
name: Resolve an Australian address to a PropTrack property profile
description: >-
  Turn a free-text Australian address into a PropTrack propertyId, then assemble
  the full property profile - attributes, listing history, sold transactions,
  planning and tenure - from the PropTrack Property Data APIs.
api: openapi/rea-group-properties-openapi.yml
operations:
- address.match
- address.suggest
- get-v2-summary
- properties-attributes
- listings
- transactions
- get-api-v2-properties-planning
- get-api-v2-properties-tenure
- get-api-v1-disclaimers
---

# Resolve an address to a PropTrack property profile

Almost every PropTrack workflow starts the same way: you have a free-text address
and you need the `propertyId` that everything else is keyed on. This skill covers
that resolution step and the fan-out that follows it.

## Before you start

- Access is **partner-gated**. You need an `api_key` and `api_secret` issued by a
  PropTrack Account Manager under a commercial agreement. There is no self-serve
  signup.
- To exercise the shapes without credentials, point at the mock servers in
  `sandbox/rea-group-sandbox.yml` instead of `https://data.proptrack.com`. They
  serve the published examples and need no auth.

## Step 1 — get a token

`POST https://data.proptrack.com/oauth2/token` (`auth-token`)

```
Authorization: Basic base64(api_key:api_secret)
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
```

Returns `access_token`, `token_type`, `expires_in` (3600). Send
`Authorization: Bearer <access_token>` on everything below.

Credentials are only accepted in the Authorization header — form parameters are
explicitly unsupported. Cache the token and refresh at expiry rather than minting
one per call; token errors are `9012` (validation failed) and `9016` (expired).

## Step 2 — resolve the address

`GET /api/v2/address/match?q=<address>` (`address.match`)

Returns `propertyId`, `gpid`, `matchScore` and the normalised `address`. This
resolves to a **single** property; if the text is ambiguous you get error `7002`
(cannot be matched).

When the input is partial or user-typed, use
`GET /api/v2/address/suggest` (`address.suggest`) first to offer candidates, then
match the chosen one. Structured (component-wise) address match is documented as
coming soon and is not yet callable.

Check `matchScore` before trusting the result. A low score on a `7002`-adjacent
input is the signal to fall back to suggest rather than proceed.

## Step 3 — fan out on propertyId

All of these take the `propertyId` from step 2:

| What you need | Operation |
|---|---|
| One-call overview: address, attributes, recent sale, active listings, market status, a photo | `GET /api/v2/properties/{propertyId}/summary` (`get-v2-summary`) |
| Full attribute set: beds, baths, car spaces, land area, property type, land use | `GET /api/v2/properties/{propertyId}/attributes` (`properties-attributes`) |
| Current and historic listings | `GET /api/v2/properties/{propertyId}/listings` (`listings`) |
| Sold transactions | `GET /api/v2/properties/{propertyId}/transactions` (`transactions`) |
| Planning and zoning | `GET /api/v2/properties/{propertyId}/planning` (`get-api-v2-properties-planning`) |
| Tenure history | `GET /api/v2/properties/{propertyId}/tenureType` (`get-api-v2-properties-tenure`) |

Start with `summary`. It answers most questions in one call and tells you whether
the deeper calls are worth making — if `activeListings` is empty there is no point
calling `listings` for a live-market question.

## Step 4 — attach the disclaimers

`GET /api/v1/disclaimers` (`get-api-v1-disclaimers`)

PropTrack **requires** attribution and disclaimer text wherever its data is
displayed. This endpoint serves the current required text and branding rules, so
fetch it rather than hardcoding — the wording changes and the requirement is
contractual, not cosmetic.

## Rules that apply throughout

- **Rate limits.** 50 requests/second per endpoint on this read surface, enforced
  on a rolling one-second window. There are no rate-limit response headers, so you
  cannot see remaining budget — you find out via a `429` with code `9011`. Pace
  deliberately and back off on 429.
- **Quota.** Separate from the rate limit, and it counts failed requests too.
  Exhaustion is also `429` + `9011`, distinguishable only by the description text
  ("Quota limit has been reached"). Do not retry into a quota wall.
- **Pagination.** Collection responses use cursors: `pageSize` (default 25, max
  200), `afterPageCursor`, `beforePageCursor`. Never send both cursors — that is
  error `7015`. Read `numberOfResults` as the total across all pages, not the page
  size.
- **Errors.** `{"errors":[{"code":<int>,"description":"..."}]}`, not RFC 9457.
  `7xxx` are your fault (validation), `9xxx` are platform (auth, quota, internal).
  Full registry in `errors/rea-group-error-codes.yml`.
- **Retries.** Every operation in this skill is a `GET` and safe to retry. Retry
  `500`/`504` with backoff; do not retry `7xxx` without changing the request.
- **Support.** Capture the `X-Transaction-Id` response header — PropTrack support
  asks for it on every issue.
