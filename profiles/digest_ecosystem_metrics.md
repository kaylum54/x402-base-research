# Digest: x402 on Base, ecosystem map and metrics (from notes dated 2026-10-11)

Source: `ecosystem_map_and_metrics.md`, the researcher's notes (about 27,000 words). Nothing here is new research. Base figures cover 2026-04-11 to 2026-10-11 (184 days) unless a row says otherwise ("window"). "30d" means the 30 days to 2026-10-11. The data pulls were made on 2026-10-11 between about 10:50 and 12:00 UTC.

Sections: 1 master list, 2 ranked uncovered projects, 3 Base metrics, 4 data sources and quirks, 5 inferences and gaps. Sub-numbers (1.3a, 1.4, 3.6, 3.9 and so on) follow the source notes, so the cross-references inside section 2 still work. Group labels in square brackets are the other researchers' assignments. UNCOVERED means the project is on none of the assigned lists.

## 1. Master list

### Takeaway
x402.org/ecosystem no longer exists (HTTP 404 on 2026-10-11; the site was deprecated in the repo on 2026-07-07). The list is rebuilt from that page's last repo snapshot (206 entries), the 29 facilitators x402scan shows settling on Base, the 135-token CoinGecko "x402 Ecosystem" category (62 tokens have a Base contract), and the Base sellers visible in x402scan and Coinbase Bazaar usage data. Only 33 of the 206 directory entries show 100 or more Base settlements or Bazaar calls in the last 30 days (another 21 show 1 to 99), 116 show no Base footprint at all by domain match, and 162 of 206 are not on the assigned list. 37 of the 62 Base-contract CoinGecko tokens show no x402 footprint that could be matched.

### Cited Findings

