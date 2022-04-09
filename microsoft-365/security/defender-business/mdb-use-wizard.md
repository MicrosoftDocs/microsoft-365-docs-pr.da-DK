---
title: Brug installationsguiden i Microsoft Defender til virksomheder
description: Defender for Business indeholder en guidelignende konfigurations- og konfigurationsproces. Brug guiden til at spare tid og kræfter.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: ad070273567d350973037f1ac5a0192036d22187
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746639"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>Brug installationsguiden i Microsoft Defender til virksomheder

> [!IMPORTANT]
> Microsoft Defender til virksomheder udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra den 1. marts 2022. Defender for Business som et separat abonnement fås som prøveversion og udrulles gradvist til kunder og [it-partnere, der tilmelder sig her](https://aka.ms/mdb-preview) for at anmode om det. Prøveversionen indeholder et [indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer jævnligt funktioner.
> 
> Nogle oplysninger i denne artikel er relateret til forhåndsudgivne produkter/tjenester, der kan blive ændret væsentligt, før de udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, for de oplysninger, der er angivet her. 

Microsoft Defender til virksomheder er udviklet til at spare tid og kræfter på små og mellemstore virksomheder med en guidelignende oplevelse til indledende konfiguration. Konfigurationsguiden hjælper dig med at tildele adgang til dit sikkerhedsteam, konfigurere mailmeddelelser til dit sikkerhedsteam og onboarde virksomhedens Windows enheder.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Skærmbillede af startskærmen i guiden til konfiguration af Defender for Business.":::

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om Microsoft Defender til virksomheder</a>. Vi vil meget gerne høre fra dig!
>

## <a name="overview-of-the-setup-wizard"></a>Oversigt over installationsguiden

> [!IMPORTANT]
> Før du begynder, skal du sørge for, at du allerede har føjet brugere til dit Microsoft 365 abonnement. Hvis du vil have hjælp til denne opgave, skal du se [Tilføj brugere og tildel licenser på samme tid](../../admin/add-users/add-users.md).

Guiden er udviklet til at hjælpe dig med hurtigt og effektivt at konfigurere Defender for Business. Guiden fører dig gennem følgende trin:

1. **Tildel brugertilladelser**. I dette trin skal du give sikkerhedsteamet adgang til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). På denne portal kan du og dit sikkerhedsteam administrere dine sikkerhedsfunktioner, få vist beskeder og foretage de nødvendige handlinger på registrerede trusler. Portaladgang tildeles via roller, der indebærer visse tilladelser.

   I Defender for Business kan medlemmer af dit sikkerhedsteam tildeles en af tre roller:<br/>
   
      - **Global administrator**: En global administrator kan få vist og redigere alle indstillinger på tværs af din Microsoft 365 lejer. Den globale administrator udfører den indledende konfiguration af din virksomheds Microsoft 365-abonnement. 
      - **Sikkerhedsadministrator**: En sikkerhedsadministrator kan få vist og redigere sikkerhedsindstillinger og udføre handlinger, når der registreres trusler.
      - **Sikkerhedslæser**: En sikkerhedslæser kan få vist oplysninger i rapporter, men kan ikke ændre nogen sikkerhedsindstillinger. 
      
      [Få mere at vide om roller og tilladelser](mdb-roles-permissions.md). 

2. **Konfigurer mailmeddelelser**. I dette trin kan du konfigurere mailmeddelelser til dit sikkerhedsteam. Når der derefter genereres en besked, eller der registreres en ny sårbarhed, vil dit sikkerhedsteam ikke om det, selvom de er væk fra deres skrivebord. 

   [Få mere at vide om mailmeddelelser](mdb-email-notifications.md). 

3. **Onboarde og konfigurer Windows enheder**. I dette trin kan du hurtigt onboarde din virksomheds Windows-enheder til Defender for Business. Onboarding af enheder med det samme hjælper med at beskytte disse enheder fra dag 1. 

   - **Hvis du allerede bruger Microsoft Endpoint Manager** (hvilket omfatter Microsoft Intune), og din virksomhed har enheder tilmeldt Endpoint Manager, bliver du spurgt, om du vil bruge [automatisk onboarding](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) til nogle eller alle dine tilmeldte Windows enheder. Automatisk onboarding konfigurerer en forbindelse mellem Endpoint Manager og Defender for Business og onboarder derefter uden problemer Windows enheder til Defender for Business. 
   - **Hvis du ikke allerede bruger Endpoint Manager**, kan du [onboarde enheder til Defender for Business ved hjælp af et lokalt script](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
   Se [Få mere at vide om onboarding af enheder til Microsoft Defender til virksomheder](mdb-onboard-devices.md).
   
4. **Konfigurer dine sikkerhedspolitikker**. Defender for Business indeholder standardsikkerhedspolitikker for næste generations beskyttelse og firewallbeskyttelse, der kan anvendes på virksomhedens enheder. Disse standardpolitikker bruger anbefalede indstillinger og er designet til at yde stærk beskyttelse af dine enheder. Du kan også oprette dine egne sikkerhedspolitikker. Og hvis du allerede bruger Endpoint Manager, kan du fortsætte med at bruge det til at administrere dine sikkerhedspolitikker.

   Du kan få mere at vide under [Få vist og rediger dine sikkerhedspolitikker og -indstillinger](mdb-configure-security-settings.md). |

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Hvad sker der, hvis jeg ikke bruger guiden?

Det er valgfrit at bruge installationsguiden. Hvis du vælger ikke at bruge guiden, eller hvis guiden lukkes, før installationsprocessen er fuldført, kan du selv fuldføre konfigurationsprocessen. Se [Konfigurer Microsoft Defender til virksomheder](mdb-setup-configuration.md) for at gennemgå disse trin:

1. **[Tildel roller og tilladelser,](mdb-roles-permissions.md)** så sikkerhedsteamet kan få adgang til og bruge Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

2. **[Konfigurer mailmeddelelser til dit sikkerhedsteam](mdb-email-notifications.md)** , så de er i løkken om nye beskeder eller sikkerhedsrisici.

3. **[Onboarde enheder](mdb-onboard-devices.md)** , så de er beskyttet af Defender for Business.

4. **[Administrer dine sikkerhedspolitikker](mdb-configure-security-settings.md)**, som omfatter næste generations beskyttelse, firewallbeskyttelse og filtrering af webindhold.

## <a name="next-steps"></a>Næste trin

- [Konfigurer mailmeddelelser til dit sikkerhedsteam](mdb-email-notifications.md)

- [Kom i gang med at bruge Microsoft 365 Defender-portalen](mdb-get-started.md)

- [Brug dashboardet Administration af sårbarheder & Threat &](mdb-view-tvm-dashboard.md)