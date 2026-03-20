# AEO and Voice Search Optimization: Implementation Reference

> Actionable implementation knowledge for Answer Engine Optimization (AEO) and Voice Search Optimization. Every section includes specifications, code, and measurement guidance.

---

## AEO Implementation

### Featured Snippet Types and How to Win Each

#### 1. Paragraph Snippets (82% of All Snippets)

**Target format:** 40 to 60 words, direct answer.

**Winning structure:**
- Open with "[Subject] is..." or "The [answer] is..."
- Follow with one clarifying sentence
- Close with outcome or application

**Example:**
```
Answer Engine Optimization (AEO) is the practice of structuring web content
so that AI assistants, voice devices, and search engines can extract direct
answers. It applies to any business that depends on organic discovery.
When done well, AEO increases zero-click visibility and drives qualified
traffic from AI-powered search surfaces.
```

**Technical requirements:**
- Place the answer capsule immediately after the H2 heading (no images, no ads between heading and answer)
- Use `<p>` tags, not `<div>` or `<span>`, for the answer paragraph
- Flesch-Kincaid reading level: Grade 8 or lower
- Subject-Verb-Object sentence structure for clean extraction
- Avoid pronouns in the first sentence (search engines lose referent context)

**Query triggers:** "What is," "What does," "Define," "Meaning of," "Why is"

---

#### 2. List Snippets (Ordered and Unordered)

**Ordered lists** win for process, ranking, and sequence queries ("steps to," "best," "top").
**Unordered lists** win for feature, type, and category queries ("types of," "examples of," "ways to").

**Winning structure:**
- H2 heading phrased as the query (e.g., "How to Optimize for Voice Search")
- 5 to 8 list items (Google truncates beyond 8 and adds "More items...")
- Each item: 1 to 2 sentences, 15 to 25 words
- Lead each item with a bolded keyword phrase

**HTML pattern:**
```html
<h2>How to Optimize for Voice Search</h2>
<ol>
  <li><strong>Add answer capsules</strong> below every H2, targeting 40 to 60 words per capsule.</li>
  <li><strong>Implement FAQPage schema</strong> on all pages containing question-and-answer pairs.</li>
  <li><strong>Target conversational keywords</strong> of 4 or more words that mirror natural speech.</li>
</ol>
```

**Query triggers:** "How to," "Steps to," "Best [plural noun]," "Top [number]," "Types of," "Ways to"

---

#### 3. Table Snippets

**Target format:** HTML `<table>` with clear `<th>` headers. 3 to 5 columns, 4 to 8 rows.

**Winning structure:**
- H2 heading with comparison or "vs" framing
- Clean semantic HTML table (no CSS-only tables, no divs pretending to be tables)
- First column: entity names. Remaining columns: attributes being compared.
- Sort rows by the most logical dimension (price, rating, alphabetical)

**HTML pattern:**
```html
<h2>AEO Tools Comparison: Pricing and Features</h2>
<table>
  <thead>
    <tr>
      <th>Tool</th>
      <th>Starting Price</th>
      <th>AI Platforms Tracked</th>
      <th>Best For</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Otterly.AI</td>
      <td>$29/mo</td>
      <td>ChatGPT, Gemini, Perplexity, Copilot</td>
      <td>SMBs and agencies</td>
    </tr>
  </tbody>
</table>
```

**Query triggers:** "[X] vs [Y]," "Compare," "Pricing," "Specifications," "[category] by [attribute]"

---

#### 4. Video Snippets

**Requirements:**
- Host on YouTube (Google owns it, priority extraction)
- Add `VideoObject` structured data with key moments / chapters
- Answer the target query within the first 30 seconds of the video
- Include a text transcript on the page (Google indexes transcript text)
- Thumbnail must be high contrast, 1280x720 minimum

