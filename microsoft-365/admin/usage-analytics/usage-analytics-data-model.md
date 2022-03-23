---
title: Microsoft 365 datamodel for forbrugsanalyse
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 08c5307c-4a6b-4761-8410-a6c96725760f
description: 'Få mere at vide om, hvordan forbrugsanalyse opretter forbindelse til en API og leverer månedlig forbrugstendens for Microsoft 365 tjenester.  '
ms.openlocfilehash: 013fdd75063ad8ad2489ebe43c9091f05f94c14c
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63588116"
---
# <a name="microsoft-365-usage-analytics-data-model"></a>Microsoft 365 datamodel for forbrugsanalyse

## <a name="data-for-the-microsoft-365-usage-analytics-tables"></a>Data til Microsoft 365 til forbrugsanalysetabeller

Microsoft 365 brugerstatistik opretter forbindelse til en API, der viser en flerdimensionel datamodel. De API'er, Microsoft 365 bruger til at generere data fra de forskellige, almindeligt tilgængelige, Graph API'er. Funktionen af API'Microsoft 365 til forbrugsanalyse er ikke generelt tilgængelig.
  
> [!NOTE]
> Få mere at vide under [Arbejde med Microsoft 365 brugsrapporter i Microsoft Graph](/graph/api/resources/report). 
  
Denne API indeholder oplysninger om den månedlige forbrugstendens for de forskellige Microsoft 365 tjenester. For de nøjagtige data, der returneres af API'en, skal du se tabellen i følgende afsnit.
  
## <a name="data-tables-returned-by-the-microsoft-365-reporting-api"></a>Datatabeller, der returneres af Microsoft 365 REPORTING API

|**Tabelnavn**|**Oplysninger i tabellen**|**Datointerval**|
|:-----|:-----|:-----|
|Lejers produktforbrug  <br/> |Indeholder månedlige totaler for aktiverede, aktive brugere, brugere bevaret måned for måned, første gangs brugere og de akkumulerede aktive brugere.  <br/> |Indeholder månedlige samlede data for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers produktaktivitet  <br/> |Indeholder månedlige totaler for aktiviteter og optælling af aktive brugere for forskellige aktiviteter inden for produkterne.  <br/> Se [definition af aktiv bruger](active-user-in-usage-reports.md) for at få oplysninger om aktiviteterne i et produkt, der returneres i denne datatabel.  <br/> |Indeholder månedlige samlede data for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers Office licenser  <br/> |Indeholder data om antallet af Microsoft Office, der er tildelt til brugere  <br/> |Indeholder data for månedsafslutningstilstand for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers brug af postkasse  <br/> |Indeholder data om brugerens postkasse, samlet antal postkasser, og hvordan lagerpladsen bruges.  <br/> |Indeholder data for månedsafslutningstilstand for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers klientforbrug  <br/> |Indeholder data om antallet af brugere, der aktivt bruger bestemte klienter/enheder til at oprette forbindelse til Exchange Online, Skype for Business og Yammer.  <br/> |Indeholder månedlige samlede data for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers SharePoint onlineforbrug  <br/> |Indeholder data om SharePoint-websteder, som omfatter team- eller gruppewebsteder, f.eks. det samlede antal websteder, antal dokumenter på webstedet, filoptælling efter aktivitetstype og anvendt lagerplads.  <br/> |Indeholder data for månedsafslutningstilstand for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers OneDrive for Business brug  <br/> |Indeholder data om OneDrive konti, f.eks. antal konti, antal dokumenter på tværs af OneDrives, brugt lagerplads, filantal efter aktivitetstype.  <br/> |Indeholder data for månedsafslutningstilstand for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers Microsoft 365 gruppeforbrug  <br/> |Indeholder data om Microsoft 365 gruppebrug, herunder postkasse, SharePoint og Yammer.  <br/> |Indeholder data for månedsafslutningstilstand for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejers Office aktivering  <br/> |Indeholder data om antallet af Office-abonnementsaktivering, antallet af aktiveringer pr. enhed (Android/iOS/Mac/pc), aktiveringer efter serviceabonnement, f.eks. Microsoft 365 Apps for enterprise, Visio, Project.  <br/> |Indeholder data for månedsafslutningstilstand for en rullende 12 måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Brugertilstand  <br/> |Indeholder metadata om brugere, herunder brugerens visningsnavn, tildelte produkter, placering, afdeling, stilling, virksomhed. Disse data er om brugere, der blev tildelt en licens i løbet af sidste fuldførte måned. Hver enkelt bruger er entydigt repræsenteret af et bruger-id.  <br/> |Disse data er om brugere, der fik en licens tildelt i løbet af sidste fuldførte måned.  <br/> |
|Brugeraktivitet  <br/> |Indeholder niveauoplysninger pr. bruger om aktivitet, der er udført af licenserede brugere.  <br/> Se [definition af aktiv bruger](active-user-in-usage-reports.md) for at få oplysninger om aktiviteterne i et produkt, der returneres i denne datatabel.  <br/> |Disse data er om brugere, der udførte en aktivitet i en af tjenesterne i løbet af sidste fuldførte måned.  <br/> |
   
