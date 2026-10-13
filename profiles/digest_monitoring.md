# Digest: monitoring infrastructure for a daily x402 ecosystem watch

Condensed from the monitoring research notes, which are not published because they describe a private setup; (researched 2026-10-11). Goal: a daily watch of dozens of x402 projects on Base and a few hundred people (about 300 X accounts). Section 1 of the original, on that private setup, has been removed. Section numbers 1-6 match the notes; section 7 is new.

**Reading notes.** Prices are as read on 2026-10-11; most pages carry no effective date and vendors say prices can change. "Live probe" means a read-only request run from a desktop machine on 2026-10-11 (aggregate counts only, no payments, no secrets files opened). The WebSearch quota ran out mid-session, so some checks rest on one page or on search-result summaries; those are flagged.

---

## 2. X data options (October 2026)

**Takeaway.** The official X API is pay-per-use only for new sign-ups, at $0.005 per post read: about $45-$270 a month for 300 accounts. The two per-item API resellers charge $0.00015-$0.0002 per tweet (about 25-33 times less; Apify actors $0.0003-$0.0004) but carry supply and terms risk.

### Recommendation and fallback (researcher's)
- **Primary, a hybrid:** official X Activity API (XAA) push for about 50 core accounts ($15-30 a month). SocialData query monitors or twitterapi.io time-filtered search for the other 250 ($3-8 a month). twitterapi.io batch profile snapshots (cents).
- **Fallback 1:** the long tail on the official API behind the same adapter ($45-$270 a month). **Fallback 2:** xAI `x_search` for one-off questions only, not as a daily collector.
- **Canary:** each week, compare the vendor's results for 5 accounts with the official API (pennies).
- **Rules:** keep the adapter thin. Store raw post IDs and URLs. Avoid anything built on Nitter-style frontends. Use `fxtwitter` (unofficial) for single-handle checks only.

