---
title: Microsoft Defender for Endpoint på Mac
ms.reviewer: ''
description: Få mere at vide om, hvordan du installerer, konfigurerer, opdaterer og Microsoft Defender for Endpoint på Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune,propf, macos, monterey, big sur, catalina, mojave, mde til mac
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
ms.openlocfilehash: 2e982a32826906feb65b05837506ff2f513eb27e
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507295"
---
# <a name="microsoft-defender-for-endpoint-on-mac"></a>Microsoft Defender for Endpoint på Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I dette emne beskrives det, hvordan du installerer, konfigurerer, opdaterer og bruger Defender til slutpunkt på Mac.

> [!CAUTION]
> Kørsel af andre tredjepartsslutpunktbeskyttelsesprodukter sammen med Microsoft Defender for Endpoint på Mac vil sandsynligvis føre til problemer med ydeevnen og uforudsete bivirkninger. Hvis ikke-Microsoft-slutpunktsbeskyttelse er et absolut krav i dit miljø, kan du stadig roligt drage fordel af Defender til Slutpunkt på Mac Slutpunktsregistrering og -svar-funktionalitet, når du har konfigureret antivirusfunktionaliteten til at køre i [passiv tilstand](mac-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="whats-new-in-the-latest-release"></a>Nyheder i den nyeste version

[Nyheder i Microsoft Defender for Endpoint](whats-new-in-microsoft-defender-endpoint.md)

[Nyheder i Microsoft Defender for Endpoint på Mac](mac-whatsnew.md)

> [!TIP]
> Hvis du har feedback, som du gerne vil dele, kan du sende den ved at åbne Microsoft Defender for Endpoint på Mac på din enhed og navigere for at **hjælpe med** \> **at sende feedback**.

Hvis du vil have de nyeste funktioner, herunder visningsfunktioner (f.eks. slutpunktsregistrering og -svar til dine Mac-enheder), skal du konfigurere din macOS-enhed, der Microsoft Defender for Endpoint til at være en "Insider"-enhed.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-mac"></a>Sådan installerer du Microsoft Defender for Endpoint på Mac

### <a name="prerequisites"></a>Forudsætninger

- Et Defender for Endpoint-abonnement og adgang til Microsoft 365 Defender-portalen
- Begynderoplevelse i macOS- og BASH-scripting
- Administrative rettigheder på enheden (i tilfælde af manuel udrulning)

### <a name="installation-instructions"></a>Installationsvejledning

Der er flere metoder og installationsværktøjer, du kan bruge til at installere og konfigurere Defender til Slutpunkt på Mac.

- Administrationsværktøjer fra tredjepart:
    - [Microsoft Intune-baseret installation](mac-install-with-intune.md)
    - [SYLF-baseret installation](mac-install-with-jamf.md)
    - [Andre MDM-produkter](mac-install-with-other-mdm.md)

- Kommandolinjeværktøj:
    - [Manuel udrulning](mac-install-manually.md)

### <a name="system-requirements"></a>Systemkrav

De tre seneste større versioner af macOS understøttes.

> [!IMPORTANT]
> På macOS 11 (Big Sur) og derover kræver Microsoft Defender for Endpoint flere konfigurationsprofiler. Hvis du er eksisterende kunde, som opgraderer fra tidligere versioner af macOS, skal du sørge for at installere de ekstra konfigurationsprofiler, der er angivet på Nye konfigurationsprofiler [til macOS Catalina og nyere versioner af macOS](mac-sysext-policies.md).

- 12 (Monterey), 11 (Big Sur), 10.15 (Catalina)
- Diskplads: 1 GB

Betaversioner af macOS understøttes ikke.

Understøttelse af macOS-enheder med M1-chipbaserede processorer er officielt understøttet siden version 101.40.84 af agenten.

Når du har aktiveret tjenesten, skal du muligvis konfigurere dit netværk eller din firewall til at tillade udgående forbindelser mellem den og dine slutpunkter.

### <a name="licensing-requirements"></a>Licenskrav

Microsoft Defender for Endpoint på Mac kræver et af følgende Microsoft Volumenlicens-tilbud:

- Microsoft 365 E5 (M365 E5)
- Microsoft 365 E5 Sikkerhed
- Microsoft 365 A5 (M365 A5)
- Windows 10 Enterprise E5
- Microsoft 365 Business Premium
- Windows 11 Enterprise E5
- Microsoft Defender for Endpoint

> [!NOTE]
> Berettigede brugere med licens kan bruge Microsoft Defender for Endpoint på op til fem samtidige enheder.
> Microsoft Defender for Endpoint kan også købes hos en Cloud Solution Provider (CSP). Når de er købt via en CSP, kræver det ikke, at Microsoft Volumenlicens-tilbud er angivet.

### <a name="configuring-exclusions"></a>Konfiguration af udeladelse

Når du tilføjer udeladelse, skal du være opmærksom [på almindelige udeladelsesfejl for Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).

### <a name="network-connections"></a>Netværksforbindelser

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Du skal sikre dig, at der ikke er nogen firewall- eller netværksfiltreringsregler, der vil nægte adgang til disse URL-adresser, eller du  skal muligvis oprette en tilladelsesregel specifikt for dem.


|Listen Regneark over domæner| Beskrivelse|
|---|---|
|Microsoft Defender for Endpoint URL-adresse for kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og operativsystem for kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender for Endpoint URL-adresseliste for Gov/GCC/DoD | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Microsoft Defender for Endpoint kan finde en proxyserver ved hjælp af følgende registreringsmetoder:

- Proxy for automatisk konfiguration (PAC)
- WPAD (Web Proxy Autodiscovery Protocol)
- Manuel statisk proxykonfiguration

Hvis en proxy eller firewall blokerer anonym trafik, skal du sørge for, at anonym trafik er tilladt i de tidligere angivne URL-adresser.

> [!WARNING]
> Godkendte proxyer understøttes ikke. Sørg for, at der kun bruges PAC, WPAD eller en statisk proxy.
>
> SSL-inspektion og skærings-proxyer understøttes heller ikke af sikkerhedsmæssige årsager. Konfigurer en undtagelse for SSL-inspektion og din proxyserver til at gå direkte gennem data fra Microsoft Defender for Endpoint på macOS til de relevante URL-adresser uden skæring. Tilføjelse af dit skæringscertifikat til det globale lager tillader ikke skæring.

Hvis du vil teste, om en forbindelse ikke er blokeret, skal du <https://x.cp.wd.microsoft.com/api/report> åbne <https://cdn.x.cp.wd.microsoft.com/ping> den og åbne den i en browser.

Hvis du foretrækker kommandolinjen, kan du også kontrollere forbindelsen ved at køre følgende kommando i Terminal:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

Outputtet fra denne kommando skal ligne følgende:

 `OK https://x.cp.wd.microsoft.com/api/report`

 `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> Vi anbefaler, at du holder [System Integrity Protection](https://support.apple.com/HT204899) (SIP) aktiveret på klientenheder. SIP er en indbygget macOS-sikkerhedsfunktion, der forhindrer tæmmelse af operativsystemet på lavniveau og er aktiveret som standard.

Når Microsoft Defender for Endpoint er installeret, kan forbindelsen valideres ved at køre følgende kommando i Terminal:

```bash
mdatp connectivity test
```

## <a name="how-to-update-microsoft-defender-for-endpoint-on-mac"></a>Sådan opdaterer du Microsoft Defender for Endpoint på Mac

Microsoft udgiver jævnligt softwareopdateringer for at forbedre ydeevnen, sikkerheden og levere nye funktioner. For at Microsoft Defender for Endpoint opdateringer på Mac bruges et program med navnet Microsoft Automatiske opdateringer (MAU). Du kan få mere at vide [under Installér opdateringer til Microsoft Defender for Endpoint på Mac](mac-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-mac"></a>Sådan konfigureres Microsoft Defender for Endpoint på Mac

Vejledning til, hvordan du konfigurerer produktet i virksomhedsmiljøer, findes [i Angiv indstillinger for Microsoft Defender for Endpoint på Mac](mac-preferences.md).

## <a name="macos-kernel-and-system-extensions"></a>macOS-kerne og systemudvidelser

I overensstemmelse med macOS's udvikling forbereder vi en Microsoft Defender for Endpoint opdatering på Mac, der udnytter systemudvidelser i stedet for kerneudvidelser. Du kan finde relevante [oplysninger under Nyheder i Microsoft Defender for Endpoint på Mac](mac-whatsnew.md).

## <a name="resources"></a>Ressourcer

- Du kan finde flere oplysninger om logføring, fjernelse eller andre emner under [Ressourcer til Microsoft Defender for Endpoint på Mac](mac-resources.md).
- [Beskyttelse af personlige Microsoft Defender for Endpoint på Mac](mac-privacy.md).