Udvid følgende afsnit for at få vist de detaljerede oplysninger for hver datatabel.
  
### <a name="data-table---user-state"></a>Datatabel – Brugertilstand

Denne tabel indeholder oplysninger på brugerniveau for alle brugere, der har fået tildelt en licens i løbet af sidste fuldførte måned. Det henter data fra Azure Active Directory.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|UserId  <br/> |Entydigt bruger-id, der repræsenterer en bruger og gør det muligt at samarbejde med andre datatabeller i datasættet.  <br/> |
|Tidsramme  <br/> |Månedsværdi, som denne tabel indeholder data for.  <br/> |
|UPN  <br/> |Brugerens hovednavn, der entydigt identificerer brugeren, så han/hun kan deltage i forbindelse med andre eksterne datakilder.  <br/> |
|DisplayName  <br/> |Brugerens viste navn.  <br/> |
|IDType  <br/> |Id-type er indstillet til 1, hvis brugeren er en Yammer-bruger, der opretter forbindelse ved hjælp af deres Yammer-id, eller 0, hvis de opretter forbindelse til Yammer ved hjælp af deres Microsoft 365-id.  <br/> Værdi er 1 for at repræsentere, at denne bruger opretter forbindelse Yammer med deres Yammer-id og ikke deres Microsoft 365-id  <br/> |
|HasLicenseEXO  <br/> |Er indstillet til sand, hvis brugeren er tildelt en licens og er Exchange på den sidste dag i måneden.  <br/> |
|HasLicenseODB  <br/> |Er indstillet til sand, hvis brugeren er tildelt en licens og er OneDrive for Business på den sidste dag i måneden.  <br/> |
|HasLicenseSPO  <br/> |Er indstillet til sand, hvis brugeren er tildelt en licens og er aktiveret til SharePoint Online på den sidste dag i måneden.  <br/> |
|HasLicenseYAM  <br/> |Er indstillet til sand, hvis brugeren er tildelt en licens og er Yammer på den sidste dag i måneden.  <br/> |
|HasLicenseSFB  <br/> |Er indstillet til sand, hvis brugeren er tildelt en licens og er aktiveret til Skype for Business på den sidste dag i måneden.  <br/> |
|HasLicenseTeams  <br/> |Er indstillet til sand, hvis brugeren er tildelt en licens og Microsoft Teams den sidste dag i måneden.  <br/> |
|Firma  <br/> |Firmadata repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|Afdeling  <br/> |Afdelingsdata repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|LocationCity  <br/> |Bydata repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|LocationCountry  <br/> |Landedata repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|LocationState  <br/> |Områdedata, der er repræsenteret Azure Active Directory for denne bruger.  <br/> |
|LocationOffice  <br/> |Brugerens kontor.  <br/> |
|Titel  <br/> |Titeldata repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|Slettet  <br/> |Sand, hvis brugeren er blevet slettet fra Microsoft 365 i den sidst fuldførte måned.  <br/> |
|DeletedDate  <br/> |Den dato, hvor brugeren blev slettet Microsoft 365.  <br/> |
|YAM_State  <br/> |Brugerens tilstande i systemet Yammer være aktiv, slettet eller afbrudt.  <br/> |
|YAM_ActivationDate  <br/> |Dato, hvor brugeren indtastede tilstanden som aktiv i Yammer.  <br/> |
|YAM_DeletionDate  <br/> |Dato, hvor brugeren indtastede tilstanden for at blive slettet Yammer.  <br/> |
|YAM_SuspensionDate  <br/> |Dato, hvor brugeren gik i tilstanden som afbrudt Yammer.  <br/> |
   
