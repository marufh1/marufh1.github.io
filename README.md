# marufh1.github.io

Personal portfolio for **Maruf Hossain** — Full-Stack Software Engineer (ASP.NET Core, C#, SQL Server, React).

Live at: https://marufh1.github.io/

## Overview

A hand-built, dependency-free static site: semantic HTML5, one CSS file (custom properties for
theming, no framework), and a small vanilla-JS file for the theme toggle, mobile nav, scroll-spy,
and scroll-reveal animation. No build step, no bundler, no backend — it's served as-is by GitHub
Pages.

All content (roles, dates, education, projects, skills) is sourced directly from Maruf's CV. Nothing
about clients, metrics, or technologies is invented — see the "Content sourcing" note at the bottom.

## Project structure

```
index.html                    Single-page site (all sections)
404.html                      Custom not-found page
assets/
  css/styles.css              Design system + layout (light/dark theme via CSS custom properties)
  js/main.js                  Theme toggle, mobile nav, scroll-spy, reveal-on-scroll, footer year
  img/maruf-hossain.png       Portrait used in the About section
  resume/Maruf-Hossain-Resume.pdf   Downloadable CV (linked from the nav and Contact section)
favicon.svg                   "MH" monogram favicon
site.webmanifest              PWA manifest (name, icons, theme color)
robots.txt / sitemap.xml      SEO basics
.nojekyll                     Tells GitHub Pages to serve files as-is (skip Jekyll processing)
google79f367f2740c7176.html   Google Search Console site-verification file — do not remove
```

## Running locally

No install, no build. Any static file server works:

```bash
npx serve .
# or
python -m http.server 8000
```

Then open the printed local URL in a browser.

## Deployment (GitHub Pages)

This repo **is** `marufh1.github.io`, so GitHub Pages serves the `main`/`master` branch root
directly — there is nothing to build or publish separately. Push to the default branch and the
live site updates automatically within a minute or two.

Settings → Pages should have **Source: Deploy from a branch**, branch `master`, folder `/ (root)`.

## Updating content later

Everything lives in `index.html`, organized by `<section id="...">`:

| Section | id | What to edit |
|---|---|---|
| Hero | `#top` | Headline, supporting line, "Currently focused on" panel |
| About | `#about` | Bio paragraphs, "How I work" list |
| Experience | `#experience` | One `<article class="timeline-item">` per role |
| Selected Work | `#work` | One `<article class="work-card">` per case study |
| Skills | `#skills` | One `<div class="skill-card">` per capability group |
| Education | `#education` | One `<div class="edu-item">` per degree |
| Contact | `#contact` | One `<a class="contact-card">` per channel |

To update the résumé PDF: replace `assets/resume/Maruf-Hossain-Resume.pdf` with the new file
(keep the same filename so existing links keep working), and update the CV facts reflected in
Experience/Education/Skills/JSON-LD to match.

Structured data (JSON-LD `Person` schema) lives in a `<script type="application/ld+json">` block
in `<head>` — keep it in sync with the visible contact/experience info if either changes.

The favicon and OG/social preview image are generated from `assets/img/maruf-hossain.png` and
`favicon.svg` — replace those files (same names) to change them without touching HTML.

## Design system

- **Typography:** Space Grotesk (headings), Inter (body), IBM Plex Mono (labels/eyebrows) — all
  loaded from Google Fonts.
- **Theme:** dark-first, with a light theme and a "system" option, toggled via a `data-theme`
  attribute on `<html>` and persisted in `localStorage`. Colors are defined once as CSS custom
  properties in `assets/css/styles.css` and overridden per theme.
- **Motion:** section reveals and the hero's SVG system diagram are the only animations, and both
  respect `prefers-reduced-motion`.
- **Icons:** a small hand-drawn SVG sprite (`<symbol>` defs at the top of `index.html`) — no icon
  font, no external icon library.

## Content sourcing

Every fact on the site (employers, dates, degrees, technologies, project descriptions) is drawn
directly from Maruf's CV (`assets/resume/Maruf-Hossain-Resume.pdf`). No client names, metrics,
certifications, or technologies beyond what the CV states are included. Where the CV didn't
support a claim (e.g. numeric outcomes, live project links, testimonials), it was left out rather
than approximated.
