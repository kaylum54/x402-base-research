# x402 on Base: due diligence on agent apps and platforms (Questflow, Bankr, Olas, screened and discovered projects)

Prepared 2026-10-11. "Window" means 2026-04-11 to 2026-10-11. All pages and APIs were accessed on 2026-10-11 unless a different date is shown. No price or chart analysis is included; token facts only. Anything I could not confirm is labelled "unconfirmed". Method and limits are in the section "Method, limits and gaps" near the end (important: web search was cut off partway through, so discovery relied on direct fetches of official sites, GitHub, npm, x402scan and the x402 ecosystem data file).

Bottom line for a daily watchlist: Olas first (deepest engineering; x402 work restarted hard in September-October 2026), Bankr second (the only priced x402 product among the three leads, but no usage numbers), BlockRun and FluxA as the x402-native names found in discovery, Zora as a one-off mention, and Questflow dropped (facilitator traffic collapsed after February 2026 and the company now sells a finance agent).

How to read the profiles: each full profile uses the headings you asked for. Numbers from GitHub come from the GitHub REST API (commit counts are "since 2026-04-01" unless stated, so April includes ten days before the window). Numbers from x402scan come from its public tRPC API (`https://www.x402scan.com/api/trpc/...`), where amounts are USDC and "tx" is settled transfers it indexed.

---

## Answers to the key questions

### Q1. Questflow: token, VC backing, what is live?

#### Takeaway
Questflow has VC backing but no confirmed token, and it was a real x402 facilitator operator for about three months before pivoting. Its Base facilitator went live 2025-10-29, peaked at 272,169 settled transfers in November 2025, fell to 32 in February 2026 and has been under 200 a month since; the facilitator hostname now redirects to the homepage. The company now sells an AI finance agent (Polymarket and Hyperliquid trading, "Financial Intelligence for All"), not an x402 product.

Lead check: confirmed that Questflow announced a facilitator and an agent-economy story in late 2025; out of date because the company pivoted in February 2026 and the facilitator is dormant.

