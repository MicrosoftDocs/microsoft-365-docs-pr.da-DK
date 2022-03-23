---
title: DeviceAlertEvents-tabel i det avancerede jagtskema
description: Få mere at vide om påmindelsesgeneratorbegivenheder i tabellen DeviceAlertEvents i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler, mdatp, microsoft defender atp, microsoft defender for slutpunkt, wdatp-søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, beskrivelse, DeviceAlertEvents, alarm, alvorsgrad, kategori
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/22/2020
ms.technology: mde
ms.openlocfilehash: 32dbff60a37c31cdbfd492eb5d746a10d9b7a185
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593515"
---
# <a name="devicealertevents"></a>DeviceAlertEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Tabellen `DeviceAlertEvents` i det [avancerede søgeskema](advanced-hunting-overview.md) indeholder oplysninger om beskeder i Microsoft 365 Defender. Brug denne reference til at oprette forespørgsler, der returnerer oplysninger fra tabellen.

Hvis du vil have oplysninger om andre tabeller i det avancerede jagtskema, skal du [se den avancerede reference til jagtskemaet](advanced-hunting-schema-reference.md).

|Kolonnenavn|Datatype|Beskrivelse|
|---|---|---|
|`AlertId`|streng|Entydigt id for beskeden|
|`Timestamp`|datetime|Dato og klokkeslæt for, hvornår begivenheden blev optaget|
|`DeviceId`|streng|Entydigt id for enheden i tjenesten|
|`DeviceName`|streng|Fuldt kvalificeret domænenavn for enheden|
|`Severity`|streng|Angiver den potentielle virkning (høj, mellem eller lav) af trusselsindikatoren eller brudaktiviteten identificeret af beskeden|
|`Category`|streng|Den type trusselsindikator eller aktivitet for brud, der identificeres af beskeden|
|`Title`|streng|Beskedens titel|
|`FileName`|streng|Navnet på den fil, som den optagede handling blev anvendt på|
|`SHA1`|streng|SHA-1 i den fil, som den optagede handling blev anvendt på|
|`RemoteUrl`|streng|URL-adressen eller det fulde domænenavn, der blev knyttet til|
|`RemoteIP`|streng|IP-adresse, der blev knyttet til|
|`AttackTechniques`|streng|MITRE ATT&CK-teknikker knyttet til den aktivitet, der udløste beskeden|
|`ReportId`|lang|Hændelses-id baseret på en gentagende tæller. Hvis du vil identificere entydige hændelser, skal denne kolonne bruges sammen med kolonnerne `DeviceName` `Timestamp`|
|`Table`|streng|Tabel, der indeholder oplysninger om begivenheden|

## <a name="related-topics"></a>Relaterede emner

- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Forstå skemaet](advanced-hunting-schema-reference.md)
