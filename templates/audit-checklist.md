# Audit Checklist

Run this audit after every complete draft. Output pass/fail per item with a
one-line fix for every failure. Write results into `gm-notes.md` under the
Audit section. Re-run after every revision until all items pass (or the GM
explicitly waives an item with a written note).

---

## Category A — NPC Motives

**A1. Every named NPC has a stated motive.**
Check `npcs.md`. Each entry must include what the NPC wants and why.
Fix: add a one-line motive to any NPC missing one.

**A2. NPC motives are consistent across scenes.**
An NPC who wants gold in Scene 1 should not inexplicably protect the party
for free in Scene 4 without a stated reason for the change.
Fix: add a beat that explains the shift, or align motives.

**A3. Antagonist motivation makes sense from the antagonist's point of view.**
The antagonist is not evil "because they are evil." Their logic must be
internally coherent even if the party disagrees with it.
Fix: rewrite the antagonist's goal section in `npcs.md`.

---

## Category B — Timeline

**B1. The adventure has a coherent timeline.**
Events that happen before the party arrives, during the adventure, and as a
result of party actions must not contradict each other in sequence.
Fix: draft a brief timeline in `gm-notes.md` and check each scene against it.

**B2. No scene requires an event that hasn't happened yet.**
A clue cannot point to a body that won't exist until Scene 6 if the clue
appears in Scene 2.
Fix: reorder, gate the clue, or adjust when the event occurs.

**B3. Time pressure (if present) is consistent.**
If the adventure has a deadline ("the ritual at midnight"), every scene's
approximate duration must fit within it.
Fix: adjust scene lengths or move the deadline.

---

## Category C — Clues & Resolution

**C1. Every clue traces to a resolution.**
Each piece of evidence, rumor, or revelation that the party can find must
connect to at least one scene where it is useful.
Fix: add a use for the orphaned clue, or cut the clue.

**C2. The climax is reachable without any single mandatory clue.**
The party must be able to reach and engage the climax through at least two
independent clue paths. No single clue should be a hard gate.
Fix: add a redundant path or make the blocking clue optional.

**C3. The stated goal from the opening is addressed in the climax.**
The thing the party was trying to do in the opening scene must pay off —
resolved, transformed, or deliberately subverted — by the end.
Fix: add a beat in the climax that explicitly addresses the opening goal.

---

## Category D — Reachability

**D1. Every spine scene is reachable from the previous one.**
There is no scene the party cannot access unless they fail a single roll with
no retry or alternate path.
Fix: add an alternate entry or remove the hard block.

**D2. Every sidetrack has a documented rejoin point.**
Each optional branch in the outline lists which spine scene it reconnects to
and how. A sidetrack cannot dead-end.
Fix: add a rejoin note to the sidetrack in `adventure.md`.

**D3. No scene requires a resource the party cannot have acquired.**
If a scene requires a key, password, or item, at least one prior scene must
make it obtainable.
Fix: add an acquisition opportunity or remove the requirement.

---

## Category E — Fail-Forward

**E1. Every scene has a documented fail-forward path.**
Check `gm-notes.md`. If the party fails the primary objective of a scene
(fails the roll, loses the fight, misses the clue), there is a described
path that keeps them moving forward — not stuck.
Fix: add a fail-forward beat to any scene missing one.

**E2. Combat defeat does not end the adventure.**
A total party defeat in any encounter must have a consequence other than
"game over." Capture, retreat, unexpected rescue, or revealed information
are all valid.
Fix: add a defeat consequence to the encounter entry in `encounters.md`.

---

## Category F — Spine Integrity

**F1. No spine scene can be permanently skipped.**
Each scene on the linear backbone must be reachable. Optional content can
be skipped; spine content cannot.
Fix: identify and reclassify the optional scene, or add a trigger mechanism.

**F2. Scenes advance in a logical dramatic order.**
Tension generally rises toward the climax. No scene feels like backtracking
without a narrative reason.
Fix: reorder scenes or add a bridging beat.

---

## Category G — Tone & Limits

**G1. No scene content crosses a Line.**
Check every scene, NPC entry, encounter, and handout against the Lines
recorded in the intake.
Fix: rewrite or cut the offending content.

**G2. Veiled content is handled off-screen.**
Any content on the Veils list must be narrated as happening without detail:
"this occurs" not "here is how it occurs."
Fix: revise the relevant passage to fade to black.

**G3. Tone is consistent with the intake dial.**
If the intake says "grim folk-horror," comic pratfall encounters are out of
place without a specific GM request.
Fix: adjust scene or NPC voice to match the stated tone.

---

## Audit output format

Write audit results to `gm-notes.md` using this structure:

```
## Audit — [Draft number or date]

### Category A — NPC Motives
A1: [PASS] ...
A2: [PASS] ...
A3: [FAIL] Antagonist's motive in Scene 3 contradicts stated goal. Fix: ...

### Category B — Timeline
...

[continue for all categories]

### Summary
Total items: 21
Pass: 19  Fail: 2  Waived: 0

Outstanding fixes required before this draft is complete:
- A3: ...
- D2: Sidetrack "old mill" has no documented rejoin point. Fix: ...
```
