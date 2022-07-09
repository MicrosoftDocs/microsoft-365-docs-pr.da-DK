---
title: Planlæg din Microsoft Defender for Endpoint udrulning
description: Vælg den bedste Microsoft Defender for Endpoint udrulningsstrategi for dit miljø
keywords: udrul, plan, udrulningsstrategi, oprindelig cloud, administration, i det lokale miljø, evaluering, onboarding, lokal, gruppepolitik, gp, slutpunktschef, mem
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 009c0ef044595781aaf1cb233550d2686f6ed7df
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/09/2022
ms.locfileid: "66696178"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planlæg din Microsoft Defender for Endpoint udrulning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Planlæg din Microsoft Defender for Endpoint udrulning, så du kan maksimere sikkerhedsfunktionerne i pakken og beskytte din virksomhed bedre mod cybertrusler.

Denne løsning indeholder en vejledning i, hvordan du identificerer din miljøarkitektur, vælger den type udrulningsværktøj, der passer bedst til dine behov, og vejledning til, hvordan du konfigurerer egenskaber.

:::image type="content" source="images/deployment-guide-plan.png" alt-text="Udrulningsflowet" lightbox="images/deployment-guide-plan.png":::

## <a name="step-1-identify-architecture"></a>Trin 1: Identificer arkitektur

Vi forstår, at alle virksomhedsmiljøer er unikke, så vi har givet dig flere muligheder for at give dig fleksibiliteten til at vælge, hvordan du vil udrulle tjenesten.

Afhængigt af dit miljø er nogle værktøjer bedre egnet til visse arkitekturer.

Brug følgende materiale til at vælge den relevante Defender for Endpoint-arkitektur, der passer bedst til din organisation.

| Element | Beskrivelse |
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Strategien for installation af Defender for Endpoint" lightbox="images/mde-deployment-strategy.png":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)  \| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) | Det arkitektoniske materiale hjælper dig med at planlægge din udrulning for følgende arkitekturer: <ul><li> Oprindelig sky </li><li> Fælles administration </li><li> Det lokale</li><li>Evaluering og lokal onboarding</li>

## <a name="step-2-select-deployment-method"></a>Trin 2: Vælg installationsmetode

I følgende tabel vises de understøttede slutpunkter og det tilsvarende udrulningsværktøj, som du kan bruge, så du kan planlægge installationen korrekt.

|Slutpunkt|Installationsværktøj|
|---|---|
|**Windows**|[Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobil Enhedshåndtering](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)|
|**Macos**|[Lokalt script](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Enhedshåndtering](mac-install-with-other-mdm.md)|
|**Linux Server**|[Lokalt script](linux-install-manually.md) <br> [Marionet](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**Ios**|[Appbaseret](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>Trin 3: Konfigurer funktioner

Når du har onboardet slutpunkter, skal du konfigurere sikkerhedsegenskaberne i Defender for Endpoint, så du kan maksimere den robuste sikkerhedsbeskyttelse, der er tilgængelig i pakken. Egenskaber omfatter:

- Slutpunktsregistrering og -svar
- Næste generations beskyttelse
- Reduktion af angrebsoverfladen

## <a name="related-topics"></a>Relaterede emner

- [Udrulningsfaser](deployment-phases.md)
