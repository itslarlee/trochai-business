# B2B Lead-Sourcing Tools for Costa Rica Real Estate (April 2026)

## Context

Targeting ~500 CR real estate agencies, broker-owner decision makers, solo founder, $0–200/mo realistic, up to $500/mo if justified.

**Key insight before the table**: most global B2B databases (Apollo, ZoomInfo, Cognism) are weak in LATAM. The CCCBR official directory only lists 320 active members. Google Maps + Instagram scraping is required to cover the long tail of agencies that aren't in any B2B DB.

## Comparison Table

| Tool | 2026 Cost | CR Coverage | Pros | Cons |
|---|---|---|---|---|
| **Apollo.io Free** | $0 (10 export credits/mo) | 2/5 | Free, Chrome extension, decent sampling | LATAM explicitly weakest region; outdated titles/invalid phones in CR |
| **Apollo.io Basic** | $49/user/mo annual | 2/5 | 1k export credits, sequences, LinkedIn integration | Same LATAM weakness; credit burn ~2–3x advertised |
| **LinkedIn Sales Navigator Core** | $79.99/mo annual ($959.88/yr); 30-day trial; 75% off 4 mo via Microsoft for Startups | 4/5 | Industry=Real Estate + Geography=CR filter works; decision-maker titles reliable; 50 InMails/mo | Scraping directly is ToS-risky; no emails/phones; ~$1,200/yr is 50% of $200/mo budget |
| **Apify Google Maps Scraper** | $4 per 1,000 places + $2 per 1,000 for emails/socials; $5 free monthly credit | 5/5 | Unmatched CR coverage — every agency with physical office is on Maps | Emails often from bios only; needs dedupe; franchise duplicates |
| **Apify Instagram Scraper** | $5 free credit/mo; ~$2–5 per 1,000 profiles | 4/5 | CR real estate is very IG-active; bios frequently contain WhatsApp + email | Meta sued Bright Data (Meta lost 2024); ToS gray area |
| **Clay Free** | $0 (100 Data Credits, 500 Actions/mo, 100 rows max) | 3/5 | Waterfall enrichment across 75+ providers; Claygent AI; unlimited seats | 100 rows ≠ 500 accounts; no phone enrichment on free |
| **Clay Launch** | $185/mo monthly, $167/mo annual | 4/5 | 2,500 Data Credits, 15k Actions, 50k rows, phone enrichment | Eats nearly entire budget; credit math gets expensive |
| **Outscraper** | Pay-as-you-go; 500 free → $3/1k for 99.5k → $1/1k after 100k | 5/5 | No monthly fee; enrichment add-ons; simpler than Apify for non-devs | Less flexibility than Apify |
| **Bright Data Google Maps** | Starts ~$500/mo | 5/5 (data) / 1/5 (cost) | Enterprise-grade proxies | Wildly overkill and over-budget |
| **ZoomInfo** | ~$15k–30k/yr minimum | 1/5 | N/A for you | US-centric; no CR real estate coverage; over budget |
| **Lusha** | Pro $29/user/mo, Premium $51/user/mo | 2/5 | Some advertised LATAM; Chrome extension | "Uneven coverage" in LATAM; shallow |
| **Instantly.ai** | Growth $37/mo, Hypergrowth $97/mo | 3/5 | SuperSearch 450M+ leads DB; email warmup on 4.2M+ network; AI Reply Agent | Lead DB weaker in LATAM; best as sending tool |
| **Smartlead** | From $39/mo flat | N/A (sending only) | Flat-fee scaling, strong deliverability | Not a data provider |
| **Lindy AI / Relevance AI / Bardeen** | Lindy Plus $49.99/mo | 3/5 | AI agents that research + enrich + message; no-code | Still early; no proprietary CR data |
| **11x.ai Alice / Artisan** | ~$5,000/mo | N/A | Enterprise autonomous SDR | Out of budget |
| **CCCBR directorio-de-asociados** | Free | 5/5 | 320 accredited CR real estate professionals by province; most authoritative; brokers with CCCBR badge are paying professionals | Not the full 500; HTML scrape required |
| **MLS Costa Rica (re.cr / mls.re.cr)** | Free | 4/5 | Agency directory with contact info; Propertyshelf-vetted | Vetted agencies only |

## Key Findings

