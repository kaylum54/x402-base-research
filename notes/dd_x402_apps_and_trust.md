# x402 apps and trust services on Base: due diligence profiles

Research notes dated 2026-10-11. Window for "last six months": 2026-04-11 to 2026-10-11. Written for a report writer; token facts only, no price analysis. Each profile follows the requested headings; the key-question summary comes first and a comparison table closes the file. "Not found" means I looked and could not confirm. All sources were accessed on 2026-10-11 unless a different date is given.

## Method and data caveats

- Usage numbers come from x402scan's own public tRPC API, the endpoints its website calls (`public.sellers.bazaar.list`, `public.stats.bucketed`, `public.stats.overall`, `public.transfers.list`, `public.origins.search`), queried on 2026-10-11 ([router source](https://github.com/Merit-Systems/x402scan/tree/main/apps/scan/src/trpc/routers/public); [example endpoint](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list)). Amounts are USDC; "buyers" are unique sender addresses; figures are Base-only unless stated; only origins registered in x402scan's Bazaar list can be matched to a named project. x402scan's paid REST API (`/api/x402/*`) answers HTTP 402; I did not pay. For manual tracking, x402scan page patterns are `/server/{originId}`, `/recipient/{payTo}`, `/facilitator/{id}` and `/buyer/{address}` ([route files](https://github.com/Merit-Systems/x402scan/tree/main/apps/scan/src/app/%28app%29)).
- Wash screen behind the "organic or scripted" calls: share of the latest 100 and largest 100 transfers from one wallet; up to 40 sampled payers checked on Base RPC for on-chain history (nonce 0 and no ETH is normal for gasless EIP-3009 payers, so only a weak signal); regularity (identical daily counts, fixed prices); and whether prices make product sense. None of this proves wash trading; it separates organic-looking from scripted.
- Network context from x402scan (Base): monthly transactions / USDC volume: Jan 12.1M / $1.20M; Feb 1.4M / $2.06M; Mar 1.8M / $2.27M; Apr 2.3M / $1.93M; May 3.0M / $1.03M; Jun 12.8M / $0.79M; Jul 11.9M / $0.65M; Aug 9.1M / $1.03M; Sep 2.2M / $0.57M; 1-11 Oct 0.72M / $0.25M. Last 30 days: Base 2.17M transactions and $702k; Solana 491k and $362k; all chains 2.66M and $1.06M ([x402scan tRPC `public.stats.bucketed`](https://www.x402scan.com/api/trpc/public.stats.bucketed)). By contrast x402.org's homepage (page dated 2026-08-25) shows 75.41M transactions, $24.24M, 94.06K buyers and 22K sellers for 30 days ([x402.org](https://x402.org)). I could not reconcile the two (different date or scope). Transaction counts are inflated by micro-payment bursts, and dollars are small.
- Limits: the WebSearch budget ran out part-way, so later work relied on direct fetches, GitHub/npm/DexScreener/Farcaster/Zora APIs and Base RPC; x.com is not fetchable, so X bios are unverified; Crunchbase, CryptoRank, pump.fun and Blockscout blocked requests; CoinGecko's API was rate-limited. People research is limited to public professional information; I did not try to identify anonymous people, and I did not record personal emails that appear in npm metadata.

## Key questions

### The four leads at a glance (confirmed or corrected)

| Lead (from memory) | Status after checking | Correction |
|---|---|---|
| Zauth: verification/trust for x402 endpoints on Base, maybe a token | Partly right | The x402 trust product is real but became secondary on 2026-07-28 when the team repositioned as an AI-security company; the token $ZAUTH is a Solana pump.fun coin, not a Base token |
| Cred Protocol: onchain credit scores for agents, sold via x402 | Mostly right | A 2021 credit-data company; x402 sales have been live on Base since 2026-01-21 but earned $0.88 there; no token |
| Snack Money: pay people by social handle via x402 | Right on the idea, dormant in practice | No x402 payment since 2025-12-04, site returns HTTP 500, API 404, last post 2026-01-10; Zora creator coin stopped trading |
| Fluora: x402 marketplace for agents | Right on the idea, dead in practice | Marketplace API host deleted, no commits since 2026-02-11, the company's site now promotes a Bali wellness product (Kula); no token or funding found |

### 1. Zauth: what is live and who runs it?

#### Takeaway
An anonymous team runs an x402 endpoint registry and monitoring SDK that launched in January 2026 and, since 2026-07-28, is one product inside an AI security company (Vector pentest agent, RepoScan). Its token is a pump.fun coin on Solana, not a Base token.

#### Cited Findings
- The company's own post says it "did not start as a security company", began with an x402 endpoint registry and now sells Vector and RepoScan, with the registry "still running" ([zauth blog, 2026-07-28](https://zauth.inc/blog/endpoints-to-industry)).
- $ZAUTH is Solana mint `DNhQZ1CE9qZ2FNrVhsCXwQJ2vZG8ufZkcYakTS5Jpump`, first PumpSwap pair 2025-12-09, tagged "Pump Fund Portfolio" on CoinGecko ([DexScreener](https://api.dexscreener.com/latest/dex/search?q=ZAUTH); [CoinGecko category](https://www.coingecko.com/en/categories/pump-fund-portfolio)).
- Public code is thin: zauthSDK has 27 commits (last 2026-02-11), the staking program 7 commits (2026-05-20/21), npm last published 2026-02-16 ([GitHub](https://github.com/zauthofficial); [npm](https://registry.npmjs.org/@zauthx402/sdk)).
- Security advisories dated 2026-09-10 and 2026-10-04 name DragonflyDB, ProFTPD and a Uniswap-vault project ([advisories](https://zauth.inc/blog/advisories)).
- No founders named; blog bylines are "Will" and "Dylan" ([blog](https://zauth.inc/blog)).

#### Inferences
- The x402 trust product is now secondary; following Zauth is a security-vendor story, not an x402 story.

#### Gaps
Team identities, actual funding amount (hackathon claim rests on a third-party X post), Provider Hub usage numbers (blank on the site).

### 2. Cred Protocol: what is live and who runs it?

#### Takeaway
A named-CEO (Julian Gay), five-year-old onchain credit-scoring company sells scores to agents through x402 on Base (since 2026-01-21), SKALE and Tempo, plus an MCP toolkit, SDKs and an ERC-8004 validator. The x402 channel has earned $0.88 on Base in total; there is no token.

#### Cited Findings
- x402 launched on Base with the Coinbase CDP facilitator on 2026-01-21 at $0.01 per score; SKALE added 2026-03-03 ([post](https://credprotocol.com/blog/x402-payments-credit-api); [SKALE post](https://credprotocol.com/blog/x402-skale-mainnet)).
- Its Base payTo address shows 44 transactions, $0.88, 4 buyers from 2026-01-16 to 2026-10-08 ([x402scan tRPC](https://www.x402scan.com/api/trpc/public.stats.overall)).
- The ERC-8004 validator agent #36785 (registered 2026-03-25) is marked inactive, with 0 validations ([explorer](https://erc-8004.quicknode.com/agents/base-mainnet/36785)).
- Investors listed: DCG, Volt Capital, Alliance, Robot Ventures, Orange DAO ([careers](https://credprotocol.com/careers)). Julian Gay is named CEO in [Cointelegraph, 2022-07-15](https://cointelegraph.com/news/cred-protocol-unveils-its-first-decentralized-credit-scores).
- Since April: one SDK release (2026-08-18) and Andromeda 1.1/1.2 model updates in September ([docs](https://docs.credprotocol.com/model-release-notes.md)).

#### Inferences
- Real company, negligible x402 demand; the blog tracks payment-rail headlines faster than customers arrived.

#### Gaps
Funding rounds and amounts; usage on SKALE/Tempo; the SKALE-announcement claim of 350,000+ requests (page returned HTTP 429).

### 3. Snack Money: what is live and who runs it?

#### Takeaway
The idea (pay people by social handle through an x402 API) is confirmed, but the project looks dormant or offline: no x402 payment since 2025-12-04, last public post 2026-01-10, `snack.money` returning HTTP 500 and `api.snack.money` returning 404. Its token is a Zora creator coin on Base that stopped trading.

#### Cited Findings
- 654 x402 transactions, $154.92, 26 buyers, all on Base, 2025-06-02 to 2025-12-04 ([x402scan](https://www.x402scan.com/server/bfc2db15-9ceb-40a3-8c2b-6604c32c162b)).
- SNACKMONEY (`0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d`) is a CREATOR coin created 2025-07-27 ([Zora API](https://api-sdk.zora.engineering/coin?address=0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d&chain=8453)); CoinGecko says it stopped trading ([CoinGecko](https://www.coingecko.com/en/coins/snackmoney)).
- Last npm release 2025-12-23; last Farcaster cast 2026-01-10 ([npm](https://registry.npmjs.org/snackmoney); [casts](https://client.farcaster.xyz/v2/profile-casts?fid=1046136&limit=10)).
- No team page; a Farcaster user `@mesut` says he is "Building @snacmoney" ([profile](https://api.warpcast.com/v2/user-by-username?username=mesut)).

#### Inferences
- Likely abandoned; the docs site is the only part still online.

#### Gaps
Who runs it, whether the shutdown is deliberate, funding.

### 4. Fluora: what is live and who runs it?

#### Takeaway
Fluora Inc., led by CEO Chetan Nandakumar, built an early MonetizedMCP/x402 marketplace for agents on Base. It has stalled: no commits since 2026-02-11, no npm release since 2025-09-22, and the marketplace API host `api.fluora.ai` points at a deleted AWS App Runner service. The site still says "developer preview" and now promotes Kula, a Bali wellness-travel product. No token or funding found.

#### Cited Findings
- CEO and background: [podcast, 2025-06-27](https://gregoryandpaulshow.castos.com/episodes/ai-agents-are-secretly-running-your-business-with-guest-chetan-nandakumar); GitHub commits under his name ([fluora-mcp](https://github.com/fluora-ai/fluora-mcp)).
- API host: `api.fluora.ai` CNAME to an App Runner hostname that returns NXDOMAIN ([DNS over HTTPS](https://cloudflare-dns.com/dns-query?name=api.fluora.ai&type=A)); the MCP server's default URL is `https://api.fluora.ai/api` ([constants.ts](https://github.com/fluora-ai/fluora-mcp/blob/main/src/utils/constants.ts)).
- Listed on x402.org 2025-08-29 ([entry](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/fluora)); no x402scan origin.

#### Inferences
- The marketplace is effectively shut down; the team's attention moved elsewhere.

#### Gaps
Funding; seller and buyer counts at peak; whether a relaunch is planned.

### 5. Which other x402-native apps on Base have real, non-wash usage on x402scan?

#### Takeaway
Very few. BlockRun (sustained, tiny dollars, bot-heavy counts) and Laso Finance (small, organic-looking orders on Base; its large Solana dollars come from one wallet) are the only ones I would call real. KORUS, Cluster Protocol, BotPay and AX1 post big numbers that look campaign- or script-driven, and claw402 and X Pay look bot- or self-funded.

#### Cited Findings
Last 30 days, Base, Bazaar-registered origins ([x402scan tRPC](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list), queried 2026-10-11):

| App | 30d transactions | 30d USDC | 30d buyers | Pattern | Call |
|---|---|---|---|---|---|
| Cluster Protocol | 66,675 | 54,756 | 722 | $5 and $15 agent runs by fresh wallets; stopped 2026-10-02 | Unproven, campaign-like |
| KORUS | 23,953 | 18,737 | 11,221 | Uniform $3 payments from single-use wallets; surge from 24 Sep | Unproven |
| AX1 | 407,446 | 8,149 | 4,698 | $0.02 mission calls, scripted | Engagement farming |
| X Pay | 42,270 | 3,439 | 159 | $408 a day, $10 "AI" calls | Likely self-funded |
| BotPay | 21,498 | 2,149 | 691 | 320 wallets x $0.10 daily | Scripted |
| BlockRun | 82,940 (+226,706 on Solana) | 1,544 (+2,901 on Solana) | 569 | 40-75 buyers a day on Base, concentrated | Real, small |
| Laso Finance | 116 (+111 on Solana) | 1,487 (+267,444 on Solana) | 59 (+30) | $5-$30 orders from mixed wallets on Base; on Solana one wallet = 99.6% of dollars | Real but small on Base; Solana is one customer |
| claw402 | 424,313 | 940 | 149 | 96% of top payments from one wallet | Bot-dominated |

- Network-wide, Base x402 dollars fell from about $2.3M in March to $0.57M in September ([monthly series](https://www.x402scan.com/api/trpc/public.stats.bucketed)).

#### Inferences
- Organic x402 revenue on Base is in the low thousands of dollars a month per app, so ranking by transaction count rewards bots. Follow BlockRun daily for what it ships (not for its totals) and check Laso monthly; treat the rest as unverified until a team, repeat buyers or a changelog appears.

#### Gaps
I did not trace whether funds are returned to payers (Base RPC log queries failed); Solana-first apps and unregistered origins are invisible here; no sybil-clustering analysis beyond sampling. Two sizeable Base recipients are not mapped to any x402scan origin, so I could not identify them: `0x93862e5b2b1fa10a01772e7e9ca7cdc7deb5ca25` (1,632 transactions, $22.6k, 151 buyers in 30 days, last payment 2026-09-28, mostly $18 payments) and `0xffde1acbac169f822dabc3d97d6d7127dcae6003` (23 transactions, $35.7k, 14 buyers, tickets of $585-$2,299). Seven Meridian-facilitated recipients each took about $19k from only 5 buyers in 30 days, which also looks like test or wash flow (Meridian is covered by another researcher).

### 6. Did these apps launch tokens to ride the x402 narrative, and which kept shipping?

#### Takeaway
Two of the four leads did: Zauth (pump.fun, Solana, Dec 2025) and Snack Money (Zora creator coin, Base, Jul 2025). Of the others, Cluster Protocol deployed CP on Base the same month its x402 gateway launched (May 2026) and AX1 teases a token. Zauth kept shipping, in a new direction; Snack Money and Cluster Protocol went quiet; the best shipper, BlockRun, has no official token.

#### Cited Findings
- Zauth: [CoinGecko](https://www.coingecko.com/en/coins/zauthx402). Snack Money: [Zora API](https://api-sdk.zora.engineering/coin?address=0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d&chain=8453). Cluster: [CPTOKEN repo](https://github.com/clusterprotocol/CPTOKEN) and [tokenomics](https://cluster-protocol.gitbook.io/whitepaper/introduction/tokenomics.md). AX1: [console](https://console.ax1.vc). BlockRun: [About](https://blockrun.ai/about) (no token) and [DexScreener](https://api.dexscreener.com/latest/dex/search?q=blockrun) (unofficial Solana "BRUN").
- No token found for Cred Protocol, Fluora, Laso Finance or KORUS.

#### Inferences
- A token launch did not predict continued shipping. The projects with the most output (BlockRun, and Zauth's non-x402 security work) either have no token or have a token that is incidental to the product.

#### Gaps
Pump.fun creation date for $ZAUTH; whether CP has ever been paid for services over x402; whether AX1 will launch.


---

## 1. Zauth (zauth, Inc.; site zauth.inc, formerly zauthx402.com)

### One-line
Started in Jan 2026 as a registry and monitoring service for paid x402 endpoints, then on 2026-07-28 said it "did not start as a security company" and repositioned as an AI security vendor (Vector penetration-test agent, RepoScan repo trust scores) with the x402 registry kept as "one piece" ([zauth blog, 2026-07-28](https://zauth.inc/blog/endpoints-to-industry)). The lead ("verification and trust for x402 endpoints on Base, possibly with a token") is half right: the x402 trust product is real but now secondary, and the token is on Solana, not Base.

### x402 role
Trust/identity plus discovery/analytics: "Provider Hub" (providers register endpoints, get uptime/latency checks, failure alerts and optional automatic refunds), a public "Database" directory of discovered/verified x402 endpoints, and the `@zauthx402/sdk` Express middleware that watches x402 v1/v2 payment headers and telemetry ([Provider Hub docs](https://zauth.inc/docs/provider-hub); [SDK README](https://github.com/zauthofficial/zauthSDK)). Not a facilitator. Not registered as a seller on x402scan (origin search for "zauth" returned nothing, [x402scan tRPC `public.origins.search`](https://www.x402scan.com/api/trpc/public.origins.search)). Also a token experiment (pump.fun).

### Chains
SDK supports Base mainnet/Sepolia and Solana mainnet/devnet/testnet; refunds can be paid from EVM or Solana keys ([README](https://github.com/zauthofficial/zauthSDK); [docs](https://zauth.inc/docs/provider-hub)). Treasury doc says token fees are converted to USDC on Base with ETH gas reserves ([treasury doc](https://zauth.inc/docs/treasury)). Base is the x402/treasury rail; the token and the staking program are on Solana.

### Token
- Ticker $ZAUTH (CoinGecko name "Zauthx402"). Chain: Solana. Mint `DNhQZ1CE9qZ2FNrVhsCXwQJ2vZG8ufZkcYakTS5Jpump` (vanity "pump" suffix = pump.fun launch) ([CoinGecko API](https://api.coingecko.com/api/v3/coins/zauthx402); [DexScreener search](https://api.dexscreener.com/latest/dex/search?q=ZAUTH)). Base contract address: none found.
- Launch: earliest DexScreener pair is a PumpSwap pair created 2025-12-09 17:05 UTC; exact pump.fun creation date not confirmed (pump.fun API returned 403). Method: pump.fun launch, later tagged in CoinGecko's "Pump Fund Portfolio" category ("officially backed by Pump Fund, the venture arm of Pump.fun") alongside four other coins ([CoinGecko category](https://www.coingecko.com/en/categories/pump-fund-portfolio)).
- Stated utility: pump.fun creator fees flow to a treasury contract that funds user credits and agent operations ("funded entirely by $ZAUTH token creator fees"); staking with time-locked positions (1 day to 1 year, weight 1x at 30 days to 2x at 365 days, 60-day epochs, early-exit penalty 15-50%, admin-distributed "protocol revenue") ([treasury doc](https://zauth.inc/docs/treasury); [staking README](https://github.com/zauthofficial/staking), Solana program `zauthsTeNbEN69fEmMVm48D2K3cEHJAtf7vnaU2uBeC`); up to 50% off Vector scans for stakers ([Vector docs](https://zauth.inc/docs/vector)).
- Does it do real work? Partly: the scan discount and fee-funded credits are tied to the product. Whether any "protocol revenue" has actually been distributed to stakers is not confirmed. The staking README was edited on 2026-05-21 to "remove dividend terminology" ([commit](https://github.com/zauthofficial/staking/commits/main)), which suggests the team saw a revenue-share wording risk.

### Team
- Founders/leads: not named on the site, docs or llms.txt ([zauth.inc/llms.txt](https://zauth.inc/llms.txt)). Blog bylines are first names only: "Will" (pivot post) and "Dylan" (2.74x post) ([blog index](https://zauth.inc/blog)). Anonymous/pseudonymous. I did not try to identify anyone. Caution: LinkedIn's `company/zauth` page belongs to an unrelated UAE company (a zero-knowledge OAuth alternative); I found no LinkedIn page for this Zauth.
- X: project handle @zauthinc (linked in site footer, set as `twitter_username` on the GitHub account, and in DexScreener socials). Confidence high for the project; none found for individuals.
- GitHub: `zauthofficial` (user account created 2025-10-20; bio "Trust infrastructure for the autonomous economy"; blog zauth.inc; company "zauth") ([profile](https://github.com/zauthofficial)). Verified because the npm package `@zauthx402/sdk` points to its repo and homepage, and the profile links zauth.inc and @zauthinc. It is the only contributor (27 commits) on zauthSDK. npm publisher user is `zpointz` (npm username only; no public tie found).
- Caution: `zauthofficial/reposcan-demo` shows commits "by" vbuterin, samczsun, gakonst, aeyakovenko and others; the repo description says "Bunch of super legit real people" - it is a RepoScan demo of spoofed authors, not a team list ([repo](https://github.com/zauthofficial/reposcan-demo)).

### Track record and pivots
- 2025-10-20: GitHub account created. 2025-12-09: first PumpSwap pair for $ZAUTH.
- 2026-01-20/21: zauthSDK first commit and initial upload; 19 commits in Jan, 8 in Feb, last 2026-02-11 ([commits](https://github.com/zauthofficial/zauthSDK/commits/main)). npm `@zauthx402/sdk` 0.1.14 on 2026-02-11, CLI 0.1.1 on 2026-02-16 ([npm registry](https://registry.npmjs.org/@zauthx402/sdk)).
- 2026-02-03: listed on x402.org's ecosystem page under Infrastructure & Tooling ([ecosystem entry](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/zauth); commit date 2026-02-03).
- About 2026-02-14: an X post by @pumpspotlight, linked from the Zauth homepage banner "Winner of pump.fun's $3M hackathon" (post date decoded from its ID; I could not read the post) ([homepage](https://zauth.inc)).
- 2026-03-05: dated sample Vector report ([Vector docs](https://zauth.inc/docs/vector)). 2026-05-20/21: staking contract published. 2026-07-28: pivot post. 2026-09-10 and 2026-10-04: first security advisories.
- Earlier projects of the team: none traceable.

### Trend-hopping score: 4
Within roughly nine months it went from an x402 endpoint registry (the hot topic of late 2025) with a pump.fun token, to a hackathon claim, to a general AI-code security company (the next hot topic). The products are real each time (SDK, advisories with named upstream projects, benchmark PDFs), so it is not a 5, but the founders say themselves that x402 "stopped being the whole company". Note the token is still named "zauthx402" while the brand dropped x402 from its domain.

### Funding
No VC round found. Claimed Pump Fund backing as a hackathon winner; pump.fun's "Build in Public" hackathon had a $3M pool, 12 winners, $250,000 each, reportedly at a $10M valuation (applications opened 2026-01-19) ([OneKey summary citing crypto.news](https://onekey.so/blog/ecosystem/how-to-capture-opportunities-in-the-pumpfun-hackathon-20260128125336)). Whether Zauth received that exact amount is not confirmed; the winners list at hackathon.pump.fun was not fetchable. Revenue signals: Vector is priced per scan ($49 blackbox, $150 whitebox) ([Vector docs](https://zauth.inc/docs/vector)); Trustpilot shows 9 reviews, 4.6 (self-displayed).

### Product and traction
- Live: Vector (blackbox/whitebox AI pentest, credit-based), RepoScan (repo originality/trust score; browser overlay claimed for Axiom, GMGN and others), Provider Hub + Database, staking, security advisories page ([homepage](https://zauth.inc)). Compliance claims "GDPR aligned, SOC 2 Type II in progress, ISO 27001 in audit" are self-reported.
- Traction numbers: Provider Hub stats on the site are blank; no endpoint or payment counts published. npm downloads 2026-09-10 to 2026-10-09: SDK 257, CLI 12 ([npm downloads API](https://api.npmjs.org/downloads/point/last-month/@zauthx402/sdk)). zauthSDK has 8 GitHub stars. x402scan shows no seller activity because Zauth does not sell via x402 there.

### Last six months (2026-04-11 to 2026-10-11)
- 2026-05-20/21: staking program open-sourced, 7 commits, reproducible-build notes added ([commits](https://github.com/zauthofficial/staking/commits/main)).
- 2026-05 (date from file name): "MayBenchmarkSummary.pdf" Vector benchmark on zauth.inc/research ([homepage links](https://zauth.inc)).
- 2026-05-27: `reposcan-demo` repo created.
- 2026-07-24 and 2026-10-05: new Meteora and Orca pools for $ZAUTH appear on DexScreener (liquidity housekeeping, not product).
- 2026-07-28: two blog posts: the pivot post and "The 2.74x problem" ([blog](https://zauth.inc/blog)).
- 2026-09-10: advisories on IndexedEx/Down To Finance vault shares (Uniswap v3/v4 exchange vaults) and ProFTPD mod_sql; 2026-10-04: advisory on DragonflyDB <= 2.0.0 ([advisories](https://zauth.inc/blog/advisories)).
- Public GitHub commits per month Apr-Oct: 0, 7, 0, 0, 0, 0, 0; last real public commit 2026-05-21 (staking), last SDK commit 2026-02-11. Releases: none on GitHub; no npm publishes after 2026-02-16. Active public contributors: 1 (`zauthofficial`). Team joins/departures: none public.

### Pace verdict
On public evidence the x402 tooling has stalled: 7 commits in six months and no package release since mid-February is far below the monthly-release, weekly-commit pace a small AI-assisted team can reach in 2026, and far below BlockRun (daily releases, section 5). The company is not idle: it has shipped three third-party security advisories in four weeks and a benchmark program, but that work sits in private code. For anyone following x402 trust tooling specifically, treat Zauth as stalled.

### Direction
Stated: "Cybersecurity for everyone", Vector at flat per-scan prices, compliance certifications, staking discounts; x402 registry "still running and supported" ([blog](https://zauth.inc/blog/endpoints-to-industry)). Shipping record agrees with the first part and contradicts any promise of x402 growth: nothing x402-specific has shipped since February 2026.

### Competitors
x402 endpoint verification/trust: x402station.io (1 USDC 30-day provider certificate), Crest `verify` CLI (signed trust receipts), x402-validator (PyPI), anchor-x402, "X402 Trust Layer" (mcp.so), MerchantGuard (GuardScore), DJD Agent Score, PEAC Protocol receipts, OMATrust ([x402 ecosystem entries](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data); search snippets for x402station, Crest and anchor-x402 seen 2026-10-11). I could not establish who is ahead; none has visible usage. Coinbase's Bazaar/agentic.market are platform-layer discovery (excluded from scope).

### Green and red flags
Green: real, dated security advisories naming upstream projects; open-source staking program with reproducible-build instructions; plain-spoken pivot post; concrete scan prices; Pump Fund tag on CoinGecko.
Red: anonymous team; token-funded business; x402 side quiet since Feb; unverifiable headline claims ("4.7x more real vulnerabilities", SOC 2/ISO "in progress/in audit", hackathon win via a third-party X post); staking "dividends" wording; Provider Hub shows no numbers; scan pricing is described inconsistently (a "hundred dollar scan" in the pivot post, $49/$150 in the docs, "$20" in a Trustpilot review snippet); spoofed-author demo repo could be mistaken for a team.

### Verdict
Credible but small (as a security vendor); Speculative if you only care about x402 trust. Momentum: Steady for the company, Stalled for the x402 piece. My read: the team found that scanning x402 endpoints surfaced a bigger market in AI-generated app security and followed it, funded by token fees and Pump Fund attention. Expect the x402 registry to be maintained but not extended; follow Zauth for its security advisories, not for x402 news.

### Tracking card
- Website https://zauth.inc (alias zauthx402.com); docs https://zauth.inc/docs; blog https://zauth.inc/blog (no RSS found); advisories https://zauth.inc/blog/advisories; changelog: none; GitHub Atom feeds https://github.com/zauthofficial/zauthSDK/commits/main.atom and https://github.com/zauthofficial/staking/commits/main.atom.
- GitHub https://github.com/zauthofficial (repos zauthSDK, staking, agent-skills; forks x402 and openclaw). npm `@zauthx402/sdk`, `@zauthx402/cli`, `@zauthx402/openclaw-x402`.
- X @zauthinc; Discord https://discord.gg/CTTB7TmKjv; Telegram: none found; Farcaster: none found.
- Token mint (Solana) `DNhQZ1CE9qZ2FNrVhsCXwQJ2vZG8ufZkcYakTS5Jpump`; staking program `zauthsTeNbEN69fEmMVm48D2K3cEHJAtf7vnaU2uBeC`; Base contract: none.
- x402scan: no origin or facilitator ID. Dune: none found.

### Sources
zauth.inc pages and docs (URLs inline above); [GitHub API zauthofficial](https://api.github.com/users/zauthofficial); [npm registry](https://registry.npmjs.org/@zauthx402/sdk); [CoinGecko](https://www.coingecko.com/en/coins/zauthx402); [DexScreener](https://api.dexscreener.com/latest/dex/search?q=ZAUTH); [OneKey](https://onekey.so/blog/ecosystem/how-to-capture-opportunities-in-the-pumpfun-hackathon-20260128125336). All accessed 2026-10-11.

---

## 2. Cred Protocol (credprotocol.com)

### One-line
A five-year-old onchain credit-scoring company (wallet scores 300-1000 for lenders, DAOs and wallets) that since January 2026 also sells the same scores, reports and sybil checks to AI agents per request through x402 (and MPP), plus an MCP toolkit, SDKs and an ERC-8004 "validator" agent. The lead is right on the product but overstates x402: the x402 channel has earned under one dollar on Base.

### x402 role
Seller/resource server (pay-per-call API) and trust/identity provider (credit score, identity attestations, sybil detection, ERC-8004 validation). Uses Coinbase's CDP facilitator on Base ([blog 2026-01-21](https://credprotocol.com/blog/x402-payments-credit-api)). Not a facilitator.

### Chains
Base mainnet is the original x402 chain (USDC, CDP facilitator); SKALE Base added 2026-03-03; Tempo and Stripe-on-Tempo via the Machine Payments Protocol (MPP) ([payments guide](https://docs.credprotocol.com/guides/payments.md); [SKALE post](https://credprotocol.com/blog/x402-skale-mainnet)). A live 402 challenge lists the same payTo address `0x2B2D0DE9a8d1747b6eEDE6d34F4C12F6590E914b` on Base, SKALE Base and Tempo, plus testnets ([challenge](https://api.credprotocol.com/api/v2/score/address/vitalik.eth)). Scoring covers 10 EVM chains, with Base at "Full" coverage ([chains doc](https://docs.credprotocol.com/chains-and-protocols.md)). Base is primary for x402 and the ERC-8004 validator, but not exclusive.

### Token
None found. The site, 16-post blog and docs do not mention a token ([blog](https://credprotocol.com/blog)). CoinGecko was not checked successfully (rate-limited), so "no listed token" is not confirmed.

### Team
- Julian Gay, CEO: named as CEO in [Cointelegraph, 2022-07-15](https://cointelegraph.com/news/cred-protocol-unveils-its-first-decentralized-credit-scores) (team of nine, San Francisco with New York and London hubs) and the byline on all 2026 blog posts I opened. npm user `julian_cred` publishes the `@cred-protocol/*` packages ([npm](https://registry.npmjs.org/@cred-protocol/sdk)). Doxxed. Personal X handle: not found. GitHub `juliangay` has the same name but only forks and no Cred link, so I do not treat it as verified.
- Others: the LinkedIn company page shows 2-10 employees (3 listed), San Francisco, founded 2021, and names Julian Gay and Aaron Henry (titles not shown) ([LinkedIn](https://www.linkedin.com/company/credprotocol/)); Aaron Henry's role is unconfirmed. The careers page says engineers and operators come from Deutsche Bank, AppDirect and other crypto projects, and that the company is remote-first and small ([careers](https://credprotocol.com/careers)).
- Company handles: X @cred_protocol, GitHub `credprotocol` (org created 2021-08-09; both linked from the homepage), LinkedIn linkedin.com/company/credprotocol.

### Track record and pivots
- 2021-08: GitHub org created. 2022-01-12: Prezenti grant. 2022-07-07: Cred Score v1.0.0 (ML on Aave health factors); Cointelegraph coverage 2022-07-15. 2023: Celo (May), Quadrata identity partnership (Nov). Dec 2024: "Andromeda 1.0" model across 10 networks ([release notes](https://docs.credprotocol.com/model-release-notes.md); [blog index](https://credprotocol.com/blog)).
- 2026-01-09 MCP Services; 2026-01-21 x402 on Base; 2026-02-19 sybil detection; 2026-02-24 ERC-8004; 2026-03-03 x402 on SKALE; 2026-03-16 "Stripe Meets x402"; 2026-03-19 MPP integration; 2026-03-25 ERC-8004 validator registered on Base (agent #36785); 2026-03-31 21 MCP tools; 2026-08-18 SDKs; September 2026 Andromeda 1.1 and 1.2.
- Pattern: same core data product, repackaged for each machine-payment narrative as it appeared. Not a change of business.

### Trend-hopping score: 2
Long-running focus on credit scoring; the agent/x402/ERC-8004/MPP layer is a natural extension of selling an API to machines. The deduction: the blog tracks every payment-rail headline (Stripe, Tempo, MPP) in rapid succession, while demand did not follow.

### Funding
Investors named by the company: DCG, Volt Capital, Alliance, Robot Ventures, Orange DAO ([homepage](https://credprotocol.com); [careers](https://credprotocol.com/careers)). Cred's Notion job-description pages (seen in a search snippet, [example](https://credprotocol.notion.site/Data-Engineer-c14bc912514b48abbcd5a27ea8006ae3)) give a longer list: AllianceDAO, Volt Capital, Robot Ventures, GSR Markets, DCG Expeditions, SNZ Holding, AngelDAO, imToken. Grant: Prezenti, 2022-01-12. Round dates, sizes and leads: not found (Crunchbase and CryptoRank returned 403).

### Product and traction
- Live: REST API v2 (score, enhanced score, reports, sybil, identity, agent registry reads), sandbox, MCP server (21 tools), TS/Python SDKs plus Express/Hono/Next.js middleware, ERC-8004 validator at validator.credprotocol.com ($0.05) ([docs index](https://docs.credprotocol.com/llms.txt)). Prices: 1 credit unit = $0.01 (score), $0.07 full report, $0.05 summary, $0.03 sybil.
- Claims: homepage "300M+ scorable addresses, 10 blockchains, 30+ lending protocols"; docs list 2 lending protocols (Aave, Compound) in 6 deployments, with Morpho, Spark, Euler and others "coming soon" - a mismatch ([chains doc](https://docs.credprotocol.com/chains-and-protocols.md)). A SKALE announcement (March 2026) reportedly claims 350,000+ score requests; I only saw this in a search snippet and the page returned HTTP 429, so it is unverified.
- On-chain x402 traction (Base, payTo above): 44 transactions, $0.88 total, 4 buyers, 2026-01-16 to 2026-10-08; last 30 days 3 transactions, $0.09 ([x402scan tRPC `public.stats.overall`](https://www.x402scan.com/api/trpc/public.stats.overall), queried 2026-10-11). This excludes SKALE and Tempo.
- ERC-8004 validator agent #36785 on Base: registered 2026-03-25, "Inactive", last activity 2026-05-05, 6 feedback entries from 2 clients (only 1 counted), 0 validations ([Quicknode explorer](https://erc-8004.quicknode.com/agents/base-mainnet/36785)). npm `@cred-protocol/sdk`: 30 downloads in the 30 days to 2026-10-09. A third-party agent-readiness scan dated 2026-05-24 graded the site F (38/100) (search snippet, [StartupHub](https://www.startuphub.ai/agent-ready-index/cred-protocol)).

### Last six months
- Base x402 payments: 2026-04-07 (2), 2026-08-16 (1), 2026-10-08 (3): six transactions, $0.12, one buyer each time (almost certainly tests).
- 2026-05-05: last on-chain activity of the validator agent.
- 2026-08-18: SDKs 0.1.0 on npm (four packages) and PyPI (`cred-protocol`), plus blog post ([post](https://credprotocol.com/blog/cred-protocol-sdks-typescript-python-trust-gates)). The SDK source repo `credprotocol/cred-sdk` is not public.
- September 2026: Andromeda 1.1 (Aave repayment/liquidation history) and 1.2 (Compound) in release notes; no entries April-August ([release notes](https://docs.credprotocol.com/model-release-notes.md)).
- Blog posts: ten between 2026-01-09 and 2026-03-31, one (2026-08-18) since. Public GitHub org: last push 2024-02-16, so zero public commits or releases in the window (the SDK repo is private). Team joins/departures: none found.

### Pace verdict
Slow. After a burst of ten posts in Q1, the visible record for the window is one SDK drop, two model updates and one blog post. Compared with BlockRun (releases most days) or Laso (docs updated weekly), Cred looks like a small team shipping in bursts. The x402 line is effectively unused.

### Direction
Stated: be the "trust layer" for agent economies - ERC-8004 scoring, MCP, trust-gate middleware, and MPP credit for high-reputation agents ([MPP post](https://credprotocol.com/blog/mpp-tempo-mainnet-agentic-credit)). The record shows delivery on tooling, none on demand.

### Competitors
Helixa Cred (0-100 agent reputation on Base), DJD Agent Score, MerchantGuard GuardScore, ClawLens, Vaaya (credit accounts for agents), Floe Labs and Credifi (Base Batches 003 credit teams, [Base](https://www.base.org/batches)), plus ERC-8004 reputation registries. Cred has the longest data history and named investors; none of them shows real x402 revenue.

### Green and red flags
Green: named CEO; five years of dated model release notes; solid docs, OpenAPI and sandbox; institutional backers; honest per-call prices.
Red: x402 revenue about zero; homepage coverage claims exceed the docs; validator inactive since May; SDK source private; blog chases each payments headline; x402 not listed on the official x402.org ecosystem page (no slug found).

### Verdict
Credible but small; momentum Slowing. This is a real credit-data business bolting machine-payment rails onto an existing API. It will probably keep shipping model and SDK updates, but agents are not buying scores through x402 yet. Worth a monthly check, not a daily one.

### Tracking card
- Site https://credprotocol.com; docs https://docs.credprotocol.com (llms.txt available); blog https://credprotocol.com/blog; changelog = [model release notes](https://docs.credprotocol.com/model-release-notes.md); OpenAPI https://api.credprotocol.com/openapi.json.
- GitHub https://github.com/credprotocol (dormant); npm `@cred-protocol/sdk|express|hono|nextjs`; PyPI `cred-protocol`.
- X @cred_protocol; Discord https://discord.gg/credprotocol (homepage) and https://discord.gg/MtDHUX9mD6 (docs); LinkedIn company page; Farcaster/Telegram: none found.
- x402: payTo `0x2B2D0DE9a8d1747b6eEDE6d34F4C12F6590E914b` (https://www.x402scan.com/recipient/0x2b2d0de9a8d1747b6eede6d34f4c12f6590e914b); validator wallet `0xc38947DA1EB4466D17d5C6c34a0f26Dbe803d107`; ERC-8004 agent #36785 (Base). Facilitator on x402scan: coinbase. No x402scan origin. Dune: none found.

### Sources
credprotocol.com blog and pages (inline); docs.credprotocol.com pages (inline); [Cointelegraph 2022-07-15](https://cointelegraph.com/news/cred-protocol-unveils-its-first-decentralized-credit-scores); [Quicknode ERC-8004 explorer](https://erc-8004.quicknode.com/agents/base-mainnet/36785); [npm](https://registry.npmjs.org/@cred-protocol/sdk); [PyPI](https://pypi.org/pypi/cred-protocol/json); x402scan tRPC. All accessed 2026-10-11.


---

## 3. Snack Money (snack.money)

### One-line
An API, CLI and Farcaster mini app for sending USDC to people by social handle (X, Farcaster, GitHub, email, web domain, Instagram), with x402 as the payment rail for apps and agents ([docs overview](https://docs.snack.money/introduction/overview)). The lead is correct about the idea, but as of 2026-10-11 the project looks dormant or offline: no x402 payment since 2025-12-04, last public post 2026-01-10, website returning HTTP 500, API host returning 404.

### x402 role
Seller/resource server (a payments API gated by x402) plus SDK/tooling (CLI, examples for x402-axios, x402-fetch, CDP SDK, thirdweb, Crossmint) and A2A/MCP endpoints ([docs index](https://docs.snack.money/llms.txt)). Listed on x402.org's ecosystem page as "Snack Money API" (commit date 2025-08-15, [entry](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/snackoney)).

### Chains
Docs say USDC on Base and Solana ([overview](https://docs.snack.money/introduction/overview)). x402scan shows 100% of its recorded x402 payments on Base, none on Solana ([x402scan tRPC `public.stats.overallByOrigin`](https://www.x402scan.com/api/trpc/public.stats.overallByOrigin), origin `bfc2db15-9ceb-40a3-8c2b-6604c32c162b`). Base primary.

### Token
- Ticker "snackmoney" / SNACKMONEY, Base, `0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d`. It is a Zora creator coin: Zora's API returns type CREATOR, supply 1,000,000,000, created 2025-07-27 16:00 UTC, paired against ZORA, and the Farcaster profile links zora.co/snackmoney ([Zora SDK API](https://api-sdk.zora.engineering/coin?address=0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d&chain=8453); [Farcaster profile API](https://api.warpcast.com/v2/user-by-username?username=snackmoney)). Contract is a 45-byte minimal proxy, consistent with a factory clone ([Base RPC `eth_getCode`](https://mainnet.base.org)).
- Stated utility: none found in docs or site. Does it do real work? No evidence. CoinGecko says the coin "stopped trading" on all listed exchanges, and DexScreener returns no pairs ([CoinGecko](https://www.coingecko.com/en/coins/snackmoney); [DexScreener](https://api.dexscreener.com/latest/dex/tokens/0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d)). Created three months after the Farcaster bot and about three weeks before the x402.org listing, so it reads as a profile coin created alongside the product, not a TGE.

### Team
- No team page, no founder named in docs, site or the x402 listing. The official Farcaster account's first casts (2025-04-28) are tip receipts that tag `@mesut` as a recipient, and `@mesut` (FID 248052) has the bio "Building @snacmoney" with a connected X account `0xmesuthere` ([Farcaster API](https://api.warpcast.com/v2/user-by-username?username=mesut)). That is a self-declaration by the person, with a typo in the project handle, so confidence is medium that he works on Snack Money; his role is unconfirmed. First name only is public; I did not look further.
- Project handles: X @snackmoneyapp (linked from docs and shown as the Farcaster account's connected X account), Farcaster `@snackmoney` (FID 1046136, 24 followers), GitHub org `snack-money` (created 2019-05-25, zero public repos), npm package `snackmoney` (published by a GitHub Actions workflow from `snack-money/snackmoney-cli`, which is not public) ([npm](https://registry.npmjs.org/snackmoney)). Pseudonymous.

### Track record and pivots
- 2025-04-28: official Farcaster account posts emoji-tip receipts (a Farcaster tipping bot). 2025-06-02: first x402 payments recorded to the project's payTo address on Base. 2025-07-27: Zora creator coin created. 2025-08-15: x402.org listing. 2025-10-15: origin registered on x402scan. 2025-11-15: CLI v1.1.1 announced; 21 npm versions, last 1.2.0 on 2025-12-23. 2025-12-04: last x402 payment seen. 2026-01-10: last cast ("Snack Agents are cooking! See [ERC-]8004 registration card") ([casts](https://client.farcaster.xyz/v2/profile-casts?fid=1046136&limit=10)).
- Earlier projects of the team: none traceable.

### Trend-hopping score: 3
One constant idea (pay a person by handle) wrapped in each fashionable layer in turn: Farcaster tipping (April 2025), a Zora creator coin (July 2025), x402 (August 2025), Base App/mini apps, A2A/MCP and ERC-8004 agents (late 2025 to January 2026). The product was real each time (bot, API, CLI) but the layers came faster than usage.

### Funding
No evidence of outside funding found.

### Product and traction
- All-time x402 on Base: 654 transactions, $154.92, 26 unique buyers, 2025-06-02 to 2025-12-04; $142 of the $155 arrived in November 2025 ([x402scan](https://www.x402scan.com/server/bfc2db15-9ceb-40a3-8c2b-6604c32c162b), queried 2026-10-11). Monthly transactions: Jun 2025 35, Jul 30, Aug 169, Sep 49, Oct 166, Nov 166, Dec 39, then zero.
- npm `snackmoney`: 56 downloads in the 30 days to 2026-10-09. Farcaster followers: 29 on 2025-12-02 (cast), 24 now.
- Liveness on 2026-10-11: `snack.money` returns HTTP 500 (generic server-error page) from both curl and WebFetch; `api.snack.money` (CNAME to a Firebase Hosting site) returns 404 for `/openapi.json` and the documented `/payments/x/pay`; `docs.snack.money` is up ([DNS over HTTPS](https://cloudflare-dns.com/dns-query?name=api.snack.money&type=A)).

### Last six months
Nothing dated inside the window: zero x402 payments, zero npm releases, zero casts, no GitHub commits (no public repos, so no last-commit date), no blog or changelog. The only change visible is the site returning HTTP 500. Team joins/departures: none public.

### Pace verdict
Stalled for roughly ten months. Against a 2026 small-team norm of monthly releases and weekly commits, there is nothing to compare; the product appears to be switched off.

### Direction
Stated: "Snack Agents" on ERC-8004 (final cast 2026-01-10). Shipping record: nothing since. The docs site still describes a working API, which is now contradicted by the 404/500 responses (possible temporary outage not excluded, but the on-chain silence began in December).

### Competitors
Laso Finance (agents pay Venmo/PayPal/bank recipients via x402, [Laso](https://laso.finance)); Bankr and Crossmint (covered by other researchers; Snack's own docs include a Crossmint example); Farcaster/Base App native tipping (my own context, not sourced). Laso is clearly ahead on real usage (section 6).

### Green and red flags
Green: early x402 mover (payments from June 2025); clear idea; clean docs with OpenAPI, CLI and SDK examples.
Red: backend offline; no payments or posts for months; no named team; coin stopped trading; no public code; docs advertise Solana support that never showed up on x402scan.

### Verdict
Likely abandoned; momentum Dead (confidence medium: dormancy is certain, deliberate shutdown is not). A product that raised no visible money, never passed 26 paying wallets, and went silent in January 2026. Follow only as a cautionary example of a profile-coin plus x402 launch that stopped.

### Tracking card
- Site https://snack.money (HTTP 500); docs https://docs.snack.money; API https://api.snack.money (404); x402.org entry above.
- GitHub org https://github.com/snack-money (empty); npm `snackmoney`.
- X @snackmoneyapp; Farcaster @snackmoney (FID 1046136); Farcaster mini app via bio link; Zora https://zora.co/snackmoney.
- Token `0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d` (Base).
- x402scan server `bfc2db15-9ceb-40a3-8c2b-6604c32c162b`; payTo `0x1223d566f05ea54e5854434c4552c9f5c2259e0f`; facilitators seen: coinbase, payAI, x402rs. Dune: none found.

### Sources
docs.snack.money pages; [x402scan tRPC](https://www.x402scan.com/api/trpc/public.stats.bucketedByOrigin); [Zora SDK API](https://api-sdk.zora.engineering/coin?address=0x69e77dd1f50e2ea1c324a9ae96dd2ba7be08849d&chain=8453); [CoinGecko](https://www.coingecko.com/en/coins/snackmoney); [npm registry](https://registry.npmjs.org/snackmoney); Farcaster APIs (inline); Cloudflare DNS over HTTPS. All accessed 2026-10-11.

---

## 4. Fluora (fluora.ai, Fluora Inc.)

### One-line
A "peer-to-peer marketplace where AI agents can discover and purchase resources and services programmatically", built on the MonetizedMCP spec and x402, with a buyer-side `fluora-mcp` server that creates a USDC wallet on Base ([fluora.ai](https://www.fluora.ai); [README](https://github.com/fluora-ai/fluora-mcp)). The lead is confirmed as to intent, but the marketplace backend host `api.fluora.ai` no longer resolves to a live service, the site still says "developer preview", and the company now promotes an unrelated wellness-travel product (Kula).

### x402 role
Discovery marketplace plus buyer agent client (the MCP server) and seller-side proxy. Listed on x402.org's ecosystem under Infrastructure & Tooling (added 2025-08-29, updated 2025-10-16, [entry](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/fluora)).

### Chains
USDC on Base mainnet and Base Sepolia only, with wallets auto-generated in `~/.fluora/wallets.json` ([README](https://github.com/fluora-ai/fluora-mcp)). Base primary, effectively sole.

### Token
None found. Neither the site nor the repos mention one. A Bitget dApp page for "Fluora" mentions funding rounds and an ICO/airdrop, but the same page also calls Fluora a digital-art and collectibles platform, so it is an unreliable aggregator listing, not evidence ([Bitget listing](https://web3.bitget.com/es/dapp/fluora-31649), seen in a search result).

### Team
- Chetan Nandakumar, founder and CEO: named in a podcast interview dated 2025-06-27 that lists UC Berkeley training, co-founder of Modista (computer-vision apparel discovery) and VP of Products at Gensyn ([episode page](https://gregoryandpaulshow.castos.com/episodes/ai-agents-are-secretly-running-your-business-with-guest-chetan-nandakumar)). GitHub `chetan-guevara` has the profile name "Chetan Nandakumar" and committed under that name to `fluora-ai/fluora-mcp` and `MonetizedMCP/typescript-sdk` ([profile](https://github.com/chetan-guevara)). Doxxed; X handle not found.
- Engineers visible in public commits (apparently outside agencies; inference from the npm maintainer domains strivelabs.io, joinplank.com and uklok.cloud, not stated by Fluora): `yunkailin10` ("Yunkai", 33 commits in typescript-sdk, 22 in core), `GuilhermeSantosPlank` (34 commits in typescript-sdk), `yonathan9669` ("Yonathan Morales", 19 in core, company field "UKLOK") ([contributors API](https://api.github.com/repos/fluora-ai/core/contributors)). None sets an X handle on GitHub. The February 2026 commits also show an author named "molty", probably an AI assistant (unconfirmed), whose changes were reverted.
- No X, Discord or Farcaster account is linked from fluora.ai or the GitHub org. The company's LinkedIn page (tagline "Agent-To-Tool Marketplace", website fluora.ai, 2-10 employees, no staff names shown) exists ([LinkedIn](https://www.linkedin.com/company/fluora/)); a different "Fluora AI" page about cold-email automation is unrelated.

### Track record and pivots
- 2025-04-05: `MonetizedMCP` GitHub org and TypeScript SDK created (77 commits April-September 2025; last push 2025-09-17). 2025-05-05: `fluora-ai` org created. 2025-06-27: podcast, "private beta with partners". 2025-07 to 2025-09: `fluora-ai/core` built (22, 16 and 3 commits); v0.1.2 on 2025-08-08, v0.1.3 on 2025-09-22; `agentkit-fluora-example` built on Coinbase AgentKit (Jul-Aug 2025). 2025-08-29: x402.org listing. 2025-09-12 to 2025-09-19: `fluora-mcp` npm 0.1.35 to 0.1.38 (38 versions in total).
- 2026-02-10/11: new `fluora-ai/fluora-mcp` repo with 14 commits, OpenClaw setup instructions, reverts. Undated: Kula (Bali wellness travel, waitlist) added to the site.
- Earlier projects of the CEO: Modista, Gensyn (dates not found).

### Trend-hopping score: 3
Real, early work on MCP monetization (April 2025) and x402 (August 2025), then an OpenClaw-style setup in February 2026 and a Bali wellness-travel product that has nothing to do with agents. The marketplace product was real; the later moves look like drift.

### Funding
No evidence of outside funding found (podcast mentions none; Crunchbase returned 403). Treat the Bitget claims as noise.

### Product and traction
- README claims 76+ listed services (undated); the site's services page shows none to a text fetch; the site says "developer preview" ([fluora.ai](https://www.fluora.ai/how-it-works)).
- No x402scan origin for Fluora, so no visible on-chain marketplace usage ([x402scan origin search](https://www.x402scan.com/api/trpc/public.origins.search), "fluora" and "monetized" returned nothing).
- npm downloads 2026-09-10 to 2026-10-09: `fluora-mcp` 106, `@fluora-ai/core` 16; GitHub stars 0-1 on the main repos.
- Liveness 2026-10-11: the MCP server's default API `https://api.fluora.ai/api` is a CNAME to an AWS App Runner hostname that no longer resolves (NXDOMAIN on DNS-over-HTTPS and local DNS), so the proxy marketplace that the MCP server calls is down. fluora.ai itself is still served from Vercel ([DoH query](https://cloudflare-dns.com/dns-query?name=api.fluora.ai&type=A); [constants.ts](https://github.com/fluora-ai/fluora-mcp/blob/main/src/utils/constants.ts)).

### Last six months
Nothing inside the window on the project's public footprint: no commits (last public commit 2026-02-11), no releases, no npm publishes (last 2025-09-22), no blog. The CEO's personal GitHub shows forks of agent-tooling repos (2026-03-26, 2026-07-03), not Fluora work. Team joins/departures: none public.

### Pace verdict
Stalled. Zero commits and releases in six months, against a norm of monthly releases and weekly commits for AI-assisted small teams, and against BlockRun's daily releases. The deleted backend is the strongest signal.

### Direction
Stated: "currently in developer preview", "actively iterating", Kula "launching soon" ([site](https://www.fluora.ai)). Shipping record shows no iteration; Kula has a waitlist but no date.

### Competitors
Coinbase CDP Bazaar and Agentic.Market (platform layer, excluded), Circle's Agent Marketplace (lists 600+ live x402 services, [Circle](https://developers.circle.com/agent-stack/agent-marketplace)), Merit Systems' AgentCash, MCPay, ATXP, and open-source MCP monetization kits such as XPack-MCP-Marketplace (173 GitHub stars). The platform players are far ahead.

### Green and red flags
Green: early and genuine MonetizedMCP/x402 work; named CEO with a credible background; clean buyer-side install flow.
Red: deleted backend; no commits since February; contractor-built codebase; no social presence; Kula pivot; a third-party listing using the Fluora name makes funding/ICO claims that nothing official supports.

### Verdict
Likely abandoned (as an x402 marketplace); momentum Stalled. It was a legitimate early attempt that never found sellers or buyers on-chain and whose backend has been taken down. Do not follow it daily; revisit only if the CEO announces a relaunch.

### Tracking card
- Site https://www.fluora.ai (/how-it-works, /getting-started, /kula, /submit); MonetizedMCP spec site https://monetizedmcp.org (fetch failed); no blog or changelog found.
- GitHub https://github.com/fluora-ai (fluora-mcp, core, agentkit-fluora-example) and https://github.com/MonetizedMCP (typescript-sdk, monetized-mcp-sample, starter-kit-template). npm `fluora-mcp`, `@fluora-ai/core`.
- X, Farcaster, Discord, Telegram: none found. Token: none. x402scan: no origin. Dune: none found.

### Sources
[fluora.ai](https://www.fluora.ai); [fluora-mcp README](https://github.com/fluora-ai/fluora-mcp); GitHub API for `fluora-ai` and `MonetizedMCP`; [npm registry](https://registry.npmjs.org/fluora-mcp); [podcast page](https://gregoryandpaulshow.castos.com/episodes/ai-agents-are-secretly-running-your-business-with-guest-chetan-nandakumar); [x402 ecosystem entry](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/fluora). All accessed 2026-10-11.


---

## 5. BlockRun (blockrun.ai, BlockRun, Inc.)

### One-line
A pay-per-call gateway for AI: one endpoint for 100+ LLMs plus image, video, music, voice, search and market-data APIs, where each request gets an HTTP 402 price quote and is settled in USDC on Base or Solana with no account or API key ([blockrun.ai](https://blockrun.ai)). Around it sits an open-source router (ClawRouter), an MCP server and an "agent with a wallet" (Franklin). Not in the leads; it is the strongest builder among the "other" apps.

### x402 role
Seller/resource server (the gateway) and payment router, plus SDK/tooling (Python, TypeScript, Go SDKs; ClawRouter; MCP) and buyer-side agent client (Franklin). Listed on x402.org's ecosystem as "BlockRun.AI" (added 2026-01-19, [entry](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/blockrun)).

### Chains
Base and Solana. "x402 LLM gateway live on Base mainnet" in January 2026, Solana added February 2026 ([About](https://blockrun.ai/about)). ClawRouter's README says new installs default to Solana while older installs keep a Base wallet ([README](https://github.com/BlockRunAI/ClawRouter)). So Base is where its on-chain history started (January-August 2026), but from late August the heavy traffic ran on Solana: x402scan's `sol.blockrun.ai` origin shows 11.8M transactions ($173.5k) in August and 10.5M ($113.4k) in September, against 0.2M on Base in September; the changelog says five free models were served on Solana from 2026-09-07 and Base reached parity on 2026-10-02 ([changelog](https://blockrun.ai/changelog); [x402scan tRPC `public.stats.bucketedByOrigin`](https://www.x402scan.com/api/trpc/public.stats.bucketedByOrigin), origin `239470e8-8384-4783-8448-b7365d80fc43`). Base is no longer its main chain by volume.

### Token
No official token. The About page, site and README mention none ([About](https://blockrun.ai/about)). Warning: DexScreener lists a Solana pump.fun token "BRUN" named "BlockRunAI" (mint `92QPy1K3yiQfEf6chrq8k1LbXWgsw4sAUQWxuqxupump`, PumpSwap pair) with no website or social links claimed ([DexScreener search](https://api.dexscreener.com/latest/dex/search?q=blockrun)); treat it as unofficial unless BlockRun says otherwise.

### Team
- Vicky Fu, founder: BlockRun's About page names her as Founder, formerly Head of Data Science at Circle, Director of Data Science at Capital One and Azure ML Tech Lead at Microsoft ([About](https://blockrun.ai/about)). HQ San Francisco. Doxxed. Personal X handle not found.
- GitHub `VickyXAI` (profile name "VickyXAI", bio "Web3 Builder") is the org's lead committer (214 commits in blockrun-mcp, 77 in Franklin, 51 in blockrun-llm, 43 in ClawRouter). Matching it to Vicky Fu is an inference (first name, role as lead committer); confidence medium ([contributors](https://api.github.com/repos/BlockRunAI/blockrun-mcp/contributors)).
- `KillerQueen-Z` ("Killer Queen"): bio "Building Franklin & ClawRouter @BlockRunAI", company @BlockRunAI; 44 commits in Franklin, 13 in blockrun-mcp. Self-declared engineer; high confidence. No X handle set.
- Other committers: `0xCheetah1` (about 10 commits; no bio), `achiurizo` ("Arthur Chiu", 15 in ClawRouter, X @onlyachiurizo on his GitHub profile), `tenequm` ("Misha Kolesnik", 13, X @opwizardx on his GitHub profile); relation to BlockRun not stated.
- Organisation handles: X @BlockRunAI (site and org profile), GitHub `BlockRunAI` (created 2025-12-21). The LinkedIn company page `blockrunai` shows 2-10 employees (4 listed), founded 2026, and names Rami Djebari, Andy Chen and Emma Hsieh (titles not shown); its address is Miami, FL, whereas the About page says San Francisco ([LinkedIn](https://www.linkedin.com/company/blockrunai/)). A separate "BlockRun Inc." page in Toronto is a different company.

### Track record and pivots
- 2025-12-21: GitHub org created; 2025-12-27 first SDK repos. 2026-01-05: BlockRun, Inc. incorporated (Delaware C-corp) and first x402 origin (blockrun.ai) registered on x402scan. January 2026: Base mainnet gateway live; 2026-01-19 x402.org listing. February 2026: Solana; 2026-02-03 ClawRouter repo created. 2026-03-22: Franklin repo. March 2026: ClawRouter open-sourced; claimed win of the Circle USDC OpenClaw Hackathon (Agentic Commerce track) ([About](https://blockrun.ai/about)). Spring 2026: one of 12 teams in Base Batches 003 ([Base](https://www.base.org/batches)); AX1 lists BlockRunAI as a "Base Batches 003 Winner" ([ax1.vc](https://ax1.vc)).
- Founder's earlier ventures: none found (prior employers only).

### Trend-hopping score: 2
Same core since day one: an x402-priced LLM and API gateway. It rides current fashions at the edges (OpenClaw/Hermes plug-ins, an "awesome-OpenClaw-Money-Maker" list with 363 stars, a Polymarket trading agent) but the paid gateway is the constant, and the code is real.

### Funding
No priced VC round found. BlockRun is listed in the Base Ecosystem Fund portfolio; that fund invests at pre-seed and seed stage in partnership with Coinbase Ventures, and neither fund size nor check size is stated ([Base Ecosystem Fund](https://www.base.org/ecosystem-fund)). It was one of 12 teams in Base Batches 003 (the batches page advertises a $100K Ecosystem Fund investment, but that text is written for Batch 004 and is unconfirmed for 003). Circle hackathon prize claimed, amount not stated. Delaware C-corp since 2026-01-05.

### Product and traction
- Live: gateway (site says 115 models in the hero and 88 LLMs in the filter - inconsistent; the LinkedIn description states a 5% overhead on provider costs), free tier of NVIDIA-hosted models, marketplace APIs (market data, prediction-market data, phone and voice, Surf crypto data), ClawRouter (about 6.6k stars, 653 forks), Franklin (555 stars), blockrun-mcp (391 stars) ([ClawRouter](https://github.com/BlockRunAI/ClawRouter)). 41 public repos, 36 pushed since 2026-04-11.
- Self-reported: "28.9 million transactions settled on-chain" and "#1 in agent payments" on x402scan's 30-day ranking through 2026-10-02 ([site](https://blockrun.ai)). My check of x402scan (Bazaar-registered Base origins, queried 2026-10-11): all-time on its two Base payTo addresses 27.6M transactions, $480,084, 3,847 buyers; last 30 days 82,940 transactions, $1,544, 569 buyers (rank 4 by transactions, 7 by USDC volume) ([x402scan tRPC `public.sellers.bazaar.list`](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list); origin `b85dcf0f-d4a9-47ce-9d0b-6ec70e2844e0`).
- Monthly Base x402 (transactions / USDC): Mar 183k / $11.9k; Apr 93k / $5.5k; May 110k / $2.8k; Jun 10.2M / $117.7k; Jul 9.5M / $163.7k; Aug 6.9M / $156.7k; Sep 213k / $6.0k; Oct 1-11 33k / $0.5k. The June-August bulge is about $0.011 per transaction. Base then fell about 97% in September because the traffic moved to Solana (see Chains); the two chains together went from 10.7M transactions and $119k in September to 189k and $1.5k in 1-11 October, a fall of roughly 95% per day. Solana adds 226,706 transactions and $2,901 to the Base last-30-day figures above.
- Daily now: 1,600-5,100 transactions (one day 10,400) from 40-75 buyers and $28-72 per day (27 Sep to 10 Oct). Concentration: the latest 100 transfers across both payTo addresses came from 4 wallets (67 from one); the 100 largest in the last 30 days came from 13 wallets. Of 27 payers sampled on one of the two payTo addresses, 22 had never sent an on-chain transaction (normal for gasless EIP-3009 payers, so only indicative). Verdict on usage: real but small, bot-heavy; headline transaction counts are not a demand signal.
- Revenue model per the changelog: chat tokens at the provider's list rate plus a flat per-call fee ("currently $0.001" on 2026-08-07; briefly $0.002 until 2026-07-29), and a 5% markup on media and live search; a flat $0.081 per search call since 2026-09-29 ([changelog](https://blockrun.ai/changelog)). At a few thousand calls a day the platform fee is single-digit dollars a day; most of the USDC passing through is pass-through to upstream providers.

### Last six months (2026-04-11 to 2026-10-11)
- ClawRouter: 127 changelog versions in the window (20 in April, 26 May, 17 Jun, 17 Jul, 27 Aug, 18 Sep, 2 Oct), latest v0.12.282 on 2026-10-05 ([CHANGELOG](https://github.com/BlockRunAI/ClawRouter/blob/main/CHANGELOG.md)). Dated highlights: 2026-04-21 market-data tools; 2026-05-03 ten prediction-market endpoints (49-endpoint registry); 2026-05-16 phone and voice APIs; 2026-05-17 Surf crypto data API as a skill-only marketplace API; 2026-05-29 Claude Opus 4.8 flagship; 2026-07-08 site repositioned as "The routing & payment layer for AI" and Marketplace renamed Services; 2026-08-07 chat pricing moved to provider list rate plus a flat per-call fee; 2026-09-07 free models served on Solana; 2026-09-08 ClawRouter desktop preview (`desktop-v0.1.3-preview.1`); 2026-09-29 search moved to a flat per-call price; 2026-10-02 Claude Fable 5.1 and GPT-6 tiers live, 2026-10-09 GPT-6.1 Sol live ([blog feed](https://blockrun.ai/feed.xml)).
- Blog: 12 posts between 2026-08-10 and 2026-10-09, including 2026-09-01 "We Audited Our Own MCP Server. We Failed.".
- GitHub commits per month Apr-Oct 11 (ClawRouter / blockrun-mcp / Franklin / blockrun-llm): Apr 133/61/466/18; May 40/32/190/40; Jun 38/65/68/36; Jul 36/75/64/33; Aug 54/57/39/18; Sep 99/50/65/25; Oct 9/10/50/8. Roughly 1,880 commits across these four repos. GitHub releases from 2026-04-01: ClawRouter 113, blockrun-mcp 61, blockrun-llm 17, Franklin 100+ (API cap; latest v3.49.6, 2026-10-08).
- Contributors (all-time, bots included): ClawRouter 8+, Franklin 8+, blockrun-llm 6, blockrun-mcp 5; the human core is VickyXAI and KillerQueen-Z. Latest commits seen 2026-10-08. Team joins/departures: none announced.

### Pace verdict
Fastest in this study and above what a small AI-assisted team is expected to do: a tagged release most days, weekly blog posts, new frontier models added the day they ship. It beats every other project here by an order of magnitude and compares with the platform players on cadence, though not on distribution.

### Direction
Stated: "the routing & payment layer for AI", agents "pay for the outcome" ([site](https://blockrun.ai)). The shipping record matches: more models and marketplace APIs, SDKs in more languages, a desktop app, an agent runtime (Franklin). The weak point is demand: paid on-chain usage fell about 95% across Base and Solana between September and early October while the feature set kept growing.

### Competitors
Other x402 inference/API gateways on Base: Cluster Protocol (section 7), claw402, Locus (3,960 APIs through one balance); Merit Systems' AgentCash/Echo and Heurist (covered elsewhere); non-crypto LLM routers and gateways (OpenRouter-style services, cloud AI gateways; my own context, not sourced) are the real alternative for most developers. BlockRun is ahead of the other x402-native gateways on shipping and open-source reach.

### Green and red flags
Green: daily open-source releases (MIT); 6.6k-star flagship; named founder with relevant career; public changelog and self-critical blog; free tier with no wallet; Base Batches 003 and Circle hackathon credentials; both Base and Solana support.
Red: transaction counts dominated by a few wallets and a roughly 95% fall in paid volume across both chains between September and early October; an unofficial Solana token using the project name; no disclosed funding; installer via `curl | bash` and a local-wallet design that deserve security care (the OpenClaw skill scanner flagged ClawRouter's SKILL.md as medium-confidence suspicious on 2026-04-20, fixed in v0.12.157/158); self-promotional rank claims; inconsistent model counts on the homepage.

### Verdict
Serious builder; momentum Steady (shipping steady-to-accelerating, paid on-chain usage falling sharply since September). The team behaves like a funded, AI-assisted startup that treats x402 as its billing layer, and it is the one app here with a compounding open-source audience. The open question is revenue: in the last 30 days about $4.5k of USDC crossed x402 on Base ($1.5k) and Solana ($2.9k) together, and the platform keeps a $0.001 per-call fee, which is small for this level of output, so expect the strategy to lean on the card/API-key billing route and on volume from Solana. Follow it daily for what ships; ignore its transaction totals.

### Tracking card
- Site https://blockrun.ai; docs https://blockrun.ai/docs; RSS https://blockrun.ai/feed.xml; changelog https://github.com/BlockRunAI/ClawRouter/blob/main/CHANGELOG.md; release feeds https://github.com/BlockRunAI/ClawRouter/releases.atom, https://github.com/BlockRunAI/blockrun-mcp/releases.atom, https://github.com/BlockRunAI/Franklin/releases.atom.
- GitHub https://github.com/BlockRunAI (ClawRouter, Franklin, blockrun-mcp, blockrun-llm, blockrun-llm-ts, blockrun-llm-go); npm `@blockrun/clawrouter`, `@blockrun/llm`; X @BlockRunAI; Farcaster, Discord, Telegram: none found.
- x402scan origins `b85dcf0f-d4a9-47ce-9d0b-6ec70e2844e0` (blockrun.ai) and `239470e8-8384-4783-8448-b7365d80fc43` (sol.blockrun.ai); Base payTo `0x6e007731870ede419cfb31889cd5c4493cecb04c`, `0xe9030014f5dae217d0a152f02a043567b16c1abf`; facilitator seen: coinbase. Dune: none found.

### Sources
[blockrun.ai](https://blockrun.ai); [About](https://blockrun.ai/about); [feed](https://blockrun.ai/feed.xml); [GitHub API](https://api.github.com/orgs/BlockRunAI/repos); [ClawRouter changelog](https://github.com/BlockRunAI/ClawRouter/blob/main/CHANGELOG.md); [Base Batches](https://www.base.org/batches); [ax1.vc](https://ax1.vc); x402scan tRPC; Base public RPC. All accessed 2026-10-11.

---

## 6. Laso Finance (laso.finance, Laso Finance LLC)

### One-line
A US money-services business that turns stablecoins into prepaid cards, gift cards, push-to-card, Venmo/PayPal payouts and bank payments, and offers agents a payment-gated x402 API and MCP tools to use them ([laso.finance](https://laso.finance)). It is an existing fintech (founded March 2023) that added x402, not an x402-native startup, but its agent API is among the few on Base with organic-looking purchases.

### x402 role
Seller/resource server (fiat rails behind x402 endpoints), with MCP server, agent SKILL file and OpenAPI discovery ([docs](https://docs.laso.finance)). Listed on x402.org (added 2026-02-26, [entry](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/laso-finance)).

### Chains
x402 settlement on Base and Solana; the managed agent wallet is a Laso-custodied Solana wallet ([site](https://laso.finance)). Both chains carry traffic on x402scan, and Solana carries most of the dollars: Solana payTo `3MZVk97x9SeRxbYpc3jhzRfU2fyA3emYutnqfn9kNfYX` shows 272 transactions and $612,817 all-time against $16,077 on Base, but one wallet supplies 99.6% of the Solana dollars (see Product and traction). By counts of distinct customers Base is primary; by dollars Solana is.

### Token
None. The site states products are funded with USDC and names no token.

### Team
- Hunter Maximillion Monk: his personal site has a post dated 2026-06-24 titled "Why I'm building Laso Finance", and he is the main committer and merger on the company's public docs repo (12 commits) ([huntermonk.com](https://huntermonk.com); [contributors](https://api.github.com/repos/LasoFinance/docs/contributors)). His Farcaster bio reads "building LF, sold LiberEx; ex-Meta TL SWE" ([profile](https://api.warpcast.com/v2/user-by-username?username=huntermonk)). X @huntermmonk (set on his GitHub profile and linked from his site); GitHub `huntermonk`. Role (founder or CEO) is not stated; my inference is that he leads the company. Doxxed.
- Other docs-repo contributors with public GitHub profiles: `kmjones1979` ("Kevin J", AI security and payments infrastructure), `0xArtex`, `mikedotexe`, `mohamedkuch`; ties to Laso unconfirmed (could be outside contributors).
- Company handles: X @lasofinance (GitHub org field), LinkedIn company page (2-10 employees, founded 2023, one staff name shown: Denrick James Dela Cruz, title not shown, [LinkedIn](https://www.linkedin.com/company/laso-finance/)), Farcaster `lasofinance` (4 followers; bio "The no-KYC stablecoin prepaid card"), GitHub org `LasoFinance` (created 2026-07-15). Based in Austin, Texas; FinCEN-registered MSB per the about page ([about](https://laso.finance/about)).

### Track record and pivots
March 2023 founded (stablecoin card). 2024-01-30: Hunter Monk's Farcaster cast already talks about "Laso cards" in Warpcast. 2026-02-26: x402.org listing for agents ("no account needed"). 2026-07-15: public GitHub org and docs repo created. 2026-09-21: bug bounty paused indefinitely. 2026-10-03: Hermes Agent plugin repo created. Consistent line: stablecoin to spendable money, now offered to agents. Earlier ventures of the lead: LiberEx (per his Farcaster bio; no dates found).

### Trend-hopping score: 1
Single focus since 2023 (spend stablecoins in the real world); the agent/x402 interface is a natural new front door. Only the "agent" language in 2026 follows the trend.

### Funding
No evidence of outside funding found (the site names none; Crunchbase not reachable). Revenue model is transaction fees: 0% on US prepaid cards ($5-$1,000), 3.8% international cards, 4.8% push-to-card, 4.9% Venmo/PayPal, 0.25% ACH ([site](https://laso.finance)).

### Product and traction
- Live: prepaid cards (US and international), gift cards ($5-$9,000), push-to-card, Venmo/PayPal payouts, ACH, web dashboard and mobile app, x402 API, MCP server (official MCP Registry, Smithery), SKILL.md, OpenAPI 3.1.
- x402scan, Base, payTo `0x3291e96b3bff7ed56e3ca8364273c5b4654b2b37`: all-time 1,427 transactions, $16,077, 283 buyers (first activity March 2026); last 30 days 116 transactions, $1,487, 59 buyers; last 7 days 22 transactions, $553. Monthly USDC volume: Mar $1.3k, Apr $1.1k, May $3.4k, Jun $3.2k, Jul $1.0k, Aug $3.3k, Sep $1.9k, Oct 1-11 $0.55k ([x402scan tRPC](https://www.x402scan.com/api/trpc/public.stats.bucketed)). Daily it is 2-5 transactions. About half of its 116 transfers in the last 30 days are $0.001 calls (63 of the latest 100); the larger ones are mostly $5-$30 orders from over 50 distinct wallets, and of 40 payers sampled 11 had more than 5 on-chain transactions. That is the most organic mix among the Base apps I screened.
- Solana side (x402scan, payTo above): 272 transactions, $612,817, 62 buyers all-time; last 30 days 111 transactions, $267,444, 30 buyers. Monthly: Apr $159, Jul $2.1k, Aug $241.0k, Sep $251.0k, Oct 1-10 $118.5k. One wallet (`9sZEFeQD...k9WXR`) made 103 payments totalling $610,167 (99.6%), 57 of them of $1,000 or more (largest $29,306, mostly non-round amounts); the other 61 wallets paid $2,650 in total ([x402scan tRPC `public.transfers.list`](https://www.x402scan.com/api/trpc/public.transfers.list), chain solana). That looks like one large customer (or a related party) using the $10k+ card-load and bank-payment rails, not broad demand; I could not identify the wallet's owner.

### Last six months
- Docs repo: 39 commits in July, 43 August, 62 September, 19 October (1-11), many from a "laso-docs-sync" bot syncing from a private monorepo; latest 2026-10-09 ([commits](https://api.github.com/repos/LasoFinance/docs/commits)). Hermes plugin repo created 2026-10-03 with 6 commits in October.
- Bug bounty paused since 2026-09-21; agent discovery files (SKILL.md, llms.txt, MCP server card) maintained.
- No tagged releases; no public changelog; latest public commit 2026-10-09 (docs sync bot). Contributors on the docs repo: `huntermonk` (12 commits), four one-commit contributors (`0xArtex`, `kmjones1979`, `mikedotexe`, `mohamedkuch`) and the sync bot. Team joins/departures: none public.

### Pace verdict
Steady and sensible: weekly docs and plugin updates track a private product pipeline. Slower than BlockRun in code output, but it does not need to match it; for a small fintech, regular agent-facing updates in 2026 are in line with the norm.

### Direction
Stated: spend USDC anywhere via agents, humans and MCP. The record matches: new agent integrations (Hermes) and documentation. Growth in x402 volume has been flat for six months at roughly $1-3k a month.

### Competitors
Bitrefill (gift cards via x402, $835 in 30 days from 77 buyers), Snack Money (dead), and agent payment layers such as Locus and Vaaya; card-issuing rivals are not covered here. Laso looks ahead of the other x402-native money-movement products on Base in actual orders.

### Green and red flags
Green: registered MSB with disclosed address and fees; organic-looking order sizes; steady agent docs; named builder with public posts; honest bounty pause notice.
Red: tiny volume; custodied agent wallet on Solana; "no-KYC" wording in the company's Farcaster bio (which may predate its MSB registration) sits awkwardly beside the "BSA-regulated" language on the site; no funding or team page; account-level compliance risk is higher for Venmo/PayPal payouts (identity verification required).

### Verdict
Credible but small; momentum Steady. A real regulated payments company with a working agent API and modest, organic usage on Base, plus very large Solana flows that come from a single wallet and cannot be called broad demand. Not a growth story yet, but one of the few places on Base where an x402 payment visibly buys a real-world product. Check monthly.

### Tracking card
- Site https://laso.finance; docs https://docs.laso.finance (llms.txt, SKILL.md, OpenAPI); GitHub https://github.com/LasoFinance (docs, hermes-plugin); docs change feed https://github.com/LasoFinance/docs/commits/main.atom.
- X @lasofinance; Farcaster `lasofinance`; Discord/Telegram: none found.
- x402scan server `2be7b63f-b369-4f66-a159-96cbc2ac3c5a`; payTo above; facilitator seen: coinbase. Dune: none found. Token: none.

### Sources
[laso.finance](https://laso.finance); [about](https://laso.finance/about); [docs](https://docs.laso.finance); [GitHub API](https://api.github.com/orgs/LasoFinance); [huntermonk.com](https://huntermonk.com); Farcaster APIs; x402scan tRPC. All accessed 2026-10-11.


---

## 7. Cluster Protocol (clusterprotocol.ai)

### One-line
An AI-infrastructure project that, since May 2026, sells an OpenAI-style inference gateway (chat, embeddings, images, speech, reranking, and "autonomous agent" runs priced from $1 to $15) paid per request in USDC on Base via x402, backed by a CP token on Base, BNB Chain and Mantle. In the last 30 days it had the largest USDC x402 volume of any Bazaar-registered app on Base ($54.8k, against $36.2k for the next one), then payments stopped almost completely on 2026-10-02.

### x402 role
Seller/resource server (AI inference API). It publishes `/openapi.json` and `/.well-known/x402` with seven priced endpoints ([OpenAPI](https://api.clusterprotocol.ai/openapi.json); [manifest](https://api.clusterprotocol.ai/.well-known/x402)). Not listed on the x402.org ecosystem page (no slug found). Also a token project.

### Chains
Base mainnet for x402 (chain 8453, USDC), per the live 402 challenge ([probe](https://api.clusterprotocol.ai/v1/chat/completions)); the whitepaper says contracts are on Base ([whitepaper](https://cluster-protocol.gitbook.io/whitepaper)); CP is also deployed at the same address on BNB Chain and Mantle (checked with `eth_getCode` on both chains' public RPCs). Base primary for payments.

### Token
- CP, Base `0x001AAd84c21A5CD4d696C56d44866e9703c43F77` (same address on BNB Chain and Mantle). The Base contract's first block with code is 46,469,823, timestamp 2026-05-25 17:09 UTC (binary search of `eth_getCode` on Base's public RPC); the project's `CPTOKEN` repo has the contract commit on 2026-05-26 ([repo](https://github.com/clusterprotocol/CPTOKEN)). The whitepaper itself gives no launch date.
- Method: not stated as a launchpad or fair launch. The tokenomics reads like a VC-style TGE: 5,000,000,000 fixed supply, 27.38% circulating at launch, pools for Community 40.38%, Foundation 21%, Team & Advisors 17% (18-month cliff, 24-month linear), Liquidity 8%, Series A & Strategic 9.33% and Seed 4.29% (12-month wait then 24 months), and liquidity "to meet exchange KPIs on launch day" ([tokenomics](https://cluster-protocol.gitbook.io/whitepaper/introduction/tokenomics.md)). A CP/USDC pool exists on Aerodrome ([DexScreener](https://api.dexscreener.com/latest/dex/tokens/0x001AAd84c21A5CD4d696C56d44866e9703c43F77)).
- Stated utility: paying for AI calls, GPU jobs and dataset purchases; access tiers; staking incentives (explicitly "not dividends"). Does it do real work? Not yet visible: x402scan shows USDC payments, not CP. The token contract supports EIP-3009 `transferWithAuthorization`, so paying in CP over x402 is technically possible, but no such flow was observed.
- Conflict to flag: the whitepaper says the contract "has no mint function", while the repo README lists role-based cross-chain mint/burn (Chainlink CCIP pool compatibility), and CoinGecko carries a GoPlus warning that the creator can modify the contract ([CoinGecko](https://www.coingecko.com/en/coins/cluster-protocol); [README](https://github.com/clusterprotocol/CPTOKEN)).

### Team
No founders or engineers are named on the site, the whitepaper (no team page) or the FAQ. Public handles: X @clusterprotocol, foundation account @OpenProtocolFND, a Korean community account (x.com/cluster_korea), Telegram t.me/clusterprotocol, Medium, GitHub org `clusterprotocol` (created 2024-05-08, description "Open Infra of Private AI, Backed by DAO5, PaperVC") ([site](https://www.clusterprotocol.ai); [org](https://api.github.com/orgs/clusterprotocol)). The only person visible in the project's own repos is `Sigmabrogz` ("Sigmabro", bio "Building autonomous AI agents | Open Source Contributor"; X @0x_Vivek set on his GitHub profile), who authored the two `CPTOKEN` commits (2026-05-26 and 2026-08-18); his relationship to the company is unconfirmed. No titles are published. The LinkedIn company page lists 12 employees (11-50 band), founded 2023, specialties AI model training/inference, GPU compute and datasets, and shows four names without titles: Tomer Warschauer Nuni, Vikash Baheliya, Saurav Upreti and Promzy Elisha ([LinkedIn](https://www.linkedin.com/company/clusterprotocol/)). A real, modest-sized staff exists, but leadership is unidentified.

### Track record and pivots
- 2023: founded (LinkedIn). 2024-05-08: GitHub org created. Earlier positioning on the site: "Orchestration layer for autonomous workflows" and "Liberation Engine for Internet Capital Market", a no-code tool to design, deploy and tokenize apps and agents, with about 100 partner and backer logos (Paper Ventures, Dao5, Maven Capital and others) ([site](https://www.clusterprotocol.ai)). Related products: CodeXero (prompt-to-dApp) and XEROBUILDERS community.
- 2026-05-15: x402scan origin created; 2026-05-25: CP deployed on Base; usage ramps June to August; 2026-08-31: resource list updated; 2026-10-02: payments collapse.
- Whitepaper now frames it as "AI inference gateway, tokenized data marketplace, compute layer, CodeXero application layer", with ERC-8004 agent identity and x402 sections.

### Trend-hopping score: 4
From tokenized-agent "Internet Capital Market" language, to a prompt-to-dApp builder, to an x402 inference gateway with ERC-8004 pages in the whitepaper, with a new token deployed in the same month the x402 gateway launched. The gateway itself is real and working (a live 402 challenge came back from each of the four endpoints I probed), which keeps this from a 5.

### Funding
Seed (4.29%) and "Series A & Strategic" (9.33%) token pools imply investor rounds; the GitHub org description names DAO5 and PaperVC as backers, and the site lists around 100 partners and backers. Round dates, amounts and leads: not found.

### Product and traction
- Live: seven x402 endpoints. Prices: chat $0.003, embeddings $0.0005, rerank $0.001, speech-to-text $0.006, text-to-speech $0.015, image $0.02, agent execute $1 (Pro $5, Max $15) ([OpenAPI](https://api.clusterprotocol.ai/openapi.json); [probe of the Pro/Max tiers](https://api.clusterprotocol.ai/v1/agents/execute/max)). Claims 500+ models.
- x402scan (Base, payTo `0x68396bd35874695ad86cd29410bd80a550991a2b`, origin `a09cb774-9331-4698-abdf-ccbaf7588f16`): all-time 532,550 transactions, $262,248, 730 buyers. Monthly USDC volume: May $2.9k, Jun $12.8k, Jul $75.5k, Aug $112.9k, Sep $55.5k, Oct 1-11 $2.6k. Through 2026-10-01: about 3,400-4,300 transactions and 545-657 buyers a day. On 2026-10-02: 152 transactions. Afterwards: about one transaction a day; last 7 days 3 transactions, $1.01 ([x402scan tRPC](https://www.x402scan.com/api/trpc/public.stats.bucketed), queried 2026-10-11).
- Revenue mix, last 30 days (I paged through the transfer list in descending order): 1,328 payments of exactly $15 (the Max agent tier) from 402 wallets ($19,920) and 5,025 payments of exactly $5 (Pro tier) from 598 wallets ($25,125), plus 47 at $1; those tiers are about $45k of the $54.8k. The cheap inference calls ($0.003 chat and similar) are the long tail of transaction count, not of dollars. Of 40 payers sampled, 34 had never sent an on-chain transaction and 19 held ETH. I could not trace whether funds were returned to payers (Base RPC log queries failed), so circular flow is not ruled out.

### Last six months
- 2026-05-15 origin registered; 2026-05-25/26 CP contract; 2026-08-18 README correction ("correct token contract address"); 2026-08-31 x402 resource list update; 2026-10-02 usage stop. Public GitHub commits: May 1, August 1 (CPTOKEN only; last commit 2026-08-18); the two other public repos are forks/templates. No releases, no blog posts found in the window (Medium returned 403). Team joins/departures: none public.

### Pace verdict
Opaque. The product evidently ships (a working multi-endpoint x402 API appeared in May), but there is no public changelog, no commit trail and no news flow, so it cannot be compared with AI-assisted teams that publish weekly (BlockRun). The abrupt stop on 2026-10-02 with no explanation is a negative.

### Direction
Stated: unified AI inference, data and compute on Base with x402 and ERC-8004 agent rails ([whitepaper](https://cluster-protocol.gitbook.io/whitepaper)). The record shows the gateway and token delivered, nothing else (no marketplace or compute evidence checked).

### Competitors
BlockRun (ahead on shipping, section 5), claw402, Locus; non-crypto inference gateways; decentralized-inference peers covered elsewhere (Heurist, Venice). Cluster led on USDC volume for three months but with far less transparency.

### Green and red flags
Green: a real, documented multi-modal x402 API; fixed-supply token with disclosed vesting; named backers on the GitHub org; token deployed to three chains with a consistent address.
Red: no named leadership or titles; usage looks campaign-like (most dollars from $5 and $15 agent-run payments by fresh wallets, then an abrupt stop); token launched the same month as the gateway; conflicting mint statements and a GoPlus warning; unverifiable "500+ models"; no public changelog.

### Verdict
Speculative; momentum Slowing (effectively stalled on-chain since 2026-10-02). It is a token-backed startup with a genuine x402 product whose best three months look at least partly campaign-driven. Watch whether payments resume and whether a team or changelog appears; until then do not treat the dollar volume as organic demand.

### Tracking card
- Site https://www.clusterprotocol.ai (blogs page, FAQ); whitepaper https://cluster-protocol.gitbook.io/whitepaper; API https://api.clusterprotocol.ai (openapi.json, .well-known/x402); Medium https://medium.com/@clusterprotocol.io.
- GitHub https://github.com/clusterprotocol (CPTOKEN); X @clusterprotocol and @OpenProtocolFND; Telegram t.me/clusterprotocol (announcements t.me/clusterprotocolann); Discord/Farcaster: none found.
- Token CP Base `0x001AAd84c21A5CD4d696C56d44866e9703c43F77`. x402scan origin and payTo above; facilitator seen: coinbase. Dune: none found.

### Sources
[clusterprotocol.ai](https://www.clusterprotocol.ai); [whitepaper](https://cluster-protocol.gitbook.io/whitepaper); [API OpenAPI](https://api.clusterprotocol.ai/openapi.json); [GitHub API](https://api.github.com/orgs/clusterprotocol); [CoinGecko](https://www.coingecko.com/en/coins/cluster-protocol); Base public RPC; x402scan tRPC. All accessed 2026-10-11.

---

## 8. KORUS (korusmusic.co)

### One-line
A music-remix marketplace where stems and packs can be bought with x402 USDC payments on Base by agents and anonymous buyers, and by session payment for signed-in web users ([KORUS Marketplace API](https://www.korusmusic.co/openapi.json)). It shows the most unique x402 buyers of any Bazaar-registered Base origin in the last 30 days (11,221), but it is new, anonymous and its payer pattern is unusual.

### x402 role
Seller/resource server in a consumer app (license purchase endpoint `POST /api/v1/licenses/{listingId}`, x402 v2). Not listed on x402.org.

### Chains
Base only (payments config: network base, chain 8453, USDC) ([config](https://www.korusmusic.co/api/v1/payments/config)).

### Token
None found; the site, API spec and marketplace mention none.

### Team
Not found. The API spec's support address is on the domain `korprotocol.io`, suggesting a "KOR Protocol" entity; that site returned only the text "KOR". The marketplace seller handles are generic combinations (`@hatsiko7`, `@cosmicflame685`, `@quietflame209`, `@opaldelta618`, `@lunarprism523`), which look auto-generated ([marketplace](https://www.korusmusic.co/marketplace)). No X, Farcaster or GitHub found. Anonymous.

### Track record and pivots
No history found. First recorded x402 payments in August 2026; origin registered on x402scan 2026-09-16; license resource last updated 2026-09-21.

### Trend-hopping score: not scoreable (provisional 3)
Too new and opaque; it combines music remixing, AI "sketch" tools and x402 license sales, which is three fashions in one pitch.

### Funding
No evidence of outside funding found.

### Product and traction
- Catalog (free, no auth): stems and packs priced from free to about 2.86 USDC and a 6.99 USD pack ([catalog](https://www.korusmusic.co/api/v1/catalog)).
- x402scan (Base, payTo `0x8a12157b27c22fb239e558dc3cb43c7d1a8c0881`, origin `a93ba2d0-67d2-49f5-87f8-3a6f82245f09`): 23,992 transactions, $18,671, 11,274 buyers all-time; last 7 days 19,122 transactions and 6,392 buyers; monthly: Aug 185 transactions ($12), Sep 2,584 ($4,258), Oct 1-10 21,223 ($14,401).
- Pattern: ramp from 168 buyers a day on 24 Sep to about 2,200 on 1 Oct; near-zero 2-5 Oct; then roughly 890-2,150 buyers a day from 6 Oct, with transactions about equal to buyers each day (23,953 transactions from 11,221 buyers over 30 days, about two payments per wallet). The 100 largest payments in the last 30 days are all exactly 2.997948 USDC from 100 different wallets; all 34 payers I sampled had never sent an on-chain transaction and held no ETH ([x402scan tRPC](https://www.x402scan.com/api/trpc/public.stats.bucketed); Base RPC, queried 2026-10-11). Real consumer purchases would show varied prices (the catalog does); a uniform price from single-use wallets fits a points campaign or wallet farm at least as well. Verdict on usage: unproven.

### Last six months
2026-08: first payments; 2026-09-16 x402scan registration; 2026-09-21 license resource updated; 2026-09-28 and 2026-10-01 first spikes; 2026-10-06 to 10-10 sustained wave. No public code, blog or releases. Team joins/departures unknown.

### Pace verdict
Cannot be judged from public evidence. Adoption growth is fast, but nothing about shipping is visible.

### Direction
Stated (site): "The future of music is participatory"; remix stems, AI sketching, live remix streams. The API suggests a plan to sell licenses to agents. No roadmap.

### Competitors
No comparable x402-native music-license app found. Other consumer-style x402 apps on Base are tiny (BaseHub, FortClaw, Clash of Coins).

### Green and red flags
Green: a clean, public OpenAPI with free catalog and license verification endpoint; moderate, varied price points; fast growth.
Red: anonymous; uniform-price payments from single-use wallets; seller names look synthetic; no team or social presence; one-week-old surge.

### Verdict
Speculative; momentum Accelerating (low confidence). It could be a real viral consumer app or an incentive campaign; the evidence does not distinguish them. Re-check in two to four weeks for repeat purchases and any named team.

### Tracking card
- Site https://www.korusmusic.co; API spec https://www.korusmusic.co/openapi.json; catalog https://www.korusmusic.co/api/v1/catalog; support domain korprotocol.io.
- x402scan origin `a93ba2d0-67d2-49f5-87f8-3a6f82245f09`; payTo above; facilitator seen: coinbase. GitHub/X/Farcaster/Discord: none found. Token: none.

### Sources
[site](https://www.korusmusic.co); [OpenAPI](https://www.korusmusic.co/openapi.json); [marketplace](https://www.korusmusic.co/marketplace); x402scan tRPC; Base RPC. All accessed 2026-10-11.

---

## 9. BotPay (botpay.network, BotYi Labs LLC)

### One-line
"AI Agent payment network and x402 infrastructure" from BotYi Labs LLC: pay-per-use endpoints (a `/pay` demo, NFT, token, safe, lottery and mint endpoints), a "BotPay Scan" agent/API marketplace and a machine-payments pitch ([botpay.network](https://botpay.network/en/)). Its x402 numbers come from about 320 wallets each paying $0.10 once a day.

### x402 role
Seller/resource server with payment-router ambitions. Its traffic settles through three facilitators on x402scan: Coinbase, PayAI and ultravioletadao ([x402scan](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list)). Not on the x402.org ecosystem list.

### Chains
Base, Solana and Arc testnet appear in the `/pay` 402 challenge ($0.01) ([probe](https://api.botpay.network/pay)). Base primary on x402scan.

### Token
No BotPay-branded token found. It does expose `/token`, `/nft`, a lottery and a `mint.botpay.network/x402` endpoint (registered 2025-10-27, x402 v1), i.e. x402-mint style experiments ([x402scan origins](https://www.x402scan.com/api/trpc/public.origins.search)). Contract address and mint details not confirmed.

### Team
Operator named as BotYi Labs LLC; the homepage says the About page lists a FinCEN MSB registration and company address (not retrievable: client-side rendered). No individuals, no X or GitHub found. The site title is in English and Chinese. Pseudonymous/anonymous.

### Track record and pivots
x402scan origins: `api.botpay.network` registered 2025-10-24; mint endpoint 2025-10-27; lottery endpoints 2026-01-25/26; video-access origin 2026-05-23 (resources updated 2026-08-10); `api.botpay.network` resources updated 2026-10-06. Product scope grew from mint and lottery experiments to a "payments for agents, robots, vending machines" message.

### Trend-hopping score: 4
x402 mint, lottery, NFT, agent marketplace, robots and vending machines in one site.

### Funding
No evidence of outside funding found.

### Product and traction
x402scan (Base, payTo `0x159be9e316bc5fac8ce05aec4eaae46e8f8a4908` and `0xcc1984e79726e7a0ae2b9df2ac9e79fb4983930e`): all-time 47,600 transactions, $3,964, 4,134 buyers; last 30 days 21,498 transactions, $2,149, 691 buyers; the Solana side of the same origin adds 11,914 transactions, $488 and 17 buyers in 30 days (about 700 payments per wallet). Monthly (Base): Jun 21 transactions, Jul 40, Aug 24,042 ($1,620), Sep 18,266 ($1,804), Oct 1-8 5,227 ($522). Between 24 Sep and 8 Oct the baseline was about 320 transactions and 320 buyers a day (spikes to 600-1,300 on 2, 3, 5 and 7 Oct), every payment exactly $0.10; all 40 payers sampled were fresh wallets (no on-chain transactions, no ETH). That is a scripted daily-claim pattern, not organic demand.

### Last six months
Dormant until August (21 transactions in June, 40 in July), then the daily-claim pattern from August; resource updates on 2026-08-10 and 2026-10-06. No public code, blog or releases found.

### Pace verdict
Unknown for engineering; on-chain activity is declining (about 1,600 transactions per active day in August, about 650 per day in early October).

### Direction
Stated: "payments and service delivery for AI agents and machines". No roadmap or dated plans found.

### Competitors
BlockRun, Laso, Locus, Merit's AgentCash; facilitator-side rivals covered elsewhere.

### Green and red flags
Green: working x402 v2 endpoints across Base/Solana; a stated regulated-entity story (unverified); discovery listing via Bazaar.
Red: anonymous; fixed daily payment pattern; mint/lottery gimmicks; no docs reachable by text fetch; no team.

### Verdict
Speculative; momentum Slowing. Treat the buyer count as farmed until proven otherwise.

### Tracking card
Site https://botpay.network/en/ (docs, news and about pages are client-rendered); x402scan origins `6083073a-bd94-4625-a719-ac64488a38d6` (api), `694bec63-dc72-4faf-8333-6b5ce4c0fa96` (video), `1946a714-d45b-42a5-82c3-9aa45dc1a6d1` (mint); payTo addresses above; facilitators seen: coinbase, payAI, ultravioletadao. X/GitHub/Farcaster/Discord/Telegram: none found. Dune: none.

### Sources
[botpay.network](https://botpay.network/en/); x402scan tRPC; live 402 probes; Base RPC. All accessed 2026-10-11.

---

## 10. AX1 (AX1 Research, ax1.vc; AX1 Console)

### One-line
A research and angel-community brand for "onchain consumer, Base, and agentic markets" that also runs "AX1 Console", where wallets and custom agents complete missions for XP, each call costing $0.02 over x402. It has the highest x402 transaction count among consumer-style apps but the traffic is engagement-farming by design.

### x402 role
Seller/resource server (console API); ecosystem/incubator. Not on x402.org.

### Chains
Base ([ax1.vc](https://ax1.vc)); XP is off-chain and a token page says liquidity updates are "soon" on Aerodrome (Base) ([console](https://console.ax1.vc)).

### Token
An "AX1 Token" page exists; no contract address or launch found. Utility as described: standing and access paths tied to hold history and console activity; selling or unstaking may reduce standing. Not launched as of 2026-10-11.

### Team
Not named. X @ax1vc. No GitHub (only a third-party repo experimenting with the console). Dune account dune.com/ax1research has no public dashboards (checked 2026-10-11) although the site links "Dune Dashboard V2" (April 2026).

### Track record and pivots
Research notes dated March to July 2026 (agentic commerce, wallet wars, perps venues, collectible cards, "Capital Chases Defensibility"); portfolio list: Upshot, OWB Studio, Glider, Lucent, BlockRunAI (labelled "USDC Hackathon. Base Batches 003 Winner"), Freeport Markets ([ax1.vc](https://ax1.vc)). Self-description: "from research firm to agentic ecosystem". x402scan origin created 2026-09-07.

### Trend-hopping score: 4
Research firm to angel network to agentic launchpad with XP and a token on the way.

### Funding
No disclosed funding; it offers "capital access" through an angel network.

### Product and traction
x402scan (Base, payTo `0x7284d41b5b852f2bd4c99bdf95043d84452d299c`, origin `2b2c3165-d4e6-4666-8770-699562804772`): 412,049 transactions, $8,241, 4,804 buyers all-time; last 30 days 407,446 transactions and 4,698 buyers; 7 days 88,775 transactions, $1,776. Monthly: Sep 292,351 transactions ($5,847), Oct 1-11 119,708 ($2,394). Every payment is $0.02. Daily volume ranges from 1,359 transactions (1 Oct) to 43,106 (27 Sep), with 41,181 on 4 Oct and a dip to 56 on 5 Oct; the largest 100 payments were all from one wallet; of 20 payers sampled, 17 had 1-5 on-chain transactions and held ETH. This is mission automation by many wallets and agents, not paying customers.

### Last six months
Research posts Mar-Jul 2026; console and x402 launch September 2026; no code. Team joins/departures unknown.

### Pace verdict
Not comparable (no public engineering record). Output is mostly writing and a console.

### Direction
Stated: coordination surface for research, founders, partners and agentic infrastructure ([ax1.vc](https://ax1.vc)); XP converting to access and a token.

### Competitors
Other quest/XP products and Base builders' programmes; BaseHub (games and XP) is a smaller x402 example.

### Green and red flags
Green: transparent about XP mechanics; credible portfolio cross-check (BlockRun in Base Batches 003).
Red: usage is incentive-driven; token narrative "soon"; no team; no public dashboards.

### Verdict
Speculative; momentum Steady. Useful as a sign of what farmed x402 volume looks like, and as a source on Base-ecosystem projects, not as an x402 business.

### Tracking card
https://ax1.vc; https://console.ax1.vc; X @ax1vc; Dune dune.com/ax1research (empty); x402scan origin above; payTo above; facilitator seen: coinbase.

### Sources
[ax1.vc](https://ax1.vc); [console.ax1.vc](https://console.ax1.vc); [Dune](https://dune.com/ax1research); x402scan tRPC; Base RPC. All accessed 2026-10-11.


---

## 11. Also scanned (brief notes, not full profiles)

These showed up in the x402scan Base rankings or the leads, but their evidence is too thin or too bot-like for a full profile. Same date, same method (x402scan Base, queried 2026-10-11).

- **claw402.ai** ("x402 API Payment Gateway", "Backed by vergex.trade"). Role: seller/gateway for market-data and AI APIs at $0.001-$0.05 per call ([llms.txt](https://claw402.ai/llms.txt)); Base only; no token or team found; origin created 2026-06-07. Last 30 days: 424,313 transactions, $940, 149 buyers; all-time 5.2M transactions, $10.7k, 763 buyers. Monthly USDC: Apr $2.3k, May $1.6k, Jun $1.2k, Jul $1.5k, Aug $2.2k, Sep $1.2k. Bot-dominated: 96 of the 100 largest payments came from one wallet and 49 of the latest 100 from another. Mostly a data feed (covered by another researcher). Speculative; momentum Steady. Origin `c03533a3-523f-4687-b1cd-c61e9de7aed9`; payTo `0xa9dd7cc9cbf0e05551332209289f04be36bc2315`; facilitator seen: coinbase.
- **X Pay (api-xpay.com)**. Utility APIs (ping, uuid, hash, echo) at $0.005, and text-AI endpoints priced at $0.01, $10 and $20 per call (rewrite, sentiment, keywords, classify, outline) ([openapi](https://www.api-xpay.com/openapi.json)); operator not stated; no token or team; Base; origin created 2026-09-11. Last 30 days: 42,270 transactions, $3,439, 159 buyers. Since 6 Oct it takes almost exactly $408 a day from 9-15 wallets; the 100 largest payments are 63 at $10 and 37 at $20; the latest 100 transfers are all $0.005 from one wallet. A $10 sentiment call is not a market price, so this reads as self-funded leaderboard volume. Speculative (likely wash); trend-hopping 5 (nothing but the x402 label). payTo `0x589a2314a2e05f45e40c4823da3ba58d421db3d8`; facilitator seen: coinbase.
- **Locus (paywithlocus.com)**. "The tool layer for capable agents": 3,960 paid APIs behind one balance, USDC wallets with spending limits, free tier and $200/$1,000 monthly plans; "Backed by Y Combinator (F25)"; X @PayWithLocus; listed on x402.org 2025-12-30; the site does not mention x402 or chains ([paywithlocus.com](https://paywithlocus.com)). Its x402 proxy origins (`*.x402.paywithlocus.com`) show 35,569 transactions, $57, 34 buyers in 30 days, and only 64 transactions in the last 7 days. Credible but small; usage tiny; shipping not assessed.
- **Vaaya (vaaya.ai)**. "Credit infrastructure for AI agents": prepaid or credit-line accounts, per-agent keys and limits ([vaaya.ai](https://vaaya.ai)); no x402, team or funding text on the site. x402scan: 1,758 transactions, $51, 111 buyers in 30 days (origin created 2026-07-06). Relevant as a competitor to Cred's credit pitch. Speculative.
- **OneShot Agent (win.oneshotagent.com)**. 45,620 transactions, $390, 58 buyers in 30 days; 80 of the 100 largest payments from one wallet; origin created 2026-09-29, activity since March. Speculative.
- **Legacy companies adding x402 (real but small, last 30 days)**: Bitrefill (698 transactions, $835, 77 buyers; on the x402.org list), ArDrive Turbo (203,405 transactions, $1,000, 117 buyers), Apify AGI (368 transactions, $695), dTelecom (16,508 transactions, $36,243 from only 25 buyers, large tickets), Venice API ($3,103, 42 buyers; AI data, out of scope).
- **Games and toys on Base (tiny)**: FortClaw (18,227 transactions, $1,477, 20 buyers), BaseHub (4,988 transactions, $284, 110 buyers), Clash of Coins (112 transactions, $875, 70 buyers).
- **Dormant**: ATXP (`iou.atxp.ai`, $336k all-time, last payment 2026-04-08), AIsa payment gateway (31.5M transactions all-time, last payment 2026-08-07).
- **Base Batches 003 teams with no x402scan origin**: 4Mica (clearing for agent micropayments), Agently, Floe Labs and Credifi (credit for agents) ([Base](https://www.base.org/batches)) - no visible x402 usage.


---

## Comparison table

Ratings as of 2026-10-11. Trend-hopping: 1 = long-running focus, x402 is a natural extension; 3 = several narrative pivots but a real product each time; 5 = narrative-only branding. "Brief" rows come from section 11 and have thinner evidence.

| Name | x402 role | Token | Seriousness | Momentum | Trend-hopping (1-5) |
|---|---|---|---|---|---|
| Zauth | Trust/identity + discovery (endpoint registry, monitoring SDK); now an AI-security vendor | $ZAUTH, Solana (pump.fun, first pool 2025-12-09); no Base token | Credible but small | Steady (company); Stalled (x402 piece) | 4 |
| Cred Protocol | Seller + trust/identity (credit/sybil scores, ERC-8004 validator) | None found | Credible but small | Slowing | 2 |
| Snack Money | Seller + SDK (pay by social handle) | SNACKMONEY, Zora creator coin on Base (2025-07-27); stopped trading | Likely abandoned | Dead | 3 |
| Fluora | Discovery marketplace + buyer client (MCP) | None found | Likely abandoned (marketplace backend deleted) | Stalled | 3 |
| BlockRun | Seller / payment router + SDKs + buyer agent | None official (unofficial Solana "BRUN" exists) | Serious builder | Steady (shipping steady-to-accelerating, paid usage falling) | 2 |
| Laso Finance | Seller (fiat rails behind x402; Base and Solana) | None | Credible but small | Steady | 1 |
| Cluster Protocol | Seller (AI inference gateway) + token | CP (Base, BNB Chain, Mantle; Base deploy 2026-05-25) | Speculative | Slowing (payments stopped 2026-10-02) | 4 |
| KORUS | Seller (consumer stem marketplace) | None found | Speculative | Accelerating (low confidence) | n/a (provisional 3) |
| BotPay | Seller / router (x402 infra, mint, lottery) | No ticker; mint endpoints | Speculative | Slowing | 4 |
| AX1 | Seller (quest console) + ecosystem brand | "AX1 Token" page, not launched | Speculative | Steady | 4 |
| claw402 (brief) | Seller / gateway (data + AI) | None found | Speculative | Steady | 4 |
| X Pay (brief) | Seller (utility APIs) | None | Speculative (likely wash) | Steady | 5 |
| Locus (brief) | Agent wallet / tool layer | None | Credible but small | Not assessed | n/a |
| Vaaya (brief) | Agent credit accounts | None found | Speculative | Not assessed | n/a |
| OneShot Agent (brief) | Seller | None found | Speculative | Steady | n/a |

