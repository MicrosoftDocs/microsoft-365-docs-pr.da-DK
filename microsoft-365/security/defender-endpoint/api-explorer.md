---
title: API Explorer i Microsoft Defender for Endpoint
ms.reviewer: ''
description: Brug API Explorer til at konstruere og udføre API-forespørgsler, teste og sende anmodninger for enhver tilgængelig API
keywords: api, explorer, sende, anmode, hente, poste,
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
ms.topic: conceptual
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 5d3d81f878e201cd00e7286bd045caa5fb3e1625
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66486789"
---
# <a name="api-explorer"></a>API Explorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint API Explorer er et værktøj, der hjælper dig med at udforske forskellige Defender for Endpoint API'er interaktivt.

API Explorer gør det nemt at konstruere og udføre API-forespørgsler, teste og sende anmodninger for alle tilgængelige Defender for Endpoint API-slutpunkter. Brug API Explorer til at udføre handlinger eller finde data, der muligvis endnu ikke er tilgængelige via brugergrænsefladen.

Værktøjet er nyttigt under appudvikling. Det giver dig mulighed for at udføre API-forespørgsler, der respekterer dine brugeradgangsindstillinger, hvilket reducerer behovet for at generere adgangstokens.

Du kan også bruge værktøjet til at udforske galleriet med eksempelforespørgsler, kopiere eksempler på resultatkode og generere fejlfindingsoplysninger.

Med API Explorer kan du:

- Kør anmodninger for en hvilken som helst metode, og se svar i realtid.
- Gennemse hurtigt API-eksemplerne, og få mere at vide om, hvilke parametre de understøtter.
- Foretag nemt API-kald. ingen grund til at godkende ud over logon til administrationsportalen.

## <a name="access-api-explorer"></a>Access API Explorer

I navigationsmenuen til venstre skal du vælge **Partnere & API-API-stifinder**\>.**[](https://security.microsoft.com/interoperability/api-explorer)**

## <a name="supported-apis"></a>Understøttede API'er

API Explorer understøtter alle de API'er, der tilbydes af Defender for Endpoint.

Listen over understøttede API'er er tilgængelig i [dokumentationen til API'er](apis-intro.md).

## <a name="get-started-with-the-api-explorer"></a>Kom i gang med API Explorer

1. I venstre rude er der en liste over eksempelanmodninger, som du kan bruge.
2. Følg linkene, og klik på **Kør forespørgsel**.

Nogle af eksemplerne kan kræve angivelse af en parameter i URL-adressen, f.eks. {machine- ID}.

## <a name="faq"></a>Ofte stillede spørgsmål

**Skal jeg have et API-token for at bruge API Explorer?** <br>
Legitimationsoplysninger for at få adgang til en API er ikke nødvendige. API Explorer bruger tokenet Defender for Endpoint-administrationsportal, når den foretager en anmodning.

Legitimationsoplysningerne til brugergodkendelse, der er logget på, bruges til at bekræfte, at API Explorer er godkendt til at få adgang til data på dine vegne.

Specifikke API-anmodninger er begrænset på baggrund af dine RBAC-rettigheder. En anmodning om at "indsende indikator" er f.eks. begrænset til sikkerhedsadministratorrollen.
