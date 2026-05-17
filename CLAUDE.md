# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

A Claude Code **skill** (`SKILL.md`) that helps a Dragonbane tabletop RPG game master design a session. When invoked, the skill runs a guided Q&A intake, drafts a multi-file adventure packet, scales encounters to the party, and runs a built-in plot/logic audit on every draft.

## Skill Invocation

The skill is triggered by a DM running `/create-adventure` (or equivalent) inside a Claude Code session pointed at this repo. There is no build step or test runner — the "executable" is `SKILL.md` itself, read by Claude at runtime.

## Verifying the Skill Works

End-to-end verification (no automated test suite — these are manual checks):

1. Invoke with `reference/` empty → skill must warn and offer to proceed with general Dragonbane knowledge or pause.
2. Add a monster stat block + rule excerpt to `reference/`, re-invoke → skill must read and cite those files.
3. Complete a full intake → `adventures/<slug>/` must be created with all five packet files seeded from templates.
4. Confirm three opening hooks are proposed, one is chosen, checklist is explicitly cited as green before scene work begins.
5. Generate a chapter → encounter must cite a `reference/` monster scaled per `templates/monster-scaling.md`.
6. After the draft, `gm-notes.md` must contain audit results including at least one detected issue + proposed fix.
7. Sanity: every spine scene is reachable, the opening's stated goal appears in the climax, each sidetrack documents its rejoin point.

## Architecture

### Skill flow (encoded in `SKILL.md`)

The skill executes a fixed nine-step pipeline:

1. **Load context** — reads all files in `reference/`.
2. **Run intake** — walks through `templates/intake-questions.md` (party, pacing, difficulty, tone, setting/continuity, themes/lines/veils).
3. **Create output folder** — `adventures/<slug>/` seeded from `templates/adventure-packet/`.
4. **Draft outline** — linear backbone of chapters, each with one optional sidetrack that rejoins the spine.
5. **Opening hook gate** — proposes 2–3 hooks; DM picks one; skill refines until `templates/opening-scene-checklist.md` is fully green. The pipeline does **not** advance past this gate until all four checks pass.
6. **Expand scenes** — chapter by chapter: prose, GM beats, NPC presence, mechanical needs.
7. **Scale encounters** — consults `reference/` first, falls back to `templates/monster-scaling.md` + `templates/encounter-budget.md`; every encounter records the scaling math.
8. **Run audit** — after every draft, applies `templates/audit-checklist.md`; results written to `gm-notes.md`.
9. **Iterate** — re-runs the audit on each redraft.

### Directory layout

```
SKILL.md                        # Skill entry point: frontmatter + full DM-flow instructions
reference/                      # DM-committed Dragonbane source material (core rules, bestiary, setting)
templates/
  intake-questions.md           # Ordered intake Q&A (each question notes its downstream use)
  opening-scene-checklist.md    # Four binary gates: action / stated goal / sensory detail / decision point
  audit-checklist.md            # Categorized pass/fail checks (motive, timeline, clues, reachability, etc.)
  monster-scaling.md            # Party advancement + count + difficulty → HP/Ferocity/damage adjustments
  encounter-budget.md           # Session-wide resource-pressure heuristics (WP/HP/conditions)
  adventure-packet/             # Output skeletons: adventure.md, npcs.md, encounters.md, handouts.md, gm-notes.md
adventures/                     # Generated output — one subfolder per session (<slug>/)
```

### Deferred / blocked work

- `templates/monster-scaling.md` and `templates/encounter-budget.md` are **blocked on bestiary ingestion**. Authoritative Dragonbane bestiary content must be committed to `reference/` before these templates are written. Do not draft them from general knowledge — fabricated numbers will produce broken encounters. The DM will ingest the bestiary in a separate session.

### Key design invariants

- **`reference/` drives mechanics.** Monster stats and rule excerpts committed here take precedence over the skill's general knowledge. If `reference/` is empty, the skill warns explicitly.
- **Opening hook is a hard gate.** The checklist in `templates/opening-scene-checklist.md` must pass before scene expansion begins — the skill must not skip or soft-pass this.
- **Audit on every draft.** `templates/audit-checklist.md` runs after the initial draft and after every revision; results always land in `gm-notes.md`, never silently discarded.
- **Linear backbone + bounded branching.** Each chapter has exactly one optional sidetrack; sidetracks must document their rejoin point back to the spine.
- **Scaling math is explicit.** Every statted encounter in `encounters.md` notes the party assumptions, threat level, and resource-cost calculation used.
