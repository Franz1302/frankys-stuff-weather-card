# Drittanbieter- und Rechtehinweise

## Open-Meteo Wetterdaten

Die Wetterkarte kann zur Laufzeit Daten der Open-Meteo Forecast API abrufen.
- Datenquelle: https://open-meteo.com/
- Datensatzlizenz: Creative Commons Attribution 4.0 International (CC BY 4.0), https://creativecommons.org/licenses/by/4.0/
- Bedingungen des kostenlosen API-Angebots: **nichtkommerziell**, siehe https://open-meteo.com/en/terms
- Die Karte zeigt einen Open-Meteo-Attributionshinweis samt Lizenzlink an, wenn dieser Datenpfad genutzt wird.
- Es wird **kein Quellcode der Open-Meteo-Serveranwendung** eingebettet oder vertrieben. Die AGPL-Lizenz der Serveranwendung ist nicht automatisch eine Lizenzpflicht für einen bloßen HTTP-API-Client.

## Home Assistant und Material Design Icons

Die Karte nutzt die Lovelace-/Home-Assistant-Oberfläche und vorhandene `ha-icon`-Elemente mit `mdi:`-Kennungen. Die Icons werden **nicht als eigene Dateien mitgeliefert**. Für eine eigenständige Verbreitung von Icons wäre deren jeweilige Lizenz gesondert zu berücksichtigen.

## Acht eingebettete WebP-Motive – eigene Projektgrafiken

Die JavaScript-Datei enthält acht Base64-WebPs mit den Schlüsseln
`clear-night`, `cloudy`, `fog`, `lightning`, `partlycloudy`, `rainy`, `snowy`, `sunny`.

Der Herausgeber hat bestätigt, dass die Bilder im Zuge dieses Projekts mit
ChatGPT erstellt wurden. Eine fremde Bildquelle wurde nicht angegeben.
Die Freigabe erfolgt für diese Bildmotive im Umfang der verfügbaren Rechte unter
**CC BY-NC 4.0** – siehe `ARTWORK_LICENSE.md`. Dies ist eine auf seiner Erklärung
beruhende Dokumentation, keine unabhängige Bildprovenienzprüfung und keine
Garantie urheberrechtlicher Exklusivität für KI-generierte Inhalte.

## Optionale externe Bilder

Verwendet der Nutzer eigene Bild-URLs in der Kartenkonfiguration, gelten die Nutzungsrechte dieser Bilder unabhängig vom Kartenpaket. Externe HTTPS-Bildquellen können Browser-Verbindungen zu den jeweiligen Drittanbietern auslösen.
