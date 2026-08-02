---
name: Quote a crypto purchase and track the order with Blockchain.com Pay
description: >-
  Check what a Blockchain.com Pay partner account can sell and where, fetch a live
  buy quote, hand the user to the Pay widget, then reconcile the resulting order by
  polling or by consuming the order webhook.
api: openapi/blockchain.com-pay-partner-api-openapi.yml
base_url: https://api.blockchain.info/partner-gateway/partner-api
operations:
  - GetCurrencies
  - GetRegions
  - GetPaymentMethods
  - GetQuoteBuy
  - ListOrders
  - GetOrderById
generated: '2026-08-02'
method: generated
source: >-
  openapi/blockchain.com-pay-partner-api-openapi.yml,
  https://docs.blockchain.com/pay/api
---

# Quote a crypto purchase and track the order with Blockchain.com Pay

## Before you start

- Every request needs `X-Public-API-Key`. Order endpoints (`ListOrders`,
  `GetOrderById`) additionally need `X-Private-API-Key` and must run
  server-to-server only.
- Keys are issued by the Blockchain.com Pay account manager (`pay@blockchain.com`);
  the private key is shown once and cannot be recovered.
- Rate limits: 10 rps per IP with only the public key, 100 rps per organization
  with the private key. Both return `429` with `Retry-After`.

## Steps

1. **Establish eligibility** before showing anything to the user:
   - `GetCurrencies` (`GET /v1/currencies`) — the fiat and crypto currencies enabled
     on this partner account.
   - `GetRegions` (`GET /v1/regions`, optional `onlyBuyAllowed`) — supported
     countries and US states.
   - `GetPaymentMethods` (`GET /v1/payment-methods`) — supported payment methods
     (`CARD`, `APPLE_PAY`, `GOOGLE_PAY`, `BANK_TRANSFER_NIP`).
2. **Quote the purchase** — `GetQuoteBuy` (`GET /v1/quote/buy`) with the required
   `quoteCurrencyCode`, `baseCurrencyCode` and `quoteCurrencyAmount`, plus optional
   `countryCode`, `usStateCode` and `walletAddress`. Tell the user the quote is
   indicative: if it expires before they reach the widget they will see a new one.
3. **Hand off to the widget** — open
   `https://www.blockchain.com/pay/widget?apiKey=<public key>` with the signed
   query parameters described in `components/blockchain.com-components.yml`.
   Always set `externalReference` (max 100 characters) so the order can be
   reconciled later.
4. **Reconcile the order.** Prefer webhooks; poll only as a fallback.
   - Webhook: a `POST` of the order event payload documented in
     `json-schema/blockchain.com-pay-webhook-event.json`, moving through
     `PENDING` → `WITHDRAWING` → `COMPLETED` or `FAILED`.
   - Polling: `ListOrders` (`GET /v1/orders`) with `limit`/`offset` (max 50 recent
     orders) and filters `externalReference`, `walletAddress`, `outputCurrency`,
     `from`, `to`; or `GetOrderById` (`GET /v1/orders/{id}`).

## Rules an agent must follow

- **Webhook delivery is at-least-once and out of order.** Persist processed
  `eventId` values and ignore repeats. A `COMPLETED` event can arrive before a
  retried `PENDING` event — never regress an order's state on a late event.
- **Acknowledge webhooks with a 2xx within 5 seconds**, before doing any real work.
  Anything slower is treated as undelivered and retried with exponential backoff
  for up to 3 days.
- **Verify the sender by source IP.** There is no webhook signature. Only accept
  events from `34.76.54.194`, `34.77.167.89`, `35.187.43.203`, `35.241.153.74`
  and `35.241.224.80`.
- **Errors are `{"type": "...", "message": "..."}`, not RFC 9457.** `type` is a
  dotted machine-readable code such as `RequestValidation.BadRequest.MissingParam`.
  Back off on `429` using `Retry-After`.
- Never send `X-Private-API-Key` from a browser or mobile client.
