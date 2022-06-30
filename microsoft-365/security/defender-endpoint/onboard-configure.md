---
title: Onboard enheder, og konfigurer Microsoft Defender for Endpoint-funktioner
description: Onboarde Windows 10 enheder, servere, ikke-Windows-enheder, og få mere at vide om, hvordan du kører en registreringstest.
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
ms.openlocfilehash: 309baa41f217cbac9a865317084f284b3d22961b
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554219"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>Onboard enheder, og konfigurer Microsoft Defender for Endpoint-funktioner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Udrulning af Microsoft Defender for Endpoint er en proces med to trin.

- Onboarder enheder til tjenesten
- Konfigurer funktioner for tjenesten

:::image type="content" source="images/deployment-steps.png" alt-text="Onboarding- og konfigurationsprocessen" lightbox="images/deployment-steps.png":::

## <a name="onboard-devices-to-the-service"></a>Onboarder enheder til tjenesten
Du skal gå til onboardingsektionen på Defender for Endpoint-portalen for at onboarde en hvilken som helst af de understøttede enheder. Afhængigt af enheden får du vejledning med de relevante trin og de indstillinger for administrations- og udrulningsværktøj, der passer til enheden. 

Sådan onboarder du enheder til tjenesten:

- Bekræft, at enheden opfylder [minimumskravene](minimum-requirements.md)
- Afhængigt af enheden skal du følge de konfigurationstrin, der er angivet i onboardingafsnittet på Defender for Endpoint-portalen
- Brug det relevante administrationsværktøj og den relevante installationsmetode til dine enheder
- Kør en registreringstest for at bekræfte, at enhederne er onboardet korrekt, og at de rapporterer til tjenesten

Denne artikel indeholder oplysninger om onboardingmetoder, der gælder for windows-klient- og serverversioner.

## <a name="onboarding-and-configuration-tool-options"></a>Indstillinger for onboarding- og konfigurationsværktøj
I følgende tabel vises de tilgængelige værktøjer, der er baseret på det slutpunkt, du skal onboarde.

