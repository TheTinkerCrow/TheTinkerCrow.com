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

## The studio and its maker

Until 14 Nov 2026 the studio was deliberately kept apart from the maker's
name, other sites and old accounts. That separation is lifted: the maker is
happy to be named and linked. Decided 14 Nov.

- **The maker's name may appear** in pages, metadata and `LICENSE`. The
  copyright holder is still "The Tinker Crow" until a page says otherwise.
- **Links out are fine**: other sites (salesforcegirl.org included), social
  accounts, and work posted elsewhere before.
- **Contact** can be a published email address or a form; neither is required.
- **Commit identity** may be the studio's or the maker's own. The repo-local
  identity is still `The Tinker Crow <hello@thetinkercrow.com>`; change it in
  the repo config rather than per commit.
- **Earlier work can be reused**, including photos and listings that were
  posted under old accounts.
- **Never name the town**, and never show the outside of the current home.
  That is about physical safety, not separation, and it stays.
- **Places in photos are fine**, and so are the maker's vehicles and tattoos.
  Keep out readable licence plates and anything identifying the people a
  piece was made for (names, initials, dates): those belong to other people.
- **People are welcome in photographs** — the site is a portfolio, and shoots
  like the ranch day are the work. Ask the people in them before posting
  (a parent for anyone under 18), and never name them in copy, alt text,
  slugs or captions. Decided 13 Nov.
- **Every photo ships with all metadata stripped.** Location, camera serial
  and editing details don't belong on a public page. Exports are re-encoded
  with no EXIF/XMP and only the stock sRGB profile. Before committing, read
  each file's JPEG segments: only JFIF, the sRGB ICC profile and the image
  tables before the scan data, with no APP1 (EXIF/XMP) or APP13 (Photoshop).
  macOS ImageIO writes both of those even when asked for none, so strip them
  after exporting. A byte search for `Exif`, `Canon` or `Lightroom` can also
  match by chance inside the compressed image data; check where a hit sits
  before rejecting the file. Originals never enter this repo.

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
  the picture, grouped by prefix, never the camera filename. Photographs use
  what's in them (`candle-`, `lantern-`, `light-`, `rust-`, `workshop-`,
  `lock-`, `flower-`, `garden-`, `glass-`, `bench-`, `place-`, `car-`, `cat-`,
  `dog-`, and `ranch-` for the ranch shoot); handmade pieces use their
  material (`glasswork-`, `metal-`, `leather-`, `string-`, `beads-`,
  `paint-`), and work in progress uses `process-`.
- **`gallery.html`** has two parts. "Made by hand" opens with "On the bench"
  (pieces in progress, choosing materials, layouts) and then groups finished
  pieces by material; it draws only on the edited craft set. "Photographs"
  opens with shoots (a nine-photo preview of the ranch, linking to the full
  shoot on `ranch.html`) and then groups by color, following the color folders
  in the photo library. At most six per group (nine on the bench and the
  ranch) and two shots of any one piece. Swatch colors live in `tokens.css`.
  Photo files that drop out of the gallery stay in `photos/`; the home page
  shows nine and links to it.
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

- Contact / commission form not built; needs a form service that doesn't
  expose the destination address.
- No branch protection on `main`. A "require a pull request" rule would block
  the local merges above; only add one that the studio account can bypass.
