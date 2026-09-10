# Black Clover portraits

Character data and portrait assets for **Black Clover: The Living Grimoire**, a Yumina roleplay scenario.

**56 characters registered · 56 base portraits and 19 character-form portraits available · 75 images total · 0 images missing.**

## Contents

| File | Contents |
|---|---|
| [GALLERY.md](GALLERY.md) | Browse all 75 available portraits by character group. |
| [roster.json](roster.json) | The 56 characters: stable keys, names, aliases, affiliations, glyphs, colors, personality and rapport notes, and story availability guidance. |
| [CHARACTERS.md](CHARACTERS.md) | Readable character list, exact image filenames, profile notes, and research links. |
| [manifest.json](manifest.json) | Image format contract, the 56 expected base files and their availability status, and the index of uploaded portraits. |
| [character-sources.json](character-sources.json) | Canon references used for the written character profiles. These are not portrait image provenance. |
| [generation.json](generation.json) | Generation prompts, image dimensions and hashes, and format conversion records for the AI-generated portraits. |

The roster covers the Black Bulls, Golden Dawn, other squad captains, Clover Kingdom allies, people of Hage, and selected rivals. It includes the six Heart Kingdom additions: Gadjah, Lolopechka, Floga, Smurik, Potrof, and Sarado.

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

## Character-form portraits

The scenario now shows some characters differently later: three reveals (Nero as Secre Swallowtail, Grey's true appearance, the Eye's "Licht" as Patry — Patry keeps his base portrait) and the post-timeskip look of the cast who trained in the Heart Kingdom. Each form has its own file at the root, same contract as the base portraits:

```text
<key>-<form>-favor.webp
```

The nineteen expected files, their conditions and their prompts are listed under `forms` in [manifest.json](manifest.json) and as completed entries in [generation.json](generation.json). Until a file exists the scenario shows the previous face (a missing `secre-timeskip` shows `secre-human`, a missing `secre-human` shows the bird), never initials.

| File | Character | Shown when |
|---|---|---|
| `secre-human-favor.webp` | Secre Swallowtail | The narrator files Nero \| form=human after the late elf-conflict revelation. |
| `grey-true-favor.webp` | Grey | The narrator files Grey \| form=true once her true appearance has been seen and understood. |
| `asta-timeskip-favor.webp` | Asta | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `noelle-timeskip-favor.webp` | Noelle Silva | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `mimosa-timeskip-favor.webp` | Mimosa Vermillion | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `leopold-timeskip-favor.webp` | Leopold Vermillion | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `luck-timeskip-favor.webp` | Luck Voltia | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `finral-timeskip-favor.webp` | Finral Roulacase | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `yuno-timeskip-favor.webp` | Yuno | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `klaus-timeskip-favor.webp` | Klaus Lunettes | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `magna-timeskip-favor.webp` | Magna Swing | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `zora-timeskip-favor.webp` | Zora Ideale | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `charmy-timeskip-favor.webp` | Charmy Pappitson | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `vanessa-timeskip-favor.webp` | Vanessa Enoteca | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `gauche-timeskip-favor.webp` | Gauche Adlai | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `gordon-timeskip-favor.webp` | Gordon Agrippa | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `henry-timeskip-favor.webp` | Henry Legolant | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `grey-timeskip-favor.webp` | Grey | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |
| `secre-timeskip-favor.webp` | Secre Swallowtail | The Heart Kingdom alliance front settles on canon (the six months of training); no narrator row is needed. |

## Adding images

1. Find the character's exact filename in [the manifest](manifest.json).
2. Add that WebP image to the root of `main`.
3. Set its `expectedPortraits` status to `available` and add an entry to `portraits` with key, character name, filename, raw URL, and the actual image's source or generation provenance.
4. Update the available/missing counts in the manifest and this README.
5. For a character-form image, do the same under `forms` in the manifest, and replace the `pending` status in its `generation.json` entry with the image's dimensions, hashes and conversion record.

The `portraits` array contains uploaded images only and currently contains 75 images. An `expectedUrl` is a planned path, not a claim that an image exists. Missing files return 404 and the scenario falls back to initials. No placeholder image files have been added.

## Scenario connection

The updated scenario already contains the matching character definitions and uses this base URL:

```js
const PORTRAIT_BASE_URI =
  "https://raw.githubusercontent.com/JMmmmm0908/black-clover-portraits/main/";
```

The scenario requests `<baseUrl><key>-favor.webp` directly. It does not fetch or import `roster.json` or `manifest.json` at runtime. Older scenario exports with an empty roster must be updated before these character images can be used. GitHub's CDN may briefly cache an older image or a missing response.

This repository stays public so those unauthenticated image requests can work. The full scenario export is distributed separately.

## Identity and story notes

- Nero's base card is the bird (`secre-favor.webp`). The scenario switches to `secre-human-favor.webp` once the narrator files her reveal, and to `secre-timeskip-favor.webp` after the training; see the character-form section above.
- Yuno's full-name alias does not make his ancestry public knowledge.
- **Licht (elf leader)** and Patry have different records. Plain "Licht" is deliberately not an alias for the historical elf.
- **Fana (Diamond Kingdom)** is the human character. Plain "Fana" is deliberately not an alias, to avoid confusing her with the separate elf.
- Story availability fields are narrative guidance, not an automatic timeline or an encounter unlock.

The profiles use the character-data structure of the supplied My Hero Academia scenario as a reference, with original Black Clover character prose. See [character-sources.json](character-sources.json) for canon references; rapport notes are authored roleplay guidance.

## September 2026 portrait update

Added the 19 registered alternate forms and six Heart Kingdom portraits following user review. Both Secre human portraits use the requested clean under-eye appearance. The 50 earlier images are unchanged; their separate accuracy audit identified further corrections, which are not included in this upload. All images are AI-generated fan art, not official anime artwork.
