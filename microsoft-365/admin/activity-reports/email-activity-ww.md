---
title: Microsoft 365 Administration mailaktivitetsrapporter
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
description: Få mere at vide om, hvordan du får en mailaktivitetsrapport og forstår tendenser for brugermails ved hjælp af dashboardet Microsoft 365 Rapporter i Microsoft 365 Administration.
ms.openlocfilehash: b84d8c3e6e85ab64b1ec70379e7c016374f28e78
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467662"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Microsoft 365 rapporter i Administration – Mailaktivitet

Dashboardet Microsoft 365 Rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).
  
Du kan f.eks. få en overordnet visning af mailtrafik i din organisation fra siden Rapporter, og derefter kan du analysere widgetten Mailaktivitet for at forstå tendenser og oplysninger på brugerniveau om mailaktiviteten i din organisation.

## <a name="how-to-get-to-the-email-activity-report"></a>Sådan kommer du til mailaktivitetsrapporten

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. På rullelisten **Mailaktivitet** skal du vælge **Exchange** \> **Mailaktivitet**.
  
## <a name="interpret-the-email-activity-report"></a>Fortolkning af mailaktivitetsrapporten

Du kan få vist din brugers mailaktivitet ved at se på diagrammerne **Aktivitet** og **Brugere** . 
  
![Mailaktivitetsrapport.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)
  
|Element|Beskrivelse|
|:-----|:-----|
|1.  <br/> |**Mailaktivitetsrapporten** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).  <br/> |
|2.  <br/> |Dataene i hver rapport dækker normalt op til de sidste 24 til 48 timer.  <br/> |
|3.  <br/> |**Aktivitetsdiagrammet** giver dig mulighed for at forstå tendensen i mængden af mailaktivitet, der foregår i din organisation. Du kan forstå opdelingen af mailsending, maillæsning, modtagne mails, mødeoprettede eller mødeinddelte aktiviteter.  <br/> |
|4.  <br/> |Med **brugerdiagrammet** kan du forstå tendensen for mængden af entydige brugere, der genererer mailaktiviteterne. Du kan se på tendensen for brugere, der sender mails, læser mails, modtager mail, opretter et møde eller interagerer med møder.  <br/> |
|5.  <br/> | I **aktivitetsdiagrammet** er Y-aksen antallet af aktiviteter for den type mail, der er sendt, mail modtaget, mail læst, møde oprettet og møde interageret.  <br/>  I aktivitetsdiagrammet **Brugere** er Y-aksen brugerens udførende aktivitet af den type mail, der er sendt, mail modtaget, læst i mail, møde oprettet eller møde interageret.  <br/>  X-aksen i begge diagrammer er det valgte datointerval for denne specifikke rapport.  <br/> |
|6.  <br/> |Du kan filtrere de serier, du kan se i diagrammet, ved at vælge et element i forklaringen.  <br/> |
|7.  <br/> | I tabellen kan du se en oversigt over mailaktiviteterne på niveauet pr. bruger. Dette viser alle brugere, der har fået tildelt et Exchange produkt, og deres mailaktiviteter. <br/> <br/> **Brugernavn** er brugerens mailadresse.  <br/> **Vist navn** er det fulde navn, hvis brugeren.  <br/> **Slettet** henviser til den bruger, hvis aktuelle tilstand er slettet, men var aktiv i en del af rapportens rapporteringsperiode.  <br/> **Slettet dato** er den dato, hvor brugeren blev slettet.  <br/> **Datoen for seneste aktivitet** refererer til det sidste tidspunkt, hvor brugeren udførte en læse- eller send-mailaktivitet.  <br/> **Send-handlinger** er det antal gange, en mailsendingshandling blev registreret for brugeren.  <br/> **Modtagelseshandlinger** er det antal gange, en mail modtaget handling blev registreret for brugeren.  <br/> **Læsehandlinger** er det antal gange, en handling for læsning af mail blev registreret for brugeren.  <br/> **Mødeoprettede handlinger** er det antal gange, en handling til afsendelse af en mødeindkaldelse blev registreret for brugeren.  <br/> **Mødehandlinger** er det antal gange, en mødeindkaldelse accepterer, foreløbig, afviser eller annullerer handling blev registreret for brugeren.  <br/> **Tildelt produkt** er de produkter, der er tildelt til denne bruger.  <br/>  Hvis organisationens politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Tjek afsnittet **Hvordan gør jeg skjule detaljer på brugerniveau?** i [aktivitetsrapporterne i Microsoft 365 Administration](activity-reports.md).  <br/> |
|8.  <br/> |Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  <br/> ![Mailaktivitetsrapport – vælg kolonner.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)|
|9.  <br/> |Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem.  <br/> |
|||
   
> [!NOTE]
> Mailaktivitetsrapporten er kun tilgængelig for postkasser, der er knyttet til brugere, der har licenser.
