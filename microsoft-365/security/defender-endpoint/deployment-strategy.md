---
title: Planlæg din Microsoft Defender for Endpoint installation
description: Vælg den bedste Microsoft Defender for Endpoint til dit miljø
keywords: deploy, plan, deployment strategy, cloud native, management, on prem, evaluation, onboarding, local, group policy, gp, endpoint manager, mem
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
ms.openlocfilehash: 05ae6e0669784aef515d678835f0fa48be0f9f3f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471247"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planlæg din Microsoft Defender for Endpoint installation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Planlæg din Microsoft Defender for Endpoint installation, så du kan maksimere sikkerhedsfunktionerne i pakken og bedre beskytte din virksomhed mod cybertrusler.

Denne løsning giver vejledning i, hvordan du identificerer din miljøarkitektur, vælger den type udrulningsværktøj, der passer bedst til dine behov, og vejledning i, hvordan du konfigurerer funktioner.

:::image type="content" source="images/deployment-guide-plan.png" alt-text="Installationsflowet" lightbox="images/deployment-guide-plan.png":::

## <a name="step-1-identify-architecture"></a>Trin 1: Identificer arkitektur

Vi forstår, at alle virksomhedsmiljøer er unikke, så vi har givet dig flere muligheder for at give dig fleksibilitet til at vælge, hvordan du vil installere tjenesten.

Afhængigt af dit miljø er nogle værktøjer bedre egnet til bestemte arkitekturer.

Brug følgende materiale til at vælge den relevante Defender til Endpoint-arkitektur, der passer bedst til din organisation.

| Element | Beskrivelse |
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Strategi for udrulning af Defender til Endpoint" lightbox="images/mde-deployment-strategy.png":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Det arkitektoniske materiale hjælper dig med at planlægge din installation for følgende arkitekturer: <ul><li> Skybaseret </li><li> Medadministration </li><li> Lokalt miljø</li><li>Evaluering og lokal onboarding</li>

## <a name="step-2-select-deployment-method"></a>Trin 2: Vælg installationsmetode

| Slutpunkt     | Udrulningsværktøj                       |
|--------------|------------------------------------------|
| **Windows**  |  [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile-Enhedshåndtering](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender til skyen](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Lokalt script](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Mobildata Enhedshåndtering](mac-install-with-other-mdm.md) |
| **Linux Server** | [Lokalt script](linux-install-manually.md) <br> [Eller Eller](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 

I følgende tabel vises de understøttede slutpunkter og det tilsvarende udrulningsværktøj, du kan bruge, så du kan planlægge installationen korrekt.

|Slutpunkt|Udrulningsværktøj|
|---|---|
|**Windows**|[Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile-Enhedshåndtering](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender til skyen](configure-server-endpoints.md#integration-with-azure-defender)|
|**macOS**|[Lokalt script](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Mobildata Enhedshåndtering](mac-install-with-other-mdm.md)|
|**Linux Server**|[Lokalt script](linux-install-manually.md) <br> [Eller Eller](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Appbaseret](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>Trin 3: Konfigurer funktioner

Efter onboarding-slutpunkter skal du konfigurere sikkerhedsfunktionerne i Defender til slutpunkt, så du kan maksimere den robuste sikkerhedsbeskyttelse, der er tilgængelig i pakken. Funktioner omfatter:

- Registrering af slutpunkt og svar
- Næste generations beskyttelse
- Reduktion af angrebsoverfladen

## <a name="related-topics"></a>Relaterede emner

- [Installationsfaser](deployment-phases.md)
