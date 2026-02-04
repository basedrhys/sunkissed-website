# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page band website for the indie rock band Sunkissed, built with Astro 4.x. The site is fully static with no JavaScript framework dependencies, focusing on fast performance and simple deployment.

## Development Commands

```bash
# Install dependencies
npm install

# Start dev server (http://localhost:4321)
npm run dev
# or
npm start

# Type-check and build for production
npm run build

# Preview production build locally
npm run preview

# Run Astro CLI commands
npm run astro
```

## Architecture

### Page Structure
The main page (`index.astro`) uses shared components, while **aesthetic variation pages** are self-contained standalone files with their own styles.

**Main Page Components:**
- Navigation (sticky header)
- SocialSidebar (fixed right-side floating social icons)
- Hero (landing section)
- About (band bio)
- Music (streaming links + embedded video)
- Contact (social links + newsletter form)

### Aesthetic Variation Pages
The site includes 7 different aesthetic variations accessible via a style switcher:

| Route | File | Aesthetic | Key Features |
|-------|------|-----------|--------------|
| `/` | `index.astro` | Original | Uses shared components, warm sun-inspired colors |
| `/synthwave` | `synthwave.astro` | Retrofuturism/VHS | Chromatic aberration, neon grid, CRT scanlines, VHS tracking glitch |
| `/zine` | `zine.astro` | Editorial/Punk | Massive cutout typography, torn paper edges, B&W + red accent only |
| `/y2k` | `y2k.astro` | Acid Graphics | Chrome metallic text, morphing gradient blobs, acid lime/magenta |
| `/vintage` | `vintage.astro` | Psychedelic 70s | Concentric sun, multi-shadow stacking, halftone overlay |
| `/dreamy` | `dreamy.astro` | Aurora/Cosmic | Aurora borealis layers, star field, blur-reveal animation, holographic text |
| `/grunge` | `grunge.astro` | 90s Grunge | Noise overlay, scan lines, glitch effects, split typography |

**Typography by Page:**
- Synthwave: Orbitron + Rajdhani
- Zine: Playfair Display + Archivo Narrow + Special Elite
- Y2K: Rubik Mono One + Space Mono + Unbounded
- Vintage: Anton + Dela Gothic One + Josefin Sans
- Dreamy: Instrument Serif + Syne
- Grunge: Bebas Neue + Space Grotesk

Each aesthetic page is **self-contained** (imports only `socialLinks.js` data) and includes:
- Google Fonts in `<head>`
- Style switcher nav at top
- Hero, About, Music, Contact sections
- All CSS in scoped `<style>` block
- Mobile responsive breakpoints at 768px
- `@media (prefers-reduced-motion)` support

### Data Management
Social media and music platform links are **centrally managed** in `src/data/socialLinks.js`. This single source of truth is imported by:
- `SocialSidebar.astro` (displays all links in floating sidebar)
- `Music.astro` (displays music platforms only via `musicPlatforms` export)
- All aesthetic variation pages

When adding or updating social/music links, only edit `src/data/socialLinks.js`.

### Design System
All design tokens (colors, spacing, typography) are defined as CSS custom properties in `src/styles/global.css`:
- Colors are extracted from the band's logo (cream, sun yellow/orange, red, charcoal)
- Includes utility classes for containers, sections, buttons, and cards
- Fully responsive with mobile breakpoints at 640px and 768px

### Component Architecture
Components are Astro components (`.astro` files) that combine:
- Frontmatter for data imports and logic
- HTML template with Astro's JSX-like syntax
- Scoped `<style>` blocks (with some global styles in Layout.astro)

## TypeScript Configuration
- Uses Astro's strict TypeScript config
- JSX configured for React (even though React is not currently used)
- Type definitions in `src/env.d.ts`

## Deployment
The site is designed for static hosting on:
- Netlify (recommended)
- Vercel
- GitHub Pages
- Any static hosting provider

Build output goes to `dist/` directory.

## Newsletter Form
The contact forms use Formspree. The form action URL contains a placeholder `YOUR_FORM_ID` that should be replaced with an actual Formspree form ID. This appears in:
- `src/components/Contact.astro`
- All aesthetic variation pages (`synthwave.astro`, `zine.astro`, etc.)

## Key Files
- `src/pages/index.astro` - Main page entry point (uses components)
- `src/pages/*.astro` - Aesthetic variation pages (self-contained)
- `src/layouts/Layout.astro` - Base HTML layout with meta tags
- `src/data/socialLinks.js` - Central configuration for all external links
- `src/styles/global.css` - Design system and global styles
- `public/logo.png` - Band logo (used as favicon and in components)
- `public/cover_photo.jpeg` - Band photo used in About sections
