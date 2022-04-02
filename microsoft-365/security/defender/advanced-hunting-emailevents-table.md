---
title: Tabellen EmailEvents i det avancerede jagtskema
description: Få mere at vide om begivenheder, der Microsoft 365 mails i EmailEvents-tabellen i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrussel på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, EmailEvents, netværksmeddelelses-id, afsender, modtager, vedhæftet fil-id, navn på vedhæftet fil, malwarekonstation, phishingkonstation, antal vedhæftede filer, antal links, URL-antal
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: baf6e8d6d896e31b5092f7d2b8948bb7771382bd
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63603137"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

Tabellen `EmailEvents` i det avancerede [søgeskema](advanced-hunting-overview.md) indeholder oplysninger om hændelser, der vedrører behandlingen af mails på Microsoft Defender Office 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `NetworkMessageId` | `string` | Entydigt id for den mail, der genereres af Microsoft 365 |
| `InternetMessageId` | `string` | Offentligt id for den mail, der er angivet af det afsendende mailsystem |
| `SenderMailFromAddress` | `string` | Afsenderens mailadresse i mailens FROM-brevhoved, også kaldet konvolutafsenderen eller Return-Path adressen |
| `SenderFromAddress` | `string` | Afsendermailadressen i overskriften FROM, som er synlig for mailmodtagere på deres mailklienter |
| `SenderDisplayName` | `string` | Navnet på afsenderen, der vises i adressekartoteket, typisk en kombination af et givet eller fornavn, en indledende mellemnavn og et efternavn eller efternavn |
| `SenderObjectId` | `string` |Entydigt id for afsenderens konto i Azure AD |
| `SenderMailFromDomain` | `string` | Afsenderdomæne i MAIL FROM-overskriften, også kaldet konvolutafsenderen eller Return-Path adresse |
| `SenderFromDomain` | `string` | Afsenderdomæne i brevhovedet FROM, som er synligt for mailmodtagere på deres mailklienter |
| `SenderIPv4` | `string` | IPv4-adressen på den senest registrerede mailserver, der viderestillede meddelelsen |
| `SenderIPv6` | `string` | IPv6-adressen på den senest registrerede mailserver, der viderestillede meddelelsen |
| `RecipientEmailAddress` | `string` | Mailadressen på modtageren eller modtagerens mailadresse efter udvidelse af distributionslisten |
| `RecipientObjectId` | `string` | Entydigt id for mailmodtageren i Azure AD |
| `Subject` | `string` | Mailens emne |
| `EmailClusterId` | `string` | Id for den gruppe af ensartede mails, der er grupperet baseret på en heuristisk analyse af indholdet |
| `EmailDirection` | `string` | Retning af mailen i forhold til dit netværk: Indgående, udgående, Intra-org |
| `DeliveryAction` | `string` | Leveringshandling for mailen: Leveret, uønsket, blokeret eller erstattet |
| `DeliveryLocation` | `string` | Placering, hvor mailen blev leveret: Indbakke/mappe, Lokal/Ekstern, Uønsket, Karantæne, Mislykket, Tabt, Slettede elementer |
| `ThreatTypes` | `string` | Konklusion fra mailfiltreringsstakken for, om mailen indeholder malware, phishing eller andre trusler |
| `ThreatNames` | `string` |Registreringsnavn for malware eller andre trusler fundet |
| `DetectionMethods` | `string` | Metoder til at detektere malware, phishing eller andre trusler, der findes i mailen |
| `ConfidenceLevel` | `string` | Liste over tillidsniveauer for uønsket post eller phishing. For spam viser denne kolonne det tillidsniveau for spam, der angiver, om mailen blev sprunget over (-1), der blev fundet ikke er spam (0,1), fundet at være spam med moderat tillid (5,6) eller fundet at være spam med høj tillid (9). For phishing viser denne kolonne, om tillidsniveauet er "Høj" eller "Lav". |
| `EmailAction` | `string` | Sidste handling, der er taget på mailen baseret på filterets konklusion, politikker og brugerhandlinger: Flyt meddelelsen til mappen med uønsket mail, Tilføj X-brevhoved, Rediger emne, Omdiriger meddelelse, Slet meddelelse, send til karantæne, Der er ikke taget nogen handling, Bcc-meddelelse |
| `EmailActionPolicy` | `string` | Handlingspolitik, der er blevet gennemført: Antispam med høj tillid, Antispam, massemails til antispam, phishing mod uønsket phishing, efterligning af domænet i antispam, bruger efterligning af phishing, uønsket phishing-graf, antimalware, Pengeskab vedhæftede filer, Enterprise Transport Rules (ETR) |
| `EmailActionPolicyGuid` | `string` | Entydigt id for den politik, der bestemte den endelige mailhandling |
| `AttachmentCount` | `int` | Antal vedhæftede filer i mailen |
| `UrlCount` | `int` | Antal integrerede URL-adresser i mailen |
| `EmailLanguage` | `string` | Det registrerede sprog for mailindholdet |
| `Connectors` | `string` | Brugerdefinerede instruktioner, der definerer organisatorisk mailflow, og hvordan mailen blev distribueret |
| `OrgLevelAction` | `string` | Handling, der er foretaget på mailen som svar på matches til en politik, der er defineret på organisationsniveau |
| `OrgLevelPolicy` | `string` | Organisationspolitik, der udløste den handling, der blev taget på mailen |
| `UserLevelAction` | `string` | Handling, der er foretaget på mailen som svar på matches til en postkassepolitik defineret af modtageren |
| `UserLevelPolicy` | `string` | Slutbrugerens postkassepolitik, der udløste den handling, der blev taget på mailen |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. Denne kolonne skal bruges sammen med kolonnerne DeviceName og Timetamp til at identificere entydige hændelser. |
| `AuthenticationDetails` | `string` | Liste over bestået eller mislykket konklusion i forbindelse med mailgodkendelsesprotokoller som DMARC, DKIM, SPF eller en kombination af flere godkendelsestyper (CompAuth) |

## <a name="related-topics"></a>Relaterede emner

- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
