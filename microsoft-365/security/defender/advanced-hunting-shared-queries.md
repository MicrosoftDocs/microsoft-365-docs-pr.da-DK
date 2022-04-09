---
title: Brug delte forespørgsler i Microsoft 365 Defender avanceret jagt
description: Start trusselsjagt med det samme med foruddefinerede og delte forespørgsler. Del dine forespørgsler til offentligheden eller til din organisation.
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto, github-lager, mine forespørgsler, delte forespørgsler
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
ms.openlocfilehash: d943f91685e3ee9d6bf12c3a47fbf68e5966dc9d
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738487"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Brug delte forespørgsler i avanceret jagt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

[Avancerede](advanced-hunting-overview.md) jagtforespørgsler kan deles mellem brugere i samme organisation. Du kan også gemme forespørgsler, der kun er tilgængelige for dig. Du kan også finde communityforespørgsler, der deles offentligt på GitHub. Med disse gemte forespørgsler kan du hurtigt forfølge specifikke trusselsjagtscenarier uden at skulle skrive forespørgsler fra bunden.

Under fanen Forespørgsler i avanceret jagt kan du finde rullemenuerne for **Delte forespørgsler**, **Mine forespørgsler** og **Community-forespørgsler**. Du kan vælge en pil, der peger nedad, for at udvide en menu.


:::image type="content" source="../../media/advanced-hunting-shared-queries-1.png" alt-text="Oplysningerne om delte forespørgsler på Microsoft 365 Defender-portalen" lightbox="../../media/advanced-hunting-shared-queries-1.png":::



## <a name="save-modify-and-share-a-query"></a>Gem, rediger og del en forespørgsel
Du kan gemme en ny eller eksisterende forespørgsel, så den kun er tilgængelig for dig eller deles med andre brugere i din organisation. 

1. Opret eller rediger en forespørgsel. 

2. Klik på rullelisten **Gem forespørgsel** , og vælg **Gem som**.
    
3. Angiv et navn til forespørgslen. 

   :::image type="content" source="../../media/shared-query-2.png" alt-text="Den nye forespørgsel, der skal til at blive gemt på Microsoft 365 Defender-portalen" lightbox="../../media/shared-query-2.png":::

4. Vælg den mappe, hvor du vil gemme forespørgslen.
    - **Delte forespørgsler** – delt med alle brugere i organisationen
    - **Mine forespørgsler** – kun tilgængelige for dig
    
5. Vælg **Gem**. 

## <a name="delete-or-rename-a-query"></a>Slet eller omdøb en forespørgsel
1. Vælg de tre prikker til højre for en forespørgsel, du vil omdøbe eller slette.

    :::image type="content" source="../../media/shared-query-3.png" alt-text="Indstillingerne for en delt forespørgsel på siden Avanceret jagt på Microsoft 365 Defender-portalen" lightbox="../../media/shared-query-3.png":::

2. Vælg **Slet** , og bekræft sletning. Eller vælg **Omdøb** , og angiv et nyt navn til forespørgslen.

## <a name="create-a-direct-link-to-a-query"></a>Opret et direkte link til en forespørgsel
Hvis du vil oprette et link, der åbner din forespørgsel direkte i den avancerede forespørgselseditor til jagt, skal du færdiggøre din forespørgsel og vælge **Del link**.

## <a name="access-community-queries-in-the-github-repo"></a>Få adgang til communityforespørgsler i det GitHub lager  
Microsofts sikkerhedsforskere deler jævnligt avancerede jagtforespørgsler i et [udpeget offentligt lager på GitHub](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/Microsoft%20365%20Defender). Bidrag til dette lager gennemses, før de publiceres. Hvis du vil bidrage, [skal du tilmelde dig GitHub gratis](https://github.com/).

Du kan også nemt finde disse forespørgsler i rullemenuen **Communityforespørgsler** .

:::image type="content" source="../../media/advanced-hunting-shared-queries-2.png" alt-text="Den nye forespørgsel, der skal til at blive gemt på Microsoft 365 Defender-portalen" lightbox="../../media/advanced-hunting-shared-queries-2.png":::

Communityforespørgsler er grupperet i mapper som *f.eks. kampagner*, *samling*, *forsvarunddragelse* og lignende. Yderligere oplysninger om forespørgslen leveres som indbyggede kommentarer i selve forespørgslen. 

>[!tip]
>Microsofts sikkerhedsforskere leverer også avancerede jagtforespørgsler, som du kan bruge til at finde aktiviteter og indikatorer, der er forbundet med nye trusler. Disse forespørgsler leveres som en del af [trusselsanalyserapporterne](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) i Microsoft 365 Defender.


## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)