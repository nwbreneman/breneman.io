# AGENTS.md - Developer Guidelines for breneman.io

This project is a Zola static site generator website - a personal resume/portfolio site for a senior software engineer.

## Build Commands

This project uses Zola (static site generator) and Nix for development. Enter the nix shell first to access Zola.

```bash
# Enter development shell (provides zola and other tools)
nix develop

# Start local development server (with live reload)
zola serve

# Build for production (outputs to public/)
zola build

# Check for errors without serving
zola check

# Exit nix shell when done
exit
```

### Single Test Commands
This project has no test suite - it's a static site with no JavaScript/TypeScript code.

## Code Style Guidelines

### General Principles
- Keep things simple - this is a personal site, not a complex webapp
- Minimal JavaScript - prefer vanilla JS if needed
- No build steps beyond Zola

### Templates (Jinja2/Tera)
- Use Tera template syntax: `{% block %}{{ variable }}{% endblock %}`
- Indent HTML tags with 2 spaces
- Use semantic HTML5 elements
- Keep templates minimal - prefer Markdown content over custom templates

Example:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{% block title %}{{ config.title }}{% endblock %}</title>
  {% block extra_head %}{% endblock %}
</head>
<body>
  <main>
    {% block content %}{% endblock %}
  </main>
</body>
</html>
```

### Configuration (TOML)
- Use lowercase with underscores for keys
- Group related settings under sections
- Keep config minimal - only set what's needed

Example:
```toml
base_url = "https://breneman.io"
default_language = "en"

[markdown]
highlight_code = true
```

### Content (Markdown)
- Use standard Markdown syntax
- Front matter should use TOML format
- Keep front matter minimal
- Use semantic heading hierarchy (h1 -> h2 -> h3)

Example:
```markdown
+++
title = "Page Title"
date = 2024-01-01
+++

# Heading

Content here...
```

### CSS/SASS
- If adding styles, use SASS (Zola compiles it)
- Follow BEM naming for complex components
- Keep styles simple and minimal
- Use CSS custom properties for theming

### Naming Conventions
- Templates: lowercase with hyphens (e.g., `base.html`, `blog-post.html`)
- Content files: lowercase with hyphens (e.g., `my-post.md`)
- Variables: snake_case in templates

### Error Handling
- Templates: use `zola check` to validate before deploying
- Broken links: verify external links are valid
- Images: ensure all referenced images exist in static/ or content/

### Git Workflow
- Commit messages: be concise and descriptive
- Main branch deploys automatically via GitHub Actions
- No protected branches or complex PR requirements

### GitHub Actions
- The site auto-deploys on push to main
- Uses `shalzz/zola-deploy-action` for GitHub Pages deployment
- No manual approval needed
- **Always verify the workflow succeeds after pushing**: `gh run list --limit 1`

## Project Structure

```
/home/nathan/code/breneman.io
├── config.toml          # Site configuration
├── content/            # Markdown content files
│   └── _index.md       # Home page
├── static/             # Static assets (images, etc.)
├── templates/          # HTML templates
│   ├── base.html       # Base template
│   ├── index.html      # Home page template
│   └── page.html       # Page template
├── .github/
│   └── workflows/
│       └── publish.yml # CI/CD pipeline
└── flake.nix           # Nix development environment
```

## Common Tasks

### Adding a New Page
1. Create `content/new-page.md` with front matter
2. Add content using Markdown
3. Run `zola serve` to preview

### Adding Static Assets
1. Place files in `static/` directory
2. Reference as `/filename.ext` in templates/content

### Modifying Templates
1. Edit files in `templates/`
2. Use `zola serve --interface 0.0.0.0` for local network access during development

## Cursor/Copilot Rules

None present - this file serves as the primary reference for agentic coding.
