# Codebase

Pi package providing one extension at `extensions/ide-integration/index.ts`.

Repository README now links GitHub-hosted release asset `demo.mp4` so the demo is visible from the README on GitHub.

The extension connects to Claude Code IDE WebSocket lock files from `~/.claude/ide` on `session_start`, only when an active lock has `transport: "ws"`, live PID, auth token, and a workspace folder exactly matching Pi's current `cwd`.

Runtime state is minimal: one WebSocket, connected IDE metadata, non-empty current selection, and current Pi extension context. It performs MCP initialize + `notifications/initialized`, replies `{}` to IDE-initiated JSON-RPC requests, tracks non-empty `selection_changed`, and handles `at_mentioned` by pasting an `@file#x-y` reference plus trailing space into the active Pi editor message.

Footer status shows connection state, IDE name, PID, and current selection using the same `file#x-y` range format as insertions. Lost IDE connections are retried automatically. `/ide` discovers matching endpoints for the current project and lets the user reconnect, switch IDE endpoints, or choose `None` to disconnect and disable auto-reconnect. No tools, prompt injection, custom footer, or automatic selection injection.
