# SLOPSPORTS — Voice Reference v1.0

**Purpose:** Drive stock-voice selection and TTS parameter tuning. This document is the spec you audition against.
**Constraint:** Stock voices only for Gate 2. No custom cloning until format is proven.

---

## Why this document exists

Voice quality is the single largest failure risk in this product. A listener decides in the first 30 seconds whether they're hearing a show or a text-to-speech demo. Everything in the show bible and the pilot script is worthless if the audio doesn't clear that bar.

Three AI voices holding a 23-minute conversation is a **harder** TTS problem than a single narrator, because:
- Interruptions and overlaps must sound intentional, not glitchy
- Three voices must be distinguishable at low volume in a car
- Emotional range has to vary within a single take
- Sustained listening exposes artifacts that a 30-second sample hides

**Test this before writing another document.**

---

## CHALK — voice spec

| Attribute | Target |
|---|---|
| **Perceived age** | 35–45 |
| **Register** | Mid-to-low, narrow pitch range |
| **Pace** | Measured, ~140 wpm, very consistent |
| **Warmth** | Low. Not hostile — *uninterested in warmth* |
| **Dynamic range** | Narrow by design. CHALK never shouts |
| **Distinguishing feature** | Precision. Consonants land. No trailing off |

**Reference feel:** a research analyst reading findings to a room he assumes is smarter than it is. Think financial-earnings-call cadence with better comic timing.

**What kills it:** any hint of "friendly assistant" warmth. If the voice sounds like a customer-service bot, it's wrong. CHALK's flatness must read as *character*, not as *TTS limitation* — this is the hardest casting problem on the show, because a flat synthetic voice and a flat character are easy to confuse.

**Mitigation if flatness reads as artifact:** give CHALK slightly more pitch variance than the character strictly wants, and let the *writing* carry the coldness. Better a warm voice saying cold things than a robotic voice saying cold things.

**TTS settings starting point:** stability high (0.6–0.75), similarity high, style exaggeration low (0.0–0.2), speed 0.95–1.0.

---

## DOG — voice spec

| Attribute | Target |
|---|---|
| **Perceived age** | 30–40 |
| **Register** | Mid-to-high, wide pitch range |
| **Pace** | Fast, ~180–200 wpm, variable |
| **Warmth** | High. Likable even when wrong |
| **Dynamic range** | Wide. Escalates hard and drops fast |
| **Distinguishing feature** | Momentum. Sentences pile up |

**Reference feel:** the guy at the bar who is definitely going to finish his point. Sports-radio caller energy, but articulate. Must be *charming*, not annoying — this is the difference between the show working and the show being unlistenable.

**What kills it:** if DOG reads as dumb rather than credulous, the whole character collapses into a punching bag and the debate stops being a debate. DOG must sound like someone you'd actually enjoy arguing with.

**The hard part:** DOG needs real dynamic range and interruption energy. Most stock TTS voices flatten under emotional load. Audition specifically on the escalation lines from Ep 001 Hot Read Topic 2, not on neutral copy.

**TTS settings starting point:** stability lower (0.35–0.5) for expressiveness, style exaggeration moderate (0.3–0.5), speed 1.05–1.1.

---

## BOOTH — voice spec

| Attribute | Target |
|---|---|
| **Perceived age** | 40–55 |
| **Register** | Low, even, resonant |
| **Pace** | Deliberate, ~150 wpm |
| **Warmth** | Medium. Dry, not cold |
| **Dynamic range** | Narrow but expressive through timing, not volume |
| **Distinguishing feature** | Authority. The voice that ends arguments |

**Reference feel:** a broadcast producer who has done ten thousand of these and finds exactly one thing per episode genuinely funny. Every laugh BOOTH gets comes from timing, not from delivery.

**What kills it:** if BOOTH sounds like a narrator rather than a participant, the audience won't bond with it — and BOOTH is the designated emotional anchor (the Vedal role). It must sound like someone *in the room*, tired of both of them.

**Critical:** BOOTH must be maximally distinct from CHALK. Both are low-warmth and measured. If they're confusable in a car at low volume, recast one. **Consider making BOOTH a different perceived gender from both hosts** — the cheapest possible separation, and it also fixes an all-same-sounding-voices problem the show would otherwise have.

**TTS settings starting point:** stability high (0.65–0.8), style low, speed 0.95.

---

## Casting requirements across the trio

1. **Three-way distinguishability at low volume.** Test in a car or on phone speaker, not headphones.
2. **No two voices in the same perceived age bracket.**
3. **Strongly consider gender diversity across the three** — helps separation, and the show should not be three men by default.
4. **All three must survive 20+ minutes** without listener fatigue. Audition on long-form, not on 30-second reads.

---

## Audition protocol (Gate 2, Step 1)

**Do this before anything else in Gate 2.**

1. Pick 4 stock candidates per role (12 total).
2. Generate **the full "Help Me Understand" segment** from Ep 001 with each combination you're seriously considering — this is ~5 minutes and contains silence, escalation, vulnerability, and dry comedy. It is the hardest passage in the script and the best audition material.
3. Listen in a car. Listen on a phone speaker. Listen at 1.25× (a large share of podcast listeners use it — check that speed-up doesn't destroy the timing).
4. **Benchmark against a real sports podcast segment.** Not against other TTS. Against the actual competition.
5. Score each combination:
   - Distinguishability (1–5)
   - Artifact frequency (1–5)
   - Emotional credibility on the DOG monologue (1–5)
   - Would you keep listening at minute 15 (yes/no — this one is a gate, not a score)

**Pass condition:** at least one combination where all three score ≥4 and the "keep listening" answer is yes.

**If nothing passes:** stop. Do not proceed to full pilot production. The options at that point are (a) custom voice cloning with real voice actors, which is a budget and licensing decision, (b) a different TTS vendor, or (c) the format doesn't work as pure-AI audio and needs a human voice in the mix. All three are real answers. Producing a pilot with voices that failed the audition is not.

---

## Cost note — this is a real finding, not a footnote

A 23-minute episode is roughly **3,300–3,800 spoken words ≈ 19,000–22,000 characters**.

At 2 episodes/week (~8.7/month) that's **~170,000–190,000 characters of final audio per month**.

Real production requires regenerating lines — bad takes, timing fixes, rewrites. Assume a **2.5–3× multiplier**: **~425,000–570,000 characters/month**.

That exceeds entry and mid tiers on most TTS platforms and lands squarely in a **~$99/month professional tier**, not the ~$22 tier assumed in earlier planning. Budget accordingly. This is still cheap in absolute terms — but it's a 4–5× correction to the earlier estimate and it should be in the model, not discovered in Month 2.

---

## Production notes for the mix

- **Interruptions must be edited, not generated.** Generate full lines, then overlap in the DAW. TTS cannot produce a natural interrupt.
- **Silence is content.** The 2-second pause in Ep 001's Help Me Understand is scripted. Protect it in the edit — the instinct to fill it is wrong.
- **Room tone under everything.** Dead-silent gaps are the loudest possible tell that audio is synthetic. A low bed of room tone is the single highest-leverage fix available.
- **Vary the gap lengths between lines.** Uniform spacing is the second-loudest tell.
- **Light compression, gentle EQ separation** between the three voices so they occupy different pockets.
