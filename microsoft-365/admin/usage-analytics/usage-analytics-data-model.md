---
title: Microsoft 365 model til forbrugsanalyse
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
description: 'Få mere at vide om, hvordan forbrugsanalyse opretter forbindelse til en API og giver en månedlig tendens i brugen af forskellige Microsoft 365 tjenester.  '
ms.openlocfilehash: 05b8a6d9a69cc6347b4d2cdcfbdeaa26bd479cbd
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65620989"
---
# <a name="microsoft-365-usage-analytics-data-model"></a>Microsoft 365 model til forbrugsanalyse

## <a name="data-for-the-microsoft-365-usage-analytics-tables"></a>Data til tabellerne med Microsoft 365 forbrugsanalyse

Microsoft 365 brugeranalyse opretter forbindelse til en API, der viser en flerdimensionel datamodel. De API'er, som Microsoft 365 brugsanalyse bruger til at generere dataene, er fra de forskellige, offentligt tilgængelige Graph API'er. Funktionen af api'en til Microsoft 365 forbrugsanalyse er ikke generelt tilgængelig.
  
> [!NOTE]
> Du kan få flere oplysninger under [Arbejde med Microsoft 365 anvendelsesrapporter i Microsoft Graph](/graph/api/resources/report). 
  
Denne API indeholder oplysninger om den månedlige tendens for brugen af de forskellige Microsoft 365 tjenester. Du kan finde de nøjagtige data, der returneres af API'en, i tabellen i følgende afsnit.
  
## <a name="data-tables-returned-by-the-microsoft-365-reporting-api"></a>Datatabeller, der returneres af API'en til Microsoft 365 rapportering

|**Tabelnavn**|**Oplysninger i tabellen**|**Datointerval**|
|:-----|:-----|:-----|
|Lejerproduktforbrug  <br/> |Indeholder månedlige totaler for aktiverede, aktive brugere, brugere, der bevares måned for måned, førstegangsbrugere og de akkumulerede aktive brugere.  <br/> |Indeholder månedlige aggregerede data for en rullende 12-måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejerproduktaktivitet  <br/> |Indeholder månedlige totaler af aktiviteter og antal aktive brugere for forskellige aktiviteter i produkterne.  <br/> Se [definitionen af den aktive bruger](active-user-in-usage-reports.md) for at få oplysninger om aktiviteterne i et produkt, der returneres i denne datatabel.  <br/> |Indeholder månedlige aggregerede data for en rullende 12-måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejer- Office licenser  <br/> |Indeholder data om antallet af Microsoft Office abonnementer, der er tildelt til brugere  <br/> |Indeholder tilstandsdata for slutningen af måneden for en rullende periode på 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Brug af lejerpostkasse  <br/> |Indeholder data om brugerens postkasse for det samlede antal postkasser, og hvordan lagerplads bruges.  <br/> |Indeholder tilstandsdata for slutningen af måneden for en rullende periode på 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Brug af lejerklient  <br/> |Indeholder data om antallet af brugere, der aktivt bruger bestemte klienter/enheder til at oprette forbindelse til Exchange Online, Skype for Business og Yammer.  <br/> |Indeholder månedlige aggregerede data for en rullende 12-måneders periode, herunder den aktuelle delvise måned.  <br/> |
|Lejer SharePoint onlinebrug  <br/> |Indeholder data om de SharePoint websteder, der dækker Team- eller Grupper-websteder, f.eks. det samlede antal websteder, antallet af dokumenter på webstedet, antallet af filer efter aktivitetstype og anvendt lager.  <br/> |Indeholder tilstandsdata for slutningen af måneden for en rullende periode på 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Lejerforbrug OneDrive for Business  <br/> |Indeholder data om de OneDrive konti, f.eks. antal konti, antal dokumenter på tværs af OneDrives, anvendt lagerplads, filantal efter aktivitetstype.  <br/> |Indeholder tilstandsdata for slutningen af måneden for en rullende periode på 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Lejerforbrug Microsoft 365-grupper  <br/> |Indeholder data om Microsoft 365-grupper brug, herunder Postkasse, SharePoint og Yammer.  <br/> |Indeholder tilstandsdata for slutningen af måneden for en rullende periode på 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Aktivering af lejer Office  <br/> |Indeholder data om antallet af Office abonnementsaktiveringer, antal aktiveringer pr. enhed (Android/iOS/Mac/PC), aktiveringer efter tjenesteplan, f.eks. Microsoft 365 Apps for enterprise, Visio, Project.  <br/> |Indeholder tilstandsdata for slutningen af måneden for en rullende periode på 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Brugertilstand  <br/> |Indeholder metadata om brugere, herunder vist navn på bruger, tildelte produkter, placering, afdeling, titel, firma. Disse data handler om brugere, der har fået tildelt en licens i løbet af den sidste hele måned. Alle brugere repræsenteres entydigt af et bruger-id.  <br/> |Disse data handler om brugere, der har fået tildelt en licens i løbet af den seneste hele måned.  <br/> |
|Brugeraktivitet  <br/> |Indeholder oplysninger på brugerniveau om aktiviteter, der udføres af brugere med licens.  <br/> Se [definitionen af den aktive bruger](active-user-in-usage-reports.md) for at få oplysninger om aktiviteterne i et produkt, der returneres i denne datatabel.  <br/> |Disse data handler om brugere, der udførte en aktivitet i en af tjenesterne i løbet af den sidste hele måned.  <br/> |
   
