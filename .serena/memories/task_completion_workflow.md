# Task Completion Workflow

## Required Steps After Making Changes

### 1. Code Quality Checks (MANDATORY)
Always run these commands after making code changes:

```bash
pnpm validate
```

This runs all quality checks: lint + format + typecheck

Or run individually:
```bash
pnpm lint          # Check for linting issues
pnpm format        # Check formatting
pnpm typecheck     # Check TypeScript types
```

### 2. Auto-fix Issues
If quality checks fail, auto-fix what's possible:

```bash
pnpm lint:fix      # Fix ESLint issues
pnpm format:fix    # Fix Prettier formatting
```

### 3. Build Verification
For significant changes, verify the build works:

```bash
pnpm build
```

### 4. Testing
**Note**: This project currently has no test setup. Consider adding tests for:
- Component rendering
- Hook functionality  
- API integration
- State management

## Pre-commit Checklist
- [ ] Code follows TypeScript strict mode
- [ ] ESLint passes (`pnpm lint`)
- [ ] Prettier formatting applied (`pnpm format`)
- [ ] TypeScript compiles (`pnpm typecheck`)
- [ ] Build succeeds (`pnpm build`)
- [ ] Manual testing completed

## Development Workflow
1. Make code changes
2. Run `pnpm validate` 
3. Fix any issues with `pnpm lint:fix` and `pnpm format:fix`
4. Test functionality manually
5. Build and verify (`pnpm build`)
6. Commit changes

## Important Notes
- **No test framework** is currently configured
- **TypeScript strict mode** is enabled - all types must be properly defined
- **Prettier and ESLint** are configured with specific rules that must be followed
- **Next.js build** must pass before deploying