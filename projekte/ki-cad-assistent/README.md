# KI-CAD-Assistent für Rhino 8

**KI-Assistent für die CAD-Software Rhino 8: Designer:innen erstellen und bearbeiten damit 3D-Möbelmodelle per Chat, Klick, Regler und Skizze.**

<img src="bilder/abb-ui-werkzeug.png" alt="Chat-Panel des Plugins mit Skizze auf Viewport-Aufnahme, KI-Rückfrage mit Auswahldialog und Objekt-Referenz-Chip" width="420">

*Das Chat-Panel: Eine Skizze auf der Viewport-Aufnahme markiert, wo die Rückenlehne sitzen soll; die KI stellt eine Rückfrage mit Auswahldialog; im Eingabefeld referenziert ein Chip die zuvor angeklickte Fläche.*

<a href="https://youtu.be/Qb64zsemRec"><img src="https://img.youtube.com/vi/Qb64zsemRec/maxresdefault.jpg" alt="Vorschaubild des Demo-Videos: Rhino AI Assistant, KI-Plugin für Rhino 8" width="420"></a>

▶️ **[Demo-Video auf YouTube](https://youtu.be/Qb64zsemRec)**

| | |
|---|---|
| Kontext | Masterarbeit „Entwerfen mit Künstlicher Intelligenz: Ein KI-gestützter Workflow für den iterativen Möbelentwurf“, M.Sc. Medieninformatik, LMU München, März bis August 2026 (Kooperation TUM Architekturinformatik) |
| Rolle | Konzeption, Entwicklung, Studie und Auswertung |
| Code | [Piibo/rhino-ai-cad-assistant](https://github.com/Piibo/rhino-ai-cad-assistant): kuratierte Code-Basis (MCP-Server + Studien-Plugin), MIT-lizenziert. Das Arbeits-Repository bleibt privat, weil es Studiendaten enthält. |
| Arbeit | Auf Anfrage |

## Was das Plugin kann

Neben dem Chat bietet das Plugin Werkzeuge, mit denen man direkt am Modell arbeitet:

- **Referenzen per Klick:** Geometrie anklicken statt beschreiben
- **Live-Regler:** Maße direkt am Modell verändern; eine Reglerbewegung lässt sich in einem Schritt rückgängig machen
- **Variantengalerien:** Entwurfsalternativen nebeneinander vergleichen
- **Skizzen:** auf Aufnahmen des Modells aus mehreren Ansichten zeichnen
- **Bestätigungs- und Auswahldialoge:** KI-Aktionen kontrolliert freigeben

<img src="bilder/abb-slider-panel.png" alt="Slider-Workflow im Plugin: Bestätigungsdialog vor dem Anlegen, dann das Parameter-Panel mit drei Live-Reglern für Plattendicke, Plattendurchmesser und Tischhöhe" width="440">

*Der Slider-Workflow an einem Beistelltisch: Vor dem Eingriff fragt der Assistent per Bestätigungsdialog nach, korrigiert beim Umsetzen einen eigenen Fehler (achsweise vs. gleichmäßige Skalierung) sichtbar im Chat. Am Ende stehen drei Live-Regler, die die Geometrie direkt in Rhino verändern.*

<img src="bilder/abb-varianten-galerie.png" alt="Variantengalerie: Original, gerade, konische und gespreizte Beinform als anklickbare Viewport-Kacheln" width="440">

*Die Variantengalerie: drei Beinform-Alternativen (gerade, konisch, gespreizt) als Viewport-Aufnahmen zum Durchschalten. Die gewählte Variante wird im Modell aktiv.*

## Mit dem Assistenten modelliert

Vier Möbel aus den Research-through-Design-Sessions, jeweils im Dialog mit dem Assistenten in Rhino entstanden, von der Nachbildung von Klassikern bis zum eigenen Entwurf:

<img src="bilder/rtd-04-beistelltisch.png" alt="Beistelltisch mit Rohrgestell, Zeitschriftenablage und Tablett-Platte, modelliert im Dialog mit dem Assistenten" width="420">

*Beistelltisch mit Rohrgestell, Zeitschriftenablage und Tablett-Platte.*

<p>
<img src="bilder/rtd-01-freischwinger.png" alt="Freischwinger-Stuhl nach Thonet-Vorbild" width="240">
<img src="bilder/rtd-02-stool60.png" alt="Stapelhocker nach dem Vorbild des Artek Stool 60" width="240">
<img src="bilder/rtd-03-sideboard.png" alt="Sideboard mit Schiebetüren" width="330">
</p>

*Freischwinger nach Thonet-Vorbild, Hocker nach dem Vorbild des Artek Stool 60, Sideboard mit Schiebetüren.*

## Wie es gebaut ist

Ein Rhino-8-Plugin aus zwei Teilen: ein **Python-Backend (FastAPI), das direkt in Rhino läuft**, und eine **Chat-Oberfläche in React**, verbunden über WebSocket. Das Backend lässt das Sprachmodell (Anthropic API) in einer Schleife arbeiten: Das Modell wählt aus **108 Werkzeugen** (etwa einen Regler anlegen oder Varianten zeigen), das Plugin führt sie in Rhino aus und meldet das Ergebnis zurück, bis die Anfrage erledigt ist.

Die Studie steckt im Plugin selbst: Eine einzige Stelle im Code schaltet zwischen den beiden Bedingungen um (nur Chat oder Chat mit Werkzeugen), jede Aktion wird in einer Datenbank protokolliert, und eine Prüfsumme stellt sicher, dass sich Anweisungen und Werkzeuge des Assistenten während der Studie nicht unbemerkt ändern.

In der Anfangsphase entstand außerdem ein **MCP-Server**, über den das Sprachmodell Claude Rhino und Grasshopper direkt bedienen konnte. Er baut auf zwei MIT-lizenzierten Open-Source-Projekten auf; die Werkzeugmodule sind neu implementiert und um eine eigene SubD-Schicht ergänzt.

## Die Studie

Räumliche Absichten lassen sich sprachlich nur schwer präzise vermitteln („das linke hintere Bein, etwas geschwungener …“). Die Arbeit untersucht deshalb, welche Werkzeuge ein chatbasierter KI-CAD-Assistent neben dem Chat braucht.

Studie mit **8 Teilnehmenden in 16 Sitzungen**: Jede Person löste Möbelentwurfsaufgaben einmal nur mit Chat und einmal mit den Werkzeugen. Ausgewertet habe ich die Sitzungen mit einer thematischen Analyse. Einwilligung und Fragebögen waren ins Plugin eingebaut; die Gespräche wurden lokal und offline transkribiert.

<img src="bilder/abb-ui-basis.png" alt="Das Chat-Panel in der Basis-Bedingung: Textdialog mit Bildanhang, ohne Interaktionswerkzeuge" width="330">

*Zum Vergleich die `basis`-Bedingung der Studie: gleiche CAD-Kompetenz des Assistenten, aber nur Chat mit Text und Bildanhang, ohne Klick, Regler und Skizze.*

**Zentrale Befunde:**

- **Chat für Maße, Zeigen für Ort und Form:** Maße und Änderungen am ganzen Modell ließen sich im Chat gut beschreiben. Ging es darum, an welcher Stelle, in welche Richtung oder in welcher Form sich etwas ändern sollte, reichte Sprache in mehreren Fällen nicht aus. Dann halfen Skizze und Klick, die Regler dienten der Feinjustage.
- **Wechseln ist ein Arbeitsprinzip:** Die Teilnehmenden wechselten je nach Entwurfsschritt zwischen Sprache, Zeigen und Reglern, teils vorausschauend, teils nach einem Fehlversuch.
- **Kontrolle braucht sichtbare Eingriffspunkte:** Wie viel Kontrolle die Teilnehmenden nach eigener Aussage erlebten, hing mit verständlichen Eingriffspunkten, nachvollziehbaren Modellzuständen und umkehrbaren Änderungen zusammen.
- **Präferenz:** Am Ende wählten alle acht Teilnehmenden die Variante mit Werkzeugen. Das zeigt eine Vorliebe, keinen nachgewiesenen Leistungsvorteil.

Daraus entstand ein Modell aus vier Schritten, die sich wiederholen: die Absicht am sichtbaren Modell festmachen, die Anweisung mit dem Assistenten aushandeln, die Ausführung an Eingriffspunkten steuern und das Ergebnis prüfen, überarbeiten und weiterentwerfen. Dieses Modell ist der wissenschaftliche Beitrag der Arbeit.

## Technologien

| Ebene | Eingesetzt |
|---|---|
| Frontend (~13.800 Zeilen TS) | React 19 · TypeScript · Vite · Zustand · Tailwind CSS · Radix UI |
| Backend (~30.700 Zeilen Python) | Python · FastAPI · WebSockets · SQLite · Anthropic API (Streaming + Tool-Use) |
| CAD | Rhino 8 · RhinoCommon · rhinoscriptsyntax · Grasshopper |
| Tests | pytest (68 Backend-Tests) · Vitest · eigene Prüfskripte |
| Studie | Studiendesign (Within-Subjects) · qualitative Interviews · thematische Analyse |