### Official X API (pay-per-use)
- Credits are bought upfront and debited per request; no subscriptions, minimum spend or contracts. Reads per resource returned: Posts $0.005, Users $0.010, Following/Followers $0.010, Lists $0.005. "Owned reads" cost $0.001 per resource when an app reads its own user's data (posts, mentions, bookmarks, followers, lists and similar). Promotions: $20 of credits after saving the first eligible card; the first auto-recharge matched up to $50 ([pricing](https://docs.x.com/x-api/getting-started/pricing)).
- Cap: 3 million post reads a month; more needs Enterprise. Resources are de-duplicated within a 24-hour UTC window (a "soft guarantee"). Only successful responses that return data are billed. Spending limits and auto-recharge exist. The usage page does not define "owned" ([usage](https://docs.x.com/x-api/fundamentals/post-cap)). Third-party guides (search summaries, not fetched) say new sign-ups get pay-per-use only and the free tier closed to new projects on 2026-02-06 ([OpenTweet](https://opentweet.io/answers/is-the-x-api-free-in-2026), [bundle.social](https://bundle.social/blog/x-api-pricing-2026-costs-limits)).
- Rate limits (per app / per user, 15-minute windows): `GET /2/users/:id/tweets` 10,000 / 900 (takes `since_id` and `exclude`; app-only bearer works); `GET /2/users/by` 300 / 900 (up to 100 usernames per call); `GET /2/lists/:id/tweets` 900 / 900; recent search 450 / 300; `GET /2/users/search` 300 / 900. None are listed for pay-per-use apps ([rate limits](https://docs.x.com/x-api/fundamentals/rate-limits), [Get Posts](https://docs.x.com/x-api/users/get-posts), [Get Users By Usernames](https://docs.x.com/x-api/users/get-users-by-usernames)).
- Lists: `GET /2/lists/:id/tweets` returns "the latest Posts from all members of a List", billed as Posts. Adding a list member ("List manage") costs $0.005 ([List Posts](https://docs.x.com/x-api/lists/list-tweets/introduction)).

### X Activity API (XAA, push)
- Events per User ID, by persistent stream (`GET /2/activity/stream`) or webhook: `post.create`, `post.delete`, mention, reply, quote and repost events, plus nine `profile.update.*` events (bio, picture, banner, display name, handle, location, URL, verified badge, affiliate badge). Self-serve limit 1,500 subscriptions (Enterprise 75,000). Each delivered post event is billed as a Post. Public events can be subscribed to by user ID without the user's authorization; protected accounts' posts are never delivered ([intro](https://docs.x.com/x-api/activity/introduction)).
- Subscribe with `POST https://api.x.com/2/activity/subscriptions` (`event_type`, `filter.user_id`, optional `tag`, `webhook_id`). An app-only bearer works for public events. Changing a filter means delete and recreate ([quickstart](https://docs.x.com/x-api/activity/quickstart)). Reading "Profile Updates" costs $0.005 ([pricing](https://docs.x.com/x-api/getting-started/pricing)).
- Webhooks: HTTPS, no port in the URL, reply within 10 seconds, CRC at registration and hourly, marked invalid after about 28 hours of failures, replay via `POST /2/webhooks/replay`, signed in `X-Twitter-Webhooks-Signature-OAuth2` (HMAC-SHA256 over the raw body) ([webhooks](https://docs.x.com/x-api/webhooks/introduction)).

### Third-party providers
- **twitterapi.io:** $0.15 per 1,000 tweets (15 credits per tweet; 1 USD = 100,000 credits). Batch profiles: 18 credits each for 1-99 users, 1 credit each for 100+ (about $0.01 per 1,000 users). Minimum $0.00015 per call. No rate limits on the pricing page; "up to 200 QPS per client" on the docs home ([pricing](https://twitterapi.io/pricing), [docs](https://docs.twitterapi.io/)). Search takes `query` with `from:`, `OR` and `since_time:`/`until_time:` Unix timestamps, 20 tweets per page ([search](https://docs.twitterapi.io/api-reference/endpoint/tweet_advanced_search)). Push monitoring is per account: Starter $29 (6 accounts), Growth $79 (20), Professional $149 (50), Enterprise $299 (150, extra $2 each), Enterprise Plus $499 (500, extra $1 each), Scale $999 (2,000), with a claimed 99.9% uptime SLA ([stream](https://twitterapi.io/twitter-stream)).
- **SocialData:** $0.0002 per item returned. Failed requests are free, and so are the first 3 empty responses a minute. 120 requests/minute per key. User monitors $4.99/month each for 1-10, down to $2.49 above 1,000. Search-query monitors $0.0002 per delivered tweet plus $0.0002 per empty execution, with a floor of about $0.14/month at hourly refresh and $1.73/month at 5-minute refresh. No uptime or SLA statement ([pricing](https://socialdata.tools/pricing.md)).
- **Apify (second-hand):** the apidojo Tweet Scraper V2 shows $0.30 or $0.40 per 1,000 tweets; one user was charged for empty runs ([listing](https://apify.com/apidojo/tweet-scraper/api)). A vendor-authored comparison (biased) lists GetXAPI at $0.05 per 1,000 ([GetXAPI](https://www.getxapi.com/blogs/cheapest-twitter-api-2026-8-providers-ranked-by-real-per-1000-tweet-cost)).
- **xAI `x_search`:** $5 per 1,000 posts and $10 per 1,000 user profiles, plus tokens; up to 20 handles per `allowed_x_handles`; dates `YYYY-MM-DD` only; the model writes its own queries, "so results vary". Pricing cited as in effect on 2026-09-21 ([x_search](https://docs.x.ai/developers/tools/x-search), [pricing](https://docs.x.ai/developers/pricing)).

### Cost of reading about 300 accounts' posts (researcher's estimate; 30-day months)
Assumptions: Low 300 posts/day (about 1 original post per account). Base 600/day (60 founders at 4, 240 engineers at 1.5). High 1,800/day (replies, quotes and reposts included). No source gives posting rates for this population; replace them after one week of data.

| Route | Low (9k/mo) | Base (18k/mo) | High (54k/mo) | Notes |
|---|---|---|---|---|
| Official X, $0.005/post | $45 | $90 | $270 | Under the 3M cap; empty polls free; use `since_id` |
| SocialData, $0.0002/item | $1.80 | $3.60 | $10.80 | Only if reads return new items (time-filtered search or query monitors) |
| twitterapi.io, $0.15/1k | $1.35 | $2.70 | $8.10 | Plus $0.00015 per call floor (about $2/month for 15 hourly queries) |
| Apify apidojo, $0.40/1k | $3.60 | $7.20 | $21.60 | Plus overhead (vendor-reported 30-50%, biased) |
| xAI `x_search`, $5/1k posts | $45+ | $90+ | $270+ | Plus tokens; non-deterministic; adds per-token model spend |
| twitterapi.io push, 300 accounts | $499 flat | $499 | $499 | Enterprise Plus covers 500 accounts |
| SocialData user monitors, 300 | about $1,200 | about $1,200 | about $1,200 | Tiered $3.99-$4.99 per monitor per month |

### Reading the numbers (researcher's inferences)
- **Per-item providers punish naive polling.** If a timeline call returns the latest 20 tweets and bills all 20, polling 300 accounts once a day costs about $36/month at SocialData rates, and four times that at four polls a day, more than the official API. Use `from:a OR from:b ... since_time:<last>` search (about 20 handles per query, an assumption) or SocialData query monitors, which bill only new tweets: about 15 queries, about $2/month plus $0.0002 per tweet.
- **Profile snapshots are nearly free on twitterapi.io:** 300 profiles cost about $0.003 a day. Diff bios, display names, handles, pinned posts and URLs daily to catch rebrands and hires. The official API charges $0.01 per user ($90/month if daily).
- **XAA suits a core tier:** `post.create` ($0.005) for 50 accounts at about 2 original posts a day is about 3,000 events, about $15/month. Profile events cost only when something changes. It needs a Worker webhook (CRC plus signature check) and a bearer token.
- **Lists:** one private list of the 300 accounts gives one stream at $0.005 per post; adding 300 members costs about $1.50. Unverified: whether list posts can exclude replies and reposts, and whether reading your own list counts as a $0.001 "owned read". Test with $1 of credit. If it counts, the official row drops fivefold.

### Reliability and terms risk
- **Reliability.** No independent uptime data exists for SocialData or twitterapi.io. SocialData states no SLA; twitterapi.io claims one for its stream product only. X enforcement is rising, so vendor continuity is the main risk.
- **X Developer Guidelines** ([page](https://docs.x.com/developer-guidelines)): delete X content within 24 hours of a removal request or deletion on X. No training or fine-tuning of ML models on X content (Grok excepted). No inferring sensitive attributes (health, politics, religion, financial status and so on) except in aggregate. "Surveillance" is prohibited, including monitoring users without consent. Linking X data to your own identifiers ("off-X matching") needs express opt-in consent. Use only the official API; never scrape or use browser automation. The page is silent on LLM inference on posts and on private Discord channels.
- **Enforcement.** X sued Bright Data over scraping; a federal court reportedly dismissed its terms-of-service claims on 2024-05-09 and later let X amend, with the outcome unconfirmed ([ZwillGen](https://www.zwillgen.com/data-security/x-gets-aggressive-about-scraping-on-its-platform/), [Mofo](https://www.mofo.com/resources/insights/240604-california-federal-court-holds-x-s-claims)). On 2026-08-24 X Corp sent cease-and-desist letters demanding a permanent takedown of Nitter instances and its repository; Nitter.net went offline ([TechCrunch, 2026-08-25](https://techcrunch.com/2026/08/25/x-sends-cease-and-desist-to-open-source-project-nitter-over-alleged-scraping/)).
- **Exposure cuts both ways (researcher).** The official route is contractually clean, but its guidelines prohibit monitoring users without consent and off-X matching without opt-in, which sits close to this project's purpose. The third-party route sidesteps X's developer contract but breaches X's scraping terms through the vendor. Mitigations (design choice, not legal advice): watch project and organisation accounts plus publicly identified team members' professional accounts only; store post IDs, URLs and derived signals, not full bodies; never infer sensitive attributes; honour deletions within 24 hours; in Discord, post links and the routine's own one-line summaries, not verbatim post text; consider UK GDPR obligations for named individuals.

---

## 3. Finding and verifying engineers' X accounts at scale

**Takeaway.** GitHub's `twitter_username` field is free and was filled in for about half of the core x402 contributors sampled (23 of 45), so it is the first pass. Farcaster (Neynar `by_x_username`), ENS text records, team pages and a cheap DataForSEO `site:x.com` query fill most of the rest. Score every match on independent evidence. A one-off pass for 300 people costs roughly $5-25.

### Pipeline (cheapest first; each step adds evidence and replaces nothing)
1. **Seed names (free).** Team pages, public GitHub org members, repo contributors (top N by commits), npm/PyPI maintainers, project X accounts' bios, the other researchers' people lists. `GET /orgs/{org}/public_members` lists members who chose to be public; `GET /orgs/{org}/members` also lists concealed ones, for org members only; `per_page` max 100 ([org members API](https://docs.github.com/en/rest/orgs/members)).
2. **GitHub `twitter_username` (free).** `GET /users/{username}` returns `twitter_username` (string or null); `GET /user/{account_id}` fetches by durable numeric ID ([users API](https://docs.github.com/en/rest/users/users)). Authenticated REST gets 5,000 requests an hour (60 unauthenticated) ([limits](https://docs.github.com/en/rest/using-the-rest-api/rate-limits-for-the-rest-api)). A `304 Not Modified` answer to an authorized conditional request (ETag / `If-None-Match`) does not use the primary limit ([best practices](https://docs.github.com/en/rest/using-the-rest-api/best-practices-for-using-the-rest-api)). About 300 calls is well under an hour of budget.
   - **Live probe, 2026-10-11 (unauthenticated):** `GET /repos/x402-foundation/x402/contributors?per_page=100` returned 100 entries (99 human accounts). For the first 45 humans by commit count, 23 had `twitter_username` (51%), 21 a `blog` URL, 22 a `company`, 26 a `bio`, 41 a `name`, 0 a public email. It used 46 of the 60 unauthenticated calls an hour ([endpoint](https://api.github.com/repos/x402-foundation/x402/contributors?per_page=100)). Top committers probably overstate the long tail.
3. **Farcaster via Neynar.** `GET /v2/farcaster/user/by_x_username` returns the users who verified a given X username (`x_username` without @, `x-api-key` auth). The user object carries `verified_accounts` (`platform` x or github; only X is supported now), `verifications` (ETH addresses), `custody_address` and `profile.bio.text` ([Neynar](https://docs.neynar.com/reference/lookup-users-by-x-username)). A hit is strong evidence, because the user proved the link. Search by name for people with no handle. Coverage among engineers is unmeasured. Limits: Free 600 requests/minute per endpoint (10/s), 1,000/minute across all APIs, 10M credits a month; Scale $249/month with 60M credits and 1,200/minute; the by-X-username credit cost is not listed ([rate limits](https://docs.neynar.com/reference/what-are-the-rate-limits-on-neynar-apis), [credits](https://docs.neynar.com/reference/compute-units)).
4. **ENS text records (free).** ENSIP-5 recommends the keys `com.twitter` and `com.github` (legacy `vnd.twitter`, `vnd.github`); a client reads `text(node, key)` and gets an empty string if unset ([ENSIP-5](https://docs.ens.domains/ensip/5)). Read them for any ENS name found on GitHub or Farcaster. Self-declared; coverage unmeasured.
5. **Team pages and personal sites (free).** Fetch each project's team/about page and each person's `blog` URL. Extract `x.com/<handle>` and `twitter.com/<handle>` links. High precision where a link exists.
6. **DataForSEO SERP, leftovers only.** Query `site:x.com "Full Name" x402` (or the project name). Google Organic and Google News cost $0.0006 per SERP (10 results) in Standard queue (about 5 minutes), $0.0012 Priority, $0.002 Live. "Multiply by 5 for each parameter used" covers operators including `site:`, and multipliers can stack ([organic pricing](https://dataforseo.com/pricing/serp/google-organic-serp-api), [news pricing](https://dataforseo.com/pricing/serp/google-news-serp-api)). One `site:` makes it $0.003 Standard or $0.01 Live, so 300 queries cost about $0.90-$3. Weak evidence: Google's coverage of x.com profiles is uneven and untested.
7. **Verification fetch.** Official `GET /2/users/by`: 100 usernames per call, $0.01 per user (about $3 for 300), with the `affiliation` expansion ([Get Users By Usernames](https://docs.x.com/x-api/users/get-users-by-usernames)). Avoid `GET /2/users/search` at its default of 100 results ($1 per call); if used, take a user token and set `max_results` to 5-10 ([Search Users](https://docs.x.com/x-api/users/search-users)). twitterapi.io has "Search user by keyword" and "Batch Get User Info By UserIds", at cents ([index](https://docs.twitterapi.io/llms.txt)). Read bio, URL, followers and affiliation for each candidate.

### Match scoring (a design, not a measured model)
+3 Farcaster-verified X username equals the candidate. +2 the X profile URL or bio links back to the person's GitHub login or personal domain (reciprocal link). +2 ENS `com.twitter` equals the candidate. +2 team page or personal site links to the handle. +1 GitHub `twitter_username` equals the candidate. +1 bio names the project or company. +1 X affiliation badge names the project's organisation. +0.5 fuzzy name match. +0.5 SERP-only hit. Accept at 3 or more, send 1.5-3 to a review queue, reject below 1.5. Reciprocity matters most: a self-declared GitHub field alone can be stale or wrong, and impersonators copy names.

### Cost, funnel and policy
About $5-25 one-off for 300 people (SERP $1-3, X verification $3 plus a few $0.10 searches, the rest free). Perhaps a fifth need a manual review. Re-verify monthly with ETag calls and the daily profile diff, and flag any handle whose bio no longer names the project. This step is the closest to X's "off-X matching" and "monitoring users" language (express opt-in consent is required for off-X matching; [guidelines](https://docs.x.com/developer-guidelines)). Keep to public professional links the person published, do not publish the mapping, and record the evidence for each match.

---

## 4. Other daily signals: sources, limits and prices

**Takeaway.** Most useful signals are free: GitHub Atom feeds and REST, npm and PyPI counts, HN's Algolia API, and the CDP x402 Bazaar, which publicly exposes 30-day paid-call counts and unique payers for 32,162 services. Paid pieces are cheap (x402scan reads $0.01 each, DataForSEO news $0.0006 a query). Dune, Etherscan-for-Base and Blockscout cost $49-$399+ a month and are not needed on day one. Discord and Telegram carry terms questions.

### GitHub (free)
- **Atom feeds** need no API quota. Live probe, 2026-10-11: `x402-foundation/x402` `releases.atom` (10 entries) and `commits/main.atom` (20) return 200. A per-user feed `github.com/<user>.atom` returned 30 entries ([releases](https://github.com/x402-foundation/x402/releases.atom)).
- **GitHub Discussions on coinbase/x402:** `discussions.atom` and the Discussions page returned 404 for both `coinbase/x402` and `x402-foundation/x402` ([page](https://github.com/x402-foundation/x402/discussions)). Discussions appear to be off, so there is nothing to collect. Use Issues, PRs and the Events API for community activity.
- **Repo universe** (search API probe): `topic:x402` matches 3,686 repositories; 529 were created after 2026-09-11 and 798 pushed after 2026-10-04 ([search](https://api.github.com/search/repositories?q=topic:x402&per_page=1)). Search limits: 30 requests/minute authenticated (10 unauthenticated), code search 10/minute and authenticated only, at most 1,000 results per search ([search API](https://docs.github.com/en/rest/search/search)).
- **Events and stats:** Events API timelines hold up to 300 events from the last 30 days, with ETag/304 (a 304 is free) and latency of about 30 seconds to 6 hours ([events](https://docs.github.com/en/rest/activity/events)). Statistics endpoints (`commit_activity`, `participation`, `contributors`) are cached, return 202 while computing, and exclude merge commits ([statistics](https://docs.github.com/en/rest/metrics/statistics)).

### npm and PyPI (free)
- **npm:** `GET https://api.npmjs.org/downloads/point/{period}/{pkg}` and `/range/`. Bulk queries take up to 128 comma-separated packages, not scoped ones. `last-day` usually means yesterday (GMT) ([doc](https://github.com/npm/registry/blob/main/docs/download-counts.md)). Live probe: the `x402` package had 90,932 downloads on 2026-10-09 ([API](https://api.npmjs.org/downloads/point/last-day/x402)). Registry search `text=x402&size=250` reports 5,806 packages ([search](https://registry.npmjs.org/-/v1/search?text=x402&size=250)).
- **PyPI:** `x402` had 8,391 downloads last day, 70,494 last week, 204,765 last month. pypistats limits are per IP (no thresholds given); data updates once daily; window 180 days ([pypistats](https://pypistats.org/api/packages/x402/recent), [API](https://pypistats.org/api/)). The PyPI JSON API gives `upload_time_iso_8601` per file; its `downloads` fields are deprecated and always -1 ([PyPI JSON API](https://docs.pypi.org/api/json/)). Counts include mirrors, bots and CI.

### CDP x402 Bazaar (free; the best stalling detector)
- A public catalog of payment-gated services found by the CDP Facilitator. Discovery needs no CDP key. Operations: search (limit up to 20), list (`type`, `limit`, `offset`), list-by-merchant (`payTo`). Search results carry `quality`: 30-day call count, unique payers, last-called time ([docs](https://docs.cdp.coinbase.com/x402/bazaar)).
- Live probe: `GET https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources` returned `total` 32,162. `limit=1000` works (one page is 3.4 MB). Items carry `accepts` (amount, asset, network, payTo, scheme), `extensions` (`bazaar`, `builder-code`), `quality` (`l30DaysTotalCalls`, `l30DaysUniquePayers`, `lastCalledAt`), `resource`, `serviceName`, `tags`. The first five showed 30-day calls from 119 to 409,288 and unique payers from 46 to 4,671. Two of the first 20 carried X/Twitter-data tags, so x402-paid X-data resellers exist ([list](https://api.cdp.coinbase.com/platform/v2/x402/discovery/resources?limit=5&offset=0)).
- Researcher: crawl it all daily (33 requests of 1,000, about 112 MB, so process page by page), storing only changed rows plus a daily aggregate. Snapshot the three `quality` fields per `payTo` or domain. A falling 30-day payer count, or a `lastCalledAt` older than a week for a once-busy service, is hard evidence of fading usage. `builder-code` and `tags` may help attribute services to builders (unverified).

### x402scan (optional; reads are paid)
- Apache-2.0 explorer by Merit Systems; the README mentions no public API ([repo](https://github.com/Merit-Systems/x402scan)). Its `llms.txt` puts the API under `/api/x402`, with an OpenAPI spec at `/openapi.json`, a free `/api/health` and read endpoints paid by x402 micropayments of roughly $0.01-$0.02 ([llms.txt](https://www.x402scan.com/llms.txt)). The OpenAPI lists 14 routes, among them `merchants/{address}/stats`, `wallets/{address}/stats`, `facilitators/stats` and `resources/search`. Unpaid calls return 402; five routes ask 10,000 base units (x402 v2, scheme exact, network eip155:8453, asset starting 0x833589fC) and `resources/search` asks 20,000 ([OpenAPI](https://www.x402scan.com/openapi.json)).
- Researcher: about 20 paid reads a day at $0.01 (facilitators/stats once, merchants/stats for watched `payTo` addresses) is about $6/month. It needs a funded Base wallet key held by the caller. Keep that key out of the Worker: run it from a local machine or routine, or defer it and rely on the free Bazaar. Reading the OpenAPI daily is free and detects new routes.

### Base on-chain and Dune
- The EVM `exact` scheme settles when the facilitator calls the token's `transferWithAuthorization` (EIP-3009, for example USDC). Events carry no facilitator field, so the facilitator is the broadcasting transaction's sender ([spec](https://github.com/x402-foundation/x402/blob/main/specs/schemes/exact/scheme_exact_evm.md)). Base public RPC `https://mainnet.base.org` (chain ID 8453) answered `eth_blockNumber`; the Base docs say nothing on its limits ([docs](https://docs.base.org/base-chain/quickstart/connecting-to-base)).
- **Etherscan V2:** Free $0 (3 calls/s, 100,000/day, "selected chains (90% coverage)"), Lite $49/month (5/s), Standard $199 (10/s, 200,000/day), up to Pro Plus $899. The page does not say whether Base is on Free; the error docs say the free tier excludes some chains, and press reported free Base access was suspended ([plans](https://etherscan.io/apis), [error docs](https://docs.etherscan.io/common-error-messages), [Yahoo Finance](https://finance.yahoo.com/news/ethereum-explorer-etherscan-locks-avalanche-143215634.html)). **Blockscout:** Base needs a paid plan: Builder $49/month (15 RPS, 100M credits), Pro $199, Business $999 ([Blockscout](https://docs.blockscout.com/base-api)). **Dune:** Free is view-only with no API; Analyst $75/month; Plus $399/month ([credits](https://docs.dune.com/learning/how-tos/credit-system)).
- Researcher: do not run an indexer. Use Bazaar `quality`, x402scan stats and public-RPC spot checks (decode `transferWithAuthorization` calls to USDC from known facilitator senders). Etherscan Lite or Blockscout Builder ($49) are the cheapest dependable explorers; skip them until a question needs them. Dune adds little over x402scan and Bazaar.

### News, mentions, forums
- **DataForSEO Google News SERP:** $0.0006 (Standard), $0.0012 (Priority), $0.002 (Live) per SERP of 10 results; operators multiply the cost ([pricing](https://dataforseo.com/pricing/serp/google-news-serp-api)). The endpoint path is unfetched (assumed `serp/google/news/...`). A local `dataforseo-tool` skill documents `serp/google/organic/live` (skill). 50 queries a day in Standard queue is about $0.90/month.
- **DataForSEO Content Analysis** (Live only, 2,000 calls/minute): $0.024 per request plus $0.000036 per row, 1,000 rows maximum ($0.06 for 1,000 rows). It finds citations of a keyword or brand with sentiment, but its overview does not say which sources it covers or how fresh they are ([pricing](https://dataforseo.com/pricing/content-analysis), [overview](https://docs.dataforseo.com/v3/content_analysis/overview/)). 10 calls a day with 100 rows is about $8/month; test coverage on a sample first. Both need a DataForSEO account.
- **Hacker News (Algolia, free):** `search_by_date?query=x402&tags=story` gave `nbHits` 1,429 all time; the newest three stories had 5, 2 and 2 points (2026-10-09, 10-08, 10-05). No rate-limit headers came back ([query](https://hn.algolia.com/api/v1/search_by_date?query=x402&tags=story&hitsPerPage=20)).
- **Blogs and RSS:** project RSS/Atom through the existing `parseFeed`. Google News RSS, Bing News RSS and Mirror/Substack feeds are untested; Google Alerts' help page mentions email only ([help](https://support.google.com/websearch/answer/4815696)).
- **Reddit (low priority):** `reddit.com/search.rss?q=x402&sort=new` returned 200 from a desktop machine. Search summaries say the Data API allows 100 queries a minute per OAuth client for non-commercial use and needs approval ([socialcrawl.dev](https://www.socialcrawl.dev/blog/reddit-api-key-limits-alternatives-2026)).

### Discord, Telegram, Farcaster
- **Discord:** the official follow endpoint is `POST /channels/{channel.id}/followers` with `webhook_channel_id`; it needs `MANAGE_WEBHOOKS` in the target channel and an announcement channel as source ([docs](https://docs.discord.com/developers/resources/channel)). Researcher: follow chosen projects' announcement channels into your own server and read that channel with your own bot token, or as a human. Never automate a user account or read servers where the bot was not added. Outbound limits: 10 embeds per message, 6,000 characters across all embeds, 4,096-character descriptions, 2,000-character content ([message docs](https://docs.discord.com/developers/resources/message)).
- **Telegram (low priority):** `t.me/s/<channel>` returned 200 with 20 messages from a desktop machine. Telegram's API terms forbid using Telegram data to train, fine-tune or otherwise "develop or deploy" AI/ML models (clause 1.5) ([terms](https://core.telegram.org/api/terms)). Use it as a human-read feed only in v1.
- **Farcaster casts via Neynar:** Free plan 10M credits/month; cast search 120 requests/minute on Free; webhook events charged per event (`cast.created` 15 credits, `user.updated` 10) ([rate limits](https://docs.neynar.com/reference/what-are-the-rate-limits-on-neynar-apis), [credits](https://docs.neynar.com/reference/compute-units)). Add after the identity pass shows how many builders are on Farcaster.

---

## 5. Digest design: contents, ranking and automatic flags

**Takeaway.** Rank events by type and entity importance: releases, maintainer and affiliation changes, usage swings and token launches above routine posts. Collapse bursts. Add a stall watch built from commit decay, release cadence, contributor concentration and Bazaar usage. Trend-hopping shows up as keyword drift in bios, taglines and repo descriptions, with falling commits and new token mentions. Scoring is deterministic in the Worker; the routine adds judgement on only the top items.

### Layout (researcher's design)
One Discord message of about 2,000-5,500 characters (up to 10 embeds; limits in section 4), with the rest linked from a dashboard. Parts, in order: headline movers (3-5 lines); shipped (releases and notable commits per tracked project, one line per release train); people moves (bio, affiliation, handle or display-name changes for core people, org membership changes, new repos by tracked people, likely departures); traction (Bazaar 30-day calls and payers, npm/PyPI weekly change, star velocity); new entrants (rising Bazaar payers, or new repos and packages past a threshold such as 50 stars in 7 days, or authored by a tracked person); narrative and token flags; stall watch (up to five projects, with the metric); source health (failed or stale collectors, from the `events` table).

### Ranking (deterministic, tunable; example values)
`score = type_weight x entity_weight x novelty x recency`. Entity weight: 3 core projects and people, 2 tracked, 1 candidates. Type weights: major or breaking release 10; multi-package release train 6 (one event); minor or patch release 4; maintainer added or removed 9; repo archived, transferred, renamed or made private 9; core person affiliation, bio or handle change 9; linked token or contract launch 9; Bazaar 30-day payers down 30% or up 50% week on week 6; npm weekly downloads change over 40% 5; new repo by a tracked person 6; launch-verb post with a link 4; routine post 1; star 0.5.

Collapse repeats by (entity, day, type). Cap each project at three lines. Demote routine noise (hiring, careers, policy, webinar at -3). Send Tier 1 items as immediate Discord alerts from rules alone, with no LLM. The routine reads the top 40 or so events and the flags, searches the web only where a flag needs context, and writes the digest in plain, short sentences.

### Automatic flags (all computable from stored snapshots)
- **Commit decay:** mean weekly commits over the last 4 weeks below 40% of the prior 12-week mean for two consecutive weeks, or no commit to the default branch in 21 days.
- **Release stall:** time since the last release above three times the median gap of the previous six.
- **Contributor concentration and loss:** Contributor Absence Factor of 1, or the top two contributors' last-4-week commits both zero. CHAOSS defines the factor as the smallest number of contributors who account for half of all contributions ([CHAOSS](https://chaoss.community/kb/metric-contributor-absence-factor/)).
- **Team departure:** affiliate badge removed, bio no longer naming the project, display name or handle changed, public org membership removed, or a core contributor silent for 30 days after a bio change. This prompts the routine to look; it is not a conclusion.
- **Rebrand:** repo `full_name` changes while the numeric ID stays; npm deprecation or a new package name; display name, handle or homepage domain change.
- **Usage fade:** `lastCalledAt` older than 7 days for a service with steady calls, or three weekly declines in unique payers or npm downloads.
- **Trend-hopping:** a managed lexicon of narrative words (agent, memecoin, launchpad, RWA, prediction market) diffed against stored bios, taglines and repo descriptions. Flag two or more new terms within 14 days, especially with commit decay or a first token mention. Also flag stars rising with no commits.
- **New token:** a contract-address pattern or a `$TICKER` near "CA" in post text, or a contract deployed by a wallet linked to the project.

Each flag stores evidence JSON, severity and first-seen time, and clears when the metric recovers.

### Cheap bulk tagging inside the cap
`@cf/cloudflare/clef-flash` ($0.038 per million input tokens, 3,455 neurons per million) could label each new post (release, hiring or departure, partnership, token, routine). 600 posts a day at about 200 tokens each is about 120,000 tokens, roughly 400 neurons against 10,000 free per day. Keep a D1 counter and stop at a daily cap.

---

## 6. Recommended stack, data flow, monthly cost and open decisions

**Takeaway.** Run the watch inside one Cloudflare Worker. Free collectors and a hybrid X layer feed D1. Deterministic scoring ranks events. A daily Claude Code routine writes the digest and the Worker posts it to Discord. Expect about $35 a month (plausible range $30-60; about $5 lean; about $180-360 if everything runs on official and paid APIs), plus key and scope decisions for whoever runs it.

### Platform limits
- Workers Paid: 10,000 subrequests per invocation, 250 Cron Triggers per account, 30 s CPU per cron run under an hourly interval (15 min at hourly or longer), 15-minute wall time for Durable Object alarms. `wrangler.jsonc` can set a 120-second CPU limit ([limits](https://developers.cloudflare.com/workers/platform/limits/), wrangler.jsonc).
- Workers AI: 10,000 Neurons a day free (reset 00:00 UTC), then $0.011 per 1,000 Neurons. `@cf/cloudflare/clef-flash` $0.038 per million input tokens (3,455 neurons); `@cf/cloudflare/clef` $0.24 (21,818) ([pricing](https://developers.cloudflare.com/workers-ai/platform/pricing/)).

### Recommended stack (researcher's recommendation; fallback in brackets)
- **Orchestration:** one Cloudflare Worker, with `watch.*` jobs in a Durable Object queue [or a separate Worker].
- **Repos, packages, people activity:** GitHub Atom plus REST (read-only token, ETag) and stats endpoints; npm and PyPI counts [Events API; BigQuery].
- **Usage:** CDP Bazaar crawl (free); x402scan reads at $0.01 if a wallet is funded [public Base RPC spot checks; Etherscan Lite or Blockscout Builder, $49].
- **Identity:** GitHub field, Neynar, ENS, team pages, DataForSEO `site:x.com`, X batch verify; scored match with a review queue [manual review].
- **X posts and profiles:** core 50 on official XAA; long tail on SocialData query monitors or twitterapi.io time-filtered search; profile snapshots on twitterapi.io batch [official API for all; `x_search` ad hoc only].
- **News and mentions:** HN Algolia; project RSS/Atom; DataForSEO Google News (Standard queue); Content Analysis after a sample test [Google News or Bing News RSS, untested].
- **Score, digest, delivery:** deterministic rules and z-scores in the Worker, with optional Clef-flash tagging under a neuron cap; a scheduled Claude Code routine [or a local scheduled task]; Discord webhooks to `#x402-watch` and optional `#x402-alerts` [dashboard page].

### Data flow
```
COLLECT  Worker, daily trigger (~06:15 UTC), spread across the DO queue:
         watch.github (Atom + REST/ETag), watch.registry (npm, PyPI), watch.bazaar (33 x 1,000),
         watch.feeds (HN, blog RSS, DataForSEO news), watch.x (third-party search, profile batch), optional x402scan
         -> normalise -> dedupe key -> D1.   X Activity API -> POST /x/webhook (CRC + HMAC verify) -> same normaliser
STORE    D1 watch_* tables (entities, handles, events, metrics daily, flags, digests); `events` table for source health
SCORE    Worker, ~06:45 UTC: type x entity x novelty x recency; z-scores; flags; optional Clef-flash tags;
         Tier-1 hits -> immediate Discord alert (no LLM)
DIGEST   Claude Code routine, ~07:30 UTC: GET /api/watch/context (top ~40 events, movers, flags, source health;
         Bearer) -> judgement + web search on flagged items only -> POST /api/watch/digest
DELIVER  Worker stores the digest, posts to #x402-watch, de-duplicates by content hash;
         Sunday "health review" routine for the stall list
```

### Monthly cost estimate (USD; 30-day months; unit prices from sections 2-4)
Assumptions: 300 people and about 50 projects. 600 X posts a day (base case, section 2). 50 DataForSEO news queries and 10 Content Analysis calls (100 rows) a day in the recommended column. 20 x402scan reads a day. D1, Worker use and Workers AI stay inside free allowances. The Claude routine runs on a Claude Code subscription (no API bill, but it uses subscription capacity).

| Item | Lean | Recommended | Official and paid everything |
|---|---|---|---|
| X post reads | $3.60 (SocialData, all 300) | $19 (50 core on XAA $15 + long tail ~$4) | $90 (600/day); $270 at 1,800/day |
| X profile snapshots | $0.10 (twitterapi.io batch) | $0.10 | $13 (official `users/by`, weekly) |
| DataForSEO news + mentions | $0.90 | $9 | $9-20 |
| x402scan reads | $0 | $6 | $18 (60/day) |
| Base explorer | $0 | $0 | $49 |
| Dune | $0 | $0 | $75-$399 |
| Free sources (GitHub, npm, PyPI, Bazaar, HN, RSS, Neynar free plan, Workers AI) | $0 | $0 | $0-1 (Neynar Scale $249 only if the free plan is not enough) |
| Cloudflare incremental (D1 rows, DO time) | $0 | $1 | $2 |
| **Total per month** | **about $5** | **about $35 (range $30-60)** | **about $180 (base volume) to $360+ (high volume, without Dune)** |

One-off: identity pass $5-25 (section 3). The first-card credit and first auto-recharge match (section 2) can offset initial X spend. A hard monthly spend limit can be set in the X Developer Console.

**Phasing (suggested):** (0) point any x402 release feeds at `x402-foundation/x402` and add its commits feed. (1) GitHub, npm/PyPI and Bazaar collectors, D1 tables, digest routine and Discord channel, all free. (2) Identity table and X layer. (3) Scoring and flags tuned on two to four weeks of data. (4) Optional sources: x402scan, DataForSEO news, Neynar casts, Discord follows.

### Open decisions (default in brackets)
1. **X risk appetite:** official-only, third-party for the long tail [default], or third-party for all. Default also: a role-based watchlist (project accounts plus publicly identified team members' professional accounts), no sensitive-attribute inference, links not verbatim text in Discord.
2. **Watchlist and stored data:** named individuals or project-level signals only; retention and deletion; whether the GitHub-to-X mapping is stored. Check UK GDPR for named-person data.
3. **X accounts and money:** create the developer account, buy credits, set a monthly spend cap, set the bearer token, webhook and client secrets (`wrangler secret put`). Accept or decline SocialData and twitterapi.io, and pick the primary.
4. **Secrets to set:** GitHub read-only token; a bearer token for the digest routine; a Discord webhook for the watch channel; optional Neynar key; DataForSEO login if the Worker calls it; a Base USDC key if x402scan reads are paid automatically.
5. **Project universe rule:** the Bazaar has 32,162 services and GitHub 3,686 `x402` repos. Choose the inclusion bar (Bazaar 30-day unique payers, GitHub stars, or membership in the other researchers' project list) and core/tracked/candidate tiers.
6. **Discord:** one channel or two; whether to follow projects' announcement channels into your own server; skip Telegram and Reddit in v1 [recommended].
7. **DataForSEO:** confirm the `cost` of a `site:` query before the 300-name pass; decide on Content Analysis after a sample test.
8. **Workers AI tagging:** yes or no; whether to try Clef-flash (never called from the account).
9. **Schedule:** 07:30 UTC digest after a 06:15 collector run (the existing ideas routine is 07:00), plus a Sunday health review.
10. **Radar quick fix now:** edit `sources.json` and redeploy, or move the feed list into D1.

---

## 7. Conflicts and gaps

### Conflicts and mismatches
1. **X read cap:** 3M a month on X's pricing page; some third-party guides say 2M. Use 3M.
2. **X plan and XAA status:** "pay-per-use is the only path for new sign-ups" and "free tier closed 2026-02-06" are unfetched third-party summaries; X's page lists no legacy tiers. A snippet calls XAA an "open beta"; the fetched page does not. The 2026-06-04 `post.create` date is third-party.
3. **Neynar plans:** docs show Free (10M credits/month) and Scale $249 (60M credits). A cached page shows free 200K, Starter $9, Growth $49, Scale $249.
4. **Dune and Etherscan:** the newer Dune page (Free has no API) conflicts with older summaries (2,500 free credits a month). Etherscan's plans page is ambiguous on Base; press says free Base access was suspended.
5. **Policy against purpose:** X's guidelines prohibit monitoring users without consent, off-X matching without opt-in, and scraping. The plan monitors named people, matches identities and (in the hybrid) uses vendors that scrape. X's Developer Agreement was not read.
6. **Run times (digest check):** section 1 of the notes mentions a 06:45 collector run; section 6 has collect ~06:15, score ~06:45, routine 07:30. The existing daily cron is `30 6 * * *` (06:30 UTC), so a 06:15 collector needs a new cron or shifted times.
7. **Cost totals (digest check):** only the $360+ high total is labelled "without Dune", but the base column's rows also sum to about $181 without it. Dune would add $75-$399.
8. **Undated prices:** X, DataForSEO and xAI pages carry no effective date (xAI cites 2026-09-21). twitterapi.io's list-call price says "effective October 1st" with no year.

### Gaps
- **From a Worker:** all probes ran from a desktop machine. GeckoTerminal answered 429 to 56 of 56 calls from Cloudflare's shared IPs in a Worker preview, so GitHub feeds, Reddit, Telegram, non-follow Discord and Etherscan/Blockscout-for-Base may behave differently from a Worker.
- **X:** no independent uptime data for SocialData or twitterapi.io. Unverified: the "owned reads" definition, whether `post.create` includes replies, XAA subscription-creation cost, per-app webhook limits, `exclude` on list posts, and pay-per-use per-app rate limits. The 20-handles-per-query ceiling and the posting rates are assumptions. Apify figures are second-hand.
- **Identity:** GitHub `twitter_username` accuracy is unmeasured (the 23 handles were not checked against X, to avoid compiling cross-source profiles of individuals). Farcaster, ENS and Google SERP coverage are unmeasured. DataForSEO's "multiply by 5" wording is ambiguous for quoted phrases; check the `cost` field in the first response.
- **Signals:** unread or unverified: HN Algolia's rate limit, Discord's developer policy, Reddit and Telegram website terms, the DataForSEO Google News path, Blockscout's public limits, CDP Onchain Data pricing, Dune per-execution credits, the Bazaar `builder-code` meaning. Google News RSS, Bing News RSS and Mirror/Substack feeds are untested.
- **Digest and cost:** weights and thresholds are proposals, unvalidated on x402 data (run the collectors two to four weeks, then tune). Bio-based departure detection misses quiet exits and false-positives on cosmetic edits. No benchmark exists for commit-decay thresholds in small crypto projects. Clef models have not been tested for this. The design is unprototyped, so D1 volume, DO time per run and Bazaar crawl duration are estimates.
