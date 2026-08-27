# Dark Matter Code for Zed

The Zed port of **Dark Matter Code**, following Zed's `v0.2.0` theme schema.

## Themes

All seven variants live in `themes/dark-matter-code.json`:

### Mars — warm, reddish dark
- Dark Matter Code Mars Medium — `#141414`
- Dark Matter Code Mars Soft — `#1c1c1c`
- Dark Matter Code Mars Hard — `#0c0c0c`

### Neptune — cool, blueish dark
- Dark Matter Code Neptune Medium — `#1A1B26`
- Dark Matter Code Neptune Soft — `#1F2031`
- Dark Matter Code Neptune Hard — `#16161E`

### Pluto — true black
- Dark Matter Code Pluto — `#000000`, OLED-friendly

Syntax colours are identical across every variant; only the UI chrome changes.

## Use it right now (no extension needed)

Drop the theme file into Zed's user themes directory:

```bash
cp themes/dark-matter-code.json ~/.config/zed/themes/dark-matter-code.json
```

Zed picks it up live. Open the theme selector (`cmd-k cmd-t`) and choose a variant.

## Install as a dev extension

1. In Zed, run `zed: install dev extension` from the command palette.
2. Select this `zed/` directory.
3. Pick a variant from the theme selector.

## Publishing to the Zed extension gallery

The extension lives in this `zed/` subdirectory of the main repository; Zed's
`extensions.toml` supports a `path` field, so no separate repository is needed.

1. Fork [`zed-industries/extensions`](https://github.com/zed-industries/extensions) and clone it:
   ```bash
   git clone https://github.com/<you>/extensions
   cd extensions
   git submodule init && git submodule update
   ```
2. Add this repository as a submodule (HTTPS, not SSH):
   ```bash
   git submodule add https://github.com/amiralibg/Dark-Matter-Code.git extensions/dark-matter-code-theme
   ```
3. Add an entry to `extensions.toml`:
   ```toml
   [dark-matter-code-theme]
   submodule = "extensions/dark-matter-code-theme"
   path = "zed"
   version = "0.0.8"
   ```
4. Run `pnpm sort-extensions`, commit, and open a PR.

For each release: bump `version` in `zed/extension.toml`, push, then update the
submodule pointer and the `version` in `extensions.toml` via a new PR.

> The extension id is `dark-matter-code-theme` because Zed requires theme
> extensions to carry `theme` in their id.
