---
title: Stream Microsoft 365 Defender hændelser til Azure Event Hubs
description: Få mere at vide om, hvordan du konfigurerer Microsoft 365 Defender til at streame avancerede jagthændelser til dine Event Hubs.
keywords: rå dataeksport, streaming-API, API, Azure Event Hubs, Azure Storage, lagerkonto, Avanceret jagt, deling af rådata
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
ms.openlocfilehash: 9cae28cc69d67bb18058e2c81cd8235ffce79997
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754394"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Konfigurer Microsoft 365 Defender til at streame avancerede jagthændelser til din Azure Event Hub

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="prerequisites"></a>Forudsætninger

Før du konfigurerer Microsoft 365 Defender til at streame data til Event Hubs, skal du sikre, at følgende forudsætninger er opfyldt:

1. Opret en Event Hubs (du kan få flere oplysninger under [Konfigurer Event Hubs](configure-event-hub.md#set-up-event-hubs)).

2. Oprettelse af et Event Hubs-navneområde (du kan få flere oplysninger under [Konfigurer Event Hubs-navneområdet](configure-event-hub.md#set-up-event-hubs-namespace)).

3. Føj tilladelser til den enhed, der har rettighederne som **bidragyder** , så denne enhed kan eksportere data til Event Hubs. Du kan få flere oplysninger om tilføjelse af tilladelser under [Tilføj tilladelser](configure-event-hub.md#add-permissions)

> [!NOTE]
> Streaming-API'en kan integreres enten via Event Hubs eller Azure Storage-konto.

## <a name="enable-raw-data-streaming"></a>Aktivér rå datastreaming

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> som en ***Global Administrator** _ eller _*_Sikkerhedsadministrator_**.

2. Gå til [siden Med indstillinger for streaming-API](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. Klik på **Tilføj**.

4. Vælg et navn til de nye indstillinger.

5. Vælg **Videresend hændelser til Azure Event Hub**.

6. Du kan vælge, om du vil eksportere hændelsesdataene til en enkelt Event Hub, eller om du vil eksportere hver hændelsestabel til en anden Event Hubs i dit Event Hubs-navneområde.

7. Hvis du vil eksportere hændelsesdataene til en enkelt Event Hub, skal du angive dit **Event Hub-navn** og dit **Event Hub-ressource-id**.

   Hvis du vil hente dit **Event Hub-ressource-id**, skal du gå til navneområdet for Azure Event Hubs under fanen **Azure-egenskaber** [](https://ms.portal.azure.com/) >  > kopiere teksten under **Ressource-id**:

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="Et Event Hub-ressource-id" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. Gå til [De understøttede Microsoft 365 Defender hændelsestyper i API'en til hændelsesstreaming](supported-event-types.md) for at gennemse supportstatussen for hændelsestyper i Microsoft 365 Streaming-API'en.

9. Vælg de hændelser, du vil streame, og klik på **Gem**.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>Skemaet for hændelserne i Azure Event Hub

```JSON
{
   "records": [
               {
                  "time": "<The time Microsoft 365 Defender received the event>"
                  "tenantId": "<The Id of the tenant that the event belongs to>"
                  "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                  "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
               }
               ...
            ]
}
```

- Hver Event Hubs-meddelelse i Azure Event Hubs indeholder en liste over poster.

- Hver post indeholder hændelsesnavnet, det tidspunkt, Microsoft 365 Defender modtog hændelsen, den lejer, den tilhører (du får kun hændelser fra din lejer) og hændelsen i JSON-format i en egenskab med navnet "**egenskaber**".

- Du kan finde flere oplysninger om skemaet for Microsoft 365 Defender begivenheder under [Oversigt over avanceret jagt](advanced-hunting-overview.md).

- I Avanceret jagt har tabellen **DeviceInfo** en kolonne med navnet **MachineGroup** , som indeholder gruppen af enheden. Her vil alle begivenheder også blive dekoreret med denne kolonne.

## <a name="data-types-mapping"></a>Tilknytning af datatyper

Benyt følgende fremgangsmåde for at hente datatyperne for hændelsesegenskaber:

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, og gå til [siden Avanceret jagt](https://security.microsoft.com/hunting-package).

2. Kør følgende forespørgsel for at hente tilknytningen af datatyper for hver hændelse:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Her er et eksempel på hændelsen Enhedsoplysninger:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="Et eksempel på en forespørgsel om enhedsoplysninger" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Microsoft 365 Defender streaming-API](streaming-api.md)
- [Understøttede Microsoft 365 Defender hændelsestyper i API til hændelsesstreaming](supported-event-types.md)
- [Stream Microsoft 365 Defender hændelser til din Azure Storage-konto](streaming-api-storage.md)
- [Dokumentation til Azure Event Hubs](/azure/event-hubs/)
- [Fejlfinding af forbindelsesproblemer – Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
