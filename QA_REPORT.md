# Prüfbericht – Frankys_Stuff Weather Card v0.3.0

**Prüfdatum:** 10.10.2026  
**Ausgangsdatei:** `Eingefügter Text.txt` (vom Herausgeber gelieferte Release-JS)  
**Ausgangs-SHA-256:** `224c6e4663dc85cda2cca65c7a6add37b4514144a88a1012e498e62eb7434800`  
**Vorheriger Releasekandidat-SHA-256:** `6c151c2c968e4b4c9d19cc2d515f67df4fe5bd415d169413dd666d5c5072b1f6`
**Finaler Release-SHA-256:** `b5ad967618679a681b628aaf7a5ca099c17754a9117fa2d43d2667a6307791bf` (zusätzlich nur Lizenzhinweis im JS-Header)

## Durchgeführte Prüfungen – bestanden

1. `node --check` – JavaScript syntaktisch gültig.
2. Isolierte Ausführung mit einer DOM-/Custom-Elements-Testumgebung: Karte und Editor registrieren sich erwartungsgemäß unter `frankys-stuff-weather-card` und `frankys-stuff-weather-card-editor`.
3. Konfigurationsprüfung: gültige Einstellungen werden übernommen; ungültige Sprache, Wetter-Entitätsdomain, Entitäts-ID und Aktualisierungszeit werden abgefangen.
4. WeatherEngine: synthetische Open-Meteo-Antwort erzeugt erwartete aktuelle Temperatur, Feuchte, Tagesminimum/-maximum und Wetterzustand.
5. Statische Prüfung: 7-Tage-Darstellung (`forecast7HTML`), 1-Sekunden-Überblendung (`opacity 1s linear`) und `Map`-Bildcache sind vorhanden.
6. Alle **acht** eingebetteten `data:image/webp;base64`-Einträge wurden Base64-dekodiert und mit PIL als gültige WebP-Dateien geöffnet.
7. Benutzerdefinierte Entitäten/Personen-/IP-Daten wurden im lesbaren JS-Quelltext stichwortbasiert gesucht; dabei keine offensichtlichen personenbezogenen Konstanten gefunden. Kein Ersatz für ein vollständiges Security-Audit.
8. Kein zusätzliches Skript-Import/Require festgestellt, kein separates Bilderverzeichnis nötig. Externe Datenabfrage: Open-Meteo-HTTP-API, optional benutzerdefinierte HTTPS-Bilder.

## Bildinventar (aus JS dekodiert, nicht ausgegeben)

| Schlüssel | Pixel | WebP-Dateigröße |
| --- | --- | ---: |
| `clear-night` | 1463 × 1075 | 254.458 Byte |
| `cloudy` | 1463 × 1075 | 180.768 Byte |
| `fog` | 1463 × 1075 | 104.128 Byte |
| `lightning` | 1463 × 1075 | 310.720 Byte |
| `partlycloudy` | **2172 × 724** | 341.230 Byte |
| `rainy` | 1463 × 1075 | 284.454 Byte |
| `snowy` | 1463 × 1075 | 369.552 Byte |
| `sunny` | 1463 × 1075 | 89.246 Byte |

**Auffälligkeit:** `partlycloudy` ist deutlich breiter/flacher. CSS nutzt `object-fit:fill`, daher kann es bei diesem Motiv zu einer abweichenden visuellen Streckung kommen. Keine automatische Bildänderung vorgenommen.

## Minimaländerungen der öffentlichen Release-Kopie

- Altlast `jarvis-weather-card` (Legacy-Kompatibilitätsalias) entfernt; öffentliche Kennung beibehalten.
- Irreführenden MANUELL-Text aus dem Wetterkarteneditor entfernt.
- Veralteten PNG-Kommentar in einen WebP-Kommentar geändert.

**Wetterlogik, eingebettete Bilddaten, Layout und Überblendungsverhalten wurden nicht modifiziert.** Der finale Schritt ergänzte ausschließlich den Lizenzhinweis im JS-Header; die übrigen Bytes der Releasekandidaten-JS blieben unverändert.

## Nicht durch isolierte Tests abgedeckt

- Komplette Browser-/DOM-Interaktion und Visueller Editor in echter HA-Installation.
- HA-Forecast-WebSocket mit echten `weather.*`-Entitäten, Netzwerk-/CORS- und Fehlerzustände.
- Bildwechsel, visuelle Qualität der Hintergründe, Größenverhältnisse und Ausrichtung auf Tablets.
- Zugänglichkeit: Der Klick auf die gesamte Kartenfläche ist nicht ausdrücklich als Tastaturbedienung dokumentiert.
- Zu prüfen auf schwächeren Geräten: Beim dynamischen Rendern wird im HTML-Markup vor dessen Entfernung vorübergehend ein großes Base64-Bild-URL-Fragment zusammengesetzt. Das Bild selbst wird gecacht; die temporäre Zeichenkettenarbeit kann dennoch Performance kosten.
- Bildherkunft/Rechte und HA-Installation wurden vom Herausgeber bestätigt, nicht unabhängig forensisch bzw. auf dessen laufendem HA überprüft.

## Quellen für die öffentliche Installations- und Lizenzdokumentation

- Home Assistant – Ressourcen registrieren: https://developers.home-assistant.io/docs/frontend/custom-ui/registering-resources/
- Home Assistant – Custom Card: https://developers.home-assistant.io/docs/frontend/custom-ui/custom-card/
- Open-Meteo – API Terms: https://open-meteo.com/en/terms
- Open-Meteo – Lizenz: https://open-meteo.com/en/licence

**Fazit:** Nach erfolgreichem Installationstest laut Herausgeber und dessen Bestätigung zur Entstehung der Bilder ist v0.3.0 als Release-Paket vorbereitet. Code und Wetterbilder haben **unterschiedliche Lizenzen** (MIT bzw. CC BY-NC 4.0). Die rechtliche Schutzfähigkeit rein KI-generierter Bilder bleibt eine allgemeine Unsicherheit; ein unabhängiges Rechtsgutachten wurde nicht erstellt.
