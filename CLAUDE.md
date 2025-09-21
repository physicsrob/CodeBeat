# Claude Code Configuration

This file contains configuration and context for working with CodeBeat using Claude Code.

## Project Overview

A modern web application for learning Morse code with real-time feedback, statistics tracking, and multiple study modes. Built with React + TypeScript + Vite.

## Development Commands

```bash
# Development
npm run dev          # Start development server
npm test            # Run all tests (watch mode)
npm run test:ui     # Interactive test UI
npm run build       # Build for production

# Quality Checks (run these before committing!)
npm run check       # Run ALL checks: TypeScript, ESLint, and tests
npm run check:fix   # Same as check but auto-fix lint issues
npm run typecheck   # TypeScript type checking only
npm run lint        # ESLint only
```

## Architecture

The app uses a runtime-based approach (NOT state machines) - see `arch.md` for details:

- **Core Domain**: `src/core/` - Timing engine, alphabet, types
- **Runtime System**: `src/features/session/runtime/` - Session orchestration
- **Services**: `src/features/session/services/` - Audio, feedback
- **Pages**: `src/pages/` - React components

## Key Files

- `src/core/morse/timing.ts` - Morse timing calculations (WPM → dit length)
- `src/core/morse/alphabet.ts` - Character to Morse pattern mappings
- `src/features/session/runtime/sessionProgram.ts` - Main session orchestrator
- `src/features/session/runtime/charPrograms.ts` - Active/Passive mode logic
- `src/pages/StudyPage.tsx` - Main UI component

## Current Status

✅ Core timing engine with tests
✅ Runtime session orchestration
✅ Audio engine (WebAudio)
✅ Basic UI with Active/Passive modes
❌ No persistence/statistics
❌ Limited text sources (random only)

## Implementation Priority

See `STATUS.md` for detailed next steps. Priority order:
1. Fix WPM configuration duplication (tech debt)
2. Add event logging and persistence
3. Implement basic statistics
4. Add more text sources
5. User settings management

## Testing

- ~32 tests currently passing
- Focus on core logic (timing, runtime, alphabet)
- Using Vitest with fake clocks for deterministic testing

## Important Notes

- Dit length = 1200/WPM ms (standard CW formula)
- Speed tiers: slow(5×dit), medium(3×dit), fast(2×dit), lightning(1×dit)
- Latency measured from audio END to keypress (0 if pressed during audio)
- No retries on failed characters - advance to next

## Documentation

- `spec.md` - What to build (product requirements)
- `arch.md` - How it's built (technical architecture)
- `STATUS.md` - Current state and next steps
- `tech_debt.md` - Known issues to fix

# Import Context
@spec.md
@arch.md
@STATUS.md

# Instructions for AI Assistants

When working on this project:
1. **Always read STATUS.md first** to understand current progress
2. **Update STATUS.md** when completing tasks or making significant progress
3. **Follow the implementation order** outlined in STATUS.md and arch.md
4. **Run tests** after implementing core logic (`npm test`)
5. **Commit frequently** with descriptive messages including 🤖 Generated with [Claude Code]
6. **Read brand.md before modifying HTML/CSS** to ensure consistent styling and branding
