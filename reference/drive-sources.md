# Google Drive Reference Sources

The skill reads these files from Google Drive at startup and merges their
content with any local files in this directory.

Add entries for any Dragonbane PDFs you have on Drive. The skill uses the
`label` for reporting and the `fileId` to fetch the content.

```yaml
- label: "Dragonbane Bestiary"
  fileId: "13gReV99zZfSB5hxXar4rJmfnPiFj9CHU"
```

## How to find a file ID

Open the file in Google Drive and look at the URL:
`https://drive.google.com/file/d/<FILE_ID>/view`

Copy the `<FILE_ID>` portion and paste it as the `fileId` value above.

## Adding more sources

```yaml
- label: "Dragonbane Core Rulebook"
  fileId: "your-rulebook-file-id-here"

- label: "Dragonbane Roleplaying Game (boxed set)"
  fileId: "your-boxed-set-file-id-here"
```

Only add files you own or have permission to read. The skill reads each
source in order and stops gracefully if a file cannot be accessed.
