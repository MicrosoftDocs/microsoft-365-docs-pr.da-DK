---
title: Microsoft 365 Administration Teams af brugeraktivitetsrapporter
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
description: Få mere at vide om, Microsoft Teams få rapporten over brugeraktivitet og få indsigt Teams i organisationen.
ms.openlocfilehash: cfb503c09577d4538371ad6a5b35520d8da24bdb
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590294"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-user-activity"></a>Microsoft 365 Rapporter i Administration – Microsoft Teams brugeraktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md). I rapporten Microsoft Teams for brugeraktivitet kan du få indsigt i Microsoft Teams aktivitet i organisationen.
 
## <a name="how-to-get-to-the-microsoft-teams-user-activity-report"></a>Sådan får du rapporten Microsoft Teams brugeraktivitet

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug.
2. Fra dashboardets startside skal du klikke på **knappen Vis** mere på Microsoft Teams aktivitetskort.

## <a name="interpret-the-microsoft-teams-user-activity-report"></a>Fortolk Microsoft Teams for brugeraktivitetsrapporten

Du kan få vist brugeraktiviteten i Teams ved at vælge **fanen Brugeraktivitet**. <br/>![Microsoft 365-rapporter – Microsoft Teams brugeraktivitet.](../../media/1011877f-3cf0-4417-9447-91d0b2312aab.png)

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Teams rapport over brugeraktivitet – vælg kolonner.](../../media/6d3c013e-2c5e-4d66-bb41-998aa4bd1c20.png)

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere. Det eksporterede format for **lydtid**, **videotid og** **skærmsharetid** følger ISO8601-varighedsformatet.

I **Microsoft Teams** for brugeraktivitet kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).

For at sikre datakvaliteten udfører vi daglige datavalideringskontroller for de seneste tre dage og udfylder eventuelle registrerede mellemrum. Du kan måske se forskelle i historiske data under processen.

|Element|Beskrivelse|
|:-----|:-----|
|**Metrisk**|**Definition**|
|Brugernavn  <br/> |Brugerens mailadresse. Du kan få vist den faktiske mailadresse eller gøre dette felt anonymt.   <br/> |
|Kanalmeddelelser   <br/> |Antallet af unikke meddelelser, brugeren har slået op i en teamchat i den angivne periode.  <br/> |
|Chatmeddelelser   <br/> |Antallet af unikke meddelelser, brugeren har sendt i en privat chat i den angivne periode.  <br/> |
|Møder i alt   <br/> |Antallet af onlinemøder, som brugeren har deltaget i i den angivne periode.  <br/> |
|1:1-opkald   <br/> | Antallet af 1:1-opkald, som brugeren har deltaget i i den angivne periode.  <br/> |
|Dato for seneste aktivitet (UTC)  <br/> |Den sidste dato, hvor brugeren deltog i en Microsoft Teams aktivitet.<br/> |
|Ad hoc-møder deltaget i   <br/> | Antallet af ad hoc-møder, en bruger har deltaget i i den angivne periode.  <br/> |
|Møder organiseret ad hoc <br/> |Antallet af ad hoc-møder, som en bruger har organiseret i den angivne periode. <br/>|
|Samlet antal organiserede møder  <br/> |Summen af enkelttids planlagte, tilbagevendende, ad hoc- og ikke-klassificeret møder, som er organiseret af en bruger i den angivne periode.  <br/> |
|Samlet antal møder deltaget i  <br/> |Summen af de enkelttids planlagte, tilbagevendende, ad hoc- og ikke-klassificeret møder, som en bruger har deltaget i i den angivne periode.  <br/> |
|Møder arrangeret én gang  <br/> |Antallet af enkelttids planlagte møder, som en bruger har arrangeret i den angivne periode.  <br/> |
|Møder organiseret planlagt tilbagevendende  <br/> |Antallet af tilbagevendende møder, som en bruger har arrangeret i den angivne periode.  <br/> |
|Møder, hvor der deltog i møder, som blev planlagt én gang  <br/> |Antallet af engangs planlagte møder, som en bruger har deltaget i i den angivne periode.  <br/> |
|Møder, hvor der deltog planlagt tilbagevendende møder  <br/> |Antallet af tilbagevendende møder, som en bruger har deltaget i i den angivne periode.  <br/> |
|Er givet i licens  <br/> |Valgt, hvis brugeren har licens til at bruge Teams. <br/>|
|Anden aktivitet  <br/>|Brugeren er aktiv, men har udført andre aktiviteter end de eksponerede handlingstyper, der tilbydes i rapporten (sende eller svare på kanalmeddelelser og chatmeddelelser, planlægge eller deltage i 1:1-opkald og -møder). Eksempler på handlinger er, når en bruger ændrer status Teams eller statusmeddelelsen Teams eller åbner et kanalmeddelelsesopslag, men ikke svarer.  <br/>|
|Ikke-klassificeret møder <br/>|Den, der ikke kan klassificeres som tidsplan eller tilbagevendende eller ad hoc. Disse er korte og kan som oftest ikke identificeres på grund af ændrede telemetrioplysninger. |
|||
