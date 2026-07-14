# SlopSports — Repository & Component Inventory

**Audit date:** 2026-07-14
**Scope:** Everything under `/home/user/SLOPSPORTS`
**Auditor's note:** Read the "Reality Check" first — the shape of what's here is not what "scan every repo" implies.

---

## 0. Reality Check (read this first)

This directory is **one git repository containing zero code repos.** It holds exactly two files:

| File | Size | What it is |
|------|------|------------|
| `SLOPSPORTS_BUSINESS_PLAN.md` | ~73 KB (1,272 lines) | Business plan v4.0 — strategy, products, architecture, unit economics |
| `SLOPSPORTS_BUILD_GUIDE.md` | ~90 KB (2,609 lines) | Step-by-step build guide with **embedded reference code** (Python), Phases 1–5 |

There is **no committed application code** — no `src/`, no `package.json`, no `pyproject.toml`, no services. The only git history is a single commit ("Add files via upload"). What looks like a codebase lives *inside* the build guide as fenced code blocks.

So this inventory does not describe "repos that exist." It describes the **portfolio of products these two documents specify**, and for each I assess: what it does, its stack, what is genuinely spec'd/coded vs. stubbed vs. conceptual, and what could be lifted into another project. Where the build guide contains real, copy-pasteable implementation, I flag it as such — that's the most reusable material here.

**One-line summary:** This is a *planning + reference-implementation* repo for a three-product AI sports-media company. It is 100% pre-build except for one product (MOONSHOT) that the plan says already exists elsewhere.

---

## 1. Portfolio at a Glance

The documents describe **three products** plus **one shared infrastructure service**:

| # | Asset | What it is | Build state (per docs) | Code in this repo? |
|---|-------|-----------|------------------------|--------------------|
| P1 | **SlopSports Engine + Studio** | AI content engine (5 sports personalities) + owned web platform | Planned; launch June 2026. Backend spec'd with real code through Layer 4/5 | ✅ Reference Python (build guide) |
| P2 | **LeagueLore** | AI narrative/assistant layer for fantasy football leagues | Planned; launch Sep 2026. Architecture only | ❌ Spec references external `LEAGUELORE_PRODUCT_SPEC.md` (not present) |
| P3 | **MOONSHOT** | Sports betting analytics platform | **"Code complete, infrastructure live"** — built, deployed, paused | ❌ Lives in a separate repo |
| S1 | **Knowledge Service** | Shared player/team data layer feeding P1 + P2 | Planned; "ships with LeagueLore v1" | ❌ Conceptual only |

Everything shares one cloud footprint (Railway, Vercel, Supabase, Stripe, Sentry, The Odds API) to keep costs down.

---

## 2. P1 — SlopSports Engine + Studio

### What it does
An AI "sports entertainment" engine. It ingests live betting/odds/scores data, interprets the raw data into *narrative events* ("line moved -7 → -5.5 despite 74% public on Boston"), routes those events to a cast of five AI personalities, generates in-character content via Claude, gates it through a human-review queue, and distributes it across X, the owned "Studio" web app, Discord, TikTok/YouTube, and podcasts. The **Studio** is the owned web surface — a real-time "War Room" feed, agent profiles with verified prediction records, a leaderboard, and a "Data Mode" that teases the paid MOONSHOT product.

### The five agents (personality layer)
| Agent | Role | Model tier bias | Launch phase |
|-------|------|-----------------|--------------|
| Ray "The Sharp" Castellano | Cold data analyst; bridge to MOONSHOT | T2 (Sonnet) | 1 (solo at launch) |
| Degen Danny | Chaotic degenerate gambler; running loss storylines | T1 (Haiku) | 2 |
| Coach Patricia Wells | Old-school "eye test," feuds with Ray | T2 | 3 |
| Conspiracy Carl | Everything is rigged; occasionally right | T1/T2 | 3 |
| Bianca "The Closer" Reyes | Insider breaking-news reporter | T1 | 4 |

