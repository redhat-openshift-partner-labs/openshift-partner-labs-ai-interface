# Codebase Structure

## Root Level
- **package.json** - Dependencies and scripts
- **tsconfig.json** - TypeScript configuration
- **eslint.config.mjs** - ESLint configuration
- **prettier.config.cjs** - Prettier configuration
- **tailwind.config.ts** - Tailwind CSS configuration
- **next.config.ts** - Next.js configuration
- **CLAUDE.md** - Project instructions for AI assistants

## Source Directory (`src/`)

### Core Application
- **app/** - Next.js App Router pages and layout
  - `layout.tsx` - Root layout with providers
  - `page.tsx` - Main playground page
  - `globals.css` - Global styles

### State Management
- **store.ts** - Zustand store with PlaygroundStore interface

### Type Definitions
- **types/playground.ts** - All TypeScript interfaces and types

### API Layer
- **api/** - API routes and client functions
  - `routes.ts` - Centralized API route definitions
  - `playground.ts` - Playground API functions

### Components Architecture
- **components/ui/** - Reusable UI components (shadcn/ui based)
  - `button.tsx`, `dialog.tsx`, `select.tsx` etc.
  - **typography/** - Text rendering components
  - **tooltip/** - Tooltip components
  - **icon/** - Icon system

- **components/playground/** - Main application components
  - **ChatArea/** - Chat interface and message display
    - **Messages/** - Message rendering and multimedia
    - **ChatInput/** - User input handling
  - **Sidebar/** - Agent selection and session management
    - **Sessions/** - Session CRUD operations

### Custom Hooks
- **hooks/** - Reusable React hooks
  - `useAIStreamHandler.tsx` - AI response streaming
  - `useSessionLoader.tsx` - Session loading logic
  - `useChatActions.ts` - Chat operations

### Utilities
- **lib/** - Utility functions
  - `utils.ts` - General utilities
  - `modelProvider.ts` - Model provider logic
  - `constructEndpointUrl.ts` - URL building
  - `audio.ts` - Audio handling utilities

## Key Architectural Patterns
- **Component co-location** - Related files grouped in folders
- **Barrel exports** - index.ts files for clean imports
- **Separation of concerns** - API, state, UI, and business logic separated
- **Custom hooks** - Reusable stateful logic
- **Type-first** - Comprehensive TypeScript interfaces