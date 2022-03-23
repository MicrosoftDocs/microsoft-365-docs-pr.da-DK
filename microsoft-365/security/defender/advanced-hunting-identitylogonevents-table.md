---
title: IdentityLogonEvents-tabel i det avancerede jagtskema
description: Få mere at vide om godkendelseshændelser, der er registreret af Active Directory i tabellen IdentityLogonEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, IdentityLogonEvents, Azure AD, Active Directory, Microsoft Defender til identitet, identiteter
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
ms.openlocfilehash: c5f8de4015ed8b031d3f228f29a6a0d63a57bf2a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63591295"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Tabellen `IdentityLogonEvents` i det avancerede [](advanced-hunting-overview.md) jagtskema indeholder oplysninger om godkendelsesaktiviteter, der er foretaget via dit lokale Active Directory registreret af Microsoft Defender til identitet og godkendelsesaktiviteter, der er relateret til Microsoft-onlinetjenester, som er registreret af Microsoft Defender til skyapps. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

>[!TIP]
> Du kan finde detaljerede oplysninger om de hændelsestyper (`ActionType` værdier), der understøttes af en tabel, ved at bruge den indbyggede skemareference, der er tilgængelig i Defender for Cloud.

>[!NOTE]
>Denne tabel omhandler Azure Active Directory (Azure AD) logonaktiviteter, der registreres af Defender til skyapps, særligt interaktive logon- og godkendelsesaktiviteter ved hjælp af ActiveSync og andre ældre protokoller. Ikke-interaktive logons, der ikke er tilgængelige i denne tabel, kan vises i Azure AD-overvågningsloggen. [Få mere at vide om at oprette forbindelse mellem Defender og skyapps Microsoft 365](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `ActionType` | `string` | Aktivitetstype, der udløste hændelsen. Se [skemareferencen i portalen for at](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) få mere at vide |
| `Application` | `string` | Program, der udførte den optagede handling |
| `LogonType` | `string` | Logonsessionstype, mere specifikt:<br><br> - **Interaktiv** – Brugeren interagerer fysisk med maskinen ved hjælp af det lokale tastatur og den lokale skærm<br><br> - **Fjerninter interaktive logons (RDP)** – Brugeren interagerer med computeren eksternt ved hjælp af Fjernskrivebord, TerminalTjenester, Fjernsupport eller andre RDP-klienter<br><br> - **Netværk** – Session startet, når computeren åbnes ved hjælp af PsExec, eller når delte ressourcer på computeren, f.eks. printere og delte mapper, tilgås<br><br> - **Batch** – Session startet af planlagte opgaver<br><br> - **Tjeneste** – session startet af tjenester, når de starter |
| `Protocol` | `string` | Anvendt netværksprotokol |
| `FailureReason` | `string` | Oplysninger, der forklarer, hvorfor den registrerede handling mislykkedes |
| `AccountName` | `string` | Brugernavn på kontoen |
| `AccountDomain` | `string` | Kontoens domæne |
| `AccountUpn` | `string` | Brugerens hovednavn (UPN) for kontoen |
| `AccountSid` | `string` | Kontoens sikkerheds-id (SID) |
| `AccountObjectId` | `string` | Entydigt id for kontoen i Azure AD |
| `AccountDisplayName` | `string` | Navnet på den kontobruger, der vises i adressekartoteket. Typisk en kombination af et givet navn eller fornavn, et mellemnavn og efternavn. |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn for enheden |
| `DeviceType` | `string` | Enhedstype |
| `OSPlatform` | `string` | Platform for operativsystemet, der kører på computeren. Dette angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7. |
| `IPAddress` | `string` | IP-adresse, der er tildelt slutpunktet og brugt under relateret netværkskommunikation |
| `Port` | `string` | TCP-port, der bruges under kommunikation |
| `DestinationDeviceName` | `string` | Navnet på den enhed, der kører det serverprogram, der behandler den optagede handling |
| `DestinationIPAddress` | `string` | IP-adressen på den enhed, der kører det serverprogram, der behandler den optagede handling |
| `DestinationPort` | `string` | Destinationsport for relateret netværkskommunikation |
| `TargetDeviceName` | `string` | Fuldt kvalificeret domænenavn for den enhed, som den optagede handling blev anvendt på |
| `TargetAccountDisplayName` | `string` | Visningsnavnet for den konto, som den registrerede handling blev anvendt på |
| `Location` | `string` | By, land eller anden geografisk placering, der er knyttet til begivenheden |
| `Isp` | `string` | Internetudbyder (ISP serviceudbyder), der er knyttet til slutpunkts-IP-adressen |
| `ReportId` | `long` | Entydigt id for hændelsen |
| `AdditionalFields` | `string` | Yderligere oplysninger om enheden eller hændelsen |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
