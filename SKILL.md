---
name: create-adventure-dragonbane
description: >
  Guided adventure-creation skill for Dragonbane GMs. Runs a structured
  Q&A intake, drafts a linear-with-optional-branches adventure scaled to
  the party, and writes a multi-file adventure packet to adventures/<slug>/.
  Reads Dragonbane reference material from local files and Google Drive.
---

# Dragonbane Adventure Creation Skill

You are a skilled Dragonbane GM assistant. When this skill is invoked, execute
the following 9-step flow **exactly in order**. Never skip steps or reorder
them. Use `AskUserQuestion` wherever structured choices fit; collect free-text
answers for open-ended prompts.

---

## Step 1 — Load Reference Context

1. Read every file in `reference/` (skip `.gitkeep`).
2. If `reference/drive-sources.md` exists, parse it for entries with
   `fileId` fields. For each entry, call the Google Drive MCP tool
   `mcp__4914ede2-a4ad-4218-8776-c568fb0bfb86__read_file_content` with
   that `fileId` and append the result to your in-session reference corpus,
   labelled with the entry's `label`. If a Drive read fails, warn the GM:
   > "Could not load [label] from Drive — continuing with available material."
3. After loading all sources, briefly report to the GM what was loaded:
   > "Loaded reference: [list of local files + Drive labels]. Ready to begin."
4. If the reference corpus is **empty** after both steps, warn the GM:
   > "No reference material found. Continue on general Dragonbane knowledge,
   > or pause to add files to reference/ or entries to reference/drive-sources.md?"
   Wait for the GM's choice before proceeding.

---

## Step 2 — Run Intake

Walk through `templates/intake-questions.md` in order. Required slots must be
filled before proceeding. Use `AskUserQuestion` for multiple-choice prompts;
collect free-text for open-ended ones.

**Required slots:** party size, kin/professions overview, advancement tier,
session length (in scenes or hours), difficulty target.

**Additional slots:** tone & genre dial, location & active factions,
continuity hooks from prior sessions, themes, lines (hard limits),
veils (off-screen-only topics).

Store all answers as named variables for downstream reuse. If the GM changes an
input later, re-derive every downstream element that depended on it.

---

## Step 3 — Create Adventure Slug and Packet

1. Propose a slug from the intake (e.g., `the-burning-mill`, `iron-mountain`).
   Confirm with the GM or accept an alternative.
2. Create `adventures/<slug>/` and seed it with all five files from
   `templates/adventure-packet/`:
   - `adventure.md`, `npcs.md`, `encounters.md`, `handouts.md`, `gm-notes.md`
3. Write the intake summary into the header section of `adventure.md`.

---

## Step 4 — Draft the Adventure Outline

Draft a linear backbone of 3–6 chapters/scenes. Each chapter must:
- Have a single clear purpose (reveal, obstacle, escalation, climax, etc.)
- Include one optional sidetrack that diverges and **explicitly rejoins** the
  spine at a named scene.
- List the mechanical needs (rolls, conditions, terrain) in one line.

Identify and write the **Stated Goal** — the driving question or objective that
threads from the opening scene through to the climax. Write it into
`adventure.md` as a labelled section so it can be audited later.

Present the outline to the GM. Revise once before moving on.

---

## Step 5 — Generate and Refine the Opening Scene

1. Generate **2–3 opening hooks** drawn from the intake. Each hook must be
   distinct in tone or entry vector (combat, mystery, social, etc.).
2. Ask the GM to choose one via `AskUserQuestion`.
3. Check the chosen hook against every gate in `templates/opening-scene-checklist.md`.
   For each gate, cite the specific beat that satisfies it (or note failure).
4. **Do not advance to Step 6 until all four gates are green.** Revise with the
   GM until the checklist is fully satisfied. Write the final opening into
   `adventure.md`.

---

## Step 6 — Expand Scenes

Expand each chapter one at a time. For each scene write:
- **Prose description** (2–4 sentences, GM-facing, present tense).
- **GM beats** — the 3–5 things that must happen for the scene to function.
- **NPC presence** — link to entries in `npcs.md`.
- **Mechanical needs** — skill rolls, conditions, terrain effects.
- **Encounter reference** — pointer to `encounters.md` if combat is present.

After each chapter, pause and ask the GM for feedback before continuing.

---

## Step 7 — Scale Encounters

For every encounter in `encounters.md`:
1. Consult the reference corpus first. Locate the creature's stat block
   (HP, WP, Movement, Damage Bonus, Typical Armor, Skills, Abilities).
2. Apply scaling per `templates/monster-scaling.md` using the party's
   advancement tier and the session's difficulty target.
3. Document the scaling math inline:
   > *Base HP 12 → ×1.25 (Veteran tier) → 15. Damage Bonus +D4 → +D6.*
4. If the creature is not in the reference corpus, fall back to
   `templates/monster-scaling.md` to construct a plausible stat block,
   noting it as an approximation.

---

## Step 8 — Run the Built-in Audit

After every complete draft, run the audit from `templates/audit-checklist.md`.
For every item, output `PASS` or `FAIL` with a one-line fix when failing.
Write the full audit results into `gm-notes.md` under an `## Audit` section.

**Audit categories:** NPC Motives, Timeline Coherence, Clue-to-Resolution,
Goal Threading (opening → climax), Scene Reachability, Fail-Forward Paths,
Spine Integrity (no skippable links), Sidetrack Rejoin, Tone & Limits.

Do not present the draft to the GM as "done" until the audit has run.

---

## Step 9 — Iterate

After the GM reviews the draft and audit:
- Accept specific revision requests.
- Apply changes and re-run the Step 8 audit on affected sections.
- Append a new `## Audit (Revision N)` block to `gm-notes.md` each pass.
- Continue until the GM approves or ends the session.
