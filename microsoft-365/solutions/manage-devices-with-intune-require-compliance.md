---
title: Trin 4. Kræv sunde og kompatible enheder med Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Conditional access policy
- Microsoft Intune
- Intune device management
manager: dougeby
audience: ITPro
description: Opret en politik for betinget adgang i Azure AD for at kræve kompatible enheder, så virksomhedens data er sikre, når brugerne arbejder fra en hvilken som helst enhed på en hvilken som helst placering.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- Conditional access policy
- Microsoft Intune
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
ms.openlocfilehash: 61191da794c065a46d709d443982849ec4c4d3e3
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747939"
---
# <a name="step-4-require-healthy-and-compliant-devices-with-intune"></a>Trin 4. Kræv sunde og kompatible enheder med Intune

Betinget adgang giver yderligere bekræftelse af enhedsstatus, før du giver adgang til en tjeneste. Betinget adgang fungerer ikke, medmindre du angiver betingelser. I [trin 3. Konfigurer politikker for overholdelse af angivne](manage-devices-with-intune-compliance-policies.md) standarder. Du har defineret politikker for overholdelse af angivne standarder, der angiver de minimumkrav, som en enhed skal opfylde for at få adgang til dit miljø. I denne artikel skal du oprette den tilsvarende politik for betinget adgang i Azure AD for at kræve kompatible enheder. Dette hjælper med at holde dine firmadata sikre, samtidig med at brugerne får mulighed for at arbejde fra enhver enhed og fra en hvilken som helst placering.

Når du har konfigureret politikker for enhedsoverholdelse og tildelt disse til brugergrupper, kan Intune Azure AD vide, om en enhed er kompatibel eller ej. Hvis du vil bruge denne status som en betingelse for adgang, skal du samarbejde med din Azure AD administrator om at oprette en regel for betinget adgang, der kræver kompatible pc'er og mobilenheder.


![Trin til administration af enheder](../media/devices/intune-mdm-step-3.png#lightbox)

Det anbefalede Nul tillid regelsæt for identitet og enhedsadgang omfatter denne regel. Se [Kræv kompatible pc'er og mobilenheder](../security/office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) som vist nedenfor.


[![Nul tillid politikker for identitet og enhedsadgang](../media/devices/identity-device-require-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-require-compliance.png)



Sørg for at:
- Koordinater de brugergrupper, du har tildelt til politikkerne for overholdelse af angivne standarder, med de brugergrupper, der er tildelt politikken Betinget adgang.
- Test dine politikker for betinget adgang ved hjælp af funktionerne What If og Audit Mode, før du fuldt ud tildeler politikken Betinget adgang. Dette hjælper dig med at forstå resultaterne af politikken.
- Angiv en udvidet periode i overensstemmelse med fortroligheden af de data og/eller apps, der tilgås. 
- Sørg for, at dine politikker for overholdelse af angivne standarder ikke forstyrrer nogen lovmæssige eller andre krav til overholdelse af angivne standarder. 
- Forstå intervallerne for enhedstjek for politikker for overholdelse af angivne standarder.
- Undgå konflikter mellem politikker for overholdelse af regler og standarder og konfigurationsprofiler. Forstå resultaterne, hvis du vælger det.

Hvis du vil foretage fejlfinding af enhedsprofiler i Intune, herunder konflikter mellem politikker, skal [du se Almindelige spørgsmål og svar med enhedspolitikker og -profiler i Microsoft Intune](/mem/intune/configuration/device-profile-troubleshoot).

Bemærk! Hvis du vil starte med at kræve pc'er, der overholder angivne standarder, men ikke mobilenheder, skal du se [Kræv kompatible pc'er (men ikke telefoner og tablets)](../security/office-365-security/identity-access-policies.md) 

## <a name="next-steps"></a>Næste trin

Gå til trin [5. Udrul enhedsprofiler i Microsoft Intune](manage-devices-with-intune-configuration-profiles.md)
