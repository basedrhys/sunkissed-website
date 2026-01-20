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
This is a **single-page application** with all sections on one page (index.astro). The page is composed of:
- Navigation (sticky header)
- SocialSidebar (fixed right-side floating social icons)
- Hero (landing section)
- About (band bio)
- Music (streaming links + embedded video)
- Contact (social links + newsletter form)

### Data Management
Social media and music platform links are **centrally managed** in `src/data/socialLinks.js`. This single source of truth is imported by:
- `SocialSidebar.astro` (displays all links in floating sidebar)
- `Music.astro` (displays music platforms only via `musicPlatforms` export)

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
The contact form in `Contact.astro` uses Formspree. The form action URL contains a placeholder `YOUR_FORM_ID` that should be replaced with an actual Formspree form ID.

## Key Files
- `src/pages/index.astro` - Main page entry point
- `src/layouts/Layout.astro` - Base HTML layout with meta tags
- `src/data/socialLinks.js` - Central configuration for all external links
- `src/styles/global.css` - Design system and global styles
- `public/logo.png` - Band logo (used as favicon and in components)
