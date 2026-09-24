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
- **No location.** No town, region, or landmarks in copy. Every photo is
  exported with metadata stripped (GPS, camera serial, owner name) and shows
  nothing that identifies a house, street, or vehicle. Originals stay in the
  gitignored `photos-original/`; only stripped exports are committed.
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
- **Icon and preview URLs carry `?v=N`.** Bump it whenever one changes.
- Custom domain: `thetinkercrow.com` (the `CNAME` file). Enforce HTTPS in
  Pages settings once the certificate issues.

## Git workflow

Defined in the parent `CLAUDE.md`; not restated here.

- Currently on **`release/v0`**: the coming-soon page. `release/v1` is the
  full site (mediums, pieces, workbench journal, commissions).
- GitHub Pages deploys from `main`, so merging to `main` *is* publishing.

## Brand

Visual identity lives in [`brand/README.md`](brand/README.md): the Apothecary
palette with measured contrast, Fraunces / Figtree / Caveat, the crow mark.
Change colors there and in `css/tokens.css` together.

- Whimsical, boho cottage, plant-loving, a little witchy. Detailed and
  made-by-hand, not hippie, not goth.
- No invented numbers, testimonials, or press. Don't show pieces that don't
  exist; use a placeholder until there's a real photo.

## Known gaps

- **Fonts not added yet.** The page renders with fallbacks until the four
  `.woff2` files are in `fonts/` (see `fonts/README.md`).
- **Initial commit carries a personal author name and email.** It was made on
  github.com before the studio identity existed. Rewrite it (single commit,
  nothing depends on it) before the site goes public.
- Set organization membership to private (org → People) so the org page
  doesn't list a personal account.
- Social images (`og-image.png`, `brand/github-social-preview.png`,
  `brand/avatar-512.png`) use Lora as a stand-in for Fraunces; re-render once
  the fonts are in. No `favicon.ico` or `apple-touch-icon.png` yet.
- Contact / commission form not built; needs a form service that doesn't
  expose the destination address.
- Protect `main` in repo Settings → Rules: require a PR, no direct pushes.
