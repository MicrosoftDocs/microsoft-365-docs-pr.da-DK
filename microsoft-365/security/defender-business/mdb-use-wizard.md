---
title: Brug installationsguiden i Microsoft Defender til virksomheder
description: Defender for Business indeholder en guidelignende konfigurations- og konfigurationsproces. Brug guiden til at spare tid og kræfter.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/12/2022
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
ms.openlocfilehash: 1f128a48e8ee2939b4bfcc270c110e0ec63d6ebe
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862582"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>Brug installationsguiden i Microsoft Defender til virksomheder

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 

Microsoft Defender til virksomheder var designet til at spare små og mellemstore virksomheder tid og kræfter. Du kan f.eks. foretage indledende konfiguration med en installationsguide. Konfigurationsguiden hjælper dig med at tildele adgang til dit sikkerhedsteam, konfigurere mailmeddelelser til dit sikkerhedsteam og onboarde virksomhedens Windows enheder.

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="how-to-start-the-setup-wizard"></a>Sådan starter du installationsguiden

Installationsguiden er udviklet til at køre, første gang en person i virksomheden logger på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). 

Hvis din virksomhed har brugt Microsoft 365 Business Premium, køres installationsguiden til Defender for Business, første gang nogen går til **EndpointsDevice-lageret** > . 

Startskærmen i installationsguiden ligner følgende billede:

:::image type="content" source="media/mdb-wizard-start.png" alt-text="Skærmbillede af startskærmen i guiden til konfiguration af Defender for Business.":::

## <a name="the-setup-wizard-flow"></a>Konfigurationsguideflowet

> [!IMPORTANT]
> Du skal være global administrator for at køre installationsguiden. Den person, der har tilmeldt dit firma til Microsoft 365 eller Microsoft Defender til virksomheder, er som standard global administrator.

Installationsguiden er udviklet til at hjælpe dig med hurtigt og effektivt at konfigurere Defender for Business. Guiden fører dig gennem følgende trin:

1. **Tildel brugertilladelser**. I dette trin skal du give sikkerhedsteamet adgang til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). På denne portal kan du og dit sikkerhedsteam administrere dine sikkerhedsfunktioner, få vist beskeder og foretage de nødvendige handlinger på registrerede trusler. Portaladgang tildeles via roller, der indebærer visse tilladelser.

   I Defender for Business kan medlemmer af dit sikkerhedsteam tildeles en af følgende tre roller:<br/>
   
   - **Global administrator**: En global administrator kan få vist og redigere alle indstillinger på tværs af din Microsoft 365 lejer. Den globale administrator udfører den indledende konfiguration af din virksomheds Microsoft 365-abonnement. 
   - **Sikkerhedsadministrator**: En sikkerhedsadministrator kan få vist og redigere sikkerhedsindstillinger og udføre handlinger, når der registreres trusler.
   - **Sikkerhedslæser**: En sikkerhedslæser kan få vist oplysninger i rapporter, men kan ikke ændre nogen sikkerhedsindstillinger. 

   [Mer informasjon om roller og tilladelser](mdb-roles-permissions.md). 

2. **Konfigurer mailmeddelelser**. I dette trin kan du konfigurere mailmeddelelser til dit sikkerhedsteam. Når der derefter genereres en besked, eller der registreres en ny sårbarhed, vil dit sikkerhedsteam ikke om det, selvom de er væk fra deres skrivebord. [Mer informasjon om mailmeddelelser](mdb-email-notifications.md). 

