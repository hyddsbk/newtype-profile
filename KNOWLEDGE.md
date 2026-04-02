# KNOWLEDGE BASE INDEX

**Generated:** 2026-03-30
**Total Files:** 100+ TypeScript, 10 markdown, 3 config

---

## OVERVIEW

newtype-profile is an OpenCode plugin that provides an 8-agent multi-layer orchestration system for content production. It extends OpenCode with specialized agents (Chief, Deputy, Researcher, Fact-Checker, Archivist, Extractor, Writer, Editor) and built-in skills for research, writing, editing, and fact-checking workflows.

---

## STRUCTURE

```
newtype-profile/
├── src/
│   ├── agents/          # 8 agent definitions (chief, deputy, researcher, etc.)
│   ├── hooks/           # Lifecycle hooks (chief-orchestrator, think-mode, etc.)
│   ├── tools/           # LSP, AST-Grep, Grep, Glob, chief-task, skill, session-manager
│   ├── features/        # Background agents, skill loaders, task toast manager
│   ├── auth/            # Google Antigravity OAuth
│   ├── config/          # Zod schemas
│   ├── mcp/             # MCP servers (exa, tavily, firecrawl)
│   ├── shared/          # Common utilities
│   └── index.ts         # Main plugin entry
├── docs/                # Documentation
├── script/              # Build utilities
├── package.json         # npm package config
└── KNOWLEDGE.md         # This file
```

## KEY DOCUMENTS

| File | Description |
|------|-------------|
| README.md | Main documentation |
| AGENTS.md | Project knowledge base |
| docs/orchestration-guide.md | Planning & execution workflow |
| docs/cli-guide.md | CLI commands |
| docs/category-skill-guide.md | Skill system |

---

## TOPICS

- **Multi-Agent System**: 8-agent orchestration (Chief, Deputy, Researcher, Fact-Checker, Archivist, Extractor, Writer, Editor)
- **Content Creation**: Writing, editing, research, fact-checking workflows
- **OpenCode Plugin**: Extends OpenCode AI assistant
- **MCP Integration**: Tavily, Firecrawl, Exa web search
- **TypeScript**: Full type safety with Zod schemas
- **Three-Layer Architecture**: Chief → Deputy → Specialists execution model
- **Built-in Skills**: Super Analyst, Super Writer, Super Fact-Checker, Super Editor, Super Interviewer, Super Obsidian
