# Reference Material

The skill reads everything in this directory at startup to ground monster
scaling, lore accuracy, and setting details.

## What to add here

- Dragonbane core rules excerpts (combat, skills, conditions, advancement)
- Bestiary stat blocks
- Setting/world material (factions, geography, history)
- Any house rules or campaign-specific notes

Files can be plain text, Markdown, or PDF (if your Claude Code environment
can read them). The skill will use whatever it finds.

## Google Drive sources

For large PDFs (Rulebook, Bestiary, supplements), add entries to
`drive-sources.md` instead of committing the files directly. The skill
fetches Drive files at runtime using the Google Drive MCP integration.

See `drive-sources.md` for the format and pre-configured sources.

## What the skill does with this material

1. Loads all local files in this directory.
2. Reads any Drive sources listed in `drive-sources.md`.
3. Uses the merged corpus to:
   - Look up creature stat blocks for encounter scaling (Step 7).
   - Check setting/lore accuracy during scene drafting (Step 6).
   - Reference mechanical rules during the audit (Step 8).

If this directory is empty and no Drive sources are configured, the skill
warns and offers to continue on built-in Dragonbane knowledge.
