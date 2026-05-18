# Dragonbane Adventure Creation Skill

A Claude Code skill that guides a Dragonbane GM through designing a complete
session — from intake to a polished, audited adventure packet.

## Quick Start

```
/create-adventure-dragonbane
```

Claude will walk you through intake questions, draft an adventure outline,
generate a refined opening scene, expand each chapter, scale encounters to
your party, and run a built-in plot audit. Output lands in `adventures/<slug>/`.

## Adding Reference Material

The skill reads Dragonbane source material at startup from two places:

### Local files
Drop any Dragonbane PDFs, rule excerpts, or notes as text files into `reference/`.
The skill reads all of them automatically.

### Google Drive (recommended for large PDFs)
Edit `reference/drive-sources.md` and add entries for any Dragonbane PDFs on
your Drive. The skill fetches them at runtime — no extraction needed.

```yaml
- label: "Dragonbane Bestiary"
  fileId: "your-google-drive-file-id-here"

- label: "Dragonbane Core Rulebook"
  fileId: "another-file-id"
```

To find a file's ID: open the file in Google Drive, copy the URL, and grab the
string between `/d/` and `/view` — e.g., for
`https://drive.google.com/file/d/13gReV99zZfSB5hxXar4rJmfnPiFj9CHU/view`
the ID is `13gReV99zZfSB5hxXar4rJmfnPiFj9CHU`.

## Output Structure

Each session creates `adventures/<slug>/` with five files:

| File | Contents |
|---|---|
| `adventure.md` | Hook, scene-by-scene spine, climax, denouement |
| `npcs.md` | NPC roster with motives, secrets, voice notes |
| `encounters.md` | Statted encounters with scaling math |
| `handouts.md` | Player-facing text: rumors, letters, maps |
| `gm-notes.md` | Pacing tips, fail-forward paths, full audit results |

## Requirements

- Claude Code with Google Drive MCP enabled (for Drive integration)
- Dragonbane reference material in `reference/` or `reference/drive-sources.md`
