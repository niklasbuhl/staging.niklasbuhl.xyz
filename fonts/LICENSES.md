# Fonts

Every face here is licensed under the SIL Open Font License 1.1. The full licence text travels with each family as `OFL-<Family>.txt` in this directory, as the OFL requires.

These are the site's three faces, adopted 2026-08-21. They are declared in [`fonts.css`](fonts.css), linked from [`app/src/app.html`](../../src/app.html), and mapped onto `--font-sans`, `--font-serif` and `--font-mono` in [`app/uno.config.ts`](../../uno.config.ts). [`/dev/fonts`](../../src/routes/dev/fonts/+page.svelte) is their specimen and loads nothing of its own.

They are served from this origin: nothing is fetched from `fonts.googleapis.com` or `fonts.gstatic.com` at runtime, so there is no third-party request and no CDN privacy leak.

Three faces, 508 KB of woff2 across six files, fetched 2026-08-21. No page pays all of it. A browser downloads a `@font-face` file only when something on the page is set in it, so an ordinary route pulls 236 KB (Space Grotesk, Ioskeley Regular and Bold), a prose route 311–390 KB as Piazzolla joins, and only `/dev/fonts` reaches 495 KB because it sets every face deliberately.

## Display

- **Space Grotesk** — Florian Karsten. Variable, `wght` 300–700, one file, 48 KB. Full charset (latin, latin-ext, vietnamese). OFL-1.1.
  - Source: <https://github.com/floriankarsten/space-grotesk> (`fonts/woff2/SpaceGrotesk[wght].woff2`, release 2.0.0)
  - Renamed to `SpaceGrotesk-Variable.woff2`; the upstream `[wght]` brackets need URL-encoding in `url()` and are not worth the trouble.

## Paragraph

- **Piazzolla** — Huerta Tipográfica / HT Fonts. Variable, `opsz` 8–30, `wght` 100–900, roman + true italic. 75 + 79 KB. Version 2.005. OFL-1.1.
  - Source: <https://github.com/huertatipografica/piazzolla>, release `v2.005`, asset `Piazzolla.zip`, `variable/ttf/`.
  - Picked 2026-08-21 out of a field of eleven; see the [2026-08-21 journal](../../../docs/progress/journal/2026-08-21-font-bakeoff.md) for the field and the argument. Set on `.prose` and nowhere else, so routes without long-form copy never fetch it.
  - Cut to the `latin` subset locally with `pyftsubset` (fontTools 4.63.0), `--flavor=woff2 --layout-features='*' --name-IDs='*' --notdef-outline --recalc-bounds`, against the same `unicode-range` the bake-off's Google-sourced contenders carried. The zip ships `variable/woff2/` too; the TTFs were taken so every file in the field was cut the same way and the byte counts compared like with like.
  - Subsetting preserves both axes: the woff2 still reports `wght` 100–900 and `opsz` 8–30.
  - HT Fonts is an independent collective that owns and releases its own libre families. That, rather than shape, is why the field was widened past the Adobe and Google-commissioned faces at all.

## Code

- **Ioskeley Mono** — Ahmed Hatem. An Iosevka-built free interpretation of Berkeley Mono; not affiliated with or endorsed by Berkeley Graphics. Static faces, no variable build. OFL-1.1.
  - Source: <https://github.com/ahatem/IoskeleyMono>, release `v2.1.0`, asset `IoskeleyMono-Web.zip` (the 4 MB web subset: Latin, punctuation, arrows, box drawing — not `-Web-Full`).
  - Three faces taken of the 40 shipped: Regular 400 (94 KB), Bold 700 (94 KB), Italic 400 (105 KB).
  - Normal width is `shape = 600` per 1000 UPM in the upstream `private-build-plans.toml`, i.e. an advance of exactly **0.6em** — the same ratio the site's ASCII borders, buttons and terminal derive their column maths from.

## Removed 2026-08-21

Ten paragraph contenders lived here during the bake-off and came out when Piazzolla was picked, along with their licences: Source Serif 4, Crimson Pro, Newsreader, Literata, Inter, Vollkorn, Libertinus Serif and Charis, plus the two system stacks, which were never files. That freed 1.2 MB.

Every one is re-fetchable from the sources recorded in the [2026-08-21 journal](../../../docs/progress/journal/2026-08-21-font-bakeoff.md), which is the reason they were deleted rather than kept: nothing here is lost, and a decided page has no reason to carry the faces that lost.
