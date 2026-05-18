---
name: create-adventure-dragonbane
description: >
  Guided adventure-creation skill for Dragonbane GMs. Runs a structured
  intake, drafts a linear-with-optional-branches adventure scaled to the
  party, enforces an in-medias-res opening, and audits every draft for
  plot/logic holes. Output is a multi-file adventure packet under
  adventures/<slug>/.
triggers:
  - "create adventure"
  - "new adventure"
  - "design session"
  - "dragonbane adventure"
---

# Dragonbane Adventure-Creation Skill

## Invocation

When this skill is triggered, execute the nine-step flow below in order.
Do not skip or reorder steps. Do not advance past a gated step until the
gate is explicitly green.

---

## Step 1 — Load context

1. Read every file in `reference/`.
2. If `reference/` is empty or contains only `.gitkeep`, warn the GM:

   > **No reference material found.** For best results, add Dragonbane
   > source excerpts (bestiary entries, rule passages) to `reference/`
   > before continuing. Do you want to (A) pause and add files now, or
   > (B) continue using general Dragonbane knowledge?

   Wait for the GM's choice. If (A), stop. If (B), note in the packet
   that reference/ was empty and all mechanics are from general knowledge.

3. Index what was loaded: list monster names, rule topics, and setting
   fragments found. Keep this index in working memory for Steps 6–8.

---

## Step 2 — Run intake

Walk the GM through `templates/intake-questions.md` group by group.
Use `AskUserQuestion` for structured choices (party size, difficulty,
tone). Collect free-text answers for setting, hooks, and limits.

Required slots (must be filled before proceeding):
- Party size, kin/professions, advancement level
- Session length / target scene count
- Difficulty target (Easy / Standard / Deadly)

Additional slots (prompt for each; accept "skip" for any):
- Tone & genre dial
- Location, active factions, continuity hooks from prior sessions
- Themes the GM wants present
- Lines (hard limits — never appear) and veils (fade to black)

Record all answers. Store them as "intake" in working memory; every
downstream step must re-derive from these answers if the GM changes one.

---

## Step 3 — Slug and packet scaffold

1. Derive a short slug from the adventure's working title or setting
   (e.g., `iron-crown-ruins`, `the-pale-ferry`). Ask the GM to confirm
   or replace it.
2. Create `adventures/<slug>/` and copy the five packet skeletons from
   `templates/adventure-packet/` into it:
   - `adventure.md`
   - `npcs.md`
   - `encounters.md`
   - `handouts.md`
   - `gm-notes.md`
3. Write the confirmed intake answers into the header block of
   `adventures/<slug>/adventure.md`.

---

## Step 4 — Draft the adventure outline

Produce a linear backbone of chapters/scenes. Requirements:

- Every chapter has a clear entry trigger and exit condition.
- Each chapter may have 0–2 optional sidetracks; each sidetrack must
  document its rejoin point on the spine.
- Identify the **Stated Goal** — the thing the party is trying to
  accomplish — and confirm it threads from the opening scene through to
  the climax.
- Write the outline into the Outline section of `adventure.md`.

Present the outline to the GM. Incorporate feedback before moving on.

---

## Step 5 — Opening scene (gated)

**This step has a hard gate. Do not proceed to Step 6 until the gate is green.**

1. Generate 2–3 distinct opening hook options, each a single evocative
   paragraph. Each must be derived from the intake.
2. Ask the GM to pick one (or describe a variant).
3. Evaluate the chosen hook against every item in
   `templates/opening-scene-checklist.md`. For each item, output:
   - **[PASS]** — cite the specific beat that satisfies it, or
   - **[FAIL]** — describe what is missing and propose a fix.
4. Revise the opening until all items show **[PASS]**.
5. Confirm the gate is green, then write the final opening into the
   Opening Scene section of `adventure.md`.

---

## Step 6 — Expand scenes

Work through the outline chapter by chapter. For each scene produce:

- **Prose description** (read-aloud or paraphrase, 2–4 sentences)
- **GM beats** — what must happen for the scene to progress
- **NPC presence** — who is here, their immediate goal, their secret
- **Mechanical needs** — rolls called for, conditions possible, terrain
  features, relevant rules passages (cite `reference/` if available)
- **Encounter reference** — if combat is possible, note the encounter ID
  from `encounters.md`

Write scene content into `adventure.md` (scenes) and `npcs.md` (NPC
entries).

---

## Step 7 — Scale encounters

For every encounter referenced in Step 6:

1. Consult `reference/` for monster stat blocks first.
2. Apply `templates/monster-scaling.md` to adjust for party size,
   advancement, and difficulty target.
3. Apply `templates/encounter-budget.md` to confirm the encounter's
   resource cost fits within the session's total budget.
4. Write the statted encounter into `encounters.md`, including:
   - Base stat block source (reference file or general knowledge)
   - Scaling math: party assumptions, threat level, adjustments made
   - Expected resource cost (WP/HP/conditions)
   - Tactics and failure modes

---

## Step 8 — Run the audit

After the full draft is written, evaluate it against every item in
`templates/audit-checklist.md`. Output per item:

- **[PASS]** with a one-line citation, or
- **[FAIL]** with a one-line diagnosis and a proposed fix.

Write the full audit results into `gm-notes.md` under the Audit section.

If any item fails, fix it in the relevant packet file and re-run the
audit. Repeat until all items pass (or the GM explicitly waives a
specific item with a note in `gm-notes.md`).

---

## Step 9 — Iterate

Present the completed packet to the GM with a summary:
- Scene count, encounter count, NPC count
- Audit status (all pass / items waived)
- Any warnings (empty reference, skipped intake slots)

For each round of GM feedback:
1. Make the requested changes to the relevant packet files.
2. Re-run the audit (Step 8) on the changed sections.
3. Report the updated audit status.

Continue until the GM indicates the adventure is ready.
