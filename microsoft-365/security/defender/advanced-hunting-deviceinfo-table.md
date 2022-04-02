---
title: DeviceInfo-tabel i det avancerede søgeskema
description: Få mere at vide om OS, computernavn og andre computeroplysninger i DeviceInfo-tabellen i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, machineinfo, DeviceInfo, enhed, maskine, OS, platform, brugere
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
ms.openlocfilehash: 245a9aa11bcaf10ba6f3b8fe0fe429267a355560
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63603069"
---
# <a name="deviceinfo"></a>DeviceInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

Tabellen `DeviceInfo` i det [avancerede søgeskema](advanced-hunting-overview.md) indeholder oplysninger om enheder i organisationen, herunder OS-version, aktive brugere og computernavn. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `ClientVersion` | `string` | Version af slutpunktsagenten eller sensoren, der kører på computeren |
| `PublicIP` | `string` | Offentlig IP-adresse, der bruges af onboarded machine til at oprette forbindelse til Microsoft Defender for Endpoint-tjenesten. Dette kan være IP-adressen på selve computeren, en NAT-enhed eller en proxy |
| `OSArchitecture` | `string` | Arkitektur for det operativsystem, der kører på computeren |
| `OSPlatform` | `string` | Platform for operativsystemet, der kører på computeren. Dette angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7. |
| `OSBuild` | `string` | Buildversion af operativsystemet, der kører på computeren |
| `IsAzureADJoined` | `boolean` | Boolesk indikator for, om computeren er forbundet til Azure Active Directory |
| `AadDeviceId` | `string` | Entydigt id for enheden i Azure AD |
| `LoggedOnUsers` | `string` | Liste over alle brugere, der er logget på computeren på tidspunktet for hændelsen i JSON-matrixformat |
| `RegistryDeviceTag` | `string` | Computermærke tilføjet via registreringsdatabasen |
| `OSVersion` | `string` | Version af operativsystemet, der kører på computeren |
| `MachineGroup` | `string` | Maskinegruppen på computeren. Denne gruppe bruges af rollebaseret adgangskontrol til at bestemme adgang til computeren |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. For at identificere entydige hændelser skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp |
| `OnboardingStatus` | `string` | Angiver, om enheden i øjeblikket er onboardet eller ej til Microsoft Defender til slutpunkt, eller om enheden ikke understøttes |
|`AdditionalFields` | `string` | Yderligere oplysninger om hændelsen i JSON-matrixformat |
|`DeviceCategory` | `string` | Bredere klassificering, der grupperer visse enhedstyper under følgende kategorier: Slutpunkt, Netværksenhed, IoT, Ukendt |
|`DeviceType` | `string` | Enhedstype, der er baseret på formål og funktionalitet, f.eks. netværksenhed, arbejdsstation, server, mobil, spilkonsol eller printer |
|`DeviceSubType` | `string` | Yderligere ændring for visse typer enheder, f.eks. en mobilenhed kan være en tablet eller en smartphone; kun tilgængelig, hvis enhedsregistrering finder nok oplysninger om denne attribut |
|`Model` | `string` | Modelnavn eller -nummer på produktet fra leverandøren eller producenten, kun tilgængeligt, hvis enhedsregistrering finder nok oplysninger om denne attribut |
|`Vendor` | `string` | Navnet på produktleverandøren eller -producenten, der kun er tilgængelig, hvis enhedsregistrering finder nok oplysninger om denne attribut |
|`OSDistribution` | `string` | Fordeling af OS-platformen, f.eks. Ubuntu eller RedHat til Linux-platforme |
|`OSVersionInfo` | `string` | Flere oplysninger om os-versionen, f.eks. det populære navn, kodenavn eller versionsnummer |
|`MergedDeviceIds` | `string` | Tidligere enheds-iD'er, der er blevet tildelt den samme enhed |
|`MergedToDeviceId` | `string` | Det seneste enheds-id, der er tildelt en enhed |

Tabellen `DeviceInfo` indeholder enhedsoplysninger, der er baseret på heartbeats, som er periodiske rapporter eller signaler fra en enhed. Hvert 15. minut sender enheden en delvis heartbeat, der indeholder hyppigt ændrede attributter som `LoggedOnUsers`. En gang om dagen sendes en fuld heartbeat, der indeholder enhedens attributter.

Du kan bruge følgende eksempelforespørgsel til at få den seneste status for en enhed:

```kusto
// Get latest information on user/device
DeviceInfo
| where DeviceName == "example" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId 
```

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
