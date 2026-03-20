---
name: ai-seo-skill
description: >
  Audit, plan, and execute traditional search engine optimization across 13 disciplines:
  SEO, AEO (answer engine optimization), Entity SEO, Semantic SEO, voice search, social search
  (TikTok, Instagram, Pinterest, LinkedIn), video SEO (YouTube), AI local SEO (Google Maps,
  Apple Maps), visual search (Google Lens), Google AI Overviews, ASO (app store optimization),
  podcast/audio search, and marketplace search (Amazon, Walmart). Use this skill whenever the
  user wants to improve search rankings, run an SEO audit, optimize for featured snippets,
  build topic clusters, fix technical SEO issues, improve local search visibility, optimize
  YouTube videos, create schema markup, research keywords, analyze competitors, or rank higher
  on any search platform. Also use when the user mentions Google rankings, Bing, SERP, backlinks,
  Core Web Vitals, page speed, meta tags, Knowledge Graph, or any specific search platform
  optimization. This skill covers traditional search engines and platforms. For AI-specific
  citation optimization (ChatGPT, Perplexity, Claude citations), use ai-search-optimization-skill.
---

# Traditional Search Optimization (13 Disciplines)

Optimize for every search surface where humans type, speak, or point a camera to find things.

## Scope

**This skill:** Google, Bing, YouTube, TikTok, Instagram, Pinterest, LinkedIn, Apple Maps, Google Maps, Google Lens, App Stores, Spotify, Amazon, Walmart.

**Companion skill:** `ai-search-optimization-skill` handles AI citation optimization (GEO, LLMO, AIVO). Use both for full coverage.

## Reference Files

Load only the 1 to 2 files from `references/` most relevant to the user's specific question. Do not load all files. This keeps responses focused and avoids unnecessary token usage.

| Need | Load |
|------|------|
| Technical SEO, keywords, backlinks, site speed | `references/seo-foundation.md` |
| Featured snippets, answer capsules, People Also Ask | `references/aeo-voice.md` |
| Voice search, speakable schema, smart speakers | `references/aeo-voice.md` |
| Knowledge Graph, Wikidata, entity markup | `references/entity-semantic.md` |
| Topic clusters, topical authority, semantic gaps | `references/entity-semantic.md` |
| Google Maps, Apple Maps, GBP, local citations | `references/ai-local-seo.md` |
| TikTok, Instagram, Pinterest, LinkedIn search | `references/social-video-visual.md` |
| YouTube optimization, video chapters, thumbnails | `references/social-video-visual.md` |
| Google Lens, Pinterest Lens, image search | `references/multimodal.md` |
| Google AI Overviews, AI-generated summaries | `references/aaio-overviews.md` |
| App Store, Google Play search rankings | `references/aso.md` |
| Apple Podcasts, Spotify, audio indexing | `references/podcast-audio.md` |
| Amazon, Walmart, marketplace algorithms | `references/marketplace.md` |
| Statistics with sources (for audits and reports) | `references/statistics.md` |
| Audit scorecards, plan templates, schema code | `references/output-templates.md` |
| SEvO meta-framework (full audit only) | `references/sevo.md` |

Only load `references/statistics.md` when producing audits, reports, or client-facing content that needs sourced data. Only load `references/output-templates.md` when the user explicitly requests a deliverable format.

## The 13 Disciplines

### Tier 1: Core

1. **SEO** -- Google/Bing organic. Keywords, backlinks, technical health, Core Web Vitals, mobile. The foundation everything else builds on. 87% of ChatGPT citations match Bing's top 10.

2. **AEO** -- Featured snippets, People Also Ask, position zero. Answer capsules (40 to 60 words after each H2), FAQ schema, HowTo schema. Win the zero-click results.

3. **Entity SEO** -- Knowledge Graph, Wikidata, structured data. Make your brand a recognized entity, not just text. Schema.org Organization/Person/LocalBusiness markup, consistent NAP.

4. **Semantic SEO** -- Topic clusters, topical authority, entity-attribute-value mapping. Search engines reward interconnected depth over isolated keyword pages.

### Tier 2: Channels

5. **Voice Search** -- Siri, Alexa, Google Assistant. Conversational long-tail keywords, speakable schema, concise 1 to 2 sentence answers. 50%+ of searches are voice.

6. **Social Search** -- TikTok, Instagram, Pinterest, LinkedIn as search engines. Caption keywords, hashtags, native formats. 64% of Gen Z use TikTok to search.

7. **Video SEO** -- YouTube, Google Video results. Title optimization, chapter timestamps, transcript accuracy, thumbnail CTR. World's second-largest search engine.

