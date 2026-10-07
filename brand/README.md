# The Tinker Crow brand

## Concept: the collector-maker

Crows solve problems, make and use tools, and collect shiny things. The
studio does the same with crafts: learn a skill, then combine it with the
others in ways they weren't meant to go.

- **Headline:** "Crows collect shiny things. So do I."
- **Motto:** "Only limited by what I haven't tried yet." Set in the hand font.
- **Look:** whimsical, boho cottage, plant-loving, a little witchy. Moon
  phases, botanical line drawings, apothecary labels. Not hippie, not goth:
  detailed and made-by-hand.
- **Language:** mediums, the workbench, pieces, curiosities. Learning on the
  fly is part of the story, not something to hide.

## Mark

A line-drawn crow in profile (long beak, flat crown, long tail) in copper on a
forest rounded square. `logo-mark.svg` is the source of truth (also
`/favicon.svg`). 48-unit grid, stroke 2.2, copper `#e0a177` on forest
`#34463a`. The first sketch had a short beak and round body and read as a
quail; the beak and tail length are what make it a crow, so keep them.

A hand-made mark (a glass or metal crow, photographed or traced) would suit
the studio even better later.

## Palette: Apothecary

In code: `/css/tokens.css`. Change a color there and in this table together.

| Token     | Light     | Dark      | Use                                 |
|-----------|-----------|-----------|-------------------------------------|
| bg        | `#f4eee3` | `#1b221d` | page background (parchment / night) |
| card      | `#fbf7ef` | `#242d27` | cards, chips                        |
| ink       | `#2b2a26` | `#efe7d8` | body text                           |
| forest    | `#34463a` | `#c9d6bc` | headings, wordmark, filled badges   |
| muted     | `#5e5a50` | `#b5ad9c` | secondary text                      |
| accent    | `#97522b` | `#e0a177` | copper: links, emphasis, hand notes |
| sage      | `#7d8b6a` | `#8fa07a` | botanical line art, moon phases     |
| line      | `#dcd2bf` | `#36423a` | borders                             |
| on-forest | `#fbf7ef` | `#1b221d` | text on a forest fill               |

### Contrast (measured 2026-09-24, WCAG 2.x formula)

Against `bg`, light / dark: ink 12.44 / 13.22, forest 8.73 / 10.69,
muted 5.95 / 7.29, accent 5.11 / 7.37. Text on a forest fill: 9.43 / 10.69.
All pass AA for body text.

**Sage is 3.15 in light mode:** decoration and large display only, never body
text or anything that has to be read. Re-measure any new pairing.

## Type

- **Fraunces** (display): headings and the wordmark. Soft, slightly odd serif;
  the italic carries the emphasis.
- **Figtree** (body): clean, warm sans for reading.
- **Caveat** (hand): margin notes and the motto only. One line at a time;
  never body copy.

All three SIL OFL, self-hosted from `/fonts/`. See `fonts/README.md`.

## Files

| File | Where it goes |
|---|---|
| `/css/tokens.css` | Palette + fonts as CSS variables. The code copy of this guide |
| `logo-mark.svg` | Source mark, site favicon |
| `avatar-512.png` | GitHub org avatar (full-bleed; GitHub rounds the corners) |
| `github-social-preview.png` (1280×640) | Repo Settings → Social preview. Also copied into the `.github` repo as `profile/banner.png` so the org profile doesn't depend on the site being live; update both together |
| `github-profile-README.md` | Reference copy of the org profile; the live one is `.github/profile/README.md` |
| `/og-image.png` (1200×630) | Link previews for thetinkercrow.com |

The PNGs were rendered with Lora standing in for Fraunces. Re-render them once
the self-hosted fonts are in `fonts/`, and bump `?v=` on `og:image`.