### Stack
- **Backend:** Python 3.11+, FastAPI, Celery + Redis (task queue/scheduling), PostgreSQL, SQLAlchemy 2.0 async + Alembic
- **Content gen:** Anthropic Python SDK — Claude Haiku 4.5 (Tier 1), Sonnet 4.6 (Tier 2), Opus 4.6 (Tier 3), with prompt caching + batch API for cost control
- **Data:** The Odds API via `httpx` (async)
- **Distribution:** `tweepy` (X API v2), Runway Characters API (video avatars), ElevenLabs (voice), Discord bot, podcast RSS
- **Studio frontend:** React + Vite + TypeScript, WebSocket for real-time feed
- **Review UI:** FastAPI + htmx (lightweight admin dashboard)
- **Infra:** Docker Compose (local), Railway (backend), Vercel (Studio), Sentry, Stripe, `structlog`
- **Tooling:** pytest + pytest-asyncio, ruff, mypy (strict)

### Architecture — the 8-layer engine
| Layer | Purpose | Build state |
|-------|---------|-------------|
| L1 Data Ingestion | Odds/scores/events polling, movement detection | ✅ **Coded** (`odds_client.py`, `odds_tracker.py`, ingest tasks) |
| L2 Interpretation | Raw movements → narrative events | ✅ **Coded** (`interpreter.py`, `events.py`) |
| L3 Agent Reaction | Which agents react, what angle, probability-weighted | ✅ **Coded** (`reactor.py` + `REACTION_MAP`) |
| L3.5 Scheduler | Stagger posts so agents don't fire at once | ✅ **Coded** (`scheduler.py`) |
| L4 Content Generation | Claude calls per agent/tier/platform + review queue | ✅ **Coded** (`generator.py`, `review_queue.py`, base agent, Ray) |
| L5 MOONSHOT Integration | REST client to MOONSHOT analytics | 🟡 **Explicitly stubbed** — deferred until MOONSHOT reactivates |
| L6 Narrative Memory | Storylines, grudges, streaks, callbacks | 🟠 **Schema only** — `AgentMemory` table exists; `memory/store.py` + `recall.py` not written |
| L7 Viral Detection | Engagement monitoring, amplification | 🟠 **Schema only** — `PostEngagement` table exists; `viral/` code not written |
| L8 Distribution | Real posting to X/video/Discord/podcast | 🟠 **Simulator only** — `SimulatorPublisher` coded; real `x_client.py`/`video_client.py` not written |

### Complete vs. stubbed (precise)
**Fully coded in the build guide (Phases 1–5):**
- DB schema — 7 SQLAlchemy models: `SportEvent`, `NarrativeEvent`, `ContentPost`, `PostEngagement`, `Prediction`, `AgentMemory` + enums
- Config (`pydantic-settings`), Docker Compose (Postgres/Redis/app/worker/beat), Dockerfile, Alembic setup
- L1→L4 pipeline end-to-end, wired through Celery tasks, runnable in **simulator mode** (no live posting)
- One agent (Ray) fully authored; base `AgentPersonality` + system-prompt builder; agent registry
- Dashboard + admin API endpoints; integration tests for the pipeline

**Stubbed / not yet written (build guide ends mid-Phase-5; Phase 6 "awaiting permission"):**
- L5 MOONSHOT client (deliberate stub)
- L6 memory read/write logic, L7 viral detection/amplification, L8 real publishers (only the mock exists)
- 4 of 5 agents (Danny, Patricia, Carl, Bianca) — pattern established, personalities not authored in code
- Studio frontend (React app) — **fully unbuilt**, spec only
- Data clients beyond odds: `scores_client.py`, `news_client.py`, `discourse_client.py` (Reddit/X sentiment) — named in tree, not implemented

