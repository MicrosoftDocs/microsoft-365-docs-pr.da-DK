---
title: Microsoft 365 Administration grupperapporter
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: a27f1a99-3557-4f85-9560-a28e3d822a40
description: Få en Microsoft 365 gruppegrupperapport for at få oplysninger om grupperne og deres aktiviteter.
ms.openlocfilehash: ff3a5fa428bb993dac9a518229744754d106e589
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63602957"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Microsoft 365 Rapporter i Administration – Microsoft 365 grupper

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md). I rapporten Microsoft 365 grupper kan du få indsigt i aktiviteten for grupper i organisationen og se, hvor mange grupper der oprettes og bruges.
  
## <a name="how-to-get-to-the-groups-report"></a>Sådan får du adgang til grupperapporten

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug.

2. Klik på knappen Vis mere på siden Aktive  brugere – Microsoft 365 Apps eller Aktive brugere – Microsoft 365 Services på dashboard-startsiden for at få adgang til siden Office 365 rapport.
  
## <a name="interpret-the-groups-report"></a>Fortolk grupperapporten

Du kan se aktiveringerne i rapporten Office 365 ved at vælge **fanen Grupper-aktivitet**.

:::image type="content" alt-text="Microsoft 365 rapporter – Microsoft Office 365 gruppeaktivitet." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.

:::image type="content" alt-text="Office 365 gruppeaktivitetsrapport – vælg kolonner." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere. 

I **rapporten** Grupper kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).

|Metrisk|Definition|
|:-----|:-----|
|Gruppenavn |Navnet på gruppen. |
|Slettet |Antallet af slettede grupper. Hvis gruppen slettes, men havde aktivitet i rapporteringsperioden, vil det blive vist i gitteret med dette flag angivet til sand. |
|Gruppeejer |Navnet på gruppeejeren. |
|Dato for seneste aktivitet (UTC) |Den seneste dato, hvor en meddelelse blev modtaget af gruppen. - Dette er den seneste dato, hvor en aktivitet skete i en mailsamtale, Yammer eller webstedet. |
|Type |Typen af gruppe. Dette kan være en privat eller offentlig gruppe. |
|Mails modtaget i Exchange |Antallet af meddelelser, der er modtaget af gruppen.|
|Mails i Exchange (i alt) |Det samlede antal elementer i gruppens postkasse. |
|Postkasselager, der bruges til Exchange (MB) |Den lagerplads, der bruges af gruppens postkasse. |
|SharePoint filer (i alt) |Antallet af filer, der er gemt SharePoint gruppewebsteder. |
|SharePoint filer (aktive) |Antallet af filer på SharePoint gruppewebsted, der blev reageret på (vist eller ændret, synkroniseret, delt internt eller eksternt) i løbet af rapporteringsperioden. |
|Samlet webstedslagerplads, der bruges SharePoint (MB) |Mængden af lagerplads i MB brugt i løbet af rapporteringsperioden. |
|Meddelelser i Yammer (opslået) |Antallet af meddelelser, der er opslået i Yammer i løbet af rapporteringsperioden. |
|Meddelelser i Yammer (læst) |Antallet af samtaler, der er læst i Yammer i løbet af rapporteringsperioden. |
|Meddelelser i Yammer (synes godt om) |Antallet af meddelelser, der er blevet syntes godt om Yammer gruppen i løbet af rapporteringsperioden. |
|Medlemmer |Antallet af medlemmer i gruppen. |
|Eksterne medlemmer |Antallet af eksterne brugere i gruppen.|


## <a name="related-content"></a>Relateret indhold

[Microsoft 365 Rapporter i Administration](activity-reports.md) (artikel)\
[Smarte rapporter og indsigt i Security & Compliance Center](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance) (artikel)\
[Microsoft 365 Rapporter i Administration – aktive brugere](../../admin/activity-reports/active-users-ww.md) (artikel)

