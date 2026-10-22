---
name: manage-partner-webhooks
title: Subscribe to realestate.com.au Partner Platform webhooks and verify deliveries
description: Create, inspect, re-validate and delete Partner Platform webhook subscriptions, fetch the public signing
  keys used to verify incoming webhook requests, and read delivery-attempt logs when deliveries fail.
api:
- openapi/rea-group-webhooks-api-openapi.yml
operations:
- getSigningKeys
- createSubscription
- getSubscriptions
- getSubscription
- validateSubscription
- getDeliveryAttempts
- deleteSubscription
---

# Manage Partner Platform webhooks

Base URL `https://api.realestate.com.au`. Auth is OAuth 2.0 client credentials
(`PartnerPlatform` scheme, token URL `https://api.realestate.com.au/oauth/token`)
with scopes `webhooks:subscriptions:write` and `webhooks:subscriptions:read`.
Credentials are issued only under a Partner Platform agreement.

## Steps

1. **Load the verification keys first.** `GET /webhooks/v1/signing` (`getSigningKeys`)
   returns the public keys used to verify incoming webhook requests. Cache them and
   reject any delivery whose signature does not verify.
2. **Check for an existing subscription.** `GET /webhooks/v1/subscriptions`
   (`getSubscriptions`, paged with `page`). The create call answers `409` on a
   conflict, so look before you create.
3. **Create.** `POST /webhooks/v1/subscriptions` (`createSubscription`) answers
   `202 Accepted`: the subscription is processed asynchronously. Do not treat 202
   as active; poll `GET /webhooks/v1/subscriptions/{subscriptionId}`
   (`getSubscription`) for its state.
4. **Recover a Failed or Disabled subscription.** Read
   `GET /webhooks/v1/subscriptions/{subscriptionId}/delivery` (`getDeliveryAttempts`)
   to find why deliveries failed, fix your receiver, then call
   `PATCH /webhooks/v1/subscriptions/{subscriptionId}/validate`
   (`validateSubscription`, also `202`).
5. **Tear down.** `DELETE /webhooks/v1/subscriptions/{subscriptionId}`
   (`deleteSubscription`) returns `204`.

## Rules

- No idempotency key is documented. A retried create can conflict (`409`). Re-list
  before you retry.
- `429` is declared on every operation. Back off and retry reads only.
- Create, validate and delete change provider state. Run them only on explicit
  user intent.
