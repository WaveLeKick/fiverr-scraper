[Fiverr Scraper](https://apify.com/sovereigntaylor/fiverr-scraper?fpr=data)

Scrape Fiverr gig listings, freelancer profiles, and reviews without API keys. Extract pricing packages, seller levels, ratings, delivery times, and full review text for freelance marketplace research and competitive intelligence.

## Features

- **Gig search** — Search by keyword, category, price range, seller level, and sort order
- **Direct gig scraping** — Provide specific gig URLs for detailed extraction
- **Seller profiles** — Extract complete freelancer profiles with stats, skills, and languages
- **Reviews** — Optionally scrape reviews for each gig with reviewer details
- **3 pricing packages** — Extract Basic, Standard, and Premium package details per gig
- **Smart extraction** — Parses `__NEXT_DATA__` JSON (primary) with HTML fallback
- **Anti-bot handling** — Detects blocks/CAPTCHAs and stops gracefully
- **12 User-Agent rotation** — Browser fingerprint diversity
- **Fiverr-specific headers** — Mimics real browser requests
- **Proxy support** — Residential proxies recommended for reliable results
- **Rate limiting** — Max 15 requests/minute to avoid detection
- **Pay-per-event** — Only pay for data you actually get

## Use Cases

### Competitive Intelligence

Monitor competitors' pricing, delivery times, and review counts across your Fiverr category. Track how top sellers position their gigs.

### Market Research

Analyze freelance marketplace trends — which categories are growing, what price points succeed, and where demand exceeds supply.

### Pricing Intelligence

Benchmark your freelance rates against hundreds of comparable gigs. Find the optimal price point for each service tier.

### Freelancer Recruitment

Search for skilled freelancers by category, rating, and seller level. Extract contact-ready profiles for recruitment outreach.

### Trend Analysis

Track new gigs and emerging categories on Fiverr. Identify rising niches (AI services, blockchain, etc.) before they saturate.

### Content Strategy

Analyze top-performing gig titles, descriptions, and tags. Reverse-engineer what makes best-selling gig copy work.

## Input

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `searchQuery` | String | *(empty)* | Search Fiverr gigs by keyword (e.g., "logo design") |
| `gigUrls` | String[] | `[]` | Direct Fiverr gig URLs to scrape |
| `sellerProfiles` | String[] | `[]` | Seller profile URLs or usernames |
| `maxResults` | Integer | `50` | Max gigs from search (1-500) |
| `category` | String | *(all)* | Category filter (graphics-design, programming-tech, etc.) |
| `minPrice` | Integer | `0` | Minimum price filter |
| `maxPrice` | Integer | `0` | Maximum price filter |
| `sellerLevel` | Enum | `any` | Filter: any, new_seller, level_one, level_two, top_rated |
| `sortBy` | Enum | `relevance` | Sort: relevance, best_selling, newest, price_low, price_high |
| `includeReviews` | Boolean | `false` | Also scrape reviews for each gig |
| `maxReviewsPerGig` | Integer | `20` | Max reviews per gig (1-100) |
| `maxConcurrency` | Integer | `3` | Parallel requests (lower = safer) |
| `proxyConfiguration` | Object | *(none)* | Apify proxy settings |

### Categories

| Slug | Category |
| --- | --- |
| `graphics-design` | Graphics & Design |
| `digital-marketing` | Digital Marketing |
| `writing-translation` | Writing & Translation |
| `video-animation` | Video & Animation |
| `music-audio` | Music & Audio |
| `programming-tech` | Programming & Tech |
| `business` | Business |
| `lifestyle` | Lifestyle |
| `ai-services` | AI Services |

## Input Examples

### Search for logo designers, sorted by best selling

```
{
    "searchQuery": "logo design",
    "sortBy": "best_selling",
    "maxResults": 100,
    "proxyConfiguration": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}
```

### Top-rated web developers under $200

```
{
    "searchQuery": "web development",
    "category": "programming-tech",
    "sellerLevel": "top_rated",
    "maxPrice": 200,
    "maxResults": 50,
    "includeReviews": true,
    "proxyConfiguration": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}
```

### Scrape specific gig pages

```
{
    "gigUrls": [
        "https://www.fiverr.com/seller1/i-will-design-a-logo",
        "https://www.fiverr.com/seller2/i-will-build-your-website"
    ],
    "includeReviews": true,
    "maxReviewsPerGig": 50,
    "proxyConfiguration": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}
```

### Extract seller profiles

```
{
    "sellerProfiles": [
        "https://www.fiverr.com/johndoe",
        "janedoe",
        "topdesigner123"
    ],
    "proxyConfiguration": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}
```

### AI services — newest gigs

```
{
    "searchQuery": "AI chatbot",
    "category": "ai-services",
    "sortBy": "newest",
    "maxResults": 200,
    "proxyConfiguration": {
        "useApifyProxy": true,
        "apifyProxyGroups": ["RESIDENTIAL"]
    }
}
```

## Output

### Gig Output

Each scraped gig is saved to the dataset with the following fields:

```
{
    "type": "gig",
    "title": "I will design a professional logo for your brand",
    "description": "Full gig description text...",
    "priceStarting": 25,
    "priceCurrency": "USD",
    "packages": [
        {
            "tier": "Basic",
            "price": 25,
            "deliveryDays": 3,
            "revisions": 2,
            "description": "1 logo concept + PNG file"
        },
        {
            "tier": "Standard",
            "price": 50,
            "deliveryDays": 2,
            "revisions": 5,
            "description": "3 logo concepts + source files"
        },
        {
            "tier": "Premium",
            "price": 100,
            "deliveryDays": 1,
            "revisions": "Unlimited",
            "description": "5 concepts + full brand kit"
        }
    ],
    "sellerUsername": "prodesigner",
    "sellerDisplayName": "Pro Designer Studio",
    "sellerLevel": "Top Rated Seller",
    "sellerRating": 4.9,
    "sellerCountry": "US",
    "sellerImage": "https://...",
    "deliveryTime": "3 days",
    "revisions": 2,
    "rating": 4.9,
    "reviewCount": 1523,
    "ordersInQueue": 12,
    "tags": ["logo design", "branding", "minimalist"],
    "category": "Graphics & Design",
    "subcategory": "Logo Design",
    "imageUrl": "https://...",
    "videoUrl": null,
    "gigUrl": "https://www.fiverr.com/prodesigner/i-will-design-a-professional-logo",
    "isFeatured": false,
    "isProVerified": true,
    "createdAt": "2024-03-15T00:00:00.000Z",
    "scrapedAt": "2026-03-01T12:00:00.000Z"
}
```

### Seller Output

```
{
    "type": "seller",
    "username": "prodesigner",
    "displayName": "Pro Designer Studio",
    "tagline": "Award-winning graphic designer with 10+ years experience",
    "description": "Full seller bio...",
    "level": "Top Rated Seller",
    "rating": 4.9,
    "reviewCount": 3200,
    "responseTime": "1 hour",
    "lastDelivery": "about 2 hours ago",
    "memberSince": "Jan 2019",
    "country": "United States",
    "languages": ["English", "Spanish"],
    "profilePicUrl": "https://...",
    "skills": ["Logo Design", "Brand Identity", "Adobe Illustrator"],
    "totalGigs": 15,
    "completedOrders": 4500,
    "profileUrl": "https://www.fiverr.com/prodesigner",
    "isPro": true,
    "isOnline": true,
    "scrapedAt": "2026-03-01T12:00:00.000Z"
}
```

### Review Output

```
{
    "type": "review",
    "reviewerName": "happyclient",
    "reviewerCountry": "United Kingdom",
    "rating": 5,
    "text": "Amazing work! Delivered exactly what I needed, ahead of schedule.",
    "date": "2026-02-15T00:00:00.000Z",
    "gigTitle": "I will design a professional logo for your brand",
    "price": 50,
    "deliveryTime": "2 days",
    "gigUrl": "https://www.fiverr.com/prodesigner/i-will-design-a-professional-logo",
    "scrapedAt": "2026-03-01T12:00:00.000Z"
}
```

## Proxy Recommendations

Fiverr has aggressive anti-bot protection. **Residential proxies are strongly recommended** for any scraping beyond a few pages.

| Setup | Reliability | Speed | Cost |
| --- | --- | --- | --- |
| No proxy | Low (blocked quickly) | Fast | Free |
| Datacenter proxy | Low-Medium | Fast | Low |
| **Residential proxy** | **High** | Medium | Medium |
| SERP proxy | Medium | Medium | Medium |

### Recommended proxy configuration:

```
{
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"]
}
```

## Performance Tips

1. **Always use residential proxies** — Fiverr blocks datacenter IPs aggressively
2. **Start with a small test** — Try `maxResults: 10` to verify scraping works before scaling
3. **Keep concurrency low** — Default of 3 is safe; increase only with good proxies
4. **Use filters** — Category, price, and seller level filters reduce pages to scrape
5. **Disable reviews for speed** — Set `includeReviews: false` (default) for faster runs
6. **Use direct URLs when possible** — Direct gig URLs skip search pagination entirely

## Rate Limiting

This actor limits requests to 15 per minute to respect Fiverr's infrastructure. The scraper:

- Rotates through 12 different User-Agent strings
- Sends browser-like headers (Accept, Referer, Sec-Fetch-*)
- Detects CAPTCHA/block pages and stops gracefully
- Retries failed requests up to 3 times
- Stops entirely after 3 consecutive blocks

## Pricing (Pay Per Event)

| Event | Price | Description |
| --- | --- | --- |
| `gig-scraped` | $0.003 | Each gig saved to dataset |
| `seller-scraped` | $0.005 | Each seller profile saved |
| `review-scraped` | $0.002 | Each batch of reviews saved |

Plus Apify platform costs (compute + proxy if used).

## Legal Notice

This actor is provided as a technical tool for market research and competitive analysis. Users are responsible for ensuring their use complies with Fiverr's Terms of Service and all applicable laws. The actor is designed for legitimate research purposes.

## Integration — Python

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("sovereigntaylor/fiverr-scraper").call(run_input={
    "searchTerm": "fiverr",
    "maxResults": 50
})

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{item.get('title', item.get('name', 'N/A'))}")
```

## Integration — JavaScript

```
import { ApifyClient } from 'apify-client';
const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('sovereigntaylor/fiverr-scraper').call({
    searchTerm: 'fiverr',
    maxResults: 50
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(item => console.log(item.title || item.name || 'N/A'));
```