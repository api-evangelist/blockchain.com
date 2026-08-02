---
name: Place and manage an order on the Blockchain.com Exchange
description: >-
  Authenticate to the Blockchain.com Exchange REST API, check the symbol's trading
  rules and current book, place a limit or market order, poll it to a terminal
  state, and cancel it if it does not fill.
api: openapi/blockchain.com-exchange-openapi.yml
base_url: https://api.blockchain.com/v3/exchange
operations:
  - getSymbolByName
  - getL2OrderBook
  - getFees
  - createOrder
  - getOrderById
  - getOrders
  - deleteOrder
  - deleteAllOrders
generated: '2026-08-02'
method: generated
source: openapi/blockchain.com-exchange-openapi.yml, https://api.blockchain.com/v3/
---

# Place and manage an order on the Blockchain.com Exchange

## Before you start

- Create an API key in the Blockchain.com Exchange under **Settings > API**. The key
  must be email-verified before it will work, and trading access is an explicit
  option on the key — a read-only key will not place orders.
- Send the key on every authenticated call as the header `X-API-Token`.
- There is **no sandbox**. Every call below hits production and moves real funds.
  Confirm with a human before any `createOrder` or `deleteAllOrders`.

## Steps

1. **Read the symbol's trading rules** — `getSymbolByName` (`GET /symbols/{symbol}`),
   e.g. `BTC-USD`. Use `min_order_size`, `max_order_size`, `lot_size`,
   `min_price_increment` and their matching `*_scale` fields to size and round the
   order. `status` must be a trading state before you submit anything.
2. **Read the book** — `getL2OrderBook` (`GET /l2/{symbol}`) for aggregated depth,
   or `getL3OrderBook` (`GET /l3/{symbol}`) for per-order depth. Both are
   unauthenticated. Use the top of book to choose a marketable or passive price.
3. **Check the fee level** — `getFees` (`GET /fees`) returns `makerRate`,
   `takerRate` and `volumeInUSD`. Quote the all-in cost to the user before placing.
4. **Place the order** — `createOrder` (`POST /orders`) with the FIX 4.2-named
   body: `clOrdId` (your own reference, max 20 characters), `symbol`, `side`
   (`buy`/`sell`), `ordType` (`market`, `limit`, `stop`, `stopLimit`),
   `orderQty`, and `timeInForce` (`GTC`, `IOC`, `FOK`, `GTD`). `price` is required
   for `limit` and `stopLimit`; `stopPx` for `stop` and `stopLimit`; `expireDate`
   (YYYYMMDD) for `GTD`. Set `execInst: ALO` to post only.
5. **Poll to a terminal state** — `getOrderById` (`GET /orders/{orderId}`) using the
   `exOrdId` from the create response, or `getOrders` (`GET /orders`) filtered by
   `symbol`, `status` and a `from`/`to` time window. Read `ordStatus`, `cumQty`,
   `leavesQty` and `avgPx`.
6. **Cancel if needed** — `deleteOrder` (`DELETE /orders/{orderId}`) for one order,
   `deleteAllOrders` (`DELETE /orders`, optional `symbol` query parameter) to flatten.

## Rules an agent must follow

- **Do not retry `createOrder` blindly.** Blockchain.com documents no idempotency
  key. `clOrdId` is a correlation reference, not a dedupe key — a retried POST can
  place a second order. On a timeout, call `getOrders` filtered by symbol and time
  window and match on your `clOrdId` before deciding to resubmit.
- **Errors are not RFC 9457.** A failure returns `{"error": "<message>"}`. Only
  `401` (missing or invalid `X-API-Token`) and `404` (unknown id) are documented in
  the spec — treat any other non-2xx as unknown and stop rather than retrying a write.
- **No rate-limit budget headers are published** for the Exchange API. Back off on
  any non-2xx burst.
- Prefer the WebSocket `trading` channel
  (`wss://ws.blockchain.info/mercury-gateway/v1/ws`) when you need execution
  notifications rather than polling; see `asyncapi/blockchain.com-event-surface.yml`.
