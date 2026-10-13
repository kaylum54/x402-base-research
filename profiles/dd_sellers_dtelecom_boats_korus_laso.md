# Due diligence: four x402 sellers (dTelecom, x402.boats, KORUS, Laso Finance), as of 2026-10-11

> Status: WORK IN PROGRESS. dTelecom profile written; x402.boats, KORUS and Laso Finance still to come. File is rewritten after each project.
> Window for "last six months": 2026-04-11 to 2026-10-11. No token price or chart analysis. Labels used: **[confirmed]** (primary source or my own data pull), **[company-reported]** (project's own claim, not independently checked), **[inference]** (my reading of evidence), **[unconfirmed]** (could not verify).
> My own data pulls (x402scan public tRPC API, all transfers per recipient, pulled 2026-10-11 about 13:30-14:40 UTC): [recipient list pattern](https://www.x402scan.com/api/trpc/public.sellers.all.list?input=%7B%22json%22%3A%7B%22timeframe%22%3A0%2C%22chain%22%3A%22base%22%2C%22recipients%22%3A%7B%22include%22%3A%5B%220x47d3394c7234714e4b9e9b74827c12be847f9dda%22%5D%7D%2C%22sorting%22%3A%7B%22id%22%3A%22total_amount%22%2C%22desc%22%3Atrue%7D%2C%22pagination%22%3A%7B%22page%22%3A0%2C%22page_size%22%3A100%7D%7D%7D) and the transfer-level endpoint `public.transfers.list` (same input shape plus `sorting: block_timestamp`, `page_size` up to 1000). Starting identifiers came from the [ecosystem map notes](ecosystem_map_and_metrics.md).

---

## 1. dTelecom (DTEL)

### One-line
A Cyprus-registered company running a "decentralized" voice, video and speech API network (WebRTC, speech-to-text, text-to-speech) on its own co-located nodes, with a consumer meetings app (dMeet) on top; its x402 gateway sells prepaid credits for those services to AI agents. ([dtelecom.org](https://www.dtelecom.org/), [x402 gateway](https://x402.dtelecom.org), accessed 2026-10-11)

### x402 role
Seller / resource server. It sells prepaid "credits" (USDC buys credits via `POST /v1/credits/purchase`; credits then pay for WebRTC, STT and TTS sessions authenticated by wallet signature). Also accepts MPP (USDC on Tempo) and USDT on TRON via the Bank of AI facilitator. It also ships a client SDK (`@dtelecom/x402-client`) and a voice-agent framework (`@dtelecom/agents-js`), so it is partly SDK/tooling. ([gateway docs](https://x402.dtelecom.org/docs.md), [llms.txt](https://x402.dtelecom.org/llms.txt), accessed 2026-10-11)

### Chains
Accepts Solana, Base, Tempo and TRON. All real settlement volume is on Base: x402scan all-time Base 52,722 tx / $111,956 (59 buyers) against Solana 46 tx / $16.36 (11 buyers, last 2026-08-13). So Base is primary for x402 revenue, though the company's own network is Solana-based. Single facilitator on Base: Coinbase (CDP). ([x402scan Base](https://www.x402scan.com/recipient/0x47d3394c7234714e4b9e9b74827c12be847f9dda), [x402scan Solana recipient](https://www.x402scan.com/recipient/8MPzJeXx1RipFmRADExptc3UK4EV3nhEFN6NRSx7o7jm); both pulled 2026-10-11)

### Token
- Ticker DTEL. CoinGecko page exists (categories AI, DePIN, AI Agents, x402 Ecosystem) but lists no contract address and says DTEL is not yet tradable. ([CoinGecko](https://www.coingecko.com/en/coins/dtelecom), accessed 2026-10-11)
- Chain: CoinGecko and the company's llms file say the network runs on Solana; a DePIN directory says Arbitrum (conflict, [unconfirmed]). Base contract: **none found**. ([dTelecom llms-full](https://www.dtelecom.org/llms-full.txt), [DePINHub](https://depinhub.io/projects/dtelecom))
- Launch: **has not launched** as of 2026-10-11 [confirmed by absence on CoinGecko; no TGE announcement found]. The TGE target has slipped: "late 2025" in third-party posts, "Q2 2026" in the company's llms file and a March 2026 article, and "Q3-Q4 2026, no fixed date" on the official airdrop page read on 2026-10-11. ([airdrop page](https://www.dtelecom.org/airdrop), [Bittime, March 2026](https://www.bittime.com/en/blog/dtelecom-platform-voice-video-dan-chat-depin))
- Method of distribution so far: points program ("airdrop") with a $2.5M then $2.6M Phase 2 pool, quest platforms (Zealy, Galxe, TaskOn, QuestN), and a paid "Origin ID" NFT sale (15,000+ paid mints announced 2026-05-21). ([airdrop post](https://blog.dtelecom.org/2-600-000-airdrop-campaign-phase-2-is-live-d31733bc0bed), [Origin IDs post](https://blog.dtelecom.org/15-000-paid-origin-ids-show-real-demand-for-dtelecom-before-tge-27fcd48f7791), via the blog RSS feed)
- Stated utility [company-reported]: total supply 1,000,000,000; 50% community / 35% founders, team and investors / 15% ecosystem; node staking (about $10,000 of DTEL per node), fees, governance, payment discounts; customer payments split 75% node operators / 5% burn / 20% operations. ([llms-full](https://www.dtelecom.org/llms-full.txt))
- Does it do real work in the product? **No, not yet.** The x402 gateway is paid in USDC (and USDT on TRON); the token does not exist on exchanges. Points are earned by using dMeet, FROGY and the voice-agent product; the points page does not list x402 credit purchases as point-earning. ([airdrop page](https://www.dtelecom.org/airdrop))

### Team
| Person | Role | X | GitHub | How verified | Doxxed? |
|---|---|---|---|---|---|
| Petr Malyukov | Co-founder and CEO | @MalyukovPetr | `richmal` | GitHub profile bio reads "Co-Founder & CEO at @dTelecom", its `twitter_username` field is MalyukovPetr, and the account is a public member of the dTelecom GitHub org; the Feb 2026 seed-round post is signed "Petr Malyukov, Co-Founder & CEO" with a LinkedIn link (linkedin.com/in/petrmalyukov). Confidence: high. | Yes (real name, public LinkedIn) |
| Vadim Filimonov | Co-founder and CTO | none found | `fffilimonov` | Role from dTelecom's llms-full file and a 2025-05-23 Quicknode Q&A. GitHub profile name "Vadim", public member of the dTelecom org, author of 42 of 44 public commits since April 2026 (handle matches surname; inference, not self-declared). Confidence: medium-high. | Yes (real name on company materials) |
| "Roman" | Engineer (contributor) | none found | `Hoenhaim` | Two commits on 2026-04-06 to `dTelecom/client-sdk-js` (a fork of a LiveKit client SDK). Surname unknown. Only tie is the commits. | Unknown (first name only) |

Sources: [GitHub richmal](https://github.com/richmal), [GitHub fffilimonov](https://github.com/fffilimonov), [Hoenhaim](https://github.com/Hoenhaim), [org members](https://github.com/orgs/dTelecom/people), [seed-round post](https://blog.dtelecom.org/dtelecom-opens-its-seed-round-investing-in-the-real-time-infrastructure-for-humans-and-ai-agents-652e2d15dc2a), [Quicknode Q&A, 2025-05-23](https://www.quicknode.com/blog/feature-fridays-dtelecom), [llms-full](https://www.dtelecom.org/llms-full.txt). Accessed 2026-10-11. No other named staff found; no joins or departures found.

### Track record and pivots
- ~2016: Petr says he began exploring decentralised technology more seriously (Quicknode Q&A, 2025-05-23).
- Before dTelecom [company-reported, not independently confirmed; two searches found nothing]: Petr "co-founder and CEO of YOUS (yous.ai)"; Vadim "CTO at Connect.Club". ([llms-full](https://www.dtelecom.org/llms-full.txt))
- 2022-02: company founded as a decentralised real-time communication (WebRTC) network on Solana [company-reported]; GitHub org created 2022-11-14. ([GitHub org](https://github.com/dTelecom))
- By 2025-05: ElevenLabs development grant, MagicBlock partnership, Privy onboarding partnership, a NEAR MetaBUILD III hackathon prize [all company-reported in the Q&A]. ([Quicknode](https://www.quicknode.com/blog/feature-fridays-dtelecom))
- 2025-06: Solana validator launched [company-reported]. ([dtelecom.org](https://www.dtelecom.org/))
- Late 2025 to 2026: points/airdrop campaign ($2.5M, then $2.6M Phase 2), dMeet consumer meetings app and FROGY livestreaming app built on the network.
- 2026-02-10 onward: speech-to-text clients and MCP server repos; 2026-02-24 seed round opened; 2026-03-03 x402 gateway registered on x402scan and npm client created.
- 2026-05 to 2026-09: blog pivots to "meetings become memory" (team workspaces, recording, end-to-end encrypted chat), not x402.
- Reading: one core idea for four years (cheap real-time voice/video infrastructure), re-labelled as DePIN, then AI voice agents, then agent payments, then AI meeting memory. [inference]

### Trend-hopping score: 2 of 5
Justification: same founders and same product line since 2022 (real-time communication nodes); x402/MPP/TRON are payment add-ons to existing APIs. Score is not 1 because the story changes with the cycle (DePIN, then AI voice agents, then x402 and MPP, then AI meeting memory) and the token/airdrop is the main marketing frame. Not higher because there is a working product (dMeet apps in the stores, SDKs) behind each label. [inference]

### Funding
- Company says it raised $1.2M ($400K pre-seed plus $800K private round) and received grants from the Solana Foundation, Google, ElevenLabs and peaq; no investor names. ([llms-full](https://www.dtelecom.org/llms-full.txt)) [company-reported]
- The 2026-02-24 seed-round post says "$1.5M in our previous round" (conflicts with $1.2M) and opens a Seed Round to institutional investors, terms under NDA. ([blog](https://blog.dtelecom.org/dtelecom-opens-its-seed-round-investing-in-the-real-time-infrastructure-for-humans-and-ai-agents-652e2d15dc2a)) [company-reported]
- Dealroom reportedly lists "no known external funding" (seen only through a search snippet; Dealroom, Crunchbase and RootData pages returned 403 or no result, so [unconfirmed]). No lead investors found. No evidence of a closed seed round as of 2026-10-11.

### Product and traction
- Live [confirmed by fetching]: WebRTC SDK, AI voice agent SDK, STT API (Parakeet-TDT and Whisper), TTS (Kokoro), x402 gateway, dMeet (web, iOS, Android), FROGY, cloud.dtelecom.org console. Prices: WebRTC $0.001 per participant-minute, STT $0.006/min, TTS $0.008 per 1K characters, bundle about $0.015/min, minimum purchase $0.10. ([x402 gateway](https://x402.dtelecom.org), [pricing API](https://x402.dtelecom.org/v1/pricing))
- Company-reported usage: "45M+ minutes processed, 70K+ community" (2026-02-24); homepage on 2026-10-11 says "110,000+" community; earlier copy says "35M+ minutes". No dated revenue figure. Public Dune dashboard exists but could not be read. ([blog](https://blog.dtelecom.org/dtelecom-opens-its-seed-round-investing-in-the-real-time-infrastructure-for-humans-and-ai-agents-652e2d15dc2a), [site](https://www.dtelecom.org/))
- x402 settlement on Base, my pull of every transfer (x402scan, 2026-10-11): all-time 52,935 tx / $112,433 from 59 wallets. By month (tx / USDC / distinct buyers): Feb 31 / $0.78 / 4; Mar 38 / $9.61 / 13; Apr 194 / $6.80 / 5; May 651 / $20.17 / 2; Jun 1,667 / $2,676 / 18; Jul 14,220 / $30,786 / 25; Aug 14,006 / $30,830 / 30; Sep 16,315 / $35,239 / 26; Oct 1-11 5,813 / $12,865 / 25. Last 30 days (since 2026-09-11): 16,788 tx / $36,883 / 25 buyers. Window total about $112.4K, rank 16 of Base recipients by USDC ([ecosystem map](ecosystem_map_and_metrics.md)).

### x402 volume: how much looks like real paying use
**Short answer: only a trivial slice (about $37 before June) is clearly tinkerer-type use; the other ~99.9% ($112K) comes from 29 single-purpose wallets whose pattern looks automated, and I found no evidence of independent customers. Best guess for "real independent paying use": 0-25%, low confidence.**
Evidence (all from the transfer-level pull, 2026-10-11):
1. Before 2026-06-01: 914 tx, $37.36, 21 buyers, mostly $0.025 and $0.10 payments: developers trying the API. That looks genuine and tiny.
2. From 2026-06-22: 29 wallets with 200+ purchases each supply 98.7% of USDC and 99.2% of tx. All 29 use exactly one price point per wallet (for example one wallet paid exactly $5.00 2,482 times; another $1.00 5,140 times; another $0.50 6,219 times). 19 of the 29 first appear between 2026-06-22 and 2026-07-03 and carry 89.6% of lifetime USDC.
3. Every one of these wallets has only ever paid dTelecom: x402scan shows 1 unique seller for each (only the wallets from the early test period have paid other sellers).
4. Clock-like schedules: 10 wallets pay at near-fixed intervals around the clock (hourly, every 2, 3 or 4 hours; coefficient of variation of gaps below 0.5, all 24 hours of the day used). They carry $51.6K, 45.9% of lifetime USDC. The other 19 are bursty with a day/night rhythm (could be usage-driven top-ups).
5. Flat plateau: from 2026-09-15 to 2026-10-10 the gateway took between 458 and 565 purchases a day (median 558, about $1,224 a day), with no weekend dip (Mon-Sun counts within about 12% of each other).
6. Capacity cross-check: `/v1/servers/status` on 2026-10-11 around 13:44-13:45 UTC (4 polls) showed 1 STT server (capacity 100, 0 active sessions) and 1 TTS server (capacity 10, 0 active sessions). $1,224 a day at the STT list price of $0.006/min would be about 204,000 minutes a day, about 142 streams running all day, above the single STT server's capacity of 100. Credits can also buy WebRTC minutes ($0.001) so this is not proof, but there is no sign that the credits are being consumed on the speech servers. [inference]
7. Developer tooling uptake is tiny: `@dtelecom/x402-client` had 165 npm downloads in the 30 days to 2026-10-10 and no release since 0.2.1 on 2026-03-05. ([npm](https://www.npmjs.com/package/@dtelecom/x402-client), [downloads API](https://api.npmjs.org/downloads/point/last-month/@dtelecom/x402-client))
8. Recipient wallet is a normal externally owned account with 117 outgoing transactions and a $376 USDC balance on 2026-10-11, so revenue is swept out regularly (cannot tell where to).
9. Points program ties points to usage and warns of farming, but does not list x402 purchases as earning points. Some other incentive, a partner integration, or internal dMeet traffic could also explain the wallets; I cannot tell which. [unconfirmed]
What I cannot show: who owns the 29 wallets, or where they are funded from (public RPC log queries are capped at 50 to 5,000 blocks, explorers sit behind bot checks).

### Last six months (2026-04-11 to 2026-10-11)
- Dated shipping (company blog RSS, 10 posts in the window; no x402 post): 2026-05-01 online schools post; 2026-05-07 meeting follow-up tools; 2026-05-21 Origin IDs sale result (15,000+); 2026-05-25 dMeet partner program (50% referral commission); 2026-06-01 dMeet chat end-to-end encrypted by default; 2026-06-16 and 06-24 "AI teammates" and "meetings become memory" essays; 2026-07-01 end-to-end encrypted 1:1 calls; 2026-07-20 Team Workspaces (shared AI memory); 2026-09-30 meeting recording in dMeet. ([blog RSS](https://blog.dtelecom.org/feed))
- x402 side: gateway docs mention MPP/Tempo and TRON-USDT via Bank of AI (dates not stated); no new public x402 SDK release since 2026-03-05 (x402-client 0.2.1) and 2026-03-16 (agents-js 0.3.7). ([npm registry](https://registry.npmjs.org/@dtelecom%2fx402-client))
- GitHub (org `dTelecom`, 44 public repos, all repos pushed since 2026-04-01 checked; `gh api`, 2026-10-11): commits per month Apr 3, May 32, Jun 6, Jul 3, Aug 0, Sep 0, Oct 0; total 44 (docs 1, dtelecom-live 2, secure-chat-client 26, vodozemac-wasm 4, livekit fork 9, client-sdk-js fork 2). Last commit 2026-07-30 (docs). Releases on GitHub: none. Active contributors: 2 (Vadim 42, "Roman" 2). Several commits carry a "Co-Authored-By: Claude Opus" trailer, so the team uses AI coding tools. The gateway server code is not in the public repos, so private activity is unknown.
- Team joins/departures: none found.

### Pace verdict
Slow in public. The reference x402 repo (x402-foundation/x402) averages roughly 20 commits a week through the window (weekly totals 8 to 41); a small AI-assisted team in 2026 would typically show weekly commits and monthly releases. dTelecom's public repos show 44 commits in six months, none in August to October, no GitHub releases and no x402 SDK release for seven months. Blog cadence (about 1.5 posts a month, all dMeet) shows the product team is still shipping, but the shipping is consumer meetings, not the x402 gateway. ([x402 repo activity](https://api.github.com/repos/x402-foundation/x402/stats/commit_activity), [dTelecom repos](https://api.github.com/orgs/dTelecom/repos?sort=pushed&per_page=30))

### Direction
Stated: TGE and airdrop conversion (target slipped to Q3-Q4 2026), seed round (opened 2026-02-24), node operators, "communication layer for AI Agents and Humans", x402/MPP gateway. Shipping record: dMeet AI meeting features, encryption, partner programme; x402 work stopped at the March SDK release. The record points to a meetings-app business with an agent-payments storefront on the side. [inference]

### Competitors
- Centralised voice stacks the company benchmarks itself against: Twilio, LiveKit, Agora, Deepgram, ElevenLabs ([dtelecom.org](https://www.dtelecom.org/)); its WebRTC stack is a LiveKit fork.
- x402-native speech sellers visible in the Coinbase Bazaar snapshot (pulled earlier on 2026-10-11 by the ecosystem-map researcher; not re-pulled): dicta-notes.com (live streaming speech-to-text with prepaid sessions), voice.forgemesh.io and x402.forgemesh.io (TTS and transcription), agent402.tools, medien.halowerk.com, x402.nexari.cloud. dTelecom itself does not appear in the Bazaar listing. I did not compare their volumes. [unconfirmed who is ahead]
- Company X account reportedly claims dTelecom is "#2 by payment volume on x402": seen only via a search summary, [unconfirmed]; the x402scan data above does not support it for Base (rank 16 by USDC in the window).

### Green and red flags
- Green: four-year-old company with named, public founders; real shipped products (dMeet apps, SDKs, STT/TTS stack); working gateway with clear pricing and docs; consistent use of AI coding tools; revenue-style framing is conservative about token.
- Red: x402 volume is concentrated in 29 single-purpose, fixed-amount wallets with clock-like schedules; no sign of capacity use; TGE slipped from Q2 to Q3-Q4 2026; conflicting funding figures ($1.2M vs $1.5M); points programme plus paid NFT sale creates an incentive to show activity; public engineering quiet since 2026-07-30; company claims ("#2 on x402", usage numbers) are not checkable.

### Verdict
**Credible but small. Momentum: Slowing.** dTelecom is a real, long-running company with identifiable founders and a working voice/meetings product, so it is not a phantom. But the x402 line is the weakest part of the story: the headline $112K and 53K transactions come from about 29 automated-looking wallets that buy only from dTelecom, and the public x402 tooling has not been touched since March. I would follow it for the token event (TGE slipped twice) and for whether the 29 wallets keep paying; I would not use its x402 numbers as evidence of agent demand. If the plateau of about $1.2K a day stops or the wallets change behaviour, that would be the clearest tell. Where it is heading: a dMeet-centred AI meetings product funded by token and seed fundraising, with x402 kept as a marketing channel.

### Tracking card
- Website: https://www.dtelecom.org ; x402 gateway: https://x402.dtelecom.org (docs: /docs.md, /openapi.json, /llms.txt, status: /v1/servers/status, pricing: /v1/pricing, discovery: /.well-known/x402)
- Docs: https://docs.dtelecom.org ; Blog: https://blog.dtelecom.org ; RSS: https://blog.dtelecom.org/feed ; Changelog: none found (use the blog and GitHub)
- GitHub org: https://github.com/dTelecom ; key repos: x402-client, agents-js, stt-mcp, docs, dtelecom-live, secure-chat-client, livekit (fork)
- npm: @dtelecom/x402-client, @dtelecom/agents-js
- X: project @dtelecom (linked from the official site and GitHub org); Petr Malyukov @MalyukovPetr; Vadim Filimonov none found. (A search summary mentioned @dTel_org; not verified, ignore unless confirmed.)
- Farcaster: none found. Discord: https://discord.gg/dtelecom ; Telegram: https://t.me/dTelecomNetwork (site) and https://t.me/dtelecomchat (llms-full). LinkedIn: https://www.linkedin.com/company/dtel-org ; Petr: https://www.linkedin.com/in/petrmalyukov
- Dune dashboard: https://dune.com/dtelecom_team/dtelecom ; Apps: dMeet iOS https://apps.apple.com/ru/app/dmeet/id6755107690
- Token contract: none (not launched). 
- x402scan recipients: Base `0x47d3394c7234714e4b9e9b74827c12be847f9dda` (origin https://x402.dtelecom.org, registered 2026-03-03); Solana `8MPzJeXx1RipFmRADExptc3UK4EV3nhEFN6NRSx7o7jm`.

### Sources (accessed 2026-10-11 unless noted)
- https://www.dtelecom.org/ ; https://www.dtelecom.org/llms-full.txt ; https://www.dtelecom.org/airdrop ; https://x402.dtelecom.org ; https://x402.dtelecom.org/docs.md ; https://x402.dtelecom.org/llms.txt ; https://x402.dtelecom.org/v1/pricing ; https://x402.dtelecom.org/v1/servers/status
- https://blog.dtelecom.org/feed ; https://blog.dtelecom.org/dtelecom-opens-its-seed-round-investing-in-the-real-time-infrastructure-for-humans-and-ai-agents-652e2d15dc2a (2026-02-24)
- https://www.quicknode.com/blog/feature-fridays-dtelecom (2025-05-23) ; https://www.coingecko.com/en/coins/dtelecom ; https://www.bittime.com/en/blog/dtelecom-platform-voice-video-dan-chat-depin
- https://github.com/dTelecom ; https://github.com/richmal ; https://github.com/fffilimonov ; https://api.github.com/orgs/dTelecom/repos ; https://registry.npmjs.org/@dtelecom%2fx402-client
- x402scan tRPC API (transfers, sellers, bazaar lists) as described at the top; Base RPC reads (publicnode, drpc) for wallet nonce/balance.

---

## 2. x402.boats
(in progress)

## 3. KORUS
(in progress)

## 4. Laso Finance (LASO)
(in progress)

## Comparison table
(to come after all four profiles)
