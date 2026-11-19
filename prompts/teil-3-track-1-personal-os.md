# Teil 3, Track 1: Personal OS

Die Prompts stammen aus dem Begleitdokument von Yannik. Das Handout liegt unter [`downloads/workshop-handout.pdf`](../downloads/workshop-handout.pdf).

KI ist ein Werkzeug, kein Autopilot. Lies jeden Vorschlag gegen, hinterfrage unnötige Komplexität und entscheide selbst, wofür du KI einsetzt.

## 1. Projekt-Repo anlegen

Leg auf github.com ein neues, leeres Repo an, klone es und öffne es in VS Code:

```bash
cd ~/Desktop
git clone https://github.com/DEIN-NAME/DEIN-REPO.git
cd DEIN-REPO && code .
```

## 2. Prompts zum Kopieren

Erst planen, dann bauen. Schick die Prompts nacheinander und lies jede Antwort.

### Prompt 1: Persönliche Fragen

Klammern ausfüllen, absenden.

```text
Ich möchte ein eigenes Personal OS als lokales Repo mit Cockpit-Dashboard aufbauen.
Meine Antworten:
1. Wichtigste 3 Lebensbereiche (z.B. Studium, Finanzen, Projekte): [HIER AUSFÜLLEN]
2. Tägliche/wöchentliche Daten (Notizen, PDFs, CSVs, Aufgaben): [HIER AUSFÜLLEN]
3. Externe Tools für später (z.B. Google Calendar, Notion): [HIER AUSFÜLLEN]
4. Fokus im Cockpit (z.B. Tagesaufgaben, Fristen, Gewohnheiten): [HIER AUSFÜLLEN]

Fasse meine Antworten kurz zusammen und stelle maximal 3 Rückfragen. Noch keinen Code.
```

### Prompt 2: Architektur & Bausteine

Legt Struktur und Tech-Stack fest.

```text
Definiere auf Basis meiner Antworten in ARCHITEKTUR.md:
1. Sinn und Zweck (2 Sätze) und maximal 4 Kernfunktionen für Version 1.
2. Bausteine: CLAUDE.md (Codex und Gemini: AGENTS.md), 00-inbox/, Bereichsordner, data/state.json, dashboard/index.html.
3. Tech-Stack: Markdown/JSON/CSV + reines HTML/CSS/JS für VS Code Live Preview (ohne Server).
4. Wie Daten von 00-inbox/ über dich in data/state.json und das Dashboard fließen.
```

### Prompt 3: Ansätze recherchieren

Vergleicht Wege vor der Umsetzung.

```text
Recherchiere anhand von ARCHITEKTUR.md zwei Ansätze für die Datenanbindung:
- Ansatz A: Rein dateibasiert (00-inbox/ -> Skill -> data/state.json -> Dashboard).
- Ansatz B: Spätere Anbindung externer Tools über Export-Skripte oder MCP-Server.
Vergleiche Vor- und Nachteile und empfiehl den besten Start für heute. Noch keinen Code.
```

### Prompt 4: Plan & schrittweise Umsetzung

Nach jedem Schritt in Live Preview prüfen.

```text
Erstelle auf Basis unserer Entscheidung:
1. CLAUDE.md, bei Codex und Gemini AGENTS.md (Ordnerdisziplin, Datenformate, Inbox-Workflow).
2. PLAN.md mit 4 kleinen Schritten (1: Ordner & Beispieldaten, 2: Dashboard in dashboard/index.html, 3: Inbox-Skill in .claude/skills/, 4: Test mit einem Eintrag in 00-inbox/).
Zeige mir den Plan. Setze danach immer nur den Schritt um, den ich freigebe.
```

## 3. Stand sichern

```bash
git add . && git commit -m "Architektur und Prototyp" && git push
```

Zu Hause kannst du weitere Lebensbereiche als Ordner ergänzen und später Kalender oder To-do-Apps über MCP-Server anbinden.
