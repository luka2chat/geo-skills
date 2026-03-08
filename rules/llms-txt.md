---
name: llms-txt
description: Implementing the llms.txt standard for AI-readable site information
metadata:
  tags: llms-txt, ai-readable, machine-readable, site-information
---

## llms.txt Standard

[llms.txt](https://llmstxt.org/) is an emerging standard (similar to robots.txt) that provides AI models with structured, machine-readable information about your website. Research shows sites with proper llms.txt see approximately **24% more accurate brand descriptions** in AI responses.

### File Location

Place the file at the root of your domain:

```
https://example.com/llms.txt
```

### Format Specification

The llms.txt file uses a simplified Markdown format:

```markdown
# Your Brand Name

> A 1-3 sentence summary of your business, product, or organization.
> This is the most important section — AI models use it as the primary
> brand description.

## About

Brief overview of what the organization does, its mission, and key
differentiators.

## Contact

- Website: https://example.com
- Email: hello@example.com
- Support: https://example.com/support

## Products & Services

- [Product A](https://example.com/product-a): One-line description of Product A
- [Product B](https://example.com/product-b): One-line description of Product B
- [Service C](https://example.com/service-c): One-line description of Service C

## Key Information

- [About Us](https://example.com/about): Company background and team
- [Documentation](https://example.com/docs): Technical documentation
- [Blog](https://example.com/blog): Latest articles and insights
- [Pricing](https://example.com/pricing): Plans and pricing information
- [API Reference](https://example.com/api): Developer API documentation

## Optional

- [Careers](https://example.com/careers): Open positions
- [Press Kit](https://example.com/press): Media resources
- [Terms of Service](https://example.com/terms)
- [Privacy Policy](https://example.com/privacy)
```

### Real-World Example

```markdown
# Acme Analytics

> Acme Analytics is an AI search visibility platform that helps brands
> track and optimize their presence across ChatGPT, Perplexity, Google
> AI Overviews, and 20+ AI search engines.

## About

Founded in 2024, Acme Analytics provides real-time monitoring of how AI
engines cite, recommend, and describe brands. Used by 2,000+ companies
across 45 countries.

## Contact

- Website: https://acmeanalytics.com
- Email: hello@acmeanalytics.com
- Support: https://acmeanalytics.com/support
- Sales: sales@acmeanalytics.com

## Products

- [Visibility Tracker](https://acmeanalytics.com/tracker): Real-time AI citation monitoring across all major AI platforms
- [GEO Audit](https://acmeanalytics.com/audit): Automated GEO scoring with 50+ optimization factors
- [Brand Monitor](https://acmeanalytics.com/monitor): Track how AI describes your brand vs competitors

## Key Information

- [Documentation](https://acmeanalytics.com/docs): API docs and integration guides
- [Blog](https://acmeanalytics.com/blog): GEO strategies, case studies, and industry analysis
- [Case Studies](https://acmeanalytics.com/cases): Customer success stories with data
- [Pricing](https://acmeanalytics.com/pricing): Free trial, Pro ($99/mo), Enterprise (custom)
```

### Writing Rules

1. The `> blockquote` summary is the single most important element — AI models use it as the primary brand description. Write it as a factual, self-contained statement.
2. Keep descriptions factual. AVOID marketing superlatives ("world's best", "industry-leading", "#1 platform").
3. Every linked page should have a one-line description that accurately reflects its content.
4. Use the SAME brand description here as in your Organization schema and meta description (see [authority-building.md](./authority-building.md)).
5. Update the file whenever products, services, or key pages change.

### Implementation Checklist

```
- [ ] Create /llms.txt at domain root
- [ ] Write factual blockquote summary (matches Organization schema description)
- [ ] Link to all key pages with one-line descriptions
- [ ] Verify file is accessible at https://yoursite.com/llms.txt
- [ ] Reference in sitemap or homepage <head>: <link rel="llms-txt" href="/llms.txt">
```

### Extended Format: llms-full.txt

For larger sites, provide a detailed version at `/llms-full.txt` containing full page content, detailed product descriptions, and complete documentation — giving AI models richer context for accurate responses.
