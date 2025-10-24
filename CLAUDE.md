# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based personal/family website for the Delgado Perez family, hosted on GitHub Pages at https://family.delgadoperez.com. The site uses the Just the Docs theme and is automatically deployed via GitHub Actions.

## Architecture

**Static Site Generator**: Jekyll with GitHub Pages compatibility
- Theme: `just-the-docs/just-the-docs` (via remote_theme)
- Domain: https://family.delgadoperez.com
- GitHub Pages deployment via `.github/workflows/jekyll.yml`

**Key Configuration**:
- `_config.yml`: Site-wide settings, theme configuration, and metadata
  - Note: Changes to `_config.yml` require server restart
- `Gemfile`: Ruby dependencies including `jekyll-theme-hydejack`, `jekyll-feed`, and `github-pages`

**Content Structure**:
- Blog posts: `_posts/` directory with naming format `YEAR-MONTH-DAY-title.markdown`
- Pages: Root-level `.markdown` or `.html` files (e.g., `about.markdown`)
- Front matter: YAML metadata at top of each content file defining layout, title, permalink, etc.

## Development Commands

### Local Development
```bash
# Install dependencies
bundle install

# Serve site locally with auto-regeneration
bundle exec jekyll serve
```

The site will be available at http://localhost:4000 (or configured port). Changes to most files trigger auto-regeneration, except `_config.yml` which requires a server restart.

### Build
```bash
# Build site to _site/ directory
bundle exec jekyll build

# Build with production environment
JEKYLL_ENV=production bundle exec jekyll build
```

## Deployment

The site auto-deploys to GitHub Pages on every push to the `main` branch via `.github/workflows/jekyll.yml`. The workflow:
1. Sets up Ruby 3.1 and installs dependencies
2. Builds the site with `bundle exec jekyll build`
3. Uploads and deploys the `_site/` directory to GitHub Pages

No manual deployment steps required.

## Content Creation

**New Blog Post**:
Create file in `_posts/` with naming format `YYYY-MM-DD-title.markdown` and front matter:
```yaml
---
layout: post
title: "Your Title"
date: YYYY-MM-DD HH:MM:SS -0600
categories: category1 category2
---
```

**New Page**:
Create `.markdown` or `.html` file in root with front matter:
```yaml
---
layout: page
title: "Page Title"
permalink: /page-url/
---
```
