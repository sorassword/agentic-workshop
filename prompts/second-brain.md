# Second Brain einrichten

Dein Agent macht aus deinen alten Chats durchsuchbare Markdown-Dateien. Dort findet er Antworten und nennt Fundstelle und Datum.

## Ein Auftrag reicht

Kopier das in Claude Code oder Codex:

> Richte mir das Second Brain von github.com/22wayan/obsidiyan-engine ein. Lies zuerst docs/INSTALL_FOR_AGENTS.md und arbeite die Anleitung Schritt für Schritt ab. Erklär mir jeden Schritt in einfachen Worten und frag, bevor du etwas installierst oder meine Chats liest. Teste zuerst mit Demodaten und zeig mir einen echten Suchtreffer. Sag mir danach, wie ich meine alten Chats einlese und meinen Wissensgraphen in Obsidian ansehe.

Dein Agent prüft den Rechner (git, uv, Python 3.12), fragt vor jeder Installation und liest deine Chats erst nach deinem Ja.

Nutzt dein Agent ein Cloud-Modell, gehen die Suchtreffer an dessen Anbieter. Lies vertrauliche Chats nur ein, wenn das für dich passt.

## Deine alten Chats holen

| Dienst | Klickpfad | Hinweis |
| --- | --- | --- |
| ChatGPT | chatgpt.com, Settings, Data controls, Export data | Link in der Mail gilt 24 Stunden |
| Claude | claude.ai, Settings, Privacy, Export data | Link gilt 24 Stunden, nicht in der Handy-App |
| Gemini | takeout.google.com, Meine Aktivitäten, nur „Gemini-Apps“ | „Gemini“ allein enthält nur die Gems |
| Copilot | account.microsoft.com/privacy, Copilot, Export all activity history | nur mit privatem Microsoft-Konto |
| Claude Code, Codex | liegen schon auf deinem Rechner | `~/.claude/projects` und `~/.codex/sessions` |

Stoß den Export heute an. Die Mails kommen oft erst nach Stunden.
