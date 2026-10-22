# RyeDB

**Persistent memory and a message channel for coding agents.**

Coding agents lose their place when the context is compacted, repeat approaches that already failed, and start subagents blind. RyeDB keeps project memory in a local database next to your code and puts a small, budgeted brief back into every agent and subagent. A rule a human has verified can stop a tool call before it runs.

```mermaid
flowchart LR
  subgraph agents[Your coding agents]
    CC[Claude Code]
    SA[Subagents]
    CX[Codex]
  end
  agents -->|hooks: before and after every tool call| D
  agents -->|MCP tools| D
  D[RyeDB daemon<br/>one per project, local] --> DB[(SQLite)]
  D -->|brief, warnings, inbox| agents
  P[Programs, CI, workers] -->|channel port or SDK| D
  H[A person] -->|verify, retire, issue credentials| D
```

## What it does

- **Memory that survives compaction.** Rules, decisions and known failures with their fixes, budgeted into a short brief.
- **Verified versus claimed.** Agents can propose; only a person (or the owner's merge of the project's rules file) can verify, and only verified rules can block.
- **Notes that notice they are stale.** A note that names a file is marked when that file changes. In our test an unmarked note was believed in 6 of 6 runs; the marked one in 0 of 6.
- **RyeChannel.** A persistent, ordered log for agents and programs: tasks that stay open until answered, receipts, presence, per-agent credentials.
- **Local first.** One SQLite file per project, loopback only, no cloud. Hooks answer in well under a millisecond at the median.

## Repositories

| Repository | What it is |
|---|---|
| `core` | The engine, daemon, hooks, MCP server and CLI. Developed in a private repository; not publicly available yet |
| [`MCP`](https://github.com/RyeDB/MCP) | The agent tool contract, client setup and conformance tests: the public interface of the MCP server |
| [`SDK`](https://github.com/RyeDB/SDK) | TypeScript client for RyeChannel (the agent-to-agent channel) |
| [`.github`](https://github.com/RyeDB/.github) | This profile, contributing guide, security policy, issue and PR templates |

## Honest status

Early. Works today with Claude Code and Codex on Linux and macOS, on one machine. Not yet: public availability of core, Windows, hosted sync, team memory, Codex subagent coverage. Every claim about effect comes from small tests whose raw data and limits are kept with the code, including results that did not favour RyeDB.

## Licences

| | |
|---|---|
| `SDK`, `MCP`, cookbooks, `.github` | Apache-2.0 (open source) |
| `core` | Proprietary, all rights reserved |

Report a vulnerability through [SECURITY.md](https://github.com/RyeDB/.github/blob/main/SECURITY.md).
