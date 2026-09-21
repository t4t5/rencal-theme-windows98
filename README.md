# renCal Windows 98 theme

A clean Windows 98-inspired light theme for [renCal](https://rencal.org). It
uses the pixel-perfect MS Sans Serif webfont from
[98.css](https://jdan.github.io/98.css/), quiet white calendar surfaces,
classic silver controls, recessed work areas, navy title bars, square event
blocks, property sheet tabs, and dotted keyboard focus indicators while
preserving calendar colours and status states.

![Windows 98 theme in renCal](preview.png)

|                Month                 |                Week                |                 Event editor                  |
| :----------------------------------: | :--------------------------------: | :-------------------------------------------: |
| ![Month view](screenshots/month.png) | ![Week view](screenshots/week.png) | ![Event editor](screenshots/event-editor.png) |

## Installation

renCal 0.8.0 or later is required. Install from a terminal on Linux:

```sh
rencal plugin install t4t5/rencal-theme-windows98
```

Choose **Windows 98** under **Settings → Themes** after installation. The
package includes its regular and bold fonts, so the theme works offline and
loads no remote resources.

## Theme design

The theme targets renCal's 0.8 theme contract. Its top-level declarations use
the public shadcn-compatible colour and radius names, Tailwind's runtime text
scale, and renCal's typography-role and control-height variables. Scoped
component rules then add the parts that make the treatment more than a palette
swap:

- two-step light and dark bevels on buttons, cards, dialogs, and menus;
- reversed bevels for pressed controls and recessed frames for fields;
- white calendar work areas with fine, low-contrast grid lines;
- navy selection and title strips with white text;
- property-sheet tabs, pale yellow tooltips, and dotted focus outlines;
- square calendar events that retain their calendar colours and RSVP states.

The styling is scoped to the selected theme and is removed when another theme
is selected. The implementation was written for renCal, with the component
hierarchy and restrained control treatment of 98.css as a visual reference.
The bundled Pixelated MS Sans Serif webfonts come from 98.css; see
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for attribution and license
details.

## Development

Develop through the complete local checkout so renCal loads both the theme and
its bundled fonts. Add this repository's absolute path (or a `~/` path) to
`~/.config/rencal/plugins.toml`:

```toml
plugins = [
  "~/dev/ren/rencal-theme-windows98",
]
```

renCal links the checkout into its plugin directory and reloads theme edits
while it is running. Copying only `themes/windows98.css` to the loose-theme
directory is useful for quick CSS experiments, but it does not exercise the
font declarations in `rencal-plugin.toml`.

The CSS file intentionally contains bare custom-property declarations followed
by nested selectors: renCal supplies the outer theme selector when it loads the
external theme.

The screenshots use synthetic calendar data.

## License

[MIT](LICENSE)
