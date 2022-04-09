---
title: Microsoft 365 Administration browserforbrugsrapporter
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
description: Få mere at vide om, hvordan du får en brugsrapport for Microsoft-browseren ved hjælp af dashboardet Microsoft 365 Rapporter i Microsoft 365 Administration.
ms.openlocfilehash: 32f834874e17376bc1b6fb2188c36f2959f504bf
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738225"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-browser-usage"></a>Microsoft 365 rapporter i Administration – Brug af Microsoft-browser

Dashboardet Microsoft 365 rapporter viser dig en aktivitetsoversigt på tværs af produkterne i din organisation. Det giver dig mulighed for at analysere individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert enkelt produkt. Se [emnet Oversigt over rapporter](activity-reports.md). I brugsrapporten for Microsoft-browseren kan du få indsigt i Internet Explorer, Den ældre version af Microsoft Edge og nye Microsoft Edge brug. Anvendelsesrapportering er baseret på Microsoft 365 onlinetjenester adgang til ved hjælp af en Microsoft-browser.

## <a name="how-to-get-to-the-microsoft-browser-usage-report"></a>Sådan kommer du til Brugsrapport for Microsoft-browseren

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<b><a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a></b>

2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på brugskortet for Microsoft-browseren.

## <a name="how-to-notify-users-to-upgrade-their-browser"></a>Sådan giver du brugerne besked om at opgradere deres browser

:::image type="content" alt-text="Handlingsflow for Brugsrapport for Microsoft-browser." source="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png" lightbox="../../media/1ef4eb08-18b8-4dda-aa15-1aad013ecd70.png":::

Globale administratorer kan vælge at sende meddelelser til brugere, der tilgår Microsoft 365-tjenester fra Internet Explorer (som en påmindelse udgår Internet Explorer-skrivebordsprogrammet den 15. juni 2022). Denne målrettede meddelelse giver brugerne besked om, at support til disse browsere snart ophører, og links til en supportartikel med oplysninger om Microsoft Edge og enkle trin, der skal følges for at skifte browsere. 

Du kan finde denne funktion på siden Med Brugsrapport for Microsoft-browser, hvis din organisation har Internet Explorer-forbrug vist i rapporten (der kræves globale administratortilladelser). Når meddelelsen er oprettet, får brugerne besked med den hyppighed, der er angivet indtil den 15. juni 2022. Du kan når som helst slå denne funktion til eller fra.

Dette er en tidsbegrænset funktion, der i øjeblikket kun er tilgængelig for globale administratorer i USA og tillader brugermeddelelser i Excel online.

## <a name="interpret-the-microsoft-browser-usage-report"></a>Fortolkning af Brugsrapport for Microsoft-browser

:::image type="content" alt-text="Anvendelsesrapport for Microsoft-browser." source="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png" lightbox="../../media/95557c88-24ee-417d-a828-96ba00b17aaf.png":::

|Element|Beskrivelse|
|:-----|:-----|
|1. |**Brugsrapporten for Microsoft-browseren** kan ses for tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. |
|2. |Dataene i hver rapport dækker normalt op til de seneste syv dage. |
|3. |Diagrammet **Daglige aktive brugere** viser det daglige antal brugere for Microsoft Edge, Den ældre version af Microsoft Edge og Internet Explorer, når de bruges til at få adgang til Microsoft 365 tjenester. |
|4. |Diagrammet **Aktive brugere** viser det samlede antal brugere, der bruger Microsoft Edge, Den ældre version af Microsoft Edge og Internet Explorer, når de bruges til at få adgang til Microsoft 365 tjenester i den valgte tidsperiode. |
|5. |I tabellen kan du se en opdeling af data på niveauet pr. bruger. Du kan tilføje eller fjerne kolonner fra tabellen. <br/><br/>**Brugernavn** er mailadressen på den bruger, der har oprettet forbindelse til Microsoft 365 tjenester ved hjælp af Microsoft-browsere.<br><br/>**Bruges Microsoft Edge** viser et aksemærke, hvis brugeren brugte Microsoft Edge til at oprette forbindelse til Microsoft 365 tjenester.<br/><br/>**Bruges Den ældre version af Microsoft Edge** viser et aksemærke, hvis brugeren brugte Den ældre version af Microsoft Edge til at oprette forbindelse til Microsoft 365 tjenester.<br/><br/>**I Internet Explorer** vises et aksemærke, hvis brugeren har brugt Internet Explorer til at oprette forbindelse til Microsoft 365 tjenester. |
|6. |Vælg ikonet **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.|
|7. |Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel aggregering, sortering og filtrering for yderligere analyse. Hvis du har færre end 100 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 100 brugere, skal du eksportere dataene for at filtrere og sortere.|
