---
name: product-feed
description: Product feed submission and structured product data for AI shopping citations
metadata:
  tags: product-feed, e-commerce, merchant-center, shopping, product-schema
---

## Product Feed for AI Platforms

AI platforms increasingly surface product recommendations and shopping results. Submitting structured product feeds helps AI engines accurately cite, compare, and recommend your products.

### Platform Submission

| Platform | Where to Submit | What It Powers |
|----------|----------------|----------------|
| **Google** | Google Merchant Center | Google AI Mode product citations, AI Overviews shopping results |
| **Microsoft** | Microsoft Merchant Center | Copilot product results, Bing Chat shopping answers |
| **ChatGPT** | OpenAI product discovery (coming soon) | ChatGPT shopping recommendations |

### Product Feed Format

Use Google's standard product feed format (also accepted by Microsoft). Minimum required fields:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:g="http://base.google.com/ns/1.0">
  <channel>
    <title>Your Store Products</title>
    <link>https://yourstore.com</link>
    <item>
      <g:id>SKU-001</g:id>
      <g:title>Product Name - Key Feature</g:title>
      <g:description>Factual product description with key specs and use cases. Avoid marketing fluff.</g:description>
      <g:link>https://yourstore.com/products/product-name</g:link>
      <g:image_link>https://yourstore.com/images/product-name.jpg</g:image_link>
      <g:price>99.00 USD</g:price>
      <g:availability>in_stock</g:availability>
      <g:brand>Your Brand</g:brand>
      <g:condition>new</g:condition>
      <g:gtin>0123456789012</g:gtin>
    </item>
  </channel>
</rss>
```

### Product Page Schema

In addition to the feed, implement Product schema on each product page:

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Product Name",
  "description": "Clear, factual description of the product and its primary use case.",
  "brand": {
    "@type": "Brand",
    "name": "Your Brand"
  },
  "sku": "SKU-001",
  "gtin13": "0123456789012",
  "image": "https://yourstore.com/images/product.jpg",
  "offers": {
    "@type": "Offer",
    "price": "99.00",
    "priceCurrency": "USD",
    "availability": "https://schema.org/InStock",
    "url": "https://yourstore.com/products/product-name"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.7",
    "reviewCount": "312"
  },
  "review": [
    {
      "@type": "Review",
      "author": { "@type": "Person", "name": "Jane D." },
      "reviewRating": { "@type": "Rating", "ratingValue": "5" },
      "reviewBody": "Specific review text with real user experience."
    }
  ]
}
```

### Product Content Optimization for AI

AI engines cite product pages in recommendation and comparison queries. Optimize product content:

```
Product page GEO checklist:
- [ ] Clear, factual product title (brand + product name + key differentiator)
- [ ] Description written as facts, not marketing copy
- [ ] Key specifications in a structured table or list
- [ ] Comparison with alternatives (AI uses this for "vs" queries)
- [ ] Real user reviews visible in HTML (not loaded via JS widget)
- [ ] Product schema with price, availability, rating, and reviews
- [ ] GTIN/UPC/EAN included in schema for product identification
- [ ] High-quality images with descriptive alt text
```

### Product Feed Writing Rules

```
DO:
- Write titles as: [Brand] [Product Name] [Key Feature/Size/Color]
- Write descriptions as factual summaries of what the product is and does
- Include specific measurements, materials, and technical specs
- Keep prices and availability accurate and updated daily

DON'T:
- Use ALL CAPS or excessive punctuation in titles
- Include promotional text ("BEST SELLER!!!", "50% OFF")
- Use vague descriptions ("amazing product", "must-have item")
- Leave GTIN/barcode fields empty if you have them
```
