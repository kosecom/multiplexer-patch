# Multiplexer Core Patch

Fixes critical stability and routing issues in the Hermes MCP multiplexer core.

## Key Fixes

### Multi-Agent Session Routing (Telegram & Other Channels)

**Problem:** All agents were replying exclusively through the main agent channel. Messages were processed correctly, but responses always routed back through the main agent instead of the responsible agent.

**Solution:** Implemented proper session isolation and routing logic. Each agent now correctly handles its own session responses.

### Core Stability

**Problem:** The multiplexer core caused instability under load and parallel MCP connections:
- Connection drops during concurrent sessions
- Race conditions in request routing
- Missing error handling in timeout scenarios

**Solution:**
- Robust connection handling with retry logic
- Thread-safe request multiplexing
- Improved timeout handling and error recovery
- Clean session isolation

## Installation

```bash
cp MULTIPLEXER_PATCH.diff /path/to/hermes/
cd /path/to/hermes
git apply MULTIPLEXER_PATCH.diff
```

## Contents

| File | Description |
|------|-------------|
| `MULTIPLEXER_PATCH.diff` | Complete core patch as unified diff |

## Compatibility

- **Hermes** v0.15.0+
- Python 3.10+
- MCP Protocol v1.0

## License

MIT
