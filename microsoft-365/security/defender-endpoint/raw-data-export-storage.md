---
title: Stream Microsoft Defender til slutpunktshændelser til din Storage-konto
description: Få mere at vide om, hvordan du konfigurerer Microsoft Defender til slutpunkt for at streame Avancerede rævebegivenheder til din Storage konto.
keywords: rå dataeksport, streaming-API, API, Hændelseshubs, Azure-lager, lagerkonto, Avanceret jagt, rå datadeling
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: a9db98456cc971b4ac4179cd4f3460dfe2137b91
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/20/2022
ms.locfileid: "63597549"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Konfigurer Microsoft Defender til slutpunkt for at streame Advanced Hunting-begivenheder til din Storage-konto

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Før du begynder

1. Opret en [Storage-konto](/azure/storage/common/storage-account-overview) i din lejer.

2. Log på din [Azure-lejer](https://ms.portal.azure.com/), gå til Abonnementer **> Dit abonnement > ressourceudbydere > Registrer dig til Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Aktivér rå datastreaming

1. Log på [Microsoft 365 Defender](https://security.microsoft.com) ***Global Administrator** _ eller _*_Security Administrator_**.

2. Gå til [siden med indstillinger for dataeksport](https://security.microsoft.com/interoperability/dataexport) Microsoft 365 Defender.

3. Klik på **Tilføj indstillinger for dataeksport**.

4. Vælg et navn til de nye indstillinger.

5. Vælg **Videressendelse af begivenheder for Azure Storage**.

6. Skriv dit **Storage-kontoressource-id**. For at få dit **Storage-kontoressource-id** skal du gå til din Storage-kontoside på fanen Egenskaber for [Azure-portal](https://ms.portal.azure.com/) \> \> kopiere teksten under **Storage for kontoressource-id**:

   :::image type="content" alt-text="Billede af id for hændelseshubressourcen ID1." source="images/storage-account-resource-id.png" lightbox="images/storage-account-resource-id.png":::

7. Vælg de hændelser, du vil streame, og klik på **Gem**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Skemaet for hændelserne i Storage konto

- Der oprettes en blobbeholder for hver hændelsestype:

  :::image type="content" alt-text="Billede af id for hændelseshubressource-id2." source="images/storage-account-event-schema.png" lightbox="images/storage-account-event-schema.png":::

- Skemaet for hver række i en blob er følgende JSON:

  ```json
  {
      "time": "<The time WDATP received the event>"
      "tenantId": "<Your tenant ID>"
      "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
      "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- Hver blob indeholder flere rækker.

- Hver række indeholder navnet på begivenheden, tidspunktet, hvor Defender for Endpoint modtog begivenheden, den lejer, den tilhører (du får kun begivenheder fra din lejer), og begivenheden i JSON-format i en egenskab kaldet "egenskaber".

- Du kan finde flere oplysninger om skemaet for Microsoft Defender til slutpunktshændelser i [Oversigt over Avanceret jagt](advanced-hunting-overview.md).

- I Avanceret jagt har **tabellen DeviceInfo** en kolonne med **navnet MachineGroup** , som indeholder gruppen af enheden. Her vil alle begivenheder også være pyntet med denne kolonne. Se [Enhedsgrupper for](machine-groups.md) at få flere oplysninger.

## <a name="data-types-mapping"></a>Tilknytning af datatyper

For at få datatyperne for vores hændelsesegenskaber skal du gøre følgende:

1. Log på Microsoft 365 Defender[,](https://security.microsoft.com) og gå til [siden Avanceret jagt](https://security.microsoft.com/hunting-package).

2. Kør følgende forespørgsel for at få tilknytningen af datatyperne for hver hændelse:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Her er et eksempel på hændelsen Enhedsoplysninger:

  ![Billede af id for begivenhedshubressource-id3.](images/data-types-mapping-query.png)

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Avanceret jagt](advanced-hunting-overview.md)
- [Microsoft Defender til Endpoint Streaming API](raw-data-export.md)
- [Stream Microsoft Defender til slutpunktshændelser til din Azure-lagerkonto](raw-data-export-storage.md)
- [Azure Storage firmadokumentation](/azure/storage/common/storage-account-overview)
