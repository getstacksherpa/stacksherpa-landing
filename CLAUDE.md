# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

StackSherpa landing page repository - a static website for an AI-powered code review tool for dbt engineers. The project consists of self-contained HTML landing pages with no build process or dependencies.

**Product tagline:** "Catch $500 mistakes in 10 seconds"

**Tech stack displayed:** FastAPI, PostgreSQL, Railway

## Development

This is a static HTML project with no build tools, package managers, or compilation steps.

### Running Locally

Open HTML files directly in a browser:
- `coming-soon-landing-page.html` - Simple gradient background variant
- `coming-soon-dark-theme.html` - Dark theme with animated stars background

For local development with live reload, use a simple HTTP server:
```bash
python3 -m http.server 8000
# Then visit http://localhost:8000/coming-soon-dark-theme.html
```

### Deployment

Static files can be deployed to any static hosting service (Vercel, Netlify, GitHub Pages, etc.). No build step required.

## File Structure

- **coming-soon-landing-page.html** - Simpler variant with gradient background, single email input
- **coming-soon-dark-theme.html** - Enhanced variant with animated stars, name + email inputs, tech stack display
- **blue_logo.png** - Main logo (300px width for landing page, 120px for dark theme)
- **favicon.svg** - Site favicon
- **Assets/StackSherpa-Brand/** - Brand asset library with organized subdirectories:
  - `01-primary-logos/` - Main logo variations
  - `02-alternate-colors/` - Color variants
  - `03-monochrome/` - Black and white versions
  - `04-banners/` - Banner graphics
  - `05-favicon/` - Favicon variations
  - `06-social-media/` - Social media assets
  - `07-reference/` - Reference materials

## Landing Page Variants

### Dark Theme (Primary - coming-soon-dark-theme.html)
- Background: Dark (#0a0e1a) with 100 animated twinkling stars
- Form: Name + Email inputs
- Features: "Powered by" tech stack section (FastAPI, PostgreSQL, Railway)
- Integration: Google Apps Script endpoint for waitlist submissions
- API endpoint: `https://script.google.com/a/macros/stacksherpa.ai/s/AKfycbw...`

### Simple Gradient (coming-soon-landing-page.html)
- Background: Blue gradient (#1a3a4d to #2C5F7C)
- Form: Email only
- Integration: Placeholder alert (needs email service connection)
- TODO comment: Connect to ConvertKit, Mailchimp, or email service

## Key Design Elements

**Brand colors:**
- Primary accent: #FF6B35 (orange)
- Dark backgrounds: #0a0e1a (dark theme), #1a3a4d to #2C5F7C (gradient theme)

**Typography:**
- Font: Inter (Google Fonts)
- Weights: 400, 500, 600, 700

**Responsive breakpoints:**
- Mobile: 480px and below
- Tablet: 768px and below

## Waitlist Form Integration

The dark theme variant uses a Google Apps Script webhook for collecting waitlist submissions. Form submissions send JSON payload with `name` and `email` fields using `no-cors` mode.

When modifying forms:
- Maintain the `no-cors` fetch mode (required for Google Apps Script)
- Alert users on success since response cannot be read in no-cors mode
- Provide user feedback via button state changes (disabled + text updates)

## Social Links

Currently placeholder links in code (commented out in dark theme):
- GitHub: `https://github.com/yourusername`
- Twitter/X: `https://twitter.com/yourusername`
- LinkedIn: `https://linkedin.com/in/yourprofile`

Update these when social profiles are ready.
