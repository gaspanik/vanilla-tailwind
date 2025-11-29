# Project Context: vanilla-tailwind

## Overview
This project is a lightweight frontend web application using **Vanilla JavaScript**, **Tailwind CSS (v4)**, and **Vite**. It employs **Lucide** for iconography and **Biome** for fast linting and formatting.

## Tech Stack
-   **Build Tool:** [Vite](https://vitejs.dev/)
-   **CSS Framework:** [Tailwind CSS](https://tailwindcss.com/) (via PostCSS)
-   **Icons:** [Lucide](https://lucide.dev/)
-   **Linter/Formatter:** [Biome](https://biomejs.dev/)

## Key Files & Structure
-   `index.html`: Main entry point.
-   `src/main.js`: JavaScript entry point. Handles icon initialization and global logic.
-   `src/style.css`: Main stylesheet, imports Tailwind.
-   `biome.json`: Configuration for Biome.
-   `postcss.config.js`: PostCSS configuration for Tailwind.

## Development Workflow

### Scripts
Run these using `pnpm` (preferred) or `npm`:

-   `pnpm dev`: Start the local development server.
-   `pnpm build`: Build the project for production.
-   `pnpm preview`: Preview the production build locally.
-   `pnpm check`: Run Biome to check and format code (lint + format).
-   `pnpm format`: Format code using Biome.
-   `pnpm lint`: Lint code using Biome.

## Coding Conventions

### Icons (Lucide)
To add an icon:
1.  **HTML**: Add an element with the `data-lucide` attribute.
    ```html
    <i data-lucide="square-dashed"></i>
    ```
2.  **JavaScript**: Import the icon in `src/main.js` and register it.
    ```javascript
    import { createIcons, SquareDashed } from 'lucide';

    createIcons({
      icons: { SquareDashed }
    });
    ```

### Styling
-   Use Tailwind utility classes directly in HTML.
-   **Syntax**: Strictly use Tailwind CSS v4 syntax. Avoid obsolete or deprecated v3 patterns.
-   Tailwind v4 is configured via PostCSS.

### Code Quality
-   The project enforces 2-space indentation and single quotes for JavaScript via Biome.
-   Always run `pnpm check` before committing.
