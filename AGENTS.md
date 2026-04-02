# AGENTS.md - Project Knowledge Base

## Build & Test Commands

```bash
bun install           # Install dependencies (bun only - never npm/yarn)
bun run build         # Full build: ESM + declarations + schema
bun run typecheck     # Type check only
bun test              # Run all tests
bun test chief        # Run tests matching "chief" pattern
bun test path/to.test.ts  # Run single test file
```

## Project Structure

```
src/
├── agents/      # 8 agents: chief, deputy, researcher, fact-checker, archivist, extractor, writer, editor
├── hooks/       # Lifecycle hooks (chief-orchestrator, comment-checker, etc.)
├── tools/       # LSP, AST-Grep, Grep, Glob, chief-task, skill
├── features/    # Background agents, skill loaders, context injector
├── auth/        # Google Antigravity OAuth
├── config/      # Zod schemas and TypeScript types
├── mcp/         # MCP server configs (exa, tavily, firecrawl)
└── index.ts     # Main plugin entry
```

## Three-Layer Architecture

| Layer | Agent | Role |
|-------|-------|------|
| 1 | Chief | Task understanding, high-level decomposition, final delivery |
| 2 | Deputy | Execute/dispatch complex tasks, aggregate results |
| 3 | Specialists | Researcher, writer, fact-checker, editor, archivist, extractor |

## Code Style

### Imports
```typescript
// External first, then internal with relative paths
import type { Plugin } from "@opencode-ai/plugin"
import { existsSync } from "node:fs"
import { log } from "../../shared/logger"
import type { AgentConfig } from "./types"
```

### Naming Conventions
| Element | Convention | Example |
|---------|------------|---------|
| Directories/Files | kebab-case | `chief-orchestrator/`, `quality-dimensions.ts` |
| Hook creators | `createXXXHook` | `createChiefOrchestratorHook()` |
| Agent factories | `createXXXAgent` | `createChiefAgent()` |
| Constants | UPPER_SNAKE | `DEFAULT_MODEL`, `HOOK_NAME` |
| Types | PascalCase | `AgentConfig`, `QualityScores` |

### Error Handling
```typescript
try {
  const result = await someAsyncOperation()
} catch (error) {
  log.error("Operation failed:", error)
  throw error
}
// NEVER: empty catch {}, as any, @ts-ignore, @ts-expect-error
```

## Testing

Test files: `*.test.ts` alongside source. Use BDD comments for clarity.

```typescript
import { describe, test, expect } from "bun:test"

describe("QualityDimensions", () => {
  test("should parse multi-dimensional scores", () => {
    // #given
    const output = "**QUALITY SCORES:**\n- Coverage: 0.85\n**OVERALL: 0.70**"
    // #when
    const result = parseQualityScores(output, "researcher")
    // #then
    expect(result.overall).toBe(0.70)
  })
})
```

## Anti-Patterns

| Forbidden | Use Instead |
|-----------|-------------|
| `npm` / `yarn` | `bun` |
| `@types/node` | `bun-types` |
| `as any`, `@ts-ignore` | Proper typing |
| Empty `catch {}` | Log and handle errors |
| `Bun.spawn` | `node:child_process` |
| Direct `npm publish` | `npm version patch && npm publish` |

## Runtime Compatibility

OpenCode loads plugins using a runtime that may not support Bun-specific APIs.

```typescript
// WRONG - causes plugin load failure
Bun.spawn([...])
Bun.write(path, data)

// CORRECT - works in both Bun and Node.js
import { spawn } from "node:child_process"
import { writeFile } from "node:fs/promises"
```

## Agent Communication

- **Chief** uses `chief_task` to delegate to Deputy
- **Deputy** dispatches to specialists via `chief_task` with appropriate `subagent_type`
- All agents use collaborative tone - never refuse tasks, always execute or decompose
