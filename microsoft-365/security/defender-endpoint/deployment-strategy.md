---
title: Planlæg din Microsoft Defender til slutpunktsinstallation
description: Vælg den bedste implementeringsstrategi for Microsoft Defender til Endpoint til dit miljø
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
ms.openlocfilehash: cfdbb84cfcc2cda08572709adb3b13db83e319fa
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63595834"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planlæg din Microsoft Defender til slutpunktsinstallation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Planlæg din installation af Microsoft Defender til slutpunkt, så du kan maksimere sikkerhedsfunktionerne i pakken og bedre beskytte din virksomhed mod cybertrusler.

Denne løsning giver vejledning i, hvordan du identificerer din miljøarkitektur, vælger den type udrulningsværktøj, der passer bedst til dine behov, og vejledning i, hvordan du konfigurerer funktioner.

![Billede af installationsflow.](images/deployment-guide-plan.png)

## <a name="step-1-identify-architecture"></a>Trin 1: Identificer arkitektur

Vi forstår, at alle virksomhedsmiljøer er unikke, så vi har givet dig flere muligheder for at give dig fleksibilitet til at vælge, hvordan du vil installere tjenesten.

Afhængigt af dit miljø er nogle værktøjer bedre egnet til bestemte arkitekturer.

Brug følgende materiale til at vælge den relevante Defender til Endpoint-arkitektur, der passer bedst til din organisation.

| Element | Beskrivelse |
|:-----|:-----|
|[![Thumb image for Defender for Endpoint deployment strategy.](images/mde-deployment-strategy.png)](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Det arkitektoniske materiale hjælper dig med at planlægge din installation for følgende arkitekturer: <ul><li> Skybaseret </li><li> Medadministration </li><li> Lokalt miljø</li><li>Evaluering og lokal onboarding</li>

## <a name="step-2-select-deployment-method"></a>Trin 2: Vælg installationsmetode

| Slutpunkt     | Udrulningsværktøj                       |
|--------------|------------------------------------------|
| **Windows**  |  [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobilenhedshåndtering](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender til skyen](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Lokalt script](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Administration af mobilenheder](mac-install-with-other-mdm.md) |
| **Linux Server** | [Lokalt script](linux-install-manually.md) <br> [Eller Eller](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 

I følgende tabel vises de understøttede slutpunkter og det tilsvarende udrulningsværktøj, du kan bruge, så du kan planlægge installationen korrekt.

|Slutpunkt|Udrulningsværktøj|
|---|---|
|**Windows**|[Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobilenhedshåndtering](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender til skyen](configure-server-endpoints.md#integration-with-azure-defender)|
|**macOS**|[Lokalt script](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Administration af mobilenheder](mac-install-with-other-mdm.md)|
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
