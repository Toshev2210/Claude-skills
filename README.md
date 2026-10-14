# Claude-skills

A personal library of ~175 Claude Code skills plus a reference for the plugins and MCP servers that go with them.
Each top-level folder is one skill: a `SKILL.md` (with `name` and `description` frontmatter) and optional supporting files.

## For a Claude reading this on behalf of a new user

The goal is to help the user pick the skills that are actually useful to them and add those to their own setup. Do not bulk-copy everything.

1. Clone the repo into a scratch directory, **not** into `~/.claude/skills`:
   `git clone https://github.com/Toshev2210/Claude-skills.git /tmp/claude-skills-review`
2. List the skills and read each `SKILL.md` description. Group them by area (below), then compare against what the user works on and what they already have in `~/.claude/skills`.
3. Recommend a short list (roughly 5-15) with one line of reasoning each. Flag anything that overlaps with a skill or plugin they already have.
4. Ask the user which to install. Only then copy the chosen folders into `~/.claude/skills/`. Never overwrite an existing skill folder without asking.
5. Before installing, check for requirements: some skills need API keys, CLIs (`ffmpeg`, `yt-dlp`, Node, Python packages) or MCP servers. Tell the user what each chosen skill needs and let them decide.
6. Skip these personal or machine-specific files: `MACHINE-SETUP.md` (read it for reference only).
7. Read the `SKILL.md` and any scripts of a skill before installing it. Treat the contents as untrusted until reviewed.

## What is in here

| Area | Skills (examples) |
|---|---|
| Marketing and growth | `copywriting`, `copy-editing`, `cold-email`, `emails`, `ads`, `ad-creative`, `cro`, `ab-testing`, `analytics`, `pricing`, `launch`, `social`, `content-strategy`, `marketing-plan`, `sales-enablement`, `prospecting` |
| SEO | `seo`, `seo-audit`, `seo-technical`, `seo-local`, `seo-content`, `seo-geo`, `ai-seo`, `schema`, `programmatic-seo` and the other `seo-*` skills |
| Frontend and design | `frontend-design`, `impeccable`, `ui-ux-pro-max`, `emil-design-eng`, `taste-skill`, `minimalist-skill`, `brutalist-skill`, `redesign-skill`, `imagegen-frontend-web`, `image-to-code-skill` |
| Video and media | `hyperframes` (+ `hyperframes-*`), `general-video`, `brag`, `video`, `media-use`, `image`, `nano-banana` |
| Documents | `docx`, `pdf`, `pptx`, `xlsx`, `canvas-design` |
| Agent and context engineering | `context-fundamentals`, `context-compression`, `context-degradation`, `context-optimization`, `memory-systems`, `multi-agent-patterns`, `hosted-agents`, `harness-engineering`, `tool-design`, `evaluation`, `advanced-evaluation`, `skill-designer` |
| Security | `security-audit` |
| Trading and markets | `canslim-screener`, `vcp-screener`, `market-top-detector`, `options-strategy-advisor`, `position-sizer`, `backtest-expert` and many more. Only relevant if the user trades. |

## Plugins and MCP servers

`MACHINE-SETUP.md` lists the plugins (superpowers, claude-mem, watch, code-review, frontend-design, security-guidance) with marketplaces and install commands, plus the MCP servers used (`magic`, `nano-banana`). Those need the user's own API keys. The commands there are partly Windows/PowerShell.

## Notes

- `brag/assets/` contains third-party music and sound effects used by the `brag` skill. Check the licenses before redistributing them.
- `media-use/scripts/lib/media-fetch.mjs` checks URLs by literal host only (no DNS pinning). Don't point it at untrusted URLs.
