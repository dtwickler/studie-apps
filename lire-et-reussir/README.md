# Lire & Réussir – studie-app Frans 5 VWO (Reva)

Een oefen-app voor de telefoon, gericht op **leesvaardigheid**: Franse teksten in examenstijl met de vraagtypes van het examen, uitleg bij elk antwoord (de zin uit de tekst wordt gemarkeerd), signaalwoorden en krantenwoorden met gespreide herhaling, streaks en badges. Geen beloningen.

Deze app gebruikt dezelfde motor als Shens Duitse app. Wat per kind anders is, staat in `profiel.json`.

## Online zetten (eenmalig, ca. 10 minuten)

1. Log in op github.com (hetzelfde account als voor Shens app mag).
2. Klik rechtsboven op **+ → New repository**. Naam bijvoorbeeld `frans-5vwo`. Kies **Public** en klik **Create repository**.
3. Klik op **uploading an existing file** en sleep alle bestanden en mappen uit deze map erin. Klik **Commit changes**.
4. Ga naar **Settings → Pages**. Kies bij *Branch* `main` en `/ (root)` en klik **Save**.
5. Na 1–2 minuten staat de app op `https://<jouw-gebruikersnaam>.github.io/frans-5vwo/`.
6. Open die link op Reva's telefoon en kies **Zet op beginscherm** (iPhone: deel-knop; Android: menu ⋮).

De voortgang van Reva en Shen zit elkaar niet in de weg, ook niet als beide apps onder hetzelfde GitHub-account staan: elke app bewaart onder een eigen naam (`opslag` in `profiel.json`).

Let op: een publieke repository is voor iedereen leesbaar. Daarom staan er geen echte examenteksten in (auteursrecht), maar zelfgeschreven teksten in examenstijl.

## Profiel (`profiel.json`)

| Veld | Betekent |
| --- | --- |
| `naam`, `appnaam` | naam van de leerling en van de app |
| `taal` | `fr` (Frans) of `de` (Duits): bepaalt accenttoetsen, lidwoorden en teksten in de app |
| `focus` | `lezen` = leesvaardigheid staat centraal op het startscherm |
| `opslag` | naam waaronder de voortgang op de telefoon wordt bewaard (niet veranderen na de start) |
| `dagdoel` | aantal vragen per dag voor de dagmissie (leesvragen + woordjes) |
| `beloningen` | `false` = geen beloningen, alleen voortgang en badges |
| `kleur` | accentkleur voor donker en licht thema |
| `examenlink` | link naar de echte oude examens |

## Leerstof toevoegen

| Wat | Bestand |
| --- | --- |
| Welke stof bij welk tentamen hoort | `content/tentamens.json` |
| Leesteksten met vragen | `content/lezen/<naam>.json` |
| Woordenlijsten | `content/woorden/<naam>.csv` met kolommen `frans,nederlands,lidwoord,meervoud,voorbeeldzin` |
| Vraagtypes en aanpak | `content/vraagtypes.json` |
| Examentips | `content/examentips.json` |

### Vraagsoorten in een leestekst

| `type` | Wat het is | Velden |
| --- | --- | --- |
| `mc` | meerkeuze (de app husselt de volgorde) | `opties`, `antwoord` (0 = eerste optie), optioneel `zin` |
| `juistonjuist` | reeks beweringen, alles goed = 1 punt | `beweringen`: `t`, `juist`, `uitleg` |
| `citeer` | eerste woord(en) van een zin overnemen | `antwoorden` |
| `alinea` | in welke alinea staat … | `antwoord` (alineanummer) |
| `open` | open vraag met modelantwoord, zelf nakijken | `model` |

### Woorden aantikken (`glossarium`)

Elk woord in een tekst is aan te tikken, zonder zichtbare hint. Woorden die in het `glossarium` van de tekst staan, tonen meteen een vertaling die bij die zin past. Voor andere woorden verschijnt de knop **Zoek op in Reverso**. Elk opgezocht woord komt in **Mijn woorden** en gaat mee in de woordjesrondes. In de uitslag staat hoeveel woorden er zijn opgezocht.

Een glossarium-regel ziet er zo uit: `{ "vorm": "avouent", "nl": "geven toe", "basis": "avouer" }`. De `vorm` moet letterlijk zo in de tekst staan (mag uit meerdere woorden bestaan); `basis` is optioneel.

Elke vraag heeft ook `vraagtype` (zie `vraagtypes.json`), `uitleg` en `bewijs` (`alinea` + de letterlijke `zin` uit de tekst die na het antwoorden gemarkeerd wordt). Een open plek in een tekst schrijf je als `___`.

## Hoe de app leert

- **Tekst van de dag:** eerst nieuwe teksten, daarna komen teksten met de laagste score terug.
- **Uitleg bij elk antwoord**, met de bewijszin gemarkeerd in de tekst.
- **Examentempo:** een timer met ongeveer 3 minuten per vraag.
- **Voortgang per vraagtype:** zo zie je waar ze sterk en minder sterk in is.
- **Woorden:** gespreide herhaling in bakjes 1–5; beheerst = meerdere keren goed op verschillende dagen.

## Testen als ouder

Onder **Profiel → Voor ouders: testen** kun je een dag vooruit springen en alles wissen.
