# SlopSports Build Guide

**Step-by-step implementation guide for the SlopSports AI Sports Entertainment Platform.**
**Companion to:** `docs/SLOPSPORTS_BUSINESS_PLAN.md` (v3.1)

---

## Phase 1: Legal & Business Formation

Everything below must be completed before any public launch, any revenue collection, or any content posted from agent accounts. This is the foundation.

---

### Step 1.1 — Form the LLC

1. **Choose your state.** File in your home state unless you have a reason to use Wyoming (privacy, no state income tax) or Delaware (investor-friendly case law). For a bootstrapped project, home state is simplest.
2. **Go to your state's Secretary of State website.** Search for "[Your State] LLC filing" — every state has an online portal.
3. **File Articles of Organization.**
   - Business name: **SlopSports LLC** (or your preferred variant)
   - Registered agent: yourself, or a registered agent service (~$50-$150/year if you don't want your home address public)
   - Management structure: member-managed (not manager-managed) for a small team
   - **Cost:** $50–$500 depending on state (e.g., California is $70, New York is $200, Wyoming is $100)
4. **Get your filing confirmation.** Save the stamped Articles of Organization PDF. You'll need it for the bank account and EIN.

### Step 1.2 — Get an EIN (Employer Identification Number)

1. Go to [https://www.irs.gov/businesses/small-businesses-self-employed/apply-for-an-employer-identification-number-ein-online](https://www.irs.gov/businesses/small-businesses-self-employed/apply-for-an-employer-identification-number-ein-online)
2. Select "Limited Liability Company" as the entity type
3. Fill out the form — takes ~5 minutes
4. You get the EIN immediately at the end. Save/print the confirmation letter (CP 575).
5. **Cost:** Free

### Step 1.3 — Open a Business Bank Account

1. Bring your Articles of Organization + EIN confirmation to a bank (or do it online with Mercury, Relay, or Bluevine for a startup-friendly experience)
2. Open a **business checking account** under SlopSports LLC
3. This is where all revenue goes in and all expenses come out. Never mix with personal accounts.
4. **Recommended:** Mercury (free, startup-focused, integrates with Stripe easily)
5. **Cost:** Free (most business checking accounts for LLCs have no monthly fee)

### Step 1.4 — Buy Domains

Purchase before anyone else does. Use Cloudflare Registrar, Namecheap, or Google Domains.

| Domain | Priority | Est. Cost |
|--------|----------|-----------|
| slopsports.com | **Immediate** | ~$10-$15/year |
| slopsports.studio | Nice to have | ~$15-$30/year |
| slopsports.app | Nice to have | ~$15/year |

Also check availability of the matching social handles (`@SlopSports`, `@RayTheSharp`, `@DegenDanny`, etc.) on X, TikTok, YouTube, Instagram. **Reserve them now** even if you won't post for weeks — handles get squatted fast.

### Step 1.5 — File Trademarks

File via **TEAS Plus** on the [USPTO website](https://www.uspto.gov/trademarks/apply).

**Priority filing order:**

| # | Mark | Class(es) | When | Est. Cost |
|---|------|-----------|------|-----------|
| 1 | SlopSports | 41 (entertainment services) + 38 (broadcasting/streaming) | **Week 1** | $500–$700 |
| 2 | MOONSHOT | 9 (software/apps) + 41 (entertainment) | **Week 2** | $500–$700 |
| 3 | Agent names (Ray, Danny, Patricia, Carl, Bianca) | 41 (entertainment) | At each agent's launch | $250–$350 each |

**How to file:**
1. Go to [https://www.uspto.gov/trademarks/apply](https://www.uspto.gov/trademarks/apply)
2. Select TEAS Plus (cheapest option — $250/class)
3. Filing basis: "Intent to Use" (1b) — you haven't launched yet, but you intend to
4. Describe services: "Entertainment services, namely, providing ongoing sports commentary, analysis, and entertainment content via social media, websites, and streaming platforms"
5. You'll get a serial number immediately. Full registration takes 8–12 months, but you have priority from the filing date.

### Step 1.6 — Draft Legal Documents

Hire a startup attorney ($500–$1,500 flat fee) or use a service like Clerky or Stripe Atlas. You need:

1. **Operating Agreement** — even as a single-member LLC, this defines:
   - Ownership percentages
   - Profit/loss distribution
   - Decision-making authority
   - What happens if a member leaves or the LLC dissolves
   - Capital contributions

2. **IP Assignment Agreement** — states that all work product (code, content, characters, prompts, designs) belongs to the LLC, not to any individual. **Critical.** Without this, if a partner leaves, they could argue they own "their" agent characters.

3. **Vesting Schedule** (if bringing in a partner):
   - Standard: 4-year vest, 1-year cliff
   - Recommended split: 70/30 or 75/25 (founder who built tech + plan retains majority)
   - Attach to the Operating Agreement as an exhibit

4. **NDA Template** — for anyone you show the business plan, strategy docs, or proprietary prompts to. Keep it simple — 2 pages max, mutual NDA.

### Step 1.7 — Set Up Accounting

1. Sign up for **Wave** (free) or **QuickBooks Self-Employed** (~$15/mo) for bookkeeping
2. Connect your business bank account
3. Create expense categories: API Costs, Hosting, Legal, Marketing, Software/SaaS
4. Track everything from day one — you'll need this for taxes and for understanding your burn rate

### Step 1.8 — S-Corp Election (Future)

Don't do this now. But once net profit exceeds ~$40K/year, consider filing Form 2553 to elect S-Corp taxation. This lets you pay yourself a "reasonable salary" and take remaining profit as distributions (avoiding self-employment tax on the distribution portion). Talk to a CPA when you hit that threshold.

---

### Phase 1 Checklist

| # | Task | Status | Cost |
|---|------|--------|------|
| 1.1 | File LLC (Articles of Organization) | ☐ | $50–$500 |
| 1.2 | Get EIN from IRS | ☐ | Free |
| 1.3 | Open business bank account | ☐ | Free |
| 1.4 | Buy domains + reserve social handles | ☐ | $25–$60 |
| 1.5 | File SlopSports trademark (Class 41 + 38) | ☐ | $500–$700 |
| 1.6 | Draft Operating Agreement + IP Assignment | ☐ | $500–$1,500 |
| 1.7 | Set up bookkeeping (Wave or QuickBooks) | ☐ | Free–$15/mo |
| 1.8 | S-Corp election | ☐ (future) | N/A |

**Phase 1 total cost: $1,075–$2,760**
**Phase 1 time estimate: 1–2 weeks**

---

## Phase 2: Account Setup & API Provisioning

Every external service SlopSports depends on, set up in order. Complete this phase before writing any code — you need API keys in hand to build against real endpoints.

---

### Step 2.1 — Anthropic API (Content Generation)

This is the brain of the entire system. Every piece of agent content is generated through Claude.

1. Go to [https://console.anthropic.com/](https://console.anthropic.com/)
2. Create an account (or sign in if you have one from MOONSHOT work)
3. Go to **Settings → API Keys → Create Key**
4. Name it `slopsports-production`
5. Copy the key immediately — it's only shown once. Store it in a password manager.
6. Go to **Settings → Plans** and add a credit card. You're on usage-based billing.
7. Set a **monthly spending limit** under Settings → Limits. Start with **$100/month** — you can raise it later. This prevents runaway costs during development.

**Models you'll use:**
| Model | Use Case | Input/Output Cost (per 1M tokens) |
|-------|----------|----------------------------------|
| Claude Haiku 4.5 | Tier 1 rapid reactions, quick replies | $0.80 / $4.00 |
| Claude Sonnet 4.6 | Tier 2 threads, analysis, quality content | $3.00 / $15.00 |
| Claude Opus 4.6 | Tier 3 creative/viral attempts (rare) | $15.00 / $75.00 |

**Cost-saving features to use from day one:**
- **Prompt caching:** Cache agent personality system prompts (they're the same every call). 90% discount on cached input tokens.
- **Batch API:** For non-urgent content (next-day previews, scheduled posts). 50% discount, 24-hour turnaround.

**Env var:** `ANTHROPIC_API_KEY=sk-ant-...`

### Step 2.2 — The Odds API (Sports Data)

This feeds the agents real betting lines, odds movement, and game data.

1. Go to [https://the-odds-api.com/](https://the-odds-api.com/)
2. Sign up for an account
3. **If MOONSHOT already has an Odds API subscription:** You can share the same key for development, but get a separate key for production (rate limits, billing clarity).
4. **Plan:** Start with the free tier (500 requests/month) for development. Upgrade to the $59/month plan (100K requests) before launch.
5. Get your API key from the dashboard.

**What you'll pull:**
- `/v4/sports/{sport}/odds` — current lines from multiple sportsbooks
- `/v4/sports/{sport}/scores` — live & completed game scores
- `/v4/sports/{sport}/events` — upcoming games

**Sports keys you'll need:**
| Sport | API Key |
|-------|---------|
| NFL | `americanfootball_nfl` |
| NBA | `basketball_nba` |
| MLB | `baseball_mlb` |
| NHL | `icehockey_nhl` |
| NCAAF | `americanfootball_ncaaf` |
| NCAAB | `basketball_ncaab` |
| UFC | `mma_mixed_martial_arts` |
| Soccer (MLS) | `soccer_usa_mls` |

**Env var:** `ODDS_API_KEY=...`

### Step 2.3 — X (Twitter) API

For posting agent content to X. **This is optional at launch** — you can start with Studio + TikTok + YouTube and add X later.

1. Go to [https://developer.x.com/](https://developer.x.com/)
2. Sign up for a developer account. You'll need to describe your use case — say: "Automated sports commentary and entertainment content from AI-driven sports personality accounts."
3. Create a **Project** (e.g., "SlopSports")
4. Create an **App** within the project (e.g., "SlopSports Engine")
5. **Plan:** Start with **Basic** ($200/month) — gives you 50K posts/month and 15K read requests/month. More than enough for launch.
6. Generate credentials:
   - **API Key & Secret** (also called Consumer Key & Secret)
   - **Access Token & Secret** (for each agent account that will post)
   - **Bearer Token** (for read-only requests)

**Important — multi-account setup:**
- You need a separate X account for each agent (start with just Ray)
- Each account needs its own Access Token & Secret
- All accounts use the same API Key & Secret (tied to your developer app)
- To get Access Tokens for each agent account: use OAuth 1.0a flow, or generate them in the developer portal while logged into each agent's X account

**Env vars (per agent):**
```
X_API_KEY=...
X_API_SECRET=...
X_RAY_ACCESS_TOKEN=...
X_RAY_ACCESS_SECRET=...
```

### Step 2.4 — ElevenLabs (Voice Synthesis)

Each agent gets a distinct, consistent voice for video content and podcasts.

1. Go to [https://elevenlabs.io/](https://elevenlabs.io/)
2. Sign up and choose the **Creator** plan ($22/month) — gives you 100K characters/month and custom voice cloning
3. Go to **Voice Lab → Add Voice**
4. For each agent, create a voice profile:
   - **Ray:** Professional, measured, slightly condescending male voice
   - **Danny:** Excitable, manic, higher energy male voice
   - **Patricia:** Authoritative, warm, older female voice
   - **Carl:** Intense, conspiratorial, hushed-then-loud male voice
   - **Bianca:** Urgent, professional, broadcast-reporter female voice
5. Start with just Ray's voice (Phase 1 is Ray solo). You can use a pre-built voice from their library and fine-tune later, or clone a voice you like.
6. Get your API key from **Profile → API Key**

**Env var:** `ELEVENLABS_API_KEY=...`

### Step 2.5 — Runway Characters API (Video Avatars)

This turns a single character image into a fully expressive, lip-synced video avatar.

1. Go to [https://dev.runwayml.com/](https://dev.runwayml.com/)
2. Sign up for a developer account
3. Get API access to **Characters** (launched March 2026)
4. Generate an API key
5. **Pricing:** Credit-based at $0.01/credit. Exact per-minute rates for Characters vary — budget ~$50-$100/month for production volume.
6. **What you'll need:** One reference image per agent (see Section 5 of the business plan for visual identity specs). Commission these from an artist or generate with an image model.

**Env var:** `RUNWAY_API_KEY=...`

### Step 2.6 — Railway (Backend Hosting)

SlopSports backend runs on Railway, separate from MOONSHOT.

1. Go to [https://railway.app/](https://railway.app/)
2. Sign in (use same account as MOONSHOT, or a separate one — your call)
3. Create a **new project** called `slopsports`
4. You'll add these services to the project later (Phase 3), but set up the project now:
   - **FastAPI app** (from GitHub repo, once code exists)
   - **PostgreSQL** database
   - **Redis** instance (for Celery task queue + caching)
5. **Plan:** Pro ($20/month base). Usage-based beyond that.
6. **Do NOT connect it to a repo yet** — we haven't written code. Just create the empty project.

### Step 2.7 — Vercel (Studio Frontend Hosting)

The SlopSports Studio React app will deploy here.

1. Go to [https://vercel.com/](https://vercel.com/)
2. Sign in (use same account as MOONSHOT, or separate)
3. **Don't create a project yet** — no frontend code exists. Just confirm your account is on Pro ($20/month) and ready.
4. When the Studio frontend is ready, you'll connect the GitHub repo and deploy.

### Step 2.8 — Sentry (Error Monitoring)

1. Go to [https://sentry.io/](https://sentry.io/)
2. Create a new project called `slopsports-backend` (Python / FastAPI)
3. Optionally create a second project `slopsports-studio` (React / JavaScript)
4. Get the DSN (Data Source Name) for each project — this is what you put in your code.
5. **Plan:** Developer tier (free) is fine to start. Upgrade to Team ($29/month) if you need more event volume.

**Env vars:**
```
SENTRY_DSN_BACKEND=https://...@sentry.io/...
SENTRY_DSN_FRONTEND=https://...@sentry.io/...
```

### Step 2.9 — Stripe (Payments — Studio Premium)

For collecting Studio Premium subscription payments.

1. Go to [https://dashboard.stripe.com/](https://dashboard.stripe.com/)
2. If MOONSHOT already has Stripe: create this as a **separate Stripe account** (Stripe allows multiple accounts). SlopSports revenue should flow through the SlopSports LLC bank account, not MOONSHOT's.
3. Create a new account → connect your SlopSports LLC business bank account
4. Go to **Products → Create Product:**
   - **SlopSports Studio Premium** — $7.99/month, recurring
   - Add a description: "Full agent access, Data Mode, game day War Room, agent interactions, priority alerts"
5. Get your API keys from **Developers → API Keys:**
   - **Publishable key** (for frontend checkout)
   - **Secret key** (for backend subscription management)
6. **Don't build the checkout yet** — just have the product and keys ready.

**Env vars:**
```
STRIPE_SECRET_KEY=sk_live_...
STRIPE_PUBLISHABLE_KEY=pk_live_...
STRIPE_WEBHOOK_SECRET=whsec_...
```

### Step 2.10 — Sportsbook Affiliate Programs

Apply to these now — approval can take 1-4 weeks, so start early.

1. **DraftKings Affiliate Program** — [https://www.draftkings.com/affiliates](https://www.draftkings.com/affiliates)
   - CPA: $100-$300+ per depositing customer
   - Apply with your SlopSports LLC info
2. **FanDuel Affiliate Program** — [https://www.fanduel.com/affiliates](https://www.fanduel.com/affiliates)
   - Similar CPA structure
3. **BetMGM Affiliate Program** — search "BetMGM affiliate program" for current application page
   - Revenue share model available

You'll get unique tracking links once approved. These go into the Studio and agent content later.

### Step 2.11 — Discord (Community)

1. Go to [https://discord.com/](https://discord.com/)
2. Create the **SlopSports** server
3. Set up channels (can be refined later):
   - `#general` — community chat
   - `#rays-desk` — Ray's data analysis drops
   - `#dannys-couch` — Danny's parlays and meltdowns
   - `#film-room` — Patricia's scouting reports
   - `#evidence-board` — Carl's conspiracy threads
   - `#breaking-news` — Bianca's scoops
   - `#game-day-war-room` — live reactions during games
   - `#predictions` — agent predictions with tracked results
4. Go to the [Discord Developer Portal](https://discord.com/developers/applications) → Create Application → Create Bot
5. Get the **Bot Token** — this is how the SlopSports engine posts to Discord channels.
6. Invite the bot to your server with `Send Messages`, `Embed Links`, `Attach Files` permissions.

**Env var:** `DISCORD_BOT_TOKEN=...`

### Step 2.12 — GitHub Repository

The SlopSports codebase lives in its own repo, completely separate from MOONSHOT.

1. Go to GitHub → **New Repository**
2. Name: `slopsports` (or `slopsports-engine` if you want to separate engine from studio later)
3. Private repo
4. Initialize with a README, `.gitignore` (Python), and MIT or proprietary license
5. Clone locally to your dev machine — **not** inside the MOONSHOT directory

```bash
cd ~/projects  # or wherever you keep repos — NOT inside MOONSHOT
git clone git@github.com:your-org/slopsports.git
cd slopsports
```

---

### Phase 2 Checklist

| # | Task | Status | Monthly Cost |
|---|------|--------|-------------|
| 2.1 | Anthropic API key + spending limit set | ☐ | $50–$150 (usage) |
| 2.2 | The Odds API key (free tier for dev) | ☐ | Free → $59 at launch |
| 2.3 | X Developer account + API keys (optional) | ☐ | $0–$200 |
| 2.4 | ElevenLabs account + Ray voice profile | ☐ | $22 |
| 2.5 | Runway Characters API key | ☐ | $50–$100 (usage) |
| 2.6 | Railway project created (empty) | ☐ | $20–$40 |
| 2.7 | Vercel account confirmed (Pro) | ☐ | $20 |
| 2.8 | Sentry projects created | ☐ | Free–$29 |
| 2.9 | Stripe account + Studio Premium product | ☐ | 2.9% + $0.30/txn |
| 2.10 | Sportsbook affiliate applications submitted | ☐ | Free (revenue share) |
| 2.11 | Discord server + bot created | ☐ | Free |
| 2.12 | GitHub repo created + cloned locally | ☐ | Free |

**Phase 2 total new monthly cost: ~$162–$561** (most services are usage-based and near-zero during development)
**Phase 2 time estimate: 2–3 days** (most is just signing up and clicking through dashboards; affiliate approvals take 1–4 weeks in the background)

**Env vars you should have after this phase:**
```
ANTHROPIC_API_KEY=sk-ant-...
ODDS_API_KEY=...
X_API_KEY=...
X_API_SECRET=...
X_RAY_ACCESS_TOKEN=...
X_RAY_ACCESS_SECRET=...
ELEVENLABS_API_KEY=...
RUNWAY_API_KEY=...
SENTRY_DSN_BACKEND=...
SENTRY_DSN_FRONTEND=...
STRIPE_SECRET_KEY=sk_live_...
STRIPE_PUBLISHABLE_KEY=pk_live_...
STRIPE_WEBHOOK_SECRET=whsec_...
DISCORD_BOT_TOKEN=...
DATABASE_URL=postgresql://...
REDIS_URL=redis://...
```

Store all of these in a password manager. They go into `.env` files (never committed to git) and Railway/Vercel environment variable settings for production.

---

## Phase 3: Project Scaffolding & Infrastructure

Set up the codebase, local development environment, database schema, and deployment pipeline. By the end of this phase you can run `docker compose up` and have a working FastAPI app connected to Postgres and Redis — with no business logic yet.

---

### Step 3.1 — Initialize the Project

From your development machine (NOT inside the MOONSHOT directory):

```bash
cd ~/projects/slopsports   # cloned in Step 2.12
```

Create the directory structure from the business plan:

```
slopsports/
├── docker-compose.yml
├── Dockerfile
├── pyproject.toml
├── requirements.txt
├── .env.example
├── .env                        # git-ignored, copy from .env.example
├── .gitignore
├── README.md
├── alembic.ini
│
├── src/
│   ├── __init__.py
│   ├── main.py                 # FastAPI app entry point
│   ├── config.py               # Pydantic Settings (reads .env)
│   │
│   ├── agents/
│   │   └── __init__.py
│   ├── data/
│   │   └── __init__.py
│   ├── engine/
│   │   └── __init__.py
│   ├── content/
│   │   └── __init__.py
│   ├── memory/
│   │   └── __init__.py
│   ├── viral/
│   │   └── __init__.py
│   ├── publisher/
│   │   └── __init__.py
│   ├── moonshot/
│   │   └── __init__.py
│   ├── api/
│   │   └── __init__.py
│   └── db/
│       ├── __init__.py
│       ├── models.py
│       ├── session.py
│       └── migrations/         # Alembic auto-generates this
│
├── tasks/
│   └── __init__.py
│
├── tests/
│   ├── conftest.py
│   └── __init__.py
│
└── scripts/
    └── __init__.py
```

Create all directories and empty `__init__.py` files:

```bash
mkdir -p src/{agents,data,engine,content,memory,viral,publisher,moonshot,api,db/migrations}
mkdir -p tasks tests scripts

# Create __init__.py in every Python package
find src tasks tests scripts -type d -exec touch {}/__init__.py \;
touch src/__init__.py
```

### Step 3.2 — pyproject.toml

Create `pyproject.toml` with all dependencies and tool config:

```toml
[project]
name = "slopsports"
version = "0.1.0"
description = "AI Sports Entertainment Engine"
requires-python = ">=3.11"

dependencies = [
    # Web framework
    "fastapi>=0.115.0",
    "uvicorn[standard]>=0.32.0",
    "python-multipart>=0.0.12",

    # Database
    "sqlalchemy[asyncio]>=2.0.36",
    "asyncpg>=0.30.0",
    "alembic>=1.14.0",

    # Cache & task queue
    "redis>=5.2.0",
    "celery[redis]>=5.4.0",

    # AI / Content generation
    "anthropic>=0.42.0",

    # Sports data
    "httpx>=0.28.0",

    # X (Twitter)
    "tweepy>=4.14.0",

    # Voice & Video
    "httpx",   # ElevenLabs + Runway via REST

    # Config
    "pydantic-settings>=2.6.0",
    "python-dotenv>=1.0.1",

    # Monitoring
    "sentry-sdk[fastapi]>=2.19.0",

    # Utilities
    "structlog>=24.4.0",
]

[project.optional-dependencies]
dev = [
    "pytest>=8.3.0",
    "pytest-asyncio>=0.24.0",
    "pytest-cov>=6.0.0",
    "httpx",           # TestClient
    "ruff>=0.8.0",
    "mypy>=1.13.0",
    "pre-commit>=4.0.0",
]

[tool.ruff]
target-version = "py311"
line-length = 100

[tool.ruff.lint]
select = ["E", "F", "I", "N", "W", "UP"]

[tool.pytest.ini_options]
testpaths = ["tests"]
asyncio_mode = "auto"

[tool.mypy]
python_version = "3.11"
strict = true
```

Also generate `requirements.txt` for Docker:

```bash
# After creating pyproject.toml
pip install pip-tools
pip-compile pyproject.toml -o requirements.txt
```

Or just maintain `requirements.txt` manually with pinned versions — either approach works.

### Step 3.3 — Environment Configuration

Create `.env.example` (this gets committed to git):

```ini
# === SlopSports Environment ===
# Copy to .env and fill in real values. NEVER commit .env to git.

# App
APP_ENV=development
APP_DEBUG=true
APP_HOST=0.0.0.0
APP_PORT=8000

# Database
DATABASE_URL=postgresql+asyncpg://slopsports:slopsports@localhost:5432/slopsports

# Redis
REDIS_URL=redis://localhost:6379/0

# Anthropic (Content Generation)
ANTHROPIC_API_KEY=sk-ant-...

# The Odds API (Sports Data)
ODDS_API_KEY=...

# X / Twitter (Optional)
X_API_KEY=
X_API_SECRET=
X_RAY_ACCESS_TOKEN=
X_RAY_ACCESS_SECRET=

# ElevenLabs (Voice)
ELEVENLABS_API_KEY=

# Runway Characters (Video)
RUNWAY_API_KEY=

# Stripe (Payments)
STRIPE_SECRET_KEY=
STRIPE_PUBLISHABLE_KEY=
STRIPE_WEBHOOK_SECRET=

# Sentry (Monitoring)
SENTRY_DSN=

# Discord
DISCORD_BOT_TOKEN=

# Content Review
AUTO_PUBLISH_TIER_1=true
AUTO_PUBLISH_TIER_2=false
AUTO_PUBLISH_TIER_3=false
```

Create `src/config.py` — a single source of truth for all config:

```python
from pydantic_settings import BaseSettings


class Settings(BaseSettings):
    # App
    app_env: str = "development"
    app_debug: bool = True
    app_host: str = "0.0.0.0"
    app_port: int = 8000

    # Database
    database_url: str = "postgresql+asyncpg://slopsports:slopsports@localhost:5432/slopsports"

    # Redis
    redis_url: str = "redis://localhost:6379/0"

    # Anthropic
    anthropic_api_key: str = ""

    # The Odds API
    odds_api_key: str = ""

    # X / Twitter
    x_api_key: str = ""
    x_api_secret: str = ""

    # ElevenLabs
    elevenlabs_api_key: str = ""

    # Runway
    runway_api_key: str = ""

    # Stripe
    stripe_secret_key: str = ""
    stripe_publishable_key: str = ""
    stripe_webhook_secret: str = ""

    # Sentry
    sentry_dsn: str = ""

    # Discord
    discord_bot_token: str = ""

    # Content review
    auto_publish_tier_1: bool = True
    auto_publish_tier_2: bool = False
    auto_publish_tier_3: bool = False

    model_config = {"env_file": ".env", "env_file_encoding": "utf-8"}


settings = Settings()
```

### Step 3.4 — Docker Compose (Local Development)

Create `docker-compose.yml`:

```yaml
services:
  app:
    build: .
    ports:
      - "8000:8000"
    env_file: .env
    volumes:
      - ./src:/app/src
      - ./tasks:/app/tasks
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_healthy
    command: uvicorn src.main:app --host 0.0.0.0 --port 8000 --reload

  celery-worker:
    build: .
    env_file: .env
    volumes:
      - ./src:/app/src
      - ./tasks:/app/tasks
    depends_on:
      postgres:
        condition: service_healthy
      redis:
        condition: service_healthy
    command: celery -A tasks worker --loglevel=info

  celery-beat:
    build: .
    env_file: .env
    volumes:
      - ./src:/app/src
      - ./tasks:/app/tasks
    depends_on:
      - redis
    command: celery -A tasks beat --loglevel=info

  postgres:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: slopsports
      POSTGRES_PASSWORD: slopsports
      POSTGRES_DB: slopsports
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U slopsports"]
      interval: 5s
      timeout: 5s
      retries: 5

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 5s
      timeout: 5s
      retries: 5

volumes:
  postgres_data:
  redis_data:
```

Create `Dockerfile`:

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### Step 3.5 — FastAPI App Entry Point

Create `src/main.py`:

```python
from contextlib import asynccontextmanager

import sentry_sdk
from fastapi import FastAPI

from src.config import settings


@asynccontextmanager
async def lifespan(app: FastAPI):
    # Startup: initialize DB connections, Redis, etc.
    yield
    # Shutdown: close connections


if settings.sentry_dsn:
    sentry_sdk.init(dsn=settings.sentry_dsn, traces_sample_rate=0.1)

app = FastAPI(
    title="SlopSports Engine",
    version="0.1.0",
    lifespan=lifespan,
)


@app.get("/health")
async def health():
    return {"status": "ok", "env": settings.app_env}
```

### Step 3.6 — Database Setup

Create `src/db/session.py`:

```python
from sqlalchemy.ext.asyncio import AsyncSession, async_sessionmaker, create_async_engine

from src.config import settings

engine = create_async_engine(settings.database_url, echo=settings.app_debug)
async_session = async_sessionmaker(engine, class_=AsyncSession, expire_on_commit=False)


async def get_session() -> AsyncSession:
    async with async_session() as session:
        yield session
```

Create `src/db/models.py` — the core database schema:

```python
import enum
from datetime import datetime
from uuid import uuid4

from sqlalchemy import (
    Boolean,
    DateTime,
    Enum,
    Float,
    ForeignKey,
    Integer,
    String,
    Text,
)
from sqlalchemy.dialects.postgresql import JSONB, UUID
from sqlalchemy.orm import DeclarativeBase, Mapped, mapped_column, relationship


class Base(DeclarativeBase):
    pass


class AgentName(str, enum.Enum):
    RAY = "ray"
    DANNY = "danny"
    PATRICIA = "patricia"
    CARL = "carl"
    BIANCA = "bianca"


class ContentTier(int, enum.Enum):
    TIER_1 = 1  # Rapid reactions (Haiku)
    TIER_2 = 2  # Threads/analysis (Sonnet)
    TIER_3 = 3  # Creative/viral (Opus)


class ContentStatus(str, enum.Enum):
    DRAFT = "draft"
    QUEUED = "queued"
    APPROVED = "approved"
    PUBLISHED = "published"
    REJECTED = "rejected"


class Platform(str, enum.Enum):
    X = "x"
    STUDIO = "studio"
    TIKTOK = "tiktok"
    YOUTUBE = "youtube"
    DISCORD = "discord"
    PODCAST = "podcast"


class SportEvent(Base):
    """Raw sports events from The Odds API."""
    __tablename__ = "sport_events"

    id: Mapped[str] = mapped_column(UUID(as_uuid=False), primary_key=True, default=lambda: str(uuid4()))
    sport_key: Mapped[str] = mapped_column(String(50), index=True)
    event_id: Mapped[str] = mapped_column(String(100), unique=True, index=True)
    home_team: Mapped[str] = mapped_column(String(200))
    away_team: Mapped[str] = mapped_column(String(200))
    commence_time: Mapped[datetime] = mapped_column(DateTime(timezone=True))
    odds_data: Mapped[dict] = mapped_column(JSONB, default=dict)
    scores_data: Mapped[dict | None] = mapped_column(JSONB, nullable=True)
    created_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), default=datetime.utcnow)
    updated_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), default=datetime.utcnow, onupdate=datetime.utcnow)


class NarrativeEvent(Base):
    """Interpreted events that agents can react to (Layer 2 output)."""
    __tablename__ = "narrative_events"

    id: Mapped[str] = mapped_column(UUID(as_uuid=False), primary_key=True, default=lambda: str(uuid4()))
    event_type: Mapped[str] = mapped_column(String(50), index=True)  # line_movement, injury, score_update, etc.
    sport_event_id: Mapped[str | None] = mapped_column(ForeignKey("sport_events.id"), nullable=True)
    headline: Mapped[str] = mapped_column(String(500))
    details: Mapped[dict] = mapped_column(JSONB, default=dict)
    significance: Mapped[float] = mapped_column(Float, default=0.5)  # 0-1, how notable
    created_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), default=datetime.utcnow)

    sport_event: Mapped[SportEvent | None] = relationship()


class ContentPost(Base):
    """Generated content waiting for review/publishing (Layer 4 output)."""
    __tablename__ = "content_posts"

    id: Mapped[str] = mapped_column(UUID(as_uuid=False), primary_key=True, default=lambda: str(uuid4()))
    agent: Mapped[AgentName] = mapped_column(Enum(AgentName), index=True)
    tier: Mapped[ContentTier] = mapped_column(Enum(ContentTier))
    status: Mapped[ContentStatus] = mapped_column(Enum(ContentStatus), default=ContentStatus.DRAFT, index=True)
    platform: Mapped[Platform] = mapped_column(Enum(Platform))
    narrative_event_id: Mapped[str | None] = mapped_column(ForeignKey("narrative_events.id"), nullable=True)
    content_text: Mapped[str] = mapped_column(Text)
    content_metadata: Mapped[dict] = mapped_column(JSONB, default=dict)  # thread parts, media refs, etc.
    model_used: Mapped[str] = mapped_column(String(50))  # haiku-4.5, sonnet-4.6, etc.
    prompt_tokens: Mapped[int] = mapped_column(Integer, default=0)
    completion_tokens: Mapped[int] = mapped_column(Integer, default=0)
    scheduled_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
    published_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
    platform_post_id: Mapped[str | None] = mapped_column(String(100), nullable=True)  # tweet ID, etc.
    created_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), default=datetime.utcnow)

    narrative_event: Mapped[NarrativeEvent | None] = relationship()
    engagement: Mapped["PostEngagement | None"] = relationship(back_populates="post", uselist=False)


class PostEngagement(Base):
    """Engagement metrics for published content (Layer 7 input)."""
    __tablename__ = "post_engagement"

    id: Mapped[str] = mapped_column(UUID(as_uuid=False), primary_key=True, default=lambda: str(uuid4()))
    post_id: Mapped[str] = mapped_column(ForeignKey("content_posts.id"), unique=True)
    likes: Mapped[int] = mapped_column(Integer, default=0)
    reposts: Mapped[int] = mapped_column(Integer, default=0)
    replies: Mapped[int] = mapped_column(Integer, default=0)
    impressions: Mapped[int] = mapped_column(Integer, default=0)
    is_viral: Mapped[bool] = mapped_column(Boolean, default=False)
    last_checked_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), default=datetime.utcnow)

    post: Mapped[ContentPost] = relationship(back_populates="engagement")


class Prediction(Base):
    """Agent predictions with tracked outcomes (Layer 6)."""
    __tablename__ = "predictions"

    id: Mapped[str] = mapped_column(UUID(as_uuid=False), primary_key=True, default=lambda: str(uuid4()))
    agent: Mapped[AgentName] = mapped_column(Enum(AgentName), index=True)
    sport_event_id: Mapped[str | None] = mapped_column(ForeignKey("sport_events.id"), nullable=True)
    prediction_type: Mapped[str] = mapped_column(String(50))  # spread, moneyline, over_under, prop
    prediction_text: Mapped[str] = mapped_column(Text)
    prediction_data: Mapped[dict] = mapped_column(JSONB, default=dict)  # structured pick details
    confidence: Mapped[float] = mapped_column(Float, default=0.5)
    outcome: Mapped[str | None] = mapped_column(String(20), nullable=True)  # win, loss, push, pending
    content_post_id: Mapped[str | None] = mapped_column(ForeignKey("content_posts.id"), nullable=True)
    created_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), default=datetime.utcnow)
    resolved_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)

    sport_event: Mapped[SportEvent | None] = relationship()


class AgentMemory(Base):
    """Running storylines, grudges, callbacks — the narrative layer (Layer 6)."""
    __tablename__ = "agent_memory"

    id: Mapped[str] = mapped_column(UUID(as_uuid=False), primary_key=True, default=lambda: str(uuid4()))
    agent: Mapped[AgentName] = mapped_column(Enum(AgentName), index=True)
    memory_type: Mapped[str] = mapped_column(String(50), index=True)  # storyline, grudge, callback, streak
    summary: Mapped[str] = mapped_column(Text)
    details: Mapped[dict] = mapped_column(JSONB, default=dict)
    active: Mapped[bool] = mapped_column(Boolean, default=True)
    created_at: Mapped[datetime] = mapped_column(DateTime(timezone=True), default=datetime.utcnow)
    expires_at: Mapped[datetime | None] = mapped_column(DateTime(timezone=True), nullable=True)
```

### Step 3.7 — Alembic Migrations

Initialize Alembic for database migrations:

```bash
cd ~/projects/slopsports
alembic init src/db/migrations
```

Edit `alembic.ini` — set the database URL (or override with env var):

```ini
# In alembic.ini, update:
sqlalchemy.url = postgresql+asyncpg://slopsports:slopsports@localhost:5432/slopsports
```

Edit `src/db/migrations/env.py` to import your models:

```python
# Add at the top of env.py:
from src.db.models import Base
target_metadata = Base.metadata
```

Create the initial migration:

```bash
alembic revision --autogenerate -m "initial schema"
alembic upgrade head
```

### Step 3.8 — Celery Configuration

Create `tasks/__init__.py` with Celery app setup:

```python
from celery import Celery
from celery.schedules import crontab

from src.config import settings

celery_app = Celery(
    "slopsports",
    broker=settings.redis_url,
    backend=settings.redis_url,
)

celery_app.conf.update(
    task_serializer="json",
    accept_content=["json"],
    result_serializer="json",
    timezone="US/Eastern",  # Sports are Eastern time
    enable_utc=True,
    task_track_started=True,
    task_acks_late=True,
    worker_prefetch_multiplier=1,
)

# Periodic task schedule — these run automatically
celery_app.conf.beat_schedule = {
    # Ingest odds every 5 minutes during active game hours
    "ingest-odds": {
        "task": "tasks.ingest.fetch_odds",
        "schedule": 300.0,  # 5 minutes
    },
    # Check scores every 2 minutes during live games
    "ingest-scores": {
        "task": "tasks.ingest.fetch_scores",
        "schedule": 120.0,  # 2 minutes
    },
    # Monitor engagement for published posts every 10 minutes
    "monitor-engagement": {
        "task": "tasks.monitor.check_engagement",
        "schedule": 600.0,  # 10 minutes
    },
    # Daily prediction resolution at 6 AM ET
    "resolve-predictions": {
        "task": "tasks.monitor.resolve_predictions",
        "schedule": crontab(hour=6, minute=0),
    },
}
```

### Step 3.9 — .gitignore

Create `.gitignore`:

```
# Environment
.env
.env.local
.env.production

# Python
__pycache__/
*.py[cod]
*.egg-info/
dist/
build/
.eggs/
*.egg

# Virtual env
.venv/
venv/
env/

# IDE
.vscode/
.idea/
*.swp
*.swo

# Testing
.coverage
htmlcov/
.pytest_cache/

# Docker
postgres_data/
redis_data/

# OS
.DS_Store
Thumbs.db

# Mypy
.mypy_cache/

# Ruff
.ruff_cache/
```

### Step 3.10 — Verify Everything Runs

```bash
cd ~/projects/slopsports

# Copy environment template
cp .env.example .env
# Fill in at least DATABASE_URL and REDIS_URL (docker-compose defaults are fine)

# Build and start everything
docker compose up --build

# In another terminal, verify:
curl http://localhost:8000/health
# Should return: {"status": "ok", "env": "development"}

# Run migrations
docker compose exec app alembic upgrade head

# Run tests
docker compose exec app pytest
```

If the health endpoint returns `200` and the migration runs cleanly, Phase 3 is complete.

---

### Phase 3 Checklist

| # | Task | Status |
|---|------|--------|
| 3.1 | Directory structure created | ☐ |
| 3.2 | pyproject.toml + requirements.txt | ☐ |
| 3.3 | .env.example + src/config.py | ☐ |
| 3.4 | docker-compose.yml + Dockerfile | ☐ |
| 3.5 | FastAPI app with /health endpoint | ☐ |
| 3.6 | Database models (all 7 tables) | ☐ |
| 3.7 | Alembic migrations initialized + first migration | ☐ |
| 3.8 | Celery configuration with beat schedule | ☐ |
| 3.9 | .gitignore | ☐ |
| 3.10 | docker compose up → health check passes | ☐ |

**Phase 3 time estimate: 1 day**
**Phase 3 cost: $0** (all local development)

---

## Phase 4: Data Ingestion Layer (Layer 1)

Build the system that pulls real sports data from The Odds API and transforms it into structured events the engine can work with. This is the foundation — agents can't react to things they can't see.

---

### Step 4.1 — The Odds API Client

Create `src/data/odds_client.py`:

```python
import httpx
import structlog

from src.config import settings

logger = structlog.get_logger()

# Sports we track, ordered by priority
TRACKED_SPORTS = [
    "americanfootball_nfl",
    "basketball_nba",
    "americanfootball_ncaaf",
    "basketball_ncaab",
    "baseball_mlb",
    "icehockey_nhl",
    "mma_mixed_martial_arts",
    "soccer_usa_mls",
]

BASE_URL = "https://api.the-odds-api.com/v4"


class OddsClient:
    """Async client for The Odds API."""

    def __init__(self):
        self.api_key = settings.odds_api_key
        self.client = httpx.AsyncClient(timeout=30.0)

    async def get_odds(
        self,
        sport: str,
        regions: str = "us",
        markets: str = "h2h,spreads,totals",
        odds_format: str = "american",
    ) -> list[dict]:
        """Fetch current odds for a sport."""
        resp = await self.client.get(
            f"{BASE_URL}/sports/{sport}/odds",
            params={
                "apiKey": self.api_key,
                "regions": regions,
                "markets": markets,
                "oddsFormat": odds_format,
            },
        )
        resp.raise_for_status()
        remaining = resp.headers.get("x-requests-remaining", "?")
        logger.info("odds_fetched", sport=sport, events=len(resp.json()), api_remaining=remaining)
        return resp.json()

    async def get_scores(self, sport: str, days_from: int = 1) -> list[dict]:
        """Fetch scores for recently completed and live games."""
        resp = await self.client.get(
            f"{BASE_URL}/sports/{sport}/scores",
            params={
                "apiKey": self.api_key,
                "daysFrom": days_from,
            },
        )
        resp.raise_for_status()
        return resp.json()

    async def get_events(self, sport: str) -> list[dict]:
        """Fetch upcoming events for a sport."""
        resp = await self.client.get(
            f"{BASE_URL}/sports/{sport}/events",
            params={"apiKey": self.api_key},
        )
        resp.raise_for_status()
        return resp.json()

    async def close(self):
        await self.client.aclose()
```

**Key design decisions:**
- Async with `httpx` — non-blocking, plays well with FastAPI
- Logs remaining API requests on every call — you'll know before you hit rate limits
- Separate methods for odds, scores, and events — different polling frequencies

### Step 4.2 — Odds Snapshot & Line Movement Detection

The raw odds aren't useful on their own. The engine needs to detect *changes* — that's what makes content. Create `src/data/odds_tracker.py`:

```python
import structlog
from sqlalchemy import select
from sqlalchemy.ext.asyncio import AsyncSession

from src.db.models import SportEvent

logger = structlog.get_logger()


class OddsTracker:
    """Compares fresh odds data against stored snapshots to detect movements."""

    async def process_odds(self, session: AsyncSession, sport_key: str, odds_data: list[dict]) -> list[dict]:
        """Store fresh odds and return list of detected movements."""
        movements = []

        for event in odds_data:
            event_id = event["id"]

            # Check if we've seen this event before
            result = await session.execute(
                select(SportEvent).where(SportEvent.event_id == event_id)
            )
            existing = result.scalar_one_or_none()

            if existing is None:
                # New event — store it
                new_event = SportEvent(
                    sport_key=sport_key,
                    event_id=event_id,
                    home_team=event["home_team"],
                    away_team=event["away_team"],
                    commence_time=event["commence_time"],
                    odds_data=event,
                )
                session.add(new_event)
            else:
                # Existing event — compare odds for movement
                old_odds = existing.odds_data
                detected = self._detect_movements(old_odds, event)
                if detected:
                    movements.extend(detected)
                    logger.info(
                        "line_movement_detected",
                        event_id=event_id,
                        movements=len(detected),
                    )
                # Update stored data
                existing.odds_data = event

        await session.commit()
        return movements

    def _detect_movements(self, old: dict, new: dict) -> list[dict]:
        """Compare two snapshots and return significant movements."""
        movements = []
        old_books = {b["key"]: b for b in old.get("bookmakers", [])}
        new_books = {b["key"]: b for b in new.get("bookmakers", [])}

        for book_key, new_book in new_books.items():
            old_book = old_books.get(book_key)
            if not old_book:
                continue

            for new_market in new_book.get("markets", []):
                market_key = new_market["key"]
                old_market = next(
                    (m for m in old_book.get("markets", []) if m["key"] == market_key),
                    None,
                )
                if not old_market:
                    continue

                for new_outcome, old_outcome in zip(
                    sorted(new_market["outcomes"], key=lambda x: x["name"]),
                    sorted(old_market["outcomes"], key=lambda x: x["name"]),
                ):
                    if new_outcome.get("point") != old_outcome.get("point"):
                        movements.append({
                            "type": "spread_move" if market_key == "spreads" else "total_move",
                            "book": book_key,
                            "team": new_outcome["name"],
                            "old_line": old_outcome.get("point"),
                            "new_line": new_outcome.get("point"),
                            "home_team": new["home_team"],
                            "away_team": new["away_team"],
                            "event_id": new["id"],
                        })

                    if abs(new_outcome.get("price", 0) - old_outcome.get("price", 0)) >= 15:
                        movements.append({
                            "type": "price_move",
                            "book": book_key,
                            "team": new_outcome["name"],
                            "market": market_key,
                            "old_price": old_outcome.get("price"),
                            "new_price": new_outcome.get("price"),
                            "home_team": new["home_team"],
                            "away_team": new["away_team"],
                            "event_id": new["id"],
                        })

        return movements
```

**What this detects:**
- Spread movements (e.g., Celtics go from -7 to -5.5 — "reverse line movement")
- Total movements (e.g., over/under drops from 220.5 to 218)
- Significant price shifts (e.g., -110 to -130 — sharp money signal)

These are the exact kinds of events that trigger Ray's data analysis, Danny's degenerate reactions, and Carl's conspiracy theories.

### Step 4.3 — Celery Ingestion Tasks

Create `tasks/ingest.py`:

```python
from tasks import celery_app


@celery_app.task(name="tasks.ingest.fetch_odds")
def fetch_odds():
    """Periodic task: fetch odds for all tracked sports."""
    import asyncio
    asyncio.run(_fetch_odds_async())


async def _fetch_odds_async():
    from src.data.odds_client import OddsClient, TRACKED_SPORTS
    from src.data.odds_tracker import OddsTracker
    from src.db.session import async_session

    client = OddsClient()
    tracker = OddsTracker()

    try:
        async with async_session() as session:
            all_movements = []
            for sport in TRACKED_SPORTS:
                try:
                    odds = await client.get_odds(sport)
                    movements = await tracker.process_odds(session, sport, odds)
                    all_movements.extend(movements)
                except Exception as e:
                    # Log but don't stop — other sports should still work
                    import structlog
                    structlog.get_logger().error("odds_fetch_failed", sport=sport, error=str(e))

            if all_movements:
                # Queue movements for interpretation (Layer 2)
                from tasks.generate import interpret_movements
                interpret_movements.delay(all_movements)
    finally:
        await client.close()


@celery_app.task(name="tasks.ingest.fetch_scores")
def fetch_scores():
    """Periodic task: fetch scores for live/recent games."""
    import asyncio
    asyncio.run(_fetch_scores_async())


async def _fetch_scores_async():
    from src.data.odds_client import OddsClient, TRACKED_SPORTS
    from src.db.session import async_session
    from src.db.models import SportEvent
    from sqlalchemy import select

    client = OddsClient()

    try:
        async with async_session() as session:
            for sport in TRACKED_SPORTS:
                try:
                    scores = await client.get_scores(sport)
                    for score_data in scores:
                        result = await session.execute(
                            select(SportEvent).where(SportEvent.event_id == score_data["id"])
                        )
                        event = result.scalar_one_or_none()
                        if event:
                            event.scores_data = score_data
                    await session.commit()
                except Exception as e:
                    import structlog
                    structlog.get_logger().error("scores_fetch_failed", sport=sport, error=str(e))
    finally:
        await client.close()
```

### Step 4.4 — API Endpoints for Data

Add data-facing API routes in `src/api/dashboard.py`:

```python
from fastapi import APIRouter, Depends
from sqlalchemy import select, func
from sqlalchemy.ext.asyncio import AsyncSession

from src.db.models import SportEvent, NarrativeEvent, ContentPost, ContentStatus
from src.db.session import get_session

router = APIRouter(prefix="/api", tags=["dashboard"])


@router.get("/events")
async def list_events(
    sport: str | None = None,
    limit: int = 50,
    session: AsyncSession = Depends(get_session),
):
    """List recent sport events with odds data."""
    query = select(SportEvent).order_by(SportEvent.commence_time.desc()).limit(limit)
    if sport:
        query = query.where(SportEvent.sport_key == sport)
    result = await session.execute(query)
    return result.scalars().all()


@router.get("/narrative-events")
async def list_narrative_events(
    limit: int = 50,
    session: AsyncSession = Depends(get_session),
):
    """List recent narrative events (Layer 2 output)."""
    query = select(NarrativeEvent).order_by(NarrativeEvent.created_at.desc()).limit(limit)
    result = await session.execute(query)
    return result.scalars().all()


@router.get("/content-queue")
async def content_queue(
    status: ContentStatus | None = None,
    session: AsyncSession = Depends(get_session),
):
    """View the content generation queue."""
    query = select(ContentPost).order_by(ContentPost.created_at.desc()).limit(100)
    if status:
        query = query.where(ContentPost.status == status)
    result = await session.execute(query)
    return result.scalars().all()


@router.get("/stats")
async def engine_stats(session: AsyncSession = Depends(get_session)):
    """Quick stats for the admin dashboard."""
    events = await session.execute(select(func.count(SportEvent.id)))
    posts = await session.execute(select(func.count(ContentPost.id)))
    published = await session.execute(
        select(func.count(ContentPost.id)).where(ContentPost.status == ContentStatus.PUBLISHED)
    )
    return {
        "total_events": events.scalar(),
        "total_posts": posts.scalar(),
        "published_posts": published.scalar(),
    }
```

Wire the router into `src/main.py`:

```python
# Add to src/main.py after app creation:
from src.api.dashboard import router as dashboard_router
app.include_router(dashboard_router)
```

### Step 4.5 — Manual Trigger Endpoints

Create `src/api/admin.py` for manually triggering ingestion (useful during development):

```python
from fastapi import APIRouter

router = APIRouter(prefix="/admin", tags=["admin"])


@router.post("/trigger/ingest-odds")
async def trigger_ingest_odds():
    """Manually trigger odds ingestion (dev/admin use)."""
    from tasks.ingest import fetch_odds
    fetch_odds.delay()
    return {"status": "queued", "task": "fetch_odds"}


@router.post("/trigger/ingest-scores")
async def trigger_ingest_scores():
    """Manually trigger scores ingestion."""
    from tasks.ingest import fetch_scores
    fetch_scores.delay()
    return {"status": "queued", "task": "fetch_scores"}
```

Wire it into `src/main.py`:

```python
from src.api.admin import router as admin_router
app.include_router(admin_router)
```

### Step 4.6 — Test the Data Pipeline

```bash
# Make sure your .env has a valid ODDS_API_KEY
docker compose up --build

# Trigger manual ingestion
curl -X POST http://localhost:8000/admin/trigger/ingest-odds

# Wait ~10 seconds for Celery to process, then check:
curl http://localhost:8000/api/events
# Should return a list of sporting events with odds data

curl http://localhost:8000/api/stats
# Should show total_events > 0
```

If events come back with real data, the data pipeline is live.

### Step 4.7 — Simulator Mode

Create `src/publisher/simulator.py` — this logs output instead of posting to real platforms. Used throughout development:

```python
import structlog

logger = structlog.get_logger()


class SimulatorPublisher:
    """Logs content instead of posting to real platforms. Used in development."""

    async def publish(self, agent: str, platform: str, content: str, metadata: dict | None = None):
        logger.info(
            "SIMULATED_POST",
            agent=agent,
            platform=platform,
            content=content[:200],
            metadata=metadata,
        )
        return {"status": "simulated", "agent": agent, "platform": platform}
```

All code paths that publish content should check `settings.app_env` — if it's `"development"`, route through SimulatorPublisher instead of real API clients. This means you can run the full pipeline end-to-end without posting a single real tweet.

---

### Phase 4 Checklist

| # | Task | Status |
|---|------|--------|
| 4.1 | OddsClient — async client for The Odds API | ☐ |
| 4.2 | OddsTracker — line movement detection | ☐ |
| 4.3 | Celery ingestion tasks (fetch_odds, fetch_scores) | ☐ |
| 4.4 | Dashboard API endpoints (/api/events, /api/stats) | ☐ |
| 4.5 | Admin trigger endpoints (/admin/trigger/*) | ☐ |
| 4.6 | End-to-end test: trigger ingestion → see events in API | ☐ |
| 4.7 | Simulator publisher for development | ☐ |

**Phase 4 time estimate: 1-2 days**
**Phase 4 cost: Free** (Odds API free tier for development, ~$0.005 in API calls)

---

## Phase 5: Agent System & Content Generation (Layers 2-4)

This is where the engine comes alive. Raw data becomes narrative events, narrative events get routed to agents, and agents generate personality-driven content through Claude.

---

### Step 5.1 — Event Type Definitions (Layer 2)

Create `src/engine/events.py` — defines every type of event the system can react to:

```python
from dataclasses import dataclass, field
from enum import Enum


class EventType(str, Enum):
    # Line movements
    LINE_MOVEMENT = "line_movement"
    REVERSE_LINE_MOVEMENT = "reverse_line_movement"  # Public on one side, line moves other way
    STEAM_MOVE = "steam_move"  # Sharp money floods in, line moves fast

    # Game events
    GAME_START = "game_start"
    SCORE_UPDATE = "score_update"
    GAME_END = "game_end"
    UPSET = "upset"
    BLOWOUT = "blowout"
    COMEBACK = "comeback"

    # News
    INJURY = "injury"
    TRADE = "trade"
    LINEUP_CHANGE = "lineup_change"

    # Agent-driven
    PREDICTION_RESULT = "prediction_result"  # An agent's pick won or lost
    STREAK_MILESTONE = "streak_milestone"  # Agent hits 5 in a row, etc.
    AGENT_CONFLICT = "agent_conflict"  # Two agents disagree on the same game

    # Meta
    DAILY_SLATE = "daily_slate"  # Morning overview of the day's games
    WEEKLY_RECAP = "weekly_recap"  # End-of-week prediction results


@dataclass
class NarrativeEventData:
    """Structured event that the agent reaction engine consumes."""
    event_type: EventType
    headline: str
    details: dict = field(default_factory=dict)
    significance: float = 0.5  # 0.0 (trivial) to 1.0 (critical)
    sport_key: str = ""
    event_id: str | None = None

    # Which agents might care about this?
    relevant_agents: list[str] = field(default_factory=list)
```

### Step 5.2 — Interpretation Engine (Layer 2)

Create `src/engine/interpreter.py` — transforms raw data movements into narrative events:

```python
import structlog
from sqlalchemy.ext.asyncio import AsyncSession

from src.db.models import NarrativeEvent
from src.engine.events import EventType, NarrativeEventData

logger = structlog.get_logger()


class Interpreter:
    """Transforms raw data signals into narrative events agents can react to."""

    def interpret_line_movements(self, movements: list[dict]) -> list[NarrativeEventData]:
        """Convert raw line movement data into narrative events."""
        events = []

        for m in movements:
            if m["type"] == "spread_move":
                old_line = m["old_line"]
                new_line = m["new_line"]
                shift = abs(new_line - old_line) if old_line and new_line else 0

                # Big moves (1.5+ points) are significant
                if shift >= 1.5:
                    event_type = EventType.REVERSE_LINE_MOVEMENT
                    significance = min(0.9, 0.5 + shift * 0.1)
                    headline = (
                        f"{m['away_team']} @ {m['home_team']}: "
                        f"spread moved from {old_line} to {new_line} at {m['book']} "
                        f"({'+' if new_line > old_line else ''}{new_line - old_line:.1f} points)"
                    )
                    events.append(NarrativeEventData(
                        event_type=event_type,
                        headline=headline,
                        details=m,
                        significance=significance,
                        event_id=m.get("event_id"),
                        relevant_agents=["ray", "danny", "carl"],
                    ))

                # Moderate moves still worth noting
                elif shift >= 0.5:
                    events.append(NarrativeEventData(
                        event_type=EventType.LINE_MOVEMENT,
                        headline=(
                            f"{m['away_team']} @ {m['home_team']}: "
                            f"spread {old_line} → {new_line} ({m['book']})"
                        ),
                        details=m,
                        significance=0.3 + shift * 0.1,
                        event_id=m.get("event_id"),
                        relevant_agents=["ray"],
                    ))

            elif m["type"] == "price_move":
                events.append(NarrativeEventData(
                    event_type=EventType.LINE_MOVEMENT,
                    headline=(
                        f"{m['away_team']} @ {m['home_team']}: "
                        f"{m['team']} {m['market']} price moved "
                        f"{m['old_price']} → {m['new_price']} ({m['book']})"
                    ),
                    details=m,
                    significance=0.3,
                    event_id=m.get("event_id"),
                    relevant_agents=["ray"],
                ))

        return events

    def interpret_game_result(self, score_data: dict, event_data: dict) -> list[NarrativeEventData]:
        """Convert a completed game into narrative events."""
        events = []

        if not score_data.get("completed"):
            return events

        scores = score_data.get("scores", [])
        if len(scores) < 2:
            return events

        home_score = next((s["score"] for s in scores if s["name"] == score_data["home_team"]), 0)
        away_score = next((s["score"] for s in scores if s["name"] == score_data["away_team"]), 0)
        home_score, away_score = int(home_score), int(away_score)
        margin = abs(home_score - away_score)

        winner = score_data["home_team"] if home_score > away_score else score_data["away_team"]

        # Check for upset (was the winner a big underdog?)
        spread = event_data.get("odds_data", {})  # Would need to extract pre-game spread
        # Simplified: treat 20+ point margins as blowouts
        if margin >= 20:
            events.append(NarrativeEventData(
                event_type=EventType.BLOWOUT,
                headline=f"BLOWOUT: {winner} wins by {margin} — {score_data['away_team']} {away_score}, {score_data['home_team']} {home_score}",
                details={"home_score": home_score, "away_score": away_score, "margin": margin},
                significance=0.7,
                relevant_agents=["ray", "danny", "patricia", "carl"],
            ))
        else:
            events.append(NarrativeEventData(
                event_type=EventType.GAME_END,
                headline=f"FINAL: {score_data['away_team']} {away_score}, {score_data['home_team']} {home_score}",
                details={"home_score": home_score, "away_score": away_score, "margin": margin},
                significance=0.4,
                relevant_agents=["ray", "danny"],
            ))

        return events

    async def save_events(self, session: AsyncSession, events: list[NarrativeEventData]) -> list[str]:
        """Persist narrative events to the database. Returns list of created IDs."""
        ids = []
        for event in events:
            db_event = NarrativeEvent(
                event_type=event.event_type.value,
                headline=event.headline,
                details=event.details,
                significance=event.significance,
                sport_event_id=event.event_id,
            )
            session.add(db_event)
            ids.append(db_event.id)
        await session.commit()
        return ids
```

### Step 5.3 — Agent Reaction Engine (Layer 3)

Create `src/engine/reactor.py` — decides which agents react and how:

```python
import random

import structlog

from src.engine.events import EventType, NarrativeEventData

logger = structlog.get_logger()


# Maps event types to which agents react and their content tier
REACTION_MAP: dict[EventType, dict[str, dict]] = {
    EventType.REVERSE_LINE_MOVEMENT: {
        "ray": {"tier": 2, "probability": 0.95, "angle": "data_analysis"},
        "carl": {"tier": 1, "probability": 0.6, "angle": "conspiracy"},
        "danny": {"tier": 1, "probability": 0.4, "angle": "degenerate_take"},
    },
    EventType.LINE_MOVEMENT: {
        "ray": {"tier": 1, "probability": 0.7, "angle": "data_analysis"},
    },
    EventType.STEAM_MOVE: {
        "ray": {"tier": 2, "probability": 1.0, "angle": "sharp_money_alert"},
        "danny": {"tier": 1, "probability": 0.8, "angle": "tail_the_sharp"},
        "carl": {"tier": 2, "probability": 0.5, "angle": "who_benefits"},
    },
    EventType.GAME_END: {
        "ray": {"tier": 1, "probability": 0.6, "angle": "result_analysis"},
        "danny": {"tier": 1, "probability": 0.8, "angle": "emotional_reaction"},
    },
    EventType.UPSET: {
        "ray": {"tier": 2, "probability": 0.9, "angle": "data_breakdown"},
        "danny": {"tier": 2, "probability": 0.9, "angle": "meltdown_or_celebration"},
        "patricia": {"tier": 2, "probability": 0.8, "angle": "coaching_analysis"},
        "carl": {"tier": 2, "probability": 0.7, "angle": "scripted_narrative"},
    },
    EventType.BLOWOUT: {
        "ray": {"tier": 1, "probability": 0.7, "angle": "result_analysis"},
        "danny": {"tier": 1, "probability": 0.9, "angle": "emotional_reaction"},
        "patricia": {"tier": 1, "probability": 0.6, "angle": "film_breakdown"},
    },
    EventType.PREDICTION_RESULT: {
        "ray": {"tier": 1, "probability": 1.0, "angle": "record_update"},
        "danny": {"tier": 1, "probability": 1.0, "angle": "emotional_reaction"},
    },
    EventType.DAILY_SLATE: {
        "ray": {"tier": 2, "probability": 1.0, "angle": "daily_breakdown"},
        "danny": {"tier": 1, "probability": 0.9, "angle": "parlay_of_the_day"},
        "patricia": {"tier": 2, "probability": 0.7, "angle": "matchup_scouting"},
    },
    EventType.AGENT_CONFLICT: {
        "ray": {"tier": 2, "probability": 0.9, "angle": "rebuttal"},
        "patricia": {"tier": 2, "probability": 0.9, "angle": "rebuttal"},
        "carl": {"tier": 1, "probability": 0.5, "angle": "side_commentary"},
    },
}


@dataclass
class AgentReaction:
    agent: str
    tier: int
    angle: str
    narrative_event: NarrativeEventData


from dataclasses import dataclass


class Reactor:
    """Determines which agents react to narrative events and how."""

    def assign_reactions(self, events: list[NarrativeEventData]) -> list[AgentReaction]:
        """Given narrative events, determine which agents react."""
        reactions = []

        for event in events:
            event_reactions = REACTION_MAP.get(event.event_type, {})

            for agent_name, config in event_reactions.items():
                # Skip agents not listed as relevant (if specified)
                if event.relevant_agents and agent_name not in event.relevant_agents:
                    continue

                # Probability check — not every event triggers every agent
                if random.random() > config["probability"]:
                    continue

                # Higher significance events can bump the content tier
                tier = config["tier"]
                if event.significance >= 0.8 and tier < 3:
                    tier += 1

                reactions.append(AgentReaction(
                    agent=agent_name,
                    tier=tier,
                    angle=config["angle"],
                    narrative_event=event,
                ))

        logger.info("reactions_assigned", count=len(reactions), events=len(events))
        return reactions
```

### Step 5.4 — Post Scheduling & Staggering

Create `src/engine/scheduler.py` — prevents all agents from posting at once:

```python
from datetime import datetime, timedelta, timezone
from dataclasses import dataclass

from src.engine.reactor import AgentReaction


@dataclass
class ScheduledReaction(AgentReaction):
    scheduled_at: datetime = None


class Scheduler:
    """Staggers agent posts so they don't all fire simultaneously."""

    # Minimum gap between posts from the same agent (seconds)
    SAME_AGENT_GAP = 300  # 5 minutes

    # Minimum gap between any two posts (seconds)
    GLOBAL_GAP = 60  # 1 minute

    # Tier-based delays — higher tier = more deliberate timing
    TIER_DELAYS = {
        1: (30, 120),    # 30s to 2min — rapid reactions
        2: (300, 900),   # 5-15min — analysis takes time
        3: (900, 3600),  # 15-60min — crafted content
    }

    def schedule(self, reactions: list[AgentReaction]) -> list[ScheduledReaction]:
        """Assign publish times to reactions with natural-feeling stagger."""
        import random

        now = datetime.now(timezone.utc)
        scheduled = []
        last_post_per_agent: dict[str, datetime] = {}
        last_global_post = now

        # Sort by tier (lower tier = faster reaction)
        reactions_sorted = sorted(reactions, key=lambda r: r.tier)

        for reaction in reactions_sorted:
            min_delay, max_delay = self.TIER_DELAYS.get(reaction.tier, (60, 300))
            delay = random.randint(min_delay, max_delay)
            proposed_time = now + timedelta(seconds=delay)

            # Enforce same-agent gap
            last_agent = last_post_per_agent.get(reaction.agent)
            if last_agent:
                earliest = last_agent + timedelta(seconds=self.SAME_AGENT_GAP)
                proposed_time = max(proposed_time, earliest)

            # Enforce global gap
            earliest_global = last_global_post + timedelta(seconds=self.GLOBAL_GAP)
            proposed_time = max(proposed_time, earliest_global)

            scheduled_reaction = ScheduledReaction(
                agent=reaction.agent,
                tier=reaction.tier,
                angle=reaction.angle,
                narrative_event=reaction.narrative_event,
                scheduled_at=proposed_time,
            )
            scheduled.append(scheduled_reaction)
            last_post_per_agent[reaction.agent] = proposed_time
            last_global_post = proposed_time

        return scheduled
```

### Step 5.5 — Base Agent Definition

Create `src/agents/base.py`:

```python
from dataclasses import dataclass, field


@dataclass
class AgentPersonality:
    """Defines an agent's personality for content generation."""
    name: str
    display_name: str
    bio: str
    voice: str  # Description of their writing style
    catchphrases: list[str] = field(default_factory=list)
    topics: list[str] = field(default_factory=list)  # What they care about
    relationships: dict[str, str] = field(default_factory=dict)  # agent_name → relationship description
    content_rules: list[str] = field(default_factory=list)  # Hard rules for content generation
    system_prompt: str = ""  # Full system prompt for Claude (built from above fields)

    def build_system_prompt(self) -> str:
        """Construct the full system prompt from personality traits."""
        relationships_text = "\n".join(
            f"- {name}: {desc}" for name, desc in self.relationships.items()
        )
        rules_text = "\n".join(f"- {rule}" for rule in self.content_rules)
        catchphrases_text = ", ".join(f'"{c}"' for c in self.catchphrases)

        self.system_prompt = f"""You are {self.display_name}, a sports personality on social media.

## Who You Are
{self.bio}

## Your Voice
{self.voice}

## Your Catchphrases (use naturally, not in every post)
{catchphrases_text}

## Topics You Care About
{', '.join(self.topics)}

## Your Relationships With Other Analysts
{relationships_text}

## Hard Rules
{rules_text}
- NEVER break character.
- NEVER mention that you are AI, a bot, or automated.
- NEVER give financial advice or tell people to bet specific amounts.
- Posts should feel like a real person typed them — imperfect, opinionated, human.
- Include sports-specific details (player names, team records, specific stats) when relevant.
"""
        return self.system_prompt
```

### Step 5.6 — Ray "The Sharp" Castellano

Create `src/agents/ray.py` — the first agent, launching solo in Phase 1:

```python
from src.agents.base import AgentPersonality

ray = AgentPersonality(
    name="ray",
    display_name='Ray "The Sharp" Castellano',
    bio=(
        "You're Ray Castellano — cold, data-obsessed sports analyst. You never bet on emotion. "
        "You respect the math. You've tracked line movements for 15 years and you can smell "
        "sharp money from a mile away. You're not here to entertain — you're here to be right. "
        "The public loses because they think with their hearts. You think with spreadsheets."
    ),
    voice=(
        "Clinical. Slightly condescending but earned. Dry wit. You speak in numbers and percentages. "
        "Short, punchy sentences. You don't waste words. When you're right, you let the data speak. "
        "When the public is wrong, you enjoy pointing it out — not cruelly, just factually. "
        "Occasionally you show a sliver of genuine excitement when a perfect data setup appears."
    ),
    catchphrases=[
        "The line tells you everything.",
        "Public money is noise.",
        "Sharp money doesn't lie.",
        "Follow the steam.",
        "The math doesn't care about your feelings.",
        "I don't make picks. I identify value.",
    ],
    topics=[
        "Line movements and what they mean",
        "Sharp vs. public money",
        "Reverse line movement (his favorite)",
        "Closing line value",
        "Betting market efficiency",
        "Data-driven game previews",
        "Post-game result analysis vs. pre-game odds",
    ],
    relationships={
        "Danny": "Condescending but not cruel. Occasionally gives Danny a nugget of real analysis, which Danny inevitably misuses. Views Danny as entertainment, not a peer.",
        "Patricia": "Respects her experience but thinks her 'eye test' is unscientific. Their disagreements are philosophical — data vs. instinct. There's grudging mutual respect underneath.",
        "Carl": "Dismissive. Carl accuses Ray of being 'part of the system.' Ray ignores him unless Carl accidentally stumbles onto a real data point, which amuses Ray.",
        "Bianca": "Professional respect. She provides the information, he provides the analysis. They occasionally collaborate on big stories.",
    },
    content_rules=[
        "Always cite specific numbers — don't just say 'the line moved,' say 'the line moved from -7 to -5.5 at Pinnacle.'",
        "When analyzing a game, mention at least one specific data point (record ATS, home/away splits, etc.).",
        "Never use all caps or excessive punctuation. You're calm. Always.",
        "When you're wrong about a prediction, acknowledge it briefly and clinically — 'Miss. Variance.' — then move on.",
        "When referencing MOONSHOT data, say it naturally: 'My models show...' or 'The data I'm looking at...'",
        "Mix in non-betting sports content — a great play, a coaching decision, a trade analysis — 60% of your content is sports entertainment, not betting.",
    ],
)

ray.build_system_prompt()
```

### Step 5.7 — Content Generator (Layer 4)

Create `src/content/generator.py` — the core content creation engine:

```python
import anthropic
import structlog

from src.agents.base import AgentPersonality
from src.config import settings
from src.engine.events import NarrativeEventData

logger = structlog.get_logger()

# Model selection by content tier
TIER_MODELS = {
    1: "claude-haiku-4-5-20251001",
    2: "claude-sonnet-4-6-20260320",
    3: "claude-opus-4-6-20260320",
}


class ContentGenerator:
    """Generates agent content via Anthropic Claude API."""

    def __init__(self):
        self.client = anthropic.AsyncAnthropic(api_key=settings.anthropic_api_key)

    async def generate(
        self,
        agent: AgentPersonality,
        event: NarrativeEventData,
        tier: int,
        angle: str,
        platform: str = "x",
        reply_to: str | None = None,
    ) -> dict:
        """Generate content for a specific agent reacting to an event."""

        model = TIER_MODELS.get(tier, TIER_MODELS[1])
        max_tokens = self._max_tokens_for_platform(platform, tier)

        user_prompt = self._build_user_prompt(event, angle, platform, reply_to)

        response = await self.client.messages.create(
            model=model,
            max_tokens=max_tokens,
            system=[{
                "type": "text",
                "text": agent.system_prompt,
                "cache_control": {"type": "ephemeral"},  # Cache the system prompt
            }],
            messages=[{"role": "user", "content": user_prompt}],
        )

        content_text = response.content[0].text
        usage = response.usage

        logger.info(
            "content_generated",
            agent=agent.name,
            tier=tier,
            model=model,
            platform=platform,
            input_tokens=usage.input_tokens,
            output_tokens=usage.output_tokens,
            content_length=len(content_text),
        )

        return {
            "content": content_text,
            "model": model,
            "input_tokens": usage.input_tokens,
            "output_tokens": usage.output_tokens,
        }

    def _build_user_prompt(
        self,
        event: NarrativeEventData,
        angle: str,
        platform: str,
        reply_to: str | None,
    ) -> str:
        """Build the user-facing prompt with event context and format instructions."""

        format_instructions = self._format_instructions(platform)

        prompt = f"""React to this event with your unique perspective.

## Event
**Type:** {event.event_type.value}
**Headline:** {event.headline}
**Details:** {event.details}
**Your Angle:** {angle}

## Format
{format_instructions}
"""
        if reply_to:
            prompt += f"\n## You're replying to this post:\n{reply_to}\n"

        return prompt

    def _format_instructions(self, platform: str) -> str:
        """Platform-specific format instructions."""
        if platform == "x":
            return (
                "Write a single tweet (max 280 characters). No hashtags unless they're natural. "
                "No emojis unless they fit your character. Just the tweet text, nothing else."
            )
        elif platform == "x_thread":
            return (
                "Write a thread of 3-5 tweets. Separate each tweet with ---. "
                "Each tweet max 280 characters. First tweet should hook. Last tweet should land."
            )
        elif platform == "studio":
            return (
                "Write a full-length take (200-500 words). This is your home turf — go deep. "
                "Include your analysis, opinions, and personality. Format with short paragraphs."
            )
        elif platform == "discord":
            return (
                "Write a Discord message (1-3 paragraphs). Casual tone. "
                "Can include markdown formatting."
            )
        return "Write a natural social media post in your voice."

    def _max_tokens_for_platform(self, platform: str, tier: int) -> int:
        if platform in ("x",):
            return 150
        elif platform == "x_thread":
            return 600
        elif platform == "studio":
            return 1500
        return 500
```

**Key design decisions:**
- **Prompt caching:** The `cache_control` on the system prompt means agent personality prompts (which are the same every call) get cached. This cuts input token costs by ~90% for repeated calls.
- **Model tiering:** Haiku for quick reactions (cheap, fast), Sonnet for analysis threads (quality), Opus for viral attempts (rare, premium).
- **Platform-aware formatting:** Same event gets different output for X (280 chars) vs. Studio (full analysis) vs. Discord (casual).

### Step 5.8 — Content Review Queue

Create `src/content/review_queue.py` — manages the human review pipeline:

```python
import structlog
from sqlalchemy import select, update
from sqlalchemy.ext.asyncio import AsyncSession

from src.config import settings
from src.db.models import ContentPost, ContentStatus, ContentTier

logger = structlog.get_logger()


class ReviewQueue:
    """Manages content approval flow based on tier."""

    async def submit(self, session: AsyncSession, post: ContentPost) -> ContentStatus:
        """Submit a post to the review queue. Returns its new status."""

        if post.tier == ContentTier.TIER_1 and settings.auto_publish_tier_1:
            post.status = ContentStatus.APPROVED
            logger.info("auto_approved", post_id=post.id, tier=1, agent=post.agent.value)

        elif post.tier == ContentTier.TIER_2 and settings.auto_publish_tier_2:
            post.status = ContentStatus.APPROVED
            logger.info("auto_approved", post_id=post.id, tier=2, agent=post.agent.value)

        elif post.tier == ContentTier.TIER_3 and settings.auto_publish_tier_3:
            post.status = ContentStatus.APPROVED
            logger.info("auto_approved", post_id=post.id, tier=3, agent=post.agent.value)

        else:
            post.status = ContentStatus.QUEUED
            logger.info("queued_for_review", post_id=post.id, tier=post.tier.value, agent=post.agent.value)

        session.add(post)
        await session.commit()
        return post.status

    async def approve(self, session: AsyncSession, post_id: str) -> ContentPost | None:
        """Manually approve a queued post."""
        result = await session.execute(
            select(ContentPost).where(ContentPost.id == post_id)
        )
        post = result.scalar_one_or_none()
        if post and post.status == ContentStatus.QUEUED:
            post.status = ContentStatus.APPROVED
            await session.commit()
            logger.info("manually_approved", post_id=post_id)
        return post

    async def reject(self, session: AsyncSession, post_id: str) -> ContentPost | None:
        """Reject a queued post."""
        result = await session.execute(
            select(ContentPost).where(ContentPost.id == post_id)
        )
        post = result.scalar_one_or_none()
        if post and post.status == ContentStatus.QUEUED:
            post.status = ContentStatus.REJECTED
            await session.commit()
            logger.info("rejected", post_id=post_id)
        return post
```

### Step 5.9 — Content Generation Celery Tasks

Create `tasks/generate.py` — wires Layer 2 → 3 → 4 together:

```python
import asyncio

from tasks import celery_app


@celery_app.task(name="tasks.generate.interpret_movements")
def interpret_movements(movements: list[dict]):
    """Layer 2: Convert raw movements into narrative events, then trigger reactions."""
    asyncio.run(_interpret_async(movements))


async def _interpret_async(movements: list[dict]):
    from src.engine.interpreter import Interpreter
    from src.engine.reactor import Reactor
    from src.engine.scheduler import Scheduler
    from src.db.session import async_session

    interpreter = Interpreter()
    reactor = Reactor()
    scheduler = Scheduler()

    # Layer 2: Raw data → narrative events
    narrative_events = interpreter.interpret_line_movements(movements)

    if not narrative_events:
        return

    # Save narrative events to DB
    async with async_session() as session:
        await interpreter.save_events(session, narrative_events)

    # Layer 3: Narrative events → agent reactions
    reactions = reactor.assign_reactions(narrative_events)

    if not reactions:
        return

    # Schedule reactions with staggered timing
    scheduled = scheduler.schedule(reactions)

    # Queue each scheduled reaction as a content generation task
    for reaction in scheduled:
        generate_content.apply_async(
            kwargs={
                "agent_name": reaction.agent,
                "event_type": reaction.narrative_event.event_type.value,
                "headline": reaction.narrative_event.headline,
                "details": reaction.narrative_event.details,
                "tier": reaction.tier,
                "angle": reaction.angle,
            },
            eta=reaction.scheduled_at,  # Celery delivers at the scheduled time
        )


@celery_app.task(name="tasks.generate.generate_content")
def generate_content(
    agent_name: str,
    event_type: str,
    headline: str,
    details: dict,
    tier: int,
    angle: str,
):
    """Layer 4: Generate content for a specific agent reaction."""
    asyncio.run(_generate_async(agent_name, event_type, headline, details, tier, angle))


async def _generate_async(
    agent_name: str,
    event_type: str,
    headline: str,
    details: dict,
    tier: int,
    angle: str,
):
    from src.agents import get_agent
    from src.content.generator import ContentGenerator
    from src.content.review_queue import ReviewQueue
    from src.db.models import AgentName, ContentPost, ContentTier, Platform
    from src.db.session import async_session
    from src.engine.events import EventType, NarrativeEventData

    agent = get_agent(agent_name)
    if not agent:
        return

    event = NarrativeEventData(
        event_type=EventType(event_type),
        headline=headline,
        details=details,
    )

    generator = ContentGenerator()
    review = ReviewQueue()

    # Generate content for X (primary platform at launch)
    result = await generator.generate(
        agent=agent,
        event=event,
        tier=tier,
        angle=angle,
        platform="x",
    )

    # Store in database
    async with async_session() as session:
        post = ContentPost(
            agent=AgentName(agent_name),
            tier=ContentTier(tier),
            platform=Platform.X,
            content_text=result["content"],
            model_used=result["model"],
            prompt_tokens=result["input_tokens"],
            completion_tokens=result["output_tokens"],
        )

        # Run through review queue (auto-approves Tier 1, holds Tier 2-3)
        await review.submit(session, post)

        # If also generating for Studio (Tier 2+ gets full-length Studio posts)
        if tier >= 2:
            studio_result = await generator.generate(
                agent=agent,
                event=event,
                tier=tier,
                angle=angle,
                platform="studio",
            )
            studio_post = ContentPost(
                agent=AgentName(agent_name),
                tier=ContentTier(tier),
                platform=Platform.STUDIO,
                content_text=studio_result["content"],
                model_used=studio_result["model"],
                prompt_tokens=studio_result["input_tokens"],
                completion_tokens=studio_result["output_tokens"],
            )
            await review.submit(session, studio_post)
```

### Step 5.10 — Agent Registry

Create `src/agents/__init__.py` — a simple registry so any part of the code can get an agent by name:

```python
from src.agents.base import AgentPersonality
from src.agents.ray import ray

# Registry of active agents — add more as they launch
_AGENTS: dict[str, AgentPersonality] = {
    "ray": ray,
}


def get_agent(name: str) -> AgentPersonality | None:
    return _AGENTS.get(name)


def get_all_agents() -> list[AgentPersonality]:
    return list(_AGENTS.values())
```

When Danny launches in Phase 2, you add `from src.agents.danny import danny` and register him. Same pattern for Patricia, Carl, and Bianca.

### Step 5.11 — End-to-End Test

Write the integration test that proves the full pipeline works, in `tests/test_integration/test_pipeline.py`:

```python
import pytest
from unittest.mock import AsyncMock, patch

from src.engine.events import EventType, NarrativeEventData
from src.engine.interpreter import Interpreter
from src.engine.reactor import Reactor
from src.engine.scheduler import Scheduler
from src.agents.ray import ray


class TestFullPipeline:
    """Test the full data → interpretation → reaction → generation pipeline."""

    def test_interpreter_detects_spread_movement(self):
        interpreter = Interpreter()
        movements = [{
            "type": "spread_move",
            "book": "fanduel",
            "team": "Celtics",
            "old_line": -7.0,
            "new_line": -5.5,
            "home_team": "Celtics",
            "away_team": "Lakers",
            "event_id": "test-event-1",
        }]
        events = interpreter.interpret_line_movements(movements)
        assert len(events) >= 1
        assert events[0].event_type == EventType.REVERSE_LINE_MOVEMENT
        assert "ray" in events[0].relevant_agents

    def test_reactor_assigns_ray_to_line_movement(self):
        reactor = Reactor()
        events = [NarrativeEventData(
            event_type=EventType.REVERSE_LINE_MOVEMENT,
            headline="Celtics spread moved -7 to -5.5",
            significance=0.7,
            relevant_agents=["ray", "danny", "carl"],
        )]
        reactions = reactor.assign_reactions(events)
        agent_names = [r.agent for r in reactions]
        assert "ray" in agent_names  # Ray should always react to RLM

    def test_scheduler_staggers_posts(self):
        scheduler = Scheduler()
        from src.engine.reactor import AgentReaction
        reactions = [
            AgentReaction(agent="ray", tier=1, angle="data_analysis",
                         narrative_event=NarrativeEventData(event_type=EventType.LINE_MOVEMENT, headline="test")),
            AgentReaction(agent="danny", tier=1, angle="degenerate_take",
                         narrative_event=NarrativeEventData(event_type=EventType.LINE_MOVEMENT, headline="test")),
        ]
        scheduled = scheduler.schedule(reactions)
        assert len(scheduled) == 2
        # Posts should be staggered
        assert scheduled[0].scheduled_at < scheduled[1].scheduled_at

    @pytest.mark.asyncio
    async def test_content_generator_produces_output(self):
        """Test that the generator produces content (requires ANTHROPIC_API_KEY or mock)."""
        from src.content.generator import ContentGenerator

        event = NarrativeEventData(
            event_type=EventType.REVERSE_LINE_MOVEMENT,
            headline="Lakers @ Celtics: spread moved from -7 to -5.5 at FanDuel — reverse line movement",
            details={"old_line": -7.0, "new_line": -5.5},
        )

        # Mock the Anthropic API for testing
        mock_response = AsyncMock()
        mock_response.content = [AsyncMock(text="Celtics -7 to -5.5. Sharp money on Lakers. Public doesn't see it yet. The line tells you everything.")]
        mock_response.usage = AsyncMock(input_tokens=500, output_tokens=30)

        with patch.object(ContentGenerator, "__init__", lambda self: None):
            generator = ContentGenerator()
            generator.client = AsyncMock()
            generator.client.messages.create = AsyncMock(return_value=mock_response)

            result = await generator.generate(
                agent=ray,
                event=event,
                tier=1,
                angle="data_analysis",
                platform="x",
            )

            assert "content" in result
            assert len(result["content"]) <= 280  # Tweet length
            assert result["input_tokens"] > 0
```

Run the tests:

```bash
docker compose exec app pytest tests/ -v
```

---

### Phase 5 Checklist

| # | Task | Status |
|---|------|--------|
| 5.1 | Event type definitions (EventType enum + NarrativeEventData) | ☐ |
| 5.2 | Interpretation engine (raw data → narrative events) | ☐ |
| 5.3 | Agent reaction engine (events → agent assignments) | ☐ |
| 5.4 | Post scheduler (staggered timing) | ☐ |
| 5.5 | Base agent personality class | ☐ |
| 5.6 | Ray "The Sharp" Castellano personality + system prompt | ☐ |
| 5.7 | Content generator (Anthropic Claude API integration) | ☐ |
| 5.8 | Content review queue (tier-based auto-approve/hold) | ☐ |
| 5.9 | Celery tasks wiring Layers 2 → 3 → 4 | ☐ |
| 5.10 | Agent registry | ☐ |
| 5.11 | Integration tests (full pipeline) | ☐ |

**Phase 5 time estimate: 2-3 days**
**Phase 5 cost: ~$1-5** (Anthropic API calls during testing — Haiku is $0.001/post)

**After Phase 5, you have a working engine:** sports data comes in → gets interpreted as narrative events → agents are assigned to react → Claude generates personality-driven content → content enters the review queue. The full pipeline runs end-to-end in simulation mode.

---

*Phase 6: Publishing & Distribution (Layer 8) — awaiting permission to proceed.*
