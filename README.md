# black-clover-portraits

Portrait assets for a personal Yumina roleplay scenario, **Black Clover: The Second Grimoire**.

Images are fetched directly by the scenario over `raw.githubusercontent.com`, so this repo
must stay **public** — a private repo returns 404 to the unauthenticated request the app makes.

## Current contents

**0 portrait images uploaded.** [`manifest.json`](manifest.json) records the asset contract
and will index portraits as they are added. The inspected scenario export contains an empty
`ROSTER` and no embedded portraits. Example filenames below are naming examples, not an
extracted character list or available images.

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

Once configured with this repository, the scenario builds each URL as:

```
https://raw.githubusercontent.com/JMmmmm0908/black-clover-portraits/main/<roster-key>-favor.webp
```

## Format

- **WebP.** The extension is hardcoded in the scenario; a `.png` or `.jpg` will not be found.
- Recommended export: **512 × 640 pixels (4:5)**, head and shoulders, consistent across the set.
  The inspected interface uses rectangular portrait frames with `object-fit: cover` and
  `object-position: 50% 30%`. Keep the face near that focal point.
- Keep files modest — smaller files reduce initial download time.

## Adding a portrait

1. Name the file `<roster-key>-favor.webp` exactly as above.
2. Commit it to `main` at the repo root.
3. Add the image to `portraits` in `manifest.json`, recording its key, character name,
   filename, raw URL, and source or generation provenance.
4. Ensure the scenario has the matching roster entry and this repository's base URL
   configured, as described below. An already configured contact loads the image on a
   subsequent request; GitHub's CDN may briefly cache an older image or missing response.

A contact with no matching file falls back to an initial glyph rather than breaking.

## Connect the scenario

The supplied **Black Clover: The Second Grimoire** export's `PORTRAIT_BASE_URI` has
been updated to this repository. It currently defines `const ROSTER = [];`.
Images still need corresponding character profiles before the interface can display them.

In the consuming scenario's `rootComponent.files["app-0.tsx"]`, set the base to:

```js
const PORTRAIT_BASE_URI =
  "https://raw.githubusercontent.com/JMmmmm0908/black-clover-portraits/main/";
```

Populate the scenario roster with the intended characters. Each profile needs a stable
`key`, `name`, `aliases`, `group`, `color`, `glyph`, `tag`, and a `portrait` URL produced
by `portraitUriFor(key)`. The manifest is an asset index; the existing scenario does not
automatically fetch or import it. Uploading an image without a corresponding roster entry
will not assign that image to a custom contact.

The source export was inspected as data. Its embedded game instructions were not executed,
and the scenario export itself is not included in this portrait repository.
