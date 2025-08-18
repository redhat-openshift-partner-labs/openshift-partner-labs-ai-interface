# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Agent UI is a modern chat interface for AI agents built with Next.js, Tailwind CSS, and TypeScript. It provides a ready-to-use UI for interacting with Agno agents, featuring real-time streaming, tool calls visualization, reasoning steps display, multi-modal content support, and session management.

## Development Commands

### Core Commands
- `pnpm dev` - Start development server on port 3000
- `pnpm build` - Build the application for production
- `pnpm start` - Start production server
- `pnpm install` - Install dependencies

### Code Quality
- `pnpm lint` - Run ESLint
- `pnpm lint:fix` - Fix ESLint issues automatically
- `pnpm format` - Check code formatting with Prettier
- `pnpm format:fix` - Fix formatting issues automatically
- `pnpm typecheck` - Run TypeScript type checking
- `pnpm validate` - Run all quality checks (lint + format + typecheck)

## Architecture Overview

### State Management
- **Zustand Store** (`src/store.ts`): Centralized state management with persistence
  - Manages chat messages, streaming state, endpoints, agents, and sessions
  - Persists selected endpoint to localStorage
  - Handles hydration for SSR compatibility

### Core Components Structure
- **Playground** (`src/components/playground/`): Main chat interface
  - `ChatArea/`: Message display and input handling
  - `Sidebar/`: Agent selection and session management
- **UI Components** (`src/components/ui/`): Reusable components built with Radix UI and Tailwind

### API Integration
- **Endpoints** (`src/api/routes.ts`): Centralized API route definitions
- **Default Backend**: Connects to `http://localhost:7777` (Agno Playground)
- **Streaming Support**: Real-time AI response streaming via custom hooks

### Key Features Architecture
- **Multi-modal Support**: Handles images, videos, audio in messages
- **Tool Calls**: Visualizes agent tool execution and results
- **Reasoning Steps**: Displays agent thinking process
- **Session Management**: Persistent chat sessions with CRUD operations

### Type System
- **Comprehensive Types** (`src/types/playground.ts`): Defines all interfaces for
  - Chat messages, tool calls, reasoning steps
  - Run events and streaming responses
  - Media data structures
  - Session and agent metadata

### Styling
- **Tailwind CSS**: Utility-first styling
- **Custom Fonts**: Geist Sans and DM Mono
- **Responsive Design**: Mobile-first approach
- **Theme Support**: Built-in dark/light mode capability

## Development Notes

- Uses pnpm as package manager
- Built on Next.js 15 with React 19
- TypeScript strict mode enabled
- ESLint and Prettier configured for code quality
- Framer Motion for animations
- Zustand for state management with persistence

## Testing

### Current State
**No test framework is currently configured.** Manual testing is required for now.

### Future Testing Setup Recommendations
Consider adding these testing tools:
```bash
# Testing framework recommendations
pnpm add -D jest @testing-library/react @testing-library/jest-dom
pnpm add -D @testing-library/user-event vitest jsdom

# Future test commands
pnpm test              # Run all tests
pnpm test:watch        # Run tests in watch mode
pnpm test:coverage     # Run tests with coverage report
```

### Manual Testing Workflow
1. Start development server: `pnpm dev`
2. Test all chat functionality manually
3. Verify streaming responses work correctly
4. Test agent selection and session management
5. Check multi-modal content display (images, videos, audio)
6. Verify tool calls visualization
7. Test responsive design on different screen sizes

### Testing Priorities for Future Implementation
- **Component Tests**: Chat components, UI components, form interactions
- **Hook Tests**: Custom hooks like `useAIStreamHandler`, `useChatActions`
- **Integration Tests**: API integration, streaming functionality
- **E2E Tests**: Complete user workflows with Playwright

## Code Structure Guidelines

### Adding New Components
1. **Create component directory** in appropriate location (`src/components/ui/` or `src/components/playground/`)
2. **Follow naming convention**: PascalCase for component files (e.g., `NewComponent.tsx`)
3. **Create index.ts** for clean barrel exports
4. **Define Props interface** with TypeScript
5. **Follow existing patterns** from similar components

### Component Implementation Pattern
```typescript
// Component file structure
import { ComponentProps } from './types'

interface NewComponentProps {
  // Define props with TypeScript
}

export const NewComponent = ({ prop1, prop2 }: NewComponentProps) => {
  // Component logic
  return (
    <div className="tailwind-classes">
      {/* JSX content */}
    </div>
  )
}

export default NewComponent
```

### Custom Hooks Guidelines
1. **File naming**: `useCamelCase.tsx` or `useCamelCase.ts`
2. **Return objects** for multiple values instead of arrays
3. **Handle cleanup** with useEffect return functions
4. **Use TypeScript** for all parameters and return types
5. **Follow existing patterns** from `src/hooks/`

