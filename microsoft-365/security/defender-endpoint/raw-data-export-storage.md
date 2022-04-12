---
title: Stream Microsoft Defender for Endpoint hændelser til din Storage konto
description: Få mere at vide om, hvordan du konfigurerer Microsoft Defender for Endpoint til at streame avancerede jagthændelser til din Storage konto.
keywords: rå dataeksport, streaming-API, API, Event Hubs, Azure Storage, lagerkonto, Avanceret jagt, rådatadeling
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
ms.openlocfilehash: d5d4917e2464964da819af0a06f0b8e4883dfea9
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783881"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>Konfigurer Microsoft Defender for Endpoint til at streame avancerede jagthændelser til din Storage konto

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>Før du begynder

1. Opret en [Storage konto](/azure/storage/common/storage-account-overview) i din lejer.

2. Log på din [Azure-lejer](https://ms.portal.azure.com/), gå til **Abonnementer > Dit abonnement > Ressourceudbydere > Tilmeld dig Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>Aktivér rå datastreaming

1. Log på [Microsoft 365 Defender](https://security.microsoft.com) som en ***Global Administrator** _ eller _*_Sikkerhedsadministrator_**.

2. Gå til [siden Indstillinger for dataeksport](https://security.microsoft.com/interoperability/dataexport) i Microsoft 365 Defender.

3. Klik på **Tilføj indstillinger for dataeksport**.

4. Vælg et navn til de nye indstillinger.

5. Vælg **Videresend hændelser for at Azure Storage**.

6. Skriv dit **Storage-kontoressource-id**. Hvis du vil hente dit **Storage-kontoressource-id**, skal du gå til din Storage kontoside under fanen \> [Azure Portal](https://ms.portal.azure.com/) \> egenskaber kopiere teksten under **Storage kontoressource-id**:

   :::image type="content" source="images/storage-account-resource-id.png" alt-text="Event Hubs med ressource-id1" lightbox="images/storage-account-resource-id.png":::

7. Vælg de hændelser, du vil streame, og klik på **Gem**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>Skemaet for hændelserne på den Storage konto

- Der oprettes en blobobjektbeholder for hver hændelsestype:

  :::image type="content" source="images/storage-account-event-schema.png" alt-text="Event Hubs med ressource-id2" lightbox="images/storage-account-event-schema.png":::

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

- Hver række indeholder hændelsesnavnet, det tidspunkt, hvor Defender for Endpoint modtog hændelsen, den lejer, den tilhører (du får kun hændelser fra din lejer) og hændelsen i JSON-format i en egenskab med navnet "egenskaber".

- Du kan finde flere oplysninger om skemaet for Microsoft Defender for Endpoint begivenheder under [Oversigt over avanceret jagt](advanced-hunting-overview.md).

- I Avanceret jagt har tabellen **DeviceInfo** en kolonne med navnet **MachineGroup** , som indeholder gruppen af enheden. Her vil alle begivenheder også blive dekoreret med denne kolonne. Se [Enhedsgrupper for at](machine-groups.md) få flere oplysninger.

## <a name="data-types-mapping"></a>Tilknytning af datatyper

Hvis du vil hente datatyperne for vores hændelsesegenskaber, skal du gøre følgende:

1. Log på [Microsoft 365 Defender](https://security.microsoft.com), og gå til [siden Avanceret jagt](https://security.microsoft.com/hunting-package).

2. Kør følgende forespørgsel for at hente tilknytningen af datatyper for hver hændelse:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Her er et eksempel på hændelsen Enhedsoplysninger:

  :::image type="content" source="images/data-types-mapping-query.png" alt-text="Event Hubs med ressource-id3" lightbox="images/data-types-mapping-query.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [API til Microsoft Defender for Endpoint streaming](raw-data-export.md)
- [Stream Microsoft Defender for Endpoint hændelser til din Azure Storage-konto](raw-data-export-storage.md)
- [dokumentation til Azure Storage-konto](/azure/storage/common/storage-account-overview)
