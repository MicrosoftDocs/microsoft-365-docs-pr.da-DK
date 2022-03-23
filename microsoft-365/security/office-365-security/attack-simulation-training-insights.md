---
title: Insights og rapporter kursus i simulering af angreb
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
description: Administratorer kan lære, hvordan simulering af angreb på Microsoft 365 Defender-portalen påvirker brugere og kan få indsigt fra simulering og kursusresultater.
ms.technology: mdo
ms.openlocfilehash: c06cea01fcc7bb8fdc9c869fe8117f85eb627685
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589848"
---
# <a name="insights-and-reports-for-attack-simulation-training-in-defender-for-office-365"></a>Insights og rapporter for angrebssimuleringskursus i Defender Office 365

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

I angrebssimuleringstræning i Microsoft Defender Office Plan 2 eller Microsoft 365 E5 leverer Microsoft indsigt og rapporter fra resultaterne af simuleringerne og de tilsvarende kurser. Disse oplysninger holder dig informeret om status for trusselsparathed for dine brugere samt anbefalede næste trin for bedre at forberede dine brugere til fremtidige angreb.

Insights og rapporter er tilgængelige på følgende placeringer i Kursus i angrebssimulering på Microsoft 365 Defender portalen:

- **Fanen Oversigt**.
- Detaljer om simulering under **fanen Simulering** .

I resten af denne artikel beskrives de tilgængelige oplysninger.

Du kan finde oplysninger om kursus i at simulere angreb i [Kom i gang med at bruge simulering af angreb](attack-simulation-training-get-started.md).

## <a name="insights-and-reports-on-the-overview-tab-of-attack-simulation-training"></a>Insights og rapporter på fanen Oversigt over angrebssimuleringskursus

For at gå til  fanen Oversigt skal du åbne Microsoft 365 Defender-portalen på , gå til Mail **&** \> samarbejde– **Simulering** af angreb og kontrollere, at  <https://security.microsoft.com>fanen Oversigt er valgt (det er standard). For at gå direkte til fanen **Oversigt på** siden til **simulering af angreb skal** du bruge <https://security.microsoft.com/attacksimulator?viewid=overview>.

Resten af dette afsnit beskriver de oplysninger, der er tilgængelige på fanen Oversigt **over simulering** af angreb.

### <a name="recent-simulations-card"></a>Seneste simuleringskort

Kortet **Seneste simuleringer** på **fanen Oversigt** viser de sidste tre simuleringer, du har oprettet eller kørt i organisationen.

Du kan vælge en simulering for at få vist detaljer.

Hvis du **vælger Vis alle simuleringer,** kommer du til **fanen Simuleringer** .

Når du vælger **Start en simulering** , startes guiden til oprettelse af simulering. Du kan få mere at vide [under Simulere et phishingangreb i Defender Office 365](attack-simulation-training.md).

![Seneste simuleringskort på fanen Oversigt i Kursus i angrebssimulering på Microsoft 365 Defender portal.](../../media/attack-sim-training-overview-recent-simulations-card.png)

### <a name="behavior-impact-on-compromise-rate-card"></a>Funktionsmådepåvirkning på forligssatskort

**Funktionsmåden påvirker forligssatskortet** på fanen Oversigt og viser, hvordan brugerne har reageret på dine simuleringer i forhold til de historiske data Microsoft 365. Du kan bruge denne indsigt til at registrere fremskridt i brugeres trusselsparathed ved at køre flere simuleringer mod de samme grupper af brugere.

Selve diagramdataene viser følgende oplysninger:

- **Forudsagte forligssats**<sup>\*</sup>: Den gennemsnitlige forligssats for simulering af angrebssimulering, der bruger den samme type nyttedata på tværs af Microsoft 365 organisationer.
- **Faktisk forligssats**<sup>\*</sup>: Den faktiske procentdel af brugere, der faldt for simulering.

Hvis du peger på et datapunkt i diagrammet, vises de faktiske procentværdier.

