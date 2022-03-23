---
title: Tabellen CloudAppEvents i det avancerede jagtskema
description: Få mere at vide om begivenheder fra skyapps og -tjenester i tabellen CloudAppEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, CloudAppEvents, Defender til skyapps
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: daed3fb87aab498cdf91247a59e48af685aed010
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/28/2021
ms.locfileid: "63593488"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender



Tabellen `CloudAppEvents` i det avancerede [jagtskema indeholder](advanced-hunting-overview.md) oplysninger om aktiviteter i forskellige skyapps og -tjenester, der er dækket af Microsoft Defender til skyapps. Du kan få en komplet liste ved at gå [til De apps og tjenester, der er dækket](#apps-and-services-covered). Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel. 

>[!IMPORTANT]
>Denne tabel indeholder oplysninger, der plejede at være tilgængelige i `AppFileEvents` tabellen. Pr. 7. marts 2021 bør brugere, der går på jagt efter filrelaterede aktiviteter i skytjenester på og efter denne dato, bruge tabellen i `CloudAppEvents` stedet. <br><br>Sørg for at søge efter forespørgsler og brugerdefinerede registreringsregler, der stadig bruger tabellen `AppFileEvents` , og rediger dem for at bruge `CloudAppEvents` tabellen. Du kan finde flere vejledninger til konvertering af berørte forespørgsler i Hunt på tværs [af appaktiviteter i skyen med Microsoft 365 Defender avanceret jagt](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857).


Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `ActionType` | `string` | Aktivitetstype, der udløste begivenheden |
| `Application` | `string` | Program, der udførte den optagede handling |
| `ApplicationId` | `string` | Entydigt id for programmet |
| `AccountObjectId` | `string` | Entydigt id for kontoen i Azure Active Directory |
| `AccountId` | `string` | En identifikator for kontoen, som blev fundet af Microsoft Defender til skyapps. Kunne være Azure Active Directory-id, brugerens hovednavn eller andre identifikatorer. |
| `AccountDisplayName` | `string` | Navnet på den kontobruger, der vises i adressekartoteket. Typisk en kombination af et givet navn eller fornavn, et mellemnavn og efternavn. |
| `IsAdminOperation` | `string` | Angiver, om aktiviteten blev udført af en administrator |
| `DeviceType` | `string` | Enhedstype baseret på formål og funktionalitet, f.eks. "Netværksenhed", "Arbejdsstation", "Server", "Mobil", "Spilkonsol" eller "Printer" | 
| `OSPlatform` | `string` | Platform for operativsystemet, der kører på enheden. Denne kolonne angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7. |
| `IPAddress` | `string` | IP-adresse, der er tildelt slutpunktet og brugt under relateret netværkskommunikation |
| `IsAnonymousProxy` | `string` | Angiver, om IP-adressen tilhører en kendt anonym proxy |
| `CountryCode` | `string` | Kode på to bogstaver, der angiver det land, hvor klientens IP-adresse er geolokeret |
| `City` | `string` | By, hvor klientens IP-adresse er geolokeret |
| `Isp` | `string` | Internet serviceudbyder (ISP), der er knyttet til IP-adressen |
| `UserAgent` | `string` | Oplysninger om brugeragenter fra webbrowseren eller et andet klientprogram |
| `ActivityType` | `string` | Aktivitetstype, der udløste begivenheden |
| `ActivityObjects` | `dynamic` | Liste over objekter, f.eks. filer eller mapper, der var involveret i den optagede aktivitet |
| `ObjectName` | `string` | Navnet på det objekt, som den optagede handling blev anvendt på |
| `ObjectType` | `string` | Objekttype, f.eks. en fil eller en mappe, som den optagede handling blev anvendt på |
| `ObjectId` | `string` | Entydigt id for det objekt, som den optagede handling blev anvendt på |
| `ReportId` | `string` | Entydigt id for hændelsen |
| `RawEventData` | `string` | Rå hændelsesoplysninger fra kildeprogrammet eller kildetjenesten i JSON-format |
| `AdditionalFields` | `dynamic` | Yderligere oplysninger om enheden eller hændelsen |
| `AccountType` | `string` | Brugerkontotype, der angiver dens generelle rolle og adgangsniveauer, f.eks. Normal, System, Administrator, DcAdmin, System, Program | 
| `IsExternalUser` | `boolean` | Angiver, om en bruger inden for netværket ikke tilhører organisationens domæne | 
| `IsImpersonated` | `boolean` | Angiver, om aktiviteten blev udført af en bruger for en anden (efterligning) bruger | 
| `IPTags` | `dynamic` | Kundedefinerede oplysninger anvendt på bestemte IP-adresser og IP-adresseintervaller | 
| `IPCategory` | `string` | Yderligere oplysninger om IP-adressen | 
| `UserAgentTags` | `dynamic` | Du kan finde flere oplysninger fra Microsoft Defender til skyapps i et mærke i feltet brugeragent. Kan have en af følgende værdier: Oprindelig klient, Forældet browser, Forældet operativsystem, Robot | 

## <a name="apps-and-services-covered"></a>Apps og tjenester, der er dækket

- Dropbox
- Dynamics 365
- Exchange Online
- Microsoft Teams
- OneDrive for Business
- Power Automate
- Power BI
- SharePoint Online
- Skype for Business
- Office 365
- Yammer 

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
