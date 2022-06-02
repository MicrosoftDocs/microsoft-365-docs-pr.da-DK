---
title: Insights og rapporter Træning i simulering af angreb
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan oplæring i simulering af angreb på Microsoft 365 Defender portalen påvirker brugerne, og de kan få indsigt i simulerings- og oplæringsresultater.
ms.technology: mdo
ms.openlocfilehash: fb08de05e0a1f31187fc4dd045d0f1ce45db2aea
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839359"
---
# <a name="insights-and-reports-for-attack-simulation-training-in-defender-for-office-365"></a>Insights og rapporter om træning i simulering af angreb i Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

I oplæringen af simulering af angreb i Microsoft Defender for Office Plan 2 eller Microsoft 365 E5 giver Microsoft indsigt og rapporter fra resultaterne af simuleringer og de tilsvarende træninger. Disse oplysninger holder dig informeret om status for trusselsparathed for dine brugere samt anbefalede næste trin for bedre at forberede dine brugere på fremtidige angreb.

Insights og rapporter er tilgængelige på følgende placeringer i oplæringen af simulering af angreb på Microsoft 365 Defender-portalen:

- Fanen **Oversigt** .
- Simuleringsoplysninger under fanen **Simuleringer** .

I resten af denne artikel beskrives de tilgængelige oplysninger.

Du kan finde oplysninger om, hvordan du kommer i gang, om oplæring i simulering af angreb under [Kom i gang med at bruge oplæring i simulering af angreb](attack-simulation-training-get-started.md).

## <a name="insights-and-reports-on-the-overview-tab-of-attack-simulation-training"></a>Insights og rapporter på fanen Oversigt under oplæring i simulering af angreb

Hvis du vil gå til fanen **Oversigt**, skal du åbne portalen Microsoft 365 Defender på <https://security.microsoft.com>, gå til **Mail & træning i samarbejde** \> **simulering af angreb** og kontrollere, at fanen **Oversigt** er valgt (det er standarden). Hvis du vil gå direkte til fanen **Oversigt** på træningssiden **Angrebssimulering** , skal du bruge <https://security.microsoft.com/attacksimulator?viewid=overview>.

I resten af dette afsnit beskrives de oplysninger, der er tilgængelige under fanen **Oversigt** i oplæringen af simulering af angreb.

### <a name="recent-simulations-card"></a>Kort til seneste simuleringer

Kortet **Seneste simuleringer** under fanen **Oversigt** viser de sidste tre simuleringer, du har oprettet eller kørt i din organisation.

Du kan vælge en simulering for at få vist detaljer.

Hvis du vælger **Vis alle simuleringer** , kommer du til fanen **Simuleringer** .

Hvis du vælger **Start en simulering** , startes guiden til oprettelse af simulering. Du kan få flere oplysninger under [Simuler et phishing-angreb i Defender for Office 365](attack-simulation-training.md).

:::image type="content" source="../../media/attack-sim-training-overview-recent-simulations-card.png" alt-text="Kortet Seneste simuleringer under fanen Oversigt i Oplæring af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-overview-recent-simulations-card.png":::

### <a name="behavior-impact-on-compromise-rate-card"></a>Adfærdspåvirkning på kortet med kompromitteret hastighed

Kortet **Adfærdspåvirkning på kompromitteret sats** under fanen **Oversigt** viser, hvordan dine brugere reagerede på dine simuleringer sammenlignet med de historiske data i Microsoft 365. Du kan bruge denne indsigt til at spore status for brugeres trusselsparathed ved at køre flere simuleringer mod de samme grupper af brugere.

Selve diagramdataene viser følgende oplysninger:

- **Forudsagt kompromisrate**<sup>\*</sup>: Den gennemsnitlige kompromisrate for simulering af angrebssimulering, der bruger den samme type nyttedata på tværs af alle andre Microsoft 365 organisationer.
- **Faktisk kompromisrate**<sup>\*</sup>: Den faktiske procentdel af brugere, der faldt for simuleringen.

