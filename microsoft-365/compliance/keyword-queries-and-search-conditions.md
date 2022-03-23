---
title: Nøgleordsforespørgsler og søgebetingelser for eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om mail- og dokumentegenskaber, som du kan søge i ved hjælp af eDiscovery-søgeværktøjerne Microsoft 365.
ms.openlocfilehash: 390d0721dc5b256da224c70573953e23bbb91225
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587682"
---
# <a name="keyword-queries-and-search-conditions-for-ediscovery"></a>Nøgleordsforespørgsler og søgebetingelser for eDiscovery

I denne artikel beskrives de mail- og dokumentegenskaber, du kan søge efter i mailelementer og Microsoft Teams-chatsamtaler i Exchange Online samt dokumenter, der er gemt på SharePoint- og OneDrive for Business-websteder ved hjælp af eDiscovery-søgeværktøjerne i Microsoft 365 Overholdelsescenter. Dette omfatter Indholdssøgning, Kerne eDiscovery og Advanced eDiscovery (eDiscovery-søgninger i Advanced eDiscovery kaldes *samlinger*). Du kan også bruge cmdlet'erne **\*-ComplianceSearch** i Security & Compliance Center PowerShell til at søge efter disse egenskaber. Artiklen beskriver også:

- Brug af booleske søgeoperatorer, søgebetingelser og andre søgeforespørgselsteknikker til at afgrænse dine søgeresultater.
- Søgning efter følsomme datatyper og brugerdefinerede følsomme datatyper i SharePoint og OneDrive for Business.
- Søge efter webstedsindhold, der deles med brugere uden for organisationen

Du kan finde en trinvis vejledning i at oprette forskellige eDiscovery-søgninger i:

- [Indholdssøgning](content-search.md)
- [Søge efter indhold i Core eDiscovery](search-for-content-in-core-ediscovery.md)
- [Opret en kladdesamling i Advanced eDiscovery](create-draft-collection.md)

> [!NOTE]
> eDiscovery-søgninger i Microsoft 365 Overholdelsescenter og de tilsvarende -ComplianceSearch-cmdlet'er i Security & Compliance Center PowerShell bruger KQL (Keyword Query Language).**\*** Du kan finde flere oplysninger i Reference til [syntaks for sprog til nøgleordsforespørgsel](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

## <a name="searchable-email-properties"></a>Søgbare mailegenskaber

I følgende tabel vises egenskaber for mails, der kan søges ved hjælp af eDiscovery-søgeværktøjerne i Microsoft 365 Overholdelsescenter eller ved hjælp af **New-ComplianceSearch** eller **cmdlet'en Set-ComplianceSearch**. Tabellen indeholder et eksempel på syntaksen  _property:value_ for hver egenskab og en beskrivelse af søgeresultaterne, der returneres af eksemplerne. Du kan skrive disse  `property:value` par i nøgleordsfeltet for en eDiscovery-søgning.

> [!NOTE]
> Når du søger efter mailegenskaber, er det ikke muligt at søge efter elementer, hvor den angivne egenskab er tom eller tom. Hvis du f.eks. *bruger egenskab:* værdiparret emne **:""** til at søge efter mails med en tom emnelinje, returneres der nul resultater. Dette gælder også, når du søger efter egenskaber for websted og kontakt.

