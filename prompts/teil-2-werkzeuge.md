# Teil 2: Werkzeuge für deinen Agenten

Kopier die Aufträge in den Chat von Claude Code oder Codex. Lies, was der Agent vorschlägt, bevor du Ja sagst.

## 1. Skills einrichten

Ein Skill ist ein Rezept als Markdown-Datei. Dein Agent liest es erst, wenn deine Bitte dazu passt. Die zwei Skills aus dem Workshop liegen in [`vorlagen/skills/`](../vorlagen/skills/).

> Kopiere die Ordner `vorlagen/skills/website-design` und `vorlagen/skills/projekt-karte` aus meinem Ordner agentic-workshop in mein Projekt. Für Claude Code nach `.claude/skills/`, für Codex nach `.agents/skills/`. Zeig mir danach, was du angelegt hast.

Test: „Welche Skills kennst du in diesem Projekt?“ Dein Agent nennt beide.

Weitere Skills findest du auf [github.com/anthropics/skills](https://github.com/anthropics/skills). Lies einen fremden Skill, bevor du ihn nutzt. Er kann Befehle enthalten, die mit deinen Rechten laufen.

## 2. MCP: Context7 anschließen

MCP ist die Steckdosenleiste, an die dein Agent andere Programme anschließt. Context7 holt ihm die aktuelle Anleitung für Tailwind, React und andere Werkzeuge. Es läuft ohne Account.

Im Terminal, nicht im Chat:

```bash
# Claude Code
claude mcp add --transport http context7 https://mcp.context7.com/mcp

# Codex
codex mcp add context7 --url https://mcp.context7.com/mcp
```

Oder als Datei: Kopier [`vorlagen/mcp/mcp.json`](../vorlagen/mcp/mcp.json) als `.mcp.json` in dein Projekt. Claude Code fragt beim nächsten Start einmal, ob der Server laufen darf.

Test: Tipp `/mcp` in Claude Code. Context7 steht dort als verbunden. Dann im Chat:

> Bau ein Kontaktformular mit Tailwind. use context7

## 3. Hooks: ein Befehl an einem festen Punkt

Ein Hook läuft immer, wenn ein bestimmter Moment kommt, zum Beispiel bevor der Agent einen Befehl ausführt. Er läuft mit deinen Rechten, lies ihn also vorher.

Am einfachsten lässt du ihn deinen Agenten bauen:

> Richte einen Hook ein, der mich benachrichtigt, wenn du auf mich wartest. Zeig mir vorher, was du in welche Datei schreibst.

Test: Tipp `/hooks` in Claude Code. Der neue Hook steht in der Liste.

Fertige Vorlage für Claude Code auf dem Mac: [`vorlagen/hooks/settings.json`](../vorlagen/hooks/settings.json). Sie enthält zwei Hooks:

- **Notification:** Der Mac meldet sich, wenn Claude auf dich wartet.
- **PreToolUse:** Claude darf kein `rm -rf` ausführen, also keinen ganzen Ordner auf einmal löschen.

> Übernimm die Hooks aus `vorlagen/hooks/settings.json` in `.claude/settings.json` in meinem Projekt. Ich nutze Windows oder Linux, passe die Benachrichtigung bitte an mein System an.

Den letzten Satz lässt du auf dem Mac weg.

## 4. Dein Agent lernt dich kennen

> Leg eine AGENTS.md für meine Website an oder ergänze die CLAUDE.md, falls es eine gibt. Frag mich vorher nach Zielgruppe, Inhalt und Stil.

Beantworte seine Fragen und öffne dann einen neuen Chat.

> Was weißt du über meine Website?

Nennt er dein Ziel, hat es geklappt.

## Befehle

| Befehl | Was er macht |
| --- | --- |
| `/init` | schreibt einen ersten Entwurf der Projektdatei |
| `/memory` | Gedächtnisdateien bearbeiten |
| `/mcp` | zeigt verbundene Werkzeuge |
| `/hooks` | zeigt eingerichtete Hooks |
| `/clear` | startet einen neuen Chat |

## Fünf Regeln für jeden Agenten

1. **Ergebnis prüfen.** Stimmt alles, was über dich drinsteht? Agenten erfinden gern Noten und Abschlüsse.
2. **Freigabe lesen.** Beim Veröffentlichen, Bezahlen und Löschen liest du erst die Frage.
3. **Keine Passwörter ins Repo.** Schlüssel gehören in eine Umgebungsvariable.
4. **Echte Daten schützen.** Adresse und Noten nur dort eingeben, wo du den Datenschutz kennst.
5. **Fremde Skills lesen.** Ein Skill oder Hook läuft mit deinen Rechten.
