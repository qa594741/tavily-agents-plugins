# Tavily Agent Skills

Web search, content extraction, site crawling, URL discovery, and deep research — powered by the Tavily CLI.

## Codex Packaging

This fork adds a Codex-compatible plugin wrapper under `plugins/tavily/` and a repo-local marketplace file at `.agents/plugins/marketplace.json`.

Original upstream repository: [tavily-ai/skills](https://github.com/tavily-ai/skills)

## Installation

### Install in Claude Code

This repository includes the official Claude Code plugin manifest at `.claude-plugin/`.

Add the marketplace, then install the plugin:

```bash
claude plugin marketplace add https://github.com/qa594741/tavily-agents-plugins
claude plugin install tavily@tavily-plugins
```

For a local checkout:

```bash
claude plugin marketplace add <path-to-this-repo>
claude plugin install tavily@tavily-plugins
```

### Install in Codex

This repository also includes a Codex plugin wrapper at `plugins/tavily/` and a Codex marketplace file at `.agents/plugins/marketplace.json`.

```bash
codex plugin marketplace add <path-to-this-repo>
codex plugin add tavily@tavily-agents-plugins
```

For the GitHub repository:

```bash
codex plugin marketplace add https://github.com/qa594741/tavily-agents-plugins
codex plugin add tavily@tavily-agents-plugins
```

### Install as raw agent skills

If you only want the skill files without plugin marketplace management:

```bash
npx skills add https://github.com/tavily-ai/skills
```

### Install the Tavily CLI

The skills require the Tavily CLI (`tvly`) to be installed. It lives in its own repository: [tavily-ai/tavily-cli](https://github.com/tavily-ai/tavily-cli).

```bash
curl -fsSL https://cli.tavily.com/install.sh | bash
```

Or install manually:

```bash
uv tool install tavily-cli   # or: pip install tavily-cli
```

### Authenticate

```bash
tvly login --api-key tvly-YOUR_KEY
# or: tvly login                      (opens browser for OAuth)
# or: export TAVILY_API_KEY=tvly-...
```

Get an API key at [tavily.com](https://tavily.com).

## Available Skills

| Skill | Description |
|-------|-------------|
| **[tavily-search](skills/tavily-search/SKILL.md)** | Search the web with LLM-optimized results. Supports domain filtering, time ranges, and multiple search depths. |
| **[tavily-extract](skills/tavily-extract/SKILL.md)** | Extract clean markdown/text content from specific URLs. Handles JS-rendered pages. |
| **[tavily-crawl](skills/tavily-crawl/SKILL.md)** | Crawl websites and extract content from multiple pages. Save as local markdown files. |
| **[tavily-map](skills/tavily-map/SKILL.md)** | Discover all URLs on a website without extracting content. Faster than crawling. |
| **[tavily-research](skills/tavily-research/SKILL.md)** | Comprehensive AI-powered research with citations. Multi-source synthesis in 30-120s. |
| **[tavily-cli](skills/tavily-cli/SKILL.md)** | Overview skill with workflow guide, install/auth instructions. |
| **[tavily-best-practices](skills/tavily-best-practices/SKILL.md)** | Reference docs for building production-ready Tavily integrations. |

## Workflow

Start simple, escalate when needed:

1. **Search** — Find pages on a topic (`tvly search "query" --json`)
2. **Extract** — Get content from a specific URL (`tvly extract "https://..." --json`)
3. **Map** — Discover URLs on a site (`tvly map "https://..." --json`)
4. **Crawl** — Bulk extract from a site section (`tvly crawl "https://..." --output-dir ./docs/`)
5. **Research** — Deep multi-source analysis (`tvly research "topic" --model pro`)
