# SpiceDispenser — KI-gesteuerter Gewürzautomat

**Gericht nennen (per Sprache oder Text) → ein lokales LLM bestimmt die typischen Gewürze samt Grammmengen → die Maschine dosiert sie automatisch.** Ein Embedded-Projekt, das KI-Anbindung, Spracherkennung und Hardware-Steuerung verbindet.

[![Demo-Video ansehen](https://img.youtube.com/vi/Efl0KOGhpKA/hqdefault.jpg)](https://youtu.be/Efl0KOGhpKA)

▶️ **[Demo-Video auf YouTube](https://youtu.be/Efl0KOGhpKA)**

| | |
|---|---|
| Jahr | 2025 |
| Rolle | Eigenständige Umsetzung: Firmware, Host-Software und Hardware-Ansteuerung |
| Code | [Piibo/SpiceDispenser](https://github.com/Piibo/SpiceDispenser) |

## Wie es funktioniert

1. **Eingabe:** Der Nutzer nennt ein Gericht — wahlweise getippt oder gesprochen. Die Spracheingabe läuft komplett lokal über faster-whisper mit Voice-Activity-Detection (webrtcvad).
2. **Gewürz-Bestimmung (Python-Host):** Ein lokales LLM (Ollama, Mistral) erzeugt eine JSON-Liste typischer Gewürze mit Mengen in Gramm, skalierbar nach Portionen und Schärfe-Intensität. Damit das robust bleibt: Wikipedia-Plausibilitätscheck (DE/EN), ob es das Gericht wirklich gibt; Synonym-Normalisierung und Fuzzy-Abgleich gegen eine Gewürz-Whitelist; Fallback-Modus, wenn das LLM kein valides JSON liefert; harte Unter- und weiche Obergrenzen mit Warnungen gegen Halluzinationen.
3. **Dosierung (ESP32-Firmware):** Der Host schickt das Ergebnis an einen ESP32-C6. Ein Schrittmotor dreht das Gewürzkarussell zur richtigen Position, ein Servo löst die Dosierung aus. Dazu entprellte Taster-Bedienung und JSON-Verarbeitung direkt auf dem Mikrocontroller.

## Was ich dabei gelernt/gezeigt habe

- **Embedded-Entwicklung:** C++ auf ESP32-C6 (Arduino-Framework, PlatformIO), Schrittmotor- und Servo-Ansteuerung auf Pin-Ebene, Debouncing, WLAN/HTTP auf dem Mikrocontroller
- **Praktische LLM-Integration mit Guardrails:** lokales Modell statt Cloud, strikte Prompts, Validierung und Normalisierung der Ausgaben — der interessante Teil ist nicht der LLM-Aufruf, sondern das Robust-Machen dagegen, dass er Unsinn liefert
- **Lokale Spracherkennung:** Whisper-ASR + Voice-Activity-Detection ohne Cloud-Dienste
- **Systemintegration:** Python-Host und Mikrocontroller-Firmware, die über eine definierte Schnittstelle zusammenspielen

## Technologien

| Ebene | Eingesetzt |
|---|---|
| Firmware (~840 Zeilen C/C++) | ESP32-C6 · Arduino-Framework · PlatformIO · ESP32Servo · ArduinoJson · U8g2 |
| Host (~570 Zeilen Python) | Python · Ollama (Mistral, lokal) · faster-whisper · webrtcvad · Wikipedia-API · pyserial |
