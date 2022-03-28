---
title: Installer Microsoft Defender til slutpunkt i ringe
description: Få mere at vide om, hvordan du installerer Microsoft Defender til slutpunkt i ringe
keywords: Deploy, rings, evaluate, pilot, insider fast, insider slow, setup, onboard, phase, deployment, deploying, adoption, configuring
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
ms.openlocfilehash: a7a9673591f4d77197390541a58169a58b04fe91
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63597522"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>Installer Microsoft Defender til slutpunkt i ringe

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Installation af Microsoft Defender til Slutpunkt kan udføres ved hjælp af en ringbaseret installations tilgang.

Installationsringene kan anvendes i følgende scenarier:

- [Nye installationer](#new-deployments)
- [Eksisterende installationer](#existing-deployments)

## <a name="new-deployments"></a>Nye installationer

![Billede af installationsringe.](images/deployment-rings.png)

En ringbaseret metode er en metode til at identificere et sæt slutpunkter til onboarding og bekræftelse af, at visse kriterier er opfyldt, før du fortsætter med at installere tjenesten på et større sæt enheder. Du kan definere udgangskriterierne for hver ring og sikre, at de er opfyldt, før du går videre til den næste ring.

At indføre en ringbaseret installation er med til at reducere potentielle problemer, der kan opstå under udrulningen af tjenesten. Ved først at afprøve et bestemt antal enheder kan du identificere potentielle problemer og mindske de potentielle risici.

Tabel 1 er et eksempel på de installationsringe, du kan bruge.

**Tabel 1**:

<br>

****

|Installationsring|Beskrivelse|
|---|---|
|Evaluer|Ring 1: Identificer 50-systemer til pilottest|
|Pilot|Ring 2: Identificer de næste 50-100 slutpunkter i produktionsmiljøet|
|Komplet udrulning|Ring 3: Udrul tjeneste til resten af miljøet i større intervaller|
|

### <a name="exit-criteria"></a>Afslut kriterier

Et eksempel på et sæt udgangskriterier for disse ringe kan omfatte:

- Enheder vises på lagerlisten for enheder
- Beskeder vises i dashboard
- [Kør en registreringstest](run-detection-test.md)
- [Kør et simuleret angreb på en enhed](attack-simulations.md)

### <a name="evaluate"></a>Evaluer

Identificer et lille antal testmaskine i dit miljø for at onboarde tjenesten. Ideelt set vil disse maskiner være færre end 50 slutpunkter.

### <a name="pilot"></a>Pilot

Microsoft Defender til Slutpunkt understøtter en række slutpunkter, som du kan få adgang til tjenesten på. I denne ring skal du identificere flere enheder til onboarding og baseret på de exitkriterier, du definerer, beslutte at fortsætte til den næste installationsring.

Følgende tabel viser de understøttede slutpunkter og det tilsvarende værktøj, du kan bruge til at onboarde enheder til tjenesten.

| Slutpunkt     | Udrulningsværktøj                       |
|--------------|------------------------------------------|
| **Windows**  |  [Lokalt script (op til 10 enheder)](configure-endpoints-script.md) <br> BEMÆRK! Hvis du vil installere mere end 10 enheder i et produktionsmiljø, skal du bruge Gruppepolitik-metoden i stedet eller de andre understøttede værktøjer, der er angivet nedenfor.<br>  [Gruppepolitik](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobilenhedshåndtering](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI-scripts](configure-endpoints-vdi.md) <br> [Integration med Microsoft Defender til skyen](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [Lokalt script](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [SYLTEF Pro](mac-install-with-jamf.md) <br> [Administration af mobilenheder](mac-install-with-other-mdm.md) |
| **Linux Server** | [Lokalt script](linux-install-manually.md) <br> [Eller Eller](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               |

### <a name="full-deployment"></a>Komplet udrulning

På dette tidspunkt kan du bruge [planlægningsinstallationsmaterialet](deployment-strategy.md) til at hjælpe dig med at planlægge din installation.

Brug følgende materiale til at vælge den relevante Microsoft Defender til slutpunktsarkitektur, der passer bedst til din organisation.

|**Element**|**Beskrivelse**|
|:-----|:-----|
|[![Thumb image for Microsoft Defender for Endpoint deployment strategy.](images/mde-deployment-strategy.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)\| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)   | Det arkitektoniske materiale hjælper dig med at planlægge din installation for følgende arkitekturer: <ul><li> Skybaseret </li><li> Medadministration </li><li> Lokalt miljø</li><li>Evaluering og lokal onboarding</li></ul>

## <a name="existing-deployments"></a>Eksisterende installationer

### <a name="windows-endpoints"></a>Windows slutpunkter

For Windows/eller Windows-servere skal du vælge flere maskiner, der skal testes i forvejen (før patchen tirsdag) ved hjælp af programmet til validering af sikkerhedsopdatering **(AFP).**

Du kan finde flere oplysninger under:

- [Hvad er valideringsprogrammet til sikkerhedsopdatering?](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [Program til validering af softwareopdatering og -Microsoft Malware Protection Center- TwC Interactive Timeline Part 4](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>Ikke-Windows slutpunkter

Med macOS og Linux kan du tage et par systemer og køre i Beta-kanalen.

> [!NOTE]
> Ideelt set mindst én sikkerhedsadministrator og én udvikler, så du kan finde kompatibilitets-, ydeevne- og pålidelighedsproblemer, før buildet gør det til den aktuelle kanal.

Valget af kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes din enhed. Enheder i beta er de første, der modtager opdateringer og nye funktioner, efterfulgt af Forhåndsvisning senere og til sidst af Aktuel.

![Billede af Insider-ringe.](images/insider-rings.png)

For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer nogle enheder i din virksomhed til at bruge enten Beta eller Preview.

> [!WARNING]
> Hvis du skifter kanal efter den indledende installation, skal produktet geninstalleres. Sådan skifter du produktkanalen: Fjern den eksisterende pakke, konfigurer enheden igen til at bruge den nye kanal, og følg trinnene i dette dokument for at installere pakken fra den nye placering.
