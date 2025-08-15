# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a SvelteKit web application called "Quokka Corner" - an interactive website about quokkas featuring educational content and a virtual pet game. The project is built with modern web technologies including Svelte 5, TailwindCSS 4, TypeScript, and uses Bun as the runtime.

## Development Commands

### Core Development
```bash
# Start development server
bun run dev

# Start development server and open in browser
bun run dev -- --open

# Build for production
bun run build

# Preview production build
bun run preview
```

### Code Quality
```bash
# Run all linting and formatting checks
bun run lint

# Format all code
bun run format

# Type checking with Svelte
bun run check

# Type checking with file watching
bun run check:watch
```

### Package Management
```bash
# Install dependencies
bun install

# Sync SvelteKit generated files
bun run prepare
```

## Project Architecture

### Directory Structure
- `src/` - Main source code directory
  - `routes/` - SvelteKit file-based routing
    - `+page.svelte` - Homepage with quokka facts and interactive elements
    - `+layout.svelte` - Root layout component with global styling
    - `quokka/` - Virtual pet game route (hidden feature)
    - `status/` - Conservation status information page
  - `components/` - Reusable Svelte components
    - `Banner.svelte` - Top banner linking to Hack Club Zoo
    - `Navbar.svelte` - Navigation component with dynamic routing
    - `QuokkaIllustration.svelte` - Interactive quokka illustration for pet game
  - `lib/` - Shared utilities and assets
    - `images/` - Static image assets
  - `app.html` - HTML template
  - `app.css` - Global styles with TailwindCSS
  - `app.d.ts` - TypeScript global type definitions

### Key Features Architecture

#### Interactive Fact System
- Located in the main page (`+page.svelte`)
- Cycles through quokka facts with state management
- Unlocks hidden "quokka" route after viewing all facts
- Uses browser localStorage to persist secret unlock state

#### Virtual Pet Game
- Hidden route at `/quokka` (unlocked after viewing all facts)
- Complex state management with multiple stats (happiness, hunger, energy)
- Real-time updates with interval-based degradation
- Persistent state using localStorage
- Interactive animations and mood system

#### Navigation System
- Dynamic navbar that shows/hides routes based on current page and unlock state
- Conditional rendering based on localStorage state for hidden features
- Responsive design with mobile-first approach

### Technology Stack

#### Frontend Framework
- **SvelteKit**: Full-stack web framework with file-based routing
- **Svelte 5**: Component framework with modern runes API (`$state`, `$derived`, `$props`)
- **TypeScript**: Full type safety across the application

#### Styling & UI
- **TailwindCSS 4**: Utility-first CSS framework with custom configuration
- **Iconify**: Icon system with TailwindCSS integration
- **Custom fonts**: Hack Club's Phantom Sans for banner
- **Responsive design**: Mobile-first approach with breakpoints

#### Development Tools
- **ESLint**: Linting with TypeScript and Svelte support
- **Prettier**: Code formatting with Svelte and TailwindCSS plugins
- **Vite**: Build tool and dev server
- **Bun**: JavaScript runtime and package manager

## Configuration Files

### Build & Development
- `vite.config.ts` - Vite configuration with SvelteKit and TailwindCSS plugins
- `svelte.config.js` - SvelteKit configuration with auto adapter
- `tsconfig.json` - TypeScript configuration extending SvelteKit defaults

### Code Quality
- `eslint.config.js` - Modern ESLint flat config with TypeScript and Svelte support
- `.prettierrc` - Prettier configuration with custom rules for this project:
  - Uses tabs instead of spaces
  - Single quotes preferred
  - No trailing commas
  - 100 character print width
  - Svelte and TailwindCSS plugin integration

### Package Management
- `package.json` - All dependencies are in devDependencies (SvelteKit pattern)
- `bun.lock` - Bun lockfile for dependency resolution
- `.npmrc` - NPM configuration

## Development Notes

### State Management Patterns
- Uses Svelte 5's modern runes API (`$state`, `$derived`, `$props`)
- LocalStorage integration for persistence across sessions
- Real-time updates using intervals and reactive statements

### Styling Approach
- TailwindCSS utility classes throughout
- Custom color palette with warm earth tones (`#F1E8DB`, `#B5A181`)
- Responsive grid layouts and flexbox patterns
- Custom animations and transitions

### Hidden Features
- The `/quokka` virtual pet route is unlocked by cycling through all facts on the homepage
- Secret URL parameter (`/status?secret=true`) also unlocks the hidden route
- localStorage key `quokkaSecret` controls visibility of hidden navigation

### External Integrations
- Links to Hack Club Zoo (https://zoo.hackclub.com)
- Custom banner component with Hack Club branding
- Uses external font resources from Hack Club assets

## Testing & Debugging

The project currently doesn't have a formal testing setup, but you can:
- Use `bun run check` for TypeScript validation
- Use `bun run lint` for code quality checks
- Use browser dev tools for debugging the pet game state management
- Check localStorage in browser for persistence debugging (keys: `quokkaSecret`, `quokkaPet`)
