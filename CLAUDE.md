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
  - Theme-specific settings like search, navigation, footer, etc.
- `Gemfile`: Ruby dependencies including `jekyll-feed`, `jekyll-remote-theme`, and `github-pages`

**Content Structure**:
- Blog posts: `_posts/` directory with naming format `YEAR-MONTH-DAY-title.markdown`
- Pages: Root-level `.markdown` or `.html` files (e.g., `about.markdown`)
- Front matter: YAML metadata at top of each content file defining layout, title, permalink, etc.

## Development Commands

### Initial Setup
```bash
# Configure Bundler to install gems locally (avoids system-wide installation issues)
bundle config set --local path 'vendor/bundle'

# Install dependencies
bundle install
```

**Important**: Dependencies are installed to `vendor/bundle/` which is excluded from git. This avoids permission issues with system Ruby.

### Local Development
```bash
# Serve site locally with auto-regeneration
bundle exec jekyll serve

# Serve with drafts and future posts
bundle exec jekyll serve --drafts --future

# Serve on a different port
bundle exec jekyll serve --port 4001
```

The site will be available at http://localhost:4000 (or configured port). Changes to most files trigger auto-regeneration, except `_config.yml` which requires a server restart.

### Build
```bash
# Build site to _site/ directory
bundle exec jekyll build

# Build with production environment
JEKYLL_ENV=production bundle exec jekyll build

# Build with verbose output (helpful for debugging)
bundle exec jekyll build --verbose
```

## Troubleshooting

### SSL Certificate Errors
If you encounter SSL certificate errors when downloading the remote theme locally:
- This is a known macOS/Ruby SSL configuration issue
- The site will still build and deploy correctly on GitHub Pages
- To fix locally: https://bundler.io/v2.0/guides/rubygems_tls_ssl_troubleshooting_guide.html
- Workaround: Let GitHub Pages handle the build (push changes and let CI/CD build it)

### Bundle Install Requires Sudo
If `bundle install` asks for sudo:
1. Run: `bundle config set --local path 'vendor/bundle'`
2. Run: `bundle install` again

### Config Changes Not Showing
If changes to `_config.yml` don't appear:
- Stop the Jekyll server (Ctrl+C)
- Restart with `bundle exec jekyll serve`

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

## Theme Customization

The Just the Docs theme is configured in `_config.yml` with the following features enabled:

**Search**: Enabled by default, searches all content
**Navigation**: Automatically generated from pages with front matter
**Back to top button**: Enabled on all pages
**Footer**: Customized with family copyright info
**SEO**: Jekyll SEO tag plugin included for better search engine visibility

For additional customization options, see: https://just-the-docs.com/docs/configuration/

### Common Customizations
- **Color schemes**: Set `color_scheme` in `_config.yml` (options: nil, dark, or custom)
- **Navigation order**: Add `nav_order: 1` to page front matter
- **Hide pages from nav**: Add `nav_exclude: true` to page front matter
- **Google Analytics**: Uncomment `ga_tracking` in `_config.yml` and add your tracking ID
