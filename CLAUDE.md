# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Type
This is a Next.js application repository.

## Development Commands

### Core Development
- `npm run dev` - Start development server (usually on port 3000)
- `npm run build` - Build production application
- `npm run start` - Start production server
- `npm run lint` - Run ESLint for code quality checks
- `npm run lint:fix` - Auto-fix linting issues where possible

### Testing
- `npm test` - Run test suite
- `npm run test:watch` - Run tests in watch mode
- `npm run test:coverage` - Run tests with coverage report

### Type Checking (if TypeScript)
- `npm run type-check` or `npx tsc --noEmit` - Type check without building
- `npm run build` - Also performs type checking during build

## Architecture Overview

### Directory Structure
- `/pages` or `/app` - Next.js routing (depends on Pages Router vs App Router)
- `/components` - Reusable React components
- `/lib` - Utility functions and configurations
- `/public` - Static assets served directly
- `/styles` - CSS/styling files
- `/api` - API routes (in `/pages/api` or `/app/api`)

### Key Configuration Files
- `next.config.js/mjs` - Next.js configuration
- `tailwind.config.js` - Tailwind CSS configuration (if used)
- `tsconfig.json` - TypeScript configuration (if TypeScript)
- `.env.local` - Local environment variables
- `middleware.js/ts` - Next.js middleware for request processing

### Routing Architecture
- **Pages Router**: File-based routing in `/pages` directory
- **App Router**: New routing system in `/app` directory with layouts and nested routes
- Check which router is being used by looking for either `/pages` or `/app` directory

### State Management
Common patterns to look for:
- React Context + useReducer for global state
- Zustand, Redux Toolkit, or Jotai for complex state management
- SWR or TanStack Query for server state management

### Styling Approach
Check for:
- Tailwind CSS (`tailwind.config.js` present)
- CSS Modules (`.module.css` files)
- Styled Components or Emotion
- PostCSS configuration

## Development Workflow

### Before Making Changes
1. Run `npm run dev` to start development server
2. Run `npm run lint` to check for existing issues
3. If TypeScript: run type checking

### After Making Changes
1. Run `npm run lint` to verify code quality
2. Run `npm run build` to ensure production build works
3. Run tests if available: `npm test`

### Environment Variables
- Use `.env.local` for local development secrets
- Use `.env.example` as template for required environment variables
- Never commit actual secrets to version control

## Common Patterns

### API Routes
- Located in `/pages/api` (Pages Router) or `/app/api` (App Router)
- Export handler functions for different HTTP methods
- Use middleware for authentication, CORS, etc.

### Data Fetching
- `getServerSideProps` - Server-side rendering with fresh data
- `getStaticProps` - Static generation with build-time data
- `getStaticPaths` - Dynamic routes with static generation
- Client-side fetching with SWR, TanStack Query, or fetch/axios

### Component Organization
- Keep components focused and single-purpose
- Use TypeScript interfaces for prop types
- Co-locate component styles and tests when possible
- Use barrel exports (`index.ts`) for clean imports

## Performance Considerations
- Use Next.js Image component for optimized images
- Implement proper loading states for async operations
- Consider code splitting with dynamic imports
- Use Next.js built-in performance monitoring tools