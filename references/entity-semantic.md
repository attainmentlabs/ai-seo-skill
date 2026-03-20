# Entity SEO and Semantic SEO: Implementation Reference

> This file is a deep implementation reference for the AI Search Visibility skill.
> It covers Entity SEO (knowledge graphs, entity homes, Wikidata, schema markup, knowledge panels, brand SERPs, LLM visibility) and Semantic SEO (EAV framework, topic clusters, topical maps, authority building).

---

## Entity SEO Implementation

### Knowledge Graph Basics

Google's Knowledge Graph contains 500+ billion facts about 5+ billion entities. It is the backbone of entity understanding for both traditional search and AI-generated answers.

**Data sources in trust order (highest to lowest):**

1. **Wikipedia** . Strongest signal for entity recognition. Human-curated, high editorial standards.
2. **Wikidata** . Structured data layer. Machine-readable. Directly ingested by Google and Gemini.
3. **CIA World Factbook** . Authoritative geographic and governmental data.
4. **Google Books** . Long-form content corpus for entity context.
5. **Licensed data partners** . MusicBrainz (music), IMDb (film/TV), sports databases.
6. **Schema.org structured data** . Webmaster-controlled entity declarations on sites.
7. **Google Business Profile** . Verified local business entity data.
8. **GSC-verified data** . Google Search Console verified ownership signals.
9. **Knowledge Vault** . Auto-mined facts from the open web, probabilistic confidence scores.

**Update cadence:**
- Algorithm-level Knowledge Graph updates roll out every 2 to 3 weeks
- Individual entity confidence scores update more continuously as new crawl data arrives
- Wikidata edits can propagate to Knowledge Panels within days of Google's next crawl cycle

---

### Entity Home (Jason Barnard / Kalicube Concept)

Your "Entity Home" is the single page that definitively describes your entity to Google. For most businesses, this is the About page. For individuals, it is a personal bio page or the about section on a company site.

**What the Entity Home must contain:**

- **Explicit entity declaration.** "FitCommit AI is a health technology company..." (not implied, stated directly)
- **Founding information.** Year, location, circumstances
- **Key people.** Founders, CEO, leadership with names and roles
- **Services and products.** Clear descriptions of what the entity offers
- **Location.** Physical address or headquarters city
- **Awards and recognition.** Third-party validation signals
- **All sameAs links pointing outward.** Links to every authoritative profile (LinkedIn, X, Crunchbase, Wikidata, YouTube, etc.)

**Why this matters:** This page becomes the anchor Google uses to validate your entity across the web. When Google finds mentions of your brand elsewhere, it cross-references back to your Entity Home to confirm the entity is the same one. Consistency between the Entity Home and external references builds entity confidence.

**Entity Home optimization checklist:**
1. URL is clean and permanent (e.g., `/about` not `/about-us-2024-v2`)
2. Page loads fast and renders fully without JavaScript
3. Organization schema on the page references the Entity Home with `@id`
4. First paragraph contains entity name, entity type, and primary topic
5. Internal links from every page on the site point to the Entity Home (footer or nav)
6. External authoritative profiles all link back to this page

---

### Wikidata Optimization

Wikidata is the structured data layer that feeds Google's Knowledge Graph, Gemini, and other AI systems directly. A complete Wikidata entry is one of the highest-leverage Entity SEO actions.

**Key properties to populate:**

| Property Code | Property Name | Example Value |
|---------------|--------------|---------------|
| P31 | instance of | Q4830453 (business), Q891723 (startup), Q7397 (software) |
| P856 | official website URL | https://yourdomain.com |
| P154 | logo image | Upload to Wikimedia Commons first |
| P112 | founded by | Link to founder's Wikidata item |
| P17 | country | Q16 (Canada), Q30 (United States) |
| P452 | industry | Q11661 (information technology), Q1321119 (health tech) |
| P159 | headquarters location | Q172 (Toronto), Q65 (Los Angeles) |
| P571 | inception date | 2024 |
| P1566 | GeoNames ID | Numeric ID from geonames.org |
| P2002 | Twitter/X username | yourhandle (without @) |
| P4264 | LinkedIn company ID | numeric ID from LinkedIn URL |
| P2013 | Facebook ID | page name or numeric ID |
| P2397 | YouTube channel ID | UC... channel ID |

