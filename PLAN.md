# Plan: Dragonbane Adventure-Creation Skill

## Context

This repo (`SKILL-of-Create-Adventure-Dragonbane-`) is currently empty. The
goal is to build a Claude Code skill that helps a Dragonbane DM design a
session: it runs a guided Q&A intake, drafts a linear-with-optional-branches
adventure scaled to the party, leans on committed Dragonbane source material
for mechanics (especially monster scaling), enforces a strong in-medias-res
opening, and runs a built-in plot/logic audit on every draft. Output is a
multi-file adventure packet per session.

User decisions captured:
- Interaction: **Guided Q&A, step-by-step** (intake → outline → scenes → audit).
- Output: **Multi-file adventure packet** under `adventures/<slug>/`.
- Source material: **Committed in the repo** under `reference/`.
- Consistency: **Built-in audit pass each draft.**
- Intake inputs: party size/level, session length, difficulty (defaults) **plus** tone & genre dial, location/factions/continuity hooks, and themes + content limits (lines/veils).
- Linearity: **Linear backbone + 1–2 optional sidetracks per chapter** that rejoin the spine.
- Opening scene: **Skill proposes 2–3 hooks, DM picks, skill refines** against an in-medias-res checklist (action, stated goal, sensory detail, decision point).

## Repo structure

```
SKILL.md                              # The skill entry point (frontmatter + DM-flow instructions)
README.md                             # How a DM uses the skill (short)

reference/                            # Dragonbane source material the DM commits
  README.md                           # What to drop here (core rules excerpts, bestiary, setting)
  .gitkeep

templates/
  intake-questions.md                 # Structured intake the skill must walk through
  opening-scene-checklist.md          # In-medias-res / goal / sensory / decision-point gate
  audit-checklist.md                  # Plot & logic hole audit applied to every draft
  monster-scaling.md                  # How to scale Dragonbane monsters to party/difficulty
  encounter-budget.md                 # Difficulty-to-resource-pressure heuristics
  adventure-packet/                   # Skeletons for the multi-file output
    adventure.md                      # Hook, scene-by-scene spine + sidetracks, climax, denouement
    npcs.md                           # NPC roster with motives, secrets, voice notes
    encounters.md                     # Statted encounters w/ scaling notes & tactics
    handouts.md                       # Player-facing text: rumors, letters, maps
    gm-notes.md                       # Pacing notes, fail-forward paths, contingencies, audit results

adventures/                           # Output destination (one folder per session)
  README.md                           # Explains the per-adventure layout
  .gitkeep
```

## Skill behavior (encoded in `SKILL.md`)

The skill, when invoked, MUST execute the following flow:

1. **Load context.** Read everything in `reference/`. If empty, warn the DM and ask whether to continue with general Dragonbane knowledge or pause to add files.
2. **Run intake** using `templates/intake-questions.md`. Required slots: party (size, kin/professions, advancement), session length / scene count, difficulty target. Additional slots: tone & genre dial, location/factions/continuity hooks, themes + lines/veils. Use `AskUserQuestion` where it fits; collect free-text notes for the rest.
3. **Choose a slug and create `adventures/<slug>/`** containing the five packet files seeded from `templates/adventure-packet/`.
4. **Draft the adventure outline** as a linear backbone of chapters/scenes, each with one optional sidetrack that rejoins the spine. Surface the stated goal that will thread from opening to climax.
5. **Generate 2–3 opening hooks** from intake. DM picks one. Refine until it passes every box in `templates/opening-scene-checklist.md` — do not advance past this step until the gate is green.
6. **Expand scenes one chapter at a time.** For each scene: prose description, GM beats, NPC presence, mechanical needs (rolls, conditions, terrain), encounter references.
7. **Scale encounters** by consulting `reference/` first, falling back to `templates/monster-scaling.md` and `templates/encounter-budget.md`. Every statted encounter notes the scaling math used (party assumptions, threat level, expected resource cost).
8. **Run the built-in audit** after every draft using `templates/audit-checklist.md`: NPC motives consistent, timeline coherent, clues traceable to resolution, opening goal still threaded into the climax, every scene reachable, every failure has a fail-forward path, no skippable spine links, sidetracks always rejoin. Audit results land in `gm-notes.md`.
9. **Iterate per the DM's feedback,** re-running the audit on each redraft.

## Key template contents

- **`templates/intake-questions.md`** — ordered question list grouped: Party, Pacing, Difficulty, Tone, Setting/Continuity, Themes & Limits. Each question notes how the answer is used downstream (so the skill can re-derive if the DM changes an input).
- **`templates/opening-scene-checklist.md`** — four binary gates plus phrasing guidance. The skill cites which box each opening beat satisfies.
- **`templates/audit-checklist.md`** — categorized checks (Motive, Timeline, Clue-to-resolution, Reachability, Fail-forward, Spine integrity, Sidetrack rejoin, Tone/limits adherence). Skill outputs a pass/fail per item with a one-line fix when failing.
- **`templates/monster-scaling.md`** — translates party advancement + count + difficulty target into HP/Ferocity/damage adjustments and "how many" guidance, plus when to swap monster types rather than rescale.
- **`templates/encounter-budget.md`** — resource-pressure heuristic across a session (WP/HP/conditions burned vs. expected) so encounters total to the chosen difficulty.

## Deferred work

- **Bestiary ingestion comes first.** Before `templates/monster-scaling.md` and `templates/encounter-budget.md` can be written, authoritative Dragonbane bestiary content must land in `reference/`. The DM will ingest the bestiary in a separate session. Until then, these two templates are **not** to be drafted from general knowledge — fabricated HP/Ferocity/damage numbers would silently produce broken encounters. Implementation of Phase 2's two scaling templates is blocked on that ingestion. All other templates can proceed independently.

## Verification

End-to-end check the skill is usable:

1. Invoke the skill in a fresh Claude Code session with `reference/` empty — confirm it warns and offers to proceed.
2. Drop a small sample of Dragonbane reference material into `reference/` (monster stat block + one rule excerpt). Re-invoke and confirm the skill reads it.
3. Run a full intake answering every prompt; confirm `adventures/<slug>/` is created with all five files seeded.
4. Confirm three opening hooks are proposed, the chosen one is refined, and the checklist is explicitly cited as green before scene work begins.
5. Generate a chapter; confirm an encounter cites a `reference/` monster scaled per `monster-scaling.md`.
6. Confirm the audit runs after the draft and writes results into `gm-notes.md`, including at least one detected issue and a proposed fix on a deliberately broken input.
7. Quick sanity: every spine scene is reachable, the opening's stated goal appears in the climax, and each sidetrack documents how it rejoins.

## Files to create (all new — repo is empty)

- `SKILL.md`
- `README.md`
- `reference/README.md`, `reference/.gitkeep`
- `templates/intake-questions.md`
- `templates/opening-scene-checklist.md`
- `templates/audit-checklist.md`
- `templates/monster-scaling.md`
- `templates/encounter-budget.md`
- `templates/adventure-packet/adventure.md`
- `templates/adventure-packet/npcs.md`
- `templates/adventure-packet/encounters.md`
- `templates/adventure-packet/handouts.md`
- `templates/adventure-packet/gm-notes.md`
- `adventures/README.md`, `adventures/.gitkeep`

After files are created, commit and push to `claude/clarify-task-4HkMF`.
