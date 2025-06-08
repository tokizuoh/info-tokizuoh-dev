# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal portfolio website built with SvelteKit and deployed as a static site. The site displays blog posts, links, highlights, and personal information for tokizuoh, a software engineer in Japan.

## Architecture

- **Framework**: SvelteKit with static adapter for deployment
- **Data Source**: JSON files in `src/data/` containing blog post metadata
- **Components**: Modular Svelte components in `src/routes/` for different sections
- **Styling**: Component-scoped CSS with global styles in the main page component
- **Build Target**: Static site generation for hosting

## Key Components

- `+page.svelte`: Main page layout and global styles
- `Posts.svelte`: Renders blog posts from JSON data with date formatting and source badges
- Component architecture supports multiple blog sources (Zenn, Hatena Blog)

## Development Commands

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Lint code (Prettier + ESLint)
npm run lint

# Format code
npm run format
```

## Data Management

Blog posts are stored in `src/data/latest_posts.json` with the following structure:
```json
{
  "publishedAt": "ISO date string",
  "source": "zenn|hatena",
  "title": "Post title",
  "url": "Full URL to post"
}
```

The Posts component automatically formats dates for Japanese locale and maps source identifiers to display names.