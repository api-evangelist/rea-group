---
name: upload-and-export-listings
title: Upload REAXML listings to realestate.com.au and track processing
description: Upload a single listing as an REAXML document to the realestate.com.au Listing Upload API, track its
  processing through upload reports, and read listings back in REAXML through the Listing Export API.
api:
- openapi/rea-group-upload-api-openapi.yml
- openapi/rea-group-report-api-openapi.yml
- openapi/rea-group-listings-export-api-openapi.yml
operations:
- uploadXml
- getUploadReport
- searchUploadReports
- listings-export
- listings-export-agency
- listings-export-listing
---

# Upload and export listings

Base URL `https://api.realestate.com.au`. Auth is OAuth 2.0 client credentials
(`PartnerPlatform`). Upload needs scope `listing:listings:write` and export needs
`listing:listings:export`. Listings use the REAXML format
(https://reaxml.realestate.com.au/propertyList.dtd).

## Steps

1. **Upload.** `POST /listing/v1/upload` (`uploadXml`) accepts an REAXML document
   holding ONE listing. A `202` means it was accepted for processing, not that it is
   published. Keep the upload id from the response. A `413` means the document is
   too large; `400` or `406` mean the content or content type was rejected.
2. **Track.** `GET /listing/v1/upload/{uploadId}` (`getUploadReport`) returns the
   processing report. To find reports without an id, use `GET /listing/v1/upload`
   (`searchUploadReports`) with `agencyId` and `externalListingId`.
3. **Verify or reconcile.** Read listings back in REAXML with
   `GET /listing/v1/export` (`listings-export`), or narrow it by agency
   (`listings-export-agency`, `agency_id`) or by listing (`listings-export-listing`,
   `listing_id`).

## Rules

- No idempotency key is documented for uploads. Before you re-send after a timeout,
  check `searchUploadReports` for the `externalListingId`.
- One listing per upload. Batch on your side, not in the document.
- Export declares `429`. Back off on reads.
