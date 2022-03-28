---
title: Tabellen AlertInfo i det avancerede søgeskema
description: Få mere at vide om påmindelsesgenereringshændelser i tabellen AlertInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrussel på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, AlertInfo, alarm, alvorsgrad, kategori, MITRE, ATT&CK, Microsoft Defender til slutpunkt, Microsoft Defender til Office 365, Microsoft Cloud App Security, MCAS og Microsoft Defender for Identity
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
ms.openlocfilehash: 0298b4f83ac748048215af4f5b1f8261a2a8c67c
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63597539"
---
# <a name="alertinfo"></a>AlertInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender



Tabellen `AlertInfo` i [det avancerede](advanced-hunting-overview.md) søgeskema indeholder oplysninger om beskeder fra Microsoft Defender til Slutpunkt, Microsoft Defender til Office 365, Microsoft Defender til skyapps og Microsoft Defender for Identity. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra denne tabel.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `AlertId` | `string` | Entydigt id for beskeden |
| `Title` | `string` | Beskedens titel |
| `Category` | `string` | Den type trusselsindikator eller aktivitet for brud, der identificeres af beskeden |
| `Severity` | `string` | Angiver den potentielle virkning (høj, mellem eller lav) af trusselsindikatoren eller brudaktiviteten identificeret af beskeden |
| `ServiceSource` | `string` | Produkt eller tjeneste, der gav beskedoplysningerne |
| `DetectionSource` | `string` | Registreringsteknologi eller sensor, der identificerede den væsentlig komponent eller aktivitet |
| `AttackTechniques` | `string` | MITRE ATT&CK-teknikker knyttet til den aktivitet, der udløste beskeden |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