### <a name="data-table---user-activity"></a>Datatabel – Brugeraktivitet

Denne tabel indeholder data om hver enkelt bruger, der havde en aktivitet i nogen af tjenesterne i den forrige måned.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|UserID  <br/> |Entydigt bruger-id, der repræsenterer en bruger og gør det muligt at samarbejde med andre datatabeller i datasættet.  <br/> |
|IDType  <br/> |Id-type er indstillet til 1, hvis brugeren er en Yammer-bruger, der opretter forbindelse ved hjælp af deres Yammer-id, eller 0, hvis de opretter forbindelse til Yammer ved hjælp af deres Microsoft 365-id.  <br/> Værdi er 1 for at repræsentere, at denne bruger opretter forbindelse Yammer med deres Yammer-id og ikke deres Microsoft 365-id  <br/> |
|Tidsramme  <br/> |Månedsværdi, som denne tabel repræsenterer data for.  <br/> |
|EXO_EmailSent  <br/> |Antal sendte mails.  <br/> |
|EXO_EmailReceived  <br/> |Antal modtagne mails.  <br/> |
|EXO_EmailRead  <br/> |Antal mails med læseaktivitet, som brugeren har udført, det kan være flere gange at læse en allerede læst mail eller en mail, der er modtaget tidligere.  <br/> |
|EXO_AppointmentCreated  <br/> |Antal aftaler, der er oprettet.  <br/> |
|EXO_MeetingAccepted  <br/> |Antal møder, der er blevet accepteret.  <br/> |
|EXO_MeetingCancelled  <br/> |Antal møder, der er blevet annulleret.  <br/> |
|EXO_MeetingDeclined  <br/> |Antal møder, der er blevet afvist.  <br/> |
|EXO_MeetingSent  <br/> |Antal møder, der er sendt.  <br/> |
|ODB_FileViewedModified  <br/> |Antal filer, som denne bruger har interageret med på OneDrive for Business filer (f.eks. oprettet, opdateret, slettet, vist eller downloadet).  <br/> |
|ODB_FileSynched  <br/> |Antal filer, som denne bruger har synkroniseret på OneDrive for Business.  <br/> |
|ODB_FileSharedInternally  <br/> |Antal filer, som denne bruger har delt internt fra OneDrive for Business brugere eller med brugere i grupper (det kan omfatte eksterne brugere).  <br/> |
|ODB_FileSharedExternally  <br/> |Antal filer, som denne bruger har delt eksternt fra OneDrive for Business.  <br/> |
|ODB_AccessedByOwner  <br/> |Antal websteder, som brugeren har interageret med, som findes på egen hånd OneDrive for Business.  <br/> |
|ODB_AccessedByOthers  <br/> |Antal websteder, som denne bruger har interageret med, som findes på en anden OneDrive for Business.  <br/> |
|SPO_GroupFileViewedModified  <br/> |Antal filer, som denne bruger har interageret med på gruppewebsteder.  <br/> |
|SPO_GroupFileSynched  <br/> |Antal filer, som denne bruger har synkroniseret på gruppewebsteder.  <br/> |
|SPO_GroupFileSharedInternally  <br/> |Antallet af filer, der er blevet delt med brugere i organisationen eller med brugere inden for grupper (som kan omfatte eksterne brugere).  <br/> |
|SPO_GroupFileSharedExternally  <br/> |Antal filer, som denne bruger har delt eksternt på gruppewebsteder.  <br/> |
|SPO_GroupAccessedByOwner  <br/> |Antal websteder, som denne bruger har interageret med, som findes på et gruppewebsted, som brugeren ejer.  <br/> |
|SPO_GroupAccessedByOthers  <br/> |Antal websteder, som denne bruger har interageret med, som findes på et gruppewebsted, som en anden bruger ejer.  <br/> |
|SPO_OtherFileViewedModified  <br/> |Antal filer, som denne bruger har interageret med på et andet websted.  <br/> |
|SPO_OtherFileSynched  <br/> |Antal filer, som denne bruger har synkroniseret fra et andet websted.  <br/> |
|SPO_OtherFileSharedInternally  <br/> |Antal filer, som denne bruger har delt internt på et andet websted eller med brugere inden for grupper (det kan omfatte eksterne brugere). <br/> |
|SPO_OtherFileSharedExternally  <br/> |Antal filer, som denne bruger har delt eksternt på et andet websted.  <br/> |
|SPO_OtherAccessedByOwner  <br/> |Antal websteder, som brugeren har interageret med, som findes på et andet websted, som brugeren ejer.  <br/> |
|SPO_OtherAccessedByOthers  <br/> |Antal websteder, som denne bruger har interageret med, som findes på et andet websted, som en anden bruger ejer.  <br/> |
|SPO_TeamFileViewedModified  <br/> |Antal filer, som denne bruger har interageret med på teamwebsteder.  <br/> |
|SPO_TeamFileSynched  <br/> |Antal filer, som denne bruger har synkroniseret fra teamwebsteder.  <br/> |
|SPO_TeamFileSharedInternally  <br/> |Antal filer, som denne bruger har delt internt på teamwebsteder eller med brugere inden for grupper (som kan omfatte eksterne brugere).  <br/> |
|SPO_TeamFileSharedExternally  <br/> |Antal filer, som denne bruger har delt eksternt på teamwebsteder.  <br/> |
|SPO_TeamAccessedByOwner  <br/> |Antal websteder, som denne bruger har interageret med, som findes på et teamwebsted, som brugeren ejer.  <br/> |
|SPO_TeamAccessedByOthers  <br/> |Antal websteder, som denne bruger har interageret med, som findes på et teamwebsted, som en anden bruger ejer.  <br/> |
|Teams_ChatMessages  <br/> |Antal chatmeddelelser, der er sendt.  <br/> |
|Teams_ChannelMessage  <br/> |Antal meddelelser sendt til kanaler.  <br/> |
|Teams_CallParticipate  <br/> |Antal opkald, som brugeren har deltaget i.  <br/> |
|Teams_MeetingParticipate  <br/> |Antal møder, som brugeren har deltaget i.  <br/> |
|Teams_HasOtherAction  <br/> |Boolesk værdi, hvis brugeren udførte andre handlinger i Microsoft Teams.  <br/> |
|YAM_MessagePost  <br/> |Antal meddelelser Yammer, som denne bruger har slået op.  <br/> |
|YAM_MessageLiked  <br/> |Antal meddelelser, Yammer, som denne bruger synes godt om.  <br/> |
|YAM_MessageRead  <br/> |Antal meddelelser Yammer som denne bruger har læst.  <br/> |
|SFB_P2PSummary  <br/> |Antal peer-to-peer-sessioner, som denne bruger deltog i.  <br/> |
|SFB_ConfOrgSummary  <br/> |Antal mødesessioner, som denne bruger organiserede.  <br/> |
|SFB_ConfPartSummary  <br/> |Antal mødesessioner, som denne bruger har deltaget i.  <br/> |

