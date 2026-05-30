# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static marketing site for **Soledger** — an iOS app that tracks running shoe mileage via Apple Health. Built with **Jekyll** so nav and footer are shared via includes. Deployed on GitHub Pages.

## Previewing locally

```bash
bundle exec jekyll serve   # renders Liquid tags; visit http://localhost:4000
```

Do not open `.html` files directly in a browser — Liquid tags won't render without Jekyll.

## File structure

| File/Dir | Purpose |
|----------|---------|
| `_layouts/default.html` | Base layout — `<head>`, nav include, `{{ content }}`, footer include |
| `_includes/nav.html` | Shared nav (uses `page.is_home` to switch between anchor and full-path links) |
| `_includes/footer.html` | Shared footer (uses `page.is_home` and `page.contact_email`) |
| `index.html` | Main landing page (hero, features, FAQ, CTA) |
| `styles.css` | All styles — shared across every page |
| `support.html` | Support/troubleshooting page |
| `privacy.html` | Privacy policy |
| `terms.html` | Terms of service |
| `assets/app-icon.png` | App icon used in nav and `<link rel="icon">` |
| `_config.yml` | Jekyll config — title, url, excludes (`CLAUDE.md`, `README.md`, `plan/`, `Gemfile`, `Gemfile.lock`) |
| `Gemfile` | Pins `jekyll ~> 4.3` plus `webrick`, `csv`, `bigdecimal` |
| `README.md` | Human-readable setup guide — excluded from Jekyll build |
| `plan/` | Working docs excluded from build: `plan.md` (accuracy corrections), `go-live-checklist.md` (App Store launch steps), `screenshot.md` (screenshot guidance) |

## Page front matter

Each page declares its layout and metadata at the top:

```yaml
---
layout: default
title: "Page Title — Soledger"
description: "Meta description for SEO."
is_home: true          # only on index.html — controls anchor vs. full-path nav/footer links
contact_email: "soledger@pragmaticts.com"   # second email shown in footer Contact column
---
```

## Design system

All CSS custom properties are defined at the top of `styles.css`:

| Variable | Value | Role |
|----------|-------|------|
| `--bone` | `#f6f1ea` | Page background |
| `--paper` | `#fbf6ef` | Card/surface background |
| `--ink` | `#29211a` | Primary text & dark sections |
| `--ember` | `#c4633a` | Accent / CTA / replace-soon alert color |
| `--clay` | `#c4946b` | Secondary accent (eyebrows, feature numbers) |
| `--umber` | `#8a7a68` | Secondary/muted text |
| `--moss` | `#6b8a4f` | "Healthy" indicator color |

Fonts: **Manrope** (`--font-display`) for headings/body, **JetBrains Mono** (`--font-mono`) for labels, stats, and monospaced values. Both loaded from Google Fonts.

## Screenshot placeholders

The hero phone and the 3-column gallery currently show `.slot` placeholder divs. When screenshots are ready:

- **Hero**: Replace the `<div class="slot">...</div>` inside `.phone-screen` with:
  ```html
  <img src="assets/screenshots/home.png" alt="Soledger home screen" style="width:100%;height:100%;object-fit:cover" />
  ```
- **Gallery**: Replace each `.shot > .slot` with an `<img>` in the same style. Capture at native simulator resolution, portrait, no device frame. See `plan/screenshot.md` for the target simulator and recommended shots per slot.

## Coming-soon pattern

App Store badges and the "Get the app" nav button are currently wrapped in a `.coming-soon-wrap` / `.coming-soon-badge` overlay to mark the app as not yet live. When the app ships, follow `plan/go-live-checklist.md` to swap these out for real links across all four pages and remove the now-unused CSS.

## Responsive breakpoints

- `980px` — tablet: single-column hero, features stack, gallery goes 2-column
- `640px` — mobile: full single-column, `.hide-sm` nav links hidden

## Shared nav / footer pattern

Nav and footer live in `_includes/nav.html` and `_includes/footer.html`. Edit those files once — all pages pick up the change automatically via Jekyll's `{% include %}` tags.

## Legal pages

`privacy.html`, `terms.html`, and `support.html` all use the `.legal` layout class from `styles.css`. The `.toc` component renders a 2-column `<ol>` grid inside a card.