**Schema:**
```json
{
  "@context": "https://schema.org",
  "@type": "VideoObject",
  "name": "How to Implement AEO for Your Website",
  "description": "Step-by-step guide to Answer Engine Optimization.",
  "thumbnailUrl": "https://example.com/thumb.jpg",
  "uploadDate": "2026-02-21",
  "duration": "PT5M30S",
  "hasPart": [
    {
      "@type": "Clip",
      "name": "What is AEO",
      "startOffset": 0,
      "endOffset": 30
    }
  ]
}
```

**Query triggers:** "How to [visual task]," "Tutorial," "Demo," "Review," "[product] unboxing"

---

#### 5. Double Snippets

Google sometimes displays two snippet types for the same query (paragraph + list, or paragraph + table).

**How to win:**
- Include both a paragraph answer capsule AND a list or table on the same page
- The paragraph goes immediately after the H2
- The list or table follows within the same section, before the next H2
- Both must directly answer the same query from different angles

---

### Answer Capsule Specifications

The answer capsule is the single most important on-page element for AEO. It is the text block that search engines and AI systems extract as the direct answer.

| Attribute | Specification |
|-----------|---------------|
| Length | 40 to 60 words (280 to 320 characters) |
| Placement | Immediately after every H2 heading |
| Reading level | Flesch-Kincaid Grade 8 or lower |
| Sentence structure | Subject-Verb-Object |
| First sentence | Direct answer (no preamble, no "In this article") |
| Second sentence | Who this applies to or qualifying context |
| Third sentence | Outcome, next step, or measurable benefit |

**Template:**
```
[Topic] is [direct definition or answer]. [Who this matters to] [use/need/benefit from]
this [when/why]. [Measurable outcome or actionable next step].
```

**Anti-patterns to avoid:**
- Starting with "In this article, we will discuss..."
- Using first person ("We believe," "Our team thinks")
- Embedding links inside the capsule text
- Including statistics without attribution
- Using jargon or acronyms without expansion

---

### People Also Ask (PAA) Optimization

**How PAA works:**
Google displays 4 initial PAA questions. Each click reveals 2 to 3 new related questions, creating an expanding tree. Pages that answer PAA questions earn additional SERP visibility even without ranking in the top 10.

**Research process:**
1. Enter seed keyword into AlsoAsked.com ($15+/mo)
2. Export the full PAA tree (can be 50 to 200+ questions per seed)
3. Group questions by intent cluster (informational, commercial, navigational)
4. Prioritize questions that appear across multiple seed keywords (high recurrence = high volume)

**On-page implementation:**
- Each PAA question becomes an H2 or H3 heading (exact match phrasing)
- Answer in 40 to 60 words directly below the heading
- Wrap in FAQPage schema (see Schema section below)
- Pages with question-format headings are 42% more likely to win snippets (Backlinko, 2024)

**PAA content architecture:**
- Hub page: covers the broad topic, links to spokes
- Spoke pages: each answers 5 to 8 related PAA questions in depth
- Internal links between hub and spokes create topical authority clusters

---

### Google AI Overviews (SGE / AIO)

AI Overviews are Google's AI-generated answer boxes that synthesize information from multiple sources. They are replacing traditional featured snippets for many query types.

**Key statistics:**
- AI Overviews now appear in 50%+ of searches
- Queries of 8+ words trigger AI Overviews at 7x the rate of shorter queries
- Featured snippets lost 64% visibility from January to June 2025 as AI Overviews replaced them
- 47% of AI Overview citations come from pages ranking below position 5
- AI Overviews synthesize from multiple sources (average 7.2 cited links), unlike snippets (single source)

**Ranking factors for AI Overview citation (correlation strength):**

| Factor | Correlation | Target |
|--------|-------------|--------|
| Semantic completeness | r=0.87 | Cover the full attribute space of the topic |
| Entity density | r=0.72 | 15 to 20 named entities per 1,000 words (4.8x higher selection rate) |
| Multi-modal content | r=0.68 | Text + images + schema yields 317% higher citation rate |
| Content freshness | r=0.61 | Content updated within 30 days earns 3.2x more citations |
| Passage structure | r=0.58 | 134 to 167 words per "semantic island" (self-contained passage) |

