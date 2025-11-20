# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a course website for "Applications multi-tiers" (Multi-tier Applications) that hosts educational slides built with Reveal.js. The site is a static website hosted on GitHub Pages, containing lecture slides, laboratory assignments, and course resources for teaching multi-tier architecture and Java development.

## Architecture

- **Static Site**: Pure HTML/CSS/JavaScript site with no build process
- **Reveal.js Presentations**: Each slide deck is a standalone HTML file in `slides/*/index.html`
- **Template-based**: All slide decks follow the structure defined in `slides/template.html`
- **Custom Plugins**: Custom Reveal.js plugin in `slides/script.js` for JavaScript code evaluation and spoiler functionality

## File Structure

- `index.html` - Main course homepage listing all slides, labs, and resources
- `slides/` - Contains numbered directories (0-14) for each lecture topic
  - Each lecture has its own `index.html` file
  - Shared `script.js` and `style.css` for all presentations
  - `template.html` - Base template for creating new slide decks
- `fontawesome-6.4.2/` - Font Awesome icons (local copy)
- `css/` - Global stylesheets including syntax highlighting
- `images/` - Course images and diagrams
- `node_modules/` - Contains only Reveal.js dependency

## Common Commands

Since this is a static site, there are no build or test commands. To develop:

```bash
# Serve the site locally (use any static server)
python3 -m http.server 8000
# or
npx serve .
```

Then navigate to `http://localhost:8000` to view the site.

## Working with Slides

### Creating a New Slide Deck

1. Copy `slides/template.html` to `slides/[number]-[topic]/index.html`
2. Update the `<title>` tag and main heading
3. Add content in Markdown format within `<textarea data-template>` sections
4. Use FontAwesome icons with `<i class="fas fa-[icon-name]"></i>`

### Slide Structure

Each slide deck follows this pattern:
- Title slide with dark background (`data-background="#333333"`)
- Overview slide listing topics
- Section dividers (dark background) followed by content slides
- Content slides use `data-markdown` for Markdown support
- Notes can be added within `<aside class="notes">` tags

### Custom Features

- **Double-click JavaScript code blocks** to evaluate them in the browser console (via `EvalJavaScript` plugin)
- **Spoiler blocks** with `.spoiler` class can be revealed by clicking
- **Print-friendly URLs** with `?showNotes=separate-page&print-pdf` parameters (Chrome/Chromium only)

## Adding Content to Main Index

The main `index.html` contains four sections:
1. **Support de cours** (Course Materials) - Links to slide decks
2. **Quizz** - Links to quizzes
3. **Laboratoires** - GitHub Classroom links for assignments
4. **Exemples** - Example repositories

When adding new slides, update the ordered list in the "Support de cours" section with both web and print links.

## Styling

- Uses Pico CSS for the main landing page (`index.html`)
- Reveal.js white theme for presentations
- Solarized Light syntax highlighting (`css/solarized-light.css`)
- Custom slide styles in `slides/style.css`

## Path References

Slide decks use absolute paths from root (`/node_modules/`, `/css/`, `/fontawesome-6.4.2/`) to work correctly both when served locally and on GitHub Pages. Maintain this convention when adding new resources.
