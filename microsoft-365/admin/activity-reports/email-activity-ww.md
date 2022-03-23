---
title: Microsoft 365 Administration af mailaktivitetsrapporter
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
ms.assetid: 1cbe2c00-ca65-4fb9-9663-1bbfa58ebe44
description: Få mere at vide om, hvordan du får en mailaktivitetsrapport Microsoft 365 dashboardet Rapporter i Microsoft 365 Administration.
ms.openlocfilehash: e7441bc24661f279a43a655d17ef23047ed48a43
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591946"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Microsoft 365 Rapporter i Administration – mailaktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i organisationen. Det gør det muligt at analysere i individuelle rapporter om produktniveau, så du kan få mere detaljeret indsigt i aktiviteterne inden for hvert produkt. Se [emnet Rapportoversigt](activity-reports.md).
  
Du kan f.eks. få en visning af mailtrafik på højt niveau i din organisation fra siden Rapporter, og du kan derefter dykke ned i widget'en Mailaktivitet for at forstå tendenser og niveaudetaljer pr. bruger om mailaktivitet i organisationen.

## <a name="how-to-get-to-the-email-activity-report"></a>Sådan får du rapporten over mailaktivitet

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug.
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. Vælg **Mailaktivitet på** rullelisten **Mailaktivitet Exchange** \> **Mailaktivitet**.
  
## <a name="interpret-the-email-activity-report"></a>Fortolk mailaktivitetsrapporten

Du kan få et indblik i dine brugeres mailaktivitet ved at se på **diagrammerne Aktivitet** **og** Brugere. 
  
![Rapport over mailaktivitet.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)
  
|Element|Beskrivelse|
|:-----|:-----|
|1.  <br/> |I **rapporten Mailaktivitet** kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).  <br/> |
|2.  <br/> |Dataene i hver rapport dækker normalt op til de seneste 24 til 48 timer.  <br/> |
|3.  <br/> |Diagrammet **Aktivitet** gør det muligt at forstå tendensen for mængden af mailaktivitet i organisationen. Du kan forstå opdelingen af sendt mail, læst mail, modtaget mail, oprettet møde eller interagerende aktiviteter for møder.  <br/> |
|4.  <br/> |Diagrammet **Bruger** gør det muligt at forstå tendensen for mængden af de unikke brugere, der genererer mailaktiviteter. Du kan se på tendensen for brugere, der udfører mailafsendelse, læsning af mail, modtagelse af mail, oprettelse af møder eller aktiviteter, der interagerer med møder.  <br/> |
|5.  <br/> | I diagrammet **Aktivitet** er Y-aksen antallet af aktiviteter af typen sendt mail, modtaget mail, læst mail, møde oprettet og møde interageret.  <br/>  I **aktivitetsdiagrammet** Brugere er Y-aksen brugerens udførte aktiviteter af typen sendt mail, modtaget mail, læst mail, møde oprettet eller mødeinterageret.  <br/>  X-aksen i begge diagrammer er det valgte datointerval for denne specifikke rapport.  <br/> |
|6.  <br/> |Du kan filtrere de serier, du får vist i diagrammet, ved at vælge et element i forklaringen.  <br/> |
|7.  <br/> | Tabellen viser dig en oversigt over mailaktiviteterne pr. bruger. Dette viser alle brugere, der har Exchange tildelt et produkt, og deres mailaktiviteter. <br/> <br/> **Brugernavn** er brugerens mailadresse.  <br/> **Visningsnavn** er det fulde navn, hvis brugeren.  <br/> **Slettet henviser** til den bruger, hvis aktuelle tilstand er blevet slettet, men som var aktiv under en del af rapporteringsperioden i rapporten.  <br/> **Slettet dato er** den dato, brugeren blev slettet.  <br/> **Dato for seneste** aktivitet refererer til den sidste gang, brugeren udførte mailaktiviteten læst eller sendt.  <br/> **Send handlinger** er antallet af gange, brugeren har registreret en afsendelseshandling for en mail.  <br/> **Modtagelseshandlinger** er det antal gange, brugeren har fået registreret en modtaget mailhandling.  <br/> **Læsehandlinger** er antallet af gange, brugeren har registreret en læsehandling for en mail.  <br/> **Mødeoprettede handlinger** er det antal gange, brugeren har registreret en afsendelseshandling for en mødeindkaldelse.  <br/> **Mødeinagerede** handlinger er det antal gange, brugeren har registreret en handling, der er blevet accepteret, foreløbigt, afvist eller annulleret af mødeindkaldelsen.  <br/> **Tildelt produkt** er de produkter, der er tildelt til denne bruger.  <br/>  Hvis din organisations politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Se sektionen **Hvordan skjuler jeg oplysninger på brugerniveau?** i [aktivitetsrapporter i Microsoft 365 Administration](activity-reports.md).  <br/> |
|8.  <br/> |Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Rapport over mailaktivitet – vælg kolonner.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)|
|9.  <br/> |Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere.  <br/> |
|||
   
> [!NOTE]
> Rapporten Mailaktivitet er kun tilgængelig for postkasser, der er knyttet til brugere, der har licenser.
