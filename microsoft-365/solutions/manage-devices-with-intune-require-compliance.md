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
description: Opret en politik for betinget adgang i Azure AD for at kræve kompatible enheder, så virksomhedens data er sikre, når brugere arbejder fra en hvilken som helst enhed på et hvilket som helst sted.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- Conditional access policy
- Microsoft Intune
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
ms.openlocfilehash: 8a953c76a3461b0f6dbf1b3663d5cef41f038371
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63593646"
---
# <a name="step-4-require-healthy-and-compliant-devices-with-intune"></a>Trin 4. Kræv sunde og kompatible enheder med Intune

Betinget adgang giver yderligere bekræftelse af enhedsstatus, før der gives adgang til en tjeneste. Betinget adgang virker ikke, medmindre du angiver betingelser. I [trin 3. Konfigurer politikker for overholdelse af regler og](manage-devices-with-intune-compliance-policies.md) standarder. Du har defineret overholdelsespolitikker, der angiver de minimumskrav, en enhed skal opfylde for at få adgang til dit miljø. I denne artikel skal du oprette den tilsvarende politik for Betinget adgang i Azure AD, så der kræves kompatible enheder. Dette er med til at beskytte virksomhedens data og samtidig give brugerne mulighed for at arbejde fra enhver enhed og fra enhver placering.

Når du har konfigureret politikker for enhedsoverholdelse og tildelt disse til brugergrupper, fortæller Intune Azure AD, om en enhed er kompatibel eller ej. Hvis du vil bruge denne status som en betingelse for adgang, skal du arbejde sammen med din Azure AD-administrator for at oprette en regel for Betinget adgang, så der kræves kompatible pc'er og mobilenheder.


![Trin til administration af enheder](../media/devices/intune-mdm-step-3.png#lightbox)

Det anbefalede nultillidssæt for identitet og enhedsadgangsregelsæt omfatter denne regel. Se [Kræv kompatible pc'er og mobilenheder](../security/office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices), som vist nedenfor.


[![Politikker for nultillidshed og enhedsadgang](../media/devices/identity-device-require-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-require-compliance.png)



Sørg for at:
- Koordiner de brugergrupper, du har tildelt til dine overholdelsespolitikker, med de brugergrupper, der er tildelt politikken Betinget adgang.
- Test politikkerne for Betinget adgang ved hjælp af funktionerne Hvad hvis- og Overvågningstilstand, før politikken Betinget adgang tildeles fuldt ud. Dette hjælper dig med at forstå resultaterne af politikken.
- Angiv en udvidet periode i overensstemmelse med fortroligheden af de data og/eller apps, der tilgås. 
- Sørg for, at dine politikker for overholdelse af regler og standarder ikke forstyrrer nogen lovkrav eller andre krav til overholdelse af regler og standarder. 
- Forstå enheders intervaller for indtjekning for politikker for overholdelse af regler og standarder.
- Undgå konflikter mellem politikker for overholdelse af regler og standarder og konfigurationsprofiler. Forstå udfaldene, hvis du vælger det.

Hvis du vil foretage fejlfinding af enhedsprofiler i Intune, herunder konflikter mellem politikker, skal du se Almindelige spørgsmål og svar med enhedspolitikker [og -profiler Microsoft Intune](/mem/intune/configuration/device-profile-troubleshoot).

Bemærk! Hvis du vil starte med at kræve kompatible pc'er, men ikke mobilenheder, skal du se Kræv kompatible [pc'er (men ikke telefoner og tablets)](../security/office-365-security/identity-access-policies.md) 

## <a name="next-steps"></a>Næste trin

Gå til Trin [5. Installér enhedsprofiler i Microsoft Intune](manage-devices-with-intune-configuration-profiles.md)
