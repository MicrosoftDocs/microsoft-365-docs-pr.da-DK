---
title: Tabellen CloudAppEvents i det avancerede jagtskema
description: Få mere at vide om hændelser fra cloudapps og -tjenester i tabellen CloudAppEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, CloudAppEvents, Defender for Cloud Apps
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
ms.openlocfilehash: 77b4ebd42a8c105340d6d965380aa42b64ae6734
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664958"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Tabellen `CloudAppEvents` i det [avancerede jagtskema](advanced-hunting-overview.md) indeholder oplysninger om aktiviteter i forskellige cloudapps og -tjenester, der er omfattet af Microsoft Defender for Cloud Apps. Du kan se en komplet liste ved at gå til [De omfattede apps og tjenester](#apps-and-services-covered). Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

> [!IMPORTANT]
> Denne tabel indeholder oplysninger, der tidligere var tilgængelige i `AppFileEvents` tabellen. Fra og med den 7. marts 2021 skal brugere, der jagter filrelaterede aktiviteter i cloudtjenester på og efter denne dato, bruge tabellen `CloudAppEvents` i stedet. <br><br>Sørg for at søge efter forespørgsler og brugerdefinerede regler for registrering, der stadig bruger tabellen `AppFileEvents` , og rediger dem for at bruge `CloudAppEvents` tabellen. Du kan finde flere vejledninger om konvertering af berørte forespørgsler i [Hunt på tværs af aktiviteter i cloudapps med Microsoft 365 Defender avanceret jagt](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857).

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `ActionType` | `string` | Aktivitetstype, der udløste hændelsen |
| `Application` | `string` | Program, der udførte den registrerede handling |
| `ApplicationId` | `string` | Entydigt id for programmet |
| `AccountObjectId` | `string` | Entydigt id for kontoen i Azure Active Directory |
| `AccountId` | `string` | Et id for kontoen, som blev fundet af Microsoft Defender for Cloud Apps. Det kan være Azure Active Directory id, brugerens hovednavn eller andre id'er. |
| `AccountDisplayName` | `string` | Navnet på den kontobruger, der vises i adressekartoteket. Typisk en kombination af et givet eller fornavn, en melleminitiering og et efternavn eller efternavn. |
| `IsAdminOperation` | `string` | Angiver, om aktiviteten blev udført af en administrator |
| `DeviceType` | `string` | Enhedstype baseret på formål og funktionalitet, f.eks. "Netværksenhed", "Arbejdsstation", "Server", "Mobil", "Spillekonsol" eller "Printer" |
| `OSPlatform` | `string` | Platform for det operativsystem, der kører på enheden. Denne kolonne angiver specifikke operativsystemer, herunder variationer inden for samme familie, f.eks. Windows 11, Windows 10 og Windows 7. |
| `IPAddress` | `string` | IP-adresse, der er tildelt slutpunktet og bruges under relateret netværkskommunikation |
| `IsAnonymousProxy` | `string` | Angiver, om IP-adressen tilhører en kendt anonym proxy |
| `CountryCode` | `string` | Kode på to bogstaver, der angiver det land, hvor klientens IP-adresse er geolokaliseret |
| `City` | `string` | By, hvor klientens IP-adresse er geolokaliseret |
| `Isp` | `string` | Internetudbyder, der er knyttet til IP-adressen |
| `UserAgent` | `string` | Brugeragentoplysninger fra webbrowseren eller et andet klientprogram |
| `ActivityType` | `string` | Aktivitetstype, der udløste hændelsen |
| `ActivityObjects` | `dynamic` | Liste over objekter, f.eks. filer eller mapper, der var involveret i den registrerede aktivitet |
| `ObjectName` | `string` | Navnet på det objekt, som den registrerede handling blev anvendt på |
| `ObjectType` | `string` | Objekttype, f.eks. en fil eller mappe, som den registrerede handling blev anvendt på |
| `ObjectId` | `string` | Entydigt id for det objekt, som den registrerede handling blev anvendt på |
| `ReportId` | `string` | Entydigt id for hændelsen |
| `RawEventData` | `string` | Rådata om hændelser fra kildeprogrammet eller tjenesten i JSON-format |
| `AdditionalFields` | `dynamic` | Yderligere oplysninger om enheden eller hændelsen |
| `AccountType` | `string` | Type af brugerkonto, der angiver dens generelle rolle og adgangsniveauer, f.eks. Regular, System, Admin, DcAdmin, System, Application |
| `IsExternalUser` | `boolean` | Angiver, om en bruger på netværket ikke tilhører organisationens domæne |
| `IsImpersonated` | `boolean` | Angiver, om aktiviteten blev udført af én bruger for en anden (repræsenteret) bruger |
| `IPTags` | `dynamic` | Kundedefinerede oplysninger, der anvendes på bestemte IP-adresser og IP-adresseområder |
| `IPCategory` | `string` | Yderligere oplysninger om IP-adressen |
| `UserAgentTags` | `dynamic` | Du kan få flere oplysninger fra Microsoft Defender for Cloud Apps i en kode i feltet brugeragent. Kan have en af følgende værdier: Oprindelig klient, Forældet browser, Forældet operativsystem, Robot |

## <a name="apps-and-services-covered"></a>Omfattede apps og tjenester

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

- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
