# TheTinkerCrow.com — studio site

Project rules for the public site. The parent `CLAUDE.md` (how we work)
still applies: branching, versioning, accessibility, git.

## This repo is public

Everything committed here, including history and commit metadata, is visible
to anyone.

- No keys, tokens, or credentials. A form service's public site key is fine;
  anything marked secret is not.
- No internal notes, drafts, or anything not yet announced.
- A mistake in history is public even after it's deleted. Check before pushing.

## The studio stands on its own

The Tinker Crow is deliberately **not linked** to any other site, account, or
name the maker uses. This is a hard rule, not a style preference.

- **No personal names** in pages, metadata, `LICENSE`, or commits. The
  copyright holder is "The Tinker Crow".
- **Commit identity for this repo is the studio's**, not a personal one: a
  repo-local `user.name` of `The Tinker Crow` and a studio email that is not
  attached to any personal GitHub account (a personal `noreply` address
  contains that account's username). Check `git log --format='%an <%ae>'`
  before every push.
- **No links out** to other sites or social accounts, and no "as seen on".
  Contact happens through a form, never a published email address.
- **No location.** No town, region, or landmarks in copy or photos: no
  house exteriors, streets, trails, signage, or vehicles. Pets and interiors
  are fine.
- **Every photo ships with all metadata stripped.** The originals carry the
  camera body serial number, which ties every photo from that camera
  together. Exports are re-encoded with no EXIF/XMP and only the stock sRGB
  profile. Before committing, read each file's JPEG segments: only JFIF, the
  sRGB ICC profile and the image tables before the scan data, with no APP1
  (EXIF/XMP) or APP13 (Photoshop). macOS ImageIO writes both of those even
  when asked for none, so strip them after exporting. A byte search for `Exif`,
  `Canon` or `Lightroom` can also match by chance inside the compressed image
  data; check where a hit sits before rejecting the file. Originals never
  enter this repo.
- **Nothing reused** from earlier shops or accounts: no old product photos,
  listings, or copy that a reverse image or text search could match.

## How it's built

- Plain static HTML/CSS served by **GitHub Pages** from `main`. No build step
  until there's a reason for one.
- **Styles live in `css/`, not in the HTML.** `css/tokens.css` holds the fonts
  and palette as CSS variables and is the one place colors are defined;
  `css/site.css` uses only `var(--…)`, never hex values.
- **No third-party requests.** Fonts are self-hosted (never Google Fonts), no
  CDNs, no analytics, no embeds. See `fonts/README.md`.
- **Strings are inline in the HTML.** The parent file's string-catalogue rule
  is for apps; this is a small English brochure site with no app behind it.
  Revisit if it ever grows a shop or a second language.
- **Photos:** `photos/<slug>.jpg` at 2000px on the long edge (quality 80,
  progressive) and `photos/thumbs/<slug>.jpg` at 640px. Slugs name what's in
  the picture, grouped by prefix (`candle-`, `lantern-`, `light-`, `rust-`,
  `workshop-`, `lock-`, `flower-`, `garden-`, `glass-`, `bench-`, `cat-`,
  `dog-`), never the camera filename.
- **`gallery.html`** holds every photo, grouped by theme; the home page shows
  a sample of nine and links to it.
- **Icon and preview URLs carry `?v=N`.** Bump it whenever one changes.
- Custom domain: `thetinkercrow.com` (the `CNAME` file), HTTPS enforced.

## Git workflow

Defined in the parent `CLAUDE.md`; not restated here.

- GitHub Pages deploys from `main`, so merging to `main` *is* publishing.
- **Merge locally with `--no-ff`, never with GitHub's merge button.** The
  button authors the merge commit as whoever is signed in to github.com, not
  as the studio.

## Brand

Visual identity lives in [`brand/README.md`](brand/README.md): the Apothecary
palette with measured contrast, Fraunces / Figtree / Caveat, the crow mark.
Change colors there and in `css/tokens.css` together.

- Whimsical, boho cottage, plant-loving, a little witchy. Detailed and
  made-by-hand, not hippie, not goth.
- No invented numbers, testimonials, or press. Don't show pieces that don't
  exist; use a placeholder until there's a real photo.

## Known gaps

- Set organization membership to private (org → People) so the org page
  doesn't list a personal account.
- No `favicon.ico` or `apple-touch-icon.png` yet.
- Contact / commission form not built; needs a form service that doesn't
  expose the destination address.
- No branch protection on `main`. A "require a pull request" rule would block
  the local merges above; only add one that the studio account can bypass.
