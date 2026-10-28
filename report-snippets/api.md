# Aeroq CRISP-DM Research

***Note:*** *This markdown file contains the text I originally wrote in the [Google Colab Notebook](https://colab.research.google.com/drive/1fzTssli75DMSBWKRzdaBCISDKLF8VVJz?usp=sharing). I'm also placing it here to make my report writing easier.*

## Aviation Weather Centre (AWC)

### METARs

Meteorological Aerodrome Reports (METARs) are standardised weather reports providing *current* weather conditions most relevant to aviation for a given airport.

METARs are typically generated and published by Met Éireann every 30 minutes, at 20 and 50 minutes past.

Special weather reports (SPECI) may be issued where there is a notable swing in weather conditions.

#### Interpreting METARs

**Full METAR interpretation guide (AWC):** [aviationweather.gov/help/data/#metar](https://aviationweather.gov/help/data/#metar) (redirect).

**Raw Data:**

`METAR EIDW 291600Z 15009KT 100V200 9999 -DZ SCT010 BKN013 OVC015 18/16 Q1001 NOSIG`

**Interpretation:**

| Field | Value | Interpretation |
| :--- | :--- | :--- |
| **Report Type** | `METAR` | METAR |
| **Place** | `EIDW` | Dublin Airport |
| **Date-Time Issued** | `291600Z` | 29th day, 16:00 UTC |
| **Wind** | `15009KT 100V200` | 150° at 9 knots (variable 100°–200°) |
| **Visibility** | `9999` | 10 km or greater |
| **Phenomena** | `-DZ` | Light drizzle |
| **Clouds** | `SCT010 BKN013 OVC015` | Scattered 1,000 ft, broken 1,300 ft, overcast 1,500 ft |
| **Temperature** | `18/16` | 18°C with 16°C dewpoint |
| **Pressure** | `Q1001` | QNH 1001 hPa |
| **Additional-Information** | `NOSIG` | No significant changes expected in window |

### TAFs

Terminal Aerodrome Forecasts (TAFs) are standardised weather *forecasts* predicting the weather conditions most relevant to aviation for a given airport.

For our three Irish airports, TAFs are generated and published by Met Éireann at 05:00, 11:00, 17:00, and 23:00 UTC.

In most circumstances, a TAF for a given airport becomes active after 1-hour and is valid for 24-hours.

A TAF may be amended at any time due to changing weather conditions (`TAF AMD`), error corrections (`TAF COR`). Both TAF amendments and TAF corrections invalidate and replace the preceding TAF. If TAF issuance is delayed, most often due to technical difficulties, it will be issued as a `TAF RTD`.

---

There are three change groups used in TAFs:

1. **From (`FM`)**

   Indicates rapid, permanent changes **to** mean weather conditions taking place from a specified time. All elements of the forecast will be retransmitted.

2. **Becoming (`BECMG`)**

   Indicates a gradual change in the weather over the specified period. Only the changing elements are listed.

3. **Temporary (`TEMPO`)**

   Indicates a temporary change **from** mean weather conditions for less than half of the specified period. Additionally, `TEMPO` can only be used for periods of temporary fluctuation greater than 30 minutes, but less than 60. So, even if a `TEMPO` change is issued over a 4-hour period, the temporary fluctuation is only expected to last a maximum of 1-hour.

- **Probability (`PROB`)**

  Used when there is a 30% probability (`PROB30`) **OR** 40% probability (`PROB40`) of a specified change in conditions over a time period. Probabilities less than 30% are not reported, probabilities over 40% should be issued as `TEMPO`, `FM`, or `BECMG`.

---

Sources:

- [TarmacView – TAF change groups](https://www.tarmacview.com/glossary/taf/#taf-change-groups-fm-tempo-prob-becmg)
- [SKYbrary – TAF guidance (PDF)](https://skybrary.aero/sites/default/files/bookshelf/34407.pdf)

#### Interpreting TAFs

**Full TAF interpretation guide (AWC):** [aviationweather.gov/help/data/#taf](https://aviationweather.gov/help/data/#taf) (redirect).

**Raw Data:**

```
TAF EICK 010500Z 0106/0206 23005KT 9999 FEW018
  PROB40
  TEMPO 0106/0109 -SHRA FEW018CB
  BECMG 0108/0110 20010KT
  TEMPO 0114/0202 20015G27KT
  TEMPO 0120/0202 4000 -RA BKN007 FEW018CB
  PROB40
  TEMPO 0121/0202 2500 RA BR BKN004
  PROB40
  TEMPO 0202/0206 2500 -SHRA BR BKN004
```

**Base Forecast Interpretation:**

| Field | Interpretation |
| :--- | :--- |
| **Report Type** | TAF |
| **Place** | Cork Airport |
| **Date-Time Issued** | 1st of month, 05:00 UTC |
| **Validity Period** | 1st of the month 06:00 UTC until 2nd of the month 06:00 UTC |
| **Wind** | 230 degrees, 5 knots |
| **Visibility** | 9999 M or more |
| **Clouds** | 40% probability of a few clouds (~2/8ths cloud cover) at 1800 feet |

**Change Groups Interpretation:**

| Change Type | Period | Value | Interpretation |
| :--- | :--- | :--- | :--- |
| Temporary | 1st of the month, 06:00–09:00 UTC | `TEMPO 0106/0109 -SHRA FEW018CB` | Showers of rain; few cumulonimbus at 1800 ft. |
| Becoming | 1st of the month, 08:00–10:00 UTC | `BECMG 0108/0110 20010KT` | Wind 200° at 10 knots |

### SIGMET

Significant Meteorological Information (SIGMET) is a non-routine severe weather advisory. SIGMETs use Flight Information Regions (FIRs) due to the nature of severe weather. A FIR is a large division of airspace in a region.

The Shannon FIR covers all of Ireland below Flight Level (FL) 245 (24,500 ft.). Above FL 245, Northern Ireland uses the Scottish FIR (EGPX).

#### SIGMET ICAO Code Prefix to Region

| Prefix | Region |
| :--- | :--- |
| A | Western South Pacific |
| B | Greenland, Iceland, and Kosovo (European Alternate) |
| C | Canada |
| D | Eastern parts of West Africa and Maghreb |
| E | Northern Europe |
| F | Most of Central Africa, Southern Africa, and the Indian Ocean |
| G | Western parts of West Africa and Maghreb |
| H | East Africa and Northeast Africa |
| K | Contiguous United States |
| L | Southern Europe, Israel, and Palestine |
| M | Central America, Mexico and northern/western parts of the Caribbean |
| N | Most of the South Pacific and New Zealand |
| O | Gulf States, Iran, Iraq, Pakistan, Jordan, West Bank |
| P | Most of the North Pacific, and Kiribati |
| R | Japan, South Korea, and the Philippines |
| S | South America |
| T | Eastern and southern parts of the Caribbean |
| U | Former USSR except the Baltics or Moldova |
| V | Many South Asian countries, mainland Southeast Asia, Hong Kong and Macau |
| W | Most of Maritime Southeast Asia |
| Y | Australia |
| Z | China, North Korea, and Mongolia |

Adapted from the exhaustive list: [Wikipedia – ICAO airport code](https://en.wikipedia.org/wiki/ICAO_airport_code)

## OpenSky Network API

**OpenSky blocks GCP servers, which Google Colab use.**

To see the notebook researching the OpenSky API, please visit the `api/opensky` directory in the working branch of my [fyp-code GitHub repo](https://github.com/JoeOMahony/fyp-code/tree/working).