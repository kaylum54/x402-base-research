# Digest: x402 platform, Coinbase, Base, Foundation, Cloudflare and big adopters (as of 2026-10-11)

Condensed from two research notes dated 2026-10-11 (`platform_coinbase_base_protocol.md`, `platform_cloudflare_and_adopters.md`). No new research. "Researcher" and "Inference" mark a researcher's judgement, not a sourced fact.

**Method limits.** GitHub figures come from `gh api` calls on 2026-10-11. Pages were read through a summarising fetch tool; key Coinbase figures were checked against slide images. Search budgets ran out in both notes; coinbase.com/blog, x402scan.com and x.com could not be opened.

**Corrections to the brief's leads.** (1) The canonical repo is `x402-foundation/x402`; `coinbase/x402` is a fork created 2026-04-02. (2) The official community channel is Slack (plus Telegram), not Discord. (3) The "deferred" idea now lives in `batch-settlement`; the schemes are exact, upto, batch-settlement and auth-capture. (4) The Linux Foundation move is confirmed by LF's own releases. (5) ERC-8004 is still formally "Draft". (6) Cloudflare's product is "Monetization Gateway", not "Gateway Monetization" (section 4).


---

## 1. Protocol state (as of 2026-10-11)

**Spec.** Still "x402 Protocol Version 2". V2 launched 2025-12-11 ([post](https://x402.org/x402-v2-launch/); CDP's changelog says 2025-12-18, [CDP](https://docs.cdp.coinbase.com/get-started/changelog)). No V3 file or label exists ([specs](https://github.com/x402-foundation/x402/tree/main/specs)). Change is additive and ships as SDK minors: `@x402/core` v2.0.0 (2025-12-11) to v2.28.0 (2026-09-29) ([tags](https://github.com/x402-foundation/x402/tags)). Inference: no V3 in sight. x402 was announced 2025-05-06 ([feed](https://x402.org/feed/)). V2 added CAIP network IDs, per-request `payTo` and dynamic pricing, PAYMENT-* headers, Sign-In-With-X (SIWX) sessions, a discovery extension and multi-facilitator support; its post cited "over 100M payments processed" and "600+ builders". No V1 deprecation date ([migration guide](https://docs.x402.org/guides/migration-v1-to-v2)).

**Schemes** ([overview](https://docs.x402.org/schemes/overview)). `exact`. `upto` (authorize a maximum, pay actual use): EVM spec merged 2026-03-04; CDP live about 2026-04-09 ([Cointelegraph](https://www.cointelegraph.com/news/coinbase-x402-rolls-out-usage-based-pricing-agentic-ai)); Solana 2026-09-14. `batch-settlement` (signed vouchers, one onchain claim): PR #1145 opened 2026-02-10, merged 2026-04-15 with Cloudflare's `cloudflare:402` binding; the PR says it unifies the earlier "deferred" PRs ([PR](https://github.com/x402-foundation/x402/pull/1145)); launch post 2026-05-11 ([post](https://x402.org/x402-batch-settlement/)). `auth-capture` (escrow, then capture, void or refund): spec files by 2026-05-20, built on Base's `commerce-payments` contracts, SDK code merged 2026-10-05 and 2026-10-06 ([commits](https://github.com/x402-foundation/x402/commits/main)).

**Chains.** EVM (any `eip155:<id>`), Solana, TON, Algorand, Stellar, Aptos, Hedera, NEAR, XRPL, Cardano, Bitcoin Lightning and others; 30+ EVM default assets, mostly USDC ([docs](https://docs.x402.org/core-concepts/network-and-token-support)). The x402.org facilitator is testnet only. SDKs: TypeScript (every network), Go (EVM and Solana), Python (lags on Solana and `auth-capture`), plus a Java folder ([SDK features](https://docs.x402.org/sdk-features)).

**Extensions.** First spec dates: Bazaar 2026-01-15, SIWX 2026-02-02, payment-identifier 2026-02-05, signed offers and receipts (draft) 2026-03-12, builder code (ERC-8021) 2026-05-04. Bazaar, a catalogue of endpoints and MCP tools "in early development", launched 2025-09-17; CDP added semantic search and an MCP surface 2026-04-14. An endpoint is listed only after a facilitator processes a paid request echoing `bazaar` ([docs](https://docs.x402.org/extensions/bazaar)).

**Who decides.** GitHub issues and PRs; merges are at the "x402 Foundation team's" discretion ([CONTRIBUTING](https://github.com/x402-foundation/x402/blob/main/CONTRIBUTING.md)). The Technical Steering Committee (TSC) charter, adopted 2026-03-31, gives three seats (Coinbase, Cloudflare, Stripe) and decides by majority; a 75% supermajority is needed to change Core Principles, remove a participating organisation, allow non-Apache licences or amend the charter; code is Apache-2.0 ([charter](https://github.com/x402-foundation/x402/blob/main/foundation/x402%20Technical%20Charter%20March%2031%2C%202026.pdf)). It meets bi-weekly ([tsc](https://github.com/x402-foundation/tsc)). Working-group repos: Identity (2026-08-03), Tax (2026-08-19), Domain Discovery (2026-09-14), Card Acceptance (2026-09-23); goals are still placeholders. `ROADMAP.md` says "(update coming soon)"; the last real roadmap is September 2025. Open proposals include post-settlement receipts (#2332, 232 comments), agent identity (#1777) and facilitator discovery via DNS (PR #2979), none decided.

**GitHub** (`gh api`, 2026-10-11). `x402-foundation/x402`: 6,702 stars, 2,158 forks, 695 open issues, last push 2026-10-10. `coinbase/x402` is a fork created 2026-04-02 (163 stars). Commits per month, including docs-bot ([history](https://github.com/x402-foundation/x402/commits/main)): Jan 95, Feb 128, Mar 128, Apr 67, May 115, Jun 82, Jul 81, Aug 109, Sep 102, Oct 1-10 15; 922 since 2026-01-01. No GitHub Releases; 672 package tags; `@x402/core` v2.10.0 2026-04-13, v2.20.0 2026-07-27. Top committers (all-time / since 2026-04-11): `phdargen` 234 / 187 (employer unconfirmed), `CarsonRoscoe` 210 / 42, `mintlify[bot]` 94 / 74.


---

## 2. Coinbase, CDP and Base

**Position.** Coinbase has moved from "owner of x402" to the largest commercial operator on an LF-governed standard: the main production facilitator, agentic.market, Agentic Wallet, Coinbase for Agents, Coinbase Business agent checkout and an x402 SDK. Researcher: "neutral protocol, commercial platform".

### 2a. Timeline, 2026-04-11 to 2026-10-11
Protocol dates are in section 1, Foundation dates in section 3. Some rows use changelog or commit dates, so launch days may differ.

| Date | Event | Source |
|---|---|---|
| 2026-04-14 | CDP CLI and MCP server; Bazaar gets semantic search, filters, ranking and an MCP surface. | [CDP](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-05-07 | Q1'26 results; x402 slide (see 2d). | [slide 15](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000053/q126earningsdeck-finalse015.jpg) |
| 2026-05-26 / 05-29 | Base MCP (pay for x402 services from Claude, ChatGPT, Codex, Cursor); Base post: x402 on Base, 30 days, 3.1M transactions, $1.2M. | [Base feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-06-12 to 07-17 | CDP: Coinbase CLI and MCP (first "Coinbase for Agents" entry, 06-12), x402 with Amazon Bedrock AgentCore, remote MCP connector for Claude and ChatGPT (06-19), `@coinbase/cdp-sdk/x402` with spend controls (07-17). | [CDP](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-07-23 | Coinbase Business: businesses accept agent payments via x402 in USDC on Base or other chains. About 5,000 customers and about $1 billion combined payments and trading volume since June 2025 (not x402-specific); about 53% of Base docs traffic agentic. | [The Block](https://www.theblock.co/post/409539/coinbase-ai-payments-most-high-conviction-bet-businesses-accepting-agent-payments) |
| 2026-07-30 | Q2'26 results; x402 slide (see 2d). | [slide 18](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/q226earningsdeck_sec018.jpg) |
| 2026-08-06 | CDP: Payment Acceptance GA; Checkouts return an `x402_url` payable by gasless USDC transfer on Base. | [CDP](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-09-10 / 09-14 | Rename: "Base Account is now Coinbase Wallet" (SDK README); CDP docs: "formerly known as Base App". CDP also adds Solana `upto` and a Java SDK (09-14). | [commits](https://github.com/base/account-sdk/commits/main/README.md), [CDP](https://docs.cdp.coinbase.com/get-started/changelog) |

Base chain, not x402-specific: Beryl (B20 token standard) went live 2026-06-25, with block-production outages on 2026-06-25 and 2026-06-26; Cobalt 2026-09-30; Denim targeted for November 2026 ([upgrades](https://docs.base.org/upgrades/overview)).

**Earlier milestones:** 2025-09-17 Bazaar launched; 2025-12-11 V2; 2026-01-15 facilitator billing starts; 2026-01-29 ERC-8004 registries live, including Base; 2026-02-11 Agentic Wallet; 2026-03-24 Polygon added to the CDP facilitator; 2026-03-31 Base strategy post; 2026-04-09/10 CDP `upto` live ([CDP](https://docs.cdp.coinbase.com/get-started/changelog)).

### 2b. CDP facilitator
- **Pricing:** first 1,000 onchain transactions a month free, then $0.001 each; verification free; only successful (2xx) settlements billed; no processor or chargeback fees; CDP pays settlement gas and holds no revenue (funds settle to `payTo`) ([facilitator](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator), [FAQ](https://docs.cdp.coinbase.com/x402/support/faq)).
- **Coverage:** Base, Base Sepolia, Polygon, Arbitrum, World, Solana. Exact, upto and batch-settlement on EVM; exact and upto on Solana. FAQ caveat: `createX402Server` does not register batch-settlement "because the server-side support was withdrawn". OFAC and Know-Your-Transaction screening applies.
- **Own scale claim** (undated): "more than 100 million transactions and $28 million in payment volume across Base and Solana".
- **Others:** the x402 docs list 15 "selected production" facilitators; only Corbits, PayAI, Polygon and T54 XRPL carry a "production-grade" label ([page](https://docs.x402.org/dev-tools/facilitators)).
- Researcher: the fee is small against an average payment and large against sub-cent ones, which likely explains the 2026 push for `upto` and batch-settlement (no source states the motive).

### 2c. Coinbase products
agentic.market is a Coinbase-run directory, "not an official product of the x402 Foundation", with 3,072 services in 10 categories on 2026-10-11 ([site](https://agentic.market)).

### 2d. Coinbase's published x402 metrics (scopes differ; do not mix)

| Date | Figure | Scope and source |
|---|---|---|
| 2026-05-07 | "100M+ total x402 payments processed as of Q1'26"; 99%+ of onchain agentic commerce in USDC; 90%+ of agentic stablecoin volume on Base. | Q1 deck, Artemis ([deck](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000053/q126earningsdeck-finalse.htm)) |
| 2026-07-30 | 97%+ of onchain agentic transactions used x402; 90%+ of agentic stablecoin volume on Base; 99%+ USDC (Q2'26). | Q2 deck, Artemis; identified "based on programmatic wallet signatures and HTTP 402 protocol interactions", EVM and Solana ([deck](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/q226earningsdeck_sec.htm)). |
| 2026-06-03 | Chainalysis: x402 wallets made 100M+ transactions on Base in about nine months; early growth driven by the PING memecoin experiment. | [Cointelegraph](https://cointelegraph.com/news/agentic-payment-activity-surpasses-100m-transactions-on-base) |
| 2026-07-28 | x402scan: 197.48M transactions, $52.51M, 846,110 buyers, 253,000 sellers (window not stated). | [Cointelegraph](https://cointelegraph.com/news/coinbase-ceo-agentic-finance-base-100-million-aifi-transactions) |
| fetched 2026-10-11 | x402.org "last 30 days": 75.41M transactions, $24.24M, 94.06K buyers, 22K sellers. | [x402.org](https://x402.org/) |
| 2026-05-29 | Base blog: x402 on Base, 30 days: 3.1M transactions, $1.2M, sellers +23%, buyers +37%. | [Base feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-04-10 | Dune via Cointelegraph: record week 2025-11-04 to 2025-11-10 at 13.7M transactions; under 1M a week in early January 2026; 112,708 in the last week of March. | [Cointelegraph](https://www.cointelegraph.com/news/coinbase-x402-rolls-out-usage-based-pricing-agentic-ai) |

Researcher: the Artemis method finds agentic activity partly through HTTP 402 interactions, so "97%+" is close to definitional. Average payments work out at about $0.27 to $0.39 across these pairs (arithmetic). Coinbase has published no seller count. The x402.org figure may be stale (section 9).

### 2e. Coinbase Ventures bets
**Coinbase Ventures x402 bets: not established** (coinbase.com/ventures returned 403). Only overlap: the Base Ecosystem Fund works "in partnership with Coinbase Ventures"; its 39-company portfolio includes Blockrun (x402 pay-per-call AI router); Batches 003 x402 teams were Blockrun.ai, 4Mica, Agently and Floe Labs ([fund](https://www.base.org/ecosystem-fund)). The Q2 2026 10-Q names no 2026 acquisitions ("immaterial, both individually and in the aggregate"), though its MD&A was not shown ([10-Q](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000088/coin-20260630.htm)).

### 2f. Base's agent strategy
- **Strategy post, 2026-03-31:** pillars are global markets, payments and stablecoins, and a home for builders. Agents get "agent-native smart accounts, documentation, CLI and MCP access, and standards like x402 to help agents do anything with money". 2025 results cited: over $17T stablecoin volume, Base App in 140+ countries, 50+ Batches teams funded ([Base feed](https://api.paragraph.com/blogs/rss/@base)).
- base.org/agents lists x402, ERC-8004, Agentic Wallets and Base MCP as its agent stack ([page](https://www.base.org/agents)). The 2026-07-16 Request for Builders (everyday-purchase agents) mentions neither x402 nor ERC-8004. Base also markets tokenized stocks.
- Batches 003 (2026-04-06 to 2026-05-19) had 12 teams, "a few" on x402; Batches 004 (applications 2026-08-19 to 2026-09-09 or 09-10, demo day 2026-11-17) has $100K per team and no x402 track ([Batches](https://www.base.org/batches)).
- Token: 2025-09-15 Base said it is "beginning to explore a network token"; nothing newer in the 2026 posts read.
- Researcher: Base's roadmap targets trading, stablecoins and wallets; agent payments mostly point to x402 and Coinbase tooling. 3.1M transactions a month at about $0.39 is small beside $17T of stablecoin volume: a growth bet, not yet a volume driver.


---

## 3. x402 Foundation

**State.** The Linux Foundation (LF) hosts the "x402 Foundation" (a directed fund) plus a technical project, "x402 a Series of LF Projects, LLC". The members page read on 2026-10-11 shows 58 organisations ([members](https://x402.org/members/)). Technical oversight sits with a three-seat TSC (Coinbase, Cloudflare, Stripe).

**Timeline**
- 2025-09-23: Cloudflare says it and Coinbase "will launch" a neutral x402 Foundation; Erik Reppel is "creator of x402 and Head of Engineering for Coinbase Developer Platform" ([Cloudflare](https://www.cloudflare.com/press/press-releases/2025/cloudflare-and-coinbase-will-launch-x402-foundation/)).
- 2026-03-31 Technical Charter adopted; 2026-04-01 `x402-foundation` GitHub org created.
- 2026-04-02: LF release (New York): LF "is launching the x402 Foundation"; Coinbase contributes the protocol; Coinbase, Cloudflare and Stripe initially developed it. 22 organisations with "initial intent and support" (including AWS, Google, Mastercard, Microsoft, Shopify, Visa). No board, TSC or tiers described ([LF](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol)).
- 2026-05-12: `TSC.md` names the TSC representatives: Erik Reppel (Coinbase), Rohin Lohe (Cloudflare), Steve Kaliski (Stripe) ([TSC.md](https://github.com/x402-foundation/x402/blob/main/TSC.md)).
- 2026-07-14: operational launch (San Francisco): Coinbase's contribution complete; 40 organisations joined since April ([release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/)). 2026-08-13: directed-fund charter "Amended August 13, 2026".
- 2026-10-01: Hursta appointed ([release](https://x402.org/linux-foundation-appoints-michael-hursta-as-executive-director-of-the-x402-foundation/)).

**Governance.** The Governing Board has one representative per Premier member (cap 25 Premier seats) plus General-member representatives (one per ten members, up to three); officers are a Chair and a Treasurer. Premier needs substantial x402 investment (for example 2.0 FTE or more of technical resources). Dues: Premier $200,000; General $25,000 to $75,000 by headcount; Associate $0 for academic and nonprofit bodies ([agreement](https://cdn.platform.linuxfoundation.org/agreements/x402-foundation.pdf), [members](https://x402.org/members/)). Technical decisions follow the TSC charter (section 1). Core Principles include "open standard", "trust minimizing" and "will never deprioritize onchain payments in favor of fiat" ([README](https://github.com/x402-foundation/x402/blob/main/README.md)).

**Members.** 2026-07-14: Premier (17) Adyen, AWS, American Express, Circle, Cloudflare, Coinbase, Fiserv, Google, Mastercard, Monad Foundation, MoonPay, Ripple, Shopify, Solana Foundation, Stellar Development Foundation, Stripe, Visa; General (18) includes Fireblocks, KakaoPay, LayerZero Labs, Polygon Labs, World Liberty Financial and zerohash. Members page 2026-10-11: Premier 19 (adds PayPal and Sui), General 27, Associate 12, total 58; the 2026-10-01 release says "more than 50 active members". April names absent from the later lists: Base (as a separate entity), Microsoft, Ampersend.ai, PPRO, Sierra, thirdweb (researcher: probably not enrolled yet; no sign of withdrawal).

**Leadership.** Michael Hursta: 20+ years in payments; most recently Partner at Commerce Technology Partners; earlier PwC (enterprise payments advisory), Amazon (North America payment acceptance) and over a decade at First Data. Start date not stated; no board chair or officers named. Lincoln Murr (Coinbase Head of AI Product) said in July that "x402 began at Coinbase".

**Researcher's view.** Neutral on paper (LF holds the trademarks, Apache-2.0, supermajority rules, Coinbase one of 19 Premier seats), but Coinbase holds the first TSC seat and is the heaviest code contributor, so its practical influence stays large. The 2.0 FTE rule is a more meaningful filter than the $200,000 dues. Unpublished: board members, chair, treasurer, an official X account.


---

## 4. Cloudflare and the "Gateway Monetization" claim

**Claim:** Cloudflare released a closed-beta product called "Gateway Monetization" that lets agents make autonomous payments.

**Verdict (from the notes).** The product is **Monetization Gateway** (the claim reversed the words): a US-only closed beta, available 2026-09-30 after a waitlist announced 2026-07-01. It is the seller side. The agent wallet that would make payments autonomous is a separate product, Cloudflare Wallets, where only handle reservation is live. The notes' one-line version: Cloudflare opened a closed beta (US only) that lets website and API owners charge AI agents per request using x402 and USDC on Base; the matching agent wallet is announced but not live.

**Product facts**
- **Name and status.** Changelog entry dated 2026-09-30: "Monetization Gateway is now available in closed beta." (the only direct quote in the notes). It names charging agents for APIs, MCP tools, sites and datasets as its use; access is requested from the dashboard ([changelog](https://developers.cloudflare.com/changelog/post/2026-09-30-closed-beta/)). Announced 2026-07-01 as a waitlist (authors Rohin Lohe, Justin Ridgely, Will Papper) ([post](https://blog.cloudflare.com/monetization-gateway/)). Closed-beta post 2026-09-30, a Birthday Week 2026 item ([beta post](https://blog.cloudflare.com/monetization-gateway-beta/)).
- **Docs** (labelled closed beta): [hub](https://developers.cloudflare.com/monetization-gateway/), [Eligibility](https://developers.cloudflare.com/monetization-gateway/eligibility/), [Get started](https://developers.cloudflare.com/monetization-gateway/get-started/), [x402](https://developers.cloudflare.com/monetization-gateway/x402/). Contact x402@cloudflare.com.
- **How it works.** The seller sets rules (URL, headers, query parameters or caller attributes), a price and a wallet. The buyer requests the resource, gets a 402, signs a payment authorization and retries. The gateway verifies it, passes a signed payment context to the origin, settles through the Coinbase x402 Facilitator and returns the resource. It uses x402 v2: `exact` for fixed prices; `upto` for variable ones, where the origin reports the actual amount in a signed JWT (`PAYMENT-CONTEXT` header). Settlement is USDC on Base (beta post); the July post named only "stablecoins". Payments go peer-to-peer to the seller's wallet. It is neither NET Dollar nor pay per crawl.
- **Pricing.** No Cloudflare fee appears on any page read. The docs give one number: a minimum price of $0.001 per request. Search Engine Journal (2026-10-01) reported a $0.001 to $100 range; the $100 ceiling is not in the docs ([SEJ](https://www.searchenginejournal.com/cloudflare-moves-monetization-gateway-pay-per-use-into-beta/591719/)). The facilitator is Coinbase's: 1,000 free onchain transactions a month, then $0.001 each ([CDP](https://docs.cdp.coinbase.com/x402/seller/facilitator)). Who bears that fee inside the Gateway is not stated.
- **Eligibility.** Buyers and sellers must both be US-based. Sellers need a card on file, a verified email and an account older than 60 days; the zone must be proxied through Cloudflare and older than 30 days. Other regions are "coming", no dates.
- **Beta users:** Cloudflare AI Gateway, Ceramic.ai, Stocktwits, API2PDF. No volumes or payouts published.

**What the claim got right**
- A closed beta, released 2026-09-30 (waitlist since 2026-07-01).
- Agents pay over x402; each signs a per-request payment authorization.
- "Very early" fits the Gateway: closed beta, US-only, four launch users, no published volumes.

**What the claim got wrong**
- The name: Monetization Gateway, not Gateway Monetization.
- "Lets agents make autonomous payments" is only partly right. The Gateway lets sellers charge agents. The agent wallet (Cloudflare Wallets) is a separate product, not yet funded or spendable. Buyers need an x402-capable client or wallet; Cloudflare's Agents SDK has had one since 2025-09-23 ([post](https://blog.cloudflare.com/x402/)).
- "Very early" does not fit x402 itself (announced 2025-05-06; Visa's data article also dates its launch to May 2025, [Visa](https://www.visa.com/en-us/thought-leadership/innovation/agentic-payments-from-the-ground-up)) or Cloudflare's SDK support (2025-09-23).

**What the claim left out**
- The US-only limit and seller requirements; x402 v2 over USDC on Base via Coinbase's facilitator; no published Cloudflare fee; the $0.001 minimum; the sister products (Wallets, AI Gateway Machine Payments, Pay Per Use, pay per crawl).

**Where the name may come from (inference).** "Gateway Monetization" may blend AI Gateway (a Gateway launch user) with Monetization Gateway; AI Gateway Machine Payments, a separate x402 beta, shipped the same day. Executive phrasing runs ahead of product too: on 2026-09-09 Cloudflare's CFO described Wallets in the present tense, though the docs (2026-08-19) showed handle reservation only. Gap: when the claim was made is unknown, so not whether he described the July waitlist or the September beta.

### Cloudflare's other related products, dated

| Date | Product or event | Status | Source |
|---|---|---|---|
| 2025-07-01 | Pay per crawl: crawlers on a paid URL get a 402 with a price header; Cloudflare is merchant of record and pays publishers. Web Bot Auth signs crawler and agent requests (2025-05-15). Docs (2026-07-28) still say closed beta and do not mention x402 or the Gateway. AI Crawl Control (GA 2025-08-27) adds custom 402 block responses. | beta | [post](https://blog.cloudflare.com/introducing-pay-per-crawl/), [docs](https://developers.cloudflare.com/ai-crawl-control/features/pay-per-crawl/what-is-pay-per-crawl/) |
| 2025-09-23 | Agents SDK clients pay with x402; MCP servers expose paid tools; testnet playground. Docs (2026-06-03): `exact` on EVM, Solana, Aptos, Stellar, Hedera, Sui; `upto` on EVM only. MPP (Machine Payments Protocol, "backward-compatible with x402") added by 2026-08-05. | shipped | [post](https://blog.cloudflare.com/x402/), [docs](https://developers.cloudflare.com/agents/tools/payments/x402/) |
| 2025-09-25 | NET Dollar, a USD-backed stablecoin for agent payments, announced; no issuer, chain or date; the site still says launch pending. Unconfirmed reports (about 2026-03-18) said Coinbase and Zerohash were competing to issue it. Cloudflare is also a partner of Open USD (live on Tempo, 2026-09-30). | announced; issuer rumoured | [CoinDesk](https://coindesk.com/business/2025/09/25/cloudflare-unveils-u-s-dollar-stablecoin-for-ai-powered-internet-economy), [site](https://netdollar.cloudflare.com/) |
| 2026-08-04 | Wallets and cloudflare.pay: Account Wallets for humans; Virtual Wallets for agents (allowance cap, allow list, maximum transaction size); identity handles; funding and spending "coming". Docs (2026-08-19): a handle cannot hold funds; no chains, fees or date. | announced | [post](https://blog.cloudflare.com/wallets/), [docs](https://developers.cloudflare.com/wallets/) |
| 2026-09-30 | Bundle with the Gateway: AI Gateway Machine Payments beta (open-model inference paid by x402 via a `Payment-Method: x402` header; US base and card on file) and Pay Per Use beta (AI buyers offer a price per use; Cloudflare bills them and pays publishers monthly; x402 not involved). | beta | [machine payments](https://developers.cloudflare.com/changelog/post/2026-09-30-machine-payments/), [Pay Per Use](https://blog.cloudflare.com/pay-per-use/) |

**Executives** (paraphrase; third-party transcripts). 2025-10-30, Matthew Prince: Cloudflare will not issue an agent currency alone, for regulatory reasons. 2026-06-09, Stephanie Cohen: more than two billion 402 responses a day cross the network, most not leading to a transaction. 2026-08-06, Prince: Gateway, Wallets and cloudflare.pay are marketplace building blocks, with no timing, revenue or take-rate guidance ([Q2 2026](https://stockanalysis.com/stocks/net/transcripts/662709-q2-2026/)).

**Researcher's inferences.** Cloudflare is the toll booth plus identity layer and hedges on rails: x402 over USDC on Base for the Gateway, MPP in its SDK, a fiat merchant-of-record binding (`cloudflare:402`) for pay per crawl. NET Dollar looks deprioritized (no 2026 product page uses it; executives stopped naming it after October 2025), though Cloudflare has not said so. Its 402 counts (over a billion a day in 2025-09, over two billion in 2026-06) are mostly block responses, not payments.


---

## 5. Big adopters

| Company | What shipped with x402 | Status | Date | Chain | Source |
|---|---|---|---|---|---|
| AWS | Bedrock AgentCore Payments: x402 plus MPP, Coinbase and Stripe/Privy wallets; GA adds x402 `upto` and session budgets. Customers named include Anchor Browser, BlockRun and Travala. No pricing stated. | shipped (GA) | preview 2026-05-07; GA 2026-08-18 | USDC; Base confirmed only in AWS reference code | [GA](https://aws.amazon.com/blogs/machine-learning/amazon-bedrock-agentcore-payments-is-now-generally-available-enabling-agents-to-transact-safely-and-autonomously-at-scale/), [preview](https://aws.amazon.com/blogs/machine-learning/agents-that-transact-introducing-amazon-bedrock-agentcore-payments-built-with-coinbase-and-stripe/) |
| Circle | Nanopayments (x402-compatible, gas-free batched USDC, minimum $0.000001); Agent Stack; Arc layer 1 (Circle cites 98.8% of agent-driven volume in USDC; method unstated). | shipped | testnet 2026-03-10; mainnet 2026-04-29; Arc 2026-09-16 | 11 EVM chains incl. Base; Arc | [mainnet](https://www.circle.com/blog/nanopayments-powered-by-circle-gateway-is-now-live-on-mainnet), [Arc](https://www.circle.com/pressroom/circle-launches-arc-mainnet-an-economic-operating-system-for-the-internet) |
| Cloudflare | Monetization Gateway (closed beta, US only); AI Gateway Machine Payments (beta); Agents SDK and MCP x402 (shipped); Wallets announced. See section 4. | beta | SDK 2025-09-23; beta 2026-09-30 | USDC on Base; Base Sepolia in SDK examples | [beta post](https://blog.cloudflare.com/monetization-gateway-beta/) |
| Stripe | Accepts x402 as PaymentIntents (preview); prefers MPP (with Tempo); mainnet x402 settles via the CDP facilitator; minimum 0.01 USDC. | beta (preview) | 2026-02-10 (via The Block and Jeff Weinstein's X post; Stripe's page not read) | x402: USDC on Base; MPP: Tempo, Solana | [The Block](https://www.theblock.co/post/389352/stripe-adds-x402-integration-usdc-agent-payments), [docs](https://docs.stripe.com/payments/machine) |
| Vercel | `x402-mcp` and an x402 AI Starter template; no 2026 update found; a logo on x402.org, not a member. | shipped | 2025-09-12 | mostly USDC on Base | [blog](https://vercel.com/blog/introducing-x402-mcp-open-protocol-payments-for-mcp-tools) |
| Google | AP2 with an A2A x402 extension, called production-ready by Google. Repo `a2a-x402`: 564 stars, no releases, commit gap 2025-11-12 to 2026-05-14. AP2 v0.2.0 adds x402 samples. | shipped (thin) | 2025-09-16; 2026-04-28 | USDC on Base, x402Version 1 (the Gateway uses v2) | [blog](https://cloud.google.com/blog/products/ai-machine-learning/announcing-agents-to-payments-ap2-protocol), [repo](https://github.com/google-agentic-commerce/a2a-x402) |
| Visa | No first-party x402 product. Its Intelligent Commerce Connect pilot supports TAP, MPP, ACP and UCP, not x402; a Nevermined pilot links Visa Intelligent Commerce to x402 (Visa executive quote, no endorsement). Visa's data article (Artemis): about $15.0M over 109.6M transactions since May 2025, as of 2026-04-21. | none first-party | 2026-04-08 | n/a | [Visa](https://investor.visa.com/news/news-details/2026/Visa-Opens-the-Door-to-AI-Driven-Shopping-for-Businesses-Worldwide/default.aspx), [data](https://www.visa.com/en-us/thought-leadership/innovation/agentic-payments-from-the-ground-up) |
| Mastercard | Agent Pay for Machines (cards, accounts, stablecoins) with 32 partners including Cloudflare, Coinbase, Stripe and Tempo; only Coinbase's quote mentions x402. | announced | 2026-06-10 | none named | [Mastercard](https://investor.mastercard.com/investor-news/investor-news-details/2026/Mastercard-Launches-Agent-Pay-for-Machines-to-Unlock-Super-Fast-Always-On-Payments/default.aspx) |
| OpenAI | Example only: a cookbook with AWS (AgentCore Payments, x402 merchant; default path is local simulation). Agents SDK maintainers closed built-in x402 requests on 2026-03-27 and 2026-09-27. | none (example) | 2026-08-13 | Base Sepolia USDC | [cookbook](https://developers.openai.com/cookbook/examples/partners/aws/controlled_agentic_commerce_with_agentcore_payments/controlled_agentic_commerce), [issue](https://github.com/openai/openai-agents-python/issues/5183) |

**No x402 product found:** Shopify (Premier member; auth-capture reuses Base's `commerce-payments` contracts, "also used by Shopify": contract reuse, not a product); Microsoft (April intent list only); PayPal (Premier on the 2026-10-11 members page); Anthropic (its commerce blueprint excludes payment processing); Akamai (2026-06-15 framework with pay-per-request via TollBit and Skyfire). Fastly shipped only a tutorial (a Compute demo of an x402 challenge at $0.001 on Base Sepolia, 2026-07-27; not a production architecture, per its author) ([blog](https://www.fastly.com/blog/automated-payments-at-the-edge-with-x402-and-fastly-compute)). PayPal, Shopify and Microsoft products were not searched.

**Rumoured or overstated:** a Heurist post says OpenAI is adopting x402 with AgentCore (the cookbook is a testnet example); an X post says Akamai and Fastly are founding Foundation members (neither is on the LF lists); a syndicated headline says Cloudflare "wired 20% of the web" for agent payments (the body says only that it carries about 20% of web traffic and is not fully live, [Lifeboat](https://lifeboat.com/blog/2026/08/cloudflare-just-wired-20-of-the-web-for-ai-agent-payments)); Cloudflare's CFO said on 2026-09-09 that every credit card and large fintech company is part of this effort, though the evidence is membership and identity partnerships, not x402 in their products.

**Researcher's reading.** None of the seven company quotes in the April LF release (Cloudflare, Google Cloud, AWS, Visa, Mastercard, Stripe, Shopify) claims a shipped x402 product; only AWS, Circle, Stripe (preview), Vercel and Cloudflare (beta) have product work behind it. Stripe and Visa hedge toward MPP. OpenAI and Anthropic are absent from the Foundation, so expect no near-term native x402 there. AWS GA is the clearest sign of x402 in managed enterprise tooling, relying on Coinbase and Stripe/Privy wallets.


---

## 6. ERC-8004 and other adjacent standards

**ERC-8004 ("trustless agents"): Draft, with live contracts.**
- Status: Standards Track ERC, created 2025-08-13. Moved to Review on 2025-10-08 (#1244); set back to Draft by the EIP editors on 2026-01-13 (#1470) ([EIP](https://eips.ethereum.org/EIPS/eip-8004), [history](https://github.com/ethereum/ERCs/commits/master/ERCS/erc-8004.md)). Authors: Marco De Rossi, Davide Crapis, Jordan Ellis and Erik Reppel (the notes name MetaMask, the Ethereum Foundation, Google and Coinbase; Ellis's and Crapis's affiliations are inferred from EIP headers).
- Design: Identity (ERC-721), Reputation (signed feedback) and Validation (0 to 100 score) registries.
- Deployed: mainnet contracts committed 2026-01-29; the same IdentityRegistry `0x8004A169FB4a3325136EB29fA0ceB6D2e539a432` and ReputationRegistry `0x8004BAa17C55a88189AE136b182e5fdA19dE9b63` are listed on Ethereum, Base, Arbitrum, Optimism, Polygon, Monad, Scroll and others; later additions Injective (2026-04-09), 0G (2026-06-11), Robinhood Chain (2026-08-15). No Validation Registry address is listed ([contracts](https://github.com/erc-8004/erc-8004-contracts/commits/master)).
- Link to x402: none in the x402 spec. The EIP calls payments "orthogonal"; its registration file has an `x402Support` flag and its feedback file a `proofOfPayment` field "used for x402 proof of payment". Reppel co-authored 8004 and created x402. The x402 Identity working group (repo 2026-08-03) has published no goals. AgentKit has an 8004 identity provider (2026-03-23); base.org/agents lists 8004 as a pillar.
- Researcher: registries went live about two weeks after the EIP went back to Draft, so "deployed" and "final" differ; say "Draft standard, live contracts". The tie to x402 is shared authors and examples, not a formal dependency.
- Gap: no primary count of registered agents (a search snippet said about 21,000 in February 2026, Ethereum above 11,000).

**Other adjacent standards**
- **ERC-8021 builder codes:** Base's attribution standard, used by the x402 builder-code extension and CDP settlement calldata.
- **Machine Payments Protocol (MPP):** Stripe and Tempo; launched with Tempo mainnet 2026-03-18 (rests on a blog index). Cloudflare says it is backward-compatible with x402; AWS and Cloudflare's SDK support both; Stripe's docs steer to MPP; Visa's pilot supports MPP, not x402 ([mpp.dev](https://mpp.dev/)).
- **Web Bot Auth** (RFC 9421): identity, not payment; Visa's Trusted Agent Protocol and Mastercard Agent Pay build on it. **Google AP2** carries an A2A x402 extension (section 5). **Stablecoins:** NET Dollar (announced 2025-09-25, not launched) and Open USD (live on Tempo per Tempo, 2026-09-30).


---

## 7. People to follow

Handles are listed only where an official page or the person's own profile links them. The researchers could not open x.com, so they verified handles, not posting activity. Confidence labels are theirs.

| Name | Organisation and role | X handle | How verified (confidence) |
|---|---|---|---|
| Erik Reppel | Coinbase. x402 creator; Head of Engineering, CDP; Coinbase TSC representative; ERC-8004 co-author. | @programmer | GitHub `erikreppel` lists it; that account made the 2026-05-12 "Update footer to Linux Foundation (#2283)" commit. No Coinbase page links it. (Medium-high) |
| Lincoln Murr | Coinbase Head of AI Product; community-facing product owner (inference). | @murrlincoln | The x402 repo says "reach out to @murrlincoln on X or GitHub"; name-to-login match is by resemblance. (High) |
| Carson Roscoe | Coinbase engineer; V2 and batch-settlement post author. | @carsonroscoe7 | Personal site linked from GitHub; dated, names no employer. (Medium) |
| Jnix2007 | CDP product lead for wallets, onchain tools and agentic commerce (GitHub bio). | @Jnix2007 | GitHub self-declared; not confirmed as Josh Nickerson, the V2 co-author. (High for handle) |
| Brian Armstrong | Coinbase CEO. | @brian_armstrong | GitHub `barmstrong` declares it. (High) |
| Ash (`Must-be-Ash`) | CDP DevRel and product designer. | @Must_be_Ash | GitHub self-declared. (High) |
| Amanda McDermott (`apmcdermott`) | Coinbase; payment-identifier extension. | @flyingkittans | GitHub self-declared; may be personal. (Medium) |
| Jesse Pollak | Created and leads Base. | @jessepollak | jesse.xyz and GitHub both declare it. (High) |
| Marco De Rossi, Davide Crapis | ERC-8004 co-authors. | @marco_derossi, @DavideCrapis | "ERC-8004 team" accounts in the org README; name match by resemblance. (Medium) |
| Notorious D.E.V. | PayAI; x402 contributor (33 commits). | @notorious_d_e_v | GitHub self-declared. (High) |
| Other contributors | Sam Ragsdale (`sragss`) @samrags_; Gui Bibeau @GuiBibeau and Ludo Galabru @ludo_txtx (Solana Foundation); Faris Habib (Opto AI) @frshbb; Misha Kolesnik (`tenequm`) @opwizardx; `wnjoon` @216___x; Efe Baran Durmaz @efebarandurmaz. | as listed | GitHub `twitter_username` fields, self-declared. (High) |
| Matthew Prince | Cloudflare co-founder and CEO. | @eastdakota | Cloudflare blog author card (2025-07-01 post). (High) |
| Will Allen | Cloudflare; wrote the pay per crawl, x402 and Visa/Mastercard posts; title unverified. | @williamallen | Author cards on two posts. (High for handle) |
| Sunil Pai | Cloudflare engineer; top Agents SDK contributor (976 contributions). | @threepointone | GitHub profile lists Cloudflare. (High, self-declared) |
| Brendan Irvine-Broque | Cloudflare; senior director of product, Workers (GitHub bio). | @irvinebroque | GitHub field. (High, self-declared) |
| Matt Carey | Cloudflare, agents and MCP; MCP v2 post author. | @mattzcarey | GitHub field. (High; adjacent to payments) |
| Jeff Weinstein | Stripe product lead. | @jeff_weinstein | The Block embeds his 2026-02-10 x402 preview post. (Medium-high) |
| Ethan Niser | Vercel; x402-mcp post author. | @ethanniser | GitHub field; name matches byline. (Medium-high) |
| Guillermo Rauch | Vercel CEO (GitHub company field). | @rauchg | GitHub website field. (Medium-high) |

**Organisation accounts:** @coinbase (the only X account linked from investor.coinbase.com), @CoinbaseDev (`cdp-sdk` README), @base (GitHub org field and base.org footer), @buildonbase and @baseapp (base.org links), @Cloudflare (blog and docs metadata). No Foundation account found.

**Named, no verified handle:** Michael Hursta (Foundation Executive Director); Jim Zemlin (LF CEO); Rohin Lohe (Cloudflare) and Steve Kaliski (Stripe), the other TSC representatives; Stephanie Cohen (Cloudflare Chief Strategy Officer); Thomas Seifert (Cloudflare CFO); Josh Nickerson, Conner Swenberg and Philippe d'Argent (Coinbase batch-settlement authors; top committer `phdargen` has an empty profile and no source ties it to d'Argent); Shan Aggarwal (Coinbase Chief Business Officer); Siddharth Coelho-Prabhu (Head of Coinbase Business); Preethi C N (AWS director, AgentCore; LinkedIn linkedin.com/in/preethi-cn-a3064460).

**Researchers' judgement:** Reppel's three hats (x402 creator, Coinbase TSC seat, ERC-8004 co-author) make him the best single person to follow for protocol direction. For Cloudflare, company accounts, changelog feeds and blog tag feeds cover the payments team better than individuals, because the product managers who write the Gateway and Wallets posts link no handles.


---

## 8. Official tracking sources

**Daily poll list (researchers' inference).** x402.org feed, the two GitHub Atom feeds, CDP changelog RSS, the two Base RSS feeds, then the TSC issues; Coinbase's 8-K earnings decks on results days. For Cloudflare: the x402 tag feed, the Monetization Gateway and AI Gateway changelog feeds, the Wallets docs page (it shows a last-updated date) and the IR events page for the Q3 2026 call. Docs and changelogs move faster than blogs.

- **x402 and Foundation.** Feed https://x402.org/feed/ (5 items: 2025-05-06, 2025-12-11, 2026-05-11, 2026-07-14, 2026-10-01; valid RSS). Tags https://github.com/x402-foundation/x402/tags.atom (every package release; valid; newest 2026-09-29). Commits https://github.com/x402-foundation/x402/commits/main.atom (about 100 a month; standard pattern, not fetched). Repo https://github.com/x402-foundation/x402, TSC issues https://github.com/x402-foundation/tsc/issues, docs index https://docs.x402.org/llms.txt. **Do not use** https://github.com/coinbase/x402/releases.atom: it is the old fork's feed, newest items 2026-04-13.
- **Community.** Slack at slack.x402.org (invite on https://x402.org/get-involved/) is the official workspace: `#tsc-public`, `#github-discussions`, `#general`, working-group channels; it is "not an official system of record". Telegram https://t.me/+ijgZ6c_f0iA1MmY5 (activity unchecked). Mailing lists https://lists.x402.org/g/TSC (also /g/Domain-Discovery, /g/Identity-Working-Group, /g/tax-working-group, /g/Card-Acceptance-Working-Group). **Discord:** none official for x402; CDP has https://discord.com/invite/cdp and Base has https://discord.gg/buildonbase.
- **Coinbase and CDP.** Changelog https://docs.cdp.coinbase.com/get-started/changelog/rss.xml (valid RSS); docs index https://docs.cdp.coinbase.com/llms.txt; facilitator page https://docs.cdp.coinbase.com/x402/core-concepts/facilitator and FAQ https://docs.cdp.coinbase.com/x402/support/faq (watch for pricing changes; the Cloudflare note cites /x402/seller/facilitator); repos github.com/coinbase/cdp-sdk, /agentkit, /agentic-wallet-skills, /spend-permissions; https://agentic.market; SEC 8-Ks https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=0001679788&type=8-K (Q2 was 2026-07-30; Q3 date not found). coinbase.com/blog and the CDP Discover page returned 403; no RSS verified.
- **Base.** Blog RSS https://api.paragraph.com/blogs/rss/@base (site blog.base.org; items to 2026-09-01) and engineering RSS https://api.paragraph.com/blogs/rss/@base-engineering-blog (site blog.base.dev); upgrades https://docs.base.org/upgrades/overview; docs index https://docs.base.org/llms.txt; Batches https://www.base.org/batches; repos github.com/base/base, /docs, /skills, /account-sdk, /commerce-payments.
- **Cloudflare.** Blog feeds https://blog.cloudflare.com/rss/ and https://blog.cloudflare.com/tag/x402/rss/ (both valid); changelog feeds under https://developers.cloudflare.com/changelog/rss/ (index.xml, monetization-gateway.xml, ai-crawl-control.xml, ai-gateway.xml, agents.xml, bots.xml); docs https://developers.cloudflare.com/monetization-gateway/, /wallets/, /agents/tools/payments/, /ai-gateway/features/machine-payments/; IR https://cloudflare.net/news/default.aspx and https://cloudflare.net/events-and-presentations/default.aspx (email alerts; no RSS listed); x402@cloudflare.com.
- **ERC-8004.** https://eips.ethereum.org/EIPS/eip-8004 ; discussion https://ethereum-magicians.org/t/erc-8004-trustless-agents/25098 ; contracts https://github.com/erc-8004/erc-8004-contracts ; X @marco_derossi, @DavideCrapis; Telegram @ERC8004.
- **Other companies.** Google https://ap2-protocol.org/ ; Stripe https://docs.stripe.com/payments/machine ; https://mpp.dev/ ; AWS https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/payments.html (AWS blogs normally expose /feed/; not fetched); Vercel https://vercel.com/atom (valid; no x402 items).
- **X accounts:** @coinbase, @CoinbaseDev, @base, @buildonbase, @baseapp, @Cloudflare, plus the people in section 7. No Foundation account found.
- **Newsletters:** none verified for x402, CDP, Base or the Foundation. The CDP changelog RSS and the TSC and working-group mailing lists are the closest equivalents.


---

## 9. Conflicts and gaps

**Conflicts between the notes, or inside their sources**
1. **The x402.org "last 30 days" figures may be stale.** The Coinbase note reads 75.41M transactions and $24.24M on 2026-10-11 as live ([x402.org](https://x402.org/)). The Cloudflare note finds the same $24.24M quoted by Circle as of 2026-04-29 ([Circle](https://www.circle.com/blog/introducing-circle-agent-stack-financial-infrastructure-for-the-agentic-economy)) and on a page updated 2026-08-25, and calls it a possibly non-refreshing dashboard.
2. **Usage figures use different definitions; do not mix them:** Visa/Artemis about $15.0M over 109.6M transactions since May 2025 (as of 2026-04-21); CDP 100M+ and $28M (undated); x402scan 197.48M and $52.51M (2026-07-28); Base 3.1M and $1.2M in 30 days to 2026-05-29.
3. **Repo and dates.** The Cloudflare note's spec and releases-feed links point at the `coinbase/x402` fork (feed newest items 2026-04-13, [fork feed](https://github.com/coinbase/x402/releases.atom)), not the canonical `x402-foundation/x402`. It dates the `cloudflare:402` doc 2026-01; the Coinbase note has the PR opened 2026-02-10 and merged 2026-04-15 ([PR #1145](https://github.com/x402-foundation/x402/pull/1145)). V2 is 2025-12-11 or 2025-12-18 (section 1). Neither GitHub account (`CameronWhiteside`, `camwhiteside`) is confirmed as Cloudflare's Cam Whiteside.
4. **Foundation.** CDP's FAQ says it launched in April 2026 with forty members; LF says April was an intent announcement and 40 members were reported on 2026-07-14 ([CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq)). Premier is 17, 16 (one secondary article) or 19 (members page, metadata "last updated 2026-07-07"). LF and Stephanie Cohen credit Coinbase, Cloudflare and Stripe with developing x402; Lincoln Murr says it began at Coinbase. A claim that Cloudflare and Stripe form the "initial governing body" is unverified: no LF release names a board; the three-seat body is the TSC.
5. **Base and CDP.** CDP lists batch-settlement on EVM, but `createX402Server` does not register it (section 2). The Coinbase Wallet rename is absent from Base's blog feed (newest item 2026-09-01). Base's Azul mainnet date is 2026-05-13 (post) or 2026-05-28 (docs).
6. **Cloudflare.** The 2026-07-01 post names Open USD and USDC; the 2026-09-30 post says USDC on Base. The Visa/Mastercard identity post is dated 2025-10-14 (AnyBiz) or 2025-10-24 (Cloudflare, used). The CFO's 2026-09-09 words (Wallets let agents transact) run ahead of the docs (2026-08-19: handle reservation only).

**Unverified or unknown**
- Coinbase Ventures x402 deals; Coinbase's own blog posts (403); shareholder letters; Q3 earnings dates for Coinbase and Cloudflare.
- Base: any 2026 token statement; any agent leader besides Jesse Pollak; whether its x402 numbers match x402.org's.
- Foundation: board members, chair, treasurer, an official X account, the Executive Director's start date.
- Cloudflare: any Gateway fee; who pays the facilitator fee; the $100 ceiling; seller and buyer counts and volumes; NET Dollar's status after October 2025; when the claim was made.
- Adopters: the AWS chain beyond Base; Stripe's own announcement page; PayPal, Shopify and Microsoft products (not searched).
- Protocol and people: per-version SDK dates; Java SDK status; working-group goals; X posting activity.
- Method: search budgets ran out in both notes; Cloudflare executive quotes come from third-party transcripts; several timeline rows rest on commit or tag dates.
