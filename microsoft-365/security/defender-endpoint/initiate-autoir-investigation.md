---
title: Start undersøgelses-API
description: Brug denne API til at starte undersøgelsen på en enhed.
keywords: API'er, graph api, understøttede API'er, undersøgelse
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
ms.openlocfilehash: efffd6bdb0ab6db5b17a8d6beab09a0d84f5ff6c
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63593469"
---
# <a name="start-investigation-api"></a>Start undersøgelses-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Start automatiseret undersøgelse på en enhed.

Se [Oversigt over automatiserede undersøgelser for at](automated-investigations.md) få flere oplysninger.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 50 opkald pr. time.

## <a name="requirements-for-air"></a>Krav til AIR

Din organisation skal have Defender til slutpunkt (se [Minimumskrav til Microsoft Defender til slutpunkt](minimum-requirements.md).

Aktuelt understøtter AIR kun følgende os-versioner:

- Windows Server 2019
- Windows Server 2022
- Windows 10, version 1709 (OS Build 16299.1085 med [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441)) eller nyere
- Windows 10, version 1803 (OS-build 17134.704 med [KB4493464](https://support.microsoft.com/help/4493464/windows-10-update-kb4493464)) eller nyere
- Windows 10, version [1803](/windows/release-information/status-windows-10-1809-and-windows-server-2019) eller nyere
- Windows 11

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Alert.ReadWrite.All|"Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto)|Alert.ReadWrite|"Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Aktive afhjælpningshandlinger" (Se [Opret og administrer](user-roles.md) roller for at få flere oplysninger)
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder (Se Opret og administrer [enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.security.microsoft.com/api/machines/{id}/startInvestigation
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
Kommenter|String|Kommentar, der skal knyttes til handlingen. **Påkrævet**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 201 – Oprettet svarkode og [undersøgelse](investigation.md) i svarteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```https
POST https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/startInvestigation
```

```json
{
  "Comment": "Test investigation"
}
```
