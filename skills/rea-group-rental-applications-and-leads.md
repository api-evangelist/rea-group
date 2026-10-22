---
name: rental-applications-and-leads
title: Poll realestate.com.au rental applications, successful applicants and leads
description: Poll the rental application feeds (published, updated, successful), update an application's status,
  retrieve successful-applicant details, and poll connection leads and enriched seller leads for a partner's agencies.
api:
- openapi/rea-group-tenant-selection-api-api-openapi.yml
- openapi/rea-group-successful-applicant-api-api-openapi.yml
- openapi/rea-group-connection-leads-api-api-openapi.yml
- openapi/rea-group-enquiries-api-openapi.yml
- openapi/rea-group-seller-leads-api-openapi.yml
operations:
- getApplicationsUsingGET
- getUpdatedApplicationsUsingGET
- updateApplicationStatusUsingPUT
- getSuccessfulApplicationsUsingGET
- getSuccessfulApplicationDetailsUsingGET
- getConnectionLeadsUsingGet
- getConnectionLeadsAffiliatedAgenciesUsingGet
- getSellerLeads
- getSellerLead
---

# Rental applications and leads

These are feed-style polling APIs on `https://api.realestate.com.au`
(`/applications/v1/rental` and `/lead`). Auth is OAuth 2.0 client credentials
(`PartnerPlatform`). The scopes are `rent:applications:read`/`write`,
`rent:successful-applications:read`, `rent:connection-leads:read` and
`lead:enquiries:read`.

## Steps

1. **Poll new applications.** `GET /applications/published/feed`
   (`getApplicationsUsingGET`) with `happenedSince` and optionally `agencyIds`. Store
   the high-water mark you used and poll forward from it.
2. **Poll changes.** `GET /applications/updated/feed`
   (`getUpdatedApplicationsUsingGET`) with the same cursor parameters.
3. **Update status.** `PUT /applications/{applicationId}/status`
   (`updateApplicationStatusUsingPUT`) returns `204`. A `409` means the transition
   conflicts with the current state: re-read before you retry. This is a write, so
   run it only on explicit user intent.
4. **Successful applicants.** `GET /applications/successful/feed`
   (`getSuccessfulApplicationsUsingGET`), then
   `GET /applications/successful/{applicationId}/details`
   (`getSuccessfulApplicationDetailsUsingGET`). A `410` means the details are no
   longer available. Treat this as personal data.
5. **Connection leads.** `GET /connection-leads` (`getConnectionLeadsUsingGet`) and
   `GET /connection-leads/agencies` (`getConnectionLeadsAffiliatedAgenciesUsingGet`),
   both keyed on `happenedSince`.
6. **Seller leads.** `GET /v2/seller-leads` (`getSellerLeads`, `since`, `page`,
   `agency_id`, `agent_profile_id`) and `GET /v2/seller-leads/{enquiry_id}`
   (`getSellerLead`). The v1 enquiry operations in the same spec declare no
   operationId and are not bound here.

## Rules

- Polling is idempotent. Re-polling the same `happenedSince` window is safe, so
  de-duplicate on the application or enquiry id.
- The leads operations declare `429`. Back off.
