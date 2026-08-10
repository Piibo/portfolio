# kemptAInability — interaktive Verkehrsfluss-Simulation für Kempten (Teamprojekt)

**Was passiert mit dem Verkehr einer Stadt, wenn ihre wichtigste Brücke gesperrt wird?** kemptAInability macht das erlebbar: eine interaktive Verkehrssimulation für Kempten, in der Bürger:innen und Stadtplaner:innen Straßen per Fingertipp sperren und sofort sehen, wie sich Verkehrsfluss, Stau, Lärm und CO₂-Emissionen verändern — entwickelt rund um die real geplante Sperrung der St.-Mang-Brücke.

![Verkehrsfluss-Simulation](bilder/trafficFlow.png)

| | |
|---|---|
| Kontext | sustAInability-Seminar, Hochschule München + TU München, 2025 · 4-köpfiges Team |
| Rolle | Datenpipeline: OSM→SUMO-Netzkonvertierung · Co-Autor (zwei der sechs Report-Teile) |
| Code | [fio-la/Sustainable_Mobility](https://github.com/fio-la/Sustainable_Mobility) (öffentlich) |
| Bericht | **[Paper als PDF](kemptainability-paper.pdf)** |

## Die Idee

Professionelle Verkehrssimulationen (SUMO, Vissim) sind für Laien unzugänglich. kemptAInability übersetzt sie in ein zugängliches Werkzeug: eine Karte der Stadt, auf der man Szenarien wie die Brückensperrung durchspielt und die Auswirkungen als Heatmaps (Stau, Lärm, CO₂) direkt sieht — mit Gamification-Elementen, die nachhaltige Verkehrskonfigurationen belohnen. Eingebettet in den UN-Nachhaltigkeitsrahmen (SDG 11: Nachhaltige Städte und Gemeinden).

## Technischer Aufbau

1. **Daten:** OpenStreetMap-Straßennetz von Kempten via Overpass-Turbo-Queries, bereinigt mit JOSM und eigenen Python-Skripten (osmnx, geopandas, pyproj)
2. **Simulation:** Konvertierung in ein SUMO-Netz (netconvert/netedit) für die Verkehrsmodellierung
3. **Frontend:** SUMO-Daten als GeoJSON in einer React/Vite-App — animierte Verkehrssimulation mit Zeitsteuerung, interaktiver Barrieren-Platzierung, Heatmap-Overlays und Echtzeit-Metriken

![Barrieren-Platzierung im Straßennetz](bilder/Barriers.png)

## Mein Beitrag

- **OSM→SUMO-Netzkonvertierung:** Umwandlung des bereinigten OpenStreetMap-Netzes in ein valides SUMO-Verkehrsnetz (`netconvert`-Workflow, `map.net.xml`-Generierung) samt Dokumentation des Konvertierungs-Workflows im Repo
- **Co-Autor des Reports:** verantwortlich für zwei der sechs Projektteile

## Technologien

React · Vite · GeoJSON · SUMO (Verkehrssimulation) · OpenStreetMap/Overpass · Python (osmnx, geopandas, pyproj) · wissenschaftliches Schreiben

<!-- TODO: Peters konkrete Rolle präzisieren (welche zwei Projektteile?); Link zum Code-Repo, falls öffentlich -->
