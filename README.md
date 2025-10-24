# Delgado Perez Family Site

Personal/family website hosted at [delgadoperez.family](https://delgadoperez.family)

## About

This is a Jekyll-based static site using the [Hydejack theme](https://hydejack.com/), deployed automatically to GitHub Pages.

## Development

### Prerequisites

- Ruby 3.1 or later
- Bundler

### Setup

```bash
# Install dependencies
bundle install
```

### Local Development

```bash
# Run local development server
bundle exec jekyll serve
```

Visit http://localhost:4000 to view the site. Changes auto-regenerate except for `_config.yml` (requires server restart).

### Build

```bash
# Build site to _site/ directory
bundle exec jekyll build
```

## Creating Content

### New Blog Post

Create a file in `_posts/` with the format `YYYY-MM-DD-title.markdown`:

```markdown
---
layout: post
title: "Your Post Title"
date: 2025-02-09 12:00:00 -0600
categories: category1 category2
---

Your content here...
```

### New Page

Create a `.markdown` file in the root directory:

```markdown
---
layout: page
title: "Page Title"
permalink: /page-url/
---

Your content here...
```

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `main` branch via GitHub Actions (see `.github/workflows/jekyll.yml`).