### Reusable components (high value)
- 🟢 **The layered content-generation pipeline** (interpret → react → schedule → generate → review) is domain-agnostic. Swap "sports odds" for any event stream and you have a generic *multi-persona AI content factory*. **The plan itself validates this** — a Year-2 horizon item is *"white-label SlopSports engine licensing,"* i.e. selling the engine as a reusable product.
- 🟢 **Admin control surface** — the spec'd Agent Control Panel (per-agent kill switch, tone dials, manual event injection, override queue) + tiered content-approval dashboard is a reusable "human-in-the-loop moderation console" for any autonomous-agent system.
- 🟢 **`AgentPersonality` + system-prompt builder** — clean, reusable pattern for any multi-character LLM app.
- 🟢 **Tiered model routing** (`TIER_MODELS` + prompt caching + platform-aware `max_tokens`/formatting) — drop-in cost-optimization pattern for any Claude app.
- 🟢 **`Scheduler` (post staggering)** — generic rate-shaping/stagger logic; useful anywhere you need natural-feeling, gap-enforced scheduling.
- 🟢 **`OddsTracker._detect_movements`** — generic "diff two JSON snapshots and emit change events" — reusable for any polling-diff use case.
- 🟢 **`SimulatorPublisher` / env-gated publishing** — good pattern for dev-safe side-effect isolation.
- 🟡 **FastAPI + Celery + Redis + async SQLAlchemy scaffold** — a solid, modern Python service starter usable for any project.

---

## 3. P2 — LeagueLore

### What it does
An AI narrative + analytics + social layer that sits on top of existing fantasy-football platforms (Sleeper at launch; Yahoo/ESPN later). It turns league data into AI-generated chronicles, power rankings, "burn books," match reports, analytical tools, and an interactive **AI co-commissioner**. Four pillars: **Lore** (historical chronicle), **Live** (in-season content), **Lab** (analytical tools), **Co-Commish** (conversational AI). Targets both dynasty leagues (narrative-first) and redraft/friend groups (assistant-first).

### Stack
FastAPI + PostgreSQL + Redis backend; React + Vite + TypeScript frontend; Railway + Vercel (shared accounts with P1); Supabase auth; Stripe payments; **Sleeper API** (free) for data; shared **Knowledge Service**.

### Architecture — two-layer cost-optimized hybrid
- **L1 Knowledge Engine (deterministic, no AI cost):** handles 60–70% of co-commish queries — standings, records, rosters, matchups, playoff math — with zero LLM spend.
- **L2 Intelligence Layer (AI, used surgically):** only invoked for narrative/reasoning — match reports, trade analysis, dispute resolution, chronicles.

### Complete vs. stubbed
🔴 **Conceptual only in this repo.** No code. The plan repeatedly defers the detail to `docs/LEAGUELORE_PRODUCT_SPEC.md`, **which is not present in this directory.** Unit economics are worked out (~$1.50–2.00/league/month), revenue model is detailed, architecture is sketched — but nothing is built here.

### Reusable components
- 🟢 The **deterministic-first / AI-surgical** query-routing pattern is the standout idea — broadly reusable for any conversational product that wants to minimize LLM spend (answer factual lookups in code, escalate to the model only for reasoning).
- 🟡 Shares P1's entire backend stack and the Knowledge Service (below).

---

## 4. P3 — MOONSHOT

### What it does
A professional sports-betting analytics platform: prop analysis, line-movement tracking, "DMR scoring," batch analysis, and user portfolios. It is the **premium upsell** at the top of the funnel — Ray (P1) organically feeds users toward it.

### Stack
Flask API + React + Vite + PostgreSQL + Redis; Supabase auth; Stripe; data from **The Odds API + `nba_api`**. Deployed on Railway (backend) + Vercel (frontend). Price $20–50/month.

### Complete vs. stubbed
🟢 **The only genuinely-built asset.** The plan states: *"Already built and deployed… Code complete, infrastructure live, subscription revenue paused until reactivation."* It is **paused**, not unbuilt — its Vercel/Railway/Stripe/Supabase/Sentry accounts are reused as the shared backbone for P1 and P2.

⚠️ **Caveat:** MOONSHOT's actual code is **not in this directory** — it lives in its own repo. This inventory can only report what the plan claims; the code itself was not available to audit.

### Reusable components
- 🟢 **The shared cloud accounts** (Railway/Vercel/Stripe/Supabase/Sentry) — MOONSHOT is literally the infrastructure foundation the other two products build on.
- 🟢 **Line-movement tracking + Odds API integration** overlaps directly with P1's L1 — the plan intends P1's Ray to consume MOONSHOT's analytics via the (stubbed) L5 REST client.
- 🟡 **React frontend "DNA"** — the plan says the Studio (P1) deliberately matches MOONSHOT's frontend so components/styling carry over.

