# SLOPSPORTS — Revenue & Cost Model v1.0

**Scope:** The podcast only. LeagueLore, MOONSHOT, and Studio are excluded from Year 1 and from this model.
**Posture:** Deliberately conservative. Every assumption is stated so it can be argued with.

---

## Headline finding, stated up front

**Break-even is realistic and reachable. The $20K/month Month-12 target from Business Plan v4.0 is not — not from this show alone, not in Year 1.**

Break-even needs roughly 40 paying subscribers *or* ~2,300 downloads per episode. That's an achievable Year-1 outcome.

$20K/month needs roughly 25,000 downloads/episode plus 70,000 YouTube views/episode plus 800 subscribers plus three paying sponsors. That is a top-few-percent sports podcast. It is a Year-3 number, not a Year-1 number.

This is not an argument against the show. It's an argument for **why the show exists**: it is a brand and audience engine whose real financial value is the products it makes possible later, not the ad reads it sells this year. Any plan that requires this podcast to produce $20K/month in Year 1 will be judged a failure by a standard it was never going to meet.

---

## 1. Cost structure

### Recurring monthly

| Item | Cost | Note |
|---|---|---|
| TTS / voice generation | $99 | Professional tier required — see §1.1 |
| Claude API (script assist) | $30 | Generous; prompt caching keeps this low |
| Podcast hosting + RSS | $19 | Transistor / Buzzsprout tier |
| Music & SFX licensing | $25 | Commercial-use library |
| Clip generation tool | $29 | Auto-caption + vertical reformat |
| Domain, landing page | $5 | Amortized; static host is free |
| NFL data | $0 | Free/public tiers in Year 1 |
| Buffer / misc | $30 | |
| **Total recurring** | **~$237/mo** | |

### One-time launch

| Item | Cost |
|---|---|
| Cover art + logo + character art | $300–800 |
| Theme music (custom or licensed) | $0–300 |
| Podcast setup, feed submissions, site | $0 (time only) |
| **Total one-time** | **$300–1,100** |

### Deliberately excluded from Year 1

Live2D rigging ($400–1,500), Discord moderation, custom voice cloning, legal review (**budget separately — $500–2,000 for a memo; still an open decision**), any paid marketing.

### 1.1 The TTS cost correction

Earlier planning assumed ~$22/month for voices. That's wrong.

- 23-minute episode ≈ 3,300–3,800 spoken words ≈ **~20,000 characters**
- 8.7 episodes/month ≈ **~175,000 characters of final audio**
- Real production regenerates lines. At a 2.5–3× multiplier: **~440,000–525,000 characters/month**

That lands in a professional tier at roughly **$99/month**. Still cheap in absolute terms, but a 4–5× correction to the earlier figure. Modeled at $99.

---

## 2. Time cost — the real constraint

Money is not the binding constraint on this product. Hours are.

| Task | Launch (hrs/ep) | Mature (hrs/ep) |
|---|---|---|
| Script — AI draft + human edit | 2.0 | 1.0 |
| Voice generation + regeneration | 1.5 | 0.75 |
| Edit & mix | 2.0 | 1.0 |
| Clip cutting (4–5 verticals) | 1.5 | 0.75 |
| Upload, metadata, posting | 1.0 | 0.5 |
| **Per episode** | **8.0** | **4.0** |
| **Per week (2 eps)** | **16** | **8** |

At 2×/week this is survivable alongside other work. **At 5×/week it would be 40 hrs/week at launch** — which is why the daily-cadence recommendation was wrong and was corrected.

**Kill metric:** if an episode still takes more than 5 hours all-in at Month 3, the pipeline has failed regardless of audience size.

---

## 3. Revenue streams and their honest timelines

| Stream | Earliest viable | Requires |
|---|---|---|
| Programmatic podcast ads | Month 1 | Nothing. Rates are terrible ($3–8 CPM) |
| YouTube Partner Program | Month 3–6 | 1,000 subs + 4,000 watch hours |
| Show Premium | Month 4 | An audience that would miss you |
| Direct host-read sponsorship | Month 6–9 | ~5,000+ downloads/ep to interest anyone |
| Sportsbook affiliate | **Blocked** | Legal review. Not modeled in Year 1 |

**Sportsbook affiliate revenue — the largest line item in Business Plan v4.0 — is excluded from this model entirely.** It's the highest-CPA category in sports media and it's also the one that carries jurisdictional gambling-regulation exposure. It stays out until there's a legal memo. If it clears, every number below improves materially.

---

## 4. Month-12 scenarios

Assumes 8.7 episodes/month, 2 ad slots per episode.

### Bear — the format works but doesn't spread

| Input | Value |
|---|---|
| Downloads/episode | 800 |
| YouTube views/episode | 1,500 |
| Premium subscribers | 15 |

