---
title: Api'er fra Microsoft Defender til Slutpunkt til Power BI
ms.reviewer: ''
description: Opret en Power Business Intelligence-rapport (BI) oven på Microsoft Defender til slutpunkt-API'er.
keywords: API'er, understøttede api'er, Power BI, rapporter
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 765af5e4a2e880aa9b6c1208495537ad8cf5f26b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592716"
---
# <a name="create-custom-reports-using-power-bi"></a>Oprette brugerdefinerede rapporter ved hjælp af Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

I dette afsnit kan du se, hvordan du opretter Power BI rapport oven på Defender til endpoint-API'er.

Det første eksempel viser, hvordan du forbinder Power BI til Avanceret api, og det andet eksempel viser en forbindelse til vores OData-API'er, f.eks. Maskinhandlinger eller Beskeder.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>Forbind Power BI til Avanceret api

- Åbn Microsoft Power BI

- Klik **på Hent tom** **dataforespørgsel** \>

  ![Billede af opret tom forespørgsel.](images/power-bi-create-blank-query.png)

- Klik **på Avanceret editor**

  ![Billede af Åbn Avanceret editor.](images/power-bi-open-advanced-editor.png)

- Kopiér nedenstående, og indsæt det i editoren:

```
    let
        AdvancedHuntingQuery = "DeviceEvents | where ActionType contains 'Anti' | limit 20",

        HuntingUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries",

        Response = Json.Document(Web.Contents(HuntingUrl, [Query=[key=AdvancedHuntingQuery]])),

        TypeMap = #table(
            { "Type", "PowerBiType" },
            {
                { "Double",   Double.Type },
                { "Int64",    Int64.Type },
                { "Int32",    Int32.Type },
                { "Int16",    Int16.Type },
                { "UInt64",   Number.Type },
                { "UInt32",   Number.Type },
                { "UInt16",   Number.Type },
                { "Byte",     Byte.Type },
                { "Single",   Single.Type },
                { "Decimal",  Decimal.Type },
                { "TimeSpan", Duration.Type },
                { "DateTime", DateTimeZone.Type },
                { "String",   Text.Type },
                { "Boolean",  Logical.Type },
                { "SByte",    Logical.Type },
                { "Guid",     Text.Type }
            }),

        Schema = Table.FromRecords(Response[Schema]),
        TypedSchema = Table.Join(Table.SelectColumns(Schema, {"Name", "Type"}), {"Type"}, TypeMap , {"Type"}),
        Results = Response[Results],
        Rows = Table.FromRecords(Results, Schema[Name]),
        Table = Table.TransformColumnTypes(Rows, Table.ToList(TypedSchema, (c) => {c{0}, c{2}}))

    in Table
```

- Klik **på Udført**

- Klik **på Rediger legitimationsoplysninger**

    ![Billede af rediger legitimationsoplysninger0.](images/power-bi-edit-credentials.png)

- Vælg **Organisationskonto** \> **Log på**

    ![Billede af angiv legitimationsoplysninger1.](images/power-bi-set-credentials-organizational.png)

- Angiv dine legitimationsoplysninger, og vent på at være logget på

- Klik **Forbind**

    ![Billede af sæt af legitimationsoplysninger2.](images/power-bi-set-credentials-organizational-cont.png)

- Nu vises resultaterne af forespørgslen som en tabel, og du kan begynde at bygge visualiseringer oven på den!

- Du kan duplikere denne tabel, omdøbe den og redigere forespørgslen Avanceret jagt inde for at få alle data, du ønsker.

## <a name="connect-power-bi-to-odata-apis"></a>Forbind Power BI til OData-API'er

- Den eneste forskel fra eksemplet ovenfor er forespørgslen i editoren.

- Kopiér nedenstående, og indsæt det i editoren for at trække **alle computerhandlinger** fra din organisation:

```
    let

        Query = "MachineActions",

        Source = OData.Feed("https://api.securitycenter.microsoft.com/api/" & Query, null, [Implementation="2.0", MoreColumns=true])
    in
        Source
```

- Du kan gøre det samme for **beskeder** og **maskiner**.
- Du kan også bruge OData-forespørgsler til forespørgselsfiltre under Brug [af OData-forespørgsler](exposed-apis-odata-samples.md)

## <a name="power-bi-dashboard-samples-in-github"></a>Power BI dashboardeksempler i GitHub

Du kan finde flere oplysninger [i Power BI rapportskabeloner](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI).

## <a name="sample-reports"></a>Eksempelrapporter

Få vist eksempler på rapporter for Microsoft Defender Power BI slutpunkter. Du kan finde flere oplysninger [i Gennemse kodeeksempler](/samples/browse/?products=mdatp).

## <a name="related-topics"></a>Relaterede emner

- [Defender til Endpoint-API'er](apis-intro.md)
- [Avanceret api til jagt](run-advanced-query-api.md)
- [Brug af OData-forespørgsler](exposed-apis-odata-samples.md)
