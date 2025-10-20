# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Nuxtship is a SaaS landing page template built with Nuxt 4 and TailwindCSS. It's designed for startups, marketing websites, and landing pages. This is a port of the Astroship template to Nuxt.

**IMPORTANT: This project uses Bun as its package manager. Always use `bun` commands, never `npm`, `yarn`, or `pnpm`.**

## Development Commands

```bash
# Install dependencies
bun install

# Start dev server (http://localhost:3000)
bun run dev

# Build for production
bun run build

# Preview production build locally
bun run preview

# Generate static site
bun run generate
```

## Architecture

### Component Structure

The project uses a component-based architecture with Nuxt 4's auto-import feature:

- **Landing Components**: All reusable landing page components live in `components/landing/`
  - Components are auto-imported with the `Landing` prefix (e.g., `<LandingHero>`)
  - Key components: `Navbar.vue`, `Hero.vue`, `Features.vue`, `Cta.vue`, `Footer.vue`, `Pricing.vue`, `Contactform.vue`
  - Utility components: `Container.vue`, `Button.vue`, `Link.vue`, `Sectionhead.vue`, `Tick.vue`, `Logos.vue`

### Page Structure

Pages use the file-based routing system:
- `pages/index.vue` - Homepage composed of landing components
- `pages/about.vue` - About page
- `pages/contact.vue` - Contact page
- `pages/pricing.vue` - Pricing page

All pages use `definePageMeta({ layout: "landing" })` to apply the landing layout.

### Layout System

- `layouts/landing.vue` wraps pages with `<LandingNavbar>` and `<LandingFooter>`
- `app.vue` provides the root layout wrapper using `<NuxtLayout>` and `<NuxtPage>`

### Styling

- TailwindCSS for utility-first styling
- Custom CSS in `assets/css/main.css`
- Typography plugin enabled (`@tailwindcss/typography`)
- Custom font: Inter (extends default sans-serif stack)
- PostCSS with autoprefixer configured

### Icon System

Uses `nuxt-icon` module for icon management. Icons are configured in `app.config.ts`.

## Configuration Files

- `nuxt.config.ts` - Main Nuxt configuration (modules, CSS, PostCSS)
- `tailwind.config.ts` - TailwindCSS configuration with content paths and theme extensions
- `app.config.ts` - App-level configuration (currently just nuxt-icon settings)
- `tsconfig.json` - TypeScript configuration

## Key Nuxt 4 Conventions

- Components in `components/` are auto-imported
- Nested folder structure creates component prefixes (e.g., `components/landing/Hero.vue` becomes `<LandingHero>`)
- Pages use file-based routing
- Layouts are defined in `layouts/` and applied via `definePageMeta()`
- Composables would go in `composables/` (auto-imported)
- Server routes/API endpoints would go in `server/` (currently minimal)