> [!NOTE]
> Teams_HasOtherAction betyder, at brugeren betragtes som aktiv, men har nulværdi for chatmeddelelser, 1:1-opkald, kanalmeddelelser, samlet antal møder og organiserede møder.
   
### <a name="data-table---tenant-product-usage"></a>Datatabel – Lejers produktforbrug

Denne tabel indeholder månedsvis indførelsesdata med hensyn til aktiverede, aktive, returnerende og førstetidsbrugere for hvert produkt inden for Microsoft 365. De Microsoft 365 værdier repræsenterer aktivt forbrug af et af produkterne.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Produkt  <br/> |Navn på produkter, for hvilke brugsoplysninger opsummeres. Microsoft 365 værdi i produktkolonnen repræsenterer aktivitet på tværs af ethvert af produkterne  <br/> |
|Tidsramme  <br/> |Månedsværdi. Der vil være én række pr. produkt pr. måned i de sidste 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|EnabledUsers  <br/> |Antal brugere, der er aktiveret til at bruge produktet til tidsrammeværdien. Hvis en bruger blev aktiveret for en del af måneden, tælles de stadig med.  <br/> |
|ActiveUsers  <br/> |Antal brugere, der udførte en bevidst aktivitet i produktet for tidsrammeværdien.  <br/> En bruger tælles som aktiv for et produkt i en bestemt måned, hvis brugeren har udført en af hovedaktiviteterne i produktet. Hovedaktiviteterne er tilgængelige i tabellen **Lejers produktaktivitet** .  <br/> |
|CumulativeActiveUsers  <br/> |Antal brugere, der er aktiveret til at bruge et produkt og har brugt produktet frem til tidsrammemåneden mindst én gang, siden dataindsamlingen startede i det nye brugssystem.  <br/> |
|MoMReturningUsers  <br/> |Antal brugere, der er aktive i tidsrammemåneden og også var aktive i den forrige måned.  <br/> |
|FirstTimeUsers  <br/> |Antal brugere, der blev aktive i tidsrammen for første gang siden dataindsamling i det nye brugssystem.  <br/> En bruger tælles som en førstetidsbruger i en bestemt måned, hvis vi registrerer deres aktivitet for første gang siden starten af dataindsamlingen i dette nye rapporteringssystem. Når en bruger er talt som en førstetidsbruger, vil denne bruger aldrig blive talt igen som en førstetidsbruger, selvom denne bruger har et stort hul i sin aktivitet.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, vil denne værdi repræsentere den seneste dato i den aktuelle måned, hvor der er tilgængelige data.  <br/> Hvis tidsrammen viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-product-activity"></a>Datatabel – Lejers produktaktivitet

