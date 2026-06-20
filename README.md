# Multiplexer Core Patch

Stabilisiert den MCP-Multiplexer-Core in Hermes Agent Native Shell.

## Problem

Der Multiplexer-Core verursachte bei hoher Last und parallelen MCP-Verbindungen Instabilitäten:
- Verbindungsabbrüche bei gleichzeitigen Sessions
- Race Conditions im Request-Routing
- Fehlende Fehlerbehandlung bei Timeout-Szenarien

## Lösung

Dieser Patch adressiert die Core-Stability-Probleme durch:
- Robusteres Connection-Handling mit Retry-Logik
- Thread-safe Request-Multiplexing
- Verbesserte Timeout-Behandlung und Error-Recovery
- Saubere Session-Isolation

## Installation

```bash
# Patch in dein Hermes Agent Native Shell Verzeichnis kopieren
cp MULTIPLEXER_PATCH.diff /pfad/zu/hermes-agent-native-shell/
cd /pfad/zu/hermes-agent-native-shell

# Patch anwenden
git apply MULTIPLEXER_PATCH.diff
```

## Inhalt

| Datei | Beschreibung |
|-------|-------------|
| `MULTIPLEXER_PATCH.diff` | Vollständiger Core-Patch als Unified Diff |

## Kompatibilität

- **Hermes Agent Native Shell** v0.15.0+
- Python 3.10+
- MCP Protocol v1.0

## Lizenz

MIT
