# Suggested Commands

## Development Commands
- `pnpm dev` - Start development server on port 3000
- `pnpm build` - Build the application for production
- `pnpm start` - Start production server
- `pnpm install` - Install dependencies

## Code Quality Commands
- `pnpm lint` - Run ESLint
- `pnpm lint:fix` - Fix ESLint issues automatically
- `pnpm format` - Check code formatting with Prettier
- `pnpm format:fix` - Fix formatting issues automatically
- `pnpm typecheck` - Run TypeScript type checking
- `pnpm validate` - Run all quality checks (lint + format + typecheck)

## Git Commands
- `git status` - Check working tree status
- `git add .` - Stage all changes
- `git commit -m "message"` - Commit changes
- `git push` - Push to remote repository

## File Operations (Linux)
- `ls -la` - List files with details
- `find . -name "*.tsx"` - Find TypeScript React files
- `grep -r "pattern" src/` - Search for patterns in source
- `cat filename` - Display file contents
- `mkdir dirname` - Create directory
- `rm filename` - Remove file

## Package Management
- `pnpm add package` - Add new dependency
- `pnpm add -D package` - Add dev dependency
- `pnpm remove package` - Remove dependency
- `pnpm list` - List installed packages

## Useful Combinations
- `pnpm validate && pnpm build` - Quality check then build
- `git add . && git commit -m "message"` - Stage and commit
- `pnpm lint:fix && pnpm format:fix` - Auto-fix code style