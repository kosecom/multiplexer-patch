# Multiplexer Core Patch

Stabilisiert den MCP-Multiplexer-Core in Hermes.

## Problem

Der Multiplexer-Core verursachte mehrere kritische Probleme:

### Stabilität
- Verbindungsabbrüche bei gleichzeitigen Sessions
- Race Conditions im Request-Routing
- Fehlende Fehlerbehandlung bei Timeout-Szenarien

### Telegram Multi-Agent Routing
- Alle Agents haben ausschließlich über den Main Agent geantwortet
- Nachrichten wurden zwar korrekt verarbeitet, aber die Antwort ging immer über den Main-Agent-Kanal zurück statt über den zuständigen Agent
- Kein sauberes Session-Routing zwischen mehreren Agenten

## Lösung

Dieser Patch adressiert die Core-Probleme durch:

- Robusteres Connection-Handling mit Retry-Logik
- Thread-safe Request-Multiplexing
- Verbesserte Timeout-Behandlung und Error-Recovery
- Saubere Session-Isolation
- Korrektes Multi-Agent-Session-Routing (Telegram und andere Kanäle)

## Installation

```bash
cp MULTIPLEXER_PATCH.diff /pfad/zu/hermes/
cd /pfad/zu/hermes
git apply MULTIPLEXER_PATCH.diff
```

## Inhalt

| Datei | Beschreibung |
|-------|-------------|
| `MULTIPLEXER_PATCH.diff` | Vollständiger Core-Patch als Unified Diff |

## Kompatibilität

- **Hermes** v0.15.0+
- Python 3.10+
- MCP Protocol v1.0

## Lizenz

MIT
