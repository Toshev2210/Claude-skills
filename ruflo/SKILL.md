---
name: ruflo
description: AI agent orchestration platform CLI (ruflo) for multi-agent swarms, memory, task management, and autonomous "autopilot" task completion. Use when the user wants to spin up agent swarms, manage long-running multi-agent workflows, or use ruflo's memory/session/task features from the command line.
---

# Ruflo

Ruflo is a CLI-based AI agent orchestration platform, installed globally via `npm install -g ruflo@latest` (https://github.com/ruvnet/ruflo). It is invoked as a regular shell command — there is no MCP server for it.

## Usage

Run via Bash/PowerShell:

```
ruflo <command> [subcommand] [options]
```

### Primary commands
- `ruflo init` — initialize ruflo in the current project directory (creates config/state)
- `ruflo start` — start the orchestration system
- `ruflo status` — show system status
- `ruflo agent ...` — agent management
- `ruflo swarm ...` — swarm coordination
- `ruflo memory ...` — memory management
- `ruflo task ...` — task management
- `ruflo session ...` — session management
- `ruflo mcp ...` — manage ruflo's own MCP integrations
- `ruflo hooks ...` — self-learning workflow hooks

### Advanced commands
- `ruflo neural ...` — neural pattern training / pattern learning
- `ruflo security ...` — security scanning, CVE detection, threat modeling
- `ruflo performance ...` — profiling and benchmarking
- `ruflo embeddings ...` — vector embeddings / semantic search
- `ruflo hive-mind ...` — queen-led consensus multi-agent coordination
- `ruflo guidance ...` — guidance control plane (compile/retrieve/enforce rules)
- `ruflo autopilot ...` — persistent swarm that keeps agents working until all tasks are done

### Utility commands
- `ruflo config ...`, `ruflo doctor`, `ruflo daemon ...`, `ruflo completions`, `ruflo migrate`

## Notes
- First run downloads a local ONNX embedding model (`all-MiniLM-L6-v2`, ~23MB) for semantic memory/search features — this is expected on first invocation.
- For interactive setup in a new project, run `ruflo init wizard`.
- To use ruflo on a task, run the relevant command via Bash and parse its output.
