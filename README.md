# black-clover-portraits

Portrait assets for a personal Yumina roleplay scenario, **Black Clover: The Second Grimoire**.

Images are fetched directly by the scenario over `raw.githubusercontent.com`, so this repo
must stay **public** — a private repo returns 404 to the unauthenticated request the app makes.

## Naming

One file per contact, at the repo root:

```
<roster-key>-favor.webp
```

`<roster-key>` is lowercase, digits and single hyphens only (`^[a-z0-9]+(?:-[a-z0-9]+)*$`),
and must match the contact's key in the scenario's roster. Examples:

```
asta-favor.webp
noelle-silva-favor.webp
yami-sukehiro-favor.webp
```

The scenario builds each URL as:

```
https://raw.githubusercontent.com/JMmmmm0908/black-clover-portraits/main/<roster-key>-favor.webp
```

## Format

- **WebP.** The extension is hardcoded in the scenario; a `.png` or `.jpg` will not be found.
- Square, and consistent across the set. The panels render them small and round-cropped.
- Keep files modest — they load over the network on every panel render.

## Adding a portrait

1. Name the file `<roster-key>-favor.webp` exactly as above.
2. Commit it to `main` at the repo root.
3. It appears in the scenario on next load. No build step, no scenario rebuild.

A contact with no matching file falls back to an initial glyph rather than breaking.
