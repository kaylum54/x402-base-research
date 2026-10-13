# Non-token x402 infrastructure on Base: due diligence profiles

Research date: 2026-10-11. Window for "last six months": 2026-04-11 to 2026-10-11. All web pages were accessed on 2026-10-11 unless a different date is shown. Projects covered: thirdweb (x402 line), Merit Systems, ampersend (Edge & Node), MCPay, Mogami, x402.rs, OpenX402, Crossmint.

## Method and limits

- Primary sources first: each project's site, docs, blog and changelog; GitHub through `gh api` (about 300 calls, at the cap); npm registry and downloads API; crates.io API; Base public RPC (https://mainnet.base.org) for facilitator-address transaction counts; the public Warpcast API for Farcaster profile checks.
- The web search quota ran out after about 20 queries. Press, LinkedIn, Crunchbase and Dune checks that needed search were not possible. These are marked "Gap".
- x402scan.com is a client-rendered app. Its live numbers could not be read from a fetch, and the browser pane refused navigation. No Dune dashboard was found for any project (not searched after the quota ran out).
- Main gaps: per-facilitator and per-server x402scan statistics; Dune dashboards; Edge & Node's funding history; any thirdweb or Crossmint round after 2022 and 2025; FareSide's pricing and status (site would not load); who runs OpenX402 and what its "Open token" is; the formal relationship between thirdweb and Agent Labs; X and LinkedIn handles for most people outside Merit; Farcaster accounts for most projects.
- On-chain proxy: for each facilitator address listed in the x402scan code, I read the Base nonce (number of transactions the address has sent) at several past blocks. Base blocks are 2 seconds apart, so 604,800 blocks is 14 days. The nonce counts every transaction the address sent, not only x402 settlements, and a facilitator can use other addresses. Treat it as an activity gauge, not as payment volume. Source for addresses: [x402scan facilitator configs](https://github.com/Merit-Systems/x402scan/tree/main/packages/external/facilitators/src/facilitators). Source for counts: Base RPC `eth_getTransactionCount` at latest block 52,464,025, queried 2026-10-11.
- X handles are recorded only when an official page, the person's own GitHub profile (`twitter_username` field) or a Farcaster-connected account gives them. The "how verified" note says which. Pseudonymous people are not linked to real identities.
- Pace benchmark used below: the reference repo [x402-foundation/x402](https://github.com/x402-foundation/x402) had 529 commits in the 26 weeks to 2026-10-11 (about 20 a week) and `@x402/core` published 19 npm releases between 2026-04-11 and 2026-09-29 ([npm registry](https://registry.npmjs.org/@x402/core)). Small AI-assisted teams in this set ship far more: Merit's OpenInstinct had 319 commits in August 2026, and agent-labs-dev/fastbrowse had 268 commits from one author in its first 3.5 weeks.

## Short answers to the key questions

- **thirdweb**: x402 is one of six featured products and a small code footprint (26 commits ever in the SDK's x402 folder, 23 by one person, Joaquim Verges). The facilitator and SDK shipped Sep-Oct 2025. After the x402 v2 update on 2026-01-13 there is one x402 commit (2026-09-10) and no x402 changelog entry. Verges, CEO Furqan Rydhan and top all-time committer Jonas Daniels all commit to repos of a separate company, Agent Labs (Nebula; org created 2026-03-24), in 2026. The lead (facilitator and payments SDK shipped in 2025) is right for 2025 and out of date for 2026.
- **Merit Systems**: confirmed $10M seed on 2025-01-16 led by a16z crypto and Blockchain Capital, raised for "open-source capitalism", before x402. x402 products: x402scan (Sep 2025), AgentCash wallet/CLI, `@agentcash/router`, MPPscan (an explorer for the rival MPP protocol), an Echo x402 SDK (stalled), Poncho. Team: Sam Ragsdale (CEO), Ryan Sproule (founder and CTO), Mason Hall, Jason Hedman. Since August 2026 the founders moved to a consumer iMessage assistant (OpenInstinct) and cut x402scan features.
- **ampersend**: confirmed. Edge & Node (The Graph's core developer) announced it 2025-10-30; open beta since 2026-04-01 on Base and USDC; TRM Labs screening and an AWS AgentCore Payments tie-in. No named customers and tiny SDK use (212 npm downloads a month). Public SDK paused since 2026-06-23. Fronted by Edge & Node's CEO Rodrigo Coelho, who presents it, with a small engineering team; no separate product lead is named.
- **MCPay**: dead as a brand. mcpay.tech redirects to Frames (frames.ag), the same builder's new product. **Mogami**: one-person Java stack on Base, stalled since May 2026. **x402.rs**: solo Rust maintainer, strong crates, stalled since 2026-07-13. **OpenX402**: anonymous free facilitator on Base, Solana and Monad, live on-chain, no public code.
- **Crossmint**: x402 is a side feature (buyer-side agent wallets, one docs page, two x402 commits in six months). The core bet is agent cards, checkouts and stablecoin infrastructure.
- **Leads from memory, checked**: thirdweb right for 2025, stale for 2026. Merit's funding is right, but the round pre-dates x402, and Echo is a user-pays AI SDK with an x402 add-on that has been abandoned since Nov 2025 (x402scan came later, Sep 2025). ampersend right. MCPay is dead; Mogami is a Java stack on Base; x402.rs is a multi-chain Rust toolkit, not Base-specific; OpenX402 is a free facilitator with an anonymous operator. Crossmint right but narrow.
- **Money**: thirdweb charges 0.3% per facilitated x402 transaction. Merit has not stated how AgentCash earns (Echo takes 2.5% of developer profits). ampersend is free during beta, pricing "announced soon". Crossmint charges $0.05 per agent checkout execution and has no x402-specific fee. Mogami, x402.rs and OpenX402 run free facilitators.

---

## 1. thirdweb (x402 product line)

### One-line
A web3 developer platform (wallets, bridge, contracts, RPC, payments) that sells a hosted x402 facilitator plus client and server x402 SDK code; its homepage now reads "Infrastructure for AI Agents" ([thirdweb.com](https://thirdweb.com), 2026-10-11).

### x402 role
Facilitator and SDK/tooling. The facilitator verifies signatures and settles on-chain through the developer's own thirdweb server wallet, gasless via EIP-7702 ([facilitator docs](https://portal.thirdweb.com/payments/x402/facilitator)). Client side: `wrapFetchWithPayment` and a React hook `useFetchWithPayment`; server side: `settlePayment` and `verifyPayment` ([x402 docs](https://portal.thirdweb.com/x402), [changelog 2025-10-09](https://portal.thirdweb.com/changelog/x402-support)). It also ships a buyer proxy endpoint `/v1/payments/x402/fetch` (2025-10-02, [post](https://portal.thirdweb.com/changelog/x402-fetch-with-payment-in-the-thirdweb-api)), an x402 analytics dashboard (2025-11-12) and developer fee sharing (2025-11-19) ([changelog list](https://portal.thirdweb.com/changelog), [fee sharing post](https://portal.thirdweb.com/changelog/fee-sharing-for-x402-transactions)).
**Core bet or side feature:** one of six homepage products (Token, Bridge, x402, AI, Wallets, Gateway). Money: 0.3% fee on each transaction run through the facilitator ([pricing](https://thirdweb.com/pricing)), plus server-wallet request fees ($1 per 1,000 requests after the first 1,000) and plans from $99 a month.

### Chains
Not Base-primary. 170+ EVM chains for tokens with ERC-2612 or ERC-3009, plus Solana (live 2025-11-11) ([x402 docs](https://portal.thirdweb.com/x402), [changelog](https://portal.thirdweb.com/changelog)). x402scan tracks thirdweb's facilitator on Base and Polygon ([x402scan config](https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/thirdweb.ts)).

### Token
None found. thirdweb's "Token" product is a launch tool for customers, not a thirdweb token ([homepage](https://thirdweb.com)). Gap: no search for token rumours after the quota ended.

### Team
- **Furqan Rydhan**, co-founder and CEO ([TechCrunch, 2022-08-24](https://techcrunch.com/2022/08/24/thirdweb-raises-24m-at-a-160m-valuation-from-haun-ventures-shopify-and-coinbase-for-its-web3-development-kit)). GitHub [furqanrydhan](https://github.com/furqanrydhan) (bio "building tech @f-inc @thirdweb-dev"); X FurqanR from that profile's `twitter_username` (self-declared, high confidence); Farcaster @furqan, bio "Building @thirdweb & f.inc" ([Warpcast API](https://client.warpcast.com/v2/user-by-username?username=furqan), no linked X, medium-high confidence). Doxxed.
- **Steven Bartlett**, co-founder per TechCrunch. No handles verified.
- **Joaquim Verges**, the x402 lead in practice: byline on the x402 changelog posts I opened (2025-09-23, 10-02, 10-07, 10-09, 11-19, 2026-01-13) and 23 of the 26 commits ever made to `packages/thirdweb/src/x402` ([commit history](https://github.com/thirdweb-dev/js/commits/main/packages/thirdweb/src/x402)). GitHub [joaquim-verges](https://github.com/joaquim-verges), X joenrv (self-declared on GitHub), company field now "@agent-labs-dev". Doxxed; his title was not confirmed from an official page.
- **0xFirekeeper** ("Firekeeper"), pseudonymous, now the main maintainer: 57 of about 72 commits to `thirdweb-dev/js` since 2026-04-11 ([commits](https://github.com/thirdweb-dev/js/commits/main)). No X handle on the profile.
- **Jonas Daniels** (jnsdls), top all-time contributor (1,673 commits), GitHub company "thirdweb", X jnsdls (self-declared), now a public member of [agent-labs-dev](https://github.com/agent-labs-dev).
- Others with thirdweb ties and no commits in the last 28 weeks: Manan Tank (X MananTank_), Adam Majmudar (X MajmudarAdam), Nacho Iacovino, greg (gregfromstl), Kien Ngo ([contributor stats](https://github.com/thirdweb-dev/js/graphs/contributors)).

### Track record and pivots
- 2021-02-23: GitHub org created; 2021-09-16 `contracts` repo; company founded 2021 as an NFT/DAO/game toolkit, $5M seed ([TechCrunch](https://techcrunch.com/2022/08/24/thirdweb-raises-24m-at-a-160m-valuation-from-haun-ventures-shopify-and-coinbase-for-its-web3-development-kit); repo dates from [GitHub](https://github.com/thirdweb-dev)).
- 2022-08-24: $24M Series A. 2022-08-28: `js` SDK repo. 2022-11-11: Unity SDK. 2023-03-02: Engine (server wallets). 2024-01-19: pay gateway contracts. 2024-09-16: Insight. 2025-01-03: Nebula AI SDK. 2025-05-11: engine-core.
- 2025-09-23: x402 on 35 chains; 2025-10-07: first facilitator transaction on Base (x402scan config); 2025-11-11: Solana x402; 2025-10-31: `x402.chat` demo (last commit 2025-12-12).
- 2026-01-13: x402 v2. 2026-03-24: Agent Labs org created; its "Nebula" workspace shares a name with thirdweb's earlier Nebula AI.
- The older tagline "The complete web3 development platform" still shows in the site's page metadata, while the homepage now says "Infrastructure for AI Agents" ([thirdweb.com](https://thirdweb.com)). Inference: the leadership appears to be putting its own time into Agent Labs; no official statement explains the relationship.

### Trend-hopping score: 3
Real products each cycle (NFTs, wallets, account abstraction, payments, AI, x402), but the pitch changes with each narrative and the x402 push peaked for about four months (Sep 2025 to Jan 2026).

### Funding
- Seed $5M (2021; angels including Mark Cuban and Gary Vaynerchuk) and Series A $24M at a $160M valuation, announced 2022-08-24, led by Haun Ventures with Coinbase Ventures, Shopify, Polygon, Protocol Labs ([TechCrunch](https://techcrunch.com/2022/08/24/thirdweb-raises-24m-at-a-160m-valuation-from-haun-ventures-shopify-and-coinbase-for-its-web3-development-kit); [VCBacked](https://www.vcbacked.co/company/thirdweb), data last updated 2022-08-25).
- No later round and no x402 grant found. Gap: Crunchbase blocked (HTTP 403) and search quota gone, so a 2023-2026 round cannot be ruled out.

### Product and traction
- No official x402 usage numbers; the [x402 page](https://thirdweb.com/x402) gives none.
- Base address `0x80c08de1a05df2bd633cf520754e40fde3c794d3` (x402scan "thirdweb", first transaction 2025-10-07) had sent 135,666 transactions by 2026-10-11, up 97 in 14 days, 221 in 30 days, 861 in 90 days and 2,957 in 180 days. Facilitated payments mostly run through customers' own server wallets, so this undercounts. Computed from the [Base RPC](https://mainnet.base.org).
- `thirdweb` npm: 206,368 downloads from 2026-09-10 to 2026-10-09 (whole SDK, not x402) ([npm API](https://api.npmjs.org/downloads/point/last-month/thirdweb)). `thirdweb-dev/js`: 639 stars.
- x402 code surface: 13 files in `packages/thirdweb/src/x402`.

### Last six months (2026-04-11 to 2026-10-11)
- Stable SDK releases (9): 5.120.0 on 05-11, 5.120.1 on 06-10, 5.121.0 on 08-13, 5.121.1 on 08-20, 5.121.2 on 09-07, 5.121.3 on 09-10, 5.121.4 on 09-11, 5.121.5 and 5.121.6 on 09-22 ([releases](https://github.com/thirdweb-dev/js/releases)). The other 59 npm versions are nightly builds ([npm registry](https://registry.npmjs.org/thirdweb)).
- Only x402 change: 5.121.3 (2026-09-10), "accept x402 v2 payment requirements that specify amount", PR #8941 by 0xFirekeeper.
- Commits to `thirdweb-dev/js` by month: Apr 5, May 2, Jun 4, Jul 1, Aug 26, Sep 33, Oct 4 (to 10-02). Last commit 2026-10-02, "[Portal] Update server wallet gas premium to 2.5%". For scale: 15 to 32 commits a week in Oct-Dec 2025 ([weekly stats](https://github.com/thirdweb-dev/js/graphs/commit-activity)).
- Stable releases per month before: 12 to 23 a month through Nov 2025, 7 in Dec 2025, 3 a month Jan-Mar 2026, then 0 to 2 a month Apr-Aug.
- Public changelog: newest entry 2026-02-10; none since ([changelog](https://portal.thirdweb.com/changelog)). Blog: crypto news posts through 2026-08-03, none about x402 ([blog](https://blog.thirdweb.com/)).
- thirdweb.com/x402 is marked published 2026-09-25 with no new content listed.
- People: no official joins or departures found. Agent Labs repos created 2026-04-17 (homebrew-nebula), 2026-09-17 (fastbrowse) and 2026-09-22 (bugpatrol, contributors joaquim-verges 23, jnsdls 12, furqanrydhan 9) ([GitHub](https://github.com/agent-labs-dev/bugpatrol)); nebula.gg footer reads "Agent Labs, Inc. Built in San Francisco" ([nebula.gg](https://nebula.gg)).

### Pace verdict
Slow, plainly. One x402 commit in six months against 20 a week at the reference repo, and about 0 to 2 stable releases a month against the x402 core's 3 to 4. For scale, Agent Labs' fastbrowse repo got 268 commits from one author in its first 3.5 weeks. Releases did pick up in Sep 2026 (5), but only one touched x402.

### Direction
Stated: agents and "thousands of chains" ([x402 page](https://thirdweb.com/x402), [homepage](https://thirdweb.com)). Shipped: no new x402 feature since v2 (2026-01-13), no x402 changelog since. Inference: the company wants the agent label, while the people who built the x402 line are working elsewhere.

### Competitors
Coinbase CDP facilitator (free to 1,000 transactions a month, then $0.001 each; verification free; x402 v2 schemes `exact`, `upto`, `batch-settlement`) ([CDP docs](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator.md)). Others listed at [docs.x402.org](https://docs.x402.org/dev-tools/facilitators): PayAI, Corbits, Dexter, Polygon, Celo, Fireblocks, Meridian, Mogami. The official `@x402/core` package had 1,492,519 downloads in the same month. My calculation: thirdweb's 0.3% is cheaper than CDP's flat $0.001 only below about $0.33 per payment. Ahead: Coinbase and the platform layer (covered elsewhere).

### Green and red flags
- Green: funded, established company; documented fee model and dashboard; multi-chain; v2 shipped quickly (2026-01-13); Solana support.
- Red: x402 lead and CEO now commit to another company's repos; public changelog silent since 2026-02-10; commit rate down about 70% (Aug-Sep) to 97% (Apr-Jul) and stable releases down from 12-23 a month to 0-5 a month, compared with Q4 2025; maintainer concentration (57 of about 72 commits); low visible facilitator use; blog is generic news.

### Verdict
Credible but small (x402 line); thirdweb overall is a serious, established builder. Momentum: Slowing, near Stalled for x402. The effort was a four-month sprint led by one engineer who now commits to Agent Labs repos, and what remains is maintenance by one pseudonymous developer. Expect the facilitator to keep running because it earns 0.3%, but not much new. Check monthly through GitHub releases, not daily. Watch for an Agent Labs announcement that explains the split.

### Tracking card
- Website https://thirdweb.com ; x402 https://thirdweb.com/x402 ; docs https://portal.thirdweb.com/x402 ; blog https://blog.thirdweb.com/ ; changelog https://portal.thirdweb.com/changelog (no RSS found).
- GitHub org https://github.com/thirdweb-dev ; key repos `js` (SDK, x402 in `packages/thirdweb/src/x402`), `x402.chat`, `engine`, `engine-core`. Release feed https://github.com/thirdweb-dev/js/releases.atom
- X: @thirdweb (GitHub org field and Farcaster-linked). People: @FurqanR, @joenrv, @jnsdls (self-declared on GitHub).
- Farcaster: @thirdweb (4,051 followers, X linked), @furqan.
- Discord/Telegram: Telegram linked on homepage; Discord not listed (Gap).
- x402scan: facilitator id `thirdweb`, url https://api.thirdweb.com/v1/payments/x402, active Base address above plus nine deprecated Base addresses (first seen 2025-11-20). Page https://www.x402scan.com/facilitator/thirdweb
- Dune: none found.

### Sources (accessed 2026-10-11)
https://thirdweb.com ; https://thirdweb.com/x402 ; https://thirdweb.com/pricing ; https://portal.thirdweb.com/x402 ; https://portal.thirdweb.com/payments/x402/facilitator ; https://portal.thirdweb.com/changelog ; changelog posts at https://portal.thirdweb.com/changelog/x402-support , /expanding-x402-payments-to-26-new-chains , /x402-payments-in-any-erc20-token , /x402-fetch-with-payment-in-the-thirdweb-api , /fee-sharing-for-x402-transactions , /support-for-x402-protocol-v2 ; https://blog.thirdweb.com/ ; https://techcrunch.com/2022/08/24/thirdweb-raises-24m-at-a-160m-valuation-from-haun-ventures-shopify-and-coinbase-for-its-web3-development-kit ; https://www.vcbacked.co/company/thirdweb ; https://github.com/thirdweb-dev/js (via gh api: commits, releases, stats) ; https://github.com/agent-labs-dev ; https://nebula.gg ; https://registry.npmjs.org/thirdweb ; https://api.npmjs.org/downloads/point/last-month/thirdweb ; https://docs.cdp.coinbase.com/x402/core-concepts/facilitator.md ; https://docs.x402.org/dev-tools/facilitators ; https://client.warpcast.com/v2/user-by-username?username=thirdweb ; https://www.privateequitywire.co.uk/thirdweb-raises-24m-series-round-160m-valuation/ (founding year, search result only) ; https://mainnet.base.org (RPC).

---

## 2. Merit Systems (x402scan, AgentCash, Echo and others)

### One-line
A New York startup that now calls itself "an agentic commerce product house" ([merit.systems](https://merit.systems)); it runs x402scan (the public x402 explorer), MPPscan, the AgentCash agent wallet and CLI, and the open-source `@agentcash/router` seller library.

### x402 role
Discovery/analytics (x402scan indexes servers, buyers, facilitators and transactions on Base and Solana; MPPscan does the same for the rival Machine Payments Protocol on Tempo, "built with Stripe and Tempo") ([llms.txt](https://merit.systems/llms.txt)). Buyer/agent client: AgentCash, "a wallet and MCP server that pays for x402 or MPP APIs per call", and the Poncho desktop agent. Seller tooling: `@agentcash/router` ([README](https://github.com/Merit-Systems/agentcash-router)) and Merit's own paid API servers (StableEnrich at stableenrich.dev, StableStudio, StableSocial, StableEmail, StablePhone, StableUpload at agentupload.dev; named in the [agentcash-skills README](https://github.com/Merit-Systems/agentcash-skills)). Also an AI-billing SDK: Echo's `@merit-systems/ai-x402` (created 2025-10-10, last publish 2025-12-18). Not a facilitator; the router defaults to Coinbase's CDP facilitator.
**Core bet or side feature:** x402 was the core of Merit's work from Sep 2025 to Jul 2026, hedged with MPP; the commit record suggests it has been sidelined since August by consumer products (inference). **Money:** AgentCash fees and revenue model are not stated ([docs](https://agentcash.dev/docs)). Echo says "No fees by default. 2.5% fees on profits" ([echo.merit.systems](https://echo.merit.systems)). No revenue line was found for x402scan. Gap.

### Chains
Base is primary for x402; Solana second. x402scan covers Base and Solana ([llms.txt](https://merit.systems/llms.txt)); the router reads a Base builder code, takes optional Solana payee settings and notes that `upto` is Base-only ([README](https://github.com/Merit-Systems/agentcash-router)); MPP runs on Tempo.

### Token
None found or announced. The "Open USD" stablecoin consortium in Merit's July 2026 report is a third party (Open Standard), not a Merit token ([report](https://www.merit.systems/blog/state-of-agentic-commerce-july-2026)).

### Team
- **Sam Ragsdale**, co-founder and CEO. X @samrags_, GitHub sragss, LinkedIn sam-ragsdale-2ba55b122, all listed on his [Merit author page](https://merit.systems/authors/sam-ragsdale) (official, high confidence). Farcaster @samrags, bio "Founder & CEO at @meritsystems", X linked ([Warpcast API](https://client.warpcast.com/v2/user-by-username?username=samrags)). Prior: former a16z investor who "helped design Jolt", a zero-knowledge VM ([SiliconANGLE](https://siliconangle.com/2025/01/16/merit-systems-raises-10m-create-new-economic-model-called-open-source-capitalism/)). Doxxed.
- **Ryan Sproule**, co-founder, "Founder and CTO". X @rsproule, GitHub rsproule, LinkedIn ryansproule ([author page](https://merit.systems/authors/ryan-sproule), official). Prior: Blockchain Capital, AWS. Doxxed.
- **Mason Hall**, "Engineering and Strategy". X @0xMasonH, GitHub fmhall, LinkedIn hallmason ([author page](https://merit.systems/authors/mason-hall), official). Prior: a16z crypto, bloXroute Labs, Consensys (as listed there). Doxxed.
- **Jason Hedman**, founding engineer. GitHub jasonhedman, bio "Founding Engineer @Merit-Systems"; X jsonhedman (self-declared). Top x402scan contributor (1,316 commits all time).
- Engineers by commits: shafu (GitHub shafu0x, X shafu0x self-declared; 718 x402scan commits, last 2026-07-21), "onchainlu" (X OnchainLu; 344 commits; bio says "prev Merit Systems"; last commit 2026-07-15), Ben Reilly (zdql, X zdql__; 936 Echo commits; last router commit 2026-05-25), Alvaro Echevarria Cuesta (alvaroechevarriacuesta; no X). Sources: [x402scan contributors](https://github.com/Merit-Systems/x402scan/graphs/contributors), [Echo contributors](https://github.com/Merit-Systems/echo/graphs/contributors).
- Contributors on x402scan in the window who are not on Merit's author pages: lgalabru (Solana payout indexing), nirholas. Joaquim Verges of thirdweb also has 9 commits to x402scan.

### Track record and pivots
- 2024-07-09: GitHub org created, "The financial stack for open-source software" (still its GitHub description) ([org](https://github.com/Merit-Systems)).
- 2025-01-01: manifesto "Open Source Capitalism". 2025-01-16: $10M seed ([blog index](https://www.merit.systems/blog)).
- 2025-05-05: Echo repo created (user-pays AI SDK). 2025-07-02: "the Terminal" for paying open-source contributors. 2025-09-04: Echo "micro-app" essay; Echo commits peak at 1,188 in Sep 2025 ([commits](https://github.com/Merit-Systems/echo/commits/main)).
- 2025-09-23: x402scan repo created. 2025-10-10: Echo x402 SDK package. 2025-11-03: "Emergence" essay; Echo falls to 71 commits in Nov, 4 in Dec 2025.
- 2026-01-17: `@x402scan/mcp` first publish; 2026-02-12: `agentcash` CLI first publish; 2026-02-14: router repo ([npm](https://registry.npmjs.org/agentcash)).
- 2026-03-27: "The Age of Open Agentic Commerce". 2026-07-01: first monthly "State of Agentic Commerce". 2026-07: claudelines, linq. 2026-08-25: OpenInstinct; homepage also lists Poncho and Theo (NYC guide over text).

### Trend-hopping score: 4
Every 3 to 5 months the pitch changed with the hot narrative (open-source funding, AI micro-apps, x402, MPP, personal agents) and each came with real, heavily committed code, so not a 5. The "product house" label admits it.

### Funding
$10M seed announced 2025-01-16, led by a16z crypto and Blockchain Capital ([SiliconANGLE](https://siliconangle.com/2025/01/16/merit-systems-raises-10m-create-new-economic-model-called-open-source-capitalism/)). Angels listed by [VCBacked](https://www.vcbacked.co/company/merit-systems): Dan Romero, Chad Byers, Packy McCormick. Confirmed against the lead. No later round and no x402 grant or sponsor found; x402scan appears to run on the seed (inference). A merged PR on 2026-07-21 adds a Discord alert at 95% of Bitquery usage, which implies a metered paid data plan behind x402scan ([PR list](https://github.com/Merit-Systems/x402scan/pulls?q=is%3Apr+is%3Amerged)).

### Product and traction
- [agentcash.dev](https://agentcash.dev): "over 1.4M paid tool calls by agents" (undated); docs say 3,200+ premium APIs ([docs](https://agentcash.dev/docs)); partners Minerva, Parallel, Nansen, Zerion.
- Merit's July 2026 report headline: "13.5 million x402 payments" for July 2026; method and period not explained ([report](https://www.merit.systems/blog/state-of-agentic-commerce-july-2026)).
- Echo site shows platform totals of $814.63 profit, 1.63M tokens and 1.69K transactions, period not stated ([echo.merit.systems](https://echo.merit.systems)).
- Stars: x402scan 397, Echo 547, OpenInstinct 438 in six weeks, router 31. npm downloads 2026-09-10 to 2026-10-09: `agentcash` 9,557; `@agentcash/router` 4,844; Echo SDK 854; `ai-x402` 315; `@x402scan/mcp` 89 ([npm API](https://api.npmjs.org/downloads/point/last-month/agentcash)).
- x402scan live stats: Gap (JS app).

### Last six months (2026-04-11 to 2026-10-11)
- 04-15 and 05-15: AgentCash partner posts (Minerva, Honcho). 06-15 to 07-20: router releases v1.10.6 to v1.20.0 (12 on the first page of releases). 07-01: first monthly report. 07-07, 07-13, 07-14: AgentCash launch and explainer posts. 07-15: router open-sourced; last post on the Merit blog. 07-28: last `agentcash` npm release (0.17.1).
- x402scan work: 07-14 deprecate inactive facilitator addresses; 07-23 agent-discovery metadata (`llms.txt`, API catalog); 08-11 adds three.ws Solana facilitator; 08-20 to 08-24 removes Ecosystem and Transactions pages, marketplace, the developer pages and the `@x402scan/mcp` package, and the ClickHouse database; 08-25 indexes `upto` and batch-settlement payouts on Solana (by lgalabru, who is not on Merit's author pages); 09-01 removes example servers; 09-16 last commit ([PRs #1087, #1089, #1096](https://github.com/Merit-Systems/x402scan/pull/1087)).
- Commits by month (April counted from 04-01): x402scan 63, 327, 143, 33, 53, 4 for Apr to Sep; agentcash-router 36, 162, 38, 84, 0, 0; OpenInstinct 319 (Aug), 131 (Sep), 47 (to 10-05) ([commits](https://github.com/Merit-Systems/x402scan/commits/main)).
- npm versions since 04-11: `agentcash` 143 (Apr 44, May 67, Jun 24, Jul 8); router 220 (Apr 28, May 103, Jun 45, Jul 44).
- Active x402scan committers in the last 26 weeks: onchainlu 276, claude 133, fmhall 106, shafu0x 28, sragss 12, rsproule 11, jasonhedman 7 ([stats](https://github.com/Merit-Systems/x402scan/graphs/contributors)). OpenInstinct: rsproule 126, jasonhedman 98, fmhall 65, sragss 28.
- Echo: 6 commits since April, all on 2026-06-26 (adding Claude model support); one SDK npm release (2026-06-27). The only Echo blog post on Merit's index is dated 2025-09-04.
- Departures: onchainlu self-describes as "prev Merit Systems". Joins: none announced.

### Pace verdict
Fast as a company, slow on x402. Hundreds of commits a month in May is far above the benchmark. But x402scan had 4 commits in September, the CLI and router have had no release for 10 to 12 weeks (last on 07-28 and 07-20), the promised August report did not appear on the blog index, and the founders' commits moved to OpenInstinct (497 commits in six weeks).

### Direction
Stated: "open agentic commerce" across x402 and MPP, monthly reports, Poncho/OpenInstinct/Theo as consumer agents ([llms.txt](https://merit.systems/llms.txt)). Shipping: August cuts to x402scan and a switch of founder time to an iMessage assistant. Inference: x402scan is being kept as a lean index, and the next product bets are consumer agents that pay with x402 or MPP, not more x402 infrastructure.

### Competitors
Explorers and registries: Coinbase's Bazaar and the ecosystem lists (platform layer, not researched here). Buyer wallets: Crossmint agent wallets, ampersend, Coinbase's own wallets. Seller libraries: thirdweb, the official `@x402/*` packages. Rival protocol: MPP (Merit hedges by indexing it). Ahead: Coinbase on discovery and distribution; Merit leads on public ecosystem data. Not verified: any Dune dashboards.

### Green and red flags
- Green: named, credible founders; confirmed institutional seed; the most complete public x402 explorer; very high shipping speed in H1 2026; public monthly data (started July); open-source code with 397 to 547 stars.
- Red: repeated pivots; Echo abandoned (6 commits since Nov 2025, off the homepage); x402scan feature cuts in August; AgentCash and router releases stopped in July; monthly report not continued; departures (onchainlu) and quiet engineers (zdql, shafu); no stated revenue model for AgentCash; GitHub org description and Farcaster bio are stale; third-party Echo numbers are tiny.

### Verdict
Serious builder; momentum Slowing (for x402). The team is real, funded and fast, which is why the drop in x402 output is meaningful: the team appears to have chosen to move on (inference from the commit record). x402scan will probably survive as the data source Merit's other products need, but expect fewer features and watch for another round of removals. AgentCash is worth tracking for call counts, not for fees. Follow weekly through GitHub, with a daily check only if you rely on x402scan data.

### Tracking card
- Sites: https://merit.systems ; https://www.x402scan.com ; https://mppscan.com ; https://agentcash.dev (docs /docs, blog /blog, discovery /discovery) ; https://poncho.merit.systems ; https://openinstinct.sh ; https://echo.merit.systems
- Blog: https://www.merit.systems/blog (no RSS found) ; llms.txt https://merit.systems/llms.txt ; agentcash blog https://agentcash.dev/blog
- GitHub org https://github.com/Merit-Systems ; repos `x402scan`, `agentcash-router`, `agentcash-skills`, `echo`, `OpenInstinct`, `awesome-agentic-commerce` (148 stars). Feed https://github.com/Merit-Systems/x402scan/commits/main.atom
- X: @merit_systems, @x402scan, @poncho_ai (listed on Sam Ragsdale's author page), @agentcashdev (linked from agentcash.dev). People: @samrags_, @rsproule, @0xMasonH (official), @jsonhedman, @zdql__, @shafu0x, @OnchainLu (self-declared on GitHub).
- LinkedIn: company https://www.linkedin.com/company/meritsystems/ ; people as above.
- Farcaster: @meritsystems (217 followers, X linked, stale bio), @samrags. The Farcaster account named "x402scan" is an empty placeholder (0 followers, no links); not official.
- Discord: https://discord.gg/merit (Echo README) ; x402scan Discord https://discord.gg/JuKt7tPnNc (x402scan README). Telegram: none found.
- x402scan identifiers: x402scan is an explorer, not a facilitator, so it has no facilitator id. Merit seller origins to look up: stableenrich.dev, agentupload.dev. Dune: none found.

### Sources (accessed 2026-10-11)
https://merit.systems ; https://merit.systems/llms.txt ; https://www.merit.systems/blog ; https://merit.systems/authors (and /sam-ragsdale, /ryan-sproule, /mason-hall) ; https://www.merit.systems/blog/state-of-agentic-commerce-july-2026 ; https://agentcash.dev ; https://agentcash.dev/docs ; https://agentcash.dev/blog ; https://echo.merit.systems ; https://siliconangle.com/2025/01/16/merit-systems-raises-10m-create-new-economic-model-called-open-source-capitalism/ ; https://www.vcbacked.co/company/merit-systems ; https://github.com/Merit-Systems (repos, commits, contributors, PRs #1087 #1089 #1096 via gh api) ; https://registry.npmjs.org/agentcash , /@agentcash%2Frouter , /@x402scan%2Fmcp , /@merit-systems%2Fai-x402 ; https://api.npmjs.org/downloads/point/last-month/ ; https://client.warpcast.com/v2/user-by-username?username=meritsystems , ?username=samrags , ?username=x402scan .

---

## 3. ampersend (Edge & Node)

### One-line
A control layer for AI-agent payments from Edge & Node, the team behind The Graph: budgets, spend policies, approvals, audit logs, compliance screening and a marketplace, built on x402, Google's A2A and MCP. Spelling note: "ampersend" with an "e"; the SDK repo carries a docs guard against "ampersand" ([commit 2026-06-11](https://github.com/edgeandnode/ampersend-sdk/commits/main)).

### x402 role
Buyer/agent-side controls plus trust/compliance. It sits between agents and x402 sellers: a Treasurer approves or blocks each payment against policy, and sellers can use it to validate inbound payments; screening comes from TRM Labs ([open beta post](https://ampersend.ai/blog/ampersend-is-now-in-open-beta), [docs](https://docs.ampersend.ai/)). The SDK supports buyer and seller roles in Python (A2A) and TypeScript (MCP) ([README](https://github.com/edgeandnode/ampersend-sdk)). Only the `exact` scheme works today; the deferred scheme is not supported ([docs](https://docs.ampersend.ai/)). Not a standalone facilitator: it is absent from x402scan's facilitator list.
**Core bet or side feature:** one of two lines on Edge & Node's homepage, next to its main blockchain-data product Amp ([edgeandnode.com](https://edgeandnode.com)). Money: free during the beta; "Pricing will be announced soon and there will be a free tier" ([FAQ](https://ampersend.ai/faq)). Marketplace fees are not described. Gap: no revenue model yet.

### Chains
Base primary. The open beta post names Base and USDC only ([post, 2026-04-01](https://ampersend.ai/blog/ampersend-is-now-in-open-beta)); the AWS co-written post says settlement is verified on Base in USDC ([AWS blog, 2026-06-22](https://aws.amazon.com/blogs/machine-learning/building-pay-per-intelligence-for-ai-agents-how-ampersend-uses-amazon-bedrock-agentcore-payments/)). Wallets are Safe smart accounts on a Coinbase CDP embedded wallet ([FAQ](https://ampersend.ai/faq)).

### Token
None announced; neither the FAQ nor the docs mention one. (Background, not verified here: The Graph has its own network token, unrelated to ampersend.)

### Team
- **Rodrigo Coelho**, CEO of Edge & Node. He demoed ampersend at an AI Engineer talk reported by StartupHub on "Sep 1" (page footer 2026) ([article](https://www.startuphub.ai/cybersecurity/agent-spending-without-controls-demo-shows-risk)); also named as CEO in the [2025-10-30 launch coverage](https://tech.yahoo.com/ai/deals/articles/graph-builders-edge-node-unveil-160033556.html). Handles not verified.
- **Pranav Maheshwari**, engineer who co-presented the same demo (StartupHub). His name is tied to the product by the demo-booking link on ampersend.ai (calendly.com/maheshwaripranav/ampersend-demo) ([site](https://ampersend.ai)). GitHub and X not verified (gap).
- **Kevin Jones**, Developer Relations at Edge & Node (author of the [Pinata article, 2026-04-08](https://edgeandnode.com/articles/build-x402-openclaw-agents-ampersend-pinata) and co-author of the AWS post). GitHub [kmjones1979](https://github.com/kmjones1979) (48 commits to `aws-agentcore-payments-ampersend`); X CryptoMastery_ (self-declared on GitHub).
- SDK engineers by commits ([contributors](https://github.com/edgeandnode/ampersend-sdk/graphs/contributors)): Pablo Carranza Velez (pcarranzav, 133 commits, X pcarranzav self-declared), "Matias" (matiasedgeandnode, 130), Chris Whited (cmwhited, GitHub company "Edge & Node", wrote the initial commit of `ampersend-core` on 2026-03-24), Maxwell Brown (IMax153, 12, X imax153 self-declared), Tomas Migone (tmigone, 3), and an independent contributor (samsamtrum, "Kaly Node") who also sent a fix to x402.rs.
- Blog and product voices: Doug Antin (wrote the open beta announcement; title not stated), Idalith Bustos, Noelle Becker Moreno, Marcus Rein ([blog](https://ampersend.ai/blog)). All named people are doxxed; no pseudonymous lead.

### Track record and pivots
- Edge & Node is the core development team behind The Graph; The Graph has served 1.8 trillion queries since 2018 ([StartupHub](https://www.startuphub.ai/cybersecurity/agent-spending-without-controls-demo-shows-risk), [Yahoo/CoinDesk](https://tech.yahoo.com/ai/deals/articles/graph-builders-edge-node-unveil-160033556.html)).
- 2025-10-21: ampersend-sdk repo created. 2025-10-30: ampersend announced with an X Spaces event; launch slated for Pragma Buenos Aires on 2025-11-20. 2025-11-25: first npm package. 2025-11-26: Amp (blockchain datasets) docs repo created, the company's other new line ([GitHub](https://github.com/edgeandnode)).
- 2026-02-24 and 02-25: pay-per-request articles. 2026-04-01: open beta. 2026-05-07 and 06-02: TRM Labs screening demo, then live. 2026-06-22: AWS AgentCore Payments post.
- Pattern: long-running blockchain-data company that added an agent-payments line in late 2025 and lists each trending partner or framework name (A2A, ERC-8004, OpenClaw, Hermes, CrewAI).

### Trend-hopping score: 3
The parent has a steady data focus (score 2 on its own), but ampersend is a new category entered when agents became the story and it name-checks each rising framework. It is a real, integrated product, so not higher.

### Funding
No separate funding found. Edge & Node's own funding history was not verified (VCBacked page returned 404; search quota gone). Gap.

### Product and traction
- Live: console (free) at app.ampersend.ai, docs, Python and TypeScript SDKs, a CLI and agent skill (`npx skills add edgeandnode/ampersend-sdk#skills/latest`), per-agent budgets, merchant allowlists, audit export, TRM Labs screening, a marketplace at app.ampersend.ai/discover (one blog post mentions "12+ APIs" in the catalog) ([blog index](https://ampersend.ai/blog)). The site still says "Now in Beta" ([ampersend.ai](https://ampersend.ai)).
- Partners and integrations: AWS (Bedrock AgentCore Payments, integration done "in under two weeks"), Pinata agent templates, CrewAI, LangChain, TRM Labs. No customers named; Chainlink and fiat on/off-ramp listed as "soon".
- Numbers: none published. `@ampersend_ai/ampersend-sdk` had 212 npm downloads from 2026-09-10 to 2026-10-09 ([npm API](https://api.npmjs.org/downloads/point/last-month/@ampersend_ai%2Fampersend-sdk)); the SDK repo has 24 stars. StartupHub calls x402 growth "still experimental", mostly OpenClaw retail tests.

### Last six months (2026-04-11 to 2026-10-11)
- 04-01 open beta; 04-08 Pinata templates; 04-29 CrewAI guide; 05-07 TRM Labs screening shown at Consensus Miami; 05-14 CLI post ("no keys, no accounts, no setup"); 06-02 TRM compliance live for enterprise; 06-17 "agent bought the Knicks a pizza with USDC"; 06-22 AWS post; 07-07 AWS follow-up; 07-17, 08-11, 08-20, 08-21 marketing posts; 09-01 AI Engineer demo ([blog](https://ampersend.ai/blog)).
- SDK commits by month: Apr 24, May 33, Jun 20, then none; last commit and last npm release 0.0.28 on 2026-06-23. Seven npm versions since 04-11 (Apr 1, May 2, Jun 4). Five PRs are open, the newest two from team members (07-10 and 07-17); outside issue comments arrived 09-11 and 09-26 to 09-27 ([PRs](https://github.com/edgeandnode/ampersend-sdk/pulls)).
- Satellite repos: `aws-agentcore-payments-ampersend` (36 commits Apr, 12 May, last 05-07), `ampersend-hermes` (9 Apr, 3 May), `ampersend-examples` (4 Apr).
- People: Kevin Jones visible from April; no departures found.

### Pace verdict
Good until 2026-06-23 (about 6 to 8 commits a week; 7 npm releases in about 11 weeks), then silent in public for 16 weeks while blog posts continued. Against the benchmark, the code side is stalled; the marketing side is not.

### Direction
Stated: "the control layer for the agent economy", compliance for enterprise buyers and sellers, fiat ramps and Chainlink soon, pricing soon ([site](https://ampersend.ai)). Shipped: the compliance and AWS pieces on schedule through June; none of the "soon" items visible by October. Inference: the product may be moving to private repos, or the team is thin; either way outsiders cannot see progress.

### Competitors
Crossmint (agent wallets with onchain spend caps, allowed counterparties and revocable signers, plus agent cards) is the closest direct rival and has more funding and licences. Merit's AgentCash is a simpler buyer wallet. Coinbase's own agent wallets and the official x402 packages set the baseline. Nevermined publishes comparison reviews of the field (an August 2026 review of Crossmint is listed at nevermined.ai/blog/crossmint-review; not opened). ampersend's own July post names Stripe, Robinhood, Mastercard and PayPal as the other rails it wants to oversee. Ahead of ampersend: Crossmint and the platform layer. Inference: ampersend's edge is the TRM screening and the AWS tie-in.

### Green and red flags
- Green: established, doxxed parent with a CEO who presents it; real integrations with AWS, TRM Labs and Coinbase CDP; Apache-2.0 SDK; steady content and a clear enterprise pitch; consistent Base + USDC choice.
- Red: tiny usage (212 monthly downloads); no named customers or numbers; SDK paused and PRs unmerged since July; open beta for six months with no pricing; second line behind Amp; several "soon" items; blog now mostly marketing.

### Verdict
Credible but small; momentum Slowing. It is a real product from a real company, but it has no visible users and its public engineering stopped in June. Edge & Node's main business is Amp (blockchain data), so ampersend's future depends on whether the company keeps funding a second line. Worth a weekly look at the blog and GitHub tags, not a daily one. Upgrade attention if pricing, a named customer or a new SDK release appears.

### Tracking card
- Site https://ampersend.ai ; docs https://docs.ampersend.ai/ ; console https://app.ampersend.ai/ ; marketplace https://app.ampersend.ai/discover ; blog https://ampersend.ai/blog (no RSS found) ; Edge & Node articles https://edgeandnode.com/articles
- GitHub org https://github.com/edgeandnode ; repos `ampersend-sdk` (tags `ts-v*`), `ampersend-examples`, `ampersend-hermes`, `aws-agentcore-payments-ampersend`, `ampersend-openclaw`. Feed https://github.com/edgeandnode/ampersend-sdk/tags.atom
- npm `@ampersend_ai/ampersend-sdk`.
- X: @ampersend_ai (linked from ampersend.ai), @edgeandnode (linked from edgeandnode.com). People: @pcarranzav, @imax153, @CryptoMastery_ (self-declared on GitHub). LinkedIn: https://www.linkedin.com/company/edgeandnode
- Farcaster: not found at @ampersend_ai or @edgeandnode (API errors). Gap.
- Telegram: https://t.me/+ycaSRKb2puIyNmQx (ampersend.ai). Discord: none listed.
- x402scan: not a listed facilitator; no server identifier found. Dune: none found.

### Sources (accessed 2026-10-11)
https://ampersend.ai ; https://ampersend.ai/blog ; https://ampersend.ai/faq ; https://ampersend.ai/blog/ampersend-is-now-in-open-beta ; https://docs.ampersend.ai/ ; https://edgeandnode.com ; https://edgeandnode.com/articles ; https://edgeandnode.com/articles/build-x402-openclaw-agents-ampersend-pinata ; https://edgeandnode.com/articles/pay-per-request-the-economic-model-that-unlocks-true-agent-autonomy ; https://tech.yahoo.com/ai/deals/articles/graph-builders-edge-node-unveil-160033556.html ; https://www.investingcube.com/cryptocurrency/industry-news/edge-node-launches-ampersend-a-platform-for-managing-agentic-ai/ ; https://www.startuphub.ai/cybersecurity/agent-spending-without-controls-demo-shows-risk ; https://aws.amazon.com/blogs/machine-learning/building-pay-per-intelligence-for-ai-agents-how-ampersend-uses-amazon-bedrock-agentcore-payments/ ; https://github.com/edgeandnode/ampersend-sdk (commits, contributors, PRs, events via gh api) ; https://registry.npmjs.org/@ampersend_ai%2Fampersend-sdk ; https://api.npmjs.org/downloads/point/last-month/ .

---

## 4. MCPay

### One-line
Open-source infrastructure for charging per call to MCP tools with x402 (registry, "monetizer" proxy, SDK, CLI). As of 2026-10-11 mcpay.tech redirects (HTTP 307) to Frames at frames.ag, the same builder's newer product. Dead as a brand.

### x402 role
Seller/resource-server proxy plus SDK and registry; a facilitator docs page exists ([docs](https://docs.mcpay.tech)) but there is no x402scan facilitator entry. **Core bet or side feature:** it was the whole product. Money: not stated; no revenue model found.

### Chains
Base in the examples; the README lists Base, Avalanche, IoTeX, Sei and Solana, with USDC and EUROe ([README](https://github.com/microchipgnu/MCPay)); the v2 page adds Polygon ([v2.mcpay.tech](https://v2.mcpay.tech)).

### Token
None found. The v2 FAQ has a token question but the answer was not visible in the fetch. Gap.

### Team
- **Luis Freitas**, GitHub [microchipgnu](https://github.com/microchipgnu) (391 of 477 commits). X microchipgnu is both self-declared on GitHub and linked on his Farcaster account @microchipgnu (bio "cto bitte.ai") ([Warpcast API](https://client.warpcast.com/v2/user-by-username?username=microchipgnu)): high confidence. Public GitHub orgs: Mintbase, BitteProtocol, aura-studios, 3xr-space; company field "@frames-engineering". Doxxed.
- **Marcelo Kunze**, GitHub marcelokunze (86 commits), X marcelokunze (self-declared), org Mintbase.

### Track record and pivots
Mintbase and BitteProtocol memberships (undated). MCPay: npm package 2025-05-16, repo 2025-05-30, "founded July 2025" per a directory listing ([Solana Compass](https://solanacompass.com/projects/mcpay)). Commits: Jul 2025 120, Aug 82, Sep 34, Oct 188, Nov 39, Dec 13, Jan 2026 1. frames-engineering org created 2026-01-07; its repos were last pushed on: `ows` 2026-03-25, `frame` 2026-05-02, `frames-monorepo` ("frame + pay + catalog") 2026-06-11 ([org](https://github.com/frames-engineering)); Frames F1 introduced 2026-07-01 ([frames.ag/blog](https://frames.ag/blog)). Solana Compass calls frames.ag "a successor product from the same creator".

### Trend-hopping score: 4
NFTs (Mintbase) to AI agents (Bitte) to MCP + x402 (MCPay) to data/model product (Frames) in a few years, with MCPay lasting about nine months of active work.

### Funding
None stated. The v2 page lists "backers" Colosseum, Coinbase, Polygon, vlayer and ETHGlobal without amounts, which looks like hackathon or sponsor recognition (inference, unconfirmed).

### Product and traction
The v2 page claims about 100,000 transactions, about $30,000 volume and about 2,500 users, undated and stale ([v2.mcpay.tech](https://v2.mcpay.tech)). npm `mcpay`: 315 downloads from 2026-09-10 to 2026-10-09; 90 GitHub stars.

### Last six months
Nothing: no commits after 2026-01-21, no npm release after 0.1.17 on 2025-12-02, no X or blog output found. Builder activity moved to Frames: blog posts 2026-07-01, 2026-08-11, 2026-10-07; frames.ag lists about 37,000 paid APIs and a free tier ([frames.ag](https://frames.ag/)).

### Pace verdict
Dead: no commits in almost nine months (last 2026-01-21), against a benchmark of weekly commits.

### Direction
Stated (v2 page): "Make your AIs more capable". Shipping record: the team left the product.

### Competitors
Other x402-for-MCP kits seen in listings: xmcp's x402 template and Civic Labs' x402-mcp (not researched); thirdweb and the official packages cover the same ground. Frames itself now competes with agent-payment catalogs such as AgentCash.

### Green and red flags
Green: shipped fast in 2025; open code. Red: brand redirected, no maintenance, stale usage claims, unclear sponsor claims.

### Verdict
Likely abandoned; momentum Dead. Do not follow MCPay. To follow the builder's next move, follow Luis Freitas and Frames, which is a different product (a paid-data model), not x402 infrastructure.

### Tracking card
Sites: mcpay.tech (redirect), https://v2.mcpay.tech, https://docs.mcpay.tech, https://frames.ag, https://frames.ag/blog. GitHub https://github.com/microchipgnu/MCPay ; https://github.com/frames-engineering. X: @mcpaytech (README), @microchipgnu. Telegram https://t.me/mcpay_tech. Farcaster @microchipgnu. x402scan: none. Dune: none found.

### Sources (accessed 2026-10-11)
https://github.com/microchipgnu/MCPay (gh api) ; https://mcpay.tech (redirect to https://frames.ag/) ; https://v2.mcpay.tech ; https://docs.mcpay.tech ; https://frames.ag/ ; https://frames.ag/blog ; https://solanacompass.com/projects/mcpay ; https://registry.npmjs.org/mcpay ; https://client.warpcast.com/v2/user-by-username?username=microchipgnu .

---

## 5. Mogami

### One-line
A Java stack for x402: client SDK, a Spring Boot server starter, a facilitator server (Docker image or hosted at facilitator.mogami.tech) and examples. The site says the company is "still in the early stages of building and exploring" x402 ([mogami.tech](https://mogami.tech)).

### x402 role
Facilitator plus SDK/tooling for Java. **Core bet or side feature:** the whole project. Money: no pricing stated; docs.x402.org lists it as a "free, developer-focused facilitator for Base with optional self-hosted Docker deployment" ([facilitator list](https://docs.x402.org/dev-tools/facilitators)).

### Chains
Base primary. The hosted facilitator's `/supported` lists `base` and `base-sepolia`, x402 version 1, scheme `exact`; the README says v1 and v2 are supported ([endpoint](https://facilitator.mogami.tech/supported), [README](https://github.com/mogami-tech/x402-facilitator)).

### Token
None mentioned on the site or in the repos.

### Team
- **Stephane Traumat**, GitHub [straumat](https://github.com/straumat): all 396 human commits to the facilitator repo (the only other contributor is Dependabot, 116 commits) ([contributors](https://github.com/mogami-tech/x402-facilitator/graphs/contributors)). Profile: company "Oak Invest", blog angara.finance, bio "Tech Entrepreneur, Developer & Investor"; X straumat (self-declared on GitHub). Mogami's site and org list no people, so "lead developer" is solid and "founder" is unconfirmed. Farcaster not checked.

### Track record and pivots
- Cassandre: Java crypto trading-bot framework; org created 2020-02-11; flagship repo 661 stars, last push 2025-03-01 ([org](https://github.com/cassandre-tech)). Royllo: Bitcoin Taproot Assets explorer; org created 2022-08-26 ([org](https://github.com/royllo)). Mogami: org created 2025-05-11 ([org](https://github.com/mogami-tech)); first x402scan facilitator transaction 2025-10-24; website V2 2026-01-12.
- Pattern: one developer, one open-source Java crypto project at a time.

### Trend-hopping score: 3
Trading bots, then Bitcoin assets, then x402. Real, documented products each time; a consistent Java/open-source angle.

### Funding
No evidence of outside funding.

### Product and traction
Five small repos (stars: Spring starter 11, facilitator 7, examples 5, client 3, commons 2). Playground at playground.mogami.tech. Base address `0xfe0920a0a7f0f8a1ec689146c30c3bbef439bf8a` (x402scan "mogami") had sent 25,950 transactions by 2026-10-11: +71 in 14 days, +2,277 in 30 days, +4,755 in 90 days, +5,408 in 180 days (from the [Base RPC](https://mainnet.base.org)). Most of the 30-day gain came in the 30-to-14-day window, so use is bursty. The site gives no usage numbers.

### Last six months
Facilitator commits: Apr 40, May 10, none after. Spring starter: Apr 19, May 2. Client: Apr 7, May 2. Commons: Apr 46, May 25. Examples: Apr 11, May 2 ([commit pages](https://github.com/mogami-tech)). Last human commit 2026-05-13 (x402-commons, "add 'exact' payment scheme documentation"); last activity 2026-05-22 (Dependabot merges). No releases found. No joins or departures. The hosted facilitator still answers (checked 2026-10-11).

### Pace verdict
Stalled. Nearly five months without feature work, against a benchmark of weekly commits.

### Direction
Stated: SDKs and a facilitator "from zero to production in minutes" ([org description](https://github.com/mogami-tech)). Shipped: SDK and docs work through May (the facilitator README says v1 and v2 are supported), then nothing.

### Competitors
The official repo ships its own Java SDK (a `java/` folder next to Go, Python and TypeScript) ([repo](https://github.com/x402-foundation/x402)); free facilitators from Dexter, PayAI, Corbits and others are listed beside it ([facilitator list](https://docs.x402.org/dev-tools/facilitators)). Ahead: the official SDKs.

### Green and red flags
- Green: working Base mainnet facilitator; self-hostable; Java niche; named developer with a visible history; v1 and v2.
- Red: single developer; no commits since May; tiny usage (26k transactions in total); no funding, no news, no named company team.

### Verdict
Credible but small; momentum Stalled. A competent solo project that found a niche (Java shops) and then stopped. The hosted facilitator still runs, but nothing new is being built, and the official Java SDK removes the reason to wait for it. Do not follow daily. Re-check in December: if there are still no commits, treat it as abandoned.

### Tracking card
Site https://mogami.tech ; docs https://mogami.gitbook.io/mogami ; playground https://playground.mogami.tech ; hosted facilitator https://facilitator.mogami.tech ; GitHub https://github.com/mogami-tech (`x402-facilitator`, `x402-spring-boot-starter`, `x402-java-client`, `x402-commons`, `x402-examples`). X: @mogami_tech (site and README). Person: @straumat. Discord/Telegram: none. x402scan: facilitator id `mogami`, url https://facilitator.mogami.tech/, Base address above. Dune: none found.

### Sources (accessed 2026-10-11)
https://mogami.tech ; https://mogami.gitbook.io/mogami ; https://facilitator.mogami.tech/supported ; https://github.com/mogami-tech (gh api) ; https://github.com/straumat ; https://github.com/cassandre-tech ; https://github.com/royllo ; https://docs.x402.org/dev-tools/facilitators ; https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/mogami.ts ; https://mainnet.base.org .

---

## 6. x402.rs

### One-line
An open-source Rust toolkit for x402: protocol types, Axum server middleware, reqwest client middleware, a local facilitator and chain crates for EVM, Solana, Aptos and Tron, plus a free testnet facilitator at facilitator.x402.rs ([x402.rs](https://x402.rs), [README](https://github.com/x402-rs/x402-rs)). Its commercial arm is FareSide.

### x402 role
SDK/tooling and facilitator (self-hosted binary and Docker image on GHCR). The site calls x402-rs "the foundation of FareSide, a hosted x402 facilitator service". **Core bet or side feature:** the project's whole focus. Money: FareSide hosted service; its site would not load (socket closed on two attempts), so pricing is a Gap.

### Chains
Not Base-primary; multi-chain. EVM (Base among them), Solana, Aptos (git-only) and Tron (added 2026-06-18). The free public facilitator is "a free testnet facilitator" (Base Sepolia, Arbitrum Sepolia, Polygon Amoy, Ethereum Sepolia, Solana Devnet, Monad and Sei testnets) ([x402.rs](https://x402.rs)); Base mainnet needs self-hosting or FareSide.

### Token
None mentioned.

### Team
- **Sergey Ukustov**, GitHub [ukstv](https://github.com/ukstv): 925 of about 960 commits ([contributors](https://github.com/x402-rs/x402-rs/graphs/contributors)). X ukstv (self-declared on GitHub). Farcaster @ukstv exists with bio "Doing stuff in Web3" but no linked account, so it is a username match only (low confidence). Public GitHub orgs: machinomy, OnderPlatform. The FareSide org (created 2025-10-21) has four repos, all committed by him, which ties FareSide to x402-rs ([org](https://github.com/fareside)). Doxxed by name.
- Occasional contributors: samsamtrum ("Kaly Node", also sent a fix to ampersend-sdk), TJ-Frederick, melonask, jtang17 (7 commits), adamdossa (6 commits; GitHub bio "SVP Engineering @ Polygon Labs").

### Track record and pivots
- Machinomy: "Micropayments for the Web of Everything", org created 2016-04-08 ([org](https://github.com/machinomy)); ØNDER, a "digital energy" platform (org 2018-07-24). x402-rs: repo created 2025-05-08, v0.1.0 the same day; v1.0.0 2026-02-04; v1.3.0 2026-02-15; v2.0.0 2026-06-16.
- FareSide repos: `bench-worker-fly` "Measuring x402 facilitators" (2026-01-28), `outgate` "Programmable action boundary for AI agents" (2026-04-18), `tron-x402-js` (2026-06-22).
- His 2026 side repos include `distilled`, `gondolin` and a KuzuDB fork, so attention is spread ([profile repos](https://github.com/ukstv?tab=repositories)).

### Trend-hopping score: 2
A micropayments developer since 2016 for whom x402 is a natural extension. The 2026 side projects show the usual agent-era drift, but the x402 work is steady and technical.

### Funding
No evidence of outside funding, sponsors or grants (README and site name none).

### Product and traction
- 291 stars, 176 forks, Apache-2.0. crates.io downloads (total / last 90 days): `x402-types` 64,139 / 38,206; `x402-chain-eip155` 55,617 / 34,991; `x402-axum` 43,378 / 10,898; `x402-facilitator-local` 32,009 / 23,852; `x402-reqwest` 8,528 / 2,593 ([crates.io API](https://crates.io/api/v1/crates/x402-types)).
- Base mainnet: the four x402scan "x402rs" addresses still marked active (`0x97d38aa5...`, `0x0168f80e...`, `0x5e437bee...`, `0xc19829b3...`) have sent 798,595 transactions in total, 4,336 in the last 180 days and none in the last 30 days (Base RPC). The facilitator's mainnet use looks dormant.
- Demand: 44 issues and PRs opened since 2026-04-11, 18 of them in September, 5 in October ([GitHub search](https://github.com/x402-rs/x402-rs/issues)).

### Last six months
- Commits by month: Apr 6, May 24, Jun 87, Jul 8, none after 2026-07-13. Releases on GitHub stop at v1.3.0 (2026-02-15), but crates went to 2.0.0 (06-16), 2.0.1 (06-19) and 2.0.2 (07-12), with 11 to 14 crate versions each since 04-11.
- Features: Rust client for the EIP-155 `upto` flow (06-10), TRON facilitation (06-18, tron crate 0.2.2 on 07-13), telemetry tracing (07-12).
- Contributors in the window: ukstv 117 commits, three others 1 each. An outside PR (GigaHierz, 2026-10-06, adding an ERC-8021 attribution tag) and issues filed 10-02 to 10-08 remain open ([issues](https://github.com/x402-rs/x402-rs/issues)).

### Pace verdict
Strong but solo: a big v2 push in June, then 90 days of nothing. Against a weekly-commit benchmark it is stalled; against what one person normally does it was a good quarter.

### Direction
Stated: a modular, production-ready toolkit for V1 and V2 across many chains, and FareSide as the hosted product. Shipped: v2 and Tron through mid-July, then a stop. No roadmap file found.

### Competitors
Official x402 SDKs (TypeScript, Python, Go, Java; no Rust listed in the repo's top-level folders) ([repo](https://github.com/x402-foundation/x402)); hosted facilitators from Coinbase, PayAI, Corbits, Dexter, Fireblocks and others ([list](https://docs.x402.org/dev-tools/facilitators)). x402.rs has little direct competition for Rust but also a small audience. Ahead: Coinbase and PayAI on hosted use.

### Green and red flags
- Green: the most complete Rust implementation; real downloads (about 38k in 90 days for the core crate); v2; multi-chain; permissive license; the author benchmarks facilitators.
- Red: single maintainer; no commits since 07-13; free hosted facilitator is testnet only; mainnet addresses dormant; FareSide status unknown (site would not load); open outside PRs and issues.

### Verdict
Credible but small; momentum Stalled. The library is good and in use, and the author knows micropayments. But all of the work depends on one person whose recent commits go to other repos, and the hosted business (FareSide) shows no visible traction. Expect it to be useful for Rust builders and not a source of x402 news. Follow only if you cover Rust or want to track facilitator benchmarks. Revisit if v2.1 or a FareSide launch appears.

### Tracking card
Site https://x402.rs ; GitHub https://github.com/x402-rs/x402-rs (also https://github.com/fareside) ; crates `x402-types`, `x402-axum`, `x402-reqwest`, `x402-facilitator-local`, `x402-chain-eip155`, `x402-chain-solana`, `x402-chain-tron` ; image ghcr.io/x402-rs/x402-facilitator. Feed https://github.com/x402-rs/x402-rs/releases.atom (stale since Feb). X: @x402rs (site), @ukstv (self-declared). Telegram https://t.me/faresidehq. Farcaster @ukstv (low confidence). Discord none. x402scan: facilitator id `x402rs`, url https://facilitator.x402.rs , four active Base addresses above plus deprecated ones. Dune: none found.

### Sources (accessed 2026-10-11)
https://x402.rs ; https://github.com/x402-rs/x402-rs (gh api: commits, releases, contributors, issues) ; https://github.com/fareside ; https://github.com/ukstv ; https://github.com/machinomy ; https://crates.io/api/v1/crates/x402-types (and x402-axum, x402-reqwest, x402-facilitator-local, x402-chain-eip155) ; https://client.warpcast.com/v2/user-by-username?username=ukstv ; https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/x402rs.ts ; https://mainnet.base.org . https://fareside.com failed to load on 2026-10-11.

---

## 7. OpenX402

### One-line
"The first permissionless x402 facilitator that any AI or developer can use to build x402 servers, without a login" ([openx402.ai](https://openx402.ai)).

### x402 role
Facilitator. Verification and settlement are free; the docs list "No sign up" (no accounts, API keys or KYC) ([docs](https://docs.openx402.ai)). **Core bet or side feature:** it is the whole project. Money: none stated.

### Chains
Base is included. Mainnet: Base (`eip155:8453`), Monad (`eip155:143`) and Solana, with Base Sepolia for tests; x402 v2 with the `discovery` extension, v1 backward compatibility ([supported endpoint](https://facilitator.openx402.ai/supported), [docs](https://docs.openx402.ai)). Base is the only chain I could measure on-chain.

### Token
Gap and a flag. The docs say PayTo wallet addresses "can register via the Open token for whitelisting"; no token name, chain or contract is given, and the register page does not mention one ([docs](https://docs.openx402.ai), [register](https://openx402.ai/register)). If this means a tradable token, OpenX402 belongs with the token-bearing facilitators. Unconfirmed.

### Team
None named. The docs and site list no people. GitHub org [openx402](https://github.com/openx402) was created 2025-10-26, has no public repositories, and links to openx402.ai; X handle @openx402 comes from the org's `twitter_username` and the site ([site footer](https://openx402.ai)). Anonymous; no real-world identity sought.

### Track record and pivots
No earlier history found. First facilitator transaction on x402scan: 2025-10-16 ([config](https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/openx402.ts)).

### Trend-hopping score: 4 (low confidence)
An anonymous operator launched a "first permissionless facilitator" in October 2025 (first x402scan transaction 2025-10-16; GitHub org created 2025-10-26) with no visible prior record. It runs a real service, so I did not score 5.

### Funding
No evidence of outside funding.

### Product and traction
Base address `0x97316fa4730bc7d3b295234f8e4d04a0a4c093e8` (x402scan "openx402", first transaction 2025-10-16) had sent 438,688 transactions by 2026-10-11, the highest of any single facilitator address checked (the four active x402.rs addresses together have sent 798,595). Gains: +1,280 in the last 14 days, +1,732 in 30, +2,277 in 90, +2,982 in 180 (Base RPC). The site's scanner shows transactions, volume, payers and registered servers, but the numbers did not load. Solana signer `5xvht4fYDs99yprfm4UeuHSLxMBRpotfBtUCQqM3oDNG`.

### Last six months
No public record. No repository, changelog or dated posts found (the "updates" page returned 404). On-chain activity continues, and picked up in the last two weeks.

### Pace verdict
Cannot be measured. There is nothing public to count, which is itself a weakness for a project calling itself open.

### Direction
Stated: free, permissionless, multi-chain, v2. No roadmap. Inconsistency: the Architecture page says receiver addresses "must be registered with the facilitator" and "only registered receivers can accept payments" ([architecture](https://docs.openx402.ai/architecture)), which is a whitelist, not a permissionless flow.

### Competitors
Other free facilitators: Mogami, Dexter, PayAI, Corbits, Built on Stellar and the testnet-only x402.org facilitator ([list](https://docs.x402.org/dev-tools/facilitators)); OpenX402 is not on that list. Ahead: Coinbase CDP and PayAI by reach; unknown by usage.

### Green and red flags
- Green: live service; v2 and discovery; three mainnet chains; steady on-chain use; free.
- Red: anonymous team; the GitHub repo linked from the docs (`openx402/openx402`) returns 404; no changelog; x402scan still points to `open.x402.host`, which serves a mismatched Railway TLS certificate; "Open token" unexplained; "permissionless" claim conflicts with its own registration rule.

### Verdict
Speculative; momentum Steady on-chain, unverifiable otherwise. It processes real transactions on Base, but nobody can inspect the code or name the operator, and the token reference needs an answer. Follow only if you wants to track free facilitator use, and treat claims as unaudited. Hand the token question to the researcher covering token-bearing facilitators.

### Tracking card
Site https://openx402.ai ; docs https://docs.openx402.ai ; facilitator https://facilitator.openx402.ai ; GitHub org https://github.com/openx402 (empty). X: https://x.com/openx402. Farcaster, Discord, Telegram: none found. x402scan: facilitator id `openx402`, url in config https://open.x402.host (stale), Base `0x97316fa4...c093e8` (a second Base address is marked deprecated), Solana `5xvht4fY...`. Dune: none found.

### Sources (accessed 2026-10-11)
https://openx402.ai ; https://openx402.ai/register ; https://docs.openx402.ai ; https://docs.openx402.ai/architecture ; https://docs.openx402.ai/quick-start ; https://facilitator.openx402.ai/supported ; https://github.com/openx402 (gh api) ; https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/openx402.ts ; https://docs.x402.org/dev-tools/facilitators ; https://mainnet.base.org . https://open.x402.host failed TLS validation (certificate for *.up.railway.app).

---

## 8. Crossmint

### One-line
A wallet, stablecoin and checkout infrastructure company. Its agent line, "Crossmint Agents", has three parts: agent cards (scoped Visa and Mastercard credentials), non-custodial agent wallets that can pay x402 and MPP endpoints, and agent checkouts that buy from online stores. It also makes lobster.cash, a payment tool for coding agents ([Agents overview](https://docs.crossmint.com/agents/overview.md), [lobster.cash](https://www.lobster.cash)).

### x402 role
Buyer/agent client. The x402 page covers one flow: an agent pays x402-protected endpoints from a Crossmint wallet, using `@x402/core` and `@x402/evm` with Base USDC; the seller side is not covered ([x402 docs](https://docs.crossmint.com/agents/payment-flows/x402.md)). A seller-side n8n "Checkout Trigger Node (x402 Paywall)" is listed in the docs index ([llms.txt](https://docs.crossmint.com/llms.txt)). Crossmint does not run a facilitator: its own explainer uses Coinbase as the facilitator and says any firm listed on x402scan can fill that role ([article, 2026-08-28](https://www.crossmint.com/learn/inside-an-x402-transaction)).
**Core bet or side feature:** side feature. The overview says cards and wallets provide spending power, and "checkouts, x402, MPP, and onchain actions" are where it is spent ([overview](https://docs.crossmint.com/agents/overview.md)). The same explainer does not list Crossmint among the 40 x402 Foundation members it names. Money: no x402 fee found. Agent Checkouts cost $0.05 per execution ([announcement, 2026-09-25](https://www.crossmint.com/announcement/agent-checkouts)); other revenue is platform and card-related and not itemised in the pages read.

### Chains
Chain-agnostic company (40+ chains claimed in March 2025 ([The Block](https://www.theblock.co/post/346863/ribbit-capital-leads-23-6-million-funding-round-for-enterprise-blockchain-platform-crossmint))). For x402, the docs example is Base USDC; lobster.cash says USDC on Solana "works with protocols like x402". Base is the example, not a focus.

### Token
None. Gap: not searched beyond site and docs.

### Team
- **Rodri Fernandez**, co-founder ([The Block](https://www.theblock.co/post/346863/ribbit-capital-leads-23-6-million-funding-round-for-enterprise-blockchain-platform-crossmint), [CrowdfundInsider](https://www.crowdfundinsider.com/2025/03/237668-ribbit-capital-leads-23-6m-crossmint-funding-round/)); quoted as "Rodri" in the licence announcement (title not stated). **Alfonso Gomez-Jordana Manas**, co-founder, quoted in the toolkit launch. **Alex Rawitz**, Head of Agentic Payments, quoted in the same post ([2026-10-08](https://www.crossmint.com/announcement/agent-commerce-toolkit-launch)). **Miguel Zapatero**, General Counsel ([2026-07-03](https://www.crossmint.com/announcement/psd2-mica)). All doxxed; X handles not verified for any of them.
- Engineers tied to the agent and x402 work by commits: "aigustin" (Agus; m2m payments sample app, 2026-10-06), "xmint-guille" (lobstercash skills, 2026-05-11); handles only, no profile detail. SDK core committers include jmderby (GitHub "Eng @Crossmint") and devlyn37 (company Crossmint, X Devlyn_3 self-declared) ([contributors](https://github.com/Crossmint/crossmint-sdk/graphs/contributors)).

### Track record and pivots
- 2021-11-17: `crossmint-sdk` repo created; org created 2021-11-26 ([GitHub](https://github.com/Crossmint)). Early NFT-checkout history is not confirmed in the sources I could read.
- 2025-01-21: `agent-launchpad-starter-kit` (AI agent launch kit). 2025-03-18: $23.6M round; 40,000 users; GOAT SDK (open-source library for AI agents) with 150,000 downloads in two months ([CrowdfundInsider, 2025-03-24](https://www.crowdfundinsider.com/2025/03/237668-ribbit-capital-leads-23-6m-crossmint-funding-round/)). 2025-09-10: `crossmint-agentic-finance` repo.
- 2026-03-23: `lobstercash-cli-skills` repo (lobster.cash). 2026-07-03: MiCA crypto-asset service provider and PSD2 payment institution authorisations in Spain (CNMV and Bank of Spain). 2026-08-28: x402 explainer. 2026-09-25: Agent Checkouts. 2026-10-06: m2m-payments-sample-app. 2026-10-08: Agent Commerce Toolkit.

### Trend-hopping score: 3
From wallets and checkout, to an AI-agent launch kit and GOAT in the 2025 agent wave, to stablecoin licences, to agent cards in 2026. Real, funded product at each step around the same core (wallets and payments APIs).

### Funding
$23.6M round announced 2025-03-18, led by Ribbit Capital, with Franklin Templeton, Nyca, First Round, Lightspeed Faction and HF0 ([The Block](https://www.theblock.co/post/346863/ribbit-capital-leads-23-6-million-funding-round-for-enterprise-blockchain-platform-crossmint)). [VCBacked](https://www.vcbacked.co/company/crossmint) lists $23.6M total raised; a jobs aggregator lists $41.7M (secondary, unreconciled). No 2026 round found; search quota limits that check. Gap.

### Product and traction
- npm `@crossmint/wallets-sdk`: 172,720 downloads from 2026-09-10 to 2026-10-09 (compare thirdweb 206,368 and `@x402/core` 1,492,519). Repos: `crossmint-sdk` 52 stars; `agent-commerce-sample-app` 10.
- No x402 volume, customer or usage numbers published. Named partners in agent materials: Visa Intelligent Commerce, Mastercard Agent Pay, Stytch, Circle, Basis Theory, Solana (on lobster.cash); no customers named in the toolkit post.
- Regulatory status is a differentiator: MiCA and PSD2 authorisations (2026-07-03) and Canadian registrations.

### Last six months (2026-04-11 to 2026-10-11)
- 04-20 `openai-agents-sdk-virtual-cards`; 05-11 lobstercash skills doc update; 06-08 agent-checkout quickstart repo; 07-03 licences; 07-10 agent-checkouts-skill; 08-28 x402 explainer; 09-25 Agent Checkouts launch; 10-06 `m2m-payments-sample-app` ("agent wallets, onramp without KYC, x402 and MPP"); 10-08 Agent Commerce Toolkit ([org repos](https://github.com/Crossmint)).
- `crossmint-sdk`: 215 commits in 26 weeks (about 2 to 21 a week, 14 in the week of 10-04); by month, grouped by GitHub week: Apr 9 (from 04-19), May 46, Jun 47, Jul 22, Aug 27, Sep 50, Oct 14 (to 10-10); last push 2026-10-10 ([commit activity](https://github.com/Crossmint/crossmint-sdk/graphs/commit-activity)). `@crossmint/wallets-sdk` npm versions since 04-11: 36 (Apr 9, May 3, Jun 10, Jul 3, Aug 4, Sep 5, Oct 2), latest 1.20.0 on 2026-10-06.
- x402-specific: only two commits in the whole org mention x402 since 04-11 (2026-05-11, 2026-10-06) ([commit search](https://github.com/search?q=org%3ACrossmint+x402&type=commits)).
- Joins and departures: none found.

### Pace verdict
Fast for the company (weekly commits, releases at least monthly), thin for x402. Better than the benchmark overall; the x402 page is a few lines of docs.

### Direction
Stated: agent cards, wallets and checkouts, protocol-agnostic (x402, MPP, Shop Pay, UCP). Shipped: that same list, on a steady cadence. x402 stays a payment destination, not a product.

### Competitors
For agent payments: Coinbase wallets and the x402 packages (platform layer), ampersend, Merit's AgentCash, Nevermined (publishes a Crossmint review, August 2026), and card-network programs. For x402 specifically Crossmint is not a contender as infrastructure; it is a customer-side wallet. Ahead of it on x402: Coinbase, PayAI, thirdweb's facilitator, and the official packages.

### Green and red flags
- Green: $23.6M from a top fintech investor; EU licences; steady releases; open-source samples; docs that match the official x402 packages.
- Red: x402 is a minor feature; buyer side only; no facilitator; no x402 numbers; not an x402 Foundation member per its own article; lobster.cash is Solana-first; frequent narrative shifts; funding totals conflict between aggregators.

### Verdict
Serious builder (company); x402 is a side feature; momentum Accelerating for the company, Steady and minor for x402. Crossmint treats x402 as one rail its agent wallets can pay, which fits how most real companies will use it. Follow it for where agent payments (cards, checkouts, licences) are heading, not for x402 news. A weekly look at its announcements page is enough.

### Tracking card
- Site https://www.crossmint.com ; docs https://docs.crossmint.com (index https://docs.crossmint.com/llms.txt) ; x402 page https://docs.crossmint.com/agents/payment-flows/x402 ; announcements https://www.crossmint.com/resources (no RSS found) ; lobster.cash https://www.lobster.cash
- GitHub org https://github.com/Crossmint ; repos `crossmint-sdk`, `agent-commerce-sample-app`, `m2m-payments-sample-app`, `lobstercash-cli-skills`, `agent-checkout-quickstart`. Feed https://github.com/Crossmint/crossmint-sdk/commits/main.atom
- X: @crossmint (GitHub org `twitter_username`). People: handles not verified.
- Farcaster: @crossmint (670 followers; bio matches the company; no linked X, medium confidence) ([Warpcast API](https://client.warpcast.com/v2/user-by-username?username=crossmint)).
- Telegram: a lobster.cash group is linked on lobster.cash (URL not captured); Discord not found.
- x402scan: not a listed facilitator; no server identifier found. Dune: none found.

### Sources (accessed 2026-10-11)
https://docs.crossmint.com/llms.txt ; https://docs.crossmint.com/agents/overview.md ; https://docs.crossmint.com/agents/payment-flows/x402.md ; https://docs.crossmint.com/agents/how-agents-pay.md ; https://www.crossmint.com/resources ; https://www.crossmint.com/learn/inside-an-x402-transaction ; https://www.crossmint.com/announcement/agent-commerce-toolkit-launch ; https://www.crossmint.com/announcement/agent-checkouts ; https://www.crossmint.com/announcement/psd2-mica ; https://www.lobster.cash ; https://www.theblock.co/post/346863/ribbit-capital-leads-23-6-million-funding-round-for-enterprise-blockchain-platform-crossmint ; https://www.crowdfundinsider.com/2025/03/237668-ribbit-capital-leads-23-6m-crossmint-funding-round/ ; https://www.vcbacked.co/company/crossmint ; https://github.com/Crossmint (gh api) ; https://registry.npmjs.org/@crossmint%2Fwallets-sdk ; https://api.npmjs.org/downloads/point/last-month/@crossmint%2Fwallets-sdk ; https://client.warpcast.com/v2/user-by-username?username=crossmint .

---

## Comparison table

Ranking, from most to least worth following: Merit Systems (best public x402 data, but x402 output is slowing), Crossmint (best-funded, x402 minor), ampersend, thirdweb, x402.rs, OpenX402, Mogami, MCPay. Seriousness labels follow the scale in the brief; momentum is for the x402 work specifically.

| Project | x402 role | Seriousness | Momentum | Trend-hopping (1-5) | Follow? |
|---|---|---|---|---|---|
| thirdweb (x402 line) | Facilitator + SDK | Credible but small (company is a serious builder) | Slowing, near Stalled | 3 | Monthly, via GitHub releases |
| Merit Systems (x402scan, AgentCash, Echo) | Discovery/analytics, buyer wallet, seller tooling | Serious builder | Slowing (x402 work) | 4 | Weekly; daily only if you quote x402scan data |
| ampersend (Edge & Node) | Agent spend control, compliance, marketplace | Credible but small | Slowing | 3 | Weekly (blog and GitHub tags) |
| MCPay | Seller proxy and registry (now Frames) | Likely abandoned | Dead | 4 | No |
| Mogami | Facilitator + Java SDK | Credible but small | Stalled | 3 | No; recheck in December |
| x402.rs | Rust SDK + facilitator (FareSide hosted) | Credible but small | Stalled | 2 | Only if you cover Rust |
| OpenX402 | Free facilitator (Base, Solana, Monad) | Speculative | Steady on-chain, unverifiable | 4 (low confidence) | Only to track free-facilitator use |
| Crossmint | Buyer-side agent wallets | Serious builder (x402 is a side feature) | Accelerating (company); steady and minor for x402 | 3 | Weekly for agent payments, not for x402 news |
