---
name: ai-seo-skill
description: >
  Traditional SEO optimization across 13 disciplines. Covers search engine optimization,
  answer engine optimization (AEO), entity SEO, semantic SEO, voice search, social search,
  video SEO, AI local SEO, visual search, Google AI Overviews, app store optimization (ASO),
  podcast search, and marketplace search (Amazon, Walmart). Keyword research, technical SEO,
  featured snippets, Knowledge Graph, schema markup, GBP optimization, YouTube SEO,
  Google Lens, site speed, backlinks, content strategy, topic clusters, local citations.
---

# AI SEO Skill: 13-Discipline Traditional Search Optimization

Comprehensive search engine optimization covering every traditional discovery surface.
From Google organic rankings to Amazon product search, this skill provides frameworks,
checklists, and implementation guidance for 13 interconnected SEO disciplines.

**Companion skill:** AI-specific optimization (GEO, LLMO, AIVO, CSO, AAIO, AI Shopping)
lives in `ai-search-optimization-skill`. Use both skills together for full-spectrum coverage.

---

## Step 1: Load Reference Guides

Before executing any task, load the relevant reference file(s) from `references/`.

| Task | Reference File(s) |
|------|--------------------|
| SEO audit, keyword research, technical SEO, backlinks | `seo-foundation.md` |
| Featured snippets, People Also Ask, answer capsules | `aeo-voice.md` |
| Voice search, conversational queries, speakable schema | `aeo-voice.md` |
| Knowledge Graph, Wikidata, entity markup | `entity-semantic.md` |
| Topic clusters, topical authority, semantic content | `entity-semantic.md` |
| Google Maps, Apple Maps, GBP, local citations | `ai-local-seo.md` |
| TikTok, Instagram, Pinterest, LinkedIn, YouTube search | `social-video-visual.md` |
| YouTube optimization, video chapters, transcripts | `social-video-visual.md` |
| Google Lens, Pinterest Lens, visual search | `social-video-visual.md`, `multimodal.md` |
| Google AI Overview optimization | `aaio-overviews.md` |
| App Store, Google Play optimization | `aso.md` |
| Apple Podcasts, Spotify, audio search | `podcast-audio.md` |
| Amazon A10/COSMO, Walmart AI, marketplace search | `marketplace.md` |
| Stats, benchmarks, citation data | `statistics.md` |
| Audit scorecards, plan templates, schema examples | `output-templates.md` |
| SEvO meta-framework (cross-discipline orchestration) | `sevo.md` |

**Always load `statistics.md`** when producing audits, reports, or client-facing content.
Stats must include source attribution.

---

## Step 2: Identify Business Context

Before recommending any optimization, establish:

1. **Business type:** Local service, SaaS/B2B, e-commerce, professional services, healthcare, media, hospitality, education
2. **Current organic performance:** Existing rankings, traffic, domain authority
3. **Target audience:** Demographics, search behavior, devices, platforms
4. **Competitive landscape:** Top 3 competitors, their strongest channels
5. **Content assets:** Existing blog, video, podcast, product listings
6. **Technical stack:** CMS, hosting, page speed baseline, mobile readiness
7. **Budget and timeline:** Resources available, priority horizon (30/60/90 days)

This context determines which disciplines to prioritize (see Step 4).

---

## Step 3: The 13 Disciplines

### Tier 1: Core (Every business needs these)

**1. SEO (Search Engine Optimization)**
Google and Bing organic rankings. Keywords, backlinks, technical SEO, site speed, mobile
optimization, Core Web Vitals. The foundation that all other disciplines build on.
Key stat: 87% of ChatGPT citations match pages already in Bing's top 10 organic results.

**2. AEO (Answer Engine Optimization)**
Featured snippets, People Also Ask, position zero, AI Overviews. Structure content with
answer capsules (40 to 60 words after every H2), FAQ schema, and HowTo schema. Direct
answers win the zero-click landscape.

**3. Entity SEO**
Google Knowledge Graph, Wikidata, structured entity recognition. Schema.org markup,
consistent NAP (Name, Address, Phone), entity disambiguation. Makes your brand a
machine-readable "thing" rather than just a string of text.

**4. Semantic SEO**
Topic clusters, entity-attribute-value content mapping, topical authority signals.
Build content hubs that demonstrate comprehensive expertise. Search engines reward
depth and interconnection over isolated keyword pages.

