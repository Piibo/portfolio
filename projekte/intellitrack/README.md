# IntelliTrack — Indoor-Ortung per WiFi-Fingerprinting und Machine Learning (Teamprojekt)

**Wo bin ich im Gebäude, wenn GPS nicht funktioniert?** IntelliTrack sagt den Raum, in dem sich ein Smartphone befindet, allein aus den empfangenen WLAN-Signalstärken vorher — als Grundlage für Indoor-Navigation über einen Gebäudeplan, z. B. in Unikliniken, Universitäten oder öffentlichen Gebäuden.

| | |
|---|---|
| Kontext | Vierköpfiges Teamprojekt, LMU München (2024) |
| Ergebnis | **92 % Raum-Vorhersagegenauigkeit** (XGBoost, 5-fach-Kreuzvalidierung) |
| Bericht | Wissenschaftliches Paper im ACM-Format ([Repo](https://github.com/Piibo/IntelliTrackLatex)) |

## Ansatz

1. **Datensammlung:** Eine eigene Android-App scannt in festen Intervallen alle empfangbaren WLAN-Netze und erfasst Signalstärke (dBm), SSID/BSSID, Frequenz und Kanalbreite — geloggt in verschiedenen Räumen samt angrenzender Außenbereiche, mit randomisierten Bewegungsmustern gegen Verzerrung.
2. **Preprocessing:** Normalisierung der Signalstärken, Ausreißer-Filterung, Feature-Extraktion und Dimensionsreduktion. Ein zentraler Befund dabei: 5-GHz-Netze liefern deutlich konsistentere Daten und trennen Räume besser als 2,4 GHz.
3. **Modellvergleich:** Decision Tree als Baseline (80,8 %), Random Forest (86,4 %), XGBoost (92,0 %) — jeweils mit 5-fach-Kreuzvalidierung evaluiert; Hyperparameter-Tuning per GridSearch.

## Technologien

Python · Machine Learning (XGBoost, Random Forest, Decision Trees) · Feature Engineering · Kreuzvalidierung, GridSearch · Android (WiFi-Scanning-App) · wissenschaftliches Schreiben (ACM-Paper, LaTeX)

<!-- TODO nachtragen: meine konkrete Rolle im Team (App? ML? Datensammlung? Paper?); Kursname; ggf. Code-Repos verlinken, wenn öffentlich -->
