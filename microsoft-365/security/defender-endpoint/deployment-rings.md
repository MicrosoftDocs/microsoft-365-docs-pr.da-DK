---
title: Installer Microsoft Defender for Endpoint i ringe
description: Få mere at vide om, hvordan du installerer Microsoft Defender for Endpoint i ringe
keywords: udrul, ringe, evaluere, pilot, insider hurtigt, insider langsom, konfiguration, onboard, fase, udrulning, implementering, implementering, konfiguration
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e308b1c1d8c26a4ec3d6b3044501ffe1ce92e1c7
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862868"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>Installer Microsoft Defender for Endpoint i ringe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Udrulning af Microsoft Defender for Endpoint kan udføres ved hjælp af en ringbaseret udrulningsstrategi.

Installationsringene kan anvendes i følgende scenarier:

- [Nye udrulninger](#new-deployments)
- [Eksisterende installationer](#existing-deployments)

## <a name="new-deployments"></a>Nye udrulninger

:::image type="content" source="images/deployment-rings.png" alt-text="Udrulningen ringer." lightbox="images/deployment-rings.png":::

En ringbaseret tilgang er en metode til at identificere et sæt slutpunkter, der skal onboardes, og til at bekræfte, at visse kriterier er opfyldt, før du fortsætter med at udrulle tjenesten til et større sæt enheder. Du kan definere udgangskriterierne for hver ring og sikre, at de er opfyldt, før du går videre til næste ring.

Brug af en ringbaseret udrulning hjælper med at reducere potentielle problemer, der kan opstå, når tjenesten udrulles. Ved først at afprøve et bestemt antal enheder kan du identificere potentielle problemer og afhjælpe potentielle risici, der kan opstå.

Tabel 1 indeholder et eksempel på de udrulningsringe, du kan bruge.

**Tabel 1**:

|Installationsring|Beskrivelse|
|---|---|
|Evaluere|Ring 1: Identificer 50 systemer til pilottest|
|Pilot|Ring 2: Identificer de næste 50-100 slutpunkter i produktionsmiljøet|
|Fuld udrulning|Ring 3: Udrul tjenesten til resten af miljøet i større trin|

### <a name="exit-criteria"></a>Afslut kriterier

Et eksempel på et sæt afslutningskriterier for disse ringe kan omfatte:

- Enheder vises på enhedslagerlisten
- Beskeder vises på dashboardet
- [Kør en registreringstest](run-detection-test.md)
- [Kør et simuleret angreb på en enhed](attack-simulations.md)

### <a name="evaluate"></a>Evaluere

Identificer et lille antal testmaskiner i dit miljø, som du kan onboarde til tjenesten. Ideelt set ville disse maskiner være mindre end 50 slutpunkter.

### <a name="pilot"></a>Pilot

Microsoft Defender for Endpoint understøtter en række slutpunkter, som du kan onboarde til tjenesten. I denne ring skal du identificere flere enheder, der skal onboarde, og på baggrund af de afslutningskriterier, du definerer, beslutte at fortsætte til den næste udrulningsring.

I følgende tabel vises de understøttede slutpunkter og det tilsvarende værktøj, du kan bruge til at onboarde enheder til tjenesten.

|Slutpunkt|Installationsværktøj|
|---|---|
|**Windows**|[Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br> BEMÆRK! Hvis du vil installere mere end 10 enheder i et produktionsmiljø, skal du i stedet bruge metoden نهج المجموعة eller de andre understøttede værktøjer, der er angivet nedenfor.<br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [Enhedshåndtering Microsoft Endpoint Manager/Mobil](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)|
|**Macos**|[Lokalt script](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobil 裝置管理](mac-install-with-other-mdm.md)|
|**Linux Server**|[Lokalt script](linux-install-manually.md) <br> [Marionet](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**Ios**|[Microsoft Endpoint Manager](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

### <a name="full-deployment"></a>Fuld udrulning

I denne fase kan du bruge [installationsmaterialet Plan](deployment-strategy.md) til at hjælpe dig med at planlægge udrulningen.

Brug følgende materiale til at vælge den relevante Microsoft Defender for Endpoint arkitektur, der passer bedst til din organisation.

|Element|Beskrivelse|
|---|---|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Strategien for Microsoft Defender for Endpoint udrulning." lightbox="images/mde-deployment-strategy.png":::](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) \| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)|Det arkitektoniske materiale hjælper dig med at planlægge din udrulning for følgende arkitekturer: <ul><li> Oprindelig sky </li><li> Fælles administration </li><li> Det lokale</li><li>Evaluering og lokal onboarding</li></ul>|

## <a name="existing-deployments"></a>Eksisterende installationer

### <a name="windows-endpoints"></a>Windows slutpunkter

I forbindelse med Windows og/eller Windows-servere skal du vælge flere computere, der skal testes på forhånd (før programrettelse tirsdag) ved hjælp af **suvp-programmet (Security Update Validation).**

Du kan finde flere oplysninger under:

- [Hvad er valideringsprogrammet for sikkerhedsopdatering](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [Software Update Validation Program and Microsoft Malware Protection Center Establishment – TwC Interactive Timeline Part 4](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>Slutpunkter, der ikke er Windows

Med macOS og Linux kan du tage et par systemer og køre i betakanalen.

> [!NOTE]
> Ideelt set skal der være mindst én sikkerhedsadministrator og én udvikler, så du kan finde kompatibilitets-, ydeevne- og pålidelighedsproblemer, før buildet overføres til den aktuelle kanal.

Valget af kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes til din enhed. Enheder i beta er de første, der modtager opdateringer og nye funktioner, efterfulgt senere af Prøveversion og sidst af Current.

:::image type="content" source="images/insider-rings.png" alt-text="Insiderringene." lightbox="images/insider-rings.png":::

For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer nogle enheder i din virksomhed til at bruge enten Beta eller Preview.

> [!WARNING]
> Hvis du skifter kanal efter den første installation, skal produktet geninstalleres. Hvis du vil skifte produktkanal: Fjern den eksisterende pakke, genkonfigurer enheden, så den bruger den nye kanal, og følg trinnene i dette dokument for at installere pakken fra den nye placering.
