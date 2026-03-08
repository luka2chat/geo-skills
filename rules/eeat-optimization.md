---
name: eeat-optimization
description: E-E-A-T implementation patterns for AI search - markup, content signals, and YMYL rules
metadata:
  tags: eeat, authority, trust, expertise, experience, schema
---

## E-E-A-T for Generative Engine Optimization

AI search engines evaluate E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness) signals even more aggressively than traditional search. AI models must decide which sources to cite in a single generated answer — they strongly favor content that demonstrates credibility.

### E-E-A-T Implementation Matrix

| Element | What AI Looks For | How to Implement |
|---------|-------------------|------------------|
| **Experience** | First-hand results, specific data, "we tested this" language | Include concrete metrics from real implementations in content |
| **Expertise** | Author credentials, professional background | Author schema with `jobTitle`, `alumniOf`, `sameAs` links |
| **Authoritativeness** | Third-party references, cross-platform entity presence | `sameAs` links to Wikipedia/Wikidata, consistent brand entity (see [authority-building.md](./authority-building.md)) |
| **Trustworthiness** | HTTPS, accurate facts, transparent sourcing, update dates | `dateModified` in schema, clear citations, editorial policy page |

### Experience — Content Patterns

AI models recognize and prefer content from authors with demonstrable first-hand experience. When writing or restructuring content, use these patterns:

```markdown
GOOD — Demonstrates real experience:

## Our GEO Implementation Results

After implementing GEO strategies across 150 client websites over 12 months,
we observed an average 340% increase in AI citation rates. Here's exactly
what we did and what worked:

- **Structured data implementation**: +85% citation rate improvement
- **llms.txt deployment**: +24% brand description accuracy
- **Content restructuring for quotability**: +120% snippet extraction rate


BAD — Generic advice without experience:

## How to Do GEO

GEO is important for your business. You should implement structured data
and optimize your content. Many companies see good results from GEO.
```

### Expertise — Author Markup

Every content page MUST include author schema that establishes expertise:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "author": {
    "@type": "Person",
    "name": "Jane Smith",
    "jobTitle": "Senior GEO Strategist",
    "url": "https://yourbrand.com/team/jane-smith",
    "alumniOf": {
      "@type": "CollegeOrUniversity",
      "name": "MIT"
    },
    "sameAs": [
      "https://linkedin.com/in/janesmith",
      "https://twitter.com/janesmith"
    ]
  }
}
</script>
```

Required author fields for GEO:
- `name` — full real name (never "Admin" or "Staff Writer")
- `jobTitle` — specific professional title
- `url` — link to a dedicated author bio page on the same domain
- `sameAs` — at least one verifiable external profile (LinkedIn preferred)

### Trustworthiness — Page-Level Signals

Implement these trust signals on every content page:

```html
<!-- 1. Accurate dateModified in schema (MUST match actual last edit) -->
"dateModified": "2026-03-01"

<!-- 2. Visible "Last updated" date in content -->
<p class="last-updated">Last updated: <time datetime="2026-03-01">March 1, 2026</time></p>

<!-- 3. Source citations within content -->
<p>According to <a href="https://backlinko.com/llm-traffic-study">Backlinko's 2025 analysis</a>,
website traffic from LLMs increased 800% year-over-year.</p>

<!-- 4. HTTPS (non-negotiable) -->
<!-- 5. Link to editorial/correction policy -->
<footer>
  <a href="/editorial-policy">Editorial Policy</a> |
  <a href="/corrections">Corrections</a>
</footer>
```

### YMYL (Your Money or Your Life) Rules

For content in sensitive categories, AI engines apply stricter E-E-A-T requirements. When generating YMYL content, ALWAYS include:

| Category | Required Author Signals | Required Content Signals |
|----------|------------------------|--------------------------|
| **Health/Medical** | `jobTitle`: licensed medical professional (MD, RN, etc.) | Cite peer-reviewed sources; add `reviewedBy` schema |
| **Financial** | `jobTitle`: certified credential (CFA, CPA, CFP) | Regulatory disclaimers; cite official data sources |
| **Legal** | `jobTitle`: licensed attorney, bar membership | Jurisdiction disclaimers; cite statutes/case law |
| **Safety** | Expert credentials relevant to domain | Official guidelines referenced; safety warnings |

YMYL `reviewedBy` schema pattern:

```json
{
  "reviewedBy": {
    "@type": "Person",
    "name": "Dr. John Doe",
    "jobTitle": "Licensed Financial Advisor, CFA",
    "url": "https://yourbrand.com/team/john-doe"
  }
}
```

For YMYL content, AI engines will rarely cite sources that lack clear professional credentials. If the content author lacks relevant credentials, add a qualified reviewer and use the `reviewedBy` field.