**Semantic completeness explained:**
AI Overviews prefer pages that cover every major attribute of a topic. For "best CRM software," this means covering pricing, features, integrations, ease of use, support, scalability, and deployment. Missing any major attribute reduces citation probability.

**Semantic island structure:**
A semantic island is a self-contained passage of 134 to 167 words that fully addresses one sub-aspect of the topic. Each island should:
- Begin with a clear topic sentence
- Include 2 to 3 named entities (people, products, companies, locations)
- End with a conclusion or transition
- Be separable from surrounding text without losing meaning

**Entity density guidelines:**
- Count named entities (proper nouns, product names, company names, location names, standard names)
- Target: 15 to 20 per 1,000 words
- Pages with high entity density are 4.8x more likely to be cited in AI Overviews
- Avoid keyword stuffing. Entities must be contextually relevant.

---

### llms.txt File Implementation

The `llms.txt` file is a plain-text Markdown file placed at the domain root that tells AI crawlers which pages contain authoritative content. Think of it as `robots.txt` for AI systems.

**File location:** `https://yoursite.com/llms.txt`

**Structure:**
```markdown
# Business Name

> One-paragraph description of the business, its expertise, and its target audience.

## Core Pages
- [Page Title](https://yoursite.com/page-1): Brief description of what this page covers
- [Page Title](https://yoursite.com/page-2): Brief description of what this page covers

## Key Topics We Cover
- Topic 1
- Topic 2
- Topic 3

## Optional: Docs
- [API Reference](https://yoursite.com/docs/api): Full API documentation
```

**Best practices:**
- Include 20 to 50 links maximum. Only highest-quality, regularly updated pages.
- Link to pages that demonstrate E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness)
- Update the file when new cornerstone content is published
- Do not include thin content, duplicate pages, or paginated archives

**Platform support:**
- Officially supported: Anthropic (Claude), Cursor, Mintlify
- Unofficially analyzed: OpenAI, Perplexity (no public announcement, but crawlers have been observed reading it)
- As of August 2025, only approximately 951 domains have published an llms.txt file. This is a significant early mover advantage.

**Companion file: llms-full.txt**
Some implementations include a longer version at `/llms-full.txt` with complete page content (not just links). This is useful for AI systems that prefer to ingest full text rather than crawl individual URLs.

---

### Schema Markup for AEO

Structured data helps search engines and AI systems understand content semantics. These are the highest-impact schema types for AEO.

#### FAQPage Schema

Use on any page with question-and-answer content. Each Q&A pair must be visible on the page (hidden content violates Google guidelines).

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is Answer Engine Optimization?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Answer Engine Optimization (AEO) is the practice of structuring content so AI assistants, voice devices, and search engines can extract direct answers. It targets featured snippets, AI Overviews, and voice search results."
      }
    },
    {
      "@type": "Question",
      "name": "How is AEO different from SEO?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "SEO optimizes for page rankings in search results. AEO optimizes for direct answer extraction by AI systems. SEO drives clicks. AEO drives visibility in zero-click environments like voice assistants, ChatGPT, and Google AI Overviews."
      }
    }
  ]
}
```

#### HowTo Schema

Use for process, tutorial, or instructional content. Each step must be visible on the page.

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "How to Implement AEO on Your Website",
  "description": "A step-by-step guide to optimizing your website for answer engines and AI search.",
  "totalTime": "PT2H",
  "step": [
    {
      "@type": "HowToStep",
      "name": "Audit existing content",
      "text": "Review your top 20 pages by traffic. Identify which ones already answer specific questions and which need answer capsules added.",
      "position": 1
    },
    {
      "@type": "HowToStep",
      "name": "Add answer capsules",
      "text": "Write 40 to 60 word direct answers and place them immediately after each H2 heading on your priority pages.",
      "position": 2
    }
  ]
}
```

