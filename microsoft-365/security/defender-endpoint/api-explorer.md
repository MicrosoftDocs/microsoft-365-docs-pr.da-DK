---
title: API Explorer i Microsoft Defender til Slutpunkt
ms.reviewer: ''
description: Brug API-stifinderen til at oprette og udføre API-forespørgsler, teste og sende anmodninger om alle tilgængelige API'er
keywords: api, stifinder, send, anmod, hent, slå op,
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
ms.openlocfilehash: 6e7d0e5927a85f2f3952221c294fe2387c268546
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591855"
---
# <a name="api-explorer"></a>API Explorer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender til Endpoint API Explorer er et værktøj, der hjælper dig med at udforske forskellige API'er til Defender til slutpunkter interaktivt.

API-stifinderen gør det nemt at opbygge og udføre API-forespørgsler, teste og sende anmodninger om en hvilken som helst tilgængelig Defender til slutpunkts-API-slutpunkt. Brug API-stifinderen til at udføre handlinger eller finde data, der muligvis endnu ikke er tilgængelige via brugergrænsefladen.

Værktøjet er nyttigt under appudvikling. Det giver dig mulighed at udføre API-forespørgsler, der respekterer dine brugeradgangsindstillinger, hvilket reducerer behovet for at oprette adgangstokens.

Du kan også bruge værktøjet til at udforske galleriet med eksempelforespørgsler, kopiere eksempler på resultatkoder og oprette fejlfindingsoplysninger.

Med API Explorer kan du:

- Kør anmodninger for enhver metode, og se svar i realtid
- Gennemse hurtigt API-eksemplerne, og find ud af, hvilke parametre de understøtter
- Foretag API-opkald uden besvær. ingen grund til at godkende ud over logon på administrationsportalen

## <a name="access-api-explorer"></a>Access API Explorer

I venstre navigationsmenu skal du vælge **Partnere & API-API-stifinder**\>.

## <a name="supported-apis"></a>Understøttede API'er

API Explorer understøtter alle de API'er, der tilbydes af Defender til Slutpunkt.

Listen over understøttede API'er er tilgængelig i [API-dokumentationen](apis-intro.md).

## <a name="get-started-with-the-api-explorer"></a>Introduktion til API-stifinderen

1. I venstre rude er der en liste over eksempelanmodninger, som du kan bruge.
2. Følg linkene, og klik på **Kør forespørgsel**.

Nogle af eksemplerne kan kræve, at der angives en parameter i URL-adressen, f.eks. {machine- ID}.

## <a name="faq"></a>Ofte stillede spørgsmål

**Skal jeg have et API-token for at bruge API-stifinderen?** <br>
Legitimationsoplysninger til at få adgang til en API er ikke nødvendige. API-stifinderen bruger tokenet Defender til slutpunktsstyringsportalen, når der anmodes.

Legitimationsoplysningerne til logonbrugergodkendelse bruges til at bekræfte, at API Explorer er autoriseret til at få adgang til data på dine vegne.

Specifikke API-anmodninger er begrænset baseret på dine RBAC-rettigheder. Eksempelvis er en anmodning om at "Send-indikator" begrænset til sikkerhedsadministratorrollen.
