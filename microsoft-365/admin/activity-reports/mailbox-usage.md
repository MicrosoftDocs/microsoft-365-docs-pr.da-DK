---
title: Microsoft 365 Administration rapporter over brug af postkasse
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
description: Få mere at vide om, hvordan du får rapporten om postkassebrug for at kende til aktiviteter for brugere med en brugerpostkasse.
ms.openlocfilehash: 6a28b6aed8721872a31af57d4c00cd82a89c06bc
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63599700"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Microsoft 365 Rapporter i Administration – Postkassebrug

Rapporten **Om postkassebrug** indeholder oplysninger om brugere med en brugerpostkasse og aktivitetsniveauet for hver bruger baseret på mailens afsendelse, læsning, oprettelse af aftale, send mødeindkaldelse, acceptér mødeindkaldelse, afvis mødeindkaldelse og annuller mødeindkaldelse. Den indeholder også oplysninger om, hvor meget lagerplads hver brugerpostkasse har brugt, og hvor mange af dem der nærmer sig lagerkvoten. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Sådan får du rapporten over postkassebrug

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug.
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. På **rullelisten Mailaktivitet** skal du **vælge Exchange** \> **postkassebrug**.

## <a name="interpret-the-mailbox-usage-report"></a>Sådan fortolker du rapporten over postkassebrug

Du kan få et indblik i din organisations **postkassebrug** ved at se på **diagrammerne Postkasse**, **Storage** **og Kvote**.
  
:::image type="content" alt-text="Rapport over postkassebrug." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

|Element|Beskrivelse|
|:-----|:-----|
|1.  |I **rapporten Brug** af postkasse kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet). |
|2.  |Dataene i hver rapport dækker normalt op til de seneste 24 til 48 timer. |
|3.  |Postkassediagrammet viser dig det samlede antal brugerpostkasser i organisationen og det samlede antal, der er aktive på en bestemt dag i rapporteringsperioden. En brugerpostkasse betragtes som aktiv, hvis der var en af disse aktiviteter: send mail, læs mail, opret aftale, send mødeindkaldelse, acceptér mødeindkaldelse, afvis mødeindkaldelse og annuller mødeindkaldelse. |
|4.  |I **Storage** vises mængden af anvendt lagerplads i organisationen. Storage Diagram inkluderer ikke arkivpostkasser. Du kan finde flere oplysninger om automatisk udvidende arkivering i Oversigt over automatisk [udvidende arkivering i Microsoft 365](../../compliance/autoexpanding-archiving.md). |
|5.  | Diagrammet **Kvote** viser antallet af brugerpostkasser i hver kvotekategori. Der er fire kvotekategorier:  <br/>  God – antallet af brugere, hvis lagerkvote er under kvoten for advarsler.  <br/>  Advarsel – antallet af brugere, hvis lagerbrug er på eller over udstedelsesmeddelelsen, men under kvoten for forbyd afsendelse  <br/>  Kan ikke sende – antallet af brugere, hvis lagerkvote er på eller over kvoten for forbyd afsendelse, men under kvoten for forbyd send/modtag  <br/>  Kan ikke sende/modtage – antallet af brugere, hvis lagerkvote er på eller over kvoten for forbyd send/modtag |
|6.  | I diagrammet **Postkasse** er Y-aksen antallet af brugerpostkasser.  <br/>  I **Storage er** Y-aksen mængden af lagerplads, der bruges af brugerpostkasser i organisationen.  <br/>  I diagrammet **Kvote** er Y-aksen antallet af brugerpostkasser i hver lagerkvote.  <br/>  X-aksen i postkasse- og Storage er det valgte datointerval for denne specifikke rapport.  <br/>  X-aksen i diagrammerne for Kvote er kvotekategorien. |
|7.  |Du kan filtrere de diagrammer, du får vist, ved at vælge et element i forklaringen. |
|8.  | Tabellen viser dig en oversigt over postkassebrug på pr. bruger-niveau. Du kan tilføje flere kolonner i tabellen.  <br/> **Brugernavn** er brugerens mailadresse.  <br/> **Visningsnavn** er det fulde navn, hvis brugeren.  <br/> **Slettet henviser** til den postkasse, hvis aktuelle tilstand er blevet slettet, men som var aktiv under en del af rapporteringsperioden i rapporten.  <br/> **Slettet dato er** den dato, postkassen blev slettet.  <br/> **Oprettelsesdato** er den dato, postkassen blev oprettet.  <br/> **Dato for seneste aktivitet** refererer til den dato, postkassen havde send- eller læseaktivitet for mail.  <br/> **Elementantal** refererer til det samlede antal elementer i postkassen.  <br/> **Storage (MB) er den** samlede anvendte lagerplads.  <br/> **Slettet antal elementer** henviser til det samlede antal slettede elementer i postkassen. <br/> **Slettet elementstørrelse (MB) er** den samlede størrelse af alle slettede elementer i postkassen. <br/> **Udstedelse af advarselskvote (MB)** er lagergrænsen, hvor postkasseejeren modtager en advarsel om, at lagerkvoten er ved at blive overskredet.  <br/> **Forbyd afsendelse-kvote (MB)** er lagergrænsen, hvor postkassen ikke længere kan sende mails.  <br/> **Forbyd afsendelse/modtagelse-kvote (MB)** er lagergrænsen, hvor postkassen ikke længere kan sende eller modtage mails.  <br/> **Kvoten for genoprettelige elementer (MB)** er lagergrænsen for genoprettelige (slettede) elementer i postkassen, når postkassen ikke længere kan slette mails.  <br/> **Har Arkiv viser** , om postkassen har et onlinearkiv aktiveret.  <br/>  Hvis din organisations politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Se sektionen **Skjul brugeroplysninger i rapporter** i [aktivitetsrapporter i Microsoft 365 Administration](activity-reports.md). |
|9.  |Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> :::image type="content" alt-text="Rapport over postkassebrug – vælg kolonner." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::|
|10. |Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. |
|||
