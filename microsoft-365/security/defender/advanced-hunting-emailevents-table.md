---
title: Tabellen EmailEvents i det avancerede jagtskema
description: Få mere at vide om hændelser, der er knyttet til Microsoft 365 mails i tabellen EmailEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, EmailEvents, netværksmeddelelses-id, afsender, modtager, vedhæftet id, vedhæftet fils navn, malware-dom, phishing-dom, antal vedhæftede filer, linkantal, URL-adresseantal
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
ms.openlocfilehash: f4456dc29f4d62703041b9c386aa7c9fa132695a
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667356"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

Tabellen `EmailEvents` i det [avancerede jagtskema](advanced-hunting-overview.md) indeholder oplysninger om hændelser, der involverer behandling af mails på Microsoft Defender for Office 365. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

> [!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `NetworkMessageId` | `string` | Entydigt id for mailen, der genereres af Microsoft 365 |
| `InternetMessageId` | `string` | Offentlig identifikator for den mail, der er angivet af det sendende mailsystem |
| `SenderMailFromAddress` | `string` | Afsendermailadresse i headeren MAIL FROM, også kendt som afsenderkonvolutten eller den Return-Path adresse |
| `SenderFromAddress` | `string` | Afsendermailadresse i fra-headeren, som er synlig for mailmodtagere på deres mailklienter |
| `SenderDisplayName` | `string` | Navnet på den afsender, der vises i adressekartoteket, typisk en kombination af et givet eller fornavn, et mellemnavn og et efternavn eller efternavn |
| `SenderObjectId` | `string` |Entydigt id for afsenderens konto i Azure AD |
| `SenderMailFromDomain` | `string` | Afsenderdomæne i headeren MAIL FROM, også kendt som afsenderkonvolutten eller den Return-Path adresse |
| `SenderFromDomain` | `string` | Afsenderdomæne i FROM-headeren, som er synligt for mailmodtagere på deres mailklienter |
| `SenderIPv4` | `string` | IPv4-adressen på den senest registrerede mailserver, der videresendte meddelelsen |
| `SenderIPv6` | `string` | IPv6-adressen på den senest registrerede mailserver, der videresendte meddelelsen |
| `RecipientEmailAddress` | `string` | Mailadresse på modtageren eller mailadresse på modtageren efter udvidelse af distributionsliste |
| `RecipientObjectId` | `string` | Entydigt id for mailmodtageren i Azure AD |
| `Subject` | `string` | Mailens emne |
| `EmailClusterId` | `string` | Identifikator for gruppen af lignende e-mails grupperet baseret på heuristisk analyse af deres indhold |
| `EmailDirection` | `string` | Retning for mailen i forhold til dit netværk: Indgående, Udgående, Intern organisation |
| `DeliveryAction` | `string` | Leveringshandling for mailen: Leveret, Uønsket, Blokeret eller Erstattet |
| `DeliveryLocation` | `string` | Placering, hvor mailen blev leveret: Indbakke/Mappe, Lokalt/Eksternt, Uønsket, Karantæne, Mislykket, Mistet, Slettede elementer |
| `ThreatTypes` | `string` | Dom fra mailfiltreringsstakken om, hvorvidt mailen indeholder malware, phishing eller andre trusler |
| `ThreatNames` | `string` |Registreringsnavn for malware eller andre trusler fundet |
| `DetectionMethods` | `string` | Metoder, der bruges til at registrere malware, phishing eller andre trusler, der findes i mailen |
| `ConfidenceLevel` | `string` | Liste over tillidsniveauer for spam- eller phishing-domme. For spam viser denne kolonne niveauet for spamsikkerhed (SCL), der angiver, om mailen blev sprunget over (-1), at den ikke er spam (0,1), at den er spam med moderat genkendelsessikkerhed (5,6), eller at den er spam med høj genkendelsessikkerhed (9). I forbindelse med phishing viser denne kolonne, om tillidsniveauet er "Høj" eller "Lav". |
| `EmailAction` | `string` | Endelig handling, der udføres på mailen baseret på filterbesigelse, politikker og brugerhandlinger: Flyt meddelelse til mappen Uønsket mail, Tilføj X-header, Rediger emne, Omdirigeringsmeddelelse, Slet meddelelse, Send til karantæne, Ingen handling udført, Bcc-meddelelse |
| `EmailActionPolicy` | `string` | Handlingspolitik, der trådte i kraft: Antispam high-confidence, Antispam, Antispam bulk mail, Antispam phishing, Anti-phishing domain impersonation, Anti-phishing user impersonation, Anti-phishing spoof, Anti-phishing graph impersonation, Antimalware, Pengeskab Attachments, Enterprise Transport Rules (ETR) |
| `EmailActionPolicyGuid` | `string` | Entydigt id for den politik, der bestemte den endelige mailhandling |
| `AttachmentCount` | `int` | Antal vedhæftede filer i mailen |
| `UrlCount` | `int` | Antallet af integrerede URL-adresser i mailen |
| `EmailLanguage` | `string` | Registreret sprog for mailindholdet |
| `Connectors` | `string` | Brugerdefinerede instruktioner, der definerer organisationens mailflow, og hvordan mailen blev distribueret |
| `OrgLevelAction` | `string` | Handling, der udføres på mailen som svar på overensstemmelser med en politik, der er defineret på organisationsniveau |
| `OrgLevelPolicy` | `string` | Organisationspolitik, der udløste den handling, der blev udført på mailen |
| `UserLevelAction` | `string` | Handling, der udføres på mailen som svar på match til en postkassepolitik, der er defineret af modtageren |
| `UserLevelPolicy` | `string` | Politik for slutbrugerpostkasse, der udløste den handling, der blev udført på mailen |
| `ReportId` | `long` | Hændelses-id baseret på en gentaget tæller. Hvis du vil identificere entydige hændelser, skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp. |
| `AuthenticationDetails` | `string` | Liste over bestået eller mislykket dom over godkendelsesprotokoller via mail, f.eks. DMARC, DKIM, SPF eller en kombination af flere godkendelsestyper (CompAuth) |

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