**Process:**
1. Create an account at wikidata.org
2. Search for an existing entry for your entity (avoid duplicates)
3. If none exists, click "Create a new Item"
4. Add a label (entity name), description (one sentence), and aliases (abbreviations, former names)
5. Add all relevant properties listed above, each with a source (reference URL)
6. For P31 (instance of), choose the most specific class that fits
7. Add qualifiers where applicable (e.g., start dates for roles)
8. Monitor the item for community edits or deletion proposals

**Important notes:**
- Wikidata is community-edited. Unsourced claims may be removed.
- Every property value should have at least one reference (source URL)
- Wikidata items for businesses are acceptable even without a Wikipedia article
- Edits can reflect in Google Knowledge Panels within days of Google's next crawl
- For founders, create a separate Wikidata item and link it via P112

---

### Schema Markup for Entity Recognition

Schema markup is the primary webmaster-controlled mechanism for declaring entity information to search engines and AI systems.

**Organization Schema (Critical for every business site):**

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://yourdomain.com/#organization",
  "name": "Business Name",
  "url": "https://yourdomain.com",
  "logo": {
    "@type": "ImageObject",
    "url": "https://yourdomain.com/logo.png",
    "width": 600,
    "height": 60
  },
  "image": "https://yourdomain.com/og-image.png",
  "description": "One-paragraph entity description matching the Entity Home first paragraph",
  "foundingDate": "2024",
  "foundingLocation": {
    "@type": "Place",
    "name": "Toronto, Ontario, Canada"
  },
  "founder": {
    "@type": "Person",
    "@id": "https://yourdomain.com/about#founder",
    "name": "Founder Name"
  },
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Toronto",
    "addressRegion": "ON",
    "addressCountry": "CA"
  },
  "sameAs": [
    "https://www.linkedin.com/company/your-company",
    "https://twitter.com/yourhandle",
    "https://www.wikidata.org/wiki/Q-NUMBER",
    "https://www.crunchbase.com/organization/your-company",
    "https://www.youtube.com/@yourchannel",
    "https://www.instagram.com/yourhandle",
    "https://github.com/yourorg"
  ],
  "knowsAbout": [
    {"@type": "Thing", "name": "AI fitness coaching"},
    {"@type": "Thing", "name": "personalized nutrition"},
    {"@type": "Thing", "name": "computer vision for exercise form"}
  ],
  "areaServed": {
    "@type": "Country",
    "name": "Worldwide"
  },
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "minValue": 2,
    "maxValue": 10
  }
}
```

**Person Schema (for founders and key leaders):**

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "@id": "https://yourdomain.com/about#founder",
  "name": "Full Name",
  "givenName": "First",
  "familyName": "Last",
  "jobTitle": "Founder & CEO",
  "worksFor": {
    "@id": "https://yourdomain.com/#organization"
  },
  "alumniOf": {
    "@type": "EducationalOrganization",
    "name": "University Name"
  },
  "knowsAbout": [
    "Artificial Intelligence",
    "Fitness Technology",
    "SaaS Product Development"
  ],
  "sameAs": [
    "https://linkedin.com/in/profile",
    "https://twitter.com/handle",
    "https://www.wikidata.org/wiki/Q-NUMBER"
  ],
  "image": "https://yourdomain.com/founder-headshot.jpg",
  "description": "Brief professional bio matching LinkedIn summary"
}
```

**Key schema properties explained:**

- **`@id`**: A unique URI that serves as the entity identifier across all schema on your site. Use consistent URIs everywhere. When two schema blocks reference the same `@id`, Google understands they describe the same entity. Convention: `https://yourdomain.com/#organization` for the org, `https://yourdomain.com/about#founder` for the founder.

- **`sameAs`**: Links your entity to external authoritative profiles. This is the single most critical property for Knowledge Graph connection. Every `sameAs` URL must resolve to a page that clearly represents the same entity. Order does not matter, but completeness does.

- **`knowsAbout`**: Declares topical expertise. Added to Schema.org for broader use in 2024. Use for both persons and organizations. Helps AI systems understand what topics your entity is authoritative about. Use specific terms, not vague ones ("AI-powered fitness coaching" not "technology").

