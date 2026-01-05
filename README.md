# Redmine Dark Mode Plugin

> Fork of [fraoustin/redmine_dark](https://github.com/fraoustin/redmine_dark) with custom **Deep Purple & Magenta** color scheme.

## Color Palette

| Color | Hex | Usage |
|-------|-----|-------|
| Aubergine | `#1E1924` | Primary background |
| Rosa | `#C46B8C` | Accent color (links, borders) |
| Pink | `#D4849E` | Secondary accent |
| Light Pink | `#E09DB3` | Highlights |
| Purple-Gray | `#4A3545` | Hover effects |
| Near-White | `#EAEAEA` | Primary text |
| Light Gray | `#F5F5F5` | Secondary background |
| Pastel Lavender | `#DED0EB` | Headers, icons (after inversion) |

## Features

- Dark mode toggle in top right corner
- Supports `prefers-color-scheme: dark` for automatic switching
- Optimized for readability with proper contrast
- Subtle table row hover effect
- Compatible with RTmaterial theme

## Installation

### Option 1: Docker with volume mount

```yaml
# docker-compose.yml
services:
  redmine:
    volumes:
      - ./plugins/redmine_dark:/home/redmine/data/plugins/redmine_dark
```

### Option 2: Dockerfile

```dockerfile
FROM redmine
WORKDIR /usr/src/redmine/plugins
RUN git clone https://github.com/KLIEBHAN/redmine_dark.git
WORKDIR /usr/src/redmine/
```

### Option 3: Manual installation

1. Download and extract to `plugins/redmine_dark`
2. Restart Redmine

If you have asset issues, run:
```bash
RAILS_ENV=production bundle exec rake assets:precompile
```

## Usage

Click **"dark mode"** in the top right corner (after login) to toggle.

![Dark Mode Selected](screenshots/darkmode_selected.png)

### With default theme
![Default Theme](screenshots/darkmode1.png)

### With RTmaterial Theme
![RTmaterial Theme](screenshots/darkmode2.png)

## Technical Notes

This plugin uses CSS `filter: invert(90%)` for dark mode. Colors are calculated to display correctly after inversion:

- Elements with `filter: invert(100%)`: Use `#F6E4FF` to display as pastel lavender
- Elements without own filter: Use `#091B00` to display as pastel lavender

## License

This plugin is released under the **GPLv2**.

## Authors

**Original Author:** Frédéric Aoustin ([fraoustin](https://github.com/fraoustin))

**Fork maintained by:** [KLIEBHAN](https://github.com/KLIEBHAN)

**Contributors:**
- Ilia Lenskii
- Claude Code (color scheme optimization)
