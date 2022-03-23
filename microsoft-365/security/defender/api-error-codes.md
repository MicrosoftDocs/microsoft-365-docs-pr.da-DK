---
title: Almindelige Microsoft 365 Defender REST API-fejlkoder
description: Få mere at vide om de Microsoft 365 Defender REST API-fejlkoder
keywords: api, fejl, koder, almindelige fejl, Microsoft 365 Defender, API-fejlkoder
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 499ab1722b2754e893361784f7ff1ce257ceb58b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63593790"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>Almindelige Microsoft 365 Defender REST API-fejlkoder

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Fejlkoder kan returneres af en handling på en af de Microsoft 365 Defender API'er. Hvert fejlsvar indeholder en fejlmeddelelse, som kan hjælpe med at løse problemet. Kolonnen med fejlmeddelelser i tabelsektionen indeholder nogle eksempelmeddelelser. Indholdet af faktiske meddelelser varierer afhængigt af de faktorer, der udløste svaret. Variabelt indhold er angivet i tabellen med vinkelparenteser.

## <a name="error-codes"></a>Fejlkoder

Fejlkode | HTTP-statuskode | Meddelelse
-|-|-
BadRequest | BadRequest (400) | Generel ugyldig anmodning-fejlmeddelelse.
ODataError | BadRequest (400) | Ugyldig OData-URI-forespørgsel \<the specific error is specified\>.
Ugyldiginput | BadRequest (400) | Ugyldigt input \<the invalid input\>.
InvalidRequestVirkey | BadRequest (400) | Ugyldig brødtekst til anmodning.
InvalidHashValue | BadRequest (400) | Hash-værdien \<the invalid hash\> er ugyldig.
InvalidDomainName | BadRequest (400) | Domænenavnet \<the invalid domain\> er ugyldigt.
InvalidIpAddress | BadRequest (400) | IP-adressen \<the invalid IP\> er ugyldig.
InvalidUrl | BadRequest (400) | URL-adressen \<the invalid URL\> er ugyldig.
MaximumBatchSizeExceeded | BadRequest (400) | Den maksimale batchstørrelse er overskredet. Modtaget: \<batch size received\>, tilladt: {batch size allowed}.
MissingRequiredParameter | BadRequest (400) | Parameteren \<the missing parameter\> mangler.
OsPlatformNotSupported | BadRequest (400) | Styresystemplatformen \<the client OS Platform\> understøttes ikke for denne handling.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> understøttes på klientversionen \<supported client version\> og derover.
Uautoriseret | Uautoriseret (401) | Uautoriseret <br /><br />*Bemærk! Dette skyldes som regel et ugyldigt eller udløbet godkendelseshoved.*
Forbudt | Forbudt (403) | Forbudt <br /><br />*Bemærk! Gyldig token, men utilstrækkelig tilladelse til handlingen*.
DisabledFeature | Forbudt (403) | Lejerfunktionen er ikke aktiveret.
DisallowedOperation | Forbudt (403) | \<the disallowed operation and the reason\>.
Blev ikke fundet | Blev ikke fundet (404) | Generel fejlmeddelelse blev ikke fundet.
Ressource blev ikke fundet | Blev ikke fundet (404) | Ressourcen \<the requested resource\> blev ikke fundet.
InternalServerError | Intern serverfejl (500) | *Bemærk! Ingen fejlmeddelelse, prøv handlingen igen, eller [kontakt Microsoft](../../admin/get-help-support.md) , hvis problemet ikke bliver løst*

## <a name="examples"></a>Eksempler

```json
{
    "error": {
        "code": "ResourceNotFound",
        "message": "Machine 123123123 was not found",
        "target": "43f4cb08-8fac-4b65-9db1-745c2ae65f3a"
    }
}
```

```json
{
    "error": {
        "code": "InvalidRequestBody",
        "message": "Request body is incorrect",
        "target": "1fa66c0f-18bd-4133-b378-36d76f3a2ba0"
    }
}
```

## <a name="body-parameters"></a>Parametre for brødtekst

> [!IMPORTANT]
> Der er store og små bogstaver i parametrene til brødtekst.

Hvis du oplever fejlen *InvalidRequestComputer eller* *MissingRequiredParameter* , kan det skyldes en slåfejl. Gennemse API-dokumentationen, og kontrollér, at de sendte parametre stemmer overens med det relevante eksempel.

## <a name="tracking-id"></a>Sporings-id

Hvert fejlsvar indeholder et entydigt id-parameter til sporing. Egenskabsnavnet for denne parameter er *destination*. Når du kontakter os om en fejl, hjælper det os med at finde den egentlige årsag til problemet ved at vedhæfte dette id.

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft 365 Defender OVERSIGT over API'er](api-overview.md)
- [Understøttede Microsoft 365 Defender API'er](api-supported.md)
- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