### Tier 2: High-Value Channels (Priority depends on business type)

**5. Voice Search Optimization**
Siri, Alexa, Google Assistant, smart speakers. Conversational long-tail keywords,
speakable schema, natural language Q&A formatting. Voice queries tend to be longer
and more question-based than typed searches.

**6. Social Search**
TikTok, Instagram, Pinterest, LinkedIn, YouTube as search engines. Caption keywords,
strategic hashtags, profile optimization, native content formats. Gen Z uses TikTok
and Instagram as primary search tools for discovery.

**7. Video SEO**
YouTube search, Google Video results, video carousels. Title optimization, chapter
timestamps with keyword anchors, transcript accuracy, thumbnail CTR. YouTube is the
world's second-largest search engine.

**8. AI Local SEO**
Google Maps, Apple Maps, Bing Places, ChatGPT local results. Google Business Profile
optimization, cross-platform citation consistency, review velocity and sentiment,
local schema markup. Critical for any business serving a geographic area.

**9. Visual Search**
Google Lens (12B+ searches per month), Pinterest Lens, visual discovery. Descriptive
alt text, ImageObject schema, high-quality product photography, visual similarity
optimization. Growing rapidly as camera-first search behavior increases.

### Tier 3: Specialized (Deploy when relevant to business model)

**10. AI Overview Optimization (Google-specific)**
Google's AI-generated summary boxes. Optimized answer blocks, targeting 8+ word
queries, passages of 134 to 167 words, high entity density. Distinct from general
AEO because it targets Google's specific AI summary algorithm.

**11. ASO (App Store Optimization)**
Apple App Store and Google Play search rankings. Keywords in title and subtitle,
screenshot A/B testing, rating management, conversion rate optimization on the
listing page. Essential for any business with a mobile app.

**12. Podcast/Audio Search**
Apple Podcasts, Spotify search, transcript indexing, RSS feed optimization.
Episode titles with target keywords, show notes with timestamps, structured
descriptions. Audio content is increasingly indexed by search engines.

**13. Marketplace Search**
Amazon A10/COSMO algorithm, Walmart AI search, Etsy, eBay. Backend keywords,
A+ content, sales velocity signals, review optimization. Each marketplace has
its own ranking algorithm distinct from Google.

---

## Step 4: Business Type Prioritization Matrix

Use this matrix to determine which disciplines to prioritize. Numbers indicate
recommended priority order (1 = highest).

| Discipline | Local Services | SaaS / B2B | E-Commerce | Professional Services | Healthcare | Media / Publishing | Hospitality / Travel | Education |
|------------|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| SEO | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| AEO | 3 | 2 | 4 | 2 | 2 | 2 | 3 | 2 |
| Entity SEO | 4 | 5 | 6 | 3 | 3 | 4 | 5 | 5 |
| Semantic SEO | 5 | 3 | 5 | 4 | 4 | 3 | 6 | 3 |
| Voice Search | 2 | 10 | 8 | 6 | 5 | 9 | 4 | 8 |
| Social Search | 7 | 7 | 3 | 8 | 8 | 5 | 2 | 6 |
| Video SEO | 8 | 6 | 7 | 7 | 7 | 6 | 7 | 4 |
| AI Local SEO | 2 | 11 | 9 | 5 | 6 | 12 | 2 | 9 |
| Visual Search | 10 | 12 | 2 | 11 | 10 | 8 | 8 | 11 |
| AI Overview Opt. | 6 | 4 | 10 | 9 | 9 | 7 | 10 | 7 |
| ASO | 11 | 8 | 11 | 12 | 11 | 10 | 9 | 10 |
| Podcast/Audio | 12 | 9 | 12 | 10 | 12 | 11 | 11 | 12 |
| Marketplace | 13 | 13 | 2 | 13 | 13 | 13 | 13 | 13 |

**How to read:** Start with priority 1, work down. Skip disciplines ranked 10+ unless
the client specifically requests them or resources allow.

---

## Step 5: Quick-Start Implementation

For any new engagement, follow this sequence:

### Week 1 to 2: Foundation
- [ ] Run technical SEO audit (Core Web Vitals, crawl errors, sitemap, robots.txt)
- [ ] Keyword research across primary and secondary disciplines
- [ ] Competitor gap analysis (top 3 competitors)
- [ ] Schema.org markup audit (Organization, LocalBusiness, Product as applicable)
- [ ] Google Business Profile audit (if local component exists)

