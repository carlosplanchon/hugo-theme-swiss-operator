# Swiss Operator

A minimalist Hugo theme inspired by Swiss editorial design, built for technical writing, engineering notes, and high-clarity personal blogs.

| Light | Dark |
|---|---|
| ![Swiss Operator - light mode](https://raw.githubusercontent.com/carlosplanchon/hugo-theme-swiss-operator/refs/heads/main/images/screenshot.png) | ![Swiss Operator - dark mode](https://raw.githubusercontent.com/carlosplanchon/hugo-theme-swiss-operator/refs/heads/main/images/screenshot-home-dark.png) |

---

## Why Swiss Operator?

The design prioritizes **legibility**, **typographic rhythm**, **grid consistency**, and **structural alignment** - the same principles that make Swiss editorial design reliable in print. These qualities matter most in contexts where precision is non-negotiable: engineering notes, technical documentation, and working knowledge bases where the content has to carry its own weight.

No gradients, no hero sections, no visual noise. Just a clean reading surface and a layout that stays out of the way.

> "Good design is as little design as possible." - Dieter Rams

---

## Features

- **Swiss editorial aesthetic** - bold typography, tight grid, deliberate whitespace
- **Dark / light mode** - auto-detects system preference; toggle persists via `localStorage`
- **Responsive layout** - 70/30 two-column grid collapses to a single column on mobile
- **Category color coding** - assign a hex color to each category; shown as a left border accent on post cards
- **Customizable accent colors** - override the default Blueprint Blue and Safety Red from `hugo.toml`
- **Multi-language** - ships with English, Spanish, and French i18n strings
- **Local or Google Fonts** - load Inter + JetBrains Mono from Google Fonts or self-host them
- **RSS feed** - enabled for home and section pages out of the box
- **Remark42 comments** - optional self-hosted comment system with automatic dark/light sync
- **Favicon support** - SVG, PNG, ICO, and JPEG

---

## Requirements

- Hugo **0.110.0+**
- Go **1.21+** (only required for Hugo Modules installation)

---

## Installation

### As a Git submodule

```bash
git submodule add https://github.com/carlosplanchon/hugo-theme-swiss-operator themes/swiss-operator
```

Set the theme in your `hugo.toml`:

```toml
theme = 'swiss-operator'
```

### Manual

Download or clone this repository into your site's `themes/swiss-operator/` directory, then set `theme = 'swiss-operator'` in your `hugo.toml`.

---

## Quick start

Copy the example site to bootstrap your configuration:

```bash
cp -r themes/swiss-operator/exampleSite/* .
```

Then run:

```bash
hugo server
```

---

## Configuration

Below is a full annotated `hugo.toml`:

```toml
baseURL = 'https://example.com/'
languageCode = 'en-us'
title = 'My Swiss Blog'
theme = 'swiss-operator'

[outputs]
home    = ['html', 'rss']
section = ['html', 'rss']

[params]
description  = "A personal blog about your topics"
postsPerPage = 10
favicon      = "/favicon.svg"

# Social links shown in the footer (all optional)
[params.social]
github    = "https://github.com/username"
linkedin  = "https://linkedin.com/in/username"
x         = "https://x.com/username"
instagram = "https://instagram.com/username"
facebook  = "https://facebook.com/username"

[params.theme]
accentBlue  = "#0055FF"   # Left-border accent / link color
accentRed   = "#E62B1E"   # Secondary accent
showRss     = true
localFonts  = false       # true → serve fonts from /assets/fonts/ instead of Google Fonts

# Map category names to hex colors (used as left-border accents on post cards)
[params.categories]
colors = { Engineering = "#0055FF", Aviation = "#E62B1E", Design = "#000000" }

# Optional: Remark42 comment system
# [params.remark42]
# url  = "https://your-remark42-instance.com"
# site = "blog"

# Navigation menu
[[menu.main]]
  name   = "About"
  url    = "/about/"
  weight = 1
```

---

## Post front matter

```yaml
---
title: "My Post Title"
date: 2024-01-15
description: "A short summary shown on the post card."
categories: ["Engineering"]
image: "/images/my-cover.jpg"   # optional cover image
draft: false
---
```

- `categories` - the first category determines the card's accent color.
- `image` - displayed as a 4:3 cover image on the post card.
- `description` - shown as the card subtitle on the home page.

---

## Typography

| Role | Typeface |
|---|---|
| Body & headings | [Inter](https://fonts.google.com/specimen/Inter) |
| Dates, code, metadata | [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) |

To self-host both fonts, set `localFonts = true` in `[params.theme]`. The font files are already bundled under `assets/fonts/`.

---

## Multi-language

The theme ships with `i18n/en.toml`, `i18n/es.toml`, and `i18n/fr.toml`. To add another language, create a new file in your site's `i18n/` directory following the same keys.

---

## Comments (Remark42)

Uncomment and fill in the `[params.remark42]` block in `hugo.toml`. The comment widget automatically inherits the active light/dark theme.

```toml
[params.remark42]
url  = "https://comments.example.com"
site = "myblog"
```

---

## License

[MIT](LICENSE)
