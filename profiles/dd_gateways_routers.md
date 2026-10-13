# x402 gateways, routers and marketplaces on Base: due diligence profiles (BlockRun, AX1 Console, claw402, AIsa, Vishwa)

> FINAL DRAFT saved 2026-10-11 (all five profiles drafted and cross-checked against primary pages where possible). All research was done by hand (no subagents). Data pulls were made on 2026-10-11 between about 11:30 and 14:30 UTC. Window = 2026-04-11 to 2026-10-11 unless stated. "tx" = USDC transfers indexed by x402scan (not HTTP requests). No token price or chart analysis is included.
> Method notes: x402scan figures come from its public tRPC endpoints (the ones behind the website); GitHub figures from `gh api`; Bazaar figures from the Coinbase discovery API. Wallet addresses are public on-chain facts; I did not try to link any wallet to a person. Claims that come only from a project's own pages are labelled "self-reported".

> **Quick answers (evidence and links are in the profiles).**
> - BlockRun: founder Vicky Fu (ex-Circle); Base Ecosystem Fund investment reported 2026-06-24 (amount undisclosed) after Base Batches 003. ClawRouter is an open-source local router that picks the cheapest capable model and signs the USDC x402 payment. Two wallets, one per chain, make 98.7% of its window transactions; the Base-to-Solana "shift" of 2026-08-19 to 09-10 looks like one payer changing chain; organic flow is about $100 a day.
> - AX1: anonymous brand; the $0.02 verdict route is the entry fee to a weekly rewards contest (its own post, 2026-09-17); 4.7K payers, about $8K in total.
> - claw402: the data gateway of the NOFX/Vergex trading stack; 4.87M tx = $0.002 polling by 25 to 40 wallets a day; the Solana "CLAW402" token appears unrelated.
> - AIsa: alive and funded ($6.5M seed, Alibaba and Tribe, 2026-07-03); its 2025 Base volume looks like a coordinated cohort of about 40 similar wallets (five checked) that stopped on 2025-12-31; it now offers Circle Gateway batched payments.
> - Vishwa: a fixed fleet of about 300 wallets; x402 idle since 2026-09-22; company claims are unverifiable.
> - Where Base volume comes from: these five are 79% of Base tx and 9% of Base USDC in the window; treat tx rank as an automation and incentive index.

---

## 1. BlockRun (including ClawRouter and the @blockrun/llm package)

### One-line
BlockRun, Inc. sells pay-per-call access to LLMs, image/video, search and market data. An agent pays each call in USDC over x402 (Base or Solana), or a person pays by card for an API key. Its open-source ClawRouter picks the cheapest capable model on the user's machine ([blockrun.ai](https://blockrun.ai), [org README](https://github.com/BlockRunAI/.github/blob/main/profile/README.md), accessed 2026-10-11).

### x402 role
Seller/resource server (blockrun.ai, sol.blockrun.ai) plus buyer-side SDK/tooling (ClawRouter proxy, `@blockrun/llm`, `blockrun-llm`, MCP, Franklin agent). Not a facilitator: Coinbase settles its Base payments; Figment and PayAI settle its big Solana flow ([Base][br-sellers-base-30d], [Solana][br-sellers-sol-30d]).

