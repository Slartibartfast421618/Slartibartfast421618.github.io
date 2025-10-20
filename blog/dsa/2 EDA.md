# Exploratory Data Analysis (EDA): Fra rå data til indsigt
Denne artikel gennemgår **11 trin** i en EDA-proces, der transformerer rå, ubehandlet data til klar, handlingsorienteret viden. Eksemplet bruger syntetisk data for frisørsaloner i Bergen.

---

## 1. Data Collection
Indsamling af den data, der skal analyseres.
- **Eksempel:** Mock data (syntetisk data) genereret af Le Chat for at simulere et dataset over frisører i Bergen.

---

## 2. Data Wrangling
Processen med at gøre "rå data" klar til analyse. Omfatter:
- **Rensning:** Eksempelvis rette `Rating`-kolonnen fra `"02.06"` til `2.6`.
- **Strukturering:** Ekstrahere `Neighborhood` fra `Address`.
- **Formatering:** Konvertere `Opening Hours` til antallet af timer.
- **Berigelse:** Tilføje nye kolonner som `Opening Hours Length`.
- **Integration:** Kombinere flere datasæt.

### Vigtige justeringer:
1. **Adskillelse af bydel og adresse:**
   - Eksempel: `"Årstad"` ekstraheret fra `"680 Charles Spurs Apt. 805, Årstad"`.
   - **Formål:** Nemmere søgning og analyse på bydelsniveau.

2. **Omkodning af services:**
   - Liste af services (f.eks. `["Beard Trim", "Coloring"]`) omdannes til separate kolonner med **1/0-værdier**.
   - **Formål:** Nem filtrering, tælling og visualisering af populære services.

---

## 3. Exploratory Visualization
Visuelle repræsentationer til at udforske, forstå og analysere data.

### Hvorfor er det vigtigt?
- Opdagelse af **mønstre** og **tendenser**.
- Identifikation af **anomalier** (f.eks. usædvanlige ratings).
- Forståelse af **datafordeling** (f.eks. prisfordeling).
- Generering af **hypoteser** (f.eks. sammenhæng mellem åbningstider og ratings).
- **Kommunikation** af komplekse indsigter.

### Typer af visualiseringer:
| Type               | Eksempel                          | Formål                                                                 |
|--------------------|-----------------------------------|------------------------------------------------------------------------|
| **Univariate**     | Histogram, boksplot, pie chart    | Fokus på én variabel (f.eks. prisfordeling).                          |
| **Bivariate**      | Scatterplot, linjediagram         | Undersøger forholdet mellem to variabler (f.eks. pris vs. rating).     |
| **Multivariate**   | Heatmap, parallelle koordinater   | Undersøger flere variabler samtidigt.                                  |

### Eksempler på visualiseringer:
1. **Neighborhood vs Price Range (NOK):**
   - **Hjælp:** Lokal prissammenligning og filtrering efter område.
   - **Praktisk anvendelse:** Interaktivt kort med prisklasser.

2. **Price Range (NOK) vs Rating:**
   - **Hjælp:** Værdi for pengene og toplister.
   - **Praktisk anvendelse:** Sammenligningsværktøj for brugere.

3. **Neighborhood vs Rating:**
   - **Hjælp:** Kvalitet efter område og beliggenhedsbaserede anbefalinger.
   - **Praktisk anvendelse:** Anbefalingssystem for bedst bedømte saloner.

4. **Number of Reviews vs Opening Hours:**
   - **Hjælp:** Popularitet og tilgængelighed.
   - **Praktisk anvendelse:** Filtrering efter åbningstider.

5. **Popularitetsgraf:**
   - Kombinerer **antal anmeldelser** og **rating** for at vise populære saloner.

---

## 4. Descriptive Statistics
Fortolkning af nøgletal for priser, ratings og anmeldelser.

5. Missing Value Treatment
Eksempel på håndtering i dit dataset:

Åbningstider: Hvis nogle saloner mangler oplysninger om åbningstider, kan du udfylde med gennemsnittet af åbningstider for saloner i samme bydel.
Services: Hvis en salong mangler oplysninger om tilbudte services, kan du antage, at de ikke tilbyder de pågældende services (0), eller udfylde med den mest almindelige service i bydelen.
Ratings/Anmeldelser: Hvis en salong mangler ratings, kan du udfylde med den gennemsnitlige rating for bydelen eller fjerne salongen, hvis antallet af manglende værdier er lille.

Hvorfor det er vigtigt:

Sikrer, at analysen ikke forvrænges af manglende data.
Forbedrer nøjagtigheden af visualiseringer og statistikker.


6. Outlier Analysis
Hvordan identificere outliers i dit dataset:

