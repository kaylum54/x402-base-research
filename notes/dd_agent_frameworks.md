# Due diligence: agent frameworks and platforms on x402 (Daydreams, Virtuals Protocol, elizaOS)

Research date 2026-10-11. All "accessed" dates are 2026-10-11. "Last six months" means 2026-04-11 to 2026-10-11. No price or chart analysis. Anything I could not confirm is labelled "unconfirmed".

How the numbers were gathered:
- GitHub: `gh` CLI (commits, contributors, stats/commit_activity, stats/contributors, code and commit search).
- x402 usage: x402scan's own public tRPC API, called from the x402scan site in a browser (facilitators.bucketedStatistics, sellers.bazaar.stats.overall, transfers.list), and its facilitator source files on GitHub.
- Token facts: Base RPC (mainnet.base.org), Blockscout, CoinGecko API, GeckoTerminal API.
- WebSearch ran out of budget partway through. A few items (4Pillars, HTX, Bankless, CoinEx) come from search snippets only and are flagged. Crunchbase, RootData, CryptoRank, Dealroom and X were not reachable, so funding and X-post cadence have gaps. I did not try to get past the Cloudflare challenge on CryptoRank.
- The elizaOS "knowledge" repo holds daily logs, council notes and monthly summaries that are written by an automated LLM pipeline from Discord and GitHub. I used them for dates and context and treat them as secondary.

## Lead check (what held up)

| Lead | Result |
|---|---|
| Daydreams: agent framework | True, but deprecated by the team on 2026-02-06. |
| Daydreams: Router paid via x402 | True from Aug 2025 to about Feb 2026. `router.daydreams.systems` no longer resolves (NXDOMAIN on 8.8.8.8). |
| Daydreams: Lucid, agent commerce, own facilitator | Confirmed. The facilitator is live and tracked by x402scan. |
| Daydreams: $DREAMS on Base | Partly. It is Solana-native (pump.fun, 2025-01-19). The Base token is a Hyperlane copy deployed 2025-09-16. Starknet copy also exists. |
| Daydreams: team from Bibliotheca DAO, Realms, Loot | Confirmed for Loaf through commits (Eternum, Loot Survivor, Dojo). |
| Virtuals: Base launchpad, ACP | Confirmed. ACP is also an ERC-8183 draft. |
| Virtuals: x402 integration | Confirmed as an optional way to fund ACP jobs (code from 2025-10-31). Usage fell about 99% after April 2026. |
| Virtuals: PathDAO origin | Stated by CoinGecko only; I found no primary source. |
| elizaOS: ai16z to elizaOS, token on several chains incl. Base | Confirmed. Base token deployed 2025-10-09. |
| elizaOS: x402 plugin and Cloud | Confirmed (wallet plugin, registry plugin, Cloud facilitator, paid routes). |
| Missing from the leads | On 2026-08-05 the elizaOS founder declared the token dead and said the foundation is winding down. |

---

## 1. Daydreams (daydreamsai)

