# Delta Airlines Flight Delay Analysis

## Prosjektoversikt

Dette prosjektet analyserer forsinkelsesdata for Delta Airlines (DL) for å identifisere mønstre og årsaker til flyforsinkelser. Analysen fokuserer på å utvikle datadrevne innsikter som kan hjelpe Delta med å redusere forsinkelser gjennom bedre ruteplanlegging og ressursbruk.

## Datasettbeskrivelse

### Grunnleggende informasjon

- **Antall rader**: 16,726 (inkludert header)
- **Antall kolonner**: 21
- **Tidsperiode**: 2013-2023 (11 år)
- **Måneder**: Januar-Desember (alle måneder representert)
- **Antall flyplasser**: 170 unike flyplasser
- **Totalt antall fly**: 8,661,561
- **Totalt forsinkede fly (15+ min)**: 1,198,884
- **Forsinkelsesrate**: 13.84%

### Kolonnebeskrivelse

| Kolonne               | Beskrivelse                           | Type    |
| --------------------- | ------------------------------------- | ------- |
| `year`                | År (2013-2023)                        | Integer |
| `month`               | Måned (1-12)                          | Integer |
| `carrier`             | Flyselskapskode (DL)                  | String  |
| `carrier_name`        | Flyselskapsnavn                       | String  |
| `airport`             | Flyplasskode (IATA)                   | String  |
| `airport_name`        | Flyplassnavn og lokasjon              | String  |
| `arr_flights`         | Antall ankommende fly                 | Float   |
| `arr_del15`           | Antall forsinkede fly (15+ min)       | Float   |
| `carrier_ct`          | Antall forsinkelser pga. flyselskap   | Float   |
| `weather_ct`          | Antall forsinkelser pga. vær          | Float   |
| `nas_ct`              | Antall forsinkelser pga. NAS-kontroll | Float   |
| `security_ct`         | Antall forsinkelser pga. sikkerhet    | Float   |
| `late_aircraft_ct`    | Antall forsinkelser pga. sen fly      | Float   |
| `arr_cancelled`       | Antall kansellerte fly                | Float   |
| `arr_diverted`        | Antall omdirigerte fly                | Float   |
| `arr_delay`           | Total forsinkelsestid (minutter)      | Float   |
| `carrier_delay`       | Forsinkelsestid pga. flyselskap       | Float   |
| `weather_delay`       | Forsinkelsestid pga. vær              | Float   |
| `nas_delay`           | Forsinkelsestid pga. NAS-kontroll     | Float   |
| `security_delay`      | Forsinkelsestid pga. sikkerhet        | Float   |
| `late_aircraft_delay` | Forsinkelsestid pga. sen fly          | Float   |

### Datakvalitet og struktur

- Datasettet inneholder månedlige aggregerte data per flyplass
- Alle forsinkelsesdata er kategorisert etter årsak
- Data dekker både volum (antall fly) og forsinkelsestid (minutter)
- Forsinkelser defineres som 15+ minutter forsinkelse

## Begrunnelse for Delta Airlines-fokus

Vi fokuserer på Delta Airlines (DL) av følgende årsaker:

1. **Stort volum**: Delta opererer et omfattende nettverk med over 8.6 millioner fly over analyserperioden
2. **Omfattende dekning**: Data dekker 170 flyplasser, noe som gir god geografisk representasjon
3. **Konsistent data**: Delta har konsistent rapportering gjennom hele perioden (2013-2023)
4. **Forretningsrelevans**: Som et av USAs største flyselskaper har Delta betydelig innvirkning på luftfartsindustrien
5. **Analysepotensial**: Det store volumet og omfattende dekningen muliggjør robuste statistiske analyser

## Background - Kontekst og Mål

### Kontekst

Luftfartsbransjen er svært avhengig av punktlighet, og forsinkelser fører både til økte kostnader og dårligere kundetilfredshet. Delta Airlines opererer et omfattende nettverk i USA, og små forbedringer i ruteplanlegging og ressursbruk kan gi stor effekt. Derfor analyserer vi hvordan forsinkelsesdata kan brukes systematisk for å identifisere og adressere rotårsaker.

### Overordnet mål

Å utvikle datadrevne innsikter som hjelper Delta med å redusere forsinkelser ved å identifisere mønstre i tid, sted og årsak.

### Spesifikke delmål

1. **Kartlegge hvilke flyplasser og tidsperioder som har høyest forsinkelsesrate**
2. **Analysere hvilke faktorer (vær, tekniske forhold, NAS-kontroll, sen ankomst osv.) som forklarer mest av variasjonen i forsinkelser**
3. **Lage indikatorer (KPI-er) som lar Delta overvåke fremgang i tiltak**
4. **Bygge et strukturert datagrunnlag (panel-format) for videre analyse, visualisering og prediktive modeller**

## Tilnærming og Metodologi

### CRISP-DM-rammeverk

Vi følger CRISP-DM-modellen (Cross-Industry Standard Process for Data Mining) som rammeverk for prosjektet:

1. **Business Understanding**: Forstå Deltas utfordringer med forsinkelser
2. **Data Understanding**: Undersøke strukturen og kvaliteten i Airline Delay Cause-datasettet
3. **Data Preparation**: Filtrere til Delta, rense data, og konstruere relevante KPI-er
4. **Modeling/Analysis**: Utføre aggregeringer, tidsserieanalyse og årsaksanalyse
5. **Evaluation**: Vurdere resultater mot prosjektmål og identifisere tiltak
6. **Deployment**: Presentere anbefalinger for hvordan Delta kan overvåke og redusere forsinkelser

### Analyseplan

1. **Data Understanding**: Utforske datasettet for å forstå struktur, variabler og dekning
2. **Data Preprocessing**: Rense og standardisere (fjerne NaN, konvertere datatyper, beregne rater og andeler)
3. **Feature Engineering**: Lage nye KPI-er som "delay rate", "avg delay per arrival", og andeler per årsak
4. **Exploratory Data Analysis (EDA)**: Visualisere forsinkelser over tid, per flyplass og årsak
5. **Interpretation**: Trekke ut mønstre og foreslå forbedringsområder (sesonger, flyplasser, årsaker)
6. **Deployment**: Presentere tiltak og anbefalinger basert på analysen

## Forventet Impact

Målet med data-strategien er å skape et datagrunnlag som muliggjør faktabaserte beslutninger hos Delta. Ved å bruke historiske forsinkelsesdata systematisk ønsker vi å identifisere mønstre som kan brukes til:

- **Prioritering av tiltak** mot de mest forsinkede rutene og flyplassene
- **Optimalisering av ruteplanlegging** i perioder med høy risiko
- **Overvåking av tiltak** gjennom nøkkelindikatorer

Resultatet skal støtte både strategiske beslutninger (langsiktig forbedring) og operative prosesser (daglig planlegging og rapportering).

## Datakilder

- **Hoveddatasett**: `delta_airlines.csv` - Filtrert data for Delta Airlines fra Bureau of Transportation Statistics
- **Referansedatasett**: `Airline_Delay_Cause.csv` - Komplett datasett med alle flyselskaper

## Tekniske Krav

- Python 3.x
- Pandas for dataanalyse
- Matplotlib/Seaborn for visualisering
- Jupyter Notebook for interaktiv analyse

## Prosjektstruktur

```
flight-delay/
├── dataset/
│   ├── delta_airlines.csv          # Hoveddatasett (Delta Airlines)
│   └── Airline_Delay_Cause.csv     # Referansedatasett (alle flyselskaper)
├── README.md                       # Denne filen
└── [analyse-filer]                 # Kommende analysefiler
```
