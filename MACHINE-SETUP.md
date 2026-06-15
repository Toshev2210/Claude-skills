# Machine Setup — Replicating this Claude Code environment

This repo (`~/.claude/skills`) covers skills, plugins reference, and Cowork scheduled-task templates.
The pieces below are **not** in git (machine config / secrets) and must be set up manually on a new device.

## 1. Prerequisites

```powershell
winget install -e --id OpenJS.NodeJS.LTS --accept-package-agreements --accept-source-agreements
winget install -e --id Python.Python.3.12 --accept-package-agreements --accept-source-agreements
winget install -e --id GitHub.cli --accept-package-agreements --accept-source-agreements
npm install -g @anthropic-ai/claude-code
npm install -g ruflo@latest
pip install numpy pandas scipy statsmodels requests jsonschema pyyaml pytest pillow opencv-python
```

## 2. Clone this skills repo

```powershell
gh auth login --hostname github.com --git-protocol https --web
git clone https://github.com/Toshev2210/Claude-skills.git "$env:USERPROFILE\.claude\skills"
```

## 3. Plugin marketplaces & plugins (`~/.claude/settings.json`)

```powershell
claude plugin marketplace add obra/superpowers
claude plugin marketplace add thedotmack/claude-mem
# claude-code-plugins (anthropics/claude-code) is built in / added automatically

claude plugin install superpowers@superpowers-dev
claude plugin install code-review@claude-code-plugins
claude plugin install frontend-design@claude-code-plugins
claude plugin install security-guidance@claude-code-plugins
claude plugin install claude-mem@thedotmack
```

This recreates the `enabledPlugins` / `extraKnownMarketplaces` block in `~/.claude/settings.json`.

## 4. MCP servers (`~/.claude.json` -> top-level `mcpServers`)

Two MCP servers are configured. Re-add them on the new device (replace the keys with your real values — rotate first if they were ever shared in plaintext):

```powershell
claude mcp add magic --scope user --env API_KEY="<21st-dev-magic-api-key>" -- npx -y @21st-dev/magic@latest
claude mcp add nano-banana --scope user --env GEMINI_API_KEY="<gemini-api-key>" -- npx -y nano-banana-mcp
```

- `magic` — 21st.dev component generation (get key at https://21st.dev/magic/console)
- `nano-banana` — Gemini 2.5 Flash Image generation/editing (get key at https://aistudio.google.com/app/apikey)

## 5. Cowork scheduled tasks

Templates are in `cowork-scheduled-tasks/`. Open Cowork on the new device → Scheduled Tasks → recreate
`daily-morning-briefing` and `weekly-briefing` using those SKILL.md files as the task instructions.
(`trade-alert-2026-06-12` was intentionally excluded — private one-off alert.)

## 6. Connectors (Google Calendar, Gmail, Drive, etc.)

Nothing to do — these are tied to your Anthropic account (vladimirtoshev09@gmail.com), not the device.
They'll already be available once you sign in.

## 7. Verify

```powershell
claude mcp list
claude plugin list
```
