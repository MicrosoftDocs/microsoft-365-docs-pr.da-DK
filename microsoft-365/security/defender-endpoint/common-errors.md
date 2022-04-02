---
title: Almindelige Microsoft Defender for Endpoint API-fejl
description: Liste over almindelige fejl i Microsoft Defender for Endpoint API med beskrivelser.
keywords: API'er, Microsoft Defender til Endpoint API, fejl, fejlfinding
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
ms.openlocfilehash: d960091409a71fd23e52a098ae3d8164c7df5aef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63603101"
---
# <a name="common-rest-api-error-codes"></a>Almindelige REST API-fejlkoder



[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


* De fejlkoder, der er angivet i følgende tabel, kan returneres af en handling på en hvilken som helst Af Microsoft Defender til slutpunkt-API'er.
* Ud over fejlkoden indeholder hvert fejlsvar en fejlmeddelelse, som kan hjælpe med at løse problemet.
* Meddelelsen er en gratis tekst, der kan ændres.
* Nederst på siden kan du finde svarekseler.

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Fejlkode|HTTP-statuskode|Meddelelse
---|---|---
BadRequest|BadRequest (400)|Generel ugyldig anmodning-fejlmeddelelse.
ODataError|BadRequest (400)|Ugyldig OData-URI-forespørgsel (den specifikke fejl er angivet).
Ugyldiginput|BadRequest (400)|Ugyldigt input {det ugyldige input}.
InvalidRequestVirkey|BadRequest (400)|Ugyldig brødtekst til anmodning.
InvalidHashValue|BadRequest (400)|Hash-værdi {den ugyldige hash} er ugyldig.
InvalidDomainName|BadRequest (400)|Domænenavnet {det ugyldige domæne} er ugyldigt.
InvalidIpAddress|BadRequest (400)|IP-adressen {den ugyldige IP} er ugyldig.
InvalidUrl|BadRequest (400)|URL-adressen {den ugyldige URL} er ugyldig.
MaximumBatchSizeExceeded|BadRequest (400)|Den maksimale batchstørrelse er overskredet. Modtaget: {batchstørrelse modtaget}, tilladt: {batch size allowed}.
MissingRequiredParameter|BadRequest (400)|Parameter {the missing parameter} mangler.
OsPlatformNotSupported|BadRequest (400)|Os-platformen {the client OS Platform} understøttes ikke for denne handling.
ClientVersionNotSupported|BadRequest (400)|{The requested action} understøttes på klientversionen {supported client version} og nyere.
Uautoriseret|Uautoriseret (401)|Uautoriseret (ugyldigt eller udløbet godkendelseshoved).
Forbudt|Forbudt (403)|Forbudt (gyldig token, men utilstrækkelig tilladelse til handlingen).
DisabledFeature|Forbudt (403)|Lejerfunktionen er ikke aktiveret.
DisallowedOperation|Forbudt (403)|{the disallowed operation and the reason}.
Blev ikke fundet|Blev ikke fundet (404)|Generel fejlmeddelelse blev ikke fundet.
Ressource blev ikke fundet|Blev ikke fundet (404)|Ressourcen {the requested resource} blev ikke fundet.
InternalServerError|Intern serverfejl (500)|(Ingen fejlmeddelelse, prøv at handlingen igen)
TooManyRequests|For mange anmodninger (429)|Svar repræsenterer en nåing af kvotegrænsen enten efter antal anmodninger eller efter CPU.

## <a name="body-parameters-are-case-sensitive"></a>Parametrene for brødtekst tager hensyn til store og små bogstaver

Der er i øjeblikket store og små bogstaver i parametrene til sendte brødtekst.

Hvis du oplever en **InvalidRequestVirkey** - eller **MissingRequiredParameter-fejl** , kan det skyldes et forkert bogstav i parameteren stort eller lille bogstav.

Gennemse siden med API-dokumentationen, og kontrollér, at de indsendte parametre stemmer overens med det relevante eksempel.

## <a name="correlation-request-id"></a>Korrelationsanmodnings-id

Hvert fejlsvar indeholder et entydigt id-parameter til sporing.

Egenskabsnavnet for denne parameter er "target".

Når du kontakter os om en fejl, kan du vedhæftning af dette id finde den egentlige årsag til problemet.

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
