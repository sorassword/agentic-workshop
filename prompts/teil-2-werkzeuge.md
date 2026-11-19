# Teil 2: Werkzeuge für deinen Agenten

Kopier die Aufträge in den Chat deines Agenten, egal ob Claude Code, Codex oder Gemini. Lies, was der Agent vorschlägt, bevor du Ja sagst. Du richtest alles für deinen Benutzer ein, dann ist es in jedem Projekt da, auch im neuen Repo aus Teil 3.

## 1. Skills einrichten

Ein Skill ist ein Rezept als Markdown-Datei. Dein Agent liest es erst, wenn deine Bitte dazu passt.

> Kopiere die Ordner aus `vorlagen/skills` in meinem Ordner agentic-workshop in deinen globalen Skill-Ordner (Claude Code: `~/.claude/skills/`, Codex: `~/.agents/skills/`, Gemini: `~/.gemini/config/skills/`). Zeig mir danach, was du angelegt hast.

Test: „Welche Skills kennst du?“ Dein Agent nennt die neuen Skills.

| Skill | Was er macht | Quelle |
| --- | --- | --- |
| website-design | Gestaltungsregeln für deine Website | [vorlagen/skills/website-design](../vorlagen/skills/website-design/SKILL.md) |
| projekt-karte | fügt deiner Website eine Projektkarte hinzu | [vorlagen/skills/projekt-karte](../vorlagen/skills/projekt-karte/SKILL.md) |
| design-brief | Vorbild und Verbotsliste, bevor du baust | [vorlagen/skills/design-brief](../vorlagen/skills/design-brief/SKILL.md) |

### Meine Design-Skills aus den Folien

Fünf davon liegen schon in `vorlagen/skills` und kommen mit dem Auftrag oben in deinen Skill-Ordner. Woher sie stammen und unter welcher Lizenz, steht in [vorlagen/skills/QUELLEN.md](../vorlagen/skills/QUELLEN.md).

| Skill | Was er macht | Im Repo |
| --- | --- | --- |
| frontend-design-direction | klare Designrichtung für Webseiten | [vorlagen/skills/frontend-design-direction](../vorlagen/skills/frontend-design-direction/SKILL.md) |
| motion-foundations | Regeln für Bewegung | [vorlagen/skills/motion-foundations](../vorlagen/skills/motion-foundations/SKILL.md) |
| motion-patterns | fertige Animationsmuster | [vorlagen/skills/motion-patterns](../vorlagen/skills/motion-patterns/SKILL.md) |
| stop-slop | Text ohne KI-Floskeln | [vorlagen/skills/stop-slop](../vorlagen/skills/stop-slop/SKILL.md) |
| unslop | entfernt den KI-Look | [vorlagen/skills/unslop](../vorlagen/skills/unslop/SKILL.md) |

Zwei Skills dürfen wir nicht mitliefern, die holt dein Agent von der Quelle: [design-styles](https://github.com/tombrewsviews/design-styles) (50 Stilrichtungen zum Nachschlagen) und [color-expert](https://github.com/meodai/skill.color-expert) (Farbe und Kontrast).

> Installiere zwei Skills in meinen globalen Skill-Ordner: den Ordner design-styles aus github.com/tombrewsviews/design-styles und das ganze Repo github.com/meodai/skill.color-expert als Ordner color-expert. Lies beide vorher und sag mir, ob etwas Bedenkliches drinsteht.

Weitere Skills findest du auf [github.com/anthropics/skills](https://github.com/anthropics/skills). Lies einen fremden Skill, bevor du ihn nutzt. Er kann Befehle enthalten, die mit deinen Rechten laufen.

## 2. MCP: Context7 anschließen

MCP ist die Steckdosenleiste, an die dein Agent andere Programme anschließt. Context7 holt ihm die aktuelle Anleitung für Tailwind, React und andere Werkzeuge. Es läuft ohne Account.

> Richte mir den HTTP-MCP-Server context7 unter https://mcp.context7.com/mcp für alle meine Projekte ein und zeig mir, ob er verbunden ist.

Gemini trägt den Server in `~/.gemini/config/mcp_config.json` ein. Oder im Terminal, nicht im Chat:

```bash
# Claude Code, für alle Projekte
claude mcp add -s user --transport http context7 https://mcp.context7.com/mcp

# Codex
codex mcp add context7 --url https://mcp.context7.com/mcp
```

Test: Tipp `/mcp` oder frag deinen Agenten, ob context7 verbunden ist. Dann im Chat:

> Bau ein Kontaktformular mit Tailwind. use context7

Nur für ein einzelnes Projekt geht es auch als Datei: Kopier [`vorlagen/mcp/mcp.json`](../vorlagen/mcp/mcp.json) als `.mcp.json` in das Projekt.

## 3. Hooks: ein Befehl an einem festen Punkt

Ein Hook läuft immer, wenn ein bestimmter Moment kommt, zum Beispiel bevor der Agent einen Befehl ausführt. Er läuft mit deinen Rechten. Lies ihn, bevor du ihn übernimmst.

> Richte für alle meine Projekte einen Hook ein, der mich benachrichtigt, wenn du auf mich wartest.

Test: Frag deinen Agenten, in welcher Datei der Hook steht. Claude Code zeigt ihn unter `/hooks`. Codex führt einen neuen Hook erst aus, wenn du ihn unter `/hooks` freigibst. Codex und Gemini kennen kein eigenes Warte-Ereignis, sie melden sich über das Ereignis `Stop`, also wenn sie fertig sind.

Fertige Vorlage für Claude Code auf dem Mac: [`vorlagen/hooks/settings.json`](../vorlagen/hooks/settings.json). Sie enthält zwei Hooks:

- **Notification:** Der Mac meldet sich, wenn Claude auf dich wartet.
- **PreToolUse:** Claude darf kein `rm -rf` ausführen, also keinen ganzen Ordner auf einmal löschen.

> Übernimm die Hooks aus `vorlagen/hooks/settings.json` in meine `~/.claude/settings.json`. Ich nutze Windows oder Linux, passe die Benachrichtigung bitte an mein System an.

Den letzten Satz lässt du auf dem Mac weg.

## Geschafft?

Frag deinen Agenten: „Welche Skills, MCP-Server und Hooks hast du?“ Er nennt website-design, projekt-karte, context7 und deinen Hook.

## 4. Weiter in Teil 3

In Teil 3 baust du in einem neuen Repo deine Portfolio-Website: [teil-3-portfolio.md](teil-3-portfolio.md).

Claude Code liest im Projekt die Datei `CLAUDE.md`, Codex und Gemini (Antigravity) die Datei `AGENTS.md`. Prompt 2 legt die passende Datei für deinen Agenten an.

## Befehle

Die Befehle gelten für Claude Code. Mit Codex oder Gemini fragst du deinen Agenten in normalen Worten, zum Beispiel „Welche MCP-Server hast du?“.

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