|Egenskab|Egenskabsbeskrivelse|Eksempler|Søgeresultater, der returneres af eksemplerne|
|---|---|---|---|
|Vedhæftede filerNavne|Navnene på de filer, der er vedhæftet en mail.|`attachmentnames:annualreport.ppt` <p> `attachmentnames:annual*` <br/> `attachmentnames:.pptx`|Meddelelser, der har en vedhæftet fil med navnet annualreport.ppt. I det andet eksempel returneres meddelelser med ordet "årlig" i filnavnet på en vedhæftet fil ved hjælp af jokertegnet ( * ). Det tredje eksempel returnerer alle vedhæftede filer med filtypenavnet pptx.|
|Bcc|Feltet Bcc i en mail. <sup>1</sup>|`bcc:pilarp@contoso.com` <p> `bcc:pilarp` <p> `bcc:"Pilar Pinilla"`|Alle eksempler returnerer meddelelser med Pilar Pinilla inkluderet i feltet Bcc.|
|Kategori|De kategorier, der skal søges i. Kategorier kan defineres af brugere ved hjælp Outlook eller Outlook på internettet (tidligere kaldet Outlook Web App). De mulige værdier er: <ul><li>blå<li>grøn<li>orange<li>lilla<li>rød<li>gul</li></ul>|`category:"Red Category"`|Meddelelser, der har fået tildelt den røde kategori i kildepostkasserne.|
|Cc|Feltet Cc i en mail. <sup>1</sup>|`cc:pilarp@contoso.com` <p> `cc:"Pilar Pinilla"`|I begge eksempler er meddelelser med Pilar Pinilla angivet i feltet Cc.|
|Folderid|Mappe-id'et for en bestemt postkassemappe. Hvis du bruger denne egenskab, skal du sørge for at søge i den postkasse, som den angivne mappe er placeret i. Der søges kun i den angivne mappe. Der søges ikke i undermapper i mappen. Hvis du vil søge i undermapper, skal du bruge egenskaben Folderid for den undermappe, du vil søge i. <p> Du kan finde flere oplysninger om at søge efter egenskaben Folderid og bruge et script til at hente mappe-id'er til en bestemt postkasse i Brug indholdssøgning [til målrettede samlinger](use-content-search-for-targeted-collections.md).|`folderid:4D6DD7F943C29041A65787E30F02AD1F00000000013A0000` <p> `folderid:2370FB455F82FC44BE31397F47B632A70000000001160000 AND participants:garthf@contoso.com`|Det første eksempel returnerer alle elementer i den angivne postkassemappe. Det andet eksempel returnerer alle elementer i den angivne postkassemappe, der blev sendt eller modtaget af garthf@contoso.com.|
|Fra|Afsenderen af en mail. <sup>1</sup>|`from:pilarp@contoso.com` <p> `from:contoso.com`|Meddelelser, der er sendt af den angivne bruger eller sendt fra et bestemt domæne.|
|HasAttachment|Angiver, om en meddelelse har en vedhæftet fil. Brug værdierne sand **eller** **falsk**.|`from:pilar@contoso.com AND hasattachment:true`|Meddelelser, der er sendt af den angivne bruger, der har vedhæftede filer.|
|Prioritet|Vigtigheden af en mail, som en afsender kan angive, når der sendes en meddelelse. Som standard sendes meddelelser med normal prioritet, medmindre afsenderen angiver prioriteten som **høj** eller **lav**.|`importance:high` <p> `importance:medium` <p> `importance:low`|Meddelelser, der er markeret som høj prioritet, mellem prioritet eller lav prioritet.|
|IsRead|Angiver, om meddelelser er blevet læst. Brug værdierne sand **eller** **falsk**.|`isread:true` <p> `isread:false`|Det første eksempel returnerer meddelelser med egenskaben IsRead angivet til **Sand**. Det andet eksempel returnerer meddelelser med egenskaben IsRead angivet til **Falsk**.|
|ItemClass|Brug denne egenskab til at søge efter bestemte tredjepartsdatatyper, som organisationen har importeret til Office 365. Brug følgende syntaks for denne egenskab:  `itemclass:ipm.externaldata.<third-party data type>*`|`itemclass:ipm.externaldata.Facebook* AND subject:contoso` <p> `itemclass:ipm.externaldata.Twitter* AND from:"Ann Beebe" AND "Northwind Traders"`|Det første eksempel returnerer Facebook-elementer, der indeholder ordet "contoso" i egenskaben Emne. I det andet eksempel returneres Twitter-elementer, der blev skrevet af Ann Beebe, og som indeholder nøgleordet "Northwind Traders". <p> Hvis du vil have en komplet liste over værdier, der skal bruges til tredjepartsdatatyper for egenskaben Elementklasse, skal du se Brug indholdssøgning til at søge efter [tredjepartsdata](use-content-search-to-search-third-party-data-that-was-imported.md), der blev importeret til Office 365.|
|Type|Typen af mail, der skal søges efter. Mulige værdier: <p>  kontakter <p>  dokumenter <p>  mail <p>  externaldata <p>  faxer <p>  im <p>  journaler <p>  møder <p>  microsoftteams (returnerer elementer fra chats, møder og opkald i Microsoft Teams) <p>  noter <p>  indlæg <p>  rssfeeds <p>  opgaver <p>  telefonsvarer|`kind:email` <p> `kind:email OR kind:im OR kind:voicemail` <p> `kind:externaldata`|Det første eksempel returnerer mails, der opfylder søgekriterierne. Det andet eksempel returnerer mails, chatsamtaler (herunder Skype for Business og chatsamtaler i Microsoft Teams) og talebeskeder, der opfylder søgekriterierne. Det tredje eksempel returnerer elementer, der er blevet importeret til postkasser i Microsoft 365 fra datakilder fra tredjeparter, f.eks. Twitter, Facebook og Cisco Jabber, der opfylder søgekriterierne. Du kan få mere at [vide under Arkivering af tredjepartsdata Office 365](https://www.microsoft.com/?ref=go).|
|Deltagere|Alle personer-felterne i en mail. Disse felter er Fra, Til, Cc og Bcc.1<sup></sup>|`participants:garthf@contoso.com` <p> `participants:contoso.com`|Meddelelser, der er sendt af eller sendt til garthf@contoso.com. I det andet eksempel returneres alle meddelelser, der er sendt af eller sendt til en bruger i contoso.com domæne.|
|Modtaget|Den dato, hvor en mail blev modtaget af en modtager.|`received:2021-04-15` <p> `received>=2021-01-01 AND received<=2021-03-31`|Meddelelser, der blev modtaget d. 15. april 2021. I det andet eksempel returneres alle meddelelser, der er modtaget mellem 1. januar 2021 og 31. marts 2021.|
|Modtagere|Alle modtagerfelter i en mail. Disse felter er Til, Cc og Bcc.1<sup></sup>|`recipients:garthf@contoso.com` <p> `recipients:contoso.com`|Meddelelser, der sendes garthf@contoso.com. Det andet eksempel returnerer meddelelser, der er sendt til alle modtagere i contoso.com domæne.|
|Sendt|Den dato, hvor afsenderen sendte en mail.|`sent:2021-07-01` <p> `sent>=2021-06-01 AND sent<=2021-07-01`|Meddelelser, der blev sendt på den angivne dato eller sendt inden for det angivne datointerval.|
|Størrelse|Størrelsen på et element i byte.|`size>26214400` <p> `size:1..1048567`|Meddelelser, der er større end 25 MB. I det andet eksempel returneres meddelelser fra 1 til 1.048.567 byte (1 MB) i størrelse.|
|Emne|Teksten i emnelinjen i en mail. <p> **Bemærk!** Når du bruger egenskaben Emne i en forespørgsel, returnerer søgningen alle meddelelser, hvor emnelinjen indeholder den tekst, du søger efter. Med andre ord returnerer forespørgslen ikke kun de meddelelser, der har et nøjagtigt match. Hvis du f.eks. søger efter  `subject:"Quarterly Financials"`, vil dine resultater indeholde meddelelser med emnet "Kvartalsvise økonomiske 2018".|`subject:"Quarterly Financials"` <p> `subject:northwind`|Meddelelser, der indeholder sætningen "Kvartalsvise økonomiske oplysninger" et vilkårligt sted i teksten i emnelinjen. Det andet eksempel returnerer alle meddelelser, der indeholder ordet northwind i emnelinjen.|
|Hvis du vil|Feltet Til i en mail. <sup>1</sup>|`to:annb@contoso.com` <p> `to:annb ` <br/> `to:"Ann Beebe"`|Alle eksempler returnerer meddelelser, hvor Ann Beebe er angivet på linjen Til:.|

> [!NOTE]
> <sup>1</sup> For værdien af en modtageregenskab kan du bruge mailadresse (også kaldet brugerens hovednavn eller UPN), visningsnavn eller alias til at angive en bruger. Du kan f.eks. bruge annb@contoso.com, annb eller "Ann Beebe" til at angive brugeren Ann Beebe.

### <a name="recipient-expansion"></a>Modtagerudvidelse

Når du søger efter nogen af modtagerens egenskaber (Fra, Til, Cc, Bcc, Deltagere og Modtagere) forsøger Microsoft 365 at udvide identiteten for hver enkelt bruger ved at søge efter dem i Azure Active Directory (Azure AD).  Hvis brugeren findes i Azure AD, udvides forespørgslen til at medtage brugerens mailadresse (eller UPN), alias, visningsnavn og LegacyExchangeDN. For eksempel udvides en `participants:ronnie@contoso.com` forespørgsel som f.eks. til `participants:ronnie@contoso.com OR participants:ronnie OR participants:"Ronald Nelson" OR participants:"<LegacyExchangeDN>"`.

Hvis du vil forhindre udvidelse af modtageren, skal du tilføje et jokertegn (stjerne) i slutningen af mailadressen og bruge et reduceret domænenavn. F.eks. `participants:"ronnie@contoso*"` skal du sørge for at omslutter mailadressen med dobbelte anførselstegn.

Du skal dog være opmærksom på, at det kan medføre, at relevante elementer ikke returneres i søgeresultaterne, hvis du forhindrer modtagerudvidelse i søgeforespørgslen. Mails i Exchange kan gemmes med forskellige tekstformater i modtagerfelterne. Modtagerudvidelse er beregnet til at hjælpe med at reducere dette ved at returnere meddelelser, der kan indeholde forskellige tekstformater. Så hvis du forhindrer udvidelse af modtager, kan det medføre, at søgeforespørgslen ikke returnerer alle elementer, der kan være relevante for din undersøgelse.

> [!NOTE]
> Hvis du er nødt til at gennemse eller reducere de elementer, der returneres af en søgeforespørgsel på grund af modtagerudvidelse, skal du overveje at Advanced eDiscovery. Du kan søge efter meddelelser (drage fordel af udvidelse af modtager), føje dem til et korrektursæt og derefter bruge gennemsynssætforespørgsler eller filtre til at gennemse eller indsnævre resultaterne. Få mere at vide under [Indsaml data for en sag](collecting-data-for-ediscovery.md) og [Forespørg dataene i et gennemsynssæt](review-set-search.md).

## <a name="searchable-site-properties"></a>Søgbare egenskaber for websted

I følgende tabel vises nogle af de SharePoint- og OneDrive for Business-egenskaber, der kan søges i ved hjælp af eDiscovery-søgeværktøjerne i Microsoft 365-overholdelsescenteret eller ved hjælp af **New-ComplianceSearch** eller **cmdlet'en Set-ComplianceSearch**. Tabellen indeholder et eksempel på syntaksen  _property:value_ for hver egenskab og en beskrivelse af søgeresultaterne, der returneres af eksemplerne.

Du kan finde en komplet liste SharePoint egenskaber, der kan søges i, i Oversigt over [gennemsøgte og administrerede egenskaber SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Der kan søges i egenskaber **,** der er markeret med **et** Ja i kolonnen Forespørgsel.

|Egenskab|Egenskabsbeskrivelse|Eksempel|Søgeresultater, der returneres af eksemplerne|
|---|---|---|---|
|Forfatter|Forfatterfeltet fra Office dokumenter, der bevares, hvis et dokument kopieres. Hvis en bruger f.eks. opretter et dokument og mailer det til en anden, som derefter overfører det til SharePoint, bevarer dokumentet stadig den oprindelige forfatter. Sørg for at bruge brugerens viste navn for denne egenskab.|`author:"Garth Fort"`|Alle dokumenter, der er skrevet af Garth Fort.|
|ContentType|Den SharePoint indholdstype for et element, f.eks. Element, Dokument eller Video.|`contenttype:document`|Alle dokumenter ville blive returneret.|
|Oprettet|Den dato, hvor et element oprettes.|`created>=2021-06-01`|Alle elementer, der er oprettet d. 1. juni 2021 eller efter.|
|CreatedBy|Den person, der har oprettet eller overført et element. Sørg for at bruge brugerens viste navn for denne egenskab.|`createdby:"Garth Fort"`|Alle elementer, der er oprettet eller uploadet af Garth Fort.|
|DetectedLanguage|Sproget for et element.|`detectedlanguage:english`|Alle elementer på engelsk.|
|DocumentLink|Stien (URL) til en bestemt mappe på et SharePoint eller OneDrive for Business websted. Hvis du bruger denne egenskab, skal du sørge for at søge på det websted, hvor den angivne mappe er placeret. <p> Hvis du vil returnere elementer, der er placeret i undermapper i den mappe, du angiver for egenskaben dokumentlink, skal du tilføje /\* til URL-adressen for den angivne mappe, f.eks. `documentlink: "https://contoso.sharepoint.com/Shared Documents/*"` <p> <br/>Hvis du vil have mere at vide om at søge efter egenskaben documentlink og bruge et script til at hente URL-adresserne til dokumentlinks for mapper på et bestemt websted, skal du se Brug indholdssøgning til målrettede [samlinger](use-content-search-for-targeted-collections.md).|`documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Private"` <p> `documentlink:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/Documents/Shared with Everyone/*" AND filename:confidential`|Det første eksempel returnerer alle elementer i den angivne OneDrive for Business mappe. Det andet eksempel returnerer dokumenter i den angivne webstedsmappe (og alle undermapper), der indeholder ordet "fortroligt" i filnavnet.|
|FileExtension|Filtypenavnet for en fil. eksempelvis docx, en, pptx eller xlsx.|`fileextension:xlsx`|Alle Excel filer (Excel 2007 og nyere)|
|Filnavn|Navnet på en fil.|`filename:"marketing plan"` <p> `filename:estimate`|Det første eksempel returnerer filer med det præcise udtryk "marketingplan" i titlen. I det andet eksempel returneres filer med ordet "estimate" i filnavnet.|
|LastModifiedTime|Den dato, hvor et element sidst blev ændret.|`lastmodifiedtime>=2021-05-01` <p> `lastmodifiedtime>=2021-05-01 AND lastmodifiedtime<=2021-06-01`|Det første eksempel returnerer elementer, der er blevet ændret den 1. maj 2021 eller efter den 1. maj 2021. Det andet eksempel returnerer elementer, der er ændret mellem 1. maj 2021 og 1. juni 2021.|
|ModifiedBy|Den person, der senest har ændret et element. Sørg for at bruge brugerens viste navn for denne egenskab.|`modifiedby:"Garth Fort"`|Alle elementer, der sidst blev ændret af Garth Fort.|
|Sti|Stien (URL) til et bestemt websted i et SharePoint eller OneDrive for Business websted. <p> Hvis du kun vil returnere elementer fra det angivne websted `/` , skal du tilføje det efterstillede til slutningen af URL-adressen, f.eks. `path: "https://contoso.sharepoint.com/sites/international/"` <p> Hvis du vil returnere elementer, der er placeret i mapper på det websted, du angiver i stiegenskaben, `/*` skal du tilføje i slutningen af URL-adressen, f.eks.  `path: "https://contoso.sharepoint.com/Shared Documents/*"` <p> **Bemærk!** Hvis du `Path` bruger egenskaben til OneDrive til at søge efter placeringer, returneres mediefiler, f.eks. .png-, .tiff- eller .wav-filer, i søgeresultaterne. Brug en anden webstedsegenskab i din søgeforespørgsel til at søge efter mediefiler OneDrive mapper. <br/>|`path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/"` <p> `path:"https://contoso-my.sharepoint.com/personal/garthf_contoso_com/*" AND filename:confidential`|Det første eksempel returnerer alle elementer på det angivne OneDrive for Business websted. Det andet eksempel returnerer dokumenter på det angivne websted (og mapper på webstedet), der indeholder ordet "fortroligt" i filnavnet.|
|SharedWithUsersOWSUser|Dokumenter, der er blevet delt med den angivne bruger og vist på  siden Delt med mig på brugerens websted OneDrive for Business webstedet. Dette er dokumenter, der udtrykkeligt er delt med den angivne bruger af andre personer i organisationen. Når du eksporterer dokumenter, der svarer til en søgeforespørgsel, der bruger egenskaben SharedWithUsersOWSUser, eksporteres dokumenterne fra den oprindelige indholdsplacering for den person, der har delt dokumentet med den angivne bruger. Du kan finde flere oplysninger i [Søge efter webstedsindhold, der deles i din organisation](#searching-for-site-content-shared-within-your-organization).|`sharedwithusersowsuser:garthf` <p> `sharedwithusersowsuser:"garthf@contoso.com"`|Begge eksempler returnerer alle interne dokumenter, der udtrykkeligt er delt med Garth Fort, og som vises på siden  Delt med mig i Garth Forts OneDrive for Business konto.|
|Websted|URL-adressen på et websted eller en gruppe af websteder i organisationen.|`site:"https://contoso-my.sharepoint.com"` <p> `site:"https://contoso.sharepoint.com/sites/teams"`|Det første eksempel returnerer elementer fra OneDrive for Business for alle brugere i organisationen. Det andet eksempel returnerer elementer fra alle teamwebsteder.|
|Størrelse|Størrelsen på et element i byte.|`size>=1` <p> `size:1..10000`|Det første eksempel returnerer elementer, der er større end 1 byte. Det andet eksempel returnerer elementer fra 1 til 10.000 byte i størrelse.|
|Titel|Titlen på dokumentet. Titelegenskaben er metadata, der er angivet i Microsoft Office dokumenter. Det er forskelligt fra filnavnet på dokumentet.|`title:"communication plan"`|Et dokument, der indeholder udtrykket "kommunikationsplan" i egenskaben Titelmetadata for en Office dokument.|

## <a name="searchable-contact-properties"></a>Søgbare egenskaber for kontakter

I følgende tabel vises de egenskaber for kontakter, der indekseres, og som du kan søge efter ved hjælp af eDiscovery-søgeværktøjer. Disse er de egenskaber, som brugerne kan konfigurere for de kontakter (også kaldet personlige kontakter), der findes i brugerens postkasses personlige adressekartotek. Hvis du vil søge efter kontakter, kan du vælge postkasserne til søgning og derefter bruge en eller flere kontaktegenskaber i nøgleordsforespørgslen.

> [!TIP]
> Hvis du vil søge efter værdier, der indeholder mellemrum eller specialtegn, skal du bruge dobbelte anførselstegn (" ") til at indeholde udtrykket. f.eks. `businessaddress:"123 Main Street"`.

|Egenskab|Egenskabsbeskrivelse|
|---|---|
|BusinessAddress|Adressen i egenskaben **Forretningsadresse** . Egenskaben kaldes også for **arbejdsadressen** på siden med egenskaber for kontakter.|
|Telefon (arbejde)|Telefonnummeret i en af **egenskaberne for business Telefon-nummer**.|
|Firmanavn|Navnet **i egenskaben Firma** .|
|Afdeling|Navnet **i egenskaben Afdeling** .|
|DisplayName|Kontaktens viste navn. Dette er navnet i **egenskaben Fulde navn** for kontakten.|
|Mailadresse|Adressen på en hvilken som helst mailadresseegenskab for kontakten. Brugere kan tilføje flere mailadresser for en kontakt. Hvis du bruger denne egenskab, returneres kontakter, der svarer til kontaktens mailadresser.|
|FileAs|Egenskaben **Arkiver** som. Denne egenskab bruges til at angive, hvordan kontakten står på brugerens liste over kontakter. En kontakt kan f.eks. være angivet  *som Fornavn,Efternavn*  *eller Efternavn,Fornavn*.|
|GivenName|Navnet i egenskaben **Fornavn** .|
|HomeAddress|Adressen i en af egenskaberne **for Hjemmeadresse** .|
|Telefon (privat)|Telefonnummeret i en af **egenskaberne for** Privat telefonnummer.|
|IMAddress|Egenskaben Chatadresse, som typisk er en mailadresse, der bruges til chat.|
|MiddleName|Navnet i egenskaben **Mellemnavn** .|
|Mobiltelefon|Telefonnummeret **i egenskaben** Mobiltelefonnummer.|
|Kaldenavn|Navnet i egenskaben **Kaldenavn** .|
|OfficeLocation|Værdien **i Office eller** **Office placering**.|
|OtherAddress|Værdien for egenskaben **Andet** adresse.|
|Efternavn|Navnet **i egenskaben Efternavn** .|
|Titel|Titlen i egenskaben **Stilling** .|

## <a name="searchable-sensitive-data-types"></a>Søgbare følsomme datatyper

Du kan bruge eDiscovery-søgeværktøjer i Microsoft 365 Overholdelsescenter til at søge efter følsomme data, f.eks. kreditkortnumre eller cpr-numre, der er gemt i dokumenter på SharePoint og OneDrive for Business websteder. Det kan du gøre ved hjælp af egenskaben `SensitiveType` og navnet (eller id'et) for en følsom oplysningstype i en nøgleordsforespørgsel. Forespørgslen returnerer f.eks `SensitiveType:"Credit Card Number"` . dokumenter, der indeholder et kreditkortnummer. Forespørgslen returnerer  `SensitiveType:"U.S. Social Security Number (SSN)"` dokumenter, der indeholder et amerikansk CPR-nummer.

Hvis du vil se en liste over de typer af følsomme oplysninger, du kan søge efter, skal du gå til **Dataklassificeringer** \> **Typer** af følsomme oplysninger Microsoft 365 Overholdelsescenter. Eller du kan bruge **Get-DlpSensitiveInformationType-cmdlet'en** i Security & Compliance Center PowerShell til at få vist en liste over typer af følsomme oplysninger.

Du kan finde flere oplysninger om at oprette forespørgsler ved hjælp af egenskaben `SensitiveType` under Opret en forespørgsel [for at finde følsomme data, der er gemt på websteder](form-a-query-to-find-sensitive-data-stored-on-sites.md).

### <a name="limitations-for-searching-sensitive-data-types"></a>Begrænsninger for søgning af følsomme datatyper

- Hvis du vil søge efter brugerdefinerede typer af følsomme oplysninger, skal du angive id'et for typen af følsomme oplysninger i `SensitiveType` egenskaben. Hvis du bruger navnet på en brugerdefineret type af følsomme oplysninger (som vist i eksemplet for indbyggede typer af følsomme oplysninger i forrige afsnit), returneres ingen resultater. Brug kolonnen **Publisher** på siden Sensitive **info types** i overholdelsescenteret (eller **Publisher-egenskaben** i PowerShell) til at skelne mellem indbyggede og brugerdefinerede typer af følsomme oplysninger. Indbyggede følsomme datatyper har en værdi af `Microsoft Corporation` for **egenskaben Publisher** data.

  Hvis du vil have vist navn og id for de brugerdefinerede følsomme datatyper i organisationen, skal du køre følgende kommando i Security & Compliance Center PowerShell:

  ```powershell
  Get-DlpSensitiveInformationType | Where-Object {$_.Publisher -ne "Microsoft Corporation"} | FT Name,Id
  ```

  Derefter kan du bruge id'et i søgeegenskaben `SensitiveType` til at returnere dokumenter, der indeholder den brugerdefinerede følsomme datatype, f.eks. `SensitiveType:7e13277e-6b04-3b68-94ed-1aeb9d47de37`

- Du kan ikke bruge typer af følsomme oplysninger `SensitiveType` og søgeegenskaben til at søge efter følsomme data in Exchange Online postkasser. Dette omfatter 1:1-chatmeddelelser, 1:N-gruppechatmeddelelser og teamkanalsamtaler i Microsoft Teams, fordi alt dette indhold er gemt i postkasser. Du kan dog bruge politikker til forebyggelse af datatab (DLP) til at beskytte følsomme maildata under overførsel. Få mere at vide under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md) [og Søg efter og find personlige data](/compliance/regulatory/gdpr).

## <a name="search-operators"></a>Søgeoperatorer

Booleske søgeoperatorer, f.eks. **OG**, **ELLER** og **IKKE**, hjælper dig med at definere mere præcise søgninger ved at medtage eller udelade bestemte ord i søgeforespørgslen. Andre teknikker, f.eks. brug af egenskabsoperatorer (`>=``..`f.eks. eller ), anførselstegn, parenteser og jokertegn, kan hjælpe dig med at afgrænse en søgeforespørgsel. I følgende tabel vises de operatorer, du kan bruge til at indsnævre eller udvide søgeresultaterne.

|Operator|Anvendelse|Beskrivelse|
|---|---|---|
|AND|nøgleord1 OG nøgleord2|Returnerer elementer, der indeholder alle de angivne nøgleord eller  `property:value` udtryk. Returnerer f.eks  `from:"Ann Beebe" AND subject:northwind` . alle meddelelser, der er sendt af Ann Beebe, som indeholdt ordet northwind i emnelinjen. <sup>2</sup>|
|+|nøgleord1 + nøgleord2 + nøgleord3|Returnerer elementer, der indeholder  *enten eller*  `keyword2`  `keyword3` *, og*  som også indeholder  `keyword1`. Derfor svarer dette eksempel til forespørgslen  `(keyword2 OR keyword3) AND keyword1`. <p> Forespørgslen (  `keyword1 + keyword2` med et mellemrum efter symbolet **+** ) er ikke det samme som at bruge **operatoren OG** . Denne forespørgsel svarer til og returnerer  `"keyword1 + keyword2"` elementer med den nøjagtige fase  `"keyword1 + keyword2"`.|
|ELLER|nøgleord1 ELLER nøgleord2|Returnerer elementer, der indeholder en eller flere af de angivne nøgleord  `property:value` eller udtryk. <sup>2</sup>|
|NOT|nøgleord1 NOT keyword2 <p> IKKE fra:"Ann Beebe" <p> NOT kind:im|Udelukker elementer, der er angivet af et nøgleord eller udtryk  `property:value` . I det andet eksempel udelades meddelelser, der er sendt af Ann Beebe. Det tredje eksempel udelader chatsamtaler, f.eks. Skype for Business samtaler, der er gemt i mappen med postkassen Samtaleoversigt. <sup>2</sup>|
|-|nøgleord1 -keyword2|Det samme som **operatoren NOT** . Så denne forespørgsel returnerer elementer, der indeholder og  `keyword1` udelader elementer, der indeholder  `keyword2`.|
|I NÆRHEDEN AF|nøgleord1 NEAR(n) nøgleord2|Returnerer elementer med ord, der er i nærheden af hinanden, hvor n er lig antallet af ord, der adskiller. Returnerer f.eks `best NEAR(5) worst` . et element, hvor ordet "værst" er inden for fem ord med "bedst". Hvis der ikke er angivet noget tal, er standardafstanden otte ord. <sup>2</sup>|
|:|egenskab:værdi|Kolonet (:)  `property:value` i syntaksen angiver, at værdien af den egenskab, der søges efter, indeholder den angivne værdi. Returnerer f.eks.  `recipients:garthf@contoso.com` alle meddelelser, der er sendt garthf@contoso.com.|
|=|property=value|Det samme som **operatoren :** .|
|\<|egenskabsværdi\<|Angiver, at den egenskab, der søges efter, er mindre end den angivne værdi. <sup>1</sup>|
|\>|egenskabsværdi\>|Angiver, at den egenskab, der søges i, er større end den angivne værdi. <sup>1</sup>|
|\<=|property\<=value|Angiver, at den egenskab, der søges efter, er mindre end eller lig med en bestemt værdi. <sup>1</sup>|
|\>=|property\>=value|Angiver, at den egenskab, der søges efter, er større end eller lig med en bestemt værdi. <sup>1</sup>|
|..|egenskab:værdi1.. værdi2|Angiver, at den egenskab, der søges efter, er større end eller lig med værdi1 og mindre end eller lig med værdi2. <sup>1</sup>|
|"  "|"rimelig værdi" <p> subject:"Quarterly Financials"|I en nøgleordsforespørgsel `property:value` (hvor du skriver parret i feltet Nøgleord) skal du bruge dobbelte anførselstegn (" ") til at søge efter et bestemt udtryk eller udtryk. Men hvis du bruger betingelsen  Emne eller Emne **/** [](#search-conditions) titel, skal du ikke tilføje dobbelte anførselstegn til værdien, da anførselstegn tilføjes automatisk ved brug af disse søgebetingelser. Hvis du føjer anførselstegn til værdien, føjes to par dobbelte anførselstegn til betingelsesværdien, og søgeforespørgslen returnerer en fejl. |
|\*|kat\* <p> emne:sæt\*|Præfikssøgninger (også kaldet *præfiksmatching*), hvor et jokertegn ( * ) er placeret i slutningen af et ord i nøgleord eller `property:value` forespørgsler. Ved præfikssøgninger returnerer søgningen resultater med ord, der indeholder ordet efterfulgt af nul eller flere tegn. Returnerer f.eks. dokumenter, der indeholder ordet "set", "setup" og "setting" (og andre ord, `title:set*` der starter med "set") i dokumentets titel. <p> **Bemærk!** Du kan kun bruge præfikssøgninger. f.eks **. cat\**_ eller _* set\**_. Suffikssøgninger (_*\*kat), infikssøgninger** (**ct\***) og understrengssøgninger **(\*\*kat**) understøttes ikke. <p> Du kan også tilføje et punktum ( \. ) til en præfikssøgning ændrer de resultater, der returneres. Det skyldes, at et punktum behandles som et stopord. For eksempel returnerer søgning **efter kat\**_ og søgning efter _* cat.\*** forskellige resultater. Vi anbefaler, at du ikke bruger et punktum i en præfikssøgning.|
|(  )|(fair OR free) OG (fra:contoso.com) <p> (IPO OR initial) OG (aktier ELLER shares) <p> (kvartalsvise regnskaber)|Parenteser grupperer booleske udtryk,  `property:value` elementer og nøgleord. Returnerer f.eks  `(quarterly financials)` . elementer, der indeholder ordene kvartalsvist og finansielt.|

> [!NOTE]
> <sup>1</sup> Brug denne operator til egenskaber, der indeholder datoværdier eller numeriske værdier.<br/> <sup>2</sup> booleske søgeoperatorer skal være store bogstaver. F.eks. **OG**. Hvis du bruger en operator med små bogstaver, f.eks. **og, behandles** den som et nøgleord i søgeforespørgslen.

## <a name="search-conditions"></a>Søgebetingelser

Du kan føje betingelser til en søgeforespørgsel for at indsnævre søgningen og returnere et mere elegant sæt resultater. Hver betingelse føjer en delsætning til KQL-søgeforespørgslen, der oprettes og køres, når du starter søgningen.

[Betingelser for fælles egenskaber](#conditions-for-common-properties)

[Betingelser for mailegenskaber](#conditions-for-mail-properties)

[Betingelser for dokumentegenskaber](#conditions-for-document-properties)

[Operatorer, der bruges med betingelser](#operators-used-with-conditions)

[Retningslinjer for brug af betingelser](#guidelines-for-using-conditions)

[Eksempler på brug af betingelser i søgeforespørgsler](#examples-of-using-conditions-in-search-queries)

### <a name="conditions-for-common-properties"></a>Betingelser for fælles egenskaber

Opret en betingelse ved hjælp af fælles egenskaber, når du søger i postkasser og websteder i samme søgning. I følgende tabel vises de tilgængelige egenskaber, der kan bruges, når du tilføjer en betingelse.

|Betingelse|Beskrivelse|
|---|---|
|Dato|For mails er den dato, hvor en meddelelse blev modtaget af en modtager eller sendt af afsenderen. For dokumenter er den dato, hvor et dokument sidst blev ændret.|
|Afsender/forfatter|Til mail er den person, der har sendt en meddelelse. For dokumenter har den person, der er citeret i forfatterfeltet, Office dokumenter. Du kan skrive mere end ét navn adskilt af kommaer. To eller flere værdier forbindes logisk af operatoren **ELLER** .|
|Størrelse (i byte)|For både mail og dokumenter, elementets størrelse (i byte).|
|Emne/titel|Hvad mail er teksten i emnelinjen i en meddelelse. For dokumenter, titlen på dokumentet. Som beskrevet tidligere er titelegenskaben metadata angivet i Microsoft Office dokumenter. Du kan skrive navnet på mere end ét emne/titelværdier adskilt af kommaer. To eller flere værdier forbindes logisk af operatoren **ELLER** . <p> **Bemærk**! Du skal ikke medtage dobbelte anførselstegn på værdierne for denne betingelse, da anførselstegn automatisk tilføjes, når du bruger denne søgebetingelse. Hvis du tilføjer anførselstegn til værdien, føjes to par dobbelte anførselstegn til betingelsesværdien, og søgeforespørgslen returnerer en fejl.|
|Opbevaringsmærkat|For både mail og dokumenter, opbevaringsetiketter, der er blevet tildelt meddelelser og dokumenter automatisk ved hjælp af politikker for automatisk mærkater eller opbevaringsetiketter, der er blevet tildelt manuelt af brugerne. Opbevaringsetiketter bruges til at klassificere mail og dokumenter med henblik på styring af oplysninger og håndhæve opbevaringsregler baseret på de indstillinger, der er defineret af etiketten. Du kan skrive en del af opbevaringsnavnet og bruge et jokertegn eller skrive hele navnet på navnet. Du kan finde flere oplysninger om opbevaringsnavne i [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).|

### <a name="conditions-for-mail-properties"></a>Betingelser for mailegenskaber

Opret en betingelse ved hjælp af mailegenskaber, når du søger i postkasser eller offentlige mapper. I følgende tabel vises de mailegenskaber, du kan bruge til en betingelse. Disse egenskaber er et undersæt af de mailegenskaber, der er blevet beskrevet tidligere. Disse beskrivelser gentages af hensyn til din brugervenlighed.

|Betingelse|Beskrivelse|
|---|---|
|Meddelelses type|Den meddelelsestype, der skal søges i. Dette er den samme egenskab som egenskaben Type mail. Mulige værdier: <ul><li>kontakter</li><li>dokumenter</li><li>mail</li><li>externaldata</li><li>fax</li><li>im</li><li>journaler</li><li>møder</li><li>microsoftteams</li><li>noter</li><li>indlæg</li><li>rssfeeds</li><li>opgaver</li><li>telefonsvarer</li></ul>|
|Deltagere|Alle personer-felterne i en mail. Disse felter er Fra, Til, Cc og Bcc.|
|Type|Meddelelsesklasseegenskaben for et mailelement. Dette er den samme egenskab som mailegenskaben Elementklasse. Det er også en betingelse med flere værdier. Så hvis du vil markere flere meddelelsesklasser, skal du holde **Ctrl** nede og derefter klikke på to eller flere meddelelsesklasser på rullelisten, som du vil føje til betingelsen. Hver meddelelsesklasse, du vælger på listen, forbindes logisk af operatoren **ELLER** i den tilsvarende søgeforespørgsel. <p> Du kan finde en liste over meddelelsesklasser (og deres tilsvarende meddelelsesklasse-id), der bruges af Exchange, og som du kan vælge på  listen Meddelelsesklasse, under Elementtyper og [Meddelelsesklasser](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Modtaget|Den dato, hvor en mail blev modtaget af en modtager. Dette er den samme egenskab som egenskaben Modtaget mail.|
|Modtagere|Alle modtagerfelter i en mail. Disse felter er Til, Cc og Bcc.|
|Afsender|Afsenderen af en mail.|
|Sendt|Den dato, hvor afsenderen sendte en mail. Dette er den samme egenskab som egenskaben Sendt mail.|
|Emne|Teksten i emnelinjen i en mail. <p> **Bemærk**! Du skal ikke medtage dobbelte anførselstegn på værdierne for denne betingelse, da anførselstegn automatisk tilføjes, når du bruger denne søgebetingelse. Hvis du tilføjer anførselstegn til værdien, føjes to par dobbelte anførselstegn til betingelsesværdien, og søgeforespørgslen returnerer en fejl.|
|Hvis du vil|Modtageren af en mail i feltet Til.|

### <a name="conditions-for-document-properties"></a>Betingelser for dokumentegenskaber

Opret en betingelse ved hjælp af dokumentegenskaber, når du søger efter dokumenter SharePoint og OneDrive for Business websteder. I følgende tabel vises de dokumentegenskaber, du kan bruge til en betingelse. Disse egenskaber er et undersæt af de webstedsegenskaber, der er blevet beskrevet tidligere. Disse beskrivelser gentages af hensyn til din brugervenlighed.

|Betingelse|Beskrivelse|
|---|---|
|Forfatter|Forfatterfeltet fra Office dokumenter, der bevares, hvis et dokument kopieres. Hvis en bruger f.eks. opretter et dokument og mailer det til en anden, som derefter overfører det til SharePoint, bevarer dokumentet stadig den oprindelige forfatter.|
|Titel|Titlen på dokumentet. Titelegenskaben er metadata, der er angivet i Office dokumenter. Det er forskelligt fra filnavnet på dokumentet.|
|Oprettet|Den dato, hvor et dokument oprettes.|
|Senest ændret|Den dato, hvor et dokument sidst blev ændret.|
|Filtype|Filtypenavnet for en fil. eksempelvis docx, en, pptx eller xlsx. Dette er den samme egenskab som egenskaben FileExtension-websted. <p> **Bemærk!** Hvis du medtager en betingelse af typen Filtype  ved hjælp af  operatoren Er lig med eller Lig med i en søgeforespørgsel, kan du ikke bruge en præfikssøgning (ved at medtage jokertegnet ( \* ) i slutningen af filtypen) til at returnere alle versioner af en filtype. Hvis du gør det, ignoreres jokertegnet. Hvis du f.eks. medtager betingelsen `Equals any of doc*`, returneres kun filer med `.doc` filtypenavnet . Filer med filtypenavnet `.docx` returneres ikke. Hvis du vil returnere alle versioner af en filtype, skal du bruge *egenskaben property:value* pair i en nøgleordsforespørgsel; f.eks. `filetype:doc*`.|

### <a name="operators-used-with-conditions"></a>Operatorer, der bruges med betingelser

Når du tilføjer en betingelse, kan du vælge en operator, der er relevant for egenskabstypen for betingelsen. I følgende tabel beskrives de operatorer, der bruges med betingelser, og den tilsvarende, der bruges i søgeforespørgslen, angives.

|Operator|Tilsvarende forespørgsel|Beskrivelse|
|---|---|---|
|Efter|`property>date`|Bruges med datobetingelser. Returnerer elementer, der er blevet sendt, modtaget eller ændret efter den angivne dato.|
|Før|`property<date`|Bruges med datobetingelser. Returnerer elementer, der er blevet sendt, modtaget eller ændret før den angivne dato.|
|Between|`date..date`|Bruges med betingelser for dato og størrelse. Når den bruges med en datobetingelse, returneres elementer, der er blevet sendt, modtaget eller ændret inden for det angivne datointerval. Når den bruges med en størrelsesbetingelse, returneres elementer, hvis størrelse er inden for det angivne område.|
|Indeholder et af|`(property:value) OR (property:value)`|Bruges med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der indeholder en del af en eller flere angivne strengværdier.|
|Indeholder ikke nogen af|`-property:value` <p> `NOT property:value`|Bruges med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der ikke indeholder nogen del af den angivne strengværdi.|
|Er ikke lig med nogen af|`-property=value` <p> `NOT property=value`|Bruges med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der ikke indeholder den bestemte streng.|
|Er lig med|`size=value`|Returnerer elementer, der er lig med den angivne størrelse. <sup>1</sup>|
|Er lig med et af|`(property=value) OR (property=value)`|Bruges med betingelser for egenskaber, der angiver en strengværdi. Returnerer elementer, der svarer til en eller flere angivne strengværdier.|
|Større|`size>value`|Returnerer elementer, hvor den angivne egenskab er større end den angivne værdi. <sup>1</sup>|
|Større eller lig med|`size>=value`|Returnerer elementer, hvor den angivne egenskab er større end eller lig med den angivne værdi. <sup>1</sup>|
|Mindre|`size<value`|Returnerer elementer, der er større end eller lig med den specifikke værdi. <sup>1</sup>|
|Mindre eller lig med|`size<=value`|Returnerer elementer, der er større end eller lig med den specifikke værdi. <sup>1</sup>|
|Ikke lig med|`size<>value`|Returnerer elementer, der ikke er lig med den angivne størrelse. <sup>1</sup>|

> [!NOTE]
> <sup>1</sup> Denne operator er kun tilgængelig for betingelser, der bruger egenskaben Størrelse.

### <a name="guidelines-for-using-conditions"></a>Retningslinjer for brug af betingelser

Vær opmærksom på følgende, når du bruger søgebetingelser.

- En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i feltet nøgleord) af **operatoren AND** . Det betyder, at elementerne skal opfylde både nøgleordsforespørgslen og den betingelse, der skal medtages i resultaterne. Det er sådan, betingelser kan hjælpe dig med at indsnævre dine resultater.

- Hvis du føjer to eller flere entydige betingelser til en søgeforespørgsel (betingelser, der angiver forskellige egenskaber), forbindes disse betingelser logisk af **operatoren AND** . Det betyder, at det kun er elementer, der opfylder alle betingelserne (ud over en nøgleordsforespørgsel), der returneres.

- Hvis du tilføjer mere end én betingelse for den samme egenskab, forbindes disse betingelser logisk af **operatoren OR** . Det betyder, at elementer, der opfylder nøgleordsforespørgslen, og en af betingelserne returneres. Grupper af de samme betingelser forbindes altså med hinanden af operatoren **ELLER** , og sæt af entydige betingelser forbindes derefter af **operatoren OG** .

- Hvis du føjer flere værdier (adskilt af kommaer eller semikolon) til en enkelt betingelse, forbindes disse værdier af **operatoren ELLER** . Det betyder, at elementer returneres, hvis de indeholder nogen af de angivne værdier for egenskaben i betingelsen.

- Alle betingelser, der bruger en operator med **logik for Indeholder** **og Er lig** med, returnerer tilsvarende søgeresultater for simple strengsøgninger. En simpel strengsøgning er en streng i den betingelse, der ikke indeholder et jokertegn. Eksempelvis returnerer en betingelse, der bruger **Lig med** et af, de samme elementer som en betingelse, der bruger **Indeholder et af.**

- Den søgeforespørgsel, der oprettes ved hjælp af nøgleordsfeltet og betingelserne,  vises på siden Søg i detaljeruden for den valgte søgning. I en forespørgsel angiver alt til højre for notationen  `(c:c)` betingelser, der føjes til forespørgslen.

- Betingelser føjer kun egenskaber til søgeforespørgslen. operatorerne tilføj ikke. Dette er grunden til, at forespørgslen, der vises i detaljeruden, ikke viser operatorer til højre for  `(c:c)` notationen. KQL tilføjer de logiske operatorer (i overensstemmelse med de tidligere forklarede regler), når forespørgslen køres.

- Du kan bruge træk og slip-kontrolelementet til at genforespørge rækkefølgen af betingelser. Klik på kontrolelementet for en betingelse, og flyt den op eller ned.

- Som tidligere nævnt giver nogle betingelsesegenskaber dig mulighed for at skrive flere værdier (adskilt af semikolon). Hver værdi er logisk forbundet af **operatoren ELLER** og resulterer i forespørgslen `(filetype=docx) OR (filetype=pptx) OR (filetype=xlsx)`. Følgende illustration viser et eksempel på en betingelse med flere værdier.

    ![Én betingelse med flere værdier.](../media/SearchConditions1.png)

  > [!NOTE]
  > Du kan ikke tilføje flere betingelser (ved at klikke på **Tilføj betingelse** for den samme egenskab. I stedet skal du angive flere værdier for betingelsen (adskilt af semikolon), som vist i det forrige eksempel.

### <a name="examples-of-using-conditions-in-search-queries"></a>Eksempler på brug af betingelser i søgeforespørgsler

Følgende eksempler viser den GUI-baserede version af en søgeforespørgsel med betingelser, syntaksen for søgeforespørgslen, der vises i detaljeruden for den valgte søgning (som også returneres af **cmdlet'en Get-ComplianceSearch** ) og logikken i den tilsvarende KQL-forespørgsel.

#### <a name="example-1"></a>Eksempel 1

I dette eksempel returneres dokumenter på SharePoint websteder OneDrive for Business der indeholder et kreditkortnummer, og som senest er blevet ændret før 1. januar 2021.

**GUI**:

![Første eksempel på søgebetingelser.](../media/SearchConditions2.png)

**Søgeforespørgselssyntaksen**:

`SensitiveType:"Credit Card Number"(c:c)(lastmodifiedtime<2021-01-01)`

**Søgeforespørgselslogik**:

`SensitiveType:"Credit Card Number" AND (lastmodifiedtime<2021-01-01)`

Bemærk i det forrige skærmbillede, at søgebrugergrænsefladen understøtter, at nøgleordsforespørgslen og -betingelsen er forbundet af **operatoren AND** .

#### <a name="example-2"></a>Eksempel 2

I dette eksempel returneres mailelementer eller dokumenter, der indeholder nøgleordet "rapport", som blev sendt eller oprettet før 1. april 2021, og som indeholder ordet "northwind" i emnefeltet i mails eller i titelegenskaben for dokumenter. Forespørgslen udelukker websider, der opfylder de andre søgekriterier.

**GUI**:

![Andet eksempel på søgebetingelser.](../media/SearchConditions3.png)

**Søgeforespørgselssyntaksen**:

`report(c:c)(date<2021-04-01)(subjecttitle:"northwind")(-filetype:aspx)`

**Søgeforespørgselslogik**:

`report AND (date<2021-04-01) AND (subjecttitle:"northwind") NOT (filetype:aspx)`

#### <a name="example-3"></a>Eksempel 3

I dette eksempel returneres mails eller kalendermøder, der blev sendt mellem 1. december 2019 og 30. november 2020, og som indeholder ord, der starter med "telefon" eller "smartphone".

**GUI**:

![Tredje eksempel på søgebetingelser.](../media/SearchConditions4.png)

**Søgeforespørgselssyntaksen**:

`phone* OR smartphone*(c:c)(sent=2019-12-01..2020-11-30)(kind="email")(kind="meetings")`

**Søgeforespørgselslogik**:

`phone* OR smartphone* AND (sent=2019-12-01..2020-11-30) AND ((kind="email") OR (kind="meetings"))`

## <a name="special-characters"></a>Specialtegn

Nogle specialtegn er ikke medtaget i søgeindekset og er derfor ikke søgbare. Dette omfatter også de specialtegn, der repræsenterer søgeoperatorer i søgeforespørgslen. Her er en liste over specialtegn, der enten erstattes af et tomt mellemrum i den faktiske søgeforespørgsel eller medfører en søgefejl.

`+ - = : ! @ # % ^ & ; _ / ? ( ) [ ] { }`

## <a name="searching-for-site-content-shared-with-external-users"></a>Søge efter webstedsindhold, der er delt med eksterne brugere

Du kan også bruge eDiscovery-søgeværktøjer i overholdelsescenteret til at søge efter dokumenter, der er gemt på SharePoint og OneDrive for Business-websteder, der er delt med personer uden for organisationen. Dette kan hjælpe dig med at identificere følsomme eller beskyttede oplysninger, der deles uden for organisationen. Det kan du gøre ved hjælp af egenskaben i  `ViewableByExternalUsers` en nøgleordsforespørgsel. Denne egenskab returnerer dokumenter eller websteder, der er delt med eksterne brugere, ved hjælp af en af følgende delingsmetoder:

- En invitation til deling, der kræver, at brugerne logger på din organisation som en godkendt bruger.
- Et anonymt gæstelink, som giver alle med dette link adgang til ressourcen uden at skulle godkendes.

Her er nogle eksempler:

- Forespørgslen returnerer  `ViewableByExternalUsers:true AND SensitiveType:"Credit Card Number"` alle elementer, der er blevet delt med personer uden for organisationen, og indeholder et kreditkortnummer.
- Forespørgslen returnerer  `ViewableByExternalUsers:true AND ContentType:document AND site:"https://contoso.sharepoint.com/Sites/Teams"` en liste over dokumenter på alle teamwebsteder i organisationen, der er delt med eksterne brugere.

> [!TIP]
> En søgeforespørgsel,  `ViewableByExternalUsers:true AND ContentType:document` som f.eks. kan returnere en masse .aspx-filer i søgeresultaterne. For at fjerne disse (eller andre typer filer) kan du bruge egenskaben  `FileExtension` til at udelukke bestemte filtyper, f.eks  `ViewableByExternalUsers:true AND ContentType:document NOT FileExtension:aspx`. .

Hvad betragtes som indhold, der deles med personer uden for organisationen? Dokumenter i organisationens websteder SharePoint og OneDrive for Business, der deles ved at sende en invitation til deling, eller som deles på offentlige placeringer. Følgende brugeraktiviteter medfører f.eks. indhold, der kan vises af eksterne brugere:

- En bruger deler en fil eller mappe med en person uden for organisationen.
- En bruger opretter og sender et link til en delt fil til en person uden for organisationen. Dette link gør det muligt for den eksterne bruger at få vist (eller redigere) filen.
- En bruger sender en invitation til deling eller et gæstelink til en person uden for organisationen for at få vist (eller redigere) en delt fil.

### <a name="issues-using-the-viewablebyexternalusers-property"></a>Problemer med at bruge egenskaben ViewableByExternalUsers

Mens egenskaben  `ViewableByExternalUsers` repræsenterer status for, om et dokument eller websted deles med eksterne brugere, er der nogle problemer med, hvad denne egenskab gør og ikke afspejler. I følgende scenarier opdateres værdien  `ViewableByExternalUsers` af egenskaben ikke, og resultaterne af en søgeforespørgsel, der bruger denne egenskab, kan være unøjagtige.

- Ændringer i delingspolitikken, f.eks. de slå ekstern deling fra for et websted eller for organisationen. Egenskaben viser stadig tidligere delte dokumenter som eksternt tilgængelige, selvom ekstern adgang kan være blevet tilbagekaldt.
- Ændringer af gruppemedlemskab, f.eks. tilføjelse eller fjernelse af eksterne brugere Microsoft 365 grupper eller Microsoft 365-sikkerhedsgrupper. Egenskaben opdateres ikke automatisk for elementer, som gruppen har adgang til.
- Afsendelse af invitationer til deling til eksterne brugere, hvor modtageren ikke har accepteret invitationen, og modtageren har derfor endnu ikke adgang til indholdet.

I disse scenarier afspejler egenskaben  `ViewableByExternalUsers` ikke den aktuelle delingsstatus, før webstedet eller dokumentbiblioteket genfindes og indekseres igen.

## <a name="searching-for-site-content-shared-within-your-organization"></a>Søge efter webstedsindhold, der er delt i din organisation

Som beskrevet tidligere kan du bruge egenskaben,  `SharedWithUsersOWSUser` så du kan søge efter dokumenter, der er delt mellem personer i organisationen. Når en person deler en fil (eller mappe) med en anden bruger i organisationen, vises der et link til den delte fil på  siden Delt med mig på OneDrive for Business-kontoen for den person, som filen blev delt med. Hvis du f.eks. vil søge efter de dokumenter, der er blevet delt med Sara Davis, kan du bruge forespørgslen  `SharedWithUsersOWSUser:"sarad@contoso.com"`. Hvis du eksporterer resultaterne af denne søgning, downloades de oprindelige dokumenter (placeret i placeringen af indholdet for den person, der har delt dokumenterne med Sara).

Dokumenter skal udtrykkeligt deles med en bestemt bruger, der skal returneres i søgeresultater, når du bruger egenskaben  `SharedWithUsersOWSUser` . Hvis f.eks. en person deler et dokument på sin OneDrive-konto, har vedkommende mulighed for at dele det med alle (i eller uden for organisationen), dele det kun med personer i organisationen eller dele det med en bestemt person. Her er et skærmbillede af vinduet **Del** i OneDrive, der viser de tre delingsindstillinger.

![Kun filer, der deles med bestemte personer, returneres af en søgeforespørgsel, der bruger egenskaben SharedWithUsersOWSUser.](../media/469a4b61-68bd-4ab0-b612-ab6302973886.png)

Kun dokumenter, der deles ved hjælp af den tredje indstilling (delt med bestemte **personer), vil** blive returneret af en søgeforespørgsel, der bruger  `SharedWithUsersOWSUser` egenskaben.

## <a name="searching-for-skype-for-business-conversations"></a>Søge efter Skype for Business samtaler

Du kan bruge følgende nøgleordsforespørgsel til specifikt at søge efter indhold Skype for Business samtaler:

```powershell
kind:im
```

Den tidligere søgeforespørgsel returnerer også chatsamtaler fra Microsoft Teams. For at undgå dette kan du indsnævre søgeresultaterne, så de kun Skype for Business samtaler ved hjælp af følgende nøgleordsforespørgsel:

```powershell
kind:im AND subject:conversation
```

Den tidligere nøgleordsforespørgsel udelukker chatsamtaler i Microsoft Teams, fordi Skype for Business-samtaler gemmes som mails med en Emne-linje, der starter med ordet "Samtale".

Hvis du vil søge Skype for Business samtaler, der er indtruffet i et bestemt datointerval, skal du bruge følgende nøgleordsforespørgsel:

```powershell
kind:im AND subject:conversation AND (received=startdate..enddate)
```

## <a name="character-limits-for-searches"></a>Tegnbegrænsninger for søgninger

Der er en tegngrænse på 4.000 tegn for søgeforespørgsler, når du søger efter indhold på SharePoint-websteder OneDrive konti.
Sådan beregnes det samlede antal tegn i søgeforespørgslen:

- Tegnene i søgeforespørgslen nøgleord (herunder både bruger- og filterfelter) tæller med i denne grænse.
- Tegnene i en hvilken som helst placeringsegenskab (f.eks. URL-adresserne for alle de SharePoint websteder eller OneDrive, der søges i), tæller med i denne grænse.
- Tegnene i alle søgetilladelsesfiltrene, der anvendes på den bruger, der kører søgningen, tæller med i grænsen.

Du kan finde flere oplysninger om tegnbegrænsninger i [eDiscovery-søgebegrænsninger](limits-for-content-search.md#search-limits).

> [!NOTE]
> Grænsen på 4.000 tegn gælder for indholdssøgning, grundlæggende eDiscovery og Advanced eDiscovery.

## <a name="search-tips-and-tricks"></a>Søgetips og -tricks

- Nøgleordssøgninger tager ikke hensyn til store og små bogstaver. Cat og **CAT returnerer** **f.eks** . de samme resultater.

- De booleske **operatorer AND**, **OR**, **NOT** **og NEAR** skal være store bogstaver.

- Et mellemrum mellem to nøgleord eller to udtryk  `property:value` er det samme som at bruge **OG**. Returnerer f.eks. alle meddelelser, der er sendt af Sara Davis,  `from:"Sara Davis" subject:reorganization` som indeholder ordet omorganisering i emnelinjen.

- Brug syntaks, der svarer til `property:value` formatet. Der er ikke store og små bogstaver i værdier, og der kan ikke være mellemrum efter operatoren. Hvis der er et mellemrum, vil din tilsigtede værdi være en fuldtekstsøgning. Søger f.eks `to: pilarp` . efter "pilarp" som et nøgleord i stedet for efter meddelelser, der blev sendt til pilarp.

- Når du søger efter en modtageregenskab, f.eks. Til, Fra, Cc eller Modtagere, kan du bruge en SMTP-adresse, et alias eller et vist navn til at angive en modtager. Du kan f.eks. bruge pilarp@contoso.com, pilarp eller "Pilar Pinilla".

- Du kan kun bruge præfikssøgninger. f.eks **. cat\**_ eller _* set\**_. Suffikssøgninger (_*\*kat), infikssøgninger** (**ct\***) og understrengssøgninger **(\*\*kat**) understøttes ikke.

- Når du søger efter en egenskab, skal du bruge dobbelte anførselstegn (""), hvis søgeværdien består af flere ord. Returnerer f.eks `subject:budget Q1` . meddelelser, der indeholder **budget** i emnelinjen, og som indeholder **Q1** et vilkårligt sted i meddelelsen eller i en af meddelelsesegenskaberne. Ved `subject:"budget Q1"` hjælp af returneres alle meddelelser, der **indeholder budget Q1** et vilkårligt sted i emnelinjen.

- Hvis du vil udelade indhold, der er markeret med en bestemt egenskabsværdi i søgeresultaterne, skal du placere et minustegn (-) før navnet på egenskaben. Udelader f.eks `-from:"Sara Davis"` . alle meddelelser, der er sendt af Sara Davis.

- Du kan eksportere elementer baseret på meddelelsestype. Hvis du f.eks. Skype eksportere samtaler og chatsamtaler i Microsoft Teams, skal du bruge syntaksen `kind:im`. Hvis du kun vil returnere mails, skal du bruge `kind:email`. Hvis du vil vende tilbage til chatsamtaler, møder og opkald Microsoft Teams, skal du bruge `kind:microsoftteams`.

- Som beskrevet tidligere skal du `/` , når du søger på websteder, tilføje de efterfølgende til slutningen af URL-adressen `path` , når du bruger egenskaben til kun at returnere elementer på et bestemt websted. Hvis du ikke medtager de efterfølgende , returneres `/`elementer fra et websted med et lignende stinavn også. Hvis du f.eks. bruger `path:sites/HelloWorld` så elementer fra websteder, der er `sites/HelloWorld_East` navngivet `sites/HelloWorld_West` eller også vil blive returneret. Hvis du kun vil returnere elementer fra HelloWorld-webstedet, skal du bruge `path:sites/HelloWorld/`.