Udvid følgende afsnit for at få vist detaljerede oplysninger om hver datatabel.
  
### <a name="data-table---user-state"></a>Datatabel – Brugertilstand

Denne tabel indeholder oplysninger på brugerniveau for alle brugere, der har fået tildelt en licens i løbet af den sidste hele måned. Den henter data fra Azure Active Directory.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Userid  <br/> |Entydigt bruger-id, der repræsenterer en bruger og gør det muligt at forbinde med andre datatabeller i datasættet.  <br/> |
|Tidsramme  <br/> |Månedsværdi, som denne tabel indeholder data for.  <br/> |
|UPN  <br/> |Brugerens hovednavn identificerer entydigt brugeren for at kunne joinforbinde med andre eksterne datakilder.  <br/> |
|Displayname  <br/> |Brugerens viste navn.  <br/> |
|IDType  <br/> |Id-typen angives til 1, hvis brugeren er en Yammer bruger, der opretter forbindelse ved hjælp af deres Yammer-id, eller 0, hvis brugeren opretter forbindelse til Yammer ved hjælp af deres Microsoft 365-id.  <br/> Værdien er 1 for at repræsentere, at brugeren opretter forbindelse til Yammer med deres Yammer-id og ikke deres Microsoft 365-id  <br/> |
|HasLicenseEXO  <br/> |Angiv til sand, hvis brugeren har fået tildelt en licens og er aktiveret til at bruge Exchange den sidste dag i måneden.  <br/> |
|HasLicenseODB  <br/> |Angiv til sand, hvis brugeren har fået tildelt en licens og er aktiveret til at bruge OneDrive for Business på den sidste dag i måneden.  <br/> |
|HasLicenseSPO  <br/> |Angiv til sand, hvis brugeren har fået tildelt en licens og er aktiveret til at bruge SharePoint Online den sidste dag i måneden.  <br/> |
|HasLicenseYAM  <br/> |Angiv til sand, hvis brugeren har fået tildelt en licens og er aktiveret til at bruge Yammer den sidste dag i måneden.  <br/> |
|HasLicenseSFB  <br/> |Angiv til sand, hvis brugeren har fået tildelt en licens og er aktiveret til at bruge Skype for Business den sidste dag i måneden.  <br/> |
|HasLicenseTeams  <br/> |Angiv til sand, hvis brugeren har fået tildelt en licens og gør det muligt at bruge Microsoft Teams den sidste dag i måneden.  <br/> |
|Virksomhed  <br/> |Firmadata, der er repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|Institut  <br/> |Afdelingsdata, der er repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|Placering  <br/> |Bydata, der er repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|Antal placeringer  <br/> |Landedata, der er repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|Placeringstilstand  <br/> |Tilstandsdata, der er repræsenteret i Azure Active Directory for denne bruger.  <br/> |
|Placeringskontor  <br/> |Brugerens kontor.  <br/> |
|Titel  <br/> |Titeldata, der repræsenteres i Azure Active Directory for denne bruger.  <br/> |
|Slettet  <br/> |Sand, hvis brugeren er blevet slettet fra Microsoft 365 i den sidste hele måned.  <br/> |
|Slettet dato  <br/> |Den dato, hvor brugeren blev slettet fra Microsoft 365.  <br/> |
|YAM_State  <br/> |Tilstande for brugeren i det Yammer system, kan være aktive, slettes eller suspenderes.  <br/> |
|YAM_ActivationDate  <br/> |Den dato, hvor brugeren angav tilstanden for at være aktiv i Yammer.  <br/> |
|YAM_DeletionDate  <br/> |Den dato, hvor brugeren indtastede tilstanden for sletning i Yammer.  <br/> |
|YAM_SuspensionDate  <br/> |Den dato, hvor brugeren blev suspenderet i Yammer.  <br/> |
   
