---
title: Stream Microsoft Defender for Endpoint begivenheder til Azure Event Hubs
description: Få mere at vide om, hvordan Microsoft Defender for Endpoint til at streame avancerede rævebegivenheder til din Begivenhedshub.
keywords: rå dataeksport, streaming-API, API, Azure Event Hubs, Azure-lager, lagerkonto, Avanceret jagt, rå datadeling
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
ms.openlocfilehash: eb58e21ee9dc2cf7c1eaf89c8fa9d06edfbbe050
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467901"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-azure-event-hubs"></a>Konfigurer Microsoft Defender for Endpoint at streame avancerede rævehændelser til dine Azure Event Hubs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Før du begynder

1. Opret en [begivenhedshub](/azure/event-hubs/) i din lejer.

2. Log på din [Azure-lejer](https://ms.portal.azure.com/), gå til Abonnementer **> Dit abonnement > ressourceudbydere > Registrer dig til Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Aktivér rå datastreaming

1. Log [på Microsoft 365 Defender *](https://security.microsoft.com)**Global Administrator** _ eller _*_Security Administrator_**.

2. Gå til siden [Med indstillinger for dataeksport](https://security.microsoft.com/interoperability/dataexport) i Microsoft Defender-portalen.

3. Klik på **Tilføj indstillinger for dataeksport**.

4. Vælg et navn til de nye indstillinger.

5. Vælg **Videressendelse af begivenheder til Azure Event Hubs**.

6. Skriv navnet **på dine hændelseshubs** og **ressource-id'et for Hændelseshubs**.

   For at få dit ressource-id for **Begivenhedshubs** skal du gå til din Azure Event Hubs-navneområdeside på [fanen Azure](https://ms.portal.azure.com/) > \> egenskaber kopiere teksten under **Ressource-id**:

   :::image type="content" source="images/event-hub-resource-id.png" alt-text="Ressource-id-1 for hændelseshubs" lightbox="images/event-hub-resource-id.png":::

7. Vælg de hændelser, du vil streame, og klik på **Gem**.

## <a name="the-schema-of-the-events-in-azure-event-hubs"></a>Skema over hændelserne i Azure Event Hubs

```json
{
    "records": [
                    {
                        "time": "<The time WDATP received the event>"
                        "tenantId": "<The Id of the tenant that the event belongs to>"
                        "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                        "properties": { <WDATP Advanced Hunting event as Json> }
                    }
                    ...
                ]
}
```

- Hver hændelseshubmeddelelse i Azure Event Hubs indeholder liste over poster.

- Hver post indeholder navnet på begivenheden, tidspunktet Microsoft Defender for Endpoint modtaget begivenheden, den lejer, den tilhører (du får kun begivenheder fra din lejer), og begivenheden i JSON-format i en egenskab kaldet "**egenskaber**".

- Du kan finde flere oplysninger om skemaet for Microsoft Defender for Endpoint i Oversigt [over Avanceret ræving](advanced-hunting-overview.md).

- I Avanceret jagt har **tabellen DeviceInfo** en kolonne med **navnet MachineGroup** , som indeholder gruppen af enheden. Her vil alle begivenheder også være pyntet med denne kolonne. Se [Enhedsgrupper for](machine-groups.md) at få flere oplysninger.

## <a name="data-types-mapping"></a>Tilknytning af datatyper

Hvis du vil hente datatyperne for hændelsesegenskaber, skal du gøre følgende:

1. Log på Microsoft 365 Defender[,](https://security.microsoft.com) og gå til [siden Avanceret jagt](https://security.microsoft.com/hunting-package).

2. Kør følgende forespørgsel for at få tilknytningen af datatyperne for hver hændelse:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- Her er et eksempel på hændelsen Enhedsoplysninger:

  :::image type="content" source="images/machine-info-datatype-example.png" alt-text="Ressource-id-2 for hændelseshubs" lightbox="images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Avanceret jagt](advanced-hunting-overview.md)
- [Microsoft Defender for Endpoint-streaming-API](raw-data-export.md)
- [Stream Microsoft Defender for Endpoint begivenheder til din Azure Storage-konto](raw-data-export-storage.md)
- [Azure Event Hubs-dokumentation](/azure/event-hubs/)
- [Fejlfinding af forbindelsesproblemer – Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
