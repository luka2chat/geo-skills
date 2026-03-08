---
name: technical-optimization
description: Technical GEO checklist including page speed, semantic HTML, SSR, and mobile optimization
metadata:
  tags: technical, seo, performance, semantic-html, ssr, mobile
---

## Technical GEO Requirements

Technical optimization ensures AI crawlers can access, parse, and understand your content. These are prerequisites — without them, even the best content won't be cited.

### Technical GEO Checklist

- [ ] Implement Schema.org structured data (see [structured-data.md](./structured-data.md))
- [ ] Optimize page load speed (Core Web Vitals passing)
- [ ] Ensure mobile-friendliness (responsive design)
- [ ] Use semantic HTML throughout
- [ ] Create and submit XML sitemap
- [ ] Configure robots.txt to allow AI crawlers (see [ai-crawler-config.md](./ai-crawler-config.md))
- [ ] Create llms.txt for structured AI-readable site information (see [llms-txt.md](./llms-txt.md))
- [ ] Implement HTTPS across the entire site
- [ ] Optimize all image alt text with descriptive, contextual descriptions
- [ ] Enable server-side rendering (SSR) for AI crawler accessibility
- [ ] Ensure clean, crawlable URL structure
- [ ] Implement canonical URLs to prevent duplicate content issues

### Semantic HTML

AI crawlers rely on HTML semantics to understand content hierarchy and meaning. Always use semantic elements:

```html
<!-- GOOD: Semantic HTML that AI crawlers understand -->
<article>
  <header>
    <h1>Complete Guide to Generative Engine Optimization</h1>
    <p>By <span itemprop="author">Jane Smith</span></p>
    <time datetime="2026-03-01">March 1, 2026</time>
  </header>

  <section>
    <h2>What is GEO?</h2>
    <p>Generative Engine Optimization (GEO) is an optimization strategy...</p>

    <h3>Key Benefits</h3>
    <ul>
      <li>Increased visibility in AI search results</li>
      <li>Higher citation rates across LLM platforms</li>
    </ul>
  </section>

  <section>
    <h2>How to Implement GEO</h2>
    <ol>
      <li>Audit your current content for AI readability</li>
      <li>Implement structured data markup</li>
      <li>Optimize content structure and quotability</li>
    </ol>
  </section>
</article>

<!-- BAD: Div-soup with no semantic meaning -->
<div class="post">
  <div class="title">Complete Guide to GEO</div>
  <div class="content">
    <div class="section">
      <div class="heading">What is GEO?</div>
      <div class="text">Generative Engine Optimization...</div>
    </div>
  </div>
</div>
```

### Server-Side Rendering (SSR)

Many AI crawlers do NOT execute JavaScript. Content rendered only via client-side JavaScript will be invisible to:

- GPTBot (OpenAI)
- ClaudeBot (Anthropic)
- PerplexityBot

Ensure critical content is available in the initial HTML response:

```javascript
// Next.js: Use SSR or SSG for content pages
// GOOD: Content is in the initial HTML
export async function getStaticProps() {
  const content = await fetchContent();
  return { props: { content }, revalidate: 3600 };
}

// BAD: Content loaded client-side only
export default function Page() {
  const [content, setContent] = useState(null);
  useEffect(() => {
    fetchContent().then(setContent);
  }, []);
  return <div>{content}</div>;
}
```

For SPAs (React, Vue, Angular), implement one of:
- **Static Site Generation (SSG)** — best for content that doesn't change often
- **Server-Side Rendering (SSR)** — best for dynamic content
- **Incremental Static Regeneration (ISR)** — best for frequently updated content at scale

### Page Speed Optimization

Faster pages are crawled more efficiently. Target these Core Web Vitals:

| Metric | Target | Impact on AI Crawling |
|--------|--------|----------------------|
| **LCP** (Largest Contentful Paint) | < 2.5s | Crawlers may timeout on slow pages |
| **FID** (First Input Delay) | < 100ms | Less direct impact on crawlers |
| **CLS** (Cumulative Layout Shift) | < 0.1 | Ensures content structure is stable |
| **TTFB** (Time to First Byte) | < 800ms | Critical for crawler efficiency |

### URL Structure

Clean URLs help AI engines categorize and reference content:

```
GOOD:
/guides/generative-engine-optimization
/blog/geo-vs-seo-comparison
/glossary/ai-search-terms

BAD:
/p?id=12345
/blog/2026/03/08/post
/content.php?category=seo&type=guide&id=789
```

### FAST Framework for AI Crawlability

Use the FAST framework to assess whether a page is ready for AI crawlers:

| Dimension | Question | Implementation |
|-----------|----------|----------------|
| **F — Fetchable** | Can AI retrieve and read your HTML without rendering JS? | Test pages with JavaScript disabled; ensure core content is in initial HTML; implement SSR/SSG |
| **A — Accessible** | Is key content understandable without executing scripts? | Include alt text on all images; use proper heading hierarchy (H1→H6); use semantic HTML5 elements |
| **S — Structured** | Are you using schema, semantic tags, and clear hierarchies? | Add Article/FAQ/Product schema; use definition boxes for key terms; implement content layers |
| **T — Trim** | Are you sending only what's needed, with no bloat? | Remove unnecessary tracking scripts; compress assets; minimize JS dependencies; reduce DOM size |

Quick test: load your top 20 pages with JavaScript disabled in your browser. What you see is approximately what AI crawlers see.

### 3-Step AI Search Readiness Plan

**Step 1 — Assessment:**
1. Test content extraction by viewing pages with JavaScript disabled
2. Audit your top 20 pages with HTML-only crawling
3. Check that all critical content is in the initial HTML response

**Step 2 — Quick Wins:**
1. Optimize page load times to under 2 seconds
2. Add FAQ schema to your most important content pages
3. Clean up robots.txt (see [ai-crawler-config.md](./ai-crawler-config.md)) and create/update llms.txt (see [llms-txt.md](./llms-txt.md))

**Step 3 — Structural Improvements:**
1. Add structured data for products, articles, and services (see [structured-data.md](./structured-data.md))
2. Create clear content hierarchies with semantic HTML
3. Implement server-side rendering for all critical content paths

### Advanced Technical GEO

- **Entity Resolution**: Clearly define and link entities within content. Use consistent naming, disambiguation, and link to authoritative sources for each entity (Wikipedia, official sites).
- **Semantic Trust Mechanisms**: Provide strong factual backing, cite peer-reviewed research, and demonstrate expertise. AI models assess intrinsic trustworthiness beyond backlinks.
- **RAG Adaptation**: Optimize content for Retrieval-Augmented Generation systems by creating modular content blocks, using clear headings and summaries, and ensuring key information is extractable for AI synthesis.
