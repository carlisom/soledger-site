# Soledger — Marketing Site

Static marketing site for the Soledger iOS app. Built with Jekyll so nav and footer are shared across all pages. Deployed on GitHub Pages.

## Setup

### Prerequisites

Install Ruby and Bundler if you don't have them:

```bash
gem install bundler
```

### Install dependencies

```bash
bundle install
```

### Run locally

```bash
bundle exec jekyll serve
```

Then open [http://localhost:4000](http://localhost:4000). Liquid tags render and the server reloads on file changes.

> **Note:** Opening `.html` files directly in a browser still works for quick visual checks, but Liquid tags (`{% include %}`, `{{ page.title }}`) will not render — you'll see raw template syntax. Use `jekyll serve` to see the real output.

### Match GitHub Pages exactly

The `Gemfile` pins the `github-pages` gem, which locks Jekyll and all plugins to the same versions GitHub uses. This ensures local output is identical to what gets deployed.