#### Speakable Schema (For Voice Search)

Tells Google which parts of a page are suitable for text-to-speech playback. Currently supported for news publishers in the US. Broader adoption expected.

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "How AEO Changes Search Strategy in 2026",
  "speakable": {
    "@type": "SpeakableSpecification",
    "cssSelector": [".answer-capsule", ".key-takeaway"]
  },
  "url": "https://yoursite.com/aeo-guide"
}
```

**Implementation notes:**
- The `cssSelector` values must match actual CSS classes on the page
- Speakable content should follow the voice-friendly writing rules (see Voice Search section)
- Maximum 2 to 3 speakable sections per page
- Each speakable section: 20 to 30 seconds when read aloud (approximately 50 to 75 words)

#### Organization Schema with sameAs

Establishes entity identity across the web. Helps AI systems understand who you are.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Your Company Name",
  "url": "https://yoursite.com",
  "logo": "https://yoursite.com/logo.png",
  "sameAs": [
    "https://www.linkedin.com/company/yourcompany",
    "https://twitter.com/yourcompany",
    "https://www.youtube.com/@yourcompany"
  ],
  "knowsAbout": [
    "Answer Engine Optimization",
    "Voice Search",
    "AI Search Visibility"
  ]
}
```

---

### AEO Measurement Stack

#### Free Tools
| Tool | What It Measures | How to Use for AEO |
|------|-----------------|-------------------|
| Google Search Console | Query impressions, clicks, position | Filter by question queries (what, how, why, best). Track impressions with 0 clicks as a snippet/AIO signal. |
| Google Rich Results Test | Schema validation | Validate all structured data before pushing to production |
| Schema.org Validator | Schema syntax and compliance | Cross-check with Rich Results Test for completeness |
| Bing Webmaster Tools | Bing snippet and answer data | Submit sitemap. Bing powers Alexa, Cortana, and DuckDuckGo. |

#### Paid Tools
| Tool | Price | What It Measures |
|------|-------|-----------------|
| Semrush | $139+/mo | Featured snippet tracking, PAA data, position monitoring, content audit |
| Ahrefs | $129+/mo | Featured snippet ownership, content gap analysis, SERP feature tracking |
| AlsoAsked | $15+/mo | Full PAA tree mapping for any keyword |
| AnswerThePublic | $99/mo | Question wheel variations, preposition queries, comparison queries |
| Otterly.AI | $29 to $489/mo | Monitor ChatGPT, Google AI Overviews, Perplexity, Copilot, Gemini daily |
| Profound | $99 to $399/mo | Enterprise AI brand visibility tracking across multiple AI platforms |

#### Key Metrics to Track Monthly
1. **Featured snippet ownership count** (Semrush or Ahrefs)
2. **Zero-click impression rate** (GSC: impressions with 0 clicks on question queries)
3. **AI Overview citation count** (Otterly.AI or manual checks)
4. **Voice search answer rate** (manual testing on 20 priority queries per month)
5. **PAA presence count** (number of PAA boxes your domain appears in)
6. **Schema validation pass rate** (Rich Results Test, target 100%)
7. **Answer capsule coverage** (percentage of H2 headings with capsules, target 100% on priority pages)

---

## Voice Search Implementation

### How Voice Queries Differ from Typed

| Dimension | Voice Query | Typed Query |
|-----------|------------|-------------|
| Average length | 29 words | 3 to 4 words |
| Tone | Conversational ("Hey Siri, what is the best gym near me") | Keyword-focused ("best gym Toronto") |
| Local intent | 3x more likely to be local | Lower local intent ratio |
| Question format | 65 to 80% are conversational questions | 20 to 30% are questions |
| Overlap | Only 13.1% of voice queries are identical to text queries | N/A |

**Implication:** Optimizing for typed keywords alone misses 87% of voice query phrasing. Content must target natural language question patterns.

