---
name: ai-search-engines
description: Platform-specific technical differences and implementation directives for each AI search engine
metadata:
  tags: chatgpt, perplexity, gemini, ai-overviews, copilot, platform-specific
---

## AI Search Engine Platform Differences

Each AI search platform crawls, indexes, and cites sources differently. When optimizing a site, apply these platform-specific implementation rules.

### Crawler-to-Platform Mapping

| Crawler User-Agent | Platform | How It Uses Your Content |
|---------------------|----------|--------------------------|
| `GPTBot` | ChatGPT Search | Fetches pages in real-time to generate cited answers |
| `OAI-SearchBot` | ChatGPT Search | Dedicated search crawler for ChatGPT |
| `ChatGPT-User` | ChatGPT | User-initiated "browse" mode fetches |
| `ClaudeBot` | Claude | Real-time web search when user enables it |
| `PerplexityBot` | Perplexity | Continuous crawling + real-time fetch for answer generation |
| `Google-Extended` | AI Overviews, Gemini | Controls whether content is used in Google's AI features (separate from Googlebot) |
| `Applebot-Extended` | Siri, Apple Intelligence | Controls AI feature usage (separate from Applebot) |
| `Bingbot` | Copilot, Bing Chat | Bing index powers Microsoft Copilot answers |

### ChatGPT Search — Implementation Rules

ChatGPT extracts concise passages and cites them with a link. Optimize for extraction:

1. **robots.txt**: Allow `GPTBot`, `OAI-SearchBot`, and `ChatGPT-User`
2. **Content structure**: Place a self-contained 1-3 sentence answer immediately after each `<h2>` heading
3. **FAQ sections**: ChatGPT heavily favors Q&A-formatted content — use `FAQPage` schema
4. **Freshness**: ChatGPT Search strongly prefers pages with recent `dateModified` — update content regularly and reflect it in schema
5. **SSR required**: GPTBot does NOT execute JavaScript — content must be in the initial HTML response

### Perplexity — Implementation Rules

Perplexity shows inline source attributions and strongly favors authoritative domains:

1. **robots.txt**: Allow `PerplexityBot`
2. **Authority signals**: Perplexity weights domain authority heavily — ensure strong E-E-A-T markup (see [eeat-optimization.md](./eeat-optimization.md))
3. **Factual density**: Include specific numbers, dates, and named sources — Perplexity extracts and attributes individual facts
4. **Original data**: First-party research and unique datasets get prioritized over content that aggregates others' data
5. **Topical completeness**: Cover the full scope of a topic on a single page rather than splitting across multiple thin pages

### Google AI Overviews — Implementation Rules

Google AI Overviews pull from pages already ranking in traditional Google Search:

1. **robots.txt**: Allow `Google-Extended` (separate from `Googlebot` which controls traditional search)
2. **Traditional SEO still applies**: Pages must rank well in regular Google results to appear in AI Overviews
3. **Schema.org is critical**: Implement `Article`, `FAQPage`, `HowTo` schemas — Google AI features rely heavily on structured data
4. **Featured Snippet format**: Content that wins Featured Snippets is more likely to be used in AI Overviews — use the definition-first paragraph pattern
5. **Google Business Profile**: For local queries, a complete and verified Google Business Profile is essential

### Microsoft Copilot — Implementation Rules

Copilot answers are powered by the Bing index:

1. **robots.txt**: Allow `Bingbot`
2. **IndexNow**: Implement the IndexNow protocol for instant indexing of new/updated content:

```html
<!-- Submit URL to IndexNow -->
<link rel="indexnow" href="https://api.indexnow.org/indexnow?url=https://yourbrand.com/new-page&key=YOUR_KEY">
```

3. **Bing Webmaster Tools**: Submit and verify your site for better Bing indexing
4. **Meta descriptions**: Bing/Copilot weights meta descriptions more than Google — write clear, factual meta descriptions

### Claude — Implementation Rules

1. **robots.txt**: Allow `ClaudeBot`
2. **Long-form depth**: Claude's web search tends to favor comprehensive, well-structured long-form content
3. **Accuracy**: Claude applies strict factual verification — ensure all claims are sourced and current
4. **SSR required**: ClaudeBot does NOT execute JavaScript

### Multi-Platform Priority

When time and resources are limited, prioritize in this order:

```
1. ChatGPT Search + Google AI Overviews  — largest reach
2. Perplexity                            — fastest growing, strong attribution
3. Copilot + Claude                      — significant user bases
4. Others (Grok, DeepSeek, etc.)         — niche or emerging
```

### Cross-Platform Consistency Rule

AI engines cross-reference information from multiple sources. Inconsistencies reduce trust:

- Use the SAME brand name, description, and facts everywhere
- Keep `dateModified` in schema accurate — if platforms see conflicting dates, they may distrust the content
- Ensure `author` schema `sameAs` links resolve correctly to real, active profiles
