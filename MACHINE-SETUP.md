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

Installed on the Mac (as of 2026-10-14):

| Plugin | Marketplace | Version |
|---|---|---|
| `superpowers` | `superpowers-dev` (obra/superpowers) | 6.1.1 |
| `claude-mem` | `thedotmack` (thedotmack/claude-mem) | 13.10.1 |
| `watch` | `claude-video` (bradautomates/claude-video) | 0.2.0 |
| `code-review` | `claude-plugins-official` (anthropics/claude-plugins-official) | f359d43b4060 |
| `frontend-design` | `claude-plugins-official` | f359d43b4060 |
| `security-guidance` | `claude-plugins-official` | 2.0.13 |

```bash
claude plugin marketplace add obra/superpowers
claude plugin marketplace add thedotmack/claude-mem
claude plugin marketplace add bradautomates/claude-video
# claude-plugins-official (anthropics/claude-plugins-official) is built in / added automatically

claude plugin install superpowers@superpowers-dev
claude plugin install claude-mem@thedotmack
claude plugin install watch@claude-video
claude plugin install code-review@claude-plugins-official
claude plugin install frontend-design@claude-plugins-official
claude plugin install security-guidance@claude-plugins-official
```

This recreates the `enabledPlugins` / `extraKnownMarketplaces` block in `~/.claude/settings.json`.

`watch` needs `GROQ_API_KEY` (preferred) or `OPENAI_API_KEY` in `~/.config/watch/.env` for the Whisper fallback on videos without captions.

Note: the commands in this guide were written on Windows (PowerShell). On macOS use Homebrew (`brew install node python gh`) instead of `winget`.

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
