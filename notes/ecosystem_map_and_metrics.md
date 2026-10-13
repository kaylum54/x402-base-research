# x402 on Base: ecosystem map, uncovered projects and usage metrics (as of 2026-10-11)

> Scope: projects building for x402 (Coinbase's HTTP 402 payment protocol, now under the Linux Foundation) that are active on Base, and the usage data that shows which have real traction. No token price or chart analysis. Every number is dated and sourced; "USDC" amounts are converted from the raw 6-decimal units the APIs return. Data pulls were made on 2026-10-11 between about 10:50 and 12:00 UTC. Group labels in square brackets are the other researchers' assignments; "UNCOVERED" means the project is on none of the assigned lists.

## 1. Master table of x402 projects active on Base

### Takeaway
The x402.org/ecosystem page no longer exists (HTTP 404 on 2026-10-11; the site was deprecated in the repo on 2026-07-07), so the master list is built from that page's last repo snapshot (206 entries), the 29 facilitators x402scan shows settling on Base, the 135-token CoinGecko "x402 Ecosystem" category (62 tokens have a Base contract), and the Base sellers visible in x402scan and Coinbase Bazaar usage data. Only 33 of the 206 directory entries show 100 or more Base settlements or Bazaar calls in the last 30 days (another 21 show 1 to 99), 116 show no Base footprint at all by domain match, and 162 of 206 are not on the assigned list; 37 of the 62 Base-contract CoinGecko tokens show no x402 footprint I could match.

### Cited Findings

#### 1.0 Method, source key and conventions
- **Source key (used throughout; each link is the exact request or page that produced the numbers).**
  - [x402scan network totals, 30 days](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%7D%7D), [all-time](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D), [7 days](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A7%7D%7D), [1 day](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A1%7D%7D) and the [daily series by chain since 2025-05-09](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D). These are the public tRPC endpoints that back the x402scan.com website ([router source](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/trpc/routers/networks.ts)); x402scan's documented REST API is paid ($0.01 to $0.02 per call per its [OpenAPI spec](https://www.x402scan.com/openapi.json)) and I did not pay for it.
  - x402scan facilitator data: [Base list, 30 days](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [Base list, all time](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [all-chain list, 30 days](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [daily Base series by facilitator](https://www.x402scan.com/api/trpc/public.facilitators.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%7D%7D). Seller and buyer data: [top Base recipients by USDC, 30 days](https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [top Base recipients by tx, all time](https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [top Base buyers by USDC, 30 days](https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [Bazaar-registered origins on Base, 30 days](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D) and [all time](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [Solana registered origins, 30 days by tx](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D) and [all time](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), and a per-recipient daily series ([example: BlockRun](https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xe9030014f5dae217d0a152f02a043567b16c1abf%22%5D%7D%7D%7D)).
  - [Coinbase CDP x402 Bazaar discovery API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0) (32,169 resources read on 2026-10-11, each with a `quality` block of 30-day calls and unique payers).
  - [CoinGecko "x402 Ecosystem" category](https://www.coingecko.com/en/categories/x402-ecosystem) (page snapshot "about 9 hours ago") and the CoinGecko API ([category markets](https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&category=x402-ecosystem&per_page=250), [coin list with platforms](https://api.coingecko.com/api/v3/coins/list?include_platform=true)) for contracts; website links for Base tokens from the [DexScreener token API](https://api.dexscreener.com/tokens/v1/base/0x4b5d32a07b8d3ec5d6928caa30196f8dd6a7c5a9).
  - Old x402.org/ecosystem data: [partner metadata files in the repo at the commit before the website was deprecated](https://github.com/x402-foundation/x402/tree/2b74587b29bd7d986c4c562e46444d74606b0e1d/typescript/site/app/ecosystem/partners-data) and the [deprecation commit (2026-07-07)](https://github.com/x402-foundation/x402/commit/7be420af0b). Current docs lists: [facilitators](https://docs.x402.org/dev-tools/facilitators), [third-party SDKs](https://docs.x402.org/dev-tools/third-party-sdks), [third-party extensions](https://docs.x402.org/dev-tools/third-party-extensions), [networks and tokens](https://docs.x402.org/core-concepts/network-and-token-support).
  - [x402 Foundation launch release (2026-07-14)](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/), [x402.org home](https://x402.org), [GitHub search q=x402 by stars](https://api.github.com/search/repositories?q=x402&sort=stars&per_page=100) (300 repos read), [npm download API](https://api.npmjs.org/downloads/range/2026-04-01:2026-10-10/x402-fetch), [PyPI stats](https://pypistats.org/api/packages/x402/overall?mirrors=false), [awesome-x402](https://github.com/xpaysh/awesome-x402), [gold-402](https://github.com/Haustorium12/gold-402).
  - Third-party trackers used only for cross-checks: [x402-list.com](https://x402-list.com), [x402watch](https://x402.printmoneylab.com) and its [daily data repo](https://github.com/printmoneylab/x402watch-data), [agenteconomy.to](https://agenteconomy.to), [Valoria](https://x402.valoria.net), [Chainalysis](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/), [Solana Compass](https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months), [presenc.ai](https://presenc.ai/research/x402-protocol-adoption-tracker-2026), [Foresight News via Bitget](https://www.bitget.com/news/detail/12560605412078).
- **What "tx" and "USDC" mean.** x402scan counts indexed USDC transfers made by facilitators, not HTTP calls; amounts are USDC with 6 decimals ([Base USDC is the default x402 asset, 6 decimals](https://docs.x402.org/core-concepts/network-and-token-support); the Bazaar's `amount: "20000"` for a service priced "$0.02" confirms the scale).
- **x402scan only shows facilitators with at least 100 transactions in the window** (`MIN_FACILITATOR_TRANSACTIONS = 100` in [lib/facilitators.ts](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/lib/facilitators.ts)), and its per-chain "unique buyers/sellers" are sums across facilitator rows ([networks/list.ts](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/services/transfers/networks/list.ts)), so they over-count wallets that use more than one facilitator.
- **x402scan indexes only transfers sent by facilitator addresses in its registry** (the [sync configuration](https://github.com/Merit-Systems/x402scan/blob/main/sync/transfers/trigger/lib/facilitators.ts) is keyed to each facilitator's addresses and tokens), so self-hosted facilitators and signers not yet registered are invisible; the token-facilitators researcher reports that FluxA's current signer is not in the registry, so its volume may be understated ([their notes](dd_token_facilitators.md)). Other researchers' notes in this folder are used only to cross-check, and each such use is labelled "their notes".
- **Status rule (my definition, applied to Base only).** active = at least 100 Base settlements (or Bazaar calls) in the last 30 days, or a facilitator whose last Base settlement is within 30 days; low activity = 10 to 99 in 30 days; minimal = 1 to 9; dormant = last Base activity 31 to 180 days ago; dead on Base = more than 180 days; unverified = no Base footprint matched. "Dormant" or "dead on Base" does not mean the project is dead on other chains or off-chain.
- **Footprint matching.** Each project's website is reduced to its registrable domain and matched against x402scan's registered origins (30-day and all-time Base lists) and the Bazaar host index. A project that sells from a different domain, or shares a payTo address with others, can be missed or over-counted; "no footprint matched" means unverified, not inactive.
- **Coverage counts (computed from the tables below).** Directory (206 rows): 33 active, 21 low-activity or minimal, 22 dormant, 14 dead on Base, 116 unverified; 44 are on the assigned list and 162 are UNCOVERED. x402scan facilitators (31 above the 100-tx floor): 18 active, 9 dormant, 2 dead on Base, 2 not on Base. CoinGecko x402 tokens: 135, of which 62 have a Base contract and 37 of those show no matched footprint.
- **Chains column.** "Base (x402scan)" means x402scan saw Base settlements; "Solana (x402scan top-100)" means the domain appears in the top-100 Solana lists I pulled (Solana has only 705 registered recipients, so coverage is good but not complete); "Bazaar accepts" lists networks the project advertises in the Bazaar, which is supply-side, not usage.

#### 1.1 Official x402.org ecosystem directory, last snapshot (206 entries), with Base footprint
Source: the [206 partner metadata files](https://github.com/x402-foundation/x402/tree/2b74587b29bd7d986c4c562e46444d74606b0e1d/typescript/site/app/ecosystem/partners-data) (native categories: Services/Endpoints 79, Infrastructure & Tooling 66, Facilitators 33, Client-Side Integrations 24, Learning & Community Resources 3, Web3 Application & Infrastructure 1). The "Category" column maps those into the requested scheme (my mapping). Footprint numbers come from the x402scan and Bazaar sources above. Assigned-group rows come first.

| Name | Category | Token (Base contract) | Chains | Base traction signal (x402scan / Bazaar, as of 2026-10-11) | Status | Group |
|---|---|---|---|---|---|---|
| [Questflow](https://questflow.ai?utm_source=x402_website&utm_medium=ecosystem) | Agent platform | — | Base (x402scan) | facilitator[questflow] Base: 30d 0 tx/$0; all-time 473,884 tx/$10,205; last 2026-10-04; x402scan seller Base: 30d 0 tx/$0; all-time 274,533 tx/$8,267; last 2026-03-02 | active (<100 tx in 30d) | [agent apps] Questflow |
| [Daydreams Router](https://router.daydreams.systems) | Seller / API (LLM router) | DREAMS: 0x176383016bb310c9f1c180dc6729d5e28104e602 | Base (x402scan) | facilitator[daydreams] Base: 30d 496 tx/$775; all-time 11,816,699 tx/$2,764,122; last 2026-10-10; x402scan seller Base: 30d 0 tx/$0; all-time 4,655 tx/$1,405; last 2026-02-03 | active | [agent frameworks] Daydreams |
| [Gloria AI](https://itsgloria.ai) | Seller / API | GLORIA: 0x3b313f5615bbd6b200c71f84ec2f677b94df8674 | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 28 tx/$1; all-time 19,157 tx/$359; last 2026-10-11; Bazaar: 5 res, 28 calls/30d, last 2026-10-11 | low activity (28 tx/calls in 30d) | [data/AI sellers] Gloria AI |
| [Otto AI Agent Swarm](https://docs.ottowallet.xyz/introduction/otto-ai-swarm) | Seller / API | OTTO: 0x380337d0180db7d0df76ac4faae2fcea908ee1fc | Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Base, Solana | x402scan seller Base: 30d 3,271 tx/$30; all-time 178,278 tx/$433; last 2026-10-11; Bazaar: 76 res, 2,337 calls/30d, last 2026-10-11; Solana: 30d 60 tx/$0; all-time 599 tx/$2 | active | [data/AI sellers] Otto AI |
| [Venice](https://venice.ai/) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 613 tx/$3,103; all-time 3,449 tx/$5,279; last 2026-10-11 | active | [data/AI sellers] Venice |
| [MCPay](https://mcpay.tech) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [non-token infra] MCPay |
| [AgentCash](https://agentcash.dev) | Wallet / agent tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [non-token infra] Merit Systems (x402scan/AgentCash/Echo) |
| [x402scan](https://x402scan.com) | Discovery / analytics | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 1,463 tx/$15; all-time 6,859 tx/$90; last 2026-10-11; Bazaar: 16 res, 1,055 calls/30d, last 2026-10-11 | active | [non-token infra] Merit Systems (x402scan/AgentCash/Echo) |
| [Mogami examples](https://mogami.tech/#examples) | Docs / examples | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [non-token infra] Mogami |
| [Mogami facilitator](https://facilitator.mogami.tech) | Facilitator | — | declared: base, base-sepolia; Base (x402scan) | facilitator[mogami] Base: 30d 2,251 tx/$10; all-time 23,397 tx/$310,378; last 2026-10-10 | active | [non-token infra] Mogami |
| [Mogami java client SDK](https://mogami.tech/#clientSDK) | Wallet / client / app | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [non-token infra] Mogami |
| [Mogami java server SDK (Spring boot)](https://mogami.tech/#serverSDK) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [non-token infra] Mogami |
| [OpenX402.ai Facilitator](https://openx402.ai) | Facilitator | — | declared: base, base-sepolia, solana, solana-devnet, avalanche, avalanche-fuji, polygon, polygon-amoy; Base (x402scan) | facilitator[openx402] Base: 30d 1,717 tx/$1,283; all-time 563,331 tx/$176,696; last 2026-10-10; x402scan seller Base: 30d 0 tx/$0; all-time 2,215 tx/$23; last 2025-12-07 | active | [non-token infra] OpenX402 |
| [ampersend](https://app.ampersend.ai/discover) | Wallet / discovery | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [non-token infra] ampersend |
| [thirdweb](https://portal.thirdweb.com/payments/x402/client) | Wallet / client / app | — | Base (x402scan) | facilitator[thirdweb] Base: 30d 210 tx/$193; all-time 222,697 tx/$119,955; last 2026-10-10 | active | [non-token infra] thirdweb |
| [thirdweb](https://portal.thirdweb.com/payments/x402/facilitator) | SDK / tooling | — | Base (x402scan) | facilitator[thirdweb] Base: 30d 210 tx/$193; all-time 222,697 tx/$119,955; last 2026-10-10 | active | [non-token infra] thirdweb |
| [x402.rs Facilitator](https://facilitator.x402.rs) | Facilitator | — | declared: base, base-sepolia, solana, solana-devnet, avalanche, avalanche-fuji, polygon, polygon-amoy; Base (x402scan) | facilitator[x402rs] Base: 30d 0 tx/$0; all-time 703,452 tx/$468,938; last 2026-08-30 | dormant (42d idle) | [non-token infra] x402.rs |
| [AWS](https://builder.aws.com/content/38fLQk6zKRfLnaUNzcLPsUexUlZ/monetize-any-http-application-with-x402-and-cloudfront-lambdaedge) | Platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [platform] AWS |
| [Cloudflare](https://blog.cloudflare.com/x402/) | Platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [platform] Cloudflare |
| [Agentic.Market](https://agentic.market) | Discovery / marketplace (Coinbase) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [platform] Coinbase/CDP |
| [CDP Facilitator](https://docs.cdp.coinbase.com/x402/docs/quickstart-sellers) | Facilitator | — | declared: base, base-sepolia, solana, solana-devnet, polygon; Base (x402scan) | facilitator[coinbase] Base: 30d 1,965,296 tx/$232,816; all-time 116,954,488 tx/$29,210,019; last 2026-10-10 | active | [platform] Coinbase/CDP |
| [Stripe](https://docs.stripe.com/payments/machine/x402) | Platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [platform] Stripe |
| [Vercel](https://vercel.com/blog/introducing-x402-mcp-open-protocol-payments-for-mcp-tools) | Platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [platform] Vercel |
| [Axios & Fetch Clients](https://github.com/x402-foundation/x402/tree/main/examples/typescript/clients) | Wallet / client / app | — | — | linked repo has 6,702 stars | unverified (no Base footprint matched) | [platform] x402 Foundation (official reference/examples) |
| [MCP Server Example](https://github.com/x402-foundation/x402/tree/main/examples/typescript/mcp) | SDK / tooling | — | — | linked repo has 6,702 stars | unverified (no Base footprint matched) | [platform] x402 Foundation (official reference/examples) |
| [Node Servers (Hono, Express, Advanced)](https://github.com/x402-foundation/x402/tree/main/examples/typescript/servers) | SDK / tooling | — | — | linked repo has 6,702 stars | unverified (no Base footprint matched) | [platform] x402 Foundation (official reference/examples) |
| [x402 Example Gallery](https://github.com/x402-foundation/x402/tree/main/examples/typescript) | Docs / examples | — | — | linked repo has 6,702 stars | unverified (no Base footprint matched) | [platform] x402 Foundation (official reference/examples) |
| [x402.org Facilitator](https://x402.org) | Facilitator | — | declared: base-sepolia, solana-devnet | no footprint matched by domain | unverified (no Base footprint matched) | [platform] x402 Foundation (official reference/examples) |
| [Corbits](https://corbits.dev) | Facilitator | — | declared: solana, solana-devnet, base, base-sepolia, monad, monad-testnet, polygon, polygon-amoy; Base (x402scan); Solana (x402scan top-100) | facilitator[corbits] Base: 30d 0 tx/$0; all-time 19,777 tx/$305; last 2026-06-20; x402scan seller Base: 30d 0 tx/$0; all-time 1,619 tx/$16; last 2026-03-20; Solana: 30d 0 tx/$0; all-time 3,660 tx/$27 | dormant (113d idle) | [rivals] Corbits/Faremeter |
| [Faremeter](https://faremeter.xyz) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [rivals] Corbits/Faremeter |
| [Dexter](https://dexter.cash) | Facilitator | DEXTER: Solana only (no Base contract on CoinGecko) | declared: solana, solana-devnet, base, base-sepolia; Base (x402scan); Solana (x402scan top-100) | facilitator[dexter] Base: 30d 0 tx/$0; all-time 110,260 tx/$7,092; last 2026-10-06; x402scan seller Base: 30d 0 tx/$0; all-time 135 tx/$6; last 2026-06-22; Solana: 30d 0 tx/$0; all-time 25,915,820 tx/$4,706,170 | active (<100 tx in 30d) | [rivals] Dexter |
| [AI Frens by Treasure](https://aifrens.lol) | Launchpad / token | MAGIC / MIO: MAGIC 0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43; MIO 0xe19e7429ab6c1f9dd391faa88fbb940c7d22f18f | — | no footprint matched by domain | unverified (no Base footprint matched) | [token experiments] (launchpad/token; assignment inferred) |
| [TokenMesa](https://www.tokenmesa.com) | Launchpad / token | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [token experiments] (launchpad/token; assignment inferred) |
| [x402 Market](https://x402.world.fun) | Launchpad / marketplace | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 68,215 tx/$123; last 2026-06-12 | dormant (121d idle) | [token experiments] (launchpad/token; assignment inferred) |
| [CodeNut](https://www.codenut.ai/x402) | Agent platform / launchpad | — | Base (x402scan) | facilitator[codenut] Base: 30d 0 tx/$0; all-time 477,861 tx/$110,030; last 2026-01-27; x402scan seller Base: 30d 1 tx/$0; all-time 403,249 tx/$103,238; last 2026-10-08 | minimal (1 tx/calls in 30d) | [token facilitators] CodeNut |
| [Heurist Facilitator](https://facilitator.heurist.ai) | Facilitator | HEU: 0xef22cb48b8483df6152e1423b19df5553bbd818b | declared: base; Base (x402scan) | facilitator[heurist] Base: 30d 0 tx/$0; all-time 7,967,176 tx/$30,160; last 2026-10-08; x402scan seller Base: 30d 0 tx/$0; all-time 67,813 tx/$1,618; last 2026-05-12 | active (<100 tx in 30d) | [token facilitators] Heurist |
| [Heurist Mesh](https://mesh.heurist.ai/) | Seller / API | HEU: 0xef22cb48b8483df6152e1423b19df5553bbd818b | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 67,813 tx/$1,618; last 2026-05-12 | dormant (151d idle) | [token facilitators] Heurist |
| [Meridian](https://mrdn.finance) | Facilitator | MRDN: 0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6 | Base (x402scan) | facilitator[mrdn] Base: 30d 3,415 tx/$129,224; all-time 148,129 tx/$3,785,105; last 2026-10-10 | active | [token facilitators] Meridian |
| [PayAI Facilitator](https://facilitator.payai.network) | Facilitator | PAYAI: Solana only (no Base contract on CoinGecko) | declared: solana, solana-devnet, base, base-sepolia, polygon, polygon-amoy, avalanche, avalanche-fuji; Base (x402scan) | facilitator[payAI] Base: 30d 24,346 tx/$5,872; all-time 23,559,919 tx/$4,432,601; last 2026-10-10; x402scan seller Base: 30d 0 tx/$0; all-time 7,261 tx/$73; last 2025-11-11 | active | [token facilitators] PayAI |
| [Primer](https://primer.systems) | Wallet | PR: CoinGecko "Primer" (PR) lists Robinhood chain only, no Base contract | — | no footprint matched by domain | unverified (no Base footprint matched) | [token facilitators] Primer |
| [Primer Facilitator](https://primer.systems) | Facilitator | PR: CoinGecko "Primer" (PR) lists Robinhood chain only, no Base contract | declared: base; Base (x402scan) | facilitator[primer] Base: 30d 5,763 tx/$1,508; all-time 39,292 tx/$8,960; last 2026-10-10 | active | [token facilitators] Primer |
| [Fluora](https://www.fluora.ai/) | Marketplace (MonetizedMCP) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | [x402 apps and trust] Fluora |
| [Snack Money API](https://api.snack.money/docs) | Payments (tipping) | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 654 tx/$155; last 2025-12-04 | dead on Base (310d idle) | [x402 apps and trust] Snack Money |
| [zauth](https://zauthx402.com) | Trust / verification | ZAUTH: Solana only (no Base contract on CoinGecko) | — | no footprint matched by domain | unverified (no Base footprint matched) | [x402 apps and trust] Zauth |
| [0x402.ai](https://0x402.ai) | Facilitator-as-a-service | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [0xArchive Facilitator](https://0xarchive.io) | Facilitator | — | declared: hyperevm, base | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [0xmeta AI](https://0xmeta.ai) | Facilitator | — | declared: base, base-sepolia | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [1Pay.ing](https://1pay.ing) | Wallet | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [1Shot API](https://docs.1shotapi.com/automation/n8n.html#monetize-n8n-workflows-with-x402) | SDK / tooling (facilitator, n8n) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [402104](https://402.load.network) | Facilitator | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [ActionGate](https://api.actiongate.xyz/docs) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 3 tx/$0; last 2026-03-09 | dead on Base (215d idle) | UNCOVERED |
| [AdEx AURA API](https://guide.adex.network/) | Seller / API | ADX (heyAura): no Base contract (CoinGecko: Ethereum, BNB, Robinhood) | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 653 tx/$2; last 2026-09-06 | dormant (34d idle) | UNCOVERED |
| [AdPrompt x402 Marketing & Advertising APIs](https://www.adprompt.ai/x402-api) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [AEON](https://aeon.xyz/AIPayment) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Agent Camo](https://agentcamo.xyz) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 5 tx/$0; all-time 2,314 tx/$27; last 2026-09-19 | minimal (5 tx/calls in 30d) | UNCOVERED |
| [Agent Health Monitor](https://agenthealthmonitor.xyz) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 10 tx/$4; last 2026-07-15 | dormant (87d idle) | UNCOVERED |
| [Agently](https://use-agently.com) | Agent platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [AgentMail](https://docs.agentmail.to/integrations/x402) | Seller / API | — | Base (x402scan); Solana (x402scan top-100) | x402scan seller Base: 30d 45 tx/$18; all-time 2,024 tx/$655; last 2026-09-29; Solana: 30d 2,249 tx/$92; all-time 3,662 tx/$244 | low activity (45 tx/calls in 30d) | UNCOVERED |
| [Agnic.AI](https://agnic.ai/x402) | Wallet / identity platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Agoragentic](https://agoragentic.com/api/x402/info) | Agent marketplace | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 62 tx/$5; last 2026-07-12 | dormant (90d idle) | UNCOVERED |
| [AI Security Guard](https://aisecurityguard.io) | Trust / security | — | Base (x402scan) | x402scan seller Base: 30d 1 tx/$0; all-time 212 tx/$21; last 2026-09-28 | minimal (1 tx/calls in 30d) | UNCOVERED |
| [AiMo Network](https://aimo.network) | Seller / API (inference network) | — | Base (x402scan); Solana (x402scan top-100) | x402scan seller Base: 30d 0 tx/$0; all-time 973,786 tx/$834; last 2026-03-09; Solana: 30d 0 tx/$0; all-time 87,097 tx/$1,969 | dead on Base (215d idle) | UNCOVERED |
| [AIsa](https://aisa.one) | Marketplace | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 31,551,163 tx/$415,841; last 2026-08-07 | dormant (64d idle) | UNCOVERED |
| [Alchemy](https://agents.alchemy.com/?utm_source=x&utm_medium=social&utm_campaign=x402) | Seller / API | — | Bazaar accepts: Base | Bazaar: 2 res, 4 calls/30d, last 2026-10-08 | minimal (4 tx/calls in 30d) | UNCOVERED |
| [AltLayer](https://altlayer.io/) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [API Paywall Cookbook](https://github.com/fabriciogava/api-paywall-cookbook) | Docs / examples | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Arch AI Tools](https://archtools.dev) | Seller / API | — | Base (x402scan); Bazaar accepts: Base, Polygon | x402scan seller Base: 30d 72 tx/$1; all-time 338 tx/$10; last 2026-10-10; Bazaar: 20 res, 74 calls/30d, last 2026-10-10 | low activity (74 tx/calls in 30d) | UNCOVERED |
| [AskClaude](https://askclaude.shop) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 42 tx/$1; last 2026-04-29 | dormant (165d idle) | UNCOVERED |
| [AsterPay](https://asterpay.io) | Settlement / off-ramp | — | Base (x402scan); Bazaar accepts: Arbitrum, Base, Optimism, Polygon, eip155:1, eip155:1187947933 | x402scan seller Base: 30d 207 tx/$4; all-time 387 tx/$5; last 2026-10-11; Bazaar: 19 res, 194 calls/30d, last 2026-10-11 | active | UNCOVERED |
| [Atomic Rail](https://www.atomicrail.com) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Augur](https://augurrisk.com/) | Seller / API (risk) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [auor.io (Oreo)](https://auor.io) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 17 tx/$0; all-time 989 tx/$5; last 2026-10-07 | low activity (17 tx/calls in 30d) | UNCOVERED |
| [AutoIncentive Facilitator](https://autoincentive.online) | Facilitator | — | declared: solana, solana-devnet, base, base-sepolia | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Bino](https://github.com/iotexproject/binoSwarm/tree/main/packages/plugin-swarm) | Agent framework | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Bitrefill](https://www.bitrefill.com) | Seller / API | — | Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Arbitrum, Base, Polygon, Solana, lnbtc | x402scan seller Base: 30d 698 tx/$835; all-time 1,526 tx/$2,176; last 2026-10-11; Bazaar: 8 res, 337 calls/30d, last 2026-10-10; Solana: 30d 128 tx/$78; all-time 734 tx/$1,144 | active | UNCOVERED |
| [Bitrefill Facilitator](https://www.bitrefill.com) | Facilitator | — | declared: base, solana, polygon; Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Arbitrum, Base, Polygon, Solana, lnbtc | facilitator[bitrefill] Base: 30d 0 tx/$0; all-time 107 tx/$411; last 2026-04-30; x402scan seller Base: 30d 698 tx/$835; all-time 1,526 tx/$2,176; last 2026-10-11; Bazaar: 8 res, 337 calls/30d, last 2026-10-10; Solana: 30d 128 tx/$78; all-time 734 tx/$1,144 | active | UNCOVERED |
| [BlackSwan](https://blackswan.wtf) | Seller / API | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 12 tx/$0; all-time 7,739 tx/$108; last 2026-10-09; Bazaar: 2 res, 8 calls/30d, last 2026-10-09 | low activity (12 tx/calls in 30d) | UNCOVERED |
| [BlockRun.AI](https://blockrun.ai) | Seller / API | — | Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Base | x402scan seller Base: 30d 82,940 tx/$1,544; all-time 27,625,250 tx/$480,147; last 2026-10-11; Bazaar: 105 res, 78,844 calls/30d, last 2026-10-11; Solana: 30d 226,706 tx/$2,901; all-time 22,539,666 tx/$292,613 | active | UNCOVERED |
| [Bloomfilter](https://bloomfilter.xyz/docs) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 31 tx/$67; last 2026-04-24 | dormant (169d idle) | UNCOVERED |
| [Browserbase](https://browserbase.com) | Seller / API | — | Bazaar accepts: Base, solana | Bazaar: 8 res, 546 calls/30d, last 2026-10-11 | active | UNCOVERED |
| [Built on Stellar](https://developers.stellar.org/docs/build/apps/x402/built-on-stellar) | Facilitator (Stellar) | — | declared: stellar:pubnet, stellar:testnet | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Cascade](https://cascade.fyi) | SDK / tooling (payment splits; facilitator) | — | Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Base, Monad, Solana | facilitator[cascade] Base: 30d 0 tx/$0; all-time 33,485 tx/$126; last 2026-08-14; x402scan seller Base: 30d 5,966 tx/$16; all-time 28,121 tx/$102; last 2026-10-11; Bazaar: 12 res, 509 calls/30d, last 2026-10-11; Solana: 30d 2,367 tx/$12; all-time 11,108 tx/$52 | active | UNCOVERED |
| [ClawdVine](https://clawdvine.sh) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 237 tx/$228; last 2026-02-19 | dead on Base (233d idle) | UNCOVERED |
| [ClawPay MCP](https://www.npmjs.com/package/clawpay-mcp) | Wallet | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Conway Automaton](https://github.com/Conway-Research/automaton) | Agent framework | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Cybercentry](https://cybercentry.gitbook.io/cybercentry/documents/x402-cybercentry) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [DappLooker AI](https://dapplooker.ai/) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [DiamondClaws DeFi Intelligence](https://diamondclaws.io) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 9 tx/$0; last 2026-03-11 | dead on Base (214d idle) | UNCOVERED |
| [DJD Agent Score](https://djd-agent-score.fly.dev) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [dTelecom STT](https://x402stt.dtelecom.org) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 16,508 tx/$36,243; all-time 52,722 tx/$111,956; last 2026-10-11 | active | UNCOVERED |
| [Einstein AI](https://emc2ai.io) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 1,161 tx/$821; last 2026-08-30 | dormant (42d idle) | UNCOVERED |
| [Ekai Labs](https://ekailabs.xyz) | Agent app (memory layer) | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 244 tx/$4; last 2025-12-18 | dead on Base (297d idle) | UNCOVERED |
| [Elsa x402](https://x402.heyelsa.ai) | Facilitator / DeFi API | ELSA: 0x29cc30f9d113b356ce408667aa6433589cecbdca | declared: base, base-sepolia; Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 5,189 tx/$48; last 2026-02-02 | dead on Base (251d idle) | UNCOVERED |
| [EntRoute](https://entroute.com) | Discovery / analytics | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Exa](https://exa.ai/) | Seller / API | — | Solana (x402scan top-100); Bazaar accepts: Arc, Base, Solana, World Chain | Bazaar: 2 res, 5,456 calls/30d, last 2026-10-11; Solana: 30d 1,021 tx/$8; all-time 1,878 tx/$16 | active | UNCOVERED |
| [Farnsworth](https://ai.farnsworth.cloud) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Firecrawl](https://firecrawl.dev) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 1,151 tx/$11; last 2026-02-01 | dead on Base (252d idle) | UNCOVERED |
| [FluxA](https://fluxapay.xyz) | Facilitator / agent wallet | — | Base (x402scan) | facilitator[fluxa] Base: 30d 136,530 tx/$322,401; all-time 2,697,731 tx/$660,556; last 2026-10-10 | active | UNCOVERED |
| [Foldset](https://foldset.com) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Freepik](https://freepik.com) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 111 tx/$11; last 2026-03-12 | dead on Base (213d idle) | UNCOVERED |
| [fretchen.eu Facilitator](https://www.fretchen.eu/x402/) | Facilitator | — | declared: optimism, base | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Genbase](https://genbase.fun) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 6,342 tx/$1,171; last 2026-08-24 | dormant (48d idle) | UNCOVERED |
| [GenVox Crypto Sentiment API](https://api.genvox.io) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 264 tx/$8; last 2026-05-01 | dormant (163d idle) | UNCOVERED |
| [GoPlausible](https://x402.goplausible.xyz/) | Facilitator | — | declared: algorand, base, solana | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Grove API](https://grove.city/api) | Payments (tipping) | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 796 tx/$406; last 2026-03-03 | dead on Base (221d idle) | UNCOVERED |
| [Hydra Protocol Facilitator](https://hydraprotocol.org/) | Facilitator | — | declared: base, solana | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Hyperbrowser](https://hyperbrowser.ai) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [ICPAY](https://icpay.org) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Idapixl Cortex](https://idapixl.com/tools) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Imference](https://imference.com) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [invy](https://invy.bot) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [KAMIYO](https://kamiyo.ai) | Agent platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [KAMIYO Facilitator](https://kamiyo.ai) | Facilitator | — | declared: base, solana | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Kevros](https://governance.taskhawktech.com) | Trust / governance | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Kobaru](https://www.kobaru.io) | Facilitator | — | declared: solana, solana-devnet, base, base-sepolia, skale, skale-sepolia | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Kobaru](https://www.kobaru.io/) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Kodo](https://www.kodo.fun) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 18 tx/$1; last 2026-06-13 | dormant (120d idle) | UNCOVERED |
| [Kurier](https://kurier.xyz/docs/x402_payments) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Laso Finance](https://agents.laso.finance) | Seller / API | — | Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Base, Solana | x402scan seller Base: 30d 122 tx/$1,487; all-time 1,427 tx/$16,077; last 2026-10-10; Bazaar: 8 res, 164 calls/30d, last 2026-10-10; Solana: 30d 111 tx/$267,444; all-time 272 tx/$612,817 | active | UNCOVERED |
| [Latinum Agentic Commerce](https://latinum.ai) | Wallet / facilitator | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Locus](https://paywithlocus.com) | Wallet | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 35,569 tx/$57; all-time 38,339 tx/$106; last 2026-10-10; Bazaar: 52 res, 328 calls/30d, last 2026-10-10 | active | UNCOVERED |
| [MerchantGuard](https://www.merchantguard.ai) | Trust / compliance | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Meson x402](https://chromewebstore.google.com/detail/meson-x402/ppdppbgbdlnnmompceomhadjminblalp) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Messari](https://messari.io/x402) | Seller / API | — | Base (x402scan); Bazaar accepts: Base, Solana, X Layer | x402scan seller Base: 30d 156 tx/$37; all-time 2,351 tx/$531; last 2026-10-08; Bazaar: 1 res, 29 calls/30d, last 2026-10-10 | active | UNCOVERED |
| [Minifetch](https://minifetch.com) | Seller / API | — | Base (x402scan); Bazaar accepts: Base, Solana | x402scan seller Base: 30d 97 tx/$0; all-time 3,910 tx/$10; last 2026-10-11; Bazaar: 7 res, 71 calls/30d, last 2026-10-10 | low activity (97 tx/calls in 30d) | UNCOVERED |
| [Moltalyzer](https://moltalyzer.xyz) | Seller / API | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 479 tx/$8; all-time 4,279 tx/$60; last 2026-10-11; Bazaar: 1 res, 69 calls/30d, last 2026-10-11 | active | UNCOVERED |
| [Mycelia Signal](https://myceliasignal.com) | Seller / API | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 1,153 tx/$61; all-time 11,013 tx/$795; last 2026-10-11; Bazaar: 176 res, 1,117 calls/30d, last 2026-10-11 | active | UNCOVERED |
| [Nansen](https://docs.nansen.ai/getting-started/x402-payments) | Seller / API | — | Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Base, Monad, Solana, X Layer, eip155:56 | x402scan seller Base: 30d 4,661 tx/$92; all-time 43,793 tx/$1,119; last 2026-10-11; Bazaar: 32 res, 3,578 calls/30d, last 2026-10-11; Solana: 30d 0 tx/$0; all-time 5,631 tx/$91 | active | UNCOVERED |
| [Nevermined](https://nevermined.ai) | SDK / tooling (agent payments) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Nevermined Facilitator](https://api.live.nevermined.app/api/v1/rest/docs) | Facilitator | — | declared: base, base-sepolia | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Neynar](https://neynar.com) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 37,451 tx/$179; last 2026-07-17 | dormant (85d idle) | UNCOVERED |
| [Numbers Protocol](https://numbersprotocol.io/) | Trust / provenance | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Nuwa AI](https://nuwa.dev/) | Client app | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Obol](https://obol.sh) | Seller / API | — | Base (x402scan) | facilitator[obol] Base: 30d 0 tx/$0; all-time 1,200 tx/$3; last 2026-08-12; x402scan seller Base: 30d 0 tx/$0; all-time 50 tx/$61; last 2026-07-14 | dormant (59d idle) | UNCOVERED |
| [Octomil](https://octomil.com) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [OMATrust: x402 Reputation](https://docs.omatrust.org/integrations/x402/overview) | Trust / identity | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Onchain](https://onchain.fi) | Infra (facilitator aggregator) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [OnVoyage](https://app.onvoyage.ai/) | App | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [OOBE Protocol & Synapse](https://oobeprotocol.ai) | Trust / identity (Solana) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Oops!402](https://oops402.com) | Client / MCP discovery | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [OpenFacilitator](https://www.openfacilitator.io) | Facilitator | — | declared: base, solana; Base (x402scan) | facilitator[openfacilitator] Base: 30d 1,000 tx/$13; all-time 16,163 tx/$30,948; last 2026-10-10 | active | UNCOVERED |
| [OpenPayment](https://openpayment.link) | Payments gateway | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [OpenZeppelin](https://github.com/OpenZeppelin/relayer-plugin-x402-facilitator) | SDK / tooling (relayer plugin) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Orac](https://orac-safety.orac.workers.dev) | Trust / security | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 44 tx/$2; last 2026-07-01 | dormant (102d idle) | UNCOVERED |
| [Ordiscan](https://ordiscan.com) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [ouchanip x402 APIs](https://ouchanip.github.io/x402-docs/) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Pay.sh](https://pay.sh) | Marketplace | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [PEAC Protocol](https://x402.peacprotocol.org) | Trust / identity | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Pinata](https://402.pinata.cloud/) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Polygon Facilitator](https://docs.polygon.technology/payment-services/agentic-payments/x402/intro/) | Facilitator (Polygon) | — | declared: polygon, polygon-amoy | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Postera](https://postera.dev) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [PredictOS](https://github.com/PredictionXBT/PredictOS/blob/main/docs/features/x402-integration.md) | Agent platform | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Proofivy](https://proofivy.com) | Seller / API | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 38 tx/$28; all-time 567 tx/$37; last 2026-10-09; Bazaar: 4 res, 29 calls/30d, last 2026-10-09 | low activity (38 tx/calls in 30d) | UNCOVERED |
| [Proxy402](https://proxy402.com/) | Seller / API (paid links) | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 80 tx/$6; last 2025-11-07 | dead on Base (337d idle) | UNCOVERED |
| [px402 by PRXVT](https://prxvt.com/) | Privacy / trust | PRXVT: 0x4b5d32a07b8d3ec5d6928caa30196f8dd6a7c5a9 | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [QuantumShield API](https://quantumshield-api.vercel.app) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [QuickNode](https://github.com/quiknode-labs/x402-rails) | SDK / tooling | — | — | linked repo has 37 stars | unverified (no Base footprint matched) | UNCOVERED |
| [QuickSilver](https://data.iotex.ai) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [RelAI](https://relai.fi) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [RelAI Facilitator](https://relai.fi) | Facilitator | — | declared: ethereum, polygon, base, avalanche, skale-base, solana; Base (x402scan) | facilitator[relai] Base: 30d 0 tx/$0; all-time 89,527 tx/$214,985; last 2026-07-08 | dormant (95d idle) | UNCOVERED |
| [Rencom](https://x402.rencom.ai) | Discovery | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 914 tx/$9; last 2026-01-22 | dead on Base (262d idle) | UNCOVERED |
| [Robtex](https://x402.robtex.com) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Rug Munch Intelligence](https://cryptorugmunch.app/api/agent/v1/status) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Run402](https://run402.com) | Seller / API | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 7 tx/$0; all-time 138 tx/$16; last 2026-10-10; Bazaar: 3 res, 62 calls/30d, last 2026-10-11 | low activity (62 tx/calls in 30d) | UNCOVERED |
| [SerenAI x402 Gateway](https://serendb.com) | Seller / API | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 3,437 tx/$19; last 2026-04-17 | dormant (177d idle) | UNCOVERED |
| [SLAMai](https://www.slamai.xyz/) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Slinky Layer](https://slinkylayer.ai/) | Marketplace / token | SLINKY: 0xbb3d6c47379abb4713acffffa27483b726ee67db | Base (x402scan) | x402scan seller Base: 30d 3,181 tx/$30; all-time 23,927 tx/$1,087; last 2026-10-11 | active | UNCOVERED |
| [SocioLogic](https://www.sociologic.ai/x402-rng) | Seller / API | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 35 tx/$0; all-time 440 tx/$15; last 2026-10-08; Bazaar: 4 res, 26 calls/30d, last 2026-10-08 | low activity (35 tx/calls in 30d) | UNCOVERED |
| [solana-pay-x402](https://www.npmjs.com/package/solana-pay-x402) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [SolPay](https://solpay.cash) | Facilitator (Solana) | — | declared: solana | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Soundside](https://soundside.ai/docs/x402) | Seller / API | — | Bazaar accepts: Base | Bazaar: 1 res, 1 calls/30d, last 2026-10-08 | minimal (1 tx/calls in 30d) | UNCOVERED |
| [Spraay x402 Gateway](https://docs.spraay.app) | Gateway | — | Base (x402scan); Bazaar accepts: Base, Robinhood Chain, Solana | x402scan seller Base: 30d 143 tx/$2; all-time 4,387 tx/$89; last 2026-10-10; Bazaar: 32 res, 155 calls/30d, last 2026-10-10 | active | UNCOVERED |
| [Stakevia](https://stakevia.xyz) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Stellar](https://stellar.org/x402) | Platform (other chain) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Subnano](https://subnano.me/) | App (micropayment content) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [T54 XRPL x402 Facilitator](https://xrpl-x402.t54.ai/) | Facilitator (XRPL); Base data shown is t54 x402-secure API (same domain) | — | declared: xrpl:0; Base (x402scan); Solana (x402scan top-100) | x402scan seller Base: 30d 33 tx/$0; all-time 29,639,577 tx/$27,195; last 2026-10-10; Solana: 30d 0 tx/$0; all-time 2,758,912 tx/$2,760 | low activity (33 tx/calls in 30d) | UNCOVERED |
| [tip.md](https://www.tip.md/documentation?tab=mcp-server) | Payments (tipping) | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 27 tx/$17; last 2026-03-06 | dead on Base (219d idle) | UNCOVERED |
| [tollbooth](https://tollbooth.sh) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Treasure Facilitator](https://x402.treasure.lol) | Facilitator | MAGIC: 0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43 | declared: base, base-sepolia; Base (x402scan) | facilitator[treasure] Base: 30d 0 tx/$0; all-time 2,461 tx/$400; last 2026-10-08 | active (<100 tx in 30d) | UNCOVERED |
| [Trusta.AI](https://app.trustalabs.ai/attest) | Trust / identity | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Tweazy](https://github.com/aaronjmars/tweazy) | App | — | — | linked repo has 46 stars | unverified (no Base footprint matched) | UNCOVERED |
| [twit.sh](https://twit.sh) | Seller / API | — | Base (x402scan); Bazaar accepts: Base | x402scan seller Base: 30d 4,793 tx/$35; all-time 273,958 tx/$21,792; last 2026-10-11; Bazaar: 17 res, 3,739 calls/30d, last 2026-10-11 | active | UNCOVERED |
| [Ubounty](https://ubounty.ai) | Marketplace | — | Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 16 tx/$217; last 2025-12-15 | dead on Base (300d idle) | UNCOVERED |
| [Ultravioleta DAO](https://facilitator.ultravioletadao.xyz) | Facilitator | — | declared: base, base-sepolia, ethereum, arbitrum, arbitrum-sepolia, avalanche, avalanche-fuji, polygon; Base (x402scan) | facilitator[ultravioletadao] Base: 30d 25,487 tx/$6,518; all-time 37,369 tx/$7,134; last 2026-10-10 | active | UNCOVERED |
| [WalletIQ](https://walletiq-zeta.vercel.app) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [World](https://docs.world.org/agents/agent-kit/integrate) | Trust / identity | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [WorldFun Facilitator](https://facilitator.world.fun) | Facilitator | — | declared: base; Base (x402scan) | x402scan seller Base: 30d 0 tx/$0; all-time 68,215 tx/$123; last 2026-06-12 | dormant (121d idle) | UNCOVERED |
| [X402 Kit](https://github.com/AIMOverse/x402-kit) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [x402 Playground](https://www.x402playground.com/) | SDK / tooling (testing) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [x402-go](https://github.com/mark3labs/x402-go) | SDK / tooling | — | — | linked repo has 32 stars | unverified (no Base footprint matched) | UNCOVERED |
| [x402-proxy](https://github.com/cascade-protocol/x402-proxy) | SDK / tooling (CLI) | — | — | linked repo has 10 stars | unverified (no Base footprint matched) | UNCOVERED |
| [x402-secure](https://x402-secure.t54.ai/) | Trust / risk control | — | Base (x402scan); Solana (x402scan top-100) | x402scan seller Base: 30d 33 tx/$0; all-time 29,639,577 tx/$27,195; last 2026-10-10; Solana: 30d 0 tx/$0; all-time 2,758,912 tx/$2,760 | low activity (33 tx/calls in 30d) | UNCOVERED |
| [x402-watch](https://github.com/logiccrafterdz/x402-watch) | Discovery / analytics (health monitor) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [x402engine](https://x402engine.app) | Seller / API | — | Base (x402scan); Solana (x402scan top-100); Bazaar accepts: Base, Solana, eip155:4326 | x402scan seller Base: 30d 907 tx/$46; all-time 34,147 tx/$248; last 2026-10-11; Bazaar: 43 res, 776 calls/30d, last 2026-10-11; Solana: 30d 85 tx/$4; all-time 970 tx/$21 | active | UNCOVERED |
| [x402jobs](https://x402.jobs) | Agent platform (workflow builder) | JOBS: Solana only (no Base contract on CoinGecko) | Base (x402scan); Solana (x402scan top-100) | facilitator[x402jobs] Base: 30d 0 tx/$0; all-time 7,600 tx/$366; last 2026-05-17; Solana: 30d 0 tx/$0; all-time 772 tx/$1,081 | dormant (147d idle) | UNCOVERED |
| [x402lint](https://x402lint.com) | SDK / tooling | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [x402list.fun](https://x402list.fun) | Discovery / analytics | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [x402r](https://x402r.org) | Trust (refund/arbitration) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [x402station](https://x402station.com/) | Discovery / analytics | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [x402wall](https://x402wall.fun/how-it-works) | App (ad-slot game) | — | Solana (x402scan top-100) | Solana: 30d 0 tx/$0; all-time 358 tx/$10,405 | unverified (no Base footprint matched) | UNCOVERED |
| [xEcho Facilitator](https://www.xechoai.xyz) | Facilitator | — | declared: base; Base (x402scan) | facilitator[xecho] Base: 30d 0 tx/$0; all-time 14,066 tx/$2,847; last 2026-06-14 | dormant (118d idle) | UNCOVERED |
| [xpay Facilitator](https://www.xpay.sh/x402-facilitators/xpay/) | Facilitator | — | declared: base, base-sepolia | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Zerion](https://zerion.io/agents) | Seller / API | — | Base (x402scan); Bazaar accepts: Base, Solana | x402scan seller Base: 30d 76 tx/$1; all-time 746 tx/$7; last 2026-10-09; Bazaar: 16 res, 98 calls/30d, last 2026-10-11 | low activity (98 tx/calls in 30d) | UNCOVERED |
| [ZeroPay](https://zpaynow.com) | Payments gateway / wallet | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [zkStash](https://zkstash.ai) | Agent platform (memory) | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |
| [Zyte API](https://python-zyte-api.readthedocs.io/en/stable/use/x402.html) | Seller / API | — | — | no footprint matched by domain | unverified (no Base footprint matched) | UNCOVERED |

#### 1.2 Facilitators tracked by x402scan (Base settlements and status)
Source: [x402scan facilitator lists](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D) (31 facilitators pass the 100-tx floor all-time; 29 settle on Base; 13 pass the floor in the last 30 days: [30-day list](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)) and the [facilitator registry package](https://github.com/Merit-Systems/x402scan/tree/main/packages/external/facilitators/src/facilitators) (33 ids). Tokens from CoinGecko where one exists.

| Facilitator (x402scan id) | Chains seen by x402scan (all-time) | Base all-time tx / USDC | Base last 30d tx / USDC | Last Base settlement | Status on Base | Token | Group |
|---|---|---|---|---|---|---|---|
| [Coinbase](https://docs.cdp.coinbase.com/x402/welcome) ([x402scan](https://www.x402scan.com/facilitator/coinbase); `coinbase`) | base,solana | 117.0M / $29.21M | 1.97M / $233K | 2026-10-10 | active | — | [platform] Coinbase/CDP |
| [PayAI](https://payai.network) ([x402scan](https://www.x402scan.com/facilitator/payAI); `payAI`) | base,solana | 23.6M / $4.43M | 24K / $5.9K | 2026-10-10 | active | PAYAI (Solana only) | [token facilitators] PayAI |
| [Daydreams](https://facilitator.daydreams.systems) ([x402scan](https://www.x402scan.com/facilitator/daydreams); `daydreams`) | base,solana | 11.8M / $2.76M | 496 / $775 | 2026-10-10 | active | DREAMS 0x176383016bb310c9f1c180dc6729d5e28104e602 | [agent frameworks] Daydreams |
| [Heurist](https://docs.heurist.ai/x402-products/facilitator) ([x402scan](https://www.x402scan.com/facilitator/heurist); `heurist`) | base | 7.97M / $30K | <100 tx (below x402scan display floor) | 2026-10-08 | active (<100 tx in 30d) | HEU 0xef22cb48b8483df6152e1423b19df5553bbd818b | [token facilitators] Heurist |
| [Figment](https://docs.figment.io/reference/x402) ([x402scan](https://www.x402scan.com/facilitator/figment-facilitator); `figment-facilitator`) | solana | 0 / $0 | n/a | — | not on Base (x402scan: solana) | — | UNCOVERED |
| [FluxA](https://fluxapay.xyz) ([x402scan](https://www.x402scan.com/facilitator/fluxa); `fluxa`) | base | 2.70M / $661K | 137K / $322K | 2026-10-10 | active | — | UNCOVERED |
| [Virtuals Protocol](https://app.virtuals.io) ([x402scan](https://www.x402scan.com/facilitator/virtuals); `virtuals`) | base | 1.99M / $4.34M | 2.8K / $28 | 2026-09-28 | active | VIRTUAL (not in CoinGecko x402 category) | [agent frameworks] Virtuals |
| [X402rs](https://x402.rs) ([x402scan](https://www.x402scan.com/facilitator/x402rs); `x402rs`) | base,polygon | 703K / $469K | <100 tx (below x402scan display floor) | 2026-08-30 | dormant (42d idle) | — | [non-token infra] x402.rs |
| [OpenX402](https://open.x402.host) ([x402scan](https://www.x402scan.com/facilitator/openx402); `openx402`) | base,solana | 563K / $177K | 1.7K / $1.3K | 2026-10-10 | active | — | [non-token infra] OpenX402 |
| [AnySpend](https://docs.b3.fun/anyspend/x402-overview) ([x402scan](https://www.x402scan.com/facilitator/anyspend); `anyspend`) | base,solana | 521K / $141K | <100 tx (below x402scan display floor) | 2026-08-17 | dormant (54d idle) | ANY 0xc17dda248e2d50fc006d8febb5a406dd31972712 | UNCOVERED |
| [CodeNut](https://docs.codenut.ai/guides/x402-facilitator) ([x402scan](https://www.x402scan.com/facilitator/codenut); `codenut`) | base,solana | 478K / $110K | <100 tx (below x402scan display floor) | 2026-01-27 | dead on Base (257d idle) | — | [token facilitators] CodeNut |
| [Questflow](https://facilitator.questflow.ai) ([x402scan](https://www.x402scan.com/facilitator/questflow); `questflow`) | base | 474K / $10K | <100 tx (below x402scan display floor) | 2026-10-04 | active (<100 tx in 30d) | — | [agent apps] Questflow |
| [AurraCloud](https://x402-facilitator.aurracloud.com) ([x402scan](https://www.x402scan.com/facilitator/aurracloud); `aurracloud`) | base,solana | 235K / $54K | <100 tx (below x402scan display floor) | 2026-01-13 | dead on Base (271d idle) | AURA "Aurra by Virtuals" 0xdcaa5e062b2be18e52ea6ed7ba232538621ddc10 (name match unverified) | [token facilitators] AurraCloud |
| [Thirdweb](https://portal.thirdweb.com/payments/x402/facilitator) ([x402scan](https://www.x402scan.com/facilitator/thirdweb); `thirdweb`) | base,polygon | 223K / $120K | 210 / $193 | 2026-10-10 | active | — | [non-token infra] thirdweb |
| [Meridian](https://docs.mrdn.finance) ([x402scan](https://www.x402scan.com/facilitator/mrdn); `mrdn`) | base | 148K / $3.79M | 3.4K / $129K | 2026-10-10 | active | MRDN 0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6 | [token facilitators] Meridian |
| [Dexter](https://dexter.cash/facilitator) ([x402scan](https://www.x402scan.com/facilitator/dexter); `dexter`) | base,solana | 110K / $7.1K | <100 tx (below x402scan display floor) | 2026-10-06 | active (<100 tx in 30d) | DEXTER (Solana only) | [rivals] Dexter |
| [three.ws](https://three.ws/docs/x402-distribution) ([x402scan](https://www.x402scan.com/facilitator/three-ws); `three-ws`) | solana | 0 / $0 | n/a | — | not on Base (x402scan: solana) | — | UNCOVERED |
| [RelAI](https://relai.fi/relai-facilitator) ([x402scan](https://www.x402scan.com/facilitator/relai); `relai`) | base,solana | 90K / $215K | <100 tx (below x402scan display floor) | 2026-07-08 | dormant (95d idle) | — | UNCOVERED |
| [Polymer](https://docs.polymerlabs.org/docs/build/start/) ([x402scan](https://www.x402scan.com/facilitator/polymer); `polymer`) | base | 58K / $8.7K | 4.7K / $1.6K | 2026-10-09 | active | — | UNCOVERED |
| [Primer](https://github.com/Primer-Systems/x402) ([x402scan](https://www.x402scan.com/facilitator/primer); `primer`) | base | 39K / $9.0K | 5.8K / $1.5K | 2026-10-10 | active | PR (Robinhood chain only) | [token facilitators] Primer |
| [Ultravioleta DAO](https://facilitator.ultravioletadao.xyz) ([x402scan](https://www.x402scan.com/facilitator/ultravioletadao); `ultravioletadao`) | base,solana | 37K / $7.1K | 25K / $6.5K | 2026-10-10 | active | — | UNCOVERED |
| [Cascade](https://cascade.fyi) ([x402scan](https://www.x402scan.com/facilitator/cascade); `cascade`) | base,solana | 33K / $126 | <100 tx (below x402scan display floor) | 2026-08-14 | dormant (57d idle) | — | UNCOVERED |
| [Mogami](https://mogami.tech/) ([x402scan](https://www.x402scan.com/facilitator/mogami); `mogami`) | base | 23K / $310K | 2.3K / $10 | 2026-10-10 | active | — | [non-token infra] Mogami |
| [Corbits](https://corbits.dev) ([x402scan](https://www.x402scan.com/facilitator/corbits); `corbits`) | base,solana | 20K / $305 | <100 tx (below x402scan display floor) | 2026-06-20 | dormant (113d idle) | — | [rivals] Corbits/Faremeter |
| [OpenFacilitator](https://www.openfacilitator.io) ([x402scan](https://www.x402scan.com/facilitator/openfacilitator); `openfacilitator`) | base,solana | 16K / $31K | 1.0K / $13 | 2026-10-10 | active | — | UNCOVERED |
| [xEcho](https://www.xechoai.xyz) ([x402scan](https://www.x402scan.com/facilitator/xecho); `xecho`) | base | 14K / $2.8K | <100 tx (below x402scan display floor) | 2026-06-14 | dormant (118d idle) | — | UNCOVERED |
| [x402 Jobs](https://www.x402.jobs) ([x402scan](https://www.x402scan.com/facilitator/x402jobs); `x402jobs`) | base,solana | 7.6K / $366 | <100 tx (below x402scan display floor) | 2026-05-17 | dormant (147d idle) | JOBS (Solana only) | UNCOVERED |
| [Treasure](https://x402.treasure.lol/facilitator) ([x402scan](https://www.x402scan.com/facilitator/treasure); `treasure`) | base | 2.5K / $400 | <100 tx (below x402scan display floor) | 2026-10-08 | active (<100 tx in 30d) | MAGIC 0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43 | UNCOVERED |
| [Obol](https://obol.org) ([x402scan](https://www.x402scan.com/facilitator/obol); `obol`) | base | 1.2K / $3 | <100 tx (below x402scan display floor) | 2026-08-12 | dormant (59d idle) | — | UNCOVERED |
| [Openmid](https://github.com/open-mid/8004-facilitator) ([x402scan](https://www.x402scan.com/facilitator/openmid); `openmid`) | base | 241 / $66 | <100 tx (below x402scan display floor) | 2026-09-29 | active (<100 tx in 30d) | — | UNCOVERED |
| [Bitrefill](https://www.bitrefill.com) ([x402scan](https://www.x402scan.com/facilitator/bitrefill); `bitrefill`) | base,solana | 107 / $411 | <100 tx (below x402scan display floor) | 2026-04-30 | dormant (164d idle) | — | UNCOVERED |

Facilitators the docs list as production options but x402scan does not show: [Built on Stellar, Celo, Fireblocks, FTP Canton, HPP, NEAR (mikedotexe), Polygon, Solvador, T54 XRPL](https://docs.x402.org/dev-tools/facilitators) (all UNCOVERED; none is Base-first). x402-list.com reports the Polygon Facilitator at [$141,064 of USDC settled in the trailing 30 days](https://x402-list.com), which is on Polygon, not Base.

#### 1.3 Tokens: CoinGecko "x402 Ecosystem" category (135 coins)
Source: [CoinGecko category API](https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&category=x402-ecosystem&per_page=250) (135 coins on 2026-10-11) joined to [CoinGecko platform data](https://api.coingecko.com/api/v3/coins/list?include_platform=true) for contracts. Category membership is not proof of x402 usage: the list includes Chainlink, EigenCloud, peaq and SKALE alongside micro-caps. CoinGecko coin-page categories were fetched for all 62 Base-contract tokens (not for the 73 others); a dash means none of the topic categories I kept applies. No price or market-cap figures are used; the "CG rank" column is only CoinGecko's own listing rank, shown as a listing signal.

**1.3a Tokens with a Base contract on CoinGecko (62)**

| CG rank | Token | Ticker | Base contract | Website | CoinGecko categories (where fetched) | x402 footprint matched by website domain | Group |
|---|---|---|---|---|---|---|---|
| 15 | [Chainlink](https://www.coingecko.com/en/coins/chainlink) | LINK | [`0x88fb150bdc53a65fe94dea0c9ba0a6daf8c6e196`](https://basescan.org/token/0x88fb150bdc53a65fe94dea0c9ba0a6daf8c6e196) | [chain.link](https://chain.link/) | Infrastructure, Oracle, Privacy Infrastructure, Privacy | Bazaar 3 res / 46K calls30 | UNCOVERED |
| 169 | [EigenCloud (prev. EigenLayer)](https://www.coingecko.com/en/coins/eigenlayer) | EIGEN | [`0x2081ab0d9ec9e4303234ab26d86b20b3367946ee`](https://basescan.org/token/0x2081ab0d9ec9e4303234ab26d86b20b3367946ee) | [www.eigencloud.xyz](https://www.eigencloud.xyz/) | Artificial Intelligence (AI), Infrastructure, Data Availability, Restaking | none matched | UNCOVERED |
| 282 | [peaq](https://www.coingecko.com/en/coins/peaq-2) | PEAQ | [`0x9b56b112bbd6343a8961a093315a9a60b8cb1f36`](https://basescan.org/token/0x9b56b112bbd6343a8961a093315a9a60b8cb1f36) | [www.peaq.xyz](https://www.peaq.xyz/) | Smart Contract Platform, Layer 1 (L1), DePIN, Robotics | none matched | UNCOVERED |
| 537 | [Treasure](https://www.coingecko.com/en/coins/magic) | MAGIC | [`0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43`](https://basescan.org/token/0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43) | [treasure.lol](https://treasure.lol/) | Artificial Intelligence (AI), Smart Contract Platform, NFT, Metaverse | facilitator `treasure`: 2.5K tx / $400 all-time; AI Frens launchpad (x402 character tokens) | UNCOVERED |
| 557 | [Acurast](https://www.coingecko.com/en/coins/acurast) | ACU | [`0xc5fed7c8ccc75d8a72b601a66dffd7a489073f0b`](https://basescan.org/token/0xc5fed7c8ccc75d8a72b601a66dffd7a489073f0b) | [acurast.com](https://acurast.com/) | Artificial Intelligence (AI), DePIN | none matched | UNCOVERED |
| 656 | [BankrCoin](https://www.coingecko.com/en/coins/bankercoin-2) | BNKR | [`0x22af33fe49fd1fa80c7149773dde5890d3c76f3b`](https://basescan.org/token/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b) | [bankr.bot](https://bankr.bot) | Artificial Intelligence (AI), AI Agents, AI Applications, DeFAI | Bankr x402 SDK repos (BankrBot/x402-cli-example 3 stars); no Base seller footprint matched | [agent apps] Bankr |
| 689 | [SKALE](https://www.coingecko.com/en/coins/skale) | SKL | [`0xb9caa63e09c646c1ec79acb2158d173e64a5fed3`](https://basescan.org/token/0xb9caa63e09c646c1ec79acb2158d173e64a5fed3) | [skale.space](https://skale.space/) | Smart Contract Platform, Gaming (GameFi), Layer 1 (L1), Gaming Blockchains | none matched | UNCOVERED |
| 756 | [FLOCK](https://www.coingecko.com/en/coins/flock-2) | FLOCK | [`0x5ab3d4c385b400f3abb49e80de2faf6a88a7b691`](https://basescan.org/token/0x5ab3d4c385b400f3abb49e80de2faf6a88a7b691) | [flock.io](https://flock.io/) | Artificial Intelligence (AI), AI Applications | none matched | UNCOVERED |
| 978 | [OpenServ](https://www.coingecko.com/en/coins/openserv) | SERV | [`0x5576d6ed9181f2225aff5282ac0ed29f755437ea`](https://basescan.org/token/0x5576d6ed9181f2225aff5282ac0ed29f755437ea) | [openserv.ai](https://openserv.ai/) | Artificial Intelligence (AI), AI Agents, AI Framework | none matched | UNCOVERED |
| 1047 | [Autonolas](https://www.coingecko.com/en/coins/autonolas) | OLAS | [`0x54330d28ca3357f294334bdc454a032e7f353416`](https://basescan.org/token/0x54330d28ca3357f294334bdc454a032e7f353416) | [olas.network](https://olas.network) | Artificial Intelligence (AI), AI Agents, AI Agent Launchpad, AI Framework | none matched | [agent apps] Olas |
| 1136 | [Elsa](https://www.coingecko.com/en/coins/elsa) | ELSA | [`0x29cc30f9d113b356ce408667aa6433589cecbdca`](https://basescan.org/token/0x29cc30f9d113b356ce408667aa6433589cecbdca) | [heyelsa.ai](https://heyelsa.ai) | Artificial Intelligence (AI), AI Agents, DeFAI | Elsa x402 origin (x402.heyelsa.ai): 5.2K tx / $48 all-time, last 2026-02-02 (dead on Base) | UNCOVERED |
| 1494 | [Anyspend](https://www.coingecko.com/en/coins/anyspend) | ANY | [`0xc17dda248e2d50fc006d8febb5a406dd31972712`](https://basescan.org/token/0xc17dda248e2d50fc006d8febb5a406dd31972712) | [anyspend.com](https://anyspend.com) | Infrastructure | facilitator `anyspend`: 521K tx / $141K all-time (last 2026-08-17); x402.anyspend.com seller $25K in 6 months | UNCOVERED |
| 1980 | [Daydreams](https://www.coingecko.com/en/coins/daydreams) | DREAMS | [`0x176383016bb310c9f1c180dc6729d5e28104e602`](https://basescan.org/token/0x176383016bb310c9f1c180dc6729d5e28104e602) | [www.dreams.fun](https://www.dreams.fun) | Artificial Intelligence (AI), AI Agents, AI Applications, AI Framework | facilitator `daydreams`: 11.8M tx / $2.76M all-time on Base (peak Nov 2025); 496 tx in last 30d | [agent frameworks] Daydreams |
| 2089 | [vAPI Network](https://www.coingecko.com/en/coins/vapi-network) | VAPI | [`0x1ea8deb921aa6015f4938010c848140b98108dd2`](https://basescan.org/token/0x1ea8deb921aa6015f4938010c848140b98108dd2) | [vapinetwork.ai](https://vapinetwork.ai/) | — | Bazaar 1 res / 12 calls30 | UNCOVERED |
| 2276 | [PRXVT by Virtuals](https://www.coingecko.com/en/coins/prxvt-by-virtuals) | PRXVT | [`0x4b5d32a07b8d3ec5d6928caa30196f8dd6a7c5a9`](https://basescan.org/token/0x4b5d32a07b8d3ec5d6928caa30196f8dd6a7c5a9) | [prxvt.com](http://prxvt.com/) | Artificial Intelligence (AI), Privacy Infrastructure, Privacy | none matched | [agent frameworks] Virtuals ecosystem token (inferred) |
| 2526 | [Aubrai by Bio](https://www.coingecko.com/en/coins/aubrai-by-bio) | AUBRAI | [`0x9d56c29e820dd13b0580b185d0e0dc301d27581d`](https://basescan.org/token/0x9d56c29e820dd13b0580b185d0e0dc301d27581d) | [aubr.ai](https://aubr.ai/) | Artificial Intelligence (AI), AI Agents | x402-api.aubr.ai: 14.5K tx / $321 in 6 months; 2.3K Bazaar calls30 | UNCOVERED |
| 2726 | [Ethy AI](https://www.coingecko.com/en/coins/ethy-ai) | ETHY | [`0xc44141a684f6aa4e36cd9264ab55550b03c88643`](https://basescan.org/token/0xc44141a684f6aa4e36cd9264ab55550b03c88643) | [ethyai.app](https://ethyai.app/) | Artificial Intelligence (AI), AI Applications | x402scan Base seller: 30d 0 tx/$0; all-time 24 tx/$9; last 2025-11-15 | UNCOVERED |
| 2985 | [Slinky Layer](https://www.coingecko.com/en/coins/slinky-layer) | SLINKY | [`0xbb3d6c47379abb4713acffffa27483b726ee67db`](https://basescan.org/token/0xbb3d6c47379abb4713acffffa27483b726ee67db) | [slinkylayer.ai](https://slinkylayer.ai) | Artificial Intelligence (AI), Privacy | slinkylayer.ai: 3.2K tx / $30 in last 30d; 23.9K tx / $1.1K all-time | UNCOVERED |
| 3061 | [Sally A1C](https://www.coingecko.com/en/coins/sally-a1c) | A1C | [`0x1f1c695f6b4a3f8b05f2492cef9474afb6d6ad69`](https://basescan.org/token/0x1f1c695f6b4a3f8b05f2492cef9474afb6d6ad69) | [a1c.io](https://a1c.io/) | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| 3312 | [ArAIstotle](https://www.coingecko.com/en/coins/araistotle) | FACY | [`0xfac77f01957ed1b3dd1cbea992199b8f85b6e886`](https://basescan.org/token/0xfac77f01957ed1b3dd1cbea992199b8f85b6e886) | [www.facticity.ai](https://www.facticity.ai) | Artificial Intelligence (AI), Meme, AI Meme, AI Agents | none matched | UNCOVERED |
| 3415 | [Regent](https://www.coingecko.com/en/coins/regent-2) | REGENT | [`0x6f89bca4ea5931edfcb09786267b251dee752b07`](https://basescan.org/token/0x6f89bca4ea5931edfcb09786267b251dee752b07) | [www.regents.sh](https://www.regents.sh/) | — | none matched | UNCOVERED |
| 3669 | [ROBA](https://www.coingecko.com/en/coins/roba) | ROBA | [`0xe88419a3fc78364cfe3de88080ee4853fab754c6`](https://basescan.org/token/0xe88419a3fc78364cfe3de88080ee4853fab754c6) | [www.robalabs.com](https://www.robalabs.com/) | Robotics | none matched | UNCOVERED |
| 3761 | [Otto AI](https://www.coingecko.com/en/coins/otto-ai) | OTTO | [`0x380337d0180db7d0df76ac4faae2fcea908ee1fc`](https://basescan.org/token/0x380337d0180db7d0df76ac4faae2fcea908ee1fc) | [useotto.xyz](https://useotto.xyz/) | Artificial Intelligence (AI), AI Agents, DeFAI | ottoai.services: 178K tx / $433 all-time, 3.3K tx / $30 in last 30d; 2.3K Bazaar calls30 | [data/AI sellers] Otto AI |
| 3790 | [Ping](https://www.coingecko.com/en/coins/ping) | PING | [`0xd85c31854c2b0fb40aaa9e2fc4da23c21f829d46`](https://basescan.org/token/0xd85c31854c2b0fb40aaa9e2fc4da23c21f829d46) | — | Meme, Base Meme | Oct 2025 pay-to-mint experiment (Chainalysis); CoinGecko lists Base contract | [token experiments] PING |
| 3808 | [Alphakek](https://www.coingecko.com/en/coins/alphakek-ai) | AIKEK | [`0x681a09a902d9c7445b3b1ab282c38d60c72f1f09`](https://basescan.org/token/0x681a09a902d9c7445b3b1ab282c38d60c72f1f09) | [www.alphakek.ai](https://www.alphakek.ai/) | Artificial Intelligence (AI), AI Agents, AI Applications, AI Framework | none matched | UNCOVERED |
| 3858 | [Heurist](https://www.coingecko.com/en/coins/heurist) | HEU | [`0xef22cb48b8483df6152e1423b19df5553bbd818b`](https://basescan.org/token/0xef22cb48b8483df6152e1423b19df5553bbd818b) | [heurist.ai](https://heurist.ai) | Artificial Intelligence (AI), DePIN, AI Agents, AI Framework | facilitator `heurist`: 8.0M tx / $30K all-time; x402 vending machine origin 105.6K tx / $43.3K | [token facilitators] Heurist |
| 3889 | [Hive Intelligence](https://www.coingecko.com/en/coins/hive-intelligence) | HINT | [`0x91da780bc7f4b7cf19abe90411a2a296ec5ff787`](https://basescan.org/token/0x91da780bc7f4b7cf19abe90411a2a296ec5ff787) | [hiveintelligence.xyz](http://hiveintelligence.xyz) | Artificial Intelligence (AI), Infrastructure, AI Agents, AI Framework | none matched | UNCOVERED |
| 3974 | [Cod3x](https://www.coingecko.com/en/coins/cod3x) | CDX | [`0xc0d3700000c0e32716863323bfd936b54a1633d1`](https://basescan.org/token/0xc0d3700000c0e32716863323bfd936b54a1633d1) | [cod3x.org](https://Cod3x.Org) | Artificial Intelligence (AI), AI Agent Launchpad, AI Framework, DeFAI | none matched | UNCOVERED |
| 4013 | [SMOL](https://www.coingecko.com/en/coins/smolcoin-2) | SMOL | [`0xa4bbac7ed5bda8ec71a1af5ee84d4c5a737bd875`](https://basescan.org/token/0xa4bbac7ed5bda8ec71a1af5ee84d4c5a737bd875) | [smolcoin.lol](https://smolcoin.lol/) | Meme, AI Meme | none matched | UNCOVERED |
| 4253 | [Gloria AI](https://www.coingecko.com/en/coins/gloria-ai) | GLORIA | [`0x3b313f5615bbd6b200c71f84ec2f677b94df8674`](https://basescan.org/token/0x3b313f5615bbd6b200c71f84ec2f677b94df8674) | [itsgloria.ai](https://itsgloria.ai/) | Artificial Intelligence (AI), AI Agents, AI Applications, AI Framework | api.itsgloria.ai origin: 19.2K tx / $359 all-time; 28 tx in last 30d | [data/AI sellers] Gloria AI |
| 4403 | [Neurobro](https://www.coingecko.com/en/coins/neurobro) | BRO | [`0xc796e499cc8f599a2a8280825d8bda92f7a895e0`](https://basescan.org/token/0xc796e499cc8f599a2a8280825d8bda92f7a895e0) | [neurobro.ai](https://neurobro.ai) | Artificial Intelligence (AI), AI Agents, AI Framework | x402scan Base seller: 30d 3 tx/$3; all-time 63 tx/$42; last 2026-09-26 | UNCOVERED |
| 4491 | [SANTA by Virtuals](https://www.coingecko.com/en/coins/santa-by-virtuals) | SANTA | [`0x815269d17c10f0f3df7249370e0c1b9efe781aa8`](https://basescan.org/token/0x815269d17c10f0f3df7249370e0c1b9efe781aa8) | [santagent.xyz](https://santagent.xyz/) | Artificial Intelligence (AI), AI Agents | none matched | [agent frameworks] Virtuals ecosystem token (inferred) |
| 4579 | [Capminal](https://www.coingecko.com/en/coins/capminal) | CAP | [`0xbfa733702305280f066d470afdfa784fa70e2649`](https://basescan.org/token/0xbfa733702305280f066d470afdfa784fa70e2649) | [www.capminal.ai](https://www.capminal.ai) | Artificial Intelligence (AI), AI Agents, DeFAI | x402scan Base seller: 30d 16 tx/$0; all-time 346 tx/$11; last 2026-10-11; Bazaar 1 res / 15 calls30 | UNCOVERED |
| 4619 | [MiroShark](https://www.coingecko.com/en/coins/miroshark) | MIROSHARK | [`0xd7bc6a05a56655fb2052f742b012d1dfd66e1ba3`](https://basescan.org/token/0xd7bc6a05a56655fb2052f742b012d1dfd66e1ba3) | [miroshark.xyz](https://miroshark.xyz) | Artificial Intelligence (AI), AI Framework | x402scan Base seller: 30d 19 tx/$19; all-time 51 tx/$50; last 2026-10-09; Bazaar 1 res / 48 calls30 | UNCOVERED |
| 4737 | [Meridian](https://www.coingecko.com/en/coins/meridian-2) | MRDN | [`0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6`](https://basescan.org/token/0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6) | [www.mrdn.finance](https://www.mrdn.finance) | Artificial Intelligence (AI) | facilitator `mrdn`: $3.79M all-time, >96% round-trip between the same wallets (see 3.6) | [token facilitators] Meridian |
| 4821 | [VPay](https://www.coingecko.com/en/coins/vpay) | VPAY | [`0x98ac5b33a4ef1151f138941c979211599c2ff953`](https://basescan.org/token/0x98ac5b33a4ef1151f138941c979211599c2ff953) | [vpay.fund](https://vpay.fund/) | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| 5161 | [x420](https://www.coingecko.com/en/coins/x420) | X420 | [`0x68e284f21d04d4d62398c290ec3ef41c97f80b07`](https://basescan.org/token/0x68e284f21d04d4d62398c290ec3ef41c97f80b07) | [x420.dev](https://x420.dev) | Meme | x8004.x420.dev origin: 144.8K tx / $31.2K all-time | [token experiments] x402-branded token |
| n/a | [Maya World](https://www.coingecko.com/en/coins/maya-world) | MAYA | [`0x072915a43ac255cde1fa568218e5b6b10d0cb10f`](https://basescan.org/token/0x072915a43ac255cde1fa568218e5b6b10d0cb10f) | [www.mayaworld.co](https://www.mayaworld.co) | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| 5759 | [Aurra by Virtuals](https://www.coingecko.com/en/coins/aurra-by-virtuals) | AURA | [`0xdcaa5e062b2be18e52ea6ed7ba232538621ddc10`](https://basescan.org/token/0xdcaa5e062b2be18e52ea6ed7ba232538621ddc10) | [aurracloud.com](https://aurracloud.com) | Artificial Intelligence (AI), AI Applications, AI Framework | x402scan Base seller: 30d 0 tx/$0; all-time 1.2K tx/$118; last 2026-05-10 | [token facilitators] AurraCloud? (name match unverified) |
| 6159 | [Replicat-One by Virtuals](https://www.coingecko.com/en/coins/replicat-one-by-virtuals) | RCAT | [`0x6af73d4579c70a24d52e4f4b43eecb2a75019f94`](https://basescan.org/token/0x6af73d4579c70a24d52e4f4b43eecb2a75019f94) | [replicats.ai](https://replicats.ai/) | Artificial Intelligence (AI), AI Agents | none matched | [agent frameworks] Virtuals ecosystem token (inferred) |
| n/a | [MIO](https://www.coingecko.com/en/coins/mio) | MIO | [`0xe19e7429ab6c1f9dd391faa88fbb940c7d22f18f`](https://basescan.org/token/0xe19e7429ab6c1f9dd391faa88fbb940c7d22f18f) | [www.miocoin.lol](https://www.miocoin.lol/) | Meme, AI Meme | none matched | UNCOVERED |
| n/a | [HEIR](https://www.coingecko.com/en/coins/heir) | HEIR | [`0x01e75e59eabf83c85360351a100d22e025a75bc2`](https://basescan.org/token/0x01e75e59eabf83c85360351a100d22e025a75bc2) | [heir.es](https://heir.es) | — | none matched | UNCOVERED |
| n/a | [Trackgood AI](https://www.coingecko.com/en/coins/trackgood-ai) | TRAI | [`0xdd32659b1e7a6a6b3c6e96cd8a4c936bcfea0607`](https://basescan.org/token/0xdd32659b1e7a6a6b3c6e96cd8a4c936bcfea0607) | [trackgood.ai](https://trackgood.ai/) | Artificial Intelligence (AI), AI Agents, AI Applications | none matched | UNCOVERED |
| 6578 | [Loky by Virtuals](https://www.coingecko.com/en/coins/loky-by-virtuals) | LOKY | [`0x1a3e429d2d22149cc61e0f539b112a227c844aa3`](https://basescan.org/token/0x1a3e429d2d22149cc61e0f539b112a227c844aa3) | [lokyai.com](https://lokyai.com/) | Artificial Intelligence (AI), AI Agents | none matched | [agent frameworks] Virtuals ecosystem token (inferred) |
| 6731 | [StarkBot](https://www.coingecko.com/en/coins/starkbot) | STARKBOT | [`0x587cd533f418825521f3a1daa7ccd1e7339a1b07`](https://basescan.org/token/0x587cd533f418825521f3a1daa7ccd1e7339a1b07) | [www.starkbot.ai](https://www.starkbot.ai/) | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| 6752 | [Dobi](https://www.coingecko.com/en/coins/dobi-2) | DOBI | [`0x931ef8053e997b1bab68d1e900a061305c0ff4fb`](https://basescan.org/token/0x931ef8053e997b1bab68d1e900a061305c0ff4fb) | [dobi.guru](https://dobi.guru) | Artificial Intelligence (AI), Meme, AI Agents | none matched | UNCOVERED |
| 6777 | [Arbus](https://www.coingecko.com/en/coins/arbus) | ARBUS | [`0xbdc27118ca76b375c6887b0ff068afb03dfc21a0`](https://basescan.org/token/0xbdc27118ca76b375c6887b0ff068afb03dfc21a0) | [arbus.ai](https://arbus.ai/) | Artificial Intelligence (AI), AI Applications | none matched | UNCOVERED |
| 6955 | [WachAI](https://www.coingecko.com/en/coins/wachxbt) | WACH | [`0xcc9ad02796dec5f4f0710df80c1f011af85eb9e1`](https://basescan.org/token/0xcc9ad02796dec5f4f0710df80c1f011af85eb9e1) | [wach.ai](https://wach.ai/) | Artificial Intelligence (AI), AI Agents | x402scan Base seller: 30d 185 tx/$1; all-time 524 tx/$22; last 2026-10-11; Bazaar 1 res / 5 calls30 | UNCOVERED |
| n/a | [AInalyst](https://www.coingecko.com/en/coins/ainalyst) | AIN | [`0xe47dd5197c5b5194cbe10b0333ed45570fb63eb0`](https://basescan.org/token/0xe47dd5197c5b5194cbe10b0333ed45570fb63eb0) | [ainalyst.xyz](https://ainalyst.xyz/) | Artificial Intelligence (AI), AI Agents, AI Applications | ainalyst-api.xyz (AinX402): 8.9M tx / $2.74M all-time, mostly Oct-Dec 2025; last 2026-08-30 | UNCOVERED |
| n/a | [TRANSLATE](https://www.coingecko.com/en/coins/translate) | TRANSLATE | [`0x5cd9166494673c15cbdfe8750def8bbab80a5b07`](https://basescan.org/token/0x5cd9166494673c15cbdfe8750def8bbab80a5b07) | [www.apinow.fun](https://www.apinow.fun/try/apinowfun/translate-TRANSLATE) | — | x402scan Base seller: 30d 78 tx/$1; all-time 14K tx/$228; last 2026-10-09 | UNCOVERED |
| n/a | [Halo](https://www.coingecko.com/en/coins/halo-3) | HALO | [`0x0a56431ecc9d0b39be0b1e27e795f4c4f19d0ba3`](https://basescan.org/token/0x0a56431ecc9d0b39be0b1e27e795f4c4f19d0ba3) | [halo.zhc.company](https://halo.zhc.company/) | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| 7376 | [Karum](https://www.coingecko.com/en/coins/karum) | KARUM | [`0xf3280115245a7470e7bbdd35e2b4f4094f511443`](https://basescan.org/token/0xf3280115245a7470e7bbdd35e2b4f4094f511443) | [www.karum.ai](https://www.karum.ai/) | — | none matched | UNCOVERED |
| 7667 | [Otonix](https://www.coingecko.com/en/coins/otonix) | OTX | [`0xf7e2a6226ffe0693dd85406ac3a8917cbea5dc40`](https://basescan.org/token/0xf7e2a6226ffe0693dd85406ac3a8917cbea5dc40) | — | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| n/a | [NOD](https://www.coingecko.com/en/coins/nod) | NOD | [`0xdfb51ec9941cc684b72dc2b0f532d74a244e4ccf`](https://basescan.org/token/0xdfb51ec9941cc684b72dc2b0f532d74a244e4ccf) | [0xnod.com](https://0xnod.com/) | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| n/a | [Sniper Search](https://www.coingecko.com/en/coins/sniper-search) | SS | [`0xa2d4aec94ba0896d95ccc5451c9525b9ec0314de`](https://basescan.org/token/0xa2d4aec94ba0896d95ccc5451c9525b9ec0314de) | [snipersearch.fun](https://snipersearch.fun/) | — | x402scan Base seller: 30d 0 tx/$0; all-time 144 tx/$5; last 2026-06-18 | UNCOVERED |
| 8741 | [$TRUST ME BROs by Virtuals](https://www.coingecko.com/en/coins/trust-me-bros-by-virtuals) | TRUST | [`0xc841b4ead3f70be99472ffdb88e5c3c7af6a481a`](https://basescan.org/token/0xc841b4ead3f70be99472ffdb88e5c3c7af6a481a) | [trustmebros.fun](http://trustmebros.fun) | Meme, AI Meme | none matched | [agent frameworks] Virtuals ecosystem token (inferred) |
| n/a | [The SWARM](https://www.coingecko.com/en/coins/the-swarm) | SWARM | [`0xea87169699dabd028a78d4b91544b4298086baf6`](https://basescan.org/token/0xea87169699dabd028a78d4b91544b4298086baf6) | [www.slamai.xyz](https://www.slamai.xyz/) | Artificial Intelligence (AI), AI Agents | none matched | UNCOVERED |
| n/a | [ZorbyAI](https://www.coingecko.com/en/coins/zorbyai) | $ZORBYAI | [`0x3e04dee527a90ddfa1fe6f9e12a4d62677d00071`](https://basescan.org/token/0x3e04dee527a90ddfa1fe6f9e12a4d62677d00071) | [zorby.wtf](https://zorby.wtf/) | — | none matched | UNCOVERED |
| n/a | [x402MKT](https://www.coingecko.com/en/coins/x402mkt) | LOOP | [`0xa763b711b55935f6d7ba2f93e1adf741e2446b07`](https://basescan.org/token/0xa763b711b55935f6d7ba2f93e1adf741e2446b07) | [www.clanker.world](https://www.clanker.world/clanker/0xA763B711B55935f6D7BA2f93E1adF741E2446B07) | Infrastructure | none matched | [token experiments] x402-branded token (x402MKT) |
| n/a | [Token Metrics AI [OLD]](https://www.coingecko.com/en/coins/token-metrics-ai) | TMAI | [`0xca4569949699d56e1834efe9f58747ca0f151b01`](https://basescan.org/token/0xca4569949699d56e1834efe9f58747ca0f151b01) | [www.tokenmetrics.com](https://www.tokenmetrics.com/) | Artificial Intelligence (AI), AI Agents, DeFAI | x402scan Base seller: 30d 0 tx/$0; all-time 3.2K tx/$105; last 2025-12-10 | UNCOVERED |
| n/a | [Dealer Node](https://www.coingecko.com/en/coins/dealer-node) | DNODE | [`0xa7f6e8a35d83228cc6c241c8dd0fb687552f75d1`](https://basescan.org/token/0xa7f6e8a35d83228cc6c241c8dd0fb687552f75d1) | [dealernode.app](https://dealernode.app) | — | none matched | UNCOVERED |
| n/a | [BluePay](https://www.coingecko.com/en/coins/bluepay) | BLUE | [`0x15eda1086c54c148037597e9dc60e5a87b618aa1`](https://basescan.org/token/0x15eda1086c54c148037597e9dc60e5a87b618aa1) | [bluepay.network](http://bluepay.network) | — | none matched | UNCOVERED |

**1.3b Category tokens with no Base contract on CoinGecko (73)**

| CG rank | Token | Ticker | Chains per CoinGecko (non-Base) | Group |
|---|---|---|---|---|
| 137 | [Unibase](https://www.coingecko.com/en/coins/unibase) | UB | binance-smart-chain, ethereum | UNCOVERED |
| 526 | [Concordium](https://www.coingecko.com/en/coins/concordium) | CCD | (none listed) | UNCOVERED |
| 1217 | [Brickken](https://www.coingecko.com/en/coins/brickken) | BKN | ethereum, binance-smart-chain | UNCOVERED |
| 1220 | [heyAura](https://www.coingecko.com/en/coins/adex) | ADX | ethereum, robinhood, binance-smart-chain | UNCOVERED |
| 1316 | [PayAI Network](https://www.coingecko.com/en/coins/payai-network-2) | PAYAI | solana | [token facilitators] PayAI |
| 1465 | [Codec Flow](https://www.coingecko.com/en/coins/codec-flow) | CODEC | solana, peaq | UNCOVERED |
| 2320 | [Amiko](https://www.coingecko.com/en/coins/amiko) | AMIKO | solana | UNCOVERED |
| 2449 | [Zauthx402](https://www.coingecko.com/en/coins/zauthx402) | ZAUTH | solana | [x402 apps and trust] Zauth |
| 3194 | [NodeOps](https://www.coingecko.com/en/coins/node-2) | NODE | ethereum, binance-smart-chain | UNCOVERED |
| 3466 | [Avo](https://www.coingecko.com/en/coins/avo) | AVO | solana | UNCOVERED |
| 3473 | [Coral Protocol](https://www.coingecko.com/en/coins/coral-protocol) | CORAL | solana | UNCOVERED |
| 3675 | [XONA AGENT](https://www.coingecko.com/en/coins/xona-agent) | XONA | solana | UNCOVERED |
| 3822 | [Homebrew Robotics](https://www.coingecko.com/en/coins/homebrew-robotics-club) | BREW | solana, peaq | UNCOVERED |
| 3942 | [Magic Hash](https://www.coingecko.com/en/coins/magic-hash) | MHA | binance-smart-chain | UNCOVERED |
| 4031 | [Opus Genesis](https://www.coingecko.com/en/coins/opus-2) | OPUS | solana | UNCOVERED |
| 4085 | [Orbofi AI](https://www.coingecko.com/en/coins/orbofi-ai) | OBI | ethereum, binance-smart-chain | UNCOVERED |
| 4102 | [Dexter AI](https://www.coingecko.com/en/coins/dexter-ai) | DEXTER | solana | [rivals] Dexter |
| 4311 | [Ace Data Cloud](https://www.coingecko.com/en/coins/ace-data-cloud-2) | ACE | solana | UNCOVERED |
| 4372 | [0xGasless](https://www.coingecko.com/en/coins/0xgasless-2) | 0XGAS | ethereum | UNCOVERED |
| 4659 | [Jatevo](https://www.coingecko.com/en/coins/jatevo) | JTVO | solana | UNCOVERED |
| 4848 | [ZARA AI](https://www.coingecko.com/en/coins/zara-ai) | ZARA | solana | UNCOVERED |
| 5281 | [Eliza](https://www.coingecko.com/en/coins/eliza) | ELIZA | solana | [agent frameworks] elizaOS |
| n/a | [Agent Virtual Machine](https://www.coingecko.com/en/coins/agent-virtual-machine) | AVM | ethereum | UNCOVERED |
| 5448 | [Cra Agent](https://www.coingecko.com/en/coins/cra-agent) | CRA | arc | UNCOVERED |
| 5610 | [Dice Protocol](https://www.coingecko.com/en/coins/dice-protocol) | DICE | robinhood | UNCOVERED |
| 5633 | [MESH Gateway](https://www.coingecko.com/en/coins/mesh-gateway) | MESH | robinhood | UNCOVERED |
| 5669 | [x402 Singularity Layer](https://www.coingecko.com/en/coins/x402-singularity-layer) | SGL | solana | [token experiments] x402-branded token |
| 5725 | [Naven Network](https://www.coingecko.com/en/coins/naven-network) | NAVEN | robinhood | UNCOVERED |
| 5849 | [WURK](https://www.coingecko.com/en/coins/wurk) | WURK | solana | UNCOVERED |
| 6129 | [Hood Domains](https://www.coingecko.com/en/coins/hooddomains) | HD | robinhood | UNCOVERED |
| 6124 | [Primer](https://www.coingecko.com/en/coins/kilt-protocol-3) | PR | robinhood | [token facilitators] Primer |
| 6150 | [MOSS AI](https://www.coingecko.com/en/coins/moss) | MOSS | solana | UNCOVERED |
| 6177 | [Arcus Network](https://www.coingecko.com/en/coins/arcus-network) | ARCUS | arc | UNCOVERED |
| 6253 | [Syra Agent](https://www.coingecko.com/en/coins/syra-agent) | SYRA | solana | UNCOVERED |
| 6269 | [Fuci](https://www.coingecko.com/en/coins/fuci) | FUCI | arc | UNCOVERED |
| 6354 | [hey.lol](https://www.coingecko.com/en/coins/hey-lol) | HEY | solana | UNCOVERED |
| n/a | [QUAIN](https://www.coingecko.com/en/coins/quain) | QUAIN | solana | UNCOVERED |
| 6721 | [PayAI Network [OLD]](https://www.coingecko.com/en/coins/payai-network) | PAYAI | solana | [token facilitators] PayAI |
| 6763 | [blormmy](https://www.coingecko.com/en/coins/blormmy) | BLORMMY | solana | UNCOVERED |
| n/a | [ChainAware.ai](https://www.coingecko.com/en/coins/chainaware-ai) | AWARE | binance-smart-chain | UNCOVERED |
| n/a | [Praxis](https://www.coingecko.com/en/coins/praxis) | PRXS | ethereum | UNCOVERED |
| n/a | [OOPS](https://www.coingecko.com/en/coins/oops) | OOPS | solana | UNCOVERED |
| n/a | [AgentHub](https://www.coingecko.com/en/coins/agenthub) | DIRA | solana | UNCOVERED |
| n/a | [sparkleware](https://www.coingecko.com/en/coins/sparkleware) | SPARKLE | robinhood | UNCOVERED |
| 8008 | [Ace Data Cloud](https://www.coingecko.com/en/coins/ace-data-cloud) | $ACE | solana | UNCOVERED |
| 8076 | [SVM Claw](https://www.coingecko.com/en/coins/svm-claw) | SVM | solana | UNCOVERED |
| n/a | [Laika AI](https://www.coingecko.com/en/coins/laika-ai) | LKI | binance-smart-chain | UNCOVERED |
| n/a | [Foundry](https://www.coingecko.com/en/coins/foundry) | FDRY | solana | UNCOVERED |
| 8319 | [x4Pay](https://www.coingecko.com/en/coins/x4pay) | X4PAY | solana | [token experiments] x402-branded token |
| 8778 | [RADR](https://www.coingecko.com/en/coins/radr) | RADR | solana | UNCOVERED |
| 8821 | [FREGO](https://www.coingecko.com/en/coins/frego) | FREGO | solana | UNCOVERED |
| 8884 | [Animus](https://www.coingecko.com/en/coins/animus) | ANIMUS | binance-smart-chain | UNCOVERED |
| n/a | [Switchboard](https://www.coingecko.com/en/coins/switchboard) | SWTCH | solana | UNCOVERED |
| 9042 | [x402jobs](https://www.coingecko.com/en/coins/x402jobs) | JOBS | solana | UNCOVERED |
| n/a | [Khorus](https://www.coingecko.com/en/coins/khorus) | KHO | binance-smart-chain | UNCOVERED |
| n/a | [Artificer](https://www.coingecko.com/en/coins/artificer) | ARTI | solana | UNCOVERED |
| 9437 | [Robinhood Payments Protocol](https://www.coingecko.com/en/coins/robinhood-payments-protocol) | RPP402 | robinhood | [token experiments] x402-branded token |
| n/a | [DND](https://www.coingecko.com/en/coins/dnd) | DND | solana | UNCOVERED |
| n/a | [Scry Agent Ward](https://www.coingecko.com/en/coins/scry-agent-ward) | SCRY | robinhood | UNCOVERED |
| 9614 | [AgentBank x402 Protocol](https://www.coingecko.com/en/coins/agentbank-x402-protocol) | AGENTBANK | solana | [token experiments] x402-branded token |
| 9693 | [Token](https://www.coingecko.com/en/coins/token-3) | TOKEN | solana | UNCOVERED |
| n/a | [CollabraChain](https://www.coingecko.com/en/coins/collabrachain) | COLLA | solana | UNCOVERED |
| 9772 | [Stakefy](https://www.coingecko.com/en/coins/stakefy) | SFY | solana | UNCOVERED |
| n/a | [HyperAGI](https://www.coingecko.com/en/coins/hyperdust) | HYPT | arbitrum-one, solana | UNCOVERED |
| n/a | [REL](https://www.coingecko.com/en/coins/rel) | REL | solana | UNCOVERED |
| n/a | [Horizon Oracles](https://www.coingecko.com/en/coins/horizon-oracles) | HORIZON | binance-smart-chain | UNCOVERED |
| n/a | [ShadowOS](https://www.coingecko.com/en/coins/shadowos) | SOS | solana | UNCOVERED |
| n/a | [SimiliScan](https://www.coingecko.com/en/coins/similiscan) | SMS | ethereum | UNCOVERED |
| 10245 | [Readia.io](https://www.coingecko.com/en/coins/readia-io) | READ | solana | UNCOVERED |
| n/a | [zk402](https://www.coingecko.com/en/coins/zk402) | ZK402 | solana | [token experiments] x402-branded token |
| n/a | [SolenceAi](https://www.coingecko.com/en/coins/solenceai) | SAI | solana | UNCOVERED |
| n/a | [Veilra by ElizaOS](https://www.coingecko.com/en/coins/veilraos) | VEILRA | solana | [agent frameworks] elizaOS (Veilra by ElizaOS) |
| n/a | [MPP TestKit](https://www.coingecko.com/en/coins/mpp-testkit) | MTK | solana | UNCOVERED |

#### 1.4 Sellers and projects seen in Base usage data but absent from the official directory
Source: x402scan per-recipient daily series (candidate recipients: top 70 by USDC and by tx in the 7-day, 30-day and all-time lists, plus Meridian/FluxA counterparties) summed over 2026-04-11 to 2026-10-11, x402scan 30-day lists, the Bazaar API, and registry titles. Category is my reading of the project's own title or description. "Chains seen" combines x402scan Base, x402scan Solana top-100 lists and Bazaar `accepts`.

| Project | Category | Token (Base contract) | Chains seen | Base last 6 months (tx / USDC) | Base last 30d (tx / USDC) | Solana (x402scan top-100 lists) | Bazaar calls 30d | Last Base settlement | Status | Group |
|---|---|---|---|---|---|---|---|---|---|---|
| [BlockRun](https://blockrun.ai) ([x402scan](https://www.x402scan.com/recipient/0xe9030014f5dae217d0a152f02a043567b16c1abf)) | LLM gateway / router (seller + agent routing) | none found (not in CoinGecko x402 category) | Base, Solana | 27.0M / $450K | 83K / $1.5K | 30d 227K tx/$2.9K; all-time 22.5M tx/$293K | 79K | 2026-10-11 | active | UNCOVERED |
| [AX1 Console](https://ax1.vc) ([x402scan](https://www.x402scan.com/recipient/0x7284d41b5b852f2bd4c99bdf95043d84452d299c)) | Agent "launchpad" console; paid Base-token verdict API | none found | Base | 412K / $8.2K | 407K / $8.1K | not in top-100 lists | 409K | 2026-10-11 | active | UNCOVERED |
| [Cluster Protocol](https://api.clusterprotocol.ai) ([x402scan](https://www.x402scan.com/recipient/0x68396bd35874695ad86cd29410bd80a550991a2b)) | AI/agent infra ("Liberation Engine for Internet Capital Market") | CP 0x001aad84c21a5cd4d696c56d44866e9703c43f77 (CoinGecko coin list; not in x402 category) | Base | 533K / $262K | 67K / $55K | not in top-100 lists | — | 2026-10-10 | active | UNCOVERED |
| [ATXP](https://atxp.ai) ([x402scan](https://www.x402scan.com/recipient/0x7f9d1a879750168b8f4a59734b1262d1778fdb5a)) | Agent account / payments | none found | Base, Solana | 314K / $122K | 0 / $0 | 30d 0 tx/$0; all-time 568K tx/$232K | — | 2026-06-18 | dormant (114d idle) | UNCOVERED |
| [x402.boats](https://mcp.x402.boats) ([x402scan](https://www.x402scan.com/recipient/0xb0af3ccf9154f81af07a194150113523767d7de0)) | Game for AI agents | none found | Base | 29K / $208K | 0 / $0 | not in top-100 lists | — | 2026-09-04 | dormant (36d idle) | UNCOVERED |
| [Vishwa](https://api.vishwalab.com) ([x402scan](https://www.x402scan.com/recipient/0x6a5e7d954f49712abf3f873f037ec845b7b8c666)) | API seller (title "Vishwa"; function not stated) | none found | Base, Solana | 481K / $42K | 10 / $0 | 30d 106K tx/$106; all-time 728K tx/$752 | — | 2026-09-15 | low activity (10 tx/calls in 30d) | UNCOVERED |
| [KORUS](https://www.korusmusic.co) ([x402scan](https://www.x402scan.com/recipient/0x8a12157b27c22fb239e558dc3cb43c7d1a8c0881)) | Consumer music-creation app paid via x402 | none found | Base | 24K / $19K | 24K / $19K | not in top-100 lists | — | 2026-10-11 | active | UNCOVERED |
| [MineBean](https://api.minebean.com) ([x402scan](https://www.x402scan.com/recipient/0x78f993378ff7890daac1689f79e7db2291e73928)) | Game / mining app (title "MineBean") | none found | Base | 154K / $15K | 0 / $0 | not in top-100 lists | — | 2026-08-03 | dormant (69d idle) | UNCOVERED |
| [claw402](https://claw402.ai) ([x402scan](https://www.x402scan.com/recipient/0xa9dd7cc9cbf0e05551332209289f04be36bc2315)) | x402 API payment gateway (micro-calls) | CLAW402 on Solana only (CoinGecko coin list) | Base | 4.87M / $9.5K | 424K / $940 | not in top-100 lists | — | 2026-10-11 | active | UNCOVERED |
| [FortClaw](https://mcp.fortclaw.com) ([x402scan](https://www.x402scan.com/recipient/0xf000ab8b02aa5c52b62bdb10bf63312317e994fc)) | Territory game for AI agents | none found | Base | 59K / $5.3K | 18K / $1.5K | not in top-100 lists | — | 2026-10-11 | active | UNCOVERED |
| [BotPay](https://api.botpay.network) ([x402scan](https://www.x402scan.com/recipient/0xcc1984e79726e7a0ae2b9df2ac9e79fb4983930e)) | Agent payment network / video-access API | none found | Base, Solana | 48K / $4.0K | 21K / $2.1K | 30d 12K tx/$488; all-time 20K tx/$855 | 4 | 2026-10-08 | active | UNCOVERED |
| [X Pay](https://www.api-xpay.com) ([x402scan](https://www.x402scan.com/recipient/0x589a2314a2e05f45e40c4823da3ba58d421db3d8)) | Payment-receipt / health-check API ("X Pay") | none found | Base | 42K / $3.4K | 42K / $3.4K | not in top-100 lists | 42K | 2026-10-11 | active | UNCOVERED |
| [BaseHub](https://basehub-alpha.vercel.app) ([x402scan](https://www.x402scan.com/recipient/0x7d2ceb7a0e0c39a3d0f7b5b491659fde4bb7bcfe)) | Games / web3 tools ("earn XP") | none found | Base | 41K / $3.0K | 5.0K / $284 | not in top-100 lists | — | 2026-10-11 | active | UNCOVERED |
| [Orbis API](https://orbisapi.com) ([x402scan](https://www.x402scan.com/recipient/0x2bb72231eed303cc91a462a1fa738b42b6a9ac6d)) | API marketplace (1,000+ APIs at $0.01) | none found | Base | 439K / $2.1K | 0 / $0 | not in top-100 lists | — | 2026-06-28 | dormant (104d idle) | UNCOVERED |
| [OneShot Agent](https://win.oneshotagent.com) ([x402scan](https://www.x402scan.com/recipient/0x9fb365e4e9385e2a39febad70368267e6f571d9a)) | Agent tool APIs (web-read, enrichment) | none found | Base | 123K / $1.0K | 46K / $390 | not in top-100 lists | 45K | 2026-10-11 | active | UNCOVERED |
| [agentutility](https://x402.agentutility.ai) ([x402scan](https://www.x402scan.com/recipient/0x6c0752c09e7f6fa6526fcdf40e456a159ebb5621)) | Paid x402 API catalog | none found | Base, Solana | 69K / $1.7K | 9.4K / $244 | 30d 2.1K tx/$53; all-time 7.6K tx/$160 | 317 | 2026-10-11 | active | UNCOVERED |
| [KEYRING AGENT](https://keyring-agent.blockchhub.link) ([x402scan](https://www.x402scan.com/recipient/0x17cd53c04d707ef0dd615ef56c633f02915a7905)) | Token-send execution-fee API | none found | Base | 24K / $1.2K | 24K / $1.2K | not in top-100 lists | 25K | 2026-10-11 | active | UNCOVERED |
| [JarvisClaw](https://api.jarvisclaw.ai) ([x402scan](https://www.x402scan.com/recipient/0xdc59fa7b64988b846e76ec9849bb68f889071506)) | API seller ("JarvisClaw API") | none found | Base, Solana | 33K / $1.0K | 7.7K / $38 | 30d 0 tx/$0; all-time 180 tx/$53 | 1.1K | 2026-10-11 | active | UNCOVERED |
| [Losbeto](https://losbeto-production-dd7c.up.railway.app) ([x402scan](https://www.x402scan.com/recipient/0xd5ba9711a3d052846a3695c70e7fcb8b3168fe7d)) | LLM inference + market data / trading swarm | none found | Base, Algorand, Polygon | 9.0K / $623 | 5.8K / $394 | not in top-100 lists | 5.3K | 2026-10-11 | active | UNCOVERED |
| [Agent402](https://agent402.tools) ([x402scan](https://www.x402scan.com/recipient/0xabf4fabd7c416fb67202e5f9002389fc75e2a9d0)) | 500+ pay-per-call tools; demand-intel site (intel.agent402.app) | none found | Base, Solana, Algorand, Arbitrum, Avalanche, Celo | 38K / $579 | 10K / $264 | 30d 168 tx/$2; all-time 3.1K tx/$47 | 8.1K | 2026-10-11 | active | UNCOVERED |
| [x402node](https://api.x402node.dev) ([x402scan](https://www.x402scan.com/recipient/0x4466d4a84b7c49a6a094ec6eef4a0712d6dd125e)) | 528 pay-per-call APIs (data, dev tools) | none found | Base, Solana | 21K / $503 | 4.1K / $81 | 30d 0 tx/$0; all-time 2.4K tx/$97 | 3.4K | 2026-10-11 | active | UNCOVERED |
| [OneSource](https://api.onesource.io) ([x402scan](https://www.x402scan.com/recipient/0x52e29e0d2aa49bfbfc548c0a9f2196f4aa51f3ea)) | Blockchain data API for agents | none found | Base | 98K / $408 | 13K / $100 | not in top-100 lists | 13K | 2026-10-11 | active | UNCOVERED |
| [Pocket Network (Agentic Portal)](https://agent.pocket.network) ([x402scan](https://www.x402scan.com/recipient/0xf732ea490c5766071785a2310523f7fa2cebb829)) | Agent-only messaging + security APIs; x402/MPP APIs | POKT 0x764a726d9ced0433a8d7643335919deb03a9a935 (Base; not in x402 category) | Base | 14K / $70 | 14K / $70 | not in top-100 lists | 14K | 2026-10-11 | active | UNCOVERED |
| [Apify AGI](https://agi.apify.com) ([x402scan](https://www.x402scan.com/recipient/0x4aabe17c239ef71c3a26ba7c2b3e0aebbfc1df26)) | Agent general interface (scraping actors) | none (company) | Base | 2.1K / $2.5K | 368 / $695 | not in top-100 lists | 367 | 2026-10-11 | active | UNCOVERED |
| [Strale](https://api.strale.io) ([x402scan](https://www.x402scan.com/recipient/0x66d7c2f952362bfb24fd7f02a9bec9c754ea83bc)) | 250+ business-data / compliance capabilities | none found | Base | 13K / $805 | 3.3K / $183 | not in top-100 lists | 3.4K | 2026-10-11 | active | UNCOVERED |
| [Arkham API](https://api.arkm.com) ([x402scan](https://www.x402scan.com/recipient/0x942bd3e3073543c674efc0c378d5bce20f9120c1)) | On-chain intelligence API | none (Arkham token not matched) | Base, Solana | 1.3K / $1.0K | 570 / $141 | 30d 16 tx/$3; all-time 179 tx/$44 | 220 | 2026-10-11 | active | UNCOVERED |
| [Glassnode](https://x402.glassnode.com) | On-chain metrics API | none (company) | Base | not matched in x402scan registry (Bazaar only) | not matched | not in top-100 lists | 1.2K | 2026-10-11 | active | UNCOVERED |
| [Tavily](https://x402.tavily.com) | Web search API | none (company) | Base | not matched in x402scan registry (Bazaar only) | not matched | not in top-100 lists | 978 | 2026-10-08 | active | UNCOVERED |
| [Orthogonal](https://x402.orthogonal.com) | API gateway (157 resources; x402 Foundation general member) | none found | Base, Monad | not matched in x402scan registry (Bazaar only) | not matched | not in top-100 lists | 2.0K | 2026-10-11 | active | UNCOVERED |
| [Chainlink for Agents](https://agents.chain.link) | Chainlink workflow-execution API for agents | LINK 0x88fb150bdc53a65fe94dea0c9ba0a6daf8c6e196 (in CoinGecko x402 category) | Base | not matched in x402scan registry (Bazaar only) | not matched | not in top-100 lists | 46K | 2026-10-06 | active | UNCOVERED |
| [Zapper API](https://public.zapper.xyz) ([x402scan](https://www.x402scan.com/recipient/0x43a2a720cd0911690c248075f4a29a5e7716f758)) | Portfolio data API | none found | Base | 26K / $46 | 0 / $0 | not in top-100 lists | — | 2026-08-03 | dormant (68d idle) | UNCOVERED |
| [ArDrive Turbo](https://turbo.ardrive.io) ([x402scan](https://www.x402scan.com/recipient/0x6a0a10ffd285c971b841bee8892878c0d583bf67)) | Payment service for Arweave uploads | none found | Base | 203K / $1.0K | 203K / $1.0K | not in top-100 lists | — | 2026-10-11 | active | UNCOVERED |
| [Anyspend (B3)](https://x402.anyspend.com) ([x402scan](https://www.x402scan.com/recipient/0x1e8e93cb91778e5b1a3639706789195a838960f8)) | x402 payments + facilitator (also in 1B) | ANY 0xc17dda248e2d50fc006d8febb5a406dd31972712 | Base | 15K / $25K | 0 / $0 | not in top-100 lists | — | 2026-08-17 | dormant (54d idle) | UNCOVERED |
| [Aubrai (Bio)](https://aubr.ai) ([x402scan](https://www.x402scan.com/recipient/0x44dc2dceaa22c7ef6b2e2cf2362fd3fb476b7c2c)) | Longevity-research agent API | AUBRAI 0x9d56c29e820dd13b0580b185d0e0dc301d27581d | Base | 14K / $321 | 2.3K / $63 | not in top-100 lists | 2.3K | 2026-10-10 | active | UNCOVERED |
| [Vaaya](https://vaaya.ai) ([x402scan](https://www.x402scan.com/recipient/0x7c655d3d3944bd27994dd81a036c3afb19806c40)) | Credit accounts / prepaid balance for agents (+ tokenized shares) | none found | Base | 3.8K / $121 | 1.8K / $51 | not in top-100 lists | 1.6K | 2026-10-10 | active | UNCOVERED |
| [Locus x402 wrappers](https://paywithlocus.com) ([x402scan](https://www.x402scan.com/recipient/0x3c5cbe28eca3b96023c45d3f877da834f1c7d5fa)) | Pay-per-use wrappers for Gemini, Stability AI, etc. (also in 1A) | none found (CoinGecko "Locus Chain" is a different project) | Base | 38K / $106 | 36K / $57 | not in top-100 lists | 328 | 2026-10-10 | active | UNCOVERED |
| [Merit "Stable*" family (StableEnrich, StableSocial, StableTravel, StableEmail, StableStudio)](https://stableenrich.dev) ([x402scan](https://www.x402scan.com/recipient/0x325bdf6f7efab24a2210c48c1b64cab2eae1d430)) | Pay-per-call data APIs run by Merit Systems (assigned) | none | Base, Solana | 480K / $14K | 57K / $1.7K | 30d 0 tx/$0; all-time 8.6K tx/$252 | 35K | 2026-10-11 | active | [non-token infra] Merit Systems |

#### 1.5 Oct-Dec 2025 mint/launchpad-era recipients (the wash/spike evidence) and their status
These belong to the assigned [token experiments] group (and Virtuals ACP to [agent frameworks]); they are listed because they explain the October 2025 spike and show which are dead. Names are the titles in x402scan's registry. Recipient addresses link to x402scan.

| Recipient (x402scan) | Name seen in x402scan registry | Oct-Dec 2025 tx / USDC | Peak month (tx) | Last 6 months (Apr 11-Oct 11 2026) tx / USDC | Last tx in series | Status |
|---|---|---|---|---|---|---|
| [`0xf7b1356c...`](https://www.x402scan.com/recipient/0xf7b1356cfed0eebe01d76da7ba9e9f8bf12d9d57) | x402.arvos.xyz (ARVOS token page / "Arvos AI by Virtuals") | 12.4M / $11.51M | 2025-11 (12.1M) | 0 / $0 | 2025-11-28 | dead (317d idle) |
| [`0x07737a1f...`](https://www.x402scan.com/recipient/0x07737a1fb3863202bcd3c7408b801eed68604d39) | QRBase ($SCAN) | 886K / $7.00M | 2025-11 (886K) | 40 / $1 | 2026-08-31 | dormant (41d idle) |
| [`0x45a33ac6...`](https://www.x402scan.com/recipient/0x45a33ac6db4455460b364a1fc1ae8c489bc644a7) | Barvis (api.barvis.io) | 10.9M / $2.60M | 2025-11 (10.8M) | 0 / $0 | 2025-11-28 | dead (317d idle) |
| [`0x5e50d23e...`](https://www.x402scan.com/recipient/0x5e50d23ec14ea4436582029a25313e5048e01d10) | AinX402 / AInalyst (ainalyst-api.xyz) | 8.80M / $2.73M | 2025-11 (6.42M) | 9 / $3 | 2026-08-30 | dormant (42d idle) |
| [`0x4e9bce25...`](https://www.x402scan.com/recipient/0x4e9bce2547a9491b09ed092c433b19888e665edb) | Canza (api.canza.app) | 6.47M / $2.06M | 2025-11 (6.17M) | 0 / $0 | 2025-11-28 | dead (317d idle) |
| [`0x66fa4d79...`](https://www.x402scan.com/recipient/0x66fa4d79ca84016b42352be33c908dd812952ec8) | AIsa Payment Gateway (pay.lnpay.ai, openapi.aisa.one) | 31.6M / $416K | 2025-12 (19.2M) | 121 / $2 | 2026-08-07 | dormant (65d idle) |
| [`0x0495d60c...`](https://www.x402scan.com/recipient/0x0495d60c927b97d67d5018c6aa65c9b2bebaeed9) | t54 x402-secure API (x402-secure-api.t54.ai) | 21.5M / $22K | 2025-12 (13.3M) | 353 / $5 | 2026-10-10 | active |
| [`0x27599d82...`](https://www.x402scan.com/recipient/0x27599d824bbb4f506f985af865d840f61ba848c8) | AI Ape Signals (x402.aiape.tech) | 4.97M / $497K | 2025-12 (3.78M) | 0 / $0 | 2026-01-12 | dead (272d idle) |
| [`0x83240485...`](https://www.x402scan.com/recipient/0x83240485b70e5c820e5f180533fc6156470cfd0e) | Lucy (x402.lucyos.ai) | 3.15M / $31K | 2025-12 (1.63M) | 10 / $0 | 2026-09-07 | dormant (34d idle) |
| [`0xfa0ee7b2...`](https://www.x402scan.com/recipient/0xfa0ee7b2f13d80680f31771abc93d06a2c749150) | badai.fun ("The First CTO on x402") | 527K / $422K | 2025-11 (527K) | 0 / $0 | 2025-12-08 | dead (307d idle) |
| [`0x089127f3...`](https://www.x402scan.com/recipient/0x089127f34ff7c55cec0a92ce4c386b9962ef204b) | x402 Slot Machine (slotx402.fun) | 76K / $257K | 2025-10 (76K) | 0 / $0 | 2025-10-29 | dead (347d idle) |
| [`0xad1f20d4...`](https://www.x402scan.com/recipient/0xad1f20d42cf00acc0e41775be090711ff6b79089) | mint-rpc.x402.vip | 3.1K / $209K | 2025-10 (3.1K) | 0 / $0 | 2025-10-29 | dead (347d idle) |
| [`0xdc365f7a...`](https://www.x402scan.com/recipient/0xdc365f7a21568e02280c7427065114fa914240bd) | 402coin.xyz | 172K / $174K | 2025-10 (172K) | 0 / $0 | 2025-10-30 | dead (346d idle) |
| [`0x5b30e6d9...`](https://www.x402scan.com/recipient/0x5b30e6d93f5c50f92159394547b586b4e0047628) | pong.wtf ($PONG) | 142K / $149K | 2025-10 (142K) | 0 / $0 | 2025-10-29 | dead (347d idle) |
| [`0x48ebf769...`](https://www.x402scan.com/recipient/0x48ebf769b80ffa1c83a00459adbdf5556ef49a3a) | penny.tech | 203K / $2.2K | 2025-10 (203K) | 0 / $0 | 2025-11-28 | dead (317d idle) |
| [`0x7f9d1a87...`](https://www.x402scan.com/recipient/0x7f9d1a879750168b8f4a59734b1262d1778fdb5a) | iou.atxp.ai (ATXP) | 1.4K / $336K | 2025-10 (998) | 0 / $0 | 2026-04-08 | dead (186d idle) |
| [`0xef4364fe...`](https://www.x402scan.com/recipient/0xef4364fe4487353df46eb7c811d4fac78b856c7f) | Virtuals ACP (acp-x402.virtuals.io) | 729K / $1.45M | 2025-12 (587K) | 18K / $5.5K | 2026-09-28 | active |

#### 1.6 Reconciliation of the assigned list: what I could and could not find on Base
For each assigned name: evidence found in the sources above (x402scan facilitator or seller data, Bazaar, CoinGecko, GitHub, npm, docs). "No footprint found" means the project's domain does not appear in x402scan's registered origins or the Bazaar and I found no x402 repo or token tied to it; it does not prove the project is inactive.

| Name | Group | Website | What I found (2026-10-11) | Token (Base contract) | Status on Base |
|---|---|---|---|---|---|
| Coinbase / CDP | [platform] | [docs.cdp.coinbase.com](https://docs.cdp.coinbase.com/x402/welcome) | [CDP facilitator](https://www.x402scan.com/facilitator/coinbase): 117.0M tx / $29.2M on Base all-time; 91.0% of Base tx and 29.7% of Base USDC in the 2026-04-11..10-11 window; operates the [Bazaar API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0) (32,169 resources, 2,212 hosts) | none | active |
| Base (chain) | [platform] | [base.org](https://www.base.org) | x402scan Base: 168.8M tx / $46.9M all-time ([source](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D)); Base said cumulative agent payments passed $50M with more than 85% on Base on 2026-05-14 ([Foresight News via Bitget](https://www.bitget.com/news/detail/12560605412078)); [base.org/ecosystem](https://www.base.org/ecosystem) is client-rendered and could not be read | n/a | active |
| x402 Foundation | [platform] | [x402.org](https://x402.org) | Launched operationally 2026-07-14 with 40 members ([release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/)); repo [x402-foundation/x402](https://github.com/x402-foundation/x402) 6,702 stars, pushed 2026-10-10 | none | active |
| Cloudflare | [platform] | [blog](https://blog.cloudflare.com/x402/) | Premier Foundation member; directory entry only; no x402scan/Bazaar seller footprint matched (the "stableflare.dev" origin is a different seller) | none | platform support, seller footprint unverified |
| Google AP2 | [platform] | [a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) | A2A x402 extension repo 564 stars, pushed 2026-08-04; Google is a Premier member; no on-chain footprint of its own | none | repo active |
| Stripe | [platform] | [docs](https://docs.stripe.com/payments/machine/x402) | Premier member; directory says it "integrated x402" for stablecoin payments; no x402scan origin matched | none | platform support, footprint unverified |
| Visa | [platform] | [visa.com](https://www.visa.com) | Premier member; no x402 Base footprint found (a "visa.orizn.app" visa-requirements API in x402scan is unrelated) | none | unverified |
| Mastercard | [platform] | [mastercard.com](https://www.mastercard.com) | Premier member; "Mastercard Agent Pay for Machines" appears in the [launch release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/); no Base footprint found | none | unverified |
| Circle | [platform] | [circle.com](https://www.circle.com) | Premier member; npm [@circle-fin/x402-batching](https://www.npmjs.com/package/@circle-fin/x402-batching) v3.5.0 (2026-09-16) had 65,480 downloads in the 30 days to 2026-10-10; Arc (eip155:5042) is a default x402 network in the [docs](https://docs.x402.org/core-concepts/network-and-token-support) and 1,358 Bazaar `accepts` entries name it | none | active (tooling) |
| AWS | [platform] | [builder.aws.com post](https://builder.aws.com/content/38fLQk6zKRfLnaUNzcLPsUexUlZ/monetize-any-http-application-with-x402-and-cloudfront-lambdaedge) | Premier member; sample repos [aws-samples/sample-agentcore-cloudfront-x402-payments](https://github.com/aws-samples/sample-agentcore-cloudfront-x402-payments) (25 stars) and two others; no seller footprint | none | samples only |
| Vercel | [platform] | [vercel.com blog](https://vercel.com/blog/introducing-x402-mcp-open-protocol-payments-for-mcp-tools) | Member page on x402.org; [vercel-labs/x402-ai-starter](https://github.com/vercel-labs/x402-ai-starter) 72 stars, archived, last push 2025-12-11 | none | starter archived |
| ERC-8004 | [platform] | [eips.ethereum.org/EIPS/eip-8004](https://eips.ethereum.org/EIPS/eip-8004) | Standard, not a seller; agenteconomy.to counts 626.6K registered agents across 24 chains ([2026-10-11](https://agenteconomy.to)); x402scan origin x8004.x420.dev had 144.8K tx / $31.2K (last 2025-11-12) | none | n/a |
| PayAI | [token facilitators] | [payai.network](https://payai.network) | [Facilitator](https://www.x402scan.com/facilitator/payAI): 23.6M tx / $4.43M all-time; 688K tx (1.7%) and $1.12M (19.8%) in the window; 24.3K tx in the last 30 days; npm @payai/facilitator 10,761 downloads/30d | PAYAI is Solana-only on [CoinGecko](https://www.coingecko.com/en/coins/payai-network-2); no Base contract | active |
| Heurist | [token facilitators] | [heurist.ai](https://docs.heurist.ai/x402-products/facilitator) | [Facilitator](https://www.x402scan.com/facilitator/heurist): 7.97M tx / $30K all-time (Nov-Dec 2025 peak), under 100 tx in 30 days; its x402 vending-machine seller (vending-machine.heurist.xyz) 105.6K tx / $43.3K, idle since 2026-05-12 | HEU [`0xef22cb48...bd818b`](https://basescan.org/token/0xef22cb48b8483df6152e1423b19df5553bbd818b) | facilitator active (low), sellers dormant |
| AurraCloud | [token facilitators] | [aurracloud.com](https://x402-facilitator.aurracloud.com) | [Facilitator](https://www.x402scan.com/facilitator/aurracloud): 235K tx / $53.6K all-time, last Base settlement 2026-01-13 | none confirmed ("Aurra by Virtuals" AURA `0xdcaa5e06...` is a name match, unverified) | dead on Base (271d idle) |
| Meridian | [token facilitators] | [mrdn.finance](https://mrdn.finance) | [Facilitator](https://www.x402scan.com/facilitator/mrdn): $3.79M all-time, 96.2% of it paid and received by the same 41 wallets (see 3.6); 36.5% of Base USDC in the window on 0.2% of tx | MRDN [`0xe57e601c...8400c6`](https://basescan.org/token/0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6) | active, but volume is circular |
| Primer | [token facilitators] | [primer.systems](https://primer.systems) | [Facilitator](https://www.x402scan.com/facilitator/primer): 39.3K tx / $9.0K all-time; 5.8K tx in 30 days; supports SKALE Base per [awesome-x402](https://github.com/xpaysh/awesome-x402) | CoinGecko "Primer" (PR) lists Robinhood chain only, no Base contract | active (small) |
| CodeNut | [token facilitators] | [codenut.ai](https://docs.codenut.ai/guides/x402-facilitator) | [Facilitator](https://www.x402scan.com/facilitator/codenut): 478K tx / $110K all-time, last Base settlement 2026-01-27; origin codenut.ai 403K tx / $103K all-time, 1 tx in 30 days | none on CoinGecko | dead on Base (257d idle) |
| thirdweb | [non-token infra] | [portal.thirdweb.com](https://portal.thirdweb.com/payments/x402/facilitator) | [Facilitator](https://www.x402scan.com/facilitator/thirdweb): 222.7K tx / $120K all-time; 210 tx in 30 days (Base, Polygon) | none | active (low) |
| Merit Systems (x402scan, AgentCash, Echo) | [non-token infra] | [x402scan.com](https://www.x402scan.com) | x402scan live; StableEnrich alone 405K tx / $11.7K in the window (plus StableSocial, StableTravel, StableEmail); Echo router (echo.router.merit.systems) 49.4K tx / $9.9K all-time, last 2026-07-17; npm [agentcash](https://www.npmjs.com/package/agentcash) 9,557 downloads/30d; [x402scan repo](https://github.com/Merit-Systems/x402scan) 397 stars | none | active |
| ampersend (Edge & Node) | [non-token infra] | [app.ampersend.ai](https://app.ampersend.ai/discover) | [ampersend-sdk](https://github.com/edgeandnode/ampersend-sdk) 24 stars, pushed 2026-07-17; no seller footprint matched | none | unverified |
| MCPay | [non-token infra] | [mcpay.tech](https://mcpay.tech) | [microchipgnu/MCPay](https://github.com/microchipgnu/MCPay) 90 stars, last push 2026-01-21; npm `mcpay` about 11 downloads/day; no footprint | none | dormant (repo idle 263d) |
| Mogami | [non-token infra] | [mogami.tech](https://mogami.tech/) | [Facilitator](https://www.x402scan.com/facilitator/mogami): 23.4K tx / $310K all-time, 2.3K tx in 30 days; Java SDK repos 7 to 11 stars | none | active (low) |
| x402.rs | [non-token infra] | [x402.rs](https://x402.rs) | [Facilitator](https://www.x402scan.com/facilitator/x402rs): 703K tx / $469K all-time, last Base settlement 2026-08-30; [repo](https://github.com/x402-rs/x402-rs) 291 stars | none | dormant (42d idle) |
| OpenX402 | [non-token infra] | [openx402.ai](https://open.x402.host) | [Facilitator](https://www.x402scan.com/facilitator/openx402): 563K tx / $177K all-time; 1.7K tx / $1.3K in 30 days | none | active (low) |
| Crossmint | [non-token infra] | [crossmint.com](https://www.crossmint.com) | [crossmint-agentic-finance](https://github.com/Crossmint/crossmint-agentic-finance) 19 stars (2026-03-13); no x402scan facilitator or seller footprint | none | unverified |
| Daydreams | [agent frameworks] | [daydreams.systems](https://facilitator.daydreams.systems) | [Facilitator](https://www.x402scan.com/facilitator/daydreams): 11.8M tx / $2.76M all-time, mostly Nov 2025, 496 tx in 30 days; repos [daydreams](https://github.com/daydreamsai/daydreams) 619 stars, [lucid-agents](https://github.com/daydreamsai/lucid-agents) 199 stars (pushed 2026-07-26) | DREAMS [`0x17638301...e602`](https://basescan.org/token/0x176383016bb310c9f1c180dc6729d5e28104e602) | active (low) |
| Virtuals Protocol | [agent frameworks] | [app.virtuals.io](https://app.virtuals.io) | [Facilitator](https://www.x402scan.com/facilitator/virtuals): 1.99M tx / $4.34M all-time; ACP-x402 origin 2.37M tx / $4.89M (about $1.5M a month in Feb-Mar 2026), 2.8K tx / $28 in 30 days | many "by Virtuals" tokens in the CoinGecko category (see 1.3a) | active (low) |
| elizaOS | [agent frameworks] | [elizaos.ai](https://elizaos.ai) | elizaos.ai redirected to elizaresearch.ai ("Eliza Research") on 2026-10-11; ELIZA is in the CoinGecko x402 category but with a Solana contract only; no Base x402 footprint found | ELIZA (Solana only) | unverified on Base |
| Questflow | [agent apps] | [questflow.ai](https://questflow.ai) | [Facilitator](https://www.x402scan.com/facilitator/questflow): 474K tx / $10.2K all-time, last 2026-10-04; its own seller origin 21 tx | none | active (low) |
| Bankr | [agent apps] | [bankr.bot](https://bankr.bot) | BNKR is in the category (Base); [x402-cli-example](https://github.com/BankrBot/x402-cli-example) 3 stars (2025-10-26); no seller footprint matched; the agent apps researcher calls it the only priced x402 product among their three leads, with no usage numbers ([their notes](dd_agent_apps_platforms.md)) | BNKR [`0x22af33fe...c76f3b`](https://basescan.org/token/0x22af33fe49fd1fa80c7149773dde5890d3c76f3b) | unverified |
| Olas | [agent apps] | [olas.network](https://olas.network) | OLAS (Base) is in the category; agenteconomy.to counts 19.4M Olas transactions, which are not x402; no x402 footprint matched; the agent apps researcher finds buyer-side x402 support in Pearl agents since Oct-Nov 2025 and seller-side (mech facilitator) work restarting in Sep-Oct 2026 ([their notes](dd_agent_apps_platforms.md)) | OLAS [`0x54330d28...3416`](https://basescan.org/token/0x54330d28ca3357f294334bdc454a032e7f353416) | unverified |
| Giza | [agent apps] | [giza.tech](https://www.giza.tech) | DefiLlama lists "Giza" as an AI-agent DeFi protocol (about $12.8K TVL on Hyperliquid/Arbitrum/Base on 2026-10-11, [API](https://api.llama.fi/protocols)); only x402 link found is a 0-star repo | none | no x402 footprint found |
| Theoriq | [agent apps] | [theoriq.ai](https://www.theoriq.ai) | DefiLlama lists "Theoriq Gold Vault" on Ethereum; the site's 2026-10-11 title now describes risk-managed onchain yield on tokenized real-world assets; no x402 footprint found | none | no x402 footprint found |
| Recall | [agent apps] | [recall.network](https://recall.network) | No x402 footprint found (name matches in the Bazaar are unrelated "recalls" APIs) | none | no x402 footprint found |
| Spectral | [agent apps] | [spectrallabs.xyz](https://www.spectrallabs.xyz) | The spectral.finance address returned HTTP 404 on 2026-10-11 and the agent apps researcher finds no x402 work at Spectral Labs ([their notes](dd_agent_apps_platforms.md)); no x402 footprint found ("Spectral-signed receipts" repos by another author are a name collision) | none | site 404; no x402 footprint found |
| Wayfinder | [agent apps] | [wayfinder.ai](https://wayfinder.ai) | No x402 footprint found | none | no x402 footprint found |
| Clanker | [agent apps] | [clanker.world](https://clanker.world) | Token launcher (its 2026-10-11 site title says multi-chain); CoinGecko tags BNKR as "Clanker Ecosystem"; no Clanker x402 footprint found (x402scan "Clanker Banker" and "clankerceo" origins are unrelated sellers) | none | no x402 footprint found |
| Zora | [agent apps] | [zora.co](https://zora.co) | No seller footprint; the agent apps researcher found a `zora pay` command in Zora's agent CLI (v1.6.0, 2026-06-25), a buyer-side x402 v2 client on Base ([changelog](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/CHANGELOG.md), [their notes](dd_agent_apps_platforms.md)) | none | buyer-side feature only |
| Zauth | [x402 apps and trust] | [zauthx402.com](https://zauthx402.com) | Listed under [third-party extensions](https://docs.x402.org/dev-tools/third-party-extensions) (@zauthx402/sdk); [zauthSDK](https://github.com/zauthofficial/zauthSDK) 8 stars (2026-02-11); no x402scan Base origin matched; the x402 apps and trust researcher reports the team repositioned as an AI-security company on 2026-07-28 with the registry "still running", and that the token is a pump.fun coin on Solana ([their notes](dd_x402_apps_and_trust.md)) | ZAUTH is Solana-only on [CoinGecko](https://www.coingecko.com/en/coins/zauthx402) | unverified on Base; repositioned |
| Cred Protocol | [x402 apps and trust] | [credprotocol.com](https://credprotocol.com) | My domain match found nothing; the x402 apps and trust researcher reports x402 sales live on Base since 2026-01-21 that had earned $0.88 there ([their notes](dd_x402_apps_and_trust.md)) | none | tiny (cross-checked) |
| Snack Money | [x402 apps and trust] | [api.snack.money](https://api.snack.money/docs) | 654 tx / $155 all-time, last Base settlement 2025-12-04 | none | dead on Base (310d idle) |
| Fluora | [x402 apps and trust] | [fluora.ai](https://www.fluora.ai/) | Directory entry (MonetizedMCP marketplace); no footprint found here; the x402 apps and trust researcher reports the marketplace API host deleted, no commits since 2026-02-11 and the company site now promoting an unrelated wellness product ([their notes](dd_x402_apps_and_trust.md)) | none | dead per cross-check |
| Gloria AI | [data/AI sellers] | [itsgloria.ai](https://itsgloria.ai) | api.itsgloria.ai: 19.2K tx / $359 all-time, 28 tx in 30 days | GLORIA [`0x3b313f56...f8674`](https://basescan.org/token/0x3b313f5615bbd6b200c71f84ec2f677b94df8674) | low activity |
| Otto AI | [data/AI sellers] | [ottoai.services](https://x402.ottoai.services) | 178K tx / $433 all-time, 3.3K tx / $30 in 30 days, 2,337 Bazaar calls in 30 days; also 599 tx on Solana | OTTO [`0x380337d0...ea908ee1fc`](https://basescan.org/token/0x380337d0180db7d0df76ac4faae2fcea908ee1fc) | active |
| AIXBT | [data/AI sellers] | [api.aixbt.tech](https://api.aixbt.tech) | 1,535 tx / $2,766 all-time, last Base settlement 2026-07-11; AIXBT is not in the CoinGecko x402 category | none in category | dormant (92d idle) |
| Cookie DAO | [data/AI sellers] | [cookie.fun](https://www.cookie.fun) | No x402 footprint found | none | no x402 footprint found |
| Venice | [data/AI sellers] | [venice.ai](https://venice.ai) | api.venice.ai: 3.4K tx / $5.3K all-time; 613 tx / $3.1K in 30 days (about $5 per payment); [veniceai/x402-client](https://github.com/veniceai/x402-client) 11 stars | none in category | active |
| PING | [token experiments] | n/a | Oct 2025 pay-to-mint experiment (Chainalysis reports more than 150,000 transactions in its first month: [Chainalysis](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/)); listed on [CoinGecko](https://www.coingecko.com/en/coins/ping) | PING [`0xd85c3185...f829d46`](https://basescan.org/token/0xd85c31854c2b0fb40aaa9e2fc4da23c21f829d46) | experiment over |
| x402-minted tokens and launchpads | [token experiments] | see 1.5 | ARVOS, QRBase, Barvis, AinX402, Canza took 90.7% of Base USDC in Nov 2025 (3.6); 15 of the 17 recipients I traced are dead (11) or dormant (4) | various | mostly dead |
| Other x402-branded Base tokens | [token experiments] | see 1.3a | x420 (X420, `0x68e284f2...f80b07`), x402MKT (LOOP, `0xa763b711...2446b07`); x8004.x420.dev 144.8K tx / $31.2K, last 2025-11-12 | see 1.3a | dormant/dead |
| Dexter | [rivals] | [dexter.cash](https://dexter.cash) | Solana-first: api.dexter.cash 25.9M tx / $4.71M on Solana all-time (last 2026-04-09); Dexter facilitator on Base 110K tx / $7.1K, last 2026-10-06; [dexter-mcp](https://github.com/Dexter-DAO/dexter-mcp) 11 stars | DEXTER is Solana-only on CoinGecko | active on Solana, marginal on Base |
| Corbits / Faremeter | [rivals] | [corbits.dev](https://corbits.dev) | [Corbits facilitator](https://www.x402scan.com/facilitator/corbits) on Base: 19.8K tx / $305 all-time, last 2026-06-20; [faremeter](https://github.com/faremeter/faremeter) 69 stars; npm @faremeter/middleware 73 to 204 downloads/day | none | dormant on Base (113d idle) |
| Kite AI | [rivals] | [gokite.ai](https://gokite.ai) | Its own chain, not Base; General member of the Foundation; GitHub hits for "kite x402" are Kite-chain apps; the x402scan origins named "KiteEndpoints.ai" are an unrelated name collision; mainnet and Agent Passport launched 2026-04-30 with no independent usage data ([rivals notes](competition_rival_rails_chains.md)) | none in category | not on Base |
| Pieverse | [rivals] | [pieverse.io](https://www.pieverse.io) | Described as a BNB Chain facilitator in [awesome-x402](https://github.com/xpaysh/awesome-x402); its site title on 2026-10-11 reads "Web3 AI Agent for Line, Kakao & WhatsApp"; no Base footprint or repo found; the rivals researcher finds its last dated news in October 2025 and says the 2026 BNB Chain x402 story is Binance's own B402 ([rivals notes](competition_rival_rails_chains.md)) | none | not on Base (unverified) |

#### 1.7 x402 Foundation launch roster (2026-07-14): who is in and who is assigned
Source: [launch release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/) (the release says 40 members but names 39 entries); [x402.org member pages](https://x402.org/llms.txt) also list Nansen, World, Vercel, Stripe and Quicknode. Base relevance is from the sources above.

| Member | Tier | Assigned group | Base x402 relevance found |
|---|---|---|---|
| Adyen, American Express, Fiserv, MoonPay, Ripple, Shopify, zerohash, World Liberty Financial, KakaoPay, Hecto Financial, Galaxia Moneytree, Quant Network, utexo, Aleo, Injective, LayerZero Labs, Monad Foundation, BSV Association, Cardano Foundation, Casper (with Japanese Contents Blockchain Initiative) | Premier / General / Associate | UNCOVERED | No Base x402 footprint found; payments or chain players whose x402 plans are not visible in Base data |
| Orthogonal | General | UNCOVERED | x402.orthogonal.com: 157 Bazaar resources on Base, Monad and Solana, 1,959 calls in 30 days |
| SKALE | General | UNCOVERED | SKL has a Base contract and sits in the CoinGecko x402 category; Primer and PayAI list SKALE Base networks |
| t54 labs | General | UNCOVERED | x402-secure API on Base (29.6M tx all-time, peak Dec 2025) plus an XRPL facilitator |
| Polygon Labs | General | UNCOVERED | Polygon facilitator, $141,064 settled in the trailing 30 days per [x402-list.com](https://x402-list.com) (Polygon, not Base) |
| Solana Foundation | Premier | UNCOVERED | [solana-foundation/pay](https://github.com/solana-foundation/pay) 1,788 stars, pushed 2026-10-09 (Solana) |
| Stellar Development Foundation | Premier | UNCOVERED | "Built on Stellar" facilitator and Stellar x402 docs (Stellar chain) |
| Fireblocks, NEAR Foundation | General | UNCOVERED | Facilitators listed in the [docs](https://docs.x402.org/dev-tools/facilitators); no Base footprint found |
| OMA3 | Associate | UNCOVERED | OMATrust "x402 Reputation" in the directory and [third-party extensions](https://docs.x402.org/dev-tools/third-party-extensions) |
| Nansen, World, Quicknode | x402.org member pages | UNCOVERED | Nansen: api.nansen.ai 32 Bazaar resources, 3,578 calls in 30 days, 4.7K Base tx / 30 days. World: AgentKit extension in docs. Quicknode: x402-rails gem (37 stars) |
| AWS, Circle, Cloudflare, Coinbase, Google, Mastercard, Stripe, Visa, Vercel, Merit Systems, Kite AI | Premier / General | assigned (see 1.6) | see 1.6 |

#### 1.8 GitHub: most-starred repositories matching "x402"
Source: [GitHub repository search](https://api.github.com/search/repositories?q=x402&sort=stars&per_page=100), pages 1 to 3 on 2026-10-11 (top 45 shown). Stars can be inflated: the 6,710-star internet-court-skill repo had 4 commits and 10 watchers when fetched ([repo](https://github.com/internet-court/internet-court-skill)), and it names x402 as one of many payment standards.

| Repo | Stars | Last push | Created | Description | Flag |
|---|---|---|---|---|---|
| [NoFxAiOS/nofx](https://github.com/NoFxAiOS/nofx) | 13,033 | 2026-10-04 | 2025-10-28 | Your AI trading terminal assistant for US stocks, commodities, forex, and crypto. | x402-adjacent (AI trading terminal) |
| [internet-court/internet-court-skill](https://github.com/internet-court/internet-court-skill) | 6,710 | 2026-08-19 | 2026-06-16 | The trust layer for agent-to-agent commerce — natural-language mandates, ERC-7710 delegated permissions, x402  | x402 listed as one of many payment standards; 6.7K stars vs 4 commits/10 watchers = unusual ratio (verify) |
| [x402-foundation/x402](https://github.com/x402-foundation/x402) | 6,702 | 2026-10-10 | 2025-02-21 | A payments protocol for the internet. Built on HTTP. |  |
| [BlockRunAI/ClawRouter](https://github.com/BlockRunAI/ClawRouter) | 6,622 | 2026-10-05 | 2026-02-03 | The agent-native LLM router for autonomous agents. Every frontier model behind one wallet, <1ms local routing, |  |
| [alsk1992/CloddsBot](https://github.com/alsk1992/CloddsBot) | 2,958 | 2026-10-02 | 2026-01-26 | Open Source AI trading agent that operates autonomously across 1000+ markets - Polymarket, Kalshi, Binance, Hy | x402-adjacent (trading agent) |
| [Bitterbot-AI/bitterbot-desktop](https://github.com/Bitterbot-AI/bitterbot-desktop) | 2,471 | 2026-10-11 | 2026-03-28 | Bitterbot - a mesh of agents that turns shared experience into collective capability. | x402-adjacent |
| [solana-foundation/pay](https://github.com/solana-foundation/pay) | 1,788 | 2026-10-09 | 2021-10-19 | CLI for Agentic payments (x402, MPP, AP2). |  |
| [apify/mcpc](https://github.com/apify/mcpc) | 1,011 | 2026-10-09 | 2025-12-09 | The most compatible MCP CLI client. Supports: tools, resources, prompts, completions, async tasks, skills, std | x402-adjacent (MCP client) |
| [daydreamsai/daydreams](https://github.com/daydreamsai/daydreams) | 619 | 2026-10-09 | 2024-12-20 | Daydreams is a set of tools for building agents for commerce |  |
| [qntx/ovo](https://github.com/qntx/ovo) | 569 | 2026-10-07 | 2026-01-28 | Agent behavior that compiles | x402-adjacent |
| [google-agentic-commerce/a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) | 564 | 2026-08-04 | 2025-06-10 | The A2A x402 Extension brings cryptocurrency payments to the Agent-to-Agent (A2A) protocol, enabling agents to |  |
| [BlockRunAI/Franklin](https://github.com/BlockRunAI/Franklin) | 555 | 2026-10-08 | 2026-03-22 | The AI agent with a wallet — spends USDC autonomously to get real work done. Apache-2.0, TypeScript. |  |
| [auscaster/frantic-board](https://github.com/auscaster/frantic-board) | 543 | 2026-10-11 | 2026-06-11 | HELP WANTED: AI AGENTS. Real bounties, real money, every payout sealed to a public ledger. The notice board fo | x402-adjacent (agent bounty board) |
| [Merit-Systems/x402scan](https://github.com/Merit-Systems/x402scan) | 397 | 2026-09-25 | 2025-09-23 | x402 Ecosystem Explorer |  |
| [BlockRunAI/blockrun-mcp](https://github.com/BlockRunAI/blockrun-mcp) | 391 | 2026-10-11 | 2026-01-12 | Live data for AI agents — search, research, markets, crypto, X/Twitter. Pay-per-call via x402 micropayments. |  |
| [moov-io/awesome-fintech](https://github.com/moov-io/awesome-fintech) | 389 | 2026-10-05 | 2021-07-13 | A curated collection of open source fintech libraries for payments, banking, and financial infrastructure.  | list, not x402-specific |
| [x402-rs/x402-rs](https://github.com/x402-rs/x402-rs) | 291 | 2026-07-13 | 2025-05-08 | x402 payments in Rust: verify, settle, and monitor payments over HTTP 402 flows |  |
| [xpaysh/awesome-x402](https://github.com/xpaysh/awesome-x402) | 290 | 2026-07-28 | 2025-11-02 | 🚀 Curated list of x402 resources: HTTP 402 Payment Required protocol for blockchain payments, crypto micropaym |  |
| [qntx/openai-python](https://github.com/qntx/openai-python) | 262 | 2026-10-07 | 2026-02-11 | Drop-in OpenAI Python client with transparent x402 payment support. |  |
| [nirholas/three.ws](https://github.com/nirholas/three.ws) | 231 | 2026-10-11 | 2026-01-08 | Open-source platform for 3D AI agents. Turn text or a photo into a rigged, animated GLB avatar, give it an LLM | x402-adjacent (3D agents); many sibling repos by same author |
| [apiguru-app/amazon-scraper-v2](https://github.com/apiguru-app/amazon-scraper-v2) | 214 | 2026-09-21 | 2025-10-20 | Agent-ready Amazon Scraper API: real-time product details (batch ASIN), offers & stock, reviews, search, best  | x402-adjacent (scraper API) |
| [FinAegis/core-banking-prototype-laravel](https://github.com/FinAegis/core-banking-prototype-laravel) | 204 | 2026-10-07 | 2024-08-14 | Open-source core banking platform — 61 DDD domains with event sourcing, CQRS, and a schema-first GraphQL API.  | x402-adjacent (core banking) |
| [daydreamsai/lucid-agents](https://github.com/daydreamsai/lucid-agents) | 199 | 2026-07-26 | 2025-11-04 | Lucid Agents Commerce SDK. Bootstrap AI agents in 60 seconds that can pay, sell, and participate in agentic co |  |
| [Goncafer47/Stablecoin-Payment-Gateway](https://github.com/Goncafer47/Stablecoin-Payment-Gateway) | 195 | 2026-10-11 | 2026-09-22 | Self-hosted, non-custodial stablecoin payment gateway with x402 and invoice checkout. Accepts USDC, USDT, PYUS |  |
| [second-state/x402-payment-link](https://github.com/second-state/x402-payment-link) | 190 | 2026-03-04 | 2025-10-21 |  | stale (221d since push) |
| [dabit3/x402-starter-kit](https://github.com/dabit3/x402-starter-kit) | 181 | 2026-03-02 | 2025-10-27 |  | stale (223d since push) |
| [qntx-labs/ra2a](https://github.com/qntx-labs/ra2a) | 169 | 2026-10-08 | 2026-01-30 | Rust SDK for the Agent2Agent (A2A) Protocol. |  |
| [mogons/noraz-agent](https://github.com/mogons/noraz-agent) | 169 | 2026-10-03 | 2026-09-11 | Open-source Robinhood trading agent infrastructure with MCP-powered DEX research, autonomous trading, agent wa |  |
| [vybenetwork/x402-client](https://github.com/vybenetwork/x402-client) | 164 | 2026-05-13 | 2026-05-11 | Client SDK for the Vybe x402 API. Pay-per-call USDC over HTTP and prepaid-credit WebSocket streaming for Vybe' |  |
| [qntx/r402](https://github.com/qntx/r402) | 155 | 2026-09-14 | 2026-02-09 | Rust SDK for the x402 payment protocol. |  |
| [qntx/openai](https://github.com/qntx/openai) | 154 | 2026-10-10 | 2026-02-11 | Drop-in OpenAI Typescript client with transparent x402 payment support. |  |
| [qntx/facilitator](https://github.com/qntx/facilitator) | 151 | 2026-09-15 | 2026-02-10 | Production-ready x402 facilitator server. |  |
| [bolivian-peru/os-moda](https://github.com/bolivian-peru/os-moda) | 120 | 2026-06-24 | 2026-02-20 | An operating system built for AI agents — talk to your NixOS server instead of SSH-ing in. Typed, audited tool |  |
| [AlephantAI/AIephant-AI-Agent-Gateway](https://github.com/AlephantAI/AIephant-AI-Agent-Gateway) | 114 | 2026-06-12 | 2026-05-09 | Alephant is an open-source AI Agent Gateway for routing, tracking, and controlling LLM usage across AI agents, |  |
| [dabit3/a2a-x402-typescript](https://github.com/dabit3/a2a-x402-typescript) | 104 | 2026-07-07 | 2025-10-06 | A complete TypeScript implementation of the Python x402 payment protocol extension for A2A (Agent-to-Agent) co |  |
| [chu2bard/pinion-os](https://github.com/chu2bard/pinion-os) | 97 | 2026-02-23 | 2026-02-11 | Client SDK, Claude plugin and skill framework for the Pinion protocol. x402 micropayments on Base. | stale (230d since push) |
| [AnkanMisra/MicroAI-Paygate](https://github.com/AnkanMisra/MicroAI-Paygate) | 95 | 2026-10-05 | 2025-12-08 | A high-performance, crypto-monetized AI microservice architecture implementing the x402 Protocol |  |
| [azep-ninja/x402-gateway-template](https://github.com/azep-ninja/x402-gateway-template) | 94 | 2026-05-02 | 2026-02-20 |  |  |
| [TLAY-IO/boat-mer](https://github.com/TLAY-IO/boat-mer) | 94 | 2026-09-03 | 2026-08-11 | Lightweight C runtime for connected machines: on-device identity, attestation, and BLE-native per-slice stable |  |
| [microchipgnu/MCPay](https://github.com/microchipgnu/MCPay) | 90 | 2026-01-21 | 2025-05-30 | Open-source Infrastructure for MCP and x402 | stale (263d since push) |
| [xpaysh/awesome-agentic-commerce](https://github.com/xpaysh/awesome-agentic-commerce) | 82 | 2026-06-24 | 2025-11-10 | Curated list of active protocols and implementations for agent-to-merchant commerce (ACP, UCP, AP2, x402, MPP, |  |
| [AgentlyHQ/aixyz](https://github.com/AgentlyHQ/aixyz) | 82 | 2026-07-17 | 2026-01-13 | Next.js-like framework building AI Agents that are payment-native. Bootstrap your agent with A2A, MCP, x402 pa |  |
| [nirholas/agenti](https://github.com/nirholas/agenti) | 80 | 2026-10-11 | 2020-04-06 | Give any AI agent a crypto wallet. Agents deserve access to money.  Pay x402 APIs, receive USDC, check balance |  |
| [solana-foundation/pay-kit](https://github.com/solana-foundation/pay-kit) | 73 | 2026-10-09 | 2026-03-18 | Building blocks for Agentic payments (x402, MPP) over HTTP/MCP/A2A/RPC for TypeScript, Rust, Go, Python, Ruby, |  |
| [AgentlyHQ/use-agently](https://github.com/AgentlyHQ/use-agently) | 73 | 2026-07-14 | 2026-02-24 | The way AI coordinates and transacts. Routing and settlement layer for your agent economy. |  |

#### 1.9 The analytics and discovery layer itself (all UNCOVERED except where noted)
- [x402scan](https://www.x402scan.com) ([Merit Systems], assigned) and the [CDP Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0) ([platform], assigned) are the two primary sources.
- [x402-list.com](https://x402-list.com): directory of 944 services with on-chain facilitator volumes; for the trailing 30 days it reports Coinbase $572,269, FluxA $322,408, Polygon Facilitator $141,064 and Meridian $130,663, and says listed services cover 34.8% of measurable flow and its top 10 services hold 97.1% of settlement volume (page dated 2026-10-11; operator not stated on the page I fetched).
- [x402watch](https://x402.printmoneylab.com) (PrintMoneyLab): wash-filtered index, 109,693 services and 24.4M transactions analysed, "86.8% real volume", daily CC0 files in [x402watch-data](https://github.com/printmoneylab/x402watch-data) (page updated 2026-10-02).
- [agenteconomy.to](https://agenteconomy.to): cross-protocol dashboard (x402, ERC-8004, Tempo MPP, Virtuals ACP, Olas, Masumi) citing Dune authors @thechriscen, @hashed_official, @ax1research and @adrian0x (updated 2026-10-11).
- [Valoria](https://x402.valoria.net): claims 102,319 services and $148.2M tracked volume; its only named top earner is x402.arvos.xyz at $57.6M, a token-mint recipient that x402scan shows at $11.5M (see 3.9), so treat it as unreliable.
- Others named in [awesome-x402](https://github.com/xpaysh/awesome-x402) (self-submitted list, low signal): SmartFlow Observatory (claims 22,251 endpoints), Demand Intel (intel.agent402.app), EntRoute, Rencom, nohumans.directory, x402search. [gold-402](https://github.com/Haustorium12/gold-402) (24K Labs) lists 580 hand-checked services and states in its README banner that most of the x402 catalogue no longer answers.

#### 1.10 awesome-x402 entries with measurable Base usage that are not listed above
Source: [awesome-x402 README](https://github.com/xpaysh/awesome-x402) (816 linked entries parsed; self-submitted, so inclusion says nothing about quality), matched by registrable domain to x402scan and the Bazaar as in 1.0; entries whose domain is already in 1.1 or 1.4 are omitted, and entries sharing the same payTo address are shown once. Shown: those with at least 100 Base tx or Bazaar calls in 30 days, or at least 20,000 Base or Solana tx all-time (44 matched, 40 shown). All UNCOVERED. These are the long tail: individually tiny (under $100 a month each) but they make up most of the registered-origin count.

| Name (as listed in awesome-x402) | What the list says | Base 30d tx / USDC | Base all-time tx / USDC | Bazaar calls 30d | Solana 30d tx (top-100 lists) | Last Base settlement | Status |
|---|---|---|---|---|---|---|---|
| [glim.sh](https://glim.sh) | Live data from Twitter, Reddit, the web, GitHub, Amazon, and YouTube for AI agents. 11 MCP tools, $0.002-$0.01 | 6.0K / $16 | 17K / $69 | 921 | 2.4K | 2026-10-11 | active |
| [RobinX](https://robinx.io) | Deployer-reputation and insider-flow intelligence for Robinhood Chain (chain 4663) memecoins, computed from co | 2.4K / $55 | 2.7K / $60 | 56 | — | 2026-10-10 | active |
| [x402stock](https://x402stock.xyz) | Real-time US stock market data for AI agents. 23 pay-per-call endpoints: quotes, snapshots, OHLC aggregates, c | 1.8K / $50 | 9.2K / $253 | 1.0K | — | 2026-10-11 | active |
| [Deepnets](https://api.deepnets.ai) | Solana token intelligence: safety analysis, deep wallet-funding-network mapping, holder breakdowns, social/Twi | 0 / $0 | 0 / $0 | 1.2K | 1.1K | 2026-10-11 | active |
| [Gotobi Calendar API](https://gotobi.hugen.tokyo) | Japanese FX gotobi date intelligence for trading agents. Holiday-aware USD settlement day detection with next- | 878 / $7 | 92K / $2.7K | 803 | 53 | 2026-10-11 | active |
| [2s.io](https://2s.io) | Pay-per-call JSON API for AI agents. 35 endpoints: geo/IP, web extract + summarize + translate + screenshot, i | 844 / $16 | 36K / $118 | 584 | 34 | 2026-10-11 | active |
| [agentsvc.io](https://agentsvc.io) | 20 utility tools for AI agents via x402 USDC micropayments on Base. Tools: `ip-lookup`, `dns-lookup`, `qr-code | 820 / $6 | 817 / $6 | 836 | — | 2026-10-11 | active |
| [DDG Agent-Payable Services](https://agents.daedalusdevelopmentgroup.com) | 83 AI-agent-native services for checkout/payment conformance, MCP/tool security, prompt injection scans, DNS/W | 795 / $7 | 795 / $7 | 617 | — | 2026-10-07 | active |
| [IPIntel.ai](https://ipintel.ai/x402-api) | Machine-payable IP threat intelligence lookup via x402 on Base. Pay $0.001 USDC per IP lookup, no account or A | 758 / $18 | 1.4K / $27 | 750 | — | 2026-10-11 | active |
| [LoneStarOracle](https://lonestaroracle.xyz) | 39 x402-gated AI data services on Base: token forensics (TokenScope), smart contract audits (RattlerAI/Cottonm | 637 / $41 | 3.3K / $341 | 490 | — | 2026-10-10 | active |
| [PulseNetwork](https://pulsenetwork.theaslangroupllc.com) | 75 pay-per-call intelligence APIs (930+ endpoints) for AI agents under one federated catalog: token-safety ver | 636 / $63 | 12K / $1.8K | 215 | 29 | 2026-10-11 | active |
| [Sirenic](https://api.sirenic.eu) | Official French & European company data for AI agents, from open government sources (INSEE/INPI, Etalab 2.0).  | 602 / $23 | 2.3K / $137 | 341 | — | 2026-10-11 | active |
| [botsmith](https://x402.botsmith.dev) | Pay-per-call web and on-chain intelligence for AI agents, no API keys. `read` (any URL to clean, boilerplate-f | 521 / $10 | 1.0K / $14 | 434 | — | 2026-10-10 | active |
| [x402 Bazaar](https://402.com.tr) | The Base token-safety toolkit for AI agents: the only [B20](https://docs.base.org/base-chain/specs/upgrades/be | 0 / $0 | 0 / $0 | 518 | — | 2026-10-11 | active |
| [Relaystation](https://relaystation.ai) | Pay-per-call agent infrastructure with x402 micropayments: durable file storage and handoff (batons), 150+ com | 455 / $7 | 1.9K / $29 | 467 | — | 2026-10-10 | active |
| [Skim](https://skim402.com) | x402-native clean reader for AI agents. POST a URL, get back agent-ready Markdown plus structured metadata (ti | 456 / $1 | 3.7K / $16 | 446 | — | 2026-10-11 | active |
| [GlobalAPI](https://globalapi.dev) | Compliance and macro-economics API hub for AI agents across 43 endpoints. Crypto wallet sanctions screening ch | 380 / $2 | 9.1K / $45 | — | — | 2026-10-11 | active |
| [Kronos x402 API](https://kronossignals.com) | Pay-per-call crypto derivatives, forecasting, and market-signal API for AI agents. 20 tools priced $0.001–$0.0 | 376 / $11 | 5.9K / $119 | 348 | — | 2026-10-10 | active |
| [FiatDock](https://fiatdock.com) | Non-custodial MCP marketplace for AI agents: discover and pay for MCP services per call in USDC over x402 on B | 259 / $1 | 317 / $4 | 311 | — | 2026-10-11 | active |
| [PayAPI Market](https://payapi.market) | First marketplace for x402-powered APIs. 10 APIs, 65 endpoints: UK property data, email verification, company  | 268 / $1 | 2.2K / $5 | 49 | — | 2026-10-10 | active |
| [tokenguard](https://eltociear-tokenguard.hf.space/scan) | ERC-20 rug/safety scanner: detects mint, blacklist, pausable, transfer-tax, upgradeable-proxy & ownership trap | 265 / $6 | 847 / $12 | 222 | — | 2026-10-08 | active |
| [GEDX402](https://gedx402.com) | Cloudflare Workers AI hub with x402 v2 USDC (Base, Polygon, Arbitrum, World, Solana). Eight modality shards. [ | 260 / $2 | 2.6K / $105 | 214 | — | 2026-10-11 | active |
| [AI Rook — Trading Intelligence + General Agent APIs](https://agents.ai-rook.com) | 22 endpoints across 4 categories: trading intelligence (market pulse, trade signals, order flow, liquidation h | 226 / $2 | 722 / $19 | 254 | — | 2026-10-10 | active |
| [SuVerse Pay](https://suverse-pay.suverse.io) | Payment gateway + API catalog with ~490 paid endpoints on one origin: crypto market data, Polymarket smart-mon | 90 / $5 | 2.5K / $94 | 251 | 29 | 2026-10-10 | active |
| [_done](https://underscoredone.com) | Suite of x402 micropayment-gated utility APIs for AI agents (Web lookups, site analysis, data and more). Pay-p | 249 / $3 | 889 / $49 | 137 | — | 2026-10-11 | active |
| [Vibe Springs](https://vibesprings.net) | Hosted MCP server (`https://vibesprings.net/mcp`, streamable-http — no install, no API keys) with 22 tools spa | 243 / $1 | 3.8K / $101 | 102 | — | 2026-10-11 | active |
| [WebberSites x402 Data API](https://x402.webbersites.com) | 41 pay-per-call endpoints for AI agents, all $0.001–$0.009 USDC on Base via CDP facilitator: web scraping, doc | 239 / $2 | 1.4K / $11 | 103 | — | 2026-10-11 | active |
| [agentdata-nl](https://agentdata-api.sander-van-aard.workers.dev) | European company screening for AI agents, straight from official public registers: company registers (UK, FR,  | 230 / $59 | 764 / $80 | 129 | — | 2026-10-11 | active |
| [LION](https://lionx402.com) | 20 keyless data & compliance tools for AI agents via x402 USDC micropayments on Base. OFAC sanctions screening | 224 / $3 | 858 / $32 | 91 | — | 2026-10-11 | active |
| [afriref / latamref / asiaref / euroref / usaref / ausref](https://afriref.dev) | Verified government reference data for 58 countries across six continent-scoped brands on one engine: central- | 219 / $11 | 363 / $13 | 16 | — | 2026-10-10 | active |
| [AgentLux](https://agentlux.ai) | Identity, marketplace, and services platform for AI agents. Uses x402 for agent purchases, service hiring with | 209 / $0 | 13K / $248 | — | — | 2026-10-05 | active |
| [anchor-x402](https://anchor-x402.com) | 16 x402-paid services for AI agents on Base + Solana mainnet. 9 commodity primitives (OFAC sanctions screen, b | 169 / $6 | 4.2K / $152 | 56 | — | 2026-10-11 | active |
| [SignalFuse](https://api.signalfuse.co) | Trading intelligence + x402 API gateway. Crypto signals fusing sentiment, macro regime, and market structure ( | 131 / $1 | 1.3K / $15 | 153 | — | 2026-10-10 | active |
| [scrape402](https://x402.shizu.me) | 16 pay-per-call utility APIs for AI agents: web scraping (clean text, markdown, PDF-to-text, LLM structured ex | 150 / $1 | 2.6K / $13 | 103 | — | 2026-10-09 | active |
| [SYNTHORA md-extract](https://pay.hergertsynthora.com/service) | Western EN/EU web → clean markdown + token budget for AI agents. Every response ships an **Ed25519 attestation | 135 / $3 | 707 / $11 | 77 | — | 2026-10-11 | active |
| [PreReason](https://www.prereason.com) | Financial context API with x402 pay-per-call ($0.01-$0.03 USDC on Base). 17 pre-analyzed market briefings cove | 132 / $5 | 193 / $6 | 132 | — | 2026-10-10 | active |
| [TradingAgents x402](https://tradingagents-x402.fly.dev) | Multi-agent LLM ticker consensus. Five specialist analysts (fundamentals / sentiment / news / technical) plus  | 126 / $21 | 178 / $40 | — | — | 2026-10-08 | active |
| [modelprices.xyz](https://modelprices.xyz) | Normalized LLM market data: per-token prices, context windows and capability limits, and a price-change feed f | 116 / $1 | 238 / $2 | 103 | — | 2026-10-10 | active |
| [Kraken Crypto Signals](https://signals.nsgoods.org) | Pay-per-call crypto market-state signals (BUY/SELL/HOLD + confidence) for AI agents, from a live multi-timefra | 115 / $1 | 386 / $11 | 114 | — | 2026-10-11 | active |
| [FractalAI x402 Proofs](https://fractalai.net.co/.well-known/x402.json) | Post-quantum verification services for AI agents, self-facilitated on Base (USDC). Dilithium-2 (NIST FIPS 204) | 110 / $3 | 120 / $3 | 71 | — | 2026-10-08 | active |

### Inferences
- The official directory is mostly a marketing list, not a usage list: 116 of 206 entries have no Base settlement or Bazaar footprint by domain, and the active ones are dominated by a few facilitators, BlockRun, and a handful of data providers.
- The token-bearing universe is largely unconnected to measured x402 usage: 37 of 62 Base-contract tokens have no matching footprint, and the ones that do (DREAMS, HEU, MRDN, PAYAI, ANY, OTTO, GLORIA) mostly show large transaction counts with tiny dollar amounts, or circular volume (Meridian).
- Several assigned names have no visible x402 footprint on Base at all (Mastercard, Visa, Giza, Theoriq, Recall, Spectral, Wayfinder, Zora, Cookie DAO, Cred Protocol, Fluora, Pieverse, Kite AI) and several are Solana- or other-chain-first (Dexter, PayAI's token, Zauth's token, Kite, Pieverse). That is a flag for the researchers covering them, not proof the projects are fake.
- The projects with real, repeated Base usage that are not on the assigned list are BlockRun, FluxA, AX1, Cluster Protocol, ATXP, Anyspend and a tail of small API sellers (section 2).

### Gaps
- x402.org/ecosystem is gone; the directory snapshot is as of 2026-07-07, so projects added after that date are only visible if they also appear in usage data.
- Domain-based matching misses sellers that use a different domain or a shared payTo address; "unverified" rows may be active. Recipient addresses I could not name (for example the large unlabeled recipients in 3.4) stay unidentified because Blockscout blocks scripted lookups (HTTP 403), I did not use an Etherscan-family API (needs a key), and x402scan only names registered origins.
- x402scan indexes Base, Solana, Polygon and Optimism only; activity on other chains (Stellar, Celo, Monad, XRPL, Arc and others advertised in the Bazaar) is not in these numbers. Solana seller coverage is limited to the top-100 pages of 705 registered recipients.
- CoinGecko categories were fetched for the 62 Base-contract tokens but not the 73 others (the free API rate-limits); token websites come from CoinGecko coin pages (preferred) or DexScreener profiles and are missing for 2 of 62.
- Dune dashboards were not readable (the Dune profile pages load client-side and showed no dashboards for @x402 or @hashed_official), Artemis returned 404, and base.org/ecosystem is client-rendered. The WebSearch budget ran out mid-task, so I did not find Messari, Galaxy, The Block or Coinbase research posts on x402 volume.
- Status is based only on public settlement and Bazaar signals; off-chain revenue, private deployments and Solana-only activity are invisible here.

## 2. Ranked list of uncovered projects worth full due diligence

### Takeaway
Ranked by evidence of repeated Base usage first, then token presence, then credibility, the strongest uncovered names are BlockRun, FluxA, AX1, Cluster Protocol, ATXP and Laso Finance; the token-bearing uncovered names that matter are Anyspend (ANY), Treasure (MAGIC), Cluster Protocol (CP), Pocket Network (POKT) and SKALE (SKL), while most other Base-contract tokens in the CoinGecko x402 category show no x402 usage.

### Cited Findings
All "window" figures are Base, 2026-04-11 to 2026-10-11, from the [x402scan daily series](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D) and per-recipient series; "30d" figures are to 2026-10-11. One line each; full detail is in sections 1 and 3.

| Rank | Project | Type / token | Why it merits full due diligence (one line) | Evidence |
|---|---|---|---|---|
| 1 | [BlockRun](https://blockrun.ai) | LLM gateway / router; no token found | Produced 27.0M of the window's 41.5M Base tx (65%) and $450K USDC; #2 in the Bazaar by 30-day calls (78,844 calls, 1,073 payers); its traffic moved to Solana from 2026-08-20 to 2026-09-08 (22.5M Solana tx all-time) and Base fell to 211K tx in September; ClawRouter repo 6,622 stars | [x402scan](https://www.x402scan.com/recipient/0xe9030014f5dae217d0a152f02a043567b16c1abf), [GitHub](https://github.com/BlockRunAI/ClawRouter), [npm @blockrun/llm](https://www.npmjs.com/package/@blockrun/llm) (10,532 downloads/30d), [Solana Compass](https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months) |
| 2 | [FluxA](https://fluxapay.xyz) | Facilitator + agent wallet; no token found | #2 Base facilitator by window tx (2.66M, 6.4%) and by 30-day USDC ($322K), but one wallet paid $270K of it in 18 tx, so check how much is real wallet usage (49.7K buyers and 62.1K sellers all-time) | [x402scan](https://www.x402scan.com/facilitator/fluxa), [x402-list.com](https://x402-list.com), [whale table](#36-wash-trading-self-dealing-and-how-much-is-real-api-commerce) |
| 3 | [AX1 Console](https://ax1.vc) | Agent "launchpad" console, token-verdict API; no token found | #1 in the Bazaar by 30-day calls: 409,288 calls and 4,671 payers on one $0.02 "Base token verdict" endpoint (only $8.2K USDC), and its research arm publishes Dune x402 dashboards (@ax1research) | [Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0), [x402scan](https://www.x402scan.com/recipient/0x7284d41b5b852f2bd4c99bdf95043d84452d299c), [agenteconomy.to](https://agenteconomy.to) |
| 4 | [Cluster Protocol](https://api.clusterprotocol.ai) | Token CP on Base (`0x001aad84...3f77`) | $262K and 533K tx in the window (largest multi-buyer Base seller by USDC after BlockRun), 722 buyers and $54.8K in the last 30 days; its registry description does not say what is sold | [x402scan](https://www.x402scan.com/recipient/0x68396bd35874695ad86cd29410bd80a550991a2b), [CoinGecko](https://www.coingecko.com/en/coins/cluster-protocol) |
| 5 | [ATXP](https://atxp.ai) | Agent account / payments; no token found | Widest buyer base of any x402 seller in the lists I pulled: 108.5K Base buyers and 192.6K Solana buyers all-time, $122K / 314K tx on Base in the window (idle since 2026-06-18) and $232K on Solana | [x402scan Base](https://www.x402scan.com/recipient/0x10c140022927429afb5f7779f4bc5495da8c1e24), [Solana list](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D) |
| 6 | [Laso Finance](https://laso.finance) | Prepaid and gift cards; LASO on Solana | One of the few clearly real-world purchases: $267K in 111 Solana tx in the last 30 days (about $2,400 each) and $613K Solana all-time, plus $1.5K on Base | [Solana list](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0) |
| 7 | [x402.boats](https://mcp.x402.boats) | "Game for AI Agents"; no token found | $208K in the window, $197K of it in August 2026 (26K tx), then idle since 2026-09-04; check whether it was a promotion or self-funded | [x402scan](https://www.x402scan.com/recipient/0xb0af3ccf9154f81af07a194150113523767d7de0) |
| 8 | [Anyspend (B3)](https://x402.anyspend.com) | Token ANY on Base (`0xc17dda24...2712`) | Token plus facilitator (521K tx / $141K all-time, idle since 2026-08-17) plus a seller ($25K in the window) | [x402scan facilitator](https://www.x402scan.com/facilitator/anyspend), [CoinGecko](https://www.coingecko.com/en/coins/anyspend) |
| 9 | [dTelecom](https://x402.dtelecom.org) | Telecom APIs (WebRTC, speech-to-text); DTEL token has no contract data on CoinGecko | Real service: $112K / 53K tx in the window and $36K in 30 days, but only 25 buyers in the last 30 days, so concentrated | [x402scan](https://www.x402scan.com/recipient/0x47d3394c7234714e4b9e9b74827c12be847f9dda) |
| 10 | [KORUS](https://www.korusmusic.co) | Consumer music-creation app; no token found | 11,221 buyers in 30 days, the widest buyer base of any Base seller in x402scan's 30-day list, $18.7K; all activity is in the last 30 days | [x402scan](https://www.x402scan.com/recipient/0x8a12157b27c22fb239e558dc3cb43c7d1a8c0881) |
| 11 | Incumbent data providers: [Exa](https://exa.ai), [Nansen](https://docs.nansen.ai/getting-started/x402-payments), [Glassnode](https://x402.glassnode.com), [Tavily](https://x402.tavily.com), [Messari](https://messari.io/x402), [Arkham](https://api.arkm.com), [Zapper](https://public.zapper.xyz) | Established companies, no tokens | Live Base sellers with small dollars: Bazaar calls in 30 days Exa 5,456, Nansen 3,578 (4.7K Base tx), Glassnode 1,246, Tavily 978, Arkham 220; Nansen is a Foundation member | [Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0) |
| 12 | [Locus](https://paywithlocus.com) | Agent wallet with spend controls; no token found | Wraps 52 Bazaar resources (Gemini, Stability AI and others) for x402: 35.6K Base tx in 30 days but only $57 | [x402scan](https://www.x402scan.com/recipient/0x3c5cbe28eca3b96023c45d3f877da834f1c7d5fa) |
| 13 | [Treasure](https://x402.treasure.lol) | Token MAGIC on Base (`0xf1572d1d...3f43`) | Runs an x402 facilitator (2.5K tx all-time, last 2026-10-08) and the "AI Frens" x402 character-token launchpad; tiny usage but the clearest token-plus-launchpad story | [x402scan](https://www.x402scan.com/facilitator/treasure), [CoinGecko](https://www.coingecko.com/en/coins/magic) |
| 14 | [Pocket Network](https://agent.pocket.network) | Token POKT has a Base contract (`0x764a726d...a935`) | "Agentic Portal" with 114 Bazaar resources and 14,078 calls in 30 days, but only $70 | [Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0), [CoinGecko](https://www.coingecko.com/en/coins/pocket-network) |
| 15 | [AIsa](https://aisa.one) | Resource marketplace; no token found | Largest recipient by tx count ever on Base: 31.55M tx but only $416K all-time (19.2M tx in Dec 2025), idle since 2026-08-07; a case study in huge counts hiding tiny dollars | [x402scan](https://www.x402scan.com/recipient/0x66fa4d79ca84016b42352be33c908dd812952ec8) |
| 16 | [Ultravioleta DAO](https://facilitator.ultravioletadao.xyz) | Facilitator; no token found | Fastest-growing small facilitator: 25.5K tx / $6.5K in the last 30 days against 37.4K tx all-time; Rust, claims 19 mainnets | [x402scan](https://www.x402scan.com/facilitator/ultravioletadao) |
| 17 | [t54 labs](https://x402-secure.t54.ai/) | Risk-control API and XRPL facilitator; Foundation general member | x402-secure API logged 29.6M Base tx all-time (13.3M in Dec 2025) at about $0.001 each but only 353 in the window; check what is real | [x402scan](https://www.x402scan.com/recipient/0x0495d60c927b97d67d5018c6aa65c9b2bebaeed9) |
| 18 | [claw402](https://claw402.ai) | x402 API gateway; CLAW402 token on Solana only | 4.87M tx but only $9.5K in the window (second only to BlockRun among multi-buyer sellers by tx) | [x402scan](https://www.x402scan.com/recipient/0xa9dd7cc9cbf0e05551332209289f04be36bc2315) |
| 19 | [SKALE](https://skale.space) | Token SKL has a Base contract (`0xb9caa63e...a5fed3`); Foundation general member | In the CoinGecko x402 category; PayAI, Primer, RelAI and Kobaru list SKALE networks; SKALE's own Base x402 usage not found | [CoinGecko](https://www.coingecko.com/en/coins/skale), [awesome-x402](https://github.com/xpaysh/awesome-x402) |
| 20 | [Chainlink for Agents](https://agents.chain.link) | LINK is in the CoinGecko x402 category | 45,575 Bazaar calls in 30 days from only 3 payers (31.6K and 14.0K calls from one payer each), so it reads as internal or test traffic | [Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0) |
| 21 | [Vishwa](https://api.vishwalab.com) | API seller; no token found | 481K Base tx / $42K in the window and 106K Solana tx in the last 30 days (393 buyers); what it sells is not stated | [x402scan](https://www.x402scan.com/recipient/0x6a5e7d954f49712abf3f873f037ec845b7b8c666) |
| 22 | OneSource, Orbis API, MineBean, FortClaw, BaseHub, X Pay, OneShot Agent | Mid-size micro-sellers | Tens to hundreds of thousands of tx each and under $20K USDC each in the window; check which are products and which are games or farming | section 1.4 |
| 23 | OpenServ (SERV), Elsa (ELSA), Acurast (ACU), FLOCK, EigenCloud (EIGEN), peaq (PEAQ) | Base-contract tokens in the CoinGecko x402 category | No x402 footprint matched for any (Elsa's x402 origin idle since 2026-02-02); membership in the category alone is not usage | section 1.3a |
| 24 | [x402-list.com](https://x402-list.com), [x402watch](https://x402.printmoneylab.com), [agenteconomy.to](https://agenteconomy.to) | Data sources, not investments | x402-list.com independently reproduces x402scan's facilitator volumes; x402watch's wash label looks too narrow (see 3.6); both worth using, with caveats | section 3.9 |
| 25 | [Internet Court](https://github.com/internet-court/internet-court-skill) | GitHub skill bundle | 6,710 stars against 4 commits and 10 watchers, x402 only one of many standards named: probable star inflation, low priority | [repo](https://github.com/internet-court/internet-court-skill) |

### Inferences
- The uncovered projects with the most Base evidence are infrastructure and gateways (BlockRun, FluxA, ATXP, AX1), not the token-bearing agent projects that dominate the CoinGecko category; the two groups barely overlap.
- Ranks 1, 3, 4 and 5 can be checked quickly because each has a single identifiable recipient address on x402scan; ranks 2, 7 and 17 need a manual look at whether the dollars are product revenue.
- If the angle is "who is actually paying", BlockRun (volume), Laso (real purchases), KORUS (consumer breadth) and the incumbent data providers (credibility) are the clean examples; Meridian, FluxA's whale flows and the 2025 mint tokens are the cautionary ones (section 3.6).

### Gaps
- The ranking is my judgment from public settlement data; I have no revenue, user, funding or token-holder data, and "importance" is not independently measurable here.
- Several top names (Cluster Protocol, ATXP, x402.boats, Vishwa) describe themselves vaguely in the registry; I did not open their products to confirm what is sold.
- Tokens: for most uncovered projects I found no token, but I only checked CoinGecko's coin list and category, so a token launched elsewhere (for example on a launchpad without a CoinGecko page) would be missed.

## 3. Metrics: x402 activity on Base, April to October 2026

### Takeaway
In the six months to 2026-10-11 x402scan shows 41.5M Base transactions and $5.66M USDC (Solana: 25.6M tx and $1.51M). Base monthly USDC fell from $1.93M in April to $0.57M in September while monthly tx rose to 9M to 13M in June to August, because one seller (BlockRun) produced 65% of the window's Base tx. Roughly 27% to 49% of Base USDC looks like API-style commerce, 36% is a closed loop between the same wallets (Meridian) and 15% to 24% is a handful of large one-off transfers; Coinbase's facilitator carries 91% of tx. Solana out-counted Base on only 19 of 184 days (the episode ran from 2026-08-20 to 2026-09-08). The core npm packages grew 2.3x to 3.6x in daily downloads from April to September and the PyPI `x402` package 1.7x (2.6x by early October), with the v2 `@x402/*` packages far ahead of v1.

### Cited Findings

#### 3.1 Monthly transactions, USDC volume and participants on Base (with Solana for comparison)
Source: [x402scan daily series by chain](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D) summed by month (daily buckets; months before April are context for the October 2025 spike). \*Buyers and sellers are x402scan's per-day distinct counts summed across facilitator rows, so they over-count wallets using several facilitators; true monthly distinct counts cannot be built because x402scan only materialises 1-, 7-, 14-, 30-day and all-time windows ([time-range code](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/lib/time-range.ts)).

| Month | Base tx | Base USDC | Avg ticket (USDC) | Days with tx | Avg daily buyers* | Peak daily buyers* | Avg daily sellers* | Peak daily sellers* | Peak daily tx | Solana tx | Solana USDC | Base share of Base+Solana tx | Base share of USDC |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2025-10 (context) | 4.07M | $3.97M | $0.975 | 31 | 9.3K | 46K | 1.6K | 14K | 759K | 55K | $40K | 98.7% | 99.0% |
| 2025-11 (context) | 64.3M | $27.88M | $0.434 | 30 | 20K | 41K | 3.3K | 10K | 3.79M | 4.38M | $908K | 93.6% | 96.8% |
| 2025-12 (context) | 43.0M | $3.26M | $0.076 | 31 | 17K | 24K | 1.3K | 5.0K | 1.81M | 22.0M | $5.15M | 66.1% | 38.8% |
| 2026-01 (context) | 12.1M | $1.20M | $0.099 | 31 | 4.6K | 11K | 176 | 411 | 799K | 9.45M | $600K | 56.2% | 66.7% |
| 2026-02 (context) | 1.42M | $2.06M | $1.452 | 28 | 1.8K | 4.5K | 179 | 416 | 112K | 2.25M | $178K | 38.6% | 92.0% |
| 2026-03 (context) | 1.82M | $2.27M | $1.245 | 31 | 2.8K | 5.0K | 353 | 1.5K | 130K | 1.10M | $153K | 62.4% | 93.7% |
| 2026-04 | 2.30M | $1.93M | $0.838 | 30 | 2.4K | 8.2K | 1.6K | 4.1K | 152K | 430K | $123K | 84.3% | 94.0% |
| 2026-05 | 3.04M | $1.03M | $0.339 | 31 | 6.0K | 13K | 4.6K | 9.1K | 137K | 736K | $124K | 80.5% | 89.2% |
| 2026-06 | 12.8M | $788K | $0.062 | 30 | 4.1K | 13K | 3.3K | 8.6K | 988K | 603K | $211K | 95.5% | 78.9% |
| 2026-07 | 11.9M | $655K | $0.055 | 31 | 2.7K | 3.7K | 3.4K | 8.9K | 1.52M | 725K | $79K | 94.3% | 89.2% |
| 2026-08 | 9.07M | $1.03M | $0.114 | 31 | 2.4K | 3.5K | 1.1K | 2.0K | 1.29M | 12.2M | $424K | 42.6% | 70.9% |
| 2026-09 | 2.23M | $570K | $0.256 | 30 | 2.8K | 5.6K | 2.0K | 25K | 250K | 10.8M | $414K | 17.0% | 57.9% |
| 2026-10 (to Oct 11 only) | 719K | $246K | $0.343 | 11 | 3.7K | 5.8K | 1.5K | 2.9K | 109K | 192K | $166K | 79.0% | 59.8% |
| **Window 2026-04-11..2026-10-11 (184 days)** | **41.5M** | **$5.66M** | $0.136 | 184 | | | | | | **25.6M** | **$1.51M** | 61.8% | 78.9% |

- Base USDC per month, April to September 2026: $1.93M, $1.03M, $0.79M, $0.65M, $1.03M, $0.57M; tx: 2.30M, 3.04M, 12.8M, 11.9M, 9.07M, 2.23M; the first 11 days of October show 0.72M tx and $0.25M ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)).
- Average payment fell from $0.84 in April to $0.055 in July, the months BlockRun's roughly $0.017 calls took over (see 3.4) ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)).
- Busiest Base day in the window by tx was 2026-07-13 (1.52M tx); by USDC it was 2026-04-21 ($418K from 73K tx); the median Base day had about 112K tx, and the mean since 2026-09-15 is about 72.9K tx a day ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)).
- Context: Base peaked in November 2025 at 64.3M tx and $27.9M; cumulative Base tx reached 126.7M by 2026-03-31, consistent with Chainalysis' report of more than 100 million Base transactions through Q1 2026 ([Chainalysis](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/)). The first Base transfer in x402scan is 2025-05-09.

#### 3.2 Unique buyers and sellers (windows ending 2026-10-11)
Source: [x402scan network totals](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%7D%7D) for 1, 7, 30 days and all time ([1-day](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A1%7D%7D), [7-day](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A7%7D%7D), [all-time](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D)), plus the per-chain overall stats for 14 days (Base [30-day](https://www.x402scan.com/api/trpc/public.stats.overall?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%7D%7D) and [all-time](https://www.x402scan.com/api/trpc/public.stats.overall?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%7D%7D) shown as examples of the call). \*Over-counted as above.

| Window (ending 2026-10-11) | Base tx | Base USDC | Base buyers* | Base sellers* | Solana tx | Solana USDC | Solana buyers* | Solana sellers* |
|---|---|---|---|---|---|---|---|---|
| last 1 day | 57K | $13K | 3.0K | 1.1K | 14K | $2.9K | 167 | 97 |
| last 7 days | 520K | $212K | 14K | 6.1K | 135K | $116K | 544 | 181 |
| last 14 days | 1.02M | $382K | 24K | 9.2K | 230K | $250K | 772 | 272 |
| last 30 days | 2.17M | $703K | 35K | 39K | 506K | $368K | 1.4K | 417 |
| all time (since 2025-05-09) | 168.8M | $46.89M | 659K | 282K | 65.0M | $8.57M | 230K | 31K |

- Cross-checks on buyer counts: x402-list.com measures 10,871 distinct on-chain buyers across 713 services in the trailing 30 days ([x402-list.com](https://x402-list.com)); x402watch labels 45,836 buyers "organic_user" in its 2026-10-10 snapshot ([data](https://github.com/printmoneylab/x402watch-data)); the Bazaar shows 4,671 payers for AX1 alone and about 11.2K buyers for KORUS in x402scan's 30-day list.

#### 3.3 Facilitators by share on Base
Source: [x402scan daily Base series by facilitator](https://www.x402scan.com/api/trpc/public.facilitators.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%7D%7D), summed by month; each cell is tx share / USDC share of Base (the facilitator series sum exactly to the Base total, so every Base transfer is attributed to one listed facilitator). Window = 2026-04-11 to 2026-10-11.

| Month | Coinbase tx% / USD% | FluxA tx% / USD% | PayAI tx% / USD% | Meridian tx% / USD% | Dexter tx% / USD% | Daydreams tx% / USD% | Heurist tx% / USD% | Virtuals tx% / USD% | Other tx% / USD% |
|---|---|---|---|---|---|---|---|---|---|
| 2025-10 (context) | 68.7 / 59.6 | 0.0 / 0.0 | 10.0 / 17.3 | 0.0 / 0.0 | 0.0 / 0.0 | 3.7 / 2.3 | 0.0 / 0.0 | 0.0 / 0.0 | 17.6 / 20.8 |
| 2025-11 (context) | 69.2 / 81.9 | 0.0 / 0.0 | 9.5 / 6.7 | 0.0 / 0.0 | 0.0 / 0.0 | 14.9 / 9.5 | 3.9 / 0.0 | 0.2 / 0.6 | 2.4 / 1.2 |
| 2025-12 (context) | 64.2 / 39.2 | 0.0 / 0.0 | 15.9 / 1.7 | 0.0 / 20.2 | 0.0 / 0.0 | 4.9 / 0.3 | 12.0 / 0.1 | 1.3 / 35.9 | 1.7 / 2.6 |
| 2026-01 (context) | 18.9 / 30.0 | 0.0 / 0.0 | 73.8 / 3.9 | 0.1 / 43.5 | 0.0 / 0.0 | 0.0 / 0.0 | 2.7 / 1.7 | 2.4 / 15.9 | 2.0 / 5.0 |
| 2026-02 (context) | 49.9 / 14.3 | 0.0 / 0.0 | 15.5 / 0.4 | 1.3 / 13.9 | 0.2 / 0.0 | 0.3 / 0.0 | 0.0 / 0.0 | 31.1 / 68.7 | 1.7 / 2.7 |
| 2026-03 (context) | 47.6 / 15.5 | 0.0 / 0.0 | 17.3 / 9.4 | 1.0 / 8.9 | 1.1 / 0.0 | 0.2 / 0.1 | 0.0 / 0.0 | 28.5 / 59.7 | 4.3 / 6.3 |
| 2026-04 | 81.1 / 7.0 | 6.4 / 2.1 | 8.1 / 74.9 | 0.9 / 11.3 | 0.3 / 0.0 | 0.0 / 0.0 | 0.0 / 0.0 | 1.4 / 1.7 | 1.9 / 2.9 |
| 2026-05 | 75.3 / 16.4 | 16.1 / 5.5 | 5.9 / 1.1 | 0.7 / 72.9 | 0.5 / 0.1 | 0.0 / 0.0 | 0.0 / 0.0 | 0.1 / 0.0 | 1.5 / 4.1 |
| 2026-06 | 90.8 / 26.2 | 6.5 / 10.2 | 2.1 / 5.0 | 0.1 / 53.5 | 0.1 / 0.0 | 0.0 / 0.1 | 0.0 / 0.0 | 0.0 / 0.0 | 0.4 / 5.1 |
| 2026-07 | 94.7 / 53.0 | 4.4 / 2.8 | 0.3 / 0.4 | 0.1 / 42.0 | 0.2 / 0.1 | 0.0 / 0.1 | 0.0 / 0.0 | 0.0 / 0.0 | 0.3 / 1.6 |
| 2026-08 | 94.4 / 55.3 | 4.4 / 12.9 | 0.5 / 4.8 | 0.1 / 25.8 | 0.4 / 0.4 | 0.0 / 0.1 | 0.0 / 0.0 | 0.0 / 0.0 | 0.2 / 0.7 |
| 2026-09 | 87.2 / 39.3 | 9.3 / 32.7 | 1.5 / 1.0 | 0.4 / 25.4 | 0.0 / 0.0 | 0.0 / 0.1 | 0.0 / 0.0 | 0.1 / 0.0 | 1.5 / 1.4 |
| 2026-10 | 84.8 / 24.1 | 12.5 / 58.8 | 0.7 / 0.8 | 0.2 / 14.6 | 0.0 / 0.0 | 0.0 / 0.1 | 0.0 / 0.0 | 0.0 / 0.0 | 1.8 / 1.6 |
| **Window 2026-04-11..10-11** | 91.0 / 29.7 | 6.4 / 11.6 | 1.7 / 19.8 | 0.2 / 36.5 | 0.2 / 0.1 | 0.0 / 0.1 | 0.0 / 0.0 | 0.0 / 0.1 | 0.5 / 2.2 |

| Facilitator (Base) | Tx in window | % of Base tx | USDC in window | % of Base USDC |
|---|---|---|---|---|
| Coinbase (`coinbase`) | 37.7M | 91.0% | $1.68M | 29.7% |
| FluxA (`fluxa`) | 2.66M | 6.4% | $659K | 11.6% |
| PayAI (`payAI`) | 688K | 1.7% | $1.12M | 19.8% |
| Meridian (`mrdn`) | 83K | 0.2% | $2.06M | 36.5% |
| Dexter (`dexter`) | 82K | 0.2% | $5.1K | 0.1% |
| primer (`primer`) | 38K | 0.1% | $8.7K | 0.2% |
| polymer (`polymer`) | 34K | 0.1% | $5.6K | 0.1% |
| cascade (`cascade`) | 32K | 0.1% | $119 | 0.0% |
| ultravioletadao (`ultravioletadao`) | 31K | 0.1% | $6.7K | 0.1% |
| relai (`relai`) | 27K | 0.1% | $62K | 1.1% |
| Virtuals (`virtuals`) | 18K | 0.0% | $5.5K | 0.1% |
| anyspend (`anyspend`) | 15K | 0.0% | $25K | 0.4% |
| **Total attributed to listed facilitators** | **41.5M** | | **$5.66M** | |

- Last 30 days on Base (facilitators above x402scan's 100-tx floor): Coinbase 1.97M tx / $233K, FluxA 137K / $322K, Ultravioleta DAO 25.5K / $6.5K, PayAI 24.3K / $5.9K, Primer 5.8K / $1.5K, Polymer 4.7K / $1.6K, Meridian 3.4K / $129K, Virtuals 2.8K / $28 ([source](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)). Across Base and Solana the 30-day list also shows Figment (107K tx, Solana), three.ws (43K tx, Solana) and Dexter (30K tx) ([source](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)).
- All-time Base ranking by tx: Coinbase 117.0M, PayAI 23.6M, Daydreams 11.8M, Heurist 8.0M, FluxA 2.7M, Virtuals 2.0M; by USDC: Coinbase $29.2M, PayAI $4.43M, Virtuals $4.34M, Meridian $3.79M, Daydreams $2.76M ([source](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)).
- The December 2025 story that Dexter overtook Coinbase (about half of daily tx, from Dune data cited by Hashed) refers to all chains: on Base x402scan shows Dexter at 1.1% of tx in March 2026 and 0.2% in the window, while Dexter's seller origin has 25.9M tx on Solana ([Cryptopolitan](https://www.cryptopolitan.com/dexter-overtakes-coinbase-x402-transactions/), [source](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)).

#### 3.4 Top servers (sellers) by volume
Source: x402scan per-recipient daily series for 243 candidate recipients, summed over 2026-04-11..2026-10-11; names from the x402scan registry; "buyer-days" sums each day's distinct buyers (a breadth proxy). Class rules: Meridian round-trip wallet = recipient in Meridian's seller list; few-party large transfer = 15 or fewer buyer-days and at least $1,000; high-ticket one-offs = average at least $500 per tx and 500 or fewer tx.

**Top 25 Base recipients by USDC in the window**

| Rank | Recipient | Registry name | Tx (window) | USDC (window) | Buyer-days* | Class |
|---|---|---|---|---|---|---|
| 1 | [`0x8e7769d4...`](https://www.x402scan.com/recipient/0x8e7769d440b3460b92159dd9c6d17302b036e2d6) | (unregistered) | 30K | $746K | 502 | Meridian round-trip wallet |
| 2 | [`0xe9030014...`](https://www.x402scan.com/recipient/0xe9030014f5dae217d0a152f02a043567b16c1abf) | https://blockrun.ai | 27.0M | $450K | 11K | multi-buyer seller |
| 3 | [`0x57a6b054...`](https://www.x402scan.com/recipient/0x57a6b0547557ed5817d5988ce30fc4729aef0ed7) | (unregistered) | 8 | $407K | 8 | few-party large transfer |
| 4 | [`0xfa02300b...`](https://www.x402scan.com/recipient/0xfa02300b1a598daba1b27b2bf79f9775355dac82) | (unregistered) | 13 | $331K | 8 | few-party large transfer (FluxA) |
| 5 | [`0x68396bd3...`](https://www.x402scan.com/recipient/0x68396bd35874695ad86cd29410bd80a550991a2b) | https://api.clusterprotocol.ai | 533K | $262K | 64K | multi-buyer seller |
| 6 | [`0xb0af3ccf...`](https://www.x402scan.com/recipient/0xb0af3ccf9154f81af07a194150113523767d7de0) | https://mcp.x402.boats | 29K | $208K | 361 | multi-buyer seller |
| 7 | [`0x13db4caf...`](https://www.x402scan.com/recipient/0x13db4caf175f23f1429c2df6b333350c24705192) | (unregistered) | 6.8K | $199K | 515 | Meridian round-trip wallet |
| 8 | [`0xfe8f511d...`](https://www.x402scan.com/recipient/0xfe8f511d8542f687cf70b798c388ef4c3265794d) | (unregistered) | 6.8K | $198K | 520 | Meridian round-trip wallet |
| 9 | [`0xe55eb84c...`](https://www.x402scan.com/recipient/0xe55eb84c37e90dfb7304969e5c6bff02c600f748) | (unregistered) | 6.7K | $198K | 515 | Meridian round-trip wallet |
| 10 | [`0x542793a5...`](https://www.x402scan.com/recipient/0x542793a5f0e26fc6b7ec17653c14d010fcdcf089) | (unregistered) | 135 | $193K | 135 | high-ticket one-offs (avg >= $500/tx, <= 500 tx; unlabeled) |
| 11 | [`0x1cec447d...`](https://www.x402scan.com/recipient/0x1cec447da1915f018bd74006ff6d695468b68dd4) | (unregistered) | 5.8K | $156K | 501 | Meridian round-trip wallet |
| 12 | [`0xffde1acb...`](https://www.x402scan.com/recipient/0xffde1acbac169f822dabc3d97d6d7127dcae6003) | (unregistered) | 98 | $137K | 85 | high-ticket one-offs (avg >= $500/tx, <= 500 tx; unlabeled) |
| 13 | [`0xa6a90366...`](https://www.x402scan.com/recipient/0xa6a90366a307080bccb859642d3378121fe8809d) | (unregistered) | 5.2K | $131K | 493 | Meridian round-trip wallet |
| 14 | [`0xe2c37f7a...`](https://www.x402scan.com/recipient/0xe2c37f7ae68f60f640277ba3e85109127965f440) | (unregistered) | 3.1K | $127K | 68 | Meridian round-trip wallet |
| 15 | [`0x10c14002...`](https://www.x402scan.com/recipient/0x10c140022927429afb5f7779f4bc5495da8c1e24) | https://hub.atxp.ai | 314K | $122K | 133K | multi-buyer seller |
| 16 | [`0x47d3394c...`](https://www.x402scan.com/recipient/0x47d3394c7234714e4b9e9b74827c12be847f9dda) | https://x402.dtelecom.org | 53K | $112K | 2.4K | multi-buyer seller |
| 17 | [`0x475436ef...`](https://www.x402scan.com/recipient/0x475436ef0a97286081d0fc2a762ad6296949327b) | (unregistered) | 4.0K | $101K | 471 | Meridian round-trip wallet |
| 18 | [`0xe96e69c5...`](https://www.x402scan.com/recipient/0xe96e69c5f2aa672f6c49984923907422d90ff476) | (unregistered) | 4.6K | $64K | 30 | Meridian round-trip wallet |
| 19 | [`0x93862e5b...`](https://www.x402scan.com/recipient/0x93862e5b2b1fa10a01772e7e9ca7cdc7deb5ca25) | (unregistered) | 5.2K | $60K | 3.0K | multi-buyer seller |
| 20 | [`0xe5d5c29e...`](https://www.x402scan.com/recipient/0xe5d5c29e6fecc6fbd304e00c103506ecfe1baf00) | (unregistered) | 4.0K | $58K | 26 | Meridian round-trip wallet |
| 21 | [`0x1452af43...`](https://www.x402scan.com/recipient/0x1452af43065628a82464bafb8ceba13481db1fce) | (unregistered) | 69 | $53K | 69 | high-ticket one-offs (avg >= $500/tx, <= 500 tx; unlabeled) |
| 22 | [`0xfa5ffc8d...`](https://www.x402scan.com/recipient/0xfa5ffc8dfd54c45bed139e0676ea697e7d88b7e1) | (unregistered) | 67 | $51K | 67 | high-ticket one-offs (avg >= $500/tx, <= 500 tx; unlabeled) |
| 23 | [`0x4dff19eb...`](https://www.x402scan.com/recipient/0x4dff19ebae58a1a736d0ec020835ead62c94b2a4) | (unregistered) | 67 | $51K | 67 | high-ticket one-offs (avg >= $500/tx, <= 500 tx; unlabeled) |
| 24 | [`0xce2646d8...`](https://www.x402scan.com/recipient/0xce2646d8b6ab269987f3c8823022ed4a0ce31318) | (unregistered) | 2 | $50K | 2 | few-party large transfer (FluxA) |
| 25 | [`0x6a5e7d95...`](https://www.x402scan.com/recipient/0x6a5e7d954f49712abf3f873f037ec845b7b8c666) | https://api.vishwalab.com | 481K | $42K | 19K | multi-buyer seller |

**Top 20 multi-buyer Base sellers by transactions in the window**

| Rank | Recipient | Registry name | Tx (window) | USDC (window) | Buyer-days* |
|---|---|---|---|---|---|
| 1 | [`0xe9030014...`](https://www.x402scan.com/recipient/0xe9030014f5dae217d0a152f02a043567b16c1abf) | https://blockrun.ai | 27.0M | $450K | 11K |
| 2 | [`0xa9dd7cc9...`](https://www.x402scan.com/recipient/0xa9dd7cc9cbf0e05551332209289f04be36bc2315) | https://claw402.ai | 4.87M | $9.5K | 5.8K |
| 3 | [`0xfe802b35...`](https://www.x402scan.com/recipient/0xfe802b35182f49778eec14db3153fcb8b92a47ee) | (unregistered) | 1.23M | $1.2K | 37K |
| 4 | [`0x68396bd3...`](https://www.x402scan.com/recipient/0x68396bd35874695ad86cd29410bd80a550991a2b) | https://api.clusterprotocol.ai | 533K | $262K | 64K |
| 5 | [`0x6a5e7d95...`](https://www.x402scan.com/recipient/0x6a5e7d954f49712abf3f873f037ec845b7b8c666) | https://api.vishwalab.com | 481K | $42K | 19K |
| 6 | [`0x2bb72231...`](https://www.x402scan.com/recipient/0x2bb72231eed303cc91a462a1fa738b42b6a9ac6d) | https://orbisapi.com | 439K | $2.1K | 1.2K |
| 7 | [`0x7284d41b...`](https://www.x402scan.com/recipient/0x7284d41b5b852f2bd4c99bdf95043d84452d299c) | https://ax1.vc | 412K | $8.2K | 7.9K |
| 8 | [`0x325bdf6f...`](https://www.x402scan.com/recipient/0x325bdf6f7efab24a2210c48c1b64cab2eae1d430) | https://stableenrich.dev | 405K | $12K | 8.9K |
| 9 | [`0x9c955c40...`](https://www.x402scan.com/recipient/0x9c955c40dc98fce89a133f402ffbf94070e6e299) | (unregistered) | 392K | $395 | 7.1K |
| 10 | [`0x10c14002...`](https://www.x402scan.com/recipient/0x10c140022927429afb5f7779f4bc5495da8c1e24) | https://hub.atxp.ai | 314K | $122K | 133K |
| 11 | [`0x9dba4146...`](https://www.x402scan.com/recipient/0x9dba414637c611a16bea6f0796bfcbcbdc410df8) | https://x402.twit.sh | 216K | $1.4K | 1.9K |
| 12 | [`0x6a0a10ff...`](https://www.x402scan.com/recipient/0x6a0a10ffd285c971b841bee8892878c0d583bf67) | https://payment.ardrive.io | 203K | $1.0K | 150 |
| 13 | [`0x158e90dd...`](https://www.x402scan.com/recipient/0x158e90dd58fbe897ed8c244f472febee37283d00) | (unregistered) | 191K | $1.9K | 264 |
| 14 | [`0x78f99337...`](https://www.x402scan.com/recipient/0x78f993378ff7890daac1689f79e7db2291e73928) | https://api.minebean.com | 154K | $15K | 189 |
| 15 | [`0x0e84dded...`](https://www.x402scan.com/recipient/0x0e84ddedaae6a779c462c22a59f301ec31b6b808) | https://x402.ottoai.services | 140K | $365 | 6.2K |
| 16 | [`0x9fb365e4...`](https://www.x402scan.com/recipient/0x9fb365e4e9385e2a39febad70368267e6f571d9a) | https://win.oneshotagent.com | 123K | $1.0K | 893 |
| 17 | [`0x6d274867...`](https://www.x402scan.com/recipient/0x6d27486790ce5918f1bc68be3fccc25304d09d31) | (unregistered) | 104K | $0 | 153 |
| 18 | [`0x40a8cdd6...`](https://www.x402scan.com/recipient/0x40a8cdd6a10ec1a8cb3dfb2834675e7a2cf4ad8b) | https://api.loyalspark.online | 101K | $698 | 12K |
| 19 | [`0x6d6e695b...`](https://www.x402scan.com/recipient/0x6d6e695b09861467c7d462f5aaf31cf3540b9192) | (unregistered) | 100K | $695 | 2.7K |
| 20 | [`0x52e29e0d...`](https://www.x402scan.com/recipient/0x52e29e0d2aa49bfbfc548c0a9f2196f4aa51f3ea) | https://api.onesource.io | 98K | $408 | 8.3K |

**Bazaar view (Coinbase-facilitated, listed resources), 30 days to 2026-10-11**

| Rank | Host | Resources | Calls (30d) | Share of all Bazaar calls | Payers (sum over resources) | Networks accepted | Service name |
|---|---|---|---|---|---|---|---|
| 1 | www.ax1.vc | 1 | 409,288 | 43.8% | 4,671 | Base | AX1 Console |
| 2 | blockrun.ai | 105 | 78,844 | 8.4% | 1,073 | Base | BlockRun.AI |
| 3 | agents.chain.link | 3 | 45,575 | 4.9% | 3 | Base | — |
| 4 | win.oneshotagent.com | 17 | 45,295 | 4.8% | 89 | Base | — |
| 5 | www.api-xpay.com | 14 | 42,380 | 4.5% | 1,197 | Base | X Pay |
| 6 | x402.sniperx.fun | 10 | 34,524 | 3.7% | 51 | Solana | — |
| 7 | stableenrich.dev | 15 | 30,532 | 3.3% | 443 | Base, Solana | StableEnrich |
| 8 | keyring-agent.blockchhub.link | 6 | 24,542 | 2.6% | 125 | Base | — |
| 9 | agent.pocket.network | 113 | 14,078 | 1.5% | 496 | Base | Pocket Network |
| 10 | api.onesource.io | 70 | 13,275 | 1.4% | 12,389 | Base | — |
| 11 | svm402.com | 15 | 12,506 | 1.3% | 51 | Solana | svm402-service |
| 12 | market.datapackvibe.com | 8,447 | 11,304 | 1.2% | 11,238 | Base | Blender: Convert Glb |
| 13 | agent402.tools | 608 | 8,074 | 0.9% | 2,023 | Algorand, Arbitrum, Avalanche, Base, Celo | Responses pro (OpenAI Responses |
| 14 | api.solenrich.com | 50 | 7,366 | 0.8% | 152 | Base, Solana | SolEnrich |
| 15 | api.exa.ai | 2 | 5,456 | 0.6% | 123 | Arc, Base, Solana, World Chain | Exa |

**Top Base buyers, last 30 days** ([source](https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D); wallets are unlabeled)

By USDC:

| Rank | Buyer wallet | USDC (30d) | Tx (30d) | Distinct sellers | Facilitator(s) |
|---|---|---|---|---|---|
| 1 | [`0x15eae079...`](https://www.x402scan.com/recipient/0x15eae0792636b3dca7b5002f673b66d27c9d7aff) | $270K | 18 | 5 | fluxa |
| 2 | [`0xacc7aebf...`](https://www.x402scan.com/recipient/0xacc7aebf890612432522c7971cf3882272cdb406) | $42K | 25 | 17 | fluxa |
| 3 | [`0xe55eb84c...`](https://www.x402scan.com/recipient/0xe55eb84c37e90dfb7304969e5c6bff02c600f748) | $20K | 560 | 6 | mrdn |
| 4 | [`0x1cec447d...`](https://www.x402scan.com/recipient/0x1cec447da1915f018bd74006ff6d695468b68dd4) | $20K | 579 | 5 | mrdn |
| 5 | [`0xa6a90366...`](https://www.x402scan.com/recipient/0xa6a90366a307080bccb859642d3378121fe8809d) | $20K | 562 | 6 | mrdn |
| 6 | [`0x13db4caf...`](https://www.x402scan.com/recipient/0x13db4caf175f23f1429c2df6b333350c24705192) | $19K | 543 | 5 | mrdn |
| 7 | [`0xfe8f511d...`](https://www.x402scan.com/recipient/0xfe8f511d8542f687cf70b798c388ef4c3265794d) | $19K | 554 | 5 | mrdn |
| 8 | [`0x475436ef...`](https://www.x402scan.com/recipient/0x475436ef0a97286081d0fc2a762ad6296949327b) | $19K | 529 | 6 | mrdn |
| 9 | [`0x1cfffac9...`](https://www.x402scan.com/recipient/0x1cfffac9aa5590338f2650f1461b70feddad0fcb) | $13K | 69 | 2 | mrdn |
| 10 | [`0x4853c070...`](https://www.x402scan.com/recipient/0x4853c070ccce3ccead5f6221b68ed9dede945255) | $11K | 2 | 1 | coinbase |

By transaction count:

| Rank | Buyer wallet | Tx (30d) | USDC (30d) | Distinct sellers | Facilitator(s) |
|---|---|---|---|---|---|
| 1 | [`0xcfa370b0...`](https://www.x402scan.com/recipient/0xcfa370b01125f985ca1be78bfda9fd790b3da8dc) | 45K | $479 | 1 | coinbase |
| 2 | [`0x9d3d9410...`](https://www.x402scan.com/recipient/0x9d3d9410be95fa1d230734b961997427fc61d837) | 44K | $852 | 749 | coinbase |
| 3 | [`0x355d6082...`](https://www.x402scan.com/recipient/0x355d6082235395569a48004ec34b30b541cf4d32) | 44K | $68 | 1 | coinbase |
| 4 | [`0x27abcddd...`](https://www.x402scan.com/recipient/0x27abcddd44c4959ac729d080703e677f13a3248c) | 37K | $73 | 28 | coinbase |
| 5 | [`0x52ad2c4e...`](https://www.x402scan.com/recipient/0x52ad2c4ed3a315a4ab6cc631cb5cf1a4428d1fee) | 32K | $64 | 1 | coinbase |
| 6 | [`0x105538b0...`](https://www.x402scan.com/recipient/0x105538b0d9744c9e2442b91dd26cc77c1abe5cf1) | 28K | $55 | 1 | coinbase |
| 7 | [`0x102e3c4a...`](https://www.x402scan.com/recipient/0x102e3c4af5b144c4235ab73bfecd948bf7aaab43) | 27K | $54 | 1 | coinbase |
| 8 | [`0x8000dce4...`](https://www.x402scan.com/recipient/0x8000dce4a82e68053326c1f2853d00081084efeb) | 26K | $262 | 1 | coinbase |
| 9 | [`0xefa2a5b5...`](https://www.x402scan.com/recipient/0xefa2a5b572d665778849834f936bf4756c4d54e9) | 26K | $49 | 1 | coinbase, mogami |
| 10 | [`0xa3fa8524...`](https://www.x402scan.com/recipient/0xa3fa85244686a5264bdacedff7e8fa8a0b191753) | 24K | $244 | 24,383 | coinbase |

The tenth wallet by tx count paid 24,383 different sellers once each (about $244 in total), which looks like a crawler or indexer probing the catalogue rather than a customer (inference); the first, third and fifth wallets by tx count each paid a single seller tens of thousands of times for $50 to $480 in total.

- In the last 30 days, the 25 largest Base recipients by USDC hold 89.9% of that period's $703K, and the largest 10 buyers hold 64.5% ([source](https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [buyers](https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)).

#### 3.5 Base versus Solana and other chains
Source: [x402scan daily series by chain](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D) summed by ISO week.

| Week starting (Mon) | Base tx | Base USDC | Solana tx | Solana USDC | Base share of tx |
|---|---|---|---|---|---|
| 2026-04-06 | 533K | $519K | 61K | $26K | 89.7% |
| 2026-04-13 | 521K | $295K | 108K | $24K | 82.8% |
| 2026-04-20 | 681K | $903K | 121K | $42K | 84.9% |
| 2026-04-27 | 670K | $203K | 141K | $33K | 82.6% |
| 2026-05-04 | 662K | $143K | 207K | $40K | 76.2% |
| 2026-05-11 | 696K | $273K | 221K | $24K | 75.9% |
| 2026-05-18 | 681K | $271K | 187K | $42K | 78.4% |
| 2026-05-25 | 684K | $261K | 71K | $14K | 90.6% |
| 2026-06-01 | 993K | $228K | 77K | $56K | 92.8% |
| 2026-06-08 | 2.05M | $161K | 100K | $52K | 95.4% |
| 2026-06-15 | 4.18M | $170K | 193K | $53K | 95.6% |
| 2026-06-22 | 4.55M | $191K | 198K | $45K | 95.8% |
| 2026-06-29 | 2.15M | $122K | 92K | $20K | 95.9% |
| 2026-07-06 | 4.89M | $170K | 105K | $5.6K | 97.9% |
| 2026-07-13 | 3.20M | $152K | 172K | $37K | 94.9% |
| 2026-07-20 | 1.53M | $127K | 259K | $13K | 85.5% |
| 2026-07-27 | 1.48M | $157K | 165K | $16K | 90.0% |
| 2026-08-03 | 1.50M | $268K | 87K | $48K | 94.5% |
| 2026-08-10 | 2.41M | $308K | 187K | $40K | 92.8% |
| 2026-08-17 | 4.28M | $253K | 2.78M | $87K | 60.6% |
| 2026-08-24 | 491K | $135K | 7.87M | $189K | 5.9% |
| 2026-08-31 | 627K | $102K | 9.79M | $158K | 6.0% |
| 2026-09-07 | 383K | $72K | 2.05M | $121K | 15.7% |
| 2026-09-14 | 413K | $120K | 125K | $47K | 76.8% |
| 2026-09-21 | 673K | $183K | 87K | $82K | 88.6% |
| 2026-09-28 | 509K | $166K | 101K | $111K | 83.4% |
| 2026-10-05 | 425K | $205K | 120K | $111K | 78.0% |

- Solana out-counted Base on tx on 19 of the 184 days in the window; the first such day was 2026-08-20, and Base's weekly share of Base+Solana tx fell to 5.9% in the week of 2026-08-24 and was back at 76.8% by the week of 2026-09-14 ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)). The [Solana Compass report](https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months) (2026-08-25) attributes the flip to BlockRun routing traffic through Solana, citing x402scan.
- The Solana Compass framing (Base held the lead for six months until 2026-08-25, with Solana's one earlier edge on 2026-01-20) does not match x402scan: its daily series has Solana ahead on 26 of 28 days from 2026-01-22 to 2026-02-18 (February 2026 Base 1.42M tx versus Solana 2.25M) and on 19 days from 2026-08-20 to 2026-09-08; the rivals researcher's Artemis-based figures (Solana 76% of x402 tx in the four weeks to 2026-09-22) agree on direction ([their notes](competition_rival_rails_chains.md)).
- Last 30 days: Base 2.17M tx / $703K versus Solana 0.51M tx / $368K, i.e. Base 81% of tx and 66% of USDC ([source](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%7D%7D)). All-time: Base 168.8M tx / $46.9M, Solana 65.0M tx / $8.57M, Polygon 190 tx, Optimism none ([source](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D)).
- Solana's top sellers in the last 30 days by tx: sol.blockrun.ai 226.7K, Vishwa 106.2K, SniperX 33.8K, three.ws 32.8K, Xona Agent 16.4K, SVM402 12.2K, BotPay 11.9K; by USDC: Laso Finance $267K from 111 tx ([source](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)).
- Chains advertised in the Bazaar (supply side, not usage), count of `accepts` entries: Base 33,427, Solana 8,328, Polygon 4,832, Arbitrum 2,787, Base Sepolia 2,397, Optimism 1,719, Arc 1,358, Monad 920 ([Bazaar API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0)).

#### 3.6 Wash trading, self-dealing, and how much is real API commerce
**(a) The October-December 2025 mint era.** Base logged 111.3M tx and $35.1M USDC in Oct-Dec 2025 (4.07M + 64.3M + 43.0M tx), then 12.1M tx in January 2026 ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)). In November 2025 five recipients took 90.7% of Base USDC:

| Nov 2025 recipient | USDC | % of Base Nov-2025 USDC | Tx | % of Base Nov-2025 tx |
|---|---|---|---|---|
| ARVOS | $11.45M | 41.1% | 12.1M | 18.9% |
| QRBase | $7.00M | 25.1% | 886K | 1.4% |
| Barvis | $2.53M | 9.1% | 10.8M | 16.8% |
| AinX402/AInalyst | $2.35M | 8.4% | 6.42M | 10.0% |
| Canza | $1.96M | 7.0% | 6.17M | 9.6% |
| **Top 5 combined** | **$25.29M** | **90.7%** | **36.4M** | **56.6%** |

Chainalysis describes the same episode: Q4 2025 volume driven largely by meme-coin activity, particularly PING, a pay-to-mint test where users paid 1 USDC per mint and which processed more than 150,000 transactions in its first month; payer retention of 87% during the PING rush fell to 5% once those wallets went dormant; and payments of $1 or more rose from 49% of value in early 2025 to 95% by early 2026 ([Chainalysis](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/)). Fifteen of the 17 mint-era recipients I traced are dead or dormant (section 1.5).

**(b) Meridian: a closed loop.** Meridian's facilitator carried 36.5% of Base USDC in the window on 0.2% of tx. In the last 30 days seven wallets appear on both sides of its flows and paid almost exactly what they received; all-time, 41 wallets sit on both sides of 65 sellers and 68 buyers, accounting for 96.2% of its $3.79M ([sellers 30d](https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [buyers 30d](https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [sellers all-time](https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [buyers all-time](https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)):

| Wallet | Paid as buyer, last 30d (USDC / tx) | Received as seller, last 30d (USDC / tx) |
|---|---|---|
| [`0xe55eb84c...`](https://www.x402scan.com/recipient/0xe55eb84c37e90dfb7304969e5c6bff02c600f748) | $20K / 560 | $20K / 565 |
| [`0x1cec447d...`](https://www.x402scan.com/recipient/0x1cec447da1915f018bd74006ff6d695468b68dd4) | $20K / 579 | $20K / 565 |
| [`0xa6a90366...`](https://www.x402scan.com/recipient/0xa6a90366a307080bccb859642d3378121fe8809d) | $20K / 562 | $20K / 570 |
| [`0x13db4caf...`](https://www.x402scan.com/recipient/0x13db4caf175f23f1429c2df6b333350c24705192) | $19K / 545 | $19K / 549 |
| [`0xfe8f511d...`](https://www.x402scan.com/recipient/0xfe8f511d8542f687cf70b798c388ef4c3265794d) | $19K / 555 | $19K / 550 |
| [`0x475436ef...`](https://www.x402scan.com/recipient/0x475436ef0a97286081d0fc2a762ad6296949327b) | $18K / 528 | $18K / 524 |
| [`0x7cb60b6f...`](https://www.x402scan.com/recipient/0x7cb60b6fb38e1f13ffa72683123f531f64d424c8) | $1 / 1 | $1 / 1 |
| **7 wallets on both sides** | **$116K** | **$115K** |
| Meridian 30d facilitator total (14 buyers, 14 sellers) | $129K | $129K |
| All-time: 41 wallets on both sides of 65 sellers / 68 buyers | paid $3.64M | received $3.63M (facilitator all-time total $3.79M; overlap share 96.2%) |

**(c) FluxA and single-wallet whales.** Of FluxA's $322K in the last 30 days, one wallet paid $270K in 18 tx; the biggest recipient received $220K in 5 tx from a single buyer ([buyers](https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22fluxa%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D), [sellers](https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22fluxa%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)):

| Side | Wallet | Last 30d USDC | Tx | Counterparties |
|---|---|---|---|---|
| buyer | [`0x15eae079...`](https://www.x402scan.com/recipient/0x15eae0792636b3dca7b5002f673b66d27c9d7aff) | $270K | 18 | 5 sellers |
| buyer | [`0xacc7aebf...`](https://www.x402scan.com/recipient/0xacc7aebf890612432522c7971cf3882272cdb406) | $42K | 25 | 17 sellers |
| buyer | [`0x577d7ceb...`](https://www.x402scan.com/recipient/0x577d7ceb8325fdf13072623e42d739a15b1a0bd8) | $2.9K | 122 | 3 sellers |
| buyer | [`0x093a1ead...`](https://www.x402scan.com/recipient/0x093a1ead779b6ff919a026a794e32c812c3592e0) | $1.5K | 12 | 3 sellers |
| buyer | [`0xd2f74a14...`](https://www.x402scan.com/recipient/0xd2f74a14522d40e4a1d7fbb62aa97ce99fa1a7e5) | $1.5K | 12 | 5 sellers |
| seller | [`0xfa02300b...`](https://www.x402scan.com/recipient/0xfa02300b1a598daba1b27b2bf79f9775355dac82) | $220K | 5 | 1 buyers |
| seller | [`0xce2646d8...`](https://www.x402scan.com/recipient/0xce2646d8b6ab269987f3c8823022ed4a0ce31318) | $50K | 2 | 1 buyers |
| seller | [`0x6d3d6df3...`](https://www.x402scan.com/recipient/0x6d3d6df3f5394d588e4a4ce798fe59820b901ace) | $10K | 1 | 1 buyers |
| seller | [`0x1a199cd4...`](https://www.x402scan.com/recipient/0x1a199cd404b4eea21678fe6713c8bc807f9dacf4) | $8.0K | 1 | 1 buyers |
| seller | [`0x63f10330...`](https://www.x402scan.com/recipient/0x63f103304ed9f0f1b47b90b10b30e47b639c46c9) | $7.5K | 1 | 1 buyers |

Concentration of Base buyers, last 30 days ([source](https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)): the top buyer alone is 38.4% of USDC, and the top 25 buyers by USDC make only 1.0% of tx while the top 25 buyers by tx count make 26.0% of tx but only 1.3% of USDC:

| Top-N Base buyers by USDC (last 30d) | USDC | % of Base 30d USDC | Tx | % of Base 30d tx |
|---|---|---|---|---|
| top 1 | $270K | 38.4% | 18 | 0.00% |
| top 5 | $372K | 52.9% | 1.7K | 0.08% |
| top 10 | $453K | 64.5% | 3.4K | 0.16% |
| top 25 | $507K | 72.1% | 22K | 1.03% |
| top 100 | $559K | 79.5% | 203K | 9.32% |
| top 10 by tx count | $2.2K | 0.3% | 334K | 15.3% |
| top 25 by tx count | $9.1K | 1.3% | 566K | 26.0% |
| top 100 by tx count | $15K | 2.2% | 959K | 44.1% |

**(d) Decomposition of the window's Base volume** (recipient-level classes defined in 3.4; "registered" = appears in x402scan's Bazaar registry):

| Class (Base, 2026-04-11..2026-10-11) | Recipients | Tx | % of Base tx | USDC | % of Base USDC |
|---|---|---|---|---|---|
| Meridian round-trip wallet | 19 | 79K | 0.2% | $2.04M | 36.1% |
| multi-buyer seller (avg ticket < $500), registered in Bazaar/x402scan | 95 | 36.5M | 88.0% | $1.36M | 24.0% |
| high-ticket one-offs (avg >= $500/tx, <= 500 tx; unlabeled) | 7 | 438 | 0.0% | $486K | 8.6% |
| few-party large transfer (FluxA) | 12 | 91 | 0.0% | $447K | 7.9% |
| few-party large transfer | 1 | 8 | 0.0% | $407K | 7.2% |
| multi-buyer seller (avg ticket < $500), unregistered | 58 | 2.48M | 6.0% | $190K | 3.4% |
| (long tail: ~38.8K other recipients active in 30d alone; not itemised) | n/a | 2.41M | 5.8% | $733K | 13.0% |
| **Base total** | | **41.5M** | 100% | **$5.66M** | 100% |

Estimate: API-style commerce is the two multi-buyer rows, $1.55M or about 27% of Base USDC and about 94% of tx (strict). Adding the unclassified long tail and the high-ticket one-offs gives an upper bound of about $2.77M or 49% of USDC. Equivalent daily figures: about $8.4K to $15K of API-style USDC a day on Base, against $30.8K a day reported in total.

**(e) Independent views.** x402-list.com says listed services cover 34.8% of the flow it can measure over 30 days and that its top 10 services hold 97.1% of settlement volume ([x402-list.com](https://x402-list.com)), in line with the 21% of Base 30-day USDC (and 80% of tx) that goes to Bazaar-registered recipients ($147.3K of $702.7K; 1.74M of 2.17M tx; [source](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)). x402watch classifies 87.4% of its 30-day volume as real in its 2026-10-10 snapshot but flags only $979 as wash in that window, while the Meridian loop moved $129K ([x402watch data](https://github.com/printmoneylab/x402watch-data)); its flagged wash volume was $130,774 in the 2026-08-10 snapshot and $57 in the 2026-09-10 one, which shows the filter is unstable. CoinDesk's estimate of about $28K a day of real commerce in March 2026 comes via [presenc.ai](https://presenc.ai/research/x402-protocol-adoption-tracker-2026) (snapshot 2026-05-15).

#### 3.7 Package downloads (npm and PyPI)
Source: [npm download API](https://api.npmjs.org/downloads/range/2026-04-01:2026-10-10/x402-fetch) for 2026-04-01..2026-10-10 and [pypistats](https://pypistats.org/api/packages/x402/overall?mirrors=false) (without mirrors; data starts 2026-04-08). Figures are average downloads per day for the month (October = 1 to 10). Counts include CI, mirrors and transitive installs (for example `@x402/core` is a dependency of the other `@x402/*` packages).

| npm package | Apr | May | Jun | Jul | Aug | Sep | Oct 1-10 | Sep/Apr | 6-month total |
|---|---|---|---|---|---|---|---|---|---|
| `x402` | 24,492 | 33,391 | 37,022 | 45,155 | 49,847 | 57,640 | 65,177 | 2.35x | 8,206,542 |
| `@x402/core` | 11,586 | 13,906 | 23,357 | 23,655 | 34,986 | 41,913 | 51,350 | 3.62x | 5,068,148 |
| `@x402/evm` | 8,731 | 9,138 | 10,042 | 13,912 | 21,968 | 27,422 | 33,963 | 3.14x | 3,121,060 |
| `@x402/extensions` | 4,888 | 6,255 | 10,219 | 8,825 | 13,025 | 17,769 | 22,861 | 3.64x | 2,086,155 |
| `@x402/fetch` | 5,886 | 5,908 | 6,604 | 9,641 | 15,017 | 16,354 | 17,455 | 2.78x | 1,987,427 |
| `@coinbase/x402` | 3,233 | 4,678 | 10,083 | 6,787 | 8,521 | 8,050 | 11,956 | 2.49x | 1,380,099 |
| `@x402/svm` | 3,157 | 3,848 | 6,637 | 7,268 | 9,681 | 10,645 | 11,552 | 3.37x | 1,373,390 |
| `x402-fetch` | 1,915 | 2,430 | 3,315 | 2,754 | 3,184 | 3,176 | 1,905 | 1.66x | 530,631 |
| `@x402/express` | 1,597 | 1,702 | 1,431 | 2,297 | 3,650 | 4,347 | 4,091 | 2.72x | 499,241 |
| `@x402/hono` | 832 | 1,395 | 1,362 | 1,772 | 3,067 | 4,902 | 7,592 | 5.89x | 482,041 |
| `@x402/next` | 649 | 935 | 1,057 | 1,274 | 1,752 | 2,281 | 3,747 | 3.51x | 279,890 |
| `@x402/paywall` | 337 | 501 | 592 | 634 | 894 | 1,028 | 1,872 | 3.05x | 140,347 |
| `x402-express` | 491 | 552 | 506 | 642 | 633 | 1,137 | 1,299 | 2.31x | 133,639 |
| `x402-axios` | 430 | 912 | 700 | 882 | 640 | 528 | 196 | 1.23x | 127,129 |
| `@x402/mcp` | 90 | 208 | 232 | 431 | 654 | 694 | 1,130 | 7.73x | 81,838 |
| `@x402/axios` | 289 | 334 | 305 | 386 | 323 | 265 | 148 | 0.92x | 59,565 |
| `x402-next` | 396 | 338 | 242 | 244 | 247 | 320 | 327 | 0.81x | 57,685 |
| `x402-hono` | 114 | 177 | 166 | 161 | 301 | 234 | 108 | 2.05x | 36,302 |
| `@x402/stellar` | 117 | 67 | 111 | 179 | 430 | 427 | 381 | 3.64x | 44,463 |
| `@payai/facilitator` | 116 | 99 | 82 | 134 | 168 | 289 | 332 | 2.50x | 30,367 |
| `@x402/avm` | 9 | 21 | 46 | 84 | 270 | 233 | 215 | 25.59x | 22,408 |
| `@faremeter/middleware` | 77 | 155 | 204 | 161 | 74 | 87 | 73 | 1.14x | 23,849 |
| `x402-solana` | 48 | 71 | 35 | 36 | 99 | 116 | 109 | 2.45x | 13,479 |
| `mcpay` | 8 | 12 | 8 | 12 | 15 | 8 | 11 | 0.98x | 2,023 |

- Aggregates (average downloads per day, April / September / October 1-10): v2 framework wrappers (`@x402/fetch`, `axios`, `express`, `hono`, `next`) 9.3K / 28.1K / 33.0K; v1 wrappers (`x402-fetch`, `x402-axios`, `x402-express`, `x402-hono`, `x402-next`) 3.3K / 5.4K / 3.8K; all listed v2 packages 38.2K / 128.3K / 156.4K versus v1 including `x402` 27.8K / 63.0K / 69.0K ([source](https://api.npmjs.org/downloads/range/2026-04-01:2026-10-10/x402-fetch)).
- Latest versions: `x402` 1.2.0 (2026-04-16) and `@x402/*` 2.28.0 (2026-09-29) ([npm registry search](https://registry.npmjs.org/-/v1/search?text=x402&size=250&from=0)).
- PyPI `x402`: 3,720 downloads a day in April (23 days from 2026-04-08), 3,740 in May, 5,689 in June, 5,760 in July, 5,936 in August, 6,489 in September and 9,539 in 2026-10-01..10; pypistats reports 204,765 for the last month, 70,494 for the last week and 8,391 for the last day as of 2026-10-11 ([pypistats](https://pypistats.org/api/packages/x402/overall?mirrors=false), [recent](https://pypistats.org/api/packages/x402/recent)).
- Other ecosystem packages, downloads in the 30 days to 2026-10-10: `@circle-fin/x402-batching` 65,480; `@payai/facilitator` 10,761; `@blockrun/llm` 10,532; `@okxweb3/x402-core` 10,098; `@blockrun/clawrouter` 10,068; `@okxweb3/x402-evm` 9,939; `agentcash` 9,557; `@alchemy/x402` 8,945; `@x402/fastify` 7,370; `@x402/hedera` 7,059; `@x402-avm/core` 5,262; `x402-stellar` 4,738; `x402-solana` 3,959; `@metaplex-foundation/x402` 3,362; `@metamask/x402` 3,229 (a few packages returned no data because the npm API rate-limited the batch, so absence from this list is not evidence of zero).

#### 3.8 The Coinbase Bazaar catalogue
Source: [Bazaar discovery API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0), read 2026-10-11.
- 32,169 resources on 2,212 hosts; 31,665 resources accept Base mainnet; the `quality` field reports 934,886 calls in the last 30 days in total.
- The median resource had 2 calls in 30 days; 89.5% of resources had 5 or fewer calls (6.0% of all calls); only 277 resources had 100 or more and 57 had 1,000 or more. Every resource shows a last call within 30 days, which suggests the Bazaar's own probing contributes a baseline of about one call per resource per month (inference).
- Top hosts by 30-day calls hold 43.8% (AX1), 57.1% (top 3), 66.5% (top 5) and 79.0% (top 10) of all calls. [gold-402](https://github.com/Haustorium12/gold-402), a hand-checked directory, states that most of the catalogue no longer answers a live 402.

#### 3.9 Where sources disagree
| Claim | Source | Compared with | Reading |
|---|---|---|---|
| 30 days to 2026-08-25: 75.41M tx, $24.24M volume, 94.06K buyers, 22K sellers | [x402.org home](https://x402.org) (static page, "last updated 2026-08-25") | x402scan, same 30 days, Base+Solana: 14.37M tx and $1.27M ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)) | x402.org is 5.2x on tx and 19x on USDC; I could not reconcile it |
| Cumulative agent payments passed $50M, more than 85% on Base (2026-05-14) | [Foresight News via Bitget](https://www.bitget.com/news/detail/12560605412078) | x402scan cumulative to 2026-05-14: $50.18M, Base 85.6% of USDC but 76.5% of tx ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)) | Matches on USDC; the 85% share of transactions does not match by count |
| About 167M settled tx, about 85% on Base (snapshot 2026-05-15) | [presenc.ai](https://presenc.ai/research/x402-protocol-adoption-tracker-2026) | x402scan to 2026-05-14: 170.4M tx, Base 76.5% | Total matches, share does not |
| Well over 100M tx on Base through Q1 2026 | [Chainalysis](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/) | x402scan Base to 2026-03-31: 126.7M | Consistent |
| Solana about 70% of monthly volume across chains in mid-August 2026 | [Solana Compass](https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months), citing x402scan | x402scan August 2026: Solana 57% of Base+Solana tx, 29% of USDC | Not reproduced; the article gives no unit |
| Solana passed Base on daily count on 2026-08-25, the first time in six months (Jan 20: Solana 518,400 vs Base 505,000) | [Solana Compass](https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months) | x402scan: Solana ahead on 26 of 28 days from 2026-01-22 to 2026-02-18 and on 19 days from 2026-08-20 to 09-08; on 2026-01-20 x402scan shows Base 307,185 vs Solana 246,333 ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)) | Not reproduced: in x402scan Solana led before August too; different datasets |
| Solana carried 76% of x402 tx (23.2M) in the four weeks to 2026-09-22; Base about 10% in the week ending 2026-08-31 (Artemis data) | [Solana Compass](https://solanacompass.com/news/solana-processes-76-of-all-x402-ai-agent-transactions-232-million-in-four-weeks) and [Coin-Turk](https://en.coin-turk.com/solana-overtakes-base-with-90yuzde-share-in-x402-transaction-volume-and-count/), as cited in the rivals researcher's notes ([their notes](competition_rival_rails_chains.md)) | x402scan 2026-08-25..09-22: Solana 19.8M tx vs Base 1.98M (Solana 90.9% of the two); week of 08-24 to 08-30: Base 5.9% | Direction agrees; Artemis share is lower because it counts other chains and uses its own filter |
| Solana cumulative: over 35M tx and about $10M since launch (2026-09-04) | [Coin-Turk](https://en.coin-turk.com/solana-overtakes-base-with-90yuzde-share-in-x402-transaction-volume-and-count/) via [their notes](competition_rival_rails_chains.md) | x402scan Solana to 2026-08-31: 53.9M tx and $7.99M | x402scan's tx count is 54% higher; its USDC is about 20% lower |
| 191.8M x402 tx and $41.9M settled across 12 chains | [agenteconomy.to](https://agenteconomy.to) (2026-10-11) | x402scan all-time: 233.8M tx and $55.5M (Base+Solana+Polygon) | agenteconomy.to is lower; different sources (Dune authors) |
| $148.2M tracked volume, 586.3M payments, top earner x402.arvos.xyz at $57.6M | [Valoria](https://x402.valoria.net) (example responses) | x402scan: ARVOS $11.5M, all-time total $55.5M | Valoria is 2.7x the whole market; unreliable |
| 30 days: Coinbase $572K, FluxA $322K, Meridian $131K | [x402-list.com](https://x402-list.com) | x402scan 30 days: Coinbase $580K (all chains), FluxA $322K, Meridian $129K | Independent corroboration |
| Real-commerce volume about $28K a day (March 2026) | CoinDesk via [presenc.ai](https://presenc.ai/research/x402-protocol-adoption-tracker-2026) | My Base estimate for Apr-Oct 2026: $8.4K to $15K a day of API-style USDC | Same order of magnitude, lower now |

### Inferences
- Base x402 is not growing in dollars: September USDC was about 30% of April's level and about 2% of the November 2025 peak, while transaction counts depend on one or two high-frequency sellers; the apparent June to August surge was BlockRun, not broad adoption.
- The Solana "flip" in August was a three-week episode of one seller's traffic, not a durable share shift; by mid-September Base had most of the tx again. x402scan also has Solana ahead on 26 of 28 days from 2026-01-22 to 2026-02-18, so the "first time in six months" framing is not supported by that dataset.
- The headline USDC totals overstate commerce: about 36% of window volume is a single closed loop and another 15% to 24% is a few large transfers, leaving roughly 27% to 49% that looks like API purchases.
- Package downloads (core npm packages up 2.3x to 3.6x from April to September, PyPI up 1.7x) are rising while on-chain USDC is flat to down, so downloads probably reflect builders, CI and transitive installs and the v1-to-v2 migration rather than paid usage; v2 accounted for about 84% of framework-wrapper downloads in September (28.1K versus 5.4K a day).
- Coinbase's facilitator is effectively the Base rail by tx (91%) but not by dollars (30%), because the largest dollar flows go through small facilitators (Meridian, FluxA, PayAI) with few counterparties.

### Gaps
- Monthly unique buyers and sellers cannot be built from x402scan; only daily sums and 1/7/14/30-day/all-time windows exist, and these over-count wallets across facilitators.
- The cause of the unreconciled x402.org figures (75.41M tx, $24.24M) is unknown; the page is static WordPress content and cites no source.
- Dune dashboards (authors @thechriscen, @hashed_official, @ax1research, @adrian0x per agenteconomy.to) were not readable, so I could not compare facilitator shares against them for 2026; Artemis and DefiLlama have no x402 series (DefiLlama lists only AI-agent DeFi protocols).
- x402scan only indexes transfers sent by facilitator addresses in its registry (self-hosted facilitators and unregistered signers are invisible; the token-facilitators researcher says FluxA's current signer is missing, so FluxA may be understated: [their notes](dd_token_facilitators.md)). It also counts transfers, not HTTP requests; it cannot tell a paid API call from a payment between related wallets, so the real-commerce range is a classification of recipients, not of intent. The three large unlabeled recipients in the April and September windows (for example 0x57a6b054..., 0x542793a5..., 0xfa02300b...) could not be named.
- I did not find Messari, Galaxy, The Block or Coinbase publications with 2026 monthly x402 figures; the search tool ran out of budget mid-task.
