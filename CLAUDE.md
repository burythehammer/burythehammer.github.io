# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal website and blog powered by Jekyll, hosted on GitHub Pages at burythehammer.com. The site features blog posts, projects portfolio, speaking engagements, and CV.

## Build and Development Commands

### Local Development
```bash
# Install dependencies (requires Ruby 3.3.4)
bundle install

# Build and serve locally (with live reload)
bundle exec jekyll serve

# Build site only (output to _site/)
bundle exec jekyll build

# Build with LSI (related posts) - slower but more accurate
bundle exec jekyll build --lsi
```

### Ruby Version
This project requires Ruby 3.3.4 (specified in Gemfile and .ruby-version). Use a Ruby version manager like rbenv or rvm if needed.

## Architecture

### Jekyll Structure

- **_config.yml**: Main Jekyll configuration. Permalink format is `/blog/:title`. LSI (related posts) is enabled. Default layout is "default", posts use "post" layout with TOC enabled by default.

- **_layouts/**:
  - `default.html`: Base layout with conditional header inclusion (all pages except home)
  - `post.html`: Blog post layout with metadata (title, date, tags) and conditional TOC generation

- **_includes/**: Reusable components (header, post_summary, smooth_scroll for TOC navigation)

- **_posts/**: Blog posts in Markdown format, named `YYYY-MM-DD-title.md`

- **_data/**: YAML data files
  - `projects.yml`: Portfolio projects with descriptions, tools, time ranges
  - `speaking.yml`: Speaking engagement information

### Custom Plugins (_plugins/)

Three custom Jekyll plugins extend functionality:

1. **excerpt.rb**: Liquid filter `excerpt` that extracts first paragraph from HTML using Nokogiri, stripping headers/markup

2. **static.rb**: Custom `{% static %}` tag for converting file paths to resource URLs in blog posts. Infers resource directory from post title.

3. **tocGenerator.rb**: Generates table of contents from H1/H2 headers with:
   - Anchor links with smooth scrolling
   - Configurable via _config.yml (minItemsToShowToc, anchorPrefix, labels)
   - Skip TOC per page with `noToc: true` in front matter
   - Auto-adds syntax highlighting classes to code blocks

### Styling

- **CSS**: Uses Sass (`.sass` files in `/css/` and `/_sass/`)
- **Variables**: `_sass/_variables.sass` contains theme colors and shared styling
- **Compression**: Sass style is set to `:compressed` in _config.yml
- **Fonts**: Custom icon fonts for projects and social media in `/fonts/`

### Deployment

- **Method**: GitHub Actions (modern, recommended approach as of 2025)
- **Workflow**: `.github/workflows/jekyll.yml` handles build and deployment
- **Ruby version**: 3.3.4 (GitHub Pages compatible)
- **GitHub Pages gem**: v232 for dependency compatibility
- **Custom domain**: Configured via CNAME file

The site automatically deploys when changes are pushed to the `main` branch. GitHub Actions provides better control, faster builds, and clearer error messages compared to legacy branch-based deployment.

## Important Notes

- The `_site/` directory is the build output and should not be edited directly
- Blog posts require front matter with title, date, tags, and optionally `toc: true`
- LSI (Latent Semantic Indexing) is enabled for better related posts but increases build time
- To disable TOC on a specific page, add `noToc: true` to front matter
