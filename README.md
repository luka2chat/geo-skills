# geo-best-practices

Production-grade best practices for **Generative Engine Optimization (GEO)** — everything you need to optimize content for AI-powered search engines and LLM-based answer engines.

<p align="center">
  <a href="https://skills.sh/luka2chat/geo-skills/geo-best-practices"><img src="https://img.shields.io/badge/skills.sh-geo--best--practices-blue" alt="skills.sh"></a>
  <img src="https://img.shields.io/github/license/luka2chat/geo-skills" alt="License">
  <img src="https://img.shields.io/badge/rules-12-green" alt="Rules">
</p>

## Install

```bash
npx skills add luka2chat/geo-skills
```

Or install from the full GitHub URL:

```bash
npx skills add https://github.com/luka2chat/geo-skills
```

Supports Cursor, Claude Code, Codex, OpenCode, Gemini CLI, GitHub Copilot, and [37+ AI agents](https://github.com/vercel-labs/skills#supported-agents).

## Why This Skill?

AI search traffic is growing **357% YoY**, and AI visitors convert at **4.4x** the rate of traditional organic search. This skill gives your AI coding agent the domain knowledge to implement GEO correctly — from Schema.org markup to robots.txt crawler rules to content structure patterns that AI engines actually cite.

Every rule is **actionable**: code templates, configuration files, checklists, and implementation patterns. No tool recommendations or SaaS listings — only what an AI agent can directly execute.

## What's Included

12 rule files covering the full GEO stack:

### Content & Strategy
| Rule | What It Covers |
|------|----------------|
| [Content Strategy](./rules/content-strategy.md) | The 4 pillars: authority, quotability, comprehensiveness, structure — with good/bad examples |
| [Content Types](./rules/content-types.md) | Which formats earn AI citations, "chunkable" writing rules, length guidelines |
| [Brand Mentions](./rules/brand-mentions.md) | Buyer journey optimization, mention frequency & sentiment, emerging brand strategies |

### Technical Implementation
| Rule | What It Covers |
|------|----------------|
| [Technical Optimization](./rules/technical-optimization.md) | FAST framework, SSR code examples, semantic HTML, Core Web Vitals, 3-step readiness plan |
| [Structured Data](./rules/structured-data.md) | JSON-LD templates for Article, FAQ, Organization, Product, HowTo schemas |
| [AI Crawler Config](./rules/ai-crawler-config.md) | Complete robots.txt with all AI crawlers, selective blocking strategy |
| [llms.txt](./rules/llms-txt.md) | Format spec, real-world example, implementation checklist |
| [Product Feed](./rules/product-feed.md) | XML feed format, Product schema, Google/Microsoft/ChatGPT submission |

### Authority & Trust
| Rule | What It Covers |
|------|----------------|
| [E-E-A-T Optimization](./rules/eeat-optimization.md) | Author markup, trust signals, YMYL rules with `reviewedBy` schema |
| [Authority Building](./rules/authority-building.md) | Brand entity markup, `sameAs` linking, description consistency, syndication rules |

### Platform & Analytics
| Rule | What It Covers |
|------|----------------|
| [AI Search Engines](./rules/ai-search-engines.md) | Platform-specific rules for ChatGPT, Perplexity, Google AI Overviews, Copilot, Claude |
| [Analytics & Monitoring](./rules/analytics-monitoring.md) | GA4 regex setup, citation patterns across LLMs, traffic share data, audit process |

## What is GEO?

**Generative Engine Optimization (GEO)** is an optimization strategy for improving content visibility in AI search engines. Unlike traditional SEO, GEO focuses on being **cited** and **recommended** by AI systems.

| | SEO | GEO |
|---|---|---|
| **Target** | Google, Bing | ChatGPT, Perplexity, Gemini, AI Overviews |
| **Focus** | Keywords, backlinks | Authority, quotability, factual accuracy |
| **Metrics** | Rankings, CTR | AI citation rate, brand mentions |
| **Content** | Web pages, blogs | In-depth, data-backed, structured content |

## Resources

Based on the [Awesome GEO](https://github.com/luka2chat/awesome-geo) curated resource list — 120+ GEO resources including research papers, tools, strategies, and case studies.

## License

MIT
