---
title: Tilføj eller fjern computermærkers API
description: Få mere at vide om, hvordan du bruger Add or Remove machine tags API til at tilføje eller fjerne et mærke til en computer i Microsoft Defender til slutpunkt.
keywords: API'er, graph api, understøttede api'er, mærker, maskinmærker
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
ms.openlocfilehash: 2ec34011d00e77c5e32f58567a0b705cf7c0dc1c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591264"
---
# <a name="add-or-remove-machine-tags-api"></a>Tilføj eller fjern computermærkers API

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1 ](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2 ](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Føjer eller fjerner mærket til en bestemt [computer](machine.md).

## <a name="limitations"></a>Begrænsninger

1. Du kan lægge på maskiner, der sidst er set i henhold til din konfigurerede opbevaringsperiode.

2. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Use Defender for Endpoint API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.ReadWrite.All|"Læs og skriv alle computeroplysninger"
Delegeret (arbejds- eller skolekonto)|Machine.ReadWrite|"Læs og skriv maskinoplysninger"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: 'Administrer sikkerhedsindstilling'. Få mere at vide ( [Se Oprette og administrere roller](user-roles.md) for at få flere oplysninger)
> - Brugeren skal have adgang til computeren baseret på indstillinger for maskingrupper (Se Opret og administrer [maskingrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/tags
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse|String|Bearer {token}. **Påkrævet**.
Indholdstype|streng|application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive et JSON-objekt med følgende parametre:

Parameter|Type|Beskrivelse
:---|:---|:---
Værdi|String|Kodenavnet. **Påkrævet**.
Handling|Enum|Tilføj eller Fjern. Tilladte værdier er: 'Tilføj' eller 'Fjern'. **Påkrævet**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 - OK-svarkode og den opdaterede computer i svarteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på en anmodning, der tilføjer maskinmærke.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/tags
```

```json
{
  "Value" : "test Tag 2",
  "Action": "Add"
}
```

- Hvis du vil fjerne et computermærke, skal du indstille handlingen til "Fjern" i stedet for "Tilføj" i brødteksten i anmodningen.
