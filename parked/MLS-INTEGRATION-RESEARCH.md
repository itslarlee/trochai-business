# Listing Source Auto-Sync Research

**Purpose**: Evaluate listing sources for Trochai auto-sync. Remove manual catalog entry as an onboarding blocker.
**Scope**: Costa Rica primary, LATAM secondary. Sort by coverage x feasibility.
**Status**: Research only — do not build until ICP validation complete.
**Date**: 2026-04-16

## Executive summary

- **The biggest lever is not "MLS" — it's WordPress.** ~70% of the 21 audited CR agencies run WordPress with Houzez / RealHomes / WPResidence / Real Places. All register Properties as a custom post type; if `show_in_rest=true`, we pull them through stock WP REST API + an Application Password. One generic adapter, four themes.
- **Houzez is the single highest-leverage integration.** Largest share of the WP stack, well-documented REST endpoint, and the free `Houzez Property Feed` plugin (v2.5.43 released 2026-03-24, 1,000+ installs, 40+ source connectors) proves the data contract is stable.
- **Propertyshelf has a real REST API but it is private.** `mls.apiclient` (Propertyshelf's own Python client) confirms a RESTful backend exists, but base URL, auth flow, and endpoint catalog are not public. Access appears gated via CCCBR partnership. Do not build until one paying customer demands it + we secure API credentials.
- **Skip Encuentra24 and EasyBroker for now.** Encuentra24 is a syndication portal, not a catalog source — no public API. EasyBroker has one user (Palm Real Estate) out of 21 and the MLS API is a paid tier.
- **Universal fallback: Schema.org `RealEstateListing` JSON-LD.** Covers the ~20% long tail (Next.js, Drupal, Squarespace, Luxury Presence). Yoast SEO emits JSON-LD on most WP sites; scraping `sitemap.xml` + `application/ld+json` normalizes to Trochai's schema.

## The listing-source landscape in Costa Rica

From the April 2026 audit of 21 CR agencies (memory: `project_cr_real_estate_tech_stack.md`):

| Source | Agencies | Coverage | Integration path |
|---|---|---|---|
| WordPress + Houzez | 5-7 | 25-33% | WP REST API + Houzez Property Feed |
| WordPress + RealHomes | 3-4 | 15-20% | WP REST API + WP All Import add-on |
| WordPress + WPResidence | 2-3 | 10-15% | WP REST API + WP All Import add-on |
| WordPress + Real Places | 1-2 | 5-10% | WP REST API + WP All Import add-on |
| Plone + Propertyshelf (CCCBR MLS) | Propiedades Leiton, KRAIN, +3-5 | 15-25% [unverified] | Partner-gated Propertyshelf REST API |
| HubSpot CMS Hub | Casa Escazu | 5% | HubSpot Properties API |
| EasyBroker | Palm Real Estate | 5% | EasyBroker REST API |
| Propertybase | 2Costa Rica | 5% | WebToProspect / GO API |
| Custom (Next.js, Drupal, Squarespace, Luxury Presence) | 4-5 | ~20% | Scraping / Schema.org JSON-LD |

## Detailed breakdown per source

### WordPress themes (highest coverage)

**Architectural insight**: all four themes below register Properties as a custom post type. With `show_in_rest=true` (default in current Houzez/RealHomes/WPResidence), `/wp-json/wp/v2/property` is live out of the box, auth via WP 5.6+ Application Password (Basic Auth over HTTPS). **One generic "WordPress Property" adapter covers 55-75% of the market** with per-theme field maps.

#### Houzez

- **Description**: Most common WP real-estate theme on ThemeForest; paid theme by favethemes ($69 one-time).
- **Coverage**: Largest single-theme share of the 21 audited agencies.
- **API**: WP REST API + a Houzez-specific `houzez-api/v1/properties` endpoint (filtering limited to featured/sort/pagination — no direct price/beds query; full-sync polling is fine). The free `Houzez Property Feed` plugin by Property Hive is actively maintained (v2.5.43, 2026-03-24) and proves 40+ inbound source formats; the reverse read direction is via standard WP REST.
- **Auth**: Application Password (Basic Auth / HTTPS).
- **Cost**: Free. No API tier.
- **ToS for AI**: No published restriction. Data is the agency's own; they grant us access via their credentials.
- **Data quality**: Structured — price, beds, baths, size, lat/lng, images, status, agent. Clean fit for pgvector embedding.
- **Maintenance**: Low. Standard WP REST contract; Property Feed ecosystem absorbs theme version drift.
- **MVP effort**: 3-5 days for read-sync + optional thin companion plugin that POSTs webhooks on `save_post_property`. 1-2 days if polling-only.

#### RealHomes (Inspiry)

- **Coverage**: 3-4 of 21.
- **API**: Native feed at `?feed/?post_type=property`; WP REST API when `show_in_rest` enabled. Ecosystem leans on WP All Import.
- **Cost**: Free ($59 theme).
- **MVP effort**: 1-2 days reusing the generic WP adapter.

#### WPResidence

- **Coverage**: 2-3 of 21.
- **API**: Has a "WPResidence API" per vendor marketing, but published material is mostly about import *into* WPResidence, not outbound. Falls back to WP REST when `show_in_rest=true`. WP All Import add-on supports scheduled XML/CSV sync.
- **MVP effort**: 1-2 days on the generic adapter.

#### Inspiry Real Places

- **Coverage**: 1-2 of 21.
- **API**: WP REST API + add-on (long tail — only 30+ global installs).
- **MVP effort**: 0.5-1 day after Houzez.

### Propertyshelf (CR-regional MLS)

- **Description**: Runs the official CCCBR MLS (mls.re.cr / mls-costarica.com). CCCBR selected Propertyshelf as the national MLS; members get access bundled. Listings auto-translated to 5 languages, syndicated to realtor.com via Immobel.
- **Coverage**: 3-8 of 21 [unverified — only KRAIN + Propiedades Leiton confirmed on Plone; more agencies likely use mls.re.cr as a data source even with a non-Plone public site].
- **API**: **A REST API exists but is not publicly documented.** Propertyshelf publishes `mls.apiclient` on PyPI/GitHub explicitly as "Python client for the RESTful API of the Propertyshelf MLS." Consumed by `plone.mls.listing` and `ps.plone.mls` (actively maintained, latest release June 2025). Base URL, auth, and endpoint catalog not public. [unverified — partnership inquiry required].
- **Cost**: Developer MLS Package $1,099/year (for builders/developers publishing listings). Individual REST API access pricing unknown.
- **ToS for AI**: Not found publicly. MLS data typically has redistribution restrictions; realtor.com syndication suggests tight rules. **Get written approval before indexing.**
- **Data quality**: Highest in CR — structured, multilingual, with auction integration.
- **MVP effort**: Unknown until API access granted. Plan 1-2 weeks after partnership approval.
- **Honest take**: Highest strategic value (CCCBR endorsement = moat), highest uncertainty (private API, partnership friction). Start a conversation now, write no code.

### Other MLS / listing platforms

- **CCCBR unified MLS**: Same as Propertyshelf (CCCBR picked them as provider). Not separate.
- **EasyBroker**: 1 of 21. Paid "MLS API Plan" tier, server-only, 20 req/sec. Good docs + Ruby gem. Defer.
- **Propertybase**: 1 of 21 (2Costa Rica — no WhatsApp, not ICP). Salesforce-based; WebToProspect + GO API. Defer.
- **Encuentra24**: No public API or syndication docs. Agencies push *to* it as classifieds; not a canonical source.
- **EspacioFuturo** (Realty ONE): Direct outreach required. Defer.

### Generic fallbacks

- **Schema.org `RealEstateListing` JSON-LD**: 99% of Yoast-using WP sites emit structured data (Yoast covers 37% of all WP). Real Places / RealHomes / WPResidence emit property JSON-LD by default. Plain HTTP + `application/ld+json` parsing covers the long tail.
- **Sitemap-based crawling**: For sites without JSON-LD, parse `sitemap.xml` -> property URLs -> LLM extraction. Last resort.
- **Generic RETS/IDX**: US-first; no confirmed CR usage. Skip.

## Ranked recommendation

### Top 3 to integrate, in order

1. **Generic WordPress WP REST API adapter** (Houzez, RealHomes, WPResidence, Real Places — potentially 11-16 of 21). Ship first as a "connect your WordPress site" onboarding flow: site URL + Application Password, auto-detect theme, map Properties fields. Polling every 15 min initially; optional companion plugin that POSTs webhooks on `save_post_property` for real-time. ~1-2 engineer-weeks MVP. Highest coverage, lowest risk.
2. **Schema.org JSON-LD fallback scraper**. Any site we can't integrate natively. Sitemap -> JSON-LD -> normalize. Covers ~20% long tail (Next.js, Drupal, Squarespace, Luxury Presence). ~1 engineer-week. Daily cron, detect deltas via ETag + content hash.
3. **Propertyshelf MLS** — only after (a) customer demand and (b) confirmed API access. Strategic moat if won. Open partnership conversation *now*; write code later. If partnership stalls, fall back to per-customer scraping of their own mls.re.cr listings (ToS permitting).

### Top 2 to explicitly skip

- **Encuentra24** — not a data source, it's a downstream portal. Nothing to pull.
- **Propertybase** — one non-ICP user. 2-4 weeks of Salesforce integration work not justified pre-revenue.

### The "wait for demand" pile

EasyBroker (1 paid-tier user), HubSpot CMS Hub properties (1 user, covered if/when we do CRM sync), Espacio Futuro (1 user), Luxury Presence (proprietary, scrape only).

## Validation plan (pre-build)

Before writing integration code, ask in 3-5 ICP discovery calls:

1. "Where does the canonical list of your properties live today? If you rebuilt your site tomorrow, which system holds the truth?"
2. "How often do listings change? Daily price updates, weekly new inventory, monthly?"
3. "Who updates listings — agents directly in WordPress, a central admin, or someone pulling from an MLS?"
4. "Do you pay for Propertyshelf / CCCBR MLS? Do you actually use it, or does it sit idle?"
5. "If Trochai auto-imported your properties in under 5 minutes with no manual work, would you commit to a paid plan this month?"

Target: Propiedades Leiton (Plone+Propertyshelf), Tamarindo Real Estate (HubSpot), KRAIN (Plone + Luxury Presence), Casa Escazu (HubSpot CMS), Palm Real Estate (EasyBroker).

## ToS / legal risk notes

- **WordPress themes**: Agency owns the data and grants access via their credentials. No platform ToS concern.
- **Propertyshelf / CCCBR MLS**: Likely redistribution-restricted. Get written partner approval before AI indexing.
- **Schema.org scraping**: Fair on the agency's own site with consent. Respect `robots.txt`; publish a `Trochai-Bot` UA.
- **Encuentra24 / Facebook Marketplace scraping**: Explicitly disallowed by ToS — do not consider.

## Estimated effort matrix

| Source | API | AI ToS | MVP effort | Coverage | Moat |
|---|---|---|---|---|---|
| Generic WP REST (4 themes) | Native WP REST | Agency-owned — OK | 1-2 weeks | 55-75% | Medium |
| Schema.org JSON-LD scrape | Public HTML + sitemap | OK with consent | 1 week | 20-30% long tail | Low (fallback) |
| Propertyshelf (Plone MLS) | Private REST | Likely restricted | 1-2 weeks + partner wait | 15-25% [unverified] | High (CCCBR-backed) |
| EasyBroker | Public REST, paid tier | OK | 3-5 days | 5% | Low |
| Propertybase | WebToProspect + GO | OK | 2-3 weeks | 5% | Low |
| HubSpot Properties | Public REST | OK | 3-5 days | 5% | Low (pairs with CRM sync) |
| Encuentra24 | None published | N/A | - | 0% source | None |

## Sources

- Houzez Property Feed plugin: https://wordpress.org/plugins/houzez-property-feed/
- Houzez REST API docs: https://houzez.apidog.io/properties-13742776e0
- Propertyshelf developer page: https://propertyshelf.com/en/real-estate-builders-and-developers/developer-mls-solutions
- Propertyshelf GitHub (mls.apiclient, plone.mls.listing, ps.plone.mls): https://github.com/propertyshelf
- CCCBR + Propertyshelf partnership: https://www.re.cr/en/news/cccbr-proud-to-announce-propertyshelf-as-costa-ricas-new-mls-provider
- EasyBroker API docs: https://dev.easybroker.com/docs/api-de-easybroker
- EasyBroker MLS endpoint: https://dev.easybroker.com/reference/get_mls-properties
- Propertybase WebToProspect REST API: https://help.propertybase.com/hc/en-us/articles/360003180752-WebToProspect-REST-API
- Schema.org RealEstateListing: https://schema.org/RealEstateListing
- Yoast structured data adoption: https://yoast.com/features/structured-data/
- WP REST API Application Passwords: https://developer.wordpress.org/rest-api/using-the-rest-api/authentication/
- WP All Import Real Places / WPResidence / RealHomes add-ons: https://wordpress.org/plugins/realplaces-xml-csv-property-listings-import/ | https://wordpress.org/plugins/wp-residence-add-on-for-wp-all-import/ | https://wordpress.org/plugins/realhomes-xml-csv-property-listings-import/
- Internal: CR RE tech stack audit (`project_cr_real_estate_tech_stack.md`, April 2026)
