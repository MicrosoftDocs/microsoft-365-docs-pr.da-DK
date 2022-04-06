---
title: Stream Microsoft 365 Defender begivenheder til Azure Event Hub
description: Få mere at vide om, hvordan Microsoft 365 Defender til at streame Avancerede rævebegivenheder til din Begivenhedshub.
keywords: rå dataeksport, streaming-API, API, Azure Event Hub, Azure-lager, lagerkonto, Avanceret jagt, rå datadeling
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
ms.openlocfilehash: 064ce5f796d59994b9d7ec4c3403711b1d683e56
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500469"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>Konfigurer Microsoft 365 Defender at streame avancerede rævebegivenheder til din Azure Event Hub

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>Før du begynder

1. Opret en [begivenhedshub](/azure/event-hubs/) i din lejer.

2. Log på din [Azure-lejer](https://ms.portal.azure.com/), gå til **Abonnementer > Dit abonnement > ressourceudbydere > registrere dig til Microsoft.Insights**.

3. Opret et navneområde for begivenhedshub, gå til Begivenhedshub **>** Tilføj og vælg prisniveau, overførselshastighedsenheder og automatisk opsnævning, der passer til den forventede belastning. Du kan få mere at vide [under Priser på begivenhedshubs](https://azure.microsoft.com/pricing/details/event-hubs/).

### <a name="add-contributor-permissions"></a>Tilføj bidragydertilladelser

Når navneområdet For begivenhedshub er oprettet, skal du:

1. Definer den bruger, der skal logge Microsoft 365 Defender som bidragyder.

2. Hvis du opretter forbindelse til et program, skal du tilføje App-registreringstjenestens Hovedstol som Læser, Azure Event Hub-datamodtager (dette kan også gøres på ressourcegruppe- eller abonnementsniveau).

    Gå til **navneområdet for hændelseshubs > Access-kontrolelement (IAM), > Tilføj** og bekræft under **Rolletildelinger**.

## <a name="enable-raw-data-streaming"></a>Aktivér rå datastreaming

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender som</a> ***Global administrator** _ eller _*_Sikkerhedsadministrator_**.

2. Gå til siden [med indstillinger for Streaming API](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. Klik på **Tilføj**.

4. Vælg et navn til de nye indstillinger.

5. Vælg **Videressendelse af begivenheder til Azure Event Hub**.

6. Du kan vælge, om du vil eksportere begivenhedsdataene til en enkelt hændelseshub, eller om du vil eksportere hver hændelsestabel til en anden hændelseshub i dit Hændelseshub-navneområde.

7. Hvis du vil eksportere begivenhedsdataene til en enkelt Hændelseshub, skal du angive navnet **på din Hændelseshub** og dit **Hændelseshub-ressource-id**.

   Hvis du vil have **dit Event** Hub-ressource-id, skal du gå til din Azure Event Hub-navneområdeside på fanen **AzureProperties** [](https://ms.portal.azure.com/) >  > kopiere teksten under **Ressource-id**:

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="Ressource-id for hændelseshub" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. Gå til [understøttede Microsoft 365 Defender begivenhedshændelsestyper i hændelsesstreaming-API'en](supported-event-types.md) for at se supportstatus for hændelsestyper i Microsoft 365 Streaming API.

9. Vælg de hændelser, du vil streame, og klik på **Gem**.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>Skema over hændelserne i Azure Event Hub

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

- Hver hændelseshubmeddelelse i Azure Event Hub indeholder liste over poster.

- Hver post indeholder navnet på begivenheden, tidspunktet Microsoft 365 Defender modtaget begivenheden, den lejer, den tilhører (du får kun begivenheder fra din lejer), og begivenheden i JSON-format i en egenskab kaldet "**egenskaber**".

- Du kan finde flere oplysninger om skemaet for Microsoft 365 Defender i Oversigt [over Avanceret ræveing](advanced-hunting-overview.md).

- I Avanceret jagt har **tabellen DeviceInfo** en kolonne med **navnet MachineGroup** , som indeholder gruppen af enheden. Her vil alle begivenheder også være pyntet med denne kolonne.

## <a name="data-types-mapping"></a>Tilknytning af datatyper

Hvis du vil hente datatyperne for hændelsesegenskaber, skal du gøre følgende:

1. Log på Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">,</a> og gå til [siden Avanceret jagt](https://security.microsoft.com/hunting-package).

2. Kør følgende forespørgsel for at få tilknytningen af datatyperne for hver hændelse:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- Her er et eksempel på hændelsen Enhedsoplysninger:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="En eksempelforespørgsel til enhedsoplysninger" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Avanceret jagt](advanced-hunting-overview.md)
- [Microsoft 365 Defender-streaming-API](streaming-api.md)
- [Understøttede Microsoft 365 Defender hændelsestyper i hændelsesstreaming-API'en](supported-event-types.md)
- [Stream Microsoft 365 Defender begivenheder til din Azure-lagerkonto](streaming-api-storage.md)
- [Azure Event Hub-dokumentation](/azure/event-hubs/)
- [Fejlfinding af forbindelsesproblemer – Azure Event Hub](/azure/event-hubs/troubleshooting-guide)
