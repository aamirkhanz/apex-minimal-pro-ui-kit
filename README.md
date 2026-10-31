# Minimal Pro UI Kit for Oracle APEX

The look of modern product tools for Oracle APEX Universal Theme: crisp 1px hairlines instead of heavy shadows, near-flat white panels on a light grey page, one indigo accent, and a deep dark mode where the accent glows. One CSS file styles every Universal Theme component, in light and dark mode, without changing your pages, templates or template options.

[![Live demo](https://img.shields.io/badge/Live_demo-5e6ad2?style=for-the-badge)](https://oracleapex.com/ords/r/aamirkhanz/plugins/minimal-pro-ui-kit) &nbsp; Sign in as `demo` with the password `Demo`.

![Overview in light mode](screenshots/overview-light.png)

| | |
|---|---|
| **Files** | `minimal-pro.css` (the look), `minimal-pro.js` (optional light/dark switch) |
| **Version** | 1.0.0 |
| **Built for** | Oracle APEX 26.2, Universal Theme with the Iris theme style (tested); other styles are not tested yet |
| **License** | MIT |

## What it styles

Every component of the Universal Theme reference: Alert, Avatar, Badge, Badges List, Breadcrumb, Button, Button Container, Button Group, Calendar, Card Regions, Card Templates, Carousel, Charts, Classic Report, Collapsible, Column Toggle Report, Comments, Content Block, Content Row, Contextual Info, Flexbox Container, Form Field (every item type and label template), Help Text, Hero, Image, Inline Dialog, Interactive Grid, Interactive Report, Links List, List View, Media List, Menu Bar, Menu Popup, Metric Card, Navigation Bar, PL/SQL Dynamic Content, Reflow Report, Region Display Selector, Standard, Static Content, Tabs Container, Timeline, Title Bar and Tree.

It also styles the page shell (header, side navigation, title bar, footer), modal and inline dialogs, drawers, popups, menus, page messages, tooltips, the date picker, Faceted Search, the rich text editor and select lists.

## Install

1. Download `minimal-pro.css` and, for the light/dark switch, `minimal-pro.js` from the [latest release](https://github.com/aamirkhanz/apex-minimal-pro-ui-kit/releases/latest) or from this repository.
2. In App Builder, go to **Shared Components > Static Application Files** and upload both files.
3. Go to **Shared Components > User Interface Attributes** and add:
   - CSS File URLs: `#APP_FILES#minimal-pro.css`
   - JavaScript File URLs: `#APP_FILES#minimal-pro.js`

That's all: every page of the application now uses the kit. Remove the two URLs to go back to plain Universal Theme.

## Dark mode

![Forms in dark mode](screenshots/forms-dark.png)

`minimal-pro.js` switches between light and dark and remembers the choice (localStorage `mp-mode`); until the user chooses, it follows the operating system.

- Add a button or link with the attribute `data-mp-mode-toggle`, or call `minimalPro.toggle()`.
- `minimalPro.setMode( "light" | "dark" | "auto" )` sets a mode; `minimalPro.getMode()` returns the current one.
- `<html>` fires `mp-modechange` with `detail.mode` after a change, for example to redraw charts.

To open each page in the saved mode without a flash, put this snippet in the page template's HTML header, before the CSS:

```html
<script>(function(d){var m;try{m=localStorage.getItem("mp-mode")}catch(e){}
if(m!=="dark"&&m!=="light")m=matchMedia("(prefers-color-scheme: dark)").matches?"dark":"light";
d.documentElement.classList.add("mp-"+m)})(document);</script>
```

Without the JavaScript, the kit is light; add the class `mp-dark` to `<html>` yourself for dark.

## Make it yours

Override the tokens in your own CSS, loaded after the kit:

```css
:root { --mp-accent: #0e9f6e; --mp-accent-2: #0b7a55; --mp-accent-text: #0b7a55; --mp-radius: 12px; }
html.mp-dark { --mp-accent: #34d399; --mp-accent-text: #6ee7b7; }
```

| Token | What it sets |
|---|---|
| `--mp-page`, `--mp-bg` | The page (and side navigation), and the panels on it |
| `--mp-line`, `--mp-line-strong` | Hairlines: panel edges and separators, and the edges of buttons |
| `--mp-well`, `--mp-field-edge` | Fields and their edge (accent on focus) |
| `--mp-track` | Tab bars and segmented controls |
| `--mp-accent`, `--mp-accent-2`, `--mp-accent-text` | The accent, its hover and edge shade, and accent text |
| `--mp-text`, `--mp-text-2` | Text and secondary text |
| `--mp-font` | The font (system UI; Inter when installed) |
| `--mp-radius`, `--mp-radius-sm` | Corner rounding of regions, and of buttons and fields |
| `--mp-success`, `--mp-warning`, `--mp-danger`, `--mp-info` | Status colors |

For your own regions, items and HTML, add a CSS class: `mp-card`, `mp-raised`, `mp-inset`, `mp-subtle`, `mp-flat`, `mp-pill` or `mp-accent`.

## Screenshots

| | |
|---|---|
| ![Buttons](screenshots/buttons-light.png) | ![Alerts](screenshots/alerts-light.png) |
| ![Cards in dark mode](screenshots/cards-dark.png) | ![Interactive Report](screenshots/reports-light.png) |
| ![Overview in dark mode](screenshots/overview-dark.png) | ![Charts in dark mode](screenshots/charts-dark.png) |

## Notes

- **No markup changes.** The kit only overrides Universal Theme's CSS variables and styles its components; your templates and template options stay standard.
- **Accessibility.** Text keeps WCAG AA contrast on the surfaces, fields have a clear edge, keyboard focus always shows a ring, and motion is reduced when the user asks for it.
- **Fonts.** The kit uses the system UI font (Inter, if your users have it installed); it loads no web fonts.
- **Select lists.** In browsers with customizable selects (Chrome and Edge 135 and later) the open list takes the kit's style; other browsers show their native list.
- **Charts.** Chart series keep the colors you set in each chart; the kit styles the region around them.

## License

MIT, see [LICENSE](LICENSE).

## More

Plug-ins and updates for Oracle APEX by [TechRevX](https://www.techrevx.com). More UI kits: [Neumorphism UI Kit](https://github.com/aamirkhanz/apex-neumorphism-ui-kit), [Glassmorphism UI Kit](https://github.com/aamirkhanz/apex-glassmorphism-ui-kit), [Skeuomorphism UI Kit](https://github.com/aamirkhanz/apex-skeuomorphism-ui-kit), [Material 3 Expressive UI Kit](https://github.com/aamirkhanz/apex-material-expressive-ui-kit), [Claymorphism UI Kit](https://github.com/aamirkhanz/apex-claymorphism-ui-kit), [Liquid Glass UI Kit](https://github.com/aamirkhanz/apex-liquid-glass-ui-kit), [Swiss Grid UI Kit](https://github.com/aamirkhanz/apex-swiss-grid-ui-kit).
