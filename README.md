[Fiverr Scraper](https://apify.com/igview-owner/fiverr-scraper?fpr=data)

# Fiverr Search Gig Scraper 🎯

Extract comprehensive Fiverr gig data with a simple keyword search. Get gig titles, seller information, pricing, ratings, performance metrics, and more in seconds. Perfect for market research, competitor analysis, price comparison, and lead generation. 🚀

---

## 📋 Table of Contents

- What You Get
- How to Use
- Input Parameters
- Output Data
- Use Cases
- Tips & Best Practices
- FAQ

---

## 🎯 What You Get

This Fiverr scraper extracts comprehensive gig information:

### 📝 Gig Details

- **Basic Info**: Gig ID, title, URL, slug, thumbnail
- **Gallery Images**: All gig portfolio images (optional)
- **Categories**: Category and subcategory IDs

### 👤 Seller Information

- **Profile**: Username, display name, profile image
- **Location**: Country code
- **Status**: Online status, Pro badge
- **Level**: Seller level (new, level 1, level 2, top rated)
- **Languages**: Spoken languages with proficiency levels
- **Ratings**: Overall rating score and review count

### 💰 Pricing Details

- **Starting Price**: Minimum gig price
- **Currency**: USD, EUR, etc.
- **Package Info**: Recommended package details
- **Delivery Time**: Delivery days for each package
- **Total Packages**: Number of pricing tiers available

### 📈 Performance Metrics

- **Position**: Search result position
- **Badges**: Fiverr's Choice, Featured status
- **Buying Metrics**: Buying rating and review count
- **Impression ID**: Unique impression identifier

### ⚙️ Features & Capabilities

- Consultation availability
- Video intro presence
- Work samples availability
- Recurring options
- Personalized pricing

---

## 🚀 How to Use

### Quick Start (3 Steps)

1. **Enter Search Query**: Type the service you're looking for (e.g., "logo design", "voice over")
2. **Configure Options**: Set pages to scrape and data options
3. **Run & Export**: Click start, wait for results, then export as JSON/CSV/Excel

No coding required! Simple form-based interface with emoji-rich descriptions. ✨

---

## ⚙️ Input Parameters

### 🔎 Search Configuration

| Parameter | Type | Required | Description | Default |
| --- | --- | --- | --- | --- |
| **query** 🔍 | string | ✅ Yes | Service or keyword to search (e.g., "poster design", "wordpress developer") | `poster design` |
| **startPage** 📄 | integer | No | Page number to start from (each page ≈ 48 gigs) | `1` |
| **maxPages** 📚 | integer | No | Maximum pages to scrape (1-50) | `1` |

### ⚙️ Data Options

| Parameter | Type | Description | Default |
| --- | --- | --- | --- |
| **includeSellerDetails** 👤 | boolean | Extract seller info (username, rating, level, etc.) | `true` |
| **includePricing** 💰 | boolean | Extract pricing and package details | `true` |
| **includePerformance** 📈 | boolean | Extract performance metrics and badges | `true` |
| **includeGallery** 🖼️ | boolean | Extract all gallery image URLs | `false` |

### Example Input

```
{
  "query": "logo design",
  "startPage": 1,
  "maxPages": 3,
  "includeSellerDetails": true,
  "includePricing": true,
  "includePerformance": true,
  "includeGallery": false
}
```

---

## 📊 Output Data

Each gig is saved as a separate result with comprehensive data:

### Sample Output

```
{
  "id": 449562576,
  "title": "design professional flyers and posters to boost your brand",
  "url": "https://www.fiverr.com/fist_of_fury/design-professional-flyers-and-posters-to-boost-your-brand",
  "slug": "design-professional-flyers-and-posters-to-boost-your-brand",
  "thumbnail": "https://fiverr-res.cloudinary.com/t_main1,q_auto,f_auto/gigs/449562576/original/...",
  
  "seller_id": 3483309,
  "seller_username": "fist_of_fury",
  "seller_displayName": "Usama Z",
  "seller_country": "PK",
  "seller_isOnline": true,
  "seller_isPro": false,
  "seller_level": "top_rated_seller",
  "seller_languages": "en (Level 3)",
  "seller_rating_score": 4.9141455,
  "seller_rating_count": 4333,
  
  "starting_price": 25,
  "currency": "USD",
  "delivery_days": 1,
  "total_packages": 3,
  
  "position": 1,
  "isFiverrChoice": false,
  "isFeatured": false,
  "buying_rating": 4.9,
  "buying_review_count": 11,
  
  "category_id": 3,
  "subcategory_id": 55,
  "offerConsultation": true,
  "hasVideoIntro": false,
  "hasWorkSamples": true,
  
  "scraped_at": "2024-11-24T06:34:12.345Z"
}
```

### 📋 Table Views

The actor provides two organized table views:

#### 📊 Gigs Overview

Clean, essential data for quick analysis:

- Gig ID, Title, URL, Thumbnail
- Seller Username, Name, Country, Level
- Rating, Reviews, Price, Delivery Time
- Position in search results

#### 📋 Detailed View

Comprehensive data including:

- All overview fields
- Online status, Pro badge
- Package details, buying metrics
- Category IDs, features, video intro

### Export Formats

- **JSON**: Full structured data with all fields
- **CSV**: Spreadsheet-friendly format
- **Excel**: Ready for analysis and reporting

---

## 💼 Use Cases

### 🎯 Market Research

- Analyze service offerings in your niche
- Identify trending services and keywords
- Study pricing strategies across categories
- Track market saturation levels

### 🔍 Competitor Analysis

- Monitor competitor gig performance
- Compare pricing and delivery times
- Analyze top-rated seller strategies
- Track Fiverr's Choice and Featured gigs

### 💰 Price Intelligence

- Compare pricing across sellers
- Identify optimal price points
- Analyze package structures
- Track pricing trends over time

### 👥 Lead Generation

- Find potential collaboration partners
- Identify top sellers in your category
- Build seller contact lists
- Discover Pro sellers and agencies

### 📈 SEO & Optimization

- Research high-performing gig titles
- Analyze successful gig positioning
- Study category and subcategory trends
- Identify keyword opportunities

### 🎨 Portfolio Building

- Collect design inspiration
- Study successful gig presentations
- Analyze gallery image strategies
- Research video intro effectiveness

---

## 💡 Tips & Best Practices

### 🔍 Search Optimization

- **Be Specific**: Use detailed keywords like "minimalist logo design" instead of just "logo"
- **Try Variations**: Test different keyword combinations to find all relevant gigs
- **Use Categories**: Include category names like "wordpress", "voice over", "video editing"
- **Check Spelling**: Ensure correct spelling for accurate results

### 📊 Data Collection

- **Start Small**: Test with 1-2 pages first, then scale up
- **Respect Rate Limits**: The actor includes 2-second delays between pages
- **Monitor Costs**: Each page ≈ 48 gigs, plan your maxPages accordingly
- **Regular Updates**: Re-run weekly/monthly to track changes

### 💾 Data Management

- **Choose Data Options Wisely**:

- Enable `includeGallery` only if you need image URLs (increases data size)
- Keep other options enabled for comprehensive analysis
- **Export Strategically**:

- JSON for databases and APIs
- CSV for Excel and Google Sheets
- Excel for business reports
- **Track Timestamps**: Use `scraped_at` field to track data freshness

### ⚡ Performance

- **Batch Processing**: Run multiple searches with different queries
- **Schedule Runs**: Use Apify scheduling for automated data collection
- **Parallel Actors**: Run multiple actor instances for different categories
- **Monitor Logs**: Check console output for errors and progress

### 🎯 Analysis Tips

- **Sort by Position**: Find top-ranking gigs
- **Filter by Rating**: Identify high-quality sellers (4.8+ rating)
- **Compare Prices**: Analyze pricing strategies
- **Track Badges**: Focus on Fiverr's Choice and Featured gigs
- **Study Levels**: Compare new sellers vs. top-rated sellers

---

## ❓ FAQ

### What data can I extract?

You can extract gig titles, URLs, seller information (username, rating, level, country), pricing details, delivery times, performance metrics, badges, categories, features, and optionally gallery images.

### Do I need coding skills?

No! This is a no-code solution. Just fill in the search query and options in the simple form interface with helpful emoji descriptions.

### How many gigs can I scrape?

Each page contains approximately 48 gigs. You can scrape up to 50 pages per run (≈2,400 gigs). For more, run the actor multiple times.

### Is this legal?

Yes. This scraper extracts publicly available data from Fiverr that anyone can see. Always comply with Fiverr's Terms of Service and applicable laws. Use responsibly.

### Can I automate this?

Yes! Use Apify's scheduling feature to run the scraper automatically at set intervals (hourly, daily, weekly, etc.).

### What if I get errors?

- **429**: Rate limit exceeded, wait and try again or upgrade your plan
- **No results**: Verify your search query and try different keywords
- **Timeout**: Reduce maxPages or check your internet connection

### How do I export the data?

After the run completes:

1. Go to the **Storage** → **Dataset** tab
2. Choose a view: "📊 Gigs Overview" or "📋 Detailed View"
3. Click **Export** and select format (JSON, CSV, Excel)
4. Download your data

### Can I scrape specific categories?

Yes! Include category names in your search query (e.g., "logo design", "wordpress development", "voice over artist").

### How often should I run this?

Depends on your use case:

- **Market Research**: Weekly or monthly
- **Competitor Tracking**: Daily or weekly
- **Price Monitoring**: Weekly
- **One-time Analysis**: As needed

### Can I scrape seller profiles?

This actor focuses on gig search results. For detailed seller profiles, you may need additional tools or API endpoints.

### How accurate is the data?

The data comes directly from Fiverr's search results and is as accurate as what Fiverr displays. Data freshness depends on when you run the scraper.

---

### Features

- ✅ Clean, organized table views with emojis
- ✅ Configurable data extraction options
- ✅ Automatic rate limiting (2s delay between pages)
- ✅ Comprehensive error handling
- ✅ Progress logging with emojis
- ✅ Flat data structure for easy analysis
- ✅ Timestamp tracking
- ✅ Multiple export formats

---

## 📞 Support

Need help? Have questions?

- **Documentation**: You're reading it! 📖
- **Apify Support**: Contact via Apify platform

---

## 🏷️ Find Me

Fiverr scraper, Fiverr gig scraper, Fiverr data extraction, scrape Fiverr, Fiverr search scraper, Fiverr API, freelance marketplace scraper, gig economy data, Fiverr lead generation, Fiverr market research, Fiverr competitor analysis, Fiverr price comparison, Fiverr seller data, Fiverr gig data, extract Fiverr data, Fiverr automation, Fiverr data mining, Fiverr business intelligence, Fiverr analytics, Fiverr pricing data, Fiverr rating scraper, Fiverr review scraper, freelance data scraper, gig scraper, service marketplace scraper, Apify Fiverr, no-code Fiverr scraper, Fiverr to Excel, Fiverr to CSV, export Fiverr data, Fiverr bulk export, Fiverr search API, Fiverr gig search, Fiverr category scraper