**Schema implementation rules:**
1. Use JSON-LD format, not Microdata or RDFa (Google's preferred format)
2. Place in `<head>` or at the bottom of `<body>`
3. Validate with Google Rich Results Test and Schema.org validator
4. One Organization schema per site, placed on every page (or at minimum the homepage and Entity Home)
5. Person schema on the Entity Home and any author bio pages
6. Never include schema that contradicts visible page content
7. Update schema when entity details change (new address, new products, etc.)

**Additional schema types for content pages:**

- **Article**: For blog posts, news articles, guides. Include `author`, `datePublished`, `dateModified`, `publisher`.
- **FAQPage**: For pages with question-and-answer content. High impact for featured snippets.
- **HowTo**: For tutorial and instructional content.
- **BreadcrumbList**: For site navigation. Helps Google generate sitelinks.
- **WebSite**: For the homepage. Include `potentialAction` with SearchAction for sitelinks search box.
- **SoftwareApplication**: For SaaS products. Include `applicationCategory`, `operatingSystem`, `offers`.

---

### Knowledge Panel: How to Get One

A Knowledge Panel is the information box that appears on the right side of Google search results for recognized entities. It signals strong entity recognition.

**Prerequisites (in priority order):**

1. **Be a recognized entity.** A Wikipedia article is the strongest signal, but it is not strictly required. Entities without Wikipedia articles can still trigger Knowledge Panels through strong Wikidata entries and consistent web presence.

2. **Complete Wikidata entry.** Fill all relevant properties with sourced references. This is the minimum viable path to a Knowledge Panel without Wikipedia.

3. **Organization schema with sameAs links.** Deployed on your site, connecting to all authoritative profiles.

4. **Consistent entity information across 50+ directories.** Name, logo, description, and key facts must match across the web.

5. **Google Business Profile.** Required for local entities. Strongly recommended for all businesses with a physical address.

6. **Press coverage.** Articles in DA 60+ publications that mention your entity by name with consistent details.

**Once a Knowledge Panel appears:**
- Claim it via Google's Knowledge Panel verification process (search your entity, click "Claim this knowledge panel")
- Verification options: Google Search Console, YouTube, X/Twitter, or official website
- After claiming, you can suggest edits (Google reviews them)
- Monitor for accuracy. Report inaccuracies via the "Feedback" link

**Common reasons Knowledge Panels do not appear:**
- Entity is too new (insufficient web coverage)
- Entity name is ambiguous (shares name with more prominent entity)
- Inconsistent entity data across the web
- No Wikidata entry
- Schema markup is missing or incorrect

---

### NAP Consistency

NAP stands for Name, Address, Phone. Character-level consistency across every directory and listing is critical for entity recognition, especially for local businesses.

**Why it matters:** Google cross-references entity data across hundreds of sources. Inconsistencies reduce entity confidence scores. Even small variations create mismatch signals.

**Common inconsistency problems:**
- "St." vs "Street" vs "St"
- "Suite 100" vs "Ste 100" vs "#100"
- "(416) 555-1234" vs "416-555-1234" vs "4165551234"
- "FitCommit AI" vs "FitCommit" vs "Fit Commit AI"
- Outdated addresses after a move

**NAP audit process:**
1. Define canonical NAP (the exact format you will use everywhere)
2. Audit all existing listings using tools below
3. Update every inconsistency to match canonical NAP
4. Set calendar reminder for quarterly re-audit

**Audit tools:**
- BrightLocal (Citation Tracker): scans 1,000+ directories
- Moz Local: distribution + monitoring
- Yext: automated distribution to 200+ publishers (paid)
- Whitespark: manual audit and citation building

**Directory tiers:**

| Tier | Examples | Priority |
|------|----------|----------|
| Tier 1 (Critical) | Google Business Profile, Apple Maps, Yelp, BBB, LinkedIn | Fix within 24 hours |
| Tier 2 (Important) | Facebook, Yellow Pages, Foursquare, Bing Places, TripAdvisor | Fix within 1 week |
| Tier 3 (Aggregators) | Data Axle (formerly Infogroup), Acxiom, Localeze, Factual | Fix once, they feed hundreds of smaller directories |
| Tier 4 (Industry) | Niche directories for your industry | Fix within 2 weeks |

**Aggregator strategy:** Fixing Tier 3 aggregators first can cascade corrections to hundreds of smaller directories automatically. Data Axle and Acxiom supply data to the majority of small local directories.

---

### Brand SERP Optimization

Your Brand SERP is what appears when someone searches your exact brand name. It is your digital business card and the first impression for journalists, investors, customers, and AI systems performing retrieval.

**Priority ranking for Brand SERP elements:**

1. **Homepage must rank #1 for brand name.** If it does not, there is a serious technical or authority problem. Fix title tag, H1, and internal linking immediately.

2. **Claim all major social profiles.** LinkedIn, YouTube, X, Instagram, Facebook, GitHub, Crunchbase. Even if you do not actively post, secure the handles. These dominate Brand SERP positions 2 through 8.

3. **Sitelinks control.** Implement BreadcrumbList schema. Clear navigation structure with descriptive link text. Google auto-generates sitelinks, but you influence them through site architecture.

4. **Knowledge Panel maintenance.** See Knowledge Panel section above.

5. **Image pack optimization.** Brand name in image alt text. Upload high-quality branded images. Google Image results often appear in Brand SERPs.

6. **YouTube channel with branded video titles.** YouTube results frequently appear in Brand SERPs. Title format: "Brand Name: Topic" or "Topic | Brand Name."

7. **Reputation management.** Push negative content below fold by strengthening positive content in positions 1 through 10. Create authoritative profiles on high-DA sites. Publish press releases. Guest post on industry sites.

**Monitoring tools:**
- Kalicube Pro: purpose-built for Brand SERP tracking and entity management
- Semrush Position Tracking: track brand keywords across devices and locations
- Google Alerts: monitor new mentions of your brand name
- Mention.com or Brand24: real-time brand monitoring across web and social

**Brand SERP audit checklist (monthly):**
- [ ] Homepage ranks #1 for exact brand name
- [ ] Knowledge Panel is accurate (if present)
- [ ] All social profiles in top 10 results are claimed and up to date
- [ ] No negative content in top 10
- [ ] Image pack shows branded images (not competitor or stock)
- [ ] Video results show branded content (if any)
- [ ] People Also Ask contains questions you have answered on your site

---

### How LLMs Use Entity Data

Understanding how large language models access and surface entity information is critical for AI search visibility. Different LLM-powered systems use different data access patterns.

**Training data inclusion:**
- GPT-4, Gemini, Claude, and other major LLMs were trained on text corpora that included Wikipedia and Wikidata dumps
- Well-documented entities have strong implicit representation in LLM weights (the model "knows" about them from training)
- Entities with thin web presence have weak or nonexistent representation
- Training data has a cutoff date. Information published after that date is not in the model's weights.

**Retrieval-Augmented Generation (RAG) systems:**
- Perplexity, Bing Copilot, Gemini (with Search), and SearchGPT use RAG: they retrieve current web content at query time, then generate answers using that content
- ChatGPT without browsing relies solely on training data
- Gemini has direct access to Google's Knowledge Graph in addition to RAG
- Perplexity heavily indexes and cites Reddit, news sites, and authoritative publications

**Data access patterns by system:**

| System | Training Data | Live RAG | Knowledge Graph | Key Sources |
|--------|--------------|----------|-----------------|-------------|
| ChatGPT (no browse) | Yes | No | No | Wikipedia, Wikidata dumps in training |
| ChatGPT (with browse) | Yes | Yes (Bing) | No | Live web via Bing |
| Perplexity | Yes | Yes (multi-source) | No | Reddit, news, authoritative sites |
| Gemini | Yes | Yes (Google) | Yes (direct) | Knowledge Graph, Google Search index |
| Bing Copilot | Yes | Yes (Bing) | Partial | Bing index, LinkedIn (Microsoft-owned) |
| Claude | Yes | Limited | No | Training data primarily |

**Priority actions for LLM visibility (ranked by impact):**

1. **Wikipedia article (if eligible).** Very high impact. Appears in training data of all major LLMs. Must meet Wikipedia notability guidelines (significant coverage in multiple independent reliable sources). Do not create a promotional article. It will be deleted.

2. **Wikidata entry (complete).** High impact, especially for Gemini which has direct Knowledge Graph access. Structured data is cleanly parseable by all systems.

3. **Crunchbase and LinkedIn profiles.** Medium-high impact. Frequently retrieved by Perplexity and Bing Copilot during RAG. Crunchbase is particularly important for startups. Keep profiles complete and current.

4. **Press coverage in DA 60+ publications.** High impact. These articles appear in RAG results. Target TechCrunch, Forbes, VentureBeat, industry-specific outlets. Even a single mention in a credible publication can become the primary source an LLM cites.

5. **Reddit and Quora presence.** Medium impact. Perplexity heavily cites Reddit. Organic discussions about your brand or product (not self-promotional posts) carry significant weight. Monitor relevant subreddits. Answer questions on Quora where your expertise applies.

6. **Blog content on your own site.** Medium impact when combined with strong E-E-A-T signals. RAG systems index blog posts, especially those ranking in Google's top 10.

7. **YouTube video descriptions and transcripts.** Medium impact. YouTube content is indexed by Google's systems and accessible to Gemini. Perplexity also retrieves YouTube content.

**Content formatting for LLM extraction:**
- Use clear, declarative sentences at the start of sections (LLMs prefer explicit statements)
- Lead paragraphs should contain entity name + key fact (e.g., "FitCommit AI is a health technology company founded in 2024 in Toronto")
- Use structured formats: tables, numbered lists, definition lists
- Include specific numbers, dates, and proper nouns (LLMs anchor on specifics)
- Avoid vague language ("industry-leading," "best-in-class") in favor of concrete descriptions

---

## Semantic SEO Implementation

### Koray Tugberk Gubur's Entity-Attribute-Value (EAV) Framework

The EAV framework is the most actionable model for building topical authority through content. Core principle: Google ranks entities and their attribute-value coverage, not just keywords. A page that covers more relevant attributes of an entity demonstrates deeper understanding and earns higher rankings.

**The 4 key rules:**

**Rule 1: One macro context per page.**
Each page has exactly one primary topic focus. This does not mean the page only mentions one thing. It means there is one clear subject that the page is about, and everything on the page supports or extends understanding of that subject. Mixing macro contexts dilutes topical relevance.

- Correct: A page about "intermittent fasting for weight loss" covers fasting methods, mechanisms, research, and protocols all in the context of weight loss.
- Incorrect: A page about "intermittent fasting and keto diet and meal prep tips" covers three macro contexts.

**Rule 2: H2 headings as user questions.**
Do not use keyword-stuffed phrases as H2s. Use actual questions that a searcher would ask. This aligns with how Google extracts featured snippets and how AI systems parse content for answers.

- Correct: `## How long should you fast for weight loss?`
- Incorrect: `## Intermittent Fasting Duration Weight Loss`

**Rule 3: 40-word extractive answer after each H2.**
Immediately after each H2 question heading, write a 35 to 50 word answer in Subject-Verb-Object structure. This answer should be extractable as a standalone snippet. Google's featured snippet algorithm and LLM RAG systems both favor content structured this way.

Example:
```
## How long should you fast for weight loss?

Most research supports a 16-hour fasting window for sustainable weight loss.
The 16:8 protocol allows eating within an 8-hour window daily, which reduces
total caloric intake by 10 to 25 percent without requiring calorie counting
or meal tracking.
```

**Rule 4: EAV coverage completeness.**
Map all attributes and values for your topic entity. The more complete your coverage, the stronger your topical relevance signal. Do not leave obvious attributes unaddressed.

**EAV Inventory Example:**

```
Entity: Intermittent Fasting

  Attribute: Duration
    Values: 12 hours, 14 hours, 16 hours, 18 hours, 20 hours, 24 hours, 36 hours

  Attribute: Method
    Values: 16:8, 14:10, 18:6, 5:2, OMAD (one meal a day), alternate day fasting, eat-stop-eat

  Attribute: Biological mechanism
    Values: insulin reduction, autophagy activation, ketone production, growth hormone increase, circadian rhythm alignment

  Attribute: Health benefit
    Values: weight loss, improved insulin sensitivity, reduced inflammation, cardiovascular health, cognitive function

  Attribute: Contraindication
    Values: pregnancy, type 1 diabetes, eating disorder history, underweight individuals, children under 18

  Attribute: Research
    Values: Yoshinori Ohsumi (2016 Nobel, autophagy), NEJM 2019 review, clinical trials on time-restricted eating

  Attribute: Common mistake
    Values: overeating during feeding window, inadequate hydration, starting with extreme protocols, ignoring micronutrient intake
```

**Attribute mining sources (where to find all relevant attributes):**

1. **Google People Also Ask.** Search your topic, expand all PAA questions. Each question reveals an attribute Google considers relevant. Use tools like AlsoAsked.com to map the full PAA tree.

2. **Reddit and Quora discussions.** Real user questions reveal attributes that academic or commercial content often misses. Sort by "top" to find the most common questions.

3. **Competitor content that ranks well.** Analyze top 10 ranking pages for your target keywords. What subtopics do they all cover? Those are mandatory attributes.

4. **Wikipedia infobox attributes.** If the entity has a Wikipedia article, the infobox sidebar contains the attributes Wikipedia editors consider most important.

5. **Google Knowledge Panel.** If the entity has a Knowledge Panel, the fields displayed are attributes Google has already recognized.

6. **Academic papers.** Google Scholar searches reveal attributes discussed in research. Use these for depth and authority.

7. **Google Autocomplete and Related Searches.** Type your entity name and note the suggestions. These reflect real search patterns and imply important attributes.

**Attribute filtering principle:** Not all attributes belong on one page. Filter by asking: "Given this page's macro context and the searcher's intent, which attributes are most relevant?" A page about "intermittent fasting for beginners" should cover methods, duration, and common mistakes, but probably not deep autophagy biochemistry.

---

### Topic Cluster Architecture (Hub-and-Spoke)

Topic clusters are the structural implementation of topical authority. A cluster consists of one hub page (pillar) and multiple spoke pages, all interlinked.

**Hub (Pillar Page):**
- Word count: 3,000 to 5,000 words
- Covers the broad topic comprehensively but not exhaustively
- Links to every spoke page in the cluster
- Uses broad, high-volume keywords (e.g., "intermittent fasting guide")
- Serves as the entity home for the topic on your site
- Updated regularly as new spoke content is published
- Table of contents with jump links
- Summary or overview sections for each subtopic (with links to the full spoke)

**Spokes (Cluster Content):**
- Word count: 1,500 to 3,000 words each
- Each spoke covers one specific subtopic in depth
- Links back to the hub using consistent anchor text
- Links laterally to 2 to 3 adjacent spokes when genuine topical overlap exists
- Uses long-tail, specific keywords (e.g., "16:8 intermittent fasting schedule for beginners")

**Cluster sizing:**
- Minimum: 5 spoke pages per hub (anything fewer lacks critical mass)
- Optimal: 8 to 15 spoke pages per hub (best authority-to-maintenance ratio)
- Maximum: 20 to 25 spoke pages per hub (beyond this, split into two clusters)

**Internal linking patterns within clusters:**

| Link Type | Direction | Frequency | Anchor Text Strategy |
|-----------|-----------|-----------|---------------------|
| Pillar to spoke | Hub links to every spoke | Once per spoke in body text, once in ToC | Descriptive, includes spoke's primary keyword |
| Spoke to pillar | Every spoke links to hub | Minimum twice: within first 200 words and near conclusion | Consistent anchor text across all spokes |
| Spoke to spoke | Between related spokes | 2 to 3 lateral links per spoke | Only when genuine topical overlap exists |

**Anchor text distribution:**
- 20 to 30% exact match (spoke's primary keyword as anchor)
- 30 to 40% partial match (variation or synonym of keyword)
- 15 to 20% branded (company name + keyword)
- 10 to 20% natural language (contextual phrases)
- 0% generic ("click here," "learn more," "read this"). Never use generic anchors.

**URL structure for clusters:**
```
/intermittent-fasting/                          (hub)
/intermittent-fasting/16-8-method/              (spoke)
/intermittent-fasting/benefits-weight-loss/     (spoke)
/intermittent-fasting/beginners-guide/          (spoke)
/intermittent-fasting/common-mistakes/          (spoke)
```

This flat-subfolder structure signals topical relationship through URL hierarchy. Avoid deeply nested URLs (more than 3 levels).

---

### Building a Topical Map

A topical map is the strategic blueprint for all content in your niche. It defines what to write, in what order, and how everything connects.

**Step 1: Define niche domain precisely.**
Specificity is critical. "AI fitness coaching for busy professionals aged 30 to 50" is actionable. "Fitness" is not. The niche definition determines what is in scope and what is out of scope for your content.

**Step 2: Identify 3 to 7 pillar topics.**
These are the major themes that fully define your niche. Every piece of content you create should fall under one of these pillars.

Example for AI fitness coaching:
- Pillar 1: AI-powered workout programming
- Pillar 2: Personalized nutrition and meal planning
- Pillar 3: Exercise form analysis and injury prevention
- Pillar 4: Fitness tracking and progress analytics
- Pillar 5: Behavioral science and habit formation

**Step 3: Keyword research per pillar.**
For each pillar, conduct thorough keyword research.
- Tools: Ahrefs Keywords Explorer, Semrush Keyword Magic, Google Keyword Planner
- Volume range: 100 to 10,000 monthly searches (sweet spot for growing sites)
- Filter by keyword difficulty appropriate to your site's authority
- Export and tag each keyword with its parent pillar

**Step 4: Assign content types per keyword group.**
Different intents require different content formats.

| Content Type | Best For | Intent Signal |
|-------------|---------|---------------|
| Definition pages | "What is X" queries | Informational |
| How-to tutorials | "How to X" queries | Informational/Transactional |
| Comparison pages | "X vs Y" queries | Commercial investigation |
| Reviews | "X review" queries | Commercial investigation |
| Listicles | "Best X" or "Top X" queries | Commercial investigation |
| Data/research | "X statistics" or "X study" queries | Informational |
| Product pages | "Buy X" or "X pricing" queries | Transactional |

**Step 5: Content gap analysis.**
Identify what competitors cover that you do not.
- Ahrefs Content Gap: finds keywords competitors rank for that you do not
- MarketMuse: evaluates semantic depth and identifies missing subtopics
- Frase: SERP-level analysis showing what top-ranking pages include
- Manual review: read the top 5 results for each target keyword, note what they all cover

**Step 6: Map the hierarchy.**
Organize your keywords and content types into a clear hierarchy.
```
Hub URL: /ai-workout-programming/
  Spoke: /ai-workout-programming/how-it-works/
  Spoke: /ai-workout-programming/vs-personal-trainer/
  Spoke: /ai-workout-programming/best-apps/
  Spoke: /ai-workout-programming/beginner-plan/
  Spoke: /ai-workout-programming/advanced-periodization/
```

**Step 7: Define publishing sequence.**
Not all content should be published in random order.
1. Hub pages first (establish pillar authority)
2. Highest-traffic spokes second (capture demand early)
3. Long-tail spokes third (fill out coverage)
4. Lateral and supporting content last (strengthen the mesh)

**Step 8: Set publishing cadence.**
- Minimum: 2 to 3 cluster pages per week for a growing site
- Each page must meet quality standards (EAV coverage, schema markup, internal links)
- Consistency matters more than volume. 2 pages per week for 6 months beats 20 pages in one week then silence.

**Topical map tools:**
- Topicalmap.ai: automated topic cluster generation
- Surfer SEO Topical Map: keyword clustering and gap detection
- Keyword Insights: intent-based keyword clustering
- Screaming Frog: crawl your existing site to map current coverage
- Miro or Whimsical: visual mapping of cluster architecture
- Google Sheets: functional and free for organizing keyword data

---

### How Google Evaluates Topical Authority

Google uses multiple signals to determine whether a site is authoritative on a given topic. Understanding these signals helps prioritize efforts.

**Signals in approximate order of weight:**

1. **Topic coverage completeness.** Does the site cover the full attribute space of the topic? Sites that address a topic from every angle signal deep expertise. This is the EAV framework in action.

2. **Content depth per subtopic.** Each page must demonstrate thorough coverage of its specific subtopic. Surfer SEO's "content score" and Clearscope's "content grade" approximate this signal. Thin content (under 800 words on a complex topic) signals shallow understanding.

3. **Internal link density within topic clusters.** Dense, relevant internal links within a topic cluster signal topical cohesion. Orphan pages (no internal links) receive minimal topical authority transfer.

4. **Contextual backlink profile.** Links from topically relevant sites carry more weight than links from off-topic sites. A fitness tech company getting links from health publications matters more than links from generic directory sites.

5. **E-E-A-T signals for the topic.** Experience, Expertise, Authoritativeness, Trustworthiness. Author bios with relevant credentials. First-person experience markers. Citations to research. Transparent business information.

6. **Publishing consistency over time.** Sites that publish on a topic consistently over months and years signal ongoing expertise. A burst of content followed by silence signals lower commitment.

7. **User engagement signals.** Low pogo-sticking (users clicking back to search results after visiting your page) signals content satisfaction. High dwell time signals relevance. These are indirect but meaningful signals.

---

### 90-Day Semantic Authority Build

A structured timeline for building topical authority from zero (or near-zero) to measurable results.

**Days 1 to 14: Foundation**

- [ ] Full keyword research for your niche (target 200+ keywords minimum)
- [ ] Cluster keywords into 3 to 7 pillar topics
- [ ] Build complete topical map with hub and spoke URLs defined
- [ ] Audit existing content: what can be updated vs. what must be created
- [ ] Run content gap analysis against top 3 competitors
- [ ] Implement Organization schema with full sameAs links on every page
- [ ] Implement Person schema for founders and key authors
- [ ] Create or optimize Entity Home page (About page)
- [ ] Create or complete Wikidata entry for your organization
- [ ] Create or complete Wikidata entry for founder (if applicable)
- [ ] Audit and fix NAP consistency across Tier 1 directories
- [ ] Set up Google Search Console and submit sitemap
- [ ] Set up Google Business Profile (if applicable)

**Days 15 to 45: Hub Phase**

- [ ] Write and publish all hub/pillar pages (3,000 to 5,000 words each)
- [ ] Each hub page includes: table of contents, BreadcrumbList schema, Article schema, internal links to planned spoke URLs (even if spoke pages are not yet published, use the planned URLs)
- [ ] Implement FAQPage schema on hubs where appropriate
- [ ] Build internal links from existing content to new hubs
- [ ] Submit all hub URLs to Google Search Console for indexing
- [ ] Begin Tier 3 aggregator NAP corrections (Data Axle, Acxiom)
- [ ] Set up Brand SERP monitoring

**Days 46 to 90: Spoke Phase and Authority Building**

- [ ] Publish 3+ spoke pages per week (45+ total spoke pages in this phase)
- [ ] For each spoke page:
  - [ ] Complete EAV inventory before writing
  - [ ] Question-based H2 headings
  - [ ] 40-word extractive answer immediately after each H2
  - [ ] Internal link to hub page (first 200 words + near conclusion)
  - [ ] Internal links to 2 to 3 lateral spokes
  - [ ] Article schema with author, dates, publisher
  - [ ] Alt text on all images
- [ ] Run content gap analysis again at day 60 (compare against updated competitor content)
- [ ] Digital PR campaign: 5 pitches per week to relevant publications
- [ ] Guest posting: 2 to 3 guest posts per month on topically relevant DA 50+ sites
- [ ] Quarterly NAP audit (full re-check at day 90)
- [ ] Monitor GSC for indexing issues, crawl errors, and ranking changes
- [ ] Identify underperforming spoke pages and update with additional EAV coverage

**Expected outcomes at day 90:**
- 3 to 7 hub pages published and indexed
- 45+ spoke pages published and indexed
- Initial rankings for long-tail keywords (positions 5 to 30)
- Some hub pages beginning to rank for medium-volume keywords
- Knowledge Panel may appear if entity signals are strong enough
- Brand SERP shows 8+ owned or positive results in top 10

**Post-90-day ongoing maintenance:**
- Continue publishing 2 to 3 pages per week
- Update hub pages quarterly with new spoke links and updated information
- Refresh spoke pages annually or when information becomes outdated
- Continue digital PR and link building
- Monitor and respond to changes in competitor coverage
- Expand topical map as new subtopics emerge

---

## Quick Reference: Entity SEO vs Semantic SEO

| Aspect | Entity SEO | Semantic SEO |
|--------|-----------|--------------|
| Focus | Making your entity recognizable to search engines and AI | Making your content topically authoritative |
| Key actions | Wikidata, schema markup, NAP, Entity Home, Brand SERP | EAV inventory, topic clusters, internal linking, content depth |
| Timeline | Some results in weeks (Knowledge Graph) | Results in 60 to 90 days (topical authority) |
| Tools | Kalicube Pro, BrightLocal, Schema validators | Surfer SEO, MarketMuse, Ahrefs, Frase |
| Maintenance | Quarterly audits | Ongoing content publishing |
| AI impact | High (entity data in training data and RAG) | High (content retrieved by RAG systems) |

Both strategies are complementary. Entity SEO establishes who you are. Semantic SEO establishes what you know. Together they form the foundation of AI search visibility.

---

## Sources and Further Reading

- Jason Barnard, "The Fundamentals of Brand SERPs for Business" (Kalicube)
- Koray Tugberk Gubur, "Semantic SEO and Topical Authority" (Holistic SEO)
- Google Search Central documentation on structured data
- Schema.org vocabulary reference
- Wikidata property documentation at wikidata.org
- Google Knowledge Graph API documentation