### <a name="data-table---user-activity"></a>Datatabel – Brugeraktivitet

Denne tabel indeholder data om hver bruger, der havde en aktivitet i en af tjenesterne i den forrige måned.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Userid  <br/> |Entydigt bruger-id, der repræsenterer en bruger og gør det muligt at forbinde med andre datatabeller i datasættet.  <br/> |
|IDType  <br/> |Id-typen angives til 1, hvis brugeren er en Yammer bruger, der opretter forbindelse ved hjælp af deres Yammer-id, eller 0, hvis brugeren opretter forbindelse til Yammer ved hjælp af deres Microsoft 365-id.  <br/> Værdien er 1 for at repræsentere, at brugeren opretter forbindelse til Yammer med deres Yammer-id og ikke deres Microsoft 365-id  <br/> |
|Tidsramme  <br/> |Månedsværdi, som denne tabel repræsenterer data for.  <br/> |
|EXO_EmailSent  <br/> |Antal mails, der er sendt.  <br/> |
|EXO_EmailReceived  <br/> |Antal modtagne mails.  <br/> |
|EXO_EmailRead  <br/> |Antallet af mails, som brugeren har udført, kan være flere gange at læse en mail, der allerede er læst, eller en mail, der er modtaget tidligere.  <br/> |
|EXO_AppointmentCreated  <br/> |Antal aftaler, der er oprettet.  <br/> |
|EXO_MeetingAccepted  <br/> |Antal accepterede møder.  <br/> |
|EXO_MeetingCancelled  <br/> |Antal aflyste møder.  <br/> |
|EXO_MeetingDeclined  <br/> |Antal møder, der er afslået.  <br/> |
|EXO_MeetingSent  <br/> |Antal sendte møder.  <br/> |
|ODB_FileViewedModified  <br/> |Antal filer, som denne bruger interagerede med på en OneDrive for Business (f.eks. oprettet, opdateret, slettet, vist eller downloadet).  <br/> |
|ODB_FileSynched  <br/> |Antal filer, som denne bruger har synkroniseret på en hvilken som helst OneDrive for Business.  <br/> |
|ODB_FileSharedInternally  <br/> |Antallet af filer, som denne bruger har delt internt fra en OneDrive for Business eller med brugere i grupper (der kan omfatte eksterne brugere).  <br/> |
|ODB_FileSharedExternally  <br/> |Antal filer, som denne bruger har delt eksternt fra en OneDrive for Business.  <br/> |
|ODB_AccessedByOwner  <br/> |Antallet af websteder, som brugeren interagerede med, og som er placeret på egen OneDrive for Business.  <br/> |
|ODB_AccessedByOthers  <br/> |Det antal websteder, som brugeren interagerede med, og som er placeret på en anden brugers OneDrive for Business.  <br/> |
|SPO_GroupFileViewedModified  <br/> |Antallet af filer, som brugeren interagerede med på et gruppewebsted.  <br/> |
|SPO_GroupFileSynched  <br/> |Antal filer, som denne bruger har synkroniseret på et vilkårligt gruppewebsted.  <br/> |
|SPO_GroupFileSharedInternally  <br/> |Antallet af filer, der er blevet delt med brugere i organisationen eller med brugere i grupper (der kan omfatte eksterne brugere).  <br/> |
|SPO_GroupFileSharedExternally  <br/> |Antallet af filer, som denne bruger har delt eksternt fra et gruppewebsted.  <br/> |
|SPO_GroupAccessedByOwner  <br/> |Antallet af websteder, som brugeren interagerede med, og som er placeret på et gruppewebsted, som brugeren ejer.  <br/> |
|SPO_GroupAccessedByOthers  <br/> |Antal websteder, som brugeren interagerede med, og som er placeret på et gruppewebsted, som en anden bruger ejer.  <br/> |
|SPO_OtherFileViewedModified  <br/> |Antal filer, som brugeren interagerede med på et andet websted.  <br/> |
|SPO_OtherFileSynched  <br/> |Antal filer, som denne bruger har synkroniseret fra et hvilket som helst andet websted.  <br/> |
|SPO_OtherFileSharedInternally  <br/> |Antallet af filer, som denne bruger har delt internt fra et hvilket som helst andet websted eller med brugere i grupper (der kan omfatte eksterne brugere). <br/> |
|SPO_OtherFileSharedExternally  <br/> |Antal filer, som denne bruger har delt eksternt fra et andet websted.  <br/> |
|SPO_OtherAccessedByOwner  <br/> |Antallet af websteder, som brugeren interagerede med, og som er placeret på et andet websted, som brugeren ejer.  <br/> |
|SPO_OtherAccessedByOthers  <br/> |Det antal websteder, som brugeren interagerede med, og som er placeret på et andet websted, som en anden bruger ejer.  <br/> |
|SPO_TeamFileViewedModified  <br/> |Antallet af filer, som brugeren interagerede med på et teamwebsted.  <br/> |
|SPO_TeamFileSynched  <br/> |Antal filer, som denne bruger har synkroniseret fra et teamwebsted.  <br/> |
|SPO_TeamFileSharedInternally  <br/> |Antallet af filer, som denne bruger har delt internt fra et teamwebsted eller med brugere i grupper (der kan omfatte eksterne brugere).  <br/> |
|SPO_TeamFileSharedExternally  <br/> |Antallet af filer, som denne bruger har delt eksternt fra et teamwebsted.  <br/> |
|SPO_TeamAccessedByOwner  <br/> |Antallet af websteder, som brugeren interagerede med, og som er placeret på et teamwebsted, som brugeren ejer.  <br/> |
|SPO_TeamAccessedByOthers  <br/> |Antallet af websteder, som brugeren interagerede med, og som er placeret på et teamwebsted, som en anden bruger ejer.  <br/> |
|Teams_ChatMessages  <br/> |Antal chatbeskeder, der er sendt.  <br/> |
|Teams_ChannelMessage  <br/> |Antal meddelelser, der er sendt til kanaler.  <br/> |
|Teams_CallParticipate  <br/> |Antal opkald, som brugeren har deltaget i.  <br/> |
|Teams_MeetingParticipate  <br/> |Antal møder, som brugeren deltager i.  <br/> |
|Teams_HasOtherAction  <br/> |Boolesk værdi, hvis brugeren udførte andre handlinger i Microsoft Teams.  <br/> |
|YAM_MessagePost  <br/> |Antal Yammer meddelelser, som brugeren har sendt.  <br/> |
|YAM_MessageLiked  <br/> |Antal Yammer meddelelser, som brugeren synes godt om.  <br/> |
|YAM_MessageRead  <br/> |Antal Yammer meddelelser, som brugeren har læst.  <br/> |
|SFB_P2PSummary  <br/> |Antallet af peer-to-peer-sessioner, som denne bruger deltog i.  <br/> |
|SFB_ConfOrgSummary  <br/> |Antallet af mødesessioner, som denne bruger har organiseret.  <br/> |
|SFB_ConfPartSummary  <br/> |Antal mødesessioner, som denne bruger har deltaget i.  <br/> |

