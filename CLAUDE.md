# CLAUDE.md

Guidance for Claude Code (claude.ai/code) working w/ code in this repo.

## Project Overview

Personal website + blog, Hugo-powered, hosted GitHub Pages at burythehammer.com. Site has blog posts, projects portfolio, speaking engagements, CV.

## Build and Development Commands

```bash
# Build and serve locally (with live reload)
hugo server

# Build site only (output to public/)
hugo

# Build with minification (production)
hugo --minify
```

Hugo v0.151.0+extended required — extended needed for Sass compilation. Exact version pinned in `.github/workflows/hugo.yml`; keep two in sync if bumped.

No test suite, linter, package manager in repo — validation = `hugo` build w/o error + visual review via `hugo server`.

## Architecture

### Templates and rendering (`layouts/`)

- `_default/baseof.html` = single base template all pages render through. Conditionally includes: page header (skipped on homepage, where `.Title` is `"home"`), page-specific stylesheet (loaded from `sass/<page-title>.sass` when front matter sets `stylesheet: true`), MathJax (when front matter sets `math: true`).
- Content-type templates (`blog/single.html`, `blog/list.html`, `projects/list.html`, `speaking/list.html`, `_default/tags.html`, `index.html`) plug into base via Hugo's `main`/`head` blocks.
- `layouts/partials/header.html` = hardcoded nav — links to about/projects/speaking/blog/cv/contact live here, not config or data.

### Content and data

- `content/blog/*.md`: posts named `YYYY-MM-DD-title.md`, permalinked as `/blog/:title` per `hugo.toml`. Front matter drives per-page behavior: `tags` (string or array — templates handle both), `toc: true`, `stylesheet: true`, `math: true`.
- `data/projects.yml`, `data/speaking.yml`: structured YAML consumed directly by respective list templates — add/edit entries here, not as content pages.

### Styling

- Sass lives in `assets/sass/`, compiled via Hugo's `css.Sass` pipeline + `resources.Minify`, invoked inline in `baseof.html` (no separate build step).
- `main.sass` always loaded; `header.sass` loads on every non-home page; other files (`code.sass`, per-page stylesheets matching page's `.Title`) load conditionally per logic in `baseof.html` above.
- Note: `assets/sass/_sass/_mixins.sass` and `assets/sass/_sass/_variables.sass` = byte-identical dupes of `assets/sass/_mixins.sass` and `assets/sass/_variables.sass`, leftover from Jekyll→Hugo rebuild. Nothing references `_sass/` copies — edit top-level files, treat `_sass/` as dead weight if cleaning up.

### Deployment

- `.github/workflows/hugo.yml` builds w/ `hugo --minify`, deploys to GitHub Pages on every push to `main` — no separate staging step or PR preview.
- `public/` = build output (gitignored), `resources/` = Hugo's resource cache — never edit either directly.
- Custom domain set via `static/CNAME`.

## Agent skills

### Issue tracker

Issues tracked as GitHub Issues on this repo (`burythehammer/burythehammer.github.io`), via the `gh` CLI. See `docs/agents/issue-tracker.md`.

### Domain docs

Single-context layout — `CONTEXT.md` + `docs/adr/` at the repo root. See `docs/agents/domain.md`.