Følgende oversigtsoplysninger vises også på kortet:

- **Brugere mindre følsomme over for phishing**: Forskellen mellem det faktiske antal brugere, der er kompromitteret ved den simulerede angreb og den forventede forfaldshastighed. Dette antal brugere er mindre tilbøjelige til at blive kompromitteret af lignende angreb i fremtiden.
- **x % bedre end forventet rente**: Angiver, hvordan brugerne generelt gjorde det i modsætning til den forventede forligssats.

![Adfærdspåvirkning på forfaldskortet på fanen Oversigt i Angrebssimuleringskursus i Microsoft 365 Defender portal.](../../media/attack-sim-training-overview-behavior-impact-card.png)

Hvis du vil have vist en mere detaljeret rapport, skal **du klikke på Vis simulering og rapporten over undervisningsfuldhed**. Denne rapport forklares [senere i denne artikel](#training-efficacy-tab-for-the-attack-simulation-report).

### <a name="simulation-coverage-card"></a>Simulerings dækningskort

Kortet **Simulerings** dækning  under fanen Oversigt viser procentdelen af brugere i organisationen, som har modtaget en simulering **(** Simulerede brugere) i forhold til dem, der ikke har modtaget en simulering (**ikke-simulerede brugere**). Du kan pege på en sektion i diagrammet for at få vist det faktiske antal brugere i hver kategori.

Når du **vælger Start simulering for ikke-simulerede** brugere, starter guiden til oprettelse af simulering, hvor de brugere, der ikke har modtaget simulering, automatisk vælges på **siden Målbruger** . Du kan få mere at vide [under Simulere et phishingangreb i Defender Office 365](attack-simulation-training.md).

Hvis du vælger **Vis simulerings dækningsrapport** , kommer du til [fanen Bruger dækning for angrebssimuleringsrapporten](#user-coverage-tab-for-the-attack-simulation-report).

![Simulerings dækningskort på fanen Oversigt i Kursus i angrebssimulering Microsoft 365 Defender portalen.](../../media/attack-sim-training-overview-sim-coverage-card.png)

### <a name="training-completion-card"></a>Fuldførelseskort for kurser

Kortet **Til fuldførelse** **af kurser på** fanen Oversigt organiserer procentdelene af brugere, der har modtaget kurser baseret på resultaterne af simulering, i følgende kategorier:

- **Fuldført**
- **I gang**
- **Ufuldstændig**

Du kan pege på en sektion i diagrammet for at få vist det faktiske antal brugere i hver kategori.

Hvis du **vælger Vis rapport over fuldførelse af kurser** , kommer du til [fanen Træning](#training-completion-tab-for-the-attack-simulation-report) i simulering af angreb.

### <a name="repeat-offenders-card"></a>Gentag kortet

Kortet **Gentag vises på** fanen **Oversigt og viser** oplysninger om gentagelser. En _gentagelse er en_ bruger, der er blevet kompromitteret af flere simuleringer efter hinanden. Standardtallet af fortløbende simuleringer er <https://security.microsoft.com/attacksimulator?viewid=setting>to, men du kan ændre værdien på fanen **Indstillinger** i Angrebssimulering på .

Diagrammet organiserer gentagelser af data fra [simuleringstypen](attack-simulation-training.md#select-a-social-engineering-technique):

- **Alle**
- **Vedhæftet malware**
- **Link til malware**
- **Indsamling af legitimationsoplysninger**
- **Link i vedhæftede filer**
- **Drive-by URL**

Hvis du vælger **Vis gentagelse-rapport, kommer** du til [fanen Gentag gentagelse for at bruge simuleringsrapporten for angreb](#repeat-offenders-tab-for-the-attack-simulation-report).

### <a name="recommendations-card"></a>Anbefalinger kort

Kortet **Anbefalinger** oversigt **foreslår forskellige typer** simulering at køre.

Når du vælger **Start, starter** du nu guiden til oprettelse af simulering med den angivne simuleringstype valgt automatisk på **siden Vælg** teknik. Du kan få mere at vide [under Simulere et phishingangreb i Defender Office 365](attack-simulation-training.md).

![Anbefalinger på fanen Oversigt i Kursus i angrebssimulering på Microsoft 365 Defender portal.](../../media/attack-sim-training-overview-recommendations-card.png)

### <a name="attack-simulation-report"></a>Rapport over angrebssimulering

Du kan åbne **simuleringsrapporten** for angreb **fra** fanen Oversigt ved at klikke på **Vis ... rapportknapper** , der er tilgængelige på mange af de kort, der er beskrevet i denne artikel. Hvis du vil gå direkte til rapporten, skal du bruge <https://security.microsoft.com/attacksimulationreport>

#### <a name="training-efficacy-tab-for-the-attack-simulation-report"></a>Fanen Til uddannelse af effekt for angrebssimuleringsrapporten

På siden **Rapport for angrebssimulering** **er fanen Kursusfuldhed** valgt som standard. Denne fane indeholder de samme oplysninger, der er tilgængelige i Funktionsmådepåvirkning på kortet Forligssats med yderligere kontekst fra simulering selv.

![Fanen Til uddannelse af effektivitet i angrebssimuleringsrapporten Microsoft 365 Defender portalen.](../../media/attack-sim-report-training-efficacy-view.png)

Diagrammet viser den forventede **forligssats** og **den faktiske kompromitterede rente**. Hvis du peger på en sektion i diagrammet, vises de faktiske procentværdier.

Detaljetabellen under diagrammet viser følgende oplysninger:

- **Simuleringsnavn**
- **Simuleringsteknik**
- **Simuleringstaktik**
- **Forudsagte kompromitterede rate**
- **Faktisk kompromitteret rente**
- **Samlet antal brugere målrettet**
- **Antallet af brugere, der klikkes på**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik **på Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på Anvend, når du er **færdig**.

Brug ![søgeikonets](../../media/m365-cc-sc-search-icon.png) **søgefelt** til at filtrere resultaterne efter **Simuleringsnavn** **eller Simuleringsteknik**. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér** rapport, status for oprettelse af rapporter vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at .csv filen, gemme .csv fil og huske markeringen.

#### <a name="user-coverage-tab-for-the-attack-simulation-report"></a>Fanen Bruger dækning for angrebssimuleringsrapporten

![Fanen Brugerdækning i angrebssimuleringsrapporten Microsoft 365 Defender portalen.](../../media/attack-sim-report-user-coverage-view.png)

På fanen **Bruger dækning** viser diagrammet Simulerede brugere **og** **Ikke-simulerede brugere**. Hvis du peger på et datapunkt i diagrammet, vises de faktiske værdier.

Detaljetabellen under diagrammet viser følgende oplysninger:

- **Brugernavn**
- **Mailadresse**
- **Inkluderet i simulering**
- **Dato for sidste simulering**
- **Sidste simuleringsresultat**
- **Antal klikkede**
- **Antallet af kompromitterede**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik **på Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på Anvend, når du er **færdig**.

Brug ![**søgeikonets**](../../media/m365-cc-sc-search-icon.png) søgefelt til at filtrere resultaterne efter **Brugernavn** **eller Mailadresse**. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér** rapport, status for oprettelse af rapporter vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at .csv filen, gemme .csv fil og huske markeringen.

#### <a name="training-completion-tab-for-the-attack-simulation-report"></a>Fanen Til fuldførelse af kursus for angrebssimuleringsrapporten

![Fanen Til fuldførelse af kurser i angrebssimuleringsrapporten Microsoft 365 Defender portalen.](../../media/attack-sim-report-training-completion-view.png)

På fanen **Fuldførelse af** kurser viser diagrammet antallet af **fuldførte,** **igangværende og** **ufuldstændige** simulering. Hvis du peger på en sektion i diagrammet, vises de faktiske værdier.

Detaljetabellen under diagrammet viser følgende oplysninger:

- **Brugernavn**
- **Mailadresse**
- **Inkluderet i simulering**
- **Dato for sidste simulering**
- **Sidste simuleringsresultat**
- **Navnet på det senest fuldførte kursus**
- **Dato fuldført**
- **Alle kurser**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik **på Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på Anvend, når du er **færdig**.

Klik ![på filterikonet.](../../media/m365-cc-sc-filter-icon.png) **Filtrer** for at filtrere tabellen med diagram og detaljer efter en eller flere af følgende værdier:

- **Fuldført**
- **I gang**
- **Alle**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Brug ![**søgeikonets**](../../media/m365-cc-sc-search-icon.png) søgefelt til at filtrere resultaterne efter **Brugernavn** **eller Mailadresse**. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér** rapport, status for oprettelse af rapporter vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at .csv filen, gemme .csv fil og huske markeringen.

#### <a name="repeat-offenders-tab-for-the-attack-simulation-report"></a>Fane med gentagelser for angrebssimuleringsrapporten

![Gentag fanen med gentagelser i angrebssimuleringsrapporten Microsoft 365 Defender portalen.](../../media/attack-sim-report-repeat-offenders-view.png)

En _gentagelse er en_ bruger, der er blevet kompromitteret af flere simuleringer efter hinanden. Standardtallet af fortløbende simuleringer er <https://security.microsoft.com/attacksimulator?viewid=setting>to, men du kan ændre værdien på fanen **Indstillinger** i Angrebssimulering på .

På fanen **Gentag gentagelser arrangerer** diagrammet gentagelser af simuleringsdata ved hjælp [af simuleringstype](attack-simulation-training.md#select-a-social-engineering-technique):

- **Alle**
- **Indsamling af legitimationsoplysninger**
- **Vedhæftet malware**
- **Link i vedhæftet fil**
- **Link til malware**
- **Drive-by URL**

Hvis du peger på et datapunkt i diagrammet, vises de faktiske værdier.

Detaljetabellen under diagrammet viser følgende oplysninger:

- **Bruger**
- **Antal gentagelser**
- **Simuleringstyper**
- **Simulering**

Du kan sortere resultaterne ved at klikke på en tilgængelig kolonneoverskrift.

Klik **på Tilpas kolonner** for at fjerne de kolonner, der vises. Klik på Anvend, når du er **færdig**.

Klik ![på filterikonet.](../../media/m365-cc-sc-filter-icon.png) **Filtrer** for at filtrere diagrammet og detaljetabellen efter nogle eller alle værdierne for simuleringstypen:

- **Indsamling af legitimationsoplysninger**
- **Vedhæftet malware**
- **Link i vedhæftet fil**
- **Link til malware**
- **Drive-by URL**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Brug ![**søgeikonets**](../../media/m365-cc-sc-search-icon.png) søgefelt til at filtrere resultaterne efter kolonneværdierne. Jokertegn understøttes ikke.

Hvis du klikker på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksportér** rapport, status for oprettelse af rapporter vises som en procentdel af fuldført. I den dialogboks, der åbnes, kan du vælge at .csv filen, gemme .csv fil og huske markeringen.

## <a name="insights-and-reports-in-the-simulation-details-of-attack-simulation-training"></a>Insights og rapporter i simuleringsdetaljerne for angrebssimuleringskursus

Gå til fanen **Simuleringer** ved at <https://security.microsoft.com>åbne Microsoft 365 Defender-portalen på , gå til Mail **&** \> kursus i simulering af **samarbejde, og** vælg derefter fanen **Simulering**. For at gå direkte til fanen **Simulering på** siden for angrebssimulering **skal** du bruge <https://security.microsoft.com/attacksimulator?viewid=simulations>.

Når du vælger en simulering på listen, åbnes en detaljeside. Denne side indeholder konfigurationsindstillingerne for simulering, som du ville forvente at se (status, startdato, nyttedata osv.).

Resten af dette afsnit beskriver indsigter og rapporter, der er tilgængelige på siden med simuleringsoplysninger.

### <a name="simulation-impact-section"></a>Afsnittet Simuleringspåvirkning

Afsnittet **Om Simuleringspåvirkning** på siden med simuleringsoplysninger viser, hvor mange brugere der blev narret fuldstændigt af simulering, og det samlede antal brugere i simulering. De viste oplysninger varierer afhængigt af simuleringstypen. Eksempel:

- Links: **Indtastede legitimationsoplysninger** **og Indtastede ikke legitimationsoplysninger**.

  ![Sektionen Simuleringspåvirkning for linkrelaterede simuleringsoplysninger.](../../media/attack-sim-training-sim-details-sim-impact-links.png)

- Vedhæftede filer: **Åbnet vedhæftet fil og** Har **ikke åbnet vedhæftet fil**.

  ![Afsnittet Simulering af virkning for simuleringsrelaterede simuleringsoplysninger.](../../media/attack-sim-training-sim-details-sim-impact-attachments.png)

Hvis du peger på en sektion i diagrammet, vises de faktiske tal for hver kategori.

### <a name="all-user-activity-section"></a>Sektionen Alle brugeraktiviteter

Sektionen **Alle brugeraktivitet på** siden med simuleringsdetaljer viser tal for de mulige udfald af simulering. De viste oplysninger varierer afhængigt af simuleringstypen. Eksempel:

- **LeveretEmail**
- **ReportedEmail**: Hvor mange brugere har rapporteret simuleringsmeddelelsen som mistænkelig.
- Links:
  - **EmailLinkKlik: Hvor** mange brugere der klikkede på linket i simuleringsmeddelelsen.
  - **CredSupplied**: Når du har klikket på linket, hvor mange brugere har angivet deres legitimationsoplysninger.

    ![Sektionen Alle brugeraktivitet for linkrelaterede simuleringsoplysninger.](../../media/attack-sim-training-sim-details-all-user-activity-links.png)

- Vedhæftede filer:
  - **Vedhæftet filÅbnet**: Hvor mange brugere der åbnede den vedhæftede fil i simuleringsmeddelelsen.

    ![Sektionen Alle brugeraktiviteter til simuleringsrelaterede simuleringsoplysninger.](../../media/attack-sim-training-sim-details-all-user-activity-attachments.png)

### <a name="training-completion-section"></a>Sektionen Fuldførelse af kurser

Afsnittet **Om fuldførelse** af kurser på siden med simuleringsdetaljer viser de kurser, der kræves til simulering, og hvor mange brugere der har fuldført kurserne.

![Sektionen Til fuldførelse af uddannelse til simuleringsrelaterede simuleringsoplysninger.](../../media/attack-sim-training-sim-details-training-completed.png)

## <a name="recommended-actions-section"></a>Sektionen Anbefalede handlinger

Afsnittet **Anbefalede handlinger** på siden med simuleringsoplysninger viser anbefalede handlinger fra [Microsoft Secure Score](../defender/microsoft-secure-score.md) og den effekt, handlingen har på din Secure Score. Disse anbefalinger er baseret på den nyttebelastning, der blev brugt i simulering, og hjælper med at beskytte dine brugere og dit miljø. Når du vælger **en forbedringshandling** på listen, kommer du til placeringen for at implementere den foreslåede handling.

![Sektionen Anbefalingshandlinger på kursus i angrebssimulering.](../../media/attack-sim-training-sim-details-recommended-actions.png)

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge simuleringskursus til angreb](attack-simulation-training-get-started.md)

[Opret en simulering af phishingangreb](attack-simulation-training.md)

[opret en nyttedata til uddannelse af dine medarbejdere](attack-simulation-training-payloads.md)