Priser: Brug boksplot til at identificere saloner med usædvanligt høje eller lave priser.
Ratings: Saloner med ratings langt under gennemsnittet (f.eks. under 3.5) kan være outliers.
Antal anmeldelser: Saloner med ekstraordinært få eller mange anmeldelser kan undersøges nærmere.

Håndtering af outliers:

Undersøg årsagen: Er det en fejl, eller er der en reel forklaring (f.eks. en ny salong med få anmeldelser)?
Fjern eller juster: Hvis outliers er fejl, kan de fjernes. Hvis de er reelle, kan de analyseres separat for at forstå, hvad der gør dem unikke.

Eksempel:

En salong med en pris på 1500 NOK (langt over gennemsnittet) kan undersøges for at se, om de tilbyder premium services.


7. Data Transformation
Formål: Forberede data til bedre analyse og visualisering.
Eksempler:

Log-transformation: Hvis priserne er skævt fordelte, kan en log-transformation gøre fordelingen mere normal.
Normalisering: Skalere priser og ratings til en fælles skala (f.eks. 0–1) for at sammenligne dem i multivariate analyser.
Binning: Grupper priser i intervaller (f.eks. 500–600 NOK, 600–700 NOK) for at simplificere analysen.

Praktisk anvendelse:

Gør det nemmere at sammenligne variabler med forskellige skalaer (f.eks. pris vs. rating).


8. Dimensionality Reduction
Hvorfor: Reducerer kompleksiteten i data med mange variabler (f.eks. mange services).
Metoder:

PCA (Principal Component Analysis): Kan reducere antallet af variabler, mens de vigtigste mønstre bevares.
Feature Selection: Vælg kun de mest relevante variabler (f.eks. de 5 mest populære services).

Eksempel:

Hvis du har 20 forskellige services, kan PCA reducere dem til 3–5 hovedkomponenter, der forklarer det meste af variationen.


9. Bivariate Exploration
Undersøgelse af to variabler ad gangen.
Eksempler:

Scatterplot: Pris vs. Rating – er der en sammenhæng mellem højere priser og bedre ratings?
Barplot: Bydel vs. Gennemsnitlig Rating – hvilke bydele har de højeste ratings?
Boxplot: Åbningstider vs. Antal Anmeldelser – har saloner med længere åbningstider flere anmeldelser?

Indsigt:

Hjælper med at identificere direkte sammenhænge, f.eks. om længere åbningstider korrelerer med højere popularitet.


10. Multivariate Exploration
Undersøgelse af flere variabler samtidigt.
Eksempler:

Heatmap: Korrelation mellem pris, rating, antal anmeldelser og åbningstider.
Parallel Coordinates Plot: Sammenlign saloner på tværs af pris, rating, bydel og services.
Cluster Analysis: Grupper saloner baseret på pris, rating og services for at identificere segmenter (f.eks. "Budget", "Premium", "Familievenlig").

Indsigt:

Kan afsløre komplekse mønstre, f.eks. om saloner i visse bydele med specifikke services har højere ratings.


11. Communication of Insights
Formål: Præsentere dine fund på en klar og handlingsskabende måde.
Metoder:

Dashboards: Interaktive visualiseringer (f.eks. Tableau eller Power BI), hvor brugere kan filtrere efter bydel, pris eller service.
Historiefortælling: Brug en kombination af grafer, tekst og anbefalinger til at kommunikere dine resultater.
Toplister: "Top 5 saloner i Årstad med bedste værdi for pengene" baseret på pris, rating og services.

Eksempel på output:

En rapport med:

Kort over Bergen med saloners ratings og priser.
Graf over sammenhængen mellem pris og rating.
Anbefalinger til brugere (f.eks. "Hvis du søger farvning, er saloner i Fyllingsdalen billigere end i centrum").




Opsummering af EDA-proces for dit projekt:

Data Collection: Syntetisk data for frisører i Bergen.
Data Wrangling: Renset og struktureret data (bydel, services).
Exploratory Visualization: Opdaget mønstre i pris, rating og beliggenhed.
Descriptive Statistics: Gennemsnit, variation og fordeling af priser, ratings og anmeldelser.
Missing Value Treatment: Udfyldt manglende åbningstider med bydelsgennemsnit.
Outlier Analysis: Identificeret og undersøgt saloner med usædvanlige priser/ratings.
Data Transformation: Normaliseret priser for bedre sammenligning.
Dimensionality Reduction: Reduceret antallet af service-variabler med PCA.
Bivariate Exploration: Undersøgt sammenhænge mellem pris, rating og bydel.
Multivariate Exploration: Grupperet saloner i segmenter baseret på flere variabler.
Communication of Insights: Oprettet et interaktivt dashboard med anbefalinger til brugere.