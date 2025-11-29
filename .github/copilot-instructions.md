# vanilla-tailwind: AI Coding Agent Instructions

## Project Overview

A minimal, modern frontend starter using **Vite + Tailwind CSS + Lucide Icons**. The codebase is intentionally simple: single HTML file, minimal JavaScript (only icon initialization), and one CSS file with Tailwind imports. No bundled components or complex architectures.

## Architecture

### File Structure
```
index.html           # Single entry point with Tailwind utility classes
src/
  main.js           # Only icon initialization (Lucide)
  style.css         # Single import: @import "tailwindcss"
postcss.config.js   # Handles Tailwind CSS compilation
biome.json          # Code formatting & linting rules
```

### Technology Stack
- **Build**: Vite (configured via package.json scripts)
- **Styling**: Tailwind CSS v4.1+ with PostCSS
- **Icons**: Lucide (ES module import + `createIcons()` initialization)
- **Linting/Formatting**: Biome 2.3.8+

## Key Developer Workflows

### Development
- `pnpm dev` - Start Vite dev server (http://localhost:5173)
- `pnpm build` - Production build to `dist/`
- `pnpm preview` - Preview built output locally

### Code Quality
- `pnpm format` - Apply Biome formatting (2-space indents, 80-char lines)
- `pnpm lint` - Check & auto-fix linting issues
- `pnpm check` - Combined format + lint in one command
- `biome migrate --write` - Update Biome config to latest schema

**Biome Configuration** (biome.json):
- 2-space indentation, LF line endings
- Line width: 80 characters
- HTML attributes: auto positioning
- Recommended lint rules enabled
- Ignores: `dist/` directory

## Critical Patterns

### Icon Implementation (Lucide)
Icons are **NOT automatically rendered**. Three-step process required:

1. **HTML**: Place `<i data-lucide="icon-name"></i>` placeholder
2. **JavaScript**: Import icon from lucide and pass to `createIcons()`
3. **Result**: SVG replaces the placeholder

**Example** (current state):
```html
<!-- index.html -->
<i data-lucide="square-dashed"></i>
```
```javascript
// src/main.js
import { createIcons, SquareDashed } from 'lucide'
createIcons({ icons: { SquareDashed } })
```

**When adding new icons**:
- Add icon name to `data-lucide` attribute
- Import corresponding camelCase export from 'lucide'
- Register in `createIcons()` object

### Styling Approach
- **Tailwind-first**: Use utility classes directly in HTML (no custom CSS)
- **No CSS-in-JS**: All styling via `class` attributes
- **Single CSS file**: `src/style.css` contains only `@import "tailwindcss"`
- **Custom styles rare**: If needed, add to `src/style.css` before/after import

**Tailwind CSS v4 Syntax**:
Use modern v4 utilities.
- ✅ **v4**: Use the latest Tailwind CSS v4 features and utility classes.
- ❌ **Legacy**: Avoid deprecated patterns or obsolete configuration methods from v3.
- Reference: https://tailwindcss.com/docs/upgrade-guide

### HTML Structure
- Single semantic div wrapper for layout
- Tailwind flexbox utilities for alignment (e.g., `flex flex-col justify-center items-center`)
- Simple, flat structure—no component files

## Conventions

### Naming & Formatting
- **File extensions**: `.html`, `.js`, `.css` only
- **Element naming**: Use semantic HTML (`<h1>`, `<p>`, `<div>`)
- **Icon names**: Use kebab-case in `data-lucide` (e.g., "square-dashed", "home")
- **Lucide imports**: Use PascalCase matching the icon's camelCase export

### When to Extend
- **New pages**: Add inline to `index.html` (no multi-page routing yet)
- **Icons**: Follow pattern above—always init via `createIcons()` in `main.js`
- **Styles**: Add utilities in HTML; custom CSS only if truly needed

## Common Tasks

### Add Icon to Existing Content
```javascript
// 1. Import new icon
import { createIcons, Home, Plus } from 'lucide'  // Add icon name

// 2. Register it
createIcons({ icons: { Home, Plus } })

// 3. Use in HTML
<i data-lucide="plus"></i>
```

### Change Styling
- Edit `class` attribute directly in HTML (Tailwind utilities)
- Avoid creating `.css` files for layout/color changes
- Reference: https://tailwindcss.com/docs/utility-first

### Code Quality Issues
- Run `pnpm check` to fix formatting/linting automatically
- If errors persist, check biome.json rules align with your intent
- Biome enforces: trailing commas, semicolon omission, double-quoted JSX

## External References

- **Vite**: https://vitejs.dev/ (dev server, build tool)
- **Tailwind CSS**: https://tailwindcss.com/docs/utility-first
- **Lucide Icons**: https://lucide.dev/guide/packages/lucide#with-esmodules
- **Biome**: https://biomejs.dev/ (config format in `biome.json`)

## Project Philosophy

This starter intentionally avoids framework complexity (React, Vue, etc.). Modifications should maintain this simplicity:
- Keep HTML minimal and readable
- Use Tailwind utilities—don't duplicate styling
- Only add scripts when truly needed (like icon initialization)