---

### Voice Search Ranking Factors (Ordered by Impact)

1. **Featured Snippet Ownership** (highest impact)
   - 40%+ of voice answers come from the featured snippet
   - Winning the snippet is the single most effective voice optimization
   - See Featured Snippet section above for implementation

2. **Page Speed**
   - Voice results load in 4.6 seconds on average (52% faster than the average web page)
   - Target: sub-3 second load time
   - Priority optimizations: image compression, code splitting, CDN, server-side rendering
   - Use Google PageSpeed Insights and Web Vitals (LCP < 2.5s, FID < 100ms, CLS < 0.1)

3. **Domain Authority**
   - 80%+ of voice answers come from pages in the top 3 organic positions
   - Build authority through backlinks, topical coverage, and E-E-A-T signals
   - Voice search amplifies existing authority rather than replacing the need for it

4. **Answer Length**
   - Google Assistant average answer: 41 words
   - Alexa average answer: 11 words
   - General target: 29 words for the speakable portion
   - Write a 29-word speakable summary, then expand with 40 to 60 word answer capsule

5. **HTTPS**
   - 70%+ of voice results come from HTTPS sites
   - Non-negotiable requirement for any modern site

6. **Mobile Optimization**
   - 50%+ of voice searches happen on smartphones
   - Responsive design, touch targets, readable font sizes
   - Mobile-first indexing means the mobile version is the indexed version

