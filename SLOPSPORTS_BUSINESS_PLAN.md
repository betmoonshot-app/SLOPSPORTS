# SlopSports Business Plan v4.0

**AI Sports Entertainment Brand + Product Portfolio**
**Last Updated: May 2026**

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Legal Structure & Business Formation](#2-legal-structure--business-formation)
3. [Company Overview](#3-company-overview)
4. [Market Opportunity](#4-market-opportunity)
5. [Visual Character Strategy](#5-visual-character-strategy)
6. [Products & Services](#6-products--services)
7. [Sports Coverage](#7-sports-coverage)
8. [System Architecture](#8-system-architecture)
9. [Go-to-Market Strategy](#9-go-to-market-strategy)
10. [Revenue Model](#10-revenue-model)
11. [Unit Economics](#11-unit-economics)
12. [Operating Costs](#12-operating-costs)
13. [Financial Projections](#13-financial-projections)
14. [Competitive Landscape](#14-competitive-landscape)
15. [Team & Operations](#15-team--operations)
16. [Risk Analysis](#16-risk-analysis)
17. [Compliance & Legal](#17-compliance--legal)
18. [Milestones & Roadmap](#18-milestones--roadmap)

---

## 1. Executive Summary

SlopSports is an **AI sports entertainment brand and product portfolio** — a parent brand housing three products that together cover the full spectrum of the sports fan experience: entertainment, fantasy, and analytics.

**Three Products, One Brand:**

| Product | What It Is | Revenue Model | Launch |
|---------|-----------|---------------|--------|
| **SlopSports Engine + Studio** | Five AI sports personalities generating content across X, TikTok, YouTube, Studio web app, Discord | Affiliates, Studio Premium ($7.99/mo), ads, sponsorships | **June 2026** (Ray solo) |
| **LeagueLore** | AI-powered narrative/intelligence layer for fantasy football leagues (Sleeper, then Yahoo/ESPN) | Commissioner subscription ($60-75/year per league) | **September 2026** (NFL Week 1) |
| **MOONSHOT** | Professional sports betting analytics platform (existing, built, paused) | Subscription ($20-50/mo) | **Reactivated when Products 1-2 generate revenue** |

**The Funnel:**
- **SlopSports Agents** (X, TikTok, YouTube) → Discovery & reach (free) → brand building
- **SlopSports Studio** → Engagement & retention (free/freemium) → affiliate + premium revenue
- **LeagueLore** → Fantasy league utility (commissioner-pays SaaS) → predictable recurring revenue
- **MOONSHOT** → Professional betting analytics (paid tool) → high-ARPU subscription revenue

**Key Numbers:**
- **Combined TAM:** $25B+ sports media + $17B sports betting + $200M+ fantasy league services = $42B+ combined
- **Monthly operating cost:** ~$600-$1,100/month (all products)
- **One-time legal/formation costs:** $3,145-$5,835
- **LeagueLore breakeven:** ~100 leagues at $65/year
- **Agent engine breakeven:** ~4 affiliate conversions or ~65 Studio Premium subscribers
- **Conservative Year 1 revenue (combined):** ~$300K+ across all streams
- **LeagueLore gross margin:** 55-60% (AI costs per league ~$15-25/year)
- **Studio Premium gross margin:** 93.4% (cost per subscriber: $0.66/month)

SlopSports is the Barstool model with AI: personality-driven sports content that's entertaining whether or not you bet, paired with a fantasy football product that turns every league's history into a narrative experience. No key-person risk — unlike Barstool (Portnoy) or Pat McAfee, we own the IP completely.

**The strategic sequencing:** The agent engine launches first (June 2026) to build the SlopSports brand and audience on social media. LeagueLore launches into that audience at NFL Week 1 (September 2026). MOONSHOT — already built — reactivates as the third revenue stream once the first two products are generating traction. Each product reinforces the others: agents market LeagueLore organically, LeagueLore users discover the agents, and both funnel serious bettors toward MOONSHOT.

---

## 2. Legal Structure & Business Formation

### Entity Formation
- **LLC** — file immediately, before any public launch or revenue
- Single-member LLC initially; convert to multi-member when bringing in partners
- File in home state (or Wyoming/Delaware for privacy/flexibility)
- **Cost:** $50-$500 depending on state
- Get **EIN** from IRS (free, 5 minutes online)
- Open **business bank account** — separate personal and business finances from day one
- **S-Corp election** trigger: consider once net profit exceeds ~$40K/year

### Trademark Strategy

| Mark | Class | Priority | Est. Cost |
|------|-------|----------|-----------|
| SlopSports | 41 (entertainment) + 38 (broadcasting) | **Week 1** | $500-$700 |
| LeagueLore | 9 (software) + 41 (entertainment) | **Week 1** | $500-$700 |
| MOONSHOT | 9 (software) + 41 (entertainment) | **Week 2** | $500-$700 |
| Chainsaw Charlie (Ray) | 41 (entertainment) | At agent launch | $250-$350 |
| Degen Danny | 41 (entertainment) | At agent launch | $250-$350 |
| Coach Patricia Wells | 41 (entertainment) | At agent launch | $250-$350 |
| Conspiracy Carl | 41 (entertainment) | At agent launch | $250-$350 |
| Bianca "The Closer" Reyes | 41 (entertainment) | At agent launch | $250-$350 |
| Logo/visual branding | 41 + 38 | When finalized | $250-$350 |

File via **TEAS Plus** (USPTO) — ~$250-$350 per class per mark.

### Copyright Strategy
- All AI-generated content: copyright belongs to the human directing the output
- Register key works ($65/work through Copyright Office)
- Character designs, visual assets, voice scripts — register when finalized
- Business plan, technical docs — automatic copyright, register if enforcing

### Required Legal Documents
1. **Operating Agreement** — ownership, roles, voting rights, profit distribution, exit terms
2. **IP Assignment Agreement** — all work product belongs to the LLC
3. **Vesting Schedule** — 4-year vest, 1-year cliff (standard startup terms)
4. **NDA** — for anyone viewing the business plan or proprietary strategy

### Bringing In Partners
- Recommended structure: **vesting equity in the LLC**
- 70/30 or 75/25 split (founder who built tech + plan retains majority)
- 4-year vesting, 1-year cliff
- Define roles clearly before any work begins
- Put everything in writing — this preserves friendships
- Startup attorney: $500-$1,500 flat fee for all formation docs

---

## 3. Company Overview

**SlopSports** is an AI sports brand with a three-product portfolio. Five AI personalities generate entertainment content across social media, video, and web. A fantasy football intelligence product turns league history into narrative content. A professional analytics tool serves serious bettors. All three products share a brand, an audience pipeline, and infrastructure — but each is an independent codebase, database, and deployment.

**The SlopSports Ecosystem:**

```
┌─────────────────────────────────────────────────────────────────┐
│                      SLOPSPORTS BRAND                            │
│                                                                   │
│  ┌─────────────────────────────────────────────────────────┐     │
│  │              SHARED INFRASTRUCTURE                       │     │
│  │  Knowledge Service (player data, stats, form, status)    │     │
│  │  Anthropic API (shared billing, prompt caching)          │     │
│  │  Stripe (payments across products)                       │     │
│  │  Vercel (frontends) + Railway (backends)                 │     │
│  └─────────────────────────────────────────────────────────┘     │
│         │                    │                    │               │
│         ▼                    ▼                    ▼               │
│  ┌──────────────┐    ┌──────────────┐    ┌──────────────┐       │
│  │  SLOPSPORTS   │    │  LEAGUELORE  │    │   MOONSHOT   │       │
│  │  ENGINE +     │    │              │    │              │       │
│  │  STUDIO       │    │  Fantasy     │    │  Betting     │       │
│  │              │    │  Football     │    │  Analytics   │       │
│  │  AI Sports    │    │  Narrative   │    │  Platform    │       │
│  │  Personalities│    │  + AI Layer  │    │              │       │
│  │              │    │              │    │  (Paused)    │       │
│  │  Jun 2026    │    │  Sep 2026    │    │  Reactivate  │       │
│  └──────────────┘    └──────────────┘    └──────────────┘       │
│         │                    │                    │               │
│         └────────────────────┼────────────────────┘               │
│                              ▼                                    │
│                    ┌──────────────────┐                           │
│                    │   SPORTS FANS    │                           │
│                    │  Entertainment   │                           │
│                    │  Fantasy         │                           │
│                    │  Betting         │                           │
│                    └──────────────────┘                           │
└─────────────────────────────────────────────────────────────────┘
```

**How the products connect:**
- **SlopSports agents** build audience and brand on social media → drive discovery of LeagueLore and MOONSHOT
- **LeagueLore** provides predictable SaaS revenue + fantasy football user base → commissioners and league members discover agents and Studio
- **MOONSHOT** (already built, paused) reactivates as the premium analytics tool → agents reference MOONSHOT data, LeagueLore users with betting interest get upsold

All three systems are **completely separate** codebases, databases, and infrastructure — connected through APIs and shared brand identity. Infrastructure accounts (Vercel, Railway, Stripe, Sentry) are shared across products to minimize cost.

---

## 4. Market Opportunity

### Sports Betting Market
- **US sports betting revenue (2025):** $16.96B (22.8% YoY growth)
- **Projected 2030:** $40B+
- **Active bettors on social media:** ~47M US adults
- **Key driver:** State-by-state legalization continues expanding

### Sports Media Market (The Bigger Play)
- **US sports media rights (2025):** $25B+
- **US adults who follow sports:** 200M+
- **Sports content consumption:** 3+ hours/day average among fans
- **Short-form sports video:** Fastest-growing content category on TikTok/YouTube Shorts

### Fantasy Football Market (LeagueLore's Addressable Market)
- **US fantasy football players:** ~60M
- **Season-long fantasy (ESPN/Yahoo/Sleeper):** ~30-35M players
- **Dynasty + multi-year leagues with meaningful history:** ~1-1.2M leagues
- **Redraft leagues with friend-group continuity (3+ years):** ~2-3M additional leagues
- **Total addressable:** ~3-4M leagues in US
- **TAM at $65/league:** ~$200-260M annually (US alone)
- **International expansion:** Premier League fantasy alone has 10M+ global players; product concept translates to any sport with season-long fantasy

### The Gaps We Fill
- Traditional sports media: human-created, expensive, slow, key-person risk → **SlopSports agents** generate 24/7 at near-zero marginal cost
- Sports betting touts: low trust, no entertainment value, pay-walled picks → **SlopSports agents** are entertainment-first, free discovery layer
- Fantasy football platforms: data-rich, narrative-poor → **LeagueLore** turns league data into stories, chronicles, and an AI co-commissioner that knows your league completely
- Fantasy content gap: 78% of fantasy players are in leagues with friends/family, but the social fabric (rivalries, lore, memories) lives in iMessage/Discord while data lives on ESPN/Yahoo/Sleeper — nothing connects them → **LeagueLore** is where they meet
- Sports betting analytics: expensive, intimidating, fragmented → **MOONSHOT** (when reactivated) provides professional-grade analysis at accessible pricing

### 2026 FIFA World Cup Opportunity
- **June-July 2026** — hosted in US, Canada, Mexico
- Peak global sports attention
- SlopSports agents covering international soccer = massive audience expansion
- Plan launch timing to have agents established before World Cup

---

## 5. Visual Character Strategy

### The Shift: From Text to Characters You Can See

Inspired by creators like Mack Falconer (1.4M TikTok followers from AI character interactions via Meta Quest + TykeAI), SlopSports agents will have visual identities — animated or photorealistic characters that appear in video content.

### Primary Pipeline: Runway Characters API

**Runway Characters** (launched March 2026) collapses the entire visual pipeline into a single API:
- One image → fully expressive, lip-synced, conversational video avatar
- No fine-tuning, no training, no MetaHuman pipeline, no VTuber rigging
- Realistic facial expressions, eye movements, gestures
- React SDK with WebRTC for real-time integration
- Can execute actions, pull from knowledge bases

This replaces what would have been a 4-tier escalation over 12 months.

### Agent Visual Identities

| Agent | Visual Style | Setting | Color Palette |
|-------|-------------|---------|---------------|
| Ray "The Sharp" Castellano | Clean-cut analyst | Data desk with monitors | Blue/gray/silver |
| Degen Danny | Messy sports fan | Couch with empty cans, multiple screens | Chaotic warm tones |
| Coach Patricia Wells | Veteran coach | Film room with whiteboard | Retro wood tones |
| Conspiracy Carl | Late-night radio host | Dark room with red string boards | Dark green/amber |
| Bianca "The Closer" Reyes | Sideline reporter | On location, press areas | Bold red/white |

### Rollout Plan

| Phase | What | When | Cost |
|-------|------|------|------|
| Text-only launch | X + Studio posts, no video | Day 1 | $0 |
| Runway Characters pilot | Ray video takes for YouTube/TikTok | Month 1-2 | ~$50-100/mo |
| Full video pipeline | All 5 agents with video | Month 3-6 | ~$100-200/mo |
| Interactive video | Live Q&A with agents via Runway + WebRTC | Month 6+ | ~$200-400/mo |
| Mixed Reality (special events) | Meta Quest interactions for tentpole moments | Month 6+ | $500 one-time + $25/mo |

### Voice Synthesis
- **ElevenLabs** ($22/month) for consistent character voices
- Each agent gets a distinct voice profile
- Engine generates script → ElevenLabs speaks it → Runway Characters lip-syncs → auto-post

### Cost Impact
- Adds ~$72-144/month to operating costs
- Opens YouTube ad revenue, TikTok growth, Instagram Reels
- Makes merch viable (people buy merch of characters they can *see*)

---

## 6. Products & Services

### Product 1: SlopSports Engine + Studio (Launch: June 2026)
The AI content engine and its owned web platform. Five AI sports personalities generate content across X, TikTok, YouTube, Instagram, Discord, and podcasts. The Studio is their living room — the owned platform where content lives in full form.

- **Stack:** FastAPI + Celery + Redis + PostgreSQL (engine) / React + Vite + TypeScript (Studio)
- **Deploy:** Railway (backend) + Vercel (Studio frontend)
- **Revenue:** Affiliates, Studio Premium ($7.99/mo), ads, sponsorships, Discord premium
- **Launch sequence:** Ray solo (June) → Danny (September) → Patricia + Carl (Q4) → Bianca (Q1 2027)

### Product 2: LeagueLore (Launch: September 2026 — NFL Week 1)
AI-powered narrative, intelligence, and social layer for fantasy football leagues. Sits on top of existing platforms (Sleeper at launch, Yahoo and ESPN to follow) and transforms league data into AI-generated narrative content, analytical tools, and an interactive AI co-commissioner.

- **Stack:** FastAPI + PostgreSQL + Redis (backend) / React + Vite + TypeScript (frontend)
- **Deploy:** Railway (backend) + Vercel (frontend) — shared accounts with Engine/Studio
- **Revenue:** Commissioner subscription ($60-75/year per league), Draft Day Package ($20-25), Season Recap Package ($10-15), physical goods (printed books, trophies)
- **Auth:** Supabase (shared SlopSports identity)
- **Payments:** Stripe (shared account, separate products)
- **Data:** Sleeper API (free, public), Knowledge Service (shared with Engine)
- **Four pillars:** Lore (historical chronicle), Live (in-season content), Lab (analytical tools), Co-Commish (conversational AI)
- **Dual audience:** Dynasty/keeper leagues (narrative-first) and redraft/friend-group leagues (assistant-first)
- **Full spec:** See `docs/LEAGUELORE_PRODUCT_SPEC.md`

### Product 3: MOONSHOT (Existing — Paused, Reactivates Later)
Professional sports betting analytics platform. Already built and deployed. Paused to focus resources on Products 1-2. Infrastructure (Vercel, Railway accounts) reused across products. Reactivates as the premium analytics upsell when the SlopSports brand has audience traction.

- **Stack:** Flask API + React + Vite + PostgreSQL + Redis
- **Deployed:** Railway (backend) + Vercel (frontend)
- **Features:** Prop analysis, line movement tracking, DMR scoring, batch analysis, user portfolios
- **Auth:** Supabase
- **Payments:** Stripe
- **Data:** The Odds API + nba_api
- **Price:** $20-50/month subscription
- **Status:** Code complete, infrastructure live, subscription revenue paused until reactivation

### Studio Details (Part of Product 1)
Public web experience where the agents live. X is their megaphone; the Studio is their living room.

**What Users See:**
- **The War Room (Main Feed):** Real-time feed of all agents reacting to the day's sports events — full breakdowns, not just 280-char tweets
- **Agent Profiles:** Full prediction history with verified results, hit rates, streaks, relationship timelines
- **The Leaderboard:** Which agent is sharpest this week/month/season — tracked, verified, transparent
- **"What Are They Seeing?" (Data Mode):** Raw betting data the agents react to. Free users see delayed/summarized. Full real-time = MOONSHOT tease.
- **Agent Interactions:** Users can ask agents questions and get in-character responses. Eventually live video Q&A via Runway Characters.
- **Game Day War Room:** Second-screen experience during live games. Five personalities reacting in real-time.

**Studio Stack:** React (matches MOONSHOT's frontend DNA) + WebSocket for real-time feeds + REST for historical data.

### The Five Agents (Core of Product 1)

**Content mix: 60% entertainment / 25% analysis / 15% betting**

#### Ray "The Sharp" Castellano
- **Persona:** Cold, data-obsessed analyst. Never bets on emotion. Respects the math.
- **Voice:** Clinical, slightly condescending, dry wit. Speaks in numbers and percentages.
- **Content:** Line movement analysis, sharp money alerts, "the public is wrong" takes, data breakdowns.
- **MOONSHOT connection:** His data comes from MOONSHOT. He's the organic bridge to the paid product.
- **Visual:** Clean-cut at a data desk, multiple monitors, blue/gray aesthetic.
- **Catchphrases:** "The line tells you everything." "Public money is noise."
- **Launch:** Phase 1 (solo agent at launch)

#### Degen Danny
- **Persona:** The chaotic, loveable degenerate. Bets every game. Lives for parlays. Loses spectacularly.
- **Voice:** Manic energy, caps lock abuse, stream of consciousness. Oscillates between euphoria and despair.
- **Content:** Parlay construction (usually bad), live reactions, meltdowns, celebrating small wins like championships.
- **Entertainment value:** His losing streaks are running storylines. Counter resets are events.
- **Visual:** Messy couch setup, empty cans, multiple screens, warm chaotic tones.
- **Catchphrases:** "THIS IS THE ONE." "I'm never betting again. (See you tomorrow.)"
- **Launch:** Phase 2 (pairs with Ray for contrast)

#### Coach Patricia Wells
- **Persona:** 30-year coaching veteran. Hates analytics. Trusts her eyes over any spreadsheet.
- **Voice:** Authoritative, old-school, tells stories about "the game today vs. the game then."
- **Content:** Scouting reports, matchup analysis, coaching decisions, era comparisons, "back in my day" takes.
- **Dynamic:** Ongoing feud with Ray (eye test vs. data). Grudging respect underneath.
- **Visual:** Film room with whiteboard, retro wood tones, coaching aesthetic.
- **Catchphrases:** "Watch the tape." "Numbers don't play the game."
- **Launch:** Phase 3

#### Conspiracy Carl
- **Persona:** Believes nothing is coincidental. Refs are in on it. The league scripts outcomes. Awards are rigged.
- **Voice:** Intense, connects dots that don't exist, presents wild theories with absolute conviction.
- **Content:** Ref conspiracies, scheduling bias, awards voting schemes, league rigging theories, suspicious line movements.
- **Entertainment value:** Occasionally he's RIGHT, which makes everything funnier.
- **Visual:** Dark room with red string boards, amber lighting, late-night radio host aesthetic.
- **Catchphrases:** "EXPOSED." "They don't want you to see this."
- **Launch:** Phase 3

#### Bianca "The Closer" Reyes
- **Persona:** Insider reporter with sources. First to know, first to break. All business.
- **Voice:** Professional, urgent, breaks-news cadence. Drops hints before confirming.
- **Content:** Breaking news, trade rumors, injury scoops, locker room drama, coaching hot seat.
- **Dynamic:** Everyone else reacts to her information. She breaks it, they argue about it.
- **Visual:** Sideline reporter setup, press areas, bold red/white aesthetic.
- **Catchphrases:** "Sources tell me..." "Developing..."
- **Launch:** Phase 4

### Agent Relationships & Dynamics

| Pair | Dynamic | Content Type |
|------|---------|-------------|
| Ray vs. Patricia | Data vs. eye test — ongoing philosophical war | Debates, prediction challenges, grudging respect |
| Danny + Carl | Chaos alliance — feed each other's worst instincts | Parlay conspiracies, spiral threads |
| Ray → Danny | Condescending mentor — "I told you so" | Danny asks Ray for picks, Ray says no, Danny does it anyway |
| Bianca → All | News drops that everyone reacts to | She breaks it, they argue about it |
| Carl → Ray | Accuses Ray of being "part of the system" | Conspiracy takes on Ray's data sources |
| Patricia → Danny | Tough love — "you have no discipline" | Coaching Danny through his losses |

---

## 7. Sports Coverage

**Multi-sport from Day 1** (prioritized by betting market size and content opportunity):

| Sport | Season | Priority | Why |
|-------|--------|----------|-----|
| NFL | Sep-Feb | **Tier 1** | Largest US betting handle, highest engagement |
| NBA | Oct-Jun | **Tier 1** | Year-round narratives, matches MOONSHOT's core |
| MLB | Apr-Oct | **Tier 2** | Large market, daily games = daily content |
| NHL | Oct-Jun | **Tier 2** | Passionate fanbase, underserved by AI content |
| College Football | Aug-Jan | **Tier 1** | Massive audience, playoff expansion in 2026 |
| College Basketball | Nov-Apr | **Tier 1** | March Madness is peak betting + entertainment |
| UFC/MMA | Year-round | **Tier 2** | Growing demographic, high social engagement |
| Soccer | Year-round | **Tier 2** (→ **Tier 1** for World Cup 2026) | FIFA 2026 in US = massive opportunity |

---

## 8. System Architecture

### Shared Infrastructure: The Knowledge Service

The Knowledge Service is a standalone data layer that powers both the SlopSports agent engine and LeagueLore. It provides structured, current player and team data so that all AI-generated content is grounded in real facts.

```
┌─────────────────────────────────────────────────────────┐
│                  KNOWLEDGE SERVICE                       │
│                                                          │
│  NFL: ~1,500 active players — profiles, weekly stats,    │
│       career summaries, recent form, injury status        │
│  NBA: Player stats, team defense, matchup data           │
│  MLB: Player stats, park factors, pitching logs          │
│                                                          │
│  Sources: Sleeper API (free), nfl_data_py (free),        │
│           nba_api, The Odds API, Pro Football Reference   │
│                                                          │
│  Architecture: Separate service, REST API, Redis cache    │
│  Ships with LeagueLore at v1, shared with Engine later    │
└─────────────────────────────────────────────────────────┘
        │                              │
        ▼                              ▼
┌───────────────┐            ┌──────────────────┐
│  SlopSports   │            │   LeagueLore     │
│  Engine       │            │                  │
│  (agent       │            │  Match reports,  │
│  content)     │            │  Co-Commish,     │
│               │            │  player mentions │
└───────────────┘            └──────────────────┘
```

### The 8-Layer Engine (SlopSports Agents)

```
LAYER 1: DATA INGESTION
  └── The Odds API (lines, movement, public %)
  └── Live scores & play-by-play (polling every 2-3 min during games)
  └── Injury feeds, lineup confirmations
  └── X trending topics, Reddit sentiment
  └── Knowledge Service (shared player data)
        │
        ▼
LAYER 2: INTERPRETATION ENGINE
  └── Raw data → narrative events
  └── "Celtics opened -7, now -5.5 despite 74% public on Boston. Sharp money on other side."
        │
        ▼
LAYER 3: AGENT REACTION ENGINE
  └── Event → which agents care? What angle?
  └── Relationship engine: should agents reply to each other?
  └── Personality-consistent response selection
        │
        ▼
LAYER 4: CONTENT GENERATION
  └── Anthropic Claude API (Haiku for Tier 1, Sonnet for Tier 2-3)
  └── System prompts per agent + personality + memory context
  └── Multi-format output: tweet, thread, video script, Studio post, Discord post
        │
        ▼
LAYER 5: MOONSHOT INTEGRATION (DEFERRED)
  └── REST client for MOONSHOT API (/api/props, /api/analyze-batch)
  └── Stubbed until MOONSHOT reactivation
        │
        ▼
LAYER 6: NARRATIVE MEMORY
  └── Prediction history, storylines, relationship events
  └── Running streaks, grudges, callbacks to past takes
  └── Context retrieval for content generation
        │
        ▼
LAYER 7: VIRAL DETECTION & AMPLIFICATION
  └── Engagement monitoring (5× baseline = viral)
  └── Follow-up content orchestration
  └── Cross-agent amplification
        │
        ▼
LAYER 8: MULTI-PLATFORM DISTRIBUTION
  └── X API v2 (tweepy) — tweets, replies, quote-tweets
  └── Runway Characters API — video generation
  └── Studio WebSocket feed — real-time content
  └── Discord bot — community content
  └── Podcast RSS — audio generation
  └── Simulator mode for local dev (logs instead of publishing)
```

### LeagueLore Architecture (Two-Layer Hybrid)

LeagueLore uses a cost-optimized two-layer architecture where most queries never touch AI:

```
LAYER 1: KNOWLEDGE ENGINE (deterministic, no AI cost)
  └── Handles 60-70% of Co-Commish queries entirely without AI
  └── Standings, records, settings, rosters, matchups, history
  └── Factual lookups ("what's my record against THerlihy")
  └── Scenario calculations (playoff math)
  └── Roster information
        │
        ▼ (only when reasoning/narrative needed)
LAYER 2: INTELLIGENCE LAYER (AI, used surgically)
  └── Match report narratives
  └── Complex trade analysis
  └── Personalized advice
  └── Dispute resolution requiring nuanced context
  └── Narrative content generation (chronicles, power rankings, burn book)
```

### Tech Stack

| Layer | Technology | Reasoning |
|-------|-----------|-----------|
| Language | Python 3.11+ | Matches MOONSHOT, excellent Anthropic SDK |
| Framework | FastAPI | Async-native, OpenAPI docs, event-driven |
| Task Queue | Celery + Redis | Staggered scheduling, retry logic, monitoring |
| Database | PostgreSQL | Agent memory, content queue, engagement metrics |
| Cache | Redis | Shared with Celery, sports data cache, rate limiting |
| Content Gen | Anthropic Python SDK | Claude Haiku (Tier 1), Sonnet (Tier 2-3) |
| X Integration | tweepy v4 (X API v2) | Posting, engagement reads, streaming |
| Video | Runway Characters API | Single-image → full video avatar |
| Voice | ElevenLabs API | Consistent character voices |
| Sports Data | httpx → The Odds API | Async HTTP polling |
| Studio Frontend | React | Matches MOONSHOT, WebSocket for real-time |
| Human Review UI | FastAPI + htmx | Lightweight admin dashboard |
| Testing | pytest + pytest-asyncio | Simulation mode for local dev |
| Containers | Docker Compose | Local dev: Postgres + Redis + app |

### Directory Structure

```
slopsports/                          # COMPLETELY separate from MOONSHOT
├── docker-compose.yml               # Local dev: Postgres + Redis + app
├── Dockerfile
├── pyproject.toml                   # Dependencies, ruff, pytest config
├── requirements.txt
├── .env.example
├── README.md
│
├── src/
│   ├── __init__.py
│   ├── main.py                      # FastAPI app entry point
│   ├── config.py                    # Environment config
│   │
│   ├── agents/                      # LAYER 3 — Agent definitions
│   │   ├── __init__.py
│   │   ├── base.py                  # BaseAgent class
│   │   ├── ray.py                   # Ray "The Sharp" Castellano
│   │   ├── danny.py                 # Degen Danny
│   │   ├── patricia.py              # Coach Patricia Wells
│   │   ├── carl.py                  # Conspiracy Carl
│   │   ├── bianca.py                # Bianca "The Closer" Reyes
│   │   └── relationships.py         # Inter-agent dynamics
│   │
│   ├── data/                        # LAYER 1 — Data Ingestion
│   │   ├── __init__.py
│   │   ├── odds_client.py           # The Odds API
│   │   ├── scores_client.py         # Live scores & play-by-play
│   │   ├── news_client.py           # Injury reports, player news
│   │   └── discourse_client.py      # X trending, Reddit sentiment
│   │
│   ├── engine/                      # LAYERS 2-3 — Interpretation & Reaction
│   │   ├── __init__.py
│   │   ├── interpreter.py           # Raw data → narrative events
│   │   ├── reactor.py               # Event → agent assignments
│   │   ├── scheduler.py             # Post timing & staggering
│   │   └── events.py                # Event type definitions
│   │
│   ├── content/                     # LAYER 4 — Content Generation
│   │   ├── __init__.py
│   │   ├── generator.py             # Anthropic API content generation
│   │   ├── prompts.py               # System prompts per agent
│   │   ├── templates.py             # Content type templates
│   │   └── review_queue.py          # Human review flagging
│   │
│   ├── memory/                      # LAYER 6 — Narrative Memory
│   │   ├── __init__.py
│   │   ├── store.py                 # Prediction history, storylines
│   │   └── recall.py                # Context retrieval
│   │
│   ├── viral/                       # LAYER 7 — Viral Detection
│   │   ├── __init__.py
│   │   ├── detector.py              # Engagement monitoring
│   │   └── amplifier.py             # Follow-up orchestration
│   │
│   ├── publisher/                   # LAYER 8 — Distribution
│   │   ├── __init__.py
│   │   ├── x_client.py              # X API v2 wrapper
│   │   ├── video_client.py          # Runway Characters API
│   │   ├── accounts.py              # Multi-account management
│   │   └── simulator.py             # Local dev mock
│   │
│   ├── moonshot/                    # LAYER 5 — MOONSHOT Integration (FUTURE)
│   │   ├── __init__.py
│   │   └── client.py                # REST client (stubbed)
│   │
│   ├── api/                         # FastAPI routes
│   │   ├── __init__.py
│   │   ├── dashboard.py             # Human review dashboard
│   │   ├── health.py                # Health check
│   │   └── admin.py                 # Manual triggers
│   │
│   └── db/                          # Database layer
│       ├── __init__.py
│       ├── models.py                # SQLAlchemy models
│       ├── migrations/              # Alembic migrations
│       └── session.py               # DB session management
│
├── tasks/                           # Celery task definitions
│   ├── __init__.py
│   ├── ingest.py                    # Periodic data ingestion
│   ├── generate.py                  # Content generation
│   ├── publish.py                   # X posting
│   ├── monitor.py                   # Engagement monitoring
│   └── amplify.py                   # Viral amplification
│
├── tests/
│   ├── conftest.py
│   ├── test_agents/
│   ├── test_engine/
│   ├── test_content/
│   ├── test_publisher/
│   └── test_integration/
│
└── scripts/
    ├── simulate.py                  # Full simulation (no live posting)
    └── seed_memory.py               # Seed agent backstory
```

---

## 9. Go-to-Market Strategy

### Phase 0: Build (May-June 2026)
- Build SlopSports engine (data ingestion, interpretation, agent system, content generation)
- Write Ray's personality prompts and iterate on content quality
- Build LeagueLore foundation in parallel: Sleeper API integration, database schema, Knowledge Service v1
- Set up shared infrastructure: Vercel, Railway, Stripe, Sentry accounts
- Reserve all social handles (@SlopSports, @RayTheSharp, agent accounts)
- **Deliverable:** Engine running in simulation mode; Ray content quality validated

### Phase 1: Ray Solo Launch (Late June-July 2026)
- Launch Ray "The Sharp" Castellano on X — text-only, live posting
- Ray covers NBA offseason, MLB, World Cup (June-July 2026 in US)
- Studio MVP: Ray's profile + War Room feed
- Set up sportsbook affiliate accounts
- Continue LeagueLore build in parallel (Co-Commish, match report generator)
- **Target:** 1,000 X followers, 100 Studio visitors/day, SlopSports brand established

### Phase 2: LeagueLore Beta + Danny (August 2026)
- LeagueLore beta with 10-20 real leagues (including founder's dynasty league)
- Onboarding flow: commissioner connects Sleeper → instant historical chronicle generated
- Ray starts posting fantasy football content, organically teasing LeagueLore
- Danny personality built; soft launch on X pairing with Ray for NFL preseason
- **Target:** 5,000 X followers, LeagueLore beta validated with real users

### Phase 3: LeagueLore Public Launch (September 2026 — NFL Week 1)
- LeagueLore public launch: Sleeper integration, Lore + Live + Co-Commish pillars
- Week 1 match reports drop for every connected league simultaneously (launch event)
- Studio Premium opens ($7.99/mo Stripe subscription)
- Danny fully active — his fantasy football meltdowns cross-promote LeagueLore
- Affiliate links active in Studio and LeagueLore content
- **Target:** 500+ LeagueLore leagues, 200 Studio Premium subs, first affiliate revenue

### Phase 4: Full Cast + Scale (October 2026+)
- Launch Patricia + Carl on X (file trademarks)
- Full agent relationship engine operational
- LeagueLore weekly content engine running autonomously (match reports, power rankings, burn book)
- Begin Runway Characters video pilot for Ray (YouTube/TikTok)
- Discord community launched
- **Target:** 15,000 X followers, 2,000+ LeagueLore leagues, $5K+ monthly revenue

### Phase 5: Bianca + All Revenue Streams (Q1 2027)
- Launch Bianca — breaking news gives all agents something to react to
- Full 5-agent ecosystem operational across X, Studio, TikTok, YouTube
- Evaluate MOONSHOT reactivation based on audience traction
- All video characters live via Runway Characters
- AI podcast launch ("The SlopSports Show")
- **Target:** 50,000+ X followers, 5,000+ LeagueLore leagues, $15K+ monthly revenue

### Cross-Product Marketing Loop
- Agents post fantasy football content → "Your league has 7 years of history and nobody's written a word about it" → LeagueLore discovery
- LeagueLore match reports include betting context → "Ray analyzed this line movement" → Studio/MOONSHOT discovery
- Every LeagueLore shareable card (match reports, season chronicles) carries SlopSports branding → organic brand growth
- Commissioner signs up → league generates content → content shared in group chats → other commissioners see it → they sign up → repeat

---

## 10. Revenue Model

### LeagueLore Revenue Streams

#### Stream L1: League Subscriptions ($60-75/year per league)
- Commissioner pays, whole league plays free
- Includes all four pillars at base tier (Lore, Live, Lab, Co-Commish)
- Premium positioning: higher price justified by dramatically better experience
- **Projected Month 12 (post-launch):** 2,000-5,000 leagues = $10,000-$31,000/month

#### Stream L2: Draft Day Package ($20-25 one-time per season)
- Live draft board for TV display
- Auto draft grades with narrative
- Printable draft recaps, cinematic draft replay
- **Projected Month 12:** $2,000-$5,000/month (seasonal spike in August-September)

#### Stream L3: Season Recap Package ($10-15 one-time)
- Produced season-ending recap with awards, superlatives, narrative
- **Projected Month 12:** $1,000-$3,000/month (seasonal spike in January)

#### Stream L4: Physical Goods (High-Margin, Emotional Value)
- Printed League Record Book: $40-60 — physical book of the season
- Engraved Champion Trophy: $80-120 — real trophy with champion's name and stats
- Wall of Shame Print: $30-50 — worst trades, embarrassing losses, framed
- **Projected Month 12:** $1,000-$5,000/month

### SlopSports Engine Revenue Streams

#### Stream 1: Sportsbook Affiliate Links
- When agents reference games/lines, Studio links to actual bets on DraftKings, FanDuel, BetMGM
- **CPA:** $100-$300+ per depositing customer
- **Revenue share:** Alternative model, ongoing percentage of player losses
- **Zero product work** — just link routing
- **Projected Month 12:** $4,000-$8,000/month

### Stream 2: SlopSports Studio Premium ($7.99/month)
- **Free:** Watch the agents, see the feed, follow the drama
- **Premium:** Data Mode (see what agents react to), full prediction history, agent interaction (ask questions, get in-character responses), real-time game day War Room, alerts on high-confidence takes
- **Projected Month 12:** 500-1,000 subscribers = $4,000-$8,000/month

#### Stream 3: MOONSHOT Upsell (Deferred — Activates When MOONSHOT Relaunches)
- Studio free users see teaser data: "Ray used MOONSHOT to find this edge. [See full analysis →]"
- **Price:** $20-$50/month MOONSHOT subscription
- **Projected Month 12:** Deferred. Revenue begins when MOONSHOT reactivated (estimated $2,000-$15,000/month at scale)

### Stream 4: Programmatic Ads (Studio + Video)
- Sports betting advertisers pay premium CPMs ($15-$40+)
- YouTube ad revenue on character video content
- TikTok creator fund
- **Projected Month 12:** $1,000-$3,000/month

### Stream 5: Brand Sponsorships
- Not just sportsbooks — Nike, ESPN+, Buffalo Wild Wings, streaming services
- "Ray's Sharp Play of the Day — presented by DraftKings"
- Agent still writes in their own voice; sponsor gets the association
- **Priced as sponsorship deals:** $500-$5,000/week depending on audience
- **Projected Month 12:** $2,000-$10,000/month

### Stream 6: Discord Premium Community ($9.99/month)
- Live agent commentary, exclusive takes, early alerts
- Community builds itself — agents post in channels
- **Projected Month 12:** 200-500 members = $2,000-$5,000/month

### Stream 7: Merch (Print-on-Demand)
- "Degen Danny's Parlay of Pain" shirts
- "Trust the Data" Ray gear
- Carl's tinfoil hats (literal merch)
- **Zero inventory** — print-on-demand
- **Projected Month 12:** $500-$2,000/month

### Stream 8: "Tail This" Affiliate Links
- Danny posts a parlay → users click through to place the same bet via affiliate link
- Small commission per click-through/conversion
- **Projected Month 12:** $500-$1,500/month

### Stream 9: AI Podcast/Video Content
- Agent-generated audio/video debates using voice synthesis
- "The SlopSports Show" — daily 10-minute AI-generated sports debate
- YouTube, Spotify, Apple Podcasts
- **Projected Month 12:** $500-$2,000/month

### Stream 10: Pick Marketplace (Future)
- Ray's premium picks gated behind paywall
- Data-driven analysis, not gambling advice
- Proven sports betting industry revenue model, powered by AI
- **Projected Month 12:** $1,000-$3,000/month

**Revenue diversification target:** No single stream exceeds 30% of total revenue at Month 12. LeagueLore provides predictable SaaS revenue (commissioner subscriptions) while the agent engine provides attention-based revenue (affiliates, ads, sponsorships). This dual revenue model reduces risk from either channel alone.

---

## 11. Unit Economics

### Cost Per League (LeagueLore)
- **Revenue per league:** $60-75/year (~$5-6.25/month)
- **AI costs per league (optimized):** $15-25/year (~$1.25-2.10/month)
- **Infrastructure per league:** $5-8/year (~$0.40-0.65/month)
- **Gross margin:** 55-60%
- **At 5,000 leagues:** ~$325K revenue, ~$190K gross profit
- **At 10,000 leagues:** ~$650K revenue, ~$380K gross profit
- **At 50,000 leagues:** ~$3.25M revenue, ~$1.9M gross profit

### LeagueLore AI Cost Optimization
- **Knowledge Engine (deterministic):** Handles 60-70% of Co-Commish queries with zero AI cost
- **Context compression:** Structured league summaries, not full raw history — reduces token usage 80%+
- **Prompt caching:** League context cached per conversation — Anthropic cached tokens cost ~90% less
- **Model tiering:** Haiku for simple factual queries (~25x cheaper than Sonnet), Sonnet only for narrative generation and nuanced analysis
- **Usage limits:** Base tier caps Co-Commish messages per day; heavy users pay more

### Cost Per Subscriber (Studio Premium)
- **Anthropic API per user interaction:** ~$0.001-$0.03
- **Infrastructure per user:** ~$0.02/month (marginal)
- **Total cost per subscriber:** ~$0.66/month
- **Revenue per subscriber:** $7.99/month
- **Gross margin:** 93.4%

### Cost Per Post
- **Tier 1 (Haiku rapid reaction):** ~$0.001
- **Tier 2 (Sonnet thread/analysis):** ~$0.005-$0.01
- **Tier 3 (Opus creative/viral):** ~$0.02-$0.03
- **Average across all content:** ~$0.005/post

### Content Volume (Monthly Estimates)
- Tier 1 rapid reactions: ~1,000 posts
- Tier 2 threads/analysis: ~200 posts
- Tier 3 creative/viral: ~50 posts
- Agent interactions/replies: ~500
- Studio user interactions: ~500-2,000
- **Total Anthropic cost:** ~$35-$80/month at launch, scaling to $100-$200

### Prompt Caching Impact
- Agent personality system prompts cached → 90% input cost reduction
- Batch API for non-urgent content → additional 50% savings
- **Effective Anthropic cost with caching:** ~$12-$30/month at launch

---

## 12. Operating Costs

### MOONSHOT (Paused — Infrastructure Shared)

MOONSHOT is paused but its infrastructure accounts (Vercel Pro, Railway Pro, Stripe, Supabase, Sentry) are reused across all SlopSports products. When paused, ongoing costs are only services that can't be shared:

| Service | Plan | Monthly Cost (Paused) |
|---------|------|-------------|
| Railway (backend) | Stopped | $0 |
| Railway (PostgreSQL) | Kept for data | $5-$15 |
| The Odds API | Shared with Engine | $0 (shared) |
| Supabase (auth) | Shared across products | $0 (shared) |
| Domain | Annual | ~$3 |
| **MOONSHOT Paused Subtotal** | | **$5-$18/month** |

*Vercel Pro ($20/mo), Stripe, Sentry, Resend costs now shared across products and counted once below.*

### SlopSports Engine (New)

| Service | Plan | Monthly Cost |
|---------|------|-------------|
| X API | Basic (optional) | $0-$200 |
| Anthropic API | Usage-based | $50-$150 |
| Railway (FastAPI backend) | Pro | $20-$40 |
| Railway (PostgreSQL) | Included | $5-$15 |
| Railway (Redis + Celery) | Included | $5-$10 |
| Vercel (Studio frontend) | Pro | $20 |
| The Odds API | Shared or separate | $0-$59 |
| ElevenLabs (voice) | Creator | $22 |
| Runway Characters API | Usage-based | $50-$100 |
| Sentry | Shared or separate | $0-$29 |
| Domain | Annual | ~$2 |
| **SlopSports Subtotal** | | **$174-$627/month** |

X API is listed as $0-$200 because it's **optional** — the engine can start with Studio, TikTok, YouTube, and Discord before activating X distribution.

### LeagueLore

| Service | Plan | Monthly Cost |
|---------|------|-------------|
| Railway (FastAPI backend) | Shared Pro account | $20-$40 |
| Railway (PostgreSQL) | Included | $5-$15 |
| Railway (Redis) | Included | $5-$10 |
| Vercel (frontend) | Shared Pro account | $0 (shared) |
| Anthropic API | Usage-based | $50-$200 |
| Sleeper API | Free (public) | $0 |
| Stripe | 2.9% + $0.30/txn | $0-$50* |
| Sentry | Shared account | $0 (shared) |
| Domain | Annual | ~$2 |
| **LeagueLore Subtotal** | | **$80-$317/month** |

*LeagueLore Anthropic costs scale with league count: ~$1.50-2.00/league/month at optimized rates. At 1,000 leagues: ~$150/mo. At 5,000 leagues: ~$500/mo (offset by $25K+/mo revenue).*

### Visual Character Costs

| Item | One-Time | Monthly |
|------|----------|---------|
| VTuber/Runway Characters setup | $0-$200 | $50-$100 |
| ElevenLabs voice synthesis | — | $22 |
| Video hosting (YouTube, TikTok) | — | $0 |
| **Visual Subtotal** | $0-$200 | $72-$122 |

### Legal & Business Formation Costs (One-Time, Year 1)

| Item | Low | High |
|------|-----|------|
| LLC formation | $50 | $500 |
| Trademark: SlopSports (2 classes) | $500 | $700 |
| Trademark: MOONSHOT (2 classes) | $500 | $700 |
| Trademark: Agent names (5 × 1 class) | $1,250 | $1,750 |
| Copyright registrations (5-10 works) | $325 | $650 |
| Startup attorney (operating agreement, IP assignment) | $500 | $1,500 |
| NDA template | $20 | $35 |
| **Legal Subtotal** | **$3,145** | **$5,835** |

### Combined Monthly Operating Costs

| Category | Low | High |
|----------|-----|------|
| MOONSHOT (paused) | $5 | $18 |
| SlopSports Engine | $174 | $627 |
| LeagueLore | $80 | $317 |
| Shared Infrastructure (Vercel Pro, Sentry, Supabase, Stripe) | $45 | $75 |
| **Total Monthly** | **$304** | **$1,037** |

**Day 1 realistic number (June 2026):** ~$400/month (Engine only, MOONSHOT paused, LeagueLore in dev)
**Post-LeagueLore launch (September 2026):** ~$600-800/month (Engine + LeagueLore live)

### What Scales With Success (And What Doesn't)

**Stays flat:** Railway hosting, Vercel, Supabase, The Odds API, domains
**Scales with revenue:** Anthropic API (more users = more interactions), Stripe fees, X API tier, Runway Characters usage

---

## 13. Financial Projections

### Year 1 — Month-by-Month (Conservative)

*Month 1 = June 2026 (Ray launch). LeagueLore revenue starts Month 4 (September — NFL Week 1).*

| Month | Engine Revenue | LeagueLore Revenue | Costs | Net | Notes |
|-------|---------------|-------------------|-------|-----|-------|
| 1 (Jun) | $0 | $0 | $400 | -$400 | Ray launch, engine live, LeagueLore in dev |
| 2 (Jul) | $200 | $0 | $400 | -$200 | First affiliate conversions, World Cup buzz |
| 3 (Aug) | $500 | $0 | $500 | $0 | Danny soft launch, LeagueLore beta, NFL preseason |
| 4 (Sep) | $1,500 | $2,000 | $700 | +$2,800 | **LeagueLore public launch at NFL Week 1** |
| 5 (Oct) | $3,000 | $4,000 | $750 | +$6,250 | Patricia + Carl launch, LeagueLore word-of-mouth |
| 6 (Nov) | $5,000 | $5,500 | $800 | +$9,700 | Studio Premium growing, LeagueLore weekly content humming |
| 7 (Dec) | $7,000 | $6,000 | $850 | +$12,150 | Fantasy playoffs = peak LeagueLore engagement |
| 8 (Jan) | $8,000 | $4,000 | $900 | +$11,100 | Season Recap Packages, championship content |
| 9 (Feb) | $10,000 | $2,500 | $900 | +$11,600 | Bianca launch, NFL offseason (LeagueLore stays active) |
| 10 (Mar) | $15,000 | $2,000 | $950 | +$16,050 | Video content ramping, sponsorships |
| 11 (Apr) | $20,000 | $2,000 | $1,000 | +$21,000 | All 5 agents active, brand deals |
| 12 (May) | $25,000 | $3,000 | $1,050 | +$26,950 | Full operation, draft season starts, renewals |
| **Year 1 Total** | **$95,200** | **$31,000** | **$9,200** | **$117,000** | **Combined: $126,200 revenue** |

**Plus one-time costs:** $3,145-$5,835 (legal/formation)

**Year 1 net profit (conservative):** ~$111,000-$114,000

*Note: These are conservative estimates. LeagueLore revenue assumes 500 leagues at launch growing to 2,000 by Month 12. Engine revenue assumes slower affiliate ramp-up since MOONSHOT upsell is deferred.*

### Moderate Scenario
- Year 1 combined revenue: $250K-$400K
- LeagueLore: 3,000-5,000 leagues by Month 12
- Monthly run rate by Month 12: $50K-$80K/month

### Optimistic Scenario
- Year 1 combined revenue: $400K-$700K
- LeagueLore: 10,000+ leagues by Month 12 (viral commissioner-to-commissioner spread)
- Monthly run rate by Month 12: $80K-$150K/month
- Viral agent moments + LeagueLore group-chat sharing could accelerate significantly

### Platform & Product Growth Projections (Conservative)

| Metric | Month 3 (Aug) | Month 6 (Nov) | Month 12 (May) |
|--------|---------------|---------------|----------------|
| X followers (combined) | 3,000 | 15,000 | 75,000 |
| TikTok | 1,000 | 30,000 | 300,000 |
| YouTube | 200 | 5,000 | 30,000 |
| Instagram | 500 | 10,000 | 50,000 |
| Studio DAU | 200 | 3,000 | 15,000 |
| Discord | — | 500 | 3,000 |
| LeagueLore leagues | 0 (beta) | 1,500 | 3,000 |
| LeagueLore league members | 0 | 18,000 | 36,000 |

---

## 14. Competitive Landscape

### Direct Competitors (Sports Betting Content)
- **Action Network:** Editorial sports betting content. Human-created, expensive, slow. No AI personalities, no entertainment angle.
- **Unabated:** Betting tools and analytics. Pure utility, no personality layer.
- **Sports betting touts:** Low trust, paywall-first, no entertainment value. SlopSports is free entertainment that monetizes through engagement.
- **Gambling Twitter:** Individual human personalities. Key-person risk, inconsistent posting, burnout.

### Adjacent Competitors (Sports Entertainment)
- **Barstool Sports:** Personality-driven sports entertainment. Proof the model works at scale. But key-person risk (Portnoy), human content costs, regulatory challenges.
- **Pat McAfee Show:** Single personality, massive audience. Key-person risk. Can't scale beyond one person's hours.
- **Bleacher Report / The Athletic:** Traditional sports media. High production costs, human-dependent.
- **Overtime:** Youth-focused sports entertainment. Video-first. Different demographic but similar engagement model.

### Virtual Character Competitors
- **AIvilization:** AI agent simulation sandbox. Self-contained world, not real social media. Research project, not a media business.
- **Mack Falconer / virtual influencers:** One-off creators with AI characters. No multi-agent ecosystem, no sports focus, no monetization engine.
- **Character.AI / Replika:** AI conversation products. No public social media presence, no sports focus.

### Fantasy Football Competitors (LeagueLore's Space)
- **Sleeper/Yahoo/ESPN:** The platforms themselves. Data-rich, narrative-poor. They host leagues but don't tell stories. LeagueLore sits on top of them, not against them.
- **Fantasy Pros / Fantasy Footballers:** Advice-first content. Generic, not personalized to your league. No narrative engine, no Co-Commish.
- **KeepTradeCut / Fantasy Calc:** Dynasty value calculators. Pure utility, no personality, no league-specific context.
- **ChatGPT/generic AI chat:** Users can ask ChatGPT about fantasy, but it doesn't know their league, their history, their rivalries. No platform integration, no persistent memory.

### Our Moat
1. **No key-person risk** — unlike every human-driven sports media company, we own the IP completely
2. **Near-zero marginal content cost** — AI generation vs. human creators
3. **24/7 content** — agents never sleep, never burn out, never have scandals
4. **Multi-agent dynamics** — emergent storylines from agent interactions are unique
5. **Three-product portfolio** — SaaS revenue (LeagueLore) + attention revenue (agents) + analytics revenue (MOONSHOT) = resilient diversification
6. **Platform-agnostic** — not dependent on any single distribution channel
7. **LeagueLore's league data moat** — every season of connected league data makes the product better and harder to leave (chronicles build on each other, Co-Commish gets smarter)
8. **Cross-product growth loop** — agents build brand → brand drives LeagueLore signups → LeagueLore content shared in group chats → new commissioners discover SlopSports → repeat

---

## 15. Team & Operations

### Team Size: 1-3 People

| Role | Who | Responsibilities |
|------|-----|-----------------|
| Technical Lead / Founder | You | Engine development, infrastructure, AI prompts, analytics |
| Content Director / Brand | Partner (optional) | Social strategy, community, brand voice, platform growth |
| Community Manager | Hire when justified | Discord, fan engagement, content review queue |

### Daily Management Workflow (~30-60 min/day)

1. **Morning:** Glance at agent content queue, approve Tier 3 posts, check overnight engagement
2. **Game time:** Optionally watch War Room, system runs itself
3. **Evening:** Review results, flag agent behavior to tune, spot-check LeagueLore content quality
4. **Weekly:** Review funnel metrics across both products, adjust agent personalities if needed, review LeagueLore onboarding/churn metrics

### Admin Dashboard Features (SlopSports Engine)
- **Content Queue:** Every generated post with approval levels (Tier 1 auto-publish, Tier 2 notification, Tier 3 held for review)
- **Agent Control Panel:** Kill switch per agent, tone dials, manual event injection, override queue
- **Analytics Dashboard:** Per-agent metrics, funnel tracking, revenue by stream, API costs in real-time
- **Memory Viewer:** Active storylines, prediction records, relationship state

### LeagueLore Operations
- **Mostly autonomous:** Once onboarded, content generates automatically per NFL schedule
- **Content quality monitoring:** Spot-check match reports and Co-Commish responses for tone/accuracy
- **Commissioner support:** Handle onboarding issues, Sleeper integration edge cases
- **Seasonal rhythm:** Heavy operations during draft season (Aug-Sep) and playoffs (Dec-Jan); lighter in offseason
- **Offseason engagement:** LeagueLore stays active year-round with dynasty content, what-if analysis, mock drafts, historical retrospectives — this is when other products go dark

---

## 16. Risk Analysis

### Content Quality Risk
- **Risk:** AI-generated content is repetitive, unfunny, or off-brand
- **Mitigation:** Extensive personality prompts, human review for Tier 2-3, feedback loops, A/B testing content styles, prompt iteration

### Platform Risk (Any Single Platform)
- **Risk:** Any platform changes API, bans accounts, or declines in relevance
- **Mitigation:** Platform-agnostic architecture. X is one channel. Studio is the owned platform. TikTok, YouTube, Discord, podcasts are all independent distribution. Engine generates for all simultaneously. If X disappears tomorrow, we lose one output channel.

### Regulatory Risk
- **Risk:** Sports betting advertising regulations tighten
- **Mitigation:** Agents are entertainment-first (60/25/15 split). Betting content is one flavor, not the identity. Comply with FTC disclosure requirements. State-by-state compliance.

### API Cost Risk
- **Risk:** Anthropic, X, or Runway raises prices significantly
- **Mitigation:** Prompt caching reduces Anthropic costs 90%. X API is optional. Runway Characters can be swapped for alternatives (HeyGen, Synthesia, future competitors). No single API dependency exceeds 25% of operating costs.

### Competition Risk
- **Risk:** Larger company copies the concept
- **Mitigation:** First-mover advantage in AI sports personalities. Agent memory and established storylines are a moat. Audience relationships compound over time. The concept is easy to copy; the execution and established characters are not.

### Reputation Risk
- **Risk:** Agent says something offensive, inaccurate, or harmful
- **Mitigation:** Content review tiers, kill switches per agent, explicit content filters in prompts, rapid response protocol, human review for MOONSHOT mentions and any Tier 3 content.

### LeagueLore Platform Dependency Risk
- **Risk:** Sleeper changes their public API, breaks integration
- **Mitigation:** Multi-platform roadmap (Yahoo within 6 months, ESPN within 12). Once league data is ingested, it's stored locally — API only needed for initial sync and weekly updates. Yahoo has an official OAuth API. ESPN integration is harder (no official API) but largest user base justifies the effort.

### LeagueLore Content Quality Risk
- **Risk:** Generated narrative content is generic, unfunny, or feels like "AI slop"
- **Mitigation:** The SlopSports brand explicitly reclaims "slop" by being demonstrably high-craft. Member profile data makes content personal and specific. Knowledge Service grounds every player mention in real stats. Prompt engineering is the highest-priority dev task — content quality validated before any public launch.

### Execution Risk (Two Products Simultaneously)
- **Risk:** Building both the agent engine and LeagueLore in parallel stretches a 1-person team too thin
- **Mitigation:** Sequential launch (engine first in June, LeagueLore in September) means focus shifts, not splits. Shared infrastructure reduces duplicate work. LeagueLore's hard deadline (NFL Week 1) forces scope discipline — MVP is Lore + Live + Co-Commish on Sleeper only.

---

## 17. Compliance & Legal

### AI Content Disclosure
- All accounts clearly labeled as AI-generated in bios
- Comply with FTC guidelines on AI-generated content
- Disclosed as affiliated when mentioning MOONSHOT

### FTC Compliance
- Affiliate links disclosed per FTC endorsement guidelines
- Sponsored content clearly marked
- "Not financial advice" disclaimers on betting content

### X (Twitter) Policies
- Comply with X's automation and bot policies
- Accounts labeled as automated per X's requirements
- No manipulation, spam, or fake engagement

### Sports Betting Regulations
- No unlicensed operation as a sportsbook
- Content is entertainment and analysis, not gambling services
- State-by-state compliance awareness for betting-adjacent content
- Responsible gambling messaging included periodically

### Intellectual Property
- **Trademark strategy:** See Section 2
- **Copyright strategy:** All AI-generated content directed by human operators → copyright protected
- **Defensive measures:**
  - NDA for all external parties viewing proprietary strategy
  - IP Assignment Agreement for all contributors (employees, contractors, partners)
  - Monitor for trademark infringement on character names
  - Domain portfolio: secure slopsports.com, slopsports.studio, and common misspellings

### Privacy (Studio Users)
- Standard privacy policy for Studio web app
- GDPR/CCPA compliance if collecting user data
- No sale of personal information
- Anonymous analytics only

### Privacy (LeagueLore Users)
- Fantasy league data is private and personal — treated as sensitive
- League data stored in isolated per-league partitions
- Member profile survey data used only for content generation within that league
- No cross-league data sharing or aggregation
- Commissioner controls data — can delete league and all associated data
- Clear privacy policy explaining what data is collected (league history, rosters, matchups, member profiles) and how it's used (solely for generating league-specific content)
- GDPR/CCPA compliance: data export and deletion on request

---

## 18. Milestones & Roadmap

### Pre-Launch: Legal & Infrastructure (May 2026 — Week 1-2)
- [ ] File LLC, get EIN, open business bank account
- [ ] File "SlopSports" trademark (2 classes)
- [ ] File "MOONSHOT" trademark (2 classes)
- [ ] Buy domains (slopsports.com, leaguelore.com)
- [ ] Reserve social handles (@SlopSports, @RayTheSharp, agent accounts)
- [ ] Set up shared infrastructure: Vercel Pro, Railway Pro, Stripe, Sentry, Supabase
- [ ] Set up API accounts: Anthropic, X, The Odds API, ElevenLabs
- [ ] Pause MOONSHOT (stop Railway backend, keep database)
- [ ] Scaffold SlopSports engine codebase (separate repo)
- [ ] Scaffold LeagueLore codebase (separate repo)

### Build Phase: Engine + LeagueLore Foundation (May-June 2026)
- [ ] **Engine:** Data ingestion layer (The Odds API)
- [ ] **Engine:** Interpretation engine (raw data → narrative events)
- [ ] **Engine:** Agent reaction engine + Ray's personality prompts
- [ ] **Engine:** Content generation pipeline (Anthropic Claude)
- [ ] **Engine:** Simulator mode (full pipeline, no live posting)
- [ ] **Engine:** Publishing layer (X API via tweepy, simulator-to-live toggle)
- [ ] **LeagueLore:** Sleeper API integration (league sync, historical data walk)
- [ ] **LeagueLore:** Database schema (leagues, members, matchups, history)
- [ ] **LeagueLore:** Knowledge Service v1 (NFL player profiles, stats, form)
- [ ] **LeagueLore:** Match report generator — iterate prompts until content quality is genuinely good
- [ ] **Shared:** Deploy shared Knowledge Service

### Phase 1: Ray Solo Launch (Late June 2026)
- [ ] Create Ray's X account, file trademark
- [ ] Launch Ray posting to X (Tier 1 auto, Tier 2-3 manual review)
- [ ] Ray covers NBA offseason, MLB, **2026 FIFA World Cup** (huge moment)
- [ ] Studio MVP deployed: Ray profile + War Room feed
- [ ] Set up sportsbook affiliate accounts
- [ ] Continue LeagueLore build (Co-Commish, member profiles, onboarding)
- **Target:** 1,000 X followers, first affiliate conversions, SlopSports brand established

### Phase 2: LeagueLore Beta + Danny (August 2026)
- [ ] LeagueLore beta: 10-20 real leagues including founder's dynasty league
- [ ] Commissioner onboarding flow: paste Sleeper league ID → instant chronicle
- [ ] Co-Commish v1 functional (deterministic + basic AI responses)
- [ ] Write Danny's personality prompts, build Ray ↔ Danny dynamics
- [ ] Soft launch Danny on X for NFL preseason
- [ ] Ray starts posting fantasy football content, teasing LeagueLore
- [ ] Legal checkpoint: review operating agreement if partner joining
- **Target:** 5,000 X followers, LeagueLore beta validated, content quality confirmed

### Phase 3: LeagueLore Public + NFL Week 1 (September 2026)
- [ ] **LeagueLore public launch** — Sleeper integration, Lore + Live + Co-Commish
- [ ] Week 1 match reports drop for every connected league (launch event)
- [ ] Studio Premium opens ($7.99/mo Stripe subscription)
- [ ] LeagueLore subscription live ($60-75/year per league via Stripe)
- [ ] Affiliate links active in Studio and agent content
- [ ] Danny fully active — fantasy meltdowns cross-promote LeagueLore
- [ ] Begin Runway Characters video pilot for Ray
- **Target:** 500+ LeagueLore leagues, 200 Studio Premium subs, revenue live

### Phase 4: Full Cast + Scale (October-December 2026)
- [ ] Launch Patricia and Carl (file trademarks)
- [ ] Full relationship engine operational
- [ ] LeagueLore weekly content running autonomously
- [ ] Danny video content (meltdowns = TikTok gold)
- [ ] Launch Discord community
- [ ] Begin sponsorship outreach
- [ ] Draft Day Packages for late-season dynasty drafts
- **Target:** 15,000 X followers, 2,000+ LeagueLore leagues, $10K+ monthly revenue

### Phase 5: Bianca + All Revenue (Q1 2027)
- [ ] Launch Bianca (file trademark)
- [ ] All 5 agents active across X, Studio, TikTok, YouTube
- [ ] All video characters live via Runway Characters
- [ ] Evaluate MOONSHOT reactivation
- [ ] AI podcast launch ("The SlopSports Show")
- [ ] Merch store launch (print-on-demand)
- [ ] LeagueLore Season Recap Packages (fantasy playoffs + championship)
- [ ] LeagueLore offseason content: dynasty grades, what-if engine, mock drafts
- **Target:** 50,000+ X followers, 5,000+ LeagueLore leagues, $20K+ monthly revenue

### Month 9-12: Growth & Optimization (Q2-Q3 2027)
- [ ] Full IP portfolio review: all trademarks filed, copyrights registered
- [ ] LeagueLore Yahoo integration (Phase 2 platform)
- [ ] LeagueLore Draft Day Package for August 2027 draft season
- [ ] Scale video production (all agents, all platforms)
- [ ] Brand sponsorship scaling
- [ ] Begin LeagueLore ESPN integration research
- [ ] MOONSHOT reactivation (if audience traction justifies)
- [ ] Interactive video Q&A (Runway + WebRTC in Studio)
- **Target:** 100K+ X followers, 10,000+ LeagueLore leagues, $40K+ monthly revenue

### Year 2 Horizon
- [ ] LeagueLore ESPN integration
- [ ] LeagueLore international expansion (Premier League fantasy)
- [ ] White-label SlopSports engine licensing
- [ ] LeagueLore physical goods at scale (printed books, trophies)
- [ ] User-generated betting personalities (compete against the 5 agents)
- [ ] Potential Series A if growth justifies

---

## Appendix A: 2026 FIFA World Cup Opportunity

The 2026 World Cup is hosted in the US, Canada, and Mexico (June-July 2026). This coincides perfectly with Ray's solo launch — his first weeks on X will be during peak global sports attention.

**Opportunity:**
- Peak global sports attention for 4+ weeks
- Soccer coverage expands addressable audience internationally
- Agent reactions to World Cup games = massive engagement potential
- Carl's conspiracy theories about FIFA = guaranteed entertainment
- **Ray's launch into the World Cup** gives him immediate high-engagement content from day one

**Plan:**
- Ray launches during World Cup, covering games with data-driven takes
- Temporary expansion of soccer coverage from Tier 2 to Tier 1
- Special World Cup content series across all platforms
- Leverage international interest to grow non-US following
- World Cup attention establishes the SlopSports brand before LeagueLore launches in September

## Appendix B: Revenue Stack Visualization

```
┌─────────────────────────────────────────────────────────────┐
│                    SLOPSPORTS REVENUE STACK                   │
│                                                               │
│  ═══ LEAGUELORE (SaaS — Predictable) ═══                    │
│  ┌─── League Subscriptions ($60-75/yr) ──────────────┐      │
│  │  Commissioner-pays, 55-60% gross margin            │      │
│  └───────────────────────────────────────────────────┘      │
│  ┌─── Draft Day Package ($20-25) ────────────────────┐      │
│  │  Seasonal upsell, August-September spike           │      │
│  └───────────────────────────────────────────────────┘      │
│  ┌─── Season Recap + Physical Goods ($10-120) ───────┐      │
│  │  High-margin emotional purchases                   │      │
│  └───────────────────────────────────────────────────┘      │
│                                                               │
│  ═══ ENGINE + STUDIO (Attention — Scalable) ═══              │
│  ┌─── Sportsbook Affiliates ─────────────────────────┐      │
│  │  $100-300 CPA per conversion                       │      │
│  └───────────────────────────────────────────────────┘      │
│  ┌─── Studio Premium ($7.99/mo) ─────────────────────┐      │
│  │  93.4% gross margin                                │      │
│  └───────────────────────────────────────────────────┘      │
│  ┌─── Brand Sponsorships ────────────────────────────┐      │
│  │  $500-5,000/week                                   │      │
│  └───────────────────────────────────────────────────┘      │
│  ┌─── Programmatic Ads + Video Revenue ──────────────┐      │
│  │  $15-40+ CPM (sports betting)                      │      │
│  └───────────────────────────────────────────────────┘      │
│  ┌─── Discord + Merch + Tail-This + Podcast ─────────┐      │
│  │  Supporting streams, diversification               │      │
│  └───────────────────────────────────────────────────┘      │
│                                                               │
│  ═══ MOONSHOT (Deferred — High ARPU) ═══                     │
│  ┌─── MOONSHOT Upsell ($20-50/mo) ──────────────────┐      │
│  │  Reactivates when Products 1-2 have traction       │      │
│  └───────────────────────────────────────────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

## Appendix C: LeagueLore Full Product Specification

The complete LeagueLore product specification lives in its own document: `docs/LEAGUELORE_PRODUCT_SPEC.md`. It covers the four pillars (Lore, Live, Lab, Co-Commish), dual audience strategy (dynasty vs. redraft), hybrid token architecture, onboarding flow, platform integrations, content calendar, and the 6-month build plan in full detail.

---

*Version 4.0 — May 2026*
*SlopSports is a three-product portfolio: SlopSports Engine + Studio, LeagueLore, and MOONSHOT. All three are separate codebases, databases, and deployments under the SlopSports LLC umbrella. Infrastructure accounts (Vercel, Railway, Stripe, Sentry) are shared across products. MOONSHOT is paused; its infrastructure is reused.*
