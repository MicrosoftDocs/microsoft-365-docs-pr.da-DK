---
title: Onboard enheder og konfigurer Microsoft Defender for Endpoint egenskaber
description: Onboard Windows 10 enheder, servere, ikke-Windows-enheder, og få mere at vide om, hvordan du kører en registreringstest.
keywords: onboarding, Microsoft Defender for Endpoint onboarding, sccm, gruppepolitik, mdm, lokalt script, registreringstest
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 350f5675d1426c354f1e2ac848d3a9d14f1ecc76
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469663"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>Onboard enheder og konfigurer Microsoft Defender for Endpoint egenskaber

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Installation Microsoft Defender for Endpoint er en proces i to trin.

- Onboard-enheder til tjenesten
- Konfigurere tjenestens funktioner

:::image type="content" source="images/deployment-steps.png" alt-text="Onboarding- og konfigurationsprocessen" lightbox="images/deployment-steps.png":::

## <a name="onboard-devices-to-the-service"></a>Onboard-enheder til tjenesten
Du skal gå til onboardingsektionen i Defender for Endpoint-portalen for at onboarde en af de understøttede enheder. Afhængigt af enheden bliver du vejledt med de relevante trin og de administrations- og installationsværktøjsindstillinger, der passer til enheden. 

Generelt til onboard enheder til tjenesten:

- Kontrollér, at enheden opfylder [minimumskravene](minimum-requirements.md)
- Afhængigt af enheden skal du følge de konfigurationstrin, der er angivet i onboardingsektionen i Defender for Endpoint-portalen
- Brug det relevante administrationsværktøj og installationsmetode til dine enheder
- Kør en registreringstest for at bekræfte, at enhederne er korrekt onboardet og rapporterer til tjenesten



## <a name="onboarding-and-configuration-tool-options"></a>Indstillinger for onboarding- og konfigurationsværktøj
I følgende tabel vises de tilgængelige værktøjer baseret på det slutpunkt, du skal bruge til onboarding.

| Slutpunkt     | Værktøjsindstillinger                       |
|--------------|------------------------------------------|
| **Windows**  |  [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile-Enhedshåndtering](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender til skyen](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Lokale scripts](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Mobildata Enhedshåndtering](mac-install-with-other-mdm.md) |
| **Linux Server** | [Lokalt script](linux-install-manually.md) <br> [Eller Eller](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)               |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)            | 


I følgende tabel vises de tilgængelige værktøjer baseret på det slutpunkt, du skal bruge til onboarding.

## <a name="configure-capabilities-of-the-service"></a>Konfigurere tjenestens funktioner
Onboardingenheder aktiverer effektivt slutpunktsregistrering og -svar funktion af Micorosft Defender til slutpunkt.

Når du har onboardet enhederne, skal du derefter konfigurere de andre funktioner i tjenesten. I følgende tabel vises de funktioner, du kan konfigurere for at få den bedste beskyttelse af dit miljø.

