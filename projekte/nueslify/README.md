# Nüslify — persönliches KI-Radio

**Ein Radioprogramm für eine einzige Person:** Nüslify holt per KI aktuelle Nachrichten zu den eigenen Interessen, bereitet sie auf und mischt sie mit der eigenen Spotify-Musik — wie ein klassisches Radioprogramm aus Moderation und Musik, nur personalisiert auf Interessen und Hörgewohnheiten.

| | |
|---|---|
| Kontext | Kurs Intelligent User Interfaces (IUI), LMU München, WiSe 2023/24 · 5-köpfiges Team |
| Rolle | Interessen-Feature durchgängig von der Oberfläche bis zur Datenbank, dazu Teile des Player-Dashboards |
| Code | [NoelHuibers/nueslify](https://github.com/NoelHuibers/nueslify) (öffentlich, GPL-3.0) |
| Deployment | Lief als PWA auf Vercel (nueslify.vercel.app); die Anmeldung über Spotify funktioniert inzwischen nicht mehr (Stand 09/2026) |

## Die Idee

Im Kurs Intelligent User Interfaces haben wir im Team eine Web-App gebaut und veröffentlicht, in der KI den Kern des Nutzungserlebnisses bildet.

Radio lebt von der Mischung aus Information und Musik — aber das Programm bestimmt der Sender. Nüslify dreht das um: Die News kommen KI-kuratiert zu selbst gewählten Themen, die Musik aus dem eigenen Spotify-Account. Umgesetzt als Progressive Web App, die sich wie eine native App nutzen lässt.

## Mein Beitrag

- **Das Interessen-Feature:** die Seiten und Formulare, auf denen Nutzer:innen ihr Profil anlegen und festlegen, welche News-Themen sie interessieren, wie viel News und wie viel Musik sie hören wollen, welches KI-Modell und welcher Moderationsstil die News aufbereiten und welche Musik sie mögen (React/Next.js), samt Styling, tRPC-API-Router und Anbindung an das Drizzle-Datenbankschema — die Grundlage für die personalisierte News-Auswahl
- **Teile des Player-Dashboards:** News-Player als eigenständige Komponente herausgelöst und gestylt, Spotify-Button, Navbar-Styling, Ladezustände

## Technologien

| Ebene | Eingesetzt |
|---|---|
| Web-App | Next.js · TypeScript · tRPC · Tailwind CSS (T3-Stack), als PWA |
| Daten | Drizzle ORM · SQL (PlanetScale) |
| Integrationen | Spotify-API (Login via NextAuth) · LangChain mit wählbarem Modell (OpenAI GPT / Google Gemini) für die News-Aufbereitung · AWS S3 |
| Betrieb | Vercel |