| Slutpunkt     | Værktøjsindstillinger                       |
|--------------|------------------------------------------|
| **Windows-klient**  |     [Mobil Enhedshåndtering/Microsoft Intune](configure-endpoints-mdm.md) <br> [Gruppepolitik](configure-endpoints-gp.md) <br> [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br>[VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **Windows Server**  | [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **Macos**    | [Lokale scripts](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil Enhedshåndtering](mac-install-with-other-mdm.md) |
| **Linux Server** | [Lokalt script](linux-install-manually.md) <br> [Marionet](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md) <br> [Integration med Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)     |
| **Ios**      | [Microsoft Endpoint Manager](ios-install.md)           |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)            | 


> [!NOTE]
> For enheder, der ikke administreres af en Microsoft Endpoint Manager (enten Microsoft Intune eller Microsoft Endpoint Configuration Manager), kan du bruge Sikkerhedsadministration til Microsoft Defender for Endpoint  for at modtage sikkerhedskonfigurationer til Microsoft Defender direkte fra Endpoint Manager.

I følgende tabel vises de tilgængelige værktøjer, der er baseret på det slutpunkt, du skal onboarde.

## <a name="configure-capabilities-of-the-service"></a>Konfigurer funktioner for tjenesten
Onboardingenheder muliggør effektivt registrering af slutpunkter og svarfunktionalitet for Microsoft Defender for Endpoint.

Når du har onboardet enhederne, skal du derefter konfigurere tjenestens andre funktioner. I følgende tabel vises de funktioner, du kan konfigurere for at få den bedste beskyttelse af dit miljø.

| Kapacitet | Beskrivelse |
|-|-|
| [Konfigurer trussel & administration af sårbarheder (TVM)](tvm-prerequisites.md) | Administration af trussel & sårbarheder er en komponent i Microsoft Defender for Endpoint og giver både sikkerhedsadministratorer og sikkerhedshandlinger en entydig værdi, herunder: <br><br> – EDR-indsigt (endpoint detection and response) i realtid, der er korreleret med sårbarheder i forbindelse med slutpunkter. <br><br> – Kontekst for uvurderlig sårbarhed over for enheder under efterforskning af hændelser. <br><br> - Indbyggede afhjælpningsprocesser via Microsoft Intune og Microsoft System Center Configuration Manager.  |
| [Konfigurer næste generation af beskyttelse (NGP)](configure-microsoft-defender-antivirus-features.md) | Microsoft Defender Antivirus er en indbygget antimalwareløsning, der yder næste generations beskyttelse af stationære computere, bærbare computere og servere. Microsoft Defender Antivirus indeholder:<br> <br>–Skybaseret beskyttelse til næsten øjeblikkelig registrering og blokering af nye og nye trusler. Sammen med maskinel indlæring og Intelligent Security Graph er cloudbaseret beskyttelse en del af de næste teknologier, der styrer Microsoft Defender Antivirus.<br> <br> - Altid ved scanning ved hjælp af avanceret overvågning af fil- og procesadfærd og andre heuristik (også kendt som "beskyttelse i realtid").<br><br> – Dedikerede beskyttelsesopdateringer baseret på maskinel indlæring, analyse af menneskelige og automatiserede big data og dybdegående forskning i trusselsresistens. |
| [Konfigurer reduktion af angrebsoverflade (ASR)](overview-attack-surface-reduction.md) | Reduktion af angrebsoverfladen i Microsoft Defender for Endpoint hjælpe med at beskytte enheder og programmer i organisationen mod nye og nye trusler. |
| [Konfigurer air-funktioner (Auto Investigation & Remediation)](configure-automated-investigations-remediation.md) | Microsoft Defender for Endpoint bruger automatiserede undersøgelser til at reducere mængden af beskeder, der skal undersøges individuelt. Funktionen Automatiseret undersøgelse udnytter forskellige inspektionsalgoritmer og processer, der bruges af analytikere (f.eks. playbooks), til at undersøge beskeder og foretage øjeblikkelig afhjælpning for at løse brud. Dette reducerer alarmmængden betydeligt, hvilket giver eksperter i sikkerhedsoperationer mulighed for at fokusere på mere avancerede trusler og andre initiativer med høj værdi. |
| [Konfigurer funktioner for Microsoft-trusselseksperter (MTE)](configure-microsoft-threat-experts.md) | Microsoft-trusselseksperter er en administreret jagttjeneste, der leverer sikkerhedsoperationscentre med overvågning og analyse på ekspertniveau for at hjælpe dem med at sikre, at kritiske trusler i deres unikke miljøer ikke overses.      |


## <a name="supported-capabilities-for-windows-devices"></a>Understøttede funktioner til Windows-enheder

|Operativsystem  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |Windows Server 2016<sup>[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**Forebyggelse**    |         |         |         |         |         |
|Regler for reduktion af angrebsoverflade     |    Y     |   Y      |    Y     |    Y     |    Y     |
|Enhedsstyring     |     Y    |    N     |    N     |    N     |    N     |  
|Firewall     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Netværksbeskyttelse     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Næste generations beskyttelse     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Ændringsbeskyttelse     |        Y   |    Y     |     Y    |    Y    |    Y   |
|Webbeskyttelse     |       Y   |    Y     |     Y    |    Y    |    Y   |
|||||||
|**Påvisning**     |         |         |         |||
|Avanceret jagt     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Brugerdefinerede filindikatorer     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Brugerdefinerede netværksindikatorer     |      Y   |    Y     |     Y    |    Y    |    Y   |
|EDR-blok & passiv tilstand     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Sanseregistreringssensor     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Slutpunkt & netværksenhedsregistrering     |      Y   |    N     |     N    |    N    |    N   |
|||||||
|**Svar**     |         |         |         |||
|Automatiseret undersøgelse & svar (AIR)    |      Y   |    Y     |     Y    |    Y    |    Y   |
|Enhedssvarfunktioner: isolation, indsaml undersøgelsespakke, kør AV-scanning     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Funktioner til filsvar: Indsaml fil-, detaljeret analyse-, bloker fil-, stop- og karantæneprocesser     |      Y   |    Y     |     Y    |    Y    |    Y   |
|Live-svar    |      Y   |    Y     |     Y    |    Y    |    Y   |

(<a id="fn1">1</a>) Refererer til den moderne, samlede løsning til Windows Server 2012 R2 og 2016. Du kan finde flere oplysninger under [Onboarder Windows-servere til Defender for Endpoint-tjenesten](configure-server-endpoints.md).

>[!NOTE]
>Windows 7, 8.1, Windows Server 2008 R2 omfatter understøttelse af EDR-sensoren og AV ved hjælp af System Center Endpoint Protection (SCEP).