---

## 5. S1 — Knowledge Service (shared infrastructure)

### What it does
A standalone REST data service providing structured, current player/team data (NFL ~1,500 active players + profiles/weekly stats/injury status; NBA stats/defense/matchups; MLB stats/park factors/pitching) so all AI content across P1 and P2 is grounded in real facts. Redis-cached. Sources: Sleeper API, `nfl_data_py`, `nba_api`, The Odds API, Pro Football Reference.

### Complete vs. stubbed
🔴 **Conceptual only.** Described as "ships with LeagueLore at v1, shared with Engine later." No code here.

### Reusable by design
This component is *explicitly framed as reusable* — it's the one piece both P1 and P2 consume. A clean "grounding data layer" (fetch → normalize → cache → serve over REST) is a portable pattern for any RAG/LLM product that needs factual grounding.

---

## 6. Cross-Cutting Reusable-Component Matrix

Ranked by portability to an unrelated project:

| Component | Where | Portability | Why it travels well |
|-----------|-------|-------------|---------------------|
| Multi-persona LLM content pipeline (interpret→react→schedule→generate→review) | P1 build guide | ★★★★★ | Event stream + personas is a generic shape; sports is just the current fill |
| `AgentPersonality` + system-prompt builder | P1 `agents/base.py` | ★★★★★ | Clean data-driven character definition for any multi-character LLM app |
| Tiered Claude routing + prompt caching + platform formatting | P1 `content/generator.py` | ★★★★★ | Drop-in cost/quality optimization for any Anthropic integration |
| Deterministic-first / AI-surgical query router | P2 architecture | ★★★★☆ | Cuts LLM spend in any conversational product |
| Snapshot-diff change detector | P1 `odds_tracker.py` | ★★★★☆ | Generic "detect changes between two polls" |
| Post scheduler / stagger | P1 `scheduler.py` | ★★★★☆ | Reusable rate-shaping with per-entity + global gaps |
| Grounding/knowledge data layer | S1 | ★★★★☆ | Portable RAG-grounding pattern (conceptual only) |
| FastAPI + Celery + Redis + async SQLAlchemy scaffold | P1 build guide | ★★★★☆ | Modern Python service starter, fully worked example |
| Env-gated simulator publisher | P1 `simulator.py` | ★★★☆☆ | Dev-safe side-effect isolation pattern |
| Shared cloud-account topology (Railway/Vercel/Supabase/Stripe/Sentry) | P3 | ★★★☆☆ | Reusable cost-sharing blueprint, not code |

---

## 7. Completeness Summary

| Asset | Spec'd | Real code present | Runnable | Deployed |
|-------|:------:|:-----------------:|:--------:|:--------:|
| P1 SlopSports Engine | ✅ Full | 🟢 L1–L4 + simulator | 🟡 Simulator mode only | ❌ |
| P1 Studio (frontend) | ✅ Full | ❌ None | ❌ | ❌ |
| P2 LeagueLore | 🟡 Architecture only | ❌ None (spec doc missing) | ❌ | ❌ |
| P3 MOONSHOT | ✅ (elsewhere) | ⚠️ Not in this repo | — | 🟢 Live but paused |
| S1 Knowledge Service | 🟡 Sketch | ❌ None | ❌ | ❌ |

**Bottom line for a reader deciding what to do next:**
- If you want *working software*, the only realizable thing today is P1's engine — copy the build-guide code into a real repo and you get an end-to-end pipeline running in simulator mode in ~a day. Layers 6–8, the 4 remaining agents, and the entire Studio frontend are greenfield.
- The **highest-leverage reusable IP** is the generic multi-persona content pipeline and the Claude cost-tiering pattern (§6) — both are cleanly extractable from sports.
- Two referenced artifacts are **missing from this directory**: `LEAGUELORE_PRODUCT_SPEC.md` and the MOONSHOT codebase. Any assessment of those is secondhand from the business plan.

---

*Generated by auditing the two documents in this repository. No application source code exists in this directory; all "code" assessed above is the reference implementation embedded in `SLOPSPORTS_BUILD_GUIDE.md`.*
