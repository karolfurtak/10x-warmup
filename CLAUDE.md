# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a warmup repository for the 10xDevs.pl training program, focusing on AI-assisted development with tools like GitHub Copilot, Cursor, Windsurf, Aider, and Cline. The repository contains practical exercises for testing AI editors and models.

## Core Commands

**Installation:**
```bash
npm install
```

**Testing:**
```bash
npm test                    # Run all tests with Vitest
npx vitest --watch          # Run tests in watch mode
```

## Project Structure

The repository is organized into focused exercise areas:

- **`banking/`** - Core TypeScript exercise implementing a banking system
  - `banking.ts` - Domain logic for account management and withdrawals
  - `banking.test.ts` - Vitest test suite
  - `types.ts` - Shared type definitions
  - `banking-spec.md` - Business requirements specification (in Polish)

- **`prompts/`** - Prompt engineering experiments with English/Polish variants
  - `decomposer.md` / `decomposer_pl.md` - Task decomposition prompts
  - `unblocker.md` / `unblocker_pl.md` - Problem-solving prompts

- **`charts/request.md`** - Mermaid diagram exercises demonstrating sequence diagrams for web requests

- **`agent-sandbox/`** - Example legacy code for testing AI refactoring
  - `Dashboard.tsx` - React component with legacy patterns
  - `example.js` - FizzBuzz implementation for review
  - `package.legacy.json` - Outdated package configuration

- **`.cursor/`** - Cursor-specific rules and commands
  - `.cursor/rules/typescript.mdc` - TypeScript coding rules
  - `.cursor/rules/hooks.mdc` - React Hooks compliance rules
  - `.cursor/commands/*.md` - Custom slash commands for Cursor

## TypeScript Configuration

The project uses TypeScript 5.8+ with strict mode enabled (`tsconfig.json`). Key constraints:

- Target: ES2016
- Module: CommonJS
- Strict type checking enabled
- Prefer `const` over `let`/`var`
- Avoid `any` type
- **Emoji rule**: Always use emojis in error messages (per `.cursor/rules/typescript.mdc`)

## Banking Exercise Architecture

The banking module follows a specification-driven development approach:

1. **Specification first**: `banking-spec.md` defines business rules in Given-When-Then format
2. **Test-driven**: Tests in `banking.test.ts` verify all specification requirements
3. **Type-safe domain logic**: Implementation in `banking.ts` with strong typing from `types.ts`

Key business rules enforced:
- Account creation with unique IDs and proper currency
- Withdrawal validation (positive amounts, sufficient funds, currency matching)
- Error handling with specific codes: `INSUFFICIENT_FUNDS`, `INVALID_AMOUNT`, `ACCOUNT_NOT_FOUND`
- Transaction logging with timestamps and remaining balance

## Testing Philosophy

- Vitest is the test runner (configured in `package.json`)
- Tests auto-discover `*.test.ts` files
- Mirror `describe`/`it` nesting patterns from existing tests
- Cover both happy paths and error scenarios
- Assert explicit error messages and codes
- Keep tests alongside implementation code

## Commit Conventions

Follow Conventional Commits pattern visible in git history:
- `feat:` for new features
- `fix:` for bug fixes
- `doc:` for documentation
- `chore:` for maintenance tasks

Recent examples from git log:
```
feat: implement complete banking withdrawal logic with emoji error messages
feat: add Dashboard component and legacy FizzBuzz implementation
doc: readme
```

## Exercise Workflow

The four pre-work exercises are designed to test AI tooling:

1. **Banking System** - Implement functionality based on `banking-spec.md` and pass all tests
2. **Test Analysis** - Compare test coverage against specification
3. **Mermaid Diagrams** - Generate diagrams from `charts/request.md`
4. **Rule-Based Behavior** - Observe how AI adapts to `.cursor/rules/` constraints

## Environment & Compatibility

- Node version specified in `.nvmrc`
- Environment template available in `.env.template`
- Cross-platform compatible (Windows paths shown in examples)
