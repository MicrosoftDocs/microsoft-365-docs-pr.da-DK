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
ms.openlocfilehash: d544ffffa36c679a1d86faf4e2106faa74321d24
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467574"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Microsoft 365 rapporter i Administration – Brug af postkasse

**Forbrugsrapporten for postkassen** indeholder oplysninger om brugere med en brugerpostkasse og aktivitetsniveauet for hver baseret på afsendelse, læsning, oprettelse af aftale, send møde, acceptér møde, afvis møde og annuller mødeaktivitet. Den indeholder også oplysninger om, hvor meget lagerplads der er blevet forbrugt af hver brugerpostkasse, og hvor mange af dem der nærmer sig lagerkvoter. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Sådan kommer du til rapporten over postkassens forbrug

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. På rullelisten **Mailaktivitet** skal du vælge **Exchange** \> **Postkasseforbrug**.

## <a name="interpret-the-mailbox-usage-report"></a>Fortolkning af rapporten over postkasseforbrug

Du kan få vist din organisations **brug af postkasser** ved at se diagrammerne **Postkasse**, **Storage** og **Kvote**.
  
:::image type="content" alt-text="Rapport over postkasseforbrug." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

|Element|Beskrivelse|
|:-----|:-----|
|1.  |Rapporten **postkasseforbrug** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret). |
|2.  |Dataene i hver rapport dækker normalt op til de sidste 24 til 48 timer. |
|3.  |Diagrammet Postkasse viser det samlede antal brugerpostkasser i din organisation og det samlede antal aktive på en given dag i rapporteringsperioden. En brugerpostkasse anses for at være aktiv, hvis den har sendt, læst, oprettet en aftale, sendt møde, accepteret møde, afvis møde og annulleret mødeaktivitet. |
|4.  |Diagrammet **Storage** viser mængden af lagerplads, der bruges i din organisation. Storage diagram indeholder ikke arkivpostkasser. Du kan få flere oplysninger om automatisk udvidelse af arkivering under [Oversigt over automatisk udvidelse af arkivering i Microsoft 365](../../compliance/autoexpanding-archiving.md). |
|5.  | I **kvotediagrammet** kan du se antallet af brugerpostkasser i hver kvotakategori. Der er fire kvotakategorier:  <br/>  God – antallet af brugere, hvis lager er brugt, er under kvoten for problemadvarsel.  <br/>  Advarsel ! Antallet af brugere, hvis anvendte lagerplads er ved eller over advarsel om, men under forbyd afsendelseskvote  <br/>  Kan ikke sende – antallet af brugere, hvis lager er brugt, er på eller over kvoten for forbyd afsendelse, men under forbyd send/modtag-kvote  <br/>  Der kan ikke sendes/modtages – antallet af brugere, hvis anvendte lagerplads er på eller over, forbyder afsendelses-/modtagelseskvoten |
|6.  | I diagrammet **Postkasse** er Y-aksen antallet af brugerpostkasser.  <br/>  I diagrammet **Storage** er Y-aksen den mængde lagerplads, der bruges af brugerpostkasser i din organisation.  <br/>  I **kvotediagrammet** er Y-aksen antallet af brugerpostkasser i hver lagerkvote.  <br/>  X-aksen i diagrammerne Postkasse og Storage er det valgte datointerval for denne specifikke rapport.  <br/>  X-aksen i kvotadiagrammerne er kvotakategorien. |
|7.  |Du kan filtrere diagrammer, du kan se, ved at vælge et element i forklaringen. |
|8.  | I tabellen kan du se en oversigt over brugen af postkasser på brugerniveau. Du kan føje flere kolonner til tabellen.  <br/> **Brugernavn** er brugerens mailadresse.  <br/> **Vist navn** er det fulde navn, hvis brugeren.  <br/> **Slettet** henviser til den postkasse, hvis aktuelle tilstand er slettet, men var aktiv i en del af rapportens rapporteringsperiode.  <br/> **Datoen for** sletning er den dato, hvor postkassen blev slettet.  <br/> **Oprettelsesdatoen** er den dato, postkassen blev oprettet.  <br/> **Datoen for seneste aktivitet** refererer til den dato, hvor postkassen havde en afsendelses- eller læseaktivitet via mail.  <br/> **Antallet** af elementer refererer til det samlede antal elementer i postkassen.  <br/> **Storage (MB)** refererer til det samlede anvendte lager.  <br/> **Antal slettede** elementer refererer til det samlede antal slettede elementer i postkassen. <br/> **Størrelsen på slettede elementer (MB)** refererer til den samlede størrelse af alle slettede elementer i postkassen. <br/> **Kvote for problemadvarsel (MB)** refererer til lagergrænsen, når postkasseejeren modtager en advarsel om, at den er ved at overskride lagerkvoten.  <br/> **Forbyd afsendelseskvote (MB)** refererer til lagergrænsen, når postkassen ikke længere kan sende mails.  <br/> **Forbyd afsendelse af modtagelseskvote (MB)** refererer til lagergrænsen, når postkassen ikke længere kan sende eller modtage mails.  <br/> **Kvote for genoprettelige elementer (MB)** refererer til lagergrænsen for gendanbare (slettede) elementer i postkassen, når postkassen ikke længere kan slette mails.  <br/> **Viser Arkiv** , om postkassen har aktiveret et onlinearkiv.  <br/>  Hvis organisationens politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Se afsnittet **Skjul brugeroplysninger i rapportafsnittet** i [Aktivitetsrapporter i Microsoft 365 Administration](activity-reports.md). |
|9.  |Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> :::image type="content" alt-text="Rapport over postkasseanvendelse – vælg kolonner." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::|
|10. |Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. |
|||
