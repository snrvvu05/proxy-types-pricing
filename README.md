# proxies for web scraping: pick the right proxy type, read the real 9Proxy prices, and wire it into your pipeline

One address, four thousand requests, forty minutes. That is usually all it takes before a target site stops serving you real pages and starts handing back 429s, a Cloudflare interstitial, or a CAPTCHA served with a perfectly cheerful HTTP 200. Your headers were fine. Your parser was fine. The problem is that your requests all came from the same place.

That single fact drives almost every real decision in this space: which proxy type you buy, how you rotate it, and how you measure whether it was cheap or expensive. Below is what actually matters when you are shopping for proxies for web scraping, plus the current 9Proxy plan list, what each model is genuinely good at, and where the limits are.

## Your scraper isn't blocked by its headers, it's blocked by its exit IP

Anti-bot systems score the address before they bother scoring your behaviour. Cloud IP ranges are known ranges, so a datacenter IP from a well-known hosting block gets extra scrutiny from the first request. Residential addresses carry the reputation of a normal household connection, which is why they survive checks that kill datacenter traffic.

That scoring is measurable. Independent testing has used IPQualityScore, a fraud-risk metric, to grade pool hygiene: anywhere an IP scores above 90, the odds of being blocked climb sharply. CNET's 2026 proxy roundup made the same point from the other direction, noting that even the best commercial pools still contain a majority of addresses above that threshold, and that the useful signal is the mix inside the pool rather than the headline IP count.

There is a second reality check that most provider pages skip. AIMultiple has been running scheduled request cycles against protected sites across residential, datacenter and unblocker products, and its published results put residential and datacenter proxies at roughly **55% to 75% success on a given day** on sites that actively fight automation, not the 95% to 99% you see in marketing. Their explanation is worth internalising: a CAPTCHA page returned with HTTP 200 counts as a failure in their tests, while plenty of vendor dashboards count it as a success. Those are two different numbers wearing the same name.

So budget on successful responses, not on requests sent. That one change reorders almost every comparison you will read this year.

## Which proxy type your targets actually need

Four families, four different jobs, and you usually only need the cheap one.

Datacenter proxies are fast and cheap and get identified quickly. On light or moderately protected targets they are enough, and AIMultiple's data supports trying them first: even on Google, Instagram, TikTok, Walmart and X, datacenter IPs returned real pages more than half the time on most days.

Residential proxies are the default when a target blocks cloud ranges outright, or when you need the page a household in that city actually sees. Localised pricing, local search results, ad placements and stock availability only appear if the exit IP is in the right market.

ISP or static residential proxies sit between the two: a residential address that stays put, which is what you want when a target rewards a stable identity across a login-and-paginate flow.

Mobile proxies carry carrier-grade NAT trust and cost the most per gigabyte. Worth it for mobile-facing targets, wasteful as a default.

The practical rule: send 100 requests through a cheap datacenter proxy first. If more than about 60% come back as real pages, you do not need to spend more. If they do not, move up.

One thing to know before you shop: 9Proxy sells residential proxies only. There is no datacenter line and no mobile line. If your project genuinely needs a datacenter tier for the easy 80% of your targets, that lives somewhere else.

## Cost per successful page beats cost per gigabyte

The formula that settles arguments:


cost per 1,000 successful pages = (spend ÷ successful responses) × 1,000


Run it on 9Proxy's GB pricing. The 100 GB pack lists at $150, which is $1.50 per GB. Say your average fetch costs 2 MB at the proxy. That is roughly 51,000 fetches per pack. At a 70% success rate you keep about 35,800 real pages, which lands near **$4.20 per 1,000 successful pages**. If your pages are heavier, the same $150 buys fewer of them. If your success rate is better, it buys more.

