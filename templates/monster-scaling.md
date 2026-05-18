# Monster Scaling

Use this template when scaling Dragonbane creatures to a specific party tier
and difficulty target. Always consult the reference corpus for the base stat
block first; use the approximation rules at the bottom only if the creature
is not found there.

---

## Dragonbane Stat Block Format

Every creature in the Bestiary has this structure:

```
Movement: <value>
Damage Bonus: <STR bonus die, AGL bonus die, or —>
HP: <value>
Typical Armor: <name (armor value)>
WP: <willpower points>
Skills: <Skill Name value, ...>
Typical Weapons: <weapon (skill level, damage dice)>
Abilities: <ability list>
Special traits: <e.g., Nocturnal, Large, Non-Monster>
```

---

## Advancement Tier HP Multipliers

| Advancement | HP Multiplier | WP Multiplier | Note |
|---|---|---|---|
| Apprentice | ×0.75 | ×0.75 | Reduce if creatures feel overwhelming |
| Journeyman | ×1.0 | ×1.0 | Base stat block as-written |
| Veteran | ×1.25 | ×1.25 | Increase HP and add one Ability |
| Master | ×1.5 | ×1.5 | Increase HP, add two Abilities, +D4 to damage dice |

Round HP to nearest whole number. WP always rounds up.

---

## Difficulty Multipliers (stack with tier)

| Difficulty | Additional HP | Additional WP | Damage |
|---|---|---|---|
| Easy | ×0.75 | ×0.75 | Downgrade one damage die (D10→D8) |
| Standard | ×1.0 | ×1.0 | As-written |
| Hard | ×1.25 | ×1.0 | Upgrade one damage die (D8→D10) |
| Punishing | ×1.5 | ×1.25 | Upgrade one damage die + add Damage Bonus die |

**Combined multiplier** = Tier × Difficulty. Example: Veteran + Hard = 1.25 × 1.25 = 1.5625 → round to 1.6.

---

## Headcount Guidelines

The encounter budget (see `encounter-budget.md`) governs total pressure.
Use these headcounts as a starting point:

| Monster Role | Suggested Count |
|---|---|
| Solo boss (high HP, multiple abilities) | 1 |
| Elite (Veteran/Chieftain variant) | 1–2 |
| Standard warrior/fighter | Party size ÷ 2 (round up) |
| Grunt/scout | Party size × 1–2 |

Do not mix more than three distinct creature types in one encounter — it
complicates tactics and slows play.

---

## When to Swap Rather Than Rescale

Rescaling has limits. Swap to a different creature type when:

- HP exceeds 3× the party's average starting HP (creature becomes a slog).
- The creature's special traits (Nocturnal, Large, Venomous) are incompatible
  with the scene's environment.
- The adventure calls for a Punishing encounter but the only available
  creature has no meaningful abilities — swap to a creature with more tools.

Swap up: use the next-tier variant listed in the Bestiary (Scout → Warrior →
Chieftain) or a creature from a higher-threat category.

---

## Ability Guidelines by Tier

When adding Abilities for Veteran/Master tiers, prefer abilities the creature
already has access to in the Bestiary:

| Ability | Effect summary |
|---|---|
| Veteran | Re-roll one failed attack per round |
| Robust | +D6 HP per stack (can add multiple) |
| Defensive | +2 to armor value |
| Dual Wield | Two weapon attacks per round |
| Poisonous | Bite/sting inflicts poison on hit |
| Fearsome | Target must WIL roll or flee |
| Regeneration | Regain D6 HP per round |

---

## Approximation Rules (No Reference Stat Block)

If the creature is not in the reference corpus, construct a stat block using
these baselines for a Journeyman/Standard encounter:

| Size | HP | WP | Armor | Damage |
|---|---|---|---|---|
| Small (cat, goblin) | 6–10 | 6–8 | 0–1 | D6–D8 |
| Medium (human, wolf) | 10–16 | 8–12 | 1–3 | D8–D10 |
| Large (ogre, bear) | 16–24 | 10–16 | 2–4 | 2D6–2D8 |
| Huge (giant, dragon) | 24–40 | 14–20 | 3–6 | 2D8–2D12 |

Then apply tier and difficulty multipliers as above. Note the stat block as
an approximation in `encounters.md`.

---

## Scaling Notation

Always document scaling math inline in `encounters.md`:

```
**Goblin Scout** (Journeyman/Standard)
Base: HP 9, WP 8, Armor 1, Short sword D10
Tier ×1.0 / Difficulty ×1.0 → Final: HP 9, WP 8, Armor 1, Short sword D10
```

```
**Orc Warrior** (Veteran/Hard)
Base: HP 12, WP 9, Armor 2, Scimitar 2D6, Damage Bonus +D4
Tier ×1.25 → HP 15, WP 12 / Difficulty ×1.25 → HP 19, upgrade damage → 2D6+D6
Added Ability: Veteran
Final: HP 19, WP 12, Armor 2, Scimitar 2D6, Damage Bonus +D6, Ability: Veteran
```