#### Cited findings
- $6.5M seed announced 2025-07-22, led by CyberFund, with Delphi Labs, Systemic Ventures, Eden Block, White Star Capital, Web3.com, Animoca Brands, HashKey Capital, Wagmi Ventures, ElizaOS, Tezos Foundation and CatcherVC; grants from Aptos, Coinbase Developer Platform and Virtuals Protocol — [The Block press release](https://www.theblock.co/amp/post/363633/questflow-secures-6-5m-seed-round-to-build-ai-agent-economy-for-every-workflow).
- Earlier $1.5M angel round announced 2024-07-08, led by MiraclePlus — [Questflow blog](https://blog.questflow.ai/p/questflow-labs-secures-angel-funding).
- Token: a 2024-06-25 "community incentive plan" described a 1B-supply token (85% Guardian Nodes, 10% DAO treasury, 5% apps), points in Q3 and a TGE in Q4 (year implied 2024) — [Questflow blog](https://blog.questflow.ai/p/questflow-community-incentive-plan). I found no evidence that a TGE happened: CoinGecko has no page at `/en/coins/questflow` (HTTP 404), and neither the 2025 press release nor the 2025 year-in-review names a token — [CoinGecko probe](https://www.coingecko.com/en/coins/questflow), [2025 review](https://blog.questflow.ai/p/questflow-2025-from-belief-to-system). An affiliate site claims a "confirmed native token" with 1B supply but cites no official announcement — [airdropalert](https://airdropalert.com/airdrops/questflow-ai/) (low reliability).
- Facilitator: announced 2025-10-29 ("Questflow Facilitator for x402 goes live") — [blog](https://blog.questflow.ai/p/questflow-facilitator-for-x402-goes). x402scan shows 10 Base addresses, first transaction 2025-10-29 — [x402scan config](https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/questflow.ts). All-time 473,884 tx, $10,205 total, 14,254 buyers, 13,297 sellers, last 2026-10-04 — [x402scan API](https://www.x402scan.com/api/trpc/public.facilitators.list).
- `GET https://facilitator.questflow.ai/supported` and `/` return HTTP 302 to `https://questflow.ai/` (checked 2026-10-11) — direct probe.
- Product pivot: changelog moves from x402 facilitator and app monetization (2025-11-14) to Polymarket AI Clone (2026-02-27), Hyperliquid (2026-05-05) — [changelog](https://feedback.questflow.ai/changelog); homepage now reads "AI finance agent for outsized returns" — [questflow.ai](https://questflow.ai).

#### Inferences
- The November-December 2025 spike looks like agent-to-agent traffic among thousands of Questflow-created agent wallets (13,297 recipients, 14,254 payers, about $0.02 average ticket) rather than outside demand; it faded as the company's focus moved to prediction markets. This is an inference from the on-chain shape, not a Questflow statement.
- The planned token appears to have been shelved or never launched.

#### Gaps
- No usage numbers for the new finance product; no named co-founders besides Bob Xu; Crunchbase and RootData pages were not retrievable.

### Q2. Bankr: x402 product (paid endpoints, agent wallets)?

#### Takeaway
Yes. Bankr launched x402 Cloud on 2026-04-02: deploy a TypeScript handler, get a payment-gated endpoint at `x402.bankr.bot/<wallet>/<name>`, with Bankr acting as facilitator and covering gas. Free for the first 1,000 settled requests a month, then a 5% fee. It also has agent wallets, an x402 pay-per-prompt SDK (alpha on npm since 2025-07-30; example repo from 2025-10-26) and a CLI that pays x402 endpoints. No public usage numbers and no x402scan footprint were found.

Lead check: confirmed (Base and Farcaster origin, BNKR token exists on Base); incomplete, because Bankr is now a multi-chain agent platform and token launcher, and its token launches default to Robinhood Chain rather than Base.

#### Cited findings
- Launch on 2026-04-02, same day the x402 protocol joined the Linux Foundation; "Bankr acts as the x402 facilitator and covers gas" — [Yellow.com copy of the Chainwire release](https://yellow.com/press-releases/bankr-launches-x402-cloud-on-4-02-day-as-x402-protocol-joins-the-linux-foundation), [Chainwire](https://chainwire.org/2026/04/02/bankr-launches-x402-cloud-on-4-02-day-as-x402-protocol-joins-the-linux-foundation/).
- Mechanics: handler plus `bankr.x402.json`, `upto` scheme via Permit2, any ERC-20 on Base (USDC default, EURC), logs, dashboard, marketplace at bankr.bot/terminal/x402/discover, `facilitator: https://api.bankr.bot/facilitator`, `payTo` is a Bankr fee-router contract — [Bankr docs (llms-full)](https://docs.bankr.bot/llms-full.txt), [x402 Cloud overview](https://docs.bankr.bot/x402-cloud/overview).
- Pricing: Free 0% up to 1,000 requests/month; Pro 5%; Enterprise 3% — [docs](https://docs.bankr.bot/x402-cloud/pricing).
- Agent wallet side: every agent gets a wallet; `/wallet/x402-pay` endpoint; apps can request a `pay:x402` permission so a visitor's wallet pays an x402 URL — [docs](https://docs.bankr.bot/llms-full.txt).
- Earlier x402 use: `@bankr/sdk` first published 2025-07-30 (alpha, last 2026-01-16); `BankrBot/x402-cli-example` (2025-10-26) charges USDC on Base per Bankr agent request — [npm](https://www.npmjs.com/package/@bankr/sdk), [repo](https://github.com/BankrBot/x402-cli-example).
- x402scan origin search for "bankr" returns nothing; the x402 ecosystem directory has no Bankr entry — [x402scan origins.search](https://www.x402scan.com/api/trpc/public.origins.search), [ecosystem data](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data).

#### Inferences
- Bankr runs its own discovery layer instead of relying on x402scan or the Coinbase Bazaar, so its volume is invisible to public x402 dashboards.

#### Gaps
- Number of deployed endpoints, settled requests and revenue are not published. Funding unknown.

### Q3. Olas: does it support x402, and how?

#### Takeaway
Yes, in three layers of different maturity. (1) Buyer: Pearl agents (Prediction Trader/Omenstrat, Polystrat, Optimus, Modius, Basius) pay x402 APIs such as CoinGecko and Gemini with USDC, shipped since Oct-Nov 2025, using an x402 client library in `valory-xyz/genai`. (2) "Mech facilitator": from 2026-10-02 four Pearl agents pay API calls through the Mech Marketplace using Safe-signed marketplace requests instead of USDC transfers; this is x402-flavoured rather than standard x402 (the client is a "drop-in sibling" of the x402 requests adapter and a 402 means "pre-deposit too low", but there is no EIP-3009 payment header). (3) Seller/facilitator on the Mech Marketplace itself: written specs only (June 2026), described as "planned" in the repo as of 2026-10-04 and "short-term" on the roadmap. A commit-message search for "x402" across the valory-xyz org (196 commits, 2026-10-11) hits only genai (81), optimus (54), trader (33), olas-operate-app (12), autonolas-marketplace (12) and olas-operate-middleware (4); the mech, mech-client and mech-server repos have zero.

Lead check: confirmed (Valory builds Olas and the Mech Marketplace); the x402 support is real but mostly on the buyer side, not on the marketplace's seller side as the lead implied.

#### Cited findings
- First x402 commit in the org 2025-10-28 (genai, "implement x402 support", adapted from Coinbase's SDK); Optimus and trader x402 commits 2025-10-30; Pearl v1 with x402 merged 2025-11-04 — [genai](https://github.com/valory-xyz/genai), [optimus](https://github.com/valory-xyz/optimus), [trader](https://github.com/valory-xyz/trader).
- Olas timeline: "Q4 2025 Pearl v1 agents integrated x402" — [olas.network/timeline](https://olas.network/timeline).
- Mech facilitator: Pearl flags `X402_ENABLED_FLAGS` and `MECH_FACILITATOR_ENABLED_FLAGS`; commit 2026-10-02 "move omenstrat, polystrat, Optimus and Basius onto the mech facilitator" — [olas-operate-app constants](https://github.com/valory-xyz/olas-operate-app/blob/main/frontend/constants/x402.ts), [genai mech client](https://github.com/valory-xyz/genai/blob/main/packages/valory/connections/x402/clients/mech.py).
- Seller-side spec: `docs/x402_spec.md` (updated 2026-06-29) makes the mech both resource server and facilitator via a new `BalanceTrackerX402USDC` contract; `CLAUDE.md` calls x402 "planned" and one of two candidate payment families — [spec](https://github.com/valory-xyz/autonolas-marketplace/blob/main/docs/x402_spec.md), [CLAUDE.md](https://github.com/valory-xyz/autonolas-marketplace/blob/main/CLAUDE.md).
- Roadmap: Marketplace "Now: support for ERC-8004 and x402"; "Short-Term: native x402 support" — [olas.network/roadmap](https://olas.network/roadmap).

#### Inferences
- Olas uses x402 mainly as agent-as-buyer plumbing; its newest "mech facilitator" borrows x402's shape (HTTP 402 plus a facilitator) but settles through the marketplace, which also makes the payments count as staking activity; no outside agent can yet pay a mech over x402 because the seller side is unbuilt.

#### Gaps
- No Olas facilitator or verified Olas seller appears on x402scan (two unattributed ngrok "mech" origins registered; see Olas profile).

### Q4. Screening: Giza, Theoriq, Recall, Spectral, Wayfinder, Clanker, Zora

#### Takeaway
Only Zora has shipped a material x402 feature: a `zora pay` command in its agent CLI (v1.6.0, 2026-06-25), a buyer-side x402 v2 client on Base. Giza, Theoriq, Recall, Spectral, Wayfinder and Clanker: no material x402 work found as of 2026-10-11. One-line entries are under "Screened projects".

#### Cited findings
- Zora CLI `pay` command and x402 library: [changelog](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/CHANGELOG.md), [pay.ts](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/src/commands/pay.ts).
- GitHub code search for "x402" across each org found nothing relevant for Giza, Theoriq (chain-ml), Recall, Spectral, Wayfinder, Clanker (details in the one-liners).

#### Inferences
- The screened names are mostly 2024-era "AI agent on Base" projects that moved toward DeFi vaults, evals or launch tooling; none treats x402 as a product line. Zora's `pay` command looks like a convenience for its agent CLI rather than a strategy.

#### Gaps
- Theoriq docs host and thegrid.ai (Spectral) were unreachable from my environment; Wayfinder docs were read through a GitBook mirror.

### Q5. Other Base agent platforms or launchpads with x402 central

#### Takeaway
Three discovered projects have x402 as a core product and real footprint: AWE Network (x402 Market launchpad plus facilitator, but 2026 marketing has moved to prediction-market vaults), BlockRun (x402-native AI gateway; its Base and Solana origins are #3 and #5 all-time among Bazaar origins by transaction count), and FluxA (agent payments platform, second only to Coinbase by facilitated volume in the last 30 days). Smaller or faded: Locus, Conway, Treasure/AI Frens, Claw402/NoFx, x402.jobs, Agoragentic, Agently.

#### Cited findings
- The x402.org ecosystem page URL `x402.org/ecosystem` returned 404; the same data is the `partners-data` folder in the x402 GitHub repo (202 entries on 2026-10-11) — [partners-data](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data).
- x402scan 30-day facilitator ranking (2026-10-11): Coinbase 2,045,372 tx / $579,783; PayAI 254,407 tx / $8,233; FluxA 136,530 tx / $322,401 — [x402scan API](https://www.x402scan.com/api/trpc/public.facilitators.list).
- BlockRun origins are #3 and #5 all-time by transaction count among Bazaar origins (27.6M and 22.5M tx) — [x402scan API](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list).

#### Inferences
- The x402-central projects with real footprint are either founded in 2026 around x402 (BlockRun) or payments-first (FluxA); the older "agent platform with a token" group (Questflow, AWE) shows narrative drift, with both moving to Polymarket-based products in 2026.
- Typical x402 tickets are tiny (BlockRun about $0.017 per tx all-time, Questflow facilitator about $0.02), so transaction counts overstate economic value. FluxA is the exception: its average ticket rose from about $0.10 in June to about $0.9-1.6 in September-October while its transaction count fell.

#### Gaps
- Base's ecosystem directory (base.org/ecosystem) renders client-side ("Loading...") and could not be read; the directory listing was not checked.
- x402scan buyer lists are address-only, so I could not attribute top buyers (agents) to platforms.

---

## Full profiles

### 1. Questflow

#### One-line
Multi-agent orchestration startup that ran an x402 facilitator on Base in late 2025, then pivoted in 2026 to an AI finance agent that copies top investors on Polymarket and Hyperliquid.

#### x402 role
- Facilitator (Base): live 2025-10-29; x402scan facilitator id `questflow` with 10 Base addresses ([config](https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/questflow.ts)). Needed an API key (Bearer) per the same config.
- Seller/resource server: `api.questflow.ai` exposes 105 registered x402 resources; top row 200,210 tx, $7,076, 14,086 buyers, last tx 2026-03-02 ([x402scan](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list)).
- App/agent client: Multi-Agent Orchestration Protocol (MAOP) with CDP server wallets per agent; Coinbase case study dated 2025-08-01 claims 130,000+ microtransactions and 30+ third-party agents ([Coinbase](https://www.coinbase.com/developer-platform/discover/case-studies/questflow); vendor-reported, unverified; pre-dates the facilitator's visible on-chain history).
- Status on 2026-10-11: dormant. Facilitator host redirects (HTTP 302) to the homepage.

#### Chains
Base primary (x402scan shows Base only). The facilitator post does not name specific chains (Base appears only as an example) and invites other L1/L2s to apply; the 2025 review claims expansion to X Layer and Mantle in October 2025 ([blog](https://blog.questflow.ai/p/questflow-facilitator-for-x402-goes), [review](https://blog.questflow.ai/p/questflow-2025-from-belief-to-system)); I saw no on-chain evidence outside Base.

#### Token
- Ticker/contract: none confirmed. 2024-06-25 plan: 1B supply, halving every two years (150M/yr in years 1-2, 75M/yr in years 3-4), 85% Guardian Nodes, 10% DAO treasury, 5% applications; points Q3, community airdrop September, TGE Q4, CEX/DEX listings ([plan](https://blog.questflow.ai/p/questflow-community-incentive-plan)).
- Launch date/method: not found. CoinGecko `/coins/questflow` is 404. "QF Coin" appears on a low-authority directory only.
- Utility: stated (node mining, rewards, tokenized swarms) but unproven; nothing in 2026 posts references it.

#### Team
- Bob Xu (Boyue Xu), co-founder and CEO. Doxxed: named in the press release ([The Block](https://www.theblock.co/amp/post/363633/questflow-secures-6-5m-seed-round-to-build-ai-agent-economy-for-every-workflow)) and CB Insights lists "Boyue Xu, CEO" ([CB Insights](https://www.cbinsights.com/company/questflow/people)). GitHub `xuboyuebobb` (bio "Questflow - AI Finance Agent", sole author of investorskills). X @bobbxu is set as his GitHub `twitter_username`, i.e. self-declared (high confidence) ([GitHub](https://github.com/xuboyuebobb)). A search snippet of Crunchbase says he previously founded DECODE (not fetched, unverified).
- Carney Chu: engineer. GitHub `CarneyChu` (bio "@questflowai"), committed to the org's x402scan fork on 2025-11-01/02 ([GitHub](https://github.com/CarneyChu)); also listed on the LinkedIn company page. No X handle found.
- LinkedIn company page lists Carney Chu, Fagoriola Boluwatife and Una Chen, "2-10 employees", HQ Emeryville, California ([LinkedIn](https://www.linkedin.com/company/questflow/)). Roles not shown. Other committers to org forks: `sparrowfly` ("rideman"), `QianWu184`, `tonliyp` ("Yongpan Li"); no self-declared roles.
- Blog posts publish under the account "Questflow.ai" (Substack handle `timisbuilding`); not mapped to a person.

#### Track record and pivots
- 2023-03/05: blog and GitHub org start; Telegram/Discord bots, Stable Diffusion, wallet and ERC-20 features ([sitemap](https://blog.questflow.ai/sitemap.xml)).
- 2024-01/03: Product Hunt launches; 2024-06: "Questflow Labs", decentralised agent network and token plan; 2024-07-08: $1.5M angel round.
- 2024-09 to 11: Tars AI assistant, agent teams, "tokenizing agent swarms".
- 2025-03 to 07: PayFi/DeFAI posts, Google A2A, StakeKit yield automation; 2025-07-22: $6.5M seed.
- 2025-08: x402 launched, agents in the Base App; 2025-09: ERC-8004/AP2 posts; 2025-10-29: facilitator; 2025-11-12: "x402 for Everything" meetup in Singapore with Coinbase developers; 2025-12-03: Questflow Developer Platform (publish an MCP/API as a paid agent) ([QDP post](https://blog.questflow.ai/p/launch-and-monetize-your-ai-agent)).
- 2026-02-11 to 02-26: prediction-market posts and "Questflow Next" (AI clones for Polymarket) ([post](https://blog.questflow.ai/p/questflow-next-one-ai-clone-every)). 2026-05: Hyperliquid, trading arena. 2026-08-20: "Financial Intelligence for All". 2026-08-26: users told to move off the CDP-based wallet to a new non-custodial wallet ([migration guide](https://blog.questflow.ai/p/questflow-account-migration-and-activation)).

#### Trend-hopping score
4 of 5. Real products each time (workflow tool, agent network, facilitator, developer platform, trading clones), but the headline narrative changed about every six months (AI workflows, DeFAI/PayFi, x402/agent economy, prediction markets, finance agent), and the x402 line was dropped within about three months of launching the facilitator. x402 was not a natural extension of the new product.

#### Funding
- 2024-07-08: $1.5M angel, led by MiraclePlus; participants include founders from PAKA, AgentLayer, TypoX, Dmail Network, Chasm and Litentry; incubators Cohere, SpringX, Web3+AI ([blog](https://blog.questflow.ai/p/questflow-labs-secures-angel-funding)).
- 2025-07-22: $6.5M seed, led by CyberFund (investors and grants are listed in the Q1 answer above).
- Totals: CB Insights search snippet says $8M over 8 rounds (includes grants; not fetched).

#### Product and traction
- Live now: next.questflow.ai app with AI Clones, Smart Clone auto-trading, copy trading, leaderboards from Hyperliquid and Polymarket ([changelog](https://feedback.questflow.ai/changelog)); open-source Investor Skills library (1,900 stars) plus closed paid skills ([repo](https://github.com/questflowai/investorskills)).
- Traction numbers: x402 facilitator monthly settled transfers: Oct 2025 6,652; Nov 272,169; Dec 174,589; Jan 2026 20,054; Feb 32; Mar 75; Apr 91; May 180; Jun 28; Jul 3; Aug 9; Sep 0; Oct (to 10-04) 2 ([x402scan](https://www.x402scan.com/api/trpc/public.stats.bucketed)). Volume $10.2k lifetime. No user counts published for the finance product.

#### Last six months
- 2026-04-20/21 changelog: sports markets, one-click copy trading, Smart Clone auto-trading. 2026-05-05: native Hyperliquid trading, V2, natural-language trades. 2026-05-22: Discover page, leaderboards, Trade Desk ([changelog](https://feedback.questflow.ai/changelog)).
- 2026-05-27: investorskills repo created; 20 commits (May 7, Jul 12, Aug 1 by month since Apr 1), one contributor, no releases, last commit 2026-08-21 ("Add Grayscale Crypto Sectors skill") ([repo](https://github.com/questflowai/investorskills)). All other org repos are forks last pushed 2026-02-04 or earlier ([org](https://github.com/questflowai)).
- Weekly blog (about 27 posts since 04-11; latest 2026-10-09), e.g. 2026-08-12 benchmark of ten AIs trading real money ([feed](https://blog.questflow.ai/feed)).
- 2026-08-26: wallet migration. x402: under 200 tx/month, last tx 2026-10-04.
- Team joins/departures: none announced; LinkedIn shows 5 profiles.

#### Pace verdict
Product pace is fine for a 2-10 person team (weekly blog, changelog every 2-4 weeks). Public code pace is slow: one repo, one contributor, 20 commits (all between 05-27 and 08-21), and no x402 code at all. Category leaders are far ahead on x402: Coinbase processes about 2.0M facilitated tx per 30 days, and the x402 core repo has roughly 65-115 commits a month ([x402 repo](https://github.com/x402-foundation/x402)).

#### Direction
Stated: "Financial Intelligence for All", investor-skill agents with permissioned execution across prediction markets, equities, FX and crypto ([post](https://blog.questflow.ai/p/questflow-financial-intelligence-cb9)); docs do not mention x402, facilitator, MAOP or a token ([docs](https://docs.questflow.ai)). Shipping record matches this and contradicts the 2025 agent-economy/x402 roadmap.

#### Competitors
For x402 facilitation: Coinbase CDP, PayAI, Dexter, FluxA. For the new product: Polymarket copy-trading tools and AI trading agents (e.g. NoFxAiOS/nofx on GitHub, 13k stars) ([search](https://github.com/NoFxAiOS/nofx)).

#### Green and red flags
- Green: real funding; doxxed CEO; shipped a facilitator and developer platform; regular public writing.
- Red: x402 abandonment after a short burst; facilitator redirects to homepage; planned token never visible; heavy narrative changes; users asked to migrate wallets; the Coinbase case study's 130k-microtx claim cannot be matched to x402scan data (the facilitator's visible history starts 2025-10-29, three months after the case study); tiny public engineering footprint.

#### Verdict
Credible but small as a company; its x402 line is likely abandoned. Momentum: Stalled for x402, Steady for the finance product. Questflow is a good case study in how quickly x402 enthusiasm turned into a different business, and the next signal worth watching is whether the finance pivot gains users, not whether the facilitator returns. For a daily x402 watchlist, drop it.

#### Tracking card
- Website https://questflow.ai ; app https://next.questflow.ai ; docs https://docs.questflow.ai ; blog/RSS https://blog.questflow.ai/feed ; changelog https://feedback.questflow.ai/changelog
- GitHub org https://github.com/questflowai (repos: investorskills; x402scan, qf-x402, erc-8004-contracts are forks)
- X @questflow (linked from the website footer and the GitHub org profile, high confidence); Farcaster @questflow (fid 1363868; its connected X account is shown as Questflow_, so which X account is primary is unconfirmed); CEO X @bobbxu; LinkedIn company/questflow; YouTube @QuestflowLabs
- Discord https://discord.com/invite/ZJEBVRfcWp ; Telegram https://t.me/+8Hh5JNE4i-w1ZDI1
- Token: none. x402scan: facilitator id `questflow` (addresses 0x724efafb051f17ae824afcdf3c0368ae312da264, 0xa9a54ef09fc8b86bc747cec6ef8d6e81c38c6180, plus 8 more); origin https://api.questflow.ai ; facilitator host facilitator.questflow.ai (redirects)
- Dune: none found

#### Sources
All accessed 2026-10-11: [questflow.ai](https://questflow.ai); [blog sitemap](https://blog.questflow.ai/sitemap.xml); [blog feed](https://blog.questflow.ai/feed); [changelog](https://feedback.questflow.ai/changelog); [docs](https://docs.questflow.ai); [The Block](https://www.theblock.co/amp/post/363633/questflow-secures-6-5m-seed-round-to-build-ai-agent-economy-for-every-workflow); [Coinbase case study](https://www.coinbase.com/developer-platform/discover/case-studies/questflow) (fetched with a browser user agent; the fetch tool got 403); [facilitator post](https://blog.questflow.ai/p/questflow-facilitator-for-x402-goes); [x402 meetup post](https://blog.questflow.ai/p/why-we-hosted-the-x402-everything); [2025 review](https://blog.questflow.ai/p/questflow-2025-from-belief-to-system); [incentive plan](https://blog.questflow.ai/p/questflow-community-incentive-plan); [angel post](https://blog.questflow.ai/p/questflow-labs-secures-angel-funding); [QDP](https://blog.questflow.ai/p/launch-and-monetize-your-ai-agent); [Questflow Next](https://blog.questflow.ai/p/questflow-next-one-ai-clone-every); [migration guide](https://blog.questflow.ai/p/questflow-account-migration-and-activation); [GitHub org](https://github.com/questflowai); [x402scan PR #242](https://github.com/Merit-Systems/x402scan/pull/242); [x402scan API](https://www.x402scan.com/api/trpc/public.stats.bucketed); [LinkedIn](https://www.linkedin.com/company/questflow/); [CB Insights people](https://www.cbinsights.com/company/questflow/people); [x402 ecosystem entry](https://github.com/coinbase/x402/blob/main/typescript/site/app/ecosystem/partners-data/questflow/metadata.json); [Warpcast API](https://api.warpcast.com/v2/user-by-username?username=questflow).

---

### 2. Bankr

#### One-line
An AI agent with a built-in wallet (started as a Farcaster/X trading bot) that now also launches tokens, hosts pay-per-request x402 endpoints, runs an LLM gateway and works across Base, Robinhood Chain, Arbitrum, Arc and more.

#### x402 role
- Seller platform and facilitator: x402 Cloud hosts developer handlers as payment-gated endpoints on `x402.bankr.bot`; `payTo` is a Bankr fee-router contract; facilitator URL `https://api.bankr.bot/facilitator`; x402 v2, `exact` and `upto` (Permit2) schemes ([docs](https://docs.bankr.bot/llms-full.txt)).
- Buyer/agent client: Bankr agent wallet pays x402 endpoints; CLI `bankr x402 call` with `--max-payment` cap (0.3.23, 2026-08-14); wallet API `/wallet/x402-pay`; apps can request `pay:x402` ([docs](https://docs.bankr.bot/llms-full.txt)).
- Discovery: marketplace at bankr.bot/terminal/x402/discover and `bankr x402 search`.
- SDK/tooling: `@bankr/sdk` (alpha, USDC per prompt), `@bankr/cli`, `BankrBot/claude-plugins` (x402-sdk-dev plugin) ([repo](https://github.com/BankrBot/claude-plugins)).

#### Chains
Base is primary for x402 (USDC and EURC on Base) and for BNKR. For token launching the docs now default to Robinhood Chain, with Base, Arbitrum and Arc also supported; CLI wallet commands cover Robinhood Chain (2026-07-02) and Arc (2026-09-16) ([docs changelog](https://docs.bankr.bot/llms-full.txt)).

#### Token
- BNKR ("BankrCoin"), Base `0x22aF33FE49fD1Fa80c7149773dDe5890D3c76F3b`; Robinhood Chain `0x178E54df3D091EE4D0B2534742eF9e3692b76526`. Total supply 100 billion ([CoinGecko](https://www.coingecko.com/en/coins/bankercoin-2)); contracts also listed in Bankr docs.
- Launch: first Uniswap pool on Base created 2024-12-03 ([DexScreener](https://api.dexscreener.com/tokens/v1/base/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b)); described as deployed by Bankr itself in a Farcaster cast ([GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/base/tokens/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b/info)); exact launchpad contract not confirmed. CoinGecko tags it "Clanker Ecosystem" and "x402 Ecosystem".
- Utility (docs): accepted payment for Bankr Club ($20/month or $198/year in USDC, BNKR or ETH), a quote asset for token launches on Base and Robinhood Chain, and 0.2375% of trading volume on each Doppler launch goes to BNKR buybacks and protocol-owned BNKR liquidity (part of the 1.75% all-in swap fee) ([docs](https://docs.bankr.bot/llms-full.txt)). It does real work in the launchpad and subscription flows; x402 Cloud itself runs on USDC/EURC.

#### Team
- "Deployer", founder: quoted as "Deployer, Founder, Bankr" in the x402 Cloud release ([Chainwire](https://chainwire.org/2026/04/02/bankr-launches-x402-cloud-on-4-02-day-as-x402-protocol-joins-the-linux-foundation/)). Pseudonymous. npm maintainer `0xdeployer` of `@bankr/cli` and `@bankr/sdk` ([npm](https://www.npmjs.com/package/@bankr/cli)); GitHub `0xdeployer` (site deployer.wtf, which links X); Farcaster @deployer (fid 4482, bio "Currently deploying. www.bankr.bot", profile token = BNKR) with connected X account `0xDeployer` ([Warpcast](https://warpcast.com/deployer)). Confidence high that these are one person; real identity not sought. His older public repos suggest an NFT/Farcaster-tooling background (nounoclock 2022, hamcaster 2024) ([GitHub](https://github.com/0xdeployer)).
- Igor Yuzovitskiy, DevRel: Farcaster bio "DevRel @bankr" (igoryuzo.eth, fid 17714); GitHub `igoryuzo` has `twitter_username` igoryuzo (self-declared); top committer in BankrBot/skills (124) ([Warpcast](https://warpcast.com/igoryuzo.eth), [GitHub](https://github.com/igoryuzo)).
- Danny Brown Wolf, "COO", named as press contact in the Yellow.com copy of the release; the Chainwire page I fetched shows no name, so treat it as unconfirmed ([Yellow](https://yellow.com/press-releases/bankr-launches-x402-cloud-on-4-02-day-as-x402-protocol-joins-the-linux-foundation)).
- Community contributors to the skills repo (third parties, not necessarily employees): saltoriousSIG (X saltorious1), sidrisov, chackle, tylerbroqs (X tylerbroqs), anondevv69, tekkaadan (co-founder of another project, per his bio) ([contributors](https://github.com/BankrBot/skills/graphs/contributors)).

#### Track record and pivots
- 2024-12-03: BNKR pool created; Bankr bot is "first AI agent on Farcaster" for buying coins by cast (GeckoTerminal description).
- 2025-02-18: BankrBot GitHub org created. 2025-07-30: `@bankr/sdk` alpha. 2025-10-26: x402 CLI example. 2025-11-21: docs repo.
- 2026-01-15 to 02-26: Claude plugins, skills repo (2026-01-26), tokenized-agents, token-strategist; `@bankr/cli` first release 2026-02-09 ([npm](https://www.npmjs.com/package/@bankr/cli)).
- 2026-04-02: x402 Cloud (the release also mentions an LLM gateway already live). 2026-07: Robinhood Chain launches. 2026-09: Arbitrum and Arc launches, stock-paired token launches, repeated model-list refreshes for Max Mode, passkey/TOTP login.
- Core stayed constant (chat-driven agent that holds a wallet and moves money); chains and surface area expanded.

#### Trend-hopping score
2 of 5. One continuous product (an agent wallet you talk to). An x402 pay-per-prompt SDK was on npm (alpha) from 2025-07-30 with an example repo on 2025-10-26, and x402 Cloud is a real product with pricing. Expansion into Robinhood Chain, stock-paired tokens and Arc follows market themes, which keeps it above 1.

#### Funding
No evidence of outside funding found. The release, docs and help pages do not mention investors; RootData returned an empty page and CryptoRank returned 403, Crunchbase not tried for Bankr. Treat as unknown rather than none.

#### Product and traction
- Live: agent wallet and chat, terminal, Bankr Club subscription, token launching (Doppler and Bankr Launch v3), x402 Cloud, LLM gateway, apps, webhooks, wallet and agent APIs, CLI ([docs](https://docs.bankr.bot/)).
- Numbers: BankrBot/skills 1,203 stars, 643 forks; Farcaster @bankr 8,368 followers, @deployer 24,580 ([Warpcast API](https://api.warpcast.com/v2/user-by-username?username=bankr)). No published x402 Cloud usage, revenue or endpoint counts; no x402scan origin matching "bankr".

#### Last six months
- `@bankr/cli` npm releases in window: 13 (Apr 2, Jun 2, Jul 2, Aug 1, Sep 5, Oct 1): 0.2.15 (04-19), 0.3.1 (04-22), 0.3.8 (06-16), 0.3.11 (06-29), 0.3.12 (07-02), 0.3.13 (07-06), 0.3.23 (08-14), 0.3.32 (09-09), 0.3.35 (09-16), 0.3.37 (09-17), 0.3.38 (09-18), 0.3.43 (09-30), 0.3.45 (10-02) ([registry](https://registry.npmjs.org/@bankr%2Fcli)). Gap with no release 04-22 to 06-16.
- Shipped per CLI changelog: multi-profile projects, private TEE models, Robinhood Chain support (07-02, 07-06), `bankr x402 call --max-payment` cap, no-vesting and quote-only-fee launches (08-14), Arbitrum launches (09-09), launch quote tokens/tokenized stocks and Arc (09-16), passkey and authenticator-app login (09-18, 10-02), `bankr llm usage` (10-02) ([changelog](https://docs.bankr.bot/llms-full.txt)).
- GitHub: BankrBot/skills commits by month since Apr 1: Apr 72, May 76, Jun 102, Jul 99, Aug 78, Sep 54, Oct (to 10-11) 7; about 15+ distinct authors since 04-11; last commit 2026-10-11 ([repo](https://github.com/BankrBot/skills)). Other public repos idle: claude-plugins (last push 2026-03-24), tokenized-agents (02-26), x402-cli-example (2025-10-26). `@bankr/sdk` last published 2026-01-16.
- Team joins/departures: none announced.

#### Pace verdict
Fast on the closed product (CLI release roughly every 1-3 weeks outside the April-June gap, a versioned changelog, several chains added in about 90 days) and the skills repo sees about 3 commits a day, but most commits there come from partners and community. It is comparable to what a small AI-assisted team ships. The public x402 repos are stale, the only visible x402 evidence is docs plus the CLI, and the first-party SDK has not moved since January. Against leaders: the x402 core repo has roughly 65-115 commits a month; BlockRun's ClawRouter ships a tagged release every 2-13 days.

#### Direction
Stated: "Build an AI agent. Launch a token. Trading fees pay for your compute", i.e. infrastructure for self-sustaining agents, with x402 Cloud, LLM gateway and wallet APIs as developer surfaces ([docs](https://docs.bankr.bot/)). Shipping record agrees; x402 is one of several surfaces, and recent shipping effort is mostly chains, launches and login security rather than x402 features.

#### Competitors
x402 hosting and monetisation: Cloudflare (Workers with x402), Vercel (x402-mcp), Coinbase CDP facilitator and Bazaar, Merit Systems/AgentCash, thirdweb, Foldset, Tollbooth. Agent wallet and launches: Coinbase agent wallets, Virtuals, Clanker, Zora, pump.fun. Ahead on x402 volume: Coinbase CDP, PayAI, BlockRun; ahead in agent-token distribution: Virtuals and Clanker.

#### Green and red flags
- Green: x402 Cloud is shipped with pricing, docs and CLI; consistent releases; clear BNKR utility tied to fees; thorough security docs and a bug bounty; real x402 buyer controls (`--max-payment`).
- Red: no usage data for x402; no x402scan or Bazaar visibility; funding undisclosed; founder pseudonymous; core closed source; first-party SDK stale; BNKR utility depends on launchpad trading fees rather than x402 revenue.

#### Verdict
Serious builder. Momentum: Steady (CLI cadence picked up in September). It is the only one of the three that sells x402 as a priced product today, but there is no proof anyone pays for it yet. Expect Bankr to keep stacking surfaces (chains, stock-paired launches, LLM gateway) and treat x402 Cloud as a feature of that stack. Worth a daily glance at the CLI changelog and docs because it ships fast; judge x402 traction only once endpoint or revenue numbers appear.

#### Tracking card
- Website https://bankr.bot ; docs https://docs.bankr.bot (full text https://docs.bankr.bot/llms-full.txt) ; help https://help.bankr.bot ; x402 Cloud https://docs.bankr.bot/x402-cloud/overview ; dashboard https://bankr.bot/x402 ; marketplace https://bankr.bot/terminal/x402/discover
- Changelog: CLI changelog inside docs; npm https://www.npmjs.com/package/@bankr/cli
- GitHub org https://github.com/BankrBot (skills, claude-plugins, tokenized-agents, x402-cli-example)
- X @bankrbot (docs/CoinGecko); founder X @0xDeployer; DevRel X @igoryuzo; Farcaster @bankr, @deployer, @igoryuzo.eth
- Discord https://discord.gg/bankr ; Telegram bot https://t.me/bankr_ai_bot
- Token: BNKR Base 0x22aF33FE49fD1Fa80c7149773dDe5890D3c76F3b
- x402 identifiers: endpoint host x402.bankr.bot/<wallet>/<name>; facilitator https://api.bankr.bot/facilitator; no x402scan facilitator or origin
- Dune: none found

#### Sources
All accessed 2026-10-11: [Bankr docs](https://docs.bankr.bot/); [llms-full](https://docs.bankr.bot/llms-full.txt); [x402 Cloud overview](https://docs.bankr.bot/x402-cloud/overview); [Chainwire release](https://chainwire.org/2026/04/02/bankr-launches-x402-cloud-on-4-02-day-as-x402-protocol-joins-the-linux-foundation/); [Yellow copy](https://yellow.com/press-releases/bankr-launches-x402-cloud-on-4-02-day-as-x402-protocol-joins-the-linux-foundation); [npm registry cli](https://registry.npmjs.org/@bankr%2Fcli); [npm registry sdk](https://registry.npmjs.org/@bankr%2Fsdk); [BankrBot/skills](https://github.com/BankrBot/skills); [x402-cli-example](https://github.com/BankrBot/x402-cli-example); [CoinGecko BNKR](https://www.coingecko.com/en/coins/bankercoin-2); [DexScreener](https://api.dexscreener.com/tokens/v1/base/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b); [GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/base/tokens/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b/info); [Warpcast API](https://api.warpcast.com/v2/user-by-username?username=deployer); [deployer.wtf](https://deployer.wtf); [x402scan origins.search](https://www.x402scan.com/api/trpc/public.origins.search).

---

### 3. Olas (Valory)

#### One-line
Open-source network for autonomous AI agents built by Valory AG (Zug, Switzerland), made of the Pearl desktop "agent app store", the Mech Marketplace where agents hire agents, a staking system paid in OLAS, and Open Autonomy, the agent framework.

#### x402 role
- Buyer/agent client (shipped): x402 client library in `valory-xyz/genai` (EIP-3009 signing, httpx/requests transports), used by Pearl agents to pay CoinGecko and Gemini with USDC; x402 flags on for Prediction Trader, Optimus, Modius, Basius and Polystrat ([constants](https://github.com/valory-xyz/olas-operate-app/blob/main/frontend/constants/x402.ts)).
- Mech facilitator (shipped 2026-10-02; x402-flavoured, not standard x402): the agent posts to a facilitator URL that proxies the upstream API, and each call becomes a Safe-signed marketplace request that debits the service Safe's pre-deposit; the facilitator answers HTTP 402 with balance/required details when the deposit is too low (`MechDepositRequiredError`). Because these are marketplace requests they also move the on-chain activity counter that staking programs read ([constants](https://github.com/valory-xyz/olas-operate-app/blob/main/frontend/constants/x402.ts), [mech client](https://github.com/valory-xyz/genai/blob/main/packages/valory/connections/x402/clients/mech.py)).
- Seller/resource server and facilitator for mechs (specified, not shipped): the mech is both resource server and facilitator via `BalanceTrackerX402USDC` ([spec](https://github.com/valory-xyz/autonolas-marketplace/blob/main/docs/x402_spec.md)); discovery via `/.well-known/x402` and x402scan registration ([doc](https://github.com/valory-xyz/autonolas-marketplace/blob/main/docs/x402scan_integration.md)).
- Discovery/analytics: none yet; an earlier facilitator proof-of-concept repo `valory-xyz/x402-poc` is not public (404).

#### Chains
Not Base-primary overall: mechs started on Gnosis (H1 2023), and Pearl agents run on Gnosis (Omen), Polygon (Polystrat), Base (Basius, Agents.fun) and several chains (Optimus); the marketplace lists Ethereum, Gnosis, Arbitrum, Optimism, Base, Polygon and Robinhood Chain ([marketplace](https://olas.network/mech-marketplace)). For x402 the target is Base: the spec says "x402 ecosystem heavily concentrated on Base" and notes Gnosis has no public facilitator and bridged USDC may lack EIP-3009. The x402 client's USDC table covers Base, Optimism, Gnosis, Polygon and Avalanche.

#### Token
- OLAS. Base `0x54330d28ca3357F294334BDC454a032e7f353416` (Olas' own deployment config, [globals_base_mainnet.json](https://github.com/valory-xyz/autonolas-registries/blob/main/scripts/deployment/l2/globals_base_mainnet.json)); Ethereum `0x0001a500a6b18995b03f44bb040a5ffc28e45cb0`; also Gnosis, Arbitrum, Optimism, Polygon, Celo, Mode, Robinhood, Solana ([CoinGecko](https://www.coingecko.com/en/coins/autonolas)).
- Launch: public launch 2023-07-12 through a week-long Liquidity Bootstrapping Pool on Ethereum ([Olas timeline](https://olas.network/timeline)). CoinGecko lists total supply about 473.7M and no hard cap.
- Utility and real work: staking for agent services (Pearl agents earn OLAS activity rewards; staking programs on Base exist in the registries config), bonding, veOLAS governance; 15% marketplace protocol fee activated by a DAO vote on 11-14 June with OLAS burned (the timeline lists it under 2026 Q2 without stating the year) ([timeline](https://olas.network/timeline)). The token does real work in the product; x402 payments themselves are USDC.

#### Team
All doxxed. Sources: [valory.xyz team](https://valory.xyz).
- David Minarsch, co-founder and CEO; GitHub `DavidMinarsch` (bio "Co-founder at valoryag"), X @david_enim (self-declared on his GitHub profile, high confidence); 81 commits to autonolas-marketplace since 04-11, including the x402 and per-request-nonce contract work.
- David Galindo, co-founder and CTO (team page; no handles found).
- Gemma Welsh, COO since 2025-05-08. Ellie Hirschhorn, Chief Growth Officer since 2025-09-08 (from CoinDesk) ([posts](https://valory.xyz/post/c-suite-shuffle-2), [post](https://valory.xyz/post/valory-welcomes-ellie-hirschhorn-chief-growth-officer)).
- Aleksandr Kuperman, GitHub `kupermind` (company @valory-xyz, X @kupermind self-declared on GitHub, high confidence); 542 commits to autonolas-marketplace overall, 23 since 04-11 (tokenomics/governance audits as of 2026-08-21). Not on the team page.
- Engineers (team page + GitHub): Divya Nautiyal (`DivyaNautiyal07`, Python Engineer; author of the x402 spec/docs and most x402 code: 86 genai commits, 348 optimus commits since 04-11); Ojuswi Rastogi (`OjusWiZard`, Senior Python Engineer per his GitHub bio, X @OjuswiRastogi self-declared, high confidence); Adamantios Zaras (`Adamantios`); Jose Moreira-Sanchez (`jmoreira-valory`); Tanya Priemova (Lead Frontend; GitHub `Tanya-atatakai`, name match only); Iason Rovis (Senior PM, `iasonrovis`); Jenslee Dsouza (`LOCKhart07`, profile says Valory; built the trader x402 support). `valory-coding-agent` is a bot account that commits PRs.
- Departure: Oaksprout the Tan, co-founder and CPO, stepped back on 2025-05-08 ([post](https://valory.xyz/post/c-suite-shuffle-2)).

#### Track record and pivots
- 2021-12: first Autonolas buildathon call; 2022: autonomous services for DAOs (Balancer grant 2022-08, Ceramic grant 2023-01); 2023-03: whitepaper, "co-owned AI"; 2023-07-12: OLAS LBP; 2023: mechs on Gnosis, prediction agents, Governatooorr.
- 2024: staking launched, Pearl (2024-05-21 "Stake an agent"), Propel Genie (2024-07), Olas Predict, BabyDegen/Optimus.
- 2025: Mech Marketplace, $13.8M raise led by 1kx, Olas Accelerator ($1M), Pearl v1 (with x402) and pearl.you (2025-12-16), agents.fun on Base.
- 2026: ERC-8004 identity, Polystrat (Polygon), Basius (Base), Pearl Mini (launched Q2, discontinued Q3), Pearl Connect (wallet for coding agents), Robinhood Chain, off-chain mech requests ([timeline](https://olas.network/timeline)).

#### Trend-hopping score
2 of 5. Same thesis for five years: autonomous agents coordinated through on-chain services and staking. Naming changed (Autonolas to Olas, "co-owned AI" to agent economies to Pearl) and 2026 adds Robinhood Chain and coding-agent wallets, but x402 slots straight into the Mech Marketplace idea of paid agent services.

#### Funding
- $13.8M raise led by 1kx, reported Q1 2025 ([Olas timeline](https://olas.network/timeline), [Valory post 2025-05-08](https://valory.xyz/post/c-suite-shuffle-2)). Valory's investor logos: True Ventures, Signature Ventures, Semantic, Prime Block, Proof, Atka (names inferred from logo file names on [valory.xyz](https://valory.xyz); round attribution unconfirmed). Earlier grants from Balancer (2022) and Ceramic (2023).

#### Product and traction
- Mech Marketplace page (2026-10-11 10:00 UTC): $109,885 lifetime marketplace fees (including legacy mechs) and 14,768,564 agent-to-agent transactions across seven chains ([olas.network](https://olas.network/mech-marketplace)). Timeline: 20M on-chain agent transactions passed 2026-08-16; Q1 2026 record 834 daily active agents; marketplace passed 10M A2A tx in Q1 2026.
- Pearl: seven agents listed (Connect, Polystrat, Omenstrat, Basius live; Optimus, PettBro, Agents.fun marked unavailable) ([pearl.you](https://pearl.you)).
- x402 specific: no public counts. The only x402scan hits are two ngrok-hosted "mech" origins (weather-mech, dexes-mech) with one pay-to address, 20 tx, last 2026-02-06; I could not attribute them to Olas ([x402scan](https://www.x402scan.com/api/trpc/public.origins.search)).

#### Last six months
- 2026-06-08/09: `x402_vs_mpp.md` decision guide; Basius agent added to Pearl with x402 flag (2026-06-08); 2026-06-29: x402 spec, implementation plan, x402scan integration doc revised.
- 2026-06 (mid): DAO activates the 15% marketplace fee; 2026-07-13: Pearl Connect phase 1; 2026-08-16: 20M tx.
- September 2026: 60 genai commits, mostly x402 mech-facilitator work (nonce slots, replay handling) concentrated on 09-23 to 09-30; releases genai v7.2.3 (09-25), v7.2.4 (09-28), v7.2.5 (09-30) ([releases](https://github.com/valory-xyz/genai/releases)).
- 2026-10-01/02: CEO commits `deliverMarketplaceWithSignatures` overload with per-request nonces (groundwork for batching); 2026-10-02: four agents moved to the mech facilitator; Nevermined contract set marked deprecated ([marketplace commits](https://github.com/valory-xyz/autonolas-marketplace/commits/main)).
- Releases 2026-10-09: optimus v0.13.4, trader v0.41.3, Pearl app v1.11.2, mech v0.35.9.
- Commits per month since Apr 1 (Apr/May/Jun/Jul/Aug/Sep/Oct): genai 16/40/0/2/9/60/0; autonolas-marketplace 2/18/36/24/20/32/14; optimus 60/117/153/36/16/52/69; trader 163/223/59/67/62/59/54; olas-operate-app 498/450/273/141/167/207/124.
- Commit messages mentioning "x402" across the whole org by month: Oct 2025 29, Nov 8, Dec 2, Jan 2026 4, Mar 10, Apr 4, May 28, Jun 14, Jul 1, Aug 2, Sep 78, Oct (to 10-11) 16 ([GitHub commit search](https://github.com/search?q=x402+org%3Avalory-xyz&type=commits)). Olas-operate-middleware has 4, all from 2025-10-31 to 11-02 (x402 agent funding).
- Active x402 contributors since 04-11: DivyaNautiyal07, DhairyaPatel7, OjusWiZard, Tanya-atatakai, DavidMinarsch, kupermind, valory-coding-agent. Last commits: genai 2026-09-30, marketplace 2026-10-04, optimus and trader 2026-10-09.
- Team joins/departures in the window: none announced; Valory's blog has no 2026 posts (newest 2025-12-31).

#### Pace verdict
Fast and broad: about 25 repos pushed between 2026-09-14 and 2026-10-09, multiple tagged releases a week across product repos, an AI coding agent in the loop (CLAUDE.md files, a bot account), and the CEO committing contracts. Against category leaders (x402 core repo roughly 65-115 commits/month) Olas matches or beats them on raw engineering volume. The x402-specific slice is uneven: genai had no commits in June and 2 in July, then 60 in September. Seller-side x402 is behind its own "short-term" roadmap label.

#### Direction
Stated: Marketplace "native x402 support and dynamic fees" short-term, MCP-based single-signature access mid-term, Pearl for mainstream users ([roadmap](https://olas.network/roadmap)). Shipping record: buyer-side x402 and mech facilitator are done; marketplace x402 contracts are specs plus preparatory contract work; the repo also weighs MPP sessions as an alternative payment family.

#### Competitors
Virtuals ACP (about 2.4M x402scan tx, $4.9M volume), elizaOS, Daydreams, Fetch.ai/ASI ecosystem (shared AEA lineage), Coinbase AgentKit and agentic wallets, Bankr for consumer agent wallets. Ahead on x402 volume: Coinbase CDP, Virtuals, BlockRun. Olas is ahead on staking-backed agent distribution and open-source depth.

#### Green and red flags
- Green: five-year history; funded ($13.8M); doxxed team; real token utility; heavy commit and release cadence; honest docs that label x402 seller side as "planned"; x402 spec reviewed for settlement-race and chain limits.
- Red: x402 marketplace revenue is small ($109,885 lifetime fees); x402 usage is mostly self-consumption by Pearl agents; Optimus, PettBro and Agents.fun marked unavailable in Pearl; MPP vs x402 choice not final; Valory blog silent in 2026; reliance on a few engineers (one engineer authors most x402 commits).

#### Verdict
Serious builder. Momentum: Accelerating on x402 (September-October 2026 burst) and Steady overall. Olas is the most technically serious x402 adopter in this group, but its x402 is internal plumbing rather than an open seller economy so far. The interesting experiment is the mech facilitator, which turns x402-style paid API calls into marketplace requests that also count toward staking rewards. If the marketplace contracts for native x402 ship, Olas becomes a seller platform; until then, follow it for how agents consume x402, not how they sell it.

#### Tracking card
- Websites https://olas.network ; https://valory.xyz ; https://pearl.you ; marketplace https://marketplace.olas.network ; docs https://docs.olas.network ; roadmap https://olas.network/roadmap ; timeline https://olas.network/timeline
- Blog: https://olas.network/blog (index showed no list); Valory posts https://valory.xyz/post (last 2025-12-31). Changelog: GitHub releases.
- GitHub org https://github.com/valory-xyz (key repos: genai, autonolas-marketplace, optimus, trader, olas-operate-app, mech, mech-client, autonolas-registries)
- X @autonolas (CoinGecko), @valoryag (valory.xyz), @pearldotyou (pearl.you); Farcaster @olas (fid 196827) and @autonolas (fid 310971); persons: @david_enim, @kupermind, @OjuswiRastogi (GitHub-declared)
- Discord https://discord.gg/BQzYqhjGjQ (CoinGecko)
- Token OLAS Base 0x54330d28ca3357F294334BDC454a032e7f353416
- x402scan: no facilitator id, no verified origin; unattributed ngrok mech origins weather-mech.ngrok-free.dev, dexes-mech.ngrok-free.dev
- Dune: not found

#### Sources
All accessed 2026-10-11: [genai](https://github.com/valory-xyz/genai); [x402 mech client](https://github.com/valory-xyz/genai/blob/main/packages/valory/connections/x402/clients/mech.py); [autonolas-marketplace docs](https://github.com/valory-xyz/autonolas-marketplace/tree/main/docs) (x402_spec.md, x402_vs_mpp.md, x402scan_integration.md, x402_implementation_plan.md); [marketplace CLAUDE.md](https://github.com/valory-xyz/autonolas-marketplace/blob/main/CLAUDE.md); [optimus](https://github.com/valory-xyz/optimus); [trader](https://github.com/valory-xyz/trader); [olas-operate-app](https://github.com/valory-xyz/olas-operate-app); [GitHub commit search "x402" in org](https://github.com/search?q=x402+org%3Avalory-xyz&type=commits); [Olas timeline](https://olas.network/timeline); [roadmap](https://olas.network/roadmap); [mech marketplace](https://olas.network/mech-marketplace); [valory.xyz](https://valory.xyz); [Valory posts](https://valory.xyz/post); [C-suite post](https://valory.xyz/post/c-suite-shuffle-2); [Pearl rebrand post](https://valory.xyz/post/from-olas-to-pearl-dot-you); [CoinGecko](https://www.coingecko.com/en/coins/autonolas); [registries config](https://github.com/valory-xyz/autonolas-registries/blob/main/scripts/deployment/l2/globals_base_mainnet.json); [pearl.you](https://pearl.you).

---

### 4. Zora (screened; real but narrow x402 work)

#### One-line
Onchain social/creator-coin protocol on Base whose agent-oriented CLI gained an x402 buyer command in June 2026.

#### x402 role
Buyer/agent client and SDK/tooling: `zora pay` (CLI v1.6.0, 2026-06-25) signs x402 v2 payments for Base resources from the agent's smart wallet or EOA, `exact` scheme only, prefers USDC, honours `--max-value`; two modes (pay-and-fetch with `--url`, sign-only with `--accepts`) ([changelog](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/CHANGELOG.md), [docs](https://github.com/ourzora/zora-protocol/blob/main/cli-docs/docs/pages/commands/pay.mdx), [skill](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/skills/pay/SKILL.md)). Single commit, PR #1890, by `alexanderwende` ([commit history](https://github.com/ourzora/zora-protocol/commits/main/packages/cli/src/lib/x402)). No seller, facilitator or discovery role. Not on x402scan or in the ecosystem directory.

#### Chains
Base (command is Base-only).

#### Token
ZORA on Base `0x1111111111166b7FE7bd91427724B487980aFc69`; total/max supply 10B; CoinGecko tags "Coinbase Ventures Portfolio" and "Base Native" ([CoinGecko](https://www.coingecko.com/en/coins/zora)). Launch date and method not confirmed in this pass. Utility described as an ecosystem utility asset; no role in x402.

#### Team
Not fully verified. Public GitHub: Iain Nash (`iainnash`, company @ourzora, X @isiain self-declared; 577 commits), Dan Oved (`oveddan`, X @oveddan; 531), `alexanderwende` (x402 author, no profile details), `kulkarohan`, `IsabellaSmallcombe`; npm maintainers of `@zoralabs/cli`: `j-s` and `gilllo` ([npm](https://www.npmjs.com/package/@zoralabs/cli)). Founders were not verified because no fetchable official page named them.

#### Track record and pivots
Protocol repo created 2020-01 (org) and zora-protocol 2023-02; NFT marketplace, then Zora Network, then Coins (attention trading) and creator coins, then agent-first CLI (v1.0.0 2026-03-31). Dates for earlier phases not verified here.

#### Trend-hopping score
3 of 5. Real product at each stage (NFTs, L2, coins, agents). The x402 command is a feature, not a pivot.

#### Funding
Not verified; CoinGecko lists it in the Coinbase Ventures portfolio.

#### Product and traction
Zora app, Coins SDK, CLI (26 npm versions total, `1.9.2` latest). zora-protocol 211 stars. No x402 usage numbers.

#### Last six months
CLI releases: 1.1.0 (04-20), 1.2.0 (06-16), 1.3.0 and 1.4.0 (06-17), 1.4.1 (06-18), 1.4.2 (06-22), 1.5.0 (06-24), 1.6.0 (06-25, pay), 1.6.1/1.6.2 (06-26), 1.7.0 (06-30), 1.8.0 (07-14), 1.9.0 (07-16), 1.9.1 (07-20), 1.9.2 (07-23); none since. zora-protocol commits by month: Apr 24, May 1, Jun 100, Jul 8, Aug 2, Sep 0; last commit 2026-08-11 (merge of a bug-bounty docs sync by `gilllo`). Authors since 04-11 (top): alexanderwende 34, Alexzander-Ciminillo 33, carter-zora 10, ninazo 8, gilllo 8, pedroapfilho 5 ([repo](https://github.com/ourzora/zora-protocol)).

#### Pace verdict
A burst of 14 CLI releases between 06-16 and 07-23, then no release for about eleven weeks; slow now. Any x402 follow-up would have appeared in the CLI package, and nothing has.

#### Direction
Agent-first CLI (DMs, wallets, coin commands). x402 is a convenience for agents to pay APIs, not a stated priority.

#### Competitors
Coinbase's own agent wallet/CDP tools, Bankr, thirdweb client SDK, x402-proxy, Merit's AgentCash.

#### Green and red flags
Green: shipped, documented, safe defaults (spend cap, smart wallet). Red: one commit, no follow-up, development quiet since July, founders/funding not verified.

#### Verdict
Credible but small as an x402 project (x402 is a minor feature of a larger company). Momentum: Slowing. Worth a one-off mention; not worth a daily watch.

#### Tracking card
Website https://zora.co ; docs https://docs.zora.co (CLI docs in the repo) ; GitHub https://github.com/ourzora/zora-protocol ; npm @zoralabs/cli ; X @zora ; Farcaster @zora (fid 20910) ; token ZORA Base 0x1111111111166b7FE7bd91427724B487980aFc69 ; x402scan: none ; Dune: not checked.

#### Sources
[Zora CLI changelog](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/CHANGELOG.md); [pay.ts](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/src/commands/pay.ts); [pay SKILL](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/skills/pay/SKILL.md); [npm registry](https://registry.npmjs.org/@zoralabs%2Fcli); [CoinGecko ZORA](https://www.coingecko.com/en/coins/zora); [Warpcast](https://api.warpcast.com/v2/user-by-username?username=zora); accessed 2026-10-11.

---

### 5. AWE Network (World.fun, x402 Market)

#### One-line
Formerly STP Network, now "The Agentic World Economy": a Base-token project that runs a free x402 facilitator, "x402 Market" (a launchpad that mints service tokens for x402-priced agents) and the ERC-8004/x402 "800402 Initiative", while its 2026 marketing is mostly about Polymarket vaults.

#### x402 role
- Facilitator: World.fun facilitator, live; `/supported` lists x402 v1 and v2 `exact` on Base (eip155:8453), Base Sepolia and Polygon, signer `0x6Cb960c17A623575dd8db626899C0645ed30E3d5` ([probe 2026-10-11](https://facilitator.world.fun/supported)); fee-free USDC on Base per docs ([docs](https://docs.awenetwork.ai/llms-full.txt)).
- Launchpad/token experiment: x402 Market issues fungible service tokens for agents that sell via x402, graduates them to a DEX at a market-cap threshold, and routes liquidity and fees to the agent wallet ([800402 docs](https://docs.awenetwork.ai/llms-full.txt)).
- Tooling and trust/analytics: AWEtoAgent Kit (agent scaffold with x402 and ERC-8004), AgentBeat (analytics for ERC-8004 agents including x402 flows), AWESOME (capability index).
- Seller: `api-x402.world.fun` on x402scan: 68,177 tx, $122, 123 buyers, last tx 2026-04-18 ([x402scan](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list)).

#### Chains
Base primary (token and facilitator), plus Polygon support in the facilitator.

#### Token
AWE (formerly STPT), Base `0x1b4617734c43f6159f3a70b7e06d883647512778`; old Ethereum `0xde7d85157d9714eadf595045cc12ca4a5f3e2adb`; max supply 2B ([CoinGecko](https://www.coingecko.com/en/coins/awe-network)). Migration 1:1 announced May 2025; first Base pair (Aerodrome) 2025-05-21 ([docs timeline](https://docs.awenetwork.ai/llms-full.txt), [DexScreener](https://api.dexscreener.com/tokens/v1/base/0x1b4617734c43f6159f3a70b7e06d883647512778)). Stated utility: create/customise agents and pay protocol fees for world orchestration; 2,660,000 AWE locked per site snapshot of 2026-09-16 ([awenetwork.ai](https://awenetwork.ai)). The STPT migration window was scheduled to close 2026-09-21 (I did not confirm that it did). x402 payments themselves use USDC.

#### Team
No individuals named on the site, docs, blog or annual report. GitHub org `STPDevteam` (created 2019-11-04). AWEtoAgent-Kit contributor list overlaps with Daydreams' `lucid-agents` (beauwilliams, ponderingdemocritus, RedBeardEth), so it appears derived from Daydreams' open-source code (inference); other contributors `overdosed-22`, `togodn2` are pseudonymous ([repo](https://github.com/STPDevteam/AWEtoAgent-Kit), [lucid-agents](https://github.com/daydreamsai/lucid-agents)). Project X @awenetwork_ai; research X @aw_research.

#### Track record and pivots
2019-2022 STP Network (tokenization/DAO tooling); 2023-24 autonomous worlds and multi-agent engine, World.fun; 2025-05 STPT becomes AWE; late 2025 x402 facilitator, x402 Market, ERC-8004 identity, AgentBeat, AWESOME; 2026 Polyvaults (Polymarket vaults, launched end of April) and Realyse (trading-card price layer) ([docs](https://docs.awenetwork.ai/llms-full.txt)).

#### Trend-hopping score
4 of 5. Long-lived team and real products at each step, but the narrative moved with the market (tokenization, AI worlds, agents, x402/8004, prediction markets, RWA price data).

#### Funding
No evidence found. 2026-06: AWE Foundation moved part of its assets to Coinbase Custody ([June update](https://awenetwork.ai/blog/june-2026-update)). Exchange listings include Binance, Coinbase, Upbit ([annual report](https://awenetwork.ai/blog/awe-2025-annual-report)).

#### Product and traction
Site snapshot dated 2026-09-16: 112,250 x402 transactions settled (labelled "latest WorldFun daily snapshot"; daily versus cumulative unclear), 5,522 registered agents, 1,322,977 price observations on Realyse ([awenetwork.ai](https://awenetwork.ai)). Polyvaults passed $150K monthly volume mid-July ([July update](https://awenetwork.ai/blog/july-2026-update)).

#### Last six months
Monthly updates Apr-Aug 2026 are almost all Polyvaults, token visibility and custody; x402 appears once (April: "Top 10 AI project of the week on Base", citing x402 momentum) ([April](https://awenetwork.ai/blog/april-2026-update)). Public GitHub: 6 commits in the org since 04-11, all docs in `narrative-index-skill` (last 2026-07-07); AWEtoAgent-Kit last push 2026-02-04. No releases.

#### Pace verdict
Marketing cadence monthly, public engineering cadence near zero; core code is closed. Looks slow on open x402 work compared with BlockRun (releases every few days) or Olas.

#### Direction
Docs headline x402 and ERC-8004 as "the rails"; the 2026 shipping record is prediction-market vaults and RWA data.

#### Competitors
Virtuals ACP, Daydreams, Clanker/Zora for launches, Coinbase CDP facilitator.

#### Green and red flags
Green: live facilitator, exchange liquidity, a detailed x402 Market design. Red: anonymous team, no funding disclosure, derivative SDK, public code quiet, x402 messaging faded, headline traction figure ambiguous.

#### Verdict
Speculative. Momentum: Steady (marketing) / Stalled (open x402 engineering). Worth a mention as the clearest x402-launchpad design on Base, not as a builder to follow daily.

#### Tracking card
https://awenetwork.ai ; docs https://docs.awenetwork.ai ; blog https://awenetwork.ai/blog ; GitHub https://github.com/STPDevteam ; X @awenetwork_ai, @aw_research ; Farcaster @awenetwork (fid 3197828) ; Telegram https://t.me/AWEofficial ; Discord https://discord.com/invite/srqXY7SnSc ; token AWE Base 0x1b4617734c43f6159f3a70b7e06d883647512778 ; facilitator https://facilitator.world.fun ; x402scan origin api-x402.world.fun ; Dune: a "worldfun" contract dashboard is linked in the blog footer (URL not captured).

#### Sources
[awenetwork.ai](https://awenetwork.ai); [docs llms-full](https://docs.awenetwork.ai/llms-full.txt); [blog posts Apr-Aug 2026](https://awenetwork.ai/blog); [annual report](https://awenetwork.ai/blog/awe-2025-annual-report); [CoinGecko](https://www.coingecko.com/en/coins/awe-network); [facilitator](https://facilitator.world.fun/supported); [x402 ecosystem entries](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data); accessed 2026-10-11.

---

### 6. BlockRun

#### One-line
x402-native AI gateway: one endpoint for 88-115 LLMs and about 100 tools and data APIs, paid per call in USDC over x402 on Base and Solana.

#### x402 role
Seller/resource server and gateway; also SDK/tooling and buyer-side client (ClawRouter, BlockRun MCP, `blockrun-llm` SDKs, Franklin agent). Per x402scan it settles through Coinbase's facilitator on Base and through Figment and PayAI on Solana (Corbits and Coinbase appear earlier in the all-time data). On x402scan: `blockrun.ai` 27,574,606 tx, $479,924, 3,254 buyers (all-time rank 3 by tx); `sol.blockrun.ai` 22,539,666 tx (rank 5) ([x402scan](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list)). 30-day (2026-10-11): `blockrun.ai` 82,720 tx, `sol.blockrun.ai` 226,706 tx, though `claw402.ai` and `ax1.vc` show more tx; BlockRun's own claim of "more payments than any other service" covers the 30 days to 2026-10-02 ([site](https://blockrun.ai)).

#### Chains
Base and Solana (Solana added February 2026; changelog 2026-10-02 says the five newest models are now served on both).

#### Token
None mentioned on the site or About page (GitHub READMEs not checked for a token).

#### Team
Vicky Fu, founder (About page): ex-Circle (Head of Data Science), ex-Capital One, ex-Microsoft ([About](https://blockrun.ai/about)). GitHub `VickyXAI` is the top committer in the four main BlockRunAI repos I checked (ClawRouter, blockrun-mcp, Franklin, blockrun-llm); linking it to the named founder rests on a first-name match, so moderate confidence. `KillerQueen-Z` (bio "Building Franklin & ClawRouter @BlockRunAI", 44 commits to Franklin). Project X @BlockRunAI. No personal X handles found.

#### Track record and pivots
BlockRun, Inc. incorporated in Delaware 2026-01-05; x402 LLM gateway live on Base January 2026; Solana February; ClawRouter won the Circle USDC OpenClaw Hackathon (Agentic Commerce track) March 2026 and was open-sourced; 2026-07-08 "Marketplace" renamed "Services" and site repositioned as "routing and payment layer for AI" ([About](https://blockrun.ai/about), [changelog](https://blockrun.ai/changelog)).

#### Trend-hopping score
2 of 5. Born as an x402 gateway in 2026 and stayed on it; side products (Franklin agent, OpenClaw routing) are extensions, though OpenClaw timing is trend-driven.

#### Funding
None disclosed.

#### Product and traction
Site claims 28.9M transactions settled, 88-115 models (page inconsistent), 100 data and tool APIs, 40-chain RPC, ClawRouter 6.6k stars, MCP 391, Franklin 555 ([site](https://blockrun.ai)).

#### Last six months
Changelog entries nearly every week, mostly model additions and payment tweaks: 2026-04-27 insufficient-USDC wallets fall back to a free model; 2026-07-08 repositioning; 2026-08-07 flat $0.001 per-call fee, per-call settlement; 2026-10-02 Solana/Base parity ([changelog](https://blockrun.ai/changelog)). GitHub commits per month since Apr 1: ClawRouter 133/40/38/36/54/99/9 (v0.12.279 09-16 to v0.12.282 10-05); blockrun-mcp 61/32/65/75/57/50/10 (v0.54.2 10-08); Franklin 466/190/68/64/39/65/50 (v3.49.6 10-08); blockrun-llm 18/40/36/33/18/25/8 (v1.17.1 09-30) ([org](https://github.com/BlockRunAI)). Contributors: VickyXAI, KillerQueen-Z, achiurizo, tenequm, 0xCheetah1.

#### Pace verdict
Fastest of the discovered projects: tagged releases every few days, weekly changelog, active across five repos. Matches a small AI-assisted team and the x402 core repo cadence.

#### Direction
Stated: routing and payment layer for agents, more models/tools, enterprise and platform offerings. Shipping agrees.

#### Competitors
OpenRouter (not x402), Daydreams Router, Venice, Locus Pro, Coinbase CDP resources, AgentCash.

#### Green and red flags
Green: doxxed founder with stablecoin-infrastructure background, real volume, open-source repos with stars, no token. Red: tiny average ticket (about $0.017/tx), possible bot or test traffic inflating counts, no disclosed funding, self-reported claims differ from x402scan ranking, resale margin dependent on upstream providers.

#### Verdict
Serious builder. Momentum: Accelerating. One of the clearest examples of a company built around x402 rather than adding it.

#### Tracking card
https://blockrun.ai ; docs /docs ; changelog https://blockrun.ai/changelog ; RSS https://blockrun.ai/feed.xml ; GitHub https://github.com/BlockRunAI ; X @BlockRunAI ; no Farcaster/Discord/Telegram found ; no token ; x402scan origins blockrun.ai, sol.blockrun.ai ; Base pay-to addresses include 0x058a5961fbe8cd8e4b47c69d3d82e159cb5d8f17.

#### Sources
[blockrun.ai](https://blockrun.ai); [about](https://blockrun.ai/about); [changelog](https://blockrun.ai/changelog); [GitHub org](https://github.com/BlockRunAI); [x402scan API](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list); accessed 2026-10-11.

---

### 7. FluxA

#### One-line
Agent payments company (FLUXA LIMITED) with an AI wallet, single-use cards, a marketplace and an "AEP2" mandate protocol, and one of the fastest-growing x402 facilitators on Base.

#### x402 role
Facilitator (x402scan id `fluxa`, 6 Base addresses), seller marketplace ("AgentMarket"), buyer wallet and SDK. Open Deferred Payments (ODP) on x402 v2 batches receipts (2026-01-25 post) ([blog](https://fluxapay.substack.com)). All-time 2,697,731 tx, $660,556, 49,693 buyers, 62,074 sellers; last 2026-10-10. 30 days: 136,530 tx / $322,401, second to Coinbase by volume ([x402scan](https://www.x402scan.com/api/trpc/public.facilitators.list)).
Monthly tx (volume): Apr 2026 146,337 ($40k); May 488,657 ($57k); Jun 834,488 ($80k); Jul 529,751 ($18k); Aug 403,666 ($133k); Sep 206,061 ($187k); Oct (to 10-11) 89,713 ($145k) ([x402scan bucketed](https://www.x402scan.com/api/trpc/public.stats.bucketed)).

#### Chains
Base only on x402scan; docs mention EVM.

#### Token
None mentioned.

#### Team
Not disclosed. GitHub org `FluxA-Agent-Payment` (created 2025-10-24); contributors `cpppppp7` and `ZSkyX` (pseudonymous). X @FluxA_Official (site link).

#### Track record and pivots
2025-11-26 FluxA Wallet; 2025-12-19 Mandate (AP2); 2026-01-25 ODP; 2026-02-10 Payment Links; 2026-04-20 Agentic Checkout; 2026-06-05 Baidu AI Cloud partnership; 2026-08-21 AIHubMix (40+ models); 2026-09-21 Visa Intelligent Commerce context; 2026-10-08 "ActWithin" ([blog](https://fluxapay.substack.com)).

#### Trend-hopping score
2 of 5. Consistent agent-payments focus; protocol-agnostic (AP2, x402).

#### Funding
None disclosed.

#### Product and traction
140,393 agents created wallets (undated, site) ([fluxapay.xyz](https://www.fluxapay.xyz/)). Volume series above.

#### Last six months
Blog about monthly; GitHub FluxA-AI-Wallet-MCP commits Apr 19, Jun 2, Jul 24, Aug 1, Sep 25; npm `@fluxa-pay/fluxa-wallet-mcp` 0.2.0 (2026-03-02); public repos small (4 stars).

#### Pace verdict
Mid: product ships, public code thin.

#### Direction
Mandates, payment security, cards, partnerships (Baidu, Visa). x402 is one rail.

#### Competitors
Coinbase CDP, Locus, Crossmint, ampersend.

#### Green and red flags
Green: real, rising volume; consistent writing. Red: team and funding undisclosed; transaction counts falling since June while dollar volume rises (average ticket growing); counts may include automated traffic.

#### Verdict
Credible but small. Momentum: Steady. Not covered in the three assigned leads but worth tracking as a facilitator.

#### Tracking card
https://www.fluxapay.xyz ; docs https://docs.fluxapay.xyz ; blog https://fluxapay.substack.com (feed /feed) ; GitHub https://github.com/FluxA-Agent-Payment ; X @FluxA_Official ; Discord https://discord.gg/Btt4XvgNgm ; x402scan facilitator id `fluxa` (e.g. 0x7f72a02c682e908d46a5677fe937cdb612d94a3b).

#### Sources
[fluxapay.xyz](https://www.fluxapay.xyz/); [blog](https://fluxapay.substack.com); [GitHub](https://github.com/FluxA-Agent-Payment); [x402scan](https://www.x402scan.com/api/trpc/public.facilitators.list); accessed 2026-10-11.

---

## Screened projects (one line each)

- **Giza**: no material x402 work found as of 2026-10-11. Checked: GitHub code search in `gizatechxyz` (5 hits, all in airdrop CSV data files, none in code), docs `llms-full.txt` (271 KB, 0 mentions), x402scan origin search "giza" (0), x402 ecosystem list (absent). Giza today is an Agent SDK for DeFi yield optimisation agents with Base as the default chain ([docs](https://docs.gizatech.xyz/llms.txt)).
- **Theoriq**: no material x402 work found as of 2026-10-11. Checked: GitHub code search in `chain-ml` (0), site (no mention; describes a DeFi strategy curator for tokenised assets, THQ token, no named primary chain), x402scan (0), ecosystem list (absent). Docs host unreachable ([theoriq.ai](https://www.theoriq.ai)).
- **Recall**: no material x402 work found as of 2026-10-11. Checked: `recallnet` code search (0), docs `llms-full.txt` (276 KB, 0), site (arena platform; RECALL ERC-20 live on Base 2025-10-15; latest dated post Dec 2025), x402scan hits for "recall" are unrelated product-recall APIs ([recall.network](https://recall.network)).
- **Spectral**: no material x402 work found as of 2026-10-11. Checked: `Spectral-Finance` code search (3 hits in a repo of scraped Solidity files, not an x402 integration; not inspected further), main site (The Grid, SPEC on Base and Ethereum; no x402 text), x402scan (0). thegrid.ai and the GitBook docs could not be read ([spectrallabs.xyz](https://www.spectrallabs.xyz)).
- **Wayfinder**: no material x402 work found as of 2026-10-11. Checked: org and `wayfinder-paths-sdk` code search (0), docs via GitBook mirror (Shells, Paths, SDK; PROMPT bond; no x402), x402scan (0) ([docs](https://wayfinder-1.gitbook.io/wayfinder)).
- **Clanker**: no material x402 work found as of 2026-10-11. Checked: `clanker-devco` code search for clanker-sdk and DOCS (0), docs site (Droids fund their own compute from LP rewards; API payment not described), x402scan origins containing "clanker" are third-party. The site nav shows an unexplained "Agent Skill" link ([docs](https://clanker.world/docs/)).
- **Zora**: material but narrow; see full profile above.

## Other discovered projects (short entries)

- **Locus** (YC F25): "Locus Pro" tool layer (3,960 APIs through one integration) and USDC wallets; 25 `*.x402.paywithlocus.com` origins on x402scan reselling third-party APIs, about 35,600 tx in 30 days; founding engineer Wes Jorgensen (`wjorgensen`, X @wezabis); the homepage I fetched does not mention x402 ([site](https://paywithlocus.com), [org](https://github.com/locus-technologies)). Not profiled in full.
- **Conway / Automaton**: "sovereign" self-paying agents on Base with ERC-8004 and x402 credits; repo 7,163 stars, commits by month 253 (Feb 2026), 39 (Mar), 13 (Apr), 1 (May), 0 (Jun-Jul), 1 (Aug); conway.tech now presents underdog.ai on-device models; founder Sigil Wen (X @0xSigil, GitHub-declared). Faded ([repo](https://github.com/Conway-Research/automaton), [site](https://conway.tech)).
- **Treasure / AI Frens (Summon)**: Treasure x402 facilitator on Base (tokens USDC, MAGIC, SMOL, MIO) with 2,461 tx all-time and an AI-character token launcher; negligible usage ([facilitator](https://x402.treasure.lol/facilitator)).
- **Claw402 / NoFx (Vergex)**: `claw402.ai` ("x402 API Payment Gateway") is the #1 Bazaar origin by 30-day transaction count (424,313 tx but only $940, buyers 149); the NoFx open-source AI trading terminal (13,031 stars, AGPL-3.0, "backed by vergex.trade") documents Claw402 as a keyless way to pay for models in USDC on Base via x402. NoFx commits fell from 53 (Apr) to 1 (Sep). Operator of claw402 not identified beyond that link; x402 is optional in NoFx, so not central ([repo](https://github.com/NoFxAiOS/nofx), [x402scan](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list)).
- **x402.jobs**: workflow builder with facilitator id `x402jobs`, 21,935 tx all-time, last tx 2026-07-07; stale.
- **Agoragentic**: agent marketplace with 62 tx on x402scan; negligible. **Agently** (AgentlyHQ): repos last pushed July 2026; quiet.
- **Nevermined**: listed as facilitator on Base; no x402scan footprint; Olas marked its Nevermined contracts deprecated on 2026-10-02. Not researched further.
- **Cluster Protocol (unconfirmed attribution)**: `api.clusterprotocol.ai` is the #2 x402 seller by 30-day volume ($54,756 over 66,675 tx); the project's site does not mention x402 and I could not confirm the operator.
- **Tokenmesa, PING and x402-minted tokens**: token experiments, left to another researcher.

---

## Method, limits and gaps

- WebSearch hit its shared per-turn limit after about ten queries, so most discovery used direct fetches (official sites, docs `llms-full.txt`, GitHub REST API and code/commit search, npm registry, x402scan tRPC, Warpcast API, DexScreener/GeckoTerminal by contract address, CoinGecko pages). I did not use search engines or third-party readers after the limit.
- Blocked or empty: Crunchbase (403), CryptoRank (403), RootData (empty), DeFiLlama raises API (returns HTTP 402 payment-required), Coinbase case-study via the fetch tool (403; read with a browser user agent), Blockscout (Cloudflare challenge), x.com (not fetchable), thegrid.ai and docs.theoriq.ai (connection failures), Base ecosystem directory (client-rendered), Bankr web pages (client-rendered), Olas token page (region block).
- x402scan figures: "tx" and USD are as indexed by x402scan; amounts are USDC with 6 decimals. Facilitator-level totals include only transfers it attributes to a known facilitator address.
- Pseudonymous people were not linked to real-world identities. X handles are recorded only where the person declared them on GitHub/Farcaster/their own site or an official project page links them.
- Not verified: Zora founders and funding; AWE and FluxA teams and funding; Bankr funding; Olas investor attribution beyond the 1kx-led $13.8M; Dune dashboards for all projects.

---

## Comparison table

| Name | x402 role | Token | Seriousness | Momentum | Trend-hopping (1-5) |
|---|---|---|---|---|---|
| Questflow | Facilitator + seller (dormant since Feb 2026) | None confirmed (2024 plan only) | Credible but small; x402 line likely abandoned | Stalled (x402) / Steady (finance product) | 4 |
| Bankr | Facilitator, seller platform (x402 Cloud), buyer wallet | BNKR, Base 0x22aF33FE...6F3b | Serious builder | Steady | 2 |
| Olas (Valory) | Buyer (shipped), mech facilitator (shipped), seller/facilitator (spec) | OLAS, Base 0x54330d28...3416 | Serious builder | Accelerating (x402), Steady overall | 2 |
| Zora | Buyer CLI command only | ZORA, Base 0x1111...Fc69 | Credible but small (x402 minor) | Slowing | 3 |
| AWE Network | Facilitator, x402 Market launchpad, tooling | AWE, Base 0x1b46...2778 | Speculative | Steady (marketing) / Stalled (open x402 work) | 4 |
| BlockRun | Seller gateway, SDK, buyer client | None | Serious builder | Accelerating | 2 |
| FluxA | Facilitator, wallet, marketplace | None | Credible but small | Steady | 2 |
| Locus | Reseller of x402 APIs, wallet | None found | Credible but small (not fully profiled) | Steady | not scored |
| Conway / Automaton | Buyer-style agents (Base) | none confirmed | Faded | Stalled | not scored |
| Treasure / AI Frens | Facilitator (tiny) | MAGIC (not x402-specific) | Speculative | Stalled | not scored |
| Giza, Theoriq, Recall, Spectral, Wayfinder, Clanker | No material x402 work found | GIZA, THQ, RECALL, SPEC, PROMPT, CLANKER | n/a | n/a | n/a |
