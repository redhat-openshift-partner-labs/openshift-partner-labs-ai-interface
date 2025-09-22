# Code Style & Conventions

## General Conventions
- **TypeScript strict mode** enabled
- **ES2017** target with modern ES features
- **Functional components** with React hooks
- **Interface-based** type definitions

## Code Formatting (Prettier)
- **Single quotes** for strings
- **No semicolons** (semi: false)
- **No trailing commas** (trailingComma: 'none')
- **Tailwind CSS plugin** for class sorting
- Targets: `./src/**/*.{js,ts,jsx,tsx}`

## Naming Conventions
- **PascalCase** for components and interfaces
- **camelCase** for functions, variables, and methods
- **kebab-case** for file names when containing multiple words
- **Index files** for clean imports (index.ts exports)

## File Structure Patterns
- **Barrel exports** via index.ts files
- **Co-located** related files in component folders
- **Separation** of types, hooks, components, and API logic
- **Absolute imports** using `@/*` path mapping

## Component Patterns
- **Functional components** with TypeScript
- **Props interfaces** defined per component
- **Custom hooks** for reusable logic
- **Zustand store** for global state management
- **Conditional rendering** with early returns

## TypeScript Patterns
- **Strict typing** with interfaces
- **Utility types** for transformations
- **Enum-like** constants objects
- **Generic types** where appropriate
- **Type exports** from dedicated type files

## Import Organization
- External dependencies first
- Internal utilities and types
- Components last
- Relative imports at the end