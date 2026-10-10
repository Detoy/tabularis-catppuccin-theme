# Catppuccin for Tabularis

[![Validate theme](https://github.com/Detoy/tabularis-catppuccin-theme/actions/workflows/validate.yml/badge.svg)](https://github.com/Detoy/tabularis-catppuccin-theme/actions/workflows/validate.yml)

Soothing pastel theme for [Tabularis](https://tabularis.dev), based on the
[Catppuccin](https://catppuccin.com) palette. One package, two variants:

- **Catppuccin Latte**: the light flavour. Warm off-white surfaces with mauve, green and peach accents.
- **Catppuccin Mocha**: the dark flavour. Deep blue-grey surfaces with soft pastel accents.

Both variants style the application chrome, the data grid's semantic colours (strings, numbers,
dates, `NULL`, keys, pending edits) and the Monaco SQL editor, including SQL token colours.
The package is declarative JSON only: no code runs.

| Variant | Mode | Background | Text | Accent |
| --- | --- | --- | --- | --- |
| Catppuccin Latte | light | `#eff1f5` (base) | `#4c4f69` (text) | `#802cee` (mauve, darkened) |
| Catppuccin Mocha | dark | `#1e1e2e` (base) | `#cdd6f4` (text) | `#cba6f7` (mauve) |

## Preview

> **Preview component render.** These images were rendered in a browser from the real Tabularis
> React components (SQL editor, table toolbar and data grid) with this package's theme files
> applied through the app's own theme resolver. The data is simulated and the rest of the app
> window (sidebar, tabs, modals) is not shown. They are not screenshots of the desktop app.

**Catppuccin Mocha**, preview component render:

![Catppuccin Mocha: preview component render of the SQL editor, toolbar and data grid](https://raw.githubusercontent.com/Detoy/tabularis-catppuccin-theme/main/docs/screenshots/preview-mocha.png)

**Catppuccin Latte**, preview component render:

![Catppuccin Latte: preview component render of the SQL editor, toolbar and data grid](https://raw.githubusercontent.com/Detoy/tabularis-catppuccin-theme/main/docs/screenshots/preview-latte.png)

### Screenshots of the full app coming soon

Screenshots of both variants in the full desktop app (SQL editor, data grid, sidebar and a modal)
will be added here.

## Installation

Requires Tabularis **0.26.0 or later**, the first release with installable theme packages.

1. Download `theme-universal.zip` from the
   [latest release](https://github.com/Detoy/tabularis-catppuccin-theme/releases/latest).
2. In Tabularis, open **Settings → Appearance → Manage themes → Local package** and pick the ZIP.
3. Preview the variants, then install the package.
4. Choose **Catppuccin Latte** or **Catppuccin Mocha** and apply it. Installing does not change
   your selected theme on its own. You can also assign Latte to the system light mode and Mocha
   to the system dark mode.

The ZIP is universal: the same file works on every operating system. Once the package is listed in
the Tabularis theme registry, you will also be able to install it from Appearance discovery.

## Colour adjustments for contrast

Tabularis' built-in themes meet WCAG 2.2 AA on the token pairs listed in the Contrast section of
its [DESIGN.md](https://github.com/TabularisDB/tabularis/blob/main/DESIGN.md). Several Catppuccin
colours fall short of that on their own background, so they were nudged (same hue, lower or higher
lightness) rather than ignored. Every other colour is the unmodified Catppuccin value.

**Mocha** needed one change:

| Used for | Catppuccin | This theme |
| --- | --- | --- |
| `NULL` values in the grid | overlay1 `#7f849c` | `#81869e` |

**Latte** is a light palette with bright accents, so more of them were darkened to reach at least 4.5:1 on `#eff1f5`
(3:1 for the focus ring and cursor, which are not text):

| Used for | Catppuccin | This theme |
| --- | --- | --- |
| Muted text | subtext0 `#6c6f85` | `#5f6276` |
| Accent text, SQL keywords | mauve `#8839ef` | `#802cee` |
| Index markers | mauve `#8839ef` | `#8737ef` |
| Secondary accent | pink `#ea76cb` | `#bf1d94` |
| Success, strings, new rows | green `#40a02b` | `#307820` |
| Warning, primary keys, modified cells | yellow `#df8e1d` | `#925d13` |
| Error, deleted rows, invalid tokens | red `#d20f39` | `#d00f38` |
| Info, foreign keys | sapphire `#209fb5` | `#177383` |
| Numbers, booleans | peach `#fe640b` | `#b74301` |
| Dates | teal `#179299` | `#12747a` |
| `NULL` values | overlay1 `#8c8fa1` | `#65687c` |
| SQL comments and delimiters | overlay2 `#7c7f93` | `#6a6d81` |
| SQL operators | sky `#04a5e5` | `#0375a3` |
| SQL built-in functions | blue `#1e66f5` | `#1862f5` |
| Quoted identifiers | flamingo `#dd7878` | `#cc3434` |
| Focus ring | lavender `#7287fd` | `#637afd` |
| Editor cursor | rosewater `#dc8a78` | `#d46e58` |

## Editing and validation

The package follows the Tabularis
[theme authoring guide](https://github.com/TabularisDB/tabularis/blob/main/packages/create-plugin/THEMES.md).
Edit `themes/light.json` (Latte) and `themes/dark.json` (Mocha), then validate and package
with Node.js 22. The bundled tool works offline and needs no install:

```sh
node tools/theme.mjs validate .
node tools/theme.mjs package . --output theme-universal.zip
```

Branch pushes and pull requests run the same checks in CI. Pushing a `v*` tag that matches the
`version` in `.tabularium` creates a draft GitHub release with `theme-universal.zip` and the
`.tabularium` manifest attached, ready for review and publishing.

The package ID (`catppuccin-theme`) and the variant IDs (`latte`, `mocha`) stay stable across
releases, so saved theme selections keep working after updates.

## Credits and licence

- Colour palette: [Catppuccin](https://github.com/catppuccin/palette), © 2021 Catppuccin,
  [MIT licence](https://github.com/catppuccin/palette/blob/main/LICENSE).
- This theme package: MIT licence, © 2026 Yug Patel. See [LICENSE.txt](LICENSE.txt), which also
  carries the Catppuccin copyright notice.
- `tools/theme.mjs` is the Tabularis theme tool, distributed under its own licences; see
  [tools/THIRD-PARTY-LICENSES.txt](tools/THIRD-PARTY-LICENSES.txt).

This is a community port and is not an official Catppuccin project.
