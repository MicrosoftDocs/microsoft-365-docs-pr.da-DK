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
description: Denne artikel indeholder beskrivelser af yderligere egenskaber, der er inkluderet, når du eksporterer resultater for en Office 365 overvågningslogpost.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7e65b5e27f8c6821b12c7f0b7f03e4ecb472c0a9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948941"
---
# <a name="detailed-properties-in-the-audit-log"></a>Detaljerede egenskaber i overvågningsloggen

Når du eksporterer resultaterne af en søgning i en overvågningslog fra Microsoft Purview-overholdelsesportalen, har du mulighed for at downloade alle de resultater, der opfylder dine søgekriterier. Det gør du ved at vælge **Eksportér resultater** \> **Download alle resultater** på **søgesiden Overvågningslog** . Du kan finde flere oplysninger i [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).
  
 Når du eksporterer alle resultater for en søgning i en overvågningslog, kopieres rådata fra den samlede overvågningslog til en kommasepareret værdifil (CSV), der downloades til din lokale computer. Denne fil indeholder flere oplysninger fra hver overvågningspost i en kolonne med navnet **AuditData**. Denne kolonne indeholder en egenskab med flere værdier for flere egenskaber fra overvågningslogposten. Hver af **egenskaben: værdipar** i denne egenskab med flere værdier er adskilt af et komma. 
  
I følgende tabel beskrives de egenskaber, der er inkluderet (afhængigt af den tjeneste, som en hændelse opstår i) i kolonnen **AuditData** med flere egenskaber. Den **Office 365 tjeneste, der har denne egenskabskolonne**, angiver den tjeneste og aktivitetstype (bruger eller administrator), der indeholder egenskaben. Du kan finde flere detaljerede oplysninger om disse egenskaber eller om egenskaber, der muligvis ikke er angivet i dette emne, under [API-skema til administration af aktivitet](/office/office-365-management-api/office-365-management-activity-api-schema).
  
> [!TIP]
> Du kan bruge transformationsfunktionen JSON i Power Query i Excel til at opdele kolonnen **AuditData** i flere kolonner, så hver egenskab har sin egen kolonne. Det giver dig mulighed for at sortere og filtrere på en eller flere af disse egenskaber. Du kan få mere at vide om, hvordan du gør dette, under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md). 
  