Now the by-IP model, which bills the other way round. The 100-IP pack is $24 and bandwidth on those IPs is unlimited, so page weight stops mattering entirely. What matters instead is how many requests each address survives before it gets rate-limited or killed. If each of your 100 IPs lasts 5,000 requests and 70% succeed, that is about 350,000 successful pages from a $24 pack. That is arithmetic, not a promise, and your number will depend on your targets and how politely you crawl. But it shows why heavy, rendering-heavy pages and the per-IP model tend to end up in the same sentence.

The crossover is not magic. Light requests at high rotation favour pay-per-GB. Fat responses through fewer exits favour pay-per-IP. Pick the model that matches your traffic shape and the price argument mostly resolves itself.

## Two billing models, two very different workflows

9Proxy runs a residential network of 20M+ IPs across 90+ countries, with HTTP/HTTPS and SOCKS5 support and targeting that goes down to country, state, city, ZIP and ISP level. On top of that network sit two products that behave almost nothing alike.

**Residential by IPs** hands you a fixed number of addresses and never meters your traffic. Unused IPs do not expire, which is unusual and useful if your projects arrive in bursts. Individual IPs last somewhere between a few hours and about a day, and there is no natural rotation, so you drive rotation yourself through a rotating port at whatever interval you set. The setup runs through the 9Proxy desktop app, which forwards traffic locally at the operating-system layer. That is genuinely handy for tools that have no proxy field of their own, and mildly annoying if your fleet is headless Linux servers.

**Residential by GB** meters traffic and does not care how many endpoints you create. You can generate as many as you like from the dashboard, choose rotating or sticky sessions, and authenticate with username/password or by whitelisting your server's IP. Sticky sessions hold an address for the window you set, which is what multi-step flows need; rotating hands every request a fresh IP, which is what broad crawling needs. Purchased bandwidth is valid for 180 days on standard plans, and unlimited on Enterprise. No app required.

If your scrapers live in the cloud and you would rather not install software, the GB model is the one. If you are running fat, rendering-heavy requests or account-bound work where a session has to survive, the by-IP model usually costs less.

**A pricing note worth flagging.** On June 1, 2026, 9Proxy raised prices on the by-IP and bundle packages for the first time since launch, leaving GB pricing untouched. Anything you read quoting $20 for 100 IPs is describing the old rate. The vendor published the change in advance so existing customers could lock in earlier rates; that window has closed.

Also ignore the "$0.015 per IP" and "$0.68 per GB" headlines you see in ads and forum signatures. Those are the far end of the volume ladder. Realistic entry pricing is the table below.

## Every current 9Proxy plan