| Revenue | Monthly |
|---|---|
| Podcast ads (13,920 imp @ $5 CPM) | $70 |
| YouTube (13,050 views @ $4 RPM) | $52 |
| Premium (15 × $6) | $90 |
| **Total revenue** | **$212** |
| Costs | ($237) |
| **Net** | **–$25/mo** |

**Read:** roughly break-even in cash, deeply negative in hours. This is the outcome where you've spent a year and ~700 hours to fund your own hosting bill. Day-90 kill criteria exist to catch this before Month 12.

### Base — it works

| Input | Value |
|---|---|
| Downloads/episode | 4,000 |
| YouTube views/episode | 8,000 |
| Premium subscribers | 80 |
| Sponsors | 1 @ $500/mo |

| Revenue | Monthly |
|---|---|
| Podcast ads (69,600 imp @ $12 blended CPM) | $835 |
| YouTube (69,600 views @ $4 RPM) | $278 |
| Premium (80 × $6) | $480 |
| Sponsorship | $500 |
| **Total revenue** | **$2,093** |
| Costs | ($237) |
| **Net** | **+$1,856/mo** |

**Read:** ~$22K/year net. Not a business yet. But it's a real audience, a proven format, and — critically — the asset that makes LeagueLore launchable in 2027 with a warm audience instead of a cold start. **This is the outcome to plan for.**

### Bull — it breaks out

| Input | Value |
|---|---|
| Downloads/episode | 15,000 |
| YouTube views/episode | 40,000 |
| Premium subscribers | 400 |
| Sponsors | 2 @ $1,500/mo |

| Revenue | Monthly |
|---|---|
| Podcast ads (261,000 imp @ $20 CPM) | $5,220 |
| YouTube (348,000 views @ $5 RPM) | $1,740 |
| Premium (400 × $6) | $2,400 |
| Sponsorships | $3,000 |
| **Total revenue** | **$12,360** |
| Costs | ($237) |
| **Net** | **+$12,123/mo** |

**Read:** ~$145K/year. A real job. Requires the show to become a genuine phenomenon in twelve months — realistically requires at least one breakout moment that can't be planned, only prepared for. Assign this maybe 10–15% probability.

---

## 5. Break-even

**Monthly nut: ~$237.**

Any one of these clears it:

- **40 Premium subscribers** at $6/mo — by far the easiest path
- **~2,300 downloads/episode** at a $12 blended CPM
- **60,000 YouTube views/month** (~6,900/episode)
- **One $250/mo sponsor**

Break-even is a genuinely modest bar. That's the good news in this model, and it's why the show is worth trying: **the downside is bounded at a few hundred dollars a month and your time.**

---

## 6. What $20K/month would actually require

Reverse-engineering v4.0's Month-12 target:

| Requirement | Value |
|---|---|
| Downloads/episode | ~25,000 |
| YouTube views/episode | ~70,000 |
| Premium subscribers | ~800 |
| Sponsors | 3 @ ~$2,000/mo |

That is a top-tier independent sports podcast. Achievable — but on a 24-to-36-month arc, with an audience compounding the whole way, and probably with sportsbook affiliate revenue unlocked.

**Recommendation: formally retire the $20K Month-12 target and replace it with the Base case (~$2,000/mo net) as the planning number.** Keeping an unreachable target is how a working product gets killed for underperforming.

---

## 7. Sensitivity — what actually moves the number

Ranked by leverage per unit of effort:

1. **Premium conversion rate.** At 4,000 downloads/ep, going from 1% to 3% conversion is +$480/mo — more than doubling ad revenue would deliver. **Premium is the highest-leverage lever in the model and it costs nothing to build.**
2. **Clip performance.** Every download comes from discovery, and discovery is clips. One clip at 2M views can move a quarter's numbers. This is the highest-variance input.
3. **Sponsorship rate.** Going from $500 to $1,500/mo per sponsor triples that line without a single additional listener. Depends entirely on audience quality, not size.
4. **Sportsbook affiliate unlock.** Excluded here, but at $100–300 CPA it could exceed every other line combined. Gated on legal.
5. **Episode cadence.** Doubling to 4×/week roughly doubles ad inventory — and doubles the hours. Worst ratio on the list. Do not pull this lever to fix revenue.

---

## 8. The honest strategic case

The podcast is unlikely to be a good standalone business in Year 1. What it plausibly produces:

- A **proven format** and a repeatable production pipeline
- An **audience** that makes the 2027 LeagueLore launch warm instead of cold
- A **brand** with cultural permission to do AI sports content, earned publicly
- **Optionality** on sponsorship, licensing, and formats that don't exist yet
- **Bounded downside** — roughly $237/month and your evenings

Judged as "a podcast that must earn $20K/month," this fails. Judged as "a ~$240/month bet that buys a format, an audience, and a brand," it's a good bet.

Pick which one you're judging it as **before launch**, not at Month 12.
