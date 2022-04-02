---
title: Opret besked fra hændelses-API
description: Få mere at vide om, hvordan du bruger Opret påmindelses-API'en til at oprette en ny besked oven på Begivenhed i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, besked, oplysninger, id
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
ms.openlocfilehash: cc28ea9082e7afbb6f623e325a48119de393f075
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63603029"
---
# <a name="create-alert-api"></a>Opret påmindelses-API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>API-beskrivelse

Opretter ny [besked](alerts.md) oven på **Begivenhed**.

- **Microsoft Defender til slutpunktshændelse er** påkrævet for oprettelse af beskeden.
- Du skal angive tre parametre fra hændelsen i anmodningen: **Hændelsestid**, **Computer-id** og **Rapport-id**. Se eksemplet nedenfor.
- Du kan bruge en begivenhed, der findes i Advanced Hunting API eller Portal.
- Hvis der findes en åben besked på den samme Enhed med samme Titel, flettes den nye oprettede besked med den.
- En automatisk undersøgelse starter automatisk på beskeder, der er oprettet via API'en.

## <a name="limitations"></a>Begrænsninger

1. Begrænsningerne for denne API er 15 opkald pr. minut.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er](apis-intro.md)

Tilladelsestype | Tilladelse | Visningsnavn for tilladelse
:---|:---|:---
Program | Alert.ReadWrite.All | "Læs og skriv alle beskeder"
Delegeret (arbejds- eller skolekonto) | Alert.ReadWrite | "Læse- og skrivebeskeder"

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal mindst have følgende rolletilladelse: "Undersøgelse af beskeder" (Få mere at vide under [Opret og administrer roller](user-roles.md) )
> - Brugeren skal have adgang til den enhed, der er knyttet til beskeden, baseret på enhedsgrupperingsindstillinger (få mere at vide under [Opret og administrer enhedsgrupper](machine-groups.md)

## <a name="http-request"></a>HTTP-anmodning

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
:---|:---|:---
Godkendelse | String | Bearer {token}. **Påkrævet**.
Indholdstype | String | application/json. **Påkrævet**.

## <a name="request-body"></a>Anmodningstekst

I brødteksten til anmodningen skal du angive følgende værdier (alle er påkrævede):

Egenskab | Type | Beskrivelse
:---|:---|:---
eventTime | DateTime(UTC) | Den nøjagtige tid for begivenheden som streng, som kommer fra avanceret jagt. f.eks. **Påkrævet**```2018-08-03T16:45:21.7115183Z```.
reportId | String | Rapport-id for hændelsen, som hentet fra avanceret jagt. **Påkrævet**.
machineId | String | Id for den enhed, hvor hændelsen blev identificeret. **Påkrævet**.
alvorsgrad | String | Beskedens alvorsgrad. Egenskabsværdierne er: 'Lav', 'Mellem' og 'Høj'. **Påkrævet**.
titel | String | Beskedens titel. **Påkrævet**.
beskrivelse | String | Beskrivelse af beskeden. **Påkrævet**.
recommendedAction| String | Sikkerhedsmedarbejder skal udføre denne handling, når du analyserer beskeden. **Påkrævet**.
kategori| String | Kategori for beskeden. Egenskabsværdierne er: "Generelt", "CommandAndControl", "Collection", "CredentialAccess", "DefenseEvasion", "Discovery", "Exfiltration", "Exploit", "Execution", "InitialAccess", "LateralMovement", "Malware", "Per persistens", "PrivilegeEscalation", "Ransomware", "SuspiciousActivity" **Required**.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200 OK og et nyt [påmindelsesobjekt](alerts.md) i brødteksten. Hvis hændelse med de angivne egenskaber (_reportId_, _eventTime_ og _machineId_) ikke blev fundet – 404 Blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request"></a>Anmod

Her er et eksempel på anmodningen.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/CreateAlertByReference
```

```json
{
    "machineId": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "severity": "Low",
    "title": "example",
    "description": "example alert",
    "recommendedAction": "nothing",
    "eventTime": "2018-08-03T16:45:21.7115183Z",
    "reportId": "20776",
    "category": "Exploit"
}
```
