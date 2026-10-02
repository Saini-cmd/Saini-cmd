# assets/ — SVG banners and libraries

## Purpose
- Self-contained SVGs rendered in the GitHub profile `README.md` through GitHub's camo proxy and SVG sanitizer.

## Ownership
- `banner.svg` — hand-kept canonical boilerplate reference.
- `glyphs.svg` — generated glyph library + reference sheet (`../tools/glyphs.py`).
- `icons.svg` — generated icon library + reference sheet (`../tools/icons.py`).
- `icons/<slug>.svg` — imported pixel-art snippets (`../tools/convert.py`); each is self-contained with a local exact palette and a copyable `<g id="i-<slug>">`.
- `<name>.svg` / `<name>-<theme>.svg` / `<name>.snippet.html` — generated banners (`../tools/build.py` from `../banners/*.json`).
- `sword.svg`, `bottle.svg` — standalone 4× sprites (`crispEdges`); `sword` uses the shared icon tokens, `bottle` carries its own local `--bottle-*` palette from `q.txt`.
- `badge-test.svg` — GitHub render test comparing raw data-URI vs normalized shields.io logos.
- Banners with a `badges` block (e.g. `tech-stack.svg`) inline normalized shields.io badges and carry `data-allow-raw-hex` (third-party fills, not tokens).
- Design spec lives one level up in `../data.md`; theme presets in `../themes/`.

## Local Contracts
- Generated files are build output: edit the source (`../tools/*.py`, `../banners/*.json`, `../themes/*.json`), never the SVG.
- One file, everything inline: no external assets, `<script>`, `<foreignObject>`, `@font-face`, or `@import`.
- Colors go through `--pf-*` token classes; no raw `#hex` outside token/style blocks.
- `id` values unique; glyphs 5×7 (20×28px), advance 24px, corners chamfered one cell.
- Filenames contain no spaces; README references depend on these exact paths.

## Work Guidance
- Add a banner by adding `../banners/*.json` and running `python3 tools/build.py`.
- Icons are placed inline by the engine (`icons` / `tiles[].icon`); reference sheets use `<use>`.

## Verification
- `python3 tools/build.py && python3 tools/check.py`.

## Child DOX Index
- `icons/AGENTS.md` — imported pixel-art icon snippets with local exact palettes.
