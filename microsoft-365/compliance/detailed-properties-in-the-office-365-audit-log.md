---
title: Detaljerede egenskaber i overvågningsloggen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- BCS160
- MET150
ms.assetid: ce004100-9e7f-443e-942b-9b04098fcfc3
description: Denne artikel indeholder beskrivelser af yderligere egenskaber, der er inkluderet, når du eksporterer resultater for Office 365 overvågningslogpost.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1293cdda6ae99fc64b331b7e10cf827c62504456
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/15/2022
ms.locfileid: "63587884"
---
# <a name="detailed-properties-in-the-audit-log"></a>Detaljerede egenskaber i overvågningsloggen

Når du eksporterer resultaterne af en søgning i overvågningsloggen fra Microsoft 365 Overholdelsescenter, har du mulighed for at hente alle de resultater, der opfylder dine søgekriterier. Det gør du ved at vælge **Eksportér resultater** \> **Download alle resultater** på siden **Søgning i overvågningslogfil** . Du kan finde flere oplysninger [i Søge i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).
  
 Når du eksporterer alle resultater for en søgning i overvågningsloggen, kopieres de rå data fra den samlede overvågningslog til en fil med kommaseparerede værdier (CSV),der downloades til din lokale computer. Denne fil indeholder yderligere oplysninger fra hver overvågningspost i en kolonne med navnet **AuditData**. Denne kolonne indeholder en egenskab med flere værdier for flere egenskaber fra overvågningslogposten. Hver af egenskaben **: værdipar** i denne egenskab med flere værdier er adskilt af et komma. 
  
I følgende tabel beskrives de egenskaber, der er inkluderet (afhængigt af den tjeneste, hvor en hændelse forekommer) i kolonnen **AuditData med flere** egenskaber. Den **Office 365 tjeneste, der** har denne egenskabskolonne, angiver den tjeneste og type aktivitet (bruger eller administrator), der indeholder egenskaben. Du kan finde flere oplysninger om disse egenskaber eller om egenskaber, der muligvis ikke er angivet i dette emne, i Skema [for Management Activity API](/office/office-365-management-api/office-365-management-activity-api-schema).
  
> [!TIP]
> Du kan bruge JSON-transformeringsfunktionen i Power-forespørgsel i Excel til at opdele **kolonnen AuditData** i flere kolonner, så hver egenskab har sin egen kolonne. Dette giver dig mulighed for at sortere og filtrere efter en eller flere af disse egenskaber. Se Eksportér, konfigurer og få vist overvågningslogposter for at få mere at vide [om, hvordan du gør dette](export-view-audit-log-records.md). 
  
