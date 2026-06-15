---
name: nano-banana
description: AI image generation and editing via Google's Gemini 2.5 Flash Image model (nano-banana-mcp MCP server). Use when the user asks to generate a new image from a text prompt, edit/modify an existing image file with a text instruction, or iteratively refine a previously generated image.
---

# Nano Banana (Gemini Image Generation)

This skill wraps the `nano-banana-mcp` MCP server (https://github.com/ConechoAI/Nano-Banana-MCP), which exposes Google Gemini 2.5 Flash Image generation/editing as MCP tools. The server is configured in `~/.claude.json` under `mcpServers.nano-banana` and runs via `npx -y nano-banana-mcp`, authenticated with a `GEMINI_API_KEY`.

## Available MCP tools (prefix `mcp__nano-banana__`)

- **generate_image** — create a new image from a text prompt
- **edit_image** — modify an existing image file using a text prompt, optionally with reference images
- **continue_editing** — iteratively refine the most recently generated/edited image
- **get_last_image_info** — get metadata (path, prompt, etc.) about the most recent image
- **configure_gemini_token** — set/update the Gemini API key at runtime
- **get_configuration_status** — check whether the API key is configured

## Usage notes

- These tools are deferred — use ToolSearch with `select:mcp__nano-banana__generate_image` (etc.) to load the schema before calling.
- Generated images are saved automatically (Windows: Documents folder; macOS/Linux: current working directory).
- For multi-step edits, call `generate_image` first, then `continue_editing` or `edit_image` with the saved image path to iterate.
- If the API key needs rotating, call `configure_gemini_token` with the new key, or update the `GEMINI_API_KEY` env var in `~/.claude.json`.
