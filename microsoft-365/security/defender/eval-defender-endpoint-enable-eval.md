---
title: Aktivér Microsoft Defender for Endpoint evaluering
description: Aktivér dit Microsoft 365 Defender prøvelaboratorium eller pilotmiljø, herunder kontrol af licenstilstand og onboardingslutpunkter
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 2acde87daaff88ec9ce7458218919342a9f1edd8
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782495"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>Aktivér Microsoft Defender for Endpoint evalueringsmiljø


I denne artikel gennemgås trinnene til konfiguration af evalueringsmiljøet for Microsoft Defender for Endpoint ved hjælp af produktionsenheder. 


> [!TIP]
> Microsoft Defender for Endpoint leveres også med et laboratorie til evaluering i produktet, hvor du kan tilføje forudkonfigurerede enheder og køre simuleringer for at evaluere platformens funktioner. Laboratoriet leveres med en forenklet konfiguration, der kan hjælpe med hurtigt at demonstrere værdien af Microsoft Defender for Endpoint herunder vejledning til mange funktioner som avanceret jagt og trusselsanalyse. Du kan finde flere oplysninger under [Evaluer funktioner](../defender-endpoint/evaluation-lab.md). <br> Den primære forskel mellem vejledningen i denne artikel og evalueringslaboratoriet er, at evalueringsmiljøet bruger produktionsenheder, mens evalueringslaboratoriet bruger enheder, der ikke er produktionsenheder. 

Brug følgende trin til at aktivere evalueringen for Microsoft Defender for Endpoint.

:::image type="content" source="../../media/defender/m365-defender-endpoint-eval-enable-steps.png" alt-text="Trinnene til aktivering af Microsoft Defender for Endpoint i Microsoft Defender-evalueringsmiljøet" lightbox="../../media/defender/m365-defender-endpoint-eval-enable-steps.png":::

- [Trin 1. Kontrollér licenstilstand](#step-1-check-license-state)
- [Trin 2. Onboard-slutpunkter](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>Trin 1. Kontrollér licenstilstand

Du skal først kontrollere licenstilstanden for at bekræfte, at den er korrekt klargjort. Det kan du gøre via Administration eller via **Microsoft Azure-portalen**.


1. Hvis du vil have vist dine licenser, skal du gå til **Microsoft Azure-portalen** og navigere til [afsnittet Microsoft Azure portallicens](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="../../media/defender/atp-licensing-azure-portal.png" alt-text="Siden Azure Licensing på Microsoft 365 Defender-portalen" lightbox="../../media/defender/atp-licensing-azure-portal.png":::

1. Alternativt kan du gå til **FaktureringAbonnementer** >  i Administration.

    På skærmen kan du se alle de klargjorte licenser og deres aktuelle **status**.

    :::image type="content" source="../../media/defender/atp-billing-subscriptions.png" alt-text="Siden Faktureringslicenser på Microsoft Azure-portalen" lightbox="../../media/defender/atp-billing-subscriptions.png":::
    

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Trin 2. Onboarde slutpunkter ved hjælp af et af de understøttede administrationsværktøjer

Når du har bekræftet, at licenstilstanden er klargjort korrekt, kan du begynde at onboarde enheder til tjenesten. 

Med henblik på evaluering af Microsoft Defender for Endpoint anbefaler vi, at du vælger et par Windows enheder til at udføre evalueringen på.

Du kan vælge at bruge et hvilket som helst af de understøttede administrationsværktøjer, men Intune sikrer optimal integration. Du kan få flere oplysninger under [Konfigurer Microsoft Defender for Endpoint i Microsoft Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

I emnet [Planinstallation](../defender-endpoint/deployment-strategy.md) beskrives de generelle trin, du skal udføre for at installere Defender for Endpoint.  

Se denne video for at få et hurtigt overblik over onboardingprocessen og få mere at vide om de tilgængelige værktøjer og metoder.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>Indstillinger for onboardingværktøj

I følgende tabel vises de tilgængelige værktøjer, der er baseret på det slutpunkt, du skal onboarde.

Slutpunkt | Værktøjsindstillinger
:---|:---
**Windows** | [Lokalt script (op til 10 enheder),](../defender-endpoint/configure-endpoints-script.md) [Gruppepolitik](../defender-endpoint/configure-endpoints-gp.md), [Microsoft Endpoint Manager/Mobil-Enhedshåndtering](../defender-endpoint/configure-endpoints-mdm.md), [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md), [VDI-scripts](../defender-endpoint/configure-endpoints-vdi.md), [ Integration med Microsoft Defender for Cloud](../defender-endpoint/configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)
**Macos** | [Lokale scripts](../defender-endpoint/mac-install-manually.md), [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md), [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md), [Mobil Enhedshåndtering](../defender-endpoint/mac-install-with-other-mdm.md)
**Linux Server** | [Lokalt script](../defender-endpoint/linux-install-manually.md),  [dukke](../defender-endpoint/linux-install-with-puppet.md),  [ansibel](../defender-endpoint/linux-install-with-ansible.md)
**Ios** | [Appbaseret](../defender-endpoint/ios-install.md)
**Android** | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>Næste trin
[Konfigurer piloten til Microsoft Defender for Endpoint](eval-defender-endpoint-pilot.md)
 
Vend tilbage til oversigten for [Evaluate Microsoft Defender for Endpoint](eval-defender-endpoint-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
