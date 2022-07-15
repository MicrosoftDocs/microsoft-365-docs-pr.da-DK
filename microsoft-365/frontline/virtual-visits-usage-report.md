---
title: Brugsrapport for virtuelle besøg i Microsoft Teams
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: Admin
ms.topic: article
ms.service: microsoft-365-frontline
ms.reviewer: ''
f1.keywords:
- NOCSH
ms.localizationpriority: high
search.appverid: MET150
ms.collection:
- M365-collaboration
- m365-frontline
description: Få mere at vide om, hvordan du bruger brugsrapporten for virtuelle besøg i Microsoft Teams Administration til at få et overblik over aktiviteter med virtuelle aftaler i din organisation.
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5f609ebb1d48e1e7c9b55d2998c793403dec8fa0
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66824125"
---
# <a name="microsoft-teams-virtual-visits-usage-report"></a>Brugsrapport for virtuelle besøg i Microsoft Teams

Brugsrapporten for virtuelle besøg i Microsoft Teams Administration giver dig et overblik over Teams's virtuelle aftaleaktivitet i din organisation. Du kan få vist detaljeret aktivitet for virtuelle aftaler, der er planlagt via [Bookings-appen](bookings-virtual-visits.md) og [MICROSOFT Teams EHR-connectoren (Electronic Health Record](teams-in-hc.md#virtual-appointments-and-electronic-healthcare-record-ehr-integration)).

Hvis du vil have vist rapporten, skal du være global administrator eller Teams-administrator.

Rapporten indeholder følgende faner. De oplysninger, du får vist i rapporten, afhænger af, om du har en licens til Bookings-appen, Teams EHR-connectoren eller begge dele.

