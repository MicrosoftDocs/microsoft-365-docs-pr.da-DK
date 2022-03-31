---
title: Importere et ordsæt ved hjælp af et SKOS-baseret format
description: Få mere at vide om, hvordan du importerer et ordsæt ved hjælp af et SKOS-baseret format
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.prod: microsoft-365-enterprise
ms.topic: article
ms.service: ''
ms.collection: enabler-strategic
ms.custom: admindeeplinkSPO
search.appverid: ''
ms.localizationpriority: high
ms.openlocfilehash: c7a23b8da32f5ae9132a41661a1141f34df48a6b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601687"
---
# <a name="import-a-term-set-using-a-skos-based-format"></a>Importere et ordsæt ved hjælp af et SKOS-baseret format

Du kan importere et ordsæt ved hjælp af et SKOS-baseret format. Du kan finde flere oplysninger om [formatet SharePoint referencen til taksonomi-SKOS-formatet](skos-format-reference.md). Denne funktion kræver en [SharePoint Syntex](index.md) licens.

Vi anbefaler, at du beholder dine importfiler til mindre end 20.000 vilkår. Større filer kan øge den tid, det tager at validere og importere.

1. I Administration SharePoint skal du udvide **Indholdstjenester** og derefter vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185073" target="_blank">**Ordlager**</a>.

2. Vælg den ordgruppe, hvor du vil importere ordsættet.

3. Klik på Importér ordsæt **på kommandolinjen**.

4. Hvis du vil hente en eksempelfil til brug som en skabelon, skal du klikke på **eksempelmetadata.ttl** for at få en eksempelfil, der bruger det SKOS-baserede format.

5. Opret den importfil, der indeholder de ordsæt, & ord, du vil importere.

6. Under **Filformat skal** du vælge **SKOS (*.ttl)**.

7. Klik **på Gennemse** , og naviger til og tilføj importfilen.

8. Klik **på Importér**. Luk ikke panelet, før importen er fuldført.

Når importen af filen er udført, vises der en vellykket meddelelse, og ordlageret opdateres, og du kan navigere til de nyligt oprettede ordsæt.

## <a name="see-also"></a>Se også

[Introduktion til administrerede metadata](/sharepoint/managed-metadata)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Importere ordsæt (webstedsniveau)](https://support.microsoft.com/office/168fbc86-7fce-4288-9a1f-b83fc3921c18)
