---
title: Nøgleordsforespørgsler og søgebetingelser for eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SearchQueryLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: c4639c2e-7223-4302-8e0d-b6e10f1c3be3
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om mail- og dokumentegenskaber, som du kan søge i ved hjælp af eDiscovery-søgeværktøjerne i Microsoft 365.
ms.openlocfilehash: 3ff2143a170531b527850b4805cb9a79f10afb5e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623865"
---
# <a name="keyword-queries-and-search-conditions-for-ediscovery"></a>Nøgleordsforespørgsler og søgebetingelser for eDiscovery

I denne artikel beskrives de mail- og dokumentegenskaber, du kan søge efter i mailelementer og Microsoft Teams-chatsamtaler i Exchange Online, og dokumenter, der er gemt på SharePoint og OneDrive for Business websteder ved hjælp af eDiscovery-søgeværktøjerne i Microsoft Purview-compliance-portal. Dette omfatter indholdssøgning, Microsoft Purview eDiscovery (Standard) og Microsoft Purview eDiscovery (Premium) (eDiscovery-søgninger i eDiscovery (Premium) kaldes *samlinger*). Du kan også bruge **\*-ComplianceSearch-cmdlet'erne** i Security & Compliance PowerShell til at søge efter disse egenskaber. I artiklen beskrives også:

- Brug booleske søgeoperatorer, søgebetingelser og andre teknikker til søgeforespørgslen til at tilpasse søgeresultaterne.
- Søger efter følsomme datatyper og brugerdefinerede følsomme datatyper i SharePoint og OneDrive for Business.
- Søger efter webstedsindhold, der er delt med brugere uden for din organisation

Du kan finde en trinvis vejledning i, hvordan du opretter forskellige eDiscovery-søgninger, under:

- [Indholdssøgning](content-search.md)
- [Søg efter indhold i eDiscovery (Standard)](search-for-content-in-core-ediscovery.md)
- [Opret en kladdesamling i eDiscovery (Premium)](create-draft-collection.md)

> [!NOTE]
> eDiscovery-søgninger i overholdelsesportalen og de tilsvarende **\*-ComplianceSearch-cmdlet'er** i Security & Compliance PowerShell bruger KQL (Keyword Query Language). Du kan finde flere detaljerede oplysninger under [Reference til nøgleordsforespørgselssprog](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

## <a name="searchable-email-properties"></a>Egenskaber for mail, der kan søges i

I følgende tabel vises de egenskaber for mailmeddelelser, der kan søges i ved hjælp af eDiscovery-søgeværktøjerne på overholdelsesportalen eller ved hjælp af **New-ComplianceSearch** eller **Set-ComplianceSearch-cmdlet'en** . Tabellen indeholder et eksempel på syntaksen  _property:value_ for hver egenskab og en beskrivelse af de søgeresultater, der returneres af eksemplerne. Du kan skrive disse  `property:value` par i nøgleordsfeltet for en eDiscovery-søgning.

> [!NOTE]
> Når du søger efter mailegenskaber, er det ikke muligt at søge efter elementer, hvor den angivne egenskab er tom eller tom. Hvis du f.eks. bruger *emneparret property:value***:""** til at søge efter mails med en tom emnelinje, returneres der nul resultater. Dette gælder også, når du søger efter egenskaber for websteder og kontakter.