### Chains
Base until August 2026, Solana since. The org README says "prefer Solana at sol.blockrun.ai, followed by Base"; ClawRouter v0.12.246 (2026-08-22) made Solana the default for new installs ([release](https://github.com/BlockRunAI/ClawRouter/releases/tag/v0.12.246)); Franklin also supports Circle Arc ([Franklin](https://github.com/BlockRunAI/Franklin)). Last 30 days to 2026-10-11: Solana 224,924 tx / $1,369; Base 83,186 tx / $1,552.

### Token
None official: not on the site, docs, changelog, feed or GitHub README ([docs](https://blockrun.ai/docs), [feed](https://blockrun.ai/feed.xml)). Unofficial Solana look-alikes with no official link found: "BRUN / BlockRunAI" (`92QPy1K3…upump`, pair created 2026-10-07) and "ROUTER / ClawRouter" (`61stt2WZ…BAGS`, pair created 2026-02-07) ([DexScreener](https://api.dexscreener.com/latest/dex/search?q=blockrun), [second](https://api.dexscreener.com/latest/dex/search?q=clawrouter)). Base contract: none. Utility: not applicable.

### Team
- **Vicky Fu, founder (doxxed).** About page: ex-Circle Head of Data Science, ex-Capital One Director of Data Science, ex-Microsoft Azure ML tech lead (self-reported, [About](https://blockrun.ai/about)); Circle's Arc hub lists her as "Founder @ BlockRun AI" ([Arc](https://community.arc.io/home/videos/replay-usdc-openclaw-hackathon-winner-spotlight-clawrouter-by-blockrunai-2026-03-19)). Base's own announcement of the cohort links her name to X `@bc1beat` ([Base blog](https://blog.base.org/introducing-base-batches-003-2); official, confidence high); the ClawRouter README gives a founder Telegram contact `@bc1max` ([README](https://github.com/BlockRunAI/ClawRouter)).
- **GitHub engineers (pseudonymous)**, from commit logs and `gh api users`: `1bcMax` (1,219 window commits, the most; the login no longer resolves on the GitHub users API; also the ClawHub publisher of ClawRouter); `VickyXAI` (429 commits; bio "Web3 Builder"); `KillerQueen-Z` (84 commits; profile: "Building Franklin & ClawRouter @BlockRunAI", a self-declared team member); `0xCheetah1` (about 20 commits, empty profile). None sets an X handle, and no official source says who operates these accounts.
- Outside contributor: `notorious-d-e-v` (a PayAI engineer, per his own GitHub profile).

### Track record and pivots
- 2025-12-21 org created; 2025-12-26 first Base x402 payment; 2026-01-05 incorporated in Delaware, gateway live on Base ([About](https://blockrun.ai/about), [Base daily][br-base-daily]).
- 2026-02-03 to 08 ClawRouter wins the Agentic Commerce track of Circle's USDC OpenClaw hackathon ([Circle](https://www.circle.com/blog/meet-the-winners-of-our-first-usdc-openclaw-hackathon----and-what-we-learned), 2026-02-11); Solana gateway registered 2026-02-23.
- 2026-03-22 Franklin agent; 04-09 one of 12 Base Batches 003 teams ([AICoin](https://www.aicoin.com/en/news-flash/2831961)), Demo Day 05-19; 05-17 Hermes plugin; 07-11 Polymarket trading; 09-03 card-funded API keys; 10-07 Solana batch settlement.
- One thesis throughout (agent-paid LLM gateway); the add-ons chase agent fads (OpenClaw, Hermes, Polymarket).

### Trend-hopping score
**2 of 5.** Ten months on one product thesis, each hook shipped for real. It is too young to score 1.

### Funding
- Base Ecosystem Fund investment reported 2026-06-24 (Foresight News); amount, round and co-investors undisclosed ([Bitget](https://www.bitget.com/news/detail/12560605475819)). Base's programme page offers selected teams $100K from the fund ([Base Batches](https://www.base.org/batches)); that is the standard offer, not a confirmed BlockRun figure.
- Base Batches 003 cohort (12 teams from 1,175 applications; programme 04-06 to 05-19; the page names no winners). AX1 said on 2026-05-19 it welcomed BlockRun "into the AX1 ecosystem" (terms unknown; [AX1 post](https://x.com/ax1vc/status/2056718708664320038), search snippet). AX1's site calls BlockRun a "Base Batches 003 Winner"; no winner list names it (unverified).
- Circle hackathon: a track win in a $30,000 pool over three tracks; share undisclosed. No equity round found (Dealroom is paywalled).

### Product and traction
- Live: gateway (home page claims 115 models, 100 data/tool APIs, 40-chain RPC; other pages say 88 chat LLMs, 105, 110 or 113), 7 free models, ClawRouter (MIT, 6,622 stars; a local proxy that scores each request on 15 dimensions, picks the cheapest capable model and signs the USDC payment; its "84% cheaper than always using Claude Opus" is self-published), Franklin (555), MCP (19 tools, 391), SDKs (`@blockrun/llm` is the TypeScript SDK, repo blockrun-llm-ts, v3.20.1; `blockrun-llm` on PyPI, v1.17.1). Downloads in the month to 2026-10-10: `@blockrun/clawrouter` 10,457, `@blockrun/llm` 10,920, `@blockrun/franklin` 3,667, `@blockrun/mcp` 3,902; PyPI `blockrun-llm` 1,508 ([pypistats](https://pypistats.org/api/packages/blockrun-llm/recent)). Since 2026-08-07: provider list price plus $0.001 a call, media +5% ([changelog](https://blockrun.ai/changelog)).
- Bazaar: 113 resources, 80,593 calls in 30 days, 84% on chat completions (67,578 calls, 238 payers) ([Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0)).
- x402scan all-time: Base 27.57M tx / $479.9K / 3,254 buyers; Solana 22.54M tx / $292.6K / 435 buyers ([Base][br-sellers-base-all], [Solana][br-sellers-sol-all]). Window: Base 27.04M tx / $450.1K (65% of Base's 41.5M) ([daily][br-base-daily]); Solana 22.52M tx / $291.2K ([daily][br-sol-daily]).
- BlockRun's own claim: "rank 1", 8,241,102 tx and $97,598 in 30 days to 2026-10-02, runner-up 466,221 tx ([numbers.json](https://blockrun.ai/brand/numbers.json), read directly). My sums for 09-02..10-01 are 8.9M tx / $101.9K, so it matches, and it is the Solana burst below.

**Real paying use versus self-generated traffic.** Two wallets, one per chain, make 98.7% of the window's transactions (48.90M of 49.56M) and 97.7% of its USDC ($724K of $741K):
- Base `0x2b4ee338…9037`: 26,696,231 of 27,574,606 Base transfers (96.8%) and $438,280 (91.3%), 2026-05-18 04:58 UTC to 2026-09-11 02:56 UTC ([buyers][br-top-base-buyers], [first][br-first-base], [last][br-last-base]). That one wallet is 64% of all Base x402 tx in the window.
- Solana `BhFRCUXH…ox5U`: 22,206,124 of 22,539,666 transfers (98.5%) and $286,202 (97.8%), 2026-08-12 to 2026-09-12 ([buyers][br-top-sol-buyers], [first][br-first-sol], [last][br-last-sol]).
- Both only buy, never receive, and they look like one operator: the Solana wallet starts as the Base wallet's volume falls, and both stop within a day of each other. Amounts are token-metered and repeat: in 100 Base payments made within 4 seconds on 2026-08-18, one amount ($0.007858) appears 7 times and four others 3 to 5 times, which fits scripted repeated prompts (inference); the average over the run is about 3 payments a second, with bursts of 12 to 25. A third-party check (committed 2026-08-05) found the Base wallet paid 99.4% of BlockRun's $35,256 in a 7-day window and was not funded directly by BlockRun's treasury in a 120-day look-back; it misses indirect funding ([x402-measure](https://github.com/meloliva14/x402-measure/blob/main/circularity.json)). A tracker logged its USDC balance at $6,102 (2026-08-22) and $2,447 (2026-09-08), then flat ([whale-watch](https://github.com/halobartku/agent-forge-site/blob/main/registry/data/whale-watch.jsonl)).
- A secondary report (2026-08-26) says BlockRun "has said most paid calls hit free-tier models", adds in its own words that many look like two-token "heartbeat" probes, and relays PayAI's claim of 5.4M Solana payments in a week (over $60,000). I could not find BlockRun's original statement, so this is a lead only ([OurCryptoTalk](https://ourcryptotalk.com/news/solana-agentic-payments-payai-blockrun)).
- Everyone else: 660,537 tx and $16,769 in six months. The organic run-rate now is about 308K tx and $2.9K per 30 days (about $100 a day) from 367 Base and 211 Solana buyers ([30-day][br-sellers-base-30d]).
- Read: real money from one very heavy payer, not broad agent demand. The owner is unknown (customer, partner, or a probe or load bot); explorers block scripts, so I could not trace funding.
- Batching will shrink counts: Solana batch settlement (live 2026-10-07) and Circle Gateway batching (used by AIsa) settle many calls in one transaction, so x402scan counts should fall without demand falling.

**Why the traffic moved from Base to Solana (about 2026-08-19 to 09-10).**
- BlockRun's Base daily tx fell from 1,216,761 (08-17) to 2,911 (08-24) while its Solana daily tx rose from 245 (08-18) to 470,729 (08-19) and 1.8M (09-01), then collapsed on 09-09 ([Base][br-base-daily], [Solana][br-sol-daily]). Solana Compass (2026-08-25) credited BlockRun's routing for the "flip", quoting one Solana developer ([article](https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months)); its 09-22 follow-up omits BlockRun.
- The Solana flow used Figment and PayAI; the Base flow used Coinbase, which charges $0.001 per onchain transaction after 1,000 free a month ([CDP docs](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator)). On 2026-10-07 BlockRun and PayAI launched Solana batch settlement and BlockRun said it could save over $20,000 a month in fees ([Bitcoin.com](https://news.bitcoin.com/technology/solana-x402-lets-ai-agents-batch-usdc-payments-slashing-fees/)). At $0.001 each, about 20M settlements a month cost about $20K, the size of that saving, and BlockRun's flat $0.001 per-call fee (from 2026-08-07) equals Coinbase's per-transaction fee (both inference).
- Inference, not confirmed: one payer changed chain, probably for cost, and BlockRun's Solana-first defaults (08-22, 09-05) followed. The "Solana passes Base" episode was one buyer's choice, not a market shift. No public BlockRun statement explains it.

### Last six months
- **Commits (04-11 to 10-11), Apr/May/Jun/Jul/Aug/Sep/Oct:** ClawRouter 59/40/38/36/54/99/9 (335); Franklin 319/190/68/64/39/65/50 (795); blockrun-mcp 20/32/65/75/57/50/10 (309); blockrun-llm 16/40/36/33/18/25/8 (176); blockrun-llm-ts 15/22/18/30/36/48/44 (213); total about 1,828 ([ClawRouter](https://github.com/BlockRunAI/ClawRouter/commits/main), [Franklin](https://github.com/BlockRunAI/Franklin/commits/main), [MCP](https://github.com/BlockRunAI/blockrun-mcp/commits/main)). SDK counts include sync commits by `github-actions[bot]`.
- **Releases:** ClawRouter 105 (v0.12.148 on 04-12 to v0.12.282 on 10-05); Franklin 189 (v3.0.0 to v3.49.6 on 10-08); blockrun-mcp 60 (to v0.54.2); blockrun-llm 17 (v1.17.1); blockrun-llm-ts 33 (v3.20.1): about 404.
- **Contributors and last commits:** four core committers plus about a dozen one-off authors and bots; ClawRouter 2026-10-05, MCP and Franklin 2026-10-08. No joins or departures announced; a third-party "TWZRD AutoGate" was merged and removed on 2026-09-07.
- **Shipped:** 05-17 Surf data; 07-08 marketplace renamed Services; 08-04 100+ endpoints published; 08-07 provider-rate pricing; 08-22 Solana default; 09-02 Desktop; 09-03 card billing; 09-08 pricing corrections; 10-05 security fix; 10-07 Solana batch settlement; new frontier models listed within days of release, latest GPT-6.1 Sol on 10-09 ([changelog](https://blockrun.ai/changelog)).

### Pace verdict
Fast. About 1,830 commits and 400 releases across five repos in six months, about 10 commits a day, against 555 commits in the x402 Foundation reference repo and 613 in x402scan over the same window ([x402](https://github.com/x402-foundation/x402), [x402scan](https://github.com/Merit-Systems/x402scan)). A small AI-assisted team is expected to ship weekly; BlockRun ships several releases a day at peak (Franklin 89 in May). Commits are cheap with AI tools; the price corrections show real upkeep.

### Direction
Stated: "the routing and payment layer for AI": router, wallet and card billing, Solana first, batching, Desktop. The record matches. The org README now leads with the API-key path, so x402 receipts alone do not carry the business.

### Competitors
In x402: Daydreams (router seller origin 4,655 tx, last 2026-02-03), AiMo (973,786 tx, last 2026-03-09), Heurist Mesh (dormant since 2026-05-12), Locus, AIsa ([ecosystem notes](./ecosystem_map_and_metrics.md), sections 1.1, 1.4). Outside: OpenRouter raised $113M at a $1.3B valuation in May 2026 and claims about 25 trillion tokens a week ([Dealroom](https://dealroom.co/news/129679-openrouter-raises-113m-series-b-hits-1-3b-valuation/)); LiteLLM has 60,952 stars. Both lead the conventional market by orders of magnitude. BlockRun leads x402 LLM gateways by calls (Bazaar #2), not by organic dollars.

### Green and red flags
- Green: named, relevant founder; extreme shipping cadence; open code; third-party validation (Circle, Base Batches, Base Ecosystem Fund); public changelog; no token; SECURITY.md added 2026-10-05.
- Red: 98.7% of x402 tx from two wallets, and its "rank 1" claim rests on one week of it; organic x402 receipts about $100 a day; model counts differ by page; main committer's account does not resolve; no disclosed funding amount; only the founder is named. Until v0.12.282 (2026-10-05) the wallet-holding local proxy accepted cross-site `Origin` and non-local `Host` requests, read local image paths without a type check, and ran paid channel commands without an authorised sender; fixed ([commit](https://github.com/BlockRunAI/ClawRouter/commit/f63e3425)). Earlier versions deserve caution.

### Verdict
**Serious builder. Momentum: Accelerating (shipping), Steady (organic x402 use).** The strongest product team of the five and the weakest evidence of organic x402 demand. Read its transaction rank as one payer's behaviour; follow it for what ships (Solana batching, card mode, Desktop), not volume. If card billing takes off it becomes a normal LLM gateway that also accepts USDC.

### Tracking card
- Site https://blockrun.ai ; docs https://blockrun.ai/docs ; changelog https://blockrun.ai/changelog ; feed https://blockrun.ai/feed.xml ; status https://blockrun.ai/status ; live feed https://blockrun.ai/live ; accounts https://user.blockrun.ai
- GitHub https://github.com/BlockRunAI (ClawRouter, Franklin, blockrun-mcp, blockrun-llm, blockrun-llm-ts, router-core, model-catalog) ; npm @blockrun/clawrouter, @blockrun/llm, @blockrun/franklin, @blockrun/mcp ; PyPI blockrun-llm
- X https://x.com/BlockRunAI ; Telegram https://t.me/blockrunAI ; Vicky Fu X https://x.com/bc1beat ; founder Telegram @bc1max ; Farcaster, Discord, Dune: none found
- x402scan recipients: Base `0xe9030014f5dae217d0a152f02a043567b16c1abf` ([page](https://www.x402scan.com/recipient/0xe9030014f5dae217d0a152f02a043567b16c1abf)); Solana `AQqnMFBwGZEoti85aTVRy8XYpKrho7GaMDx9ZB3CEeKA`; facilitators: coinbase (Base); coinbase, corbits, figment-facilitator, payAI (Solana). Heavy payers (on-chain addresses): Base `0x2b4ee3387008e5ff1a9996fc8b48d2fd61389037`; Solana `BhFRCUXHVm76PmXkSzus8T4LUGrD2MTW9Au6bocBox5U`. Token: none official.

### Sources
Accessed 2026-10-11. Primary: BlockRun site, About, changelog, feed, numbers.json, GitHub org (links above) and the [Base blog](https://blog.base.org/introducing-base-batches-003-2). Third party links are inline; also the [Circle partner page](https://partners.circle.com/partner/blockrun) and [x402-measure](https://github.com/meloliva14/x402-measure).

[br-base-daily]: https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xe9030014f5dae217d0a152f02a043567b16c1abf%22%5D%7D%7D%7D
[br-sol-daily]: https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22solana%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%22AQqnMFBwGZEoti85aTVRy8XYpKrho7GaMDx9ZB3CEeKA%22%5D%7D%7D%7D
[br-sellers-base-30d]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xe9030014f5dae217d0a152f02a043567b16c1abf%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[br-sellers-sol-30d]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22solana%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%22AQqnMFBwGZEoti85aTVRy8XYpKrho7GaMDx9ZB3CEeKA%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[br-sellers-base-all]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xe9030014f5dae217d0a152f02a043567b16c1abf%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[br-sellers-sol-all]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%22AQqnMFBwGZEoti85aTVRy8XYpKrho7GaMDx9ZB3CEeKA%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[br-top-base-buyers]: https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A60%7D%7D%7D
[br-top-sol-buyers]: https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A12%7D%7D%7D
[br-first-base]: https://www.x402scan.com/api/trpc/public.transfers.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22senders%22%3A%7B%22include%22%3A%5B%220x2b4ee3387008e5ff1a9996fc8b48d2fd61389037%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22block_timestamp%22%2C%22desc%22%3Afalse%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[br-last-base]: https://www.x402scan.com/api/trpc/public.transfers.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22senders%22%3A%7B%22include%22%3A%5B%220x2b4ee3387008e5ff1a9996fc8b48d2fd61389037%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22block_timestamp%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[br-first-sol]: https://www.x402scan.com/api/trpc/public.transfers.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22senders%22%3A%7B%22include%22%3A%5B%22BhFRCUXHVm76PmXkSzus8T4LUGrD2MTW9Au6bocBox5U%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22block_timestamp%22%2C%22desc%22%3Afalse%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A3%7D%7D%7D
[br-last-sol]: https://www.x402scan.com/api/trpc/public.transfers.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22senders%22%3A%7B%22include%22%3A%5B%22BhFRCUXHVm76PmXkSzus8T4LUGrD2MTW9Au6bocBox5U%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22block_timestamp%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A3%7D%7D%7D

---

## 2. AX1 Console (AX1, research arm "ax1research")

### One-line
AX1 is a Base-focused crypto research and angel-syndicate brand (public since at least September 2023) that now runs "AX1 Console", a missions-and-points launchpad where wallets and AI agents earn XP and compete for weekly USDC payouts. Its x402 route sells a $0.02 AI-written "verdict" (a "roast") for any Base token contract ([ax1.vc](https://www.ax1.vc), [console](https://console.ax1.vc/), accessed 2026-10-11).

### x402 role
Seller/resource server with one paid route, `POST https://www.ax1.vc/api/dashboard/q-verdict/resource` (service "AX1 Console", x402 v2, Base USDC, payTo `0x7284D41b…d299C`) ([Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0)). Also discovery/analytics (Dune handle `ax1research`), a planned trust service ("AX1 Assay", human review of agent behaviour, [page](https://www.ax1.vc/agent-eval)) and a pre-launch token experiment.

### Chains
Base only, settled by Coinbase's facilitator. The route declares ERC-8021 builder code `bc_tyhmcm97`; Base describes builder codes as an input for future rewards and leaderboards, though the [x402 docs](https://docs.x402.org/extensions/builder-code) do not mention rewards.

### Token
No token exists yet. ax1.vc/token: "No official token exists yet... Any token currently listed is not ours... No contract address or trading link is official before TGE." Planned `$AX1` is the "access key to ecosystem rewards", with tiers by weekly XP or by locking it for the season ([token page](https://www.ax1.vc/token)); the console names Aerodrome as the venue to watch ([console](https://console.ax1.vc/)). Launch date and method: none announced. Real work: none yet.

### Team
- **Anonymous brand.** No person is named on ax1.vc, the console, the Assay page, the Dune profile or Telegram; the footer says "© 2026 AX1 Research".
- One promotional third-party article (2023-10-05) names four "board members" (two as co-founders of other companies, two by pseudonym) ([Teletype](https://teletype.in/@fastmvm/AX1-mytalktowall)). No AX1 page or independent source confirms them or their current role, so I do not record the names here; see the link.
- Handles: X `@ax1vc` (linked from ax1.vc); Telegram `t.me/ax1vc` (20.5K subscribers; market commentary and token calls, [channel](https://t.me/s/ax1vc)); Dune `ax1research` (no dashboards listed when fetched, though search results cite [BASE Agentic Ecosystem](https://dune.com/ax1research/base-agentic-ecosystem)); Farcaster `ax1vc` (2 followers; unverified). `ax1research` is the Dune handle; I found no X account of that name. No GitHub.

### Track record and pivots
- 2023-05 press releases call AX1 a "web3 venture club" with an "investment DAO", naming no people ([FinancialContent](https://markets.financialcontent.com/stocks/article/marketersmedia-2023-5-6-venture-capital-firm-ax1-to-release-groundbreaking-report-on-crypto-wallets-market)); 2023-09-18 Trust Wallet research release ([Bitcoin.com](https://news.bitcoin.com/ax1-unveils-comprehensive-research-on-the-web3-landscape/)); 2023-10-05 "syndicate" that sponsored Messari Mainnet 2023 and ran $TWT airdrops (self-reported); 2025-08-13 "AX1 3.0, the next era of Web3 communities" (X post via search).
- 2026: research notes March to July; 04-16 Agentic Dune dashboard V2; 05-19 welcomes BlockRun into its ecosystem (also Upshot, OWB Studio, Glider, Lucent, Freeport Markets); 08-20 Console beta; 09-07 first x402 payment; 09-17 leaderboard and payouts.

### Trend-hopping score
**4 of 5.** Syndicate, Trust Wallet research, Web3 community platform, Base research firm, agent quest console, pre-TGE token and agent assurance in about three years; the x402 route serves the rewards contest.

### Funding
No evidence of outside funding. AX1 presents itself as an investor ("capital access", angel network), not an investee ([ax1.vc](https://www.ax1.vc)).

### Product and traction
- x402scan: first payment 2026-09-07; all-time 412,049 tx / $8,241 / 4,804 buyers; 30 days 407,182 tx / $8,144 / 4,695 buyers; 7 days 86,514 tx / 452 buyers; every payment exactly $0.02 ([daily][ax-daily], [30-day][ax-sellers-30d], [all-time][ax-sellers-all]).
- Bazaar: 408,579 calls and 4,667 unique payers in 30 days (2026-10-11 12:27 UTC), about 44% of all Bazaar calls. x402-list: score 91/100, uptime 99.3%, top buyer 4% of volume ([x402-list](https://x402-list.com/services/ax1-console)).
- Peaks: 43,106 tx on 2026-09-27 and 41,181 on 10-04. Every weekly peak falls on a Sunday (09-13, 09-20, 09-27, 10-04), the day before the Monday 00:00 UTC contest cutoff described below.

**Why one $0.02 endpoint tops the Bazaar: it is the entry fee to a weekly rewards contest.** AX1's Telegram post #3166 (2026-09-17, in Russian; I read the original embed, [post](https://t.me/ax1vc/3166?embed=1&mode=tme)) explains the "Roast a token (Q-Verdict)" quest. A player signs in with Privy, pastes any Base token address and presses Check. The first 5 checks are free through a $0.10 promo credit claimed in the quest. Each verdict card is 1 contest point, but only for the first check of each new token in the week. A minimum of 10 points a week is needed to be in the payout, so the other 5 points cost 5 checks at $0.02 paid from USDC the player sends to an "agent funds" address on Base. A CONTEST tab shows rank, points, the pool and a timer; the week closes Monday 00:00 UTC; the USDC payout reaches the agent wallet within 48 hours; the pool size is not stated in the post. AX1 also says the x402 product reached the top spot for active buyers within a week of launch on a 2-3% marketing push. A search snippet of AX1's X feed reports a weekly USDC pool for the 300 most active agents (unverified). The console pitches "a custom AI agent to complete quests for you" and ties XP tiers to $AX1. So the payments are real money from players, but they are contest entry fees, which explains the Sunday peaks before the cutoff. In a sample of 2,100 transfers (09-12 to 10-10), 202 payers appear; the top 10 made 31.5% and the top 20 45% ([sample][ax-transfers]). My estimate of independent end-user demand for token roasts: under 10% (judgement; not measurable).

### Last six months
No public repos, so no commit, release or contributor counts. Dated outputs: 04-16 Dune V2; 05-19 BlockRun welcome; research posts 06-17 to 07-08; 08-20 Console beta; 09-07 x402 route; 09-17 leaderboard; an undated token page with the "no official token" warning. Joins/departures: unknown.

### Pace verdict
Not measurable by code. Launch speed is high (beta 08-20, x402 live 18 days later, top Bazaar spot within a week) but it is a contest campaign, not engineering depth.

### Direction
Stated: "research firm, then ecosystem, then agentic provider", with $AX1 as access key and Assay for agent evaluation. Shipped: Console and the x402 route; Assay and token not live.

### Competitors
Quest and XP hubs that pay for on-chain activity. Next in the Bazaar by calls: BlockRun (80.6K), Chainlink for Agents (45.6K from 3 payers), OneShot Agent (45.3K), X Pay (42.4K) ([ecosystem notes](./ecosystem_map_and_metrics.md), section 3.4).

### Green and red flags
- Green: explains the mechanism openly; route passes 14/14 x402 checks; labels output "entertainment, not trading advice".
- Red: no named team; closed source; contest-driven volume; AX1 both measures Base agent activity (Dune) and runs the top endpoint; a pre-TGE token; a Telegram channel that mixes research with token price calls.

### Verdict
**Speculative. Momentum: Steady.** The 409K-call figure is a rewards contest, not demand for token verdicts. Worth watching as a case study of incentivised x402 volume and for the $AX1 launch; expect the call count to follow contest and reward changes.

### Tracking card
- Site https://www.ax1.vc ; console https://console.ax1.vc ; token https://www.ax1.vc/token ; Assay https://www.ax1.vc/agent-eval ; docs, blog, RSS, changelog: none
- X https://x.com/ax1vc ; Telegram https://t.me/ax1vc ; Dune https://dune.com/ax1research ; Farcaster @ax1vc (unverified) ; GitHub, Discord: none
- x402scan recipient `0x7284d41b5b852f2bd4c99bdf95043d84452d299c` ([page](https://www.x402scan.com/recipient/0x7284d41b5b852f2bd4c99bdf95043d84452d299c)); facilitator coinbase; builder code `bc_tyhmcm97`; resource `https://www.ax1.vc/api/dashboard/q-verdict/resource` ; [x402-list](https://x402-list.com/services/ax1-console). Token: none yet.

### Sources
Accessed 2026-10-11: links inline above; also the [OpenSea listing](https://opensea.io/tools/x402-bazaar/base/1021066470704690836) and [Bazaar API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0).

[ax-daily]: https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x7284d41b5b852f2bd4c99bdf95043d84452d299c%22%5D%7D%7D%7D
[ax-sellers-30d]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x7284d41b5b852f2bd4c99bdf95043d84452d299c%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[ax-sellers-all]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x7284d41b5b852f2bd4c99bdf95043d84452d299c%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[ax-transfers]: https://www.x402scan.com/api/trpc/public.transfers.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x7284d41b5b852f2bd4c99bdf95043d84452d299c%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22block_timestamp%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D

---

## 3. claw402 (claw402.ai)

### One-line
claw402 is a pay-per-call gateway for crypto market-data, trading-signal and AI-model APIs: $0.0001 to $0.05 in USDC on Base per call (most routes $0.002 or $0.01), no API key. It is the data and payment back end of the open-source NOFX AI trading terminal and says it is "Backed by vergex.trade" ([claw402.ai](https://claw402.ai), [llms.txt](https://claw402.ai/llms.txt), accessed 2026-10-11).

### x402 role
Seller/resource server (a gateway reselling CoinAnk, RootData, NOFXOS, Vergex, OpenAI, Anthropic, DeepSeek, Z.AI) plus SDK/tooling (claw402-js, -python, -go; the npm and PyPI packages that `llms.txt` tells users to install return 404). Not a facilitator; Coinbase settles.

### Chains
Base only (USDC, x402 v2, EIP-3009), payTo `0xa9dd7cc9…bc2315`. Not in the Coinbase Bazaar (full index scanned 2026-10-11: no claw402 resource).

### Token
Two different things share the name.
1. The gateway: no token on its site, `llms.txt`, README or the NOFX README.
2. A Solana token "CLAW402", `FJPoRjKUkE4BP3cULAKiqztBjTxRG3qcRTV9SFf7pump`, launched on pump.fun, PumpSwap pool created 2026-03-02 17:09 UTC; CoinGecko homepage `claw402.xyz`, X `@claw402dotxyz`, description "MCP-native integration layer for AI agents on x402" ([CoinGecko](https://www.coingecko.com/en/coins/claw402), [GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/solana/tokens/FJPoRjKUkE4BP3cULAKiqztBjTxRG3qcRTV9SFf7pump)).
The gateway's own handle is `@Claw402ai` and its domain is .ai ([claw402-open](https://github.com/NoFxAiOS/claw402-open)). I found no link between the two, and the token appeared a day after the gateway's first payment, so it is probably an unofficial namesake (unconfirmed). Utility in the gateway: none found. Base contract: none.

### Team
- **"Tinkle" (pseudonym), founder of NOFX**: the NoFxAiOS org profile lists "Founder @Web3Tinkle" ([profile](https://github.com/NoFxAiOS/.github/blob/main/profile/README.md)). GitHub `tinkle-community` (created 2025-10-28; blog `x.com/Web3Tinkle`) is the only committer to claw402-open and the SDK repos; the org field lists X `aiTinkle`. Confidence the handles belong to the project lead: high; real name unknown.
- NOFX engineers (not tied to the closed gateway code): `shinchan-zhai`, `lky-spec` (23 window commits each), `Dean-afei`/`deanokk`, and earlier `icyouo`, `the-dev-z` (X `the_dev_z`, bio "Building NoFX"), `0xEmberZz` (X `0xEmberZz`), `SkywalkerJi` (X `Skywalker_Ji`). All pseudonymous.

### Track record and pivots
- 2025-10-28 NOFX open-sourced (AGPL-3.0); 2026-01-30 rebrand "AI Trading OS". An older README carried a "Backed by Amber.ac" badge (seen via a search summary; unverified).
- 2026-03-01 first claw402 payment; 03-23 NOFX "removes BlockRun provider, retains Claw402 as sole x402 payment provider" ([commit](https://github.com/NoFxAiOS/nofx/commit/966995fb88)); 05-25 README adds "Backed by vergex.trade"; 05-29 WorldClaw and VergeX AI announce a cooperation ([ChainCatcher](https://www.chaincatcher.com/en/article/2267975)).

### Trend-hopping score
**3 of 5.** One thread (AI trading agents paying for data and models) with several reframings (Trading OS, x402, OpenClaw skill, Vergex, WorldClaw), each with real code.

### Funding
No disclosed rounds. "Backed by vergex.trade" names a sibling brand, not an investor. NOFX takes GitHub Sponsors and exchange referral income ([NOFX](https://github.com/NoFxAiOS/nofx)).

### Product and traction
- x402scan, Base: first payment 2026-03-01; all-time 5,207,886 tx / $10,675 / 763 buyers; window 4,869,938 tx / $9,502; 30 days 423,874 tx / $939 / 148 buyers; 7 days 88,258 tx / 64 buyers ([daily][c4-daily], [all-time][c4-sellers-all], [30-day][c4-sellers-30d]). Monthly tx: Apr 1.11M, May 1.06M, Jun 0.58M, Jul 0.76M, Aug 1.02M, Sep 0.50M.
- Catalog on 2026-10-11: 141 routes, 8 providers (CoinAnk 79, RootData 19, NOFXOS 18, Vergex 11, OpenAI 8, DeepSeek 3, Anthropic 2, Z.AI 1) ([catalog](https://claw402.ai/api/v1/catalog)), down from "247+ endpoints, 16 providers" in the March README. NOFX has 13,033 stars and 3,053 forks.
- **Why 4.87M tx for $9.5K:** 98% of 1,400 sampled payments are exactly $0.002, the price of the Vergex, NOFXOS and RootData routes (the rest are $0.01 CoinAnk calls). About 25 to 40 wallets pay each day, roughly 1,000 calls per wallet per day: a polling loop. The NOFX README names claw402 as its x402 option and the "Claw402.ai · Vergex data stack" as its decision source ([README](https://github.com/NoFxAiOS/nofx)).
- **Real versus self-generated:** it looks like genuine automated use by a few dozen NOFX/Vergex trading agents: stable wallet set, fixed prices, a product that depends on it. In the sample, 45 payers, top 10 = 58.6% of payments, top 1 = 12.2%; x402-list counts 147 buyers in 30 days, with the top buyer at 7% of volume and the top 3 at 20% ([x402-list](https://x402-list.com/services/claw402)). Another researcher found 96 of the 100 largest payments came from one wallet ([sibling notes](./dd_x402_apps_and_trust.md), section 11). Whether the wallets are independent users or team-run traders is unknown (no funding-link test). In dollars it is tiny, about $1.4K a month.

### Last six months
- Dated: 05-25 Vergex backing line; 05-29 WorldClaw cooperation; 08-15 "migrate to direction change radar APIs" and "simplify Claw402 direction trading"; 08-20 "fail closed across trading and payment workflows"; 09-05 GPT-6 Astra support; 10-04 Vergex holder win-rate matrix; catalog regenerated 2026-10-11; site last modified 2026-10-04.
- NOFX commits by month (from 04-11): Apr 46, May 32, Jun 30, Jul 47, Aug 6, Sep 1, Oct 2 (164); no GitHub releases; `tinkle-community` made 105; last commit 2026-10-04 ([commits](https://github.com/NoFxAiOS/nofx/commits/dev)). The claw402 repos have not been pushed since 2026-03-09. Other contributors went quiet after July.

### Pace verdict
Slowing. Public work fell from about 40 commits a month to 1 to 6 after July and the open gateway repos are untouched since March; the closed gateway still updates its catalog. Against a small AI-assisted team's 2026 norm (weekly commits) NOFX is now slow.

### Direction
Stated: universal x402 gateway and provider marketplace ("Start getting paid" onboarding) plus the Vergex trading layer. Shipped: fewer providers and endpoints than in March.

### Competitors
Merit's StableEnrich (405K Base tx / $12K in the window), AgentUtility (69K / $1.7K), OneSource (98K / $408) and BlockRun's data endpoints ([ecosystem notes](./ecosystem_map_and_metrics.md), section 1.4). claw402 has the most tx after BlockRun and roughly equals StableEnrich in dollars; all are small.

### Green and red flags
- Green: real, steady use by a live open-source product; consistent pricing; every call maps to a documented dependency.
- Red: tiny dollars; a namesake Solana memecoin; docs name packages that do not exist; open repos stale since March; provider list halved; commit pace collapsed; one pseudonymous lead.

### Verdict
**Credible but small. Momentum: Slowing.** Alive? Yes, serving calls and updating its catalog on 2026-10-11. A real service for one customer family (NOFX/Vergex traders) with many cheap calls. Its transaction count measures polling frequency, not market demand. Do not follow daily; check it when NOFX or Vergex announce something.

### Tracking card
- Site https://claw402.ai ; catalog https://claw402.ai/api/v1/catalog ; llms.txt https://claw402.ai/llms.txt ; GitHub https://github.com/NoFxAiOS (nofx, claw402-open, claw402-js, claw402-python, claw402-go)
- X https://x.com/Claw402ai ; Vergex https://x.com/vergex_ai ; founder https://x.com/Web3Tinkle ; Telegram https://t.me/nofx_dev_community ; Farcaster, Dune: none found
- x402scan recipient `0xa9dd7cc9cbf0e05551332209289f04be36bc2315` ([page](https://www.x402scan.com/recipient/0xa9dd7cc9cbf0e05551332209289f04be36bc2315)); facilitator coinbase ; namesake token (Solana) `FJPoRjKUkE4BP3cULAKiqztBjTxRG3qcRTV9SFf7pump`.

### Sources
Accessed 2026-10-11: claw402.ai pages above, [claw402-open](https://github.com/NoFxAiOS/claw402-open), [NOFX](https://github.com/NoFxAiOS/nofx), [CoinGecko](https://www.coingecko.com/en/coins/claw402), [GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/solana/tokens/FJPoRjKUkE4BP3cULAKiqztBjTxRG3qcRTV9SFf7pump), [ChainCatcher 2026-05-29](https://www.chaincatcher.com/en/article/2267975).

[c4-daily]: https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xa9dd7cc9cbf0e05551332209289f04be36bc2315%22%5D%7D%7D%7D
[c4-sellers-all]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xa9dd7cc9cbf0e05551332209289f04be36bc2315%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D
[c4-sellers-30d]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xa9dd7cc9cbf0e05551332209289f04be36bc2315%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D

---

## 4. AIsa (aisa.one)

### One-line
AIsa sells one API key, or per-call x402/USDC payment, that reaches 5,000+ APIs, 40+ skills and 110+ models, with agent spending controls: a resource gateway plus payment layer for AI agents, based in San Francisco ([aisa.one](https://aisa.one), [funding post](https://aisa.one/news/aisa-raises-6-5m-ai-agent-resource-network), accessed 2026-10-11).

### x402 role
Seller/resource server (routes "AI Marketplace-402" and "AgentPayWall-402", registered at x402scan under `pay.lnpay.ai`, `agent.paywall402.com`, `openapi.aisa.one`) plus SDK/tooling (skills, CLI, Dify plugins). Its current x402 challenge asks for Circle Gateway batched payments, which x402scan's per-transfer view probably cannot see (inference, below).

### Chains
All of the Base story is Oct-Dec 2025. A live unpaid request to `api.aisa.one` on 2026-10-11 returned a 402 offering the "GatewayWalletBatched" scheme on 12 networks including Base and Arc, payTo `0xBd7b9f3e…BdeE3`, $0.10 for a Twitter lookup ([response header, decoded](https://api.aisa.one/apis/v2/twitter/user/info?userName=jack)). Base is not primary: 121 Base tx in the window.

### Token
None found on the site, the funding post, GitHub or the 2025 pre-seed post.

### Team
- **Jordan Liu, founder and CEO (doxxed)**, named in AIsa's funding post and in Blockworks' 2026-04-09 episode ([Blockworks](https://blockworks.com/podcast/thebreakdown/1cc078a4-3353-11f1-81fb-6308695f4afb)). Earlier co-founder of UXUY, a Telegram multi-chain wallet (press releases name "Jordan L, Co-founder, UXUY"; $3M seed 2023, Binance Labs investment 2024, $7M Pre-A 2024) ([2023](https://www.globenewswire.com/news-release/2023/04/11/2644626/0/en/UXUY-raised-3-million-to-build-the-next-gen-MPC-based-decentralized-trading-platform.html), [2024](https://globenewswire.com/news-release/2024/03/08/2842969/0/en/UXUY-Secures-Strategic-Investment-from-Binance-Labs-to-Propel-Bitcoin-Lightning-Network-Ecosystem.html)). A LinkedIn profile `jordanaisa` shows in search with the AIsa title (not opened; unverified). No personal X handle found.
- **GitHub engineers** (org `AIsa-team`, created 2025-11-20; read 2026-10-11): `karensheng` (Karen Sheng, bio "Product in web3 & AI"; top contributor to agent-skills, docs and the x402 skill), `JONY-AISA` (171 CLI commits), `eddiearc`, `fatflowers` (the one public org member), `liuhaonan00` (bio: "Founding Engineer from @AIsa-team"), `chaimengphp`, `houzhongjian`, `lijing-22`, `zhenlonghe`. `renning22` (X `totheagi`) and `lhymmEU` (X `MagicS86643`) look like outside contributors. Accounts created in the window that now commit: `SELAT-DEV` (2026-06-03), `aisa-barry` (07-02), `kennnnk-aisa` (07-15). Pseudonymous.

### Track record and pivots
- 2023-24 UXUY wallet (above). 2025-01-14 "AIsa" launched as a Lightning-plus-stablecoin payment network, "backed by over $10m ... like Binance Labs"; that conflicts with AIsa's own 2026 "$6.5M total" and matches UXUY's totals ([FinTech Global](https://fintech.global/2025/01/14/aisa-launches-revolutionary-payment-network-for-the-ai-economy/)).
- 2025-10-27 pre-seed and x402 "AI Marketplace-402" ([ChainCatcher](https://www.chaincatcher.com/en/article/2215658)); 11-10 "1M x402 transactions", 11-28 "10.5M" ([ChainCatcher](https://www.chaincatcher.com/en/article/2218696)).
- 2026: OpenClaw skills (Jan-Mar), Circle nanopayments, Arc hackathon, Tempo MPP skill (Apr), Hermes agent CLI (Jul), Dify plugins (Aug), spending controls (Sep) ([repos](https://github.com/AIsa-team), [blog](https://aisa.one/blog)).

### Trend-hopping score
**3 of 5.** Agent payments is the constant thesis; the rails and hooks change every quarter (Lightning, x402, Circle Gateway/Arc, MPP, OpenClaw, Hermes, Dify), each with real code.

### Funding
- Seed announced 2026-07-03: US$6.5M total funding to date including the new seed, co-led by Alibaba and Tribe Capital, with Draper Associates, Sumitomo Corporation, Saison Capital and others; Francis Zhan (Tribe) is quoted in AIsa's post and Qin Jin (Investment Director, Alibaba Group) in the press coverage ([post](https://aisa.one/news/aisa-raises-6-5m-ai-agent-resource-network), [AI Insider](https://theaiinsider.tech/2026/07/17/aisa-secures-6-5m-co-led-by-alibaba-and-tribe-capital-to-build-the-transaction-network-for-ai-agents/)).
- Pre-seed 2025-10-27, amount not stated: Draper Associates, Fenbushi Capital US, BoostVC and six other funds and angels.

### Product and traction
- x402scan Base: all-time 31,551,163 tx / $415,841 / 340 buyers, 2025-07-19 to 2026-08-07. Monthly tx: Oct 2025 108K, Nov 12.25M ($180K), Dec 19.19M ($231K), then 70, 1, 22, 30, 60, 13, 20, 1 for Jan-Aug 2026. **Window total: 121 tx and about $2** ([daily][ai-daily], [all-time][ai-sellers-all]).
- Self-reported: 50,000+ registered agents, users up 150x and calls 200x (Feb to Jun 2026), "250,000+ agents" and "100,000,000+ transactions" on the home page, "top seller and top server" on x402 leaderboards. None is visible on Base after 2025.
- **Real versus self-generated:** the 2025 Base volume looks coordinated. Forty wallets share one profile (Coinbase facilitator only, 2 to 6 sellers, 200K to 510K tx each, last payment 2026-01-01) and hold 15.3M tx and $221K across their sellers; five of them were checked and all paid AIsa's recipient until the same seven minutes on 2025-12-31 (16:30 to 16:37 UTC) ([top Base buyers][br-top-base-buyers]; per-wallet checks via transfers.list). So about half of AIsa's 31.55M tx plausibly came from this cohort (inference). Early samples show 50+ distinct payers inside 30 to 90 seconds, and only 340 wallets ever paid. I read it as a scripted fleet or campaign (judgement). Real paid use on Base in the window: nil.
- Caveat: a Gateway-batched flow probably would not show on x402scan (inference), so "idle since 2026-08-07" proves little about 2026 usage; the company's own numbers cannot be checked on-chain.
- Real product elsewhere: a 104-endpoint x402/Circle Gateway skill (Twitter, finance, search, scholar, Perplexity, YouTube, CoinGecko; $0.00044 to $0.12) and about 50 blog posts ([nanopayment-x402](https://github.com/AIsa-team/nanopayment-x402)).

### Last six months
- `AIsa-team` commits by month, Apr/May/Jun/Jul/Aug/Sep/Oct (from 04-01): docs 80/27/14/79/133/113/138 (includes bot commits); cli 12/0/0/4/99/156/0, with v0.2.3 and v0.2.4 on 08-07 and v0.3.0 on 08-19; agent-skills 72/38/0/15/0/12/0; nanopayment-x402 74 in April; agent-index 106/30/17 (Jul-Sep). About 14 active handles; last commit 2026-10-11 ([org](https://github.com/AIsa-team)).
- Dated: 04-20 CoinGecko endpoints (83 to 104); 04-30 x402 skill v0.2.0 (11 chains); 07-03 seed; 08-19 CLI v0.3.0; 08-27 authorised Similarweb platform; 09-10 spending controls ([blog](https://aisa.one/blog)).

### Pace verdict
Fast on the company's own product (hundreds of commits a month, a CLI release train, weekly posts), silent on Base x402; well above a small AI-assisted team's "weekly commits, monthly releases" bar.

### Direction
Stated: a transaction network and resource gateway with enterprise controls (budgets, approvals, audit trails), more providers, stablecoin settlement ([post](https://aisa.one/news/aisa-raises-6-5m-ai-agent-resource-network)). Shipped: API-key gateway, skills, CLI, MCP, Dify; x402 is one option beside USDC, Nanopayments and MPP.

### Competitors
BlockRun (also moved to card keys), Locus (3,960 paid APIs behind one balance, YC F25; [sibling notes](./dd_x402_apps_and_trust.md), section 11), Orthogonal (157 Bazaar resources) and Merit's StableEnrich ([ecosystem notes](./ecosystem_map_and_metrics.md), section 1.4). Outside x402, OpenRouter ($1.3B valuation, May 2026) is far larger. AIsa's $6.5M seed is the largest funding found in this group.

### Green and red flags
- Green: named founder with a prior funded company; $6.5M seed from Alibaba and Tribe; sustained engineering; real partners.
- Red: 31.5M tx from a coordinated fleet that stopped on one date, and "top seller" claims that rest on it; unverifiable home-page user numbers; the Jan-2025 "over $10m" funding claim conflicts with AIsa's own $6.5M total.

### Verdict
**Credible but small as a company; its Base x402 channel is likely abandoned. Momentum: Steady (company), Dead (visible Base x402).** Alive? Yes: commits on 2026-10-11, a CLI release train and a July seed round. A funded gateway business that used x402 transaction counts as marketing in late 2025 and has moved to API keys and batched settlement. Follow it for funding and product news, not x402 volume.

### Tracking card
- Site https://aisa.one ; docs https://aisa.one/docs ; blog https://aisa.one/blog ; console https://console.aisa.one ; status https://status.aisa.one ; changelog: none (404)
- GitHub https://github.com/AIsa-team and https://github.com/AISA-skills ; X https://x.com/AIsaOneHQ ; Discord https://discord.gg/7rDnYnXra8 ; LinkedIn company `aipayhq` ; founder LinkedIn `jordanaisa` (unverified) ; Farcaster, Telegram, Dune: none found
- x402scan recipient `0x66fa4d79ca84016b42352be33c908dd812952ec8` ([page](https://www.x402scan.com/recipient/0x66fa4d79ca84016b42352be33c908dd812952ec8)); current batched payTo `0xBd7b9f3e0CD3E1f6e698D0eeBb99F96E093BdeE3`; facilitator coinbase (2025); token: none. Fleet wallets checked paying AIsa until 2025-12-31 16:30 to 16:37 UTC: `0xcbbe92abb8110ecf3078f94d4b5e03667660142c`, `0xa29f27eddf096d31822528dbcb0575b3b06210ba`, `0x47fe1c4272e7bb0c538dc9f0eea41404eef39e6f`, `0xd6e86ee864942d715042cec15a4146ee8f0f1f30`, `0x6720d282676f8bcf74763bd92492eef4b5214a88`.

### Sources
Accessed 2026-10-11: links inline above; also [aisa.one](https://aisa.one) and the [AIsa-team](https://github.com/AIsa-team) org.

[ai-daily]: https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x66fa4d79ca84016b42352be33c908dd812952ec8%22%5D%7D%7D%7D
[ai-sellers-all]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x66fa4d79ca84016b42352be33c908dd812952ec8%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D

---

## 5. Vishwa (VishwaLab, api.vishwalab.com)

### One-line
Vishwa (now "VishwaLab") calls itself financial infrastructure for autonomous agents: "Veta", a pre-execution policy check that tests an agent's payment against a mandate before capital moves, plus PredX (prediction markets), OpenNEXT (a GPU price index) and a CLI. Its x402 API resells prediction-market data and order endpoints at $0.01 a call ([vishwalab.com](https://www.vishwalab.com/), [OpenAPI](https://api.vishwalab.com/openapi.json), accessed 2026-10-11).

### x402 role
Seller/resource server: a 16-path "Vishwa x402 API" (events, markets, orderbook, trades, orders, positions); `POST /v1/prediction/orders` is priced at $9.90, everything else $0.01. Also a trust/verification pitch (Veta; the ERC-8150 draft). Facilitator: PayAI on both chains.

### Chains
Base first (2026-02-17 to 2026-06-14), then Solana (2026-06-03 to 2026-09-22). Base shows 10 tx in the last 30 days (last 2026-09-15); Solana's last payment was 2026-09-22 ([Base][vb-daily], [Solana][vs-daily]). The endpoints use Solana order and position keys, so Solana is the natural home.

### Token
None. DefiLlama lists "Vishwa" with no symbol, category "Anchor BTC" on Sui and Bitcoin, listed 2025-09-22, with a $55.4M Bitcoin balance counted as TVL through an adapter that reads `vault.vishwalab.com` (self-reported) ([DefiLlama](https://api.llama.fi/protocol/vishwa)). Utility: not applicable.

### Team
- **SJ Liang (Nathan) and Nova Wang, "Co-Founders, Vishwa Lab"**, as signed on the company's own paper "Agent-Native Banking" (2026-03-07, read from the RSS feed) ([feed](https://medium.com/feed/vishwa-research)). Posts appear under the author name "David L". The company's ERC-8150 draft (a Notion page I could not open; a search result lists two authors, one with a first name matching "Nathan") is at [vishwa-network.notion.site](https://vishwa-network.notion.site/ERC-8150-Zero-Knowledge-Agent-Payment-Verification-3169119fc7078030935ed850ad8aa316). No independent source confirms the founders; no personal X, GitHub or LinkedIn handles found.
- npm maintainers of `@vishwalab/cli`: `harry-vishwalab` and `vincentcaptain` (usernames only). GitHub org `vishwanetwork` (created 2024-10-30; 13 repos, mostly forks; original: website-homepage, vete-mcp, pred_mkt_clawbot, VAEB, Auno, continental-network). Project X `@Vishwa_lab` (older `@Vishwa_xyz`). Pseudonymous.

### Track record and pivots
- 2024-10-30 GitHub org created. 2025 "Vishwa Network": zero-knowledge proofs and a "world model of finance" across 160 chains, idle-asset and credit themes, a Kite AI collaboration (2025 Annual Report, [Medium feed](https://medium.com/feed/vishwanetwork)); 2025-09-22 DefiLlama listing.
- 2026-02-17 first Base x402 payment; 03 "agent-native banking" papers; 05 renamed VishwaLab with Veta, PredX, Naro; 05-13 CLI beta; 06-03 Solana x402 starts; 06-14 Base fleet stops; 08-07 last Medium recap; 09-22 last x402 payment ([recaps](https://medium.com/feed/vishwanetwork)).

### Trend-hopping score
**4 of 5.** ZK and DeFi (2025), agentic credit, agent-native banking, prediction markets, GPU compute and an ERC draft within a year; the x402 API followed whichever story was current.

### Funding
No outside funding found. Claimed affiliations: Anthropic Cyber Verification Program, Plug and Play (Fall 2026 cohort), Circle Alliance Program; "trusted by" logos Pharos, Fidelity Labs, Ondo, Solana (all self-reported, [site](https://www.vishwalab.com/)).

### Product and traction
- x402scan Base: 992,037 tx / $43,280 / 611 buyers all-time; window 480,587 tx / $41,610 (full-month tx: Apr 157K, May 145K, Jun 230K at 15 cents average, Jul 1, Sep 10). Solana: 727,523 tx / $752 / 405 buyers (Jun 233K, Jul 167K, Aug 111K, Sep 217K) ([Base all-time][vb-sellers-all]).
- **Real versus self-generated:** a fleet. About 295 to 305 distinct wallets paid every day from March to 2026-06-14, nearly always exactly $0.001 or $0.01, with 78 to 90 distinct payers in any 100 consecutive payments (samples at 12 dates). That is a fixed set of about 300 wallets on a timer; Solana repeats it (200 to 390 a day). A few $9.90 order payments (3 in 100 on 2026-06-03) carry most of the dollars, up to about $3.6K a day. I found no sign of independent buyers (judgement).
- Self-reported claims that do not agree: "~$170M capital under enforcement" in the June and July recaps (the company says this is not AUM or revenue) against "$9M+ autonomous execution live, $60M+ capital under control" on the [Veta page](https://vetagate.com/). The recaps also claim "#1 on x402scan across marketplace and server leaderboards (June 2026)" and "#2 by usage (July 2026)"; by transactions Vishwa was fifth among Base sellers in the window (BlockRun had 56 times more), so the rank must rest on another sort such as buyers (not reproducible).
- `@vishwalab/cli`: 25 beta versions (to beta.32) from 2026-05-13 to 07-03, 270 downloads in the last month, "latest" still `0.0.1-beta.0` ([npm](https://registry.npmjs.org/@vishwalab%2fcli)).

### Last six months
- Medium monthly recaps: 04-03 (March), 05-08 (April), 06-23 (May), 07-07 (June), 08-07 (July); none since. Dated claims: 05 rename to VishwaLab; 05-13 CLI beta; 06 agents trading prediction markets via Jupiter under Vishwa controls; 07 talks with Kite AI's founders and Fidelity Labs.
- GitHub: org last pushed 2026-10-08 (website-homepage, created 09-28); no product repo to count. Releases: npm betas only. Joins/departures: none announced.

### Pace verdict
Content was monthly until 2026-08-07; npm betas stopped 2026-07-03; x402 traffic stopped 2026-09-22; public code is thin. Slow and slowing next to BlockRun or AIsa.

### Direction
Stated: banking infrastructure for autonomous capital and an agent compute market (OpenNEXT; site rebuilt 2026-09-28). Shipped: marketing site, index pages, CLI betas, an x402 API now idle.

### Competitors
For prediction-market data, BlockRun sells Polymarket and Predexon endpoints over x402 (its `/pm/polymarket/markets` route has 127 Bazaar calls from 88 payers in 30 days, [Bazaar](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0)). For spend controls: AIsa (2026-09-10), Locus, ampersend, Crossmint and Vaaya ([sibling notes](./dd_x402_apps_and_trust.md), section 11). None is clearly ahead; Vishwa's x402 volume has stopped.

### Green and red flags
- Green: named co-founders on its own papers; monthly recaps through July; a real OpenAPI spec; institutional partner logos.
- Red: a constant ~300-wallet fleet at a fixed micro-price; x402 idle since 2026-09-22; unverifiable and inconsistent "capital" claims and a BTC-balance "TVL"; no funding found; frequent reinvention; sparse public code.

### Verdict
**Speculative. Momentum: Slowing.** Alive? Partly: the site was rebuilt on 2026-09-28, but Medium has been silent since 2026-08-07, npm betas stopped 2026-07-03 and the x402 API has been idle since 2026-09-22. The x402 numbers were a bot fleet that put it near the top of x402scan lists for a few months. Whether Veta has a business is not testable from public data. Watch only for a funding announcement or a restart of the API.

### Tracking card
- Site https://www.vishwalab.com ; API https://api.vishwalab.com ; OpenAPI https://api.vishwalab.com/openapi.json ; Veta https://vetagate.com ; OpenNEXT https://open-next.ai ; CLI https://cli.vishwalab.com ; vault https://vault.vishwalab.com ; blogs https://medium.com/vishwanetwork and https://medium.com/vishwa-research (RSS at /feed/...)
- GitHub https://github.com/vishwanetwork ; npm @vishwalab/cli ; X https://x.com/Vishwa_lab ; DefiLlama https://defillama.com/protocol/vishwa ; Farcaster, Telegram, Discord, Dune: none found
- x402scan recipients: Base `0x6a5e7d954f49712abf3f873f037ec845b7b8c666` ([page](https://www.x402scan.com/recipient/0x6a5e7d954f49712abf3f873f037ec845b7b8c666)); Solana `CvX23FNQsNQww8ALR3EWgQv2Wt5yM7VvU4HRigGBMMJu`; facilitator payAI. Token: none.

### Sources
Accessed 2026-10-11: [vishwalab.com](https://www.vishwalab.com/), [OpenAPI](https://api.vishwalab.com/openapi.json), Medium feeds ([vishwanetwork](https://medium.com/feed/vishwanetwork), [vishwa-research](https://medium.com/feed/vishwa-research)), [DefiLlama](https://api.llama.fi/protocol/vishwa), [npm](https://registry.npmjs.org/@vishwalab%2fcli), [Veta](https://vetagate.com/).

[vb-daily]: https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x6a5e7d954f49712abf3f873f037ec845b7b8c666%22%5D%7D%7D%7D
[vs-daily]: https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22solana%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%22CvX23FNQsNQww8ALR3EWgQv2Wt5yM7VvU4HRigGBMMJu%22%5D%7D%7D%7D
[vb-sellers-all]: https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x6a5e7d954f49712abf3f873f037ec845b7b8c666%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A5%7D%7D%7D

---

## 6. What this group says about where Base x402 volume comes from

### Takeaway
Base's x402 transaction count is mostly machines paying machines at tiny prices, not a broad market of paying customers. These five projects supplied 79.1% of the window's Base transactions (32.8M of 41.5M) and 9.0% of its USDC ($0.51M of $5.66M), and each headline number traces to one mechanism: one wallet, a polling loop, a bot fleet, a rewards contest, or a coordinated 2025 fleet. The honest demand signal is distinct buyers, which sit in the hundreds (BlockRun 367 in the last 30 days) except where rewards pay for activity (AX1 about 4,700).

### Cited findings
Base totals for 2026-04-11 to 2026-10-11 are 41,496,473 tx and $5,661,369 ([x402scan network series](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)); project figures are in the sections above.

| Project | Base window headline | What produces it | Evidence (section) |
|---|---|---|---|
| BlockRun | 27.04M tx, $450K (65% of Base tx) | One Base wallet made 26.70M tx (64.3% of all Base tx); a second wallet did the same on Solana | wallet-level x402scan queries (1) |
| claw402 | 4.87M tx, $9.5K | 25 to 40 wallets polling $0.002 signal endpoints all day | payment sample (3) |
| Vishwa | 0.48M tx, $41.6K | A fixed fleet of about 300 wallets paying $0.001 daily; a few $9.90 order payments | daily buyers, 12 samples (5) |
| AX1 | 0.41M tx, $8.2K | $0.02 entry fees to a weekly rewards contest with a Monday cutoff | AX1 post #3166, Sunday peaks (2) |
| AIsa | 121 tx (31.5M in Oct-Dec 2025) | 2025: a cohort of about 40 similar wallets (five checked) that stopped within minutes on 2025-12-31 | wallet checks (4) |

- Without the one BlockRun wallet, Base had 14.8M tx in the window and BlockRun's share would be 2.3%, not 65%.
- The Base-to-Solana "flip" of 2026-08-19 to 09-10 looks like one payer changing chain (inference, section 1); Artemis-based Solana shares (76% of x402 tx in four weeks to 2026-09-22) are credited by Solana Compass to enterprise integrations and Coinbase's Solana facilitator upgrade, not to BlockRun ([Solana Compass](https://solanacompass.com/news/solana-processes-76-of-all-x402-ai-agent-transactions-232-million-in-four-weeks)).
- Sub-cent payments are expensive to settle one by one: Coinbase's hosted facilitator charges $0.001 per onchain transaction after 1,000 free a month ([CDP docs](https://docs.cdp.coinbase.com/x402/core-concepts/facilitator)), and BlockRun says Solana batching can save over $20,000 a month ([Bitcoin.com](https://news.bitcoin.com/technology/solana-x402-lets-ai-agents-batch-usdc-payments-slashing-fees/)). AIsa's live 402 challenge already offers Circle Gateway batched payments.

### Inferences
- Read x402scan transaction rank as an index of automation and incentives. Prefer distinct buyers over 30 days, USDC per buyer, and repeat buyers across weeks.
- As batching spreads (Solana batch settlement from 2026-10-07, Circle Gateway), on-chain counts should fall without demand falling, so transaction totals will become less comparable over time.
- Where to look daily: BlockRun first (GitHub releases and changelog change daily), AIsa weekly (funding and product), AX1 weekly around reward and token news, claw402 and Vishwa monthly.
- Direction of travel: none of the five is betting on per-call Base x402 alone. BlockRun is moving to Solana and cards, AIsa to batched settlement and API keys, Vishwa to Solana, AX1 to a rewards contest and a token, claw402 to the NOFX/Vergex stack.

### Gaps
- The owners and funding sources of BlockRun's two heavy wallets are unknown; block explorers refuse scripted access and I did not bypass that. BlockRun's own statement that most paid calls hit free-tier models could not be found; X could not be opened.
- AX1 names no team; some AX1 mechanics come from a summarised Telegram post and search snippets of X posts.
- AIsa's batched flow is invisible to x402scan; its home-page numbers cannot be checked on-chain.
- Vishwa's rank and capital claims are unverifiable and I found no funding.
- claw402's wallets were not tested for independence; the CLAW402 token's link to the gateway is unresolved.
- Commit counts include bots and AI-assisted commits, so they overstate effort. Dune and Farcaster presence was mostly not found.

## 7. Comparison table

| Project | x402 role | Token | Share of volume that looks real | Seriousness | Momentum | Trend-hopping (1-5) |
|---|---|---|---|---|---|---|
| BlockRun | Seller (LLM/data gateway) + SDK/tooling | None official; unofficial Solana look-alikes | About 1.3% of window tx and 2.3% of USDC outside two single-wallet streams; the other 98.7% is one payer per chain, unverified | Serious builder | Accelerating (shipping); Steady (organic x402) | 2 |
| AX1 Console | Seller (one $0.02 route) + analytics + planned trust service | None yet; `$AX1` planned (pre-TGE) | Low (judgement: under 10%); a weekly rewards contest drives the calls | Speculative | Steady | 4 |
| claw402 | Seller (data/AI gateway) + SDK | None for the gateway; a Solana "CLAW402" memecoin (`FJPoRj…pump`) appears unrelated | Probably most of it is genuine automated use by a few dozen NOFX/Vergex agents (judgement); independence unverified; about $1.4K a month | Credible but small | Slowing | 3 |
| AIsa | Seller (marketplace/gateway) + SDK/tooling | None | Near nil in the window (121 tx); 2025 volume looks like a coordinated fleet | Credible but small (Base x402 likely abandoned) | Steady (company); Dead (visible Base x402) | 3 |
| Vishwa | Seller (prediction-market API) + trust pitch | None | Low (judgement): fixed ~300-wallet fleet at $0.001; dollars from a few $9.90 payments | Speculative | Slowing | 4 |