> [!NOTE]
> Teams_HasOtherAction betyder, at brugeren betragtes som aktiv, men har en nulværdi for chatbeskederne, 1:1-opkald, kanalmeddelelser, samlet antal møder og organiserede møder.
   
### <a name="data-table---tenant-product-usage"></a>Datatabel – Lejerproduktforbrug

Denne tabel indeholder data om indførelse måned for måned med hensyn til aktivering, aktiv, returnering og førstegangsbrugere for hvert produkt inden for Microsoft 365. De Microsoft 365 værdier repræsenterer aktivt forbrug i et af produkterne.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Produkt  <br/> |Navnet på de produkter, som forbrugsoplysningerne opsummeres for. Microsoft 365 værdi i produktkolonnen repræsenterer aktivitet på tværs af et af produkterne  <br/> |
|Tidsramme  <br/> |Månedsværdi. Der vil være én række pr. produkt pr. måned for de sidste 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|EnabledUsers  <br/> |Antallet af brugere, der er aktiveret til at bruge produktet til tidsrammeværdien, hvis en bruger blev aktiveret for en del af måneden, tælles de stadig med.  <br/> |
|ActiveUsers  <br/> |Antallet af brugere, der udførte en bevidst aktivitet i produktet for tidsrammeværdien.  <br/> En bruger tælles som aktiv for et produkt i en bestemt måned, hvis brugeren har udført en af de vigtigste aktiviteter i produktet. Nøgleaktiviteterne er tilgængelige i tabellen **Lejerproduktaktivitet** .  <br/> |
|CumulativeActiveUsers  <br/> |Antallet af brugere, der har tilladelse til at bruge et produkt og har brugt produktet inden for en bestemt tidsramme mindst én gang, siden dataindsamlingen startede i det nye forbrugssystem.  <br/> |
|MoMReturningUsers  <br/> |Antallet af brugere, der er aktive i en bestemt periodemåned, og som også var aktive i den forrige måned.  <br/> |
|FirstTimeUsers  <br/> |Antallet af brugere, der blev aktive inden for tidsrammen for første gang siden dataindsamlingen i det nye forbrugssystem.  <br/> En bruger tælles som førstegangsbruger i en bestemt måned, hvis vi registrerer deres aktivitet for første gang siden starten af dataindsamlingen i dette nye rapporteringssystem. Når den tælles som førstegangsbruger, vil brugeren aldrig blive talt igen som førstegangsbruger, selvom der er et stort hul i brugerens aktivitet  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, repræsenterer denne værdi den seneste dato i den aktuelle måned, for hvilken der er tilgængelige data.  <br/> Hvis Tidsramme viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-product-activity"></a>Datatabel – Lejerproduktaktivitet

