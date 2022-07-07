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
description: Få mere at vide om, hvordan du får en mailaktivitetsrapport og forstår tendenser for brugermails ved hjælp af dashboardet Microsoft 365-rapporter i Microsoft 365 Administration.
ms.openlocfilehash: 2cbea5265976f46be41379843981afb5a5a057de
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66662091"
---
# <a name="microsoft-365-reports-in-the-admin-center---email-activity"></a>Microsoft 365-rapporter i Administration – Mailaktivitet

Dashboardet Microsoft 365-rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).
  
Du kan f.eks. få en overordnet visning af mailtrafik i din organisation fra siden Rapporter, og derefter kan du analysere widgetten Mailaktivitet for at forstå tendenser og oplysninger på brugerniveau om mailaktiviteten i din organisation.

## <a name="how-to-get-to-the-email-activity-report"></a>Sådan kommer du til mailaktivitetsrapporten

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>
2. Vælg **Vis mere** under **Mailaktivitet**. 
3. På rullelisten **Mailaktivitet** skal du vælge **Exchange** \> **Mailaktivitet**.
  
## <a name="interpret-the-email-activity-report"></a>Fortolkning af mailaktivitetsrapporten

Du kan få vist din brugers mailaktivitet ved at se på diagrammerne **Aktivitet** og **Brugere** . 
  
![Mailaktivitetsrapport.](../../media/5eb1d9e9-8106-4843-acb7-c0238c0da816.png)

**Mailaktivitetsrapporten** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret). Dataene i hver rapport dækker normalt op til de sidste 24 til 48 timer.

**Aktivitetsdiagrammet** giver dig mulighed for at forstå tendensen i mængden af mailaktivitet, der foregår i din organisation. Du kan forstå opdelingen af mailsending, maillæsning, modtagne mails, mødeoprettede eller mødeinddelte aktiviteter. 

Diagrammet **Bruger** giver dig mulighed for at forstå tendensen i antallet af entydige brugere, der genererer mailaktiviteterne. Du kan se på tendensen for brugere, der sender mails, læser mails, modtager mail, opretter et møde eller interagerer med møder. 

I aktivitetsdiagrammet er Y-aksen antallet af aktiviteter for den type mail, der er sendt, mail modtaget, mail læst, møde oprettet og møde interageret. 

I aktivitetsdiagrammet Brugere er Y-aksen brugerens udførende aktivitet af den type mail, der er sendt, mail modtaget, læst i mail, møde oprettet eller møde interageret. 

X-aksen i begge diagrammer er det valgte datointerval for denne specifikke rapport. 

Du kan filtrere de serier, du kan se i diagrammet, ved at vælge et element i forklaringen.

 I tabellen kan du se en oversigt over mailaktiviteterne på niveauet pr. bruger. Dette viser alle brugere, der har fået tildelt et Exchange-produkt, og deres mailaktiviteter.

  
|Element|Beskrivelse|
|:-----|:-----|
|Brugernavn  |Brugerens mailadresse. |
|Vist navn |Brugerens fulde navn. |
|Slettet |Refererer til den bruger, hvis aktuelle tilstand er slettet, men var aktiv i en del af rapportens rapporteringsperiode. |
|Slettet dato |Den dato, hvor brugeren blev slettet. |
|Seneste aktivitetsdato  | Det sidste tidspunkt, hvor brugeren udførte en læse- eller send-mailaktivitet. |
|Send handlinger |Det antal gange, en mailsendingshandling blev registreret for brugeren.  |
|Modtag handlinger  |Det antal gange, en handling, der blev modtaget via mail, blev registreret for brugeren. |
|Læsehandlinger |Det antal gange, en handling for læsning af mail blev registreret for brugeren. |
|Mødeindrettede handlinger  |Det antal gange, en handling til afsendelse af en mødeindkaldelse blev registreret for brugeren. |
|Mødehandlinger, der er interageret med |Det antal gange, en mødeindkaldelse accepterer, foreløbig, afviser eller annullerer handling blev registreret for brugeren. |
|Tildelt produkt  |De produkter, der er tildelt denne bruger.  |


Hvis organisationens politikker forhindrer dig i at få vist rapporter, hvor brugeroplysninger kan identificeres, kan du ændre indstillingen for beskyttelse af personlige oplysninger for alle disse rapporter. Tjek afsnittet **Hvordan gør jeg skjule detaljer på brugerniveau?** i [aktivitetsrapporterne i Microsoft 365 Administration](activity-reports.md).

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.  

![Mailaktivitetsrapport – vælg kolonner.](../../media/80ffa0ad-61c5-4a6f-8a1d-5f6730ff7da9.png)

Du kan også eksportere rapportdataene til en Excel-.csv-fil ved at vælge linket **Eksportér** . Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. 
   
> [!NOTE]
> Mailaktivitetsrapporten er kun tilgængelig for postkasser, der er knyttet til brugere, der har licenser.