3. **Onboarde og konfigurer Windows enheder**. I dette trin kan du hurtigt onboarde din virksomheds Windows-enheder til Defender for Business. Onboarding af enheder med det samme hjælper med at beskytte disse enheder fra dag 1. 

   - **Hvis du allerede bruger Microsoft Endpoint Manager** (hvilket omfatter Microsoft Intune), og din virksomhed har enheder tilmeldt Endpoint Manager, bliver du spurgt, om du vil bruge [automatisk onboarding](#what-is-automatic-onboarding) til nogle eller alle dine tilmeldte Windows enheder. Automatisk onboarding konfigurerer en forbindelse mellem Endpoint Manager og Defender for Business og onboarder derefter uden problemer Windows enheder til Defender for Business. 
   - **Hvis du ikke allerede bruger Endpoint Manager**, kan du [onboarde enheder til Defender for Business](mdb-onboard-devices.md). 
   
   [Mer informasjon om onboarding af enheder til Microsoft Defender til virksomheder](mdb-onboard-devices.md).
   
4. **Konfigurer dine sikkerhedspolitikker**. Defender for Business indeholder standardsikkerhedspolitikker for næste generations beskyttelse og firewallbeskyttelse, der kan anvendes på virksomhedens enheder. Disse standardpolitikker bruger anbefalede indstillinger og er designet til at yde stærk beskyttelse af dine enheder. Du kan også oprette dine egne sikkerhedspolitikker. Og hvis du allerede bruger Endpoint Manager, kan du fortsætte med at bruge det til at administrere dine sikkerhedspolitikker.

   [Få vist og rediger dine sikkerhedspolitikker og -indstillinger](mdb-configure-security-settings.md).

## <a name="what-is-automatic-onboarding"></a>Hvad er automatisk onboarding?

Automatisk onboarding er en forenklet måde at onboarde Windows enheder på til Defender for Business. Automatisk onboarding er kun tilgængelig for Windows enheder, der allerede er tilmeldt Microsoft Endpoint Manager (eller Microsoft Intune). 

Mens du bruger installationsguiden, registrerer systemet, om Windows enheder allerede er tilmeldt Endpoint Manager. Du bliver spurgt, om du vil bruge automatisk onboarding for alle eller nogle af disse enheder. Du kan onboarde alle Windows enheder på én gang, eller du kan vælge bestemte enheder, du vil starte med, og derefter tilføje flere enheder senere. 

Hvis du vil onboarde andre enheder, skal du se [Onboard enheder til Microsoft Defender til virksomheder](mdb-onboard-devices.md).

> [!TIP]
> - Vi anbefaler, at du vælger indstillingen "alle de enheder, der er tilmeldt". På den måde bliver Windows enheder automatisk onboardet i Defender for Business, når de er tilmeldt Endpoint Manager senere. 
> - Hvis du har administreret sikkerhedspolitikker og -indstillinger i Endpoint Manager, anbefaler vi, at du skifter til Microsoft 365 Defender portal for at administrere dine enheder, politikker og indstillinger. Du kan få mere at vide under [Vælg, hvor du vil administrere sikkerhedspolitikker og -enheder](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices).

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Hvad sker der, hvis jeg ikke bruger guiden?

Det er valgfrit at bruge installationsguiden. Hvis du vælger ikke at bruge guiden, eller hvis guiden lukkes, før installationsprocessen er fuldført, kan du selv fuldføre konfigurationsprocessen. 

Se [Konfigurer Microsoft Defender til virksomheder](mdb-setup-configuration.md) for at gennemgå disse trin:

1. **[Tildel roller og tilladelser,](mdb-roles-permissions.md)** så sikkerhedsteamet kan få adgang til og bruge Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

2. **[Konfigurer mailmeddelelser til dit sikkerhedsteam](mdb-email-notifications.md)** , så de er i løkken om nye beskeder eller sikkerhedsrisici.

3. **[Onboarde enheder](mdb-onboard-devices.md)** , så de er beskyttet af Defender for Business.

4. **[Administrer dine sikkerhedspolitikker](mdb-configure-security-settings.md)**, som omfatter næste generations beskyttelse, firewallbeskyttelse og filtrering af webindhold.

## <a name="next-steps"></a>Næste trin

- [Onboarder flere enheder for at Microsoft Defender til virksomheder](mdb-onboard-devices.md)
- [Få vist og rediger dine sikkerhedspolitikker og -indstillinger i Microsoft Defender til virksomheder](mdb-configure-security-settings.md)