Hvis du holder markøren over et datapunkt i diagrammet, vises de faktiske procentværdier.

Følgende oversigtsoplysninger vises også på kortet:

- **brugere, der er mindre modtagelige for phishing**: Forskellen mellem det faktiske antal brugere, der er kompromitteret af det simulerede angreb, og den forudsagte kompromitterelsesrate. Dette antal brugere er mindre tilbøjelige til at blive kompromitteret af lignende angreb i fremtiden.
- **x % bedre end forudsagt hastighed**: Angiver, hvordan brugerne generelt klarede sig i modsætning til den forudsagte kompromisrate.

:::image type="content" source="../../media/attack-sim-training-overview-behavior-impact-card.png" alt-text="Kortet Funktionsmåde påvirker kompromitteret sats på fanen Oversigt i oplæring i simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-overview-behavior-impact-card.png":::

Hvis du vil se en mere detaljeret rapport, skal du klikke på **Vis simuleringer og rapporten over træningseffektivitet**. Denne rapport er forklaret [senere i denne artikel](#training-efficacy-tab-for-the-attack-simulation-report).

### <a name="simulation-coverage-card"></a>Kort til simuleringsdækning

Kortet **Simuleringsdækning** under fanen **Oversigt** viser procentdelen af brugere i din organisation, der har modtaget en simulering (**simulerede brugere**) vs. dem, der ikke har modtaget en simulering (**ikke-simulerede brugere**). Du kan holde markøren over en sektion i diagrammet for at se det faktiske antal brugere i hver kategori.

Hvis du vælger **Start simulering for ikke-simulerede brugere, startes** guiden til oprettelse af simulering, hvor de brugere, der ikke modtog simuleringen, automatisk vælges på siden **Målbruger** . Du kan få flere oplysninger under [Simuler et phishing-angreb i Defender for Office 365](attack-simulation-training.md).

Hvis du vælger **Vis rapport over simuleringsdækning** , kommer du til [fanen Brugerdækning for simuleringsrapporten Angreb](#user-coverage-tab-for-the-attack-simulation-report).

:::image type="content" source="../../media/attack-sim-training-overview-sim-coverage-card.png" alt-text="Kortet Simuleringsdækning under fanen Oversigt i Oplæring af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-overview-sim-coverage-card.png":::

### <a name="training-completion-card"></a>Kort til fuldførelse af oplæring

Kortet **Oplæringsfuldførelse** under fanen **Oversigt** organiserer procentdelen af brugere, der har modtaget kurser baseret på resultaterne af simuleringer, i følgende kategorier:

- **Afsluttet**
- **Igangværende**
- **Ufuldstændig**

Du kan holde markøren over en sektion i diagrammet for at se det faktiske antal brugere i hver kategori.

Hvis du vælger **Vis rapport over oplæringsfuldførelse,** kommer du til [fanen Oplæringsfuldførelse for rapporten Simulering af angreb](#training-completion-tab-for-the-attack-simulation-report).

### <a name="repeat-offenders-card"></a>Kortet Gentag lovovertrædere

Kortet **Repeat offenders** under fanen **Overview (Oversigt)** viser oplysninger om gentagne lovovertrædere. En _gentaget gerningsmand_ er en bruger, der blev kompromitteret af flere simuleringer. Standardantallet af fortløbende simuleringer er to, men du kan ændre værdien på fanen **Indstillinger** under oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=setting>.

Diagrammet organiserer gentagne data for lovovertræderen efter [simuleringstype](attack-simulation-training.md#select-a-social-engineering-technique):

- **Alle**
- **Vedhæftet malware**
- **Link til malware**
- **Høst af legitimationsoplysninger**
- **Link i vedhæftede filer**
- **Drev efter URL-adresse**

Hvis du vælger **Vis rapport over gentagelsesovertrædere** , kommer du til [fanen Gentag lovovertrædere for rapporten Simulering af angreb](#repeat-offenders-tab-for-the-attack-simulation-report).

### <a name="recommendations-card"></a>Anbefalinger kort

Kortet **Anbefalinger** under fanen **Oversigt** foreslår forskellige simuleringstyper, der skal køres.

Hvis du vælger **Start,** startes guiden til oprettelse af simulering med den angivne simuleringstype automatisk valgt på siden **Vælg teknik** . Du kan få flere oplysninger under [Simuler et phishing-angreb i Defender for Office 365](attack-simulation-training.md).

:::image type="content" source="../../media/attack-sim-training-overview-recommendations-card.png" alt-text="Kortet Anbefalinger under fanen Oversigt under oplæring i simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-overview-recommendations-card.png":::

### <a name="attack-simulation-report"></a>Rapport over simulering af angreb

Du kan åbne **simuleringsrapporten angreb** fra fanen **Oversigt** ved at klikke på **vis ... rapportknapper** , der er tilgængelige på mange af de kort, der er beskrevet i denne artikel. Hvis du vil gå direkte til rapporten, skal du bruge <https://security.microsoft.com/attacksimulationreport>

#### <a name="training-efficacy-tab-for-the-attack-simulation-report"></a>Fanen Oplæringseffektivitet for rapporten over simulering af angreb

På **rapportsiden Simulering af angreb** er fanen **Træningseffektivitet** valgt som standard. Denne fane indeholder de samme oplysninger, som er tilgængelige på kortet **Funktionsmådepåvirkning på kompromitteret sats** , med yderligere kontekst fra selve simuleringen.

:::image type="content" source="../../media/attack-sim-report-training-efficacy-view.png" alt-text="Fanen Træningseffektivitet i rapporten om simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-report-training-efficacy-view.png":::

Diagrammet viser **den forudsagte kompromisrate** og **den faktiske kompromitterede sats**. Hvis du peger på en sektion i diagrammet, vises de faktiske procentværdier for.

I detaljetabellen under diagrammet vises følgende oplysninger:

- **Simuleringsnavn**
- **Simuleringsteknik**
- **Simuleringstaktik**
- **Forudsagt kompromitteret sats**
- **Faktisk kompromitteret sats**
- **Samlet antal brugere, der er målrettet**
- **Antal brugere, der klikkes på**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik på **Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på **Anvend**, når du er færdig.

Brug ![søgeikonet](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at filtrere resultaterne efter **simuleringsnavn** eller **simuleringsteknik**. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér rapport** . Status for oprettelse af rapport vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at åbne den .csv fil, gemme den .csv fil og huske markeringen.

#### <a name="user-coverage-tab-for-the-attack-simulation-report"></a>Fanen Brugerdækning for rapporten over simulering af angreb

:::image type="content" source="../../media/attack-sim-report-user-coverage-view.png" alt-text="Fanen Brugerdækning i rapporten over simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-report-user-coverage-view.png":::

Under fanen **Brugerdækning** vises de **simulerede brugere** og **ikke-simulerede brugere** i diagrammet. Hvis du holder markøren over et datapunkt i diagrammet, vises de faktiske værdier.

I detaljetabellen under diagrammet vises følgende oplysninger:

- **Brugernavn**
- **Mailadresse**
- **Inkluderet i simulering**
- **Dato for seneste simulering**
- **Sidste simuleringsresultat**
- **Antal klikkede**
- **Antal kompromitterede**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik på **Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på **Anvend**, når du er færdig.

Brug ![søgeikonet](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at filtrere resultaterne efter **brugernavn** eller **mailadresse**. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér rapport** . Status for oprettelse af rapport vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at åbne den .csv fil, gemme den .csv fil og huske markeringen.

#### <a name="training-completion-tab-for-the-attack-simulation-report"></a>Fanen Oplæringsfuldførelse for rapporten over simulering af angreb

:::image type="content" source="../../media/attack-sim-report-training-completion-view.png" alt-text="Fanen Fuldførelse af oplæring i rapporten over simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-report-training-completion-view.png":::

Under fanen **Oplæringsfuldførelse** viser diagrammet antallet af **fuldførte**, **igangværende** og **ufuldstændige** simuleringer. Hvis du holder markøren over en sektion i diagrammet, vises de faktiske værdier.

I detaljetabellen under diagrammet vises følgende oplysninger:

- **Brugernavn**
- **Mailadresse**
- **Inkluderet i simulering**
- **Dato for seneste simulering**
- **Sidste simuleringsresultat**
- **Navnet på den seneste fuldførte oplæring**
- **Dato for færdiggørelse**
- **Alle træninger**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik på **Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på **Anvend**, når du er færdig.

Klik på ![Filterikon.](../../media/m365-cc-sc-filter-icon.png) **Filtrer** for at filtrere diagrammet og detaljetabellen efter en eller flere af følgende værdier:

- **Afsluttet**
- **Igangværende**
- **Alle**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Brug ![søgeikonet](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at filtrere resultaterne efter **brugernavn** eller **mailadresse**. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér rapport** . Status for oprettelse af rapport vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at åbne den .csv fil, gemme den .csv fil og huske markeringen.

#### <a name="repeat-offenders-tab-for-the-attack-simulation-report"></a>Fanen Gentag lovovertrædere for rapporten over simulering af angreb

:::image type="content" source="../../media/attack-sim-report-repeat-offenders-view.png" alt-text="Fanen Repeat offenders i rapporten over simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-report-repeat-offenders-view.png":::

En _gentaget gerningsmand_ er en bruger, der blev kompromitteret af flere simuleringer. Standardantallet af fortløbende simuleringer er to, men du kan ændre værdien på fanen **Indstillinger** under oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=setting>.

På fanen **Repeat offenders (Gentag lovovertrædere** ) organiserer diagrammet data for gentagne lovovertrædere efter [simuleringstype](attack-simulation-training.md#select-a-social-engineering-technique):

- **Alle**
- **Høst af legitimationsoplysninger**
- **Vedhæftet malware**
- **Link i vedhæftet fil**
- **Link til malware**
- **Drev efter URL-adresse**

Hvis du holder markøren over et datapunkt i diagrammet, vises de faktiske værdier.

I detaljetabellen under diagrammet vises følgende oplysninger:

- **Bruger**
- **Antal gentagelser**
- **Simuleringstyper**
- **Simuleringer**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik på **Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på **Anvend**, når du er færdig.

Klik på ![Filterikon.](../../media/m365-cc-sc-filter-icon.png) **Filtrer** for at filtrere diagrammet og detaljetabellen efter nogle eller alle værdier af simuleringstypen:

- **Høst af legitimationsoplysninger**
- **Vedhæftet malware**
- **Link i vedhæftet fil**
- **Link til malware**
- **Drev efter URL-adresse**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Brug ![søgeikonet](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at filtrere resultaterne efter en af kolonneværdierne. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér rapport** . Status for oprettelse af rapport vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at åbne den .csv fil, gemme den .csv fil og huske markeringen.

## <a name="insights-and-reports-in-the-simulation-details-of-attack-simulation-training"></a>Insights og rapporter i simuleringsdetaljerne for oplæringen af angrebssimulering

Hvis du vil gå til fanen **Simuleringer**, skal du åbne portalen Microsoft 365 Defender på <https://security.microsoft.com>, gå til **Mail & samarbejde** \> **Oplæring af simulering af angreb** og derefter vælge fanen **Simuleringer**. Hvis du vil gå direkte til fanen **Simuleringer** på træningssiden **Angrebssimulering**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulations>.

Når du vælger en simulering på listen, åbnes der en side med detaljer. Denne side indeholder konfigurationsindstillingerne for den simulering, du forventer at se (status, startdato, anvendt nyttedata osv.).

I resten af dette afsnit beskrives de indsigter og rapporter, der er tilgængelige på siden med simuleringsoplysninger.

### <a name="simulation-impact-section"></a>Afsnit om simuleringseffekt

Afsnittet **Effekt af simulering** på siden med simuleringsoplysninger viser, hvor mange brugere der blev helt narret af simuleringen og det samlede antal brugere i simuleringen. De viste oplysninger varierer afhængigt af simuleringstypen. Eksempel:

- Links: **Angivne legitimationsoplysninger** og **Har ikke angivet legitimationsoplysninger**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-links.png" alt-text="Afsnittet Simuleringseffekt for linkrelaterede simuleringsoplysninger" lightbox="../../media/attack-sim-training-sim-details-sim-impact-links.png":::

- Vedhæftede filer: **Den vedhæftede fil** **blev åbnet, og den vedhæftede fil blev ikke åbnet**.

  :::image type="content" source="../../media/attack-sim-training-sim-details-sim-impact-attachments.png" alt-text="Afsnittet Simuleringseffekt for oplysninger om vedhæftning relateret til simulering" lightbox="../../media/attack-sim-training-sim-details-sim-impact-attachments.png":::

Hvis du peger på en sektion i diagrammet, vises de faktiske tal for hver kategori.

### <a name="all-user-activity-section"></a>Alle brugeraktivitetsafsnit

Afsnittet **Alle brugeraktivitet** på siden med simuleringsoplysninger viser tal for de mulige resultater af simuleringen. De viste oplysninger varierer afhængigt af simuleringstypen. Eksempel:

- **Mail, der er oprettet**
- **ReportedEmail**: Hvor mange brugere, der rapporterede simuleringsmeddelelsen som mistænkelig.
- Links:
  - **EmailLinkClicked**: Hvor mange brugere, der klikkede på linket i simuleringsmeddelelsen.
  - **CredSupplied**: Når du har klikket på linket, hvor mange brugere der har angivet deres legitimationsoplysninger.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-links.png" alt-text="Afsnittet Alle brugeraktivitet for linkrelaterede simuleringsoplysninger" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-links.png":::

- Vedhæftede filer:
  - **AttachmentOpened**: Hvor mange brugere, der har åbnet den vedhæftede fil i simuleringsmeddelelsen.

    :::image type="content" source="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png" alt-text="Afsnittet Alle brugeraktivitet for oplysninger om simulering relateret til vedhæftede filer" lightbox="../../media/attack-sim-training-sim-details-all-user-activity-attachments.png":::

### <a name="training-completion-section"></a>Afsnittet Oplæringsfuldførelse

Afsnittet **Oplæringsafslutning** på siden med simuleringsoplysninger viser de oplæringer, der kræves til simuleringen, og hvor mange brugere der har gennemført træningerne.

:::image type="content" source="../../media/attack-sim-training-sim-details-training-completed.png" alt-text="Afsnittet Oplæringsafslutning for oplysninger om simulering relateret til vedhæftede filer" lightbox="../../media/attack-sim-training-sim-details-training-completed.png":::

## <a name="recommended-actions-section"></a>Afsnittet Anbefalede handlinger

Afsnittet **Anbefalede handlinger** på siden med simuleringsoplysninger viser anbefalingshandlinger fra [Microsoft Secure Score](../defender/microsoft-secure-score.md) og den effekt, handlingen vil have på din Secure Score. Disse anbefalinger er baseret på de nyttedata, der blev brugt i simuleringen, og hjælper med at beskytte dine brugere og dit miljø. Hvis du vælger en **forbedringshandling** på listen, kommer du til placeringen for at implementere den foreslåede handling.

:::image type="content" source="../../media/attack-sim-training-sim-details-recommended-actions.png" alt-text="Afsnittet Anbefalingshandlinger om træning i simulering af angreb" lightbox="../../media/attack-sim-training-sim-details-recommended-actions.png":::

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge kursus i angrebssimulering](attack-simulation-training-get-started.md)

[Opret en simulering af phishingangreb](attack-simulation-training.md)

[oprette en nyttedata til oplæring af dine personer](attack-simulation-training-payloads.md#create-payloads)
