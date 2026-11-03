# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page band website for indie rock band Sunkissed, built with Astro 4.x. Fully static with no JavaScript framework dependencies.

## Development Commands

```bash
npm install          # Install dependencies
npm run dev          # Start dev server (http://localhost:4321)
npm run build        # Type-check and build for production
npm run preview      # Preview production build locally
```

**Note:** The dev server is typically already running. Do not start it automatically.

## Architecture

### Main Page
`src/pages/index.astro` is **self-contained** with all content and styles inline (no shared components).

**Sections:** Hero → About → Music → Contact

**Aesthetic:**
- Typography: Anton + Dela Gothic One + Josefin Sans
- Colors: Psychedelic orange, electric purple, acid yellow, hot coral, burnt umber, cream
- Effects: Halftone overlay, animated concentric sun, multi-shadow stacking, spinning starburst

### Unlisted Pages
These pages are **not linked** from the main site but accessible directly via URL:

| Route | File | Description |
|-------|------|-------------|
| `/zine` | `zine.astro` | Editorial/punk aesthetic (B&W + red, torn paper edges) |
| `/hero-original` | `hero-original.astro` | Original hero layout variation |
| `/hero-top-title` | `hero-top-title.astro` | Hero with title at top |

### Data Management
Social media and music platform links are **centrally managed** in `src/data/socialLinks.js`. When adding or updating links, only edit this file.

Exports:
- `socialLinks` - All links with name, url, color, icon SVG path, ariaLabel
- `musicPlatforms` - Filtered: Bandcamp, Spotify, Apple Music, YouTube
- `socialMedia` - Filtered: Instagram, TikTok

### Legacy Components (Unused)
Components in `src/components/` are **no longer used** by the main page but kept for reference:
Navigation, SocialSidebar, Hero, About, Music, Contact

### Design System
`src/styles/global.css` defines CSS custom properties (colors, spacing, typography) but the main page defines its own variables inline.

## Newsletter Form
The signup form in `src/pages/index.astro` posts to the band's Kit (kit.com) "fan list" landing page form (ID `10136084`), so signups land directly on the Kit list with double opt-in. A small script submits it in the background and shows the success message in place. `src/pages/zine.astro` still uses an older Netlify form.

## Key Files
- `src/pages/index.astro` - Main page (self-contained)
- `src/data/socialLinks.js` - Central link configuration
- `public/logo.png` - Band logo (favicon and pages)
- `public/cover_photo.jpeg` - Band photo for About sections
