---
title: Onboard til Microsoft Defender for Endpoint-tjenesten
description: Få mere at vide om at onboarde slutpunkter til Microsoft Defender for Endpoint-tjenesten
keywords: microsoft defender til slutpunkt, onboard, deploy
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
- m365solution-endpointprotect
- m365solution-scenario
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 78f78208798635fb38381deaba3fa2f20e373bea
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63599319"
---
# <a name="onboard-to-the-microsoft-defender-for-endpoint-service"></a>Onboard til Microsoft Defender for Endpoint-tjenesten

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Få mere at vide om de forskellige faser i udrulning af Microsoft Defender til slutpunkt, og hvordan du kan konfigurere funktionerne i løsningen.


Dette er de trin, du skal bruge for at installere Defender til Slutpunkt:

- Trin 1: Onboard slutpunkter til tjenesten
- Trin 2: Konfigurer funktioner

![Illustration af installationstrinnene](images/deployment-steps.png)



## <a name="step-1-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Trin 1: Onboard slutpunkter ved hjælp af et af de understøttede administrationsværktøjer

Emnet [Planlæg](deployment-strategy.md) installation beskriver de generelle trin, du skal følge for at installere Defender til Slutpunkt.

Watch this video for a quick overview of the onboarding process and learn about the available tools and methods.


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Når du har identificeret din arkitektur, skal du beslutte, hvilken installationsmetode der skal bruges. Det udrulningsværktøj, du vælger, påvirker, hvordan du onboarder slutpunkter til tjenesten.

### <a name="onboarding-tool-options"></a>Indstillinger for onboardingværktøj

I følgende tabel vises de tilgængelige værktøjer baseret på det slutpunkt, du skal bruge til onboarding.

| Slutpunkt     | Værktøjsindstillinger                       |
|--------------|------------------------------------------|
| **Windows**  |  [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobilenhedshåndtering](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender til skyen](azure-server-integration.md) |
| **macOS**    | [Lokale scripts](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Administration af mobilenheder](mac-install-with-other-mdm.md) |
| **Linux Server** | [Lokalt script](linux-install-manually.md) <br> [Eller Eller](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 


## <a name="step-2-configure-capabilities"></a>Trin 2: Konfigurer funktioner
Når du har onboardet slutpunkterne, skal du derefter konfigurere egenskaberne. I følgende tabel vises de komponenter, du kan konfigurere. Vælg de komponenter, du vil bruge, og fjern dem, der ikke er gældende.

| Funktion | Beskrivelse |
|-|-|
| [Slutpunktsregistrering & svar (Slutpunktsregistrering og -svar)](overview-endpoint-detection-response.md) | Defender for Endpoint slutpunktsregistrering og -svar funktioner giver avancerede registreringer af angreb, der er næsten i realtid og kan handles på. Sikkerhedsanalytikere kan prioritere beskeder effektivt, få overblik over det fulde omfang af en overtrædelse og reagere på handlinger for at løse trusler. |
| [Administration & af trusselssikkerhedsrisiko (TVM)](next-gen-threat-and-vuln-mgt.md) | Threat & Vulnerability Management er en komponent i Microsoft Defender til slutpunkt og giver både sikkerhedsadministratorer og sikkerhedsteams unik værdi, herunder: - slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar ) Indsigter korreleret med slutpunktssårbarheder – Uvurderlig enhedssikkerhedsrisikokontekst under hændelsesundersøgelse – Indbyggede afhjælpningsprocesser via Microsoft Intune og Microsoft System Center Configuration Manager.  |
| [Næste generations beskyttelse (NGP)](microsoft-defender-antivirus-windows.md) | Microsoft Defender Antivirus er en indbygget antimalwareløsning, der giver næste generations beskyttelse til stationære computere, bærbare computere og servere. Microsoft Defender Antivirus indeholder:<br> <br>Cloud-leveret beskyttelse til øjeblikkelig registrering og blokering af nye og nye trusler. Ud over maskinlæring og intelligent sikkerheds Graph er cloud-leveret beskyttelse en del af den næste generation af teknologier, der Microsoft Defender Antivirus.<br> <br> - Scanning altid ved hjælp af avanceret overvågning af fil- og procesfunktionsmåder og andre heuristiske funktioner (også kaldet "beskyttelse i realtid").<br><br> - Dedicated protection updates based on machine learning, human and automated big-data analysis, and in-depth threat resistance research. |
| [Reduktion af angrebsoverfladen (ASR)](overview-attack-surface-reduction.md) | Funktioner til reduktion af angrebsoverfladen i Microsoft Defender til Slutpunkt hjælper med at beskytte enheder og programmer i organisationen mod nye og fremspirende trusler. |
| [Automatisk afhjælpning & undersøgelse (AIR)](automated-investigations.md) | Microsoft Defender til Slutpunkt bruger automatiserede undersøgelser til at reducere mængden af beskeder, der skal undersøges individuelt. Funktionen Automatiseret undersøgelse udnytter forskellige inspektionsalgoritmer og processer, der bruges af analytikere (f.eks. playbooks), til at undersøge vigtige beskeder og omgående afhjælpe eventuelle overtrædelser. Dette reducerer mængden af beskeder betydeligt, så sikkerhedseksperter kan fokusere på mere avancerede trusler og andre initiativer med høj værdi. |
| [Microsoft-trusselseksperter (MTE)](microsoft-threat-experts.md) | Microsoft-trusselseksperter er en administreret jagttjeneste, der leverer SECURITY Operation Centers (SOCs) med ekspertniveauovervågning og -analyse for at hjælpe dem med at sikre, at kritiske trusler i deres unikke miljøer ikke overser.      |

Når du har onboardet slutpunkterne, skal du konfigurere de forskellige funktioner, f.eks. slutpunktsregistrering og -svar, næste generations beskyttelse og reduktion af angrebsoverfladen.

## <a name="example-deployments"></a>Eksempelinstallationer

I denne installationsvejledning guider vi dig gennem brug af to udrulningsværktøjer til onboard slutpunkter, og hvordan du konfigurerer funktioner.

Værktøjerne i eksempelinstallationerne er:

- [Onboarding ved hjælp Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Onboarding ved hjælp Microsoft Endpoint Manager](onboarding-endpoint-manager.md)

Ved hjælp af de nævnte installationsværktøjer ovenfor bliver du derefter vejledt i konfigurationen af følgende Funktioner for Defender til slutpunkt:

- Konfiguration af slutpunktsregistrering og svar
- Næste generations beskyttelseskonfiguration
- Konfiguration af reduktion af angrebsoverfladen

## <a name="related-topics"></a>Relaterede emner

- [Onboarding ved hjælp Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Onboarding ved hjælp Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
- [Sikre dokumenter i Microsoft 365 E5](../office-365-security/safe-docs.md)