Denne tabel indeholder månedlige totaler for aktivitet og optælling af aktive brugere for forskellige aktiviteter inden for produkterne.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Tidsramme  <br/> |Månedsværdi. Der vil være én række pr. produkt pr. måned i de sidste 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Produkt  <br/> |Navnet på det produkt i Microsoft 365, hvor der er tilgængelige forbrugsdata.  <br/> |
|Aktivitet  <br/> |Navn på aktiviteten i et produkt, der bruges til at fremvise aktivt brug af produktet.  <br/> |
|ActivityCount  <br/> |Dette er det samlede antal handlinger, der tælles for hver aktivitet, der udføres i produktet, på tværs af alle aktive brugere.  <br/> **Bemærk!** For SharePoint Online og OneDrive for Business aktiviteter repræsenterer denne værdi antallet af forskellige dokumenter, som brugere interagerer med.  <br/> |
|ActiveUserCount  <br/> |Antal brugere, der udførte aktiviteten i produktet.  <br/> |
|TotalDurationInMinute  <br/> |Varighed i minutter på tværs af alle aktive brugere, der har brugt lyd- eller videosession i en relevant Skype for Business aktivitet.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, vil denne værdi repræsentere den seneste dato i den aktuelle måned, hvor der er tilgængelige data.  <br/> Hvis tidsrammen viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-mailbox-usage"></a>Datatabel – Lejers brug af postkasse

Denne tabel består af opsummeringsdata på tværs af Exchange Online brugere, der har en brugerpostkasse. Den indeholder månedssluttilstand på tværs af alle brugerpostkasser. Dataene i denne tabel er ikke additive på tværs af flere måneder. Sidste måneds data i denne tabel repræsenterer den seneste tilstand.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|TotalMailboxes  <br/> |Antal brugerpostkasser til Microsoft 365 abonnement.  <br/> |
|IssueWarningQuota  <br/> |Samlet kvote for udstedelse af advarsler på tværs af alle brugeres postkasser.  <br/> |
|ProhibitSendQuota  <br/> |Samlet kvote for forbud mod afsendelse på tværs af alle brugerpostkasser.  <br/> |
|ProhibitSendReceiveQuota  <br/> |Samlet kvote for forbud mod afsendelse og modtagelse på tværs af alle brugerpostkasser.  <br/> |
|TotalItemBytes  <br/> |Mængden af lagerplads, der bruges på tværs af alle brugerpostkasser i byte.  <br/> |
|MailboxesNoWarning  <br/> |Antal brugerpostkasser, der var under lageradvarselsgrænsen.  <br/> |
|MailboxesIssueWarning  <br/> |Antal brugerpostkasser, der fik udstedt en advarsel for lagerkvote.  <br/> |
|MailboxesExceedSendQuota  <br/> |Antal brugerpostkasser, der har overskredet afsendelseskvoten.  <br/> |
|MailboxesExceedSendReceiveQuota  <br/> |Antal brugerpostkasser, der har overskredet send/modtag-kvoten.  <br/> |
|DeletedMailboxes  <br/> |Antal brugerpostkasser, der er blevet slettet i tidsrammen.  <br/> |
|Tidsramme  <br/> |Månedsværdi.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, vil denne værdi repræsentere den seneste dato i den aktuelle måned, hvor der er tilgængelige data.  <br/> Hvis tidsrammen viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-client-usage"></a>Datatabel – Lejers klientforbrug

