# Token-bearing x402 facilitators with Base support: due diligence profiles

Status: final version. Items that could not be confirmed are labelled **Unconfirmed** or listed under each profile's Gaps.

Research date: 2026-10-11. "Last six months" = 2026-04-11 to 2026-10-11. All sources accessed 2026-10-11 unless stated. Token facts only: no prices, market caps or charts are recorded here.

## How this was researched, and limits

- **Usage numbers** come from x402scan's own public data endpoint (the same data the x402scan website renders): `https://www.x402scan.com/api/trpc/public.facilitators.list` and `.bucketedStatistics`, queried 2026-10-11 ([x402scan facilitators page](https://www.x402scan.com/facilitators)). x402scan's paid REST API returned HTTP 402; I did not pay and did not use it. x402scan counts on-chain transfers sent by *known facilitator addresses* on **Base, Solana and Polygon only** (see the [facilitator address registry](https://github.com/Merit-Systems/x402scan/tree/main/packages/external/facilitators/src/facilitators)); activity on other chains, or from unregistered signer addresses, is invisible to it. It hides facilitators with fewer than 100 transactions in the selected window. USD = raw token units / 1e6 (USDC).
- **Transaction counts are not a measure of real demand.** Several facilitators show millions of transactions worth fractions of a cent each (automation, load tests, token-mint loops). PayAI itself says so in its own 2026-09-06 post ([PayAI blog](https://blog.payai.network/x402-is-gaining-momentum-on-solana-thats-a-win-for-the-whole-ecosystem/)).
- **The x402.org ecosystem page** (`https://www.x402.org/ecosystem`) returned 404 on 2026-10-11, so the facilitator list was read from its source data in the `coinbase/x402` repo (`typescript/site/app/ecosystem/partners-data`); x402scan's registry and live rankings supplied the rest.
- **Web search quota ran out mid-task.** After that I used direct page, API and GitHub fetches only. CryptoRank returned 403, RootData returned an empty page, x.com and LinkedIn are not fetchable. So **funding and team claims rest on project pages, GitHub, CoinGecko and a few aggregator pages (AskSurf, CoinCodex, CoinCarp, TechFlow)**, flagged where used. Nothing here comes from X posts except where a project's own site links to them.
- **People rules followed.** Only professional, public information. X handles are recorded only when an official page links them or the person self-declares them (GitHub profile `twitter_username` field counts as self-declared). No attempt was made to tie a pseudonym to a real name. Companies House was deliberately not searched for Primer.
- **Scope.** Platform layer, non-token infrastructure, agent frameworks, agent apps, x402 apps, data sellers, token experiments and rival-chain projects (Dexter, Corbits, Daydreams, Virtuals, Questflow, thirdweb, x402.rs, OpenX402, Mogami) are covered by other researchers; they appear here only as competitors.

## Answers to the key questions (summary)

### 1. PayAI Network: how much is on Base, who runs it, has it grown beyond facilitation?

**Takeaway.** PayAI is a real, continuously shipping facilitator, Solana-first by its own words, run by one publicly identified but pseudonymous founder. Base was its main chain until about June 2026 and is now under 4% of its tracked transactions; it has added discovery, SDKs, credits billing and batch settlement but remains a facilitation business.

**Cited findings.**
- PayAI's site says "PayAI is Solana-first" and lists Solana, Base, Polygon, Avalanche, Arbitrum, Sei, X Layer and SKALE ([payai-website source, Partners.jsx](https://github.com/PayAINetwork/payai-website/blob/main/src/components/sections/Partners.jsx)); the live `/supported` endpoint confirms those networks plus `batch-settlement` ([facilitator.payai.network/supported](https://facilitator.payai.network/supported)).
- x402scan lifetime to 2026-10-10: PayAI 52.71M transactions / $6.75M, second only to Coinbase (118.03M / $30.19M). Base = 23.56M tx / $4.43M (44.7% of tx, 65.7% of USD); Solana = 29.15M tx / $2.32M ([x402scan](https://www.x402scan.com/facilitators)).
- Six-month window (2026-04-11 to 2026-10-11): Base 687,832 tx / $1.12M vs Solana 17.28M tx / $356K, so Base is 3.8% of tx but 76% of USD. Base monthly tx fell from 8.95M (Jan 2026) to about 33K (Sep 2026) ([x402scan bucketed series](https://www.x402scan.com/facilitators)).
- Founder: "Notorious, founder at PayAI (@notorious_d_e_v)" appears in PayAI's own post ([blog.payai.network, Pay.sh post](https://blog.payai.network/payai-powers-pay-sh-the-agentic-payments-layer-for-solana/)). Entity is PayAI Network, LLC, Delaware ([Terms of Service](https://payai.network/terms-of-service)). Pseudonymous.
- Beyond facilitation: Bazaar discovery catalog (1,033 hosts / 18,988 resources on 2026-10-11), `@payai/facilitator` and `x402-solana` SDKs, merchant portal with prepaid credits, Echo test merchant, Anthropic-commerce checkout, x402+MPP SDK, Solana and Base batch settlement ([discovery stats](https://facilitator.payai.network/discovery/stats), [docs index](https://docs.payai.network/llms.txt)).

**Inferences.** The headline volume is mostly Solana automation; Base is a secondary market where Coinbase's free tier dominates (Coinbase = 90.4% of Base transactions in the last 30 days). PayAI's differentiation is chain breadth, discovery and Solana depth, not Base.

**Gaps.** No funding information found; no named team besides the founder; the token-migration mechanics of 2025-11-18 are undocumented in sources I could reach.

### 2. Heurist: how central is x402, what was built before?

**Takeaway.** x402 is a side rail for Heurist, not the business. The facilitator did 7.97M transactions worth only $30K, almost all in Nov 2025 to Jan 2026, and moved $59 in the last six months. Heurist has pivoted at least six times since 2023 (GPU network, agent framework, tool marketplace, ZK chain, equity tokenization, stock-research desk) with a real product each time.

**Cited findings.**
- x402scan (Base only): lifetime 7,967,176 tx / $30,160, last transaction 2026-10-08; window total 5,997 tx / $59; below the 100-tx display threshold for the last 30 days ([x402scan](https://www.x402scan.com/facilitators)).
- Docs list Mesh access by "API key, x402 pay-per-use payments, and MCP"; the credits page (primary monetisation) does not mention x402 ([Mesh overview](https://docs.heurist.ai/heurist-mesh/overview.md), [credits](https://docs.heurist.ai/protocol-overview/credits.md)).
- Timeline: testnet mining 2024, $2M pre-seed 2024-11-14, HEU live 2024-12-09, Agent Framework 2024-12-20, Mesh 2025-04-17, Deep Research 2025-05-29, Heurist Chain 2025-07-23, Ask Heurist 2026-04-06, Heurist Finance (stocks) 2026-08-01 ([Heurist blog index](https://heurist.ai/blog), [Medium feed](https://medium.com/feed/@heuristai)).

**Inferences.** The team treats x402 as a payment option for Mesh data, and now builds for stocks and Robinhood Chain. Do not follow Heurist for x402 news; follow it monthly as a company.

**Gaps.** Cause of the 7.97M-transaction burst (avg $0.004) is undocumented; team page does not exist on official sites.

### 3. AurraCloud, Meridian, Primer, CodeNut: exist, active, Base, token?

| Project | Exists | Active now | Base | Token | Plain verdict |
|---|---|---|---|---|---|
| AurraCloud | Yes (GitHub org since 2025-05-16, X @AurraCloud) | **Facilitator dead**: facilitator domain no longer resolves; last x402scan tx 2026-01-13; x402scan marks it deprecated. Company still ships a Hyperliquid CLI (`openbroker`, 29 npm releases since Apr) | Yes while live (236K tx, $53.6K) | **Yes**: $AURA, Virtuals launch on Base 2025-01-08 | Facilitator abandoned |
| Meridian | Yes (Swiss association, docs + API live) | Active but shrinking: 3,415 tx / $129K in last 30d from 14 buyers | Yes, Base is the fee/cashback chain | **Yes**: $MRDN on Base (first pools 2025-09-16) and Robinhood Chain | Alive, volume concentrated in a handful of wallets |
| Primer | Yes (org since 2025-12-11) | Active: 5,763 tx in last 30d, releases weekly | Yes | **Yes**: $PR, fair launch Dec 2025 on Base, migrated to Robinhood Chain 2026-08-14 (no Base contract now) | Alive, tiny usage |
| CodeNut | Yes (vibe-coding DApp builder) | **Facilitator dead**: `facilitator.codenut.ai` unreachable; last tx 2026-01-27; GitHub quiet since 2025-12-12; x402scan marks deprecated | Yes while live (478K tx, $110K) | **None found** (not in CoinGecko or Virtuals) | Abandoned |

([x402scan registry](https://github.com/Merit-Systems/x402scan/tree/main/packages/external/facilitators/src/facilitators), live probes 2026-10-11, details in each profile.)

### 4. Other token-bearing facilitators with Base support and real volume

**Takeaway.** Only two additional token-bearing facilitators clear a "real volume" bar (>=100K lifetime x402scan tx or >=$100K USD) after excluding the groups assigned elsewhere: **AnySpend ($ANY, Base)** and **Relai ($REL, Solana)**. Both are stalled. The biggest non-Coinbase Base facilitator by 30-day tx, **FluxA** (136K tx, $322K), has no token.

**Cited findings.** AnySpend 521K tx / $141K lifetime, last tx 2026-08-17; Relai 303K tx / $508K, last tx 2026-07-08 and its facilitator hostname does not respond; FluxA 2.70M tx / $660K, Base only, no token on its site or in CoinGecko ([x402scan](https://www.x402scan.com/facilitators), [FluxA](https://fluxapay.xyz), [CoinGecko list](https://api.coingecko.com/api/v3/coins/list?include_platform=true)). Screened-out names are in the table near the end.

### 5. Versus Coinbase CDP, and how projects avoid being squeezed

**Takeaway.** CDP prices at 1,000 free on-chain transactions per month, then $0.001, with verification free; it supports Base, Polygon, Arbitrum, World and Solana and carries 90% of Base facilitator transactions. Nobody profiled here beats it on price on Base: PayAI charges gas plus 30% (about $0.0022 to $0.0023 per Base settlement), Meridian charges a 1% protocol fee on Base x402 payments (offset by token cashback). Survival strategies are: multi-chain breadth (PayAI 8 chains, Meridian 25 networks, Primer 4), discovery and billing layers (PayAI), selling their own data or AI inference over x402 (Heurist, Meridian), token subsidy (Meridian) and new-chain first-mover claims (Primer on Robinhood Chain).

**Cited findings.** [CDP facilitator docs](https://docs.cdp.coinbase.com/x402/seller/facilitator.md); [PayAI pricing snapshot 2026-09-22](https://docs.payai.network/x402/facilitators/pricing.md); [Meridian tokenomics](https://docs.mrdn.finance/tokenomics.md); Coinbase share from x402scan Base 30-day table.

**Cross-project observation.** Three of the four main profiles moved to Robinhood Chain in Jul to Sep 2026: Primer (first facilitator there 2026-07-05, token migrated 2026-08-14), Meridian (MRDN deployed 2026-07-31), Heurist (Mesh adds Robinhood chain 2026-09-02, plus the stock-research pivot). That is a trend-hopping signal.

### Follow list (suggested)

- **Daily:** PayAI (blog RSS, GitHub, x402scan). **Weekly:** Primer (homepage update log, GitHub releases); Meridian (x402scan, docs; low priority). **Monthly:** Heurist (Medium feed), AnySpend. **Skip for x402 news:** Relai, AurraCloud, CodeNut (dead or stalled facilitators).
- Token-less but worth a glance for Base volume: FluxA (2nd on Base by 30-day tx) and Ultravioleta DAO.

## Snapshot: x402scan numbers for the projects in this file (fetched 2026-10-11)

| Facilitator (x402scan id) | Token | Lifetime tx / USD (to 2026-10-10) | Base last 30d tx / USD | Base 30d buyers / sellers | Last tx |
|---|---|---|---|---|---|
| Coinbase (`coinbase`) | none | 118.03M / $30.19M | 1,965,296 / $232,816 | 29,911 / 34,199 | 2026-10-11 |
| PayAI (`payAI`) | $PAYAI (Solana) | 52.71M / $6.75M (Base 23.56M / $4.43M) | 24,346 / $5,872 | 1,208 / 1,045 | 2026-10-11 |
| Heurist (`heurist`) | $HEU | 7.97M / $30,160 | <100 (hidden) | n/a | 2026-10-08 |
| Meridian (`mrdn`) | $MRDN | 148,129 / $3.79M | 3,415 / $129,224 | 14 / 14 | 2026-10-10 |
| Primer (`primer`) | $PR | 39,292 / $8,960 | 5,763 / $1,508 | 96 / 28 | 2026-10-11 |
| AnySpend (`anyspend`) | $ANY | 521,040 / $140,701 | 0 | n/a | 2026-08-17 |
| Relai (`relai`) | $REL (Solana) | 303,181 / $508,026 (Base 89,527 / $214,985) | 0 | n/a | 2026-07-08 |
| AurraCloud (`aurracloud`, deprecated) | $AURA | 235,975 / $53,551 | 0 | n/a | 2026-01-13 |
| CodeNut (`codenut`, deprecated) | none found | 477,922 / $110,037 | 0 | n/a | 2026-01-27 |

Base 30-day shares of the 13 listed facilitators: Coinbase 90.4% of tx but 33.2% of USD; FluxA 6.3% of tx and 45.9% of USD; PayAI 1.1% / 0.8%; Primer 0.3% / 0.2%; Meridian 0.2% of tx but 18.4% of USD.

## Coinbase CDP vs these facilitators (price, chains, features)

| Facilitator | Price | Chains (live `/supported` or docs, 2026-10-11) | Notable features |
|---|---|---|---|
| Coinbase CDP | First 1,000 on-chain tx/month free, then $0.001; verify free ([CDP](https://docs.cdp.coinbase.com/x402/seller/facilitator.md)) | Base, Polygon, Arbitrum, World, Solana (+ testnets) | exact/upto/batch-settlement, OFAC+KYT, Bazaar, ERC-8021 builder codes, "more than 100 million transactions and $28 million" (undated) |
| PayAI | 1,000 lifetime free credits per receiving wallet, then gas + 30% in $0.001 credits; Base exact about 2.2 to 2.3 credits; cost-plus live since 2026-09-21; 10% discount if credits bought with $PAYAI ([pricing](https://docs.payai.network/x402/facilitators/pricing.md)) | Solana, Base, Polygon, Arbitrum, Avalanche, Sei, X Layer, SKALE Base | Bazaar, batch-settlement (Solana + Base), gas sponsorship extensions, Auto Top-Up |
| Heurist | No fees stated; no API key ([docs](https://docs.heurist.ai/x402-products/facilitator)) | Base, X Layer, Stable | OFAC screening, builder-code extension; token conversion "coming soon" |
| Meridian | 1% protocol fee on x402 txs on Base; MRDN cashback 2% (cap $5) ([tokenomics](https://docs.mrdn.finance/tokenomics.md)); org API key | 25 network names incl. Base, Arc, Robinhood, MegaETH, Solana | Proxy-facilitator contracts, Circle Gateway nanopayments, Permit2, "upto", Command Centre |
| Primer | No pricing published ([docs](https://docs.primer.systems/facilitator.html)); no signup | Base, SKALE Base, Robinhood Chain, LitVM | exact/upto/batch-settlement, Permit2/"Prism" ERC-20 support, smart wallets |
| AnySpend | Not published | 9 networks incl. Base; x402 v1 `exact` only | cross-chain routing |

---

# PROFILE 1: PayAI Network ($PAYAI)

### One-line
A hosted x402 payment facilitator (verifies and settles stablecoin payments for APIs and AI agents) that calls itself Solana-first but also settles on Base and six other EVM chains, run by a Delaware LLC with a single publicly visible founder ([About page](https://payai.network/about.md)).

### x402 role
Facilitator (core). Also discovery/analytics (PayAI Bazaar catalog, [stats endpoint](https://facilitator.payai.network/discovery/stats)), SDK/tooling (`@payai/facilitator`, `x402-solana`, `x402-solana-react`, `agentic-payments` x402+MPP SDK, docs MCP server, AI "skills"), seller-side test tool (Echo Merchant at x402.payai.network) and a billing portal (prepaid credits). Founder also contributes to the x402 reference repo (33 contributions; at least 30 PRs found, incl. SVM batch settlement) ([x402-foundation/x402 contributors](https://github.com/x402-foundation/x402/graphs/contributors)).

### Chains
- Live `/supported` (2026-10-11): Base, Polygon, Arbitrum, Avalanche, Sei, X Layer, SKALE Base, Solana (+ testnets); schemes `exact` and `batch-settlement`; extensions `bazaar`, `eip2612GasSponsoring`, `erc20ApprovalGasSponsoring` ([supported](https://facilitator.payai.network/supported)). Homepage text: "PayAI is Solana-first" ([site source](https://github.com/PayAINetwork/payai-website/blob/main/src/components/sections/Partners.jsx)).
- **Is Base primary? No, not since about June 2026.** x402scan (Base + Solana only): lifetime Base 44.7% of tx / 65.7% of USD; last six months Base 3.8% of tx / 76% of USD; last 30 days Base 24,346 tx ($5,872) vs Solana 230,061 tx ($2,361). Monthly Base tx: Oct 2025 406K, Nov 6.10M, Dec 6.83M, Jan 2026 8.95M, Feb 219K, Mar 315K, Apr 185K, May 178K, Jun 265K, Jul 33K, Aug 43K, Sep 33K ([x402scan](https://www.x402scan.com/facilitators)). First PayAI Base facilitator address dates to 2025-05-18, Solana to 2025-07-01 ([registry](https://raw.githubusercontent.com/Merit-Systems/x402scan/main/packages/external/facilitators/src/facilitators/payai.ts)). Arbitrum, Avalanche, Sei, X Layer and SKALE activity is invisible to x402scan.

### Token
- **$PAYAI, Solana only. No Base contract** (the docs list only Solana contracts) ([official links](https://docs.payai.network/llms-full.txt)).
- Current mint `PAYmo6moDF3Ro3X6bU2jwe2UdBnBhv8YjLgL1j4DxGu`: supply 999,942,167 (9 decimals), mint and freeze authority both null (Solana RPC `getTokenSupply`/`getAccountInfo`, 2026-10-11). Launch of the current mint: migration announced on X on 2025-11-18 (post ID 1990864889666023557 decodes to 2025-11-18 19:29 UTC; CoinGecko links it), first Raydium pool the same day ([CoinGecko](https://www.coingecko.com/en/coins/payai-network-2), [DexScreener](https://api.dexscreener.com/latest/dex/tokens/PAYmo6moDF3Ro3X6bU2jwe2UdBnBhv8YjLgL1j4DxGu)). Swap ratio/mechanism: not found.
- Original token: pump.fun launch `E7NgL19JbN8BhUDgWjkH8MtnbhJoaGaWJqosxZZepump`, first Raydium pool 2025-03-09, now "PayAI Network [OLD]" on CoinGecko; docs still link its pump.fun page ([CoinGecko](https://www.coingecko.com/en/coins/payai-network)).
- Stated utility ("Token Use & Legal Disclaimer"): lower platform fees between agents, boost listings, governance, arbitration fees; "not required" to use the platform. This text is from the 2025 agent-marketplace era. **Documented live function today: 10% discount when buying facilitator credits with $PAYAI on Solana** ([pricing](https://docs.payai.network/x402/facilitators/pricing.md)). So: minor real work, optional.

### Team
- **Notorious D.E.V.** (pseudonym), founder. X **@notorious_d_e_v**: named by PayAI's own post ("Notorious, founder at PayAI (@notorious_d_e_v)") and set on his GitHub profile (high confidence) ([Pay.sh post](https://blog.payai.network/payai-powers-pay-sh-the-agentic-payments-layer-for-solana/)). GitHub **notorious-d-e-v** (company "PayAI", blog payai.network, bio "Gettin' these ai agents PAID."), verified by commits: 273 of 303 public commits in the window. Farcaster **@notorious-d-e-v** (fid 1341247), bio "Gettin' AI agents paid @ PayAI Network" ([Warpcast](https://client.warpcast.com/v2/user-by-username?username=notorious-d-e-v)). Pseudonymous.
- **aptum11** (GitHub, no name/bio): 15 commits 2026-04-11 to 2026-07-15; top committer to `x402-echo-merchant` (66 lifetime). Link to PayAI by commits only.
- **twzrd-sol** (4 commits, 2026-07-12/13). Earlier (pre-window) public committers: NinoTabet ("Anthony Tabet", freelance full-stack dev per bio), postmanode (pseudonym), riqfams (web developer per bio), Mbdulrohim (X @Mbdulrohim), kohasummons (DevRel, X @kohawithstuff): outside/freelance contributors, not confirmed staff.
- **Wize**: pseudonymous blog author (10 of the latest 15 posts), no profile ([author page](https://blog.payai.network/author/wize/)).
- Not PayAI staff: `lgalabru` and `MicaiahReid` (Solana Foundation) appear in `PayAINetwork/pay-skills` only because it is a fork of `solana-foundation/pay-skills`.
- Entity: PayAI Network, LLC, Delaware; "the team works remotely" ([ToS](https://payai.network/terms-of-service), [About](https://payai.network/about.md)). Joins/departures: none announced; aptum11 silent since 2026-07-15 (inference only).

### Track record and pivots (dated)
- 2025-02-25 website repo created; 2025-03-09 first DEX pool of the original pump.fun token; 2025-03 `payai-http-gateway` and `payai-solana-smart-contracts`; 2025-04-22 `plugin-payai` ElizaOS plugin (25 stars). CoinGecko still describes PayAI as an "open-source, decentralized AI Agent marketplace... Built on ElizaOS, libp2p, IPFS, and Solana" ([CoinGecko](https://www.coingecko.com/en/coins/payai-network-2)).
- 2025-05-03 GitHub org created; 2025-05-17 Echo merchant; **2025-05-18 first facilitator transactions on Base** (pivot from agent marketplace to x402 facilitator).
- 2025-10-15 `x402-solana` v0.1.0; Oct to Dec 2025 volume peak; 2025-11-18 token migration; 2025-12-10 ToS update.
- 2026-02-16 free service becomes credits-based; 2026-05-05 launch partner of Solana Foundation's Pay.sh; 2026-09-21 cost-plus pricing.
- One real pivot (marketplace to facilitator), then 17 months of x402 focus ([GitHub org](https://github.com/PayAINetwork), [PayAI blog](https://blog.payai.network/rss/)).

### Trend-hopping score: 2 / 5
x402 is the continuous thread since May 2025; the earlier ElizaOS marketplace was the previous narrative and the only pivot. Adjacent bets (MPP, Anthropic commerce checkout, Pay.sh, SEO-style posts on BlackRock/Visa/Circle Arc) follow news but ship on the same facilitator. Marketing claims were corrected on 2026-09-13 (see flags).

### Funding
No evidence of outside funding found (nothing on PayAI's site, docs or blog; CryptoRank blocked, RootData empty). Revenue: prepaid credits at $0.001 since 2026-02-16 and gas + 30% since 2026-09-21 ([pricing post](https://blog.payai.network/product-update-payai-facilitator-pricing-is-now-live/)).

### Product and traction
- Live: facilitator (Solana, Base, 6 more EVM), Bazaar catalog, merchant portal and credits, Auto Top-Up, Echo merchant, `/discovery/stats`.
- Bazaar stats 2026-10-11 (PayAI's own, self-reported): 1,033 hosts, 18,988 resources; 24h 10,957, 7d 86,617, 30d 336,893 settlements; top "merchants" include `loadgen.x402bench.dev` and a `localhost` entry. Host cleanup of unreachable entries was done in Sep 2026 ([stats](https://facilitator.payai.network/discovery/stats), [Bazaar docs](https://docs.payai.network/llms-full.txt)).
- x402scan: lifetime 52.71M tx / $6.75M (rank 2); 30d 254,407 tx / $8,233, 1,852 buyers / 1,114 sellers (rank 2 by tx all chains). Solana is spiky: 1,525,922 tx on 2026-09-01 for $15,164 from 151 buyers; 17.28M Solana tx in six months averaging about $0.02.
- Customer claims (vendor-written): Holoworld/FightID 3,000 passes at 50 USDC = $150K (2026-02-15) ([post](https://blog.payai.network/holoworld-case-study/)); ClawRouter $1,825 over 63 days (2026-05-08).

### Last six months (2026-04-11 to 2026-10-11)
- Releases (npm): `@payai/facilitator` 2.4.0 (04-13), 2.4.1 (04-22), 2.4.2/2.4.3 (05-29), 2.4.4 (07-16), 2.4.5 (09-29), 2.4.6 (10-01); `x402-solana` 2.0.5 and 2.1.0 (08-01), 3.0.0 (08-12), 3.0.1 (10-01); `x402-solana-react` 2.1.0 (08-12); `x402-batch-preview` GitHub releases 09-21, 09-22, 09-28, 09-29 ([npm](https://registry.npmjs.org/@payai%2ffacilitator), [GitHub releases](https://github.com/PayAINetwork/x402-batch-preview/releases)).
- 05-05 Pay.sh launch partner; 05-15 x402 vs MPP post; 06-12 Arbitrum One support; **07-24 Base Flashblocks preconfirmation receipts: Base p50 settlement from about 1.7 s to about 750 ms (own benchmark)**; 08-11 Auto Top-Up for credits on Solana and Base; 09-03 `x402-commerce-checkout` (open-source checkout for Anthropic commerce agents) created; 09-13 to 09-29 Solana batch settlement public preview; **09-29 docs for EVM Batch Settlement on Base** (docs PR #96; 10-01 PayAI-held authorizer option); 09-21 cost-plus pricing live ([blog](https://blog.payai.network/rss/), [docs history](https://github.com/PayAINetwork/docs/commits/main)).
- Public commits (excl. fork): Apr 27, May 46, Jun 6, Jul 19, Aug 94, Sep 102, Oct 9 (to 10-05) = 303; contributors: notorious-d-e-v 273, aptum11 15, twzrd-sol 4, bot 11; commits in 23 of 26 ISO weeks; last public push 2026-10-06. By repo: docs 92, payai-website 87, agentic-payments 37, x402-solana 28, x402-commerce-checkout 25, x402-echo-merchant 20, x402-batch-preview 6, payai-x402-skill 5, x402-solana-react 3. Lifetime top contributors: notorious-d-e-v 177 (docs), 137 (website), 55 (x402-solana).

### Pace verdict
Not slow. About 10 commits a week from the founder, 12 npm releases in six months (7 facilitator, 4 x402-solana, 1 React) plus 4 batch-preview releases, 3 new product areas (batch settlement, credits/auto top-up, commerce checkout) in Aug to Sep, and at least 30 upstream PRs. A small AI-assisted team is expected to commit weekly and release roughly monthly; PayAI fits, apart from a quiet June (6 commits, no releases between 05-29 and 07-16). The reference x402 repo itself runs 67 to 115 commits a month with a much larger contributor base ([x402-foundation/x402](https://github.com/x402-foundation/x402)). Single-founder dependency is the structural weakness.

### Direction
Stated (homepage): Payment Splitting and Token Gateway "coming soon" ([homepage](https://payai.network)). Shipping record: neither visible; effort went into batch settlement for metered APIs, credits billing, discovery hygiene and multi-chain additions. Expect PayAI to keep positioning as agent-commerce plumbing with paid usage, centred on Solana and metered-API (batch) payments.

### Competitors
Coinbase CDP (Base leader, 90.4% of Base 30d tx; PayAI is 1.1%); Dexter (28.0M lifetime tx, Solana-first); Figment (Solana, 107K tx/30d, one seller); three.ws; Corbits; thirdweb; OpenX402; Mogami; x402.rs; Solana Foundation's Pay.sh as a channel. On Solana 30d PayAI leads tracked tx (230K vs Figment 107K, Coinbase 80K, Dexter 30K); on Base it is far behind Coinbase and FluxA ([x402scan](https://www.x402scan.com/facilitators)).

### Green and red flags
- Green: 17 months of continuous shipping; protocol-level upstream contributions; published, dated pricing with a real revenue model; public `/supported` and stats endpoints; corrected overstated posts on 2026-09-13; mint and freeze authorities revoked on both token mints; real Base engineering (Flashblocks, batch channels).
- Red: one-person public core; Base usage down more than 99% from the Jan 2026 peak; Solana counts dominated by micro-payment automation (and test/load hosts in the catalog); the 2026-05-29 "largest x402 facilitator on Solana" post had market-share and "artificial activity" claims later withdrawn for lacking "a reproducible, dated denominator" ([post](https://blog.payai.network/largest-x402-facilitator-solana/)); two token contracts and a stale token-utility page; priced above CDP on Base (about $0.0023 vs $0.001 after free tiers); no named team beyond the founder; no funding disclosure.

### Verdict
**Serious builder (small team). Momentum: Steady** (shipping accelerating, Base usage slowing). PayAI is the best-evidenced token-bearing facilitator here: sustained delivery, protocol-level credibility and an actual price list. But it is effectively a founder-plus-AI-tools operation whose Base business has largely evaporated while Solana automation inflates the headline counts. It is heading toward paid, Solana-centric agent-commerce infrastructure (facilitation plus discovery plus batch settlement for metered APIs); on Base, CDP's free tier will keep winning. **Follow daily** (blog RSS, GitHub, x402scan).

### Tracking card
- Website https://payai.network | Docs https://docs.payai.network (llms.txt, MCP at /mcp) | Blog https://blog.payai.network, RSS https://blog.payai.network/rss/ | Changelog: none (use npm + docs commits https://github.com/PayAINetwork/docs/commits/main)
- GitHub org PayAINetwork: `docs`, `payai-website`, `x402-solana`, `x402-solana-react`, `x402-echo-merchant`, `agentic-payments`, `x402-batch-preview`, `x402-commerce-checkout`, `payai-x402-skill`
- X: @PayAINetwork (official, linked on site/docs); founder @notorious_d_e_v. LinkedIn linkedin.com/company/payai-network. Farcaster: founder @notorious-d-e-v (fid 1341247); no project account found. Telegram t.me/PayAINetwork; Discord discord.gg/eWJRwMpebQ
- Token: Solana `PAYmo6moDF3Ro3X6bU2jwe2UdBnBhv8YjLgL1j4DxGu` (old `E7NgL19JbN8BhUDgWjkH8MtnbhJoaGaWJqosxZZepump`); payment handler program `5FhmaXvWm1FZ3bpsE5rxkey5pNWDLkvaGAzoGkTUZfZ3`
- x402scan id `payAI`; Base addresses `0xc6699d2aadA6c36Dfea5C248DD70f9CB0235cB63`, `0xB2Bd29925CBbCEA7628279c91945Ca5B98bf371B` (+ deprecated set); Solana fee payer `2wKupLR9q6wXYppw8Gr2NvWxKBUqm4PPJKkQfoxHDBg4`
- Dune: https://dune.com/hashed_official/x402-analytics (covers PayAI, Heurist, Ultravioleta, Treasure and others)

### Sources (accessed 2026-10-11)
https://payai.network ; https://payai.network/about.md ; https://payai.network/llms.txt ; https://payai.network/terms-of-service ; https://docs.payai.network/llms.txt ; https://docs.payai.network/llms-full.txt ; https://docs.payai.network/x402/facilitators/pricing.md ; https://docs.payai.network/x402/supported-networks.md ; https://facilitator.payai.network/supported ; https://facilitator.payai.network/discovery/stats ; https://blog.payai.network/rss/ ; https://blog.payai.network/sitemap-posts.xml ; blog posts (Pay.sh, pricing, Holoworld, largest-x402..., Flashblocks, x402-is-gaining-momentum) ; https://www.coingecko.com/en/coins/payai-network-2 ; https://www.coingecko.com/en/coins/payai-network ; https://api.dexscreener.com/latest/dex/tokens/PAYmo6moDF3Ro3X6bU2jwe2UdBnBhv8YjLgL1j4DxGu ; https://api.mainnet-beta.solana.com ; https://github.com/PayAINetwork (GitHub REST API) ; https://registry.npmjs.org/@payai%2ffacilitator ; https://www.x402scan.com/facilitators ; https://github.com/x402-foundation/x402

### Gaps
Funding; team beyond founder; migration terms of the 2025-11-18 token swap; project Farcaster account; PayAI revenue; Arbitrum/Avalanche/Sei/X Layer/SKALE volume (not on x402scan).

---

# PROFILE 2: Heurist ($HEU)

### One-line
A crypto-and-AI company that began as a decentralized GPU inference network (2023 to 2024) and now sells pay-per-call crypto data and agent tools (Heurist Mesh), a crypto research agent (Ask Heurist) and, since Aug 2026, a stock-research desk (Heurist Finance); it runs an x402 facilitator on Base that carries almost no traffic today. Operator: Heurist AI Inc. ([Terms](https://heurist.ai/terms)).

### x402 role
Seller/resource server (Mesh x402 gateway: "Base, Solana, and XRPL", every tool indexed in Bazaar) ([heurist-mesh-x402 README](https://github.com/heurist-network/heurist-mesh-x402)); facilitator for its own and third-party traffic ([facilitator docs](https://docs.heurist.ai/x402-products/facilitator)); token experiment (x402 Vending Machine launchpad: 14-day USDC sale, graduation swaps raised USDC into HEU) ([docs](https://docs.heurist.ai/x402-products/vending-machine.md)); buyer tooling (x402 buyer and builder-code verification scripts, June 2026).

### Chains
- Facilitator `/supported` (2026-10-11): Base (v1+v2), X Layer (`eip155:196`), Stable (`eip155:988`), extension `builder-code` ([supported](https://facilitator.heurist.xyz/supported)). The docs page contradicts itself (lists X Layer as supported and "coming soon" in the same page).
- **Base is primary for x402**: all x402scan-tracked activity is Base. HEU itself lives on Ethereum (canonical), ZKsync Era and Base. Heurist Chain, a ZK Stack L2 for credits, was announced 2025-07-23 ([blog](https://heurist.ai/blog/scaling-the-agentic-economy-bringing-heurist-credits-to-the-heurist-chain)).

### Token
- **HEU**; Ethereum `0xec463D00aa4dA76fb112cD2e4AC1C6BeF02da6ea`, ZKsync Era `0xAbEc5eCBe08b6c02F5c9A2fF82696e1E7dB6f9bf`, **Base `0xEF22cb48B8483dF6152e1423b19dF5553BbD818b`** ([contract addresses](https://docs.heurist.ai/protocol-overview/contract-addresses.md)).
- Launch: "Trading opens December 9th at 4:00 AM UTC" 2024; 11% of the 1B max supply circulating on day 1; listed on Gate.io and MEXC, Aerodrome (Base) and PancakeSwap (ZKsync) ([launch post](https://heurist.ai/blog/announcement-heu-token-is-live)). Method: VC-backed ($2M) plus Gate IEO (Dec 6 to 8, 2024; CoinCodex shows $2.03M raised, AskSurf shows $30K: **conflict**) plus airdrop to testnet miners (50M HEU, snapshot 2024-07-19) ([CoinCodex](https://coincodex.com/ieo/heurist/), [AskSurf](https://asksurf.ai/hub/project/heurist)). First Base pool 2024-12-05 (Uniswap v3), Aerodrome 2024-12-09 ([GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/base/tokens/0xef22cb48b8483df6152e1423b19df5553bbd818b/pools)).
- Allocation: mining/staking 50% (3-month cliff, 120-month vest), treasury 16.7%, team and advisors 15% (3-month cliff, 24-month vest), private angels/VC 6% (same terms), testnet miners 5% ([tokenomics](https://docs.heurist.ai/protocol-overview/tokenomics.md)).
- Utility actually in the product: 20% bonus credits when paying with HEU ([credits](https://docs.heurist.ai/protocol-overview/credits.md)); staking on Base (stHEU, 50% APR from emissions plus a share of API-credit revenue, 30-day unlock) ([staking](https://docs.heurist.ai/protocol-overview/stake.md)); Vending Machine graduations buy HEU; governance and Heurist Chain gas are stated, not verified. **Real work: partial/optional.** x402 payments settle in USDC; HEU is not needed for them.

### Team
- **Jiewen Wang**, "Founder", and **Tao He**, "Co-Founder": named by the AskSurf aggregator only (**unconfirmed**) ([AskSurf](https://asksurf.ai/hub/project/heurist)). The October 2024 whitepaper is credited to "Heurist Team" and names no individuals ([whitepaper PDF](https://github.com/heurist-network/whitepaper/blob/main/Heurist_Whitepaper.pdf)), and no other official page I could reach names them. No handles confirmed.
- **Frank He**, "Co-Founder and Engineering Lead at Heurist": quoted in Heurist's own post (2025-09-23) ([Medium feed](https://medium.com/feed/@heuristai)). Possibly the GitHub user **tsubasakong** (GitHub name "Frank", self-declared X **@gpt3_eth**; commits to Heurist repos; 2 in window) but no official source ties the two: **unconfirmed**.
- **wjw12** (GitHub name "JW", bio "Web3 / AI"): main public committer, 23 of 41 commits in the window; identity not stated.
- **Balraj** (GitHub **balrajsingh165**, company "Heurist AI", "Backend & Infrastructure Engineer; AI agents, x402 payments"; self-declared X **@drhinofficial**): 10 commits 2026-04-22 to 2026-06-15, 372 lifetime in the agent framework.
- **mridul** (**rexdotsh**, self-declared X **@rexmkv**): 4 commits Apr to May 2026 (176 lifetime). **Kevin Peng** (**kays0x**, bio "vibing @heurist-network", self-declared X **@kayslitt**): first public commit 2026-08-28. External: punkpeye (Glama).
- "RvalReal": byline of the 2024 funding post (pseudonym). Founders partly doxxed via third-party; engineers mostly pseudonymous. Joins/departures: no announcements; Balraj and rexdotsh stop committing publicly in Jun/May 2026, Kevin Peng appears Aug 2026 (inferences only).
- Farcaster: **@heurist** (fid 1357358, "Ask Heurist", connected X heurist_ai), **@heurist-ai** (fid 318728) ([Warpcast](https://client.warpcast.com/v2/user-by-username?username=heurist)).

### Track record and pivots (dated)
- 2023-07-30 GitHub org created; 2024-03-20 testnet mining; 2024-04-03 Aethir partnership; 2024-07-15 "Mining Season 2: From POW to DePIN"; products Heurist Imagine (AI images), Pondera, Heurist Search.
- 2024-11-14 raises $2M for a "decentralized AI cloud"; 2024-12-09 HEU live; 2024-12-20 Agent Framework (now 830 stars).
- 2025-04-17 Heurist Mesh; 2025-05-29 Deep Research; 2025-07-15 A2A/Linux Foundation tie-in; 2025-07-23 Heurist Chain and onchain credits; 2025-07-31 Google Cloud Startup Program, $350K; 2025-09-23 confidential MCP servers with Oasis.
- 2025-10-10 `heurist-mesh-x402`; 2025-10-24 x402 Vending Machine; **2025-11-07 first facilitator transactions on Base**; 2025-12-04 Caesar research agent in Mesh.
- 2026-04-06 Ask Heurist; 2026-06-03 FasterClaude (coding-model API) accepts Heurist credits; **2026-08-01 Heurist Finance, AI research desk for stocks** (Claude on Amazon Bedrock AgentCore); 2026-09-02 Mesh adds Robinhood Chain. Docs also list "Heurist Digital Assets (Beta)", a "regulated platform for tokenizing AI startup equity" (undated; site returned HTTP 503 on 2026-10-11) ([blog index](https://heurist.ai/blog), [docs intro](https://docs.heurist.ai/introduction.md)).

### Trend-hopping score: 4 / 5
GPU DePIN, agent framework, MCP/tool marketplace, ZK chain, ERC-8004 and x402 payment rails, token launchpad, equity tokenization, crypto research agent, then US stocks and Robinhood Chain in 2026. A real product shipped for almost every narrative, but the focus changes every 3 to 6 months and x402 is one rail among several.

### Funding
- **$2M pre-seed announced 2024-11-14**: Amber Group, Contango Digital, Manifold Trading, Selini Capital, X Ventures, Sharding Capital, Blue7 Capital, Mozaik Capital, Zephyrus Capital, Origin Capital, Steroids Capital, DCF God, plus unnamed angels; no lead named ([Heurist post](https://heurist.ai/blog/decentralized-ai-cloud-heurist-raises-2m), [TechFlow](https://www.techflowpost.com/en-US/newsletter/64949), [CoinCarp](https://www.coincarp.com/fundraising/heurist-preseed/)).
- Gate IEO Dec 2024 (amount disputed above); Google Cloud Startup Program (Scale tier), $350K support, 2025-07-31; no round announced since.

### Product and traction
- Mesh landing: 40 agents, 100 tools, 25 data providers (undated, undefended) ([mesh.heurist.ai](https://mesh.heurist.ai)); agent framework 830 stars; Ask Heurist on web, Base App, Farcaster (81 followers on its bot account), Telegram; Heurist Finance live at finance.heurist.ai with 20+ skills.
- **x402 facilitator (x402scan, Base)**: lifetime 7,967,176 tx / $30,160 (4,833 buyers, 1,077 sellers); monthly tx Nov 2025 2.50M, Dec 5.14M, Jan 2026 324K, Feb 439, Mar 500, Apr 976, May 351, Jun 2,195, Jul 2,573, Aug 23, Sep 52, Oct (11 days) 9; window total 5,997 tx / $59; last tx 2026-10-08 ([x402scan](https://www.x402scan.com/facilitators)). Average ticket $0.004: almost certainly automated micro-flows, cause undocumented. All eight live signer addresses are in x402scan's registry, so the collapse is not a tracking gap.
- Vending Machine (`vending-machine.heurist.xyz`) returned HTTP 522 and the Digital Assets site HTTP 503 on 2026-10-11; repo last pushed 2025-11-21.

### Last six months (2026-04-11 to 2026-10-11)
- 04-06 Ask Heurist launch (five days before the window); 06-03 FasterClaude on Heurist credits; 06-18 x402 buyer/builder-code scripts; 06-27/29 XRPL x402 routes with cross-currency settlement (RLUSD); 08-01 Heurist Finance; 09-02 Mesh token resolver/trending add Robinhood Chain; 09-14 to 09-26 `video-ai` repo (agent-made videos, prepared for MIT release); 09-15 InFlow seller discovery and payments in the x402 gateway ([GitHub](https://github.com/heurist-network), [Medium](https://medium.com/feed/@heuristai)).
- Public commits (10 repos): Apr 3, May 11, Jun 9, Jul 3, Aug 1, Sep 14 = 41 (wjw12 23, balrajsingh165 10, rexdotsh 4, tsubasakong 2, kays0x 1, other 1); commits in 17 of 26 ISO weeks (by repo: heurist-agent-framework 18, video-ai 11, heurist-mesh-x402 10, gpt-search-web 2; the other repos had none); no GitHub releases; last public commit 2026-09-26. Medium posts inside the window: 2 (06-03, 08-01).

### Pace verdict
Slow in public, moderate in product. 41 public commits in six months (about 1.6 a week, over 80% of them in May, June and September) and no tagged releases is well below what a small AI-assisted team ships in public; two launches inside the window (FasterClaude link-up, Heurist Finance, with Ask Heurist days earlier) is respectable but spread over unrelated products, and the closed-source facilitator shows no visible maintenance. For scale, PayAI shipped 12 npm releases in the same period and the x402 reference repo commits 67 to 115 times a month.

### Direction
Stated: facilitator "automatic conversion of USDC revenue into a project's native token... Coming Soon" and "BNB Chain and X Layer coming soon" ([docs](https://docs.heurist.ai/x402-products/facilitator)). Shipping record: X Layer and Stable chain are now in `/supported`; no sign of token conversion; effort has moved to stock research, finance skills and Robinhood Chain. x402 will likely stay a payment option for Mesh rather than a product.

### Competitors
For facilitation: Coinbase CDP (90.4% of Base 30d tx), PayAI, FluxA, Primer. For paid crypto data over x402: other API sellers in Bazaar (for example Nansen's API appears among PayAI's top merchants). Coinbase and FluxA (not profiled here) are far ahead on live x402 volume; PayAI and Primer are profiled above.

### Green and red flags
- Green: named institutional investors; 3-year operating history; real products and an 830-star open-source framework; OFAC screening and builder-code support in the facilitator; HEU contracts and vesting published.
- Red: facilitator effectively dormant (about $59 moved in six months); 7.97M-transaction footprint is low-value automation; narrative changes every few months; founders only third-party named, no team page; Vending Machine and Digital Assets sites down on 2026-10-11; conflicting docs on chains; IEO figures disputed.

### Verdict
**Credible but small. Momentum: Slowing (x402 side Stalled).** Heurist is a real company with funded history and shipping habits, but its x402 facilitator is a rounding error and the strategy has moved to AI finance research. Expect HEU-linked news to be about Heurist Finance, credits and Robinhood Chain, not facilitation. **Follow monthly** (Medium feed), not daily.

### Tracking card
- Website https://heurist.ai | Docs https://docs.heurist.ai (llms.txt) | Blog https://heurist.ai/blog (no RSS) | Medium RSS https://medium.com/feed/@heuristai | Changelog: none
- GitHub org heurist-network: `heurist-agent-framework`, `heurist-mesh-x402`, `heurist-mesh-mcp-server`, `x402-vending-machine`, `heurist-finance`, `video-ai`
- X @heurist_ai (official: linked from docs and GitHub org). People: @drhinofficial (Balraj), @rexmkv (mridul), @kayslitt (Kevin Peng), @gpt3_eth (tsubasakong, unconfirmed role). Farcaster @heurist (1357358), @heurist-ai (318728). LinkedIn linkedin.com/company/heurist-ai. Telegram t.me/heurist_ai. Discord discord.com/invite/heuristai
- Token: Base `0xEF22cb48B8483dF6152e1423b19dF5553BbD818b`; staking (Base) `0xfa13536bc4181db19fe93da82115f43f5c95761c`; Vending Machine (Base) `0xca85edab3ede15059fdabf27d861a942196ccccf`
- x402scan id `heurist` (Base addresses include `0xb578b7db22581507d62bdbeb85e06acd1be09e11`, `0x021cc47adeca6673def958e324ca38023b80a5be`, `0x3f61093f61817b29d9556d3b092e67746af8cdfd` and five more); facilitator https://facilitator.heurist.xyz
- Dune: https://dune.com/hashed_official/x402-analytics (lists Heurist)

### Sources (accessed 2026-10-11)
https://docs.heurist.ai/llms.txt ; /introduction.md ; /protocol-overview/tokenomics.md ; /credits.md ; /stake.md ; /contract-addresses.md ; /heurist-mesh/overview.md ; /x402-products/facilitator ; /x402-products/vending-machine.md ; https://heurist.ai ; https://heurist.ai/blog ; https://heurist.ai/blog/announcement-heu-token-is-live ; https://heurist.ai/blog/decentralized-ai-cloud-heurist-raises-2m ; https://heurist.ai/terms ; https://mesh.heurist.ai ; https://medium.com/feed/@heuristai ; https://facilitator.heurist.xyz/supported ; https://www.coingecko.com/en/coins/heurist ; https://coincodex.com/ieo/heurist/ ; https://asksurf.ai/hub/project/heurist ; https://www.techflowpost.com/en-US/newsletter/64949 ; https://www.coincarp.com/fundraising/heurist-preseed/ ; https://github.com/heurist-network (REST API) ; https://github.com/heurist-network/whitepaper (PDF, text extracted locally) ; https://www.x402scan.com/facilitators ; https://client.warpcast.com/v2/user-by-username?username=heurist

### Gaps
Cause of the Nov 2025 to Jan 2026 transaction burst; official team page; whether Frank He is tsubasakong; IEO amount; Heurist Chain live status; Digital Assets regulatory status; HEU staking participation; Mesh x402 usage (only visible if settled through other facilitators).

---

# PROFILE 3: Meridian ($MRDN)

### One-line
An anonymous-team payments layer run by a Swiss association (Zug) that settles x402 payments through its own proxy-facilitator contracts on 19 mainnets, sells AI-model access through an x402 "decentralized inference router", and pays $MRDN cashback on Base volume ([Terms](https://mrdn.finance/terms), [docs](https://docs.mrdn.finance), [homepage](https://mrdn.finance)).

### x402 role
Facilitator (proxy architecture: payer wallet to Meridian facilitator contract to recipient, with onchain fee accounting; docs call it "a layer built on top of Coinbase's infrastructure"); seller (Meridian Inference router); wallet/payment UI (Mpay gasless transfers, Command Centre dashboard); token experiment (cashback emissions) ([overview](https://docs.mrdn.finance/index.md), [inference](https://docs.mrdn.finance/inference/overview.md)). Listed on x402.org under "Infrastructure & Tooling", not "Facilitators" ([ecosystem data](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/meridian)).

### Chains
- Live `/v1/supported` (2026-10-11), x402 v1 only, schemes `exact` and `upto`: arbitrum, arc, avalanche, **base**, bot-chain, bsc, ethereum, hyperevm, ink, megaeth, monad, optimism, polygon, robinhood, sei, solana, tempo, unichain, worldchain (+ testnets) ([supported](https://api.mrdn.finance/v1/supported)). Homepage says "19 settlement chains".
- **Base is the economic centre**: the 1% protocol fee and the MRDN cashback apply to x402 transactions on Base only ([tokenomics](https://docs.mrdn.finance/tokenomics.md)). x402scan sees only Base for Meridian (first tx 2025-11-26).

### Token
- **$MRDN**, 1,000,000,000 supply. **Base `0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6`**; Robinhood Chain `0xbaabcb1800c539a58a46035d3982403a37fd6d5d` ([CoinGecko](https://api.coingecko.com/api/v3/coins/list?include_platform=true)).
- Launch: first Base liquidity pools 2025-09-16 (Aerodrome Slipstream MRDN/USDC, then Uniswap v4 pools) ([GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/base/tokens/0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6/pools)); Robinhood Chain pool first seen 2026-07-31 ([DexScreener](https://api.dexscreener.com/latest/dex/tokens/0xbaabcb1800c539a58a46035d3982403a37fd6d5d)). Method not documented (no fair-launch or Clanker statement); tokenomics list a 1% "Closed Round" (10M, "to boot strap initial liquidity pool") and a 1% airdrop to "uOS" holders.
- Allocation: 70% cashback emissions, 10% treasury, 10% team (**burned**), 5% liquidity/listings, 3% Pool2 (**burned**), 1% closed round, 1% uOS airdrop; burn tx is linked on Basescan (`0xe2c36b89...c9e24`) ([tokenomics](https://docs.mrdn.finance/tokenomics.md)).
- Utility: cashback paid in MRDN on Base x402 payments at a rate of 2% x e^(-13.9e-9 x cumulative volume), capped at $5 per transaction, self-payments excluded; "future governance"; "real yield" from the 1% fee. **Real work: it is the incentive that pays users to route volume through Meridian, not something the product needs.**

### Team
- No named people on any official page. Entity: **Meridian Association**, "established under Swiss law", seat Canton of Zug ([Terms](https://mrdn.finance/terms)).
- GitHub org **meridian-protocol** (created 2025-07-31; 5 repos, at most 1 star each). Commit authors on `meridian-protocol/demo`: **dolphinman7777** (display name is a dolphin emoji, self-declared X **@_dolphin_man_**; also owns the earlier `meridian` repo, "Meridian Protocol: The staked-access protocol for x402 payments", and the uOS repos) multiple commits Sep 2025 to Jul 2026; **beskay** ("Smart contract engineer", self-declared X **@beskay0x**, Farcaster **@beskay** fid 322676 with the same X account connected; blog beskay.com; repos `eip3009-forwarder`, `meridian-permit2-demo`) 2 commits Jul 2026; **pinkie-ai** ("pinkie", no bio; 2 contributions to upstream x402; the org's x402 and x402scan forks carry its commits) ([GitHub](https://github.com/meridian-protocol), [Warpcast](https://client.warpcast.com/v2/user-by-username?username=beskay)). All pseudonymous; employment status of beskay (contractor vs staff) unknown.
- Joins/departures: nothing public. Telegram t.me/mrdnfinance.

### Track record and pivots (dated)
- 2024-12-16 dolphinman7777 forks ElizaOS as "eliza-uos: Autonomous agents for everyone / Universal Operating System" (uOS, a Solana token); 2025-04-01 to 04-05 a Solana-to-Base uOS migration tool (Merkle claims) and an LP staking dashboard were built ([uOS-migration](https://github.com/dolphinman7777/uOS-migration)).
- 2025-07-13 `meridian` repo: "staked-access protocol for x402 payments"; 2025-09-16 MRDN pools on Base, with a 1% uOS airdrop; 2025-11-26 first facilitator tx visible on x402scan; 2025-12-10 x402scan fork.
- 2026: Circle Gateway nanopayments ("Completed" on roadmap), inference router (suppliers Venice, Surplus, AntSeed), `pay.mrdn.finance` gasless transfers; 2026-07-31 MRDN on Robinhood Chain; planned mrUSD stablecoin via M0 ("Q2 to Q4 2026") ([roadmap](https://docs.mrdn.finance/roadmap.md)).
- **Unconfirmed**: the uOS to Meridian lineage is **inferred** (shared GitHub account across both projects plus the "uOS Airdrop" line in tokenomics); Meridian itself does not state it.

### Trend-hopping score: 4 / 5
ElizaOS agent token (Dec 2024), x402 staked access (2025), cashback facilitator, AI inference router, stablecoin plan and Robinhood Chain token in 2026. Products exist at each step (a working API with 25 network names and a model catalog) but each step rides the current theme and the facilitator volume is incentive-shaped.

### Funding
No evidence of outside funding; no investors named. The 1% "Closed Round" (10M MRDN) is the only external allocation and its size/price is undisclosed ([tokenomics](https://docs.mrdn.finance/tokenomics.md)).

### Product and traction
- x402scan (Base): lifetime 148,129 tx / $3.79M (average $25.55 per tx) with only 68 buyers and 65 sellers; last 30 days 3,415 tx / $129,224 from 14 buyers and 14 sellers, i.e. 0.2% of Base tx but **18.4% of Base facilitator USD**; six-month window 82,797 tx / $2.06M ([x402scan](https://www.x402scan.com/facilitators)). Monthly Base tx: Dec 2025 4.9K, Jan 18.0K, Feb 18.0K, Mar 18.2K, Apr 19.9K, May 22.2K, Jun 16.7K, Jul 12.0K, Aug 8.4K, Sep 8.7K; USD peaks May 2026 $751K, down to $145K in Sep.
- Ten to fifteen wallets producing about $25 payments, with a 2% cashback token behind them, looks like incentive farming or closed-loop flows (**inference, not proven**). Daily buyers are 6 to 8 on the biggest days.
- Inference: "400+" models, 3 suppliers; usage not published. Docs have a Command Centre (analytics, balances, refunds, marketplace fees) and Circle Gateway batched payments.

### Last six months (2026-04-11 to 2026-10-11)
- Public GitHub: 3 commits (07-06 viem-only x402 reference demo and 07-12 Solana demo by beskay; 07-20 branding by dolphinman7777); no releases; last push 2026-07-21. Everything else is visible only through docs/API.
- 07-31 MRDN deployed on Robinhood Chain; roadmap shows Circle Nanopayments done, UMA arbitration "in progress", mrUSD "planned" (no sign of mrUSD shipping by 10-11).
- Base tx per month fell 61% from the May peak to September.

### Pace verdict
Opaque and slow in public: 3 commits and no changelog in six months, against weekly commits and monthly releases for small AI-assisted teams. The API and docs are broad and current (25 network names, inference registry), so work is probably happening in private repos, but nothing external confirms cadence. Looks slow in public and cannot be called "fast".

### Direction
Stated: UMA arbitration, Circle Nanopayments (done), mrUSD via M0 in "Q2 to Q4 2026", inference router growth, "x402 Innovation Initiative" (homepage link, no details). Shipping record: Robinhood token deployment and docs/API expansion; no mrUSD evidence three weeks before Q4 ends. Likely direction: AI-inference routing plus a stablecoin, with Base cashback as the user-acquisition subsidy.

### Competitors
Coinbase CDP and PayAI for facilitation; Circle Gateway nanopayments (Meridian wraps it); suppliers Venice, Surplus Intelligence, AntSeed for inference. On Base Meridian is 0.2% of tx and the only facilitator besides FluxA and Coinbase with a double-digit share of USD.

### Green and red flags
- Green: team and Pool2 tokens burned on-chain; real, documented API with 25 network names; Circle integration; Swiss association; many chains; open reference demo.
- Red: anonymous team; 1% protocol fee (about $0.25 on a $25 payment vs CDP's $0.001) funded or offset by token emissions; volume from 14 wallets; 70% of supply earmarked for cashback; minimal public commits; token on a second chain within 10 months; uOS to Meridian lineage never stated; mrUSD (planned Q2 to Q4 2026) not yet visible.

### Verdict
**Speculative. Momentum: Slowing.** Meridian is alive and technically broader than its public footprint suggests, but its Base x402 numbers are concentrated in very few wallets, shaped by a cashback token, and fading since May. Treat as a token-incentive experiment sitting on real plumbing; watch whether the inference router or mrUSD ever produces organic users. **Follow weekly** via x402scan and docs; low priority.

### Tracking card
- Website https://mrdn.finance | Docs https://docs.mrdn.finance (llms.txt, llms-full.txt) | Blog/RSS/changelog: none found
- GitHub org meridian-protocol (`demo`, forks of `x402`, `x402scan`); related personal repos github.com/dolphinman7777/meridian, /uOS-migration
- X @mrdn_finance (linked from site); people: @_dolphin_man_ (dolphinman7777), @beskay0x (beskay). Farcaster: @beskay (fid 322676); an account `@meridian` (fid 475721, empty bio) exists but is **unverified**. Telegram t.me/mrdnfinance. No Discord.
- Token: Base `0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6`; Robinhood `0xbaabcb1800c539a58a46035d3982403a37fd6d5d`
- x402scan id `mrdn`; Base addresses `0x3210d7b21bfe1083c9dddbe17e8f947c9029a584` (active) and `0x8e7769d440b3460b92159dd9c6d17302b036e2d6` (deprecated); API https://api.mrdn.finance/v1
- Dune: Meridian was not in the Hashed dashboard's chart legend I could read (page truncated).

### Sources (accessed 2026-10-11)
https://mrdn.finance ; https://mrdn.finance/terms ; https://docs.mrdn.finance/llms.txt ; /index.md ; /tokenomics.md ; /roadmap.md ; /inference/overview.md ; /inference/suppliers.md ; https://docs.mrdn.finance/llms-full.txt ; https://api.mrdn.finance/v1/supported ; https://github.com/meridian-protocol ; https://github.com/dolphinman7777 (REST API) ; https://github.com/beskay ; https://api.geckoterminal.com/api/v2/networks/base/tokens/0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6/pools ; https://api.dexscreener.com/latest/dex/tokens/0xbaabcb1800c539a58a46035d3982403a37fd6d5d ; https://www.x402scan.com/facilitators ; https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/meridian ; https://client.warpcast.com/v2/user-by-username?username=beskay

### Gaps
Team identity and structure; launch method of MRDN; size of the closed round; actual Meridian cashback paid; inference usage; whether the 14 wallets are independent; private repo activity; mrUSD status.

---

# PROFILE 4: Primer ($PR)

### One-line
A London-based, pseudonymous, one-developer shop that ships an x402 facilitator (Base, SKALE, Robinhood Chain, LitVM), SDKs, a browser wallet, agent-management and agent-trading tools, with a fair-launched token ($PR) that now lives on Robinhood Chain ([primer.systems](https://primer.systems)).

### x402 role
Facilitator and SDK/tooling (TypeScript and Python SDKs wrapping the official x402 SDK; WordPress plugin; Chrome wallet "Primer Pay"; validator and test-paywall tools); buyer/agent client (MultiClaw, Vault); trust/identity (AP2 registry, ERC-8004 repo); discovery/analytics (`x402view`, an "investment-focused directory of x402 projects and tokens" updated by a GitHub Action); token experiment (adaptive-burn hook) ([x402 README](https://github.com/Primer-Systems/x402), [x402view](https://github.com/Primer-Systems/x402view)).

### Chains
- Live `/supported` (2026-10-11): Base (v1+v2), Base Sepolia, SKALE Base, Robinhood Chain (`eip155:4663`), Robinhood testnet, LitVM LiteForge; live `/supported` lists only scheme `exact` (docs also claim `upto` and `batch-settlement`: a mismatch); ERC-20 beyond EIP-3009 via Permit2 and "Prism" contracts ([supported](https://x402.primer.systems/supported), [docs](https://docs.primer.systems/facilitator.html)).
- **Base is the only chain x402scan can see** and where all tracked volume sits (first tx 2025-12-14), but the project's own emphasis since July 2026 is Robinhood Chain ("first x402 facilitator on Robinhood Chain" 2026-07-05).

### Token
- **$PR**, now on **Robinhood Chain `0x3bbfDBC9c6DCB95577FEE16eEd10f0bC2856a03D`** (first Uniswap pool 2026-09-18 per DexScreener; site says migrated 2026-08-14). **Launched December 2025 on Base** as a "fair launch... no private sale, no public sale, no VCs"; 600,000,000 initial supply; 305,721,952 burned on 2026-04-17 (51% reduction, leaving 294,278,048); 1:1 Base to Robinhood bridge launched 2026-07-13 ([PR token docs](https://docs.primer.systems/pr-token.html), [update log](https://primer.systems)). **Base-era contract address: not located.** An unconfirmed candidate "PR" token with Uniswap v4 pools on Base (created 2026-02-05 to 2026-03-21) is `0x2357110f5f0c5344eef75966500c75116a4aa153` per GeckoTerminal search; I could not tie it to Primer.
- Mechanics: Uniswap v4 "Adaptive Burn" hook (introduced 2026-03-21): burn on buys, sell-side ETH into a Buyback Vault that buys and burns PR; burn rate 0 to 5%, set by the team "informed by community governance"; staking v1 (2026-09-19: wrap PR to stPR for a share of buyback rewards); "Premium app features unlock with PR holdings"; $PR-staked relays in a privacy-network design only.
- **Real work: partial**: value accrual (burn, buyback, staking) and feature gating, not needed to use the facilitator.

### Team
- **Unconfirmed**: no individuals named; "Based in London, England"; team "active in digital assets since 2013" (self-description) ([site](https://primer.systems)).
- GitHub org **Primer-Systems** (created 2025-12-11); sole human committer **primersystems-dev** (no name/bio/X; 40 public commits in the window); `x402` repo also shows 16 contributions from the GitHub account `claude`, consistent with AI-assisted coding ([GitHub](https://github.com/Primer-Systems/x402)). X **@primer_systems** and Telegram t.me/primer_HQ are linked from the site. Pseudonymous/anonymous. Joins/departures: none visible. (The Farcaster account "primer", bio "Coming Soon...", is unverified and probably unrelated.)

### Track record and pivots (dated)
No earlier projects found; the brand appears 2025-12-11.
- 2026-01: x402 SDK v0.3 to v0.4 (x402 v2, Python), Primer Pay wallet (01-27), listed on x402.org (01-29). 02-01 OpenClaw integration (xClaw02, ERC-800Claw skills); 02-13 SF x402 Agentic Commerce Hackathon submission; 02-19 MultiClaw v1.
- 03-12 SKALE Base L3; 03-21 Adaptive Burn; 03-24 Bittensor integration. 04-10 WordPress plugin; 04-17 51% burn.
- 05-15 batch settlement; 05-26 PAYLOAD agent game; 06-06 new website; 06-09 NONOS partnership; 06-19/25 SDK v1.0.0, facilitator v1.4 (Permit2) and v2.0.0 (smart wallets).
- 07-05 first facilitator on Robinhood Chain; 07-07 Prism ERC-20 contracts; 07-13 bridge; 08-07 Vault (agentic RWA/token trading on Robinhood Chain); 08-14 PR migrated; 08-27 Circle Alliance Program; 09-10 Sleuth Intel, 09-16 1Claw, 09-30 Blocktronics partnerships; 09-19 PR Staking v1 ([update log](https://primer.systems)).

### Trend-hopping score: 3 / 5
x402 is the constant (facilitator + SDK since day one) and a real product ships for every hop, but the add-ons track the news cycle quickly: OpenClaw, ERC-8004/AP2, Bittensor, privacy architecture, Robinhood Chain RWA trading, and an investment-style x402 token directory. Leans toward 4 on the newest Vault/RWA turn.

### Funding
No evidence of outside funding; the project says "No VCs. Entirely community-controlled." No grants found (SKALE docs listing 2026-04-09 and Circle Alliance Program membership 2026-08-27 are partnerships, not funding).

### Product and traction
- x402scan (Base): lifetime 39,292 tx / $8,960; last 30 days 5,763 tx / $1,508 (96 buyers, 28 sellers); six-month window 37,987 tx / $8,676. Monthly tx: Dec 2025 99, Jan 95, Feb 26, Mar 14, Apr 4,932, May 9,449, Jun 5,791, Jul 5,572, Aug 5,997, Sep 5,403 ([x402scan](https://www.x402scan.com/facilitators)). Flat at 5 to 6K a month; 0.3% of Base facilitator tx. The site's own activity counters are blank.
- Packages: npm `@primersystems/x402` 1.0.0 (2026-06-22) and 1.1.0 (2026-07-05), PyPI `primer-x402`; Chrome Web Store and WordPress plugin listings; no download numbers published.

### Last six months (2026-04-11 to 2026-10-11)
- Dated items from Primer's update log: see timeline above (33 dated items from 04-17 to 09-30, about 1.4 a week).
- GitHub releases: MultiClaw v2.2.0 (04-21), v2.2.2/v2.3.0/v2.3.1 (05-20), v2.4.0 (06-28), v2.5.0 (07-20), v2.6.0 (07-21); Vault v0.1.0 (08-07), v0.2.0/v0.2.1 (08-24/25), v0.3.0 (09-03), v0.4.0/v0.4.1 (09-25), v0.4.2 (10-02); Primer Pay v0.6.0 (08-21) ([GitHub releases](https://github.com/Primer-Systems/vault/releases)).
- Public human commits (primersystems-dev): Apr 12, May 8, Jun 4, Jul 3, Aug 9, Sep 3, Oct 1 = 40, in 16 of 26 ISO weeks, last 2026-10-02; the facilitator source is not public. By repo (human): multiclaw 13, primer-pay-wordpress 11, vault 8, x402 2, uniswap-v4-hooks 2, ap2-registry 2, primer-pay 1, multiclaw-skills 1. `agent-manifold` (272 bot commits) and `x402view` (about 2,470 price-update commits) are automation, not development.

### Pace verdict
Fast on releases, light on public commits. Roughly 1.4 dated updates a week and a tagged release every one to two weeks (15 GitHub releases: MultiClaw 7, Vault 7, Primer Pay 1; plus 2 npm SDK releases) beats the "monthly releases, weekly commits" benchmark for an AI-assisted small team. But one anonymous developer, a closed facilitator, and flat usage mean speed is not translating into adoption.

### Direction
Stated: privacy network ("3-hop onion routing through $PR-staked relays", Federated Composers, Dark Pool, decoy traffic), agent trading tools, staking and buybacks, more chains. Shipping record: Vault, staking, bridge, chain additions and partnerships are real; the privacy network is architecture text only (no status given) ([docs](https://docs.primer.systems/facilitator.html), [homepage](https://primer.systems)). Direction is drifting from x402 plumbing to token-linked trading/agent apps on Robinhood Chain.

### Competitors
Coinbase CDP (Base); PayAI, OpenFacilitator, Mogami, x402.rs, OpenX402, thirdweb on EVM; Coinbase's own agentic wallet versus Primer Pay/MultiClaw. Primer is smaller than all of them by Base volume but is first-mover on Robinhood Chain, SKALE and LitVM.

### Green and red flags
- Green: the fastest release cadence of the group; MIT-licensed SDK; Permit2/ERC-20 breadth; clear dated changelog; token supply burn executed and documented; admits "no VCs"; early on new chains.
- Red: anonymous, single visible developer; token-forward (burn hooks, staking, investment directory); token migrated off Base and Base-era contract unlocated; usage tiny and flat; narrative-following; privacy architecture claimed before built; fee model undisclosed ("Network fees (USDC, ETH)" go to buybacks and staking).

### Verdict
**Credible but small. Momentum: Steady** (output high, usage flat). Primer is a hard-working one-person operation shipping weekly, but the interesting product work is now token-linked apps for Robinhood Chain rather than x402 infrastructure, and Base usage is a rounding error. Expect more releases and partnerships; do not expect facilitator adoption to change on its own. **Follow weekly** via the update log and GitHub releases.

### Tracking card
- Website https://primer.systems (dated update log on homepage; no RSS) | Docs https://docs.primer.systems | Blog/changelog: homepage log
- GitHub org Primer-Systems: `x402`, `vault`, `multiclaw`, `primer-pay`, `primer-pay-wordpress`, `uniswap-v4-hooks`, `ap2-registry`, `agent-manifold`, `x402view`
- X @primer_systems (linked from site). Telegram t.me/primer_HQ. No Discord. Farcaster: none verified.
- Token: Robinhood Chain `0x3bbfDBC9c6DCB95577FEE16eEd10f0bC2856a03D`; hook `0xc3C15bDe8bfb101bbDb36932B2222791F5f1c0Cc`
- x402scan id `primer`; Base address `0x37dfb4033d5dd98fd335f24d0d42e8fe68d587d6`; facilitator https://x402.primer.systems
- Dune: Primer was not in the Hashed dashboard's chart legend I could read (page truncated).

### Sources (accessed 2026-10-11)
https://primer.systems ; https://docs.primer.systems ; /facilitator.html ; /pr-token.html ; https://x402.primer.systems/supported ; https://github.com/Primer-Systems (REST API: repos, releases, contributors, commits) ; https://github.com/Primer-Systems/x402view ; https://registry.npmjs.org/@primersystems%2fx402 ; https://api.coingecko.com/api/v3/coins/list?include_platform=true ; https://api.dexscreener.com/latest/dex/tokens/0x3bbfDBC9c6DCB95577FEE16eEd10f0bC2856a03D ; https://api.geckoterminal.com/api/v2/search/pools?query=primer&network=base ; https://www.x402scan.com/facilitators

### Gaps
Who is behind Primer; Base-era PR contract; fee schedule; facilitator source/uptime; real user counts; privacy network status; whether the London claim is a registered company (deliberately not searched).

---

# PROFILE 5: AnySpend by B3 ($ANY)

### One-line
AnySpend is B3's cross-chain payments, swap and fiat on-ramp product; it also runs a small x402 facilitator (`mainnet.anyspend.com/x402`) that was busy in Nov 2025 to Jan 2026 and has been near-idle since ([CoinGecko text](https://api.coingecko.com/api/v3/coins/anyspend), [B3 docs](https://docs.b3.fun/llms.txt)).

### x402 role
Facilitator as a side feature of a payments product (x402 middleware packages, demo repos; `b3-fun/anyspend-x402` is a fork of Coinbase's x402 "powered by AnySpend").

### Chains
Live `/supported` (2026-10-11): abstract, arbitrum, avalanche, **base**, bsc, ethereum, optimism, polygon, solana; x402 v1, scheme `exact` only ([supported](https://mainnet.anyspend.com/x402/supported)). Base was where x402scan saw it (Base addresses first used 2025-11-03; the Solana address is marked deprecated).

### Token
**$ANY, Base `0xC17dda248E2D50fC006d8fEbb5A406dd31972712`** (CoinGecko categories: Base Native, x402 Ecosystem). First DEX pool 2025-10-10 (Aerodrome Slipstream ANY/WETH, GeckoTerminal); launch method and stated utility: not found. It is separate from B3's $B3 token (Base, 100B supply), whose docs do not mention AnySpend ([B3 tokenomics](https://docs.b3.fun/protocol/tokenomics)). Real work in the facilitator: none documented.

### Team
Parent B3 (b3.fun) names three co-founders: Viktoriya Hying (Co-Founder & COO), Daryl Xu (Co-Founder & CEO) and Sean Geng (Co-Founder & CTO); the page links no personal X or LinkedIn profiles, only the company LinkedIn (linkedin.com/company/b3-labs-inc), and lists Anyspend among B3's products ([b3.fun](https://b3.fun)). AnySpend's own team is **unconfirmed**. GitHub org **b3-fun** (created 2024-04-27, 17 repos). `anyspend-x402` contributors include aqt-dev (68) and Trung Mai / mttrung (26; last commit 2026-02-04) beside upstream Coinbase authors. No X handles verified for individuals; project X **@anyspend** (linked from CoinGecko).

### Track record and pivots
B3's docs describe an "Open Gaming ecosystem" with a $B3 token on Base; AnySpend repos start in July 2025 (`anyspend-demo` 2025-07-19) and the x402 facilitator follows (`anyspend-x402` created 2025-10-30, first facilitator tx 2025-11-03, last push 2026-02-04). No other dated pivots found.

### Trend-hopping score: 3 / 5
Gaming ecosystem to cross-chain payments to an x402 side feature; payments is a coherent through-line and x402 is a natural extension.

### Funding
b3.fun shows a "Backed By:" heading with no names and states no rounds; B3's funding history was not otherwise researched because the search budget ran out (**unconfirmed**).

### Product and traction
x402scan: lifetime 521,040 tx / $140,701, 317 buyers and 71 sellers; Base monthly tx Nov 2025 134K, Dec 181K, Jan 2026 183K, Feb 3.3K, Mar 4.1K, Apr 4.0K, May 4.2K, Jun 1.6K, Jul 4.3K, Aug 2.2K, Sep 0; last tx 2026-08-17 ([x402scan](https://www.x402scan.com/facilitators)).

### Last six months
x402 side: no repo commits since 2026-02-04; endpoint still answers. Parent: `@b3dotfun/sdk` had 28 npm versions since 2026-04-11 (last 2026-08-14) and `b3os` 35 commits ([npm](https://registry.npmjs.org/@b3dotfun%2fsdk)). No team join/leave data.

### Pace verdict
Parent company ships; the x402 piece is stalled (about 4K Base tx a month, then zero) and below the "weekly commits, monthly releases" bar.

### Direction
No x402 roadmap found. Treat x402 as incidental to AnySpend payments.

### Competitors
Coinbase CDP, PayAI, Primer, FluxA on Base; all ahead on live volume today.

### Green and red flags
Green: live endpoint across 9 networks; real parent product. Red: x402 activity ended in August; fork-based x402 code idle since February; v1 only; token role undocumented; no team page.

### Verdict
**Credible but small (parent); x402 line Stalled.** Not worth following for x402 news; revisit only if AnySpend announces x402 v2 support. Follow: monthly at most.

### Tracking card
Website https://anyspend.com | Docs https://docs.b3.fun | GitHub org b3-fun (`anyspend-x402`, `b3os`) | X @anyspend | Token Base `0xC17dda248E2D50fC006d8fEbb5A406dd31972712` | x402scan id `anyspend`, Base address `0x179761d9eed0f0d1599330cc94b0926e68ae87f1` | Dune: not seen in the Hashed dashboard legend (page truncated).

### Sources (accessed 2026-10-11)
https://mainnet.anyspend.com/x402/supported ; https://www.coingecko.com/en/coins/anyspend ; https://api.geckoterminal.com/api/v2/networks/base/tokens/0xc17dda248e2d50fc006d8febb5a406dd31972712/pools ; https://github.com/b3-fun/anyspend-x402 ; https://b3.fun ; https://docs.b3.fun/protocol/tokenomics ; https://www.x402scan.com/facilitators

### Gaps
ANY launch method and utility; AnySpend-specific team; B3 funding; whether newer x402 work lives in private repos.

---

# PROFILE 6: Relai ($REL)

### One-line
"Payment infrastructure for autonomous AI agents": an x402 marketplace, payment links and Solana subscriptions product with a facilitator and a Solana token; its facilitator hostname does not respond and x402scan activity stopped on 2026-07-08 ([relai.fi](https://relai.fi)).

### x402 role
Facilitator, seller marketplace (pay-per-call endpoints in USDC), subscriptions and shielded payment links; token experiment.

### Chains
Facilitator page: Base, Avalanche, Polygon (EIP-3009), Solana (SPL), SKALE; "All transactions settle in USDC" ([facilitator page](https://relai.fi/relai-facilitator)). Registry shows Base and Solana first used 2026-01-23. **`facilitator.x402.fi` returned no response twice on 2026-10-11** while relai.fi loads; the facilitator dashboard showed "No data yet".

### Token
**$REL, Solana only**, 1B supply, "Fair launch & bonded DEX", 6-month linear vesting; team 18%, ops 10%, marketing 9%, ecosystem 4%, community 3% of a 50% "treasury" bucket; utility claimed: fee discounts when paying API fees in $REL, premium tiers, governance, 1 to 2% auto-burn, buyback and burn ([tokenomics](https://relai.fi/tokenomics)). **No contract address is published and I could not find it** (not in CoinGecko list; DexScreener search returned unrelated tokens). No Base contract. Launch date unknown.

### Team
**Unconfirmed.** Not named anywhere reachable; no GitHub found; contact addresses only (contact@, support@).

### Track record and pivots
**Unconfirmed.** Brand and facilitator appear 2026-01-23; no earlier history found.

### Trend-hopping score: 4 / 5 (low confidence)
Marketplace, privacy-shielded links, "Privacy Pools", Solana subscriptions, fair-launch token: many narratives on a short record; evidence is thin.

### Funding
None found.

### Product and traction
x402scan: lifetime 303,181 tx / $508,026 (Base 89,527 tx / $214,985; Solana 213,654 tx / $293,040), 1,098 buyers; Base monthly tx Mar 2026 46.0K, Apr 18.0K, May 12.0K, Jun 13.3K, Jul 81, Aug 0; last tx 2026-07-08 ([x402scan](https://www.x402scan.com/facilitators)).

### Last six months
Activity up to 2026-07-08, then nothing visible; site live with a 2026 footer. No GitHub, blog or changelog to count.

### Pace verdict
Cannot be assessed from public code; usage fell to zero within two months of July, which reads as stalled or abandoned.

### Direction
Whitepaper/roadmap links exist but their contents were not retrievable; nothing shipping is visible.

### Competitors
Coinbase CDP, PayAI, Primer, FluxA, OpenFacilitator.

### Green and red flags
Green: documented token terms; real volume at the peak ($215K on Base in 2026). Red: dead facilitator hostname; zero activity since July; no team, code or contract address; auto-burn and revenue-burn claims unverifiable.

### Verdict
**Speculative. Momentum: Stalled.** Do not follow.

### Tracking card
Website https://relai.fi | Facilitator https://facilitator.x402.fi (down) | X: none found | Token Solana (address not published) | x402scan id `relai`, Base address `0x1892f72fdb3a966b2ad8595aa5f7741ef72d6085`, Solana `4x4ZhcqiT1FnirM8Ne97iVupkN4NcQgc2YYbE2jDZbZn` | Dune: no.

### Sources (accessed 2026-10-11)
https://relai.fi ; https://relai.fi/tokenomics ; https://relai.fi/relai-facilitator ; https://facilitator.x402.fi/supported ; https://www.x402scan.com/facilitators

### Gaps
Token contract/launch date; team; whether x402.fi was moved to a new host.

---

# PROFILE 7: AurraCloud ($AURA) - short entry

### One-line
A one-visible-developer AI-tooling shop (MCP server hosting, then an x402 facilitator, now a Hyperliquid trading CLI and an "open inference gateway") whose x402 facilitator is dead; the $AURA token is from a Jan 2025 Virtuals launch.

### x402 role
Facilitator (dead) and seller (hosted MCP tools monetised with x402 micropayments on Base, per the Virtuals listing).

### Chains
Base (first tx 2025-10-05) and Solana (2025-10-30) while live. `x402-facilitator.aurracloud.com` no longer resolves (2026-10-11); x402scan marks it `deprecated`; last x402scan tx 2026-01-13 ([registry](https://raw.githubusercontent.com/Merit-Systems/x402scan/main/packages/external/facilitators/src/facilitators/aurracloud.ts)).

### Token
**$AURA, Base `0xdCaA5E062b2be18E52eA6ED7ba232538621dDC10`**, Virtuals Protocol agent #18336 "Aurra", created and launched 2025-01-08 (status AVAILABLE), described as "AI agent infrastructure for crypto-native applications. Host MCP servers... monetize with on-chain x402 micropayments on Base"; original X @AurraBot ([Virtuals API](https://api.virtuals.io/api/virtuals/18336), [CoinGecko](https://www.coingecko.com/en/coins/aurra-by-virtuals)). Method: Virtuals Protocol launch (per the Virtuals API, launched and LP created 2025-01-08 19:00 UTC). Utility in product: none documented. A second Virtuals launch "AURRA by Virtuals" on Robinhood Chain (2026-08-08, no socials) is **unverified** as theirs ([Virtuals API](https://api.virtuals.io/api/virtuals/131495)).

### Team
**Yahya** (GitHub **ya7ya**, self-declared X **@ya7ya**, company "@monemetrics"): the only committer to the AurraCloud org (52 commits in the window, last 2026-09-06). Project X **@AurraCloud** (set on the GitHub org). Farcaster: none found. Org created 2025-05-16.

### Track record and pivots
2025-01-08 Virtuals agent "Aurra"; 2025-05 Etherscan and Hyperliquid MCP servers; 2025-10 x402 facilitator; 2026-02 OpenBroker (Hyperliquid CLI, 29 npm releases since April, 1.13.0 on 2026-09-06); 2026-07-12 site now "the open inference gateway".

### Trend-hopping score: 4 / 5
Virtuals agent, MCP hosting, x402, Hyperliquid, inference gateway: a new theme about every 4 months, each with some code.

### Funding
None found (token launch via Virtuals only).

### Product and traction
x402scan lifetime 235,975 tx / $53,551 (14,170 buyers): Oct 2025 121.6K, Nov 113.8K, Dec 31, Jan 2. Nothing since.

### Last six months
x402 facilitator: none. OpenBroker: 29 npm releases, `agentic-x402` skill 0.4.0 (2026-08-27). Commits per month: Apr 13 (from 04-15), May 11, Jun 22, Jul 3, Aug 1, Sep 2 = 52 (open-broker 37, openbroker-monitoring 10, openbroker-plugin 4, agentic-x402 1); last commit 2026-09-06.

### Pace verdict
The developer ships fast (a release every 6 days on OpenBroker) but not on x402; the facilitator was abandoned within three months.

### Direction
Hyperliquid trading tools and an inference gateway, not x402.

### Competitors
Any Base facilitator; Coinbase CDP leads.

### Green and red flags
Green: named dev; real tools elsewhere. Red: facilitator offline; API key embedded in the facilitator URL design; token has no documented use; no team.

### Verdict
**Likely abandoned (as an x402 facilitator). Momentum: Dead for x402; company alive on other products.** Do not follow for x402.

### Tracking card
Site https://aurracloud.com | GitHub org Aurracloud (`open-broker`, `agentic-x402`) | X @AurraCloud, @AurraBot | Token Base `0xdCaA5E062b2be18E52eA6ED7ba232538621dDC10` | x402scan id `aurracloud` (deprecated), Base `0x222c4367a2950f3b53af260e111fc3060b0983ff`, `0xb70c4fe126de09bd292fe3d1e40c6d264ca6a52a`, `0xd348e724e0ef36291a28dfeccf692399b0e179f8`; Solana `8x8CzkTHTYkW18frrTR7HdCV6fsjenvcykJAXWvoPQW`.

### Sources (accessed 2026-10-11)
https://aurracloud.com ; https://github.com/Aurracloud (REST API) ; https://api.virtuals.io/api/virtuals/18336 ; https://www.coingecko.com/en/coins/aurra-by-virtuals ; https://registry.npmjs.org/openbroker ; https://www.x402scan.com/facilitators

### Gaps
Whether Monemetrics is the legal owner; token holders' utility; exact reason the facilitator was shut.

---

# PROFILE 8: CodeNut - short entry

### One-line
"Agentic vibe-coding platform for crypto" (describe a DApp, AI builds it for EVM or Solana) that added an x402 facilitator in Oct 2025; the facilitator has been unreachable since Jan 2026.

### x402 role
Developer platform plus facilitator ("CodeNut Pay") and payment links (x402Pay); listed on x402.org under Infrastructure & Tooling ([site](https://www.codenut.ai/x402), [ecosystem data](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data/codenut)).

### Chains
Docs: Base/Solana at `facilitator.codenut.ai`, X Layer at `/xlayer/`. x402scan: Base first tx 2025-10-13, Solana 2025-11-03; last tx 2026-01-27; marked `deprecated`. `facilitator.codenut.ai/supported` returned no response twice on 2026-10-11 and the pay page shows "Loading..." ([docs](https://docs.codenut.ai/guides/x402-facilitator), [pay.codenut.ai](https://pay.codenut.ai)).

### Token
**None found**: no mention on codenut.ai or docs, no CoinGecko or Virtuals entry.

### Team
None named. GitHub org **vibe-codenut** (created 2025-08-05, 5 repos, no commits after 2025-12-12). X **@codenut_ai** (site-linked). Farcaster **@codenut** (fid 1334477, bio matches the product, 1 follower, not cross-linked: probable).

### Track record and pivots
2025-08 org; 2025-10 facilitator; 2025-11-01 `cypherpunk-hack` (repo name suggests a hackathon entry); 2025-12-12 last docs push. No earlier projects found.

### Trend-hopping score: 3 / 5
Vibe-coding is the core; x402 was a plug-in during the Oct 2025 hype.

### Funding
None found.

### Product and traction
x402scan lifetime 477,922 tx / $110,037 (14,562 buyers): Nov 2025 333K, Dec 144K, Jan 2026 567. The website is still up (HTTP 307 to a live page).

### Last six months
Nothing public: zero commits in the window; no releases.

### Pace verdict
Stalled since December 2025.

### Direction
None stated for x402.

### Competitors
Any live Base facilitator.

### Green and red flags
Green: product site still live. Red: facilitator endpoint dead; no token, team, funding or code activity.

### Verdict
**Likely abandoned. Momentum: Dead** (for x402). Do not follow.

### Tracking card
Site https://codenut.ai | Docs https://docs.codenut.ai | GitHub vibe-codenut | X @codenut_ai | Farcaster @codenut (1334477) | Discord discord.gg/cU6RQhcxB9 | x402scan id `codenut` (deprecated), Base `0x8d8Fa42584a727488eeb0E29405AD794a105bb9b`, `0x87aF99356d774312B73018b3B6562e1aE0e018C9`, `0x65058CF664D0D07f68B663B0D4b4f12A5E331a38`, `0x88E13D4c764a6c840Ce722A0a3765f55A85b327E`.

### Sources (accessed 2026-10-11)
https://codenut.ai ; https://www.codenut.ai/x402 ; https://docs.codenut.ai/guides/x402-facilitator ; https://pay.codenut.ai ; https://github.com/vibe-codenut (REST API) ; https://www.x402scan.com/facilitators ; https://client.warpcast.com/v2/user-by-username?username=codenut

### Gaps
Whether a token exists unlisted; team; funding.

---

# Screened and not profiled (token-bearing or Base-capable facilitators below the "real volume" bar, or covered elsewhere)

| Project | Token | Base | x402scan lifetime tx (last tx) | Note |
|---|---|---|---|---|
| FluxA | none found (site, CoinGecko) | Base only; live | 2.70M ($660K); Base 30d 136,530 tx / $322,401; 2026-10-11 | Real volume, no token; its current signer `0x3be45f57...` is not in x402scan's registry, so tracked volume may understate ([facilitator](https://facilitator.fluxapay.xyz/supported)) |
| Ultravioleta DAO | none mentioned | yes (23 mainnets) | 39,213 (2026-10-10); Base 30d 25,487 | "0% fees"; no token found |
| Polymer | none found | yes | 58,013 (2026-10-09) | no token found |
| Treasure | $MAGIC (Base `0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43`) | Base only | 2,461 (2026-10-08) | too small |
| x402 Jobs | $JOBS (Solana `6cNcXWqYvK9nhD1TsjJ1ZH1KATXcaPaRJtZPHyVkJoBs`) | Base + Solana | 21,935 (2026-07-07) | too small; endpoint live |
| Kamiyo | $KAMIYO (Solana, pump.fun) | claims Base + Solana | not in x402scan | facilitator HTTP 503 on 2026-10-11 |
| WorldFun (AWE Network) | $AWE (Base `0x1b4617734c43f6159f3a70b7e06d883647512778`) | Base only | not in x402scan | endpoint live; no tracked volume |
| Elsa x402 (HeyElsa) | $ELSA (Base `0x29cc30f9d113b356ce408667aa6433589cecbdca`) | Base only | not in x402scan | endpoint live; no tracked volume |
| OpenFacilitator | $OPEN (Solana `cpbqtLWH8DkwuVYvKeVVjV9JowkFd8kkpo1vjCSopen`, pump.fun; CoinGecko says it "has stopped trading" on listed exchanges) | Base + Solana (+ Stacks per site) | 31,851 (2026-10-10); Base 30d 1,000 tx | Free, Apache-2.0, one maintainer (GitHub rawgroundbeef "Ben", no X set): 33 commits in May 2026, none after 2026-06-07; X @openfacilitator, Telegram t.me/OpenFacilitator ([site](https://www.openfacilitator.io), [CoinGecko](https://www.coingecko.com/en/coins/openfacilitator)) |
| AutoIncentive | $AIT (Solana, pump.fun mint `9QRknyCszLEmzgfEHuW4v8cygf4Hu5Dwc1LjgSaRpump`) | Base + Solana | not in x402scan | free public facilitator per ecosystem listing; link between token and facilitator not verified |
| Obol | $OBOL (Ethereum) | Base | 1,200 (2026-08-12) | too small; token is the Obol Network's, not facilitator-specific |
| Hydra Protocol | unverified (a "Hydra" token exists on Base `0x0c0db132c6c4f687b7f772e3514ae2a172cab2bb`, no link to the project found) | Base + Solana | not in x402scan | `api.hydraprotocol.org` returned no response on 2026-10-11 |
| three.ws, Figment | $THREE (Solana) / none | Solana only | 98,374 / 6.16M | no Base support, out of scope |

**x402.org ecosystem "Facilitators" category (28 entries; read from the source repo because `https://www.x402.org/ecosystem` returned 404 on 2026-10-11)**: profiled here: PayAI, Heurist, Primer. Excluded by assignment: Coinbase CDP, Corbits, Dexter, Mogami, OpenX402. Screened above: Elsa, Kamiyo, OpenFacilitator, AutoIncentive, Relai, Treasure, WorldFun, Ultravioleta DAO, Hydra Protocol. No Base support: Built on Stellar, Polygon Facilitator, SolPay (Solana), OpenZeppelin (plugin). Base-capable but no CoinGecko listing found by name: 0xArchive, 0xmeta AI, Bitrefill, fretchen.eu, GoPlausible, Kobaru, Nevermined. AurraCloud and AnySpend are not in that category at all; Meridian and CodeNut are listed under "Infrastructure & Tooling"; FluxA, Polymer, x402 Jobs, Cascade, Openmid appear only in x402scan's registry ([ecosystem data](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data), [x402scan registry](https://github.com/Merit-Systems/x402scan/tree/main/packages/external/facilitators/src/facilitators)).

Excluded by assignment (covered by other researchers): Dexter (28.0M lifetime tx), Daydreams (11.8M), Virtuals (1.99M), Questflow (474K), thirdweb (223K), x402.rs (703K), OpenX402 (710K), Mogami (23K), Corbits (203K) ([x402scan](https://www.x402scan.com/facilitators), [CoinGecko list](https://api.coingecko.com/api/v3/coins/list?include_platform=true), [x402.org ecosystem data](https://github.com/coinbase/x402/tree/main/typescript/site/app/ecosystem/partners-data)).

---

# Comparison table (all projects covered)

| Name | x402 role | Token (chain) | Seriousness | Momentum | Trend-hopping (1-5) | Follow |
|---|---|---|---|---|---|---|
| PayAI Network | Facilitator + discovery/SDK/billing | $PAYAI (Solana; no Base contract) | Serious builder | Steady | 2 | Daily |
| Heurist | Seller (Mesh), minor facilitator, token launchpad | $HEU (Ethereum, ZKsync, Base) | Credible but small | Slowing (x402 Stalled) | 4 | Monthly |
| Meridian | Facilitator + inference seller | $MRDN (Base, Robinhood) | Speculative | Slowing | 4 | Weekly, low priority |
| Primer | Facilitator + SDK/wallet/tools | $PR (Robinhood; Base-era contract not located) | Credible but small | Steady | 3 | Weekly |
| AnySpend (B3) | Facilitator, side feature | $ANY (Base) | Credible but small (x402 line) | Stalled | 3 | Monthly at most |
| Relai | Facilitator + marketplace | $REL (Solana) | Speculative | Stalled | 4 (low confidence) | No |
| AurraCloud | Facilitator (dead) + MCP seller | $AURA (Base, Virtuals) | Likely abandoned (x402) | Dead (x402) | 4 | No |
| CodeNut | Facilitator (dead) + dev platform | none found | Likely abandoned | Dead | 3 | No |
| Screened only: FluxA, Ultravioleta DAO, Polymer, Treasure, x402 Jobs, Kamiyo, WorldFun, Elsa, OpenFacilitator, AutoIncentive, Obol, Hydra | see table above | see table above | not scored | not scored | not scored | FluxA and Ultravioleta DAO worth a glance for Base volume |
