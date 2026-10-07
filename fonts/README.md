# Fonts

Self-hosted so the site makes no third-party requests. `css/tokens.css`
expects these four files here; until they exist, the fallback stacks render.

| File | Source (Google Fonts, SIL OFL 1.1) |
|---|---|
| `Fraunces.woff2` | Fraunces, variable, upright |
| `Fraunces-Italic.woff2` | Fraunces, variable, italic |
| `Figtree.woff2` | Figtree, variable |
| `Caveat.woff2` | Caveat, variable |

Plus each family's licence as `OFL-Fraunces.txt`, `OFL-Figtree.txt`,
`OFL-Caveat.txt` (the `OFL.txt` inside each download, renamed).

## Getting them

Google Fonts downloads are TTF zips, not woff2. Unzip into `fonts/src/`
(gitignored), then convert the variable TTFs to Latin-only woff2:

```sh
pip install fonttools brotli
pyftsubset "src/Fraunces-VariableFont_SOFT,WONK,opsz,wght.ttf" \
  --flavor=woff2 --layout-features='*' \
  --unicodes="U+0000-00FF,U+0131,U+0152-0153,U+02BB-02BC,U+02C6,U+02DA,U+02DC,U+2000-206F,U+20AC,U+2122,U+2191,U+2193,U+2212,U+2215,U+FEFF,U+FFFD" \
  --output-file=Fraunces.woff2
```

Same command for the italic and the other two families. `--layout-features='*'`
keeps every OpenType feature; Caveat's handwritten look relies on its
contextual alternates, which a default subset can drop.
