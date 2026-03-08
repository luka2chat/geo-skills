---
name: ai-crawler-config
description: robots.txt configuration for AI search engine crawlers
metadata:
  tags: robots-txt, crawlers, gptbot, claudebot, perplexitybot, ai-indexing
---

## AI Crawler Configuration

Configuring robots.txt correctly is critical for AI search visibility. Unlike traditional search crawlers (Googlebot, Bingbot), AI crawlers are used by LLMs to fetch real-time information and build their knowledge base.

### Recommended robots.txt Configuration

```robots.txt
# ==============================================
# AI Search Crawlers (affect real-time AI responses)
# ==============================================

# OpenAI - ChatGPT Search & real-time web browsing
User-agent: GPTBot
Allow: /

# OpenAI - ChatGPT Search specifically
User-agent: OAI-SearchBot
Allow: /

# OpenAI - ChatGPT user-initiated browsing
User-agent: ChatGPT-User
Allow: /

# Anthropic - Claude web search
User-agent: ClaudeBot
Allow: /

# Perplexity AI - answer engine
User-agent: PerplexityBot
Allow: /

# Google - AI features (AI Overviews, Gemini)
User-agent: Google-Extended
Allow: /

# Apple - Siri and Apple Intelligence
User-agent: Applebot-Extended
Allow: /

# Microsoft - Copilot and Bing Chat
User-agent: Bingbot
Allow: /

# ==============================================
# AI Training Crawlers (affect future model knowledge)
# ==============================================

# Common Crawl - used by many AI training datasets
User-agent: CCBot
Allow: /

# Anthropic - training data collection
User-agent: anthropic-ai
Allow: /

# ByteDance - AI training
User-agent: Bytespider
Allow: /

# Meta - AI training
User-agent: FacebookBot
Allow: /

# ==============================================
# Standard crawlers
# ==============================================

User-agent: Googlebot
Allow: /

User-agent: *
Allow: /

# Sitemap reference
Sitemap: https://example.com/sitemap.xml
```

### Crawler Reference Table

| Crawler | Operator | Purpose | Impact |
|---------|----------|---------|--------|
| `GPTBot` | OpenAI | ChatGPT web browsing | Direct: affects ChatGPT citations |
| `OAI-SearchBot` | OpenAI | ChatGPT Search feature | Direct: affects ChatGPT Search results |
| `ChatGPT-User` | OpenAI | User-initiated web browsing | Direct: affects browse-mode answers |
| `ClaudeBot` | Anthropic | Claude web search | Direct: affects Claude citations |
| `PerplexityBot` | Perplexity | Answer engine crawling | Direct: affects Perplexity citations |
| `Google-Extended` | Google | AI Overviews, Gemini | Direct: affects Google AI features |
| `Applebot-Extended` | Apple | Siri, Apple Intelligence | Direct: affects Apple AI features |
| `CCBot` | Common Crawl | Open web archive | Indirect: training data for many models |
| `anthropic-ai` | Anthropic | Training data | Indirect: future Claude knowledge |
| `Bytespider` | ByteDance | Training data | Indirect: future model knowledge |

### Selective Blocking Strategy

If you want to allow AI search citations but prevent your content from being used for training:

```robots.txt
# Allow real-time AI search (you get cited)
User-agent: GPTBot
Allow: /

User-agent: OAI-SearchBot
Allow: /

User-agent: ChatGPT-User
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /

# Block training-only crawlers (your content isn't used for training)
User-agent: CCBot
Disallow: /

User-agent: anthropic-ai
Disallow: /

User-agent: Bytespider
Disallow: /
```

### Important Notes

1. **Blocking GPTBot blocks ChatGPT Search entirely** — your content won't appear in any ChatGPT responses that use web browsing
2. **Google-Extended only controls AI features**, not traditional Google Search (that's Googlebot)
3. **robots.txt is advisory, not enforced** — reputable AI companies respect it, but not all crawlers do
4. **Changes take effect gradually** — after updating robots.txt, it may take days to weeks for AI engines to reflect the change
5. Always test your robots.txt at `https://yoursite.com/robots.txt` to ensure it's accessible
