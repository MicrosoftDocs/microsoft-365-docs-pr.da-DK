---
title: Microsoft 365 Administration Teams brugeraktivitetsrapporter
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Få mere at vide om, hvordan du får Microsoft Teams brugeraktivitetsrapport og får indsigt i Teams-aktiviteten i din organisation.
ms.openlocfilehash: cbd9bdb73dc69da5e36e0fb9c3ff2ff15b5269a4
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882258"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Microsoft 365 rapporter i Administration – Microsoft Teams brugeraktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md). I Microsoft Teams brugeraktivitetsrapport kan du få indsigt i den Microsoft Teams aktivitet i din organisation.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Sådan får du adgang til rapporten over Microsoft Teams brugeraktivitet

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>
2. Klik på knappen **Vis mere** på Microsoft Teams aktivitetskortet på startsiden for dashboardet.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Fortolkning af rapporten over Microsoft Teams brugeraktivitet

Du kan få vist brugeraktiviteten i Teams rapport ved at vælge fanen **Brugeraktivitet**. <br/>![Microsoft 365 rapporter – Microsoft Teams brugeraktivitet.](../../media/user-activity-charts.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Teams brugeraktivitetsrapport – vælg kolonner.](../../media/user-activity-columns.png)

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem. Det eksporterede format for **lydtid**, **videotid** og **skærmdelingstid** følger ISO8601-varighedsformatet.

Den **Microsoft Teams brugeraktivitetsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).

For at sikre datakvaliteten udfører vi daglige datavalideringskontroller i de seneste tre dage og udfylder eventuelle huller, der er registreret. Du kan bemærke forskelle i historiske data under processen.

|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Brugernavn  <br/> |Brugerens mailadresse. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt.   <br/> |
|Lejernavn  <br/> |Navnet på en intern eller ekstern lejer, hvor en bruger tilhører.   <br/> <br/> Hvis en bruger tilhører en ekstern lejer, beregnes tilsvarende datamålepunkter (f.eks. postmeddelelser, svarmeddelelser osv.) på baggrund af deres interaktioner i delte kanaler i administratorens lejer. Interaktioner, der udføres af brugeren i deres egen lejer (uden for delte kanaler for den angivne lejer), tages ikke i betragtning som administratorforbrugsrapport for den angivne lejer.  |
|Lejernavne for delte kanaler   <br/> |Navnene på interne eller eksterne lejere på delte kanaler, hvor brugeren deltog.   <br/> |
|Kanalmeddelelser   <br/> |Antallet af entydige meddelelser, som brugeren har sendt i en teamchat i den angivne tidsperiode.  <br/> |
|Indlæg   <br/> |Antallet af meddelelser i alle kanaler i den angivne tidsperiode <br/> |
|Svar   <br/> |Antallet af besvarede meddelelser i alle kanaler i den angivne tidsperiode. <br/> |
|Vigtige meddelelser    <br/> |Antallet af hastemeddelelser i den angivne tidsperiode. <br/> |
|Chatbeskeder   <br/> |Antallet af entydige meddelelser, som brugeren har sendt i en privat chat i den angivne tidsperiode.  <br/> |
|Møder i alt   <br/> |Antallet af onlinemøder, som brugeren har deltaget i i den angivne tidsperiode.  <br/> |
|1:1 opkald   <br/> | Antallet af 1:1-opkald, som brugeren har deltaget i i den angivne tidsperiode.  <br/> |
|Seneste aktivitetsdato (UTC)  <br/> |Den sidste dato, hvor brugeren deltog i en Microsoft Teams aktivitet.<br/> |
|Møder deltog ad hoc   <br/> | Antallet af ad hoc-møder, som en bruger har deltaget i i den angivne tidsperiode.  <br/> |
|Møder organiseret ad hoc <br/> |Antallet af ad hoc-møder, som en bruger har arrangeret i den angivne tidsperiode. <br/>|
|Samlede organiserede møder  <br/> |Summen af engangs planlagte, tilbagevendende, ad hoc- og ikke-klassificerede møder, som en bruger har organiseret i løbet af den angivne tidsperiode.  <br/> |
|Samlet antal deltagermøder  <br/> |Summen af planlagte, tilbagevendende, ad hoc- og ikke-klassificerede møder, som en bruger har deltaget i i løbet af den angivne tidsperiode.  <br/> |
|Arrangerede møder planlagt én gang  <br/> |Antallet af engangsmøder, som en bruger har organiseret i løbet af den angivne tidsperiode.  <br/> |
|Arrangerede møder, der er planlagt som tilbagevendende  <br/> |Antallet af tilbagevendende møder, som en bruger har organiseret i løbet af den angivne tidsperiode.  <br/> |
|Møder deltog i planlagte engangsmøder  <br/> |Antallet af engangsmøder, som en bruger har deltaget i i løbet af den angivne tidsperiode.  <br/> |
|Møder, der har deltaget i planlagte tilbagevendende møder  <br/> |Antallet af tilbagevendende møder, som en bruger deltog i i den angivne tidsperiode.  <br/> |
|Er licenseret  <br/> |Valgt, hvis brugeren har licens til at bruge Teams. <br/>|
|Anden aktivitet  <br/>|Brugeren er aktiv, men har udført andre aktiviteter end de eksponerede handlingstyper, der tilbydes i rapporten (afsendelse eller svar på kanalmeddelelser og chatbeskeder, planlægning eller deltagelse i 1:1-opkald og -møder). Eksempler på handlinger er, når en bruger ændrer status for Teams eller Teams statusmeddelelse eller åbner et kanalmeddelelsesindlæg, men ikke svarer.  <br/>|


## <a name="make-the-user-specific-data-anonymous"></a>Gør de brugerspecifikke data anonyme

Hvis du vil gøre dataene i Teams brugeraktivitetsrapport anonyme, skal du være global administrator. Dette skjuler identificerbare oplysninger (ved hjælp af MD5-hashen), f.eks. vist navn, mail og Azure Active Directory objekt-id i rapporten og deres eksport.

1. I Microsoft 365 Administration skal du gå til **Indstillinger** >  **Ellerg Indstillinger**, og under fanen **Tjenester** skal du vælge **Rapporter**.

2. Vælg **Rapporter**, og vælg derefter Vis **anonyme id'er**. Denne indstilling anvendes både på forbrugsrapporterne i Microsoft 365 Administration og Teams Administration.

3. Vælg **Gem ændringer**.


## <a name="see-also"></a>Se også
[Microsoft Teams rapport over enhedsforbrug](../activity-reports/microsoft-teams-device-usage-preview.md)

[Microsoft Teams forbrugsaktivitetsrapport](../activity-reports/microsoft-teams-usage-activity.md) 
