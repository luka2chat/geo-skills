---
name: structured-data
description: Schema.org JSON-LD markup patterns for articles, FAQs, products, and organizations
metadata:
  tags: schema, structured-data, json-ld, rich-results
---

## Structured Data for GEO

Schema.org structured data helps AI engines understand the type, authorship, and relationships within your content. Implement JSON-LD in the `<head>` of every content page.

### Article Schema

Use for blog posts, guides, news articles, and editorial content:

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Complete Guide to Generative Engine Optimization (GEO)",
  "description": "Learn how to optimize your content for AI search engines like ChatGPT, Perplexity, and Google AI Overviews.",
  "author": {
    "@type": "Person",
    "name": "Jane Smith",
    "url": "https://example.com/authors/jane-smith",
    "jobTitle": "Director of Content Strategy",
    "sameAs": [
      "https://linkedin.com/in/janesmith",
      "https://twitter.com/janesmith"
    ]
  },
  "datePublished": "2026-01-15",
  "dateModified": "2026-03-01",
  "publisher": {
    "@type": "Organization",
    "name": "Example Inc.",
    "url": "https://example.com",
    "logo": {
      "@type": "ImageObject",
      "url": "https://example.com/logo.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://example.com/guides/geo-optimization"
  },
  "image": "https://example.com/images/geo-guide-hero.jpg",
  "keywords": ["GEO", "generative engine optimization", "AI search", "LLM optimization"]
}
```

### FAQ Schema

Use for FAQ pages and content with Q&A sections. This format directly maps to how AI engines answer user questions:

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is Generative Engine Optimization (GEO)?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Generative Engine Optimization (GEO) is an optimization strategy aimed at improving content visibility in AI-powered search engines and LLM-based answer engines such as ChatGPT, Perplexity, and Google AI Overviews."
      }
    },
    {
      "@type": "Question",
      "name": "How is GEO different from SEO?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "While SEO focuses on ranking in traditional search engines through keywords and backlinks, GEO focuses on being cited by AI engines through authority, quotability, factual accuracy, and structured data."
      }
    }
  ]
}
```

### Organization Schema

Use on the homepage or about page to establish entity identity:

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example Inc.",
  "url": "https://example.com",
  "logo": "https://example.com/logo.png",
  "description": "Example Inc. is a content optimization platform helping brands increase visibility in AI search engines.",
  "foundingDate": "2020-01-01",
  "sameAs": [
    "https://twitter.com/example",
    "https://linkedin.com/company/example",
    "https://github.com/example"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "contactType": "customer support",
    "email": "support@example.com"
  }
}
```

### Product Schema

Use for product pages to be cited in AI shopping and recommendation queries:

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "GEO Analytics Platform",
  "description": "Track and optimize your brand's visibility across AI search engines.",
  "brand": {
    "@type": "Brand",
    "name": "Example Inc."
  },
  "offers": {
    "@type": "Offer",
    "price": "99.00",
    "priceCurrency": "USD",
    "availability": "https://schema.org/InStock"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "reviewCount": "250"
  }
}
```

### HowTo Schema

Use for step-by-step guides and tutorials:

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to Optimize Content for AI Search Engines",
  "description": "A step-by-step guide to implementing Generative Engine Optimization.",
  "step": [
    {
      "@type": "HowToStep",
      "name": "Audit Current Content",
      "text": "Review your existing content for AI readability, quotability, and authority signals."
    },
    {
      "@type": "HowToStep",
      "name": "Implement Structured Data",
      "text": "Add Schema.org JSON-LD markup to all content pages."
    },
    {
      "@type": "HowToStep",
      "name": "Configure AI Crawlers",
      "text": "Update robots.txt to allow GPTBot, ClaudeBot, and PerplexityBot access."
    }
  ]
}
```

### Implementation Rules

1. Use **JSON-LD** format — place `<script type="application/ld+json">` in the `<head>` section
2. Every article page MUST have `Article` schema with `author`, `datePublished`, and `dateModified`
3. Keep `dateModified` accurate — AI engines use it to assess freshness; a stale date reduces citation likelihood
4. Use `sameAs` to link author and organization to external authoritative profiles
5. Implement `author` with full details: `name`, `jobTitle`, `url`, and `sameAs`
6. Nest schemas logically: Article → Author (Person) → Employer (Organization)
7. For pages with Q&A sections, add `FAQPage` schema in addition to `Article` schema
8. Validate markup by checking that all `@type`, `name`, and required fields are present before deploying