Denne tabel indeholder månedlige totaler af aktivitet og antal aktive brugere for forskellige aktiviteter i produkterne.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Tidsramme  <br/> |Månedsværdi. Der vil være én række pr. produkt pr. måned for de sidste 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Produkt  <br/> |Navnet på produktet i Microsoft 365, for hvilket der er tilgængelige forbrugsdata.  <br/> |
|Aktivitet  <br/> |Navnet på aktiviteten i et produkt, der bruges til at fremvise aktiv brug af produktet.  <br/> |
|Aktivitetsantal  <br/> |Dette er det samlede antal handlinger, der tælles for hver aktivitet, der udføres i produktet på tværs af alle aktive brugere.  <br/> **Bemærk:** I forbindelse med SharePoint Online- og OneDrive for Business-aktiviteter repræsenterer denne værdi antallet af forskellige dokumenter, som brugerne interagerede med.  <br/> |
|ActiveUserCount  <br/> |Antallet af brugere, der udførte aktiviteten i produktet.  <br/> |
|TotalDurationInMinute  <br/> |Varighed i minutter på tværs af alle aktive brugere, der har brugt lyd- eller videosession i en relevant Skype for Business aktivitet.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, repræsenterer denne værdi den seneste dato i den aktuelle måned, for hvilken der er tilgængelige data.  <br/> Hvis Tidsramme viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-mailbox-usage"></a>Datatabel – Lejerpostkasseforbrug

Denne tabel består af oversigtsdata på tværs af alle licenserede Exchange Online brugere, der har en brugerpostkasse. Den indeholder tilstanden for slutningen af måneden på tværs af alle brugerpostkasser. Dataene i denne tabel er ikke additive på tværs af flere måneder. Den seneste måneds data i denne tabel repræsenterer den seneste tilstand.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|TotalMailboxes  <br/> |Antal brugerpostkasser til Microsoft 365 abonnement.  <br/> |
|IssueWarningQuota  <br/> |Samlet kvote for udstedelse af advarsel på tværs af alle brugernes postkasser.  <br/> |
|ForbydSendQuota  <br/> |Den samlede kvote for forbud mod afsendelse på tværs af alle brugerpostkasser.  <br/> |
|ForbydSendReceiveQuota  <br/> |Den samlede kvote for forbud mod afsendelse af modtagelseskvoter på tværs af alle brugerpostkasser.  <br/> |
|TotalItemBytes  <br/> |Den mængde lagerplads, der bruges på tværs af alle brugerpostkasser i byte.  <br/> |
|PostkasserNoWarning  <br/> |Antallet af brugerpostkasser, der var under lageradvarselsgrænsen.  <br/> |
|Postkasser ErsueAdvarsel  <br/> |Antallet af brugerpostkasser, der blev udstedt en advarsel om lagerkvoten.  <br/> |
|PostkasserExceedSendQuota  <br/> |Antallet af brugerpostkasser, der har overskredet afsendelseskvoten.  <br/> |
|PostkasserExceedSendReceiveQuota  <br/> |Antallet af brugerpostkasser, der har overskredet send/modtag-kvoten.  <br/> |
|Slettedemailkasser  <br/> |Antal brugerpostkasser, der er slettet inden for tidsrammen.  <br/> |
|Tidsramme  <br/> |Månedsværdi.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, repræsenterer denne værdi den seneste dato i den aktuelle måned, for hvilken der er tilgængelige data.  <br/> Hvis Tidsramme viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-client-usage"></a>Datatabel – Lejerklientforbrug

