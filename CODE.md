# Codebase

Pi package providing one extension at `extensions/ide-integration/index.ts`.

The extension connects to Claude Code IDE WebSocket lock files from `~/.claude/ide` on `session_start`, only when an active lock has `transport: "ws"`, live PID, auth token, and a workspace folder exactly matching Pi's current `cwd`.

Runtime state is minimal: one WebSocket, connected IDE metadata, non-empty current selection, and current Pi extension context. It performs MCP initialize + `notifications/initialized`, replies `{}` to IDE-initiated JSON-RPC requests, tracks non-empty `selection_changed`, and handles `at_mentioned` by pasting an `@file#Lx-Ly` reference into the active Pi editor message.

Footer status shows connection state, IDE name, PID, and current selection. No tools, prompt injection, or automatic selection injection.
