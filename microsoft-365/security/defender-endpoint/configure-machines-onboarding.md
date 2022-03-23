---
title: Få enheder onboardet til Microsoft Defender til Slutpunkt
description: Spor onboarding af Intune-administrerede enheder til Microsoft Defender for Endpoint, og øg onboardinghastigheden.
keywords: onboard, Intune-administration, Microsoft Defender til slutpunkt, Microsoft Defender, Windows Defender, konfigurationsstyring
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
ms.openlocfilehash: ef0f461bef452336052018a26970bad94400fa71
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591284"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Få enheder onboardet til Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Hver onboarded device tilføjer en ekstra slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) sensor og øger synligheden i forhold til brudaktivitet i dit netværk. Onboarding sikrer også, at en enhed kan kontrolleres for følsomme komponenter samt problemer med sikkerhedskonfiguration og kan modtage kritiske afhjælpningshandlinger under angreb.

Før du kan spore og administrere onboarding af enheder:

- [Tilmeld dine enheder til intune-administration](configure-machines.md#enroll-devices-to-intune-management)
- [Sørg for, at du har de nødvendige tilladelser](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>Find og spor ubeskyttede enheder

Onboarding-kortet giver en detaljeret oversigt over din **onboardinghastighed** ved at sammenligne antallet af Windows-enheder, der faktisk er onboardet til Defender til slutpunkt med det samlede antal Intune-administrerede Windows enheder.

![Onboardingkort til enhedskonfiguration.](images/secconmgmt_onboarding_card.png)

*Kort, der viser onboardede enheder sammenlignet med det samlede antal Intune-administrerede Windows enhed*

> [!NOTE]
> Hvis du har Konfigurationsstyring, onboardingscriptet eller andre onboardingmetoder, der ikke bruger Intune-profiler, kan der opstå datauoverensstemmelser. Du kan løse disse uoverensstemmelser ved at oprette en tilsvarende Intune-konfigurationsprofil for Defender til slutpunkts onboarding og tildele denne profil til dine enheder.

## <a name="onboard-more-devices-with-intune-profiles"></a>Onboard flere enheder med Intune-profiler

Defender til Slutpunkt giver dig adskillige praktiske muligheder for [onboarding Windows enheder](onboard-configure.md). På Intune-administrerede enheder kan du dog udnytte Intune-profiler til nemt at udrulle Defender til Endpoint-sensoren for at vælge enheder og hurtigt onboarde disse enheder til tjenesten.

Fra **Onboarding-kortet** skal du vælge **Onboard flere enheder** for at oprette og tildele en profil på Intune. Linket fører dig til siden til enhedsoverholdelse på Intune, som giver en lignende oversigt over din onboardingtilstand.

![Microsoft Defender for endpoint-enhedsoverholdelsesside på administration af Intune-enheder.](images/secconmgmt_onboarding_1deviceconfprofile.png)

*Microsoft Defender for endpoint-enhedsoverholdelsesside på administration af Intune-enheder*

> [!TIP]
> Du kan også gå til siden til overholdelse af regler og standarder for Defender for Endpoint onboarding i [Microsoft Azure-portalen](https://portal.azure.com/) fra **Alle tjenester > Intune > Enhedsoverholdelse > Microsoft Defender ATP**.

> [!NOTE]
> Hvis du vil have vist de mest opdaterede enhedsdata, skal du klikke på Liste **over enheder uden ATP-sensor**.

Fra siden til enhedsoverholdelse skal du oprette en konfigurationsprofil, der er specifikt for installation af Defender til Endpoint-sensoren og tildele denne profil til de enheder, du vil onboarde. For at gøre dette kan du enten:

- Vælg **Opret en enhedskonfigurationsprofil for at konfigurere ATP-sensoren** til at starte med en foruddefineret enhedskonfigurationsprofil.
- Opret enhedskonfigurationsprofilen fra bunden.

Du kan få mere at [vide ved at læse om at bruge Intune-enhedskonfigurationsprofiler til at onboarde enheder til Defender til Slutpunkt](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Sørg for, at dine enheder er konfigureret korrekt](configure-machines.md)
- [Øg overholdelse af sikkerhed i Defender for Endpoint på grundlinjen](configure-machines-security-baseline.md)
- [Optimer installation og registrering af ASR-regler](configure-machines-asr.md)