**CCCBR directory is the single highest-value asset.** Official chamber (founded 1974), member of CILA and FECEPAC, 320 accredited broker-owners publicly searchable by province at [camara.cr/directorio-de-asociados/](https://www.camara.cr/directorio-de-asociados/). These are the most qualified buyers because (a) they pay professional dues — willingness to pay for software is demonstrated, (b) they're the formal sector (matches the "no punching down on informal sector" feedback), (c) each profile has name, agency, specialty.

**Google Maps covers the other ~180 agencies beyond CCCBR.** Apify or Outscraper on query "real estate agency" + geo=Costa Rica returns all of them with websites + phones + categories. Outscraper is simpler for non-devs; ~$3 per 1,000 records means covering all of CR costs ~$2–3 one-time.

**Instagram is disproportionately important in CR.** Real estate runs more on Instagram + WhatsApp than LinkedIn or standalone websites. Bios routinely contain WhatsApp number + email. Apify Instagram Profile Scraper extracts these at ~$2–5 per 1,000 profiles. Legal risk: Meta has sued scrapers (Bright Data case, Meta lost) and continues enforcement. Don't make it a load-bearing long-term dependency.

**Apollo.io is not worth paying for here.** Multiple 2026 reviews explicitly flag LATAM + APAC as weakest regions with stale titles and invalid phones. Use free tier only as spot-check enrichment for named agencies.

**LinkedIn Sales Navigator IS worth it.** Your buyer is an agency principal/broker-owner — a job title reliably populated on LinkedIn even in small CR markets. Industry=Real Estate + Location=Costa Rica + Seniority=Owner/Director returns ~800–1,500 results. 30-day free trial lets you export your complete list before paying. Microsoft for Startups gives 75% off 4 months → ~$20/mo effective.

**Clay overkill at your stage.** $185/mo burns entire budget on a tool optimized for 10k-lead workflows. For 500 accounts, free Clay doesn't fit and paid Clay doesn't pay back. Revisit post-PMF.

## Recommended Stack (<$200/mo, 500 CR Agencies)

**Month 1 — Sourcing (one-time spend ~$30):**

1. **CCCBR directory scrape** (free). Manual or Python/Playwright → 320 broker profiles with agency name.
2. **Outscraper Google Maps** (~$3–5 one-time). Query "real estate agency" + each CR province → 400–600 Maps listings with websites/phones. Dedupe against CCCBR.
3. **Apify Instagram Profile Scraper** (~$5–10 one-time). Feed IG handles found on websites + Maps to pull WhatsApp/email from bios.
4. **LinkedIn Sales Navigator Core — 30-day free trial** ($0). Day 1: Industry=Real Estate + Geography=CR + Seniority=Owner/Director. Export list via Evaboot or manual. Cancel before day 30 or keep if ROI clear.

**Month 1 result**: single deduplicated CSV of ~500 CR agencies with agency name, website, phone, WhatsApp, IG handle, email, and broker-owner name for the CCCBR/LinkedIn subset.

**Month 2+ — Ongoing ($130–150/mo):**

5. **LinkedIn Sales Navigator Core** — $80/mo annual ($960/yr). Apply for Microsoft for Startups 75% off first. Continuous account monitoring + broker-owner lookup.
6. **Instantly.ai Growth** — $37/mo. Sending infrastructure + warmup + 450M-lead backup. Pair with custom CSV.
7. **Apify pay-as-you-go** (~$10–20/mo). Quarterly Google Maps refresh + ad-hoc Instagram pulls.
8. **Clay Free + Lindy Plus free tier** ($0). AI research/personalization on top 50 accounts/week.

**Total recurring: ~$130–150/mo.** Leaves headroom under $200 ceiling.

**Explicitly skip:** ZoomInfo, Cognism, Bright Data, Phantombuster, 11x.ai, Clay Launch. Over-budget or under-relevant.

## Sources

- [CCCBR Directorio de Asociados](https://www.camara.cr/directorio-de-asociados/)
- [Apollo.io Pricing 2026 – Saleshandy](https://www.saleshandy.com/blog/apolloio-pricing/)
- [LinkedIn Sales Navigator Pricing 2026 – Postiv AI](https://postiv.ai/blog/linkedin-sales-navigator-cost)
- [Apify Google Maps Scraper](https://apify.com/compass/crawler-google-places)
- [Apify Instagram Profile Scraper with email/phone](https://apify.com/logical_scrapers/instagram-profile-scraper)
- [Meta loses Bright Data scraping lawsuit](https://www.socialmediatoday.com/news/meta-loses-data-scraping-highlighting-need-clarified-regulation/705814/)
- [Clay.com Pricing](https://www.clay.com/pricing)
- [Outscraper Pricing](https://outscraper.com/pricing/)
- [Instantly.ai Pricing](https://coldemailkit.com/tools/instantly)
- [MLS Costa Rica](https://www.re.cr/en)
