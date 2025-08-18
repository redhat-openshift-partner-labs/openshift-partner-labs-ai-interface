# Development Guidelines

## Design Patterns

### State Management
- **Zustand store** (`src/store.ts`) for global state
- **Persistent state** for user preferences (selectedEndpoint)
- **Hydration handling** for SSR compatibility
- **Custom hooks** for complex state logic

### Component Architecture
- **Functional components** with TypeScript
- **Props interfaces** for every component
- **Barrel exports** via index.ts files
- **Co-located files** in component directories

### API Integration
- **Centralized routes** in `src/api/routes.ts`
- **Streaming responses** with custom hooks
- **Error handling** for network failures
- **Default endpoint**: `http://localhost:7777`

### Styling Approach
- **Tailwind CSS** utility classes
- **shadcn/ui** component library
- **Responsive design** with mobile-first
- **Theme support** via next-themes
- **Custom fonts**: Geist Sans and DM Mono

## Key Features to Maintain

### Real-time Streaming
- AI responses stream in real-time
- Streaming state management in Zustand
- Error handling for connection issues

### Multi-modal Support
- Images, videos, audio in chat messages
- Proper type definitions for media data
- Responsive media display components

### Tool Calls Visualization
- Agent tool execution display
- Results visualization
- Proper TypeScript interfaces

### Session Management
- Persistent chat sessions
- CRUD operations for sessions
- Session loading states

## Code Organization Principles

### Import Strategy
1. External dependencies
2. Internal utilities and types  
3. Components
4. Relative imports

### File Naming
- **Components**: PascalCase.tsx
- **Hooks**: useCamelCase.tsx
- **Utilities**: camelCase.ts
- **Types**: camelCase.ts
- **Directories**: kebab-case

### TypeScript Best Practices
- **Strict mode** enabled
- **Interface over type** for object shapes
- **Utility types** for transformations
- **Proper error types** for API responses
- **Generic constraints** where needed

## Performance Considerations
- **React.memo** for expensive renders
- **Custom hooks** for reusable logic
- **Proper key props** for lists
- **Lazy loading** for large components
- **Optimistic updates** for better UX