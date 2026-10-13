# x402, Coinbase, Base and the x402 Foundation: platform and protocol picture as of 2026-10-11

> Method note (read first). Research date 2026-10-11. GitHub facts come from `gh api` calls run on 2026-10-11 (roughly 270 of the ~300 call budget used). Web pages were read through a summarising fetch tool, so the highest-stakes Coinbase figures were checked against the slide images themselves. The shared WebSearch budget ran out part-way through the session, so Coinbase Ventures deals, acquisitions and any 2026 Base token news rest on direct fetches of official pages only and are listed as gaps. Several fetches were blocked (403) or JavaScript-only: coinbase.com/blog, blog.base.org pages, x402scan.com, base.org stat counters.
>
> Corrections to the leads in the brief: (1) the canonical repo is no longer `coinbase/x402`; it is `x402-foundation/x402` and `coinbase/x402` is now a fork created 2026-04-02. (2) The official x402 community channel is Slack (plus a Telegram group), not Discord; the CDP and Base Discords exist for those products. (3) The "deferred" payment idea now lives in the `batch-settlement` scheme; the scheme set is exact, upto, batch-settlement and auth-capture. (4) The move to the Linux Foundation is confirmed by LF's own press releases. (5) ERC-8004 is still formally "Draft" even though registries are live on mainnets, including Base.

---

## 1. Protocol: current spec version, how it changed from May 2025 to now, where changes are decided, and GitHub activity

### Takeaway
The spec is still "x402 Protocol Version 2" (V2 launched 2025-12-11); no V3 spec exists in the repo on 2026-10-11. Since V2, change has arrived additively: new payment schemes (upto, batch-settlement, auth-capture), many more chains, and extensions (Bazaar discovery, SIWX, payment-identifier, builder codes, signed offers and receipts), shipped as SDK minor releases (`@x402/core` v2.0.0 on 2025-12-11 to v2.28.0 on 2026-09-29). Proposals are made on GitHub and decided under a Technical Steering Committee (TSC) charter adopted 2026-03-31; the repo itself moved to the `x402-foundation` org in April 2026.

### Cited Findings

