---
title: Microsoft 365 Administration rapporter over brug af browsere
ms.author: waxiaoyu
author: sarahwxy
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: Få mere at vide om, hvordan du får en rapport over brug af Microsoft-Microsoft 365 i dashboardet Rapporter Microsoft 365 Administration.
ms.openlocfilehash: cfeed7f311816e72d06f63e36aabe9f6ffad718f
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63590508"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-browser-usage"></a>Microsoft 365 Rapporter i Administration – brug af Microsoft-browser

Dashboardet Microsoft 365 Rapporter viser dig en aktivitetsoversigt på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md). I rapporten Om brug af Microsoft-browser kan du få indsigt i Internet Explorer, Den ældre version af Microsoft Edge og ny Microsoft Edge brug. Brugsrapportering er baseret på Microsoft 365 onlinetjenester, der åbnes via en Microsoft-browser.

## <a name="how-to-get-to-the-microsoft-browser-usage-report"></a>Sådan får du Rapporten over brug af Microsoft-browser

1. I Administration skal du gå til **siden Rapporter** \> <b><a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a></b> brug.

2. På dashboard-startsiden skal du klikke på **knappen Vis mere** på Microsoft-browserbrugskortet.

## <a name="how-to-notify-users-to-upgrade-their-browser"></a>Sådan giver du brugerne besked om, at de skal opgradere deres browser

:::image type="content" alt-text="Handlingsflow i Microsoft-browserbrugsrapport." source="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png" lightbox="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png":::

Globale administratorer kan tilmelde sig afsendelse af meddelelser til brugere, der har adgang til Microsoft 365-tjenester fra Internet Explorer (som en påmindelse, vil Internet Explorer-programmet på computeren udgå d. 15. juni 2022). Denne målrettede meddelelse giver brugere besked om, at understøttelse af disse browsere snart sender links til en supportartikel med oplysninger om Microsoft Edge og enkle trin til at skifte browsere. 

Du kan finde denne funktion på siden Rapport over brug af Microsoft-browser, hvis din organisation har Internet Explorer-brug vist i rapporten (globale administratortilladelser er nødvendige). Når meddelelsen er oprettet, får brugerne besked med den hyppighed, der er angivet indtil 15. juni 2022. Du kan når som helst slå denne funktion til eller fra.

Dette er en tidsbegrænset funktion, der i øjeblikket kun er tilgængelig for globale administratorer i USA og tillader brugerbeskeder i Excel online.

## <a name="interpret-the-microsoft-browser-usage-report"></a>Fortolk rapporten over brug af Microsoft-browser

:::image type="content" alt-text="Anvendelsesrapport om Microsoft-browser." source="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png" lightbox="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png":::

|Element|Beskrivelse|
|:-----|:-----|
|1. |I **rapporten Brug af Microsoft-browser** kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. |
|2. |Dataene i hver rapport dækker normalt op til de seneste syv dage. |
|3. |Diagrammet **Daglige aktive brugere viser** den daglige brugertælling for Microsoft Edge, Den ældre version af Microsoft Edge Og Internet Explorer, når de bruges til at få adgang til Microsoft 365 tjenester. |
|4. |Diagrammet **Aktive brugere** viser dig det samlede antal brugere, der bruger Microsoft Edge, Den ældre version af Microsoft Edge og Internet Explorer, når de bruges til at få adgang til Microsoft 365-tjenester i den valgte tidsperiode. |
|5. |Tabellen viser dig en oversigt over dataene pr. bruger. Du kan tilføje eller fjerne kolonner fra tabellen. <br/><br/>**Brugernavn** er mailadressen på den bruger, der har oprettet forbindelse til Microsoft 365 tjenester ved hjælp af Microsoft-browsere.<br><br/>**Used Microsoft Edge** viser et flueben, hvis brugeren har brugt Microsoft Edge at oprette forbindelse til Microsoft 365 tjenester.<br/><br/>**Used Den ældre version af Microsoft Edge** viser et flueben, hvis brugeren har brugt Den ældre version af Microsoft Edge at oprette forbindelse til Microsoft 365 tjenester.<br/><br/>**Anvendt Internet Explorer viser** et flueben, hvis brugeren har brugt Internet Explorer til at oprette forbindelse Microsoft 365 tjenester. |
|6. |Vælg ikonet **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.|
|7. |Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel akkumulering, sortering og filtrering til yderligere analyse. Hvis der er mindre end 100 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 100 brugere, skal du eksportere dataene, før du kan filtrere og sortere.|
