# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal website and blog powered by Hugo, hosted on GitHub Pages at burythehammer.com. The site features blog posts, projects portfolio, speaking engagements, and CV.

## Build and Development Commands

### Local Development
```bash
# Build and serve locally (with live reload)
hugo server

# Build site only (output to public/)
hugo

# Build with minification (production)
hugo --minify
```

### Hugo Version
This project uses Hugo v0.151.0+extended. The extended version is required for Sass/SCSS compilation.

## Architecture

### Hugo Structure

- **hugo.toml**: Main Hugo configuration file with:
  - Base URL: https://www.burythehammer.com
  - Permalink format: `/blog/:title` (matches previous Jekyll setup)
  - Markdown renderer: Goldmark with unsafe HTML enabled
  - Table of contents: H1-H2 headers
  - Taxonomies: tags enabled

- **layouts/**:
  - `_default/baseof.html`: Base template with conditional header, page-specific stylesheets, MathJax support
  - `blog/single.html`: Blog post template with metadata, tags, and TOC support
  - `blog/list.html`: Blog index listing all posts
  - `index.html`: Homepage template
  - `404.html`: Custom 404 error page
  - `_default/tags.html`: Tags taxonomy page
  - `projects/list.html`: Projects portfolio page
  - `speaking/list.html`: Speaking engagements page

- **layouts/partials/**:
  - `header.html`: Site navigation header
  - `post_summary.html`: Blog post summary for listings

- **content/**:
  - `blog/`: Blog posts in Markdown format, named `YYYY-MM-DD-title.md`
  - `_index.md`: Homepage content
  - `projects/_index.md`: Projects section index
  - `speaking/_index.md`: Speaking section index

- **data/**: YAML data files
  - `projects.yml`: Portfolio projects with descriptions, tools, time ranges
  - `speaking.yml`: Speaking engagement information

### Hugo Features Replacing Jekyll Plugins

Hugo's built-in features replace all previous Jekyll custom plugins:

1. **Excerpt generation**: Hugo's `.Summary` replaces custom excerpt.rb plugin
2. **Table of Contents**: Hugo's `.TableOfContents` replaces tocGenerator.rb plugin
3. **Static resource URLs**: Hugo's resource pipeline and shortcodes replace static.rb plugin

### Styling

- **Sass/SCSS**: Hugo processes Sass files from `/assets/sass/`
- **Variables**: `assets/sass/_variables.sass` contains theme colors and shared styling
- **Mixins**: `assets/sass/_mixins.sass` contains reusable style patterns
- **Processing**: Uses Hugo's `css.Sass` filter with minification
- **Fonts**: Custom icon fonts for projects and social media in `/static/fonts/`

### Deployment

- **Method**: GitHub Actions (modern approach)
- **Workflow**: `.github/workflows/hugo.yml` handles build and deployment
- **Hugo version**: v0.151.0+extended (specified in workflow)
- **Custom domain**: Configured via CNAME file in /static/
- **Build output**: `public/` directory (generated, not committed)

The site automatically deploys when changes are pushed to the `main` branch. Hugo builds complete in ~10-20ms compared to Jekyll's ~500ms builds (25-50x faster).

## Important Notes

- The `public/` directory is the build output and should not be edited directly (equivalent to Jekyll's `_site/`)
- Blog posts require front matter with title, date, tags, and optionally `toc: true`
- Hugo's built-in features eliminate need for custom plugins
- Tags can be single strings or arrays - templates handle both cases
- Page-specific stylesheets are automatically loaded based on page title when `stylesheet: true` is set in front matter
- Old Jekyll files (_posts/, _layouts/, _includes/, _plugins/, Gemfile) are retained during migration but not used by Hugo