Denne tabel indeholder oversigtsdata for hver måned for de klienter, som brugerne bruger til at oprette forbindelse til Exchange Online, Skype for Business og Yammer. Denne tabel har endnu ikke klientbrugsdata til SharePoint Online og OneDrive for Business.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Produkt  <br/> |Navnet på produktet i Microsoft 365, som klientbrugsdata er tilgængelige for.  <br/> |
|ClientId  <br/> |Navnet på hver enhed, der bruges til at oprette forbindelse til produktet.  <br/> |
|Antal brugere  <br/> |Antallet af brugere, der brugte hver af klienterne for hvert produkt.  <br/> |
|Tidsramme  <br/> |Månedsværdi  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, repræsenterer denne værdi den seneste dato i den aktuelle måned, for hvilken der er tilgængelige data.  <br/> Hvis Tidsramme viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-sharepoint-online-usage"></a>Datatabel – lejer SharePoint onlinebrug

Denne tabel består af månedsoversigtsdata om brugen eller aktiviteten af SharePoint Online-websteder. Dette omfatter kun teamwebsteder og gruppewebsteder. Tilstanden for slutningen af måneden for SharePoint Online-websteder repræsenteres i denne kolonne, hvis en bruger f.eks. oprettede fem dokumenter og brugte 10 MB som samlet lager og derefter slettede nogle filer og tilføjede flere filer, så der ved slutningen af måneden er syv i alt, der bruger fem MB lagerplads,  værdien af repræsenteret i denne tabel er slutningen af månedens tilstand. Denne tabel er skjult for at undgå dubletantal af sammenlægninger og bruges som kilde til at oprette to referencetabeller.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Webstedstype  <br/> |Webstedstypeværdi (alle/team/gruppe) (alle repræsenterer en af disse to webstedstyper).  <br/> |
|Samlet antal websteder  <br/> |Antal websteder, der fandtes i slutningen af tidsrammen.  <br/> |
|Antal dokumenter  <br/> |Det samlede antal dokumenter, der fandtes på webstedet i slutningen af tidsrammen.  <br/> |
|Diplansed  <br/> |Det samlede anvendte lager, der er opsummeret på tværs af alle websteder i slutningen af tidsrammen.  <br/> |
|Aktivitetstype  <br/> |Antal websteder, der har registreret de forskellige typer filaktivitet (alle/aktive filer/filer, der deles EXT/INT/filer synkroniseret).  <br/> Repræsenterer en hvilken som helst af de filaktiviteter, der blev udført.  <br/> |
|SitesWithOwnerActivities  <br/> |Antallet af aktive websteder, hvor webstedets ejer udførte en bestemt filaktivitet på deres egne websteder. Du kan få webstedets ejer via **PowerShell-kommandoen get-sposite**. Dette er den person, der er ansvarlig for webstedet.   <br/> |
|SitesWithNonOwnerActivities  <br/> |Antallet af aktive websteder opsummeret for måneden, hvor andre brugere end webstedets ejer udførte en bestemt filaktivitet på websteder. Du kan få webstedets ejer via **PowerShell-kommandoen get-sposite**. Dette er den person, der er ansvarlig for webstedet. <br/> |
|AktivitetTotalSites  <br/> |Antallet af websteder, der har registreret en aktivitet inden for tidsrammen. Hvis et websted havde aktivitet tidligere inden for tidsrammen, og det blev slettet inden udgangen af tidsrammen, tælles det stadig med i det aktive websteds samlede antal for den pågældende tidsramme.  <br/> |
|Tidsramme  <br/> |Denne kolonne har datoværdien. Bruges som mange til én-relation for tabellen Kalender.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, repræsenterer denne værdi den seneste dato i den aktuelle måned, for hvilken der er tilgængelige data.  <br/> Hvis Tidsramme viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-onedrive-usage"></a>Datatabel – lejerforbrug OneDrive

