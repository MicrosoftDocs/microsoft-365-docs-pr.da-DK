---
title: Stream Microsoft 365 Defender begivenheder til din Storage-konto
description: Få mere at vide om, hvordan Microsoft 365 Defender til at streame Avancerede rævebegivenheder til din Storage konto.
keywords: rå dataeksport, streaming-API, API, Hændelseshubs, Azure-lager, lagerkonto, Avanceret jagt, rå datadeling
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 159b4a41d423c2a7af3d367185e29af35a378b6b
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/15/2021
ms.locfileid: "63597963"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Konfigurer Microsoft 365 Defender at streame avancerede rævebegivenheder til din Storage-konto

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Før du begynder

1. Opret en [Storage-konto](/azure/storage/common/storage-account-overview) i din lejer.

2. Log på din [Azure-lejer](https://ms.portal.azure.com/), gå til **Abonnementer > Dit abonnement > ressourceudbydere > registrere dig til Microsoft.Insights**.

## <a name="enable-raw-data-streaming"></a>Aktivér rå datastreaming

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> ***Global Administrator** _ eller _*_Security Administrator_**.

2. Gå til **Indstillinger** \> **Microsoft 365 Defender** \> **Streaming API**. Hvis du vil gå direkte til **siden Streaming API** , skal du bruge <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. Klik **på Tilføj**.

4. I pop **op-menuen Tilføj nye Streaming API-indstillinger** , der vises, skal du konfigurere følgende indstillinger:
   1. **Navn**: Vælg et navn til de nye indstillinger.
   2. Vælg **Videressendelse af begivenheder for Azure Storage**.
   3. I feltet **Storage for Ressourcekonto, der** vises, skal du skrive dit **Storage firmaressource-id**. Hvis du vil have **dit** Storage-kontoressource-id, skal du åbne Azure-portalen <https://portal.azure.com>på , klikke på **Storage-konti** \> \> gå til fanen Egenskaber og kopiere teksten under **Storage Kontoressource-id**.

      ![Billede af id for hændelseshubressourcen ID1.](../defender-endpoint/images/storage-account-resource-id.png)

   4. Tilbage i pop **op-menuen Tilføj nye Streaming API-indstillinger** skal du vælge **de hændelsestyper** , du vil streame.

   Klik på Send, når du er **færdig**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Skemaet for hændelserne i Storage konto

- Der oprettes en blobbeholder for hver hændelsestype:

  ![Billede af id for hændelseshubressource-id2.](../defender-endpoint/images/storage-account-event-schema.png)

- Skemaet for hver række i en blob er følgende JSON:

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- Hver blob indeholder flere rækker.

- Hver række indeholder navnet på begivenheden, tidspunktet, hvor Defender for Endpoint modtog begivenheden, den lejer, den tilhører (du får kun begivenheder fra din lejer), og begivenheden i JSON-format i en egenskab kaldet "egenskaber".

- Du kan finde flere oplysninger om skemaet for Microsoft 365 Defender i Oversigt [over Avanceret ræveing](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>Tilknytning af datatyper

For at få datatyperne for vores hændelsesegenskaber skal du gøre følgende:

1. Log på en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender og</a> gå til **En avanceret jagt**\>. Brug <security.microsoft.com/advanced-hunting> **for at gå** direkte til <security.microsoft.com/advanced-hunting>.

2. På fanen **Forespørgsel skal** du køre følgende forespørgsel for at få tilknytningen af datatyperne for hver hændelse:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Her er et eksempel på hændelsen Enhedsoplysninger:

  ![Billede af id for begivenhedshubressource-id3.](../defender-endpoint/images/machine-info-datatype-example.png)

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Avanceret jagt](../defender/advanced-hunting-overview.md)
- [Microsoft 365 Defender Streaming API](streaming-api.md)
- [Stream Microsoft 365 Defender begivenheder til din Azure-lagerkonto](streaming-api-storage.md)
- [Azure Storage firmadokumentation](/azure/storage/common/storage-account-overview)
