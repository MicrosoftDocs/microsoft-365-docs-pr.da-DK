---
title: Få enheder onboardet til Microsoft Defender for Endpoint
description: Spor onboarding af Intune-administrerede enheder for at Microsoft Defender for Endpoint og øge onboardinghastigheden.
keywords: onboard, Intune administration, Microsoft Defender for Endpoint, Microsoft Defender, Windows Defender, konfigurationsstyring
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1e77f404b70ee770bd4d5c441362739cc7b2f13c
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622962"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Få enheder onboardet til Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Hver onboardede enhed tilføjer en ekstra slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) sensor og øger synligheden over brudaktivitet på dit netværk. Onboarding sikrer også, at en enhed kan kontrolleres for sårbare komponenter samt problemer med sikkerhedskonfiguration og kan modtage kritiske afhjælpningshandlinger under angreb.

Før du kan spore og administrere onboarding af enheder:

- [Tilmeld dine enheder til Intune administration](configure-machines.md#enroll-devices-to-intune-management)
- [Sørg for, at du har de nødvendige tilladelser](configure-machines.md#obtain-required-permissions)

Se denne video for at få mere at vide om, hvordan du nemt onboarder klienter med Microsoft Defender for Endpoint.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4bGqr?rel=0]

## <a name="discover-and-track-unprotected-devices"></a>Find og spor ubeskyttede enheder

**Onboarding-kortet** giver et højt overblik over din onboardingfrekvens ved at sammenligne antallet af Windows enheder, der faktisk er onboardet til Defender for Endpoint, med det samlede antal Intune-administrerede Windows enheder.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="Onboarding-kortet administration af enhedskonfiguration" lightbox="images/secconmgmt_onboarding_card.png":::

*Kort, der viser onboardede enheder sammenlignet med det samlede antal Intune-administrerede Windows enheder*

> [!NOTE]
> Hvis du har brugt Configuration Manager, onboardingscriptet eller andre onboardingmetoder, der ikke bruger Intune profiler, kan du støde på dataafvigelser. Du kan løse disse uoverensstemmelser ved at oprette en tilsvarende Intune konfigurationsprofil til onboarding af Defender for Endpoint og tildele denne profil til dine enheder.

## <a name="onboard-more-devices-with-intune-profiles"></a>Onboarder flere enheder med Intune profiler

Defender for Endpoint indeholder flere praktiske muligheder for [onboarding Windows enheder](onboard-configure.md). For Intune-administrerede enheder kan du dog udnytte Intune profiler til nemt at udrulle Defender for Endpoint-sensoren til at vælge enheder og effektivt onboarde disse enheder til tjenesten.

På **Onboarding-kortet** skal du vælge **Onboarder flere enheder** for at oprette og tildele en profil på Intune. Linket fører dig til siden med overholdelse af angivne standarder for enheden på Intune, som giver et lignende overblik over din onboarding-tilstand.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="Siden Microsoft Defender for Endpoint enhedsoverholdelse på Intune enhedsstyring" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Microsoft Defender for Endpoint siden med enhedsoverholdelse på Intune enhedshåndtering*

> [!TIP]
> Du kan også navigere til siden med overholdelse af angivne standarder for onboarding af Defender for Endpoint på [Microsoft Azure-portalen](https://portal.azure.com/) fra **Alle tjenester > Intune > Enhedens overholdelse > Microsoft Defender ATP**.

> [!NOTE]
> Hvis du vil have vist de nyeste enhedsdata, skal du klikke på **Liste over enheder uden ATP-sensor**.

Fra siden med enhedsoverholdelse skal du oprette en konfigurationsprofil specifikt til installation af Defender for Endpoint-sensoren og tildele denne profil til de enheder, du vil onboarde. For at gøre dette kan du enten:

- Vælg **Opret en enhedskonfigurationsprofil for at konfigurere ATP-sensoren** til at starte med en foruddefineret enhedskonfigurationsprofil.
- Opret enhedskonfigurationsprofilen fra bunden.

Du kan finde flere oplysninger [ved at læse om, hvordan du bruger Intune enhedskonfigurationsprofiler til at føje enheder til Defender for Endpoint](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Sørg for, at dine enheder er konfigureret korrekt](configure-machines.md)
- [Øg overholdelse af defender for endpoint security baseline](configure-machines-security-baseline.md)
- [Optimer udrulning og registreringer af ASR-regler](configure-machines-asr.md)