8. **AI Local SEO** -- Google Maps, Apple Maps, Bing Places, ChatGPT local. GBP optimization, cross-platform citations, review velocity. Critical for any geographic business.

9. **Visual Search** -- Google Lens (12B+ monthly searches), Pinterest Lens. Descriptive alt text, ImageObject schema, product photography.

### Tier 3: Specialized

10. **AI Overview Optimization** -- Google's AI summary boxes. 8+ word queries, 134 to 167 word passages, entity density 15 to 20 per 1,000 words.

11. **ASO** -- Apple App Store, Google Play. Keywords in title/subtitle, screenshot A/B testing, rating velocity. 65% of downloads come from search.

12. **Podcast/Audio Search** -- Apple Podcasts, Spotify, transcript indexing, RSS optimization. Audio is increasingly indexed.

13. **Marketplace Search** -- Amazon A10/COSMO, Walmart AI. Backend keywords, A+ content, review velocity. Each marketplace has its own algorithm.

## Prioritization by Business Type

Ask or determine: What type of business? Then focus on the disciplines that matter most.

| Business Type | Start With | Then Add | Lower Priority |
|---------------|-----------|----------|---------------|
| Local Services (dental, HVAC) | SEO, AI Local SEO, Voice Search | AEO, Entity SEO | Social, Video, ASO |
| SaaS / B2B | SEO, AEO, Semantic SEO | AI Overviews, Entity SEO, Video | Voice, ASO, Marketplace |
| E-Commerce / DTC | SEO, Visual Search, Marketplace | Social Search, Video SEO | Voice, ASO, Podcast |
| Professional Services | SEO, AEO, Entity SEO, Semantic | Video SEO, AI Overviews | Social, ASO, Marketplace |
| Healthcare | SEO, AI Local SEO, AEO | Voice Search, Entity SEO | Social, ASO, Marketplace |
| Media / Publishing | SEO, AEO, Semantic SEO | Social Search, Video SEO | ASO, Marketplace, Voice |
| Hospitality / Travel | SEO, AI Local SEO, Social | Voice Search, Visual Search | ASO, Podcast, Marketplace |
| Education | SEO, AEO, Semantic SEO | Video SEO, Entity SEO | ASO, Marketplace, Podcast |

## Implementation Sequence

### Weeks 1 to 2: Foundation
- Technical SEO audit (crawl errors, CWV, sitemap, robots.txt)
- Keyword research for primary disciplines
- Competitor gap analysis (top 3 competitors)
- Schema.org audit (Organization, LocalBusiness, Product as needed)
- GBP audit if local component exists

### Weeks 3 to 4: Content Structure
- Map content to topic clusters (Semantic SEO)
- Add answer capsules to top pages (AEO)
- FAQ schema on top 10 pages by traffic
- Optimize titles and meta descriptions
- Entity disambiguation page or About schema

### Month 2: Channel Expansion
- Deploy channel-specific optimizations per priority table
- Internal linking for topic clusters
- Launch video or social strategy if prioritized
- Structured data for all content types
- Rank tracking across active disciplines

### Month 3: Measure and Iterate
- Analyze ranking changes
- Review featured snippet wins/losses
- Check AI Overview appearances
- Adjust strategy based on data
- Plan next quarter's expansion

## Content Optimization Checklist

Apply to every page:

**On-Page SEO:**
- Primary keyword in title (front-loaded), H1, URL slug
- Semantic variations in H2s and H3s
- Meta description with keyword and CTA (under 160 chars)
- 3+ internal links, 1 to 2 external authority links

**AEO Layer:**
- Answer capsule (40 to 60 words) after every H2
- "What is..." or definition section
- FAQ section with 3 to 5 questions + FAQ schema
- Lists and tables for scannable data

**Entity and Semantic:**
- Schema.org markup (Article, FAQPage, HowTo, or relevant type)
- Consistent entity naming throughout
- Topic cluster interlinks to pillar page

**Technical:**
- LCP under 2.5s
- Mobile-responsive
- Images have descriptive alt text
- Open Graph and Twitter Card meta tags
- Canonical URL set

## Output Formats

| Output | When |
|--------|------|
| SEO Audit Scorecard | Baseline assessment, scored per discipline |
| Discipline Deep-Dive | Single-discipline analysis with recommendations |
| 90-Day Plan | Prioritized roadmap with weekly milestones |
| Content Brief | Page-level optimization guide for writers |
| Schema Markup Package | Ready-to-implement JSON-LD |
| Competitive Gap Report | Side-by-side per discipline |
| Monthly Performance Report | Rankings, traffic, snippet tracking |

Load `references/output-templates.md` for full templates.
