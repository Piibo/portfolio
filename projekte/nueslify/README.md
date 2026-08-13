# Nüslify — dein persönliches KI-Radio (Teamprojekt)

**Ein Radiosender, der nur für dich sendet:** Nüslify holt per KI aktuelle Nachrichten zu deinen Interessen, bereitet sie auf und mischt sie mit deiner eigenen Spotify-Musik — wie ein klassisches Radioprogramm aus Moderation und Musik, nur eben personalisiert auf Interessen und Hörgewohnheiten.

| | |
|---|---|
| Kontext | Kurs Intelligent User Interfaces (IUI), LMU München, WiSe 2023/24 · 5-köpfiges Team |
| Rolle | Frontend: Interessen-Feature (UI bis Datenbank) und Teile des Player-Dashboards |
| Code | [NoelHuibers/nueslify](https://github.com/NoelHuibers/nueslify) (öffentlich, GPL-3.0) |
| Demo | [nueslify.vercel.app](https://nueslify.vercel.app) |

## Die Idee

Radio lebt von der Mischung aus Information und Musik — aber das Programm bestimmt der Sender. Nüslify dreht das um: Die News kommen KI-kuratiert zu den Themen, die dich interessieren, die Musik kommt aus deinem eigenen Spotify-Account. Umgesetzt als Progressive Web App, die sich wie eine native App nutzen lässt.

## Mein Beitrag

<img src="bilder/interests-feature.png" alt="Das Interessen-Feature: Profil, News-Musik-Balance-Slider, KI-Auswahl, Radio-Host-Stil, Musik-Favoriten und News-Genre-Kacheln" width="480">

*Das Interessen-Feature — mein Hauptbeitrag: Profil, News↔Musik-Balance, KI- und Host-Auswahl, Musik-Favoriten und die Genre-Kacheln für die News-Personalisierung.*

Ich war mit 32 Commits der zweitaktivste Entwickler im fünfköpfigen Team, Schwerpunkt Frontend:

- **Das Interessen-Feature von UI bis Datenbank:** die Seiten und Formulare, mit denen Nutzer:innen ihre Themeninteressen auswählen (React/Next.js), samt Styling, tRPC-API-Router und Anbindung an das Drizzle-Datenbankschema — die Grundlage für die personalisierte News-Auswahl
- **Teile des Player-Dashboards:** News-Player als eigenständige Komponente herausgelöst und gestylt, Spotify-Button, Navbar-Styling, Ladezustände
- Kleinere Beiträge: Genre-Übersetzungen (Internationalisierung), Icons und Bild-Assets

## Technologien

| Ebene | Eingesetzt |
|---|---|
| Web-App | Next.js · TypeScript · tRPC · Tailwind CSS (T3-Stack), als PWA |
| Daten | Drizzle ORM · SQL (PlanetScale) |
| Integrationen | Spotify-API (Login via NextAuth) · LangChain mit wählbarem Modell (OpenAI GPT / Google Gemini) für die News-Aufbereitung · AWS S3 |
| Betrieb | Vercel (Live-Deployment) |
