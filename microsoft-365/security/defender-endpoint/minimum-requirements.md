---
title: Minimumskrav til Microsoft Defender for Endpoint
description: Forstå licenskravene og kravene til onboarding af enheder til tjenesten
keywords: minimumkrav, licenser, sammenligningstabel
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
ms.openlocfilehash: b2b1303fc9ab0841643536ccf5a85470243fe74e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490569"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>Minimumskrav til Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

Der er nogle minimumskrav til onboarding af enheder til tjenesten. Få mere at vide om licens-, hardware- og softwarekrav og andre konfigurationsindstillinger til onboarding af enheder til tjenesten.

> [!TIP]
>
> - I denne artikel beskrives minimumskravene til Microsoft Defender for Endpoint Plan 2. Hvis du leder efter oplysninger om Defender for Endpoint Plan 1, skal du se [Krav til Defender for Endpoint Plan 1](mde-p1-setup-configuration.md#review-the-requirements).
> - Få mere at vide om de seneste forbedringer i Defender for Endpoint: [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Defender for Endpoint viste brancheførende optik- og registreringsfunktioner i den seneste MITRE-evaluering. Læs: [Indsigt fra MITRE ATT&CK-baseret evaluering](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Licenskrav

Du kan få flere oplysninger om licenskrav til Microsoft Defender for Endpoint [under Microsoft Defender for Endpoint licensoplysninger](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).

Du kan finde detaljerede licensoplysninger på [webstedet Produktvilkår](https://www.microsoft.com/licensing/terms/) og arbejde sammen med dit kontoteam for at få mere at vide om vilkår og betingelser.

Du kan få flere oplysninger om en række funktioner i Windows-udgaver under [Sammenlign Windows-udgaver](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>Krav til browser

Adgang til Defender for Endpoint udføres via en browser, der understøtter følgende browsere:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> Mens andre browsere kan fungere, er de nævnte browsere dem, der understøttes.

## <a name="hardware-and-software-requirements"></a>Hardware- og softwarekrav

### <a name="supported-windows-versions"></a>Understøttede Windows-versioner

- Windows 11 Enterprise
- Windows 11 Education
- Windows 11 Pro
- Windows 11 Pro Education
- Windows 10 Enterprise
- [Windows 10 Enterprise LTSC 2016 (eller nyere)](/windows/whats-new/ltsc/)
- Windows 10 Enterprise IoT

    >[!NOTE]
    >Selvom Windows 10 IoT Enterprise er et understøttet operativsystem i Microsoft Defender for Endpoint og gør det muligt for OEM'er/ODM'er at distribuere det som en del af deres produkt eller løsning, bør kunderne følge OEM/ODM's vejledning om værtsbaseret installeret software og supportabilitet.

- Windows 10 Education
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 8.1 Enterprise
- Windows 8.1 Pro
- Windows 7 SP1 Enterprise ([kræver ESU for at få support](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 7 SP1 Pro ([kræver ESU for at få support](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows Server
  - Windows Server 2008 R2 SP1 ([kræver ESU for at få support](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - Windows Server 2016
  - Windows Server, version 1803 eller nyere
  - Windows Server 2019
  - Windows Server 2022
- Windows Virtual Desktop
- Windows 365

Enheder på netværket skal køre en af disse versioner.

Hardwarekravene til Defender for Endpoint på enheder er de samme for de understøttede udgaver.

> Kerner: 2 minimum, 4 foretrukken hukommelse: minimum 1 GB, 4 foretrukket

Du kan få flere oplysninger om understøttede versioner af Windows 10 under (/windows/release-health/release-information).

> [!NOTE]
> - Slutpunkter, der kører mobilversioner af Windows (f.eks. Windows CE og Windows 10 Mobile), understøttes ikke.
>
> - Virtual Machines, der kører Windows 10 Enterprise 2016 LTSB, kan der opstå problemer med ydeevnen, hvis der køres på ikke-Microsoft-virtualiseringsplatforme.
>
> - Vi anbefaler, at du bruger Windows 10 Enterprise LTSC 2019 eller nyere til virtuelle miljøer.
>
> - De separate versioner af [Defender for Endpoint Plan 1 og Plan 2](defender-endpoint-plan-1-2.md) indeholder ikke serverlicenser. Hvis du vil føje servere til disse planer, skal du bruge Defender for Servers Plan 1 eller Plan 2 som en del af [Defender for Cloud-tilbuddet](/azure/defender-for-cloud/defender-for-cloud-introduction) . For at få mere at vide. se [Oversigt over Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction).

Når komponenter er opdaterede på Microsoft Windows-operativsystemer, følger Microsoft Defender for Endpoint support det respektive operativsystems livscyklus. Du kan få flere oplysninger under [Ofte stillede spørgsmål om livscyklus](/lifecycle/faq/general-lifecycle). Nye funktioner eller funktioner leveres typisk kun på operativsystemer, der endnu ikke har nået slutningen af deres livscyklus. Sikkerhedsintelligensopdateringer (definitions- og programopdateringer) og registreringslogik vil fortsat blive leveret indtil mindst:

- [Slutdatoen for support](/lifecycle/products/) (for operativsystemer, der ikke har et ESU-program (Extended Security Opdateringer).
- [Slutningen af ESU-datoen](/lifecycle/faq/extended-security-updates) (for operativsystemer, der har et ESU-program).

### <a name="other-supported-operating-systems"></a>Andre understøttede operativsystemer

- [Android](microsoft-defender-endpoint-android.md)
- [Ios](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [Macos](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Du skal bekræfte, at Linux-distributioner og -versioner af Android, iOS og macOS er kompatible med Defender for Endpoint, for at integrationen kan fungere.

### <a name="network-and-data-storage-and-configuration-requirements"></a>Krav til netværks- og datalagring og konfiguration

Første gang du kører onboardingguiden, skal du vælge, hvor dine Microsoft Defender for Endpoint-relaterede oplysninger skal gemmes: i EU, Storbritannien eller USA datacenter.

> [!NOTE]
>
> - Du kan ikke ændre placeringen af datalageret efter første gang.
> - Gennemse [Microsoft Defender for Endpoint datalager og beskyttelse af personlige oplysninger](data-storage-privacy.md) for at få flere oplysninger om, hvor og hvordan Microsoft gemmer dine data.

### <a name="diagnostic-data-settings"></a>Indstillinger for diagnosticeringsdata

> [!NOTE]
> Microsoft Defender for Endpoint kræver ikke noget bestemt diagnosticeringsniveau, så længe det er aktiveret.

Sørg for, at diagnosticeringsdatatjenesten er aktiveret på alle enheder i din organisation.
Denne tjeneste er som standard aktiveret. Det er god praksis at kontrollere for at sikre, at du får sensordata fra dem.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>Brug kommandolinjen til at kontrollere starttypen for diagnostiske Windows-datatjenester

1. Åbn en kommandolinjeprompt med administratorrettigheder på enheden:
   1. Gå til **Start,** og skriv **cmd**.
   2. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```console
   sc qc diagtrack
   ```

   Hvis tjenesten er aktiveret, skal resultatet se ud som på følgende skærmbillede:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="Resultat af kommandoen sc-forespørgsel for diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

Du skal indstille tjenesten til automatisk at starte, hvis **START_TYPE** ikke er angivet til **AUTO_START**.

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>Brug kommandolinjen til at indstille diagnostiske Windows-datatjeneste til automatisk at starte

1. Åbn en kommandolinjeprompt med administratorrettigheder på slutpunktet:
    1. Gå til **Start,** og skriv **cmd**.
    2. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

    ```console
    sc config diagtrack start=auto
    ```

3. Der vises en meddelelse om, at det lykkedes. Kontrollér ændringen ved at angive følgende kommando, og tryk på **Enter**:

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>Internetforbindelse

Der kræves internetforbindelse på enheder enten direkte eller via proxy.

Defender for Endpoint-sensoren kan bruge en daglig gennemsnitlig båndbredde på 5 MB til at kommunikere med Defender for Endpoint-cloudtjenesten og rapportere cyberdata. Engangsaktiviteter, f.eks. filoverførsler og indsamling af undersøgelsespakker, er ikke inkluderet i denne daglige gennemsnitlige båndbredde.

Du kan finde flere oplysninger om yderligere proxykonfigurationsindstillinger under [Konfigurer indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md).

Før du onboarder enheder, skal diagnosticeringsdatatjenesten være aktiveret. Tjenesten er som standard aktiveret i Windows 10 og Windows 11.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Konfigurationskrav til Microsoft Defender Antivirus

Defender for Endpoint-agenten afhænger af Microsoft Defender Antiviruss mulighed for at scanne filer og angive oplysninger om dem.

Konfigurer opdateringer til sikkerhedsintelligens på Defender for Endpoint-enheder, uanset om Microsoft Defender Antivirus er det aktive antimalwareprogram eller ej. Du kan finde flere oplysninger under [Administrer opdateringer til Microsoft Defender Antivirus og anvend grundlinjer](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

Når Microsoft Defender Antivirus ikke er det aktive antimalwareprogram i din organisation, og du bruger tjenesten Defender for Endpoint, går Microsoft Defender Antivirus i passiv tilstand.

Hvis din organisation har deaktiveret Microsoft Defender Antivirus via gruppepolitik eller andre metoder, skal enheder, der er onboardet, udelukkes fra denne gruppepolitik.

Hvis du onboarder servere, og Microsoft Defender Antivirus ikke er det aktive antimalwareprogram på dine servere, skal Microsoft Defender Antivirus enten konfigureres til at gå i passiv tilstand eller fjernes. Konfigurationen afhænger af serverversionen. Du kan få flere oplysninger under [Microsoft Defender Antivirus-kompatibilitet](microsoft-defender-antivirus-compatibility.md).

> [!NOTE]
> Din almindelige gruppepolitik gælder ikke for Tamper Protection, og ændringer af Microsoft Defender Antivirus-indstillingerne ignoreres, når Tamper Protection er slået til.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Microsoft Defender Antivirus ELAM-driver (Early Launch Antimalware) er aktiveret

Hvis du kører Microsoft Defender Antivirus som det primære antimalwareprodukt på dine enheder, bliver Defender for Endpoint-agenten onboardet korrekt.

Hvis du kører en antimalwareklient fra tredjepart og bruger Mobile Enhedshåndtering-løsninger eller Microsoft Endpoint Manager (aktuel forgrening), skal du sikre dig, at Microsoft Defender Antivirus ELAM-driveren er aktiveret. Du kan få flere oplysninger under [Kontrollér, at Microsoft Defender Antivirus ikke er deaktiveret af en politik](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="related-topics"></a>Relaterede emner

- [Konfigurer Microsoft Defender for Endpoint installation](production-deployment.md)
- [Onboard enheder](onboard-configure.md)
