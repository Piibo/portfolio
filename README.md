# Portfolio — Peter Trenkle

M.Sc. Medieninformatik (LMU München, 2026), Schwerpunkt Mensch-Computer-Interaktion und KI-gestützte Werkzeuge. Dieses Repo sammelt meine Projekte — jeweils mit Problemstellung, Lösung, meiner Rolle und den eingesetzten Technologien.

## Projekte

| Projekt | Was es ist | Technologien |
|---|---|---|
| [KI-CAD-Assistent für Rhino 8](projekte/ki-cad-assistent/) | Masterarbeit: chatbasierter KI-Assistent mit Human-in-the-Loop-Werkzeugen, evaluiert in einer Nutzerstudie (n = 8) | React, TypeScript, Python, FastAPI, WebSockets, SQLite, Anthropic API |
| [SpAice](projekte/spice-dispenser/) | KI-gesteuerter Gewürzautomat, komplett selbst konstruiert und gebaut: Gericht nennen (Sprache/Text), lokales LLM bestimmt Gewürze + Mengen, die Maschine dosiert ([Video](https://youtu.be/Efl0KOGhpKA)) | CAD/3D-Druck, C++ (ESP32), PlatformIO, Python, Ollama, faster-whisper |
| [E-Mission Z](projekte/e-mission-z/) | Interaktives Dashboard zu Verkehr und CO₂-Emissionen der Bundesländer 2011–2021: Karte, Zeitreihe und Verkehrsmittel-Aufteilung als verknüpfte Ansichten (Teamprojekt, LMU) — meine Rolle: Zeitreihen-Diagramm, Zeitraum-Slider und die Kopplung der Ansichten ([live](https://www.cip.ifi.lmu.de/~wildva/infovis/)) | React, D3, Recharts, GeoJSON |
| [Sendlingers Escape](projekte/sendlingers-escape/) | Escape-Game rund um das Sendlinger Tor München, Teamprojekt im LMU-Game-Development-Praktikum — meine Rolle: 3D-Objekt-Arbeit + erstes Rätsel ([Video](https://youtu.be/RlHncoayMY8)) | Unreal Engine, 3D-Modellierung |
| [Bloomie](projekte/bloomie/) | Gestengesteuerte Schreibtischlampe an einem Roboterarm (HRI-Teamprojekt, LMU) — meine Rolle: Lampenkopf mit verstellbarem Lichtkegel (Zoom-Objektiv-Mechanik, 3D-Druck) + LED-Hardware | MyCobot/ROS, MediaPipe, 3D-Druck, Hardware-Prototyping |
| [IntelliTrack](projekte/intellitrack/) | Indoor-Ortung per WiFi-Fingerprinting: ML-Modell sagt den Raum im Gebäude aus WLAN-Signalstärken vorher — 92 % Genauigkeit (Teamprojekt, LMU) — meine Rolle: Android-App (Dashboard mit Gebäudeplan) | Python, XGBoost, Machine Learning, Android/Kotlin |
| [GRAB-E](projekte/grab-e/) | Simulierter 5-Achsen-Greifarm, der per Reinforcement Learning greifen und ablegen lernt — selbst implementierte SAC/TD3/DDPG gegen Standard-Baselines (Teamprojekt, LMU) — meine Rolle: Trainings- und Auswertungsinfrastruktur (Seeding, Logging, Baseline-Läufe) | Python, PyTorch, Stable-Baselines3, Unity ML-Agents |
| [kemptAInability](projekte/kemptainability/) | Interaktive Verkehrsfluss-Simulation für Kempten: Straßen sperren, Auswirkungen auf Stau/Lärm/CO₂ live sehen (Teamprojekt, sustAInability-Seminar HM+TUM) — meine Rolle: die komplette Datenpipeline (OSM → SUMO → GeoJSON) | React, SUMO, OpenStreetMap, Python |
| [Nüslify](projekte/nueslify/) | Persönliches KI-Radio: KI-kuratierte News gemischt mit der eigenen Spotify-Musik, als PWA mit Live-Deployment (Teamprojekt) — meine Rolle: Interessen-Feature (UI bis DB) + Player-UI | Next.js, TypeScript, tRPC, Spotify-API |

*(Weitere Projekte folgen.)*

## Aufbau

Jedes Projekt liegt unter `projekte/<name>/` mit einer eigenen Seite nach dem gleichen Aufbau: **worum es geht → wie es gelöst ist → was mein Anteil war → welche Technologien im Einsatz waren**, dazu Bilder oder ein Video, wo vorhanden. Bei Teamprojekten ist mein Beitrag jeweils getrennt ausgewiesen und über Commit-Historie oder Projektbericht belegt.
