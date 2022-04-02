---
title: ISO
description: Få mere at vide om, hvordan du bruger Isoler maskin-API'en til at isolere en enhed fra at få adgang til eksternt netværk i Microsoft Defender til slutpunkt.
keywords: API'er, graph api, understøttede API'er, isoler enhed
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
ms.openlocfilehash: 52063135280d9e91ca531546b4ae03cf5b42ccbf
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63603098"
---
# <a name="isolate-machine-api"></a>ISO

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Isolerer en enhed fra at få adgang til eksternt netværk.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - Fuld isolation er tilgængelig for enheder på Windows 10, version 1703 og Windows 11.
> - Selektiv isolation er tilgængelig for enheder på Windows 10, version 1709 eller nyere, og på Windows 11.
> - Når du isolerer en enhed, er det kun visse processer og destinationer, der er tilladt. Derfor kan enheder, der er bag en fuld VPN-slutpunkt, ikke nå Microsoft Defender til slutpunktsskytjenesten, når enheden er isoleret. Vi anbefaler, at du bruger et opdelt VPN til Microsoft Defender til slutpunkt og Microsoft Defender Antivirus skybaseret beskyttelsesrelateret trafik.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|Machine.Isoler|'Isoler maskine'
Delegeret (arbejds- eller skolekonto)|Machine.Isoler|'Isoler maskine'

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Aktive afhjælpningshandlinger" (Se [Opret og administrer](user-roles.md) roller for at få flere oplysninger)
> - Brugeren skal have adgang til enheden baseret på indstillingerne for gruppen af enheder (Se Opret og administrer [enhedsgrupper](machine-groups.md) for at få flere oplysninger)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/isolate
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
Isolationstype|String|Type af isolation. Tilladte værdier er: 'Fuld' eller 'Selektiv'.

**Isolationstype** kontrollerer den type isolation, der skal udføres, og kan være en af følgende:

- Fuld: Fuld isolation
- Selektivt: Begræns kun et begrænset sæt programmer i at få adgang til netværket (se [Isoler enheder fra netværket for at](respond-machine-alerts.md#isolate-devices-from-the-network) få flere oplysninger)

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 201 – Oprettet svarkode og [Computerhandling](machineaction.md) i svarteksten.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/isolate
```

```json
{
  "Comment": "Isolate machine due to alert 1234",
  "IsolationType": "Full" 
}
```

- Hvis du vil frigive en enhed fra isolation, skal [du se Frigiv enhed fra isolation](unisolate-machine.md).
