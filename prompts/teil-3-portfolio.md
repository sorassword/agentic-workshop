# Teil 3: Deine persönliche Portfolio-Website

Du baust mit Vite, React (TypeScript), Tailwind CSS und Lucide Icons eine Website mit fünf Abschnitten und stellst sie über GitHub Pages online. Dieselben Schritte stehen im Handout auf Seite 3 und 4 ([`downloads/workshop-handout.pdf`](../downloads/workshop-handout.pdf)).

Die Prompts funktionieren mit Claude Code, Codex und Gemini. Claude Code schreibt seine Projektregeln in `CLAUDE.md`, Codex und Gemini (Antigravity) in `AGENTS.md`. Die Prompts sagen das jeweils dazu.

Du steuerst: Lies jeden Vorschlag, frag bei unnötiger Komplexität nach und entscheide selbst.

## Schritt A: Neues Repo öffnen und Dev-Server starten

1. Leg auf [github.com/new](https://github.com/new) ein leeres Public-Repo `mein-portfolio` an, ohne README.
2. In VS Code: `Shift+Cmd+P` (Windows: `Strg+Shift+P`), dann **Git: Clone**, Repo-URL einfügen und in Dokumente öffnen.
   Ohne GitHub-Konto: leeren Ordner `mein-portfolio` in Dokumente anlegen und per **File, Open Folder…** öffnen.
3. Menü **Terminal, New Terminal** öffnen, Node prüfen und das Projekt starten:

```bash
node -v && npm -v
# Nur falls Node.js fehlt (danach neues Terminal öffnen):
# Mac:     brew install node
# Windows: winget install OpenJS.NodeJS.LTS

npm create vite@latest . -- --template react-ts
npm install
npm install tailwindcss @tailwindcss/vite lucide-react
npm run dev
```

Geschafft, wenn http://localhost:5173 im Browser läuft. Fragt `npm create vite` wegen `.git` nach, wähl **Ignore files and continue**.

## Schritt B: Planen, dann Abschnitt für Abschnitt bauen

Schick die Prompts nacheinander in den Chat deines Agenten und lies jede Antwort.

### Prompt 1: Steckbrief und Rückfragen

Klammern ausfüllen, noch kein Code.

```text
Ich möchte meine persönliche Portfolio-Website mit Vite, React (TypeScript), Tailwind CSS und Lucide Icons für GitHub Pages bauen.
Meine Antworten:
1. Wer bin ich (Name, Studiengang/Rolle, Fokus): [HIER AUSFÜLLEN]
2. Zielgruppe (z.B. Recruiter, Praktikum, Kunden): [HIER AUSFÜLLEN]
3. 2 bis 3 Projekte (Name + kurze Wirkung): [HIER AUSFÜLLEN]
4. Stationen / Lebenslauf (Studium, Jobs, Engagement): [HIER AUSFÜLLEN]
5. Gewünschter Stil (z.B. ruhig & redaktionell, hell/dunkel): [HIER AUSFÜLLEN]
6. Kontaktlinks (GitHub, LinkedIn, E-Mail): [HIER AUSFÜLLEN]
Fasse mein Ziel kurz zusammen und stelle mir maximal 4 gezielte Rückfragen zu Tonalität, visueller Richtung und Prioritäten der Abschnitte. Schreibe noch keinen Code.
```

### Prompt 2: Architektur und Design-Skill

Nach deinen Antworten auf die Rückfragen.

```text
Lege auf Basis meiner Antworten zwei Steuerungsdateien an (noch keinen App-Code):
1. ARCHITEKTUR.md:
   - Ziel, Zielgruppe und die 5 Abschnitte: Hero, Über mich, Projekte, Stationen/CV, Kontakt.
   - Stack: Vite + React (TypeScript) + Tailwind CSS (@tailwindcss/vite) + Lucide Icons.
   - Struktur: src/data/profile.ts (Inhalte), src/index.css (Design-Tokens), src/components/Hero.tsx, About.tsx, Projects.tsx, Timeline.tsx, Contact.tsx.
2. CLAUDE.md (falls du Codex oder Gemini bist: AGENTS.md):
   - Verbindliche Design-, Typografie- und Kontrastregeln auf Basis meines Skills "website-design" aus Teil 2.
   - Keine generischen Standard-Layouts, mobile Ansicht von Anfang an mitdenken.
Zeige mir beide Dateien zur Prüfung, bevor wir weitergehen.
```

### Prompt 3: Plan, Design-Tokens und eigene Daten

```text
Erstelle auf Basis von ARCHITEKTUR.md und CLAUDE.md (bzw. AGENTS.md):
1. PLAN.md mit 5 Bauschritten (1 Hero, 2 Über mich, 3 Projekte, 4 Stationen/CV, 5 Kontakt).
2. Richte @tailwindcss/vite in vite.config.ts und unsere Design-Tokens in src/index.css ein.
3. Lege alle meine echten Daten sauber strukturiert in src/data/profile.ts an.
Baue noch keine fertigen Sektionen. Zeige mir zuerst PLAN.md.
```

### Prompt 4: Abschnitt für Abschnitt bauen

Prüf jeden Schritt auf localhost:5173.

```text
Starte mit Schritt 1 aus PLAN.md und baue ausschließlich Hero.tsx (inkl. Navigation) nach dem Skill "website-design" und CLAUDE.md (bzw. AGENTS.md).
Nutze nur meine echten Daten aus src/data/profile.ts (erfinde nichts) und prüfe, dass http://localhost:5173 fehlerfrei läuft.
Warte auf mein Feedback, bevor du den nächsten Abschnitt (About.tsx → Projects.tsx → Timeline.tsx → Contact.tsx) baust.
```

Ein neues Projekt nachtragen? Sag „Füg ein Projekt hinzu“, dann greift der Skill `projekt-karte` aus Teil 2.

### Prompt 5: GitHub Pages vorbereiten

Wenn alle fünf Abschnitte stehen.

```text
Mache das Projekt bereit für GitHub Pages (Repo-Name: mein-portfolio):
1. Ergänze base: '/mein-portfolio/' in vite.config.ts.
2. Erstelle .github/workflows/deploy.yml für das automatische Deployment über GitHub Actions.
3. Führe npm run build aus und behebe eventuelle Fehler.
```

## Schritt C: In zwei Minuten live

Öffne über das **+** im Terminal ein zweites Terminal. Im ersten läuft noch `npm run dev`.

```bash
git add .
git commit -m "Persoenliche Portfolio-Website"
git push
```

Fragt Git nach Name, E-Mail oder Login? Nimm links in VS Code **Source Control, Sign in with GitHub, Commit & Sync**.

Letzter Klick auf GitHub: Repo öffnen, **Settings, Pages, Source: GitHub Actions**. Nach rund 60 Sekunden ist deine Website unter `https://DEIN-NAME.github.io/mein-portfolio/` erreichbar.
