---
title: Stream Microsoft 365 Defender hændelser til din lagerkonto
description: Få mere at vide om, hvordan du konfigurerer Microsoft 365 Defender til at streame avancerede jagthændelser til din lagerkonto.
keywords: rå dataeksport, streaming-API, API, Event Hubs, Azure Storage, lagerkonto, Avanceret jagt, rådatadeling
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
ms.openlocfilehash: 0f5195e5a74395073267fd4df87f077c6a1d5f20
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530570"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>Konfigurer Microsoft 365 Defender til at streame hændelser for avanceret jagt til din lagerkonto

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Før du begynder

1. Opret en [lagerkonto](/azure/storage/common/storage-account-overview) i din lejer.

2. Log på din [Azure-lejer](https://ms.portal.azure.com/), gå til **Abonnementer > Dit abonnement > Ressourceudbydere > Tilmeld dig Microsoft.Insights**.

### <a name="add-contributor-permissions"></a>Tilføj bidragydertilladelser

Når lagerkontoen er oprettet, skal du:

1. Definer den bruger, der skal logge på Microsoft 365 Defender som bidragyder.

    Gå til **Lagerkonto > Adgangskontrol (IAM) > Tilføj** og bekræft under **Rolletildelinger**.

## <a name="enable-raw-data-streaming"></a>Aktivér rå datastreaming

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> som en ***Global Administrator** _ eller _*_Sikkerhedsadministrator_**.

2. Gå til **Indstillinger** \> **Microsoft 365 Defender** \> **Streaming-API**. Hvis du vil gå direkte til siden **Streaming-API** , skal du bruge <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. Klik på **Tilføj**.

4. I pop op-vinduet **Tilføj nye streaming-API-indstillinger** , der vises, skal du konfigurere følgende indstillinger:
   1. **Navn**: Vælg et navn til de nye indstillinger.
   2. Vælg **Videresend hændelser til Azure Storage**.
   3. I feltet **Ressource-id for lagerkonto** , der vises, skal du skrive **ressource-id'et for din lagerkonto**. Hvis du vil hente **ressource-id'et for din lagerkonto**, skal du åbne Azure Portal på <https://portal.azure.com>, klikke på **Lagerkonti** \> gå til fanen \> Egenskaber kopiere teksten under **Ressource-id for lagerkonto**.

      :::image type="content" source="../defender-endpoint/images/storage-account-resource-id.png" alt-text="Et ressource-id for en lagerkonto" lightbox="../defender-endpoint/images/storage-account-resource-id.png":::

   4. Tilbage på pop op-vinduet **Tilføj nye streaming-API-indstillinger** skal du vælge de **hændelsestyper** , du vil streame.

   Klik på **Send**, når du er færdig.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Skemaet for hændelserne på lagerkontoen

- Der oprettes en blobobjektbeholder for hver hændelsestype:

  :::image type="content" source="../defender-endpoint/images/storage-account-event-schema.png" alt-text="Eksempel på en blobobjektbeholder" lightbox="../defender-endpoint/images/storage-account-event-schema.png":::

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

- Hver række indeholder hændelsesnavnet, det tidspunkt, hvor Defender for Endpoint modtog hændelsen, den lejer, den tilhører (du får kun hændelser fra din lejer) og hændelsen i JSON-format i en egenskab med navnet "egenskaber".

- Du kan finde flere oplysninger om skemaet for Microsoft 365 Defender begivenheder under [Oversigt over avanceret jagt](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>Tilknytning af datatyper

Hvis du vil hente datatyperne for vores hændelsesegenskaber, skal du gøre følgende:

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> og gå til **Jagt** \> **Avanceret jagt**. Hvis du vil gå direkte til siden **Avanceret jagt** , skal du bruge <security.microsoft.com/advanced-hunting>.

2. Kør følgende forespørgsel under fanen **Forespørgsel** for at hente tilknytningen af datatyper for hver hændelse:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Her er et eksempel på hændelsen Enhedsoplysninger:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Et eksempel på en forespørgsel om enhedsoplysninger" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="monitoring-created-resources"></a>Overvågning af oprettede ressourcer

Du kan overvåge de ressourcer, der oprettes af streaming-API'en, ved hjælp af **Azure Monitor**. Du kan få flere oplysninger under [Overvåg destinationer – Azure Monitor | Microsoft Docs](/azure/azure-monitor/logs/logs-data-export?tabs=portal#monitor-destinations).

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over avanceret jagt](../defender/advanced-hunting-overview.md)
- [api til Microsoft 365 Defender streaming](streaming-api.md)
- [Stream Microsoft 365 Defender hændelser til din Azure Storage-konto](streaming-api-storage.md)
- [Dokumentation til Azure Storage-konto](/azure/storage/common/storage-account-overview)
