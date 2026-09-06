# Black Clover portraits

Character data and portrait assets for **Black Clover: The Second Grimoire**, a Yumina roleplay scenario.

**50 characters registered · 50 portrait images uploaded · 0 images missing.**

## Contents

| File | Contents |
|---|---|
| [GALLERY.md](GALLERY.md) | Browse all 50 available portraits by character group. |
| [roster.json](roster.json) | The 50 characters: stable keys, names, aliases, affiliations, glyphs, colors, personality and rapport notes, and story availability guidance. |
| [CHARACTERS.md](CHARACTERS.md) | Readable character list, exact image filenames, profile notes, and research links. |
| [manifest.json](manifest.json) | Image format contract, the 50 expected files and their availability status, and the index of uploaded portraits. |
| [character-sources.json](character-sources.json) | Canon references used for the written character profiles. These are not portrait image provenance. |
| [generation.json](generation.json) | Generation prompts, image dimensions and hashes, and format conversion records for the AI-generated portraits. |

The roster covers the Black Bulls, Golden Dawn, other squad captains, Clover Kingdom allies, people of Hage, and selected rivals. It matches the 50-character scenario update, which adds 150 trust, respect, and attachment fields while retaining the black, antique gold, parchment, and crimson interface.

The scenario reveals contacts in Bonds after an established encounter. Roster membership and default scores do not imply a meeting. Custom contacts remain supported.

## Portrait filenames

Place one WebP file per character at the repository root. Use the exact key from the roster:

```text
<key>-favor.webp
```

Examples from this roster:

```text
asta-favor.webp
noelle-favor.webp
yami-favor.webp
secre-favor.webp
licht-favor.webp
fana-favor.webp
```

The keys are stable identifiers; filenames are not automatically derived from the full display name. For example, Noelle Silva uses `noelle-favor.webp`, and Nero uses `secre-favor.webp`.

Recommended image format is **512 × 640 WebP (4:5)**, with the face around the upper center. The interface uses `object-fit: cover` and `object-position: 50% 30%`.

The portraits retain their generated resolution (approximately 4:5). They use a shared charcoal, gold, and crimson atmosphere with parchment lighting. Exact prompts, corrections, dimensions and hashes are recorded in [generation.json](generation.json).

## Adding images

1. Find the character's exact filename in [the manifest](manifest.json).
2. Add that WebP image to the root of `main`.
3. Set its `expectedPortraits` status to `available` and add an entry to `portraits` with key, character name, filename, raw URL, and the actual image's source or generation provenance.
4. Update the available/missing counts in the manifest and this README.

The `portraits` array contains uploaded images only and currently contains 50 images. An `expectedUrl` is a planned path, not a claim that an image exists. Missing files return 404 and the scenario falls back to initials. No placeholder image files have been added.

## Scenario connection

The updated scenario already contains the matching character definitions and uses this base URL:

```js
const PORTRAIT_BASE_URI =
  "https://raw.githubusercontent.com/JMmmmm0908/black-clover-portraits/main/";
```

The scenario requests `<baseUrl><key>-favor.webp` directly. It does not fetch or import `roster.json` or `manifest.json` at runtime. Older scenario exports with an empty roster must be updated before these character images can be used. GitHub's CDN may briefly cache an older image or a missing response.

This repository stays public so those unauthenticated image requests can work. The full scenario export is distributed separately.

## Identity and story notes

- Nero's public card remains bird-focused. Use Nero's bird form for `secre-favor.webp` in the opening-era scenario; the single static path does not switch forms automatically. The Secre alias is for identity continuity; later identity and magic are described only in conditional lore.
- Yuno's full-name alias does not make his ancestry public knowledge.
- **Licht (elf leader)** and Patry have different records. Plain "Licht" is deliberately not an alias for the historical elf.
- **Fana (Diamond Kingdom)** is the human character. Plain "Fana" is deliberately not an alias, to avoid confusing her with the separate elf.
- Story availability fields are narrative guidance, not an automatic timeline or an encounter unlock.

The profiles use the character-data structure of the supplied My Hero Academia scenario as a reference, with original Black Clover character prose. See [character-sources.json](character-sources.json) for canon references; rapport notes are authored roleplay guidance.