#### 1.0 Method, conventions and coverage counts
- **Rows.** One row per project. Assigned names are in 1.6 (facilitators also in 1.2, mint-era recipients in 1.5). Other projects with Base activity are in 1.1, 1.2, 1.4 and 1.10; every Base token is in 1.3. Entries with no Base footprint, no Base token and no assignment are counted, not listed.
- **"tx" and "USDC".** x402scan counts indexed USDC transfers made by facilitators, not HTTP calls. USDC has 6 decimals ([docs](https://docs.x402.org/core-concepts/network-and-token-support); the Bazaar's `amount: "20000"` for a service priced "$0.02" confirms it). x402scan's blind spots are in 4.1.
- **Status rule (researcher's, Base only).** active = at least 100 Base settlements (or Bazaar calls) in the last 30 days, or a facilitator whose last Base settlement is within 30 days; low activity = 10 to 99; minimal = 1 to 9; dormant = last Base activity 31 to 180 days ago; dead on Base = more than 180 days; unverified = no Base footprint matched. "Dormant" or "dead on Base" does not mean dead on other chains or off-chain.
- **Footprint matching.** Each website is reduced to its registrable domain and matched against x402scan's registered origins (30-day and all-time Base lists) and the Bazaar host index. A project that sells from another domain, or shares a payTo address, can be missed or over-counted. "No footprint matched" means unverified, not inactive.
- **Chains (digest convention).** The union of chains where x402scan saw settlements (Base; Solana top-100 lists, which cover only part of Solana's 705 registered recipients), chains advertised in the Bazaar `accepts` field (supply, not usage) and chains a facilitator declares; testnets dropped. Rows say "Multi: ..." when more than Base appears, otherwise Base only. Base token contracts are as CoinGecko lists them (Basescan pattern `https://basescan.org/token/<contract>`).

| Cohort | Count (computed from the source tables and re-checked row by row) |
|---|---|
| Directory entries | 206: 44 assigned, 162 UNCOVERED |
| Active (100+ Base settlements or Bazaar calls in 30d) | 33 (12 assigned, 21 UNCOVERED) |
| 1 to 99 in 30d (low activity or minimal) | 21, including 4 facilitators the source labels "active (<100 tx in 30d)": Questflow, Dexter, Heurist, Treasure |
| Dormant | 22 (4 assigned, 18 UNCOVERED) |
| Dead on Base | 14 (1 assigned, 13 UNCOVERED) |
| No Base footprint matched | 116 (22 assigned, 94 UNCOVERED) |
| x402scan facilitators above the 100-tx floor | 31: 18 active, 9 dormant, 2 dead on Base, 2 not on Base |
| CoinGecko "x402 Ecosystem" tokens | 135: 62 with a Base contract (25 with a matched footprint, 37 without), 73 without |

#### 1.1 Official x402.org directory, last snapshot (206 entries): UNCOVERED entries with a Base footprint
Source: the [206 partner metadata files](https://github.com/x402-foundation/x402/tree/2b74587b29bd7d986c4c562e46444d74606b0e1d/typescript/site/app/ecosystem/partners-data) at the commit before the site was removed, and the [deprecation commit (2026-07-07)](https://github.com/x402-foundation/x402/commit/7be420af0b). Native categories: Services/Endpoints 79, Infrastructure & Tooling 66, Facilitators 33, Client-Side Integrations 24, Learning & Community Resources 3, Web3 Application & Infrastructure 1. Category is the researcher's mapping. Group is UNCOVERED for every entry in 1.1.

Of the 162 UNCOVERED entries, 68 have a Base footprint: 29 rows below (active, low or minimal), 28 dormant or dead (listed after the table), and 11 carried elsewhere (facilitator-only or duplicate entries FluxA, Ultravioleta DAO, OpenFacilitator, Treasure Facilitator, Bitrefill Facilitator, RelAI Facilitator, xEcho Facilitator, WorldFun Facilitator and T54 XRPL x402 Facilitator are in 1.2 or 1.6; BlockRun.AI and Locus are in 1.4). Rows are sorted by 30-day Base settlements or Bazaar calls.

| Name | Category [chains if not Base only; token] | Base signal (30d to 2026-10-11) | Status |
|---|---|---|---|
| [dTelecom STT](https://x402stt.dtelecom.org) | Seller / API | 30d 16,508 tx/$36,243; all-time 52,722 tx/$111,956; last 2026-10-11 | active |
| [Cascade](https://cascade.fyi) | SDK / tooling (payment splits; facilitator) [Multi: Base, Monad, Solana] | facilitator[cascade]: 30d 0 tx/$0; all-time 33,485 tx/$126; last 2026-08-14; seller: 30d 5,966 tx/$16; all-time 28,121 tx/$102; last 2026-10-11; Bazaar 509 calls (12 res); Solana 30d 2,367 tx/$12; all-time 11,108 tx/$52 | active |
| [Exa](https://exa.ai/) | Seller / API [Multi: Base, Arc, Solana, World Chain] | Bazaar 5,456 calls (2 res), last 2026-10-11; Solana 30d 1,021 tx/$8; all-time 1,878 tx/$16 | active |
| [twit.sh](https://twit.sh) | Seller / API | 30d 4,793 tx/$35; all-time 273,958 tx/$21,792; last 2026-10-11; Bazaar 3,739 calls (17 res) | active |
| [Nansen](https://docs.nansen.ai/getting-started/x402-payments) | Seller / API [Multi: Base, eip155:56, Monad, Solana, X Layer] | 30d 4,661 tx/$92; all-time 43,793 tx/$1,119; last 2026-10-11; Bazaar 3,578 calls (32 res); Solana 30d 0 tx/$0; all-time 5,631 tx/$91 | active |
| [Slinky Layer](https://slinkylayer.ai/) | Marketplace / token [token SLINKY: 0xbb3d6c47379abb4713acffffa27483b726ee67db] | 30d 3,181 tx/$30; all-time 23,927 tx/$1,087; last 2026-10-11 | active |
| [Mycelia Signal](https://myceliasignal.com) | Seller / API | 30d 1,153 tx/$61; all-time 11,013 tx/$795; last 2026-10-11; Bazaar 1,117 calls (176 res) | active |
| [x402engine](https://x402engine.app) | Seller / API [Multi: Base, eip155:4326, Solana] | 30d 907 tx/$46; all-time 34,147 tx/$248; last 2026-10-11; Bazaar 776 calls (43 res); Solana 30d 85 tx/$4; all-time 970 tx/$21 | active |
| [Bitrefill](https://www.bitrefill.com) | Seller / API (also directory entry Bitrefill Facilitator: facilitator all-time 107 tx/$411, last 2026-04-30) [Multi: Base, Arbitrum, lnbtc, Polygon, Solana] | 30d 698 tx/$835; all-time 1,526 tx/$2,176; last 2026-10-11; Bazaar 337 calls (8 res); Solana 30d 128 tx/$78; all-time 734 tx/$1,144 | active |
| [Browserbase](https://browserbase.com) | Seller / API [Multi: Base, Solana] | Bazaar 546 calls (8 res), last 2026-10-11 | active |
| [Moltalyzer](https://moltalyzer.xyz) | Seller / API | 30d 479 tx/$8; all-time 4,279 tx/$60; last 2026-10-11; Bazaar 69 calls (1 res) | active |
| [AsterPay](https://asterpay.io) | Settlement / off-ramp [Multi: Base, Arbitrum, eip155:1, eip155:1187947933, Optimism, Polygon] | 30d 207 tx/$4; all-time 387 tx/$5; last 2026-10-11; Bazaar 194 calls (19 res) | active |
| [Laso Finance](https://agents.laso.finance) | Seller / API [Multi: Base, Solana] | 30d 122 tx/$1,487; all-time 1,427 tx/$16,077; last 2026-10-10; Bazaar 164 calls (8 res); Solana 30d 111 tx/$267,444; all-time 272 tx/$612,817 | active |
| [Messari](https://messari.io/x402) | Seller / API [Multi: Base, Solana, X Layer] | 30d 156 tx/$37; all-time 2,351 tx/$531; last 2026-10-08; Bazaar 29 calls (1 res) | active |
| [Spraay x402 Gateway](https://docs.spraay.app) | Gateway [Multi: Base, Robinhood Chain, Solana] | 30d 143 tx/$2; all-time 4,387 tx/$89; last 2026-10-10; Bazaar 155 calls (32 res) | active |
| [Zerion](https://zerion.io/agents) | Seller / API [Multi: Base, Solana] | 30d 76 tx/$1; all-time 746 tx/$7; last 2026-10-09; Bazaar 98 calls (16 res) | low activity |
| [Minifetch](https://minifetch.com) | Seller / API [Multi: Base, Solana] | 30d 97 tx/$0; all-time 3,910 tx/$10; last 2026-10-11; Bazaar 71 calls (7 res) | low activity |
| [Arch AI Tools](https://archtools.dev) | Seller / API [Multi: Base, Polygon] | 30d 72 tx/$1; all-time 338 tx/$10; last 2026-10-10; Bazaar 74 calls (20 res) | low activity |
| [Run402](https://run402.com) | Seller / API | 30d 7 tx/$0; all-time 138 tx/$16; last 2026-10-10; Bazaar 62 calls (3 res) | low activity |
| [AgentMail](https://docs.agentmail.to/integrations/x402) | Seller / API [Multi: Base, Solana] | 30d 45 tx/$18; all-time 2,024 tx/$655; last 2026-09-29; Solana 30d 2,249 tx/$92; all-time 3,662 tx/$244 | low activity |
| [Proofivy](https://proofivy.com) | Seller / API | 30d 38 tx/$28; all-time 567 tx/$37; last 2026-10-09; Bazaar 29 calls (4 res) | low activity |
| [SocioLogic](https://www.sociologic.ai/x402-rng) | Seller / API | 30d 35 tx/$0; all-time 440 tx/$15; last 2026-10-08; Bazaar 26 calls (4 res) | low activity |
| [x402-secure](https://x402-secure.t54.ai/) | Trust / risk control (same domain and Base data as the directory entry T54 XRPL x402 Facilitator, which declares xrpl:0) [Multi: Base, Solana] | 30d 33 tx/$0; all-time 29,639,577 tx/$27,195; last 2026-10-10; Solana 30d 0 tx/$0; all-time 2,758,912 tx/$2,760 | low activity |
| [auor.io (Oreo)](https://auor.io) | Seller / API | 30d 17 tx/$0; all-time 989 tx/$5; last 2026-10-07 | low activity |
| [BlackSwan](https://blackswan.wtf) | Seller / API | 30d 12 tx/$0; all-time 7,739 tx/$108; last 2026-10-09; Bazaar 8 calls (2 res) | low activity |
| [Agent Camo](https://agentcamo.xyz) | Seller / API | 30d 5 tx/$0; all-time 2,314 tx/$27; last 2026-09-19 | minimal |
| [Alchemy](https://agents.alchemy.com/?utm_source=x&utm_medium=social&utm_campaign=x402) | Seller / API | Bazaar 4 calls (2 res), last 2026-10-08 | minimal |
| [AI Security Guard](https://aisecurityguard.io) | Trust / security | 30d 1 tx/$0; all-time 212 tx/$21; last 2026-09-28 | minimal |
| [Soundside](https://soundside.ai/docs/x402) | Seller / API | Bazaar 1 calls (1 res), last 2026-10-08 | minimal |

- **Dormant on Base, 15 (last settlement 31 to 180 days ago; all-time Base figures; by days idle).** With at least 1,000 tx or $100 all-time: [Einstein AI](https://emc2ai.io) (seller 1,161 tx/$821, last 2026-08-30; 42d idle); [Genbase](https://genbase.fun) (seller 6,342 tx/$1,171, last 2026-08-24; 48d idle); [Obol](https://obol.sh) (facilitator 1,200 tx/$3, last 2026-08-12; seller 50 tx/$61, last 2026-07-14; 59d idle); [AIsa](https://aisa.one) (seller 31,551,163 tx/$415,841, last 2026-08-07; 64d idle; Marketplace); [Neynar](https://neynar.com) (seller 37,451 tx/$179, last 2026-07-17; 85d idle); [x402jobs](https://x402.jobs) (facilitator 7,600 tx/$366, last 2026-05-17; Solana 772 tx/$1,081; 147d idle; Agent platform (workflow builder); JOBS: Solana only (no Base contract on CoinGecko)); [SerenAI x402 Gateway](https://serendb.com) (seller 3,437 tx/$19, last 2026-04-17; 177d idle). Below both thresholds: [AdEx AURA API](https://guide.adex.network/), [Agent Health Monitor](https://agenthealthmonitor.xyz), [Agoragentic](https://agoragentic.com/api/x402/info), [Orac](https://orac-safety.orac.workers.dev), [Kodo](https://www.kodo.fun), [GenVox Crypto Sentiment API](https://api.genvox.io), [AskClaude](https://askclaude.shop), [Bloomfilter](https://bloomfilter.xyz/docs).
- **Dead on Base, 13 (more than 180 days idle).** With at least 1,000 tx or $100 all-time: [AiMo Network](https://aimo.network) (seller 973,786 tx/$834, last 2026-03-09; Solana 87,097 tx/$1,969; 215d idle); [Grove API](https://grove.city/api) (seller 796 tx/$406, last 2026-03-03; 221d idle; Payments (tipping)); [ClawdVine](https://clawdvine.sh) (seller 237 tx/$228, last 2026-02-19; 233d idle); [Elsa x402](https://x402.heyelsa.ai) (seller 5,189 tx/$48, last 2026-02-02; 251d idle; Facilitator / DeFi API; ELSA: 0x29cc30f9d113b356ce408667aa6433589cecbdca); [Firecrawl](https://firecrawl.dev) (seller 1,151 tx/$11, last 2026-02-01; 252d idle); [Ubounty](https://ubounty.ai) (seller 16 tx/$217, last 2025-12-15; 300d idle; Marketplace). Below both thresholds: [Freepik](https://freepik.com), [DiamondClaws DeFi Intelligence](https://diamondclaws.io), [ActionGate](https://api.actiongate.xyz/docs), [tip.md](https://www.tip.md/documentation?tab=mcp-server), [Rencom](https://x402.rencom.ai), [Ekai Labs](https://ekailabs.xyz), [Proxy402](https://proxy402.com/).

**No Base footprint matched (116 entries).** 22 are assigned and appear in 1.6. 94 are UNCOVERED: Seller/API 26, SDK/tooling/docs 18, Facilitator 17, agent platform/app/client 12, trust/identity/security 10, wallet/payments 5, discovery/analytics 4, other 2 (Pay.sh marketplace, Stellar platform). Ten of the 17 unverified facilitators declare Base but show no x402scan settlements: 0xArchive (HyperEVM, Base), 0xmeta AI, AutoIncentive, fretchen.eu (Optimism, Base), GoPlausible (Algorand, Base, Solana), Hydra Protocol, KAMIYO, Kobaru (Solana, Base, SKALE), Nevermined, xpay. One has a Solana-only footprint: x402wall (Solana 30d 0 tx/$0; all-time 358 tx/$10,405).

#### 1.2 Facilitators tracked by x402scan (Base settlements and status)
Source: [x402scan facilitator list, Base, all time](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D) (31 facilitators pass the 100-tx floor all-time; 29 settle on Base; 13 pass it in the last 30 days: [30-day list](https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)) and the [facilitator registry package](https://github.com/Merit-Systems/x402scan/tree/main/packages/external/facilitators/src/facilitators) (33 ids). Tokens from CoinGecko where one exists.

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
Source: [CoinGecko category API](https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&category=x402-ecosystem&per_page=250) (135 coins on 2026-10-11) joined to [CoinGecko platform data](https://api.coingecko.com/api/v3/coins/list?include_platform=true) for contracts; category page [coingecko.com/en/categories/x402-ecosystem](https://www.coingecko.com/en/categories/x402-ecosystem). Category membership is not proof of x402 usage: the list includes Chainlink, EigenCloud, peaq and SKALE alongside micro-caps. Coin-page categories were fetched only for the 62 Base-contract tokens. Sites come from CoinGecko pages or the [DexScreener token API](https://api.dexscreener.com/tokens/v1/base/0x4b5d32a07b8d3ec5d6928caa30196f8dd6a7c5a9) and are missing for 2 of 62. No price or market-cap figures are used. A blank Group means UNCOVERED.

**1.3a Tokens with a Base contract (62)**

*With an x402 footprint matched by website domain (25)*

| Token (site) | Ticker | Base contract | CoinGecko category | x402 footprint matched (as of 2026-10-11) | Group |
|---|---|---|---|---|---|
| [Chainlink](https://www.coingecko.com/en/coins/chainlink) ([chain.link](https://chain.link/)) | LINK | `0x88fb150bdc53a65fe94dea0c9ba0a6daf8c6e196` | Infrastructure, Oracle | Bazaar 3 res / 46K calls30 |  |
| [Treasure](https://www.coingecko.com/en/coins/magic) ([treasure.lol](https://treasure.lol/)) | MAGIC | `0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43` | AI, Smart Contract Platform | facilitator `treasure`: 2.5K tx / $400 all-time; AI Frens launchpad (x402 character tokens) |  |
| [BankrCoin](https://www.coingecko.com/en/coins/bankercoin-2) ([bankr.bot](https://bankr.bot)) | BNKR | `0x22af33fe49fd1fa80c7149773dde5890d3c76f3b` | AI, AI Agents | Bankr x402 SDK repos (BankrBot/x402-cli-example 3 stars); no Base seller footprint matched | [agent apps] Bankr |
| [Elsa](https://www.coingecko.com/en/coins/elsa) ([heyelsa.ai](https://heyelsa.ai)) | ELSA | `0x29cc30f9d113b356ce408667aa6433589cecbdca` | AI, AI Agents | Elsa x402 origin (x402.heyelsa.ai): 5.2K tx / $48 all-time, last 2026-02-02 (dead on Base) |  |
| [Anyspend](https://www.coingecko.com/en/coins/anyspend) ([anyspend.com](https://anyspend.com)) | ANY | `0xc17dda248e2d50fc006d8febb5a406dd31972712` | Infrastructure | facilitator `anyspend`: 521K tx / $141K all-time (last 2026-08-17); x402.anyspend.com seller $25K in 6 months |  |
| [Daydreams](https://www.coingecko.com/en/coins/daydreams) ([www.dreams.fun](https://www.dreams.fun)) | DREAMS | `0x176383016bb310c9f1c180dc6729d5e28104e602` | AI, AI Agents | facilitator `daydreams`: 11.8M tx / $2.76M all-time on Base (peak Nov 2025); 496 tx in last 30d | [agent frameworks] Daydreams |
| [vAPI Network](https://www.coingecko.com/en/coins/vapi-network) ([vapinetwork.ai](https://vapinetwork.ai/)) | VAPI | `0x1ea8deb921aa6015f4938010c848140b98108dd2` |  | Bazaar 1 res / 12 calls30 |  |
| [Aubrai by Bio](https://www.coingecko.com/en/coins/aubrai-by-bio) ([aubr.ai](https://aubr.ai/)) | AUBRAI | `0x9d56c29e820dd13b0580b185d0e0dc301d27581d` | AI, AI Agents | x402-api.aubr.ai: 14.5K tx / $321 in 6 months; 2.3K Bazaar calls30 |  |
| [Ethy AI](https://www.coingecko.com/en/coins/ethy-ai) ([ethyai.app](https://ethyai.app/)) | ETHY | `0xc44141a684f6aa4e36cd9264ab55550b03c88643` | AI, AI Applications | x402scan Base seller: 30d 0 tx/$0; all-time 24 tx/$9; last 2025-11-15 |  |
| [Slinky Layer](https://www.coingecko.com/en/coins/slinky-layer) ([slinkylayer.ai](https://slinkylayer.ai)) | SLINKY | `0xbb3d6c47379abb4713acffffa27483b726ee67db` | AI, Privacy | slinkylayer.ai: 3.2K tx / $30 in last 30d; 23.9K tx / $1.1K all-time |  |
| [Otto AI](https://www.coingecko.com/en/coins/otto-ai) ([useotto.xyz](https://useotto.xyz/)) | OTTO | `0x380337d0180db7d0df76ac4faae2fcea908ee1fc` | AI, AI Agents | ottoai.services: 178K tx / $433 all-time, 3.3K tx / $30 in last 30d; 2.3K Bazaar calls30 | [data/AI sellers] Otto AI |
| [Ping](https://www.coingecko.com/en/coins/ping) | PING | `0xd85c31854c2b0fb40aaa9e2fc4da23c21f829d46` | Meme, Base Meme | Oct 2025 pay-to-mint experiment (Chainalysis); CoinGecko lists Base contract | [token experiments] PING |
| [Heurist](https://www.coingecko.com/en/coins/heurist) ([heurist.ai](https://heurist.ai)) | HEU | `0xef22cb48b8483df6152e1423b19df5553bbd818b` | AI, DePIN | facilitator `heurist`: 8.0M tx / $30K all-time; x402 vending machine origin 105.6K tx / $43.3K | [token facilitators] Heurist |
| [Gloria AI](https://www.coingecko.com/en/coins/gloria-ai) ([itsgloria.ai](https://itsgloria.ai/)) | GLORIA | `0x3b313f5615bbd6b200c71f84ec2f677b94df8674` | AI, AI Agents | api.itsgloria.ai origin: 19.2K tx / $359 all-time; 28 tx in last 30d | [data/AI sellers] Gloria AI |
| [Neurobro](https://www.coingecko.com/en/coins/neurobro) ([neurobro.ai](https://neurobro.ai)) | BRO | `0xc796e499cc8f599a2a8280825d8bda92f7a895e0` | AI, AI Agents | x402scan Base seller: 30d 3 tx/$3; all-time 63 tx/$42; last 2026-09-26 |  |
| [Capminal](https://www.coingecko.com/en/coins/capminal) ([www.capminal.ai](https://www.capminal.ai)) | CAP | `0xbfa733702305280f066d470afdfa784fa70e2649` | AI, AI Agents | x402scan Base seller: 30d 16 tx/$0; all-time 346 tx/$11; last 2026-10-11; Bazaar 1 res / 15 calls30 |  |
| [MiroShark](https://www.coingecko.com/en/coins/miroshark) ([miroshark.xyz](https://miroshark.xyz)) | MIROSHARK | `0xd7bc6a05a56655fb2052f742b012d1dfd66e1ba3` | AI, AI Framework | x402scan Base seller: 30d 19 tx/$19; all-time 51 tx/$50; last 2026-10-09; Bazaar 1 res / 48 calls30 |  |
| [Meridian](https://www.coingecko.com/en/coins/meridian-2) ([www.mrdn.finance](https://www.mrdn.finance)) | MRDN | `0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6` | AI | facilitator `mrdn`: $3.79M all-time, >96% round-trip between the same wallets (see 3.6) | [token facilitators] Meridian |
| [x420](https://www.coingecko.com/en/coins/x420) ([x420.dev](https://x420.dev)) | X420 | `0x68e284f21d04d4d62398c290ec3ef41c97f80b07` | Meme | x8004.x420.dev origin: 144.8K tx / $31.2K all-time | [token experiments] x402-branded token |
| [Aurra by Virtuals](https://www.coingecko.com/en/coins/aurra-by-virtuals) ([aurracloud.com](https://aurracloud.com)) | AURA | `0xdcaa5e062b2be18e52ea6ed7ba232538621ddc10` | AI, AI Applications | x402scan Base seller: 30d 0 tx/$0; all-time 1.2K tx/$118; last 2026-05-10 | [token facilitators] AurraCloud? (name match unverified) |
| [WachAI](https://www.coingecko.com/en/coins/wachxbt) ([wach.ai](https://wach.ai/)) | WACH | `0xcc9ad02796dec5f4f0710df80c1f011af85eb9e1` | AI, AI Agents | x402scan Base seller: 30d 185 tx/$1; all-time 524 tx/$22; last 2026-10-11; Bazaar 1 res / 5 calls30 |  |
| [AInalyst](https://www.coingecko.com/en/coins/ainalyst) ([ainalyst.xyz](https://ainalyst.xyz/)) | AIN | `0xe47dd5197c5b5194cbe10b0333ed45570fb63eb0` | AI, AI Agents | ainalyst-api.xyz (AinX402): 8.9M tx / $2.74M all-time, mostly Oct-Dec 2025; last 2026-08-30 |  |
| [TRANSLATE](https://www.coingecko.com/en/coins/translate) ([www.apinow.fun](https://www.apinow.fun/try/apinowfun/translate-TRANSLATE)) | TRANSLATE | `0x5cd9166494673c15cbdfe8750def8bbab80a5b07` |  | x402scan Base seller: 30d 78 tx/$1; all-time 14K tx/$228; last 2026-10-09 |  |
| [Sniper Search](https://www.coingecko.com/en/coins/sniper-search) ([snipersearch.fun](https://snipersearch.fun/)) | SS | `0xa2d4aec94ba0896d95ccc5451c9525b9ec0314de` |  | x402scan Base seller: 30d 0 tx/$0; all-time 144 tx/$5; last 2026-06-18 |  |
| [Token Metrics AI [OLD]](https://www.coingecko.com/en/coins/token-metrics-ai) ([www.tokenmetrics.com](https://www.tokenmetrics.com/)) | TMAI | `0xca4569949699d56e1834efe9f58747ca0f151b01` | AI, AI Agents | x402scan Base seller: 30d 0 tx/$0; all-time 3.2K tx/$105; last 2025-12-10 |  |

*No x402 footprint matched (37)*

| Token (site) | Ticker | Base contract | Group |
|---|---|---|---|
| [EigenCloud (prev. EigenLayer)](https://www.coingecko.com/en/coins/eigenlayer) ([www.eigencloud.xyz](https://www.eigencloud.xyz/)) | EIGEN | `0x2081ab0d9ec9e4303234ab26d86b20b3367946ee` |  |
| [peaq](https://www.coingecko.com/en/coins/peaq-2) ([www.peaq.xyz](https://www.peaq.xyz/)) | PEAQ | `0x9b56b112bbd6343a8961a093315a9a60b8cb1f36` |  |
| [Acurast](https://www.coingecko.com/en/coins/acurast) ([acurast.com](https://acurast.com/)) | ACU | `0xc5fed7c8ccc75d8a72b601a66dffd7a489073f0b` |  |
| [SKALE](https://www.coingecko.com/en/coins/skale) ([skale.space](https://skale.space/)) | SKL | `0xb9caa63e09c646c1ec79acb2158d173e64a5fed3` |  |
| [FLOCK](https://www.coingecko.com/en/coins/flock-2) ([flock.io](https://flock.io/)) | FLOCK | `0x5ab3d4c385b400f3abb49e80de2faf6a88a7b691` |  |
| [OpenServ](https://www.coingecko.com/en/coins/openserv) ([openserv.ai](https://openserv.ai/)) | SERV | `0x5576d6ed9181f2225aff5282ac0ed29f755437ea` |  |
| [Autonolas](https://www.coingecko.com/en/coins/autonolas) ([olas.network](https://olas.network)) | OLAS | `0x54330d28ca3357f294334bdc454a032e7f353416` | [agent apps] Olas |
| [PRXVT by Virtuals](https://www.coingecko.com/en/coins/prxvt-by-virtuals) ([prxvt.com](http://prxvt.com/)) | PRXVT | `0x4b5d32a07b8d3ec5d6928caa30196f8dd6a7c5a9` | [agent frameworks] Virtuals ecosystem token (inferred) |
| [Sally A1C](https://www.coingecko.com/en/coins/sally-a1c) ([a1c.io](https://a1c.io/)) | A1C | `0x1f1c695f6b4a3f8b05f2492cef9474afb6d6ad69` |  |
| [ArAIstotle](https://www.coingecko.com/en/coins/araistotle) ([www.facticity.ai](https://www.facticity.ai)) | FACY | `0xfac77f01957ed1b3dd1cbea992199b8f85b6e886` |  |
| [Regent](https://www.coingecko.com/en/coins/regent-2) ([www.regents.sh](https://www.regents.sh/)) | REGENT | `0x6f89bca4ea5931edfcb09786267b251dee752b07` |  |
| [ROBA](https://www.coingecko.com/en/coins/roba) ([www.robalabs.com](https://www.robalabs.com/)) | ROBA | `0xe88419a3fc78364cfe3de88080ee4853fab754c6` |  |
| [Alphakek](https://www.coingecko.com/en/coins/alphakek-ai) ([www.alphakek.ai](https://www.alphakek.ai/)) | AIKEK | `0x681a09a902d9c7445b3b1ab282c38d60c72f1f09` |  |
| [Hive Intelligence](https://www.coingecko.com/en/coins/hive-intelligence) ([hiveintelligence.xyz](http://hiveintelligence.xyz)) | HINT | `0x91da780bc7f4b7cf19abe90411a2a296ec5ff787` |  |
| [Cod3x](https://www.coingecko.com/en/coins/cod3x) ([cod3x.org](https://Cod3x.Org)) | CDX | `0xc0d3700000c0e32716863323bfd936b54a1633d1` |  |
| [SMOL](https://www.coingecko.com/en/coins/smolcoin-2) ([smolcoin.lol](https://smolcoin.lol/)) | SMOL | `0xa4bbac7ed5bda8ec71a1af5ee84d4c5a737bd875` |  |
| [SANTA by Virtuals](https://www.coingecko.com/en/coins/santa-by-virtuals) ([santagent.xyz](https://santagent.xyz/)) | SANTA | `0x815269d17c10f0f3df7249370e0c1b9efe781aa8` | [agent frameworks] Virtuals ecosystem token (inferred) |
| [VPay](https://www.coingecko.com/en/coins/vpay) ([vpay.fund](https://vpay.fund/)) | VPAY | `0x98ac5b33a4ef1151f138941c979211599c2ff953` |  |
| [Maya World](https://www.coingecko.com/en/coins/maya-world) ([www.mayaworld.co](https://www.mayaworld.co)) | MAYA | `0x072915a43ac255cde1fa568218e5b6b10d0cb10f` |  |
| [Replicat-One by Virtuals](https://www.coingecko.com/en/coins/replicat-one-by-virtuals) ([replicats.ai](https://replicats.ai/)) | RCAT | `0x6af73d4579c70a24d52e4f4b43eecb2a75019f94` | [agent frameworks] Virtuals ecosystem token (inferred) |
| [MIO](https://www.coingecko.com/en/coins/mio) ([www.miocoin.lol](https://www.miocoin.lol/)) | MIO | `0xe19e7429ab6c1f9dd391faa88fbb940c7d22f18f` |  |
| [HEIR](https://www.coingecko.com/en/coins/heir) ([heir.es](https://heir.es)) | HEIR | `0x01e75e59eabf83c85360351a100d22e025a75bc2` |  |
| [Trackgood AI](https://www.coingecko.com/en/coins/trackgood-ai) ([trackgood.ai](https://trackgood.ai/)) | TRAI | `0xdd32659b1e7a6a6b3c6e96cd8a4c936bcfea0607` |  |
| [Loky by Virtuals](https://www.coingecko.com/en/coins/loky-by-virtuals) ([lokyai.com](https://lokyai.com/)) | LOKY | `0x1a3e429d2d22149cc61e0f539b112a227c844aa3` | [agent frameworks] Virtuals ecosystem token (inferred) |
| [StarkBot](https://www.coingecko.com/en/coins/starkbot) ([www.starkbot.ai](https://www.starkbot.ai/)) | STARKBOT | `0x587cd533f418825521f3a1daa7ccd1e7339a1b07` |  |
| [Dobi](https://www.coingecko.com/en/coins/dobi-2) ([dobi.guru](https://dobi.guru)) | DOBI | `0x931ef8053e997b1bab68d1e900a061305c0ff4fb` |  |
| [Arbus](https://www.coingecko.com/en/coins/arbus) ([arbus.ai](https://arbus.ai/)) | ARBUS | `0xbdc27118ca76b375c6887b0ff068afb03dfc21a0` |  |
| [Halo](https://www.coingecko.com/en/coins/halo-3) ([halo.zhc.company](https://halo.zhc.company/)) | HALO | `0x0a56431ecc9d0b39be0b1e27e795f4c4f19d0ba3` |  |
| [Karum](https://www.coingecko.com/en/coins/karum) ([www.karum.ai](https://www.karum.ai/)) | KARUM | `0xf3280115245a7470e7bbdd35e2b4f4094f511443` |  |
| [Otonix](https://www.coingecko.com/en/coins/otonix) | OTX | `0xf7e2a6226ffe0693dd85406ac3a8917cbea5dc40` |  |
| [NOD](https://www.coingecko.com/en/coins/nod) ([0xnod.com](https://0xnod.com/)) | NOD | `0xdfb51ec9941cc684b72dc2b0f532d74a244e4ccf` |  |
| [$TRUST ME BROs by Virtuals](https://www.coingecko.com/en/coins/trust-me-bros-by-virtuals) ([trustmebros.fun](http://trustmebros.fun)) | TRUST | `0xc841b4ead3f70be99472ffdb88e5c3c7af6a481a` | [agent frameworks] Virtuals ecosystem token (inferred) |
| [The SWARM](https://www.coingecko.com/en/coins/the-swarm) ([www.slamai.xyz](https://www.slamai.xyz/)) | SWARM | `0xea87169699dabd028a78d4b91544b4298086baf6` |  |
| [ZorbyAI](https://www.coingecko.com/en/coins/zorbyai) ([zorby.wtf](https://zorby.wtf/)) | $ZORBYAI | `0x3e04dee527a90ddfa1fe6f9e12a4d62677d00071` |  |
| [x402MKT](https://www.coingecko.com/en/coins/x402mkt) ([www.clanker.world](https://www.clanker.world/clanker/0xA763B711B55935f6D7BA2f93E1adF741E2446B07)) | LOOP | `0xa763b711b55935f6d7ba2f93e1adf741e2446b07` | [token experiments] x402-branded token (x402MKT) |
| [Dealer Node](https://www.coingecko.com/en/coins/dealer-node) ([dealernode.app](https://dealernode.app)) | DNODE | `0xa7f6e8a35d83228cc6c241c8dd0fb687552f75d1` |  |
| [BluePay](https://www.coingecko.com/en/coins/bluepay) ([bluepay.network](http://bluepay.network)) | BLUE | `0x15eda1086c54c148037597e9dc60e5a87b618aa1` |  |

**1.3b Category tokens with no Base contract (73).** 12 are assigned: PayAI Network and its [OLD] listing (PAYAI), Zauthx402 (ZAUTH), Dexter AI (DEXTER), Eliza (ELIZA), Primer (PR), Veilra by ElizaOS (VEILRA) and five x402-branded experiments (x402 Singularity Layer SGL, x4Pay X4PAY, Robinhood Payments Protocol RPP402, AgentBank x402 Protocol, zk402). 61 are UNCOVERED, including x402jobs (JOBS, Solana only; also in 1.1). By CoinGecko chain: Solana 46 (43 Solana-only), BNB Smart Chain 11, Ethereum 9, Robinhood chain 9, Arc 3, peaq 2, Arbitrum One 1; Concordium lists none.


#### 1.4 Sellers and projects seen in Base usage data but absent from the official directory
Source: x402scan per-recipient daily series (candidate recipients: top 70 by USDC and by tx in the 7-day, 30-day and all-time lists, plus Meridian/FluxA counterparties) summed over 2026-04-11 to 2026-10-11 ([example series: BlockRun](https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xe9030014f5dae217d0a152f02a043567b16c1abf%22%5D%7D%7D%7D)), the x402scan 30-day lists, the [Bazaar API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0) and registry titles. Category is the researcher's reading of the project's own title or description. Group is UNCOVERED for every row except the last (Merit "Stable*" family, assigned [non-token infra]). BlockRun and Locus are also directory entries (BlockRun.AI, Locus); their figures are here, not in 1.1.

| Project | Category | Token (Base contract) | Chains seen | Base last 6 months (tx / USDC) | Base last 30d (tx / USDC) | Solana (x402scan top-100 lists) | Bazaar calls 30d | Last Base settlement | Status |
|---|---|---|---|---|---|---|---|---|---|
| [BlockRun](https://blockrun.ai) ([x402scan](https://www.x402scan.com/recipient/0xe9030014f5dae217d0a152f02a043567b16c1abf)) | LLM gateway / router (seller + agent routing) | none (not in CoinGecko x402 category) | Base, Solana | 27.0M / $450K | 83K / $1.5K | 30d 227K tx/$2.9K; all-time 22.5M tx/$293K | 79K | 2026-10-11 | active |
| [AX1 Console](https://ax1.vc) ([x402scan](https://www.x402scan.com/recipient/0x7284d41b5b852f2bd4c99bdf95043d84452d299c)) | Agent "launchpad" console; paid Base-token verdict API | none | Base | 412K / $8.2K | 407K / $8.1K | — | 409K | 2026-10-11 | active |
| [Cluster Protocol](https://api.clusterprotocol.ai) ([x402scan](https://www.x402scan.com/recipient/0x68396bd35874695ad86cd29410bd80a550991a2b)) | AI/agent infra ("Liberation Engine for Internet Capital Market") | CP 0x001aad84c21a5cd4d696c56d44866e9703c43f77 (CoinGecko coin list; not in x402 category) | Base | 533K / $262K | 67K / $55K | — | — | 2026-10-10 | active |
| [ATXP](https://atxp.ai) ([x402scan](https://www.x402scan.com/recipient/0x7f9d1a879750168b8f4a59734b1262d1778fdb5a)) | Agent account / payments | none | Base, Solana | 314K / $122K | 0 / $0 | 30d 0 tx/$0; all-time 568K tx/$232K | — | 2026-06-18 | dormant (114d idle) |
| [x402.boats](https://mcp.x402.boats) ([x402scan](https://www.x402scan.com/recipient/0xb0af3ccf9154f81af07a194150113523767d7de0)) | Game for AI agents | none | Base | 29K / $208K | 0 / $0 | — | — | 2026-09-04 | dormant (36d idle) |
| [Vishwa](https://api.vishwalab.com) ([x402scan](https://www.x402scan.com/recipient/0x6a5e7d954f49712abf3f873f037ec845b7b8c666)) | API seller (title "Vishwa"; function not stated) | none | Base, Solana | 481K / $42K | 10 / $0 | 30d 106K tx/$106; all-time 728K tx/$752 | — | 2026-09-15 | low activity (10 tx/calls in 30d) |
| [KORUS](https://www.korusmusic.co) ([x402scan](https://www.x402scan.com/recipient/0x8a12157b27c22fb239e558dc3cb43c7d1a8c0881)) | Consumer music-creation app paid via x402 | none | Base | 24K / $19K | 24K / $19K | — | — | 2026-10-11 | active |
| [MineBean](https://api.minebean.com) ([x402scan](https://www.x402scan.com/recipient/0x78f993378ff7890daac1689f79e7db2291e73928)) | Game / mining app (title "MineBean") | none | Base | 154K / $15K | 0 / $0 | — | — | 2026-08-03 | dormant (69d idle) |
| [claw402](https://claw402.ai) ([x402scan](https://www.x402scan.com/recipient/0xa9dd7cc9cbf0e05551332209289f04be36bc2315)) | x402 API payment gateway (micro-calls) | CLAW402 on Solana only (CoinGecko coin list) | Base | 4.87M / $9.5K | 424K / $940 | — | — | 2026-10-11 | active |
| [FortClaw](https://mcp.fortclaw.com) ([x402scan](https://www.x402scan.com/recipient/0xf000ab8b02aa5c52b62bdb10bf63312317e994fc)) | Territory game for AI agents | none | Base | 59K / $5.3K | 18K / $1.5K | — | — | 2026-10-11 | active |
| [BotPay](https://api.botpay.network) ([x402scan](https://www.x402scan.com/recipient/0xcc1984e79726e7a0ae2b9df2ac9e79fb4983930e)) | Agent payment network / video-access API | none | Base, Solana | 48K / $4.0K | 21K / $2.1K | 30d 12K tx/$488; all-time 20K tx/$855 | 4 | 2026-10-08 | active |
| [X Pay](https://www.api-xpay.com) ([x402scan](https://www.x402scan.com/recipient/0x589a2314a2e05f45e40c4823da3ba58d421db3d8)) | Payment-receipt / health-check API ("X Pay") | none | Base | 42K / $3.4K | 42K / $3.4K | — | 42K | 2026-10-11 | active |
| [BaseHub](https://basehub-alpha.vercel.app) ([x402scan](https://www.x402scan.com/recipient/0x7d2ceb7a0e0c39a3d0f7b5b491659fde4bb7bcfe)) | Games / web3 tools ("earn XP") | none | Base | 41K / $3.0K | 5.0K / $284 | — | — | 2026-10-11 | active |
| [Orbis API](https://orbisapi.com) ([x402scan](https://www.x402scan.com/recipient/0x2bb72231eed303cc91a462a1fa738b42b6a9ac6d)) | API marketplace (1,000+ APIs at $0.01) | none | Base | 439K / $2.1K | 0 / $0 | — | — | 2026-06-28 | dormant (104d idle) |
| [OneShot Agent](https://win.oneshotagent.com) ([x402scan](https://www.x402scan.com/recipient/0x9fb365e4e9385e2a39febad70368267e6f571d9a)) | Agent tool APIs (web-read, enrichment) | none | Base | 123K / $1.0K | 46K / $390 | — | 45K | 2026-10-11 | active |
| [agentutility](https://x402.agentutility.ai) ([x402scan](https://www.x402scan.com/recipient/0x6c0752c09e7f6fa6526fcdf40e456a159ebb5621)) | Paid x402 API catalog | none | Base, Solana | 69K / $1.7K | 9.4K / $244 | 30d 2.1K tx/$53; all-time 7.6K tx/$160 | 317 | 2026-10-11 | active |
| [KEYRING AGENT](https://keyring-agent.blockchhub.link) ([x402scan](https://www.x402scan.com/recipient/0x17cd53c04d707ef0dd615ef56c633f02915a7905)) | Token-send execution-fee API | none | Base | 24K / $1.2K | 24K / $1.2K | — | 25K | 2026-10-11 | active |
| [JarvisClaw](https://api.jarvisclaw.ai) ([x402scan](https://www.x402scan.com/recipient/0xdc59fa7b64988b846e76ec9849bb68f889071506)) | API seller ("JarvisClaw API") | none | Base, Solana | 33K / $1.0K | 7.7K / $38 | 30d 0 tx/$0; all-time 180 tx/$53 | 1.1K | 2026-10-11 | active |
| [Losbeto](https://losbeto-production-dd7c.up.railway.app) ([x402scan](https://www.x402scan.com/recipient/0xd5ba9711a3d052846a3695c70e7fcb8b3168fe7d)) | LLM inference + market data / trading swarm | none | Base, Algorand, Polygon | 9.0K / $623 | 5.8K / $394 | — | 5.3K | 2026-10-11 | active |
| [Agent402](https://agent402.tools) ([x402scan](https://www.x402scan.com/recipient/0xabf4fabd7c416fb67202e5f9002389fc75e2a9d0)) | 500+ pay-per-call tools; demand-intel site (intel.agent402.app) | none | Base, Solana, Algorand, Arbitrum, Avalanche, Celo | 38K / $579 | 10K / $264 | 30d 168 tx/$2; all-time 3.1K tx/$47 | 8.1K | 2026-10-11 | active |
| [x402node](https://api.x402node.dev) ([x402scan](https://www.x402scan.com/recipient/0x4466d4a84b7c49a6a094ec6eef4a0712d6dd125e)) | 528 pay-per-call APIs (data, dev tools) | none | Base, Solana | 21K / $503 | 4.1K / $81 | 30d 0 tx/$0; all-time 2.4K tx/$97 | 3.4K | 2026-10-11 | active |
| [OneSource](https://api.onesource.io) ([x402scan](https://www.x402scan.com/recipient/0x52e29e0d2aa49bfbfc548c0a9f2196f4aa51f3ea)) | Blockchain data API for agents | none | Base | 98K / $408 | 13K / $100 | — | 13K | 2026-10-11 | active |
| [Pocket Network (Agentic Portal)](https://agent.pocket.network) ([x402scan](https://www.x402scan.com/recipient/0xf732ea490c5766071785a2310523f7fa2cebb829)) | Agent-only messaging + security APIs; x402/MPP APIs | POKT 0x764a726d9ced0433a8d7643335919deb03a9a935 (Base; not in x402 category) | Base | 14K / $70 | 14K / $70 | — | 14K | 2026-10-11 | active |
| [Apify AGI](https://agi.apify.com) ([x402scan](https://www.x402scan.com/recipient/0x4aabe17c239ef71c3a26ba7c2b3e0aebbfc1df26)) | Agent general interface (scraping actors) | none (company) | Base | 2.1K / $2.5K | 368 / $695 | — | 367 | 2026-10-11 | active |
| [Strale](https://api.strale.io) ([x402scan](https://www.x402scan.com/recipient/0x66d7c2f952362bfb24fd7f02a9bec9c754ea83bc)) | 250+ business-data / compliance capabilities | none | Base | 13K / $805 | 3.3K / $183 | — | 3.4K | 2026-10-11 | active |
| [Arkham API](https://api.arkm.com) ([x402scan](https://www.x402scan.com/recipient/0x942bd3e3073543c674efc0c378d5bce20f9120c1)) | On-chain intelligence API | none (Arkham token not matched) | Base, Solana | 1.3K / $1.0K | 570 / $141 | 30d 16 tx/$3; all-time 179 tx/$44 | 220 | 2026-10-11 | active |
| [Glassnode](https://x402.glassnode.com) | On-chain metrics API | none (company) | Base | not matched in x402scan registry (Bazaar only) | not matched | — | 1.2K | 2026-10-11 | active |
| [Tavily](https://x402.tavily.com) | Web search API | none (company) | Base | not matched in x402scan registry (Bazaar only) | not matched | — | 978 | 2026-10-08 | active |
| [Orthogonal](https://x402.orthogonal.com) | API gateway (157 resources; x402 Foundation general member) | none | Base, Monad | not matched in x402scan registry (Bazaar only) | not matched | — | 2.0K | 2026-10-11 | active |
| [Chainlink for Agents](https://agents.chain.link) | Chainlink workflow-execution API for agents | LINK 0x88fb150bdc53a65fe94dea0c9ba0a6daf8c6e196 (in CoinGecko x402 category) | Base | not matched in x402scan registry (Bazaar only) | not matched | — | 46K | 2026-10-06 | active |
| [Zapper API](https://public.zapper.xyz) ([x402scan](https://www.x402scan.com/recipient/0x43a2a720cd0911690c248075f4a29a5e7716f758)) | Portfolio data API | none | Base | 26K / $46 | 0 / $0 | — | — | 2026-08-03 | dormant (68d idle) |
| [ArDrive Turbo](https://turbo.ardrive.io) ([x402scan](https://www.x402scan.com/recipient/0x6a0a10ffd285c971b841bee8892878c0d583bf67)) | Payment service for Arweave uploads | none | Base | 203K / $1.0K | 203K / $1.0K | — | — | 2026-10-11 | active |
| [Anyspend (B3)](https://x402.anyspend.com) ([x402scan](https://www.x402scan.com/recipient/0x1e8e93cb91778e5b1a3639706789195a838960f8)) | x402 payments + facilitator (facilitator row in 1.2) | ANY 0xc17dda248e2d50fc006d8febb5a406dd31972712 | Base | 15K / $25K | 0 / $0 | — | — | 2026-08-17 | dormant (54d idle) |
| [Aubrai (Bio)](https://aubr.ai) ([x402scan](https://www.x402scan.com/recipient/0x44dc2dceaa22c7ef6b2e2cf2362fd3fb476b7c2c)) | Longevity-research agent API | AUBRAI 0x9d56c29e820dd13b0580b185d0e0dc301d27581d | Base | 14K / $321 | 2.3K / $63 | — | 2.3K | 2026-10-10 | active |
| [Vaaya](https://vaaya.ai) ([x402scan](https://www.x402scan.com/recipient/0x7c655d3d3944bd27994dd81a036c3afb19806c40)) | Credit accounts / prepaid balance for agents (+ tokenized shares) | none | Base | 3.8K / $121 | 1.8K / $51 | — | 1.6K | 2026-10-10 | active |
| [Locus x402 wrappers](https://paywithlocus.com) ([x402scan](https://www.x402scan.com/recipient/0x3c5cbe28eca3b96023c45d3f877da834f1c7d5fa)) | Pay-per-use wrappers for Gemini, Stability AI, etc. (directory entry Locus) | none found (CoinGecko "Locus Chain" is a different project) | Base | 38K / $106 | 36K / $57 | — | 328 | 2026-10-10 | active |
| [Merit "Stable*" family (StableEnrich, StableSocial, StableTravel, StableEmail, StableStudio)](https://stableenrich.dev) ([x402scan](https://www.x402scan.com/recipient/0x325bdf6f7efab24a2210c48c1b64cab2eae1d430)) | Pay-per-call data APIs run by Merit Systems (assigned) | none | Base, Solana | 480K / $14K | 57K / $1.7K | 30d 0 tx/$0; all-time 8.6K tx/$252 | 35K | 2026-10-11 | active |

#### 1.5 October-December 2025 mint and launchpad-era recipients (the wash and spike evidence)
These belong to the assigned [token experiments] group (Virtuals ACP to [agent frameworks]). They are listed because they explain the October 2025 spike and show which are dead. Names are the titles in x402scan's registry.

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

#### 1.6 Assigned list: what was found on Base for each assigned name
"No footprint found" means the domain does not appear in x402scan's registered origins or the Bazaar and the researcher found no x402 repo or token tied to it; it does not prove the project is inactive. For AI Frens, TokenMesa and x402 Market the source marks the group as inferred (launchpad/token). Facilitator rows repeat the key numbers from 1.2.

| Name | Group | Category | Token (Base contract) | Chains | Traction signal (numbers, dates) | Status on Base |
|---|---|---|---|---|---|---|
| [Coinbase / CDP](https://docs.cdp.coinbase.com/x402/welcome) | [platform] | Facilitator; Bazaar operator | none | Multi: Base, Solana, Polygon | [x402scan](https://www.x402scan.com/facilitator/coinbase): 117.0M tx / $29.2M Base all-time; 30d 1,965,296 tx / $232,816; window 91.0% of Base tx and 29.7% of Base USDC. [Bazaar API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0): 32,169 resources, 2,212 hosts. Agentic.Market (directory): no footprint matched | active |
| [Base (chain)](https://www.base.org) | [platform] | Chain | n/a | n/a | x402scan Base: 168.8M tx / $46.9M all-time ([source](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D)). Base said cumulative agent payments passed $50M, over 85% on Base, on 2026-05-14 ([Foresight News via Bitget](https://www.bitget.com/news/detail/12560605412078)). [base.org/ecosystem](https://www.base.org/ecosystem) is client-rendered and unreadable | active |
| [x402 Foundation](https://x402.org) | [platform] | Standards body | none | n/a | Operational launch 2026-07-14 with 40 members ([release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/)); repo [x402-foundation/x402](https://github.com/x402-foundation/x402) 6,702 stars, pushed 2026-10-10. Its four example entries share that repo; the x402.org Facilitator entry declares only testnets (base-sepolia, solana-devnet); no footprint matched | active |
| [Cloudflare](https://blog.cloudflare.com/x402/) | [platform] | Platform | none | n/a | Premier member; directory entry only; no seller footprint matched (the "stableflare.dev" origin is a different seller) | platform support; seller footprint unverified |
| [Google AP2](https://github.com/google-agentic-commerce/a2a-x402) | [platform] | Agent-payments standard | none | n/a | A2A x402 extension repo 564 stars, pushed 2026-08-04; Premier member; no on-chain footprint of its own | repo active |
| [Stripe](https://docs.stripe.com/payments/machine/x402) | [platform] | Platform | none | n/a | Premier member; directory says it "integrated x402" for stablecoin payments; no x402scan origin matched | platform support; footprint unverified |
| [Visa](https://www.visa.com) | [platform] | Card network | none | n/a | Premier member; no x402 Base footprint ("visa.orizn.app" in x402scan is an unrelated visa-requirements API) | unverified |
| [Mastercard](https://www.mastercard.com) | [platform] | Card network | none | n/a | Premier member; "Mastercard Agent Pay for Machines" is in the [launch release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/); no Base footprint | unverified |
| [Circle](https://www.circle.com) | [platform] | Stablecoin issuer | none | Arc is a default x402 network | Premier member; npm [@circle-fin/x402-batching](https://www.npmjs.com/package/@circle-fin/x402-batching) v3.5.0 (2026-09-16): 65,480 downloads in the 30 days to 2026-10-10; Arc (eip155:5042) is a default network in the [docs](https://docs.x402.org/core-concepts/network-and-token-support); 1,358 Bazaar `accepts` entries name it | active (tooling) |
| [AWS](https://builder.aws.com/content/38fLQk6zKRfLnaUNzcLPsUexUlZ/monetize-any-http-application-with-x402-and-cloudfront-lambdaedge) | [platform] | Cloud | none | n/a | Premier member; sample repos [aws-samples/sample-agentcore-cloudfront-x402-payments](https://github.com/aws-samples/sample-agentcore-cloudfront-x402-payments) (25 stars) and two others; no seller footprint | samples only |
| [Vercel](https://vercel.com/blog/introducing-x402-mcp-open-protocol-payments-for-mcp-tools) | [platform] | Cloud | none | n/a | Member page; [vercel-labs/x402-ai-starter](https://github.com/vercel-labs/x402-ai-starter) 72 stars, archived, last push 2025-12-11 | starter archived |
| [ERC-8004](https://eips.ethereum.org/EIPS/eip-8004) | [platform] | Agent-identity standard | none | n/a | agenteconomy.to: 626.6K registered agents across 24 chains ([2026-10-11](https://agenteconomy.to)); x402scan origin x8004.x420.dev 144.8K tx / $31.2K (last 2025-11-12) | n/a |
| [PayAI](https://payai.network) | [token facilitators] | Facilitator | PAYAI is Solana-only on [CoinGecko](https://www.coingecko.com/en/coins/payai-network-2); no Base contract | Multi: Base, Solana, Polygon, Avalanche | [x402scan](https://www.x402scan.com/facilitator/payAI): 23.6M tx / $4.43M all-time; window 688K tx (1.7%) and $1.12M (19.8%); 30d 24.3K tx / $5,872; npm @payai/facilitator 10,761 downloads/30d | active |
| [Heurist](https://docs.heurist.ai/x402-products/facilitator) | [token facilitators] | Facilitator; seller | HEU `0xef22cb48b8483df6152e1423b19df5553bbd818b` | Base only | [x402scan](https://www.x402scan.com/facilitator/heurist): 7.97M tx / $30K all-time (Nov-Dec 2025 peak); under 100 tx in 30 days; last 2026-10-08. Vending-machine seller 105.6K tx / $43.3K, idle since 2026-05-12; Heurist Mesh entry 67,813 tx / $1,618, last 2026-05-12 | facilitator active (low); sellers dormant (151d idle) |
| [AurraCloud](https://x402-facilitator.aurracloud.com) | [token facilitators] | Facilitator | none confirmed; "Aurra by Virtuals" AURA `0xdcaa5e062b2be18e52ea6ed7ba232538621ddc10` is an unverified name match | Base, Solana | [x402scan](https://www.x402scan.com/facilitator/aurracloud): 235K tx / $53.6K all-time, last Base settlement 2026-01-13 | dead on Base (271d idle) |
| [Meridian](https://mrdn.finance) | [token facilitators] | Facilitator | MRDN `0xe57e601c06689d3e2bf7db7bebb14b4ff28400c6` | Base only | [x402scan](https://www.x402scan.com/facilitator/mrdn): $3.79M all-time on 148K tx, 96.2% paid and received by the same 41 wallets (see 3.6); window 36.5% of Base USDC on 0.2% of tx; 30d 3,415 tx / $129,224 | active, but volume is circular |
| [Primer](https://primer.systems) | [token facilitators] | Facilitator | CoinGecko "Primer" (PR) lists Robinhood chain only; no Base contract | Base only | [x402scan](https://www.x402scan.com/facilitator/primer): 39.3K tx / $9.0K all-time; 30d 5,763 tx / $1,508; supports SKALE Base per [awesome-x402](https://github.com/xpaysh/awesome-x402) | active (small) |
| [CodeNut](https://docs.codenut.ai/guides/x402-facilitator) | [token facilitators] | Facilitator; agent platform and launchpad | none on CoinGecko | Base, Solana | [x402scan](https://www.x402scan.com/facilitator/codenut): 478K tx / $110K all-time, last Base settlement 2026-01-27. Origin codenut.ai 403K tx / $103K all-time, 1 tx in 30 days (last 2026-10-08) | facilitator dead on Base (257d idle); seller minimal |
| [thirdweb](https://portal.thirdweb.com/payments/x402/facilitator) | [non-token infra] | Facilitator; wallet and SDK | none | Base, Polygon | [x402scan](https://www.x402scan.com/facilitator/thirdweb): 222.7K tx / $120K all-time; 30d 210 tx / $193 (last 2026-10-10) | active (low) |
| [Merit Systems (x402scan, AgentCash, Echo)](https://www.x402scan.com) | [non-token infra] | Discovery and analytics; agent wallet; data APIs | none | Base, Solana (Stable* family) | x402scan as seller: 30d 1,463 tx / $15, all-time 6,859 tx / $90, Bazaar 1,055 calls. StableEnrich alone 405K tx / $11.7K in the window (family totals in 1.4). Echo router 49.4K tx / $9.9K all-time, last 2026-07-17. npm [agentcash](https://www.npmjs.com/package/agentcash) 9,557 downloads/30d; [x402scan repo](https://github.com/Merit-Systems/x402scan) 397 stars. AgentCash entry: no footprint matched | active |
| [ampersend (Edge & Node)](https://app.ampersend.ai/discover) | [non-token infra] | Wallet and discovery | none | n/a | [ampersend-sdk](https://github.com/edgeandnode/ampersend-sdk) 24 stars, pushed 2026-07-17; no seller footprint matched | unverified |
| [MCPay](https://mcpay.tech) | [non-token infra] | SDK / tooling | none | n/a | [microchipgnu/MCPay](https://github.com/microchipgnu/MCPay) 90 stars, last push 2026-01-21; npm `mcpay` about 11 downloads/day; no footprint | dormant (repo idle 263d) |
| [Mogami](https://mogami.tech/) | [non-token infra] | Facilitator; Java SDKs | none | Base only | [x402scan](https://www.x402scan.com/facilitator/mogami): 23.4K tx / $310K all-time; 30d 2.3K tx / $10 (last 2026-10-10). Java SDK repos 7 to 11 stars; the example and Java SDK entries show no footprint | active (low) |
| [x402.rs](https://x402.rs) | [non-token infra] | Facilitator (Rust) | none | Base, Polygon; declares more | [x402scan](https://www.x402scan.com/facilitator/x402rs): 703K tx / $469K all-time, last Base settlement 2026-08-30; [repo](https://github.com/x402-rs/x402-rs) 291 stars | dormant (42d idle) |
| [OpenX402](https://open.x402.host) | [non-token infra] | Facilitator | none | Multi: Base, Solana, Avalanche, Polygon | [x402scan](https://www.x402scan.com/facilitator/openx402): 563K tx / $177K all-time; 30d 1.7K tx / $1.3K (last 2026-10-10) | active (low) |
| [Crossmint](https://www.crossmint.com) | [non-token infra] | Wallet / agent finance | none | n/a | [crossmint-agentic-finance](https://github.com/Crossmint/crossmint-agentic-finance) 19 stars (2026-03-13); no facilitator or seller footprint | unverified |
| [Daydreams](https://facilitator.daydreams.systems) | [agent frameworks] | Facilitator; framework; LLM router | DREAMS `0x176383016bb310c9f1c180dc6729d5e28104e602` | Base, Solana | [x402scan](https://www.x402scan.com/facilitator/daydreams): 11.8M tx / $2.76M all-time, mostly Nov 2025; 30d 496 tx / $775 (last 2026-10-10). Repos [daydreams](https://github.com/daydreamsai/daydreams) 619 stars, [lucid-agents](https://github.com/daydreamsai/lucid-agents) 199 stars (pushed 2026-07-26). Router entry: seller 4,655 tx / $1,405, last 2026-02-03 | active (low) |
| [Virtuals Protocol](https://app.virtuals.io) | [agent frameworks] | Facilitator; agent launchpad (ACP) | many "by Virtuals" tokens in the category (1.3a) | Base only | [x402scan](https://www.x402scan.com/facilitator/virtuals): 1.99M tx / $4.34M all-time; ACP-x402 origin 2.37M tx / $4.89M (about $1.5M a month in Feb-Mar 2026); 30d 2.8K tx / $28 (last 2026-09-28). ACP recipient in 1.5: 18K tx / $5.5K in the window | active (low) |
| [elizaOS](https://elizaos.ai) | [agent frameworks] | Agent framework | ELIZA (Solana only) | n/a | elizaos.ai redirected to elizaresearch.ai ("Eliza Research") on 2026-10-11; ELIZA has a Solana contract only; no Base x402 footprint found | unverified on Base |
| [Questflow](https://questflow.ai?utm_source=x402_website&utm_medium=ecosystem) | [agent apps] | Agent platform; facilitator | none | Base only | [x402scan](https://www.x402scan.com/facilitator/questflow): 474K tx / $10.2K all-time (473,884 tx / $10,205), under 100 tx in 30 days, last 2026-10-04. Seller: the reconciliation says its own origin has 21 tx; the directory match shows questflow.ai at 274,533 tx / $8,267 all-time, last 2026-03-02 | active (low) |
| [Bankr](https://bankr.bot) | [agent apps] | Agent app | BNKR `0x22af33fe49fd1fa80c7149773dde5890d3c76f3b` | n/a | [x402-cli-example](https://github.com/BankrBot/x402-cli-example) 3 stars (2025-10-26); no seller footprint. The agent-apps researcher calls it the only priced x402 product among their three leads, with no usage numbers ([their notes](dd_agent_apps_platforms.md)) | unverified |
| [Olas](https://olas.network) | [agent apps] | Agent framework and network | OLAS `0x54330d28ca3357f294334bdc454a032e7f353416` | n/a | agenteconomy.to counts 19.4M Olas transactions, which are not x402; no x402 footprint. The agent-apps researcher finds buyer-side x402 support in Pearl agents since Oct-Nov 2025 and seller-side (mech facilitator) work restarting in Sep-Oct 2026 ([their notes](dd_agent_apps_platforms.md)) | unverified |
| [Giza](https://www.giza.tech) | [agent apps] | DeFi agent | none | n/a | DefiLlama lists it as an AI-agent DeFi protocol (about $12.8K TVL on Hyperliquid/Arbitrum/Base on 2026-10-11, [API](https://api.llama.fi/protocols)); only x402 link found is a 0-star repo | no x402 footprint found |
| [Theoriq](https://www.theoriq.ai) | [agent apps] | DeFi agent | none | n/a | DefiLlama lists "Theoriq Gold Vault" on Ethereum; the site's 2026-10-11 title now describes risk-managed onchain yield on tokenized real-world assets | no x402 footprint found |
| [Recall](https://recall.network) | [agent apps] | Agent network | none | n/a | No x402 footprint (Bazaar name matches are unrelated "recalls" APIs) | no x402 footprint found |
| [Spectral](https://www.spectrallabs.xyz) | [agent apps] | Onchain agents | none | n/a | The spectral.finance address returned HTTP 404 on 2026-10-11; the agent-apps researcher finds no x402 work at Spectral Labs ([their notes](dd_agent_apps_platforms.md)); "Spectral-signed receipts" repos by another author are a name collision | site 404; no x402 footprint found |
| [Wayfinder](https://wayfinder.ai) | [agent apps] | Agent app | none | n/a | No x402 footprint found | no x402 footprint found |
| [Clanker](https://clanker.world) | [agent apps] | Token launcher | none | its site title says multi-chain | CoinGecko tags BNKR as "Clanker Ecosystem"; no Clanker x402 footprint (x402scan "Clanker Banker" and "clankerceo" origins are unrelated sellers) | no x402 footprint found |
| [Zora](https://zora.co) | [agent apps] | Creator protocol | none | Base (client side) | No seller footprint; a `zora pay` command in Zora's agent CLI (v1.6.0, 2026-06-25) is a buyer-side x402 v2 client on Base ([changelog](https://github.com/ourzora/zora-protocol/blob/main/packages/cli/CHANGELOG.md), [their notes](dd_agent_apps_platforms.md)) | buyer-side feature only |
| [Zauth](https://zauthx402.com) | [x402 apps and trust] | Trust / verification | ZAUTH is Solana-only on [CoinGecko](https://www.coingecko.com/en/coins/zauthx402) | n/a | In [third-party extensions](https://docs.x402.org/dev-tools/third-party-extensions) (@zauthx402/sdk); [zauthSDK](https://github.com/zauthofficial/zauthSDK) 8 stars (2026-02-11); no Base origin matched. The apps-and-trust researcher reports the team repositioned as an AI-security company on 2026-07-28 with the registry "still running", and the token is a pump.fun coin on Solana ([their notes](dd_x402_apps_and_trust.md)) | unverified on Base; repositioned |
| [Cred Protocol](https://credprotocol.com) | [x402 apps and trust] | Credit-scoring API | none | Base | The domain match found nothing; the apps-and-trust researcher reports x402 sales live on Base since 2026-01-21 that had earned $0.88 there ([their notes](dd_x402_apps_and_trust.md)) | tiny (cross-checked) |
| [Snack Money](https://api.snack.money/docs) | [x402 apps and trust] | Payments (tipping) | none | Base only | 654 tx / $155 all-time, last Base settlement 2025-12-04 | dead on Base (310d idle) |
| [Fluora](https://www.fluora.ai/) | [x402 apps and trust] | Marketplace (MonetizedMCP) | none | n/a | No footprint found here; the apps-and-trust researcher reports the marketplace API host deleted, no commits since 2026-02-11 and the company site now promoting an unrelated wellness product ([their notes](dd_x402_apps_and_trust.md)) | dead per cross-check |
| [Gloria AI](https://itsgloria.ai) | [data/AI sellers] | Seller / API | GLORIA `0x3b313f5615bbd6b200c71f84ec2f677b94df8674` | Base only | api.itsgloria.ai: 19.2K tx / $359 all-time; 30d 28 tx / $1; Bazaar 5 resources, 28 calls (last 2026-10-11) | low activity |
| [Otto AI](https://x402.ottoai.services) | [data/AI sellers] | Seller / API (agent swarm) | OTTO `0x380337d0180db7d0df76ac4faae2fcea908ee1fc` | Multi: Base, Solana | 178K tx / $433 all-time; 30d 3.3K tx / $30 (3,271 tx); Bazaar 2,337 calls (76 resources); Solana 599 tx / $2 | active |
| [AIXBT](https://api.aixbt.tech) | [data/AI sellers] | Seller / API | none in the category | Base | 1,535 tx / $2,766 all-time, last Base settlement 2026-07-11 | dormant (92d idle) |
| [Cookie DAO](https://www.cookie.fun) | [data/AI sellers] | Data | none | n/a | No x402 footprint found | no x402 footprint found |
| [Venice](https://venice.ai) | [data/AI sellers] | Seller / API (LLM inference) | none in the category | Base only | api.venice.ai: 3.4K tx / $5.3K all-time; 30d 613 tx / $3.1K (about $5 per payment); [veniceai/x402-client](https://github.com/veniceai/x402-client) 11 stars | active |
| PING | [token experiments] | Pay-to-mint meme token | PING `0xd85c31854c2b0fb40aaa9e2fc4da23c21f829d46` | Base | Oct 2025 pay-to-mint experiment; Chainalysis reports more than 150,000 transactions in its first month ([Chainalysis](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/)); [CoinGecko](https://www.coingecko.com/en/coins/ping) | experiment over |
| x402-minted tokens and launchpads | [token experiments] | Mint and launchpad recipients | various | Base | ARVOS, QRBase, Barvis, AinX402 and Canza took 90.7% of Base USDC in Nov 2025 (3.6); 15 of the 17 recipients traced are dead (11) or dormant (4) (table in 1.5) | mostly dead |
| x420 and x402MKT | [token experiments] | x402-branded tokens | X420 `0x68e284f21d04d4d62398c290ec3ef41c97f80b07`; LOOP (x402MKT) `0xa763b711b55935f6d7ba2f93e1adf741e2446b07` | Base | x8004.x420.dev 144.8K tx / $31.2K all-time, last 2025-11-12 | dormant / dead |
| [x402 Market](https://x402.world.fun) | [token experiments] | Launchpad / marketplace | none | Base only | Seller 68,215 tx / $123 all-time, last 2026-06-12; the WorldFun Facilitator entry (declares Base) shows the same figures | dormant (121d idle) |
| [AI Frens by Treasure](https://aifrens.lol) | [token experiments] | Launchpad / token | MAGIC `0xf1572d1da5c3cce14ee5a1c9327d17e9ff0e3f43`; MIO `0xe19e7429ab6c1f9dd391faa88fbb940c7d22f18f` | n/a | No footprint matched; the Treasure facilitator (2.5K tx / $400 all-time, last 2026-10-08) is in 1.2 | unverified |
| [TokenMesa](https://www.tokenmesa.com) | [token experiments] | Launchpad / token | none | n/a | No footprint matched | unverified |
| [Dexter](https://dexter.cash) | [rivals] | Facilitator; Solana-first seller | DEXTER is Solana-only on CoinGecko | Multi: Base, Solana | api.dexter.cash 25.9M tx / $4.71M on Solana all-time (last 2026-04-09). Base facilitator 110K tx / $7.1K all-time, last 2026-10-06, under 100 tx in 30 days; [dexter-mcp](https://github.com/Dexter-DAO/dexter-mcp) 11 stars | active on Solana, marginal on Base |
| [Corbits / Faremeter](https://corbits.dev) | [rivals] | Facilitator; SDK | none | Multi: Base, Solana, Monad, Polygon | [x402scan](https://www.x402scan.com/facilitator/corbits) on Base: 19.8K tx / $305 all-time, last 2026-06-20; [faremeter](https://github.com/faremeter/faremeter) 69 stars; npm @faremeter/middleware 73 to 204 downloads/day | dormant on Base (113d idle) |
| [Kite AI](https://gokite.ai) | [rivals] | Own L1 chain | none in the category | Not Base | General Foundation member; GitHub "kite x402" hits are Kite-chain apps; the x402scan "KiteEndpoints.ai" origins are an unrelated name collision; mainnet and Agent Passport launched 2026-04-30 with no independent usage data ([rivals notes](competition_rival_rails_chains.md)) | not on Base |
| [Pieverse](https://www.pieverse.io) | [rivals] | BNB Chain facilitator | none | Not Base | Listed as a BNB Chain facilitator in [awesome-x402](https://github.com/xpaysh/awesome-x402); its 2026-10-11 site title reads "Web3 AI Agent for Line, Kakao & WhatsApp"; no Base footprint or repo; the rivals researcher finds its last dated news in October 2025 and says the 2026 BNB Chain x402 story is Binance's own B402 ([rivals notes](competition_rival_rails_chains.md)) | not on Base (unverified) |

#### 1.7 x402 Foundation launch roster (2026-07-14)
Source: the [launch release](https://x402.org/linux-foundation-announces-operational-launch-of-x402-foundation-to-standardize-internet-native-payments-for-ai-agents-and-applications/) (it says 40 members but names 39 entries) and the [x402.org member pages](https://x402.org/llms.txt), which also list Nansen, World, Vercel, Stripe and Quicknode. Members already in 1.6: AWS, Circle, Cloudflare, Coinbase, Google, Mastercard, Stripe, Visa, Vercel, Merit Systems, Kite AI.
- 22 UNCOVERED members have no Base x402 footprint found (payments or chain players whose plans are not visible in Base data): Adyen, American Express, Fiserv, MoonPay, Ripple, Shopify, zerohash, World Liberty Financial, KakaoPay, Hecto Financial, Galaxia Moneytree, Quant Network, utexo, Aleo, Injective, LayerZero Labs, Monad Foundation, BSV Association, Cardano Foundation, Casper, Fireblocks, NEAR Foundation.
- UNCOVERED members with some footprint: Orthogonal (157 Bazaar resources on Base, Monad and Solana; 1,959 calls in 30 days); t54 labs (x402-secure API, 29.6M Base tx all-time, peak Dec 2025; XRPL facilitator); Nansen (32 Bazaar resources, 3,578 calls in 30 days, 4.7K Base tx in 30 days); SKALE (SKL has a Base contract; Primer and PayAI list SKALE Base networks); Polygon Labs (Polygon facilitator, $141,064 in the trailing 30 days per [x402-list.com](https://x402-list.com), Polygon not Base); Solana Foundation ([solana-foundation/pay](https://github.com/solana-foundation/pay) 1,788 stars, pushed 2026-10-09, Solana); Stellar Development Foundation (Stellar facilitator); OMA3 (OMATrust "x402 Reputation"); World (AgentKit extension); Quicknode (x402-rails gem, 37 stars).

#### 1.8 GitHub stars
[GitHub search](https://api.github.com/search/repositories?q=x402&sort=stars&per_page=100) on 2026-10-11 (300 repos read): the protocol repo [x402-foundation/x402](https://github.com/x402-foundation/x402) has 6,702 stars (pushed 2026-10-10), [BlockRunAI/ClawRouter](https://github.com/BlockRunAI/ClawRouter) 6,622, [solana-foundation/pay](https://github.com/solana-foundation/pay) 1,788, [daydreamsai/daydreams](https://github.com/daydreamsai/daydreams) 619, [google-agentic-commerce/a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) 564, [Merit-Systems/x402scan](https://github.com/Merit-Systems/x402scan) 397, [x402-rs/x402-rs](https://github.com/x402-rs/x402-rs) 291. Stars can be inflated: the 6,710-star [internet-court-skill](https://github.com/internet-court/internet-court-skill) repo had 4 commits and 10 watchers when fetched and names x402 as one of many payment standards (verify). The 13,033-star NoFxAiOS/nofx and several other top-45 repos are x402-adjacent (AI trading agents, MCP clients).

#### 1.9 The analytics and discovery layer
x402scan, the CDP Bazaar, x402-list.com, x402watch, agenteconomy.to, Valoria and the other trackers are covered, with exact URLs, in section 4.

#### 1.10 awesome-x402 entries with measurable Base usage not listed above
Source: [awesome-x402 README](https://github.com/xpaysh/awesome-x402) (816 linked entries parsed; self-submitted, so inclusion says nothing about quality), matched by registrable domain to x402scan and the Bazaar as in 1.0. Entries already in 1.1 or 1.4 are omitted, and entries sharing a payTo address are shown once. Shown: those with at least 100 Base tx or Bazaar calls in 30 days, or at least 20,000 Base or Solana tx all-time (44 matched, 40 shown). All UNCOVERED, all active. This is the long tail: individually tiny (under $100 a month each) but most of the registered-origin count. The 12 most active (by 30-day Base tx or Bazaar calls) are in the table ("What it is" is a short tag condensed from the list's own description); the other 28 follow as a list.

| Name | What it is | Base 30d tx / USDC | Base all-time tx / USDC | Bazaar calls 30d | Solana 30d tx | Last Base settlement |
|---|---|---|---|---|---|---|
| [glim.sh](https://glim.sh) | social/web data (11 MCP tools) | 6.0K / $16 | 17K / $69 | 921 | 2.4K | 2026-10-11 |
| [RobinX](https://robinx.io) | Robinhood Chain memecoin intel | 2.4K / $55 | 2.7K / $60 | 56 | — | 2026-10-10 |
| [x402stock](https://x402stock.xyz) | US stock data | 1.8K / $50 | 9.2K / $253 | 1.0K | — | 2026-10-11 |
| [Deepnets](https://api.deepnets.ai) | Solana token intel | 0 / $0 | 0 / $0 | 1.2K | 1.1K | 2026-10-11 |
| [Gotobi Calendar API](https://gotobi.hugen.tokyo) | Japanese FX dates | 878 / $7 | 92K / $2.7K | 803 | 53 | 2026-10-11 |
| [2s.io](https://2s.io) | utility JSON API | 844 / $16 | 36K / $118 | 584 | 34 | 2026-10-11 |
| [agentsvc.io](https://agentsvc.io) | utility tools | 820 / $6 | 817 / $6 | 836 | — | 2026-10-11 |
| [DDG Agent-Payable Services](https://agents.daedalusdevelopmentgroup.com) | security/conformance services | 795 / $7 | 795 / $7 | 617 | — | 2026-10-07 |
| [IPIntel.ai](https://ipintel.ai/x402-api) | IP threat intel | 758 / $18 | 1.4K / $27 | 750 | — | 2026-10-11 |
| [LoneStarOracle](https://lonestaroracle.xyz) | AI data services | 637 / $41 | 3.3K / $341 | 490 | — | 2026-10-10 |
| [PulseNetwork](https://pulsenetwork.theaslangroupllc.com) | intel API catalog | 636 / $63 | 12K / $1.8K | 215 | 29 | 2026-10-11 |
| [Sirenic](https://api.sirenic.eu) | European company data | 602 / $23 | 2.3K / $137 | 341 | — | 2026-10-11 |

The other 28 (all active, last Base settlement 2026-10-05 to 2026-10-11), with Base 30d tx / USDC: [botsmith](https://x402.botsmith.dev) 521 / $10; [x402 Bazaar](https://402.com.tr) 0 / $0; [Relaystation](https://relaystation.ai) 455 / $7; [Skim](https://skim402.com) 456 / $1; [GlobalAPI](https://globalapi.dev) 380 / $2; [Kronos x402 API](https://kronossignals.com) 376 / $11; [FiatDock](https://fiatdock.com) 259 / $1; [PayAPI Market](https://payapi.market) 268 / $1; [tokenguard](https://eltociear-tokenguard.hf.space/scan) 265 / $6; [GEDX402](https://gedx402.com) 260 / $2; [AI Rook — Trading Intelligence + General Agent APIs](https://agents.ai-rook.com) 226 / $2; [SuVerse Pay](https://suverse-pay.suverse.io) 90 / $5; [_done](https://underscoredone.com) 249 / $3; [Vibe Springs](https://vibesprings.net) 243 / $1; [WebberSites x402 Data API](https://x402.webbersites.com) 239 / $2; [agentdata-nl](https://agentdata-api.sander-van-aard.workers.dev) 230 / $59; [LION](https://lionx402.com) 224 / $3; [afriref / latamref / asiaref / euroref / usaref / ausref](https://afriref.dev) 219 / $11; [AgentLux](https://agentlux.ai) 209 / $0; [anchor-x402](https://anchor-x402.com) 169 / $6; [SignalFuse](https://api.signalfuse.co) 131 / $1; [scrape402](https://x402.shizu.me) 150 / $1; [SYNTHORA md-extract](https://pay.hergertsynthora.com/service) 135 / $3; [PreReason](https://www.prereason.com) 132 / $5; [TradingAgents x402](https://tradingagents-x402.fly.dev) 126 / $21; [modelprices.xyz](https://modelprices.xyz) 116 / $1; [Kraken Crypto Signals](https://signals.nsgoods.org) 115 / $1; [FractalAI x402 Proofs](https://fractalai.net.co/.well-known/x402.json) 110 / $3.

Inferences and gaps for sections 1 to 3 are in section 5.


## 2. Ranked list of uncovered projects worth full due diligence

### Takeaway
Ranked by evidence of repeated Base usage first, then token presence, then credibility, the strongest uncovered names are BlockRun, FluxA, AX1, Cluster Protocol, ATXP and Laso Finance; the token-bearing uncovered names that matter are Anyspend (ANY), Treasure (MAGIC), Cluster Protocol (CP), Pocket Network (POKT) and SKALE (SKL), while most other Base-contract tokens in the CoinGecko x402 category show no x402 usage.

### Cited Findings
All "window" figures are Base, 2026-04-11 to 2026-10-11, from the [x402scan daily series](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D) and per-recipient series; "30d" figures are to 2026-10-11. One line each; full detail is in sections 1 and 3. Section references in the table (1.3a, 1.4, 3.6, 3.9) point to the matching blocks of this digest. The table below is the source's ranking as written.

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


## 3. Metrics: x402 activity on Base, April to October 2026

### Takeaway
In the six months to 2026-10-11 x402scan shows 41.5M Base transactions and $5.66M USDC (Solana: 25.6M tx and $1.51M). Base monthly USDC fell from $1.93M in April to $0.57M in September while monthly tx rose to 9M to 13M in June to August, because one seller (BlockRun) produced 65% of the window's Base tx. Roughly 27% to 49% of Base USDC looks like API-style commerce, 36% is a closed loop between the same wallets (Meridian) and 15% to 24% is a handful of large one-off transfers; Coinbase's facilitator carries 91% of tx. Solana out-counted Base on only 19 of 184 days (the episode ran from 2026-08-20 to 2026-09-08). The core npm packages grew 2.3x to 3.6x in daily downloads from April to September and the PyPI `x402` package 1.7x (2.6x by early October), with the v2 `@x402/*` packages far ahead of v1.

### Cited Findings

#### 3.1 Monthly transactions, USDC volume and participants on Base (with Solana for comparison)
Source: [x402scan daily series by chain](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D) summed by month (daily buckets; months before April are context for the October 2025 spike). \*Buyers and sellers are x402scan's per-day distinct counts summed across facilitator rows, so they over-count wallets that use several facilitators. True monthly distinct counts cannot be built: x402scan only materialises 1-, 7-, 14-, 30-day and all-time windows ([time-range code](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/lib/time-range.ts)).

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

- Average payment fell from $0.84 in April to $0.055 in July, the months BlockRun's roughly $0.017 calls took over (see 3.4) ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)).
- Busiest Base day in the window by tx: 2026-07-13 (1.52M tx). By USDC: 2026-04-21 ($418K from 73K tx). The median Base day had about 112K tx, and the mean since 2026-09-15 is about 72.9K tx a day ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)).
- Context: Base peaked in November 2025 at 64.3M tx and $27.9M. Cumulative Base tx reached 126.7M by 2026-03-31, consistent with Chainalysis' report of more than 100 million Base transactions through Q1 2026 ([Chainalysis](https://www.chainalysis.com/blog/x402-agentic-payments-adoption/)). The first Base transfer in x402scan is 2025-05-09.

#### 3.2 Unique buyers and sellers (windows ending 2026-10-11)
Source: [x402scan network totals, 30 days](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%7D%7D) and the [1-day](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A1%7D%7D), [7-day](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A7%7D%7D) and [all-time](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D) versions, plus the per-chain overall stats for 14 days (Base [30-day](https://www.x402scan.com/api/trpc/public.stats.overall?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%7D%7D) and [all-time](https://www.x402scan.com/api/trpc/public.stats.overall?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%7D%7D) shown as examples of the call). \*Over-counted as above.

| Window (ending 2026-10-11) | Base tx | Base USDC | Base buyers* | Base sellers* | Solana tx | Solana USDC | Solana buyers* | Solana sellers* |
|---|---|---|---|---|---|---|---|---|
| last 1 day | 57K | $13K | 3.0K | 1.1K | 14K | $2.9K | 167 | 97 |
| last 7 days | 520K | $212K | 14K | 6.1K | 135K | $116K | 544 | 181 |
| last 14 days | 1.02M | $382K | 24K | 9.2K | 230K | $250K | 772 | 272 |
| last 30 days | 2.17M | $703K | 35K | 39K | 506K | $368K | 1.4K | 417 |
| all time (since 2025-05-09) | 168.8M | $46.89M | 659K | 282K | 65.0M | $8.57M | 230K | 31K |

- Cross-checks on buyer counts: x402-list.com measures 10,871 distinct on-chain buyers across 713 services in the trailing 30 days ([x402-list.com](https://x402-list.com)); x402watch labels 45,836 buyers "organic_user" in its 2026-10-10 snapshot ([data](https://github.com/printmoneylab/x402watch-data)); the Bazaar shows 4,671 payers for AX1 alone and about 11.2K buyers for KORUS in x402scan's 30-day list.

#### 3.3 Facilitators by share on Base
Source: [x402scan daily Base series by facilitator](https://www.x402scan.com/api/trpc/public.facilitators.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%7D%7D), summed by month; each cell is tx share / USDC share of Base. The facilitator series sum exactly to the Base total, so every Base transfer is attributed to one listed facilitator. Window = 2026-04-11 to 2026-10-11.

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
- The December 2025 story that Dexter overtook Coinbase (about half of daily tx, from Dune data cited by Hashed) refers to all chains. On Base x402scan shows Dexter at 1.1% of tx in March 2026 and 0.2% in the window, while Dexter's seller origin has 25.9M tx on Solana ([Cryptopolitan](https://www.cryptopolitan.com/dexter-overtakes-coinbase-x402-transactions/), [source](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)).

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

- **When Solana passed Base.** Solana out-counted Base on tx on 19 of the 184 days in the window; the first such day was 2026-08-20. Base's weekly share of Base+Solana tx fell to 5.9% in the week of 2026-08-24 and was back at 76.8% by the week of 2026-09-14 ([source](https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D)).
- **Why.** The [Solana Compass report](https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months) (2026-08-25) attributes the flip to BlockRun routing traffic through Solana, citing x402scan. The researcher agrees: BlockRun's traffic moved to Solana from 2026-08-20 to 2026-09-08 (22.5M Solana tx all-time) and its Base tx fell to 211K in September (section 2, rank 1). It was a three-week episode of one seller's traffic, not a durable share shift.
- **The "first time in six months" framing does not match x402scan.** Solana Compass says Base led for six months until 2026-08-25, with one earlier Solana edge on 2026-01-20. In x402scan's daily series Solana is ahead on 26 of 28 days from 2026-01-22 to 2026-02-18 (February 2026: Base 1.42M tx versus Solana 2.25M) and on 19 days from 2026-08-20 to 2026-09-08. The rivals researcher's Artemis-based figures (Solana 76% of x402 tx in the four weeks to 2026-09-22) agree on direction ([their notes](competition_rival_rails_chains.md)).
- **Last 30 days:** Base 2.17M tx / $703K versus Solana 0.51M tx / $368K, so Base 81% of tx and 66% of USDC ([source](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%7D%7D)). **All-time:** Base 168.8M tx / $46.9M, Solana 65.0M tx / $8.57M, Polygon 190 tx, Optimism none ([source](https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D)).
- **Solana's top sellers in the last 30 days** by tx: sol.blockrun.ai 226.7K, Vishwa 106.2K, SniperX 33.8K, three.ws 32.8K, Xona Agent 16.4K, SVM402 12.2K, BotPay 11.9K. By USDC: Laso Finance $267K from 111 tx ([source](https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D)).
- **Other chains (Bazaar `accepts` entries, supply side, not usage):** Base 33,427, Solana 8,328, Polygon 4,832, Arbitrum 2,787, Base Sepolia 2,397, Optimism 1,719, Arc 1,358, Monad 920 ([Bazaar API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0)). x402scan itself indexes only Base, Solana, Polygon and Optimism.

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

- Aggregates (average downloads per day, April / September / October 1-10): v2 framework wrappers (`@x402/fetch`, `axios`, `express`, `hono`, `next`) 9.3K / 28.1K / 33.0K; v1 wrappers (`x402-fetch`, `x402-axios`, `x402-express`, `x402-hono`, `x402-next`) 3.3K / 5.4K / 3.8K; all listed v2 packages 38.2K / 128.3K / 156.4K versus v1 including `x402` 27.8K / 63.0K / 69.0K ([source](https://api.npmjs.org/downloads/range/2026-04-01:2026-10-10/x402-fetch)). Latest versions: `x402` 1.2.0 (2026-04-16), `@x402/*` 2.28.0 (2026-09-29) ([npm registry search](https://registry.npmjs.org/-/v1/search?text=x402&size=250&from=0)).
- PyPI `x402`, downloads a day: 3,720 in April (23 days from 2026-04-08), 3,740 in May, 5,689 in June, 5,760 in July, 5,936 in August, 6,489 in September, 9,539 in 2026-10-01..10. pypistats reports 204,765 for the last month, 70,494 for the last week and 8,391 for the last day as of 2026-10-11 ([pypistats](https://pypistats.org/api/packages/x402/overall?mirrors=false), [recent](https://pypistats.org/api/packages/x402/recent)).
- Other packages, downloads in the 30 days to 2026-10-10: `@circle-fin/x402-batching` 65,480; `@payai/facilitator` 10,761; `@blockrun/llm` 10,532; `@okxweb3/x402-core` 10,098; `@blockrun/clawrouter` 10,068; `@okxweb3/x402-evm` 9,939; `agentcash` 9,557; `@alchemy/x402` 8,945; `@x402/fastify` 7,370; `@x402/hedera` 7,059; `@x402-avm/core` 5,262; `x402-stellar` 4,738; `x402-solana` 3,959; `@metaplex-foundation/x402` 3,362; `@metamask/x402` 3,229. Some packages returned no data because the npm API rate-limited the batch; absence is not evidence of zero.

#### 3.8 The Coinbase Bazaar catalogue
Source: [Bazaar discovery API](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0), read 2026-10-11.
- 32,169 resources on 2,212 hosts; 31,665 resources accept Base mainnet; the `quality` field reports 934,886 calls in the last 30 days in total.
- The median resource had 2 calls in 30 days; 89.5% of resources had 5 or fewer calls (6.0% of all calls); only 277 resources had 100 or more and 57 had 1,000 or more. Every resource shows a last call within 30 days, which suggests the Bazaar's own probing contributes a baseline of about one call per resource per month (inference).
- Top hosts by 30-day calls hold 43.8% (AX1), 57.1% (top 3), 66.5% (top 5) and 79.0% (top 10) of all calls. [gold-402](https://github.com/Haustorium12/gold-402), a hand-checked directory, states that most of the catalogue no longer answers a live 402. The host table is in 3.4.

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


## 4. Data sources and their quirks

### Takeaway
x402scan's public tRPC endpoints are the only free source with daily series by chain, facilitator and recipient, so they are the base for a daily monitor; everything else is a cross-check. Every source counts transfers or listed resources, not HTTP traffic, and none separates wash trading from commerce, so the real-commerce range in 3.6 is the researcher's classification of recipients. x402-list.com independently reproduces x402scan's facilitator volumes. x402watch's wash filter is unstable. agenteconomy.to has lower totals from different sources. Dune dashboards could not be read. Valoria and the x402.org home-page totals do not reconcile and should not be used.

### Cited Findings

#### 4.1 x402scan (primary source)
- **Site and code.** [x402scan.com](https://www.x402scan.com), run by Merit Systems (assigned, [non-token infra]); repo [Merit-Systems/x402scan](https://github.com/Merit-Systems/x402scan) (397 stars, pushed 2026-09-25). The URLs below are the public tRPC endpoints that back the website ([router source](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/trpc/routers/networks.ts)). Its documented REST API is paid, $0.01 to $0.02 per call per its [OpenAPI spec](https://www.x402scan.com/openapi.json); the researcher did not pay for it.
- **URL pattern.** `https://www.x402scan.com/api/trpc/<router.procedure>?input=<URL-encoded JSON>`, where the JSON is `{"json": {...}}`. The decoded inputs are shown below; the URLs are exact and the researcher pulled them on 2026-10-11.
- **Pages.** Facilitator: `https://www.x402scan.com/facilitator/<id>` (ids such as `coinbase`, `payAI`, `fluxa`, `mrdn`, `daydreams`; 33 ids in the [registry package](https://github.com/Merit-Systems/x402scan/tree/main/packages/external/facilitators/src/facilitators)). Recipient: `https://www.x402scan.com/recipient/<0x address>`.

| Procedure | Decoded input (`json`) | What it returns, as used | Exact URL |
|---|---|---|---|
| `networks.list` | `{"timeframe":1}` | Totals by chain (tx, USDC, buyers, sellers), last 1 day | `https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A1%7D%7D` |
| `networks.list` | `{"timeframe":7}` | Same, last 7 days | `https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A7%7D%7D` |
| `networks.list` | `{"timeframe":30}` | Same, last 30 days | `https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%7D%7D` |
| `networks.list` | `{"timeframe":0}` | Same, all time (since 2025-05-09) | `https://www.x402scan.com/api/trpc/networks.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%7D%7D` |
| `networks.bucketedStatistics` | `{"timeframe":0,"numBuckets":400}` | Daily series by chain since 2025-05-09; the basis of 3.1, 3.5 and the monthly and weekly tables | `https://www.x402scan.com/api/trpc/networks.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%7D%7D` |
| `public.facilitators.list` | `{"timeframe":30,"chain":"base","sorting":{"id":"tx_count","desc":true},"pagination":{"page":0,"page_size":100}}` | Facilitator league table, Base, 30 days | `https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.facilitators.list` | same with `"timeframe":0` | Base, all time | `https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.facilitators.list` | same as the 30-day call without `"chain"` | All chains, 30 days | `https://www.x402scan.com/api/trpc/public.facilitators.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.facilitators.bucketedStatistics` | `{"timeframe":0,"numBuckets":400,"chain":"base"}` | Daily Base series by facilitator; the basis of 3.3 | `https://www.x402scan.com/api/trpc/public.facilitators.bucketedStatistics?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%7D%7D` |
| `public.sellers.all.list` | `{"timeframe":30,"chain":"base","sorting":{"id":"total_amount","desc":true},"pagination":{"page":0,"page_size":100}}` | Top Base recipients by USDC, 30 days | `https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.sellers.all.list` | `{"timeframe":0,"chain":"base","sorting":{"id":"tx_count","desc":true},"pagination":{"page":0,"page_size":100}}` | Top Base recipients by tx, all time | `https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.sellers.all.list` | 30-day USDC call plus `"facilitatorIds":["mrdn"]` | One facilitator's sellers (Meridian), 30 days; use `timeframe` 0 for all time | `https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` (all time: `https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D`) |
| `public.sellers.all.list` | same with `"facilitatorIds":["fluxa"]` | FluxA's sellers, 30 days | `https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22fluxa%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.buyers.all.list` | `{"timeframe":30,"chain":"base","sorting":{"id":"total_amount","desc":true},"pagination":{"page":0,"page_size":100}}` | Top Base buyers by USDC, 30 days | `https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.buyers.all.list` | same plus `"facilitatorIds":["mrdn"]` | Meridian's buyers, 30 days | `https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` (all time: `https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22mrdn%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D`) |
| `public.buyers.all.list` | same plus `"facilitatorIds":["fluxa"]` | FluxA's buyers, 30 days | `https://www.x402scan.com/api/trpc/public.buyers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22facilitatorIds%22%3A%5B%22fluxa%22%5D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.sellers.bazaar.list` | `{"timeframe":30,"chain":"base","sorting":{"id":"total_amount","desc":true},"pagination":{"page":0,"page_size":100}}` | Bazaar-registered origins on Base, 30 days | `https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.sellers.bazaar.list` | same with `"timeframe":0` | Bazaar-registered origins on Base, all time | `https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.sellers.bazaar.list` | `{"timeframe":30,"chain":"solana","sorting":{"id":"tx_count","desc":true},...}` | Solana registered origins, 30 days by tx | `https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22tx_count%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.sellers.bazaar.list` | `{"timeframe":0,"chain":"solana","sorting":{"id":"total_amount","desc":true},...}` | Solana registered origins, all time by USDC | `https://www.x402scan.com/api/trpc/public.sellers.bazaar.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22solana%22%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D` |
| `public.stats.bucketed` | `{"timeframe":0,"numBuckets":400,"chain":"base","recipients":{"include":["0xe9030014f5dae217d0a152f02a043567b16c1abf"]}}` | Daily series for one recipient (example: BlockRun); swap the address | `https://www.x402scan.com/api/trpc/public.stats.bucketed?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22numBuckets%22%3A400%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220xe9030014f5dae217d0a152f02a043567b16c1abf%22%5D%7D%7D%7D` |
| `public.stats.overall` | `{"timeframe":30,"chain":"base"}` | Per-chain overall stats, 30 days | `https://www.x402scan.com/api/trpc/public.stats.overall?input=%7B%22json%22%3A%7B%22timeframe%22%3A30%2C%22chain%22%3A%22base%22%7D%7D` |
| `public.stats.overall` | `{"timeframe":0,"chain":"base"}` | Same, all time | `https://www.x402scan.com/api/trpc/public.stats.overall?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%7D%7D` |

- **Good for.** The only free daily series by chain (since 2025-05-09), by facilitator and by recipient; top sellers and buyers with total_amount or tx_count sorting; facilitator-filtered seller and buyer lists (how the Meridian and FluxA flows in 3.6 were found). Its facilitator volumes match x402-list.com's.
- **Bad for, and quirks.**
  - It counts indexed USDC transfers made by facilitators, not HTTP calls. It cannot tell a paid API call from a payment between related wallets.
  - It indexes only transfers sent by facilitator addresses in its registry ([sync configuration](https://github.com/Merit-Systems/x402scan/blob/main/sync/transfers/trigger/lib/facilitators.ts)). Self-hosted facilitators and unregistered signers are invisible. FluxA's current signer is reported missing, so FluxA may be understated ([their notes](dd_token_facilitators.md)).
  - It shows only facilitators with at least 100 transactions in the window (`MIN_FACILITATOR_TRANSACTIONS = 100`, [lib/facilitators.ts](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/lib/facilitators.ts)). Smaller facilitators appear as "<100 tx" in the digest.
  - "Unique buyers/sellers" per chain are sums across facilitator rows ([networks/list.ts](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/services/transfers/networks/list.ts)), so wallets that use several facilitators are counted more than once. Daily distinct counts summed over a month over-count further.
  - Only 1-, 7-, 14-, 30-day and all-time windows are materialised ([time-range.ts](https://github.com/Merit-Systems/x402scan/blob/main/apps/scan/src/lib/time-range.ts)), so true monthly distinct buyers and sellers cannot be built. Use the daily series for monthly sums.
  - It indexes Base, Solana, Polygon and Optimism only (all-time Polygon 190 tx, Optimism none). Stellar, Celo, Monad, XRPL, Arc and others advertised in the Bazaar are outside its numbers.
  - Solana seller coverage in the notes is the top-100 pages of 705 registered recipients.
  - Names come only from registered origins. Unregistered recipients show as "(unregistered)". The researcher could not identify large unlabeled recipients: Blockscout blocks scripted lookups (HTTP 403) and Etherscan-family APIs need a key.

#### 4.2 Coinbase CDP x402 Bazaar discovery API
- **URL.** `https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=1000&offset=0` (read on 2026-10-11 with `limit` and `offset`; 32,169 resources read). Each resource has a `quality` block with 30-day calls and unique payers, and an `accepts` list of networks.
- **Good for.** Per-resource and per-host 30-day calls and payers, the networks each seller advertises, and host concentration (3.4, 3.8).
- **Bad for.** It covers Coinbase-facilitated resources only. `accepts` counts are supply, not usage. Every resource shows a last call within 30 days, so the Bazaar's own probing probably adds about one call per resource per month (inference). The median resource had 2 calls in 30 days. [gold-402](https://github.com/Haustorium12/gold-402) says most of the catalogue no longer answers a live 402. Single hosts can dominate (AX1 holds 43.8% of calls; agents.chain.link has 45,575 calls from 3 payers).

#### 4.3 x402-list.com
- **URL.** [x402-list.com](https://x402-list.com) (page dated 2026-10-11; operator not stated on the page fetched). A directory of 944 services with on-chain facilitator volumes. Trailing 30 days: Coinbase $572,269, FluxA $322,408, Polygon Facilitator $141,064, Meridian $130,663. It says listed services cover 34.8% of measurable flow, its top 10 services hold 97.1% of settlement volume, and it measures 10,871 distinct on-chain buyers across 713 services.
- **Good for.** Independent corroboration of x402scan: its Coinbase, FluxA and Meridian 30-day volumes match x402scan's ($580K for Coinbase across all chains, $322K, $129K). Also Polygon facilitator volume and a second buyer count.
- **Bad for.** Operator unknown. The Polygon figure is not Base. It does not remove the Meridian loop ($130,663 is shown as volume).

#### 4.4 x402watch (PrintMoneyLab)
- **URLs.** Site [x402.printmoneylab.com](https://x402.printmoneylab.com); daily data in [github.com/printmoneylab/x402watch-data](https://github.com/printmoneylab/x402watch-data) (CC0 files). Page updated 2026-10-02: wash-filtered index, 109,693 services and 24.4M transactions analysed, "86.8% real volume". Snapshot 2026-10-10: 45,836 buyers labelled "organic_user" and 87.4% of 30-day volume classed real.
- **Good for.** Machine-readable daily snapshots and a buyer classification.
- **Bad for.** The wash label is too narrow and unstable. It flags only $979 as wash in the 30 days to 2026-10-10 while the Meridian loop moved $129K. Its flagged wash volume was $130,774 in the 2026-08-10 snapshot and $57 in the 2026-09-10 one. Do not read "real volume" as real commerce.

#### 4.5 agenteconomy.to
- **URL.** [agenteconomy.to](https://agenteconomy.to) (updated 2026-10-11). A cross-protocol dashboard covering x402, ERC-8004, Tempo MPP, Virtuals ACP, Olas and Masumi, citing Dune authors @thechriscen, @hashed_official, @ax1research and @adrian0x. It shows 191.8M x402 tx and $41.9M settled across 12 chains, 626.6K registered agents across 24 chains (ERC-8004), and 19.4M Olas transactions (not x402).
- **Good for.** Cross-protocol context and agent-registration counts.
- **Bad for.** Its x402 totals are lower than x402scan's all-time 233.8M tx and $55.5M (Base, Solana and Polygon); the sources differ. Olas counts are not x402. The underlying Dune queries were not readable.

#### 4.6 Dune dashboards
- Authors named by agenteconomy.to: @thechriscen, @hashed_official, @ax1research (the research arm of AX1, section 2 rank 3) and @adrian0x. The Dune profile pages load client-side and showed no dashboards for @x402 or @hashed_official, so the researcher could not read any dashboard or compare 2026 facilitator shares against them.
- The December 2025 claim that Dexter overtook Coinbase (about half of daily tx) came from Dune data cited by Hashed and covers all chains; see 3.3.

#### 4.7 Other sources and how far to trust them
| Source | URL | What it says | Reading |
|---|---|---|---|
| Valoria | `https://x402.valoria.net` | $148.2M tracked volume, 102,319 services, 586.3M payments; top earner x402.arvos.xyz at $57.6M | Unreliable: 2.7x the whole market; x402scan shows ARVOS at $11.5M |
| x402.org home | `https://x402.org` | Static page "last updated 2026-08-25": 75.41M tx, $24.24M, 94.06K buyers, 22K sellers for 30 days | Not reconciled: 5.2x x402scan on tx and 19x on USDC; cites no source |
| presenc.ai | `https://presenc.ai/research/x402-protocol-adoption-tracker-2026` | About 167M settled tx, about 85% on Base (snapshot 2026-05-15); CoinDesk's estimate of about $28K a day of real commerce in March 2026 | Total matches x402scan; share does not |
| Chainalysis | `https://www.chainalysis.com/blog/x402-agentic-payments-adoption/` | More than 100M Base tx through Q1 2026; PING pay-to-mint; payer retention 87% falling to 5%; payments of $1 or more rose from 49% to 95% of value | Consistent with x402scan |
| Solana Compass | `https://solanacompass.com/news/solana-flips-base-in-daily-x402-transactions-for-the-first-time-in-six-months` and `https://solanacompass.com/news/solana-processes-76-of-all-x402-ai-agent-transactions-232-million-in-four-weeks` | Solana passed Base on 2026-08-25; Solana 76% of x402 tx (23.2M) in four weeks to 2026-09-22 | Direction agrees with x402scan; the "first time in six months" framing does not (3.5, 3.9) |
| Coin-Turk | `https://en.coin-turk.com/solana-overtakes-base-with-90yuzde-share-in-x402-transaction-volume-and-count/` | Solana over 35M tx and about $10M since launch (2026-09-04) | Via the rivals notes; x402scan has 54% more tx and about 20% less USDC |
| Foresight News via Bitget | `https://www.bitget.com/news/detail/12560605412078` | Cumulative agent payments passed $50M, over 85% on Base (2026-05-14) | Matches x402scan on USDC, not on tx share |
| Cryptopolitan | `https://www.cryptopolitan.com/dexter-overtakes-coinbase-x402-transactions/` | Dexter overtook Coinbase (Dec 2025) | An all-chains claim; on Base x402scan shows Dexter at 0.2% of window tx (3.3) |
| awesome-x402 | `https://github.com/xpaysh/awesome-x402` | 816 linked entries, self-submitted; also names SmartFlow Observatory (claims 22,251 endpoints), Demand Intel (intel.agent402.app), EntRoute, Rencom, nohumans.directory, x402search | Low signal |
| gold-402 | `https://github.com/Haustorium12/gold-402` | 580 hand-checked services; README banner says most of the x402 catalogue no longer answers | Useful sanity check |
| CoinGecko | `https://www.coingecko.com/en/categories/x402-ecosystem`, `https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&category=x402-ecosystem&per_page=250`, `https://api.coingecko.com/api/v3/coins/list?include_platform=true` | 135-coin category and contracts | Category is not usage; the free API rate-limits |
| GitHub search | `https://api.github.com/search/repositories?q=x402&sort=stars&per_page=100` | Stars ranking (300 repos read) | Stars can be inflated (1.8) |
| npm | `https://api.npmjs.org/downloads/range/2026-04-01:2026-10-10/x402-fetch` and `https://registry.npmjs.org/-/v1/search?text=x402&size=250&from=0` | Download ranges and package search | Counts include CI, mirrors, transitive installs; the API rate-limits batches |
| PyPI | `https://pypistats.org/api/packages/x402/overall?mirrors=false` and `https://pypistats.org/api/packages/x402/recent` | `x402` downloads without mirrors (data from 2026-04-08) | Same caveat |
| DefiLlama | `https://api.llama.fi/protocols` | Lists AI-agent DeFi protocols only | No x402 series |
| Artemis | (404) | No page found | No x402 series; the rivals researcher's Artemis-based figures come via Solana Compass |


## 5. The researcher's inferences and gaps (tightened)

### Inferences
**The map**
- The official directory is a marketing list, not a usage list. 116 of 206 entries have no Base settlement or Bazaar footprint by domain, and the active ones are dominated by a few facilitators, BlockRun and a handful of data providers.
- The token-bearing universe is largely unconnected to measured x402 usage. 37 of 62 Base-contract tokens have no matching footprint. Those that do (DREAMS, HEU, MRDN, PAYAI, ANY, OTTO, GLORIA) mostly show large tx counts with tiny dollar amounts, or circular volume (Meridian). PAYAI has no Base contract on CoinGecko; the source lists it here anyway.
- Several assigned names have no visible x402 footprint on Base at all: Mastercard, Visa, Giza, Theoriq, Recall, Spectral, Wayfinder, Zora, Cookie DAO, Cred Protocol, Fluora, Pieverse, Kite AI. Several are Solana- or other-chain-first: Dexter, PayAI's token, Zauth's token, Kite, Pieverse. This is a flag for the researchers covering them, not proof the projects are fake.
- Projects with real, repeated Base usage that are not on the assigned list: BlockRun, FluxA, AX1, Cluster Protocol, ATXP, Anyspend and a tail of small API sellers.

**The ranking (section 2)**
- The uncovered projects with the most Base evidence are infrastructure and gateways (BlockRun, FluxA, ATXP, AX1), not the token-bearing agent projects that dominate the CoinGecko category. The two groups barely overlap.
- Ranks 1, 3, 4 and 5 can be checked quickly because each has one identifiable recipient address on x402scan. Ranks 2, 7 and 17 need a manual look at whether the dollars are product revenue.
- If the angle is "who is actually paying", the clean examples are BlockRun (volume), Laso (real purchases), KORUS (consumer breadth) and the incumbent data providers (credibility). The cautionary ones are Meridian, FluxA's whale flows and the 2025 mint tokens (3.6).

**The metrics (section 3)**
- Base x402 is not growing in dollars. September USDC was about 30% of April's level and about 2% of the November 2025 peak, while transaction counts depend on one or two high-frequency sellers. The apparent June to August surge was BlockRun, not broad adoption.
- The Solana "flip" in August was a three-week episode of one seller's traffic, not a durable share shift; by mid-September Base had most of the tx again. x402scan also has Solana ahead on 26 of 28 days from 2026-01-22 to 2026-02-18, so the "first time in six months" framing is not supported by that dataset.
- The headline USDC totals overstate commerce. About 36% of window volume is a single closed loop and another 15% to 24% is a few large transfers, leaving roughly 27% to 49% that looks like API purchases.
- Package downloads (core npm packages up 2.3x to 3.6x from April to September, PyPI up 1.7x) rise while on-chain USDC is flat to down. Downloads probably reflect builders, CI, transitive installs and the v1-to-v2 migration, not paid usage. v2 was about 84% of framework-wrapper downloads in September (28.1K versus 5.4K a day).
- Coinbase's facilitator is effectively the Base rail by tx (91%) but not by dollars (30%), because the largest dollar flows go through small facilitators (Meridian, FluxA, PayAI) with few counterparties.

### Gaps
**Coverage**
- x402.org/ecosystem is gone. The directory snapshot is as of 2026-07-07, so projects added later show only if they also appear in usage data.
- x402scan indexes Base, Solana, Polygon and Optimism only. Other chains advertised in the Bazaar (Stellar, Celo, Monad, XRPL, Arc and others) are not in the numbers. Solana seller coverage is the top-100 pages of 705 registered recipients.
- x402scan sees only transfers sent by registered facilitator addresses. Self-hosted facilitators and unregistered signers are invisible, and FluxA's signer is reported missing, so FluxA may be understated.
- Status rests on public settlement and Bazaar signals only. Off-chain revenue, private deployments and Solana-only activity are invisible.

**Matching and identification**
- Domain matching misses sellers that use another domain or a shared payTo address, so "unverified" rows may be active. Unnamed recipients stay unidentified: Blockscout blocks scripted lookups (HTTP 403), Etherscan-family APIs need a key, and x402scan names only registered origins. Three large unlabeled recipients (0x57a6b054..., 0x542793a5..., 0xfa02300b...) could not be named.
- CoinGecko categories were fetched only for the 62 Base-contract tokens (the free API rate-limits), and token websites are missing for 2 of 62. Only CoinGecko's coin list and category were checked, so a token launched elsewhere (for example on a launchpad without a CoinGecko page) would be missed.
- For most uncovered projects no token was found, on that same limited check.

**Metrics**
- Monthly unique buyers and sellers cannot be built from x402scan: only daily sums and 1/7/14/30-day/all-time windows exist, and they over-count wallets across facilitators.
- x402scan counts transfers, not HTTP requests, and cannot tell a paid API call from a payment between related wallets. The real-commerce range classifies recipients, not intent.
- The cause of the unreconciled x402.org figures (75.41M tx, $24.24M) is unknown. The page is static WordPress content and cites no source.
- Dune dashboards were unreadable, Artemis returned 404, DefiLlama has no x402 series and base.org/ecosystem is client-rendered. The search budget ran out mid-task, so no Messari, Galaxy, The Block or Coinbase publication with 2026 monthly x402 figures was found.

**The ranking**
- The ranking is the researcher's judgment from public settlement data. There is no revenue, user, funding or token-holder data, and "importance" is not independently measurable.
- Several top names (Cluster Protocol, ATXP, x402.boats, Vishwa) describe themselves vaguely in the registry. The researcher did not open their products to confirm what is sold.

**Digest note: inconsistencies in the source notes to check before citing**
- Questflow: the reconciliation says its own seller origin has 21 tx; the directory domain match shows questflow.ai as a seller with 274,533 tx / $8,267 all-time (last 2026-03-02).
- ATXP: its row in 1.4 links to recipient 0x7f9d1a87... (iou.atxp.ai, listed in 1.5 with 1.4K tx / $336K in Oct-Dec 2025), but its window figures (314K tx / $122K) match hub.atxp.ai, recipient 0x10c14002... in 3.4 and section 2.
- The "another 21 show 1 to 99" count includes four facilitators (Questflow, Dexter, Heurist, Treasure) with fewer than 100 tx in 30 days, shown by x402scan only as "<100 tx" because of its display floor.