Denne tabel indeholder data om de OneDrive konti, f.eks. antal konti, antallet af dokumenter på tværs af OneDrive konti, anvendt lager, filantal efter aktivitetstype. Tilstanden for slutningen af måneden for OneDrive for Business konti er repræsenteret i denne tabel. Hvis en bruger f.eks. har oprettet fem dokumenter, der brugte 10 MB lagerplads, og derefter slettede nogle få og tilføjede flere filer, så de i slutningen af måneden har syv filer, der bruger fem MB lagerplads, vises værdien for slutningen af måneden i denne tabel i slutningen af måneden.
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Webstedstype  <br/> |Værdien er "OneDrive".  <br/> |
|Samlet antal websteder  <br/> |Antallet af OneDrive for Business konti, der fandtes i slutningen af tidsrammen.  <br/> |
|Antal dokumenter  <br/> |Det samlede antal dokumenter, der fandtes på tværs af alle OneDrive for Business konti i slutningen af tidsrammen  <br/> |
|Diplansed  <br/> |Det samlede anvendte lager, der er opsummeret på tværs af alle OneDrive konto i slutningen af tidsrammen.  <br/> |
|Aktivitetstype  <br/> |Antal konti, der har registreret de forskellige typer filaktivitet (alle/aktive filer/filer, der deles EXT/INT/filer synkroniseret).  <br/> Alle repræsenterer den filaktivitet, der blev udført  <br/> |
|SitesWithOwnerActivities  <br/> |Antal aktive OneDrive for Business konti, hvor kontoejeren udførte en bestemt filaktivitet på sin egen konto.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Antallet af OneDrive for Business konti, hvor filaktiviteten blev udført af andre brugere end ejeren af kontoen.  <br/> |
|AktivitetTotalSites  <br/> |Antallet af OneDrive for Business konti, der registrerede en aktivitet inden for tidsrammen. Hvis en OneDrive for Business konto havde aktivitet tidligere i tidsrammen og blev slettet inden udgangen af tidsrammen, ville den stadig blive talt på den aktive OneDrive for Business konto for den pågældende tidsramme.  <br/> |
|Tidsramme  <br/> |Denne kolonne har datoværdien. Bruges som mange til én-relation for tabellen Kalender.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, repræsenterer denne værdi den seneste dato i den aktuelle måned, for hvilken der er tilgængelige data.  <br/> Hvis Tidsramme viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
   
### <a name="data-table---tenant-microsoft-365-groups-usage"></a>Datatabel – lejerforbrug Microsoft 365-grupper

Denne tabel indeholder data om, hvordan Microsoft 365-grupper bruges på tværs af organisationen.
  
****

|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Tidsramme  <br/> |Månedsværdi. Der vil være én række pr. produkt pr. måned for de sidste 12 måneder, herunder den aktuelle delvise måned.  <br/> |
|Gruppetype  <br/> |Type af gruppe (privat/offentlig/enhver).  <br/> |
|TotalGroups  <br/> |Antallet af grupper i hver gruppetype.  <br/> |
|ActiveGroups  <br/> |Antal aktive grupper.  <br/> |
|MBX_TotalGroups  <br/> |Antal postkassegrupper.  <br/> |
|MBX_ActiveGroups  <br/> |Antal aktive postkassegrupper.  <br/> |
|MBX_TotalActivities  <br/> |Antal postkasseaktiviteter.  <br/> |
|MBX_TotalItems  <br/> |Antal postkasseelementer.  <br/> |
|MBX_StorageUsed  <br/> |Antal postkasselager, der bruges.  <br/> |
|SPO_TotalGroups  <br/> |Antal SharePoint grupper.  <br/> |
|SPO_ActiveGroups  <br/> |Antal aktive SharePoint grupper.  <br/> |
|SPO_FileAccessedActiveGroups  <br/> |Antal SharePoint grupper, der har aktiviteter, hvor der er adgang til filer.  <br/> |
|SPO_FileSyncedActiveGroups  <br/> |Antal SharePoint grupper, der har filsynkronerede aktiviteter.  <br/> |
|SPO_FileSharedInternallyActiveGroups  <br/> |Antal SharePoint grupper, der har delte aktiviteter internt eller med grupper (der kan omfatte eksterne brugere).  <br/> |
|SPO_FileSharedExternallyActiveGroups  <br/> |Antal SharePoint grupper, der har delt eksterne aktiviteter.  <br/> |
|SPO_TotalActivities  <br/> |Antal SharePoint aktiviteter.  <br/> |
|SPO_FileAccessedActivities  <br/> |Antal SharePoint aktiviteter, der er åbnet i filen.  <br/> |
|SPO_FileSyncedActivities  <br/> |Antal SharePoint synkroniserede aktiviteter.  <br/> |
|SPO_FileSharedInternallyActivities  <br/> |Antal SharePoint fildelingsaktiviteter internt eller med grupper (der kan omfatte eksterne medlemmer).  <br/> |
|SPO_FileSharedExternallyActivities  <br/> |Antal SharePoint fil, der deles eksternt.  <br/> |
|SPO_TotalFiles  <br/> |Antal SharePoint filer.  <br/> |
|SPO_ActiveFiles  <br/> |Antal aktive SharePoint filer.  <br/> |
|SPO_StorageUsed  <br/> |Det anvendte antal SharePoint lager.  <br/> |
|YAM_TotalGroups  <br/> |Antal Yammer grupper.  <br/> |
|YAM_ActiveGroups  <br/> |Antal aktive Yammer grupper.  <br/> |
|YAM_LikedActiveGroups  <br/> |Antal Yammer grupper, der har lignende aktiviteter.  <br/> |
|YAM_PostedActiveGroups  <br/> |Antal Yammer grupper, der har postaktiviteter.  <br/> |
|YAM_ReadActiveGroups  <br/> |Antal Yammer grupper, der har læseaktiviteter.  <br/> |
|YAM_TotalActivities  <br/> |Antal Yammer aktiviteter.  <br/> |
|YAM_LikedActivities  <br/> |Antal Yammer som aktiviteter.  <br/> |
|YAM_PostedActivties  <br/> |Antal Yammer postaktiviteter.  <br/> |
|YAM_ReadActivites  <br/> |Antal Yammer læseaktiviteter.  <br/> |