### One-line
Daydreams began in late 2024 as an open-source library for AI agents that play onchain games. It now describes itself as "commerce infrastructure for autonomous agents": a paid-agent SDK (Lucid Agents), a public x402 facilitator, and Task Market, a USDC bounty market on Base. The x402-paid LLM gateway (Dreams Router) appears to be offline. ([site](https://daydreams.systems), [README](https://github.com/daydreamsai/daydreams))

### x402 role
- Facilitator. `https://facilitator.daydreams.systems/supported` returned 200 on 2026-10-11 with x402 v2 `exact` and `upto` on Ethereum, Base and Base Sepolia, and `exact` on Solana ([live list](https://facilitator.daydreams.systems/supported)). x402scan tracks it as id `daydreams` ([source](https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/daydreams.ts)). The repo README also lists Starknet; the live list did not ([repo](https://github.com/daydreamsai/facilitator)).
- SDK and tooling. Lucid Agents (`@lucid-agents/*`, x402 and MPP payment packages), an OpenClaw x402 plugin, an agent-wallet package ([org](https://github.com/daydreamsai)).
- Seller. Task Market takes payment through x402 first and then a relayer calls the contract (the "PGTR" pattern) ([protocol page](https://taskmarket.dev/protocol)). Earlier the Router beta API and demo agents were x402 sellers.
- Standards. Two ERC drafts, Payment-Gated Transaction Relay ([ERCs#1603](https://github.com/ethereum/ERCs/pull/1603)) and Task Market Protocol ([#1604](https://github.com/ethereum/ERCs/pull/1604)), opened 2026-03-14 by GitHub user beauwilliams, both still open.
- x402 is central here: the live product is built on it.

### Chains
Base is primary. Task Market settles USDC on Base ([taskmarket.dev](https://taskmarket.dev)). All of the last 100 facilitator transfers (2026-10-08 to 2026-10-11) were USDC on Base ([x402scan transfers API](https://www.x402scan.com/facilitator/daydreams)). Solana and Ethereum are also supported by the facilitator.

### Token
- $DREAMS, CoinGecko id `daydreams` ([CoinGecko](https://api.coingecko.com/api/v3/coins/daydreams)).
- Addresses (site and CoinGecko agree): Solana `GMzuntWYJLpNuCizrSR7ZXggiMdDzTNiEmSNHHunpump`; Base `0x176383016BB310C9f1C180DC6729d5E28104e602`; Starknet `0x04fcaf2a7b4a072fe57c59beee807322d34ed65000d78611c909a46fead07fb1` ([tokenomics page](https://daydreams.systems/tokenomics)).
- Launch: Solana via pump.fun. First Raydium pool 2025-01-19 14:28 UTC ([GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/solana/tokens/GMzuntWYJLpNuCizrSR7ZXggiMdDzTNiEmSNHHunpump/pools)); the mint ends in "pump" and CoinGecko tags it "Pump.fun Ecosystem". The exact pump.fun creation time is unconfirmed.
- Base: deployed 2025-09-16 00:21 UTC (block 35,596,370) by `0x67220A370FD91337323018B8f00B40F3EB836Ff0`. Blockscout shows the implementation as HypERC20, a Hyperlane warp-route synthetic ([Blockscout](https://base.blockscout.com/address/0x176383016BB310C9f1C180DC6729d5E28104e602)). First Base pools 2025-09-17. Base supply was 32.59M tokens on 2026-10-11 (RPC `totalSupply`), with 941 holders and the top 10 holding about 80.9% ([GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/base/tokens/0x176383016BB310C9f1C180DC6729d5E28104e602/info)).
- Stated utility: none. The tokenomics page (reviewed 2026-07-23) asserts no allocation table, says buyback, burn and revenue share are not active, and says $DREAMS is not equity or a claim on revenue ([page](https://daydreams.systems/tokenomics)). It does no work in the product; Router, Lucid and Task Market take USDC.
- Caution: CoinGecko's homepage link, `dreams.fun`, serves an "Airdrop Round 01" claim page ("Claim 100,000 $DREAMS", wallet connect). Its docs, GitHub and X links are `#` placeholders and a CSS comment says the palette is "daydreams.systems inspired" ([page source](https://www.dreams.fun)). The official site and GitHub do not mention it. Unverified; do not connect a wallet.

### Team
No official team page.

| Person | Role and evidence | X | GitHub | Farcaster | Verification | Doxxed? |
|---|---|---|---|---|---|---|
| Loaf | Founder and lead. 925 commits in `daydreams`, 113 in `lucid-agents`, 90 in `facilitator` | @LordOfAFew | ponderingdemocritus | @loaf, fid 6214 (medium) | GitHub profile: name "Loaf", bio "@BibliothecaDAO @cartridge-gg @dojoengine @daydreamsai", `twitter_username` LordOfAFew, blog loaf.coffee, which links the same X account ([profile](https://api.github.com/users/ponderingdemocritus), [site](https://loaf.coffee)). Farcaster bio names BibliothecaDAO, Realms and Dojo but is not cross-linked. | Pseudonymous handle |
| boat | Contributor, 38 commits in `daydreams` | @frontboat | frontboat | none found | GitHub `twitter_username` | Pseudonymous |
| Beau | Top committer in `lucid-agents` (366), `taskmarket-contracts` (70), `skills-market` (44); opened both ERC PRs | none on profile | beauwilliams | none found | GitHub name "Beau", site beauwilliams.dev; profile company field says Atlassian. Role at Daydreams inferred from commits only. | First name only |
| RedBeard | 18 commits in `lucid-agents`; merged upstream OpenClaw releases into the `dreaming-claw` fork in March 2026 | none | RedBeardEth | none | commits only | Pseudonymous |
| Galego | Earlier contributor (94 commits in `daydreams`), inactive in 2026 | none | bmgalego | none | commits only | n/a |

Loaf's earlier work, from GitHub contributor counts: 4,382 commits to BibliothecaDAO/eternum, 376 to loot-survivor, 45 to dojoengine/dojo, 285 to the old elizaOS repo ([eternum](https://github.com/BibliothecaDAO/eternum), [dojo](https://github.com/dojoengine/dojo)). Bankless names him as a key figure in Eternum ([May 2025, search snippet](https://www.bankless.com/es/read/daydreams-ai-agents-gaming)). He also committed "add daydreams base facilitator address" to x402scan on 2026-03-09. Only Loaf and Beau commit in the window (plus bots and one outside docs PR on 2026-10-09). No joins or departures were announced.

### Track record and pivots
- 2024-12-20 first commit in `daydreams`; org created 2025-01-04.
- 2025-01-19 $DREAMS appears on Solana. Jan to May 2025: "generative agent library for playing anything onchain", agents in Eternum ([CoinGecko text](https://api.coingecko.com/api/v3/coins/daydreams)).
- 2025-06-02 research article "The GDP Unlock" ([site](https://daydreams.systems)); 2025-06-30 first npm release of the Router's AI SDK provider ([npm](https://registry.npmjs.org/@daydreamsai/ai-sdk-provider)).
- 2025-08-14 first x402 example and tutorial; 2025-08-15 Router docs ([commits](https://github.com/daydreamsai/daydreams/commits/main/docs/content/docs/tutorials/x402/server.mdx)). 2025-09-03 last framework release, v0.3.22 ([npm](https://registry.npmjs.org/@daydreamsai/core)).
- 2025-09-16 Base token. 2025-10-16 first facilitator transaction on x402scan.
- 2025-11-04 `lucid-agents` created (first x402 commit 2025-11-09, first npm publish 2025-11-13). 2025-12-14 `facilitator` repo. 2026-01-08 `skills-market`. 2026-02-01 `OpenClaw-x402`. 2026-02-08 `agent-wallet` v0.1.0. 2026-02-16 OpenClaw fork `dreaming-claw`.
- 2026-02-06 README notice: the agent framework "is no longer the core focus as features are already obsolete".
- 2026-03-10 `taskmarket-contracts`; 2026-03-14 ERC drafts.
- 2026-07-21 to 2026-07-26 Lucid docs rebuilt "around paid x402 applications", v5.0.0 with "current x402 and MPP payment capabilities"; last `lucid-agents` commit.

### Trend-hopping score
3, at the upper end. Each phase shipped code, so it is not narrative-only. But the headline changed every three to five months along with the market: gaming agents, agent framework, "agent GDP" and x402 (Aug 2025), ERC-8004/AP2/A2A (Nov 2025), OpenClaw and Claude skills (Jan to Feb 2026), bounty markets (Mar 2026). Earlier products were dropped quickly. x402 is the longest thread (about 14 months), and Loaf committing to x402scan suggests it is more than a label. The usage is tiny.

### Funding
No evidence of outside funding. DefiLlama has no page for Daydreams, CoinGecko lists no investors, and the token launched on pump.fun. Unconfirmed: Crunchbase, RootData and CryptoRank were not reachable; Dealroom returned 403.

### Product and traction
- Task Market: homepage on 2026-10-11 showed "385 tasks completed" and "8 open tasks". Sample bounties pay 2 to 4 USDC with 8 to 128 submissions ([homepage](https://taskmarket.dev)). The 20 top-reputation workers on the [leaderboard](https://taskmarket.dev/leaderboard) have earned about 753 USDC combined (largest single total 129.33 USDC). The dashboard shows 557, 345 and 2,885.58 USDC with unclear labels, so I do not use them.
- x402scan facilitator `daydreams`: past 30 days 496 requests, US$775.35, 77 buyers, 7 sellers. All-time 11,833,867 transactions, US$2.76M, 18,969 buyers, fourth by transactions behind Coinbase (118.0M), PayAI (52.7M) and Dexter (28.0M) ([page](https://www.x402scan.com/facilitator/daydreams), [list](https://www.x402scan.com/facilitators)). Ecosystem total, past 30 days: 2.66M transactions, US$1.06M ([home](https://www.x402scan.com/)).
- Monthly facilitator transactions and USD: 2025-10 (from the 16th) 153,651 / $91.7K; 2025-11 9,557,797 / $2.66M; 2025-12 2,111,286 / $9.3K; 2026-01 141 / $49; 02 4,548 / $1.0K; 03 3,455 / $3.1K; 04 17 / $151; 05 42 / $3; 06 562 / $650; 07 661 / $785; 08 1,032 / $1.1K; 09 444 / $689; 10 (to the 10th) 231 / $135. November 2025 holds 81% of all-time transactions and 96% of volume. Millions of tiny payments in one month looks like a promotion or farming burst; I could not confirm the cause.
- Current flow: the last 100 transfers all went to one recipient, `0x3c0820e2dabd5feae1fd03b78079dee15c7f83d8`, an externally owned account (no code on Base RPC). A third-party note dated 2026-09-21 says user deposits go to this EOA and then to a Task Market contract (`0xddc6cc3e...9c33f7`), and that the EOA held about 233 USDC that day. The author says payouts ran correctly and makes no accusation ([MoltyCel doc](https://github.com/MoltyCel/moltrust-api/blob/main/docs/taskmarket-escrow.md)). One source; treat as a custody point to know about.
- Router: x402scan origin `api-beta.daydreams.systems`: all-time 4,627 transactions, US$1,404.53, 269 buyers, last 2026-02-03, none in 30 days. Six demo-agent origins: 23,163 transactions, US$7,023.47, last 2026-02-03. `router.daydreams.systems` and `api.daydreams.systems` return NXDOMAIN; `api-beta` fails TLS. The README still links the Router.
- Stars: daydreams 619, lucid-agents 199, skills-market 31, facilitator 18.

### Last six months
- Commits by month since 2026-04-01 (author dates): `daydreams` Oct 2; `lucid-agents` Jun 1, Jul 20; `facilitator` Aug 3; `skills-market` Jul 2, Aug 3; `taskmarket-contracts` May 13, Jun 8, Jul 15, Aug 17, Sep 0, Oct 4; `agent-wallet` 0. April had none in any repo. Total 88, 65% in the Task Market contracts.
- Last commits: `taskmarket-contracts` 2026-10-10; `daydreams` 2026-10-09; `skills-market` 2026-08-10; `facilitator` 2026-08-07; `lucid-agents` 2026-07-26.
- Releases: npm `@lucid-agents/*` 4.1.0 (07-22), 4.2.0 (07-23), 5.0.0 (07-25) ([npm](https://registry.npmjs.org/@lucid-agents/core)). No GitHub release since 2026-02-12; no framework release since 2025-09-03.
- Dated items: May to Aug, Task Market contracts built; 2026-06-26 Lucid docs landing page; 2026-07-20 to 07-26 Lucid runtime refactor, storefront UI, versioned coding-agent skill, Cloudflare previews, x402 and MPP support, v5.0.0, brand refresh; 2026-07-23 tokenomics page reviewed; 2026-10-09 README link cleanup; 2026-10-11 Task Market live with 385 completed tasks.
- Active contributors: 2. Joins and departures: none announced.

### Pace verdict
Slow. A small team using AI coding tools in 2026 would show weekly commits and a release every month. Daydreams had no commits in April or September, 11 weeks without a commit in `lucid-agents`, and two trivial commits in the main repo. For comparison the x402 reference repo ran 67 to 115 commits a month over the same months ([x402-foundation/x402 activity](https://github.com/x402-foundation/x402)), Virtuals about 470 commits in three core repos, and elizaOS several thousand a month. Only the Task Market contract repo moves.

### Direction
Stated (site, 2026-10-11): "markets, payment rails, routing, and settlement", with four products: Task Market, Lucid Agents, Dreams Router, Agent Payments. The shipping record supports Task Market and its ERC drafts. Lucid went quiet after 2026-07-26 and the Router looks dead, so the stated line-up is wider than what is maintained.

### Competitors
Facilitators ahead on volume: Coinbase, PayAI, Dexter ([x402scan](https://www.x402scan.com/facilitators)). Escrowed agent jobs: Virtuals ACP (ERC-8183). Paid-agent SDKs: Coinbase's own x402 SDKs, thirdweb, Cloudflare and Vercel tooling, elizaOS's wallet plugin. Other notes cover these.

### Green and red flags
- Green: x402 work since Aug 2025; a live multi-chain facilitator; ERC drafts; a founder whose track record is verifiable through commits; an honest tokenomics page and README notices; MIT licence.
- Red: Router offline while the README still links it; two active people; facilitator volume is one burst and about 16 transactions a day now; Task Market funds pass through an EOA relayer; $DREAMS has no function; the CoinGecko homepage link is an unverified airdrop page; the Base token is a thin Hyperlane copy with concentrated holders; two different Discord invites; no blog, changelog or funding disclosure.

### Verdict
Credible but small. Momentum: Slowing.
The team is real and has been on x402 longer than most, and Task Market is a coherent use of it (pay first, then relay an onchain call). But usage is small (385 completed tasks of 2 to 4 USDC, about 500 facilitator requests a month), earlier products were dropped within months, and two people do the work. Expect more Task Market pieces in bursts and another change of headline. Watch the two ERC pull requests, Task Market's completed-task count, and whether Lucid commits resume.

### Tracking card
- Sites: https://daydreams.systems, https://lucid.daydreams.systems, https://taskmarket.dev, https://facilitator.daydreams.systems. Docs: https://docs.daydreams.systems. No blog or RSS; changelog `CHANGELOG.md` in the main repo (stale). Atom feeds: https://github.com/daydreamsai/taskmarket-contracts/commits/main.atom and https://github.com/daydreamsai/lucid-agents/commits/master.atom.
- GitHub: https://github.com/daydreamsai; repos `lucid-agents`, `facilitator`, `taskmarket-contracts`, `skills-market`, `daydreams`, `agent-wallet`, `OpenClaw-x402`.
- X: @daydreamsagents (project, from GitHub org field), @LordOfAFew, @frontboat. Farcaster: no official account found; @loaf is Loaf's personal account.
- Discord: discord.gg/P8UUNGtHZs (site), discord.gg/rt8ajxQvXh (README). Telegram: t.me/+kGzGMRvsQhY5Njg0 (CoinGecko).
- Token: see Token.
- x402scan: https://www.x402scan.com/facilitator/daydreams (id `daydreams`); Base signers `0x279e08f711182c79Ba6d09669127a426228a4653` (first tx 2025-10-16) and `0x1363C7Ff51CcCE10258A7F7bddd63bAaB6aAf678` (2026-01-16, current); Solana `DuQ4jFMmVABWGxabYHFkGzdyeJgS1hp4wrRuCtsJgT9a` (marked deprecated 2026-07-14). Router beta origin id e98c4138-7115-414d-932b-a593e29f7de4.
- Dune: no project dashboard found. DefiLlama's x402 facilitator adapter uses Dune query https://dune.com/queries/6054244 ("x402 facilitators"), which includes the Daydreams addresses ([adapter](https://github.com/DefiLlama/dimension-adapters/blob/master/dexs/x402/facilitators.ts)).

### Sources (accessed 2026-10-11)
https://daydreams.systems; https://daydreams.systems/tokenomics; https://github.com/daydreamsai (daydreams, lucid-agents, facilitator, taskmarket-contracts, skills-market, agent-wallet, dreaming-claw); https://taskmarket.dev; https://taskmarket.dev/protocol; https://lucid.daydreams.systems; https://facilitator.daydreams.systems/supported; https://www.dreams.fun; https://loaf.coffee; https://api.coingecko.com/api/v3/coins/daydreams; GeckoTerminal and Blockscout pages above; Base RPC; https://www.x402scan.com (facilitator and API data); https://github.com/Merit-Systems/x402scan; https://github.com/ethereum/ERCs/pull/1603 and /1604; https://github.com/MoltyCel/moltrust-api/blob/main/docs/taskmarket-escrow.md; https://www.bankless.com/es/read/daydreams-ai-agents-gaming (snippet); npm registry; GitHub REST API.

---

## 2. Virtuals Protocol

### One-line
Virtuals began as a launchpad on Base where each AI agent is a token paired with $VIRTUAL. It now presents an "agent economy" stack: EconomyOS (agent identity and wallets), the Agent Commerce Protocol (ACP, escrowed jobs between agents), tokenization and capital markets, and robotics ([virtuals.io](https://virtuals.io), [whitepaper](https://whitepaper.virtuals.io/about-virtuals/about-virtuals-protocol)).

### x402 role
A payment rail inside ACP, plus a facilitator-style service. x402scan lists "Virtuals Protocol" as facilitator `virtuals` (URL https://acpx.virtuals.io/, one Base address, first transaction 2025-11-05) and a seller origin `acp-x402.virtuals.io` ([source](https://github.com/Merit-Systems/x402scan/blob/main/packages/external/facilitators/src/facilitators/virtuals.ts)).

What the integration is, from code:
- ACP v2 contracts have an x402 job mode (`createJobWithX402`, `confirmX402PaymentReceived`, role `X402_MANAGER_ROLE`) ([JobManager.sol](https://github.com/Virtual-Protocol/agent-commerce-protocol/blob/main/contracts/acp/v2/modules/JobManager.sol)).
- The Python SDK signs a USDC EIP-3009 `TransferWithAuthorization` from the agent's smart wallet and posts a nonce to the ACP backend; config `BASE_MAINNET_ACP_X402_CONFIG_V2` "route[s] to x402 for payment, undefined defaulted back to direct transfer" ([x402.py](https://github.com/Virtual-Protocol/acp-python/blob/main/virtuals_acp/x402.py), [README](https://github.com/Virtual-Protocol/acp-python)). Commits run 2025-10-31 to 2026-01-19, mostly by `stevensf1998`.
- The 2025-12-01 update lists "full x402 integration for pay-per-query data" under ACP and says Pudgy AI video requests run as x402 transactions through ACP ([Substack](https://virtuals.substack.com/p/virtuals-monthly-update-september)). A 2026-03-21 report ties ACP to t54's x402 facilitator on XRPL ([HTX, snippet](https://www.htx.com/news/xrp-ledger-gets-ai-agent-payments-through-virtuals-and-t54-hnNkB9AB/)).
- The April 2026 ACP v2 rewrite (`acp-node-v2`, `acp-cli`) has no x402 code apart from a legacy-contract bridge in the CLI (`legacyContractBridge.ts`); x402 otherwise appears only in the old-SDK migration guide ([migration.md](https://github.com/Virtual-Protocol/acp-node-v2/blob/main/migration.md)). Based on GitHub code search of the org on 2026-10-11.

ACP and x402 both complement and overlap. x402 is a stateless "pay for this HTTP call" step. ACP is a job lifecycle: request, negotiation, escrow, evaluator check, release. Virtuals treats x402 as one way to fund a job, and the ERC-8183 draft names x402 only in an optional meta-transaction extension ([EIP](https://eips.ethereum.org/EIPS/eip-8183)). Both target the same use (agents paying agents), and since April the new SDK no longer funds jobs through x402. This ACP is not OpenAI and Stripe's "Agentic Commerce Protocol" ([Forkast](https://forkast.news/the-machine-as-buyer-virtuals-acp-and-the-evaluator-problem/)). A 4Pillars note dated 2025-10-31 describes Virtuals as a main beneficiary of the x402 narrative that month ([snippet](https://research.4pillars.io/en/research/virtuals-protocols-acp-back-in-the-spotlight-with-x402)).

### Chains
Base is primary. $VIRTUAL deployed there, ACP and Butler started there, x402 flows are Base USDC only, and the SDK takes a Base builder code ([acp-node-v2](https://github.com/Virtual-Protocol/acp-node-v2)). Multi-chain since: Ethereum, Solana, Ronin (CoinGecko text); ACP contracts target Ethereum, Base, Polygon, Arbitrum and BNB ([repo](https://github.com/Virtual-Protocol/agent-commerce-protocol)); Solana in the v2 SDK (2026-08-19, 2026-10-05) and Arc mainnet (SDK 2026-09-17, contracts 2026-09-23).

### Token
- $VIRTUAL, Base `0x0b3e328455c4059EEb9e3f84b5543F74E24e7E1b`. Deployed 2024-03-14 13:36 UTC (block 11,817,009) by `0x97cF38bB06Da57b6418083998b09976eC40A90a3` ([Blockscout](https://base.blockscout.com/address/0x0b3e328455c4059EEb9e3f84b5543F74E24e7E1b)). First pool seen on GeckoTerminal's top-20 list: Aerodrome VIRTUAL/WETH, 2024-03-31 (earlier pools may exist). Total supply on Base 497,704,679.68 on 2026-10-11. Other chains per CoinGecko: Ethereum `0x44ff8620b8ca30902395a7bd3f2407e1a091bf73`, Solana `3iQL8BFS2vE7mww4ehAqQHAsbmRNCrPxizWAT2Zfyr9y`, Robinhood chain `0xc6911796042b15d7fa4f6cde69e245ddcd3d9c31`, Arc `0x8c4252c87081c88c6ad57d6dd97e1cafebf842b7` ([CoinGecko](https://api.coingecko.com/api/v3/coins/virtual-protocol)).
- Launch method unconfirmed. Whitepaper: 1B supply, 60% public, 5% liquidity, 35% treasury, "fully unlocked" ([tokenomics](https://whitepaper.virtuals.io/info-hub/usdvirtual-token-base-asset-for-ai-agents/usdvirtual-token-distribution-and-tokenomics)).
- Stated utility: liquidity pair for every agent token; 100 VIRTUAL to create an agent; graduation at 42,000 VIRTUAL; LP locked 10 years; veVIRTUAL staking for DAO votes (July 2025); revenue-funded buybacks and burns ([CoinGecko](https://www.coingecko.com/en/coins/virtual-protocol)).
- Real work: yes for the launchpad. No for ACP jobs and x402: job payments moved from VIRTUAL to USDC on 2025-08-12 ([changelog](https://whitepaper.virtuals.io/acp/acp-changelogs)).

### Team
Names are public. Sources: official [core contributors page](https://whitepaper.virtuals.io/info-hub/virtuals-protocol-core-contributors) and GitHub.

| Person | Role | X | GitHub | Farcaster | Verification and confidence |
|---|---|---|---|---|---|
| Jansen Teng | Co-founder, CEO; ex-BCG | @Ethermage | none found | @ethermage, fid 315376 (medium-high) | X and LinkedIn on the official page; Farcaster bio "Building virtuals.io". Full name from CoinGecko and the 2025-12-01 post. |
| Weekee Tiew ("Wee Kee") | Co-founder; ex-BCG | @everythingempty | none found | none found | Handle on official page; full name from CoinGecko only (medium). |
| Koo Huang | Engineering; ex-Bybit | @0xkookoo | koo-virtuals (62 commits in window) | none | X on official page; GitHub by name match (medium). |
| Kahwai | Engineering | none | kahwaipd | none | name match (medium). |
| Tay Weixiong | Engineering; ERC-8183 co-author | none | twx-virtuals | none | EIP author list (high). |
| Bryan Lim | AI; ERC-8183 co-author | none | ai-virtual-b | none | EIP author list (high). |
| Chooi Zuhwa | ERC-8183 co-author | none | Zuhwa | none | EIP author list (high). |
| Celeste Ang | Ecosystem core contributor | @celesteanglm | celesteanglm | none | GitHub profile self-declares X; named on official page. |
| Joey Lau | Contributor | @0xjoeylau | LauJoeYing | none | GitHub profile self-declares company "Virtuals Protocol" and X. |
| andrew-virtuals, psmiratisu, jaimewangvirtuals | Engineers (87, 58 and 5 commits across the core repos in the window) | none | as named | none | handle carries the Virtuals name only. |

Also an ERC-8183 author: Davide Crapis (GitHub dcrapis); the EIP page gives no affiliation. CoinMarketCap lists different founders (Prakash Somosundram, Colin Choo, Christopher Johnson, Matthew) without sources; I did not use them ([CMC](https://coinmarketcap.com/currencies/virtual-protocol/)). Leaders are named with LinkedIn; several engineers are handles only.
Changes inferred from last-commit dates in the org (no announcements found): `stevensf1998`, who wrote the ACP x402 code, last committed 2026-02-26; `Ang-dot` (profile company "@bnb-chain") 2026-06-10; `koo-virtuals` 2026-07-06; `celesteanglm` 2026-08-19. Active in October: andrew-virtuals, kahwaipd, twx-virtuals, ariessa.

### Track record and pivots
- 2021 PathDAO gaming guild; pivot to AI agents about January 2024 ([CoinGecko](https://www.coingecko.com/en/coins/virtual-protocol), [Dec 2024 update](https://virtuals.substack.com/p/monthly-update-december-2024)). The PathDAO link has no primary source in my notes.
- 2024-03-14 token on Base. 2024-10-16 new platform on Base; by 2025-01-08 the team reported about 220k agent-token holders and about $60M protocol revenue (self-reported).
- 2025-01 Animoca partnership and GAME framework for entertainment agents (CoinGecko text). 2025-02 ACP work starts; 2025-07-03 ACP go-live with Butler.
- 2025-08-12 ACP payments move to USDC. 2025-10 Genesis retired, Unicorn framework, ACP SDK v2 (10-15), x402 code starts (10-31). 2025-11 ACP Scan, Robotics (Eastworlds), Agentic Fund of Funds; "$300M+ aGDP" claim (12-01).
- 2026-02-01 ERC-8004 identity for agents; 02-07 OpenClaw ACP skill pack; 02-25 ERC-8183 draft; 04 ACP v2.0 rewrite (hooks replace memos, multi-chain, Solana adapter, new SDK and CLI, ERC-8183 reference implementation) ([changelog](https://whitepaper.virtuals.io/acp/acp-changelogs)).

### Trend-hopping score
3. The core bet (tokenized AI agents on Base) is the same since 2024, but the label moved from gaming guild to entertainment agents to agent commerce to robotics and "EconomyOS", and Virtuals joined the x402 wave within weeks of the October 2025 surge. Each phase has real product. x402 is an add-on, not the identity.

### Funding
No verified venture round. CoinGecko says a "$16 million seed led by DeFiance Capital and Beam", with Master Ventures, NewTribe Capital, LVT Capital and Stakez Capital, in the 2021 PathDAO phase; CoinMarketCap instead mentions a $16M treasury. They disagree and neither cites a source, so treat the seed as unconfirmed. Token treasury: 35% of supply (350M VIRTUAL) in a DAO multisig, emissions capped at 10% a year for three years ([tokenomics](https://whitepaper.virtuals.io/info-hub/usdvirtual-token-base-asset-for-ai-agents/usdvirtual-token-distribution-and-tokenomics)). A $1M-a-month incentive programme for revenue-generating agents is reported by [Forkast](https://forkast.news/the-machine-as-buyer-virtuals-acp-and-the-evaluator-problem/).

### Product and traction
- Self-reported: $470M agent GDP and 1.77M completed jobs "as of February 2026"; Forkast notes the data does not separate real commerce from internal testing ([2026-07-22](https://forkast.news/the-machine-as-buyer-virtuals-acp-and-the-evaluator-problem/)). "$300M+ aGDP" in the 2025-12-01 update. The homepage counters read 0 when fetched.
- Protocol revenue, DefiLlama (USD): 2026-04 $78.7K; 05 $140.6K; 06 $86.8K; 07 $671.4K; 08 $206.3K; 09 $188.6K; 10 (to the 11th) $26.4K; all-time $41.7M ([DefiLlama](https://api.llama.fi/summary/fees/virtuals-protocol?dataType=dailyRevenue)). Forkast quotes about $59M trailing revenue and $170K daily fees, which does not match this series (probably fees versus revenue). Unreconciled.
- x402 through ACP (x402scan, `virtuals`): all-time 1,993,122 transactions, US$4.34M, 25,179 buyers, last 2026-09-28. Monthly (tx / USD): 2025-11 144,891 / $172K; 12 553,363 / $1.17M; 2026-01 294,743 / $191K; 02 442,223 / $1.42M; 03 518,757 / $1.35M; 04 32,342 / $33K; 05 2,015 / $421; 06 567 / $28; 07 458 / $11; 08 973 / $18; 09 2,790 / $28; 10 0. Seller origin `acp-x402.virtuals.io`: past 30 days 2,791 transactions, $27.91 ([x402scan](https://www.x402scan.com/facilitators)). The collapse follows the April 2026 rewrite.
- Stars: protocol-contracts 101, acp-cli 37.

### Last six months
- Commits since 2026-04-01 by month (Apr to Oct): `acp-cli` 116/38/46/16/15/33/1 (265); `acp-node-v2` 26/22/21/13/4/4/2 (92); `protocol-contracts` 50/11/23/23/2/2/0 (111); `butler-skills` 18 in October; `dgclaw-skill` 17; `acp-cli-demos` about 300, mostly community showcase submissions.
- Last commits: `butler-skills` 2026-10-09; `acp-node-v2` and `acp-cli` 2026-10-05; `protocol-contracts` 2026-09-23.
- Releases (npm): `acp-node-v2` 22 versions (0.1.15 on 2026-10-05); `acp-cli` 41 versions (1.0.40 on 2026-10-05) ([npm](https://registry.npmjs.org/@virtuals-protocol/acp-node-v2)). GitHub releases: `acp-node` and `openclaw-acp` were marked deprecated and archived on 2026-06-01.
- Dated items: 04 ACP v2.0; 04-09 `acp-node-v2` created; 05-04 `acp-cli` created; 07-14 peaqOS integration ([Forkast](https://forkast.news/the-machine-as-buyer-virtuals-acp-and-the-evaluator-problem/)); 07-16 8-minute anti-sniper option and 07-30 more launch options in contracts; 08-19 Solana support; 09-17 Arc in SDK, 09-23 Arc contract deploy; 09-18 token-launch CLI flags; 09-28 Hyperliquid cash in `wallet balance`; 10-05 Solana in `acp-node-v2`; 10-08 to 10-09 Butler skills (options trading, app checkout, X portfolio, DCA, copy-trade).
- Active contributors in window: 14 named accounts across the four repos, about 6 with 10 or more commits; an AI "claude" account (14 commits) appears in `acp-cli`. Substack updates stopped after 2025-12-01 and the ACP changelog's newest entry is "April 2026", so later announcements are on X (not fetchable).

### Pace verdict
Fast, and the best of the three on discipline: weekly commits throughout, about 63 npm releases (SDK and CLI combined) in 26 weeks, and visible AI-assisted commits. About 470 commits in three core repos (about 78 a month) is in line with the x402 reference repo's 67 to 115 a month. This is what a good AI-assisted small team ships in 2026. The weak spot is x402: it dropped out of the new SDK and its volume is near zero.

### Direction
Stated: EconomyOS, ACP, capital markets, robotics, and an "AI Council" marked coming soon ([virtuals.io](https://virtuals.io)). Shipping matches ACP, multi-chain reach, CLI and agent "skills", and ERC-8183. x402 is peripheral to strategy.

### Competitors
Agent payment rails and facilitators: Coinbase, PayAI, Dexter; Daydreams Task Market (a bounty-market rival); OpenAI/Stripe and Google agent-commerce standards; ERC-8004 reputation projects. Launchpads on Base and Solana are covered by other notes.

### Green and red flags
- Green: a revenue series, steady releases, public SDKs and contracts, ERC-8183 co-authored, named founders, a maintained changelog.
- Red: usage figures are self-reported; incentive programmes may reward simulated commerce (Forkast's point); x402 volume collapsed; funding claims conflict; blog stopped; the ACP name clashes with OpenAI/Stripe's; the evaluator trust problem is open; some early x402 contributors are no longer committing.

### Verdict
Serious builder. Momentum: Steady (shipping Accelerating; x402 Slowing).
Virtuals is the best resourced of the three and the only one with a revenue line and a regular release cadence. x402 was a fast add-on during the October 2025 wave (about $4.3M settled over five months) and has faded since the ACP rewrite. Expect more multi-chain and agent-skill releases, with x402 staying one optional rail.

### Tracking card
- Sites: https://virtuals.io; docs https://whitepaper.virtuals.io (index at /llms.txt); ACP spec https://os.virtuals.io/acp; changelog https://whitepaper.virtuals.io/acp/acp-changelogs; blog https://virtuals.substack.com (feed https://virtuals.substack.com/feed, last post 2025-12-01). Atom: https://github.com/Virtual-Protocol/acp-cli/commits/main.atom.
- GitHub: https://github.com/Virtual-Protocol; repos `acp-cli`, `acp-node-v2`, `acp-python`, `agent-commerce-protocol`, `protocol-contracts`, `butler-skills`.
- X: @virtuals_io (GitHub org field); @Ethermage, @everythingempty, @0xkookoo, @celesteanglm, @0xjoeylau. Farcaster: no official account found.
- Discord: discord.com/invite/virtualsio. Telegram: t.me/virtuals.
- Token: see Token. DefiLlama id 5575.
- x402scan: https://www.x402scan.com/facilitator/virtuals (id `virtuals`, URL https://acpx.virtuals.io/, Base `0x80735b3f7808e2e229ace880dbe85e80115631ca`, first tx 2025-11-05); origin id bc1f8da1-bc0c-4d2c-8879-92d60aa90f02.
- Dune: no project dashboard found; DefiLlama's x402 adapter (Dune query 6054244, "x402 facilitators") includes the Virtuals address.

### Sources (accessed 2026-10-11)
https://virtuals.io; https://whitepaper.virtuals.io (about, core contributors, ACP changelog, tokenomics); https://eips.ethereum.org/EIPS/eip-8183; https://forkast.news/the-machine-as-buyer-virtuals-acp-and-the-evaluator-problem/ (2026-07-22); https://virtuals.substack.com/p/virtuals-monthly-update-september (2025-12-01); https://virtuals.substack.com/p/monthly-update-december-2024; https://github.com/Virtual-Protocol (acp-python, agent-commerce-protocol, acp-node-v2, acp-cli, protocol-contracts, butler-skills); https://api.coingecko.com/api/v3/coins/virtual-protocol; https://www.coingecko.com/en/coins/virtual-protocol; https://coinmarketcap.com/currencies/virtual-protocol/; https://api.llama.fi/summary/fees/virtuals-protocol; Blockscout and Base RPC; x402scan; npm registry; https://research.4pillars.io/... and https://www.htx.com/news/xrp-ledger-gets-ai-agent-payments-through-virtuals-and-t54-hnNkB9AB/ (search snippets).

---

## 3. elizaOS

### One-line
elizaOS (company Eliza Labs, now presenting as Eliza Research; founder Shaw Walters) is the open-source Eliza agent framework that began as ai16z on Solana. Its repo now describes an "agentic operating system": the Eliza personal-agent app, Eliza Cloud, local Gemma-4-based models, Linux and Android images, and "Slop", a network that rewards contributors. On 2026-08-05 the founder declared the $elizaOS token dead and said the foundation is winding down ([The Block](https://www.theblock.co/post/410774/eliza-labs-native-token-dead), [Decrypt](https://decrypt.co/374958/eliza-ai-token-dead-shuts-down-foundation-lawsuit), [README](https://github.com/elizaOS/eliza)).

### x402 role
Wide in code, thin in visible use. In the monorepo (2026-10-11):
- Facilitator: Eliza Cloud has a serverless x402 facilitator ("verification and settlement as an integrated service", EIP-3009 `exact` on Base, Ethereum, BNB Chain and Solana) with routes `/api/v1/x402/verify`, `/settle`, `/requests` ([source](https://github.com/elizaOS/eliza/blob/develop/packages/cloud/shared/src/lib/services/x402-facilitator.ts)). It is not in x402scan's facilitator list.
- Seller: paid plugin routes in `@elizaos/agent`, answering 402 with both a v1 JSON body and a v2 `PAYMENT-REQUIRED` header ([paid routes](https://github.com/elizaOS/knowledge/blob/main/docs/plugins/x402-paid-routes.mdx), [roadmap](https://github.com/elizaOS/knowledge/blob/main/docs/plugins/x402-roadmap.mdx)).
- Buyer: `@elizaos/plugin-wallet` x402 client with spend budgets ([README](https://github.com/elizaOS/eliza/blob/develop/plugins/plugin-wallet/README.md)) and the registry plugin `@elizaos/plugin-x402` ([doc](https://github.com/elizaOS/knowledge/blob/main/docs/plugin-registry/x402.md)).
- Billing: Cloud credit top-ups by x402 and x402 payment requests with creator earnings (commits 2026-09-28 to 2026-10-11).
- Token experiment: payment presets `base_elizaos`, `solana_elizaos`, `solana_degenai`, added "as of May 6" ([log 2026-05-07](https://github.com/elizaOS/knowledge/blob/main/hackmd/facts/2026-05-07.md)).
- Visible usage: none. The live docs index lists no x402 page ([llms.txt](https://docs.elizaos.ai/llms.txt)). The x402scan origin `x402.elizaos.ai` ("X402 API Gateway", 2 resources) shows 0 transactions all-time, and the gateway returned HTTP 502 when I fetched it.

### Chains
Not Base-primary. The token started on Solana and was extended to Ethereum, Base and BNB Chain with Chainlink CCIP ([The Block, 2025-09-25](https://www.theblock.co/post/371639/eliza-labs-ai16z-elizaos-token-migration)). For x402, Base USDC is the first seller preset and the first network in the Cloud facilitator registry; the facilitator also covers Ethereum, BNB Chain and Solana, and the seller presets add Polygon.

### Token
- $elizaOS (CoinGecko id `elizaos`). Solana `DuMbhu7mvQvqQHGcnikDgb4XegXJRyhUBfdU22uELiZA`; Ethereum, Base and BNB Chain `0xea17Df5Cf6D172224892B5477A16ACb111182478`; 9 decimals ([CoinGecko](https://api.coingecko.com/api/v3/coins/elizaos), [tokenomics doc](https://docs.elizaos.ai/tokenomics)).
- Base contract deployed 2025-10-09 03:58 UTC (block 36,596,493) through factory `0xf4d5cD5df029E7e70cE3A828F1F36383369B8265` ([Blockscout](https://base.blockscout.com/address/0xea17df5cf6d172224892b5477a16acb111182478)). Base supply was 28,867,660.48 on 2026-10-11. The Solana token's first pools date from 2025-11-06 ([GeckoTerminal](https://api.geckoterminal.com/api/v2/networks/solana/tokens/DuMbhu7mvQvqQHGcnikDgb4XegXJRyhUBfdU22uELiZA/pools)).
- History: ai16z launched on Solana in October 2024 (launch method unconfirmed); renamed elizaOS in January 2025 after a16z objected; migration announced 2025-09-25 at 1:6, began 2025-11-06, snapshot 2025-11-11. Total supply 11,000,000,000, circulating 7,482,200,000 on 2025-11-11 ([tokenomics doc](https://docs.elizaos.ai/tokenomics)).
- Status: CoinGecko's public notice on the token says Eliza Labs began winding down the foundation and that the native token is obsolete after the Burwick Law dispute. The founder wrote that no foundation support, buybacks or supply measures will follow, and that he will never let a token near Eliza again ([The Block](https://www.theblock.co/post/410774/eliza-labs-native-token-dead)). Burwick Law filed a class action in SDNY in April 2026 (false advertising, deceptive practices, negligent misrepresentation, unjust enrichment; alleged insider control of an "AI-managed fund" and dilution in the migration). The team settled by handing over its remaining treasury; the amount was not disclosed. Walters disputes the substance of the claim.
- Real work: it was meant to, until 2026-08-05. The project log of 2026-04-30 says $ELIZA was made the default x402 payment method for elizaOS and Milady services ([log](https://github.com/elizaOS/knowledge/blob/main/hackmd/facts/2026-04-30.md)). The tokenomics doc states no utility and was last updated 2025-11-11. Now: no.

### Team
| Person | Role | X | GitHub | Farcaster | Verification |
|---|---|---|---|---|---|
| Shaw Walters | Founder, creator of elizaOS | @shawmakesmagic | lalalune | @shawmakesmagic, fid 899923 | GitHub bio "Creator of elizaOS", company "Eliza Research", `twitter_username` shawmakesmagic, blog elizaresearch.ai; named in The Block and Decrypt. Doxxed. |
| nubs | 4,608 commits in the monorepo (all-time) | @nubsvault | NubsCarson | none | GitHub self-declared; public org member; role unconfirmed. |
| shad0w | Contributor, 822 commits in window | @0xShadow | wakesync | none | GitHub self-declared; public org member. |
| Sol | Contributor, 928 | @0xSolace_ | 0xSolace | none | GitHub self-declared. |
| Sailesh Sivakumar | Contributor, 812 | @thescoho | ss251 | none | GitHub self-declared. |
| Sayo | Long-time core contributor, 428; last active week 2026-09-06 | @sayodotfun | wtfsayo | none | GitHub self-declared ("Freelancer"). |
| Odilitime | Long-time core contributor, 273; last active week 2026-08-16 | none | odilitime | none | GitHub profile. |

The company site says "a small team building in the open" and names no one ([elizaresearch.ai](https://elizaresearch.ai)). Founder history: Shaw (lalalune) also has 379 commits in the open-metaverse project webaverse/app; his title there is unconfirmed ([GitHub](https://github.com/webaverse/app)). Governance: ai16z DAO, then Eliza Foundation, now winding down; the founder says he owns the IP.
Changes, inferred from last active weeks in the monorepo (no announcements found): most 2025 core developers stopped committing by February 2026, among them tcm390 (1,657 commits in the old repo, last 2025-10-26), madjin (2025-06-22), shakkernerd (2025-03-16), 0xbbjoker (2026-02-01), mcp97 (2026-02-08), ChristopherTrimboli (2026-01-18). The 2026 work is Shaw, NubsCarson and many new or agent accounts (for example `WalkCrypto`, created 2026-10-07).

### Track record and pivots
- 2024-07-09 `eliza` repo created; 2024-10 ai16z token and "AI-run fund" story on Solana.
- 2025-01 rename to elizaOS. 2025-09-25 migration plan; 2025-10-09 Base token; 2025-11-06 migration starts; Eliza Cloud plugin first on npm 2025-11-07.
- 2025-09-05 to 2025-10-26 logs show x402 discussion, then "positioning itself as an x402 MCP registry" and Cloud x402 integration ([log](https://github.com/elizaOS/knowledge/blob/main/hackmd/facts/2025-10-26.md)).
- 2026-03 to 2026-04 v2 rewrite: monthly commits jump from 155 (Feb) to 925 (Mar) to 4,802 (Apr). 2026-04 Burwick suit filed. 2026-04-30 token tied to x402; 2026-05-07 Eliza Cloud merged into the monorepo.
- 2026-06 "Eliza Cloud Apps" hosting and Cloud x402 facilitator code (first commit 2026-06-28). 2026-07 Gemma-4 local models, LifeOps scenarios, voice.
- 2026-07-30 issue for `eliza.army`, a skill and leaderboard that turns "spare agent compute into reviewable elizaOS contributions" ([#17326](https://github.com/elizaOS/eliza/issues/17326)); launched in August. 2026-08-05 token declared dead. 2026-08-16 Cloud moves under eliza.app ([newsletter](https://github.com/elizaOS/knowledge/blob/main/hackmd/comms/weekly-newsletter/2026-08-16.md)).

### Trend-hopping score
4. The engineering is real and large, but the story changed often and the token was part of it: an "AI-managed fund" (alleged in the class action to be misleading), an agent framework, an "x402 MCP registry" (Oct 2025), token utility through x402 (Apr to May 2026) shortly before the token was declared dead, then an agentic OS and a pay-per-contribution network. x402 is one narrative among several.

### Funding
No evidence of outside venture funding. The project ran on the ai16z and Eliza token treasury, which was handed over in the settlement ([The Block](https://www.theblock.co/post/410774/eliza-labs-native-token-dead)). Walters says he drew a modest salary ([Decrypt](https://decrypt.co/374958/eliza-ai-token-dead-shuts-down-foundation-lawsuit)). Unconfirmed: Crunchbase, RootData and CryptoRank were not reachable, so private rounds or grants may exist.

### Product and traction
- GitHub: 19,568 stars, 5,793 forks, 3,358 org followers (2026-10-11).
- Products: Eliza app, Eliza Cloud ([cloud.eliza.app](https://cloud.eliza.app) is a single-page app that did not render in my fetch), Eliza-1 local models (2B to 27B text tiers on Gemma 4), OS distributions ([README](https://github.com/elizaOS/eliza)). The 2026-08-16 newsletter reports about 16% production agent-provisioning failures after 2026-08-06.
- x402 usage: none visible on x402scan. Real Eliza Cloud x402 top-up volume is unknown.

### Last six months
- Commits to the monorepo by month: Apr 4,802 (whole month), May 8,686, Jun 6,083, Jul 8,132, Aug 8,975, Sep 4,234, Oct 1-11 5,280; about 46,000 in total ([activity API](https://api.github.com/repos/elizaOS/eliza/stats/commit_activity)). Last commit 2026-10-11.
- Top authors in the window: lalalune 16,873; "claude" 13,177; NubsCarson 5,704; Dexploarer 969; 0xSolace 928; wakesync 822; ss251 812; bots 1,798; cursoragent 441; wtfsayo 428 ([contributors API](https://api.github.com/repos/elizaOS/eliza/stats/contributors)). The Claude, Cursor and Codex accounts together are about 30% of commits, and Shaw's own count may include AI-assisted work. 131 authors committed in the window (per month: Apr 17, May 26, Jun 27, Jul 15, Aug 79, Sep 37, Oct 30).
- x402: 73 commits mention x402 (Jun 13, Jul 15, Aug 23, Sep 5, Oct 17), including 2026-10-11 "verify the x402 top-up wallet signature before settling payment" and budget and refund fixes in early October ([commit search](https://github.com/search?q=repo%3AelizaOS%2Feliza+x402&type=commits)).
- Releases: npm `@elizaos/core` published 175 versions from 2026-04-11 to 2026-06-28 (155 in April), then none; the last is 2.0.3-beta.7 ([npm](https://registry.npmjs.org/@elizaos/core)). GitHub releases: `v2.0.3-beta.x` (2026-06-20 to 07-16) and "pr-evidence" prereleases to 2026-09-26; tags `v2.0.11-beta.4` to `.7` exist, dates unread.
- Dated items from the project's monthly summaries ([May](https://github.com/elizaOS/knowledge/blob/main/github/summaries/month/2026-05-01.md), [June](https://github.com/elizaOS/knowledge/blob/main/github/summaries/month/2026-06-01.md), [July](https://github.com/elizaOS/knowledge/blob/main/github/summaries/month/2026-07-01.md), [August](https://github.com/elizaOS/knowledge/blob/main/github/summaries/month/2026-08-01.md)): May hardening and plugin build changes; June Eliza Cloud Apps and unified billing; July payment safeguards, 240+ LifeOps scenarios, mobile voice; August eliza.army leaderboard and Cloud under eliza.app. The September and October summaries are empty and the daily RSS briefings have errored since at least 2026-09-21, so the commit log is the only source for those months: OS flashing tools, Gmail, calendar, wallet, web-search and x402 fixes.

### Pace verdict
Very fast by commit count, but not comparable with the other two. About 30% of commits come from AI tool accounts, and eliza.army invites outside agents to contribute. CONTRIBUTING.md now limits agent-written issues and low-value PRs ([file](https://github.com/elizaOS/eliza/blob/develop/CONTRIBUTING.md)). Official releases look weaker than the commit count: npm publishing stopped on 2026-06-28. For x402 there is steady, serious work (hardening commits through 2026-10-11) but no visible market use.

### Direction
Stated: "Your agentic operating system" (README); the Eliza personal agent, Eliza Cloud, local inference, OS images, and Slop; "starting over" without a token. The shipping record matches this. x402 is a billing and seller rail for Cloud, secondary to strategy. The Slop reward currency is not documented in anything I could read.

### Competitors
Agent runtimes: OpenClaw, Hermes Agent, LangGraph, Vercel AI SDK, Coinbase AgentKit, Daydreams Lucid. x402 facilitators: Coinbase, PayAI, Dexter. Other notes cover these.

### Green and red flags
- Green: a large, active MIT codebase; deep x402 code across facilitator, client, seller and billing; open about the token's end; ships daily.
- Red: founder declared the token dead and the foundation is winding down after a class-action settlement that took the remaining treasury; docs stale (tokenomics, no x402 page in the live index); no visible x402 usage; many new or agent contributor accounts (quality and supply-chain risk); no funding information; CoinGecko still lists the token with an unofficial-looking X account (`ElizaEcoFund`) while the project's X is @elizaOS; the project's own daily briefing feed is failing.

### Verdict
Serious builder (software). Momentum: Accelerating in code, Dead for the token.
It is the largest codebase of the three and it keeps adding x402 features, but the business behind it has just lost its token, its treasury and its foundation, and the founder says he is starting over. Expect Eliza Cloud (credits, x402 top-ups, hosting) and the Slop contribution network to be the next revenue attempts. Do not treat $elizaOS as an x402 token any more. Watch the x402 commit stream and whether any x402 volume shows up on x402scan.

### Tracking card
- Sites: https://elizaresearch.ai, https://eliza.app, https://cloud.eliza.app, https://os.eliza.app. Docs: https://docs.elizaos.ai (llms.txt; TLS errored on my last fetch). Knowledge base: https://github.com/elizaOS/knowledge (RSS in the repo at https://raw.githubusercontent.com/elizaOS/knowledge/main/rss/feed.xml, currently erroring). Atom: https://github.com/elizaOS/eliza/commits/develop.atom.
- GitHub: https://github.com/elizaOS; repos `eliza` (default branch `develop`), `knowledge`, `hub`, `os`, `benchmarks`, `docs`.
- X: @elizaOS (GitHub org field, site link); @shawmakesmagic, @nubsvault, @0xShadow, @0xSolace_, @thescoho, @sayodotfun. CoinGecko lists @ElizaEcoFund for the token.
- Farcaster: https://farcaster.xyz/elizaos (fid 1107323, "Open source for all"; CoinGecko lists it). Discord: https://discord.gg/elizaos (in the project's docs). Telegram: unconfirmed.
- Token: Solana `DuMbhu7mvQvqQHGcnikDgb4XegXJRyhUBfdU22uELiZA`; Ethereum, Base, BNB `0xea17Df5Cf6D172224892B5477A16ACb111182478`.
- x402scan: no facilitator entry; origin `x402.elizaos.ai` id d7de08df-6c7b-478e-b916-328890c05bc1 (0 transactions).
- Dune: no project dashboard found; Eliza is not in DefiLlama's x402 facilitator adapter.
- Code to watch: `packages/cloud/shared/src/lib/services/x402-facilitator.ts`, `plugins/plugin-wallet/src/sdk/x402/`, `packages/agent/src/middleware/x402/`.

### Sources (accessed 2026-10-11)
https://www.theblock.co/post/410774/eliza-labs-native-token-dead (2026-08-05); https://decrypt.co/374958/eliza-ai-token-dead-shuts-down-foundation-lawsuit (2026-08-05); https://www.theblock.co/post/371639/eliza-labs-ai16z-elizaos-token-migration (2025-09-25); https://thedefiant.io/news/tokens/eliza-labs-shaw-walters-says-ai16z-token-is-dead-after-settling-burwick-law-class-action (headline only); https://docs.elizaos.ai/tokenomics; https://docs.elizaos.ai/llms.txt; https://github.com/elizaOS/eliza; https://github.com/elizaOS/knowledge; https://github.com/elizaOS/hub; https://elizaresearch.ai; https://api.coingecko.com/api/v3/coins/elizaos; Blockscout, GeckoTerminal, Base RPC; Warpcast public API (Farcaster); npm registry; GitHub REST API.

---

## Comparison table

| | Daydreams | Virtuals Protocol | elizaOS |
|---|---|---|---|
| x402 role | Facilitator, SDK, seller (Task Market) | ACP payment rail with a facilitator-style service; minor | Cloud facilitator, buyer, seller, billing; token presets |
| Is x402 central? | Yes, but small | No, optional rail | Secondary, for Cloud billing |
| Token | $DREAMS: Solana (pump.fun, 2025-01-19), Base copy via Hyperlane (2025-09-16); no utility | $VIRTUAL: Base (2024-03-14); launchpad liquidity pair; not used for ACP or x402 | $elizaOS: Solana plus Ethereum, Base, BNB; declared dead 2026-08-05 |
| Seriousness | Credible but small | Serious builder | Serious builder (software); token dead |
| Momentum | Slowing | Steady | Accelerating (code); token Dead |
| x402 usage on x402scan | 496 requests and $775 in 30 days; 11.8M transactions all-time, 81% in Nov 2025 | 2,791 transactions and $28 in 30 days; 2.0M transactions and $4.3M all-time, down about 99% since April | None visible |
| Commits since April | about 88 | about 470 in three core repos | about 46,000 (30% AI accounts) |
| Trend-hopping (1-5) | 3 | 3 | 4 |
