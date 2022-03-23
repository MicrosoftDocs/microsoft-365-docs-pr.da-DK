---
title: Microsoft 365 Defender forudsætninger
description: Få mere at vide om licens-, hardware- og softwarekrav og andre konfigurationsindstillinger for Microsoft 365 Defender
keywords: krav, forudsætninger, hardware, software, browser, Microsoft 365 Defender, M365, licens, E5, A5, EMS, køb
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
ms.openlocfilehash: 5281df5fe500907af6bb54384bb44b5a29534460
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/08/2022
ms.locfileid: "63592122"
---
# <a name="microsoft-365-defender-prerequisites"></a>Microsoft 365 Defender forudsætninger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Få mere at vide om licenser og andre krav til klargøring [og Microsoft 365 Defender](microsoft-365-defender.md).

## <a name="licensing-requirements"></a>Licenskrav
Enhver af disse licenser giver dig adgang til Microsoft 365 Defender-funktioner via Microsoft 365 Defender-portalen uden ekstra omkostninger:

- Microsoft 365 E5 eller A5
- Microsoft 365 E3 med Microsoft 365 E5 Sikkerhed-tilføjelsesprogrammet
- Microsoft 365 E3 med Enterprise Mobility + Security E5-tilføjelsesprogrammet
- Microsoft 365 A3 med Microsoft 365 A5 Security-tilføjelsesprogrammet
- Windows 10 Enterprise E5 eller A5
- Windows 11 Enterprise E5 eller A5
- Enterprise Mobility + Security (EMS) E5 eller A5 
- Office 365 E5 eller A5
- Microsoft Defender til Slutpunkt
- Microsoft Defender for Identity 
- Microsoft Defender til skyapps
- Defender for Office 365 (Plan 2)

Få mere at vide [under Microsoft 365 Enterprise serviceplaner](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise).

> Har du endnu ikke licens? [Prøv eller køb et Microsoft 365-abonnement](../../commerce/try-or-buy-microsoft-365.md)

### <a name="check-your-existing--licenses"></a>Kontrollér dine eksisterende licenser
Gå til Microsoft 365 Administration ([admin.microsoft.com](https://admin.microsoft.com/)) for at få vist dine eksisterende licenser. I Administration skal du gå til **Faktureringslicens** > .

>[!NOTE]
> Du skal være tildelt enten **faktureringsadministratoren eller** **den globale læserrolle** [i Azure AD](/azure/active-directory/roles/permissions-reference) for at kunne se licensoplysninger. Hvis du støder på adgangsproblemer, skal du kontakte en global administrator.

## <a name="required-permissions"></a>Påkrævede tilladelser
Du skal være **global administrator eller** **sikkerhedsadministrator i** Azure Active Directory at aktivere Microsoft 365 Defender. For listen over roller, der kræves for at bruge Microsoft 365 Defender oplysninger om, hvordan adgang til data er regulerede, skal du læse om administration [af adgang til Microsoft 365 Defender](m365d-permissions.md).

## <a name="browser-requirements"></a>Browserkrav
Adgang Microsoft 365 Defender i Microsoft 365 Defender via Microsoft Edge, Internet Explorer 11 eller en HTML 5-kompatibel webbrowser.

## <a name="availability-to-us-gcc-gcc-high-and-other-us-government-institutions"></a>Tilgængelighed for amerikanske GCC, GCC High og andre amerikanske myndigheder

Du kan finde oplysninger om kunder inden for det amerikanske offentlige [Microsoft 365 Defender for kunder i det amerikanske offentlige.](usgov.md)

I øjeblikket er Microsoft Defender for Office 365 integration i de samlede Microsoft 365 Defender-funktioner ikke tilgængelige for kunder på følgende Office 365 datacenterplaceringer:

- Norge 
- Sydafrika 
- De Forenede Arabiske Emirater 
- Sverige 
- Singapore 


## <a name="related-topics"></a>Relaterede emner
- [Microsoft 365 Defender oversigt](microsoft-365-defender.md)
- [Slå Microsoft 365 Defender](m365d-enable.md)
- [Administrere adgang og tilladelser](m365d-permissions.md)