### Week 3 to 4: Content Structure
- [ ] Map existing content to topic clusters
- [ ] Identify answer capsule opportunities (AEO)
- [ ] Add FAQ schema to top 10 pages by traffic
- [ ] Optimize meta titles and descriptions for CTR
- [ ] Create entity disambiguation page or About schema

### Month 2: Channel Expansion
- [ ] Deploy discipline-specific optimizations per priority matrix
- [ ] Build internal linking structure for topic clusters
- [ ] Launch video or social content strategy (if prioritized)
- [ ] Set up rank tracking across all active disciplines
- [ ] Implement structured data for all relevant content types

### Month 3: Measurement and Iteration
- [ ] Analyze ranking changes across all tracked disciplines
- [ ] Identify featured snippet wins and losses
- [ ] Review AI Overview appearances
- [ ] Adjust content strategy based on performance data
- [ ] Plan next quarter's expansion into lower-priority disciplines

---

## Step 6: Content Optimization Checklist

Apply to every piece of content before publishing:

### On-Page SEO
- [ ] Primary keyword in title tag (front-loaded)
- [ ] Primary keyword in H1
- [ ] Semantic variations in H2s and H3s
- [ ] Meta description includes keyword and CTA (under 160 chars)
- [ ] URL slug is short, descriptive, keyword-rich
- [ ] Internal links to 3+ related pages
- [ ] External links to 1 to 2 authoritative sources

### AEO Layer
- [ ] Answer capsule (40 to 60 words) after every H2
- [ ] At least one definition or "What is..." section
- [ ] FAQ section with 3 to 5 questions (FAQ schema applied)
- [ ] Lists and tables for scannable data points

### Entity and Semantic Layer
- [ ] Schema.org markup (Article, FAQPage, HowTo, or relevant type)
- [ ] Entity mentions are consistent (same name format throughout)
- [ ] Topic cluster interlinks connect to pillar page
- [ ] Content covers subtopics identified in semantic gap analysis

### Technical
- [ ] Page loads under 2.5s (LCP)
- [ ] Mobile-responsive layout verified
- [ ] Images have descriptive alt text (Visual Search ready)
- [ ] Open Graph and Twitter Card meta tags present
- [ ] Canonical URL set correctly

---

## Step 7: Output Formats

Load `output-templates.md` for full templates. Available formats:

| Output | Use Case |
|--------|----------|
| **SEO Audit Scorecard** | Baseline assessment across all 13 disciplines. Scored 0 to 100. |
| **Discipline Deep-Dive** | Detailed analysis and recommendations for a single discipline. |
| **90-Day Optimization Plan** | Prioritized roadmap with weekly milestones. |
| **Content Brief** | Single-page optimization guide for writers. Includes keywords, structure, schema. |
| **Schema Markup Package** | Ready-to-implement JSON-LD for identified schema opportunities. |
| **Competitive Gap Report** | Side-by-side comparison against top competitors per discipline. |
| **Monthly Performance Report** | Tracking template for rankings, traffic, and featured snippet wins. |

---

## Acronym Quick Reference

| Acronym | Full Name | Discipline # |
|---------|-----------|:------------:|
| SEO | Search Engine Optimization | 1 |
| AEO | Answer Engine Optimization | 2 |
| NAP | Name, Address, Phone (Entity SEO) | 3 |
| E-A-V | Entity-Attribute-Value (Semantic SEO) | 4 |
| GBP | Google Business Profile (AI Local SEO) | 8 |
| LCP | Largest Contentful Paint (Technical SEO) | 1 |
| ASO | App Store Optimization | 11 |
| A10 | Amazon's ranking algorithm | 13 |
| COSMO | Amazon's AI ranking system | 13 |
| SEvO | Search Everywhere Optimization (meta-framework) | All |
| CWV | Core Web Vitals | 1 |
| CTR | Click-Through Rate | 1 |
| SERP | Search Engine Results Page | 1 |
| PAA | People Also Ask | 2 |

**Companion skill for AI-native search:** `ai-search-optimization-skill` covers GEO
(Generative Engine Optimization), LLMO (LLM Optimization), AIVO (AI Voice Optimization),
CSO (Conversational Search Optimization), AAIO (AI Agent & Infrastructure Optimization),
and AI Shopping Optimization.
