# pi-catppuccin

An unofficial [Catppuccin](https://github.com/catppuccin/catppuccin) theme package for [Pi](https://github.com/earendil-works/pi).

<!-- Screenshot: add an overview image from assets/ here after one is available. Capture a user message, successful and failed tools, mixed Markdown/code, and a visible thinking border. -->

## Install

```sh
pi install git:github.com/madeleineostoja/pi-catppuccin
```

For a temporary local check without changing settings:

```sh
pi -e /absolute/path/to/pi-catppuccin
```

Choose a flavour with `/settings`. Update the package with `pi update --extensions` (or `pi update --all`) and remove it with:

```sh
pi remove git:github.com/madeleineostoja/pi-catppuccin
```

| Theme | Notes |
| --- | --- |
| `catppuccin-latte` | Light flavour. <!-- Screenshot: add `assets/latte.png` when available. --> |
| `catppuccin-frappe` | Dark, muted flavour. <!-- Screenshot: add `assets/frappe.png` when available. --> |
| `catppuccin-macchiato` | The author's daily/default flavour. <!-- Screenshot: add `assets/macchiato.png` when available. --> |
| `catppuccin-mocha` | Deep dark flavour. <!-- Screenshot: add `assets/mocha.png` when available. --> |

Macchiato is a personal default, not a forced selection for package users.

## Design

Whiskers generates each file from Catppuccin's official palette. Mauve is the single accent in every flavour; this package intentionally ships four carefully curated themes instead of the full 56 flavour/accent combinations.

Surface and Overlay colors keep ordinary chrome quiet. Borders are deliberately muted rather than bright blue or cyan, leaving mauve and semantic colors to identify meaningful state. User messages and tool panels use a small, derived lightness lift above `base`; pending and successful tools are neutral, while failed tools receive a mild red tint that remains comfortable for expanded output.

The thinking border progresses monotonically from neutral Surface colors to the official mauve endpoint. Its intermediate base-to-mauve colors are intentional extrapolations, not named Catppuccin swatches. Latte also applies small lightness reductions to accent colors used as text and promotes secondary content to stronger official text swatches so it remains readable on the light base. Dark flavours use the official accent values unchanged.

Markdown and syntax stay restrained: code-block content is neutral, while syntax provides differentiation through mauve keywords, blue functions, peach variables/numbers, green strings, and teal types. Markdown uses peach headings, blue links, teal inline code, and mauve list bullets.

## Development

`catppuccin.tera` is authoritative. The committed JSON files let Pi install this repository directly, but they must never be edited manually.

```sh
nix shell nixpkgs#catppuccin-whiskers --command whiskers catppuccin.tera
nix shell nixpkgs#catppuccin-whiskers --command whiskers catppuccin.tera --check
npm pack --dry-run
```

Automated checks keep generated files in sync and smoke-test the package contents. They do not replace visual review: verify Macchiato and Latte at minimum, including transcript text, tool states, Markdown/code, dialogs, and thinking levels.

## Attribution

Palette data and generation come from [Catppuccin](https://github.com/catppuccin/catppuccin) and [Whiskers](https://github.com/catppuccin/whiskers). Pi supplies the theme schema and package system. The design draws on the author's prior personal Macchiato theme and the visual/tooling references [otahontas/pi-coding-agent-catppuccin](https://github.com/otahontas/pi-coding-agent-catppuccin) and [scarcekoi/pi](https://github.com/scarcekoi/pi).

Released under the [MIT License](LICENSE). This is an independent package and is not endorsed by or affiliated with the Catppuccin organization.