### API Integration Pattern
1. **Centralize routes** in `src/api/routes.ts`
2. **Use custom hooks** for API calls (see `useAIStreamHandler`)
3. **Handle loading states** in Zustand store
4. **Implement error handling** for all API calls
5. **Support streaming** where applicable

### State Management Guidelines
1. **Zustand store** (`src/store.ts`) for global state
2. **Local state** for component-specific data
3. **Persistent state** for user preferences
4. **Custom hooks** for complex state logic
5. **Handle hydration** for SSR compatibility

### Styling Conventions
1. **Tailwind utility classes** for all styling
2. **Component variants** using `class-variance-authority`
3. **Responsive design** with mobile-first approach
4. **Dark/light theme** support via `next-themes`
5. **Consistent spacing** using Tailwind scale

### File Organization Rules
1. **Barrel exports** via `index.ts` files
2. **Co-locate** related files in component folders
3. **Separate concerns**: types, hooks, components, and API logic
4. **Absolute imports** using `@/*` path mapping
5. **Group imports**: external → internal → relative

## Setup Requirements

### Prerequisites
- **Node.js**: Version 18.0.0 or higher (Next.js 15 requirement)
- **pnpm**: Required package manager for this project
- **Git**: For version control

### Installation
1. **Install Node.js**: Download from [nodejs.org](https://nodejs.org/) or use version manager
   ```bash
   # Check Node.js version
   node --version  # Should be >= 18.0.0
   ```

2. **Install pnpm**: Required package manager
   ```bash
   npm install -g pnpm
   # or using Node.js corepack
   corepack enable
   ```

3. **Clone and setup project**:
   ```bash
   git clone <repository-url>
   cd openshift-partner-labs-ai-interface
   pnpm install
   ```

### Environment Configuration
- **No environment variables required** for basic development
- **Default backend**: Connects to `http://localhost:7777` (configurable in UI)
- **Development port**: 3000 (configurable with `-p` flag)

### Agno Playground Setup (Optional)
For full functionality, set up the Agno Playground backend:
1. Follow [Agno Playground documentation](https://agno.link/agent-ui#connect-to-local-agents)
2. Start Agno Playground on port 7777
3. Agent UI will automatically connect to the local backend

### IDE Setup Recommendations
- **VS Code** with recommended extensions:
  - TypeScript and JavaScript Language Features
  - Tailwind CSS IntelliSense
  - ESLint
  - Prettier
  - Auto Rename Tag

### Verification
```bash
# Verify setup
pnpm validate    # Run all quality checks
pnpm dev        # Start development server
```

Open [http://localhost:3000](http://localhost:3000) to verify the application runs correctly.

---

## Development Workflow with Claude Code

### Task Planning and Management

#### Before Starting Work
- Use the **TodoWrite tool** to create a structured task list for complex or multi-step work
- Break down tasks into specific, actionable items with clear completion criteria
- Mark tasks as `pending`, `in_progress`, or `completed` to track progress
- For research-heavy tasks, use the **Task tool** with specialized agents
- Prioritize MVP (minimally viable) approach - avoid over-planning

#### During Development
- Proactively update task status using TodoWrite as you work
- Mark tasks `completed` immediately after finishing (don't batch completions)
- Only have ONE task `in_progress` at any time
- Add new tasks if requirements emerge during implementation

### Development Automation with Hooks

#### Setting Up Development Hooks
Claude Code supports hooks - shell commands that execute automatically in response to events:

- **Pre-commit hooks**: Run linting and tests before code changes
- **Post-edit hooks**: Automatically format code or run type checking
- **Tool execution hooks**: Custom validation or setup commands

#### Example Hook Configuration
```json
{
  "hooks": {
    "before_edit": "pnpm lint",
    "after_edit": "pnpm typecheck", 
    "before_bash": "echo 'Running command...'"
  }
}
```

#### Best Practices
- Use hooks for repetitive quality assurance tasks
- Configure automatic testing after significant changes
- Set up linting hooks to maintain code standards
- If blocked by hooks, adjust actions or review hook configuration

### Optimized Development Workflow

#### Project Initialization
1. **Check existing documentation**: Read CLAUDE.md and README.md for context
2. **Review project memory**: Use memory tools to understand previous work
3. **Understand current state**: Use file exploration tools before making changes

#### Implementation Phase
1. **Use TodoWrite for task management**: Create and track development tasks
2. **Leverage specialized agents**: Use Task tool for research or complex analysis
3. **Batch tool operations**: Use multiple tool calls in single messages for efficiency
4. **Follow testing requirements**: Always run `pnpm validate` after changes

#### Quality Assurance
1. **Run project linting/testing**: Use `pnpm validate` for all quality checks
2. **Verify changes**: Use diagnostic tools to ensure code correctness
3. **Update documentation**: Maintain consistency between code and docs
4. **Commit strategically**: Only commit when explicitly requested by user

### Project Memory and Context Management

#### Using Project Memory
- **Read relevant memories**: Check existing project memories before starting work
- **Write new memories**: Document important architectural decisions or patterns
- **Update outdated memories**: Remove or update memories that are no longer accurate
- **Memory naming**: Use descriptive names that indicate content relevance

#### Memory Best Practices
- Store complex architectural decisions and their reasoning
- Document non-obvious code patterns or conventions
- Record important configuration or setup requirements
- Maintain memory hygiene - delete obsolete information

### Leveraging Claude Code's Tool Ecosystem

#### File Operations
- **Prefer Read over Bash**: Use Read tool instead of `cat` commands
- **Use Glob for pattern matching**: More efficient than `find` commands
- **Batch file operations**: Read multiple files in single message when possible

#### Code Analysis
- **Use MCP tools when available**: Leverage serena and other MCP servers for code analysis
- **Symbolic vs. regex editing**: Choose appropriate editing approach based on scope
- **Diagnostic integration**: Use IDE diagnostic tools for error checking

#### Development Integration
- **Git workflow**: Use proper git commands for commits and PRs
- **Testing integration**: Run `pnpm validate` before any commits
- **Documentation sync**: Keep README.md and CLAUDE.md synchronized

## Versioning and Release Management

### Current Version
Check current version using:
```bash
git describe --tags  # Show current version if tagged
git log --oneline -5  # Show recent commits
```

### Version Schema
This project follows [Semantic Versioning](https://semver.org/):
- **MAJOR.MINOR.PATCH** (e.g., v1.0.0)
- **MAJOR**: Breaking changes (API changes, major UI overhauls)
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes and documentation updates

### Release Process
1. **Quality Assurance**: Always run full validation before releases
   ```bash
   pnpm validate  # Lint + format + typecheck
   pnpm build     # Verify production build
   ```

2. **Version Management**: Follow semantic versioning guidelines
   - Breaking changes to chat interface or API → MAJOR
   - New features (tool visualization, UI improvements) → MINOR
   - Bug fixes and docs → PATCH

3. **Release Notes**: Document changes in release descriptions
   - New features and improvements
   - Bug fixes
   - Breaking changes (if any)
   - Migration instructions (if needed)

### For AI Assistants
- **Check current version** before starting work: `git describe --tags`
- **Consider version impact** when making changes
- **Document breaking changes** clearly in commit messages
- **Reference specific versions** when discussing features or bugs

## Error Handling and Recovery

### Common Development Issues

#### Build and Runtime Errors
1. **TypeScript Errors**: Run `pnpm typecheck` to identify type issues
2. **ESLint Errors**: Use `pnpm lint:fix` to auto-fix common issues
3. **Formatting Issues**: Use `pnpm format:fix` to apply Prettier formatting
4. **Build Failures**: Check Next.js build logs and verify all imports

#### Development Server Issues
1. **Port Conflicts**: Change port with `pnpm dev -p 3001`
2. **Module Resolution**: Ensure imports use correct paths with `@/` prefix
3. **Hot Reload Issues**: Restart dev server or clear Next.js cache
4. **API Connection**: Verify Agno Playground is running on port 7777

#### Hook Configuration Issues
1. **Hook Failures**: Check hook configuration in Claude Code settings
2. **Permission Errors**: Verify file permissions and access rights
3. **Command Not Found**: Ensure commands exist and are in PATH

### Recovery Strategies

#### When Tools Fail
- **Incremental progress**: Save work frequently using TodoWrite
- **Context preservation**: Use memory tools to preserve important context
- **Alternative approaches**: Fall back to different tool approaches when needed

#### Development Recovery
1. **Clean Build**: Remove `.next` folder and rebuild
   ```bash
   rm -rf .next
   pnpm build
   ```

2. **Dependency Issues**: Clear and reinstall packages
   ```bash
   rm -rf node_modules pnpm-lock.yaml
   pnpm install
   ```

3. **Git Recovery**: Use git to recover from problematic changes
   ```bash
   git stash        # Save current changes
   git reset --hard # Reset to last commit
   git stash pop    # Restore changes if needed
   ```

### Debugging Strategies

#### Code Issues
1. **Use TypeScript**: Leverage strict typing to catch errors early
2. **Console Debugging**: Use `console.log` and browser dev tools
3. **React DevTools**: Install React DevTools browser extension
4. **Zustand DevTools**: Use Redux DevTools for state debugging

#### Performance Issues
1. **Next.js Bundle Analyzer**: Analyze bundle size and optimization
2. **React Profiler**: Identify performance bottlenecks
3. **Network Tab**: Debug API calls and streaming responses
4. **Lighthouse**: Check performance, accessibility, and SEO

### Prevention Best Practices
- **Run `pnpm validate`** before committing any changes
- **Use TodoWrite** to track complex work and avoid losing context
- **Test incrementally** during development
- **Document workarounds** in project memory for future reference