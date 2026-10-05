# Nüslify — dein persönliches KI-Radio

**Ein Radiosender, der nur für dich sendet:** Nüslify holt per KI aktuelle Nachrichten zu deinen Interessen, bereitet sie auf und mischt sie mit deiner eigenen Spotify-Musik — wie ein klassisches Radioprogramm aus Moderation und Musik, nur eben personalisiert auf Interessen und Hörgewohnheiten.

| | |
|---|---|
| Kontext | Kurs Intelligent User Interfaces (IUI), LMU München, WiSe 2023/24 · 5-köpfiges Team |
| Rolle | Interessen-Feature durchgängig von der Oberfläche bis zur Datenbank, dazu Teile des Player-Dashboards |
| Code | [NoelHuibers/nueslify](https://github.com/NoelHuibers/nueslify) (öffentlich, GPL-3.0) |
| Deployment | War als PWA auf Vercel live (nueslify.vercel.app); die Anmeldung über Spotify funktioniert inzwischen nicht mehr (Stand 09/2026) |

## Die Idee

Im Kurs Intelligent User Interfaces haben wir im Team ein lauffähiges intelligentes Interface gebaut und live deployed — eine Web-App, die KI nicht als Gimmick, sondern als Kern des Nutzungserlebnisses einsetzt.

Radio lebt von der Mischung aus Information und Musik — aber das Programm bestimmt der Sender. Nüslify dreht das um: Die News kommen KI-kuratiert zu den Themen, die dich interessieren, die Musik kommt aus deinem eigenen Spotify-Account. Umgesetzt als Progressive Web App, die sich wie eine native App nutzen lässt.

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
