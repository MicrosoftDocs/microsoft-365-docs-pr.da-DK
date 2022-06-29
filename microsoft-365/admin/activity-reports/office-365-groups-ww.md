---
title: Microsoft 365 Administration grupperingsrapporter
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
description: Få en Microsoft 365-grupper rapport for at få indsigt i aktiviteterne for grupper i din organisation og se, hvor mange grupper der oprettes og bruges.
ms.openlocfilehash: ec9f544214345de0cacd00580772867bd1e5312d
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486269"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Microsoft 365-rapporter i Administration – Microsoft 365-grupper

Dashboardet Microsoft 365-rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md). I Microsoft 365-grupperapporten kan du få indsigt i aktiviteterne for grupper i din organisation og se, hvor mange grupper der oprettes og bruges.

## <a name="how-to-get-to-the-groups-report"></a>Sådan kommer du til grupperapporten

1. Vælg **Rapporter** i Administration, og vælg derefter **Forbrug**.

2. Klik på knappen **Vis mere** på kortet Aktive brugere – Microsoft 365 Apps eller Aktive brugere – Microsoft 365 Services på startsiden for at få adgang til rapportsiden Office 365.

## <a name="interpret-the-groups-report"></a>Fortolkning af grupperapporten

Du kan få vist aktiveringerne i rapporten Office 365 ved at vælge fanen **Grupper- aktivitet**.

:::image type="content" alt-text="Microsoft 365-rapporter – Microsoft Office 365 gruppers aktivitet." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.

:::image type="content" alt-text="Office 365 grupper aktivitetsrapport – vælg kolonner." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Du kan også eksportere rapportdataene til en Excel-.csv-fil ved at vælge linket **Eksportér** . Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem.

**Grupperapporten** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).

### <a name="groupid-hidden-by-default"></a>GroupID skjult som standard
Når du eksporterer rapportdataene, kan du som standard ikke få vist variablen **GroupID** i den Excel-.csv fil, du downloader. Hvis du vil have vist GroupID-oplysninger og alle andre identificerbare oplysninger i Microsoft 365-forbrugsrapporter, kan du bruge til at vælge at [få vist brugeroplysninger i rapporter](../../admin/activity-reports/activity-reports.md#show-user-details-in-the-reports) via organisationens indstillinger i Microsoft 365 Administration.  Du skal være global administrator for at kunne foretage disse ændringer.

Følgende er definitioner af de målepunkter, der er tilgængelige i rapporttabellen.

|Metriske|Definition|
|:-----|:-----|
|Gruppenavn |Navnet på gruppen. |
|Slettet |Antallet af slettede grupper. Hvis gruppen slettes, men har aktivitet i rapporteringsperioden, vises den i gitteret med dette flag angivet til sand. |
|Gruppeejer |Navnet på gruppeejeren. |
|Seneste aktivitetsdato (UTC) |Den seneste dato, hvor en meddelelse blev modtaget af gruppen. - Dette er den seneste dato, hvor en aktivitet fandt sted i en mailsamtale, Yammer eller webstedet. |
|Type |Typen af gruppe. Dette kan være en privat eller offentlig gruppe. |
|Mails modtaget i Exchange |Antallet af meddelelser, der er modtaget af gruppen.|
|Mails i Exchange (i alt) |Det samlede antal elementer i gruppens postkasse. |
|Postkasselager, der bruges til Exchange (MB) |Det lager, der bruges af gruppens postkasse. |
|SharePoint-filer (i alt) |Antallet af filer, der er gemt på SharePoint-gruppewebsteder. |
|SharePoint-filer (aktive) |Antallet af filer på SharePoint-gruppewebstedet, der blev handlet på (vist eller ændret, synkroniseret, delt internt eller eksternt) i rapporteringsperioden. |
|Samlet webstedslager, der bruges til SharePoint (MB) |Den lagermængde i MB, der bruges i rapporteringsperioden. |
|Meddelelser i Yammer (sendt) |Antallet af meddelelser, der er sendt i Yammer-gruppen i løbet af rapporteringsperioden. |
|Meddelelser i Yammer (læs) |Antallet af samtaler, der læses i Yammer-gruppen i løbet af rapporteringsperioden. |
|Meddelelser i Yammer (synes godt om) |Antallet af meddelelser, der synes godt om i Yammer-gruppen i løbet af rapporteringsperioden. |
|Medlemmer |Antallet af medlemmer i gruppen. |
|Eksterne medlemmer |Antallet af eksterne brugere i gruppen.|
|Samlede organiserede møder  |Summen af engangs planlagte og tilbagevendende møder, som en bruger har organiseret i løbet af den angivne tidsperiode.|
|Kanalmeddelelser  |Antallet af entydige meddelelser, som en bruger har slået op i en teamchat i den angivne tidsperiode. Dette omfatter oprindelige indlæg og svar. |

## <a name="related-content"></a>Relateret indhold

[Microsoft 365-rapporter i Administration](activity-reports.md) (artikel)\
[Microsoft 365-rapporter i Administration – Aktive brugere](../../admin/activity-reports/active-users-ww.md) (artikel)
