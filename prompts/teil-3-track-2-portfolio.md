# Teil 3, Track 2: Website mit Portfolio

Die Prompts stammen aus dem Begleitdokument von Yannik. Das Word-Dokument liegt unter [`downloads/`](../downloads/).

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
Ich möchte eine persönliche Website inklusive Portfolio für GitHub Pages bauen.
Meine Antworten:
1. Wer bin ich (Name, Studiengang/Rolle, Fokus): [HIER AUSFÜLLEN]
2. Zielgruppe (z.B. Recruiter, Praktikum, Kommilitonen): [HIER AUSFÜLLEN]
3. 2 bis 3 Projekte oder Stationen, die ich zeigen will: [HIER AUSFÜLLEN]
4. Gewünschtes Design (z.B. ruhig und redaktionell, hell/dunkel, klare Kontraste): [HIER AUSFÜLLEN]
5. Kontaktlinks (GitHub, LinkedIn, E-Mail): [HIER AUSFÜLLEN]

Fasse meine Antworten kurz zusammen und stelle maximal 3 Rückfragen. Noch keinen Code.
```

### Prompt 2: Architektur & Bausteine

Trennt Inhalt, Design und Logik.

```text
Definiere auf Basis meiner Antworten in ARCHITEKTUR.md:
1. Sinn, Zweck, Zielgruppe und die Sektionen (Hero, Über mich, Projekte, Stationen, Kontakt).
2. Bausteine: data/profile.json (Inhalte), tokens.css (Farben/Schriften), style.css (Layout & Animation), app.js, index.html.
3. Tech-Stack: Reines HTML/CSS/JS ohne Build-Tool, lauffähig in Live Preview und GitHub Pages.
```

### Prompt 3: Design & Animation recherchieren

Vergleicht Gestaltung und Skills.

```text
Recherchiere auf Basis von ARCHITEKTUR.md zwei Gestaltungs- und Technikansätze:
- Wie setze ich Typografie, Farbhierarchie und Abstände um, damit die Seite eigenständig wirkt?
- Welche dezenten Animationen (CSS-Transitions, IntersectionObserver) passen ohne Überladung?
- Welche Regeln gehören dafür in CLAUDE.md oder einen Design-Skill?
Empfiehl den besten Ansatz für heute. Noch keinen Code.
```

### Prompt 4: Plan & schrittweise Umsetzung

Nach jedem Schritt in Live Preview prüfen.

```text
Erstelle auf Basis unserer Entscheidung:
1. CLAUDE.md (Stil-, Tonalitäts- und Design-Regeln, keine Klischees).
2. PLAN.md mit 4 kleinen Schritten (1: data/profile.json & tokens.css, 2: index.html & style.css, 3: Design-/Animations-Feinschliff über Skill, 4: Mobile- und Kontrast-Check).
Zeige mir den Plan. Setze danach immer nur den Schritt um, den ich freigebe.
```

## 3. Stand sichern

```bash
git add . && git commit -m "Architektur und Prototyp" && git push
```

Auf GitHub unter Settings -> Pages den Branch main auswählen. Nach etwa einer Minute ist deine Website online.
