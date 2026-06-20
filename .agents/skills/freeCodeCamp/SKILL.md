```markdown
# freeCodeCamp Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill provides a comprehensive guide to the development patterns, coding conventions, and common workflows used in the freeCodeCamp repository. The codebase is primarily written in TypeScript and does not use a specific framework. It emphasizes maintainable code, clear commit messages, and streamlined dependency management across multiple packages.

## Coding Conventions

### File Naming
- Use **camelCase** for file names.
  - Example: `userProfile.ts`, `apiHandler.ts`

### Import Style
- Use **relative imports** for referencing modules within the project.
  - Example:
    ```typescript
    import { getUser } from './userService';
    ```

### Export Style
- Use **named exports** to export functions, types, or constants.
  - Example:
    ```typescript
    // userService.ts
    export function getUser(id: string) { ... }
    export const USER_ROLE = 'admin';
    ```

### Commit Messages
- Follow **conventional commit** style.
- Common prefix: `chore`
- Example:
  ```
  chore: update dependencies in user and api packages
  ```

## Workflows

### Update Dependencies Across Multiple Packages
**Trigger:** When you need to update npm/yarn dependencies across multiple packages (often via dependabot or similar automation).
**Command:** `/update-dependencies`

1. Identify outdated dependencies in all relevant `package.json` files.
2. Update the version numbers for those dependencies in each `package.json`.
3. Update the `pnpm-lock.yaml` (or equivalent lockfile) to reflect the new dependency versions.
4. Commit all changed `package.json` files and the lockfile together.

**Files involved:**
- `*/package.json`
- `pnpm-lock.yaml`

**Example commit message:**
```
chore: update dependencies in api and client packages
```

## Testing Patterns

- Test files follow the pattern: `*.test.*`
- The specific testing framework is not detected, but tests are colocated with source files or in dedicated test directories.
- Example test file: `userService.test.ts`

**Example test structure:**
```typescript
// userService.test.ts
import { getUser } from './userService';

test('should fetch user by id', () => {
  const user = getUser('123');
  expect(user.id).toBe('123');
});
```

## Commands
| Command              | Purpose                                                        |
|----------------------|----------------------------------------------------------------|
| /update-dependencies | Update dependencies across all package.json files and lockfile. |
```