Denne tabel indeholder månedsoversigtsdata om de klienter, som brugerne bruger til at oprette forbindelse til Exchange Online, Skype for Business og Yammer. Denne tabel har endnu ikke klientbrugsdata for SharePoint Online og OneDrive for Business.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Produkt  <br/> |Navnet på det produkt i Microsoft 365 for hvilke klientforbrugsdata er tilgængelige.  <br/> |
|ClientId  <br/> |Navnet på hver enhed, der bruges til at oprette forbindelse til produktet.  <br/> |
|UserCount  <br/> |Antal brugere, der brugte hver af klienterne for hvert produkt.  <br/> |
|Tidsramme  <br/> |Månedsværdi  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, vil denne værdi repræsentere den seneste dato i den aktuelle måned, hvor der er tilgængelige data.  <br/> Hvis tidsrammen viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-sharepoint-online-usage"></a>Datatabel – Lejers SharePoint onlineforbrug

Denne tabel består af månedsvis opsummeringsdata om brugen eller aktiviteten af SharePoint Online-websteder. Dette omfatter kun teamwebsteder og gruppewebsteder. Tilstanden for slutningen af måneden for SharePoint Online-websteder er repræsenteret i denne kolonne, hvis f.eks. en bruger har oprettet fem dokumenter og har brugt 10 MB til samlet lagerplads og derefter sletter nogle filer og tilføjer flere filer, så tilstanden for filer i slutningen af måneden er syv i alt, der bruger fem MB lagerplads.  værdien af repræsenteret i denne tabel er månedssluttilstand. Denne tabel er skjult for at undgå dublerede sammenlægninger og bruges som kilde til at oprette to referencetabeller.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|SiteType  <br/> |Værdi for webstedstype (alle/team/gruppe) (enhver repræsenterer et af disse 2 webstedstyper).  <br/> |
|TotalSites  <br/> |Antal websteder, der fandtes ved afslutning af tidsrammen.  <br/> |
|DocumentCount  <br/> |Samlet antal dokumenter, der fandtes på webstedet ved afslutning af tidsrammen.  <br/> |
|Diplansed  <br/> |Samlet brugt lagerplads summeret på tværs af alle websteder ved afslutning af tidsrammen.  <br/> |
|ActivityType  <br/> |Antal websteder, der registrerede de forskellige typer filaktivitet (alle/aktive filer/filer delt EKST/INT/filer synkroniseret).  <br/> Repræsenterer enhver af de filaktiviteter, der blev udført.  <br/> |
|SitesWithOwnerActivities  <br/> |Antal aktive websteder, hvor webstedsejeren udførte en bestemt filaktivitet på deres egne websteder. Du kan hente ejeren af webstedet fra **powerShell-kommandoen get-sposite**. Dette er den person, der er ansvarlig for webstedet.   <br/> |
|SitesWithNonOwnerActivities  <br/> |Antal aktive websteder opsummeret for måneden, hvor andre brugere end ejeren af webstedet udførte en bestemt filaktivitet på websteder. Du kan hente ejeren af webstedet fra **powerShell-kommandoen get-sposite**. Dette er den person, der er ansvarlig for webstedet. <br/> |
|ActivityTotalSites  <br/> |Antal websteder, der registrerede nogen aktivitet i løbet af tidsrammen. Hvis et websted havde aktivitet tidligere i tidsrammen og blev slettet ved afslutning af tidsrammen, ville den stadig blive talt med i totalen for aktive websteder for den pågældende tidsramme.  <br/> |
|Tidsramme  <br/> |Denne kolonne indeholder datoværdien. Bruges som mange-til-én-relation til tabellen Kalender.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, vil denne værdi repræsentere den seneste dato i den aktuelle måned, hvor der er tilgængelige data.  <br/> Hvis tidsrammen viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-onedrive-usage"></a>Datatabel – Lejers OneDrive brug

