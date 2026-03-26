# KNOWLEDGE.md - newtype-profile

**AI Agent Collaboration System for Content Creation**

Version: 1.0.52 | Author: huangyihe | License: SUL-1.0

---

## OVERVIEW

newtype-profile is an AI Agent collaboration framework designed for **content creation**. Based on [oh-my-opencode](https://github.com/code-yeongyu/oh-my-opencode), redesigned for content creation scenarios.

Unlike oh-my-opencode which focuses on code programming, this project redefines the Agent system as an editorial team model, suitable for:

- 📚 Knowledge base management
- ✍️ Article writing and editing
- 🔍 Information research and fact-checking
- 📄 Document extraction and organization

### Three-Layer Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Chief (Opus 4.5)                     │
│                   思考者 / Thinker                       │
│  • 与用户对话，理解需求                                   │
│  • 高层任务拆解、最终审核与交付                           │
│  • 工具白名单限制 — 只能用 chief_task 委派执行            │
└─────────────────────┬───────────────────────────────────┘
                      │ chief_task(subagent_type="deputy")
                      ↓
┌─────────────────────────────────────────────────────────┐
│                   Deputy (Sonnet 4.5)                   │
│                   执行者 / Doer                          │
│  • 接收 Chief 的精简指令，拆解复杂任务                    │
│  • 调度专业 Agents，汇总过滤输出                         │
│  • 协作语气，永不拒绝任务                                │
└─────────────────────┬───────────────────────────────────┘
                      │ chief_task(subagent_type="researcher/writer/...")
                      ↓
┌─────────────────────────────────────────────────────────┐
│              Specialists (Gemini/Sonnet)                │
│  researcher, writer, fact-checker, editor, etc.        │
│  执行具体任务，不评判任务本身                            │
└─────────────────────────────────────────────────────────┘
```

---

## STRUCTURE

```
newtype-profile/
├── src/
│   ├── agents/          # 8 agent definitions (chief, deputy, researcher, etc.)
│   ├── hooks/           # 22+ lifecycle hooks (orchestrator, comment-checker, etc.)
│   ├── tools/           # LSP (11 tools), AST-Grep, Grep, Glob, chief-task, skill
│   ├── features/        # Background agents, skill loaders, context injector
│   ├── auth/            # Google Antigravity OAuth
│   ├── config/          # Zod schemas and TypeScript types
│   ├── mcp/             # MCP servers (exa, tavily, firecrawl, sequential-thinking)
│   ├── cli/             # CLI tools (install, doctor, run, auth)
│   ├── shared/          # Common utilities
│   └── index.ts         # Main plugin entry
├── docs/                # Documentation
│   ├── orchestration-guide.md
│   ├── cli-guide.md
│   └── category-skill-guide.md
├── script/              # Build utilities
├── assets/              # JSON schema
└── dist/                # Build output (ESM + .d.ts)
```

---

## KEY DOCUMENTS

| File | Description | Topics |
|------|-------------|--------|
| **README.md** | Main project documentation | Installation, configuration, usage |
| **README.zh-cn.md** | Chinese version of README | 简体中文文档 |
| **AGENTS.md** | Knowledge base for all modules | Root and in src/* directories |
| **docs/orchestration-guide.md** | Planning & execution separation | Prometheus, Sisyphus, workflow |
| **docs/cli-guide.md** | CLI usage guide | Commands, doctor, auth |
| **docs/category-skill-guide.md** | Category & skill system | Categories, skills, combos |
| **CONTRIBUTING.md** | Development guidelines | Setup, conventions, PR process |
| **LICENSE.md** | SUL-1.0 License | Software license |
| **CLA.md** | Contributor License Agreement | Contribution terms |

---

## CONTENT KNOWLEDGE BASE

### baoqi_library/ - 电动推杆行业知识库

**Location**: `./baoqi_library/`
**Type**: Obsidian Vault + Markdown Knowledge Base
**Total Files**: ~100+ markdown files
**Language**: Chinese (中文) + English

#### Purpose
Industry intelligence repository for the electric actuator (电动推杆) and lifting column (升降柱) sector. Contains product specifications, technical guides, industry news, and application case studies. Used for content creation research on linear actuator technology, product selection, and industrial/home automation applications.

#### Directory Structure

```
baoqi_library/
├── .obsidian/                    # Obsidian vault configuration
├── 01 - INPUT/                   # Raw article imports (folders 2-23)
│   ├── 2 - articles/            # ~9 articles (basic knowledge)
│   ├── 3 - articles/            # Lifting columns
│   ├── 4 - articles/             # Linear modules
│   ├── 5 - articles/             # Actuator basics
│   ├── 6 - articles/             # Electric actuators
│   ├── 7 - articles/             # Screw elevators
│   ├── 8 - articles/             # DIY projects
│   ├── 9 - articles/             # Troubleshooting & selection
│   └── ... (10-23)               # Various topics
├── 02 - PROCESSING/              # Analyzed content
│   └── 01 - Daily-Reading/
│       ├── product catalog.md    # Product specifications (HR61, IP42, IP60, IP70, IP80, IP600, IP800, IP1200, IP3000H, IP3000L)
│       ├── actulift website catalog link.md
│       └── 01 - Article/
│           ├── 2 - articles.md to 18 - articles.md  # Weekly/daily analysis reports
├── 03 - OUTPUT/                  # Output folder (empty)
```

#### Key Documents in 02 - PROCESSING

| File | Description | Topics |
|------|-------------|--------|
| `product catalog.md` | Complete product specifications for 10+ actuator models | HR61, IP42, IP60, IP70, IP80, IP600, IP800, IP1200, IP3000H, IP3000L |
| `2 - articles.md` to `18 - articles.md` | Weekly/daily synthesis reports | Technology, selection, applications, industry trends |

#### Content Topics

- **Product Specifications**: Technical specs for electric linear actuators (force, speed, stroke, voltage, IP rating)
- **Technology**: Working principles, duty cycle, IP ratings, motor types, limit switches
- **Selection Guide**: How to choose actuators for different applications
- **Applications**: Industrial automation, home furniture (standing desks), medical equipment, automotive
- **Brands**: ActuLift
- **Products**: Linear actuators, lifting columns, electric lifting columns, telescopic columns
- **Standards**: CCC certification, CE, RoHS

#### Workflow Pattern

**3-Stage Processing Pipeline**:
1. **INPUT** → Raw article imports (batches 2-23)
2. **PROCESSING** → AI-generated analysis with product specs and summaries
3. **OUTPUT** → Final deliverables (currently empty)

#### How to Reference

When writing content about electric actuators:
- Search `baoqi_library/02 - PROCESSING/` for product catalogs and analyzed reports
- Check `baoqi_library/01 - INPUT/` for raw source articles by topic folder
- Product catalog contains detailed specs for 10+ actuator models

---

## AGENT TEAM

| Agent | Role | Default Model | Purpose | Temperature |
|-------|------|---------------|---------|-------------|
| **chief** | Editor-in-Chief | Claude Opus 4.5 Thinking High | Thinker/Planner - user interaction, task decomposition | 0.3 |
| **deputy** | Deputy Editor | Claude Sonnet 4.5 | Doer/Coordinator - executes delegated tasks | 0.3 |
| **researcher** | Intelligence Officer | Gemini 3 Pro High | Broad search, discover new information | 0.5 |
| **fact-checker** | Verifier | Gemini 3 Pro High | Validate sources, assess credibility | 0.2 |
| **archivist** | Librarian | Claude Sonnet 4.5 | Knowledge base retrieval, find connections | 0.3 |
| **extractor** | Formatter | Gemini 3 Flash | PDF/image/document extraction | 0.2 |
| **writer** | Writer | Gemini 3 Pro High | Content production, article drafting | 0.7 |
| **editor** | Editor | Claude Sonnet 4.5 | Content refinement, structure optimization | 0.3 |

### Task Categories

| Category | Purpose | Default Model | Temperature |
|----------|---------|---------------|-------------|
| `research` | Information research, trend discovery | Gemini 3 Pro High | 0.5 |
| `fact-check` | Source verification, credibility assessment | Gemini 3 Pro High | 0.2 |
| `archive` | Knowledge base retrieval, document linking | Claude Sonnet 4.5 | 0.3 |
| `writing` | Content creation, article drafting | Gemini 3 Pro High | 0.7 |
| `editing` | Content refinement, structure optimization | Claude Sonnet 4.5 | 0.3 |
| `extraction` | PDF/image content extraction | Gemini 3 Flash | 0.2 |
| `quick` | Simple quick tasks | Gemini 3 Flash | 0.3 |

### Built-in Skills

| Skill | Command | Description |
|-------|---------|-------------|
| **playwright** | `/playwright` | Browser automation via Playwright MCP - web scraping, testing, screenshots |
| **super-analyst** | `/super-analyst` | Elite analytical consulting with 12 professional frameworks |
| **super-writer** | `/super-writer` | Professional content creation with 6 writing methodologies |

---

## HOOKS

22+ lifecycle hooks intercepting/modifying agent behavior.

### Hook Categories

| Category | Hooks | Purpose |
|----------|-------|---------|
| **Orchestration** | chief-orchestrator, sisyphus-orchestrator, start-work | Task coordination and execution |
| **Error Recovery** | session-recovery, edit-error-recovery, anthropic-context-window-limit-recovery | Automatic recovery from failures |
| **Context Management** | directory-agents-injector, directory-readme-injector, compaction-context-injector, rules-injector | Context injection and preservation |
| **Monitoring** | context-window-monitor, todo-continuation-enforcer, empty-task-response-detector | Track execution and enforce completion |
| **Notifications** | background-notification, session-notification, auto-update-checker | OS notifications and updates |
| **Quality Control** | comment-checker, thinking-block-validator, tool-output-truncator | Output quality enforcement |
| **Utilities** | keyword-detector, agent-usage-reminder, auto-slash-command, interactive-bash-session | Convenience features |
| **Memory** | memory-system | Cross-session knowledge persistence |
| **Startup** | startup-config-checker | Initial configuration validation |

### Hook Events

| Event | Timing | Can Block | Use Case |
|-------|--------|-----------|----------|
| PreToolUse | Before tool | Yes | Validate, modify input |
| PostToolUse | After tool | No | Add context, warnings |
| UserPromptSubmit | On prompt | Yes | Inject messages, block |
| Stop | Session idle | No | Inject follow-ups |
| onSummarize | Compaction | No | Preserve context |

---

## TOOLS

### LSP Tools (11)

| Tool | Purpose |
|------|---------|
| `lsp_hover` | Get type info, docs, signature |
| `lsp_goto_definition` | Jump to symbol definition |
| `lsp_find_references` | Find all usages/references |
| `lsp_document_symbols` | Hierarchical outline of file |
| `lsp_workspace_symbols` | Search symbols across workspace |
| `lsp_diagnostics` | Get errors, warnings, hints |
| `lsp_servers` | List available LSP servers |
| `lsp_prepare_rename` | Check if rename is valid |
| `lsp_rename` | Rename symbol across workspace |
| `lsp_code_actions` | Get quick fixes and refactorings |
| `lsp_code_action_resolve` | Apply a code action |

### Other Tools

| Category | Tools | Purpose |
|----------|-------|---------|
| **AST** | `ast_grep_search`, `ast_grep_replace` | Pattern-based code search/replace (25 languages) |
| **File Search** | `grep`, `glob` | Content and file pattern matching |
| **Session** | `session_list`, `session_read`, `session_search`, `session_info` | OpenCode session file management |
| **Background** | `chief_task`, `background_output`, `background_cancel` | Async agent orchestration |
| **Multimodal** | `look_at` | PDF/image analysis |
| **Terminal** | `interactive_bash` | Tmux session control |
| **Commands** | `slashcommand` | Execute slash commands |
| **Skills** | `skill`, `skill_mcp` | Load skills, invoke skill-embedded MCPs |

---

## CONFIGURATION

### Configuration Files

| Level | Path | Priority |
|-------|------|----------|
| Project | `<project>/.opencode/newtype-profile.json` | Highest |
| User | `~/.config/opencode/newtype-profile.json` | Medium |
| System | Built-in defaults | Lowest |

### Example Configuration

```json
{
  "google_auth": true,
  "agents": {
    "chief": { "model": "google/antigravity-claude-opus-4-5-thinking-high" },
    "researcher": { "model": "google/antigravity-gemini-3-pro-high" },
    "fact-checker": { "model": "google/antigravity-gemini-3-pro-high" },
    "archivist": { "model": "google/antigravity-claude-sonnet-4-5" },
    "extractor": { "model": "google/antigravity-gemini-3-flash" },
    "writer": { "model": "google/antigravity-gemini-3-pro-high" },
    "editor": { "model": "google/antigravity-claude-sonnet-4-5" }
  },
  "mcp": {
    "tavily": { "api_key": "tvly-your-api-key" },
    "firecrawl": { "api_key": "fc-your-api-key" },
    "filesystem": { "directories": ["~/Documents", "~/Projects"] },
    "sequential-thinking": true
  },
  "disabled_agents": [],
  "disabled_skills": [],
  "disabled_hooks": [],
  "disabled_mcps": []
}
```

### MCP Servers

| MCP Server | Default | Required Config | Description |
|------------|---------|-----------------|-------------|
| **websearch** (Exa) | Enabled | None | Web search via Exa.ai |
| **sequential-thinking** | Enabled | None | Structured problem-solving |
| **tavily** | Disabled | `api_key` | Advanced web search, crawl, extract |
| **firecrawl** | Disabled | `api_key` | Web scraping and content extraction |
| **filesystem** | Disabled | `directories` | Local file system access |

### Available Models

**Gemini Series:**
- `google/antigravity-gemini-3-pro-high` - High quota Pro version
- `google/antigravity-gemini-3-pro-low` - Low quota Pro version
- `google/antigravity-gemini-3-flash` - Fast response version

**Claude Series (via Antigravity):**
- `google/antigravity-claude-opus-4-5-thinking-high` - High thinking budget Opus
- `google/antigravity-claude-opus-4-5-thinking-medium` - Medium thinking budget
- `google/antigravity-claude-opus-4-5-thinking-low` - Low thinking budget
- `google/antigravity-claude-sonnet-4-5` - Sonnet 4.5
- `google/antigravity-claude-sonnet-4-5-thinking-high` - High thinking budget Sonnet

---

## BUILD & DEVELOPMENT

### Commands

```bash
# Install dependencies
bun install

# Full build
bun run build

# Type check only
bun run typecheck

# Run tests
bun test

# Build schema only
bun run build:schema

# Clean build output
bun run clean
```

### Development Setup

```bash
# Clone and setup
git clone https://github.com/newtype-01/newtype-profile.git
cd newtype-profile
bun install
bun run build

# Test locally - update opencode.json
{
  "plugin": [
    "/path/to/newtype-profile"
  ]
}
```

### Key Technologies

- **TypeScript 5.7+** - Primary language
- **Bun** - Only supported package manager
- **OpenCode Plugin SDK** - Plugin framework
- **@ast-grep/napi** - AST operations
- **Zod** - Schema validation
- **MCP (Model Context Protocol)** - Extended capabilities

---

## RECENT CHANGES

| Version | Date | Change |
|---------|------|--------|
| v1.0.52 | Current | Latest version with memory system improvements |
| v1.0.50 | 2026-01 | Improved memory system with LLM-powered summaries |
| v1.0.43 | 2025-12 | Startup config checker - validates agent model configuration |
| v1.0.41 | 2025-12 | Memory system for cross-session persistence |
| v1.0.29 | 2025-11 | Fix Deputy not executing file edits |
| v1.0.28 | 2025-11 | Remove confrontational SINGLE_TASK_DIRECTIVE from hooks |
| v1.0.27 | 2025-11 | Add forbidden phrases to Deputy prompt |
| v1.0.26 | 2025-11 | Chief uses whitelist (not blocklist) for tool restrictions |
| v1.0.25 | 2025-11 | Fix MCP tool names, improve Deputy task decomposition |
| v1.0.24 | 2025-11 | Add hard tool constraints to Chief |
| v1.0.23 | 2025-11 | Remove `call_omo_agent`, unify to `chief_task` |
| v1.0.22 | 2025-11 | Implement three-layer architecture with Deputy |

---

## NOTES

### Important Patterns

1. **Todo Enforcement** - All complex tasks must use `todowrite` to track progress
2. **Chief Tool Whitelist** - Chief can only use: `chief_task`, `todowrite`, `read`, `glob`, `grep`, LSP readonly tools, Session tools, `background_output`, `look_at`, `skill`, `slashcommand`
3. **Agent Tone** - Deputy and specialists must be collaborative, never refuse tasks
4. **Bun Only** - Never use npm/yarn for package management
5. **Node.js Compatibility** - Use `node:fs`, `node:child_process` instead of Bun-specific APIs

### Anti-Patterns

| Forbidden | Use Instead |
|-----------|-------------|
| `npm` / `yarn` | `bun` |
| `@types/node` | `bun-types` |
| `as any`, `@ts-ignore` | Proper typing |
| Empty `catch {}` | Log and handle errors |
| `Bun.spawn` | `node:child_process` |
| Direct `npm publish` | GitHub Actions workflow |
| High temperature (>0.3) for code | Lower temperature |
| Broad tool access | Explicit `include` list |

### Memory System

Auto-saves conversation summaries to `.opencode/memory/YYYY-MM-DD.md`:
- **Smart Filtering**: System instructions auto-filtered
- **LLM-Powered**: Archivist agent generates intelligent summaries
- **Auto-archive**: Logs older than 7 days consolidated into `.opencode/MEMORY.md`
- **Full Transcripts**: Complete logs in `.opencode/memory/full/<sessionID>.md`

### CLI Commands

```bash
# Interactive setup
bunx newtype-profile install

# Environment diagnostics
bunx newtype-profile doctor

# Run OpenCode session
bunx newtype-profile run

# Authentication management
bunx newtype-profile auth login
```

### Built-in Commands

| Command | Description |
|---------|-------------|
| `/switch newtype` | Switch to newtype-profile |
| `/switch omo` | Switch to oh-my-opencode |
| `/switch none` | Disable all plugins |
| `/memory-consolidate` | Manually trigger memory consolidation |
| `/configure-models` | Interactive model configuration |

---

## AUTHOR

**Created by huangyihe (黄益贺)**

- **YouTube**: https://www.youtube.com/@huanyihe777
- **Twitter**: https://x.com/huangyihe
- **Substack**: https://newtype.pro/
- **知识星球**: https://t.zsxq.com/19IaNz5wK

## LICENSE

This project follows the [SUL-1.0 License](https://github.com/code-yeongyu/oh-my-opencode/blob/master/LICENSE.md) from oh-my-opencode.

## ACKNOWLEDGMENTS

- [oh-my-opencode](https://github.com/code-yeongyu/oh-my-opencode) - Original project
- [OpenCode](https://opencode.ai) - AI programming platform
- [Google Antigravity](https://github.com/NoeFabris/opencode-antigravity-auth) - Model authentication
