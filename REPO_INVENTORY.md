# SlopSports — Repository & Component Inventory

**Audit date:** 2026-07-14
**Scanned location:** `/home/user/SLOPSPORTS`
**Auditor note:** This is an inventory of what the documents in this directory describe and, separately, what code actually exists here. The two are not the same — see the caveat below.

---

## 0. Important caveat — what is actually in this directory

The task was "scan every repo in this directory." In fact this directory is **one git repo containing exactly two Markdown planning documents** and no source code:

| File | Size | What it is |
|------|------|-----------|
| `SLOPSPORTS_BUSINESS_PLAN.md` | ~73 KB / 1,273 lines | Business plan v4.0 — strategy, financials, architecture overview for a three-product portfolio |
| `SLOPSPORTS_BUILD_GUIDE.md` | ~90 KB / 2,609 lines | Step-by-step implementation guide for **one** of the three products (the Engine), with substantial inline code |

There are **no cloned repos, no `src/` trees, no runnable projects** on disk. Every "repo" below is a *planned* codebase described in the docs. Where I say a component is "complete," I mean **complete as written code inside the build guide** — not that a working repository exists. Treat the business plan's "already built / deployed / code complete" claims (especially for MOONSHOT) as **unverified**: none of that code is present here to confirm.

One referenced document is also **missing**: `docs/LEAGUELORE_PRODUCT_SPEC.md` (cited as the full LeagueLore spec) does not exist in this directory.

---

## 1. Inventory at a glance

The docs describe **three products** under one brand (SlopSports LLC), plus one shared service.

| # | Product / Service | Role in portfolio | Stack (planned) | Code present here? | Doc-claimed status | Actual status in this repo |
|---|-------------------|-------------------|-----------------|--------------------|--------------------|----------------------------|
| 1 | **SlopSports Engine + Studio** | 5 AI sports personalities → social/web content | FastAPI · Celery · Redis · Postgres · Anthropic SDK · tweepy / React+Vite+TS (Studio) | ✅ Partial (embedded in build guide) | Building; Ray solo launch Jun 2026 | ~Phases 1–5 written as guide code; Phases 6–8 unwritten |
| 2 | **LeagueLore** | AI narrative layer for fantasy football leagues | FastAPI · Postgres · Redis · Supabase auth · Sleeper API / React+Vite+TS | ❌ None | Launch Sep 2026 (NFL Week 1) | Described only; spec doc missing |
| 3 | **MOONSHOT** | Pro betting analytics platform (upsell) | Flask · React+Vite · Postgres · Redis · Supabase · The Odds API · nba_api | ❌ None | "Code complete, deployed, paused" | Claim unverifiable — no code here |
| — | **Knowledge Service** | Shared player/team data layer for #1 and #2 | REST service · Redis cache · Sleeper / nfl_data_py / nba_api | ❌ None | Ships with LeagueLore v1 | Described only |

---

## 2. Product 1 — SlopSports Engine + Studio

### What it does
An autonomous content engine. It ingests live sports betting data, detects meaningful *changes* (line moves, upsets, blowouts), turns those into "narrative events," decides which of five AI personalities should react and how, generates in-character content via Claude, routes it through a tiered human-review queue, and (eventually) publishes to X / Studio / TikTok / YouTube / Discord. The **Studio** is a companion React web app — a public "War Room" feed, agent profiles, prediction leaderboards, and a freemium "Data Mode."

