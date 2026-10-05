# KI-CAD-Assistent für Rhino 8 — Masterarbeit

**Chatbasierter KI-Assistent, der in Rhino 8 eingebettet ist und Designer:innen 3D-Möbelmodelle über Konversation, visuelle Selektion, Live-Parameter-Slider und Skizzen-Anmerkungen erstellen und bearbeiten lässt.**

| | |
|---|---|
| Kontext | Masterarbeit „Entwerfen mit Künstlicher Intelligenz: Ein KI-gestützter Workflow für den iterativen Möbelentwurf“, M.Sc. Medieninformatik, LMU München (Kooperation TUM Architekturinformatik) |
| Zeitraum | März – August 2026 |
| Rolle | Konzeption, Entwicklung, Studie und Auswertung — allein |
| Code | **[Piibo/rhino-ai-cad-assistant](https://github.com/Piibo/rhino-ai-cad-assistant)** — kuratierte Code-Basis (MCP-Server + Studien-Plugin), MIT-lizenziert. Das Arbeits-Repository bleibt privat, weil es Studiendaten enthält. |

<img src="bilder/abb-ui-werkzeug.png" alt="Chat-Panel des Plugins mit Skizze auf Viewport-Aufnahme, KI-Rückfrage mit Auswahl-Dialog und Objekt-Referenz-Chip" width="420">

*Das Chat-Panel: Eine Skizze auf der Viewport-Aufnahme markiert, wo die Rückenlehne hin soll; die KI stellt eine Rückfrage mit Auswahl-Dialog; im Eingabefeld referenziert ein Chip die zuvor angeklickte Fläche.*

## Problem

Reine Prompt-Werkzeuge degradieren Designer:innen zu Zuschauern: Räumliche Absichten lassen sich sprachlich nur schwer präzise vermitteln („das linke hintere Bein, etwas geschwungener…“). Metrische Angaben funktionieren im Chat robust — lokale, zeigende und richtungsbezogene Bezüge brauchen dagegen sichtbare Selektion, Markierung, Vorschau und Parameter. Die Arbeit untersucht, welche Interaktionswerkzeuge ein chatbasierter KI-CAD-Assistent braucht, damit aus passivem Prompten aktive Modellinteraktion wird.

## Lösung

Ein Rhino-8-Plugin aus zwei Teilen: ein **Python-Backend (FastAPI), das direkt in Rhino läuft**, und eine **Chat-Oberfläche in React**, verbunden über WebSocket. Das Backend lässt das Sprachmodell (Anthropic API) in einer Schleife arbeiten: Das Modell wählt aus **108 Werkzeugen** — etwa einen Regler anlegen oder Varianten zeigen —, das Plugin führt sie in Rhino aus und meldet das Ergebnis zurück, bis die Anfrage erledigt ist.

Die Human-in-the-Loop-Werkzeuge, um die es in der Studie ging:

- **Referenz-Picks:** Geometrie anklicken statt beschreiben
- **Live-Parameter-Slider** mit Undo-sicherer Änderungsbündelung
- **Varianten-Galerien** zum Vergleichen von Entwurfsalternativen
- **Skizzen-Overlays** auf Multi-View-Viewport-Aufnahmen
- **Bestätigungs- und Auswahldialoge** für kontrollierte KI-Aktionen

<img src="bilder/abb-slider-panel.png" alt="Slider-Workflow im Plugin: Bestätigungsdialog vor dem Anlegen, dann das Parameter-Panel mit drei Live-Reglern für Plattendicke, Plattendurchmesser und Tischhöhe" width="440">

*Der Slider-Workflow an einem Beistelltisch: Vor dem Eingriff fragt der Assistent per Bestätigungsdialog nach, korrigiert beim Umsetzen einen eigenen Fehler (achsweise vs. gleichmäßige Skalierung) sichtbar im Chat — und am Ende stehen drei Live-Regler, die die Geometrie direkt in Rhino verändern.*

<img src="bilder/abb-varianten-galerie.png" alt="Varianten-Galerie: Original, gerade, konische und gespreizte Beinform als anklickbare Viewport-Kacheln" width="440">

*Die Varianten-Galerie: drei Beinform-Alternativen (gerade, konisch, gespreizt) als Viewport-Aufnahmen zum Durchschalten — die gewählte Variante wird im Modell aktiv.*

Die Studie steckt im Plugin selbst: Eine einzige Stelle im Code schaltet zwischen den beiden Bedingungen um (nur Chat oder Chat mit Werkzeugen), jede Aktion wird in einer Datenbank protokolliert, und eine Prüfsumme stellt sicher, dass sich Anweisungen und Werkzeuge des Assistenten während der Studie nicht unbemerkt ändern.

## Nutzerstudie & Ergebnis

<img src="bilder/abb-ui-basis.png" alt="Das Chat-Panel in der Basis-Bedingung: reiner Textdialog ohne Interaktionswerkzeuge" width="330">

*Zum Vergleich die `basis`-Bedingung der Studie: gleiche CAD-Kompetenz des Assistenten, aber nur Chat — Absichten müssen rein sprachlich vermittelt werden. Der Kontrast zwischen beiden Bedienformen ist der Kern des Studiendesigns.*

Studie mit **8 Teilnehmenden in 16 Sitzungen**: Jede Person löste Möbelentwurfsaufgaben in beiden Bedingungen. Ausgewertet habe ich die Sitzungen mit einer thematischen Analyse. Daraus entstand ein Modell, wann ein chatbasierter KI-CAD-Assistent welche Werkzeuge braucht — der wissenschaftliche Beitrag der Arbeit.

Einwilligung und Fragebögen waren ins Plugin eingebaut; die Gespräche wurden offline auf dem eigenen Rechner transkribiert.

## Technologien

| Ebene | Eingesetzt |
|---|---|
| Frontend (~13.800 Zeilen TS) | React 19 · TypeScript · Vite · Zustand · Tailwind CSS · Radix UI |
| Backend (~30.700 Zeilen Python) | Python · FastAPI · WebSockets · SQLite · Anthropic API (Streaming + Tool-Use) |
| CAD | Rhino 8 · RhinoCommon · rhinoscriptsyntax · Grasshopper |
| Testing | pytest (68 Backend-Tests) · Vitest · eigene Prüfskripte |
| Research | Studiendesign (within-subjects) · qualitative Interviews · thematische Analyse |

In der Anfangsphase entstand außerdem ein **MCP-Server**, über den Claude Rhino und Grasshopper direkt bedienen konnte. Er baut auf zwei MIT-lizenzierten Open-Source-Projekten auf, die ich deutlich erweitert habe.

## Mit dem Assistenten modelliert

Vier Möbel aus den Research-through-Design-Sessions, jeweils im Dialog mit dem Assistenten in Rhino entstanden — von der Nachbildung von Klassikern bis zum eigenen Entwurf:

<img src="bilder/rtd-04-beistelltisch.png" alt="Beistelltisch mit Rohrgestell, Zeitschriftenablage und Tablett-Platte, modelliert im Dialog mit dem Assistenten" width="420">

*Beistelltisch mit Rohrgestell, Zeitschriftenablage und Tablett-Platte.*

<p>
<img src="bilder/rtd-01-freischwinger.png" alt="Freischwinger-Stuhl nach Thonet-Vorbild" width="240">
<img src="bilder/rtd-02-stool60.png" alt="Stapelhocker nach dem Vorbild des Artek Stool 60" width="240">
<img src="bilder/rtd-03-sideboard.png" alt="Sideboard mit Schiebetüren" width="330">
</p>

*Freischwinger nach Thonet-Vorbild, Hocker nach dem Vorbild des Artek Stool 60, Sideboard mit Schiebetüren.*
