---
title: DeviceTvmSoftwareInventory i det avancerede jagtskema
description: Få mere at vide om lagerbeholdningen af software på dine enheder i tabellen DeviceTvmSoftwareInventory i det avancerede skema.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, trussel & håndtering af sikkerhedsrisici, TVM, enhedshåndtering, software, lager, sårbarheder, CVE-id, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: a9a17c6e336704cfe09e1c864e9700a4492e8c87
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592664"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

>[!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.


Tabellen `DeviceTvmSoftwareInventory` i det avancerede skema indeholder [lagerbeholdningen threat & Vulnerability Management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) af software, der aktuelt er installeret på enheder i dit netværk, herunder ophør af supportoplysninger. Du kan f.eks. lede efter begivenheder, der involverer enheder, der er installeret med en sårbar softwareversion. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

>[!NOTE]
> Tabellerne `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` og tabellerne har erstattet `DeviceTvmSoftwareInventoryVulnerabilities` tabellen. Sammen indeholder de to første tabeller flere kolonner, du kan bruge til at informere dine administrationsaktiviteter om vulnerablity eller lede efter følsomme enheder.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `OSPlatform` | `string` | Platform for operativsystemet, der kører på computeren. Dette angiver bestemte operativsystemer, herunder variationer inden for den samme familie, f.eks. Windows 11, Windows 10 og Windows 7. |
| `OSVersion` | `string` | Version af operativsystemet, der kører på computeren |
| `OSArchitecture` | `string` | Arkitektur for det operativsystem, der kører på computeren |
| `SoftwareVendor` | `string` | Navnet på softwareleverandøren |
| `SoftwareName` | `string` | Navnet på softwareproduktet |
| `SoftwareVersion` | `string` | Versionsnummer på softwareproduktet |
| `EndOfSupportStatus` | `string` | Angiver livscyklusfasen for softwareproduktet i forhold til datoen for den angivne slutdato for support (EOS) eller slutningen af levetid (EOL) |
| `EndOfSupportDate` | `string` | Dato for ophør af support (EOS) eller slutningen af levetid (EOL) for softwareproduktet |
| `ProductCodeCpe` | `string` | CPE for softwareproduktet eller "ikke tilgængeligt", hvis der ikke er nogen CPE |


## <a name="related-topics"></a>Relaterede emner

- [Proaktivt lede efter trusler](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over administration af & af sikkerhedsrisiko](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)