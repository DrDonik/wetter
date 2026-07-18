# Wetter-App "Anziehen" — Projektkontext

## Zweck
Persönliche Single-File-Web-App, die eine einzige Frage beantwortet: **Was soll ich heute anziehen?**
Bewusst keine allgemeine Wetter-App. Bestehende Apps zeigen zu viel oder das Falsche.

## Nutzungskontext (fix, nicht hinterfragen)
- Nutzer pendelt mit dem **Velo**, mittags zusätzlich **zu Fuss** draussen
- Drei relevante Zeitfenster:
  - Hinweg (Velo): 07:30–08:00 → Stunden 7–8
  - Mittag (zu Fuss): 12:00–13:00 → Stunde 12
  - Rückweg (Velo): 17:00–17:30 → Stunde 17
- Entscheidungsfaktoren: Regen (Wahrscheinlichkeit UND Menge, wegen Velo), gefühlte Temperatur, Tages-Temperaturspanne (Schichten). Wind nicht separat anzeigen.
- Sprache: Deutsch (Schweiz), kein ß

## Bewusste Design-Entscheide
- **Nur Daten, keine Empfehlungslogik** ("Regenjacke anziehen" o. ä. kommt frühestens in V2, nach Kalibrierung im Alltag)
- Ein Screen, keine Navigation, keine Karte, keine Mehrtagesprognose, kein UV/Luftdruck/Sonnenzeiten
- Vergangene Zeitfenster werden ausgegraut, nicht ausgeblendet
- Regenzeile wird ab 30 % Wahrscheinlichkeit oder 0.2 mm hervorgehoben, sonst "trocken"
- Gewitter: Open-Meteo liefert keine Gewitterwahrscheinlichkeit; stattdessen Flag "Gewitter möglich" via `weather_code` 95/96/99 in den Fensterstunden (hebt die Regenzeile mit hervor)
- Chart-Zonen zeigen die echten Zeitfenster (`from`/`to`), nicht die einfliessenden Datenstunden
- Temperatur pro Fenster: Mittelwert der Fensterstunden (offen: evtl. Minimum, wird im Gebrauch entschieden)

## Technik (Stand V1)
- Eine Datei: `index.html`, kein Build, kein Backend, kein Framework
- API: Open-Meteo `/v1/forecast` mit `hourly=apparent_temperature,precipitation_probability,precipitation,weather_code`, `forecast_days=2`, `timezone=auto`; Heute/Morgen-Umschalter, ab 20:00 Uhr Standard Morgen
- Standort: `navigator.geolocation`, Fallback Basel (47.5596, 7.5886) mit sichtbarem Hinweis
- Chart: handgebautes SVG — Temperaturkurve (orange #D9662E), Regenbalken (blau #2563C4), Zeitfenster als hinterlegte Zonen, gestrichelte Jetzt-Linie
- Farben: bg #EDF1F5, ink #17242F, muted #5C6B78; Farbe nur als Datenkodierung, keine Deko
- `prefers-reduced-motion` respektiert
- Hosting: GitHub Pages (öffentliches Repo, Datei als index.html im Root)

## Bekannte Punkte / Kandidaten für V2
- Fahrtwind: `apparent_temperature` enthält keinen Fahrtwind-Effekt; evtl. fixer "Velo-Abzug" für die beiden Velo-Fenster
- Zeitfenster konfigurierbar machen (aktuell hardcoded)
- Wochenende: Arbeitsweg-Fenster ergeben samstags/sonntags wenig Sinn
- Empfehlungslogik erst nach Kalibrierung des persönlichen Kälteempfindens

## Arbeitsweise
- Direkte, präzise Kommunikation ohne diplomatische Floskeln
- Minimalismus verteidigen: jedes neue Feature muss die Anzieh-Frage besser beantworten, sonst raus