#### 1a. Spec version and history
- x402 was announced on 2025-05-06 ("x402: An open standard for internet-native payments") — [x402.org RSS feed](https://x402.org/feed/)
- V2 launch post "Introducing x402 V2" is dated 2025-12-11 in the feed; the `@x402/core` v2.0.0 tag commit is also 2025-12-11 — [x402.org RSS feed](https://x402.org/feed/), [GitHub tags](https://github.com/x402-foundation/x402/tags). The CDP changelog dates "x402 V2 protocol spec released" 2025-12-18 — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog). (Conflict of 7 days; the 2025-12-11 date has two independent sources.)
- The core spec file opens with "Protocol Version: 2". Its scope lists the schemes `exact`, `upto` and `batch-settlement`; it excludes transports, client budget management and session handling. The `specs/` folder holds only v1 and v2 core specs (no v3) — [specs/x402-specification-v2.md](https://github.com/x402-foundation/x402/blob/main/specs/x402-specification-v2.md), [specs folder](https://github.com/x402-foundation/x402/tree/main/specs)
- V2 changes per the launch post (authors Erik Reppel, Carson Roscoe, Josh Nickerson): unified payment interface using CAIP network/asset identifiers (multi-chain by default, with legacy rails such as ACH/SEPA/cards possible through facilitators); per-request `payTo` and input-based dynamic pricing; plugin-driven SDK with lifecycle hooks; X-* headers replaced by PAYMENT-SIGNATURE, PAYMENT-REQUIRED and PAYMENT-RESPONSE; wallet-based identity/sessions via a Sign-In-With-X (CAIP-122) header so prior buyers can skip repaying; a discovery extension that facilitators crawl; multi-facilitator support; paywall moved to `@x402/paywall`; move to the `@x402` npm org. The post states "over 100M payments processed" and "600+ builders" in the Telegram group at that time, and promised an independent Foundation — [Introducing x402 V2](https://x402.org/x402-v2-launch/)
- Migration guide specifics: `X-PAYMENT` becomes `PAYMENT-SIGNATURE`; `x402Version: 1` becomes `2`; network strings become CAIP-2 (`base` becomes `eip155:8453`, `solana` becomes `solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp`); packages `x402`, `x402-express`, `x402-fetch` etc. become `@x402/core`, `@x402/express`, `@x402/fetch`, with `@x402/evm` and `@x402/svm`; a V2 server can still accept V1 clients; no V1 deprecation date is given — [Migration guide V1 to V2](https://docs.x402.org/guides/migration-v1-to-v2)
- Foundation stance on versioning: principles state x402 "will aim for backwards compatibility for non-major version changes" and will not drop existing networks except for security — [README principles](https://github.com/x402-foundation/x402/blob/main/README.md)

#### 1b. Payment schemes (dated)
- Scheme set today: `exact` (fixed price; default "authorization" flow verifies before the handler and settles after; optional "upfront" flow), `upto` (buyer authorizes a maximum, seller charges actual usage), `batch-settlement` (many per-request authorizations accumulate against a reusable channel), `auth-capture` (funds held in escrow, then captured, voided or refunded; "refundable payments") — [Schemes overview](https://docs.x402.org/schemes/overview), [specs/schemes folder](https://github.com/x402-foundation/x402/tree/main/specs/schemes)
- `upto` EVM spec merged 2026-03-04 (PR #1074, `fabrice-cheng`) — [path history](https://github.com/x402-foundation/x402/commits/main/specs/schemes/upto). CDP announced "Upto" live on its facilitator about 2026-04-09 (Cointelegraph article dated 2026-04-10; it quotes only CDP's X post) — [Cointelegraph](https://www.cointelegraph.com/news/coinbase-x402-rolls-out-usage-based-pricing-agentic-ai). CDP added `upto` on Solana on 2026-09-14 (escrow deposit, then settle-and-refund) — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog)
- `batch-settlement`: PR #1145 (opened 2026-02-10, merged 2026-04-15, author `CameronWhiteside`) added the scheme plus a Cloudflare `cloudflare:402` binding (credit-backed, RFC 9421 HTTP Message Signatures, fiat batch billing). The PR body says the scheme is "designed to unify the multiple deferred-settlement PRs under a single parent scheme", i.e. this is where the earlier "deferred" idea went — [PR #1145](https://github.com/x402-foundation/x402/pull/1145). Public launch post "Introducing x402 Batch Settlement" is dated 2026-05-11 with authors Cam Whiteside (Cloudflare) and Carson Roscoe, Conner Swenberg, Josh Nickerson, Philippe d'Argent (Coinbase) — [x402.org feed](https://x402.org/feed/), [post](https://x402.org/x402-batch-settlement/)
- Batch-settlement mechanics: EVM version uses "stateless unidirectional payment channels" (one escrow deposit, signed cumulative vouchers per request, periodic bulk claims, separate settle step, cooperative refunds, timed withdrawals); the Solana version reuses the `upto` payment-channels program and supports client-signed or server-signed vouchers — [Batch settlement docs](https://docs.x402.org/schemes/batch-settlement). Solana/Go batch-settlement SDK code merged 2026-09-25 (PR #3164, `lgalabru`) and 2026-09-29 (PR #3603) — [commits](https://github.com/x402-foundation/x402/commits/main)
- `auth-capture`: spec files exist by 2026-05-20 (rename PR #2391). The EVM binding "builds on the base/commerce-payments contract stack" (Base's escrow contracts, also used by Shopify) — [EVM binding spec](https://github.com/x402-foundation/x402/blob/main/specs/schemes/auth-capture/scheme_auth_capture_evm.md), [Base engineering blog list](https://blog.base.dev/). TypeScript "auth capture sdk v1.1" merged 2026-10-06 and EVM auth-capture for the Go SDKs 2026-10-05 — [commits](https://github.com/x402-foundation/x402/commits/main)
- "Session" semantics today come from two pieces: SIWX (re-access without repaying) and batch-settlement channels. The core spec still lists "session handling mechanisms" as out of scope — [V2 launch post](https://x402.org/x402-v2-launch/), [spec](https://github.com/x402-foundation/x402/blob/main/specs/x402-specification-v2.md)

#### 1c. Multi-chain and multi-asset
- Docs list EVM (any `eip155:<id>`), Solana, TON (`tvm`), Algorand (`avm`), Stellar, Aptos, Hedera, Keeta, NEAR, Concordium, XRPL and Cardano, plus Bitcoin Lightning (`lnbtc`) on the schemes overview. EVM transfers use EIP-3009 or Permit2 (any ERC-20); Solana uses SPL/Token-2022 — [Networks and token support](https://docs.x402.org/core-concepts/network-and-token-support), [Schemes overview](https://docs.x402.org/schemes/overview)
- Default-asset registry covers 30+ EVM entries (Base, Ethereum, Avalanche, Polygon, Arbitrum, Monad, Celo, Sei, Arc, XDC, MegaETH and others) with USDC mostly; Celo also lists USDT and USAT — [Networks and token support](https://docs.x402.org/core-concepts/network-and-token-support)
- Recent additions in commits: Monad testnet USDC default asset (2026-09-28), Arc default stablecoins (2026-09-28), exact-Lightning spec on `lnbtc` (2026-09-23, PR #2861), Starknet exact-settlement rules fix (2026-09-23), Hedera `transferExecutor` spec (2026-09-24) — [commits](https://github.com/x402-foundation/x402/commits/main)
- Public testnet facilitator at x402.org is testnet only (Base Sepolia, Solana devnet, Stellar/Aptos/Hedera/XRPL testnets); README warns not to assume it is the production path for mainnet — [Networks doc](https://docs.x402.org/core-concepts/network-and-token-support), [README](https://github.com/x402-foundation/x402/blob/main/README.md)
- SDKs: TypeScript (`@x402/core`, `evm`, `svm`, `avm`, `aptos`, `casper`, `stellar`, `tvm`, `hedera`, `keeta`, `xrpl`, `near`, `concordium`, `cardano`, `extensions`, `mcp`, `paywall` and framework adapters), Python (`x402`), Go, and a Java folder — [README](https://github.com/x402-foundation/x402/blob/main/README.md), [tag list](https://github.com/x402-foundation/x402/tags)
- SDK feature parity (docs matrix, read 2026-10-11): TypeScript supports every network and scheme listed; Go supports only EVM and Solana; Python supports EVM, Solana and TON. `upto` and `batch-settlement` on Solana exist in TypeScript and Go but not Python; `auth-capture` (EVM) exists in TypeScript and Go but not Python; the offer-receipt extension is TypeScript-only; Bazaar, SIWX, payment-identifier, builder-code and both gas-sponsoring extensions exist in all three. Java is not on the matrix — [SDK Features](https://docs.x402.org/sdk-features)

#### 1d. Extensions and discovery (Bazaar)
- Extensions documented: Bazaar (discovery), Builder Code (ERC-8021 attribution), Payment-Identifier (idempotent retries), Sign-In-With-X, Signed Offers and Receipts, EIP-2612 and ERC-20-approval gas sponsoring (Permit2), plus an HTTP-message-signatures extension and an "auth-hints" extension — [Docs index](https://docs.x402.org/llms.txt), [specs/extensions](https://github.com/x402-foundation/x402/tree/main/specs/extensions)
- First spec commits: Permit2 + gas-sponsoring extensions 2026-01-08 (#769); Bazaar spec 2026-01-15 (#956); SIWX 2026-02-02 (#921, `sragss`); MCP transport spec update 2026-02-03; payment-identifier 2026-02-05 (#1053); signed Offer & Receipt (draft) 2026-03-12; batch-settlement with http-message-signatures 2026-04-15; auth-hints 2026-04-24 (#1902); builder_code 2026-05-04 (#2050) — [path histories via commits](https://github.com/x402-foundation/x402/commits/main/specs/extensions)
- Bazaar: a machine-readable catalog of x402 HTTP endpoints and MCP tools, described as "in early development"; a facilitator that supports it may expose `GET /discovery/resources`; an endpoint is only catalogued after a facilitator processes a paid request that echoes the `bazaar` extension; facilitators define indexing and search — [Bazaar docs](https://docs.x402.org/extensions/bazaar). Bazaar launched 2025-09-17 per CDP; CDP added semantic search, structured filters, quality-aware ranking and an MCP surface on 2026-04-14 — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog)
- Builder-code extension: June 2026 CDP entry says settlements can record the exposing app, settling facilitator and initiating client using ERC-8021 (TS, Python, Go); facilitator-authored settlement metadata `m` merged 2026-10-06 (#3666) — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [commits](https://github.com/x402-foundation/x402/commits/main)

#### 1e. Where changes are proposed and decided
- GitHub issues are for "bug reports and concrete feature proposals only"; questions and showcases go to Slack. Merging is at the discretion of the "x402 Foundation team". The repo has an explicit AI-assisted-contribution policy (review output, disclose heavy AI use, no batch low-effort PRs) — [CONTRIBUTING.md](https://github.com/x402-foundation/x402/blob/main/CONTRIBUTING.md)
- New specs: open an issue or discussion first (problem, approach, why existing schemes do not suffice), write the spec from a template, then submit a PR — [specs/CONTRIBUTING.md](https://github.com/x402-foundation/x402/blob/main/specs/CONTRIBUTING.md)
- Governance: the TSC charter ("x402 a Series of LF Projects, LLC", adopted 2026-03-31) makes the TSC responsible for technical oversight. It starts with three representatives (Coinbase, Cloudflare, Stripe); more can be added by majority vote; decisions need a majority of eligible representatives; a 75% supermajority is needed to change the Core Principles, remove a participating organization, allow non-Apache licences, or amend the charter. Code is Apache-2.0 with DCO sign-off; docs are CC-BY-4.0; LF Projects holds the trademarks — [Technical Charter PDF](https://github.com/x402-foundation/x402/blob/main/foundation/x402%20Technical%20Charter%20March%2031%2C%202026.pdf)
- TSC mechanics: bi-weekly open meetings, agenda items proposed as issues in `x402-foundation/tsc`, notes in a Google Doc, recordings in LFX, public Slack `#tsc-public`, mailing lists (public and private) — [tsc README](https://github.com/x402-foundation/tsc/blob/main/README.md). Slack is "not an official system of record": spec changes and approvals must be captured in GitHub or meeting minutes — [Slack guidelines](https://github.com/x402-foundation/foundation/blob/main/policies-guidelines/slack-guidelines.md)
- Four working groups exist, each with its own repo, Slack channel, mailing list and bi-weekly meeting: Identity (repo created 2026-08-03), Tax (2026-08-19), Domain Discovery (2026-09-14), Card Acceptance (2026-09-23). Their goals sections are still template placeholders — [x402.org get-involved](https://x402.org/get-involved/), [wg-identity](https://github.com/x402-foundation/wg-identity), [wg-tax](https://github.com/x402-foundation/wg-tax), [wg-domain-discovery](https://github.com/x402-foundation/wg-domain-discovery), [wg-card-acceptance](https://github.com/x402-foundation/wg-card-acceptance)
- `ROADMAP.md` currently reads only "(update coming soon)"; its last real update was the Q4-2025 roadmap in September 2025 — [ROADMAP.md](https://github.com/x402-foundation/x402/blob/main/ROADMAP.md), [file history](https://github.com/x402-foundation/x402/commits/main/ROADMAP.md)

#### 1f. Repo move and GitHub activity (gh CLI, run 2026-10-11)
- `coinbase/x402` is now a fork (created 2026-04-02, 163 stars, issues disabled, parent `x402-foundation/x402`). The canonical repo `x402-foundation/x402` was created 2025-02-21, has 6,702 stars, 2,158 forks and 695 open issues, last pushed 2026-10-10. The `x402-foundation` org was created 2026-04-01 and has 7 public repos — [coinbase/x402](https://github.com/coinbase/x402), [x402-foundation/x402](https://github.com/x402-foundation/x402), [org](https://github.com/x402-foundation)
- Commits per month to the default branch of `x402-foundation/x402` (author-date month): 

| Month | Commits |
|---|---|
| 2026-01 | 95 |
| 2026-02 | 128 |
| 2026-03 | 128 |
| 2026-04 | 67 |
| 2026-05 | 115 |
| 2026-06 | 82 |
| 2026-07 | 81 |
| 2026-08 | 109 |
| 2026-09 | 102 |
| 2026-10 (1st to 10th) | 15 |

  Total 922 since 2026-01-01. The old `coinbase/x402` shows the same Jan/Feb/Mar numbers and only 2 in April, consistent with the move. Counts include docs-bot commits — [commit history](https://github.com/x402-foundation/x402/commits/main)
- Releases: no GitHub Releases are published (API returns an empty list). Releases are Git tags per package: 672 tags in total, such as `npm-@x402/core@v2.28.0`, `pypi-x402@v2.25.0`, `go-x402…`, plus the legacy `npm-x402@v1.2.0` line, a `v1` tag and `alpha-v2` — [tags](https://github.com/x402-foundation/x402/tags), [tags Atom feed (valid)](https://github.com/x402-foundation/x402/tags.atom)
- `@x402/core` tag dates: v2.0.0 2025-12-11; v2.1.0 2025-12-23; v2.5.0 2026-02-26; v2.10.0 2026-04-13; v2.15.0 2026-06-12; v2.20.0 2026-07-27; v2.25.0 2026-09-04; v2.28.0 2026-09-29 (latest). `pypi-x402@v2.25.0` was cut the same day (2026-09-29) — [tags](https://github.com/x402-foundation/x402/tags), [Atom feed](https://github.com/x402-foundation/x402/tags.atom)
- Top contributors (all-time commits per the contributors API; last-six-month commits since 2026-04-11; X handle is the GitHub profile `twitter_username` field unless noted; fetched 2026-10-11):

| GitHub login | All-time | Since 2026-04-11 | Profile name / affiliation as self-declared | Self-declared X |
|---|---|---|---|---|
| phdargen | 234 | 187 | none given | none |
| CarsonRoscoe | 210 | 42 | Carson Roscoe; personal site carsonroscoe.com | none on GitHub; personal site links twitter.com/carsonroscoe7 |
| mintlify[bot] | 94 | 74 | docs bot | n/a |
| erikreppel-cb | 48 | n/a (small) | none (work account; created 2025-02-21) | none (see people section for personal account) |
| apmcdermott / apmcdermott-cb | 38 / 21 | 4 / n/a | "A. McDermott", Coinbase / "Amanda McDermott" | flyingkittans (on `apmcdermott`) |
| notorious-d-e-v | 33 | 14 | Notorious D.E.V., PayAI | notorious_d_e_v |
| PhilBot402 | 27 | 27 | bot account, bio "by @phdargen" (created 2026-08-30) | none |
| wnjoon | 22 | 13 | wonjoon | 216___x |
| ryanRfox | 17 | 11 | Ryan R. Fox (LinkedIn linked) | none |
| ethanoroshiba | 14 | 7 | Ethan Oroshiba, Coinbase | none |
| manifoldfrs | 11 | n/a | Faris Habib, Opto AI | frshbb |
| marcelosalloum | 9 | n/a | Marcelo Salloum dos Santos, Stellar Development Foundation | none |
| John-peterson-coinbase | 8 | n/a | John Peterson, @coinbase | none |
| tenequm | 8 | 2 | Misha Kolesnik | opwizardx |
| Must-be-Ash | 7 | 4 | Ash, Coinbase Developer Platform ("DevRel & Product Designer") | Must_be_Ash |
| EfeDurmaz16 | 7 | 7 | Efe Baran Durmaz | efebarandurmaz |
| murrlincoln | 7 | n/a | none on profile | none on GitHub; official repo docs name @murrlincoln |
| alftom | 6 | n/a | Alfred Tom, Wivity / OMA3 | none |
| aristotle-satoshi | 6 | 5 | Frank He, t54 Labs | none |
| sragss | 5 | n/a | Sam Ragsdale | samrags_ |
| lgalabru | 4 | 4 | Ludo Galabru, @solana-foundation | ludo_txtx |
| GuiBibeau | 4 | n/a | Gui Bibeau, @Solana-Foundation | GuiBibeau |
| Jnix2007 | 3 | 3 | "jnix.base.eth", Coinbase; bio "Product Lead for Wallets, Onchain Tools, and Agentic Commerce at Coinbase Developer Platform" | Jnix2007 |

  Sources: [contributors](https://github.com/x402-foundation/x402/graphs/contributors) and the GitHub user pages for each login (for example [Must-be-Ash](https://github.com/Must-be-Ash), [Jnix2007](https://github.com/Jnix2007), [notorious-d-e-v](https://github.com/notorious-d-e-v), [sragss](https://github.com/sragss), [GuiBibeau](https://github.com/GuiBibeau)), and [carsonroscoe.com](https://www.carsonroscoe.com). "n/a" means outside the top-30 authors since 2026-04-11 (so 2 or fewer).
- The `x402-foundation/x402` CODEOWNERS file assigns teams per area: core, site (x402.org facilitator), Java, and per-network maintainers for EVM, SVM, Stellar, Aptos, AVM, Cardano, Casper, Concordium, Hedera, Keeta, NEAR, TVM and XRPL — [CODEOWNERS](https://github.com/x402-foundation/x402/blob/main/.github/CODEOWNERS)

#### 1g. What is being worked on and proposed now (proposals are not decisions)
- Most-discussed open items: post-settlement accountability and proof-of-delivery receipts (#2332, 232 comments; #2833; #1195; #2922), agent identity/trust/reputation extensions (#1777, PR #1024), DNS plus `.well-known` facilitator discovery records (PR #2979, 184 comments, ties to the Domain Discovery WG), settlement status vocabulary (PR #3325, issue #3208), bounded spending mandates (`authority` extension PR #3220), Hyperliquid scheme (PR #1177), BSV exact scheme (PR #2890) — [issues sorted by comments](https://github.com/x402-foundation/x402/issues?q=is%3Aopen+sort%3Acomments-desc)
- Community TSC agenda topics (open, 2026-07 to 2026-09): `subscribe` recurring-payment scheme review (PR #1133), Canton Network implementation review (PR #3242), proposed guiding principles and a two-tier requirements structure, refunds (x402 "can't issue refunds"), post-settlement accountability scope; "Upfront" scheme review status was raised and closed — [tsc issues](https://github.com/x402-foundation/tsc/issues)
- Latest commits (2026-09-18 to 2026-10-10) are SDK parity and hardening: EVM auth-capture across Go/TS, Solana batch settlement in Go, builder-code settlement metadata, route-matching bypass fixes, new default assets — [commits](https://github.com/x402-foundation/x402/commits/main)

### Inferences
- Because the spec file still says "Version 2" while SDKs are at 2.28, "V2.x" evolves additively through schemes and extensions; a V3 does not look imminent (no V3 file, no V3 label).
- The CDP facilitator fee of $0.001 per settled transaction plus a growing share of micro-payments helps explain why `upto` and batch-settlement (one on-chain claim for thousands of payments) were prioritised in 2026 (inference from pricing and design; no source states this motive).
- The two most active committers (`phdargen`, `CarsonRoscoe`) appear next to Coinbase-affiliated names in the V2 and batch-settlement posts, so Coinbase engineers likely still do much of the SDK work even under LF governance. I could not confirm an employer for `phdargen`.
- The volume of open issues (695) and the explicit AI-contribution policy suggest heavy, partly machine-written proposal traffic; the TSC agenda and four working groups look like an attempt to route that into structured review. This is an inference, not stated by any source.

### Gaps
- No GitHub Releases or changelog with dates for every SDK version; I only dated 8 `@x402/core` tags.
- I did not confirm when `auth-capture` was first proposed (path history before the 2026-05-20 rename was not followed).
- Java SDK status and version are not documented on the SDK feature matrix.
- Working-group goals are blank placeholders; nothing yet shows their outputs.

---

## 2. x402 Foundation: founding, members, governance, leadership, and the Linux Foundation move

### Takeaway
Confirmed: x402 is now hosted by the Linux Foundation as "x402 Foundation" (a directed fund) with a technical project "x402 a Series of LF Projects, LLC". LF announced the plan on 2026-04-02, declared it operational on 2026-07-14 with 40 member organisations, and appointed Michael Hursta Executive Director on 2026-10-01; membership had reached roughly 58 organisations on the members page I read on 2026-10-11. Technical oversight sits with a three-seat TSC (Coinbase, Cloudflare, Stripe), with Coinbase's representative being x402's creator Erik Reppel.

### Cited Findings

#### 2a. Founding timeline
- 2025-09-23: Cloudflare press release announces that Cloudflare and Coinbase "will launch" an x402 Foundation as a neutral body; Erik Reppel is described as "creator of x402 and Head of Engineering for Coinbase Developer Platform" — [Cloudflare release](https://www.cloudflare.com/press/press-releases/2025/cloudflare-and-coinbase-will-launch-x402-foundation/)
- 2026-03-31: Technical Charter adopted for "x402 a Series of LF Projects, LLC" — [Charter PDF](https://github.com/x402-foundation/x402/blob/main/foundation/x402%20Technical%20Charter%20March%2031%2C%202026.pdf)
- 2026-04-01: GitHub org `x402-foundation` created; 2026-04-02: `coinbase/x402` fork created the same day LF announced — [GitHub org](https://github.com/x402-foundation), [coinbase/x402](https://github.com/coinbase/x402)
- 2026-04-02: Linux Foundation press release, datelined New York at MCP Dev Summit North America, says LF "is launching the x402 Foundation" with Coinbase contributing the protocol; says Coinbase, Cloudflare and Stripe initially developed it; lists 22 organisations with "initial intent and support": Adyen, AWS, American Express, Ampersend.ai, Base, Circle, Cloudflare, Coinbase, Fiserv, Google, KakaoPay, Mastercard, Merit Systems, Microsoft, Polygon Labs, PPRO, Shopify, Sierra, Solana Foundation, Stripe, thirdweb, Visa. It describes no board, TSC or tiers — [LF press release](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol)
- 2026-05-12: `TSC.md` created (Coinbase: Erik Reppel; Cloudflare: Rohin Lohe; Stripe: Steve Kaliski); the same day a commit "Update footer to Linux Foundation (#2283)" landed in the repo — [TSC.md](https://github.com/x402-foundation/x402/blob/main/TSC.md), [commit history](https://github.com/x402-foundation/x402/commits/main/TSC.md)
- 2026-07-10: `x402-foundation/tsc` repo created — [tsc repo](https://github.com/x402-foundation/tsc)
- 2026-07-14: LF "announces operational launch of x402 Foundation" (San Francisco dateline), says Coinbase's contribution is complete and 40 organisations joined since April; the Foundation is "governed openly and neutrally under the Linux Foundation" — [x402.org press release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/)
- 2026-08-13: the Directed Fund charter (Exhibit B of the participation agreement) shows "Amended August 13, 2026" — [LF participation agreement PDF](https://cdn.platform.linuxfoundation.org/agreements/x402-foundation.pdf)
- 2026-09-29: policy repo `x402-foundation/foundation` created with Slack guidelines — [foundation repo](https://github.com/x402-foundation/foundation)
- 2026-10-01: LF appoints Michael Hursta Executive Director (see leadership) — [x402.org feed](https://x402.org/feed/)

#### 2b. Two-layer governance
- Directed Fund ("x402 Foundation"): Governing Board = one representative per Premier member (cap 25 Premier seats, raisable by board vote) plus General-member representatives (one per ten General members, up to three, minimum one). Officers elected by the board: a Chair and a Treasurer. Premier eligibility requires showing substantial x402 investment (for example 2.0 FTE or more of technical resources, product integration, or adding network support). Members must also be LF members — [LF participation agreement](https://cdn.platform.linuxfoundation.org/agreements/x402-foundation.pdf)
- Dues: Premier $200,000; General by headcount ($75,000 for 2,500+ employees, $50,000 for 250 to 2,500, $25,000 under 250); Associate $0 for academic and nonprofit bodies; enrolment through LFX — [x402.org members page](https://x402.org/members/)
- Technical Project: governed by the TSC charter (section 1e). Reps can be removed for publicly stating x402 should not follow the Core Principles; the Core Principles in the README include "open standard", "trust minimizing" (a facilitator or resource server may not move funds except per client intent) and "will never deprioritize onchain payments in favor of fiat" — [Charter PDF](https://github.com/x402-foundation/x402/blob/main/foundation/x402%20Technical%20Charter%20March%2031%2C%202026.pdf), [README](https://github.com/x402-foundation/x402/blob/main/README.md)

#### 2c. Membership snapshots
- 2026-07-14 release: Premier (17) Adyen, AWS, American Express, Circle, Cloudflare, Coinbase, Fiserv, Google, Mastercard, Monad Foundation, MoonPay, Ripple, Shopify, Solana Foundation, Stellar Development Foundation, Stripe, Visa. General (18) Aleo, Fireblocks, Galaxia Moneytree, Hecto Financial, Injective, KakaoPay, Kite AI, LayerZero Labs, Merit Systems, NEAR Foundation, Orthogonal, Polygon Labs, Quant Network, SKALE, t54 labs, utexo, World Liberty Financial, zerohash. Associate: BSV Association, Cardano Foundation, Casper and Japan Contents Blockchain Initiative, OMA3. The text says 40 organisations; the listed tiers add to 39 unless Casper and Japan Contents are counted separately — [press release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/)
- Members page fetched 2026-10-11 (page metadata says "last updated 2026-07-07", which is inconsistent with its content): Premier 19 (the 17 above plus PayPal and Sui); General 27 per the header (adds Arkham, Blockdaemon, Block Inc., Cyclops, ETHGas, Ledger, Monoma, Satoshi Holdings, among others); Associate 12 (adds AI Grants India Foundation, Concordium, FIO Protocol, Hedera Foundation, INFTF, Merchant Advisory Group, PPPA); 58 total — [members page](https://x402.org/members/). The 2026-10-01 release says "more than 50 active members" — [Hursta release](https://x402.org/linux-foundation-appoints-michael-hursta-as-executive-director-of-the-x402-foundation/)
- Some April "initial intent" names do not appear in the July or October lists as I read them: Base as a separate entity, Microsoft, Ampersend.ai, PPRO, Sierra, thirdweb — compare the [April release](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol) with the [members page](https://x402.org/members/)

#### 2d. Leadership
- Executive Director: Michael Hursta, appointed by LF on 2026-10-01 (San Francisco dateline). Background as stated: 20+ years in payments; most recently Partner at Commerce Technology Partners; previously led PwC's enterprise payments advisory practice; Head of payment acceptance and experience for North America at Amazon; over a decade at First Data (general manager of its global merchant prepaid business). Start date not stated; no Governing Board chair or other officers named — [Hursta release](https://x402.org/linux-foundation-appoints-michael-hursta-as-executive-director-of-the-x402-foundation/)
- LF CEO Jim Zemlin is the quoted LF voice in the April, July and October releases — [April release](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol)
- TSC representatives (listed in order of seniority): Erik Reppel (Coinbase), Rohin Lohe (Cloudflare), Steve Kaliski (Stripe) — [TSC.md](https://github.com/x402-foundation/x402/blob/main/TSC.md). The tsc README table shows Erik Reppel without an affiliation and spells "Cloudfare" — [tsc README](https://github.com/x402-foundation/tsc/blob/main/README.md)
- Quoted at the July launch: Lincoln Murr, Head of AI Product, Coinbase ("x402 began at Coinbase" to address agents lacking a native payment method) — [press release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/)
- Repo admin: GitHub user `Naomi-Wash` (profile name Naomi Washington) made the initial commits of the `tsc` and `foundation` repos (2026-07-10, 2026-09-29); her role is not stated in any source I read — [tsc commits](https://github.com/x402-foundation/tsc/commits/main), [foundation commits](https://github.com/x402-foundation/foundation/commits/main)

#### 2e. Conflicts and caveats
- CDP's FAQ says the Foundation "launched under the Linux Foundation in April 2026 with forty member organizations"; LF's own documents say April was an intent announcement and 40 members were reported at the July 14 operational launch — [CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq), [LF release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/)
- Premier counts differ by source: 17 in the July release text, 16 names in one secondary article, 19 on the members page (2026-10-11) — sources above
- Coinbase said on its Q1 2026 call (per a Nasdaq summary I could not fetch; page timed out) that x402 had moved to the Linux Foundation with contributions from Cloudflare, AWS, Stripe, Shopify and Google — [Nasdaq Q1 call highlights (via search summary)](https://www.nasdaq.com/articles/coinbase-global-q1-earnings-call-highlights)

### Inferences
- The structure is genuinely neutral on paper (LF Projects holds trademarks, Apache-2.0, supermajority rules, a Governing Board where Coinbase is one of 19 Premier seats), but Coinbase keeps the first TSC seat and stays the heaviest code contributor, so practical influence is still large.
- Premier dues of $200,000 and a 25-seat cap put an upper bound on pay-to-play governance; the Premier requirement of 2.0 FTE of technical resources is the more meaningful filter.
- Early adopters that dropped off the visible lists (Microsoft, thirdweb, Sierra, PPRO) may simply not have enrolled yet; I have no evidence of withdrawal.

### Gaps
- Governing Board members, chair and treasurer: not published in anything I fetched.
- The LF's own x402 Foundation page redirects to x402.org; no separate LF member roster was reachable.
- Official X account of the Foundation: none found (GitHub org `twitter_username` is empty; x402.org and docs list no X link).
- Next TSC/Governing Board meeting dates: only in the LFX calendar (JavaScript app), not readable.

---

## 3. Coinbase: CDP facilitator, Bazaar, agent tooling, metrics, investments and acquisitions

### Takeaway
Coinbase has shifted from "owner of x402" to "largest commercial operator on top of an LF-governed standard": it runs the main production facilitator (paid since 2026-01-15), the agentic.market directory, Agentic Wallet / Coinbase for Agents, Coinbase Business agent checkout, and an x402 client/server SDK. Its own disclosures say x402 handled 100M+ payments by end of Q1 2026 and accounted for 97%+ of "onchain agentic transactions" in Q2 2026 on Artemis's definition, but independent-looking counters give very different pictures depending on chain and window.

### Cited Findings

#### 3a. CDP facilitator
- Pricing now: first 1,000 onchain transactions per month free, then $0.001 per transaction; verification is always free; only successful settlements (2xx) are billed; no processor or chargeback fees; the facilitator pays settlement gas; CDP does not hold revenue (funds settle to `payTo`) — [CDP facilitator page](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator), [CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq)
- Pricing history from the changelog: 2025-12-03 "$0.001 minimum transaction amount" (with an Embedded Wallets x402 hook); 2025-12-10 announcement that facilitator charges begin 1 January; 2026-01-15 "facilitator billing starts (1,000 free transactions/month, then $0.001 each)" and the facilitator starts returning HTTP 400 on verify/settle failures; 2025-11-12 facilitator available in 100+ countries — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog)
- Networks (x402 v2, CAIP-2): Base `eip155:8453`, Base Sepolia, Polygon `eip155:137` (added 2026-03-24), Arbitrum `eip155:42161`, World `eip155:480`, World Sepolia, Solana mainnet and devnet. Schemes: exact, upto and batch-settlement on the EVM networks, exact and upto on Solana. Tokens: any ERC-20 (EIP-3009 or Permit2) and SPL/Token-2022 — [CDP facilitator page](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator), [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog)
- Caveat on batch-settlement: the FAQ says `createX402Server` does not register it today "because the server-side support was withdrawn"; buyer-side `CdpX402Client` registers Base exact, EVM upto and EVM auth-capture by default — [CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq)
- Controls and targets: OFAC and Know-Your-Transaction screening at verify and settle (declines return `kyt_risk_detected`); service targets 99.9% availability, P95 verify 60 ms (Base) and 275 ms (Solana), P95 settle 900 ms (Base) and 1,500 ms (Solana); `settlement_pending` is not a failure and must be reconciled rather than retried — [CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq)
- Extras: EIP-2612 gas sponsorship; Bazaar indexing after a settled payment (10 to 15 minutes); Builder Code (ERC-8021 Schema 2) attribution in settlement calldata — [CDP facilitator page](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator), [CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq)
- SDK: `@coinbase/cdp-sdk/x402` (`CdpX402Client`, `createX402Server`, `createCdpFacilitatorClient`, spend controls) added 2026-07-17; a generated Java SDK arrived 2026-09-14 — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog)
- CDP's own scale claim (undated, as fetched 2026-10-11): the facilitator "has processed more than 100 million transactions and $28 million in payment volume across Base and Solana" — [CDP facilitator page](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator)
- Facilitator landscape: the x402 docs list 15 "selected production" facilitators (CDP/Coinbase-hosted, Corbits, PayAI, Dexter, Fireblocks, Polygon, Celo, Stellar, T54 XRPL, FTP Canton, NEAR, HPP, Meridian, Mogami, Solvador); the x402.org public facilitator is testnet-only and "not intended to be the default production choice for mainnet routes". Only some entries carry a "production-grade" label (Corbits, PayAI, Polygon, T54 XRPL); CDP's entry notes KYT/OFAC checks — [Facilitators page](https://docs.x402.org/dev-tools/facilitators)

#### 3b. Bazaar and marketplace
- x402 Bazaar launched 2025-09-17 (CDP changelog); semantic search, filters, ranking and an MCP surface were added 2026-04-14; the FAQ says listing needs no registration, only a successful paid call, indexes within 10 to 15 minutes, has no delisting mechanism, and flags inactive endpoints after failed periodic checks — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq)
- agentic.market: operated by Coinbase, says it "is not an official product of the x402 Foundation", showed 3,072 services in 10 categories when fetched 2026-10-11 — [agentic.market](https://agentic.market). The x402 README lists it as a community directory alongside x402scan, Pay.sh and others — [README](https://github.com/x402-foundation/x402/blob/main/README.md)

#### 3c. Agent tooling: Agentic Wallet, Payments MCP, Coinbase for Agents, AgentKit
- Agentic Wallet launched 2026-02-11 (the same changelog entry says Payments MCP moved to x402 v2 and a Bazaar MCP server was added). It has a CLI (`awal`, installed with `npx skills add coinbase/agentic-wallet-skills`) and an "Agentic Wallet MCP (Beta)" run with `npx @coinbase/payments-mcp`; the CLI can send, trade and pay for x402 services, the MCP can only discover and pay — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [Agentic Wallet docs](https://docs.cdp.coinbase.com/agentic-wallet/welcome), [agentic-wallet-skills](https://github.com/coinbase/agentic-wallet-skills)
- `coinbase/payments-mcp` repo (created 2025-08-19, last pushed 2025-10-22) is only the npx installer — [repo](https://github.com/coinbase/payments-mcp)
- Coinbase for Agents appears in CDP docs on 2026-06-12 (Coinbase CLI and MCP server) and 2026-06-19 (remote MCP connector for Claude and ChatGPT at agents.coinbase.com); derivatives (2026-08-17) and S&P 500 equities (2026-08-21) trading were later added. The Q2 deck lists it as a first-half 2026 launch — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [Q2 deck slide 8](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/q226earningsdeck_sec008.jpg)
- "Agentic Accounts" in CDP docs means either Agentic Wallet (your own agent's wallet) or Coinbase for Agents (connect an agent to your Coinbase account) — [Agentic Accounts](https://docs.cdp.coinbase.com/x402/agentic-accounts/overview)
- Integrations: Amazon Bedrock AgentCore (2026-06-12, via an AWS Payment Manager and CDP connector) and the Payment Acceptance API — [CDP integrations](https://docs.cdp.coinbase.com/x402/integrations/overview), [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog)
- AgentKit (1,327 stars): "Every agent deserves a wallet." Recent commits are small fixes (2026-08-19, 2026-09-03); an ERC-8004 identity action provider and a LangChain 8004 example were added 2026-03-23 — [coinbase/agentkit](https://github.com/coinbase/agentkit), [8004 provider](https://github.com/coinbase/agentkit/tree/main/typescript/agentkit/src/action-providers/erc8004)

#### 3d. Coinbase Business and payments
- 2026-07-23 (The Block): Coinbase Business rolled out a stack so businesses can accept agent payments using x402, settled in USDC on Base or other chains; same-day items were Coinbase for Agents and an SDK for adding x402 payments; Coinbase Business reports about 5,000 customers and about $1 billion in combined payments and trading volume since its June 2025 launch (not x402-specific); a spokesperson said about 53% of web traffic to Base's documentation has come from agentic visitors since June — [The Block](https://www.theblock.co/post/409539/coinbase-ai-payments-most-high-conviction-bet-businesses-accepting-agent-payments)
- 2026-08-06 changelog: Payment Acceptance and Disbursements reach GA; Checkouts return an `x402_url` an agent can pay with a gasless USDC transfer on Base — [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog)
- 2026-05-05 8-K: Coinbase announced a restructuring of about 700 positions (roughly 14% of staff) to "optimize ... for the AI era" (context only; no x402-specific effect stated) — [8-K](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000049/coin-20260505.htm)

#### 3e. Base Account, spend permissions and the Coinbase Wallet rename
- `coinbase/spend-permissions`: `SpendPermissionManager` at `0xf85210B21cC50302F477BA56686d2019dC9b67Ad` on Base, Ethereum, Optimism, Arbitrum and Polygon (last push 2026-03-24); Base's docs use a wallet spend permission for scheduled charges — [repo](https://github.com/coinbase/spend-permissions), [Base docs index](https://docs.base.org/llms.txt)
- Rename trail: the `base/account-sdk` README says "Base Account is now Coinbase Wallet"; the note was added 2026-09-10; the package stays `@base-org/account`. CDP docs on 2026-09-14 say Base Account SDK docs now live under the "Coinbase Wallet" brand and the overview page calls it "formerly known as Base App". Base's docs say Base Account SDK and Base MCP "have moved" to CDP — [base/account-sdk](https://github.com/base/account-sdk), [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [Coinbase Wallet overview](https://docs.cdp.coinbase.com/coinbase-wallet/overview), [Base migrated products](https://docs.base.org/sdks/migrated-products)
- Base MCP became "Wallet MCP" (served from wallet-mcp.coinbase.com); `base/base-mcp-legacy` is archived, with its last push on 2026-05-13 (the archive date itself is not shown) — [base/skills](https://github.com/base/skills), [base-mcp-legacy](https://github.com/base/base-mcp-legacy)

#### 3f. Published x402 metrics (each with its own scope; do not mix)
| Date | Figure | Scope and source |
|---|---|---|
| 2026-05-07 | "100M+ total x402 payments processed as of Q1'26"; 99%+ of onchain agentic commerce used USDC and 90%+ of agentic stablecoin volume was on Base in Q1'26 | Coinbase Q1'26 deck slide 15, source Artemis Analytics — [slide image](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000053/q126earningsdeck-finalse015.jpg), [deck](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000053/q126earningsdeck-finalse.htm) |
| 2026-07-30 | 97%+ of onchain agentic transactions used x402; 90%+ of agentic stablecoin volume on Base; 99%+ of onchain agentic commerce used USDC (all Q2'26) | Coinbase Q2'26 deck slide 18, Artemis; footnote: agentic transactions identified "based on programmatic wallet signatures and HTTP 402 protocol interactions", EVM and Solana — [slide image](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/q226earningsdeck_sec018.jpg), [deck](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/q226earningsdeck_sec.htm) |
| 2026-07-30 | Armstrong on the call: "The vast majority ... of onchain agentic commerce is using USDC, and it's using Base, and it's using x402"; lists the x402 protocol among launches of the past year | [Q2'26 call transcript](https://s27.q4cdn.com/397450999/files/doc_financials/2026/q2/Q2-26-Earnings-Presentation-Transcript.pdf) |
| reported around 2026-07-30 | "more than 160 million autonomous transactions via the x402 agentic payments protocol in the last year" (paraphrase; venue and exact date not stated) | [The Defiant](https://thedefiant.io/brian-armstrong-says-coinbase-processes-usd1t-in-stablecoin-payments-annually) |
| 2026-06-03 | Chainalysis: wallets using x402 made 100M+ transactions on Base in roughly nine months; early growth driven by the PING memecoin experiment that required x402 payments to mint; share of value in transfers above $1 rose from about 49% (early 2025) to 95% (early 2026) | [Cointelegraph](https://cointelegraph.com/news/agentic-payment-activity-surpasses-100m-transactions-on-base) |
| 2026-07-28 | x402scan dashboard: 197.48M transactions, $52.51M volume, 846,110 buyers, 253,000 sellers (time window not stated; likely all-time) | [Cointelegraph (updated 2026-07-28)](https://cointelegraph.com/news/coinbase-ceo-agentic-finance-base-100-million-aifi-transactions) |
| fetched 2026-10-11 | x402.org "last 30 days": 75.41M transactions, $24.24M volume, 94.06K buyers, 22K sellers | [x402.org](https://x402.org/) |
| 2026-05-29 | Base's own blog: x402 on Base in the 30 days to 2026-05-29 recorded 3.1M transactions and $1.2M in value; sellers +23% and buyers +37% | [Base blog feed](https://api.paragraph.com/blogs/rss/@base) (post "The Agentic Economy Is Here") |
| 2026-04-10 | Dune (via Cointelegraph): record week 2025-11-04 to 2025-11-10 with 13.7M transactions; weekly transactions below 1M in early January 2026; 112,708 in the last week of March 2026 | [Cointelegraph](https://www.cointelegraph.com/news/coinbase-x402-rolls-out-usage-based-pricing-agentic-ai) |
| undated | CDP facilitator: more than 100M transactions and $28M volume across Base and Solana | [CDP facilitator page](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator) |

- The Q1 and Q2 shareholder letters themselves were not located (guessed URLs on Coinbase's investor CDN returned 404); the earnings decks filed with the SEC and the Q2 call transcript were used instead — [Q2 8-K filing index](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/)
- The WebFetch text extraction of the Q2 deck scrambled which percentage belongs to which tile; the slide image shows USDC 99%+, Base 90%+, x402 97%+ — [slide 18](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/q226earningsdeck_sec018.jpg)

#### 3g. Coinbase Ventures investments and acquisitions
- The Base Ecosystem Fund works "in partnership with Coinbase Ventures"; its 39-company portfolio includes Blockrun (an x402 pay-per-call AI router), BANKR, Sapien and Giza; Base Batches 003 teams building directly on x402 included Blockrun.ai, 4Mica, Agently and Floe Labs (the Batches program page states $100K from the Ecosystem Fund; the Batch 003 post itself gives no amount) — [Base Ecosystem Fund](https://www.base.org/ecosystem-fund), [Base Batches](https://www.base.org/batches), [Batches 003 post via Base feed](https://api.paragraph.com/blogs/rss/@base)
- Acquisitions: Coinbase's Q2 2026 10-Q names no 2026 acquisitions; it says business combinations in 2026 were "immaterial, both individually and in the aggregate" and the extract shows $39.8M of goodwill added in the first half. The only named deals in the note are Deribit (completed 2025-08-14, $4.3B) and Echo (completed 2025-10-08, $176.0M) — [10-Q for the period ended 2026-06-30](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000088/coin-20260630.htm). The same document did not show the MD&A section, so a small acqui-hire could sit there unnamed.

### Inferences
- Coinbase's structure is "neutral protocol, commercial platform": the revenue lines are facilitator fees, Coinbase Business checkout, wallets/agent products, USDC economics and Base usage; the open standard drives demand to them.
- The Artemis method identifies agentic activity partly through HTTP 402 interactions, so a 97%+ x402 share is close to definitional rather than a market-share measurement; the headline also covers Coinbase-chosen chains (EVM and Solana).
- Averages from the published figures are small tickets: $28M over 100M+ transactions (CDP) is about $0.28 or less each; $52.51M over 197.48M (x402scan) about $0.27; $24.24M over 75.41M (x402.org, 30 days) about $0.32; $1.2M over 3.1M (Base only, 30 days to 2026-05-29) about $0.39. At $0.001 per settled transaction the facilitator fee is a minor share of an average payment but a large share of sub-cent payments (arithmetic, not a sourced claim).
- Base-only x402 activity in May 2026 (3.1M transactions per 30 days) is far below the all-chain 30-day figure on x402.org (75.41M) in October; if the numbers are comparable, most transaction count would come from other chains, probably Solana (the LF's April release says Solana "drives a large share" of x402 transaction volume), while dollar volume on Base stays high under Artemis's definition. A chain-level breakdown from x402scan would settle this; I could not read it.
- The restructuring (May 2026) and the "AI-native pod" framing in the Q1 deck suggest Coinbase is running x402/agent work with smaller teams, but no source ties the layoffs to x402.

### Gaps
- Coinbase Ventures investments in x402 projects: not found in any official page I could reach (coinbase.com/ventures returns 403; WebSearch budget exhausted). Only the Base Ecosystem Fund overlap above.
- Acquisitions or acqui-hires of x402 teams: none confirmed; the 10-Q MD&A section was not readable.
- Q1 and Q2 shareholder letters and the Q1 call transcript were not located; Q1 call statements come only from a secondary summary.
- Coinbase blog and CDP "Discover" blog posts were blocked (403); I could not read Coinbase's own x402 announcement posts (for example the 2025-09-23 foundation post linked from the V2 article) — [linked post](https://www.coinbase.com/blog/coinbase-and-cloudflare-will-launch-x402-foundation)
- Number of sellers published by Coinbase itself: none; only third-party counters (x402scan, x402.org).
- Dates when Arbitrum and World were added to the CDP facilitator: not in the changelog entries I read.

---

## 4. Base: strategy for agents and x402, Base App, token, programs, own statistics

### Takeaway
Base positions itself as a chain for trading (including tokenized stocks), stablecoin payments and agents, and treats x402 as a standard it supports rather than builds: its own pages and blog list x402, ERC-8004, agentic wallets, Base MCP and skills as the "agent stack", while its engineering posts focus on upgrades (Azul, Beryl, Cobalt, Denim), the B20 token standard and native account abstraction. Base's own x402 statistic is modest (3.1M transactions and $1.2M value on Base in the 30 days to 2026-05-29). On a Base network token, the only statement I found is the September 2025 line that Base is "beginning to explore" one; nothing newer appears in Base's blog feed through 2026-09-01.

### Cited Findings

#### 4a. Strategy and agent positioning
- "Base 2026 Mission, Vision, and Strategy" (2026-03-31): three 2026 pillars (building global markets; scaling payments and stablecoins; being the home for builders); Base App as the place to trade, save, spend and pay; agents get "agent-native smart accounts, documentation, CLI and MCP access, and standards like x402 to help agents do anything with money"; reported 2025 results include over $17T of stablecoin volume, Base App in 140+ countries and 50+ teams funded through Base Batches — [Base blog feed](https://api.paragraph.com/blogs/rss/@base)
- base.org/agents ("Financial infrastructure for AI agents"): lists x402, ERC-8004 (onchain agent identity and reputation), Agentic Wallets (CDP), Base MCP, Base Skills, and an x402 ecosystem directory (agentic.market); partners named include Bankr, Virtuals and Cloudflare x402; its stat counters render as placeholders so no numbers could be read — [base.org/agents](https://www.base.org/agents)
- Vision page: "Upgrade the chain for agents ... agent-native smart accounts"; builders are "human or agent" — [base.org/vision](https://www.base.org/vision)
- "The Agentic Economy Is Here" (2026-05-29): x402 on Base, 30 days to 2026-05-29: 3.1M transactions, $1.2M value, sellers +23%, buyers +37%; named x402 services include Venice, BlockRun, Bankr's x402 Cloud, Browserbase and agentic.market workflows; says Base released Base MCP and is working on native wallet embedding in agent infrastructure; it does not mention ERC-8004 — [Base blog feed](https://api.paragraph.com/blogs/rss/@base)
- "Introducing Base MCP" (2026-05-26): connects a Base Account to Claude, ChatGPT, Codex or Cursor; the user confirms each action; OAuth 2.1; no private keys on the server; plugins for Morpho, Bankr, Moonwell, Avantis, Aerodrome, Virtuals and Uniswap; the x402 feature is "Pay for x402 enabled services" — [Base blog feed](https://api.paragraph.com/blogs/rss/@base)
- Request for Builders (2026-07-16) asks for agents that complete everyday purchases and for SKU tokenization; it does not mention x402 or ERC-8004 — [Base blog feed](https://api.paragraph.com/blogs/rss/@base)
- Base docs: pages for charging for an API with x402 exact, usage-based (upto) and batch settlement, and "Call a Paid Service" for agent-side limits; "Resources for AI Agents"; Builder Codes for agent developers — [Base docs index](https://docs.base.org/llms.txt)
- Builder codes (ERC-8021) are Base's attribution standard; Base's engineering blog post is dated 2026-02-12 on the blog but base.org lists it as an April 15 news item (date conflict) — [Base engineering post](https://blog.base.dev/builder-codes-and-erc-8021-fixing-onchain-attribution), [base.org](https://www.base.org/)
- The x402 `auth-capture` scheme is built on Base's open-source `commerce-payments` contracts — [spec](https://github.com/x402-foundation/x402/blob/main/specs/schemes/auth-capture/scheme_auth_capture_evm.md)

#### 4b. Chain roadmap relevant to agents and payments
- 2026-02-18: Base consolidates its stack in `base/base` and says it is "moving away from the OP Stack" while remaining a Stage 1 rollup (base.org lists the same post on 2026-04-10) — [Base engineering post](https://blog.base.dev/next-chapter-for-base-chain-1)
- Upgrade schedule per docs: Azul (Sepolia 2026-04-20, mainnet 2026-05-28; the Azul post said mainnet 2026-05-13), Beryl (Sepolia 2026-06-18, mainnet 2026-06-25; B20 native token standard), Cobalt (Sepolia 2026-09-23, mainnet 2026-09-30; validity transactions and B20 improvements), Denim (Sepolia October 2026, mainnet November 2026 target; 200 ms native blocks) — [Base upgrades](https://docs.base.org/upgrades/overview), [Azul post](https://blog.base.dev/introducing-base-azul), [Cobalt post](https://blog.base.dev/cobalt)
- Native account abstraction (EIP-8130) was announced 2026-07-17 as launching with Cobalt "this September" with session keys, sub-accounts and payer gas sponsorship (ERC-8168); the 2026-09-30 Cobalt post instead lists "Base Transactions" (smart accounts first-class at protocol level) among upcoming items — [Native AA post](https://blog.base.dev/native-account-abstraction), [Cobalt post](https://blog.base.dev/cobalt) (apparent slip; unresolved)
- 2026-06-25 and 2026-06-26 block-production outages (sequencer bug) coincided with the Beryl mainnet date — [postmortem](https://blog.base.dev/postmortem-june-25th-block-production-outage)
- Base is marketing stocks: "Trade, lend, and borrow stocks 24/7 on Base" on the home page; B20 explained as the standard behind tokenized stocks (2026-08-27) — [base.org](https://www.base.org/), [B20 post](https://blog.base.dev/b20-tokenized-stocks-on-base)

#### 4c. Base App and Coinbase Wallet
- 2026-09-14 CDP docs call the product "Coinbase Wallet ... formerly known as Base App"; `@base-org/account` remains the install name; see section 3e — [Coinbase Wallet overview](https://docs.cdp.coinbase.com/coinbase-wallet/overview)
- Base's own 2026-03-31 strategy still speaks of Base App. The Base blog feed's newest item is dated 2026-09-01 (read 2026-10-11), so it contains no post about the rename, which surfaced on 2026-09-10 (SDK README) and 2026-09-14 (CDP docs) — [Base blog feed](https://api.paragraph.com/blogs/rss/@base)

#### 4d. Base token
- 2025-09-15 ("The State of Base at BaseCamp 2025"): Base says it is "beginning to explore a network token" with no definitive plans and no details on timing, design or governance — [Base blog feed](https://api.paragraph.com/blogs/rss/@base)
- No token statement in the 2026-03-31 strategy post, on base.org/vision, or in the 2026 engineering posts I read — [Base blog feed](https://api.paragraph.com/blogs/rss/@base), [base.org/vision](https://www.base.org/vision)

#### 4e. Base Batches and grants
- Batch 003 (spring 2026): program 2026-04-06 to 2026-05-19, demo day in San Francisco on 2026-05-19, 1,175 applicants, 12 teams selected; "a few teams building directly with the x402 protocol"; teams include Blockrun.ai (per-request payments via x402), 4Mica (clearing for agentic microtransactions), Agently, Floe Labs (credit for agents); perks from CDP and Coinbase Business — [Base blog feed](https://api.paragraph.com/blogs/rss/@base), [Base Batches page](https://www.base.org/batches)
- Batch 004: applications 2026-08-19 to 2026-09-09 or 09-10 (blog says Sept 9; page says Sept 10), acceptances 2026-09-29, virtual program 2026-09-29 to 2026-11-15, demo day in New York on 2026-11-17; $100K from the Base Ecosystem Fund; focus areas trading, payments, agents and financing; no dedicated x402 track — [Base Batches page](https://www.base.org/batches), [Base blog feed](https://api.paragraph.com/blogs/rss/@base)
- Programs: Base Batches runs twice a year with $100K per team; the Base Ecosystem Fund backs pre-seed and seed teams — [Base docs: Base Batches](https://docs.base.org/get-started/base-batches)

#### 4f. Base's own published x402 statistics
- Only the 2026-05-29 blog figures above (3.1M transactions, $1.2M value, 30 days). The base.org/agents counters (agent transactions, payment volume, active agents, x402 endpoints) are unreadable placeholders in a static fetch — [base.org/agents](https://www.base.org/agents)

### Inferences
- Base's engineering roadmap (B20, validity transactions, native AA, 200 ms blocks) targets trading, stablecoins and wallets; agent payments are served mostly by pointing at x402 and Coinbase tooling, not by protocol features specific to x402.
- The Coinbase Wallet rename moves wallet branding back under Coinbase and shifts SDK documentation to CDP; whether that dilutes the "Base App" consumer brand is unknown.
- Base's May figure (about $0.39 average payment, 3.1M transactions per month) is small next to the $17T stablecoin volume cited in its strategy post; the agent story is a growth bet, not yet a volume driver.

### Gaps
- Base leadership beyond Jesse Pollak who speak on agents: none identifiable; engineering posts are unsigned.
- The Base token: no 2026 primary-source statement either way; a news search was not possible.
- Whether Base's x402 numbers are comparable to x402.org's: unresolved.
- Base blog pages themselves return 403 to my fetch tool; content was read through the Paragraph RSS feed, which may omit formatting and updates.

---

## 5. ERC-8004 (trustless agents): status, deployments, leads, relation to x402, and Base implementations

### Takeaway
ERC-8004 is still "Draft" (it was moved to Review on 2025-10-08 and back to Draft by the EIP editors on 2026-01-13) but its registries have been deployed on Ethereum mainnet and Base mainnet at identical addresses since 2026-01-29. It is co-authored by people from MetaMask, the Ethereum Foundation, Google and Coinbase (Erik Reppel). It is not part of the x402 spec; the EIP says payments are "orthogonal" and shows x402 only as an example of payment proof and a registration flag.

### Cited Findings
- Status and authorship: type Standards Track / ERC, created 2025-08-13, status Draft, requires EIP-155, 712, 721 and 1271; authors Marco De Rossi, Davide Crapis, Jordan Ellis and Erik Reppel; discussion on Ethereum Magicians — [EIP-8004](https://eips.ethereum.org/EIPS/eip-8004), [discussion thread](https://ethereum-magicians.org/t/erc-8004-trustless-agents/25098)
- Status history: "Move to Review (#1244)" on 2025-10-08; on 2026-01-13 an editor commit (#1470) changed `status: Review` to `status: Draft` and added `requires`; later community-feedback edits 2026-01-25 — [file history](https://github.com/ethereum/ERCs/commits/master/ERCS/erc-8004.md), [editor diff](https://github.com/ethereum/ERCs/commit/acf085cb8411e5da26346aec3b67884dbea9b2a0). The QuickNode explorer FAQ also says "currently in Draft status" — [QuickNode FAQ](https://erc-8004.quicknode.com/faq)
- Design: three registries — Identity (ERC-721 with URI storage; global agent id `{namespace}:{chainId}:{registry}` plus token id), Reputation (signed feedback values with tags and optional off-chain files), Validation (validators return a 0 to 100 score) — [EIP-8004](https://eips.ethereum.org/EIPS/eip-8004)
- Deployments: mainnet contracts committed 2026-01-29 ("Updates with Mainnet Contracts (#29)") and a "mainnet deployment" commit 2026-01-31; the README lists the same IdentityRegistry `0x8004A169FB4a3325136EB29fA0ceB6D2e539a432` and ReputationRegistry `0x8004BAa17C55a88189AE136b182e5fdA19dE9b63` on Ethereum, Base, Arbitrum, Avalanche, BSC, Celo, Gnosis, Linea, Mantle, MegaETH, Metis, Monad, Optimism, Polygon, Robinhood Chain, Scroll and others; later additions include 0G (2026-06-11), Injective (2026-04-09) and Robinhood Chain (2026-08-15). No Validation Registry address is listed — [contracts README](https://github.com/erc-8004/erc-8004-contracts), [commits](https://github.com/erc-8004/erc-8004-contracts/commits/master)
- Who leads: the GitHub org `erc-8004` describes itself as "Co-authors of ERC-8004, working with hundreds of builders"; the org's `awesome-8004` README lists the team's X accounts (marco_derossi, DavideCrapis, 13yearoldvc, bluzuli, isha_sangani) and a Telegram community `@ERC8004`; commits to the contracts repo come from Marco De Rossi and contributors `tetratorus` and `Eversmile12` — [erc-8004 org](https://github.com/erc-8004), [awesome-8004](https://github.com/erc-8004/awesome-8004), [contracts commits](https://github.com/erc-8004/erc-8004-contracts/commits/master)
- Relation to x402: the EIP says "Payments are orthogonal to this protocol and not covered here" but gives examples of how x402 payments can enrich feedback; the registration file has an `x402Support` flag and the feedback file has a `proofOfPayment` field "used for x402 proof of payment"; the `agentWallet` key is reserved for the agent's payment address — [EIP source](https://github.com/ethereum/ERCs/blob/master/ERCS/erc-8004.md). Erik Reppel is both an EIP-8004 co-author and x402's creator. The x402 spec folder contains no ERC-8004 spec — [specs folder](https://github.com/x402-foundation/x402/tree/main/specs). The newer x402 Identity working group (repo created 2026-08-03) has no published goals yet — [wg-identity](https://github.com/x402-foundation/wg-identity)
- Implementations touching Base: Coinbase AgentKit's ERC-8004 identity action provider and a LangChain 8004 CDP chatbot example (added 2026-03-23) — [AgentKit provider](https://github.com/coinbase/agentkit/tree/main/typescript/agentkit/src/action-providers/erc8004); Base's `base/skills` repo mentions 8004 in the `wallet-mcp` skill and its description says it covers registering agents; base.org/agents lists ERC-8004 as a pillar; the QuickNode ERC-8004 Explorer indexes Base and says contracts are live on Ethereum, Base, BNB Chain, Avalanche and Mantle — [base/skills](https://github.com/base/skills), [base.org/agents](https://www.base.org/agents), [QuickNode explorer FAQ](https://erc-8004.quicknode.com/faq)
- Third-party reference implementations listed by the 8004 team: ChaosChain, Phala TEE agent, Zpaynow (Rust), Agent0 SDK, Registry Broker — not Base-specific — [awesome-8004](https://github.com/erc-8004/awesome-8004)

### Inferences
- Registries went live on mainnets about two weeks after the EIP was set back to Draft (2026-01-13 versus 2026-01-29) and the EIP has not reached Final, so "ERC-8004 deployed" and "ERC-8004 final" are different claims; an explainer should say "Draft standard, live contracts".
- Identity of x402 and 8004 is linked by authors and examples rather than by any formal dependency; the likely bridge is the planned x402 Identity working group, but its scope is unpublished.

### Gaps
- Number of agents registered on Base and overall: only a search-snippet claim of about 21,000 agents in February 2026 (Ethereum above 11,000) from a page I did not fetch; no primary count.
- Whether the Validation Registry is deployed anywhere: not shown in the README.
- Whether the x402 reputation/trust extension proposals (PR #1024, issue #1777) build on ERC-8004: not checked.
- Jordan Ellis's and Davide Crapis's current roles: affiliations are inferred from EIP header handles and address domains, not stated.

---

## 6. People: who leads x402 work at Coinbase, Base and the Foundation (professional, public information only)

### Takeaway
x402's public faces are Erik Reppel (creator, Coinbase TSC seat), Lincoln Murr (Coinbase head of AI product, community voice), Carson Roscoe and the CDP engineering team on the code side, Jesse Pollak for Base, and Michael Hursta (new Executive Director) for the Foundation. X handles are verifiable for Reppel, Murr, Pollak, Armstrong and several contributors; the Foundation itself has no X handle I could find.

### Cited Findings
Handles are recorded only where an official page or the person's own profile links them; confidence reflects that.

| Name | Role (source) | Handles | How verified | Confidence |
|---|---|---|---|---|
| Erik Reppel | Creator of x402; Head of Engineering, CDP (2025-09-23); Coinbase TSC representative (2026-05-12); EIP-8004 co-author | X: @programmer; GitHub: erikreppel (personal), erikreppel-cb (work) | GitHub profile `erikreppel` (name Erik Reppel) has `twitter_username` = programmer; that account committed "Update footer to Linux Foundation (#2283)" to x402 on 2026-05-12; no Coinbase page linking the handle found — [GitHub](https://github.com/erikreppel), [Cloudflare release](https://www.cloudflare.com/press/press-releases/2025/cloudflare-and-coinbase-will-launch-x402-foundation/), [TSC.md](https://github.com/x402-foundation/x402/blob/main/TSC.md) | Medium-high |
| Lincoln Murr | Head of AI Product, Coinbase (2026-07-14); GitHub `murrlincoln` authored the 2025 roadmap commits (name-to-login match is by handle resemblance) | X: @murrlincoln; GitHub: murrlincoln | x402 repo says "reach out to @murrlincoln on X or GitHub"; docs.x402.org links an X post by @MurrLincoln — [PROJECT-IDEAS.md](https://github.com/x402-foundation/x402/blob/main/PROJECT-IDEAS.md), [docs intro](https://docs.x402.org/introduction), [LF release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/) | High |
| Carson Roscoe | Coinbase engineer, author of the V2 and batch-settlement posts; 210 commits | X: @carsonroscoe7; GitHub: CarsonRoscoe; LinkedIn: ca.linkedin.com/in/carsonroscoe | Personal site linked from his GitHub profile lists the X and LinkedIn links; the site is dated and names no employer; the V2 post lists his name — [site](https://www.carsonroscoe.com), [V2 post](https://x402.org/x402-v2-launch/) | Medium |
| Josh Nickerson | Co-author of the V2 and batch-settlement posts (Coinbase) | none verified | Name appears in official posts only — [batch post](https://x402.org/x402-batch-settlement/) | n/a |
| Jnix2007 | GitHub bio: Product Lead for Wallets, Onchain Tools, and Agentic Commerce at CDP; display name "jnix.base.eth" | X: @Jnix2007 | GitHub self-declared; I did not confirm this handle is the same person as the post author Josh Nickerson — [GitHub](https://github.com/Jnix2007) | High for the handle; identity link unconfirmed |
| phdargen / Philippe d'Argent | `phdargen` is the top committer (234); the batch post names "Philippe d'Argent" (Coinbase) as co-author | none | `phdargen` profile is empty; `PhilBot402` bot says "by @phdargen"; no source ties the handle to the name, so I do not assert it — [PhilBot402](https://github.com/PhilBot402) | n/a |
| Conner Swenberg | Coinbase, batch-settlement post co-author | none verified | official post only — [batch post](https://x402.org/x402-batch-settlement/) | n/a |
| Brian Armstrong | Co-founder and CEO, Coinbase; promotes x402 and "AiFi" on X (2026-07-26) | X: @brian_armstrong | GitHub `barmstrong` self-declares it — [GitHub](https://github.com/barmstrong), [Cointelegraph](https://cointelegraph.com/news/coinbase-ceo-agentic-finance-base-100-million-aifi-transactions) | High |
| Shan Aggarwal | Chief Business Officer, Coinbase; Head of IR on earnings calls; quoted in the April LF release | none verified | [Q2 transcript](https://s27.q4cdn.com/397450999/files/doc_financials/2026/q2/Q2-26-Earnings-Presentation-Transcript.pdf), [April release](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol) | n/a |
| Siddharth Coelho-Prabhu | Head of Coinbase Business (agent payments, 2026-07-23) | none verified | [The Block](https://www.theblock.co/post/409539/coinbase-ai-payments-most-high-conviction-bet-businesses-accepting-agent-payments) | n/a |
| Ash (Must-be-Ash) | DevRel and product designer, CDP; x402 starter content | X: @Must_be_Ash | GitHub self-declared — [GitHub](https://github.com/Must-be-Ash) | High |
| A. / Amanda McDermott | Coinbase; payment-identifier extension, docs and roadmap edits | X: @flyingkittans (on `apmcdermott`) | GitHub self-declared; may be a personal account — [GitHub](https://github.com/apmcdermott) | Medium |
| Jesse Pollak | Created Base and leads it day to day | X: @jessepollak; GitHub: jessepollak; LinkedIn: linkedin.com/in/jessepollak | Personal site jesse.xyz and GitHub field both declare the X handle — [jesse.xyz](https://jesse.xyz), [GitHub](https://github.com/jessepollak) | High |
| Michael Hursta | Executive Director, x402 Foundation (2026-10-01) | none verified | [Hursta release](https://x402.org/linux-foundation-appoints-michael-hursta-as-executive-director-of-the-x402-foundation/) | n/a |
| Jim Zemlin | CEO, Linux Foundation | none verified | quoted in LF releases — [April release](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol) | n/a |
| Rohin Lohe, Steve Kaliski | TSC representatives for Cloudflare and Stripe | none verified (covered by other researchers) | [TSC.md](https://github.com/x402-foundation/x402/blob/main/TSC.md) | n/a |
| Cam Whiteside | Named as Cloudflare co-author of the batch-settlement post; GitHub `CameronWhiteside` authored PR #1145 (profile lists a different company) | none verified | link between post name and GitHub account not confirmed — [post](https://x402.org/x402-batch-settlement/), [PR #1145](https://github.com/x402-foundation/x402/pull/1145) | n/a |
| Marco De Rossi, Davide Crapis | ERC-8004 co-authors | X: @marco_derossi, @DavideCrapis | listed as "ERC-8004 team" X accounts in the official org README; handle-to-name mapping rests on name resemblance — [awesome-8004](https://github.com/erc-8004/awesome-8004) | Medium |
| Notorious D.E.V. (PayAI) | Frequent third-party x402 contributor (33 commits) | X: @notorious_d_e_v | GitHub self-declared — [GitHub](https://github.com/notorious-d-e-v) | High |

- Other self-declared X handles of x402 contributors are in the table in section 1f (for example @samrags_ for `sragss`, @GuiBibeau, @frshbb, @opwizardx).
- Official organisation accounts: Coinbase is @coinbase (the only X account linked from investor.coinbase.com); CDP is @CoinbaseDev (linked in the `cdp-sdk` README); Base is @base (GitHub org field and base.org footer), plus @buildonbase and @baseapp (links on base.org) — [investor.coinbase.com](https://investor.coinbase.com/), [cdp-sdk README](https://github.com/coinbase/cdp-sdk), [Base org](https://github.com/base), [base.org](https://www.base.org/)

### Inferences
- Reppel's three hats (x402 creator, Coinbase TSC seat, ERC-8004 co-author) make him the single best person to follow for protocol direction.
- Murr appears to be the community-facing product owner (roadmap, project ideas, Foundation launch quote).

### Gaps
- Farcaster handles: not verified for anyone.
- Other Coinbase developer-relations X accounts beyond @CoinbaseDev and @coinbase: not checked.
- Any named Base leader for agents or x402 other than Pollak: none found.
- Governing Board members and chair: unpublished.
- Official X account of the x402 Foundation: none found.

---

## 7. Official sources a daily monitor should watch

### Takeaway
The cleanest daily feeds are the x402.org RSS feed, the GitHub tags and commits Atom feeds for `x402-foundation/x402`, the CDP changelog RSS, the Base blog and Base engineering RSS feeds, and the `x402-foundation/tsc` issues; the community discussion itself happens in Slack and the TSC and working-group mailing lists, not Discord.

### Cited Findings
| Source | URL | What it gives | Verified |
|---|---|---|---|
| x402.org RSS | https://x402.org/feed/ | Foundation press releases and protocol posts (5 items: 2025-05-06, 2025-12-11, 2026-05-11, 2026-07-14, 2026-10-01) | Valid RSS read 2026-10-11 — [feed](https://x402.org/feed/) |
| x402 tags Atom | https://github.com/x402-foundation/x402/tags.atom | Every package release (no GitHub Releases exist) | Valid Atom, newest entries 2026-09-29 — [feed](https://github.com/x402-foundation/x402/tags.atom) |
| x402 commits Atom | https://github.com/x402-foundation/x402/commits/main.atom | Spec and SDK changes (about 100 commits a month) | Standard GitHub feed pattern; not fetched |
| x402 repo | https://github.com/x402-foundation/x402 | Issues (695 open on 2026-10-11), PRs, specs | read via API — [repo](https://github.com/x402-foundation/x402) |
| TSC agenda issues | https://github.com/x402-foundation/tsc/issues | Community agenda topics for bi-weekly TSC meetings | read via API — [tsc issues](https://github.com/x402-foundation/tsc/issues) |
| Working-group repos | https://github.com/x402-foundation (wg-identity, wg-tax, wg-domain-discovery, wg-card-acceptance), policy repo `foundation` | WG outputs and policies | read via API — [org](https://github.com/x402-foundation) |
| x402 docs | https://docs.x402.org/llms.txt | Machine-readable docs index (schemes, extensions, networks, facilitators, migration) | read 2026-10-11 — [llms.txt](https://docs.x402.org/llms.txt) |
| x402 Slack | https://join.slack.com/t/x402workspace/shared_invite/zt-49ug1ivvr-M5LYYp_eZ4OD3lA5n2qM1g (also slack.x402.org) | Official community workspace; channels `#tsc-public`, `#github-discussions`, `#general`, WG channels | invite link on [x402.org/get-involved](https://x402.org/get-involved/); guidelines in [foundation repo](https://github.com/x402-foundation/foundation/blob/main/policies-guidelines/slack-guidelines.md) |
| TSC and WG mailing lists | https://lists.x402.org/g/TSC , /g/Domain-Discovery , /g/Identity-Working-Group , /g/tax-working-group , /g/Card-Acceptance-Working-Group | Announcements and agendas | listed in [tsc README](https://github.com/x402-foundation/tsc/blob/main/README.md) |
| LFX meeting calendar | https://zoom-lfx.platform.linuxfoundation.org/meetings/x402-foundation | TSC and WG meetings, recordings | linked from [get-involved](https://x402.org/get-involved/); JavaScript app, not readable |
| x402 Telegram | https://t.me/+ijgZ6c_f0iA1MmY5 | Builder group ("600+ builders" in Dec 2025) | link in [V2 post](https://x402.org/x402-v2-launch/); activity not checked |
| x402.org members page | https://x402.org/members/ | Membership tiers and roster | read 2026-10-11 — [members](https://x402.org/members/) |
| LF press page | https://www.linuxfoundation.org/press | Official LF announcements (April release) | [April release](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol) |
| CDP changelog RSS | https://docs.cdp.coinbase.com/get-started/changelog/rss.xml | Dated product changes (x402, Bazaar, agent wallets, Coinbase for Agents) | Valid RSS read 2026-10-11 — [feed](https://docs.cdp.coinbase.com/get-started/changelog/rss.xml) |
| CDP docs index | https://docs.cdp.coinbase.com/llms.txt | All CDP pages incl. x402, Agentic Wallet, status | [llms.txt](https://docs.cdp.coinbase.com/llms.txt) |
| CDP facilitator page and FAQ | https://docs.cdp.coinbase.com/x402/core-concepts/facilitator , https://docs.cdp.coinbase.com/x402/support/faq | Pricing, networks, schemes, targets (watch for changes) | read 2026-10-11 |
| CDP status | https://docs.cdp.coinbase.com/support/status | Service status | listed in [llms.txt](https://docs.cdp.coinbase.com/llms.txt); not opened |
| CDP Discord | https://discord.com/invite/cdp | CDP support, `#cdp-sdk`, large-traffic notices | linked in [CDP FAQ](https://docs.cdp.coinbase.com/x402/support/faq) and [cdp-sdk README](https://github.com/coinbase/cdp-sdk) |
| Coinbase repos | https://github.com/coinbase/cdp-sdk , /agentkit , /agentic-wallet-skills , /spend-permissions | SDK and agent-tool changes | read via API |
| agentic.market | https://agentic.market (llms.txt at /llms.txt) | Coinbase-run x402 directory; service count | [agentic.market](https://agentic.market) |
| Coinbase earnings and SEC | https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=0001679788&type=8-K | 8-K earnings decks (x402 metrics on slides) and 10-Q; Q2 was 2026-07-30; Q3 date not found | [8-K list](https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany&CIK=0001679788&type=8-K&dateb=&owner=include&count=40) |
| Coinbase blog and CDP Discover | https://www.coinbase.com/blog , https://www.coinbase.com/developer-platform/discover | Product announcements | both returned 403 to my fetch tool; no RSS verified |
| Base blog RSS (strategy, Batches, MCP) | https://api.paragraph.com/blogs/rss/@base (site blog.base.org) | Base strategy posts, Batches, Base MCP | Valid RSS read 2026-10-11; items up to 2026-09-01 — [feed](https://api.paragraph.com/blogs/rss/@base) |
| Base engineering blog RSS | https://api.paragraph.com/blogs/rss/@base-engineering-blog (site blog.base.dev) | Upgrades (Azul, Beryl, Cobalt), postmortems, native AA | read 2026-10-11 — [feed](https://api.paragraph.com/blogs/rss/@base-engineering-blog) |
| Base upgrades page | https://docs.base.org/upgrades/overview | Activation dates; Denim targets Sepolia Oct 2026, mainnet Nov 2026 | [page](https://docs.base.org/upgrades/overview) |
| Base docs index | https://docs.base.org/llms.txt | Agent, x402, builder-code and Batches docs | [llms.txt](https://docs.base.org/llms.txt) |
| Base status and community | https://status.base.org , https://discord.gg/buildonbase , https://x.com/base , https://x.com/buildonbase , https://x.com/baseapp | Status, Discord, official X accounts | footer and news links on [base.org](https://www.base.org/) |
| Base repos | https://github.com/base/base , /docs , /skills , /account-sdk , /commerce-payments | Chain, docs, agent skills, account SDK, escrow contracts | read via API |
| Base Batches | https://www.base.org/batches | Batch 004 runs to 2026-11-15; demo day 2026-11-17 NYC | [page](https://www.base.org/batches) |
| ERC-8004 spec | https://eips.ethereum.org/EIPS/eip-8004 ; file history https://github.com/ethereum/ERCs/commits/master/ERCS/erc-8004.md | Status changes (Draft now) | [EIP](https://eips.ethereum.org/EIPS/eip-8004) |
| ERC-8004 discussion | https://ethereum-magicians.org/t/erc-8004-trustless-agents/25098 | Spec debate | linked in EIP header |
| ERC-8004 contracts and org | https://github.com/erc-8004/erc-8004-contracts , https://github.com/erc-8004 | New chain deployments (commits) | [contracts](https://github.com/erc-8004/erc-8004-contracts) |
| ERC-8004 team X and Telegram | @marco_derossi, @DavideCrapis, Telegram @ERC8004 | Team news | listed in [awesome-8004](https://github.com/erc-8004/awesome-8004) |

X accounts to follow (verified as noted in section 6): @coinbase, @CoinbaseDev, @base, @buildonbase, @baseapp, @jessepollak, @murrlincoln, @programmer, @brian_armstrong, @Must_be_Ash, @carsonroscoe7 (medium confidence), @Jnix2007; ERC-8004: @marco_derossi, @DavideCrapis. No Foundation account found.

Newsletters: none verified for x402, CDP or Base. The CDP changelog RSS and the x402 TSC and working-group mailing lists are the closest equivalents.

### Inferences
- For a daily job, poll `x402.org/feed/`, the two GitHub Atom feeds, the CDP changelog RSS, and the two Base RSS feeds, then check TSC issues; read Coinbase 8-Ks on earnings days for x402 slide updates.
- Discord is not an official x402 channel; Slack requires an invite and is explicitly "not a system of record".

### Gaps
- Coinbase's own blog or CDP Discover RSS: could not verify.
- Newsletter sign-ups for CDP, Base or the Foundation: none found.
- Coinbase Q3 2026 earnings date: not found (the investor.coinbase.com home page lists no upcoming events).
- The commits Atom feed was not fetched (standard GitHub pattern).

---

## 8. Dated timeline (key earlier milestones as context, then 2026-04-01 to 2026-10-11, then upcoming)

### Takeaway
The last six months were defined by governance (LF operational launch, Executive Director), scheme expansion (upto, batch-settlement, auth-capture), Coinbase packaging x402 into agent and business products, and Base shipping chain upgrades while positioning for agents and tokenized assets.

### Cited Findings
| Date | Event | Source |
|---|---|---|
| 2025-05-06 | x402 announced as an open standard (context) | [x402.org feed](https://x402.org/feed/) |
| 2025-09-17 | x402 Bazaar launched; Google AP2 + x402 demo (context) | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2025-09-23 | Cloudflare and Coinbase announce plan for an x402 Foundation (context) | [Cloudflare release](https://www.cloudflare.com/press/press-releases/2025/cloudflare-and-coinbase-will-launch-x402-foundation/) |
| 2025-12-11 | x402 V2 launch; `@x402/core` v2.0.0 (context) | [V2 post](https://x402.org/x402-v2-launch/), [tags](https://github.com/x402-foundation/x402/tags) |
| 2026-01-15 | CDP facilitator billing starts: 1,000 free per month then $0.001 (context) | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-01-29 | ERC-8004 registries deployed on mainnets incl. Base (context) | [contracts repo](https://github.com/erc-8004/erc-8004-contracts/commits/master) |
| 2026-02-11 | Agentic Wallet launch; Payments MCP moved to x402 v2 (context) | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-03-31 | x402 Technical Charter adopted; Base 2026 strategy post published | [Charter](https://github.com/x402-foundation/x402/blob/main/foundation/x402%20Technical%20Charter%20March%2031%2C%202026.pdf), [Base blog feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-04-01 | `x402-foundation` GitHub org created | [GitHub org](https://github.com/x402-foundation) |
| 2026-04-02 | LF announces it is launching the x402 Foundation (22 supporters listed); `coinbase/x402` fork created | [LF release](https://www.linuxfoundation.org/press/linux-foundation-is-launching-the-x402-foundation-and-welcoming-the-contribution-of-the-x402-protocol), [coinbase/x402](https://github.com/coinbase/x402) |
| 2026-04-08 | Base Batches 003 announced (x402 teams in cohort) | [Base blog feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-04-09/10 | CDP launches `upto` on the facilitator (usage-based x402) | [Cointelegraph](https://www.cointelegraph.com/news/coinbase-x402-rolls-out-usage-based-pricing-agentic-ai) |
| 2026-04-13 | `@x402/core` v2.10.0 tagged | [tags](https://github.com/x402-foundation/x402/tags) |
| 2026-04-14 | CDP: CDP CLI and MCP server; x402 Bazaar semantic search and MCP discovery | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-04-15 | `batch-settlement` + Cloudflare binding merged (PR #1145) | [PR](https://github.com/x402-foundation/x402/pull/1145) |
| 2026-04-20 to 21 | Base Azul on Sepolia (04-20); Azul announcement (04-21); mainnet 05-13 per post, 05-28 per docs | [Azul post](https://blog.base.dev/introducing-base-azul), [Base upgrades](https://docs.base.org/upgrades/overview) |
| 2026-04-24 | x402 auth-hints extension merged (#1902) | [path history](https://github.com/x402-foundation/x402/commits/main/specs/extensions) |
| 2026-05-04 | builder_code extension spec merged (#2050) | [path history](https://github.com/x402-foundation/x402/commits/main/specs/extensions) |
| 2026-05-05 | Coinbase 8-K: restructuring of about 700 positions (14%) | [8-K](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000049/coin-20260505.htm) |
| 2026-05-07 | Coinbase Q1 results: deck says 100M+ x402 payments as of Q1; 99%+ USDC, 90%+ Base | [slide 15](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000053/q126earningsdeck-finalse015.jpg) |
| 2026-05-11 | "Introducing x402 Batch Settlement" post | [x402.org feed](https://x402.org/feed/) |
| 2026-05-12 | `TSC.md` created (Coinbase, Cloudflare, Stripe reps); footer updated to Linux Foundation (#2283) | [TSC.md](https://github.com/x402-foundation/x402/blob/main/TSC.md) |
| 2026-05-13 | `base/base-mcp-legacy` last pushed (repo is now archived) | [repo](https://github.com/base/base-mcp-legacy) |
| 2026-05-19 | Base Batches 003 demo day, San Francisco | [Base blog feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-05-20 | `auth-capture` spec files renamed/present | [path history](https://github.com/x402-foundation/x402/commits/main/specs/schemes/auth-capture) |
| 2026-05-26 | Base MCP introduced | [Base blog feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-05-29 | Base post "The Agentic Economy Is Here": x402 on Base 3.1M tx and $1.2M in 30 days | [Base blog feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-06-03 | Chainalysis: 100M+ x402 transactions on Base in about nine months | [Cointelegraph](https://cointelegraph.com/news/agentic-payment-activity-surpasses-100m-transactions-on-base) |
| 2026-06-12 | CDP: Coinbase CLI/MCP, Sign in with Base, Payment APIs, Custom Stablecoins, x402 + Amazon Bedrock AgentCore; `@x402/core` v2.15.0 | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [tags](https://github.com/x402-foundation/x402/tags) |
| 2026-06-18 / 06-25 | Base Beryl (B20) on Sepolia / mainnet; outages 06-25 and 06-26 | [Base upgrades](https://docs.base.org/upgrades/overview), [postmortem](https://blog.base.dev/postmortem-june-25th-block-production-outage) |
| 2026-06-19 | CDP: remote MCP connector for Coinbase for Agents; x402 builder-code attribution | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-07-10 | `x402-foundation/tsc` repo created | [tsc](https://github.com/x402-foundation/tsc) |
| 2026-07-14 | LF operational launch of x402 Foundation, 40 members | [press release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/) |
| 2026-07-17 | CDP: `@coinbase/cdp-sdk/x402`; Base: native AA (EIP-8130) announced | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [Native AA post](https://blog.base.dev/native-account-abstraction) |
| 2026-07-23 | Coinbase Business agent payments, Coinbase for Agents and an x402 SDK reported | [The Block](https://www.theblock.co/post/409539/coinbase-ai-payments-most-high-conviction-bet-businesses-accepting-agent-payments) |
| 2026-07-26/27 | Armstrong X post on "AiFi" (Base, USDC, x402) | [Cointelegraph](https://cointelegraph.com/news/coinbase-ceo-agentic-finance-base-100-million-aifi-transactions) |
| 2026-07-27 | `@x402/core` v2.20.0 tagged | [tags](https://github.com/x402-foundation/x402/tags) |
| 2026-07-30 | Coinbase Q2: deck says 97%+ of onchain agentic transactions used x402 (Artemis); 10-Q filed | [slide 18](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000087/q226earningsdeck_sec018.jpg), [10-Q](https://www.sec.gov/Archives/edgar/data/1679788/000167978826000088/coin-20260630.htm) |
| 2026-08-03 / 08-19 | Identity and Tax working-group repos created | [wg-identity](https://github.com/x402-foundation/wg-identity), [wg-tax](https://github.com/x402-foundation/wg-tax) |
| 2026-08-06 | CDP: Payment Acceptance GA; agentic payments on Coinbase Business Checkouts via x402 | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-08-13 | x402 Foundation Directed Fund charter "Amended August 13, 2026" | [participation agreement](https://cdn.platform.linuxfoundation.org/agreements/x402-foundation.pdf) |
| 2026-08-17 / 08-21 | Coinbase for Agents adds dated futures and S&P 500 equities | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog) |
| 2026-08-19 | Base Batches 004 announced | [Base blog feed](https://api.paragraph.com/blogs/rss/@base) |
| 2026-08-27 | Base B20 tokenized-stocks post | [B20 post](https://blog.base.dev/b20-tokenized-stocks-on-base) |
| 2026-09-04 | `@x402/core` v2.25.0 tagged | [tags](https://github.com/x402-foundation/x402/tags) |
| 2026-09-10 | `base/account-sdk` README notes "Base Account is now Coinbase Wallet" | [commit history](https://github.com/base/account-sdk/commits/main/README.md) |
| 2026-09-14 | CDP: Coinbase Wallet docs, `upto` on Solana, Java SDK; `wg-domain-discovery` repo created | [CDP changelog](https://docs.cdp.coinbase.com/get-started/changelog), [wg-domain-discovery](https://github.com/x402-foundation/wg-domain-discovery) |
| 2026-09-23 | Card Acceptance WG repo; Base Cobalt on Sepolia; Lightning exact spec (#2861) merged | [wg-card-acceptance](https://github.com/x402-foundation/wg-card-acceptance), [Base upgrades](https://docs.base.org/upgrades/overview), [commits](https://github.com/x402-foundation/x402/commits/main) |
| 2026-09-25 / 09-29 | Solana batch-settlement SDK code merged (#3164, #3603) | [commits](https://github.com/x402-foundation/x402/commits/main) |
| 2026-09-29 | `@x402/core` v2.28.0 and `pypi-x402` v2.25.0 tagged; `foundation` policy repo with Slack guidelines; Batch 004 acceptances | [tags Atom](https://github.com/x402-foundation/x402/tags.atom), [foundation repo](https://github.com/x402-foundation/foundation), [Base Batches](https://www.base.org/batches) |
| 2026-09-30 | Base Cobalt live on mainnet | [Base upgrades](https://docs.base.org/upgrades/overview) |
| 2026-10-01 | LF appoints Michael Hursta Executive Director of the x402 Foundation | [release](https://x402.org/linux-foundation-appoints-michael-hursta-as-executive-director-of-the-x402-foundation/) |
| 2026-10-06 | auth-capture TypeScript SDK v1.1 and builder-code settlement metadata `m` merged | [commits](https://github.com/x402-foundation/x402/commits/main) |
| Upcoming: October 2026 (Sepolia) and November 2026 (mainnet target) | Base Denim upgrade (200 ms native blocks); dates are planning targets | [Base upgrades](https://docs.base.org/upgrades/overview) |
| Upcoming: 2026-11-15 and 2026-11-17 | Base Batches 004 program ends; demo day New York | [Base Batches](https://www.base.org/batches) |
| Upcoming: bi-weekly | TSC and working-group meetings (LFX calendar) | [tsc README](https://github.com/x402-foundation/tsc/blob/main/README.md) |

### Inferences
- Governance, schemes and Coinbase's agent products are moving in parallel; the next visible catalysts are the Denim upgrade, Batch 004 demo day, Coinbase's Q3 results (date unknown) and whatever the new Executive Director and the working groups publish.

### Gaps
- Several rows rely on commit or tag dates rather than announcements; product "launch" days may differ from merge days.
- Events I could not date because primary pages were blocked: Coinbase blog posts, Coinbase Ventures activity, any Base token news in 2026.