|Tab |Beskrivelse  |
|---------|---------|
|**[Virtuelle besøg](#virtual-visits)**     |Viser det samlede antal virtuelle aftaler med en oversigt over antallet af aftaler, der er planlagt ved hjælp af Bookings-appen, og Teams EHR-integrerede møder, der udføres fra dit EHR-system.         |
|**[Varighed](#duration)**     |Viser den gennemsnitlige varighed af aftaler og den gennemsnitlige lobbyventetid for deltagere.         |
|**[Bookinger](#bookings)**     |Viser antallet af aftaler, der er planlagt via appen Bookings.         |
|**[EHR](#ehr)**     |Viser antallet af Teams EHR-integrerede aftaler, der udføres fra dit EHR-system.         |  

Brug denne rapport til at få indsigt i aktiviteter og tendenser for virtuelle aftaler i din organisation. Oplysningerne kan hjælpe dig med at optimere virtuelle aftaler for at levere bedre forretningsresultater.

## <a name="view-the-virtual-visits-usage-report"></a>Få vist forbrugsrapporten for virtuelle besøg

1. I venstre navigationsrude i Microsoft Teams Administration skal du vælge **Analytics & rapporter** > **Forbrugsrapporter**. Under fanen **Vis rapporter** under **Rapport** skal du vælge **Brug af virtuelle besøg**.
2. Under **Datointerval** skal du vælge et datointerval på 7 dage, 30 dage eller 90 dage. Vælg derefter **Kør rapport**.

> [!NOTE]
> Som standard er analyse af virtuelle besøg slået til, og rapporten er tilgængelig. Når du bruger denne rapport, giver du Microsoft tilladelse til at indsamle data om virtuelle aftaler i din organisation. Du kan få oplysninger om vores politikker for dataopbevaring under [Dataopbevaring, sletning og destruktion i Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).
>
>Hvis du vil slå rapporten for din organisation fra, kan du gøre det i **Indstillinger** i øverste højre hjørne af siden. Det kan tage mellem 0 (nul) og 2 timer, før denne indstilling træder i kraft, når du har ændret den.

## <a name="interpret-the-report"></a>Fortolkning af rapporten

### <a name="virtual-visits"></a>Virtuelle besøg

De grafer, du får vist her, afhænger af, om du har en licens til Bookings-appen, Teams EHR-connectoren eller begge dele. Du kan få mere at vide under [Administrer Bookings-appen](/microsoftteams/bookings-app-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json) og [Integration i Cerner EHR](ehr-admin-cerner.md) eller [Integration into Epic EHR](ehr-admin-epic.md).

:::image type="content" source="media/virtual-visits-usage-report-virtual-visits.png" alt-text="Skærmbillede af fanen Virtuelle besøg i brugsrapporten for virtuelle besøg, der viser nummererede billedforklatter." lightbox="media/virtual-visits-usage-report-virtual-visits.png":::

|Billedforklaring |Beskrivelse  |
|--------|-------------|
|**1**   |Hver rapport har en dato for, hvornår rapporten blev genereret. Rapporterne afspejler normalt en ventetid på 24 til 48 timer fra aktivitetstidspunktet. |
|**2**   |X-aksen er det valgte datointerval for rapporten. Y-aksen er antallet af aftaler.<br>Peg på prik på en given dato for at se antallet af aftaler på den pågældende dato.|
|**3**   |Du kan filtrere det, du ser i diagrammet, ved at vælge et element i forklaringen. Du kan f.eks. vælge **Samlet antal bookinger virtuelle besøg** eller **samlet antal virtuelle EHR-besøg** for kun at se de oplysninger, der er relateret til hver enkelt. Hvis du ændrer markeringen, ændres oplysningerne i tabellen ikke. |
|**4**   |Tabellen indeholder detaljerede oplysninger om hver aftale, der fandt sted i løbet af det valgte datointerval. <ul><li>**Starttidspunkt (UTC)** er den dato og det klokkeslæt, hvor både en medarbejder og deltager deltager i mødet, eller hvor den første aktivitet fandt sted i mødet.  </li> <li>**Møde-id'et** er det entydige id for mødet.</li> <li>**Ventetid for lobby** er tiden mellem, hvor en deltager første gang tilmelder sig lobbyen, til den samme deltager eller en anden deltager får adgang til mødet af en medarbejder.</li><li>**Varighed** er tidsforskellen mellem starttidspunktet, og hvornår den sidste person forlader mødet. Hvis både en medarbejder og en deltager ikke deltog i mødet, vises varigheden som 0 (nul).</li> <li>**Status** viser mødestatussen. <ul><li>**Fuldført**: Hvis en eller flere medarbejdere og deltagere deltager i mødet, og mødet er afsluttet. Eller hvis en eller flere deltagere deltager i mødet, og mødet er afsluttet.</li> <li> **Ingen visning**: Hvis en medarbejder deltager i mødet, men ingen andre deltager, og mødet er afsluttet. </li></ul> </li> <li>**Mødetype** angiver, om den virtuelle aftale blev planlagt via Appen Bookings eller Teams EHR-connectoren.</li> <li>**Deltagere** er det samlede antal medarbejdere og deltagere i mødet.</li> <li>**SMS sendt** angiver, om der blev sendt en sms-meddelelse til deltagerne. </li> </li> </ul> |
|**5**   |Vælg **Indstillinger** for at åbne ruden **Analyse af virtuelle besøg** . Herfra kan du slå rapportering af virtuelle besøg fra eller til for din organisation og tilføje eller fjerne kolonner i tabellen. Hvis du vil se de ønskede oplysninger i tabellen, skal du sørge for at føje kolonnerne til tabellen.|
|**6**   |Du kan eksportere rapporten til en CSV-fil til offlineanalyse. Vælg **Eksportér til Excel**, og vælg derefter **Download** under fanen **Downloads** for at downloade rapporten, når den er klar.|

### <a name="duration"></a>Varighed

:::image type="content" source="media/virtual-visits-usage-report-duration.png" alt-text="Skærmbillede af fanen Varighed i rapporten over brug af virtuelle besøg, der viser nummererede billedforklatter." lightbox="media/virtual-visits-usage-report-duration.png":::

|Billedforklaring |Beskrivelse  |
|--------|-------------|
|**1**   |Hver rapport har en dato for, hvornår rapporten blev genereret. Rapporterne afspejler normalt en ventetid på 24 til 48 timer fra aktivitetstidspunktet. |
|**2**   |X-aksen er det valgte datointerval for rapporten. Y-aksen er antallet af minutter.<br>Peg på prik på en given dato for at se den gennemsnitlige aftalevarighed eller den gennemsnitlige lobbyventetid for en bestemt dato.  |
|**3**   |Du kan filtrere det, du ser i diagrammet, ved at vælge et element i forklaringen. Du kan f.eks. vælge **Gennemsnitlig varighed af virtuelt besøg** eller **Gennemsnitlig ventetid for lobbyen** for kun at se de oplysninger, der er relateret til hver enkelt. Hvis du ændrer markeringen, ændres oplysningerne i tabellen ikke. |
|**4**   |Tabellen indeholder detaljerede oplysninger om hver aftale, der fandt sted i løbet af det valgte datointerval. <ul><li>**Starttidspunkt (UTC)** er den dato og det klokkeslæt, hvor både en medarbejder og deltager deltager i mødet, eller hvor den første aktivitet fandt sted i mødet.  </li> <li>**Møde-id'et** er det entydige id for mødet.</li> <li>**Ventetid for lobby** er tiden mellem, hvor en deltager første gang tilmelder sig lobbyen, til den samme deltager eller en anden deltager får adgang til mødet af en medarbejder.</li><li>**Varighed** er tidsforskellen mellem starttidspunktet, og hvornår den sidste person forlader mødet. Hvis både en medarbejder og en deltager ikke deltog i mødet, vises varigheden som 0 (nul).</li> <li>**Status** viser mødestatussen. <ul><li>**Fuldført**: Hvis en eller flere medarbejdere og deltagere deltager i mødet, og mødet er afsluttet. Eller hvis en eller flere deltagere deltager i mødet, og mødet er afsluttet.</li> <li> **Ingen visning**: Hvis en medarbejder deltager i mødet, men ingen andre deltager, og mødet er afsluttet. </li></ul> </li> <li>**Mødetype** angiver, om den virtuelle aftale blev planlagt via Appen Bookings eller Teams EHR-connectoren.</li> <li>**Deltagere** er det samlede antal medarbejdere og deltagere i mødet.</li> <li>**SMS sendt** angiver, om der blev sendt en sms-meddelelse til deltagerne. </li> </li> </ul>|
|**5**   |Vælg **Indstillinger** for at åbne ruden **Analyse af virtuelle besøg** . Herfra kan du slå rapportering af virtuelle besøg fra eller til for din organisation og tilføje eller fjerne kolonner i tabellen. Hvis du vil se de ønskede oplysninger i tabellen, skal du sørge for at føje kolonnerne til tabellen.|
|**6**   |Du kan eksportere rapporten til en CSV-fil til offlineanalyse. Vælg **Eksportér til Excel**, og vælg derefter **Download** under fanen **Downloads** for at downloade rapporten, når den er klar.|
### <a name="bookings"></a>Bookinger

Du får vist denne fane, hvis du har en licens, der indeholder appen Bookings. Du kan få mere at vide under [Administrer appen Bookings](/microsoftteams/bookings-app-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

:::image type="content" source="media/virtual-visits-usage-report-bookings.png" alt-text="Skærmbillede af fanen Bookinger i brugsrapporten for virtuelle besøg, der viser nummererede billedforklatter." lightbox="media/virtual-visits-usage-report-bookings.png":::

|Billedforklaring |Beskrivelse  |
|--------|-------------|
|**1**   |Hver rapport har en dato for, hvornår rapporten blev genereret. Rapporterne afspejler normalt en ventetid på 24 til 48 timer fra aktivitetstidspunktet. |
|**2**   |X-aksen er det valgte datointerval for rapporten. Y-aksen er antallet af Bookings-aftaler.<br>Peg på prik på en given dato for at se antallet af Bookings-aftaler, der fandt sted på den pågældende dato.|
|**3**   |Tabellen indeholder detaljerede oplysninger om hver aftale, der fandt sted i løbet af det valgte datointerval. <ul><li>**Starttidspunkt (UTC)** er den dato og det klokkeslæt, hvor både en medarbejder og deltager deltager i mødet, eller hvor den første aktivitet fandt sted i mødet.  </li> <li>**Møde-id'et** er det entydige id for mødet.</li> <li>**Ventetid for lobby** er tiden mellem, hvor en deltager første gang tilmelder sig lobbyen, til den samme deltager eller en anden deltager får adgang til mødet af en medarbejder.</li><li>**Varighed** er tidsforskellen mellem starttidspunktet, og hvornår den sidste person forlader mødet. Hvis både en medarbejder og en deltager ikke deltog i mødet, vises varigheden som 0 (nul).</li> <li>**Status** viser mødestatussen. <ul><li>**Fuldført**: Hvis en eller flere medarbejdere og deltagere deltager i mødet, og mødet er afsluttet. Eller hvis en eller flere deltagere deltager i mødet, og mødet er afsluttet.</li> <li> **Ingen visning**: Hvis en medarbejder deltager i mødet, men ingen andre deltager, og mødet er afsluttet. </li></ul> </li> <li>**Mødetype** angiver, om den virtuelle aftale blev planlagt via Appen Bookings eller Teams EHR-connectoren.</li> <li>**Deltagere** er det samlede antal medarbejdere og deltagere i mødet.</li> <li>**SMS sendt** angiver, om der blev sendt en sms-meddelelse til deltagerne. </li> </li> </ul>|
|**4**   |Vælg **Indstillinger** for at åbne ruden **Analyse af virtuelle besøg** . Herfra kan du slå rapportering af virtuelle besøg fra eller til for din organisation og tilføje eller fjerne kolonner i tabellen. Hvis du vil se de ønskede oplysninger i tabellen, skal du sørge for at føje kolonnerne til tabellen.|
|**5**   |Du kan eksportere rapporten til en CSV-fil til offlineanalyse. Vælg **Eksportér til Excel**, og vælg derefter **Download** under fanen **Downloads** for at downloade rapporten, når den er klar.|
### <a name="ehr"></a>EHR

Du får vist denne fane, hvis du har en licens, der indeholder Teams EHR-connectoren. Du kan få mere at vide under [Integration i Cerner EHR](ehr-admin-cerner.md) eller [Integration into Epic EHR](ehr-admin-epic.md).

:::image type="content" source="media/virtual-visits-usage-report-ehr.png" alt-text="Skærmbillede af fanen EHR i forbrugsrapporten for virtuelle besøg, der viser nummererede billedforklatter." lightbox="media/virtual-visits-usage-report-ehr.png":::

|Billedforklaring |Beskrivelse  |
|--------|-------------|
|**1**   |Hver rapport har en dato for, hvornår rapporten blev genereret. Rapporterne afspejler normalt en ventetid på 24 til 48 timer fra aktivitetstidspunktet. |
|**2**   |X-aksen er det valgte datointerval for rapporten. Y-aksen er antallet af EHR-aftaler.<br>Peg på prik på en given dato for at se antallet af EHR-aftaler på den pågældende dato.|
|**3**   |Tabellen indeholder detaljerede oplysninger om hver aftale, der fandt sted i løbet af det valgte datointerval. <ul><li>**Starttidspunkt (UTC)** er den dato og det klokkeslæt, hvor både en medarbejder og deltager deltager i mødet, eller hvor den første aktivitet fandt sted i mødet.  </li> <li>**Møde-id'et** er det entydige id for mødet.</li> <li>**Ventetid for lobby** er tiden mellem, hvor en deltager første gang tilmelder sig lobbyen, til den samme deltager eller en anden deltager får adgang til mødet af en medarbejder.</li><li>**Varighed** er tidsforskellen mellem starttidspunktet, og hvornår den sidste person forlader mødet. Hvis både en medarbejder og en deltager ikke deltog i mødet, vises varigheden som 0 (nul).</li> <li>**Status** viser mødestatussen. <ul><li>**Fuldført**: Hvis en eller flere medarbejdere og deltagere deltager i mødet, og mødet er afsluttet. Eller hvis en eller flere deltagere deltager i mødet, og mødet er afsluttet.</li> <li> **Ingen visning**: Hvis en medarbejder deltager i mødet, men ingen andre deltager, og mødet er afsluttet. </li></ul> </li> <li>**Mødetype** angiver, om den virtuelle aftale blev planlagt via Appen Bookings eller Teams EHR-connectoren.</li> <li>**Deltagere** er det samlede antal medarbejdere og deltagere i mødet.</li> <li>**SMS sendt** angiver, om der blev sendt en sms-meddelelse til deltagerne. </li> </li> </ul>|
|**4**   |Vælg **Indstillinger** for at åbne ruden **Analyse af virtuelle besøg** . Herfra kan du slå rapportering af virtuelle besøg fra eller til for din organisation og tilføje eller fjerne kolonner i tabellen. Hvis du vil se de ønskede oplysninger i tabellen, skal du sørge for at føje kolonnerne til tabellen.|
|**5**   |Du kan eksportere rapporten til en CSV-fil til offlineanalyse. Vælg **Eksportér til Excel**, og vælg derefter **Download** under fanen **Downloads** for at downloade rapporten, når den er klar.|

> [!NOTE]
> Hvis din organisation gerne vil deltage i en privat prøveversion, så brugere, der ikke er administratorer, f.eks. beslutningstagere i virksomheden, kan få adgang til og få vist denne rapport, skal [du kontakte os](mailto:tapmwtanalytics@microsoft.com).

## <a name="related-articles"></a>Relaterede artikler

- [Virtuelle aftaler med Teams og Bookings-appen](bookings-virtual-visits.md)
- [Virtuelle aftaler med Teams – integration i Epic EHR](ehr-admin-epic.md)
- [Virtuelle aftaler med Teams – integration i Cerner EHR](ehr-admin-cerner.md)