|**Ejendom**|**Beskrivelse**|**Microsoft 365 tjeneste, der har denne egenskab**|
|:-----|:-----|:-----|
|Skuespiller|Den bruger- eller tjenestekonto, der udførte handlingen.|Azure Active Directory|
|AddOnName|Navnet på et tilføjelsesprogram, der blev tilføjet, fjernet eller opdateret i et team. Typen af tilføjelsesprogrammer i Microsoft Teams er en bot, en connector eller en fane.|Microsoft Teams|
|AddOnType|Typen af tilføjelsesprogram, der blev tilføjet, fjernet eller opdateret i et team. Følgende værdier angiver typen af tilføjelsesprogram.  <br/> **1** – angiver en bot.<br/> **2** – Angiver en connector.<br/> **3** – Angiver en fane.|Microsoft Teams|
|AzureActiveDirectoryEventType|Typen af Azure Active Directory hændelse. Følgende værdier angiver hændelsestypen.  <br/> **0** – Angiver en kontologonhændelse.<br/> **1** – Angiver en sikkerhedshændelse for et Azure-program.|Azure Active Directory|
|ChannelGuid|Id'et for en Microsoft Teams kanal. Det team, som kanalen er placeret i, identificeres af egenskaberne **TeamName** og **TeamGuid** .|Microsoft Teams|
|ChannelName|Navnet på en Microsoft Teams kanal. Det team, som kanalen er placeret i, identificeres af egenskaberne **TeamName** og **TeamGuid** .|Microsoft Teams|
|Klient|Klientenheden, enhedens OPERATIVSYSTEM og den enhedsbrowser, der bruges til logonhændelsen (f.eks. Nokia Lumia 920; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|Oplysninger om den mailklient, der blev brugt til at udføre handlingen, f.eks. en browserversion, Outlook version og oplysninger om mobilenheder|Exchange (postkasseaktivitet)|
|ClientIP|IP-adressen på den enhed, der blev brugt, da aktiviteten blev logført. IP-adressen vises i enten et IPv4- eller IPv6-adresseformat.<br/><br/> For nogle tjenester kan den værdi, der vises i denne egenskab, være IP-adressen for et program, der er tillid til (f.eks. Office på internettet apps), der ringer til tjenesten på vegne af en bruger, og ikke IP-adressen på den enhed, der bruges af den person, der udførte aktiviteten. <br/><br/>Desuden logføres IP-adressen ikke for administratoraktivitet (eller aktivitet, der udføres af en systemkonto) for Azure Active Directory-relaterede hændelser, og værdien for egenskaben ClientIP er `null`. |Azure Active Directory, Exchange, SharePoint|
|Oprettelsestid|Den dato og det klokkeslæt i UTC (Coordinated Universal Time), hvor brugeren udførte aktiviteten.|Alle|
|DestinationFileExtension|Filtypenavnet for en fil, der kopieres eller flyttes. Denne egenskab vises kun for brugeraktiviteterne FileCopied og FileMoved.|SharePoint|
|Destinationsfilnavn|Navnet på filen kopieres eller flyttes. Denne egenskab vises kun for handlingerne FileCopied og FileMoved.|SharePoint|
|DestinationRelativeUrl|URL-adressen til destinationsmappen, hvor en fil kopieres eller flyttes. Kombinationen af værdierne for **SiteURL**, **DestinationRelativeURL** og egenskaben **DestinationFileName** er den samme som værdien for egenskaben **ObjectID** , som er det fulde stinavn for den fil, der blev kopieret. Denne egenskab vises kun for brugeraktiviteterne FileCopied og FileMoved.|SharePoint|
|EventSource|Identificerer, at der opstod en hændelse i SharePoint. De mulige værdier er **SharePoint** og **ObjectModel**.|SharePoint|
|Ekstern adgang|I forbindelse med Exchange administratoraktivitet angiver, om cmdlet'en blev kørt af en bruger i din organisation, af Microsofts datacenterpersonale eller en datacentertjenestekonto eller af en uddelegeret administrator. Værdien **False** angiver, at cmdlet'en blev kørt af en person i din organisation. Værdien **True** angiver, at cmdlet'en blev kørt af datacenterafdelingen, en datacentertjenestekonto eller en delegeret administrator.  <br/> I forbindelse med Exchange postkasseaktivitet angiver, om en postkasse blev åbnet af en bruger uden for organisationen.|Exchange|
|Udvidedeegenskaber|De udvidede egenskaber for en Azure Active Directory hændelse.|Azure Active Directory|
|ID|Id'et for rapportposten. Id'et identificerer entydigt rapportposten.|Alle|
|InternalLogonType|Reserveret til intern brug.|Exchange (postkasseaktivitet)|
|Itemtype|Den objekttype, der blev åbnet eller ændret. Mulige værdier omfatter **Fil**, **Mappe**, **Websted**, **Websted**, **Lejer** og **Dokumentbibliotek**.|SharePoint|
|Logonstatus|Identificerer logonfejl, der kan være opstået.|Azure Active Directory|
|LogonType|Typen af postkasseadgang. Følgende værdier angiver typen af bruger, der har åbnet postkassen.  <br/><br/> **0** – Angiver ejeren af en postkasse.<br/> **1** – Angiver en administrator.<br/> **2** – Angiver en stedfortræder. <br/>**3** – Angiver transporttjenesten i Microsoft-datacenteret.<br/> **4** – Angiver en tjenestekonto i Microsoft-datacenteret. <br/>**6** – Angiver en delegeret administrator.|Exchange (postkasseaktivitet)|
|MailboxGuid|Det Exchange GUID for den postkasse, der blev åbnet.|Exchange (postkasseaktivitet)|
|PostkasseEjerUPN|Mailadressen på den person, der ejer den postkasse, der blev åbnet.|Exchange (postkasseaktivitet)|
|Medlemmer|Viser de brugere, der er blevet tilføjet eller fjernet fra et team. Følgende værdier angiver den rolletype, der er tildelt brugeren.  <br/><br/> **1** – Angiver ejerrollen.<br/> **2** – Angiver rollen Medlem.<br/> **3** – Angiver gæsterollen. <br/><br/>Egenskaben Medlemmer indeholder også navnet på din organisation og medlemmets mailadresse.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|Egenskaben er inkluderet i administratorhændelser, f.eks. tilføjelse af en bruger som medlem af et websted eller en administratorgruppe for en gruppe af websteder. Egenskaben indeholder navnet på den egenskab, der blev ændret (f.eks. gruppen Webstedsadministrator) den nye værdi for den ændrede egenskab (f.eks. den bruger, der blev tilføjet som webstedsadministrator, og den forrige værdi for det ændrede objekt.|Alle (administratoraktivitet)|
|Objectid|Navnet på det objekt, der blev ændret af cmdlet'en, for Exchange administratorovervågningslogføring.  <br/> I forbindelse med SharePoint aktivitet er det fulde URL-stinavn på den fil eller mappe, en bruger har åbnet.  <br/> I forbindelse med Azure AD-aktivitet er navnet på den brugerkonto, der blev ændret.|Alle|
|Drift|Navnet på bruger- eller administratoraktiviteten. Værdien af denne egenskab svarer til den værdi, der blev valgt på rullelisten **Aktiviteter** . Hvis **Vis resultater for alle aktiviteter** er valgt, indeholder rapporten poster for alle bruger- og administratoraktiviteter for alle tjenester. Du kan finde en beskrivelse af de handlinger/aktiviteter, der er logført i overvågningsloggen, under fanen **Overvågede aktiviteter** under [Søg i overvågningsloggen i Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> For Exchange administratoraktivitet identificerer denne egenskab navnet på den cmdlet, der blev kørt.|Alle|
|Organisations-id|GUID'et for din organisation.|Alle|
|Sti|Navnet på den postkassemappe, hvor den meddelelse, der blev åbnet, er placeret. Denne egenskab identificerer også den mappe, hvor en meddelelse oprettes i eller kopieres/flyttes til.|Exchange (postkasseaktivitet)|
|Parametre|For Exchange administratoraktivitet, navn og værdi for alle parametre, der blev brugt sammen med den cmdlet, der er identificeret i egenskaben Operation.|Exchange (administratoraktivitet)|
|Posttype|Den type handling, der er angivet af posten. Denne egenskab angiver den tjeneste eller funktion, som handlingen blev udløst i. Du kan se en liste over posttyper og deres tilsvarende ENUM-værdi (som er den værdi, der vises i egenskaben **RecordType** i en overvågningspost) under [Overvågningslogposttype](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus|Angiver, om handlingen (angivet i egenskaben **Operation** ) lykkedes eller ej.  <br/> For Exchange administratoraktivitet er værdien enten **Sand** (vellykket) eller **Falsk** (mislykket).|Alle  <br/>|
|SecurityComplianceCenterEventType|Angiver, at aktiviteten var en hændelse på overholdelsesportalen. Alle aktiviteter i overholdelsescenter har en værdi på **0** for denne egenskab.|Security & Compliance Center|
|SharingType|Den type delingstilladelser, der blev tildelt den bruger, som ressourcen blev delt med. Denne bruger identificeres i egenskaben **UserSharedWith** .|SharePoint|
|Websted|GUID'et for det websted, hvor filen eller mappen, som brugeren har adgang til, er placeret.|SharePoint|
|Url-adresse for websted|URL-adressen på det websted, hvor filen eller mappen, som brugeren har adgang til, er placeret.|SharePoint|
|SourceFileExtension|Filtypenavnet for den fil, som brugeren har fået adgang til. Denne egenskab er tom, hvis det objekt, der blev åbnet, er en mappe.|SharePoint|
|Kildefilnavn|Navnet på den fil eller mappe, som brugeren har adgang til.|SharePoint|
|SourceRelativeUrl|URL-adressen til den mappe, der indeholder den fil, som brugeren har åbnet. Kombinationen af værdierne for **SiteURL**, **SourceRelativeURL** og egenskaben **SourceFileName** er den samme som værdien for egenskaben **ObjectID** , som er det fulde stinavn for den fil, som brugeren har adgang til.|SharePoint|
|Emne|Emnelinjen i den meddelelse, der blev åbnet.|Exchange (postkasseaktivitet)|
|TabType| Den type fane, der er tilføjet, fjernet eller opdateret i et team. De mulige værdier for denne egenskab er:  <br/><br/> **Excel pin** – en fane med Excel.  <br/> **Extension** – alle apps fra førstepart og tredjepart. f.eks. Klasseplan, VSTS og Formularer.  <br/> **Noter** – fanen OneNote.  <br/> **Pdfpin** – en PDF-fane.  <br/> **Powerbi** – en Power BI fane.  <br/> **Powerpointpin** – en PowerPoint fane.  <br/> **Sharepointfiles** – en fane af SharePoint.  <br/> **Webside** – en fastgjort webstedsfane.  <br/> **Wikifane** – en wikifane.  <br/> **Wordpin** – en Word-fane.|Microsoft Teams|
|Mål|Den bruger, som handlingen (identificeret i egenskaben **Operation** ) blev udført på. Hvis en gæstebruger f.eks. føjes til SharePoint eller et Microsoft-team, vises denne bruger i denne egenskab.|Azure Active Directory|
|TeamGuid|Id'et for et team i Microsoft Teams.|Microsoft Teams|
|Teamnavn|Navnet på et team i Microsoft Teams.|Microsoft Teams|
|Useragent|Oplysninger om brugerens browser. Disse oplysninger leveres af browseren.|SharePoint|
|UserDomain|Identitetsoplysninger om lejerorganisationen for den bruger (agent), der udførte handlingen.|Azure Active Directory|
|Userid|Den bruger, der udførte handlingen (angivet i egenskaben **Operation** ), som resulterede i, at posten blev logført. Overvågningsposter for aktivitet, der udføres af systemkonti (f.eks. SHAREPOINT\system eller NT AUTHORITY\SYSTEM), medtages også i overvågningsloggen. En anden fælles værdi for egenskaben UserId er app@sharepoint. Dette angiver, at den "bruger", der udførte aktiviteten, var et program, der har de nødvendige tilladelser i SharePoint til at udføre handlinger for hele organisationen (f.eks. søge på et SharePoint websted eller en OneDrive konto) på vegne af en bruger, administrator eller tjeneste. <br/><br/>Du kan finde flere oplysninger under:<br/> [Appsharepoint-brugeren\@ i overvågningsposter](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)<br/> Eller <br/>[Systemkonti i Exchange postkassens overvågningsposter](search-the-audit-log-in-security-and-compliance.md#system-accounts-in-exchange-mailbox-audit-records). |Alle|
|UserKey|Et alternativt id for den bruger, der er identificeret i egenskaben **UserID** . Denne egenskab udfyldes f.eks. med det entydige pas-id (PUID) for hændelser, der udføres af brugere i SharePoint. Denne egenskab kan også angive den samme værdi som egenskaben **UserID** for hændelser, der forekommer i andre tjenester og hændelser, der udføres af systemkonti.|Alle|
|UserSharedWith|Den bruger, som en ressource blev delt med. Denne egenskab er inkluderet, hvis værdien for egenskaben **Operation** er **SharingSet**. Denne bruger er også angivet i kolonnen **Delt med** i rapporten.|SharePoint|
|UserType|Den type bruger, der udførte handlingen. Følgende værdier angiver brugertypen. <br/> <br/> **0** – en almindelig bruger. <br/>**2** – En administrator i din Microsoft 365 organisation.<sup> 1</sup> <br/>**3** – En Microsoft-datacenteradministrator eller en datacentersystemkonto. <br/>**4** – En systemkonto. <br/>**5** – Et program. <br/>**6** – En tjenesteprincipal.<br/>**7** – En brugerdefineret politik.<br/>**8** – En systempolitik.|Alle|
|Version|Angiver versionsnummeret for den aktivitet (identificeret af egenskaben **Operation** ), der er logført.|Alle|
|Arbejdsbyrde|Den Microsoft 365 tjeneste, hvor aktiviteten fandt sted.|Alle|
||||

> [!NOTE]
><sup>1</sup> I forbindelse med Azure Active Directory-relaterede hændelser bruges værdien for en administrator ikke i en overvågningspost. Overvågningsposter for aktiviteter, der udføres af administratorer, angiver, at en almindelig bruger (f.eks **. UserType: 0**) udførte aktiviteten. Egenskaben **UserID** identificerer den person (almindelig bruger eller administrator), der udførte aktiviteten.
