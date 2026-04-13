# KNOWLEDGE BASE INDEX

**Generated:** 2026-04-02
**Last Updated:** 2026-04-02

---

## OVERVIEW

This is a **mixed-content repository** containing:
1. **newtype OS source code** — an OpenCode plugin providing 8-agent multi-layer orchestration for content production
2. **Content production output** — vape industry articles organized by publication platform
3. **Help center & guidelines** — content creation system documentation and social media workflows

---

## STRUCTURE

```
newtype-profile/
├── src/                    # newtype OS plugin source code
├── docs/                   # Plugin documentation
├── assets/                 # Schema files
├── dist/                   # Compiled output
├── node_modules/           # Dependencies
├── package.json            # npm package config
├── README.md               # Project documentation
├── KNOWLEDGE.md            # This file
├── LICENSE.md              # License
├── CLA.md                  # Contributor agreement
├── bun.lock                # Lock file
├── vape_news/              # Content production output (MAIN CONTENT)
│   ├── .obsidian/          # Obsidian vault config
│   ├── 02 - PROCESSING/    # Raw articles being processed
│   └── 03 - OUTPUT/        # Finished articles by platform
└── AAA-helpcenter/         # Help center & guidelines
    └── agoravape社媒更新- 每周2次/  # Social media update schedules
```

---

## KEY DOCUMENTS

| File | Description | Topics |
|------|-------------|--------|
| README.md | newtype OS main documentation | multi-agent system, CLI, installation |
| AAA-helpcenter/content-creation-system-guide.md | Content creation system technical guide | MCP, 3-layer architecture, memory system |
| docs/orchestration-guide.md | Planning & execution workflow | workflow, task orchestration |
| docs/cli-guide.md | CLI commands reference | command syntax |
| docs/category-skill-guide.md | Skill system documentation | skills, frameworks |

---

## CONTENT STRUCTURE (vape_news/)

### By Platform/Source

| Folder | Platform | Content Type |
|--------|----------|--------------|
| 03 - OUTPUT/agoravape-wordpresssite/ | Agoravape blog | Product reviews, guides |
| 03 - OUTPUT/auvape-wordpresssite/ | AU Vape blog | Australian market content |
| 03 - OUTPUT/medium.com/ | Medium articles | Industry trends, analysis |
| 03 - OUTPUT/chinavapefactory/ | China Vape Factory | Manufacturing content |
| 03 - OUTPUT/mmuc/ | MMUC | Product comparisons |
| 03 - OUTPUT/x.com/ | X (Twitter) threads | Social posts |
| 03 - OUTPUT/discord.com/ | Discord | Community content |
| 03 - OUTPUT/diigo/ | Diigo bookmarks | Curation |
| 03 - OUTPUT/au-reddit/ | Reddit Australia | Community discussions |
| 03 - OUTPUT/forum.planetofthevapes.co.uk/ | UK Forum | Forum posts |
| 03 - OUTPUT/vapingunderground.com/ | US Forum | Forum posts |
| 03 - OUTPUT/vapingcommunity.co.uk/ | UK Community | Community posts |
| 03 - OUTPUT/ceoca/ | CEO.ca | Canadian market |
| 03 - OUTPUT/produce/ | Product descriptions | VOZOL product specs |
| 02 - PROCESSING/01 - Daily-Reading/01 - Article/ | Processing queue | Raw articles |

### Content Topics

- **Product Reviews**: Bang King, Alibarbar, Airmez, VAPME, WASPE, Aivono, Myde
- **Flavor Profiles**: Fruit, Mint, Dessert, Beverage, Tobacco
- **Market Analysis**: Australia, UK, EU (TPD), US, Canada
- **Industry Trends**: 2026 trends, high-puff disposables, rechargeable vs disposable
- **Buying Guides**: Best vapes by region, price range, puff count

---

## HELP CENTER (AAA-helpcenter/)

### Content Creation Guides

| File | Purpose |
|------|---------|
| content-creation-system-guide.md | Technical architecture & MCP integration |
| 新增产品.md | New product onboarding |
| laji.md | Deprecated/archived content |

### Social Media Update Schedules

| File | Platform | Frequency |
|------|----------|-----------|
| agoravape社媒更新- 每周2次/Medium 话题更新.md | Medium | 2x/week |
| agoravape社媒更新- 每周2次/X.com 话题更新.md | X/Twitter | 2x/week |
| agoravape社媒更新- 每周2次/au-reddit.com.md | Reddit | 2x/week |
| agoravape社媒更新- 每周2次/au-reddit.com.md | Forum | 2x/week |
| agoravape社媒更新- 每周2次/话题制定.md | Topic planning | 2x/week |
| auvape社媒更新- 每周2次/auvape.wordpress.site.md | Blog | 2x/week |

---

## FILE TYPES

| Type | Count | Location |
|------|-------|----------|
| Markdown (.md) | 200+ | Root, vape_news/, AAA-helpcenter/ |
| TypeScript (.ts) | 100+ | src/ |
| JSON (.json) | 5+ | Root, assets/, .obsidian/ |
| Config | 3 | .obsidian/ |

---

## OBSIDIAN VAULT

The `vape_news/` folder is an Obsidian vault (contains `.obsidian/` directory):
- Used for content organization and note-taking
- Workspace settings in `.obsidian/workspace.json`
- Graph view data available

---

## NOTES

- **Mixed repository**: Combines software project (newtype OS) with content output
- **Content-first**: Main content is in `vape_news/03 - OUTPUT/` — ~100 articles
- **Multi-platform**: Content targets 10+ platforms (WordPress, Medium, X, Reddit, Forums, Discord)
- **Processing workflow**: Raw articles in `02 - PROCESSING/`, finished in `03 - OUTPUT/`
- **Vape industry**: All content relates to disposable vapes, e-cigarettes, and related accessories
- **Obsidian-enabled**: Content team uses Obsidian for content organization

---

## TOPICS & TAGS

- **vape**: disposable-vape, rechargeable, high-puff, pod-system
- **brands**: Bang-King, Alibarbar, Airmez, VAPME, WASPE, Aivono, VOZOL, Myde
- **markets**: Australia, UK, EU, USA, Canada
- **content**: product-review, buying-guide, flavor-profile, industry-trend
- **platforms**: wordpress, medium, x-com, reddit, forum, discord
- **newtype-os**: multi-agent, orchestration, content-production, opencode-plugin