Denne tabel indeholder data om OneDrive-konti, f.eks. antal konti, antal dokumenter på tværs af OneDrive-konti, anvendt lagerplads, filantal efter aktivitetstype. Månedssluttilstanden for OneDrive for Business er repræsenteret i denne tabel. Hvis en bruger f.eks. har oprettet et fem dokumenter, der bruger 10 MB lagerplads, og derefter har slettet nogle få og tilføjet flere filer, så de i slutningen af måneden har syv filer, der bruger fem MB lagerplads, vises værdien for slutningen af måneden i denne tabel i slutningen af måneden.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|SiteType  <br/> |Værdien er "OneDrive".  <br/> |
|TotalSites  <br/> |Antal OneDrive for Business konti, der fandtes ved afslutning af tidsrammen.  <br/> |
|DocumentCount  <br/> |Samlet antal dokumenter, der fandtes på tværs OneDrive for Business alle konti ved afslutning af tidsrammen  <br/> |
|Diplansed  <br/> |Samlet brugt lagerplads summeret på OneDrive én konto ved afslutning af tidsrammen.  <br/> |
|ActivityType  <br/> |Antal konti, der registrerede de forskellige typer filaktivitet (alle/aktive filer/filer delt EKST/INT/filer synkroniseret).  <br/> Enhver angiver enhver af den udførte filaktivitet  <br/> |
|SitesWithOwnerActivities  <br/> |Antal aktive konti OneDrive for Business, hvor kontoejeren udførte en bestemt filaktivitet på sin egen konto.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Antallet af OneDrive for Business, hvor der blev udført filaktivitet af andre brugere end ejeren af kontoen.  <br/> |
|ActivityTotalSites  <br/> |Antal af OneDrive for Business, der registrerede nogen aktivitet i løbet af tidsrammen. Hvis en OneDrive for Business-konto havde aktivitet tidligere i tidsrammen og blev slettet ved afslutning af tidsrammen, ville den stadig blive talt med i den aktive OneDrive for Business-konto for den pågældende tidsramme.  <br/> |
|Tidsramme  <br/> |Denne kolonne indeholder datoværdien. Bruges som mange-til-én-relation til tabellen Kalender.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, vil denne værdi repræsentere den seneste dato i den aktuelle måned, hvor der er tilgængelige data.  <br/> Hvis tidsrammen viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-microsoft-365-groups-usage"></a>Datatabel – Lejers Microsoft 365 brugen af Grupper

Denne tabel indeholder data om, Microsoft 365 grupper bruges på tværs af organisationen.
  
****

