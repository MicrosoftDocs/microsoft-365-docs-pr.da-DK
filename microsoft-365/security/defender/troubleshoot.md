---
title: Foretag fejlfinding af problemer med Microsoft 365 Defender-tjenesten
description: Find løsninger og løsninger på kendte Microsoft 365 Defender problemer
keywords: fejlfinding Microsoft 365 Defender, fejlfinding, Microsoft Defender for Identity, problemer, tilføjelsesprogram, indstillingsside
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
ms.openlocfilehash: 656599cf9ec66987119819b2f28f9a8eff1d4e77
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731664"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>Foretag fejlfinding af problemer med Microsoft 365 Defender-tjenesten

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Dette afsnit omhandler problemer, der kan opstå, når du bruger tjenesten Microsoft 365 Defender.

## <a name="i-dont-see-microsoft-365-defender-content"></a>Jeg kan ikke se Microsoft 365 Defender indhold

Hvis du ikke kan se egenskaber i navigationsruden, f.eks. Hændelser, Handlingscenter eller Jagt på din portal, skal du bekræfte, at din lejer har de relevante licenser.

Du kan få flere oplysninger under [Forudsætninger](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>Microsoft Defender for Identity beskeder vises ikke i de Microsoft 365 Defender hændelser

Hvis du har Microsoft Defender for Identity udrullet i dit miljø, men du ikke får vist Defender for Identity-beskeder som en del af Microsoft 365 Defender hændelser, skal du sikre dig, at Microsoft Defender for Cloud Apps  og Defender for Identity-integration er aktiveret.

Du kan få flere oplysninger under [Microsoft Defender for Identity integration](/cloud-app-security/mdi-integration).

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>Hvor er indstillingssiden til aktivering af tjenesten?

Hvis du vil slå Microsoft 365 Defender til, skal du få adgang **til Indstillinger** fra navigationsruden på Microsoft 365 Defender portal. Dette navigationselement er kun synligt, hvis du har de [nødvendige tilladelser og licenser](m365d-enable.md#check-license-eligibility-and-required-permissions).

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>Hvordan gør jeg oprette en undtagelse for min fil/URL-adresse?

Et falsk positivt er en fil eller URL-adresse, der registreres som skadelig, men som ikke er en trussel. Du kan oprette indikatorer og definere undtagelser for at fjerne blokeringen og tillade visse filer/URL-adresser. Se [Address false positive/negatives in Defender for Endpoint](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives).
