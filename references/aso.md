# App Store Search Optimization (ASO)

Comprehensive guide for optimizing visibility in Apple App Store and Google Play Store search.

## Why ASO Matters for AI Visibility

App stores are increasingly AI-powered discovery surfaces:
- Apple uses on-device ML for personalized search rankings (2024)
- Google Play uses BERT-based semantic understanding for queries
- 65% of app downloads originate from search (Apple, 2024)
- Voice search via Siri/Google Assistant drives app discovery

## Platform-Specific Algorithms

### Apple App Store

**Ranking Factors (weighted by importance):**
1. **App name/title** (30 chars max, highest weight)
2. **Subtitle** (30 chars, second highest)
3. **Keyword field** (100 chars, backend only, comma-separated)
4. **In-app purchases** (indexed by name)
5. **Download velocity** (recent downloads matter more)
6. **Ratings and reviews** (quantity + quality + recency)
7. **Retention** (day 1, 7, 30 signals)
8. **Update frequency** (active development signal)

**Apple Search Ads influence:** Paid installs can boost organic ranking by increasing download velocity.

### Google Play Store

**Ranking Factors:**
1. **App title** (50 chars max, highest weight)
2. **Short description** (80 chars)
3. **Long description** (4,000 chars, keyword density matters)
4. **Developer name** (indexed)
5. **Package name** (slight signal)
6. **Install count** (lifetime + recent)
7. **Ratings** (star average + review text sentiment)
8. **Engagement metrics** (crashes, ANRs, uninstalls)
9. **Backlinks** (web references to Play Store listing)

## Keyword Research

### Tools
- **App Annie / data.ai** (competitor keyword rankings)
- **Sensor Tower** (search volume estimates)
- **AppTweak** (keyword difficulty scores)
- **Mobile Action** (keyword suggestions)
- **Apple Search Ads** (search popularity 5-100 scale)

### Research Process
1. Brainstorm seed keywords from user language
2. Analyze competitor keywords (top 10 apps in category)
3. Check search volume vs. competition difficulty
4. Prioritize by: volume x relevance / difficulty
5. Group keywords by intent (feature, problem, brand)

### Keyword Placement Strategy

**Apple (100 char limit in keyword field):**
```
fitness,workout,exercise,gym,trainer,health,weight,cardio,strength
```
- No spaces after commas
- No duplicates (title/subtitle words auto-indexed)
- Singular forms only (Apple indexes plurals automatically)
- No competitor brand names (policy violation risk)

**Google (embed in long description):**
- Use primary keyword 3-5x naturally
- Include secondary keywords 1-2x each
- Front-load first sentence with main keyword
- Use keyword variations and synonyms

## Metadata Optimization

### App Title Formula
`[Brand] - [Primary Keyword] [Secondary Keyword]`

Examples:
- "FitCommit - AI Workout Tracker"
- "Calm - Sleep & Meditation"
- "Notion - Notes, Docs, Tasks"

### Subtitle/Short Description
- Lead with strongest value proposition
- Include high-value keyword not in title
- Action-oriented when possible

### Long Description (Google Play)
```
Structure:
- Paragraph 1: Problem + solution (primary keyword)
- Paragraph 2: Key features (feature keywords)
- Paragraph 3: Social proof (awards, press, numbers)
- Paragraph 4: Call to action
```

## Visual ASO

### Screenshots
- First 2 screenshots visible in search results (most important)
- Show core value prop in screenshot 1
- Use captions for keyword reinforcement
- A/B test layouts (feature vs. lifestyle)
- Optimal: 5-8 screenshots per platform

### App Preview Videos (Apple)
- 15-30 seconds max
- Auto-plays in search results (iOS 15+)
- First 3 seconds crucial (before poster frame)
- No audio assumed (captions required)

### Feature Graphic (Google Play)
- 1024x500px hero image
- Appears in browse/feature placements
- Brand + value prop, minimal text

## Ratings & Reviews

### Rating Velocity Targets
- New apps: aim for 100+ ratings in first 30 days
- Established apps: maintain 4.5+ average
- Reply to negative reviews within 24 hours

### Review Prompting Strategy
- Trigger after positive in-app moment (completed workout, achievement)
- Use native StoreKit/Play In-App Review API
- Limit prompts: 3x per year per user (Apple guideline)
- Never incentivize reviews (policy violation)

### Review Keyword Mining
- Analyze competitor reviews for language patterns
- Users describe features in their words
- Extract common pain points for positioning

## Localization

### High-Value Markets
1. United States (base)
2. United Kingdom (minimal changes)
3. Germany (high spending, requires translation)
4. Japan (high ARPU, requires cultural adaptation)
5. South Korea, France, Brazil, Spain

### Localization Checklist
- [ ] Translate title and subtitle
- [ ] Research local keywords (not direct translation)
- [ ] Localize screenshots (text overlays)
- [ ] Localize app preview video captions
- [ ] Local social proof (local press, influencers)

## Conversion Rate Optimization

### A/B Testing (Google Play Experiments)
- Test one element at a time
- Minimum 7 days per test
- Need 90% confidence before declaring winner
- Priority order: icon > screenshots > title > description

### Icon Testing
- Test color variations
- Test with/without border
- Test character vs. abstract
- Ensure visibility at small sizes (29px)

## Category Strategy

### Primary Category
- Choose category with highest relevance
- Consider competition density
- "Health & Fitness" vs. "Lifestyle" trade-offs

### Secondary Category (Apple)
- Adds additional browse visibility
- Can rank for both category charts

## Algorithm Updates to Watch

### Apple (Recent Changes)
- In-app events now indexed (2023)
- Custom product pages rankable (2024)
- Privacy nutrition labels affect trust signals

### Google Play (Recent Changes)
- Data safety section (2022)
- Target API requirements affect visibility
- LiveOps cards for engagement

## Measurement

### Key Metrics
| Metric | Target | Tool |
|--------|--------|------|
| Keyword rankings | Top 10 for priority terms | AppTweak |
| Impression to view rate | >5% | App Store Connect |
| View to install rate | >30% | App Store Connect |
| Install to trial rate | >40% | Internal analytics |

### Reporting Cadence
- Weekly: keyword rank changes, rating changes
- Monthly: conversion rates, category rank
- Quarterly: full competitive audit

## Common ASO Mistakes

1. **Keyword stuffing in title** (hurts brand perception)
2. **Ignoring subtitle** (high-value real estate)
3. **Generic screenshots** (feature list instead of benefits)
4. **Neglecting ratings** (anything below 4.0 hurts conversion)
5. **Set and forget** (algorithms change, competitors adapt)
6. **Duplicate keywords** (wastes limited character count)
7. **Direct translation** (keywords don't translate)

## ASO + AI Visibility Synergy

App store content feeds AI assistants:
- Siri uses App Store metadata for app recommendations
- Google Assistant uses Play Store data for suggestions
- ChatGPT references app descriptions when recommending tools
- Perplexity cites app store pages for "best app for X" queries

**Optimization for AI citation:**
- Include specific use cases in description
- Add comparison language ("unlike other apps...")
- Mention integrations (Siri, Shortcuts, Google Assistant)
- Include stats and social proof that AI can cite
