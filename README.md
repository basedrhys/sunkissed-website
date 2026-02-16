# Sunkissed Band Website

**Live site:** [sunkissed.band](https://sunkissed.band)

A modern, clean website for the indie rock band Sunkissed. Built with Astro for fast performance and easy deployment.

## Getting Started

### Prerequisites

- Node.js 18+ installed on your machine
- A terminal/command line interface

### View the Website Locally

1. **Open your terminal** and navigate to this directory:
   ```bash
   cd /Users/rhyscompton/Documents/git/website-test
   ```

2. **Install dependencies** (if you haven't already):
   ```bash
   npm install
   ```

3. **Start the development server**:
   ```bash
   npm run dev
   ```

4. **Open your browser** and go to:
   ```
   http://localhost:4321
   ```

   The site will automatically reload when you make changes to the files.

5. **To stop the server**, press `Ctrl + C` in the terminal.

## Project Structure

```
website-test/
├── public/
│   └── logo.png              # Your band logo
├── src/
│   ├── components/
│   │   ├── Navigation.astro  # Top navigation bar
│   │   ├── Hero.astro        # Landing section
│   │   ├── About.astro       # Band bio section
│   │   ├── Music.astro       # Streaming links + video
│   │   └── Contact.astro     # Social links + newsletter
│   ├── layouts/
│   │   └── Layout.astro      # Base HTML layout
│   ├── pages/
│   │   └── index.astro       # Main page (combines all sections)
│   └── styles/
│       └── global.css        # Global styles and design system
└── package.json
```

## Customizing Content

### Update Band Information

**Edit `src/components/About.astro`** to change:
- Band bio and description
- Formation year
- Band story

**Edit `src/components/Hero.astro`** to change:
- Tagline/subtitle
- Button text and links

### Update Music Links

**Edit `src/components/Music.astro`** to:
- Update streaming platform URLs (search for `https://` in the file)
- Change the YouTube video embed (replace the video ID in the iframe src)
- Add or remove platforms from the `platforms` array

### Update Contact Information

**Edit `src/components/Contact.astro`** to:
- Update social media links (Instagram, Facebook, Twitter, TikTok)
- Change the email address
- Set up the newsletter form (instructions in the file)

### Change Colors

**Edit `src/styles/global.css`** to modify the color scheme:
- Colors are defined as CSS variables at the top of the file
- Current colors are extracted from your logo

### Replace the Logo

Replace `/public/logo.png` with your new logo file (keep the filename as `logo.png`, or update the references in the component files).

## Building for Production

When you're ready to deploy your site:

1. **Build the site**:
   ```bash
   npm run build
   ```

2. **Preview the production build**:
   ```bash
   npm run preview
   ```

The built files will be in the `dist/` folder.

## Deploying

### Deploy to Netlify (Recommended - Free)

1. Push your code to a Git repository (GitHub, GitLab, or Bitbucket)
2. Go to [netlify.com](https://netlify.com) and sign up
3. Click "Add new site" → "Import an existing project"
4. Connect your Git repository
5. Build settings (Netlify will auto-detect these):
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Click "Deploy site"

Your site will be live in a few minutes with a free `.netlify.app` URL. You can add a custom domain later.

### Deploy to Vercel (Also Free)

1. Push your code to a Git repository
2. Go to [vercel.com](https://vercel.com) and sign up
3. Click "New Project"
4. Import your Git repository
5. Vercel will auto-detect Astro and configure everything
6. Click "Deploy"

### Deploy to GitHub Pages (Free)

1. Push your code to a GitHub repository
2. Install the Astro GitHub Pages adapter
3. Follow the [Astro GitHub Pages guide](https://docs.astro.build/en/guides/deploy/github/)

## Newsletter Form (Netlify Forms)

The newsletter forms use Netlify Forms, which is automatically enabled when deploying to Netlify. No additional configuration needed—form submissions will appear in your Netlify dashboard under **Forms**.

## Other Commands

- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build locally
- `npm run astro` - Run Astro CLI commands

## Tech Stack

- **Astro** - Static site framework
- **HTML/CSS** - No JavaScript framework needed for this simple site
- **Inter Font** - Clean, modern typography from Google Fonts

## Support

For Astro documentation: [docs.astro.build](https://docs.astro.build)

## License

This website template is provided as-is for Sunkissed's use.