The five agents: **Ray "The Sharp"** (data analyst), **Degen Danny** (chaos gambler), **Coach Patricia Wells** (old-school eye-test), **Conspiracy Carl** (everything's rigged), **Bianca "The Closer" Reyes** (insider reporter). Only Ray is written.

### Stack
- **Backend:** Python 3.11+, FastAPI (async), Celery + Redis (scheduled/queued tasks), PostgreSQL (SQLAlchemy 2.0 async + Alembic), `structlog`
- **AI:** Anthropic Python SDK, tiered models — Haiku (Tier 1 rapid), Sonnet (Tier 2 analysis), Opus (Tier 3 viral); prompt caching on system prompts
- **Integrations:** The Odds API (`httpx`), X/Twitter (`tweepy`), ElevenLabs (voice), Runway Characters (video), Discord bot, Stripe (Studio Premium), Sentry
- **Frontend (Studio):** React + Vite + TypeScript, WebSocket for real-time feed, deployed on Vercel
- **Infra:** Docker Compose (local), Railway (prod backend)

### Architecture — the 8-layer pipeline
```
L1 Data Ingestion → L2 Interpretation → L3 Agent Reaction → L4 Content Generation
→ L5 MOONSHOT integration (deferred) → L6 Narrative Memory → L7 Viral Detection
→ L8 Multi-Platform Distribution
```

### Complete vs. stubbed (mapped to actual build-guide code)

| Component | File (planned) | Status | Notes |
|-----------|----------------|--------|-------|
| Project scaffold (Docker, config, pyproject) | `docker-compose.yml`, `src/config.py`, etc. | ✅ **Written** | Full local stack: app + Postgres + Redis + Celery worker/beat |
| DB schema (7 tables) | `src/db/models.py` | ✅ **Written** | `SportEvent`, `NarrativeEvent`, `ContentPost`, `PostEngagement`, `Prediction`, `AgentMemory` + enums |
| Odds API client | `src/data/odds_client.py` | ✅ **Written** | Async, logs rate-limit headroom; odds/scores/events |
| Line-movement detection | `src/data/odds_tracker.py` | ✅ **Written** | Detects spread/total/price moves vs. stored snapshot |
| Scores/news/discourse clients | `src/data/{scores,news,discourse}_client.py` | ❌ **Missing** | Only odds client exists; scores handled inline in a task |
| Interpretation engine | `src/engine/interpreter.py` | ⚠️ **Partial** | Line-movement + game-result interpreters written; pre-game spread extraction is a TODO ("Would need to extract") |
| Reaction engine | `src/engine/reactor.py` | ✅ **Written** | Static `REACTION_MAP` + probability/tier logic |
| Scheduler (post stagger) | `src/engine/scheduler.py` | ✅ **Written** | Same-agent/global gaps, tier-based delays |
| Event definitions | `src/engine/events.py` | ✅ **Written** | `EventType` enum + `NarrativeEventData` dataclass |
| Base agent + system-prompt builder | `src/agents/base.py` | ✅ **Written** | `AgentPersonality` dataclass, prompt assembler |
| Ray personality | `src/agents/ray.py` | ✅ **Written** | Full persona, voice, catchphrases, relationships, rules |
| Danny / Patricia / Carl / Bianca | `src/agents/{danny,patricia,carl,bianca}.py` | ❌ **Missing** | Registry ships Ray only |
| Inter-agent relationship engine | `src/agents/relationships.py` | ❌ **Missing** | Relationships are prose in Ray's prompt; no engine |
| Content generator | `src/content/generator.py` | ✅ **Written** | Anthropic call, model tiering, prompt caching, platform formatting |
| Review queue | `src/content/review_queue.py` | ✅ **Written** | Tier-based auto-approve / hold |
| Prompt & template libraries | `src/content/{prompts,templates}.py` | ❌ **Missing** | Prompts currently live in agent objects |
| Celery ingestion + generation tasks | `tasks/ingest.py`, `tasks/generate.py` | ✅ **Written** | Wires L1→L2→L3→L4 |
| Dashboard + admin API | `src/api/{dashboard,admin}.py` | ✅ **Written** | `/api/events`, `/api/stats`, `/admin/trigger/*` |
| Simulator publisher | `src/publisher/simulator.py` | ✅ **Written** | Logs instead of posting (dev safety) |
| Real publishers (X, video, accounts) | `src/publisher/{x_client,video_client,accounts}.py` | ❌ **Missing** | Phase 6 "awaiting permission to proceed" |
| Narrative memory (store/recall) | `src/memory/{store,recall}.py` | ❌ **Missing** | `AgentMemory` table exists; no logic |
| Viral detection & amplification | `src/viral/{detector,amplifier}.py` | ❌ **Missing** | `PostEngagement` table exists; no logic; `tasks/monitor.py` referenced in beat schedule but not written |
| MOONSHOT client | `src/moonshot/client.py` | 🔸 **Explicitly stubbed** | Layer 5 deferred until MOONSHOT reactivation |
| Studio frontend | (separate React app) | ❌ **Missing** | Described in business plan; zero code |
| Integration tests | `tests/test_integration/test_pipeline.py` | ✅ **Written** | Interpreter/reactor/scheduler/generator (generator mocked) |

**Bottom line for Product 1:** The **read/interpret/generate spine (Layers 1–4) is written and coherent**; the **act-on-the-world half (publishing, memory, virality, the entire Studio UI) is not**. It can run end-to-end *in simulation* only.

### Reusable components (highest value)
- **`ContentGenerator`** — a clean, provider-correct pattern for tiered LLM content gen with prompt caching and per-channel formatting. Reusable in any multi-persona or multi-format generation product.
- **`AgentPersonality` + `build_system_prompt()`** — a tidy persona-to-system-prompt compiler. Drop-in for any character/agent system.
- **`OddsTracker._detect_movements`** — generic "diff two JSON snapshots and emit change events" logic; reusable for any polling-diff pipeline (price monitors, config drift, etc.).
- **`Scheduler`** — natural-feeling post staggering with per-actor and global rate gaps; reusable for any "don't look like a bot" scheduling need.
- **`ReviewQueue`** — tier-based auto-approve/hold state machine; reusable for any human-in-the-loop moderation flow.
- **`SimulatorPublisher` pattern** — env-gated dry-run publishing; reusable safety pattern for anything that writes to external platforms.

---

## 3. Product 2 — LeagueLore

### What it does
An AI narrative/intelligence layer that sits **on top of** existing fantasy-football platforms (Sleeper first, then Yahoo/ESPN). It ingests a league's history and turns it into stories: match-report narratives, power rankings, a "burn book," season chronicles, and an interactive **Co-Commissioner** chatbot that knows the league's records, rivalries, and rules. Commissioner-pays SaaS ($60–75/yr per league).

Four pillars: **Lore** (historical chronicle), **Live** (in-season content), **Lab** (analytical tools), **Co-Commish** (conversational AI).

### Stack (planned)
FastAPI + PostgreSQL + Redis backend · React + Vite + TypeScript frontend · Supabase auth · Stripe · **Sleeper API** (free/public) for league data · shared **Knowledge Service** for player grounding · Railway + Vercel (shared accounts).

### Notable architecture idea
A **two-layer, cost-optimized design**: a deterministic **Knowledge Engine** answers 60–70% of Co-Commish queries (records, standings, playoff math, rosters) with **zero AI cost**; the **Intelligence Layer** (Claude) is invoked surgically only for narrative/nuanced reasoning. Combined with context compression + prompt caching + model tiering → target 55–60% gross margin.

### Complete vs. stubbed
❌ **Entirely conceptual in this directory.** No code, no schema, no client. The referenced full spec (`docs/LEAGUELORE_PRODUCT_SPEC.md`) is **absent**. Roadmap targets a Sep 2026 launch, so it is expected to be greenfield.

### Reusable components (from/for LeagueLore)
- The **deterministic-first / AI-surgical** query router is the single most reusable *idea* in the whole portfolio — a template for any cost-sensitive RAG/chatbot product.
- Shares the Engine's **Knowledge Service** and Anthropic billing/caching.
- Physical-goods fulfillment (printed record books, trophies) is a self-contained module that could serve other products.

---

## 4. Product 3 — MOONSHOT

### What it does
A pre-existing **professional sports-betting analytics platform**: prop analysis, line-movement tracking, a proprietary "DMR" score, batch analysis, and user portfolios. Positioned as the high-ARPU upsell ($20–50/mo), currently **paused** to focus on Products 1–2, and referenced organically by Ray's content.

### Stack (per docs)
**Flask** API + React + Vite + PostgreSQL + Redis · Supabase auth · Stripe · The Odds API + `nba_api`. Deployed on Railway + Vercel.

### Complete vs. stubbed
Business plan states **"code complete, infrastructure live, revenue paused."** **This cannot be verified — no MOONSHOT code exists in this directory.** Within Product 1, MOONSHOT is present only as a **deliberately stubbed** integration point (`src/moonshot/client.py`, Layer 5), to be wired to `/api/props` and `/api/analyze-batch` on reactivation.

### Reusable components (claimed, unverified)
- Its **React frontend DNA** is meant to be the basis for the Studio UI (business plan: "React matches MOONSHOT's frontend DNA").
- **The Odds API integration** and line-tracking logic overlap heavily with the Engine's `odds_client` / `odds_tracker` — a candidate to consolidate into one shared library.
- Shared infra accounts (Vercel, Railway, Stripe, Supabase, Sentry) are explicitly reused across all three products.

---

## 5. Shared Service — Knowledge Service

A standalone REST + Redis-cached data layer providing current NFL/NBA/MLB player & team data (profiles, weekly stats, form, injury status) so all AI content is grounded in real facts. Sources: Sleeper API, `nfl_data_py`, `nba_api`, The Odds API, Pro Football Reference. Planned to **ship with LeagueLore v1, then be shared with the Engine.** No code present — conceptual.

**Reusability:** By design this is the shared spine — the one component explicitly built once and consumed by both the Engine (agent grounding) and LeagueLore (player mentions in match reports). Any third product would consume it too.

---

## 6. Cross-project reusable-component catalog

Ranked by reuse leverage across *other* projects (inside or outside SlopSports):

| Component | Lives in | Reuse target | Why it travels well |
|-----------|----------|--------------|---------------------|
| **Knowledge Service** | Shared | Any sports product needing grounded player data | Purpose-built as a shared service; clean REST boundary |
| **Tiered LLM `ContentGenerator`** (caching + per-channel format) | Engine L4 | Any multi-format / multi-persona gen system | Provider-correct, cost-aware, framework-agnostic |
| **`AgentPersonality` → system-prompt compiler** | Engine L3 | Any character/agent chatbot | Pure data → prompt; no engine coupling |
| **Deterministic-first / AI-surgical query router** | LeagueLore | Any cost-sensitive chatbot / RAG | Cuts 60–70% of LLM calls; the portfolio's best cost idea |
| **Snapshot-diff event detector** (`OddsTracker`) | Engine L1 | Any polling-diff monitor | Generic JSON-diff → change events |
| **Bot-safe `Scheduler`** (stagger + rate gaps) | Engine L3 | Any automated-posting system | Human-cadence timing logic |
| **Tier-based `ReviewQueue`** | Engine L4 | Any human-in-the-loop moderation | Simple, auditable state machine |
| **Env-gated `SimulatorPublisher`** | Engine L8 | Anything writing to external APIs | Dry-run safety pattern |
| **The Odds API client + line tracking** | Engine / MOONSHOT (dup) | Any betting/odds product | Already duplicated → consolidate into one lib |
| **Shared infra accounts** (Vercel/Railway/Stripe/Supabase/Sentry) | All | All products | Cost-sharing already assumed in the plan |

---

## 7. Gaps, risks & what's missing to actually build

1. **No runnable code exists yet.** Everything is documentation. The Engine's Phases 1–5 are *transcribable* into a real repo quickly, but nothing is installed, wired, or tested against live APIs here.
2. **The "act" half of the Engine is unbuilt:** real publishers (X/video/Discord), narrative memory (`memory/`), viral detection (`viral/` + `tasks/monitor.py`), and the **entire Studio React frontend**. The Celery beat schedule already references `tasks.monitor.*` tasks that don't exist yet.
3. **4 of 5 agents are unwritten** (Danny, Patricia, Carl, Bianca) plus the relationship engine — yet the whole entertainment premise depends on inter-agent dynamics.
4. **LeagueLore is a spec with a missing spec** — the referenced `docs/LEAGUELORE_PRODUCT_SPEC.md` is absent, despite a hard Sep-2026 launch deadline.
5. **MOONSHOT's "already built" status is unverifiable** from this directory; the reactivation and Studio-reuse plans depend on code no one here can see.
6. **Model IDs in the guide are aspirational** (e.g. `claude-sonnet-4-6-*`, `claude-opus-4-6-*`) — verify against the live model list before implementing.
7. **Duplication to resolve early:** Odds API access exists (or is planned) in *both* the Engine and MOONSHOT. Consolidate into one shared client alongside the Knowledge Service before both diverge.

### Suggested first moves
- Turn Engine Phases 1–5 into an actual repo and get `docker compose up` + the simulation pipeline green against a live Odds API key.
- Write the four missing agents + relationship engine (pure content work, no new infra).
- Recover or rewrite the LeagueLore spec before its build window.
- Locate the MOONSHOT repo and confirm its real state, or drop the "already built" assumption from planning.

---

*Inventory generated from `SLOPSPORTS_BUSINESS_PLAN.md` (v4.0) and `SLOPSPORTS_BUILD_GUIDE.md`. No source repositories were present in the scanned directory; component statuses reflect code as written in the build guide, not a verified running system.*