### <a name="data-table---tenant-office-licenses"></a>Datatabel – Lejer-Office-licenser

Denne tabel indeholder oversigtsdata for hver måned om licenstildelingen for brugere. 
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Licensnavn  <br/> |Navnet på licensen.  <br/> |
|Tildelt antal  <br/> |Antal tildelte licenser.  <br/> |
|Tidsramme  <br/> |Månedsværdi.  <br/> |

### <a name="data-table---tenant-office-activation"></a>Datatabel – aktivering af lejer Office

Tabellen indeholder data om antallet af Office abonnementsaktiveringer på tværs af tjenesteplanerne, f.eks. Microsoft 365 Apps for virksomheder, Visio, Project. Den indeholder også data om antallet af aktiveringer pr. enhed (Android/iOS/Mac/PC).
  
|**Kolonnenavn**|**Kolonnebeskrivelse**|
|:-----|:-----|
|Navn på serviceplan  <br/> |Liste over navneværdier for tjenesteplanen og antallet af aktiveringer for enheder, som vist af nedenstående kolonner.  <br/> |
|TotalEnabled  <br/> |Antallet af brugere, der er aktiveret pr. tjenesteplannavn efter udløbet af tidsrammen.  <br/> |
|TotalActivatedUsers  <br/> |Antallet af brugere, der har aktiveret hver serviceplan t inden udgangen af tidsrammen.  <br/> |
|AndroidCount  <br/> |Antal aktiveringer pr. tjenesteplan for Android-enhed inden udgangen af tidsrammen.  <br/> |
|iOSCount  <br/> |Antal aktiveringer pr. tjenesteplan for iOS-enhed inden udgangen af tidsrammen.  <br/> |
|MacCount  <br/> |Antal aktiveringer pr. tjenesteplan for MAC-enhed inden udgangen af tidsrammen.  <br/> |
|PcCount  <br/> |Antal aktiveringer pr. tjenesteplan for pc-enhed inden udgangen af tidsrammen.  <br/> |
|WinRtCount  <br/> |Antal aktiveringer pr. tjenesteplan for Windows mobilenhed inden udgangen af tidsrammen.  <br/> |
|Tidsramme  <br/> |Denne kolonne har datoværdien. Bruges som mange til én-relation for tabellen Kalender.  <br/> |
|Indholdsdato  <br/> |Hvis tidsrammen viser den aktuelle måned, repræsenterer denne værdi den seneste dato i den aktuelle måned, for hvilken der er tilgængelige data.  <br/> Hvis Tidsramme viser forrige måned, repræsenterer denne værdi den sidste dato i tidsrammemåneden.  <br/> |