|**Egenskab**|**Beskrivelse**|**Microsoft 365 tjeneste, der har denne egenskab**|
|:-----|:-----|:-----|
|Agent|Den bruger eller tjenestekonto, der udførte handlingen.|Azure Active Directory|
|AddOnName|Navnet på et tilføjelsesprogrammet, der er blevet tilføjet, fjernet eller opdateret i et team. Typen af tilføjelser i en Microsoft Teams er en bot, en forbindelse eller en fane.|Microsoft Teams|
|AddOnType|Den type tilføjelsesprogrammet, der blev tilføjet, fjernet eller opdateret i et team. Følgende værdier angiver typen af tilføjelsesprogrammet.  <br/> **1** – Angiver en bot.<br/> **2** – Angiver en forbindelse.<br/> **3** – Angiver en fane.|Microsoft Teams|
|AzureActiveDirectoryEventType|Typen af Azure Active Directory begivenhed. Følgende værdier angiver typen af hændelse.  <br/> **0** – Angiver en kontologonhændelse.<br/> **1** – Angiver en Azure-programsikkerhedshændelse.|Azure Active Directory|
|ChannelGuid|Id'et for Microsoft Teams kanal. Det team, kanalen er placeret i, er identificeret af **egenskaberne TeamName** og **TeamGuid** .|Microsoft Teams|
|ChannelName|Navnet på en Microsoft Teams kanal. Det team, kanalen er placeret i, er identificeret af **egenskaberne TeamName** og **TeamGuid** .|Microsoft Teams|
|Klient|Klientenheden, enhedens operativsystem og enhedsbrowseren, der bruges til logonhændelsen (f.eks. Nokia Lumia 920; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|Oplysninger om den mailklient, der blev brugt til at udføre handlingen, f.eks. en browserversion, en Outlook version og oplysninger om mobilenheder|Exchange (postkasseaktivitet)|
|ClientIP|IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.<br/><br/> For nogle tjenester kan den værdi, der vises i denne egenskab, være IP-adressen for et pålideligt program (f.eks. Office på internettet-apps), der ringer til tjenesten på vegne af en bruger og ikke IP-adressen på den enhed, der bruges af den person, der udførte aktiviteten. <br/><br/>Desuden logføres IP-adressen ikke for administratoraktivitet (eller aktivitet, der er udført af en systemkonto) for Azure Active Directory-relaterede hændelser, og værdien for egenskaben ClientIP er `null`. |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Dato og klokkeslæt i UTC-tid (Coordinated Universal Time), hvor brugeren udførte aktiviteten.|Alle|
|DestinationFileExtension|Filtypenavnet på en fil, der kopieres eller flyttes. Denne egenskab vises kun for brugeraktiviteterne FileCopied og FileMoved.|SharePoint|
|DestinationFileName|Navnet på filen kopieres eller flyttes. Denne egenskab vises kun for handlingerne FileCopied og FileMoved.|SharePoint|
|DestinationRelativeUrl|URL-adressen på destinationsmappen, hvor en fil kopieres eller flyttes. En kombination af værdierne for egenskaben **SiteURL**, **DestinationRelativeURL** og **DestinationFileName** er det samme som værdien af **egenskaben ObjectID** , som er det fulde stinavn for den fil, der blev kopieret. Denne egenskab vises kun for brugeraktiviteterne FileCopied og FileMoved.|SharePoint|
|EventSource|Identificerer, at der opstod en hændelse i SharePoint. Mulige værdier er **SharePoint** og **ObjectModel**.|SharePoint|
|ExternalAccess|For Exchange administratoraktivitet angiver det, om cmdlet'en blev kørt af en bruger i organisationen, af en medarbejder eller en tjenestekonto i Microsofts datacenter eller af en delegeret administrator. Værdien Falsk **indikerer** , at cmdlet'en blev kørt af en person i organisationen. Værdien Sand **angiver** , at cmdlet'en blev kørt af en datacentermedarbejder, en datacentertjenestekonto eller en delegeret administrator.  <br/> For Exchange postkasseaktivitet angiver det, om en postkasse blev åbnet af en bruger uden for organisationen.|Exchange|
|ExtendedProperties|De udvidede egenskaber for en Azure Active Directory hændelse.|Azure Active Directory|
|Id|Id'et for rapportposten. Id'et identificerer rapportposten entydigt.|Alle|
|InternalLogonType|Reserveret til intern brug.|Exchange (postkasseaktivitet)|
|ItemType|Den type objekt, der blev åbnet eller redigeret. Mulige værdier omfatter **Fil**, **Mappe**, **Websted**, **Websted**, **Lejer** og **DocumentLibrary**.|SharePoint|
|LoginStatus|Identificerer logonfejl, der kan være opstået.|Azure Active Directory|
|LogonType|Typen af postkasseadgang. Følgende værdier angiver typen af bruger, der har åbnet postkassen.  <br/><br/> **0** – Angiver en postkasseejer.<br/> **1** – Angiver en administrator.<br/> **2** – Angiver en stedfortræder. <br/>**3** – Angiver transporttjenesten i Microsofts datacenter.<br/> **4** – Angiver en tjenestekonto i Microsofts datacenter. <br/>**6** – Angiver en delegeret administrator.|Exchange (postkasseaktivitet)|
|MailboxGuid|Den Exchange GUID for den postkasse, der blev åbnet.|Exchange (postkasseaktivitet)|
|MailboxOwnerUPN|Mailadressen på den person, der ejer postkassen, som blev åbnet.|Exchange (postkasseaktivitet)|
|Medlemmer|Viser de brugere, der er blevet tilføjet eller fjernet fra et team. Følgende værdier angiver den rolletype, brugeren er tildelt.  <br/><br/> **1** – Angiver rollen Ejer.<br/> **2** – Angiver rollen Medlem.<br/> **3** – Angiver rollen Gæst. <br/><br/>Egenskaben Medlemmer omfatter også navnet på organisationen og medlemmets mailadresse.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|Egenskaben er inkluderet for administratorhændelser, f.eks. tilføjelse af en bruger som medlem af et websted eller en administratorgruppe for en gruppe af websteder. Egenskaben indeholder navnet på den egenskab, der blev ændret (f.eks. gruppen Webstedsadministrator) den nye værdi af den ændrede egenskab (f.eks. den bruger, der blev tilføjet som webstedsadministrator, og den tidligere værdi for det ændrede objekt.|Alle (administratoraktivitet)|
|ObjectId|For Exchange overvågningslogføring skal du se navnet på det objekt, der blev ændret af cmdlet'en.  <br/> For SharePoint aktivitet skal det fulde URL-stinavn på den fil eller mappe, der blev åbnet af en bruger.  <br/> For Azure AD-aktivitet: navnet på den brugerkonto, der blev ændret.|Alle|
|Handling|Navnet på bruger- eller administratoraktiviteten. Værdien af denne egenskab svarer til den værdi, der blev valgt **på rullelisten** Aktiviteter. Hvis **Vis resultater for alle aktiviteter** er markeret, medfølger rapporten poster for alle bruger- og administratoraktiviteter for alle tjenester. Du kan finde en beskrivelse af de handlinger/aktiviteter, der logføres i overvågningsloggen, under fanen Overvågede aktiviteter i Søge i [overvågningsloggen Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> For Exchange af administratoraktivitet identificerer denne egenskab navnet på den cmdlet, der blev kørt.|Alle|
|OrganizationId|GUID for organisationen.|Alle|
|Sti|Navnet på postkassemappen, hvor den meddelelse, der blev åbnet, er placeret. Denne egenskab identificerer også den mappe, hvor en meddelelse oprettes eller kopieres/flyttes til.|Exchange (postkasseaktivitet)|
|Parametre|For Exchange administratoraktivitet skal navnet og værdien for alle parametre, der blev brugt sammen med den cmdlet, der er identificeret i egenskaben Handling.|Exchange (administratoraktivitet)|
|RecordType|Den type handling, der er angivet af posten. Denne egenskab angiver den tjeneste eller funktion, som handlingen blev udløst i. Du kan finde en liste over posttyper og deres tilsvarende ENUM-værdi (som er den værdi,  der vises i posttypeegenskaben i en overvågningspost) under Posttype for [overvågningslogfil](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus|Angiver, om handlingen (angivet i **egenskaben Operation** ) blev gennemført eller ej.  <br/> For Exchange er værdien enten **Sand** (vellykket) eller **Falsk** (mislykket).|Alle  <br/>|
|SecurityComplianceCenterEventType|Angiver, at aktiviteten var en Microsoft 365 Overholdelsescenter begivenhed. Alle aktiviteter i overholdelsescenter har en værdi på **0** for denne egenskab.|Security & Compliance Center|
|SharingType|Den type tilladelser for deling, der blev tildelt til den bruger, som ressourcen blev delt med. Denne bruger er identificeret i **egenskaben UserSharedWith** .|SharePoint|
|Websted|GUID for det websted, hvor filen eller mappen, der blev åbnet af brugeren, er placeret.|SharePoint|
|SiteUrl|URL-adressen på det websted, hvor filen eller mappen, der blev åbnet af brugeren, er placeret.|SharePoint|
|SourceFileExtension|Filtypenavnet for den fil, der blev åbnet af brugeren. Denne egenskab er tom, hvis det objekt, der blev åbnet, er en mappe.|SharePoint|
|SourceFileName|Navnet på den fil eller mappe, der blev åbnet af brugeren.|SharePoint|
|SourceRelativeUrl|URL-adressen på den mappe, der indeholder den fil, der blev åbnet af brugeren. En kombination af værdierne for egenskaben **SiteURL**, **SourceRelativeURL** og **SourceFileName** er det samme som værdien af **egenskaben ObjectID** , som er det fulde stinavn for den fil, der blev åbnet af brugeren.|SharePoint|
|Emne|Emnelinjen i den meddelelse, der blev åbnet.|Exchange (postkasseaktivitet)|
|TabType| Fanetypen, der er tilføjet, fjernet eller opdateret for et team. De mulige værdier for denne egenskab er:  <br/><br/> **Excel –** en Excel fane.  <br/> **Udvidelse** – Alle apps fra første part og tredjepart; f.eks. Klassetidsplan, VSTS og Formularer.  <br/> **Noter** – OneNote fane.  <br/> **Pdfpin** – en PDF-fane.  <br/> **Powerbi** – en Power BI fane.  <br/> **Powerpointpin** – en PowerPoint fane.  <br/> **Sharepointfiles** – en SharePoint fane.  <br/> **Webside** – en fastgjort webstedsfane.  <br/> **Wiki-fane** – en wiki-fane.  <br/> **Wordpin** – En Word-fane.|Microsoft Teams|
|Destination|Den bruger, som handlingen (identificeret i **egenskaben Handling** ) blev udført på. Hvis en gæstebruger f.eks. føjes SharePoint et Microsoft-team, vil den pågældende bruger være angivet i denne egenskab.|Azure Active Directory|
|TeamGuid|Id'et for et team i Microsoft Teams.|Microsoft Teams|
|Teamnavn|Navnet på et team i Microsoft Teams.|Microsoft Teams|
|UserAgent|Oplysninger om brugerens browser. Disse oplysninger leveres af browseren.|SharePoint|
|UserDomain|Identitetsoplysninger om lejerorganisationen for den bruger (agent), der udførte handlingen.|Azure Active Directory|
|UserId|Den bruger, der udførte handlingen (angivet i egenskaben **Handling** ), som resulterede i, at posten blev logført. Overvågningsposter for aktivitet, der udføres af systemkonti (f.eks. SHAREPOINT\system eller NT AUTHORITY\SYSTEM), medtages også i overvågningsloggen. En anden fælles værdi for egenskaben UserId er app@sharepoint. Dette angiver, at den "bruger", der udførte aktiviteten, var et program, der har de nødvendige tilladelser i SharePoint til at udføre handlinger for hele organisationen (f.eks. søge i et SharePoint-websted eller en OneDrive-konto) på vegne af en bruger, administrator eller tjeneste. <br/><br/>Du kan finde flere oplysninger under:<br/> [\@Appsharepoint-brugeren i overvågningsposter](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)<br/> eller <br/>[Systemkonti i Exchange postkasse overvågningsposter](search-the-audit-log-in-security-and-compliance.md#system-accounts-in-exchange-mailbox-audit-records). |Alle|
|UserKey|Et alternativt id for den bruger, der er identificeret i **egenskaben UserID** . Denne egenskab er f.eks. udfyldt med et entydigt passport-id (PUID) for hændelser, der udføres af brugere SharePoint. Denne egenskab kan også angive den samme værdi som **egenskaben UserID** for hændelser, der forekommer i andre tjenester, og hændelser, der udføres af systemkonti.|Alle|
|UserSharedWith|Den bruger, som en ressource blev delt med. Denne egenskab er inkluderet, hvis værdien for **egenskaben Operation** er **SharingSet**. Denne bruger også er angivet **i kolonnen Delt** med i rapporten.|SharePoint|
|UserType|Den type bruger, der udførte handlingen. Følgende værdier angiver brugertypen. <br/> <br/> **0** – En almindelig bruger. <br/>**2** – En administrator i Microsoft 365 organisation.<sup> 1</sup> <br/>**3** – En Microsoft-datacenteradministrator eller datacentersystemkonto. <br/>**4** – En systemkonto. <br/>**5** – Et program. <br/>**6** – En tjenesteinspektør.<br/>**7** – En brugerdefineret politik.<br/>**8** – En systempolitik.|Alle|
|Version|Angiver versionsnummeret for den aktivitet (identificeres ved hjælp af **egenskaben Operation** ), der logføres.|Alle|
|Arbejdsbelastning|Den Microsoft 365 tjeneste, hvor aktiviteten forekom.|Alle|
||||

> [!NOTE]
><sup>1</sup> Azure Active Directory relaterede hændelser bruges værdien for en administrator ikke i en overvågningspost. Overvågningsposter for aktiviteter, der udføres af administratorer, angiver, at en almindelig bruger (f.eks. **UserType: 0**) udførte aktiviteten. Egenskaben **UserID** identificerer den person (almindelig bruger eller administrator), der udførte aktiviteten.
