---
title: Microsoft Defender for Endpoint på Mac
ms.reviewer: ''
description: Få mere at vide om, hvordan du installerer, konfigurerer, opdaterer og bruger Microsoft Defender for Endpoint på Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, installere, uninstallation, intune, jamf, macos, monterey, big sur, catalina, mojave, mde til mac
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d6438c7af3d3dbb8f4b2c19fdfdd04640cc8b4d2
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174977"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Microsoft Defender for Endpoint på Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I dette emne beskrives det, hvordan du installerer, konfigurerer, opdaterer og bruger Defender for Endpoint på Mac.

> [!CAUTION]
> Kørsel af andre tredjepartsbeskyttelsesprodukter til slutpunkter sammen med Microsoft Defender for Endpoint på Mac vil sandsynligvis medføre problemer med ydeevnen og uforudsigelige bivirkninger. Hvis beskyttelse af slutpunkter, der ikke er fra Microsoft, er et absolut krav i dit miljø, kan du stadig trygt drage fordel af Defender for Endpoint på Mac Slutpunktsregistrering og -svar funktionalitet, når du har konfigureret antivirusfunktionen til at køre i [passiv tilstand](mac-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="whats-new-in-the-latest-release"></a>Nyheder i den seneste version

[Nyheder i Microsoft Defender for Endpoint](whats-new-in-microsoft-defender-endpoint.md)

[Nyheder i Microsoft Defender for Endpoint på Mac](mac-whatsnew.md)

> [!TIP]
> Hvis du har feedback, som du gerne vil dele, kan du sende den ved at åbne Microsoft Defender for Endpoint på Mac på din enhed og navigere til **Hjælp Med** \> at **sende feedback**.

Hvis du vil have de nyeste funktioner, herunder prøveversionsfunktioner (f.eks. slutpunktsregistrering og -svar til dine Mac-enheder), skal du konfigurere din macOS-enhed, der kører Microsoft Defender for Endpoint til at være en "Insider"-enhed.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>Sådan installerer du Microsoft Defender for Endpoint på Mac

### <a name="prerequisites"></a>Forudsætninger

- Et Defender for Endpoint-abonnement og adgang til Microsoft 365 Defender-portalen
- Erfaring med macOS- og BASH-scripting på begynderniveau
- Administrative rettigheder på enheden (i tilfælde af manuel installation)

### <a name="installation-instructions"></a>Installationsvejledning

Der er flere metoder og installationsværktøjer, som du kan bruge til at installere og konfigurere Defender for Endpoint på Mac.

- Administrationsværktøjer fra tredjepart:
    - [Microsoft Intune-baseret udrulning](mac-install-with-intune.md).
    - [JAMF-baseret udrulning](mac-install-with-jamf.md)
    - [Andre MDM-produkter](mac-install-with-other-mdm.md)

- Kommandolinjeværktøj:
    - [Manuel udrulning](mac-install-manually.md)

### <a name="system-requirements"></a>Systemkrav

De tre seneste større versioner af macOS understøttes.

> [!IMPORTANT]
> På macOS 11 (Big Sur) og nyere kræver Microsoft Defender for Endpoint yderligere konfigurationsprofiler. Hvis du er en eksisterende kunde, der opgraderer fra tidligere versioner af macOS, skal du sørge for at installere de ekstra konfigurationsprofiler, der er angivet på [Nye konfigurationsprofiler til macOS Catalina og nyere versioner af macOS](mac-sysext-policies.md).

- 12 (Monterey), 11 (Big Sur), 10,15 (Catalina)
- Diskplads: 1 GB

Betaversioner af macOS understøttes ikke.

Understøttelse af macOS-enheder med M1-chipbaserede processorer er blevet officielt supporteret siden version 101.40.84 af agenten.

Når du har aktiveret tjenesten, skal du muligvis konfigurere netværket eller firewallen for at tillade udgående forbindelser mellem den og dine slutpunkter.

### <a name="licensing-requirements"></a>Licenskrav

Microsoft Defender for Endpoint på Mac kræver et af følgende Microsoft Volume Licensing-tilbud:

- Microsoft 365 E5 (M365 E5)
- Microsoft 365 E5 Sikkerhed
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Microsoft Defender for Endpoint

> [!NOTE]
> Berettigede brugere med licens kan bruge Microsoft Defender for Endpoint på op til fem samtidige enheder.
> Microsoft Defender for Endpoint kan også købes fra en Cloud Solution Provider (CSP). Når den er købt via en CSP, kræver den ikke de angivne Microsoft Volume Licensing-tilbud.

### <a name="configuring-exclusions"></a>Konfiguration af udeladelser

Når du tilføjer udeladelser, skal du være opmærksom på [almindelige udeladelsesfejl for Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>Netværksforbindelser

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Du skal sikre, at der ikke er nogen regler for firewall- eller netværksfiltrering, der vil nægte adgang til disse URL-adresser, eller du skal muligvis oprette en *regel for tilladelse* specifikt for dem.


|Regneark med domæneliste| Beskrivelse|
|---|---|
|Microsoft Defender for Endpoint URL-adresseliste til kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OPERATIVSYSTEM til kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender for Endpoint URL-adresseliste for Gov/GCC/DoD | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Microsoft Defender for Endpoint kan finde en proxyserver ved hjælp af følgende registreringsmetoder:

- Automatisk konfiguration af proxy (PAC)
- Web Proxy Autodiscovery Protocol (WPAD)
- Manuel konfiguration af statisk proxy

Hvis en proxy eller firewall blokerer anonym trafik, skal du sørge for, at anonym trafik er tilladt i de tidligere angivne URL-adresser.

> [!WARNING]
> Godkendte proxyer understøttes ikke. Sørg for, at der kun bruges PAC, WPAD eller en statisk proxy.
>
> SSL-inspektion og opfangelse af proxyer understøttes heller ikke af sikkerhedsmæssige årsager. Konfigurer en undtagelse for SSL-inspektion og din proxyserver til at overføre data direkte fra Microsoft Defender for Endpoint på macOS til de relevante URL-adresser uden opfangelse. Tilføjelse af dit aflytningscertifikat til det globale lager tillader ikke opfangelse.

Hvis du vil teste, at en forbindelse ikke er blokeret, skal du åbne <https://x.cp.wd.microsoft.com/api/report> og <https://cdn.x.cp.wd.microsoft.com/ping> i en browser.

Hvis du foretrækker kommandolinjen, kan du også kontrollere forbindelsen ved at køre følgende kommando i Terminal:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Outputtet fra denne kommando skal ligne følgende:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> Vi anbefaler, at du holder [System Integrity Protection](https://support.apple.com/HT204899) (SIP) aktiveret på klientenheder. SIP er en indbygget macOS-sikkerhedsfunktion, der forhindrer manipulation på lavt niveau med operativsystemet, og som er aktiveret som standard.

Når Microsoft Defender for Endpoint er installeret, kan forbindelsen valideres ved at køre følgende kommando i Terminal:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>Sådan opdaterer du Microsoft Defender for Endpoint på Mac

Microsoft udgiver jævnligt softwareopdateringer for at forbedre ydeevnen, sikkerheden og levere nye funktioner. Hvis du vil opdatere Microsoft Defender for Endpoint på Mac, bruges et program med navnet Microsoft Automatiske opdateringer (MAU). Du kan få mere at vide under [Udrul opdateringer til Microsoft Defender for Endpoint på Mac](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>Sådan konfigurerer du Microsoft Defender for Endpoint på Mac

Vejledning til, hvordan du konfigurerer produktet i virksomhedsmiljøer, er tilgængelig under [Angiv indstillinger for Microsoft Defender for Endpoint på Mac](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>macOS-kerne- og systemudvidelser

Fra og med macOS 11 (Big Sur) er Microsoft Defender for Endpoint fuldt ud migreret fra kerneudvidelse til systemudvidelser. Kerneudvidelsen bruges stadig på macOS 10.15 (Catalina).

## <a name="resources"></a>Ressourcer

- Du kan få flere oplysninger om logføring, fjernelse eller andre emner under [Ressourcer til Microsoft Defender for Endpoint på Mac](mac-resources.md).
- [Beskyttelse af personlige oplysninger for Microsoft Defender for Endpoint på Mac](mac-privacy.md).
