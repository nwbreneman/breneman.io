# breneman.io

Personal resume/portfolio website built with [Zola](https://www.getzola.org/), a static site generator.

## Quick Start

```bash
# Install Zola (macOS)
brew install zola

# Start local development server
zola serve

# Open http://127.0.0.1:1111 in your browser
```

## Updating Content

All content lives in `content/` as Markdown files with TOML front matter.

### Home Page

Edit `content/_index.md` to update your name, title, and bio.

### Adding New Pages

1. Create a new `.md` file in `content/`
2. Add front matter with title and optional template
3. Write content in Markdown

Example:
```markdown
+++
title = "About Me"
+++

# About Me

Your content here...
```

### Static Assets

Place images, PDFs, etc. in `static/`. Reference them as `/filename.ext` in your content.

## Customizing Templates

Templates are in `templates/`. The site uses:
- `base.html` - Main HTML shell
- `page.html` - Template for standard pages

Modify these to change the site's layout and styling.

## Deployment

The site auto-deploys to GitHub Pages when you push to main. Just commit your changes:

```bash
git add .
git commit -m "Update content"
git push origin main
```

## Project Structure

```
content/          # Markdown content files
static/           # Images, PDFs, and other assets
templates/        # HTML templates (Tera/Jinja2 syntax)
config.toml       # Site configuration
```
