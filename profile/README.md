# RyeDB

Persistent memory and a message channel for coding agents.

Coding agents lose their place when the context window is compacted, repeat failing approaches, and start subagents blind. RyeDB keeps project memory in a local database next to your code and puts a small, budgeted brief back into every agent and subagent, so they stay on course.

- **Memory that survives compaction:** rules, decisions and known failures, with fixes.
- **Verified versus claimed:** agents can propose, only a human or CI can confirm, and only confirmed rules can block a tool call.
- **RyeChannel:** a persistent, ordered log for agents and subagents to talk to each other.
- **Local first:** one SQLite file per project, no network. Works with Claude Code and Codex.
- **Measured:** hook latency, and effect on real agent runs, with the raw data and the limits written down.

## Repositories

| Repository | What it is |
|---|---|
| [`core`](https://github.com/RyeDB/core) | Engine, daemon, Claude Code hooks, MCP server and CLI |
| [`mcp`](https://github.com/RyeDB/mcp) | The MCP server's public home: tool contract, client setup, conformance checks |
| [`sdk`](https://github.com/RyeDB/sdk) | Client SDK (scaffold) |

Status: early development. Licensed under Apache-2.0.
