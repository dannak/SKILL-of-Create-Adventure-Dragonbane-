# Encounter Budget

Use this template to ensure the session's total combat and hazard pressure
matches the chosen difficulty target. Budget is expressed in expected resource
drain: HP lost, WP spent, and conditions suffered across the full session.

---

## Dragonbane Resource Overview

| Resource | Recovered by | Notes |
|---|---|---|
| HP | Rest (stretch/shift/full) | Full recovery on a shift rest |
| WP (Willpower) | Rest, Push rolls | Spent on abilities, spell boosts |
| Conditions | Rest, specific actions | Exhausted, Frightened, Entangled, Poisoned, etc. |

Conditions are the most disruptive resource — prioritize draining them in key
encounters to create tension even if HP is healthy.

---

## Session Resource Budgets by Difficulty

These are *expected totals* across the whole session, not per encounter.

| Difficulty | HP drain (avg per PC) | WP drain (avg per PC) | Conditions inflicted |
|---|---|---|---|
| Easy | 0–25% of max | 0–25% of max | 0–1 per PC |
| Standard | 25–50% of max | 25–50% of max | 1–2 per PC |
| Hard | 50–75% of max | 50–75% of max | 2–3 per PC |
| Punishing | 75–100% of max | 75–100% of max | 3+ per PC |

Assume average starting HP ~14 and average starting WP ~10 for a Journeyman PC.

---

## Encounter Weight Classes

Assign each encounter a weight based on its expected drain:

| Weight | HP drain (party total) | WP drain (party total) | Typical use |
|---|---|---|---|
| Trivial | <10% session budget | <10% | Ambush, skirmish, speed bump |
| Minor | 10–20% | 10–20% | Sidetrack combat, patrol |
| Significant | 20–35% | 20–35% | Named-enemy encounter, set piece |
| Major | 35–50% | 35–50% | Chapter climax, boss |
| Session Climax | 50%+ | 50%+ | Final boss, only one per session |

---

## Building the Session Budget

1. List every encounter (combat + hazard) in spine order.
2. Assign a weight to each.
3. Sum the weights. Total should roughly equal 100% of the session budget.
4. Adjust monster count or scaling (via `monster-scaling.md`) until the sum lands.

**Standard session example (4 scenes, Standard difficulty):**

| Scene | Encounter | Weight |
|---|---|---|
| 1 | Goblin scouts (×3) | Minor (15%) |
| 2 | Trap + ambush | Trivial (8%) |
| 3 | Orc warband | Significant (30%) |
| 4 | Orc chieftain + 2 warriors | Session Climax (47%) |
| **Total** | | **100%** |

---

## Rest Availability

Rest opportunities affect perceived difficulty. Document planned rests:

| Rest type | HP/WP recovered | When available in this session |
|---|---|---|
| Stretch rest (~15 min) | D6 HP | After each non-climax scene if safe |
| Shift rest (~8 hours) | Full HP + D6 WP | Once per session (after Scene 2 if in a safe location) |
| Full rest (~24 hours) | Full HP + full WP | Not typically available in a single session |

Note in `gm-notes.md` where rest is available and what prevents it at the
climax (pursuers, ticking clock, hostile environment).

---

## Condition Budget Notes

Conditions are asymmetric — Frightened and Poisoned are more disabling than
Exhausted for most builds. When designing Hard or Punishing sessions:

- Reserve Frightened for significant/climax encounters (it drains WP to
  resist and reduces effectiveness).
- Use Poisoned to create a slow-burn drain across the session.
- Exhausted is a good "consequence of failure" condition for non-combat scenes.

Do not stack more than 2 conditions on the same PC simultaneously — it
creates frustration rather than tension.
