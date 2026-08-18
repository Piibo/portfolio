# Bloomie — gestengesteuerte Schreibtischlampe an einem Roboterarm (HRI-Teamprojekt)

**Bloomie ist eine smarte Schreibtischlampe auf einem Roboterarm, die sich berührungslos über Handgesten steuern lässt** — entstanden als vierköpfiges Teamprojekt im Kurs Human-Robot Interaction (LMU München, 2025).

| | |
|---|---|
| Kontext | Kurs Human-Robot Interaction (HRI), LMU München, 2025 · 4-köpfiges Team |
| Rolle | Lampenkopf mit verstellbarem Lichtkegel (Linsenmechanik nach dem Zoom-Objektiv-Prinzip) + LED-Hardware |
| Projektbericht | **[Paper als PDF](bloomie-paper.pdf)** (ACM-Format) |

<img src="bilder/bloomie-gesamt.jpg" alt="Bloomie: MyCobot-Roboterarm mit dem 3D-gedruckten Lampenkopf, LED-Ring leuchtet violett" width="420">

*Bloomie komplett: der MyCobot-280-Arm mit dem 3D-gedruckten Lampenkopf. Am Kopf sichtbar: die Schrägnut mit Führungsstift (mein Verstellmechanismus) und das ESP8266-Board für die LED-Ansteuerung.*

## Das System

Eine Webcam erfasst die Hand, Googles MediaPipe erkennt in Echtzeit 21 Hand-Landmarken, und ein ROS-System aus drei Nodes (Kamera, Roboter, Licht) übersetzt die Gesten in Bewegungen eines MyCobot-280-Roboterarms. Vier Modi: Gestensteuerung, Follow-Modus (die Lampe folgt der Hand), Licht-Modus und Haltungs-Modus. Da die GPIO-Pins des Roboterarms nicht zugänglich waren, steuert ein externer ESP8266-Mikrocontroller die LED-Ringe.

## Mein Beitrag: der Lampenkopf mit verstellbarem Lichtkegel

<img src="bilder/lampenkopf-nah.jpg" alt="Nahaufnahme des Lampenkopfs: Schrägnut mit Führungsschraube, ESP8266-Board, leuchtender LED-Ring" width="360">

*Der Lampenkopf im Detail: In der Schrägnut läuft der Führungsstift, der beim Rotieren der Rohre die Linse hebt und senkt. Oben das ESP8266-Board (D1 Mini), unten der LED-Ring.*

- **Linsenmechanik nach dem Zoom-Objektiv-Prinzip:** Vor den LEDs sitzt eine bewegliche Linse, die den Lichtkegel stufenlos von breitem Ambient-Licht bis zum eng gebündelten Arbeits-Spot verändert. Umgesetzt über einen Schrägnut-Mechanismus wie in einem Kamera-Zoom: Außen- und Innenrohr tragen gegenläufige Führungsnuten, ein Führungsstift am Linsenhalter greift in beide — rotieren die Rohre gegeneinander, fährt die Linse präzise hoch oder runter.
- **Der Clou dabei:** Die Rotation kommt vom obersten Drehgelenk des Roboterarms selbst — der Mechanismus braucht keinen zusätzlichen Motor.
- **Konstruktion:** Lampenkopf als 3D-Druck, Befestigung am Arm über LEGO-kompatible Pins (Plug-and-Play).
- **LED-Hardware:** Einbau der LED-Ringe samt Ansteuerung im Lampenkopf.

## Technologien

| Ebene | Eingesetzt |
|---|---|
| Robotik | MyCobot 280 M5 · ROS (3-Node-Architektur) · Pymycobot |
| Computer Vision | MediaPipe (Hand-Tracking, 21 Landmarken) · OpenCV · Webcam |
| Licht/Hardware | 3D-gedruckter Lampenkopf · Linsenmechanik (Schrägnut-Prinzip) · ESP8266 (D1 Mini) + LED-Ringe |