|Ejendom|Beskrivelse af egenskab|Eksempler|Søgeresultater, der returneres af eksemplerne|
|---|---|---|---|
|Navn på vedhæftet fil|Navnene på de filer, der er knyttet til en mail.|`attachmentnames:annualreport.ppt` <p> `attachmentnames:annual*` <br/> `attachmentnames:.pptx`|Meddelelser, der har en vedhæftet fil med navnet annualreport.ppt. I det andet eksempel returnerer brugen af jokertegnet ( * ) meddelelser med ordet "årlig" i filnavnet på en vedhæftet fil. I det tredje eksempel returneres alle vedhæftede filer med filtypenavnet pptx.|
|Bcc|Feltet Bcc i en mail. <sup>1</sup>|`bcc:pilarp@contoso.com` <p> `bcc:pilarp` <p> `bcc:"Pilar Pinilla"`|Alle eksempler returnerer meddelelser med Pilar Pinilla, som er inkluderet i feltet Bcc.<br>([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|Kategori|De kategorier, der skal søges i. Kategorier kan defineres af brugere ved hjælp af Outlook eller Outlook på internettet (tidligere kaldet Outlook Web App). De mulige værdier er: <ul><li>Blå<li>Grøn<li>Orange<li>Lilla<li>Rød<li>Gul</li></ul>|`category:"Red Category"`|Meddelelser, der er tildelt den røde kategori i kildepostkasserne.|
|Cc|Feltet Cc i en mail. <sup>1</sup>|`cc:pilarp@contoso.com` <p> `cc:"Pilar Pinilla"`|I begge eksempler er meddelelser med Pilar Pinilla angivet i feltet Cc.<br>([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|Mappe-id|Mappe-id'et (GUID) for en bestemt postkassemappe. Hvis du bruger denne egenskab, skal du sørge for at søge i den postkasse, som den angivne mappe er placeret i. Der søges kun i den angivne mappe. Der søges ikke i nogen undermapper i mappen. Hvis du vil søge i undermapper, skal du bruge egenskaben Folderid for den undermappe, du vil søge i. <p> Du kan finde flere oplysninger om søgning efter egenskaben Folderid og brug af et script til at hente mappe-id'erne for en bestemt postkasse under [Brug indholdssøgning til målrettede samlinger](use-content-search-for-targeted-collections.md).|`folderid:4D6DD7F943C29041A65787E30F02AD1F00000000013A0000` <p> `folderid:2370FB455F82FC44BE31397F47B632A70000000001160000 AND participants:garthf@contoso.com`|I det første eksempel returneres alle elementer i den angivne postkassemappe. I det andet eksempel returneres alle elementer i den angivne postkassemappe, der blev sendt eller modtaget af garthf@contoso.com.|
|Fra|Afsenderen af en mail. <sup>1</sup>|`from:pilarp@contoso.com` <p> `from:contoso.com`|Meddelelser, der er sendt af den angivne bruger eller sendt fra et angivet domæne.<br>([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|HasAttachment|Angiver, om en meddelelse har en vedhæftet fil. Brug værdierne **true** eller **false**.|`from:pilar@contoso.com AND hasattachment:true`|Meddelelser, der er sendt af den angivne bruger, og som har vedhæftede filer.|
|Betydning|Vigtigheden af en mail, som en afsender kan angive, når der sendes en meddelelse. Meddelelser sendes som standard med normal prioritet, medmindre afsenderen angiver prioriteten som **høj** eller **lav**.|`importance:high` <p> `importance:medium` <p> `importance:low`|Meddelelser, der er markeret som høj prioritet, mellem prioritet eller lav prioritet.|
|Er læst|Angiver, om meddelelser er blevet læst. Brug værdierne **true** eller **false**.|`isread:true` <p> `isread:false`|I det første eksempel returneres meddelelser, hvor egenskaben IsRead er angivet til **Sand**. I det andet eksempel returneres meddelelser, hvor egenskaben IsRead er angivet til **Falsk**.|
|ItemClass|Brug denne egenskab til at søge efter bestemte tredjepartsdatatyper, som din organisation har importeret til Office 365. Brug følgende syntaks til denne egenskab:  `itemclass:ipm.externaldata.<third-party data type>*`|`itemclass:ipm.externaldata.Facebook* AND subject:contoso` <p> `itemclass:ipm.externaldata.Twitter* AND from:"Ann Beebe" AND "Northwind Traders"`|I det første eksempel returneres Facebook-elementer, der indeholder ordet "contoso" i egenskaben Subject. I det andet eksempel returneres Twitter-elementer, der er postet af Ann Beebe, og som indeholder nøgleordsudtrykket "Northwind Traders". <p> Du kan finde en komplet liste over værdier, der skal bruges til tredjepartsdatatyper for egenskaben ItemClass, under [Brug indholdssøgning til at søge efter tredjepartsdata, der blev importeret til Office 365](use-content-search-to-search-third-party-data-that-was-imported.md).|
|Form|Den type mail, der skal søges efter. Mulige værdier: <p>  Kontakter <p>  Docs <p>  E-mail <p>  eksterne data <p>  Faxer <p>  Im <p>  Tidsskrifter <p>  Møder <p>  microsoftteams (returnerer elementer fra chats, møder og opkald i Microsoft Teams) <p>  Noter <p>  Indlæg <p>  rssfeeds <p>  Opgaver <p>  Voicemail|`kind:email` <p> `kind:email OR kind:im OR kind:voicemail` <p> `kind:externaldata`|Det første eksempel returnerer mails, der opfylder søgekriterierne. I det andet eksempel returneres mails, chatsamtaler (herunder Skype for Business samtaler og chats i Microsoft Teams) og talebeskeder, der opfylder søgekriterierne. I det tredje eksempel returneres elementer, der er importeret til postkasser i Microsoft 365, fra datakilder fra tredjepart, f.eks. Twitter, Facebook og Cisco Jabber, som opfylder søgekriterierne. Du kan få flere oplysninger under [Arkivering af tredjepartsdata i Office 365](https://www.microsoft.com/?ref=go).|
|Deltagere|Alle personfelterne i en mail. Disse felter er Fra, Til, Cc og Bcc.1<sup></sup>|`participants:garthf@contoso.com` <p> `participants:contoso.com`|Meddelelser, der er sendt af eller sendt til garthf@contoso.com. I det andet eksempel returneres alle meddelelser, der er sendt af eller sendt til en bruger i contoso.com domæne.<br>([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|Modtaget|Den dato, hvor en mail blev modtaget af en modtager.|`received:2021-04-15` <p> `received>=2021-01-01 AND received<=2021-03-31`|Meddelelser, der blev modtaget den 15. april 2021. I det andet eksempel returneres alle meddelelser, der er modtaget mellem den 1. januar 2021 og den 31. marts 2021.|
|Modtagere|Alle modtagerfelter i en mail. Disse felter er Til, Cc og Bcc.1<sup></sup>|`recipients:garthf@contoso.com` <p> `recipients:contoso.com`|Meddelelser, der er sendt til garthf@contoso.com. I det andet eksempel returneres meddelelser, der er sendt til en hvilken som helst modtager i contoso.com domæne.<br>([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|Sendt|Den dato, hvor en mail blev sendt af afsenderen.|`sent:2021-07-01` <p> `sent>=2021-06-01 AND sent<=2021-07-01`|Meddelelser, der blev sendt på den angivne dato eller sendt inden for det angivne datointerval.|
|Størrelse|Størrelsen på et element i byte.|`size>26214400` <p> `size:1..1048567`|Meddelelser, der er større end 25 MB. I det andet eksempel returneres meddelelser fra 1 til og med 1.048.567 byte (1 MB) i størrelse.|
|Emne|Teksten i emnelinjen i en mail. <p> **Bemærk:** Når du bruger egenskaben Subject i en forespørgsel, returnerer søgningen alle meddelelser, hvor emnelinjen indeholder den tekst, du søger efter. Med andre ord returnerer forespørgslen ikke kun de meddelelser, der har et nøjagtigt match. Hvis du f.eks. søger efter  `subject:"Quarterly Financials"`, indeholder dine resultater meddelelser med emnet "Quarterly Financials 2018".|`subject:"Quarterly Financials"` <p> `subject:northwind`|Meddelelser, der indeholder udtrykket "Quarterly Financials" et vilkårligt sted i emnelinjen. I det andet eksempel returneres alle meddelelser, der indeholder ordet northwind på emnelinjen.|
|Til|Feltet Til i en mail. <sup>1</sup>|`to:annb@contoso.com` <p> `to:annb ` <br/> `to:"Ann Beebe"`|Alle eksempler returnerer meddelelser, hvor Ann Beebe er angivet på linjen Til: .|

> [!NOTE]
> <sup>1</sup> Til værdien af en modtageregenskab kan du bruge mailadresse (også kaldet *brugerens hovednavn* eller UPN), vist navn eller alias til at angive en bruger. Du kan f.eks. bruge annb@contoso.com, annb eller "Ann Beebe" til at angive brugeren Ann Beebe.

### <a name="recipient-expansion"></a>Modtagerudvidelse

Når du søger i en af modtageregenskaberne (Fra, Til, Cc, Bcc, Deltagere og Modtagere), forsøger Microsoft 365 at udvide hver brugers identitet ved at slå dem op i Azure Active Directory (Azure AD).  Hvis brugeren findes i Azure AD, udvides forespørgslen til at omfatte brugerens mailadresse (eller UPN), alias, vist navn og LegacyExchangeDN. En forespørgsel, f.eks `participants:ronnie@contoso.com` . udvides f.eks. til `participants:ronnie@contoso.com OR participants:ronnie OR participants:"Ronald Nelson" OR participants:"<LegacyExchangeDN>"`.

Hvis du vil forhindre modtagerudvidelse, skal du tilføje et jokertegn (stjerne) til slutningen af mailadressen og bruge et reduceret domænenavn. Sørg f.eks. `participants:"ronnie@contoso*"` for at omgive mailadressen med dobbelte anførselstegn.

Vær dog opmærksom på, at hvis du forhindrer modtagerudvidelse i søgeforespørgslen, kan det medføre, at relevante elementer ikke returneres i søgeresultaterne. Mails i Exchange kan gemmes med forskellige tekstformater i modtagerfelterne. Modtagerens udvidelse er beregnet til at afhjælpe dette ved at returnere meddelelser, der kan indeholde forskellige tekstformater. Derfor kan det medføre, at søgeforespørgslen ikke returnerer alle elementer, der kan være relevante for din undersøgelse.

> [!NOTE]
> Hvis du har brug for at gennemse eller reducere de elementer, der returneres af en søgeforespørgsel på grund af modtagerens udvidelse, kan du overveje at bruge eDiscovery (Premium). Du kan søge efter meddelelser (udnytte modtagerudvidelsen), føje dem til et korrektursæt og derefter bruge forespørgsler eller filtre for korrektursæt til at gennemse eller indsnævre resultaterne. Du kan finde flere oplysninger under [Indsaml data for en sag](collecting-data-for-ediscovery.md) og [Forespørg om dataene i et korrektursæt](review-set-search.md).

## <a name="searchable-site-properties"></a>Egenskaber for websted, der kan søges i

I følgende tabel vises nogle af de SharePoint- og OneDrive for Business-egenskaber, der kan søges i ved hjælp af eDiscovery-søgeværktøjerne i Microsoft Purview-compliance-portal eller ved hjælp af **New-ComplianceSearch** eller **Set-ComplianceSearch-cmdlet'en**. Tabellen indeholder et eksempel på syntaksen  _property:value_ for hver egenskab og en beskrivelse af de søgeresultater, der returneres af eksemplerne.

Du kan finde en komplet liste over SharePoint-egenskaber, der kan søges [i, under Oversigt over gennemsøgte og administrerede egenskaber i SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Der kan søges i egenskaber, der er markeret med **Ja** i kolonnen **Forespørgselstabel** .

|Ejendom|Beskrivelse af egenskab|Eksempel|Søgeresultater, der returneres af eksemplerne|
|---|---|---|---|
|Forfatter|Forfatterfeltet fra Office-dokumenter, som bevares, hvis et dokument kopieres. Hvis en bruger f.eks. opretter et dokument og sender mails med det til en anden, der derefter uploader det til SharePoint, bevarer dokumentet stadig den oprindelige forfatter. Sørg for at bruge brugerens viste navn til denne egenskab.|`author:"Garth Fort"`|Alle dokumenter, der er oprettet af Garth Fort.|
|Contenttype|SharePoint-indholdstypen for et element, f.eks. element, dokument eller video.|`contenttype:document`|Alle dokumenter returneres.|
|Lavet|Den dato, hvor et element oprettes.|`created>=2021-06-01`|Alle elementer, der er oprettet den 1. juni 2021 eller efter den 1. juni 2021.|
|Oprettet af|Den person, der har oprettet eller uploadet et element. Sørg for at bruge brugerens viste navn til denne egenskab.|`createdby:"Garth Fort"`|Alle elementer, der er oprettet eller uploadet af Garth Fort.|
|DetectedLanguage|Sproget for et element.|`detectedlanguage:english`|Alle elementer på engelsk.|
|Dokumentlink|Stien (URL-adressen) til en bestemt mappe på et SharePoint- eller OneDrive for Business websted. Hvis du bruger denne egenskab, skal du sørge for at søge på det websted, hvor den angivne mappe er placeret. <p> Hvis du vil returnere elementer, der er placeret i undermapper til den mappe, du angiver for egenskaben documentlink, skal du føje /\* til URL-adressen til den angivne mappe, f.eks. `documentlink: "https://contoso.sharepoint.com/Shared Documents/*"` <p> <br/>Du kan finde flere oplysninger om at søge efter egenskaben documentlink og bruge et script til at hente DOKUMENTlink-URL-adresserne til mapper på et bestemt websted under [Brug indholdssøgning til målrettede samlinger](use-content-search-for-targeted-collections.md).|`documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Private"` <p> `documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Shared with Everyone/*" AND filename:confidential`|I det første eksempel returneres alle elementer i den angivne OneDrive for Business mappe. I det andet eksempel returneres dokumenter i den angivne webstedsmappe (og alle undermapper), der indeholder ordet "fortroligt" i filnavnet.|
|Filudvidelse|Filtypenavnet for en fil. f.eks. docx, one, pptx eller xlsx.|`fileextension:xlsx`|Alle Excel-filer (Excel 2007 og nyere)|
|Filnavn|Navnet på en fil.|`filename:"marketing plan"` <p> `filename:estimate`|Det første eksempel returnerer filer med det nøjagtige udtryk "marketingplan" i titlen. I det andet eksempel returneres filer med ordet "estimat" i filnavnet.|
|LastModifiedTime|Den dato, hvor et element sidst blev ændret.|`lastmodifiedtime>=2021-05-01` <p> `lastmodifiedtime>=2021-05-01 AND lastmodifiedtime<=2021-06-01`|I det første eksempel returneres elementer, der blev ændret den 1. maj 2021 eller efter den 1. maj 2021. I det andet eksempel returneres elementer, der er ændret mellem den 1. maj 2021 og den 1. juni 2021.|
|Ændret af|Den person, der senest har ændret et element. Sørg for at bruge brugerens viste navn til denne egenskab.|`modifiedby:"Garth Fort"`|Alle elementer, der senest blev ændret af Garth Fort.|
|Sti|Stien (URL-adressen) til et bestemt websted på et SharePoint- eller OneDrive for Business websted. <p> Hvis du kun vil returnere elementer fra det angivne websted, skal du føje det efterfølgende `/` til slutningen af URL-adressen, f.eks. `path: "https://contoso.sharepoint.com/sites/international/"` <p> Hvis du vil returnere elementer, der er placeret i mapper på det websted, du angiver i stiegenskaben, skal du føje `/*` til slutningen af URL-adressen, f.eks.  `path: "https://contoso.sharepoint.com/Shared Documents/*"` <p> **Bemærk:** Hvis du bruger egenskaben `Path` til at søge efter OneDrive-placeringer, returneres mediefiler, f.eks. .png, .tiff- eller .wav-filer, ikke i søgeresultaterne. Brug en anden webstedsegenskab i søgeforespørgslen til at søge efter mediefiler i OneDrive-mapper. <br/>|`path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/"` <p> `path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/*" AND filename:confidential`|I det første eksempel returneres alle elementer på det angivne OneDrive for Business websted. I det andet eksempel returneres dokumenter på det angivne websted (og mapper på webstedet), der indeholder ordet "fortroligt" i filnavnet.|
|SharedWithUsersOWSUser|Dokumenter, der er blevet delt med den angivne bruger og vist på siden **Delt med mig** på brugerens OneDrive for Business websted. Dette er dokumenter, der udtrykkeligt er blevet delt med den angivne bruger af andre personer i organisationen. Når du eksporterer dokumenter, der svarer til en søgeforespørgsel, der bruger egenskaben SharedWithUsersOWSUser, eksporteres dokumenterne fra den oprindelige indholdsplacering for den person, der delte dokumentet med den angivne bruger. Du kan finde flere oplysninger under [Søgning efter webstedsindhold, der deles i din organisation](#searching-for-site-content-shared-within-your-organization).|`sharedwithusersowsuser:garthf` <p> `sharedwithusersowsuser:"garthf@contoso.com"`|Begge eksempler returnerer alle interne dokumenter, der udtrykkeligt er blevet delt med Garth Fort, og som vises på siden **Delt med mig** på Garth Forts OneDrive for Business-konto.|
|Websted|URL-adressen på et websted eller en gruppe af websteder i din organisation.|`site:"https://contoso-my.sharepoint.com"` <p> `site:"https://contoso.sharepoint.com/sites/teams"`|I det første eksempel returneres elementer fra de OneDrive for Business websteder for alle brugere i organisationen. I det andet eksempel returneres elementer fra alle teamwebsteder.|
|Størrelse|Størrelsen på et element i byte.|`size>=1` <p> `size:1..10000`|I det første eksempel returneres elementer, der er større end 1 byte. I det andet eksempel returneres elementer fra 1 til og med 10.000 byte.|
|Titel|Dokumentets titel. Egenskaben Title er metadata, der er angivet i Microsoft Office-dokumenter. Det er forskelligt fra dokumentets filnavn.|`title:"communication plan"`|Alle dokumenter, der indeholder udtrykket "kommunikationsplan" i egenskaben Title metadata for et Office-dokument.|

## <a name="searchable-contact-properties"></a>Egenskaber for kontakt, der kan søges i

I følgende tabel vises de egenskaber for kontakter, der er indekseret, og som du kan søge efter ved hjælp af eDiscovery-søgeværktøjer. Dette er de egenskaber, som brugerne kan konfigurere for de kontakter (også kaldet personlige kontakter), der er placeret i det personlige adressekartotek i en brugers postkasse. Hvis du vil søge efter kontakter, kan du vælge de postkasser, der skal søges i, og derefter bruge en eller flere kontaktegenskaber i nøgleordsforespørgslen.

> [!TIP]
> Hvis du vil søge efter værdier, der indeholder mellemrum eller specialtegn, skal du bruge dobbelte anførselstegn (" ") til at indeholde udtrykket. f.eks. `businessaddress:"123 Main Street"`.

|Ejendom|Beskrivelse af egenskab|
|---|---|
|Adresse (arbejde)|Adressen i egenskaben **Forretningsadresse** . Egenskaben kaldes **også arbejdsadressen** på siden med kontaktegenskaber.|
|Telefon (arbejde)|Telefonnummeret i en af egenskaberne for **firmatelefonnummeret** .|
|Firmanavn|Navnet i egenskaben **Firma** .|
|Institut|Navnet i egenskaben **Afdeling** .|
|Displayname|Kontaktens viste navn. Dette er navnet i egenskaben **Full Name** for kontakten.|
|Emailaddress|Adressen på en hvilken som helst mailadresseegenskab for kontakten. Brugerne kan tilføje flere mailadresser for en kontakt. Hvis du bruger denne egenskab, returneres kontakter, der svarer til en af kontaktens mailadresser.|
|Filer som|Egenskaben **Fil som** . Denne egenskab bruges til at angive, hvordan kontakten vises på brugerens liste over kontakter. En kontakt kan f.eks. være angivet som  *Fornavn,Efternavn*  eller  *Efternavn,Fornavn*.|
|Givet navn|Navnet i egenskaben **Fornavn** .|
|HomeAddress|Adressen i en af egenskaberne **for hjemmeadressen** .|
|Telefon (privat)|Telefonnummeret i en af egenskaberne for **hjemmetelefonnummeret** .|
|Chatadresse|Egenskaben chatadresse, som typisk er en mailadresse, der bruges til chat.|
|MiddleName|Navnet i egenskaben **Mellemnavn** .|
|Mobiltelefon|Telefonnummeret i egenskaben **Mobiltelefonnummer** .|
|Brugernavn|Navnet i egenskaben **Kaldenavn** .|
|OfficeLocation|Værdien **i office** - eller **Office-placeringsegenskaben** .|
|Andre adresser|Værdien for egenskaben **Anden** adresse.|
|Efternavn|Navnet i egenskaben **Efternavn** .|
|Titel|Titlen i egenskaben **Stillingsbetegnelse** .|

## <a name="searchable-sensitive-data-types"></a>Følsomme datatyper, der kan søges i

Du kan bruge eDiscovery-søgeværktøjer på overholdelsesportalen til at søge efter følsomme data, f.eks. kreditkortnumre eller cpr-numre, der er gemt i dokumenter på SharePoint og OneDrive for Business websteder. Det kan du gøre ved hjælp af egenskaben `SensitiveType` og navnet (eller id'et) for en følsom oplysningstype i en nøgleordsforespørgsel. Forespørgslen `SensitiveType:"Credit Card Number"` returnerer f.eks. dokumenter, der indeholder et kreditkortnummer. Forespørgslen  `SensitiveType:"U.S. Social Security Number (SSN)"` returnerer dokumenter, der indeholder et AMERIKANSK CPR-nummer.

Hvis du vil se en liste over de følsomme oplysningstyper, du kan søge efter, skal du gå til **Dataklassificeringer** \> **Følsomme infotyper** på overholdelsesportalen. Du kan også bruge cmdlet'en **Get-DlpSensitiveInformationType** i PowerShell til sikkerhed & overholdelse til at få vist en liste over følsomme oplysningstyper.

Du kan finde flere oplysninger om oprettelse af forespørgsler ved hjælp af egenskaben `SensitiveType` under [Formularér en forespørgsel for at finde følsomme data, der er gemt på websteder](form-a-query-to-find-sensitive-data-stored-on-sites.md).

### <a name="limitations-for-searching-sensitive-data-types"></a>Begrænsninger for søgning i følsomme datatyper

- Hvis du vil søge efter brugerdefinerede følsomme oplysningstyper, skal du angive id'et for typen af følsomme oplysninger i `SensitiveType` egenskaben. Hvis du bruger navnet på en brugerdefineret type følsomme oplysninger (som vist i eksemplet for indbyggede følsomme oplysningstyper i det forrige afsnit), returneres der ingen resultater. Brug kolonnen **Publisher** på siden **Følsomme infotyper** i Overholdelsescenter (eller egenskaben **Publisher** i PowerShell) til at skelne mellem indbyggede og brugerdefinerede typer følsomme oplysninger. Indbyggede følsomme datatyper har værdien `Microsoft Corporation` for egenskaben **Publisher** .

  Hvis du vil have vist navnet og id'et for de brugerdefinerede følsomme datatyper i din organisation, skal du køre følgende kommando i Security & Compliance PowerShell:

  ```powershell
  Get-DlpSensitiveInformationType | Where-Object {$_.Publisher -ne "Microsoft Corporation"} | FT Name,Id
  ```

  Derefter kan du bruge id'et i søgeegenskaben `SensitiveType` til at returnere dokumenter, der indeholder den brugerdefinerede følsomme datatype, f.eks. `SensitiveType:7e13277e-6b04-3b68-94ed-1aeb9d47de37`

- Du kan ikke bruge følsomme oplysningstyper og søgeegenskaben `SensitiveType` til at søge efter inaktive følsomme data i Exchange Online postkasser. Dette omfatter 1:1 chatbeskeder, 1:N gruppechatbeskeder og teamkanalsamtaler i Microsoft Teams, fordi alt dette indhold er gemt i postkasser. Du kan dog bruge DLP-politikker (forebyggelse af datatab) til at beskytte følsomme maildata under overførsel. Du kan finde flere oplysninger under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md) og [Søg efter og find personlige data](/compliance/regulatory/gdpr).

## <a name="search-operators"></a>Søgeoperatorer

Booleske søgeoperatorer, f.eks **. AND**, **OR** og **NOT**, hjælper dig med at definere mere præcise søgninger ved at inkludere eller udelade bestemte ord i søgeforespørgslen. Andre teknikker, f.eks. brug af egenskabsoperatorer (f.eks `>=` . eller `..`), anførselstegn, parenteser og jokertegn, hjælper dig med at tilpasse en søgeforespørgsel. I følgende tabel vises de operatorer, du kan bruge til at indsnævre eller udvide søgeresultater.

|Operatør|Brug|Beskrivelse|
|---|---|---|
|OG|keyword1 AND keyword2|Returnerer elementer, der indeholder alle de angivne nøgleord eller  `property:value` udtryk. Returnerer f.eks. alle meddelelser,  `from:"Ann Beebe" AND subject:northwind` der er sendt af Ann Beebe, og som indeholdt ordet northwind på emnelinjen. <sup>2</sup>|
|+|keyword1 + keyword2 + keyword3|Returnerer elementer, der indeholder  *enten*  `keyword2` eller  `keyword3` *, og*  som også indeholder  `keyword1`. Derfor svarer dette eksempel til forespørgslen  `(keyword2 OR keyword3) AND keyword1`. <p> Forespørgslen  `keyword1 + keyword2` (med et mellemrum efter symbolet **+** ) er ikke den samme som at bruge operatoren **AND** . Denne forespørgsel svarer til  `"keyword1 + keyword2"` og returnerer elementer med den nøjagtige fase  `"keyword1 + keyword2"`.|
|ELLER|keyword1 OR keyword2|Returnerer elementer, der indeholder et eller flere af de angivne nøgleord eller  `property:value` udtryk. <sup>2</sup>|
|IKKE|keyword1 NOT keyword2 <p> IKKE fra:"Ann Beebe" <p> NOT kind:im|Udelader elementer, der er angivet af et nøgleord eller et  `property:value` udtryk. I det andet eksempel udelades meddelelser, der er sendt af Ann Beebe. I det tredje eksempel udelades chatsamtaler, f.eks. Skype for Business samtaler, der er gemt i postkassen Samtaleoversigt. <sup>2</sup>|
|-|keyword1 -keyword2|Det samme som **NOT-operatoren** . Denne forespørgsel returnerer derfor elementer, der indeholder  `keyword1` og udelader elementer, der indeholder  `keyword2`.|
|NÆR|keyword1 NEAR(n) keyword2|Returnerer elementer med ord, der er tæt på hinanden, hvor n er lig med antallet af ord fra hinanden. Returnerer f.eks. et element, `best NEAR(5) worst` hvor ordet "værste" er inden for fem ord med "bedst". Hvis der ikke er angivet et tal, er standardafstanden otte ord. <sup>2</sup>|
|:|property:value|Kolon (:) i syntaksen  `property:value` angiver, at værdien af den egenskab, der søges efter, indeholder den angivne værdi. Returnerer f.eks. alle meddelelser,  `recipients:garthf@contoso.com` der er sendt til garthf@contoso.com.|
|=|property=value|Det samme som operatoren **:** .|
|\<|egenskabsværdi\<|Angiver, at den egenskab, der søges efter, er mindre end den angivne værdi. <sup>1</sup>|
|\>|egenskabsværdi\>|Angiver, at den egenskab, der søges efter, er større end den angivne værdi. <sup>1</sup>|
|\<=|property\<=value|Angiver, at den egenskab, der søges efter, er mindre end eller lig med en bestemt værdi. <sup>1</sup>|
|\>=|property\>=value|Angiver, at den egenskab, der søges efter, er større end eller lig med en bestemt værdi. <sup>1</sup>|
|..|property:value1.. value2|Angiver, at den egenskab, der søges efter, er større end eller lig med value1 og mindre end eller lig med value2. <sup>1</sup>|
|"  "|"dagsværdi" <p> subject:"Quarterly Financials"|I en nøgleordsforespørgsel (hvor du skriver parret `property:value` i feltet **Nøgleord** ), skal du bruge dobbelte anførselstegn (" ") til at søge efter et præcist udtryk eller ord. Men hvis du bruger [søgebetingelsen](#search-conditions) **Emne** eller **Emne/Titel**, skal du ikke føje dobbelte anførselstegn til værdien, fordi anførselstegn tilføjes automatisk, når disse søgebetingelser bruges. Hvis du føjer anførselstegn til værdien, føjes der to par dobbelte anførselstegn til betingelsesværdien, og søgeforespørgslen returnerer en fejl. |
|\*|Kat\* <p> emne:sæt\*|Præfikssøgninger (også kaldet *matchning af præfiks*), hvor et jokertegn ( * ) er placeret i slutningen af et ord i nøgleord eller `property:value` forespørgsler. I præfikssøgninger returnerer søgningen resultater med ord, der indeholder ordet efterfulgt af nul eller flere tegn. Returnerer f.eks. dokumenter, `title:set*` der indeholder ordet "set", "setup" og "setting" (og andre ord, der starter med "set") i dokumenttitlen. <p> **Bemærk:** Du kan kun bruge præfikssøgninger. for eksempel **cat\**_ eller _* set\**_. Suffikssøgninger (_*\*cat**), infix-søgninger (**c\*t**) og understrengssøgninger (**\*cat\***) understøttes ikke. <p> Tilføjelse af et punktum ( \. ) til en præfikssøgning, ændres de resultater, der returneres. Det skyldes, at en periode behandles som et stopord. Hvis du f.eks. søger efter **cat\**_ og søger efter _* cat,\*** returneres der forskellige resultater. Vi anbefaler, at du ikke bruger et punktum i en præfikssøgning.|
|(  )|(fair ELLER gratis) AND (from:contoso.com) <p> (IPO ELLER indledende) AND (aktier eller aktier) <p> (kvartalsvis finans)|Parenteser grupperer booleske udtryk,  `property:value` elementer og nøgleord. Returnerer f.eks. varer,  `(quarterly financials)` der indeholder ordene kvartalsvis og økonomisk.|

> [!NOTE]
> <sup>1</sup> Brug denne operator til egenskaber, der har datoværdier eller numeriske værdier.<br/> <sup>2</sup> Booleske søgeoperatorer skal være store. for eksempel **AND**. Hvis du bruger en operator med små bogstaver, f.eks. **og** , behandles den som et nøgleord i søgeforespørgslen.

## <a name="search-conditions"></a>Søgebetingelser

Du kan føje betingelser til en søgeforespørgsel for at indsnævre en søgning og returnere et mere raffineret sæt resultater. Hver betingelse føjer en delsætning til den KQL-søgeforespørgsel, der oprettes og køres, når du starter søgningen.

[Betingelser for almindelige egenskaber](#conditions-for-common-properties)

[Betingelser for mailegenskaber](#conditions-for-mail-properties)

[Betingelser for dokumentegenskaber](#conditions-for-document-properties)

[Operatorer, der bruges sammen med betingelser](#operators-used-with-conditions)

[Retningslinjer for brug af betingelser](#guidelines-for-using-conditions)

[Eksempler på brug af betingelser i søgeforespørgsler](#examples-of-using-conditions-in-search-queries)

### <a name="conditions-for-common-properties"></a>Betingelser for almindelige egenskaber

Opret en betingelse ved hjælp af almindelige egenskaber, når du søger i postkasser og websteder i samme søgning. I følgende tabel vises de tilgængelige egenskaber, der skal bruges, når du tilføjer en betingelse.

|Betingelse|Beskrivelse|
|---|---|
|Dato|For mail den dato, hvor en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter den dato, hvor et dokument sidst blev ændret.|
|Afsender/forfatter|Den person, der sendte en meddelelse i forbindelse med en mail. For dokumenter: den person, der er nævnt i forfatterfeltet, fra Office-dokumenter. Du kan skrive mere end ét navn adskilt af kommaer. To eller flere værdier er logisk forbundet af operatoren **OR** .<br>([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|Størrelse (i byte)|Størrelsen på elementet (i byte) for både mail og dokumenter.|
|Emne/titel|I forbindelse med mail er teksten i emnelinjen i en meddelelse. Titlen på dokumentet for dokumenter. Som tidligere forklaret er egenskaben Title metadata angivet i Microsoft Office-dokumenter. Du kan skrive navnet på mere end én værdi for emne/titel adskilt af kommaer. To eller flere værdier er logisk forbundet af operatoren **OR** . <p> **Bemærk**! Medtag ikke dobbelte anførselstegn til værdierne for denne betingelse, fordi anførselstegn tilføjes automatisk, når denne søgebetingelse bruges. Hvis du føjer anførselstegn til værdien, føjes der to par dobbelte anførselstegn til betingelsesværdien, og søgeforespørgslen returnerer en fejl.|
|Opbevaringsmærkat|Opbevaringsmærkater for både mail og dokumenter, der kan anvendes automatisk eller manuelt på meddelelser og dokumenter. Opbevaringsmærkater kan bruges til at deklarere poster og hjælpe dig med at administrere datalevetidscyklussen for indhold ved at gennemtvinge regler for opbevaring og sletning, der er angivet af mærkaten. Du kan skrive en del af navnet på opbevaringsmærkaten og bruge et jokertegn eller skrive det komplette navn. Du kan finde flere oplysninger om opbevaringsmærkater under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).|

### <a name="conditions-for-mail-properties"></a>Betingelser for mailegenskaber

Opret en betingelse ved hjælp af postegenskaber, når du søger i postkasser eller offentlige mapper. I følgende tabel vises de mailegenskaber, du kan bruge til en betingelse. Disse egenskaber er en delmængde af de mailegenskaber, der tidligere blev beskrevet. Disse beskrivelser gentages for nemheds skyld.

|Betingelse|Beskrivelse|
|---|---|
|Meddelelsestype|Den meddelelsestype, der skal søges i. Dette er den samme egenskab som mailegenskaben Kind. Mulige værdier: <ul><li>Kontakter</li><li>Docs</li><li>E-mail</li><li>eksterne data</li><li>Fax</li><li>Im</li><li>Tidsskrifter</li><li>Møder</li><li>microsoftteams</li><li>Noter</li><li>Indlæg</li><li>rssfeeds</li><li>Opgaver</li><li>Voicemail</li></ul>|
|Deltagere|Alle personfelterne i en mail. Disse felter er Fra, Til, Cc og Bcc. ([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|Type|Egenskaben meddelelsesklasse for et mailelement. Dette er den samme egenskab som mailegenskaben ItemClass. Det er også en betingelse med flere værdier. Hvis du vil vælge flere meddelelsesklasser, skal du holde **Ctrl nede** og derefter klikke på to eller flere meddelelsesklasser på den rulleliste, du vil føje til betingelsen. Hver meddelelsesklasse, du vælger på listen, forbindes logisk af operatoren **OR** i den tilsvarende søgeforespørgsel. <p> Du kan se en liste over de meddelelsesklasser (og deres tilsvarende meddelelsesklasse-id), der bruges af Exchange, og som du kan vælge på listen **Meddelelsesklasse** , under [Elementtyper og Meddelelsesklasser](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Modtaget|Den dato, hvor en mail blev modtaget af en modtager. Dette er den samme egenskab som egenskaben Modtaget mail.|
|Modtagere|Alle modtagerfelter i en mail. Disse felter er Til, Cc og Bcc. ([Se Modtagerudvidelse](keyword-queries-and-search-conditions.md#recipient-expansion))|
|Afsender|Afsenderen af en mail.|
|Sendt|Den dato, hvor en mail blev sendt af afsenderen. Dette er den samme egenskab som egenskaben Sendt mail.|
|Emne|Teksten i emnelinjen i en mail. <p> **Bemærk**! Medtag ikke dobbelte anførselstegn til værdierne for denne betingelse, fordi anførselstegn tilføjes automatisk, når denne søgebetingelse bruges. Hvis du føjer anførselstegn til værdien, føjes der to par dobbelte anførselstegn til betingelsesværdien, og søgeforespørgslen returnerer en fejl.|
|Til|Modtageren af en mail i feltet Til.|

### <a name="conditions-for-document-properties"></a>Betingelser for dokumentegenskaber

Opret en betingelse ved hjælp af dokumentegenskaber, når du søger efter dokumenter på SharePoint og OneDrive for Business websteder. I følgende tabel vises de dokumentegenskaber, du kan bruge til en betingelse. Disse egenskaber er et undersæt af de webstedsegenskaber, der tidligere er beskrevet. Disse beskrivelser gentages for nemheds skyld.

|Betingelse|Beskrivelse|
|---|---|
|Forfatter|Forfatterfeltet fra Office-dokumenter, som bevares, hvis et dokument kopieres. Hvis en bruger f.eks. opretter et dokument og sender mails med det til en anden, der derefter uploader det til SharePoint, bevarer dokumentet stadig den oprindelige forfatter.|
|Titel|Dokumentets titel. Egenskaben Title er metadata, der er angivet i Office-dokumenter. Den er forskellig fra dokumentets filnavn.|
|Lavet|Den dato, hvor et dokument oprettes.|
|Senest ændret|Den dato, hvor et dokument sidst blev ændret.|
|Filtype|Filtypenavnet for en fil. f.eks. docx, one, pptx eller xlsx. Dette er den samme egenskab som webstedsegenskaben FileExtension. <p> **Bemærk:** Hvis du medtager en betingelse af typen Filtype ved hjælp af operatoren **Equals** eller **Equals** i en søgeforespørgsel, kan du ikke bruge en præfikssøgning (ved at medtage jokertegnet ( \* ) i slutningen af filtypen) til at returnere alle versioner af en filtype. Hvis du gør det, ignoreres jokertegnet. Hvis du f.eks. inkluderer betingelsen `Equals any of doc*`, returneres der kun filer med filtypenavnet `.doc` . Filer med filtypenavnet `.docx` returneres ikke. Hvis du vil returnere alle versioner af en filtype, skal du bruge *egenskab:værdiparret* i en nøgleordsforespørgsel. f.eks. `filetype:doc*`.|

### <a name="operators-used-with-conditions"></a>Operatorer, der bruges sammen med betingelser

Når du tilføjer en betingelse, kan du vælge en operator, der er relevant for typen af egenskab for betingelsen. I følgende tabel beskrives de operatorer, der bruges sammen med betingelser, og viser de tilsvarende operatorer, der bruges i søgeforespørgslen.

|Operatør|Tilsvarende forespørgsel|Beskrivelse|
|---|---|---|
|Efter|`property>date`|Bruges sammen med datobetingelser. Returnerer elementer, der blev sendt, modtaget eller ændret efter den angivne dato.|
|Før|`property<date`|Bruges sammen med datobetingelser. Returnerer elementer, der blev sendt, modtaget eller ændret før den angivne dato.|
|Mellem|`date..date`|Bruges sammen med betingelser for dato og størrelse. Når den bruges sammen med en datobetingelse, returneres elementer, der blev sendt, modtaget eller ændret inden for det angivne datointerval. Når den bruges sammen med en størrelsesbetingelse, returneres elementer, hvis størrelse er inden for det angivne område.|
|Indeholder en hvilken som helst af|`(property:value) OR (property:value)`|Bruges sammen med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der indeholder en del af en eller flere angivne strengværdier.|
|Indeholder ikke nogen af|`-property:value` <p> `NOT property:value`|Bruges sammen med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der ikke indeholder nogen del af den angivne strengværdi.|
|Er ikke lig med nogen af|`-property=value` <p> `NOT property=value`|Bruges sammen med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der ikke indeholder den specifikke streng.|
|Svarer|`size=value`|Returnerer elementer, der er lig med den angivne størrelse. <sup>1</sup>|
|Er lig med en hvilken som helst af|`(property=value) OR (property=value)`|Bruges sammen med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der svarer til en eller flere angivne strengværdier.|
|Større|`size>value`|Returnerer elementer, hvor den angivne egenskab er større end den angivne værdi. <sup>1</sup>|
|Større eller lig med|`size>=value`|Returnerer elementer, hvor den angivne egenskab er større end eller lig med den angivne værdi. <sup>1</sup>|
|Mindre|`size<value`|Returnerer elementer, der er større end eller lig med den specifikke værdi. <sup>1</sup>|
|Mindre eller lig med|`size<=value`|Returnerer elementer, der er større end eller lig med den specifikke værdi. <sup>1</sup>|
|Ikke lig med|`size<>value`|Returnerer elementer, der ikke er lig med den angivne størrelse. <sup>1</sup>|

> [!NOTE]
> <sup>1</sup> Denne operator er kun tilgængelig for betingelser, der bruger egenskaben Size.

### <a name="guidelines-for-using-conditions"></a>Retningslinjer for brug af betingelser

Vær opmærksom på følgende, når du bruger søgebetingelser.

- En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i nøgleordsfeltet) af operatoren **AND** . Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og den betingelse, der skal medtages i resultaterne. Sådan hjælper betingelser med at indsnævre dine resultater.

- Hvis du føjer to eller flere entydige betingelser til en søgeforespørgsel (betingelser, der angiver forskellige egenskaber), er disse betingelser logisk forbundet af OPERATOREN **AND** . Det betyder, at det kun er elementer, der opfylder alle betingelserne (ud over en nøgleordsforespørgsel), der returneres.

- Hvis du tilføjer mere end én betingelse for den samme egenskab, er disse betingelser logisk forbundet af operatoren **OR** . Det betyder, at elementer, der opfylder nøgleordsforespørgslen, og en af betingelserne returneres. Grupper af de samme betingelser er derfor forbundet med hinanden af operatoren **OR** , og derefter forbindes sæt af entydige betingelser af operatoren **AND** .

- Hvis du føjer flere værdier (adskilt af kommaer eller semikolon) til en enkelt betingelse, forbindes disse værdier af operatoren **OR** . Det betyder, at elementer returneres, hvis de indeholder nogen af de angivne værdier for egenskaben i betingelsen.

- Alle betingelser, der bruger en operator med logikken **Contains** og **Equals** , returnerer lignende søgeresultater for simple strengsøgninger. En simpel strengsøgning er en streng i den betingelse, der ikke indeholder et jokertegn). En betingelse, der bruger **Er lig med en af** , returnerer f.eks. de samme elementer som en betingelse, der bruger **Contains of**.

- Den søgeforespørgsel, der oprettes ved hjælp af feltet med nøgleord og betingelser, vises på siden **Søg** i detaljeruden for den valgte søgning. I en forespørgsel angiver alt til højre for notationen  `(c:c)` betingelser, der føjes til forespørgslen.

- Betingelser føjer kun egenskaber til søgeforespørgslen. ikke tilføje operatorer. Det er derfor, at den forespørgsel, der vises i detaljeruden, ikke viser operatorer til højre for notationen  `(c:c)` . KQL tilføjer de logiske operatorer (i henhold til de tidligere forklarede regler), når forespørgslen udføres.

- Du kan bruge træk og slip-kontrolelementet til at genforespørge rækkefølgen af betingelser. Klik på kontrolelementet for en betingelse, og flyt det op eller ned.

- Som tidligere forklaret giver nogle betingelsesegenskaber dig mulighed for at skrive flere værdier (adskilt af semikolon). Hver værdi er logisk forbundet af operatoren **OR** og resulterer i forespørgslen `(filetype=docx) OR (filetype=pptx) OR (filetype=xlsx)`. Følgende illustration viser et eksempel på en betingelse med flere værdier.

    ![Én betingelse med flere værdier.](../media/SearchConditions1.png)

  > [!NOTE]
  > Du kan ikke tilføje flere betingelser (ved at klikke på **Tilføj betingelse** for den samme egenskab. Du skal i stedet angive flere værdier for betingelsen (adskilt af semikolon) som vist i det forrige eksempel.

### <a name="examples-of-using-conditions-in-search-queries"></a>Eksempler på brug af betingelser i søgeforespørgsler

Følgende eksempler viser den GUI-baserede version af en søgeforespørgsel med betingelser, den søgeforespørgselssyntaks, der vises i detaljeruden for den valgte søgning (som også returneres af **Get-ComplianceSearch-cmdlet'en** ) og logikken i den tilsvarende KQL-forespørgsel.

#### <a name="example-1"></a>Eksempel 1

I dette eksempel returneres dokumenter på SharePoint- og OneDrive for Business-websteder, der indeholder et kreditkortnummer, og som senest blev ændret før den 1. januar 2021.

**GUI**:

![Første eksempel på søgebetingelser.](../media/SearchConditions2.png)

**Søgeforespørgselssyntaks**:

`SensitiveType:"Credit Card Number"(c:c)(lastmodifiedtime<2021-01-01)`

**Søgeforespørgselslogik**:

`SensitiveType:"Credit Card Number" AND (lastmodifiedtime<2021-01-01)`

Bemærk på det forrige skærmbillede, at søgebrugergrænsefladen bekræfter, at nøgleordsforespørgslen og -betingelsen er forbundet af operatoren **AND** .

#### <a name="example-2"></a>Eksempel 2

I dette eksempel returneres mailelementer eller dokumenter, der indeholder nøgleordet "rapport", som blev sendt eller oprettet før den 1. april 2021, og som indeholder ordet "northwind" i emnefeltet i mails eller i titelegenskaben for dokumenter. Forespørgslen udelukker websider, der opfylder de andre søgekriterier.

**GUI**:

![Andet eksempel på søgebetingelser.](../media/SearchConditions3.png)

**Søgeforespørgselssyntaks**:

`report(c:c)(date<2021-04-01)(subjecttitle:"northwind")(-filetype:aspx)`

**Søgeforespørgselslogik**:

`report AND (date<2021-04-01) AND (subjecttitle:"northwind") NOT (filetype:aspx)`

#### <a name="example-3"></a>Eksempel 3

I dette eksempel returneres mails eller kalendermøder, der blev sendt mellem den 1. december 2019 og den 30. november 2020, og som indeholder ord, der starter med "telefon" eller "smartphone".

**GUI**:

![Tredje eksempel på søgebetingelser.](../media/SearchConditions4.png)

**Søgeforespørgselssyntaks**:

`phone* OR smartphone*(c:c)(sent=2019-12-01..2020-11-30)(kind="email")(kind="meetings")`

**Søgeforespørgselslogik**:

`phone* OR smartphone* AND (sent=2019-12-01..2020-11-30) AND ((kind="email") OR (kind="meetings"))`

## <a name="special-characters"></a>Specialtegn

Nogle specialtegn er ikke inkluderet i søgeindekset og kan derfor ikke søges i. Dette omfatter også de specialtegn, der repræsenterer søgeoperatorer i søgeforespørgslen. Her er en liste over specialtegn, der enten erstattes af et tomt mellemrum i den faktiske søgeforespørgsel eller forårsager en søgefejl.

`+ - = : ! @ # % ^ & ; _ / ? ( ) [ ] { }`

## <a name="searching-for-site-content-shared-with-external-users"></a>Søger efter webstedsindhold, der er delt med eksterne brugere

Du kan også bruge eDiscovery-søgeværktøjerne i Overholdelsescenter til at søge efter dokumenter, der er gemt på SharePoint, og OneDrive for Business websteder, der er blevet delt med personer uden for din organisation. Dette kan hjælpe dig med at identificere følsomme eller beskyttede oplysninger, der deles uden for din organisation. Det kan du gøre ved hjælp af egenskaben  `ViewableByExternalUsers` i en nøgleordsforespørgsel. Denne egenskab returnerer dokumenter eller websteder, der er blevet delt med eksterne brugere ved hjælp af en af følgende delingsmetoder:

- En invitation til deling, der kræver, at brugerne logger på din organisation som en godkendt bruger.
- Et anonymt gæstelink, som gør det muligt for alle med dette link at få adgang til ressourcen uden at skulle godkendes.

Her er nogle eksempler:

- Forespørgslen  `ViewableByExternalUsers:true AND SensitiveType:"Credit Card Number"` returnerer alle elementer, der er blevet delt med personer uden for din organisation, og indeholder et kreditkortnummer.
- Forespørgslen  `ViewableByExternalUsers:true AND ContentType:document AND site:"https://contoso.sharepoint.com/Sites/Teams"` returnerer en liste over dokumenter på alle teamwebsteder i organisationen, der er blevet delt med eksterne brugere.

> [!TIP]
> En søgeforespørgsel, f.eks  `ViewableByExternalUsers:true AND ContentType:document` . kan returnere en masse .aspx-filer i søgeresultaterne. Hvis du vil fjerne disse (eller andre filtyper), kan du bruge egenskaben  `FileExtension` til at udelade bestemte filtyper, f.eks  `ViewableByExternalUsers:true AND ContentType:document NOT FileExtension:aspx`. .

Hvad betragtes som indhold, der deles med personer uden for din organisation? Dokumenter på din organisations SharePoint- og OneDrive for Business-websteder, der deles ved at sende en invitation til deling, eller som er delt på offentlige placeringer. Følgende brugeraktiviteter resulterer f.eks. i indhold, der kan ses af eksterne brugere:

- En bruger deler en fil eller mappe med en person uden for din organisation.
- En bruger opretter og sender et link til en delt fil til en person uden for organisationen. Dette link gør det muligt for den eksterne bruger at få vist (eller redigere) filen.
- En bruger sender en invitation til deling eller et gæstelink til en person uden for organisationen for at få vist (eller redigere) en delt fil.

### <a name="issues-using-the-viewablebyexternalusers-property"></a>Problemer ved hjælp af egenskaben ViewableByExternalUsers

Selvom egenskaben  `ViewableByExternalUsers` repræsenterer statussen for, om et dokument eller et websted deles med eksterne brugere, er der nogle advarsler om, hvad denne egenskab gør og ikke afspejler. I følgende scenarier opdateres værdien af  `ViewableByExternalUsers` egenskaben ikke, og resultaterne af en søgeforespørgsel, der bruger denne egenskab, kan være unøjagtige.

- Ændringer i delingspolitikken, f.eks. deaktivering af ekstern deling for et websted eller for organisationen. Egenskaben viser stadig tidligere delte dokumenter som værende eksternt tilgængelige, selvom ekstern adgang kan være blevet tilbagekaldt.
- Ændringer af gruppemedlemskab, f.eks. tilføjelse eller fjernelse af eksterne brugere til Microsoft 365-grupper eller Microsoft 365-sikkerhedsgrupper. Egenskaben opdateres ikke automatisk for elementer, som gruppen har adgang til.
- Sender invitationer til deling til eksterne brugere, hvor modtageren ikke har accepteret invitationen, og derfor endnu ikke har adgang til indholdet.

I disse scenarier afspejler egenskaben  `ViewableByExternalUsers` ikke den aktuelle delingsstatus, før webstedet eller dokumentbiblioteket gennemsøges igen og indekseres igen.

## <a name="searching-for-site-content-shared-within-your-organization"></a>Søger efter webstedsindhold, der er delt i din organisation

Som tidligere forklaret kan du bruge egenskaben  `SharedWithUsersOWSUser` , så du kan søge efter dokumenter, der er blevet delt mellem personer i din organisation. Når en person deler en fil (eller mappe) med en anden bruger i din organisation, vises der et link til den delte fil på siden **Delt med mig** på den OneDrive for Business konto for den person, som filen blev delt med. Hvis du f.eks. vil søge efter de dokumenter, der er blevet delt med Sara Davis, kan du bruge forespørgslen  `SharedWithUsersOWSUser:"sarad@contoso.com"`. Hvis du eksporterer resultaterne af denne søgning, downloades de oprindelige dokumenter (placeret på indholdsplaceringen for den person, der delte dokumenterne med Sara).

Dokumenter skal udtrykkeligt deles med en bestemt bruger for at blive returneret i søgeresultater, når egenskaben  `SharedWithUsersOWSUser` bruges. Når en person f.eks. deler et dokument på sin OneDrive-konto, har vedkommende mulighed for at dele det med nogen (i eller uden for organisationen), kun dele det med personer i organisationen eller dele det med en bestemt person. Her er et skærmbillede af vinduet **Del** i OneDrive, der viser de tre delingsindstillinger.

![Det er kun filer, der deles med bestemte personer, der returneres af en søgeforespørgsel, der bruger egenskaben SharedWithUsersOWSUser.](../media/469a4b61-68bd-4ab0-b612-ab6302973886.png)

Det er kun dokumenter, der deles ved hjælp af den tredje indstilling (delt med **bestemte personer**), der returneres af en søgeforespørgsel, der bruger egenskaben  `SharedWithUsersOWSUser` .

## <a name="searching-for-skype-for-business-conversations"></a>Søger efter Skype for Business samtaler

Du kan bruge følgende nøgleordsforespørgsel til specifikt at søge efter indhold i Skype for Business samtaler:

```powershell
kind:im
```

Den forrige søgeforespørgsel returnerer også chats fra Microsoft Teams. For at forhindre dette kan du indsnævre søgeresultaterne, så de kun indeholder Skype for Business samtaler ved hjælp af følgende nøgleordsforespørgsel:

```powershell
kind:im AND subject:conversation
```

Den forrige nøgleordsforespørgsel udelukker chats i Microsoft Teams, fordi Skype for Business samtaler gemmes som mails med en emnelinje, der starter med ordet "Samtale".

Hvis du vil søge efter Skype for Business samtaler, der fandt sted inden for et bestemt datointerval, skal du bruge følgende nøgleordsforespørgsel:

```powershell
kind:im AND subject:conversation AND (received=startdate..enddate)
```

## <a name="character-limits-for-searches"></a>Tegngrænser for søgninger

Der er en grænse på 4.000 tegn for søgeforespørgsler, når du søger efter indhold på SharePoint-websteder og OneDrive-konti.
Sådan beregnes det samlede antal tegn i søgeforespørgslen:

- Tegnene i søgeforespørgslen med nøgleord (herunder både bruger- og filterfelter) tæller i forhold til denne grænse.
- Tegnene i en hvilken som helst placeringsegenskab (f.eks. URL-adresserne for alle SharePoint-websteder eller OneDrive-placeringer, der søges efter) tæller i forhold til denne grænse.
- Tegnene i alle filtre for søgetilladelser, der anvendes på den bruger, der kører søgeantallet i forhold til grænsen.

Du kan finde flere oplysninger om tegngrænser i [eDiscovery-søgegrænser](limits-for-content-search.md#search-limits).

> [!NOTE]
> Grænsen på 4.000 tegn gælder for indholdssøgning, eDiscovery (Standard) og eDiscovery (Premium).

## <a name="search-tips-and-tricks"></a>Tip og tricks til søgning

- Der skelnes ikke mellem store og små bogstaver i søgninger i nøgleord. **Cat** og **CAT** returnerer f.eks. de samme resultater.

- De booleske operatorer **AND**, **OR**, **NOT** og **NEAR** skal være store.

- Et mellemrum mellem to nøgleord eller to  `property:value` udtryk er det samme som at bruge **AND**. Returnerer f.eks. alle meddelelser,  `from:"Sara Davis" subject:reorganization` der er sendt af Sara Davis, og som indeholder ordet omorganisering i emnelinjen.

- Brug syntaks, der svarer til formatet `property:value` . Der skelnes ikke mellem store og små bogstaver i værdier, og de kan ikke have et mellemrum efter operatoren. Hvis der er et mellemrum, vil din tilsigtede værdi være en fuldtekstsøgning. Søger f.eks `to: pilarp` . efter "pilarp" som et nøgleord i stedet for efter meddelelser, der er sendt til pilarp.

- Når du søger i en modtageregenskab, f.eks. Til, Fra, Cc eller Modtagere, kan du bruge en SMTP-adresse, et alias eller et vist navn til at angive en modtager. Du kan f.eks. bruge pilarp@contoso.com, pilarp eller "Pilar Pinilla".

- Du kan kun bruge præfikssøgninger. for eksempel **cat\**_ eller _* set\**_. Suffikssøgninger (_*\*cat**), infix-søgninger (**c\*t**) og understrengssøgninger (**\*cat\***) understøttes ikke.

- Når du søger i en egenskab, skal du bruge dobbelte anførselstegn (" "), hvis søgeværdien består af flere ord. Returnerer f.eks `subject:budget Q1` . meddelelser, der indeholder **budgettet** på emnelinjen, og som indeholder **Q1** hvor som helst i meddelelsen eller i en af meddelelsesegenskaberne. Ved hjælp af `subject:"budget Q1"` returneres alle meddelelser, der indeholder **budgettet Q1** , hvor som helst i emnelinjen.

- Hvis du vil udelade indhold, der er markeret med en bestemt egenskabsværdi, fra dine søgeresultater, skal du placere et minustegn (-) før navnet på egenskaben. Udelukker f.eks. meddelelser, `-from:"Sara Davis"` der er sendt af Sara Davis.

- Du kan eksportere elementer baseret på meddelelsestype. Hvis du f.eks. vil eksportere Skype-samtaler og chats i Microsoft Teams, skal du bruge syntaksen `kind:im`. Hvis du kun vil returnere mails, skal du bruge `kind:email`. Hvis du vil returnere chats, møder og opkald i Microsoft Teams, skal du bruge `kind:microsoftteams`.

- Som tidligere forklaret skal du, når du søger på websteder, føje det efterfølgende `/` til slutningen af URL-adressen, når du bruger egenskaben `path` til kun at returnere elementer på et angivet websted. Hvis du ikke medtager de efterstillede `/`, returneres elementer fra et websted med et lignende stinavn også. Hvis du f.eks. bruger `path:sites/HelloWorld` elementer fra websteder med navnet `sites/HelloWorld_East` eller `sites/HelloWorld_West` også returneres. Hvis du kun vil returnere elementer fra HelloWorld-webstedet, skal du bruge `path:sites/HelloWorld/`.
