# Dragonbane Adventure-Creation Skill

A Claude Code skill that guides a Dragonbane GM through designing a complete
session-ready adventure packet.

## Quick start

1. **Add reference material** (optional but recommended)
   Drop Dragonbane source excerpts into `reference/` — monster stat blocks,
   rule passages, setting fragments. Plain text or Markdown. The skill reads
   everything in that folder before it starts.

2. **Invoke the skill**
   In a Claude Code session, type:
   ```
   /create-adventure-dragonbane
   ```
   or just say "create a Dragonbane adventure" or "design a new session".

3. **Answer the intake questions**
   The skill walks you through party details, session length, difficulty,
   tone, setting, and content limits (lines/veils). Answer what you know;
   skip what you don't.

4. **Pick an opening hook**
   The skill proposes 2–3 in-medias-res hooks. Choose one. It is refined
   against an explicit checklist before scene work begins.

5. **Review and iterate**
   The skill expands scenes, scales encounters, and runs a built-in audit
   after every draft. Give feedback; it revises and re-audits.

## Output

Each adventure is written to `adventures/<slug>/` containing:

| File | Contents |
|------|----------|
| `adventure.md` | Intake summary, outline, scene-by-scene descriptions |
| `npcs.md` | NPC roster with motives, secrets, voice notes |
| `encounters.md` | Statted encounters with scaling math and tactics |
| `handouts.md` | Player-facing text: rumors, letters, maps |
| `gm-notes.md` | Pacing notes, fail-forward paths, audit results |

## Reference material

Place any of the following in `reference/`:
- Monster stat blocks (HP, STR, AGL, INT, WIL, CHA, Ferocity, special abilities)
- Rule passages (conditions, travel, magic schools, skill challenge guidelines)
- Setting fragments (factions, locations, pantheon, calendar)

The skill cites reference files by name when it uses them, so you know
exactly where each mechanic came from.

## Templates

The `templates/` folder contains the structured guides the skill uses
internally. You can read and edit them:

- `intake-questions.md` — the full question list and how each answer is used
- `opening-scene-checklist.md` — the four-gate in-medias-res test
- `audit-checklist.md` — every plot/logic check run after each draft
- `monster-scaling.md` — how to scale monsters to party and difficulty
- `encounter-budget.md` — session-wide resource-pressure heuristics