|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Tidsramme  <br/> |Månedsværdi. Der vil være én række pr. produkt pr. måned i de sidste 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|GroupType  <br/> |Type af gruppe (privat/offentlig/enhver).  <br/> |
|TotalGroups  <br/> |Antal grupper i hver gruppetype.  <br/> |
|ActiveGroups  <br/> |Antal aktive grupper.  <br/> |
|MBX_TotalGroups  <br/> |Antal postkassegrupper.  <br/> |
|MBX_ActiveGroups  <br/> |Antal aktive postkassegrupper.  <br/> |
|MBX_TotalActivities  <br/> |Antal postkasseaktiviteter.  <br/> |
|MBX_TotalItems  <br/> |Antal postkasseelementer.  <br/> |
|MBX_StorageUsed  <br/> |Brugt lagerplads i postkassen.  <br/> |
|SPO_TotalGroups  <br/> |Antal SharePoint grupper.  <br/> |
|SPO_ActiveGroups  <br/> |Antallet af aktive SharePoint grupper.  <br/> |
|SPO_FileAccessedActiveGroups  <br/> |Antal grupper SharePoint, der har fil åbnet aktiviteter.  <br/> |
|SPO_FileSyncedActiveGroups  <br/> |Antal grupper SharePoint, der har fil synkroniserede aktiviteter.  <br/> |
|SPO_FileSharedInternallyActiveGroups  <br/> |Antal grupper SharePoint, der har delte aktiviteter internt, eller med grupper (som kan omfatte eksterne brugere).  <br/> |
|SPO_FileSharedExternallyActiveGroups  <br/> |Antal SharePoint grupper, der har eksternt delte aktiviteter.  <br/> |
|SPO_TotalActivities  <br/> |Antal SharePoint aktiviteter.  <br/> |
|SPO_FileAccessedActivities  <br/> |Antal SharePoint tilgås.  <br/> |
|SPO_FileSyncedActivities  <br/> |Antal SharePoint fil synkroniserede aktiviteter.  <br/> |
|SPO_FileSharedInternallyActivities  <br/> |Antal filer SharePoint fildelingsaktiviteter internt eller med grupper (som kan omfatte eksterne medlemmer).  <br/> |
|SPO_FileSharedExternallyActivities  <br/> |Antal eksterne SharePoint filer, der deles eksternt.  <br/> |
|SPO_TotalFiles  <br/> |Antal SharePoint filer.  <br/> |
|SPO_ActiveFiles  <br/> |Antal aktive SharePoint filer.  <br/> |
|SPO_StorageUsed  <br/> |Brugt SharePoint lagerplads.  <br/> |
|YAM_TotalGroups  <br/> |Antal Yammer grupper.  <br/> |
|YAM_ActiveGroups  <br/> |Antallet af aktive Yammer grupper.  <br/> |
|YAM_LikedActiveGroups  <br/> |Antal grupper Yammer, der har synes godt om-aktiviteter.  <br/> |
|YAM_PostedActiveGroups  <br/> |Antal grupper Yammer der har opslagsaktiviteter.  <br/> |
|YAM_ReadActiveGroups  <br/> |Antal Yammer der har læseaktiviteter.  <br/> |
|YAM_TotalActivities  <br/> |Antal Yammer aktiviteter.  <br/> |
|YAM_LikedActivities  <br/> |Antal aktiviteter Yammer f.eks.  <br/> |
|YAM_PostedActivties  <br/> |Antallet af Yammer postaktiviteter.  <br/> |
|YAM_ReadActivites  <br/> |Antal Yammer læseaktiviteter.  <br/> |

### <a name="data-table---tenant-office-licenses"></a>Datatabel – Lejers Office-licenser

Denne tabel indeholder månedsoversigtsdata om brugertildelingen af licenser. 
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|LicenseName  <br/> |Navnet på licensen.  <br/> |
|AssignedCount  <br/> |Antal tildelte licenser.  <br/> |
|Tidsramme  <br/> |Månedsværdi.  <br/> |

### <a name="data-table---tenant-office-activation"></a>Datatabel – Lejers Office aktivering

Tabellen indeholder data om antallet af Office-abonnementsaktivering på tværs af serviceabonnementer, f.eks. Microsoft 365 Apps til virksomheder, Visio og Project. Den indeholder også data om antallet af aktiveringer pr. enhed (Android/iOS/Mac/pc).
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|ServicePlanName  <br/> |Liste over værdierne for serviceabonnementsnavn og optælling af aktiveringer fra enheder, som vist i nedenstående kolonner.  <br/> |
|TotalEnabled  <br/> |Antal brugere, der er aktiveret pr. serviceabonnementsnavn ved afslutning af tidsrammen.  <br/> |
|TotalActivatedUsers  <br/> |Antal brugere, der har aktiveret hvert serviceabonnement ved afslutning af tidsrammen.  <br/> |
|AndroidCount  <br/> |Antal aktiveringer pr. serviceabonnement for Android-enhed ved afslutning af tidsrammen.  <br/> |
|iOSCount  <br/> |Antal aktiveringer pr. serviceabonnement for iOS-enhed ved afslutning af tidsrammen.  <br/> |
|MacCount  <br/> |Antal aktiveringer pr. serviceabonnement for MAC-enhed ved afslutning af tidsrammen.  <br/> |
|PcCount  <br/> |Antal aktiveringer pr. serviceabonnement for pc-enhed ved afslutning af tidsrammen.  <br/> |
|WinRtCount  <br/> |Antal aktiveringer pr. serviceabonnement Windows en mobilenhed ved afslutning af tidsrammen.  <br/> |
|Tidsramme  <br/> |Denne kolonne indeholder datoværdien. Bruges som mange-til-én-relation til tabellen Kalender.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, vil denne værdi repræsentere den seneste dato i den aktuelle måned, hvor der er tilgængelige data.  <br/> Hvis tidsrammen viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
