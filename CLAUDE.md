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
The main page (`index.astro`) is a **self-contained** standalone file with a bold psychedelic 70s aesthetic. It includes all content and styles inline without using shared components.

**Main Page Sections:**
- Hero (landing section with animated logo badge)
- About (full band bio with all 4 paragraphs)
- Music (streaming platform links + YouTube video embed)
- Contact (social links, email, newsletter form)

**Main Page Aesthetic:**
- Typography: Anton + Dela Gothic One + Josefin Sans
- Colors: Psychedelic orange, electric purple, acid yellow, hot coral, burnt umber, cream paper
- Effects: Halftone overlay, animated concentric sun, multi-shadow stacking, spinning starburst

### Unlisted Page
There is one unlisted aesthetic variation page kept for potential future use:

| Route | File | Aesthetic | Key Features |
|-------|------|-----------|--------------|
| `/zine` | `zine.astro` | Editorial/Punk | Massive cutout typography, torn paper edges, B&W + red accent only |

This page is **not linked** from the main site but remains accessible directly via URL.

**Zine Page Typography:** Playfair Display + Archivo Narrow + Special Elite

### Data Management
Social media and music platform links are **centrally managed** in `src/data/socialLinks.js`. This single source of truth is imported by:
- `index.astro` (main page)
- `zine.astro` (unlisted page)
- Legacy components (SocialSidebar.astro, Music.astro) - no longer used by main page

When adding or updating social/music links, only edit `src/data/socialLinks.js`.

### Legacy Components
The following components exist but are **no longer used** by the main page (kept for reference):
- `Navigation.astro` - Sticky header navigation
- `SocialSidebar.astro` - Fixed right-side floating social icons
- `Hero.astro` - Landing section
- `About.astro` - Band bio
- `Music.astro` - Streaming links + video
- `Contact.astro` - Social links + newsletter form

### Design System
All design tokens (colors, spacing, typography) are defined as CSS custom properties in `src/styles/global.css`:
- Colors are extracted from the band's logo (cream, sun yellow/orange, red, charcoal)
- Includes utility classes for containers, sections, buttons, and cards
- Fully responsive with mobile breakpoints at 640px and 768px

Note: The main page defines its own CSS variables inline rather than using global.css.

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
- `src/pages/index.astro`
- `src/pages/zine.astro`

## Key Files
- `src/pages/index.astro` - Main page (self-contained with vintage/psychedelic aesthetic)
- `src/pages/zine.astro` - Unlisted zine aesthetic page (for future use)
- `src/layouts/Layout.astro` - Base HTML layout with meta tags (used by legacy components)
- `src/data/socialLinks.js` - Central configuration for all external links
- `src/styles/global.css` - Design system and global styles (legacy)
- `public/logo.png` - Band logo (used as favicon and in pages)
- `public/cover_photo.jpeg` - Band photo used in About sections
