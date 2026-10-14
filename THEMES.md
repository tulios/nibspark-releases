# Making a nibspark theme

A nibspark theme is a `.toml` file of colors in nibspark's themes folder.
This guide is for anyone making one, and for AI agents asked to ("make
me a nibspark theme from my terminal colors").

## The themes folder

| Platform | Folder                                          |
| -------- | ----------------------------------------------- |
| Linux    | `~/.config/nibspark/themes`                     |
| macOS    | `~/Library/Application Support/nibspark/themes` |
| Windows  | `%APPDATA%\nibspark\themes`                     |

Settings > Themes shows the folder. Every `.toml` file directly in the
folder is a theme. nibspark ignores other
files and subfolders.

## The short version

1. Make a new `.toml` file in the themes folder, named after the theme
   (`gruvbox.toml`).
2. Give it a `name`, a `base` (`"light"` or `"dark"`) and a `[palette]`
   of colors. That's a whole theme.
3. Optionally, add the other appearance in a `[dark]` or `[light]` table
   (usually just `[dark.palette]`).
4. Pick it in Settings > Themes. To see your changes each time you save,
   turn on "Watch theme folder for updates" there.

For a complete example, see the example theme in nibspark-releases, or
download a theme from "Browse themes" in Settings > Themes and open its
file.

## The file

```toml
name = "Gruvbox"
base = "dark"
author = "Your name"
description = "Warm, retro colors."

[palette]
background = "#282828"
foreground = "#ebdbb2"
accent = "#d79921"
# …the rest of the names below

# Optional: the theme in the other appearance. Colors it doesn't set
# stay as above.
[light.palette]
background = "#fbf1c7"
foreground = "#3c3836"
```

| Key           | What it's for                                                      |
| ------------- | ------------------------------------------------------------------ |
| `name`        | The name shown in Settings > Themes. Without one, the file's name. |
| `base`        | Required. `"light"` or `"dark"`: the appearance the theme is made for. |
| `author`      | Who made the theme. Shown when browsing themes on nibspark.app.    |
| `description` | A line about the theme. Shown when browsing themes, too.           |

- **Each theme needs its own name.** If two themes have the same name,
  the second one shows an error.
- **The name "Default" is reserved** for nibspark's built-in theme. A
  theme named "Default" goes by its file's name instead.
- **`base`** is shown beside the theme's name, and nibspark switches to
  that appearance when you pick the theme.
- **Set every palette color** if you can. A color you leave out takes the
  Default theme's color for your `base`, which may not suit your colors.

## Colors

Colors are text in quotes: `"#RGB"`, `"#RGBA"`, `"#RRGGBB"` or
`"#RRGGBBAA"`, with alpha last, or `"transparent"`. `rgb()` and color
names like `"red"` don't work.

Outside `[palette]`, a color can also be `"$name"`, meaning the palette's
color of that name: `color = "$border"`.

## The palette

Every color nibspark draws comes from one of these names. The values are
the Default theme's, light and dark, to start from or compare with. You
can also add names of your own and use them elsewhere as `$name`.

### Surfaces

| Name            | What it colors                                                        | Light       | Dark        |
| --------------- | --------------------------------------------------------------------- | ----------- | ----------- |
| `background`    | The window behind everything: the editor's and the preview's page     | `#eef3f8`   | `#16152a`   |
| `surface`       | Cards, dialogs, menus, text fields: one step off the background       | `#ffffff`   | `#1f1e36`   |
| `sunken`        | Boxes inside cards, and quiet fills                                   | `#f1f0fa`   | `#121123`   |
| `raised`        | Buttons and rows under the pointer, open menus                        | `#f7f6fe`   | `#28274a`   |
| `control`       | Slider rails, checkboxes, switches at rest                            | `#e2def4`   | `#34325a`   |
| `border`        | Borders of cards, fields and dialogs                                  | `#d2cee8`   | `#302e4d`   |
| `code`          | Behind code, inline and in blocks                                     | `#e3eaf2`   | `#121123`   |
| `table_header`  | Behind the header rows of tables in the preview                       | `#e3eaf2`   | `#1f1e36`   |
| `rule`          | Lines of tables and code blocks in the preview, and `---` rules       | `#d3dce7`   | `#302e4d`   |
| `shadow`        | Shadows under cards, menus and dialogs (use alpha)                    | `#3a33802a` | `#05041080` |
| `scrim`         | Behind dialogs and drawers, over the window (use alpha)               | `#2a254a44` | `#05041099` |
| `toolbar_track` | Behind the toolbar's pickers, over the window (use alpha; optional)   | (none)      | `#00000040` |

### Text

| Name         | What it colors                                         | Light     | Dark      |
| ------------ | ------------------------------------------------------ | --------- | --------- |
| `foreground` | The text, and icons                                    | `#333333` | `#e6e4f6` |
| `muted`      | Quieter text: hints, captions and weak labels          | `#716e8e` | `#9a97b8` |
| `white`      | Text on the accent, red and green buttons              | `#ffffff` | `#ffffff` |

### Accent

| Name            | What it colors                                                   | Light     | Dark      |
| --------------- | ---------------------------------------------------------------- | --------- | --------- |
| `accent`        | Links, focus rings, the selected item, the cursor's line's tint   | `#6c68d6` | `#9a96f2` |
| `accent_light`  | Behind pressed buttons and selected rows (a pale `accent`)       | `#e4e2fa` | `#2c2a5c` |
| `accent_strong` | Primary buttons, behind `white` text                             | `#5a55c8` | `#5f5ad6` |
| `accent_deep`   | Primary buttons under the pointer                                | `#4a44b0` | `#6f6ae4` |
| `selection`     | Selected text                                                    | `#b4aff0` | `#5a55c8` |

### The editor

| Name                  | What it colors                                       | Light       | Dark        |
| --------------------- | ---------------------------------------------------- | ----------- | ----------- |
| `line_number`         | Line numbers                                         | `#a3a8b8`   | `#5f5d7a`   |
| `line_number_current` | The number of the cursor's line                      | `#e92d8a`   | `#ff5fa8`   |
| `line_current`        | The tint on the cursor's line (use a low alpha)      | `#6c68d612` | `#9a96f214` |
| `highlight`           | The marker under `==highlighted==` text              | `#ffe27a`   | `#6e5a14`   |
| `syntax_keyword`      | Keywords in code                                     | `#4a44b0`   | `#9a96f2`   |
| `syntax_string`       | Strings in code                                      | `#2f8063`   | `#4cb08b`   |
| `syntax_literal`      | Names and numbers in code                            | `#333333`   | `#e6e4f6`   |
| `syntax_comment`      | Comments in code                                     | `#716e8e`   | `#9a97b8`   |
| `syntax_punctuation`  | Punctuation in code                                  | `#55526e`   | `#b8b5d0`   |

### Named colors

Used for statuses, toasts, buttons, avatars and effects.

| Name            | What it colors                                       | Light     | Dark      |
| --------------- | ---------------------------------------------------- | --------- | --------- |
| `blue`          | Info toasts and statuses                             | `#3f74d1` | `#7aa2f0` |
| `green`         | Success: toasts, statuses, buttons (behind `white`)  | `#2f8063` | `#3fa07c` |
| `dark_green`    | Success buttons under the pointer                    | `#246a51` | `#4cb08b` |
| `orange`        | Warnings                                             | `#cf7a26` | `#e8a05a` |
| `red`           | Errors, and delete buttons (behind `white`)          | `#c9483f` | `#e05a50` |
| `bright_red`    | Delete buttons under the pointer                     | `#e26c60` | `#f07468` |
| `pink`          | Avatars and the start view's effects                 | `#cf5f9b` | `#e47ab4` |
| `shocking_pink` | The spark's ticks in the start view's wordmark       | `#e92d8a` | `#ff5fa8` |
| `purple`        | Avatars and effects                                  | `#9466d8` | `#b58cf0` |
| `sky`           | Avatars and effects                                  | `#9fb8f2` | `#7d97d8` |
| `mint`          | A pale green, unused for now                         | `#d9efe6` | `#1d3a31` |

### Charts

`chart1` to `chart8` color the folders in the docs sidebar, in turn, and
the series in charts. Keep them distinct from each other and readable on
`background`, in this order: blue, orange, aqua, yellow, magenta, green,
violet, red.

| Name     | Light     | Dark      |
| -------- | --------- | --------- |
| `chart1` | `#2a78d6` | `#3987e5` |
| `chart2` | `#eb6834` | `#d95926` |
| `chart3` | `#1baf7a` | `#199e70` |
| `chart4` | `#eda100` | `#c98500` |
| `chart5` | `#e87ba4` | `#d55181` |
| `chart6` | `#008300` | `#1f9a1f` |
| `chart7` | `#4a3aa7` | `#9085e9` |
| `chart8` | `#e34948` | `#e66767` |

## Light and dark

A theme is made for its `base` appearance. To give it a version for the
other one, add a `[dark]` table to a light theme, or a `[light]` table to
a dark one. Usually that's just `[dark.palette]` or `[light.palette]`,
with the colors that change. Colors you leave out stay the same as the
main palette.

The table can hold any of the other tables below, too: `[dark.visuals]`,
for example. A theme without one looks the same in light and dark.

## Making it read well

- **Contrast**, to aim for: `foreground` on `background`, `surface` and
  `code` at least 7:1; `muted` on `background` and `surface` at least
  4.5:1; `white` on `accent_strong`, `green` and `red`, and on their
  hovered shades (`accent_deep`, `dark_green`, `bright_red`), at least
  4.5:1. A contrast calculator is more reliable than your eye here.
- **Keep the surfaces close.** `sunken`, `background`, `surface` and
  `raised` are close shades of one another, a few percent of lightness
  apart, so cards look raised from the page.
- **Use alpha where the table says so.** `line_current`, `shadow`,
  `scrim` and `toolbar_track` are drawn over other colors. A solid
  `line_current` hides the text's background.
- **Dark themes need lighter accents.** An accent that reads well on
  white is often too dark on near-black. Write the accents again in
  `[dark.palette]` or `[light.palette]`.
- **Starting from a terminal or editor theme**: its background and
  foreground are `background` and `foreground`. Its blue, green, red,
  yellow and magenta make good `blue`, `green`, `red`, `orange` and
  `purple`, and good chart colors. Its selection color is `selection`.
  Its comment color is `syntax_comment`, and often `muted`. Make
  `surface`, `sunken` and `raised` by stepping the background a little
  lighter and darker.

## More than colors

Most themes need only the palette. A theme can also change shapes,
spacing and shadows with the tables below. Anything a theme leaves out
stays as it is in the Default theme. If a table has a key nibspark
doesn't know, for example a misspelled one, the theme doesn't load, and
Settings > Themes shows which key it is.

Some values have their own shapes:

- **Strokes**: `{ width = 1.0, color = "$border" }`
- **Shadows**: `{ offset = [0, 4], blur = 16, spread = 0, color =
  "$shadow" }`. `offset` is two whole numbers from -128 to 127, and `blur`
  and `spread` are whole numbers from 0 to 255.
- **Corner radii**: a whole number from 0 to 255 for every corner, or
  `{ nw = 8, ne = 8, sw = 0, se = 0 }`.
- **Margins**: a whole number for every side, `[x, y]`, or
  `{ left = 8, right = 8, top = 4, bottom = 4 }`.

Sizes are in points. In strokes and shadows you can leave out any key to
keep the Default's value. In corner radii and margins, a corner or side
you leave out is 0.

### `animation_time`

At the top of the file: how long widgets take to animate, in seconds.
The Default is `0.12`.

### `[spacing]`

- `[x, y]` sizes: `item_spacing`, `button_padding`, `interact_size`
- Margins: `window_margin`, `menu_margin`
- Numbers: `indent`, `slider_width`, `slider_rail_height`, `combo_width`,
  `combo_height`, `text_edit_width`, `icon_width`, `icon_width_inner`,
  `icon_spacing`, `tooltip_width`, `menu_width`, `menu_spacing`

### `[visuals]`

| Key                               | What it sets                                         |
| --------------------------------- | ---------------------------------------------------- |
| `panel_fill`                      | The color behind the window's panels                 |
| `window_fill`                     | The color of dialogs and other floating windows      |
| `extreme_bg_color`                | The color of text fields and the deepest backgrounds |
| `faint_bg_color`                  | The color of quiet fills, such as striped rows       |
| `text_edit_bg_color`              | The color behind text fields, if different           |
| `code_bg_color`                   | The color behind code                                |
| `hyperlink_color`                 | The color of links                                   |
| `weak_text_color`                 | The color of quieter text                            |
| `override_text_color`             | One color for all text                               |
| `warn_fg_color`, `error_fg_color` | The colors of warnings and errors                    |
| `window_stroke`                   | The stroke around windows                            |
| `window_shadow`, `popup_shadow`   | Shadows under windows, and under menus and popups    |
| `window_corner_radius`            | The corner radius of windows                         |
| `menu_corner_radius`              | The corner radius of menus                           |
| `selection`                       | Selected text and items: `{ bg_fill = color, stroke = stroke }` |
| `button_frame`                    | `true` to give buttons a background                  |
| `collapsing_header_frame`         | `true` to give collapsing headers a background       |
| `indent_has_left_vline`           | `true` to draw a line beside indented blocks         |
| `striped`                         | `true` to stripe tables and lists                    |
| `slider_trailing_fill`            | `true` to fill sliders up to the knob                |
| `disabled_alpha`                  | The opacity of disabled widgets, from 0 to 1         |

### `[visuals.widgets.<state>]`

How widgets look in each state:

- `noninteractive`: labels and separators
- `inactive`: buttons and other widgets at rest
- `hovered`: under the pointer
- `active`: pressed or dragged
- `open`: an open menu or drop-down
- `all`: every state at once, before the state's own table

| Key             | What it sets                                         |
| --------------- | ---------------------------------------------------- |
| `bg_fill`       | The background of widgets that always have one, such as checkboxes |
| `weak_bg_fill`  | The background of widgets that may have one, such as buttons |
| `bg_stroke`     | The stroke around the background                     |
| `fg_stroke`     | The stroke of text and icons. Its color is the text's |
| `corner_radius` | The corner radius of the background                  |
| `expansion`     | How much the widget grows in this state, in points   |

### `[elevation]`

Shadows by level: `1` for cards, `2` for menus and popovers, `3` for
dialogs and drawers, `4` for the command palette.

```toml
[elevation]
2 = { offset = [0, 2], blur = 8, spread = 0, color = "$shadow" }
```

### `[variants.<name>]`

Looks for special widgets: `primary` (main buttons), `danger` (delete
buttons), `success` and `compact`. Each can hold `animation_time`,
`[spacing]` and `[visuals]`, as above:
`[variants.primary.visuals.widgets.hovered]`.

### `[fx]` and `[ui]`

Presets for nibspark's effects, under `[fx]` (borders, transitions,
materials, backgrounds, text animations), and for its components, under
`[ui]` (buttons, tables, toasts, dialogs and more). The example theme in
nibspark-releases shows the presets and their keys. A preset can start
from another of the same kind with `extends = "<name>"`. nibspark ignores
keys it doesn't know in these two tables.

## Following Omarchy

On [Omarchy](https://omarchy.org), Settings > Themes also offers "Follow
Omarchy": the theme Omarchy is using, made into a nibspark theme from
its `colors.toml`. It follows Omarchy as it switches themes, in light or
dark as Omarchy's theme is.

Omarchy's background, foreground, accent and terminal colors are used as
they are. Surfaces, borders and quieter text are blended from the
background and the foreground. Buttons' accent, green and red are
darkened until white text on them reads. To make a theme of your own
from an Omarchy theme, start from its colors the same way, or from
Tokyo Night in nibspark-releases, made from Omarchy's.

## Trying it as you go

Turn on "Watch theme folder for updates" in Settings > Themes while you
work on a theme. nibspark reloads the themes each time you save, and
shows your changes right away. It's off by default.
