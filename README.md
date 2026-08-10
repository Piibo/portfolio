# Portfolio — Peter Trenkle

M.Sc. Medieninformatik (LMU München, 2026), Schwerpunkt Mensch-Computer-Interaktion und KI-gestützte Werkzeuge. Dieses Repo sammelt meine Projekte — jeweils mit Problemstellung, Lösung, meiner Rolle und den eingesetzten Technologien.

## Projekte

| Projekt | Was es ist | Technologien |
|---|---|---|
| [KI-CAD-Assistent für Rhino 8](projekte/ki-cad-assistent/) | Masterarbeit: chatbasierter KI-Assistent mit Human-in-the-Loop-Werkzeugen, evaluiert in einer Nutzerstudie (n = 8) | React, TypeScript, Python, FastAPI, WebSockets, SQLite, Anthropic API |
| [SpiceDispenser](projekte/spice-dispenser/) | KI-gesteuerter Gewürzautomat: Gericht nennen (Sprache/Text), lokales LLM bestimmt Gewürze + Mengen, ESP32-Maschine dosiert ([Video](https://youtu.be/Efl0KOGhpKA)) | C++ (ESP32), PlatformIO, Python, Ollama, faster-whisper |
| [Sendlingers Escape](projekte/sendlingers-escape/) | Escape-Game rund um das Sendlinger Tor München, Teamprojekt im LMU-Game-Development-Praktikum — meine Rolle: 3D-Objekt-Arbeit + erstes Rätsel ([Video](https://youtu.be/RlHncoayMY8)) | Unreal Engine, 3D-Modellierung |
| [Bloomie](projekte/bloomie/) | Gestengesteuerte Schreibtischlampe an einem Roboterarm (HRI-Teamprojekt, LMU) — meine Rolle: Lampenkopf mit verstellbarem Lichtkegel (Zoom-Objektiv-Mechanik, 3D-Druck) + LED-Hardware | MyCobot/ROS, MediaPipe, 3D-Druck, Hardware-Prototyping |
| [IntelliTrack](projekte/intellitrack/) | Indoor-Ortung per WiFi-Fingerprinting: ML-Modell sagt den Raum im Gebäude aus WLAN-Signalstärken vorher — 92 % Genauigkeit (Teamprojekt, LMU) — meine Rolle: Android-App (Dashboard mit Gebäudeplan) | Python, XGBoost, Machine Learning, Android/Kotlin |
| [kemptAInability](projekte/kemptainability/) | Interaktive Verkehrsfluss-Simulation für Kempten: Straßen sperren, Auswirkungen auf Stau/Lärm/CO₂ live sehen (Teamprojekt, sustAInability-Seminar HM+TUM) | React, SUMO, OpenStreetMap, Python |
| [Nüslify](projekte/nueslify/) | Persönliches KI-Radio: KI-kuratierte News gemischt mit der eigenen Spotify-Musik, als PWA mit Live-Deployment (Teamprojekt) — meine Rolle: Interessen-Feature (UI bis DB) + Player-UI | Next.js, TypeScript, tRPC, Spotify-API |

*(Weitere Projekte folgen.)*

## Aufbau

Jedes Projekt liegt unter `projekte/<name>/` mit einer eigenen Seite nach dem Schema: **Problem → Lösung → Meine Rolle → Ergebnis → Technologien → Bilder**.