| Funktion | Beskrivelse |
|-|-|
| [Konfigurere TVM (Threat & Vulnerability Management)](tvm-prerequisites.md) | Administration & mod trusler er en komponent i Microsoft Defender for Endpoint og giver både sikkerhedsadministratorer og sikkerhedsteams unik værdi, herunder: <br><br> - Indsigt i realtid slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) korreleret med slutpunktssårbarheder. <br><br> - Uvurderlig enhedssikkerhedsrisiko under hændelsesundersøgelse. <br><br> - Indbyggede afhjælpningsprocesser via Microsoft Intune og Microsoft System Center Configuration Manager.  |
| [Konfigurer næste generations beskyttelse (NGP)](configure-microsoft-defender-antivirus-features.md) | Microsoft Defender Antivirus er en indbygget antimalwareløsning, der giver næste generations beskyttelse til stationære computere, bærbare computere og servere. Microsoft Defender Antivirus indeholder:<br> <br>Cloud-leveret beskyttelse til øjeblikkelig registrering og blokering af nye og nye trusler. Ud over maskinlæring og intelligent sikkerheds Graph er cloud-leveret beskyttelse en del af den næste generation af teknologier, der Microsoft Defender Antivirus.<br> <br> - Scanning altid ved hjælp af avanceret overvågning af fil- og procesfunktionsmåder og andre heuristiske funktioner (også kaldet "beskyttelse i realtid").<br><br> - Dedicated protection updates based on machine learning, human and automated big-data analysis, and in-depth threat resistance research. |
| [Konfigurer reduktion af angrebsoverfladen (ASR)](overview-attack-surface-reduction.md) | Reduktion af angrebsoverfladen i Microsoft Defender for Endpoint med at beskytte enheder og programmer i organisationen mod nye og fremspirende trusler. |
| [Konfigurere funktioner til automatisk & afhjælpning (AIR)](configure-automated-investigations-remediation.md) | Microsoft Defender for Endpoint anvender automatiserede undersøgelser til at reducere mængden af beskeder, der skal undersøges individuelt. Funktionen Automatiseret undersøgelse udnytter forskellige inspektionsalgoritmer og processer, der bruges af analytikere (f.eks. playbooks), til at undersøge vigtige beskeder og omgående afhjælpe eventuelle overtrædelser. Dette reducerer mængden af beskeder betydeligt, så sikkerhedseksperter kan fokusere på mere avancerede trusler og andre initiativer med høj værdi. |
| [Konfigurere Microsoft-trusselseksperter (MTE)](configure-microsoft-threat-experts.md) | Microsoft-trusselseksperter er en administreret jagttjeneste, der leverer SECURITY Operation Centers (SOCs) med ekspertniveauovervågning og -analyse for at hjælpe dem med at sikre, at kritiske trusler i deres unikke miljøer ikke overser.      |


## <a name="supported-capabilities-for-windows-devices"></a>Understøttede funktioner til Windows enheder

|Operativsystem  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |Windows Server 2016<sup>[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**Forebyggelse**    |         |         |         |         |         |
|Regler for reduktion af angrebsoverfladen     |    Y     |   Y      |    Y     |    Y     |    Y     |
|Enhedshåndtering     |     Y    |    N     |    N     |    N     |    N     |  
|Firewall     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Netværksbeskyttelse     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Næste generations beskyttelse     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Beskyttelse mod tamper     |        Y   |    Y     |     Y    |    Y    |    Y   |
|Webbeskyttelse     |       Y   |    Y     |     Y    |    Y    |    Y   |
|||||||
|**Registrering**     |         |         |         |||
|Avanceret jagt     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Indikatorer for brugerdefinerede filer     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Brugerdefinerede netværksindikatorer     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Slutpunktsregistrering og -svar blokeret & passiv tilstand     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Sensor til registrering af sans     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Registrering af & slutpunkt på netværksenhed     |      Y   |    N     |     N    |    N    |    N   |
|||||||
|**Svar**     |         |         |         |||
|Automatiseret undersøgelse & svar (AIR)    |      Y   |    Y     |     Y    |    Y    |    Y   |
|Funktionalitet for enhedsrespons: isolation, indsamling af undersøgelsespakke, kør AV-scanning     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Egenskaber for filsvar: indsamle filer, dybdegående analyse, blokere fil, stoppe og sætte processer i karantæne     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Live-svar    |      Y   |    Y     |     Y    |    Y    |    Y   |

(<a id="fn1">1</a>) Henviser til den moderne, samlede løsning til Windows Server 2012 R2 og 2016. Få mere at vide under [Onboard Windows Servers til Defender for Endpoint-tjenesten](configure-server-endpoints.md).

>[!NOTE]
>Windows 7, 8.1, Windows Server 2008 R2 omfatter understøttelse af Slutpunktsregistrering og -svar-sensoren og AV, der bruger System Center Endpoint Protection (SCEP).
