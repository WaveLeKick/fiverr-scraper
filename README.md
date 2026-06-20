[Fiverr Scraper](https://apify.com/junipr/fiverr-scraper?fpr=data)

Extract Fiverr gig data at scale — pricing tiers, seller ratings, delivery times, order counts, reviews, and FAQs. The only Fiverr scraper that actually works: built to replace the broken 1.0-star actor that left 500+ users without a solution.

## What is Fiverr Gigs Scraper?

Fiverr is home to 4 million+ active buyers and hundreds of thousands of freelance gigs across design, development, writing, marketing, and more. This actor scrapes Fiverr gig listings in bulk, giving you structured data for competitive pricing analysis, lead generation, freelance market research, and gig economy studies.

Unlike other Fiverr scrapers that crash on first run or miss critical fields, this actor extracts complete three-tier pricing (Basic, Standard, Premium), full seller profile data, and gig metadata — reliably, at scale, with Cloudflare bypass built in.

## Key Features

- **Three-tier pricing extraction** — Basic, Standard, and Premium packages with price, delivery days, revisions, and feature lists
- **Complete seller profiles** — level (New, Level 1, Level 2, Top Rated, Pro), rating, review count, response time, member since, country, languages
- **Pro and Top Rated badge detection** — `isPro` and `level` flags for accurate seller filtering
- **Category and keyword search** — search by keyword, category slug, or subcategory slug with full filter support
- **Seller-level filtering** — narrow results to specific seller tiers (e.g. Top Rated + Pro only)
- **Price range filtering** — set minimum and maximum price bounds
- **Delivery time filtering** — filter by 1-day, 3-day, or 7-day delivery options
- **Review extraction** — up to 10 sample reviews per gig with reviewer name, rating, text, and date
- **FAQ extraction** — full FAQ section from each gig page
- **Direct URL mode** — scrape specific gig URLs by providing a list directly
- **Batch search** — run up to 50 search terms in a single actor run
- **Cloudflare bypass** — uses Playwright with realistic browser fingerprinting to handle Fiverr's Cloudflare protection

## What Data Can You Extract?

| Field | Description |
| --- | --- |
| `gigId` | Fiverr gig slug identifier |
| `url` | Full URL to the gig page |
| `title` | Complete gig title |
| `description` | Plain text gig description |
| `seller.username` | Seller's Fiverr username |
| `seller.displayName` | Seller's display name |
| `seller.level` | Seller level: new, level_one, level_two, top_rated, pro |
| `seller.isPro` | Whether the seller has Fiverr Pro verification |
| `seller.rating` | Seller rating (1–5 scale) |
| `seller.reviewCount` | Total review count |
| `seller.responseTime` | Typical response time |
| `seller.country` | Seller's country code |
| `seller.languages` | Languages the seller speaks |
| `seller.memberSince` | When the seller joined Fiverr |
| `pricing.basic` | Basic tier: price, delivery days, revisions, features |
| `pricing.standard` | Standard tier (null if not offered) |
| `pricing.premium` | Premium tier (null if not offered) |
| `category` | Main category (e.g. Graphics & Design) |
| `subcategory` | Subcategory (e.g. Logo Design) |
| `tags` | Gig tags and keywords |
| `images` | Portfolio image URLs |
| `hasVideo` | Whether gig includes a video |
| `faq` | FAQ question-and-answer pairs |
| `reviews` | Sample reviews (up to 10) |
| `orderCount` | Total orders completed |
| `scrapedAt` | Extraction timestamp |

## Proxy Requirements

This actor requires **residential proxy** to access Fiverr, which blocks datacenter IP addresses.

- **Apify paid plans**: Residential proxy is included. The actor uses it by default.
- **Apify free plan**: Free plan does not include residential proxy. You can provide your own residential proxy URL in the proxy configuration, or the actor will attempt to run without proxy (results may be empty or blocked).
- **Without residential proxy**: The actor will still run but may return zero results due to IP blocking by Fiverr.

## How to Use

### Freelance Market Research

Search for a service category and analyze pricing across hundreds of gigs to understand what the market charges, what features sellers include, and which delivery times are most common:

```
{
  "searchTerms": ["seo optimization", "content writing"],
  "maxGigs": 200,
  "sortBy": "best_selling"
}
```

### Competitive Intelligence for Sellers

Find the top-performing gigs in your niche and analyze what makes them successful — their pricing tiers, descriptions, tags, and seller levels:

```
{
  "searchTerms": ["wordpress website development"],
  "maxGigs": 100,
  "sellerLevel": ["top_rated", "pro"],
  "sortBy": "best_selling",
  "includeFaq": true
}
```

### Lead Generation

Identify active freelancers offering specific services. Filter by seller level, country, and response time to find high-quality leads for partnership outreach or talent acquisition:

```
{
  "searchTerms": ["react developer"],
  "sellerLevel": ["level_two", "top_rated"],
  "sellerCountry": "US",
  "priceMin": 100,
  "sortBy": "best_selling"
}
```

### Direct Gig Scraping

Scrape a specific list of gig URLs to monitor competitor pricing changes or build a dataset of known gigs:

```
{
  "gigUrls": [
    "https://www.fiverr.com/designpro99/design-a-modern-minimalist-logo",
    "https://www.fiverr.com/webdev_expert/build-a-wordpress-website"
  ],
  "includeReviews": true
}
```

## Pricing

**$2.60 per 1,000 gigs** extracted. Pay only for results — no charge for paused gigs, deleted gigs, zero-result searches, or blocked pages. This is a Pay-Per-Event actor: you are billed only for each gig successfully pushed to the dataset.

Pricing includes all platform compute costs — no hidden fees.

A typical run of 100 gigs costs $0.25. A batch run of 1,000 gigs costs $2.50.

## Input and Output Examples

**Minimal input (zero-config):**

```
{}
```

Scrapes 100 most relevant gigs for "logo design" with pricing tiers and FAQ.

**Full input example:**

```
{
  "searchTerms": ["logo design", "brand identity"],
  "maxGigs": 500,
  "sellerLevel": ["top_rated", "pro"],
  "priceMin": 25,
  "priceMax": 500,
  "sortBy": "best_selling",
  "includeReviews": true,
  "includeFaq": true
}
```

**Output example (single gig):**

```
{
  "gigId": "i-will-design-a-modern-minimalist-logo",
  "url": "https://www.fiverr.com/designpro99/i-will-design-a-modern-minimalist-logo",
  "title": "I will design a modern minimalist logo for your business",
  "seller": {
    "username": "designpro99",
    "level": "top_rated",
    "isPro": false,
    "rating": 4.9,
    "reviewCount": 2340
  },
  "pricing": {
    "basic": { "price": 25, "deliveryDays": 3, "revisions": 1 },
    "standard": { "price": 50, "deliveryDays": 3, "revisions": 3 },
    "premium": { "price": 120, "deliveryDays": 5, "revisions": -1 }
  },
  "category": "Graphics & Design",
  "subcategory": "Logo Design",
  "orderCount": 5678,
  "scrapedAt": "2026-03-11T12:00:00.000Z"
}
```

## Related Scrapers by Junipr

- [Glassdoor Jobs Scraper](https://apify.com/junipr/glassdoor-scraper) — Extract job postings with salary ranges, company ratings, and interview insights
- [Indeed Job Scraper](https://apify.com/junipr/indeed-scraper) — Scrape Indeed job listings with full job descriptions and employer details

---

### How much does it cost to scrape Fiverr?

$2.60 per 1,000 gigs. A 100-gig run costs $0.26. There are no monthly fees — you only pay for the gigs you successfully extract.

### Can I extract all three pricing tiers?

Yes. The actor extracts Basic, Standard, and Premium tiers from every gig that offers them — including price, delivery days, revision count, and feature list. Gigs that only offer a Basic tier will have `standard: null` and `premium: null`.

### Can I filter by seller level (Pro, Top Rated)?

Yes. Set `sellerLevel` to an array of values: `"new"`, `"level_one"`, `"level_two"`, `"top_rated"`, or `"pro"`. You can combine multiple levels in one run.

### Does it extract seller reviews?

Yes, when `includeReviews` is set to `true`. Up to 10 reviews per gig are extracted, including reviewer name, rating, text, and date.

### Can I search by category and subcategory?

Yes. Use the `category` and `subcategory` fields with Fiverr's category slugs (e.g. `"graphics-design"` and `"logo-design"`). You can combine category filtering with keyword search terms.

### Is scraping Fiverr legal?

Fiverr's Terms of Service prohibit automated scraping. However, all gig pages are publicly visible with no login required, and this actor only extracts publicly available data. Users are responsible for ensuring their use of scraped data complies with applicable laws and Fiverr's Terms of Service. This actor is intended for market research and competitive analysis purposes.