---
name: Fund and withdraw from a Blockchain.com Exchange account
description: >-
  Check balances, generate a crypto deposit address, track the deposit to
  completion, and request a withdrawal to a whitelisted beneficiary on the
  Blockchain.com Exchange REST API.
api: openapi/blockchain.com-exchange-openapi.yml
base_url: https://api.blockchain.com/v3/exchange
operations:
  - getAccounts
  - getAccountByTypeAndCurrency
  - getDepositAddress
  - getDeposits
  - getDepositById
  - getWhitelist
  - getWhitelistByCurrency
  - createWithdrawal
  - getWithdrawals
  - getWithdrawalById
generated: '2026-08-02'
method: generated
source: openapi/blockchain.com-exchange-openapi.yml, https://api.blockchain.com/v3/
---

# Fund and withdraw from a Blockchain.com Exchange account

## Before you start

- Authenticate every call with the `X-API-Token` header.
- `createWithdrawal` moves real funds off the platform and is irreversible once
  broadcast. Require explicit human confirmation of the amount, currency and
  beneficiary before calling it.

## Deposit

1. **Check current balances** — `getAccounts` (`GET /accounts`) returns a balance
   map; `getAccountByTypeAndCurrency` (`GET /accounts/{account}/{currency}`) narrows
   to one account and currency. Each `Balance` carries `balance`, `available`,
   `balance_local`, `available_local` and `rate`.
2. **Generate a deposit address** — `getDepositAddress`
   (`POST /deposits/{currency}`). Only crypto currencies are supported. The
   response is a `DepositAddressCrypto` with `type` and `address`. Show the address
   and the exact asset/network to the user; sending the wrong asset loses the funds.
3. **Track the deposit** — `getDeposits` (`GET /deposits`, filtered by `from`/`to`)
   and `getDepositById` (`GET /deposits/{depositId}`). Read `state`, `amount`,
   `txHash` and `timestamp`.

## Withdraw

4. **Resolve the beneficiary** — `getWhitelist` (`GET /whitelist`) or
   `getWhitelistByCurrency` (`GET /whitelist/{currency}`). Each `WhitelistEntry`
   has `whitelistId`, `name` and `currency`. A withdrawal can only go to a
   whitelisted beneficiary — never attempt to withdraw to a raw address supplied at
   runtime.
5. **Request the withdrawal** — `createWithdrawal` (`POST /withdrawals`) with
   `amount`, `currency`, `beneficiary` (the whitelist id) and optionally
   `sendMax`. Confirm the resulting fee with the user.
6. **Track the withdrawal** — `getWithdrawals` (`GET /withdrawals`) and
   `getWithdrawalById` (`GET /withdrawals/{withdrawalId}`). Read `state`, `fee` and
   `timestamp`.

## Rules an agent must follow

- **No idempotency key exists.** A timed-out `POST /withdrawals` must be resolved by
  listing withdrawals over the relevant time window and matching amount, currency
  and beneficiary before any resubmission. Never blind-retry.
- **No sandbox.** These operations run against production balances.
- `401` means the `X-API-Token` header is missing or invalid; `404` means the
  `depositId` or `withdrawalId` does not belong to the account. See
  `errors/blockchain.com-problem-types.yml`.
