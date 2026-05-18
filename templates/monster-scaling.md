# Monster Scaling

Use this template to adjust Dragonbane monster stat blocks to fit the party's
advancement and the session's difficulty target. Always consult `reference/`
first for the base stat block. If no reference entry exists, use general
knowledge and note "general knowledge — no reference file."

---

## Step 1 — Determine the base threat bracket

Match the party's advancement level to a threat bracket:

| Advancement | Starting | Novice | Experienced | Veteran | Legendary |
|-------------|----------|--------|-------------|---------|-----------|
| Threat bracket | 1 | 2 | 3 | 4 | 5 |

This bracket is the baseline. Most monsters in `reference/` are written
for bracket 2–3. Adjust accordingly.

---

## Step 2 — Apply difficulty modifier

| Difficulty | HP modifier | Damage modifier | Ferocity modifier |
|------------|-------------|-----------------|-------------------|
| Easy | ×0.75 | ×0.75 | −1 (min 1) |
| Standard | ×1.0 | ×1.0 | no change |
| Deadly | ×1.5 | ×1.25 | +1 |

Round HP to nearest 2. Round damage to nearest die step.
Ferocity minimum is 1; maximum is 5.

---

## Step 3 — Scale for party size

Dragonbane's default encounter assumes approximately 4 players.

| Party size | Adjustment |
|------------|------------|
| 2 players | Reduce monster count by 1, or reduce HP by 25% |
| 3 players | No change |
| 4 players | No change |
| 5 players | Add 1 additional monster of the same type, OR increase HP by 20% |
| 6+ players | Add 1–2 additional monsters, or use a named/elite version |

Do not combine HP increase and monster count increase — pick one.

---

## Step 4 — Choose between rescaling and swapping

Rescaling (adjusting stats of the existing monster) works when the bracket
gap is 1. For gaps of 2 or more, consider swapping the monster type:

- Downgrade: Replace the monster with a lesser version of the same type
  (e.g., Troll → Cave Troll, Dragon → Wyvern).
- Upgrade: Replace with a greater version or a named variant
  (e.g., Wolf → Dire Wolf → Werewolf).

Swapping preserves encounter feel better than extreme stat inflation.

---

## Step 5 — Ferocity and special abilities

Ferocity drives how aggressively the monster uses special abilities.
At Ferocity 1–2: the monster uses abilities only when cornered.
At Ferocity 3: default — abilities used opportunistically.
At Ferocity 4–5: abilities used immediately and repeatedly.

When scaling Ferocity up, also increase how often special abilities
trigger (once per round → every other round → every round).

When scaling Ferocity down, have the monster hesitate, flee earlier,
or only use abilities after taking damage.

---

## Scaling record format

Every entry in `encounters.md` must include:

```
## Encounter: [Name]

**Base monster:** [Monster name]
**Source:** [reference/filename.md | general knowledge]

**Scaling inputs:**
- Party: [size] × [advancement bracket]
- Difficulty: [Easy / Standard / Deadly]
- Base stats: HP [X], STR [X], AGL [X], Ferocity [X], Damage [Xd6+Y]

**Adjustments applied:**
- Difficulty modifier: HP ×[Z] → [final HP]
- Damage modifier: [base] → [final]
- Ferocity modifier: [base] → [final]
- Party size adjustment: [description]
- Swap applied: [yes/no — describe if yes]

**Final stat block:**
HP: [X]  STR: [X]  AGL: [X]  INT: [X]  WIL: [X]  CHA: [X]
Ferocity: [X]  Movement: [X]  Armor: [X]
Damage: [weapon/attack — Xd6+Y]
Special: [ability name — description]

**Expected resource cost:** [see encounter-budget.md]
**Tactics:** [how this monster behaves in combat]
**Defeat consequence:** [what happens if the party loses]
```
