# Tools

Interesting tools, repos, and CLI utilities worth trying or referencing.

## Claude Code Optimization

- **[rtk-ai/rtk](https://github.com/rtk-ai/rtk)** — CLI proxy that strips redundant whitespace and compresses tool output. ~20-30% token reduction.
- **[juliusbrussee/caveman](https://github.com/juliusbrussee/caveman)** — Terse-output skill. Drops conversational filler without affecting reasoning.
- **[phuryn/claude-usage](https://github.com/phuryn/claude-usage)** — Long-term Claude Code usage breakdown by session/day/week.
- **[Gronsten/claude-usage-monitor](https://github.com/Gronsten/claude-usage-monitor)** — Real-time 5-hour window + active session token monitor with color thresholds.

## Browser & Content

- **[vercel-labs/agent-browser](https://github.com/vercel-labs/agent-browser)** — Browser via accessibility tree instead of screenshots. ~82% fewer tokens. `npm i -g agent-browser && agent-browser install`

## Code Understanding

- **[tirth8205/code-review-graph](https://github.com/tirth8205/code-review-graph)** — Persistent AST map via Tree-sitter. 6.8× fewer tokens on reviews, up to 49× on daily coding. MCP integration.

## Agent Infrastructure

- **OpenClaw** — Autonomous agent that runs from vault context. Can read Obsidian vault, find connections, make decisions on your behalf.
- **Obsidian CLI** — Gives Claude Code access to vault files + inter-relationships (backlinks, graph). The bridge between your notes and the agent.
