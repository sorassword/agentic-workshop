# Workshop-Repo: Hinweise für den Agenten

Dieses Repo gehört zum Agentic Coding Workshop der DHC am 20.11.2026. Die Person vor dir lernt gerade, mit einem Coding-Agenten zu arbeiten. Erklär in einfachem Deutsch, was du tust, und frag, bevor du etwas installierst, löschst oder außerhalb dieses Ordners änderst.

## Was hier liegt

- `prompts/teil-2-werkzeuge.md`: Skills, MCP und Hooks einrichten
- `prompts/teil-3-portfolio.md`: Prompts für die Portfolio-Website (Vite, React, Tailwind)
- `prompts/second-brain.md`: Second Brain aus alten Chats
- `vorlagen/skills/`: drei Skills (website-design, projekt-karte, design-brief)
- `vorlagen/mcp/mcp.json`, `vorlagen/hooks/settings.json`: Vorlagen für Claude Code
- `downloads/`: Folien, Handout und alle Vorlagen als ZIP

## Wohin die Vorlagen gehören

| | Claude Code | Codex | Gemini (Antigravity) |
| --- | --- | --- | --- |
| Skills für alle Projekte | `~/.claude/skills/` | `~/.agents/skills/` | `~/.gemini/config/skills/` |
| Regeln im Projekt | `CLAUDE.md` | `AGENTS.md` | `AGENTS.md` |
| MCP für alle Projekte | `claude mcp add -s user ...` | `codex mcp add ...` | `~/.gemini/config/mcp_config.json` |
| Hooks für alle Projekte | `~/.claude/settings.json` | `~/.codex/hooks.json` | `~/.gemini/config/hooks.json` |

Codex und Gemini haben kein Ereignis für „wartet auf Eingabe“. Ein Benachrichtigungs-Hook hängt dort am Ereignis `Stop`.

## Regeln

- Nichts über die Person erfinden: keine Noten, Zahlen, Firmen oder Abschlüsse.
- Keine Passwörter oder Schlüssel in Dateien schreiben, die ins Git-Repo gehen.
- Die Dateien in diesem Repo nicht umschreiben. Eigene Arbeit entsteht in Teil 3 im neuen Repo `mein-portfolio`.
