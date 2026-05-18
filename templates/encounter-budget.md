# Encounter Budget

Use this template to distribute resource pressure across the full session so
that the total difficulty matches the GM's chosen target. "Resources" in
Dragonbane are primarily Willpower Points (WP), Hit Points (HP), and
conditions (Scared, Exhausted, Injured, etc.).

---

## Step 1 — Establish session totals

Estimate the party's starting resources per player at each advancement level:

| Advancement | Avg WP per player | Avg HP per player |
|-------------|-------------------|-------------------|
| Starting | 12 | 12 |
| Novice | 14 | 14 |
| Experienced | 16 | 16 |
| Veteran | 18 | 18 |
| Legendary | 20 | 20 |

**Party total WP** = avg WP per player × party size
**Party total HP** = avg HP per player × party size

---

## Step 2 — Set the session drain target

The difficulty target determines what fraction of total resources the session
should consume across all encounters combined, assuming no long rests.

| Difficulty | WP drain target | HP drain target | Conditions expected |
|------------|-----------------|-----------------|---------------------|
| Easy | 30–40% | 10–20% | 0–1 per player |
| Standard | 50–65% | 25–40% | 1–2 per player |
| Deadly | 70–85% | 45–60% | 2–3 per player |

These are session totals. Individual encounters contribute their share of the
total drain.

---

## Step 3 — Allocate per encounter

Divide the session drain target across the encounter count. A standard
session has 1–2 combat encounters and 1–2 tension scenes (skill challenges,
chases, social confrontations) that cost WP.

Recommended allocation:

| Encounter type | WP share | HP share |
|----------------|----------|----------|
| Light skirmish | 5–10% of session WP | 2–5% of session HP |
| Standard combat | 15–20% of session WP | 8–15% of session HP |
| Boss / climax fight | 25–35% of session WP | 15–25% of session HP |
| Tension scene (non-combat) | 10–15% of session WP | 0–5% of session HP |

Sum all allocated encounters. Total must not exceed the session drain target
by more than 10%. If it does, reduce a non-climax encounter's allocation.

---

## Step 4 — Validate against monster-scaling.md

After scaling each encounter per `monster-scaling.md`, estimate its actual
resource cost:

- **WP cost estimate**: (monster Ferocity × 2) + (number of special ability
  uses × 2) per monster, divided by party size.
- **HP cost estimate**: (monster damage per round) × (estimated rounds) ×
  (hit chance ~50%) divided by party size.
- **Condition risk**: Ferocity 4+ monsters impose conditions; budget 1
  condition per player for every 2 high-Ferocity monsters.

Compare estimates to the per-encounter allocation from Step 3. Adjust
monster count, stats, or Ferocity if the estimate is more than 20% off.

---

## Step 5 — Rest and recovery

Account for any rest opportunities between encounters:

- **Short rest** (10 min, no threat): restores 1d6 WP per player.
- **Long rest** (night, safe): restores full WP and HP.
- **No rest**: resources carry over as-is.

If the GM plans a long rest mid-session, reset the resource pool at that
point and apply the drain target to each half independently.

---

## Budget record format

Write the session budget into `gm-notes.md` under the Pacing section:

```
## Session Resource Budget

Party: [size] × [advancement] = [total WP] WP / [total HP] HP
Difficulty: [Easy / Standard / Deadly]
WP drain target: [X–Y]%  ([absolute value] WP)
HP drain target: [X–Y]%  ([absolute value] HP)

| # | Encounter | Type | WP est. | HP est. | Conditions |
|---|-----------|------|---------|---------|------------|
| 1 | [name]    | skirmish | [X] | [X] | [X] |
| 2 | [name]    | standard | [X] | [X] | [X] |
| 3 | [name]    | boss     | [X] | [X] | [X] |

Total estimated drain: [X] WP ([Y]%) / [X] HP ([Y]%)
Within target: [yes / no — note adjustment if no]

Rest opportunities: [list scene after which rest occurs, if any]
```
