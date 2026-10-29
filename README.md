# Blockchain.com

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

Blockchain.com is a cryptocurrency financial services company that operates the Blockchain.com Explorer (one of the longest-running Bitcoin block explorers), a self-custody and custodial wallet, an institutional spot exchange, and Blockchain.com Pay, an embeddable fiat-to-crypto on-ramp and off-ramp for partners. Its public API surface spans the Exchange REST API (market data, trading, deposits and withdrawals, authenticated with an X-API-Token header), a FIX-named WebSocket trading and market-data gateway, the Pay Partner API (eligibility, quotes and orders, authenticated with public and private API key headers plus order webhooks), the free Blockchain Data, Simple Query, Exchange Rates and Charts & Statistics APIs on blockchain.info, a real-time blockchain WebSocket notification stream, an NFT Market API, and the open-source Wallet API service (service-my-wallet-v3) with first-party client libraries for Python, Node.js, Ruby, PHP and Java.

**Areas:** Cryptocurrency · Bitcoin · Blockchain · Exchange · Trading · Market Data · Payments · On-Ramp · Wallets · Block Explorer · Fintech · Webhook

## Blockchain.com on APIs.io

Everything profiled for Blockchain.com is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/blockchain.com/](https://apis.io/providers/blockchain.com/)** — or go straight to one of the APIs or properties below.

### APIs (28)

- [Blockchain.com Exchange WebSocket API](https://apis.io/apis/blockchain.com/blockchaincom-exchange-websocket-api/) — Real-time WebSocket gateway for the Blockchain.com Exchange. Anonymous channels stream heartbeat, L2/L3 order books, prices, symbols, ticker and trades;…
- [Blockchain Data API](https://apis.io/apis/blockchain.com/blockchain-data-api/) — Free JSON API over the Blockchain.com Explorer data set — single blocks, transactions, addresses, unspent outputs, block height and latest block queries for…
- [Blockchain.com Simple Query API](https://apis.io/apis/blockchain.com/blockchaincom-simple-query-api/) — Plain-text query API returning single values for blockchain statistics such as block count, difficulty, hash rate, total bitcoins in circulation, market cap…
- [Blockchain.com Exchange Rates API](https://apis.io/apis/blockchain.com/blockchaincom-exchange-rates-api/) — Ticker and currency-conversion API returning bitcoin exchange rates across major fiat currencies, aggregated from the major exchanges.
- [Blockchain.com Charts and Statistics API](https://apis.io/apis/blockchain.com/blockchaincom-charts-and-statistics-api/) — JSON/CSV feed behind the Blockchain.com charts and stats pages — per-chart time series, network statistics, and mining pool distribution.
- [Blockchain.com Explorer WebSocket API](https://apis.io/apis/blockchain.com/blockchaincom-explorer-websocket-api/) — Low-latency streaming socket channel providing notifications on new bitcoin blocks, unconfirmed transactions and watched addresses via the unconfirmed_sub,…
- [Blockchain.com NFT Market API](https://apis.io/apis/blockchain.com/blockchaincom-nft-market-api/) — Public backend service for NFT market data, returning NFT assets owned by an address and individual asset lookups by network, contract address and token id.…
- [Blockchain.com OAuth Resources API](https://apis.io/apis/blockchain.com/blockchaincom-oauth-resources-api/) — OAuth 2.0 resource gateway that lets a third-party app read a consenting user's Blockchain.com custodial wallet data. Two endpoints are documented —…
- [Blockchain.com Wallet API](https://apis.io/apis/blockchain.com/blockchaincom-wallet-api/) — Open-source Wallet API service (service-my-wallet-v3) that runs locally and exposes HTTP endpoints for creating wallets, sending payments, and checking…
- [Blockchain.com Eligibility API](https://apis.io/apis/blockchain.com/blockchain.com-eligibility-api/) — Available currencies, regions, and payment methods for the partner account.
- [Blockchain.com Nft API](https://apis.io/apis/blockchain.com/blockchain.com-nft-api/) — The nft API from Blockchain.com — 1 operation(s) for nft.
- [Blockchain.com Nft V2 API](https://apis.io/apis/blockchain.com/blockchain.com-nft-v2-api/) — The nft_v2 API from Blockchain.com — 2 operation(s) for nft_v2.
- [Blockchain.com Orders API](https://apis.io/apis/blockchain.com/blockchain.com-orders-api/) — Order listing and lookup.
- [Blockchain.com Payments API](https://apis.io/apis/blockchain.com/blockchain.com-payments-api/) — Get account status and initiate deposits and withdrawals
- [Blockchain.com Public API](https://apis.io/apis/blockchain.com/blockchain.com-public-api/) — The Public API from Blockchain.com — 3 operation(s) for public.
- [Blockchain.com Quote API](https://apis.io/apis/blockchain.com/blockchain.com-quote-api/) — Real-time buy quotes.
- [Blockchain.com Trading API](https://apis.io/apis/blockchain.com/blockchain.com-trading-api/) — Post orders and get information about historical trades
- [Blockchain.com Unauthenticated API](https://apis.io/apis/blockchain.com/blockchain.com-unauthenticated-api/) — Retrieve current prices and markets
- [Blockchain.com WebSocket APIs](https://apis.io/apis/blockchain.com/blockchaincom-websocket-apis/) — Real-time WebSocket APIs covering two distinct surfaces — the Bitcoin / blockchain.info explorer socket (unconfirmed transactions, new blocks, per-address…
- [Blockchain.com Pay Partner API](https://apis.io/apis/blockchain.com/blockchaincom-pay-partner-api/) — Partner API for embedding Blockchain.com crypto purchases. Covers authentication, eligibility (supported currencies / regions), quotes (pricing for crypto…
- [Blockchain.com Addresses API](https://apis.io/apis/blockchain.com/blockchain.com-addresses-api/) — Bitcoin address summaries and unspent outputs.
- [Blockchain.com Blocks API](https://apis.io/apis/blockchain.com/blockchain.com-blocks-api/) — Bitcoin block lookups and the latest block.
- [Blockchain.com Charts API](https://apis.io/apis/blockchain.com/blockchain.com-charts-api/) — Historical time-series datasets for Bitcoin network metrics.
- [Blockchain.com Market Data API](https://apis.io/apis/blockchain.com/blockchain.com-market-data-api/) — Bitcoin exchange rates and fiat conversion.
- [Blockchain.com Network API](https://apis.io/apis/blockchain.com/blockchain.com-network-api/) — Simple network metrics — difficulty, block height, supply, ETA, averages.
- [Blockchain.com Pools API](https://apis.io/apis/blockchain.com/blockchain.com-pools-api/) — Mining pool distribution.
- [Blockchain.com Stats API](https://apis.io/apis/blockchain.com/blockchain.com-stats-api/) — Real-time blockchain statistics.
- [Blockchain.com Transactions API](https://apis.io/apis/blockchain.com/blockchain.com-transactions-api/) — Bitcoin transaction lookups.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Blockchain.Com Event Surface](https://apis.io/asyncapis/blockchain.com/blockchain.com-event-surface/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [blockchain.com-mcp.yml](https://apis.io/servers/blockchain.com/blockchain-com-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Blockchain.Com Agentic Access](https://apis.io/agentic-access/blockchain.com/blockchain.com-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [Blockchain.Com Pay Webhook Event](https://apis.io/schemas/blockchain.com/blockchain.com-pay-webhook-event/)

#### Collections (1)

Postman and Open Collection request collections.

- [Blockchain.com Exchange REST Unauthenticated API](https://apis.io/collections/blockchain.com/open-blockchain/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Blockchain.Com Exchange Overlay](https://apis.io/overlays/blockchain.com/blockchain.com-exchange-overlay/)
- [Blockchain.Com Pay Partner Api Overlay](https://apis.io/overlays/blockchain.com/blockchain.com-pay-partner-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Blockchain.Com Authentication](https://apis.io/security/blockchain.com/blockchain.com-authentication/)
- [Blockchain.Com Domain Security](https://apis.io/security/blockchain.com/blockchain.com-domain-security/)
- [Blockchain.Com Vulnerability Disclosure](https://apis.io/security/blockchain.com/blockchain.com-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Blockchain.Com Scopes](https://apis.io/scopes/blockchain.com/blockchain.com-scopes/)

#### Rate limits (1)

Published request limits.

- [Blockchain.Com Rate Limits](https://apis.io/rate-limits/blockchain.com/blockchain.com-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.blockchain.com/)
- [Documentation](https://docs.blockchain.com/)
- [Getting started](https://docs.blockchain.com/pay/getting-started)
- [API reference](https://api.blockchain.com/v3/)
- [Pricing](https://www.blockchain.com/prices)
- [Sign up](https://login.blockchain.com/signup)
- [Support](https://support.blockchain.com/)
- [Blog](https://www.blockchain.com/blog)
- [Security](https://www.blockchain.com/.well-known/security.txt)
- [Compliance](https://www.blockchain.com/legal/licenses)
- [Terms of service](https://www.blockchain.com/legal/terms)
- [Privacy policy](https://www.blockchain.com/legal/privacy)
- [GitHub](https://github.com/blockchain)
- [Status](https://status.blockchain.com/)

## API Evangelist rating

**Kin Score 49.4** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 41.9 |
| Contract governance | 4.5 |
| Operational transparency | 52.6 |
| Developer ergonomics | 66.1 |
| Access clarity | 39.5 |

**Agent readiness 28.3** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
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
| Operation Distinctiveness | — |

**Regulatory alignment 41.1** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/blockchain.com/](https://apis.io/providers/blockchain.com/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Blockchain.com: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/blockchain.com/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
