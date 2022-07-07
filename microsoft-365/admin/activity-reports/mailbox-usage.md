---
title: rapporter over brug af Microsoft 365 Administration postkasse
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: beffbe01-ce2d-4614-9ae5-7898868e2729
description: Få mere at vide om, hvordan du får rapporten postkasseforbrug for at få mere at vide om aktivitetsniveauer for brugere med en brugerpostkasse samt oplysninger om lager og kvoter for hver enkelt.
ms.openlocfilehash: c30cb6e9cc593aba14902d81904f3e765faa4231
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66663036"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Microsoft 365-rapporter i Administration – Brug af postkasse

**Forbrugsrapporten for postkassen** indeholder oplysninger om brugere med en brugerpostkasse og aktivitetsniveauet for hver baseret på afsendelse, læsning, oprettelse af aftale, send møde, acceptér møde, afvis møde og annuller mødeaktivitet. Den indeholder også oplysninger om, hvor meget lagerplads der er blevet forbrugt af hver brugerpostkasse, og hvor mange af dem der nærmer sig lagerkvoter. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Sådan kommer du til rapporten over postkassens forbrug

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. På rullelisten **Mailaktivitet** skal du vælge **Brug af Exchange-postkasse**\>.

## <a name="interpret-the-mailbox-usage-report"></a>Fortolkning af rapporten over postkasseforbrug

Du kan få vist din organisations **brug af postkasser** ved at se på diagrammerne **Postkasse**, **Lager** og **Kvote** .
  
:::image type="content" alt-text="Rapport over postkasseforbrug." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

Rapporten **postkasseforbrug** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret). Dataene i hver rapport dækker normalt op til de sidste 24 til 48 timer.

Diagrammet **Postkasse** viser det samlede antal brugerpostkasser i din organisation og det samlede antal aktive på en given dag i rapporteringsperioden. En brugerpostkasse anses for at være aktiv, hvis den har sendt, læst, oprettet en aftale, sendt møde, accepteret møde, afvis møde og annulleret mødeaktivitet.

Diagrammet **Lager** viser mængden af lagerplads, der bruges i din organisation. Lagerdiagrammet indeholder ikke arkivpostkasser. Du kan få flere oplysninger om automatisk udvidelse af arkivering under [Oversigt over automatisk udvidelse af arkivering i Microsoft 365](../../compliance/autoexpanding-archiving.md).

I **kvotediagrammet** kan du se antallet af brugerpostkasser i hver kvotakategori. Der er fire kvotakategorier: 
- Godt: Antallet af brugere, hvis lager bruges, er under kvoten for "problemadvarsel".
- Advarsel! Antallet af brugere, hvis lager er brugt, er på eller over kvoten for "problemadvarsel", men under kvoten "forbyd afsendelse".
- Kan ikke sende: Antallet af brugere, hvis lager er brugt, er på eller over kvoten for forbyd afsendelse, men under forbyd send/modtag-kvoten.
- Kan ikke sende/modtage: Antallet af brugere, hvis lager bruges, ligger på eller over kvoten "Forbyd send/modtag".

I diagrammet Postkasse er Y-aksen antallet af brugerpostkasser. 

I diagrammet Lager er Y-aksen den mængde lagerplads, der bruges af brugerpostkasser i din organisation.

X-aksen i diagrammerne Postkasse og Lager er det valgte datointerval for denne specifikke rapport.

I kvotediagrammet er Y-aksen antallet af brugerpostkasser i hver lagerkvote. Og X-aksen er kvotekategorien.

Du kan filtrere diagrammer, du kan se, ved at vælge et element i forklaringen.

I tabellen kan du se en oversigt over brugen af postkasser på brugerniveau. Du kan føje flere kolonner til tabellen. 

|Element|Beskrivelse|
|:-----|:-----|
|Brugernavn |Brugerens mailadresse. |
|Vist navn  |Brugerens fulde navn. |
|Slettet |Den postkasse, hvis aktuelle tilstand er slettet, men som var aktiv i en del af rapportens rapporteringsperiode.|
|Slettet dato |Den dato, hvor postkassen blev slettet. |
|Oprettelsesdato | Den dato, postkassen blev oprettet.  |
|Seneste aktivitetsdato | Den dato, hvor postkassen sidst havde en afsendelses- eller læseaktivitet via mail.   |
|Antal elementer|Det samlede antal elementer i postkassen. |
|Anvendt lager (MB)|Det samlede anvendte lager. |
|Antal slettede elementer|Det samlede antal slettede elementer i postkassen. |
|Størrelse på slettet element (MB)|Den samlede størrelse af alle slettede elementer i postkassen. |
|Problemadvarselskvote (MB)|Lagergrænsen, når ejeren af postkassen modtager en advarsel om, at den er ved at overskride lagerkvoten.  |
|Forbyd afsendelseskvote (MB)|Lagergrænsen, når postkassen ikke længere kan sende mails. |
|Forbyd modtagelseskvote for afsendelse (MB)|Lagergrænsen, når postkassen ikke længere kan sende eller modtage mails. |
|Kvote for gendanbart element (MB)|Lagergrænsen for genoprettelige (slettede) elementer i postkassen, når postkassen ikke længere kan slette mails. |
|Har arkiv|Viser, om postkassen har et onlinearkiv aktiveret. |


Hvis organisationens politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Se afsnittet **Skjul brugeroplysninger i sektionen Rapporter** i [Aktivitetsrapporter i Microsoft 365 Administration](activity-reports.md.

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> :::image type="content" alt-text="Rapport over postkasseanvendelse – vælg kolonner." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::

Du kan også eksportere rapportdataene til en Excel-.csv-fil ved at vælge linket **Eksportér** . 