# Comprehensive Implementation Plan: Sunkissed Band Website

## 1. Project Structure

```
website-test/
├── public/
│   └── logo.png                 (your logo image)
├── src/
│   ├── components/
│   │   ├── Navigation.astro     (top nav bar)
│   │   ├── Hero.astro           (landing section)
│   │   ├── About.astro          (band bio section)
│   │   ├── Music.astro          (streaming links section)
│   │   └── Contact.astro        (social + newsletter section)
│   ├── layouts/
│   │   └── Layout.astro         (base layout with global styles)
│   ├── pages/
│   │   └── index.astro          (main single-page site)
│   └── styles/
│       └── global.css           (CSS variables, resets, utilities)
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

## 2. Design System

### Color Palette (extracted from logo)
```css
--color-cream: #FAF7F2        /* Warm off-white background */
--color-sun-yellow: #FDB927   /* Golden yellow from sun */
--color-sun-orange: #F7931E   /* Warm orange from sun */
--color-red: #ED1C24          /* Red from lettering */
--color-charcoal: #2B2B2B     /* Dark text */
--color-gray: #6B6B6B         /* Secondary text */
```

### Typography
- **Primary Font**: Inter or DM Sans (clean, modern sans-serif via Google Fonts)
- **Heading sizes**:
  - H1: 3.5rem (mobile: 2.5rem) - for hero title
  - H2: 2.5rem (mobile: 2rem) - for section headings
  - H3: 1.5rem - for subsections
- **Body**: 1.125rem (18px) - comfortable reading size
- **Font weights**: 400 (regular), 600 (semi-bold), 700 (bold)

### Spacing System
- Container max-width: 1200px
- Section padding: 5rem vertical (mobile: 3rem)
- Component spacing: 1.5rem, 2rem, 3rem increments
- Border radius: 12px for cards/buttons (subtle roundness)

## 3. Page Sections (Single-Page Site)

### A. Navigation Bar
- **Position**: Sticky at top
- **Contents**:
  - Logo (small version, left side)
  - Nav links: About, Music, Contact (right side)
  - Mobile: Hamburger menu
- **Style**: Semi-transparent cream background with backdrop blur, thin bottom border

### B. Hero Section
- **Layout**: Full viewport height, centered content
- **Contents**:
  - Large logo image (your sun logo)
  - Tagline/subtitle: "Indie Rock from [City]" (placeholder text)
  - Primary CTA button: "Listen Now" (links to #music section)
  - Secondary CTA button: "Latest Video" (placeholder link)
- **Style**: Cream background, maybe subtle gradient from cream to light orange at bottom
- **Visual**: Logo dominates, clean space around it

### C. About Section
- **Layout**: Centered text block, max-width 800px
- **Contents**:
  - Section heading: "About"
  - Band bio (placeholder: 2-3 paragraphs of Lorem ipsum)
  - Optional: Band photo placeholder (logo for now)
- **Style**: White background (contrast from hero), generous padding

### D. Music Section
- **Layout**: Grid of music platform cards
- **Contents**:
  - Section heading: "Listen"
  - 4-6 cards for streaming platforms:
    - Spotify (with Spotify green accent)
    - Apple Music (with Apple Music red accent)
    - Bandcamp (with Bandcamp blue accent)
    - YouTube (with YouTube red accent)
    - Soundcloud (optional)
    - Each card: Platform icon/logo, "Listen on [Platform]" text, link
  - Below cards: Featured video section
    - Heading: "Latest Video"
    - Embedded YouTube video (placeholder iframe)
- **Style**: Cream background, cards with white bg, subtle hover effects (lift + shadow)

### E. Contact Section (Footer)
- **Layout**: Two-column on desktop, stacked on mobile
- **Contents**:
  - **Left column**:
    - Heading: "Stay Connected"
    - Social media icons/links (Instagram, Facebook, Twitter, TikTok - placeholder links)
    - Email: hello@sunkissedband.com (placeholder)
  - **Right column**:
    - Newsletter signup
    - Heading: "Get Updates"
    - Email input field + Submit button
    - Note: "We'll use a simple mailto link or Formspree for now, can integrate real service later"
- **Style**: Charcoal background, cream text (inverted), logo in background as watermark

## 4. Components Detail

### Navigation.astro
- Responsive navbar
- Smooth scroll to section anchors
- Active link highlighting
- Mobile hamburger menu with slide-in panel
- JavaScript for scroll behavior and mobile toggle

### Hero.astro
- Full viewport height container
- Centered flex layout
- Logo image with fade-in animation
- CTA buttons with hover states (scale + color shift)

### About.astro
- Simple content container
- Typography-focused
- Optional decorative element (wavy divider line in orange)

### Music.astro
- CSS Grid (3 columns on desktop, 2 on tablet, 1 on mobile)
- Card component with:
  - Icon/logo placeholder
  - Platform name
  - Hover effect: subtle lift (-2px) and shadow
  - Link wraps entire card
- YouTube embed (responsive 16:9 ratio container)

### Contact.astro
- Two-column flexbox layout
- Social icons: Simple SVG icons or icon font
- Form styling: Rounded inputs, orange submit button
- For now: Form uses Formspree (free service) or simple mailto

## 5. Technical Implementation Details

### Astro Setup
```bash
npm create astro@latest .
# Choose: Empty template
# TypeScript: Yes (strict)
# Install dependencies: Yes
```

### Dependencies
```json
{
  "dependencies": {
    "astro": "latest"
  }
}
```

### CSS Approach
- CSS Custom Properties (variables) in global.css
- Scoped component styles within .astro files
- Mobile-first responsive design
- Breakpoints: 640px (tablet), 1024px (desktop)

### Fonts
- Google Fonts: Import Inter or DM Sans in Layout.astro
- Font loading optimization via Astro font optimization

### Responsive Images
- Logo: Optimized PNG or SVG
- Use Astro's Image component for optimization

### Animations
- Subtle CSS transitions (0.3s ease)
- Scroll-triggered fade-ins (using Intersection Observer in JavaScript)
- Keep animations minimal and smooth

## 6. Content Placeholders

Since you don't have content yet, I'll use:
- **Logo**: Your provided logo image for all image placeholders
- **Text**: Short, realistic placeholder text (not Lorem ipsum walls)
- **Links**: # anchors for sections, https://spotify.com etc for platforms
- **Videos**: Generic YouTube embed example
- **Email**: Formspree free tier or simple mailto:hello@sunkissedband.com

## 7. Deliverables

After implementation, you'll have:
1. ✅ Fully functional single-page website
2. ✅ Responsive design (mobile, tablet, desktop)
3. ✅ Clean, modern aesthetic matching your logo
4. ✅ Easy-to-edit content (all text in component files)
5. ✅ Ready to deploy to Netlify/Vercel/GitHub Pages
6. ✅ README with instructions for:
   - Running locally (`npm run dev`)
   - Building for production (`npm run build`)
   - Deploying
   - Where to update content

## 8. Future Expansion (Not in this build, but easy to add)

- Shows/Tour Dates section (separate component)
- Photo Gallery with lightbox
- Music player integration
- Blog/News section
- Merch store integration

---

**Does this plan look good? Any sections you want to add, remove, or modify before I start building?**