| Plan | What you get | Price | Effective rate | Billing / validity | Buy |
| --- | --- | --- | --- | --- | --- |
| 100 IPs | Unlimited bandwidth per IP, IPs never expire, app-based setup | $24 | $0.24 per IP | One-off, no subscription | [Get the 100-IP pack](https://bit.ly/9-Proxy) |
| 500 IPs | Same as above | $72 | ~$0.144 per IP | One-off | [Get the 500-IP pack](https://bit.ly/9-Proxy) |
| 1,000 IPs + 500 bonus | 1,500 addresses total, unlimited bandwidth | $126 | ~$0.084 per IP | One-off | [Get the 1,500-IP pack](https://bit.ly/9-Proxy) |
| 100,000 IPs | Bulk allocation for large operations | $2,300 | ~$0.023 per IP | One-off | [Check bulk IP pricing](https://bit.ly/9-Proxy) |
| 500,000 IPs | Largest published IP tier | $8,625 | ~$0.017 per IP | One-off | [Check bulk IP pricing](https://bit.ly/9-Proxy) |
| 5 GB | Unlimited endpoints, rotating or sticky, dashboard only | $15 | $3.00 per GB | 180-day validity | [Get the 5 GB pack](https://bit.ly/9-Proxy) |
| 50 GB + 5 GB bonus | Same, 55 GB total | $105 | ~$2.10 per GB | 180-day validity | [Get the 55 GB pack](https://bit.ly/9-Proxy) |
| 100 GB | Same | $150 | $1.50 per GB | 180-day validity | [Get the 100 GB pack](https://bit.ly/9-Proxy) |
| 200 GB | Same | $200 | $1.00 per GB | 180-day validity | [Get the 200 GB pack](https://bit.ly/9-Proxy) |
| 1,000 GB | Same | $800 | $0.80 per GB | 180-day validity | [Get the 1,000 GB pack](https://bit.ly/9-Proxy) |
| 2,000 GB | Same | $1,500 | $0.75 per GB | 180-day validity | [Get the 2,000 GB pack](https://bit.ly/9-Proxy) |
| 10,000 GB tier | Rate drops to the advertised floor | Quoted at checkout | $0.68 per GB | 180-day validity | [Request GB volume pricing](https://bit.ly/9-Proxy) |
| Bundle (IPs + GB) | Combine an IP allocation with a bandwidth pool | From roughly $25 | Depends on the mix | Dashboard shows the exact figure | [Check bundle pricing](https://bit.ly/9-Proxy) |
| Enterprise | Unlimited data validity, team mode (owner + up to 5 members), per-member traffic controls, activity logs, VIP support | Custom quote | Custom | Custom | [Ask about Enterprise](https://bit.ly/9-Proxy) |

Two caveats on that table. The 10,000 GB rate is the published floor for the GB ladder; the total is a quote rather than a listed cart price. And bundle and Enterprise pricing moves with allocation, so the number that matters is the one your dashboard shows before you pay. Prices in this market change without much notice, so verify before checking out.

For reference, published 2026 comparisons put entry residential pricing at Bright Data and Oxylabs in the $4 to $8 per GB range, with some premium tiers quoted higher. That is the gap 9Proxy is selling into, and it is a real one at the entry tiers in the table above.

## Features that actually change your scraping workflow

Most of the feature list is noise. A handful of items do real work.

The **Proxy Generator** in the dashboard is the core of the GB workflow. Pick your authentication method, choose country, state, city, ZIP or ISP, set sticky or rotating, then export endpoints as `.txt` or `.csv` with ready-made code samples for a few languages. Exporting a thousand ports instead of hand-building them saves an afternoon.

**Session control** is the part people get wrong. Per-request rotation maximises spread, which is right for discovery crawling. Sticky sessions hold one address so a login, a filter change and a paginated walk all look like one user. If you are driving an AI agent that opens a search page, a detail page and a checkout in sequence, sticky is not a nice-to-have, it is the difference between a coherent session and a network-layer story that jumps from Tokyo to Paris between clicks.

**Geo targeting to ISP level** matters more than people expect. Matching an exit IP to the right city while your browser timezone and coordinates say something else is its own detection signal. Being able to pin an address to a specific ISP in a specific metro is what lets you build a consistent profile.

**Dead-IP handling** keeps a pipeline from stalling. 9Proxy advertises automatic replacement of offline IPs rather than leaving your retry logic to discover timeouts on its own, which matters most on the by-IP model where you hold addresses over hours.

**Compatibility** is broad enough that you probably will not fight it: SOCKS5 and HTTP work with AdsPower, Dolphin Anty, BitBrowser, proxychains and plain Python scripts. Sub-users let you split traffic across scripts or teammates, a public API covers programmatic session control and usage stats, Proxy2Web gives you a zero-install browser check with user:pass, and ProxyHub handles mobile devices if that is part of your setup. Support runs 24/7 over Telegram, email and tickets.

## Getting it into your pipeline

Two paths, depending on which model you bought.

On the GB model you generate endpoints in the dashboard and pass credentials straight to your client:

python
import requests

proxy = "http://USERNAME:PASSWORD@host:port"   # exported from your dashboard
proxies = {"http": proxy, "https": proxy}

resp = requests.get("https://example.com/product/123", proxies=proxies, timeout=30)


For sticky sessions, hold the same endpoint across a flow instead of regenerating it. For breadth, regenerate per request or per retry.

On the by-IP model you install the desktop app, forward the addresses locally, and point your tool at `127.0.0.1` ports. Anything that cannot take proxy settings by itself still gets routed, which is the whole point of that design.

Whichever you use, write the retry policy before you scale. Retry 403s, 429s and pages that render a challenge instead of product data, rotate on each retry, and cap attempts at two or three. Log success rate per target domain, because a pool that performs beautifully on one site can be mediocre on another, and the only number that tells you is your own.

## Limits worth knowing before you pay

Residential only. No datacenter, no mobile, no bundled unblocker API. If your targets need a rendering pipeline and fingerprint management on top of the proxy, that is still your problem to solve; a clean IP does not fix a bad TLS fingerprint.

The by-IP model needs the desktop app. That is fine on Windows workstations and awkward on headless servers, which is where most scraping actually runs. It is a real argument for the GB model in cloud deployments even when the per-request maths favours the IP model.

Bandwidth expires. IP allocations do not, but 180 days is the clock on standard GB packs, and it only goes away on Enterprise. If your data collection is seasonal, size the pack to the season.

Pool size is a genuine trade-off. 20M+ IPs across 90+ countries is smaller than the 100M-plus pools the premium providers advertise and covers a shorter country list. For US, Southeast Asia and Latin America work, coverage is described as strong. If you need long-tail geography or granular ASN filtering on every request, test that specific country before you commit.

There is no permanent free tier. Free trial access has historically been promotional, granted by support when a campaign is running, so do not build a plan around it.

## Test it properly, then decide

The cheapest way to find out whether a provider works on your targets is to buy the smallest unit that fits your test and run a controlled comparison. Five GB costs $15. A hundred IPs costs $24. That is less than an afternoon of engineering time.

Run the same batch on one afternoon, same URLs, same concurrency, same target countries. Count real pages, not HTTP 200s, because challenge pages lie. Sample a few exit IPs through an independent lookup to confirm the geography is where the dashboard says it is. Then divide spend by successful responses and compare that number against whatever you are running now. Whatever survives that test is the right answer, and it will be a better answer than anything a review page can give you.

If you want to start with the model that works from a cloud server with no install, 👉 [open a 9Proxy account and start with a small GB pack](https://bit.ly/9-Proxy). If your traffic is heavy and your sessions are long, the by-IP packs are cheaper per successful page.

## FAQ

**Is 9Proxy cheaper than Bright Data or Oxylabs?** At entry tiers, yes, by a wide margin: $1.50 per GB at 100 GB and $3.00 per GB at 5 GB against roughly $4 to $8 per GB at the premium networks. The cheaper rate buys a smaller pool and a shorter country list. On easy targets that does not matter. On hard ones, test before assuming the discount holds.

**Do I need residential proxies for every scraping job?** No. Try a cheap datacenter tier first and only escalate on the targets that fail. Paying residential rates for pages that a $1 proxy can fetch is the most common way scraping budgets get wasted.

**Per-IP or per-GB?** Heavy responses and long sessions: per-IP, because bandwidth is unmetered. Light requests with high rotation across many endpoints: per-GB, because you are not paying for addresses you barely use.

**What about free proxy lists?** The IPs are flagged, widely shared, slow and short-lived, and routing your traffic through unknown operators is its own risk. Fine for a throwaway test, useless in production.

**Is using proxies for scraping legal?** Proxy use itself is legal in most jurisdictions. What gets people in trouble is what they collect and how they collect it: private or login-gated data, ignoring a site's terms, or personal data handled outside applicable privacy law. Public data, sane request rates, and a conversation with counsel before commercial deployment is the boring correct answer.

## The short version

Proxy choice is a measurement problem disguised as a purchasing decision. Match the proxy type to how hard your targets fight back, match the billing model to your traffic shape, and score providers on cost per successful page instead of cost per gigabyte. On price, 9Proxy sits well below the premium networks, with a smaller pool and a residential-only catalogue as the trade. Buy the smallest pack that lets you run a fair test on your own targets, and let the success rate decide.
