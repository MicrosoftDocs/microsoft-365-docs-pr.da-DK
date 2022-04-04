---
title: Få enheder onboardet til Microsoft Defender for Endpoint
description: Spor onboarding af Intune-administrerede enheder for at Microsoft Defender for Endpoint og øge onboardinghastigheden.
keywords: onboard, Intune, Microsoft Defender for Endpoint, Microsoft Defender, Windows Defender, konfigurationsstyring
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
ms.openlocfilehash: 6caaddc208e6f73de0f49ff6d419c335848ae439
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466317"
---
# <a name="get-devices-onboarded-to-microsoft-defender-for-endpoint"></a>Få enheder onboardet til Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Hver onboarded device tilføjer en ekstra slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) sensor og øger synligheden i forhold til brudaktivitet i dit netværk. Onboarding sikrer også, at en enhed kan kontrolleres for følsomme komponenter samt problemer med sikkerhedskonfiguration og kan modtage kritiske afhjælpningshandlinger under angreb.

Før du kan spore og administrere onboarding af enheder:

- [Tilmeld dine enheder til Intune administration](configure-machines.md#enroll-devices-to-intune-management)
- [Sørg for, at du har de nødvendige tilladelser](configure-machines.md#obtain-required-permissions)

## <a name="discover-and-track-unprotected-devices"></a>Find og spor ubeskyttede enheder

**Onboarding-kortet** giver en detaljeret oversigt over din onboardinghastighed ved at sammenligne antallet af Windows-enheder, der faktisk er onboardet til Defender til slutpunkt med det samlede antal Intune-administrerede Windows-enheder.

:::image type="content" source="images/secconmgmt_onboarding_card.png" alt-text="Onboardingkortet til enhedskonfiguration" lightbox="images/secconmgmt_onboarding_card.png":::

*Kort, der viser onboardede enheder sammenlignet med det samlede antal Intune-administrerede Windows enhed*

> [!NOTE]
> Hvis du har Configuration Manager, onboardingscriptet eller andre onboardingmetoder, der ikke bruger Intune profiler, kan du støde på datauoverensstemmelser. For at løse disse uoverensstemmelser skal du oprette en Intune konfigurationsprofil for Defender til slutpunkt-onboarding og tildele denne profil til dine enheder.

## <a name="onboard-more-devices-with-intune-profiles"></a>Onboard flere enheder med Intune profiler

Defender til Slutpunkt giver dig adskillige praktiske muligheder for [onboarding Windows enheder](onboard-configure.md). På Intune-administrerede enheder kan du dog udnytte Intune-profiler til nemt at installere Defender til Endpoint-sensoren for at vælge enheder og hurtigt onboarde disse enheder til tjenesten.

Fra **onboardingkortet skal** du vælge **Onboard flere enheder for** at oprette og tildele en profil Intune. Linket fører dig til siden til enhedsoverholdelse på Intune, som giver en lignende oversigt over din onboardingtilstand.

:::image type="content" source="images/secconmgmt_onboarding_1deviceconfprofile.png" alt-text="Siden Microsoft Defender for Endpoint til enhedsoverholdelse Intune administration af enheder" lightbox="images/secconmgmt_onboarding_1deviceconfprofile.png":::

*Microsoft Defender for Endpoint til enhedsoverholdelse på Intune administration af enheder*

> [!TIP]
> Alternativt kan du gå til siden til overholdelse af regler og standarder for Defender for Endpoint onboarding i [Microsoft Azure-portalen](https://portal.azure.com/) fra Alle tjenester **> Intune > Enhedsoverholdelse > Microsoft Defender ATP**.

> [!NOTE]
> Hvis du vil have vist de mest opdaterede enhedsdata, skal du klikke på Liste **over enheder uden ATP-sensor**.

Fra siden til enhedsoverholdelse skal du oprette en konfigurationsprofil, der er specifikt for installation af Defender til Endpoint-sensoren og tildele denne profil til de enheder, du vil onboarde. For at gøre dette kan du enten:

- Vælg **Opret en enhedskonfigurationsprofil for at konfigurere ATP-sensoren** til at starte med en foruddefineret enhedskonfigurationsprofil.
- Opret enhedskonfigurationsprofilen fra bunden.

Du kan få mere at [vide ved at læse om Intune af enhedskonfigurationsprofiler til onboard-enheder til Defender til Slutpunkt](/intune/advanced-threat-protection#onboard-devices-by-using-a-configuration-profile).

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Sørg for, at dine enheder er konfigureret korrekt](configure-machines.md)
- [Øg overholdelse af sikkerhed i Defender for Endpoint på grundlinjen](configure-machines-security-baseline.md)
- [Optimer installation og registrering af ASR-regler](configure-machines-asr.md)