7. **Structured Data**
   - Does not directly rank for voice, but improves featured snippet ownership
   - Featured snippet ownership drives voice answers (factor #1)
   - FAQPage, HowTo, and Speakable schemas are the highest-impact types

---

### Platform-Specific Voice Sources

Each voice assistant pulls answers from different search backends. Optimizing for voice means optimizing for the right backend per platform.

| Platform | Primary Answer Source | Secondary Sources |
|----------|----------------------|-------------------|
| Google Assistant | Google featured snippets, Knowledge Graph | Google Actions, third-party integrations |
| Amazon Alexa | Bing search results, Amazon product data | Alexa Skills, Wikipedia |
| Apple Siri | Google (web results via Safari) | Apple Knowledge Graph, Wolfram Alpha, Apple Maps |
| Microsoft Cortana | Bing featured snippets | Microsoft Graph, LinkedIn data |

**Strategic implication:**
- Google optimization covers Google Assistant and Siri web results
- Bing optimization covers Alexa and Cortana
- Submit sitemap to both Google Search Console AND Bing Webmaster Tools
- Amazon product optimization covers Alexa commerce queries

---

### Speakable Content Requirements

Content marked as speakable (or likely to be read aloud by a voice assistant) must follow strict writing rules for text-to-speech (TTS) clarity.

**Do:**
- Write short declarative sentences (maximum 20 words each)
- Express one idea per sentence
- Use common, everyday vocabulary
- Spell out abbreviations on first use ("Search Engine Optimization" not "SEO" on first mention)
- Use numerals for numbers (TTS reads "3" correctly, may misread "three" in some contexts)
- Write as prose, not lists (TTS renders bullet points awkwardly)

**Do not:**
- Use parenthetical information (TTS reads parentheses literally or skips content)
- Use special characters: &, %, /, @, # (TTS handles these inconsistently)
- Use em dashes, en dashes, or semicolons (TTS pauses unpredictably)
- Ask rhetorical questions (voice assistants may try to answer them)
- Use idioms or culturally specific phrases (AI may misinterpret or translate literally)
- Include URLs in speakable text (TTS reads them character by character)

**Example of voice-optimized text:**
```
AEO helps businesses appear in AI search results. It works by structuring
content as direct answers to common questions. Companies that implement AEO
see higher visibility in Google AI Overviews, ChatGPT, and voice assistants.
The process starts with writing clear answer capsules for each topic.
```

---

### Local Voice Search Optimization

Local queries are the highest-converting category for voice search. "Near me" queries have grown 150%+ year over year and carry strong purchase intent.

**Key statistics:**
- 58% of consumers have used voice search for local business info
- "Near me" voice queries are the highest-conversion category across all voice search types
- 76% of smart speaker users perform local searches at least weekly

#### Google Business Profile (GBP) Optimization

The GBP is the single most important asset for local voice search. It must be 100% complete.

**Required fields (all must be filled):**
- Business name (exact legal name, no keyword stuffing)
- Address (must match website and all directories exactly)
- Phone number (local number preferred over toll-free)
- Hours of operation (including holiday hours)
- Business category (primary + up to 9 additional)
- Business description (750 characters, include service keywords naturally)
- Photos (minimum 10, updated quarterly)
- Q&A section (seed with 10 to 15 common questions and answers)
- Products/Services (list all with descriptions)
- Attributes (all applicable checkboxes)

#### NAP Consistency

NAP stands for Name, Address, Phone. Inconsistency across directories confuses search engines and reduces local ranking.

**Character-level consistency matters:**
- "St." vs "Street" creates a mismatch
- "Suite 200" vs "Ste. 200" vs "#200" creates a mismatch
- "(416) 555-1234" vs "416-555-1234" creates a mismatch

**Audit process:**
1. Use BrightLocal ($39+/mo) or Yext ($199+/mo) to scan 50+ directories
2. Fix all inconsistencies to match the GBP listing exactly
3. Priority directories: Google, Bing Places, Apple Maps, Yelp, Facebook, Yellow Pages, BBB
4. Re-audit quarterly

#### Local Landing Pages

Create one dedicated page per service area with LocalBusiness schema.

```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Your Business Name",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "123 Main Street",
    "addressLocality": "Toronto",
    "addressRegion": "ON",
    "postalCode": "M5V 1A1",
    "addressCountry": "CA"
  },
  "telephone": "+1-416-555-1234",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "09:00",
      "closes": "17:00"
    }
  ],
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": 43.6532,
    "longitude": -79.3832
  },
  "areaServed": {
    "@type": "City",
    "name": "Toronto"
  }
}
```

---

### Conversational Keyword Research Process

Voice keywords are longer, more natural, and more question-oriented than typed keywords. This process identifies them systematically.

#### Step 1: Map 5 Question Types

For each core topic, generate questions across all five types:

| Type | Pattern | Example |
|------|---------|---------|
| Who | "Who [verb] [topic]?" | "Who needs AEO?" |
| What | "What is/are [topic]?" | "What is answer engine optimization?" |
| When | "When should [action]?" | "When should I update my llms.txt file?" |
| Where | "Where [verb] [topic]?" | "Where do voice answers come from?" |
| How | "How do/does [topic]?" | "How does voice search ranking work?" |

#### Step 2: Map PAA Trees

Use AlsoAsked ($15+/mo) to expand each seed question into a full tree of 50 to 200+ related questions.

#### Step 3: Generate Question Variations

Use AnswerThePublic ($99/mo) to generate:
- Question wheel (who, what, where, when, why, how, can, will, are)
- Preposition queries ("for," "with," "without," "near," "to")
- Comparison queries ("vs," "or," "and," "like")
- Alphabetical variations

#### Step 4: Filter GSC Data

Export all queries from Google Search Console. Filter for:
- 4+ word queries (voice-adjacent length)
- Question words (what, how, why, best, where, who, when)
- Conversational modifiers ("should I," "can I," "is it worth," "do I need")

#### Step 5: Create FAQ Content

For each voice keyword:
- Question becomes the H2 or H3 heading (exact match phrasing)
- Write a 29 to 41 word answer (voice-optimized length)
- Add FAQPage schema wrapping all Q&A pairs on the page
- Internal link to the relevant hub or service page

---

### Voice Commerce (V-Commerce)

Voice-driven purchases represent a growing revenue channel, projected at $62 billion globally (2025).

#### Three Voice Commerce Paths

1. **Discovery:** "What is a good protein powder for beginners?"
   - User is researching. Win the answer, earn the click, convert on-site.
   - Optimize with comparison content, "best of" lists, and FAQPage schema.

2. **Direct Purchase:** "Alexa, reorder my protein powder."
   - User is buying a known product. This is repeat purchase territory.
   - For Amazon sellers: optimize product titles as natural language, enable Alexa purchasing, maintain 4+ star ratings.

3. **Local Conversion:** "Find a gym near me that's open now."
   - User is ready to visit. Highest conversion intent.
   - Optimize GBP hours, enable Google Reserve / booking button, create landing pages for "[service] near me" queries.

#### Highest-Converting Voice Modifiers

These words in voice queries signal strong purchase intent:
- **Transactional:** "buy," "order," "book," "reserve," "schedule"
- **Price-sensitive:** "price," "cost," "how much," "affordable," "cheap"
- **Urgency:** "open now," "today," "near me," "closest," "available"
- **Quality:** "best," "top rated," "recommended," "highest rated"

Create dedicated landing pages targeting these modifier + keyword combinations.

---

### Implementation Priority: 12-Week Sprint

#### Week 1: Foundation

| Task | Details |
|------|---------|
| Audit top 20 pages | Identify which already answer questions, which need capsules |
| Add answer capsules | Write 40 to 60 word capsules for all H2 headings on top 20 pages |
| Implement FAQPage schema | Add to 5 highest-traffic FAQ or question pages |
| Claim/verify GBP | Ensure 100% profile completion |
| Create llms.txt | Place at domain root with 20 to 50 top content links |

#### Weeks 2 to 3: Content Expansion

| Task | Details |
|------|---------|
| PAA research | Run top 10 topics through AlsoAsked, export full trees |
| LocalBusiness schema | Add to all location and service area pages |
| Speakable schema | Add to top 10 pages with answer capsules |
| NAP audit | Use BrightLocal or Yext, fix all inconsistencies |
| Bing Webmaster Tools | Submit sitemap (powers Alexa and Cortana) |

#### Weeks 4 to 8: Scale

| Task | Details |
|------|---------|
| Build 10 to 15 FAQ pages | Dedicated answer pages targeting PAA clusters |
| Create comparison tables | Target "vs" and "compare" queries with table snippets |
| Set up Otterly.AI | Monitor AI platform citations daily |
| Page speed optimization | Target sub-3 second load times on all priority pages |
| Mobile audit | Verify responsive design, touch targets, font readability |

#### Weeks 9 to 12: Measure and Optimize

| Task | Details |
|------|---------|
| Pull GSC question data | Export all question queries, identify new optimization targets |
| Manual voice testing | Test top 20 queries on Google Assistant, Siri, Alexa |
| Build monthly AEO report | Track all 7 key metrics (see Measurement section) |
| Content freshness update | Refresh top 20 pages with new data, update timestamps |
| Schema validation sweep | Run all pages through Rich Results Test, fix errors |

---

## Quick Reference: AEO Checklist Per Page

Use this checklist for every page you optimize:

- [ ] H2 headings phrased as questions or clear topic labels
- [ ] Answer capsule (40 to 60 words) immediately after every H2
- [ ] Flesch-Kincaid reading level Grade 8 or lower
- [ ] Subject-Verb-Object sentence structure in capsules
- [ ] No pronouns in first sentence of each capsule
- [ ] FAQPage schema for all Q&A content
- [ ] HowTo schema for process/tutorial content
- [ ] Speakable schema on top answer sections
- [ ] Entity density: 15 to 20 named entities per 1,000 words
- [ ] Semantic islands: 134 to 167 words per self-contained passage
- [ ] Internal links to hub page and related spokes
- [ ] Page speed under 3 seconds (LCP)
- [ ] HTTPS enabled
- [ ] Mobile-responsive layout verified
- [ ] Schema validated with Google Rich Results Test
