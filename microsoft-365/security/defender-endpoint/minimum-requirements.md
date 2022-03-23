---
title: Minimumskrav til Microsoft Defender til slutpunkt
description: Forstå licenskrav og krav til onboardingenheder til tjenesten
keywords: minimumskrav, licenser, sammenligningstabel
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
ms.openlocfilehash: 03ac5ed0d63fb88639e9b7e1b55987bf328476e1
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63593434"
---
# <a name="minimum-requirements-for-microsoft-defender-for-endpoint"></a>Minimumskrav til Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-minreqs-abovefoldlink)

Der er nogle minimumskrav til onboardingenheder til tjenesten. Få mere at vide om licens-, hardware- og softwarekrav og andre konfigurationsindstillinger for onboardingenheder til tjenesten.

> [!TIP]
>
> - I denne artikel beskrives minimumskravene til Microsoft Defender for Endpoint Plan 2. Hvis du leder efter oplysninger om Defender for Endpoint Plan 1, skal du se [Krav til Defender til Endpoint Plan 1](mde-p1-setup-configuration.md#review-the-requirements).
> - Få mere at vide om de nyeste forbedringer i Defender til Endpoint: [Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/Windows-Defender-Advanced-Threat/ct-p/WindowsDefenderAdvanced).
> - Defender til Slutpunkt demonstrerede brancheførende optik og registreringsfunktioner i den seneste MITRE-evaluering. Læs: [Insights fra den MITRE ATT&CK-baserede evaluering](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

## <a name="licensing-requirements"></a>Licenskrav
Du kan finde oplysninger om licenskrav til Microsoft Defender til Slutpunkt under [Oplysninger om microsoft Defender til slutpunktslicenser](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-defender-for-endpoint).


Du kan finde detaljerede licensoplysninger på webstedet [med produktvilkår og](https://www.microsoft.com/licensing/terms/) arbejde sammen med dit kontoteam for at få mere at vide om vilkårene og betingelserne.

Du kan finde flere oplysninger om en række funktioner i Windows-versioner i [Sammenlign Windows-udgaver](https://www.microsoft.com/windowsforbusiness/compare).

## <a name="browser-requirements"></a>Browserkrav

Access to Defender for Endpoint is done through a browser, supporting the following browsers:

- Microsoft Edge
- Google Chrome

> [!NOTE]
> Selvom andre browsere muligvis fungerer, understøttes de nævnte browsere.

## <a name="hardware-and-software-requirements"></a>Hardware- og softwarekrav

### <a name="supported-windows-versions"></a>Understøttede Windows versioner

- Windows 7 SP1 Enterprise ([Kræver ESU for support](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 7 SP1 Pro ([Kræver ESU for support](/troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq)).
- Windows 8.1 Enterprise
- Windows 8.1 Pro
- Windows 11 Enterprise
- Windows 11 Education
- Windows 11 Pro
- Windows 11 Pro Education
- Windows 10 Enterprise
- [Windows 10 Enterprise LTSC 2016 (eller nyere)](/windows/whats-new/ltsc/)
- Windows 10 Enterprise IoT

    >[!NOTE]
    >Selvom Windows 10 IoT Enterprise er et understøttet operativsystem i Microsoft Defender til slutpunkt og gør det muligt for OEMs/ODMs at distribuere det som en del af deres produkt eller løsning, skal kunder følge OEM/ODM's vejledning vedrørende værtsbaseret installeret software og supportbarhed.

- Windows 10 Education
- Windows 10 Pro
- Windows 10 Pro Education
- Windows server
  - Windows Server 2008 R2 SP1 ([Kræver ESU for support](/windows-server/get-started/extended-security-updates-deploy))
  - Windows Server 2012 R2
  - Windows Server 2016
  - Windows Server, version 1803 eller nyere
  - Windows Server 2019
  - Windows Server 2022
- Windows Virtual Desktop

Enheder på dit netværk skal køre en af disse udgaver.

Hardwarekravene til Defender til slutpunkt på enheder er de samme for de understøttede udgaver.

> Kerner: 2 minimum, 4 foretrukken hukommelse: minimum 1 GB, 4 foretrukken

Du kan finde flere oplysninger om understøttede Windows 10 i (/windows/release-health/release-information).

> [!NOTE]
> Computere, der kører mobilversioner Windows (f.eks. Windows CE og Windows 10 Mobile), understøttes ikke.
>
> Virtuelle maskiner, der Windows 10 Enterprise 2016 LTSB kan støde på problemer med ydeevnen, hvis de køres på ikke-Microsoft-virtualiseringsplatforme.
>
> Til virtuelle miljøer anbefaler vi, at du bruger Windows 10 Enterprise LTSC 2019 eller nyere.

Når komponenter er opdaterede på Microsoft Windows-operativsystemer, følger Microsoft Defender til slutpunktssupport det pågældende operativsystems livscyklus. Du kan få mere at vide under Ofte [stillede spørgsmål om livscyklus](/lifecycle/faq/general-lifecycle). Nye funktioner eller funktioner leveres typisk kun på operativsystemer, der endnu ikke har nået slutningen af deres livscyklus. Sikkerhedsintelligensopdateringer (definition og programopdateringer) og registreringslogik vil fortsat være tilgængelige indtil mindst:

- Slutdato [for support](/lifecycle/products/) (for operativsystemer, der ikke har et udvidet sikkerhedsopdateringsprogram (ESU).
- Slutningen [af ESU-datoen](/lifecycle/faq/extended-security-updates) (for operativsystemer, der har et ESU-program).



### <a name="other-supported-operating-systems"></a>Andre understøttede operativsystemer

- [Android](microsoft-defender-endpoint-android.md)
- [iOS](microsoft-defender-endpoint-ios.md)
- [Linux](microsoft-defender-endpoint-linux.md)
- [macOS](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Du skal bekræfte, at Linux-distributioner og -versioner af Android, iOS og macOS er kompatible med Defender for Endpoint, for at integrationen kan fungere.

### <a name="network-and-data-storage-and-configuration-requirements"></a>Krav til netværks- og datalagring og konfiguration

Når du kører onboardingguiden for første gang, skal du vælge, hvor dine Microsoft Defender til slutpunkt-relaterede oplysninger skal gemmes: i EU, Storbritannien eller USA's datacenter.

> [!NOTE]
>
> - Du kan ikke ændre din datalagringsplacering efter første gang, du har konfigureret den.
> - Gennemse [datalagring og beskyttelse af personlige oplysninger for Microsoft Defender til Slutpunkt](data-storage-privacy.md) for at få flere oplysninger om, hvor og hvordan Microsoft gemmer dine data.

### <a name="diagnostic-data-settings"></a>Indstillinger for diagnostiske data

> [!NOTE]
> Microsoft Defender til Slutpunkt kræver ikke et bestemt diagnosticeringsniveau, så længe det er aktiveret.

Sørg for, at den diagnostiske datatjeneste er aktiveret på alle enheder i organisationen.
Denne tjeneste er som standard aktiveret. Det er god praksis at kontrollere, at du får sensordata fra dem.

#### <a name="use-the-command-line-to-check-the-windows-diagnostic-data-service-startup-type"></a>Brug kommandolinjen til at kontrollere starttypen Windows diagnostiske datatjeneste

1. Åbn en kommandoprompt med administrator på enheden:
   1. Gå til **Start,** og skriv **cmd**.
   2. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```console
   sc qc diagtrack
   ```

   Hvis tjenesten er aktiveret, bør resultatet se ud som på følgende skærmbillede:

   ![Resultat af sc-forespørgselskommandoen for diagtrack.](images/windefatp-sc-qc-diagtrack.png)

Du skal indstille tjenesten til at starte automatisk, hvis **START_TYPE ikke er** indstillet til **AUTO_START**.

#### <a name="use-the-command-line-to-set-the-windows-diagnostic-data-service-to-automatically-start"></a>Brug kommandolinjen til at indstille Windows til automatisk start

1. Åbn en kommandoprompt med administrator på slutpunktet:
    1. Gå til **Start,** og skriv **cmd**.
    2. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

    ```console
    sc config diagtrack start=auto
    ```

3. Der vises en vellykket meddelelse. Bekræft ændringen ved at angive følgende kommando, og tryk på **Enter**:

    ```console
    sc qc diagtrack
    ```

#### <a name="internet-connectivity"></a>Internetforbindelse

Internetforbindelse på enheder kræves enten direkte eller via proxy.

Defender for Endpoint-sensoren kan bruge en daglig gennemsnitlig båndbredde på 5 MB til at kommunikere med Defender for Endpoint-skytjenesten og rapportere cyberdata. Engangsaktiviteter som filuploads og undersøgelse af pakkesamlinger er ikke inkluderet i denne daglige gennemsnitlige båndbredde.

Du kan finde flere oplysninger om yderligere konfigurationsindstillinger for proxy i [Konfigurer indstillinger for enhedsproxy og Internetforbindelse](configure-proxy-internet.md).

Før du onboarder enheder, skal diagnosticeringsdatatjenesten være aktiveret. Tjenesten er som standard aktiveret i Windows 10 Windows 11.

## <a name="microsoft-defender-antivirus-configuration-requirement"></a>Microsoft Defender Antivirus konfigurationskrav

Agenten Defender til Slutpunkt afhænger af muligheden for at Microsoft Defender Antivirus scanne filer og give oplysninger om dem.

Konfigurer sikkerhedsintelligensopdateringer på Defender til slutpunktsenheder, Microsoft Defender Antivirus er den aktive antimalware eller ej. Få mere at vide under [Administrer Microsoft Defender Antivirus opdateringer, og anvend oprindelige planer](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus).

Når Microsoft Defender Antivirus ikke er den aktive antimalware i organisationen, og du bruger Defender for Endpoint-tjenesten, Microsoft Defender Antivirus den passive tilstand.

Hvis din organisation har deaktiveret Microsoft Defender Antivirus gruppepolitik eller andre metoder, skal enheder, der er onboardingenheder, udelukkes fra denne gruppepolitik.

Hvis du onboardingservere, og Microsoft Defender Antivirus ikke er den aktive antimalware på dine servere, skal Microsoft Defender Antivirus enten være konfigureret til at gå i passiv tilstand eller afinstalleret. Konfigurationen afhænger af serverversionen. Du kan finde flere oplysninger [Microsoft Defender Antivirus kompatibilitet.](microsoft-defender-antivirus-compatibility.md)

> [!NOTE]
> Din almindelige gruppepolitik gælder ikke for Tamper Protection, og ændringer i Microsoft Defender Antivirus ignoreres, når Tamper Protection er tændt.

## <a name="microsoft-defender-antivirus-early-launch-antimalware-elam-driver-is-enabled"></a>Microsoft Defender Antivirus for tidlig start-antimalwaredriver (ELAM) er aktiveret

Hvis du kører Microsoft Defender Antivirus det primære antimalwareprodukt på dine enheder, onboarder Defender til Endpoint-agenten.

Hvis du kører en tredjeparts antimalwareklient og bruger løsninger til administration af mobilenheder eller Microsoft Endpoint Manager (aktuel forgrening), skal du sikre dig, at Microsoft Defender Antivirus ELAM-driveren er aktiveret. Du kan finde flere oplysninger [under Sørg for, Microsoft Defender Antivirus ikke er deaktiveret af politikken](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

## <a name="related-topics"></a>Relaterede emner

- [Konfigurer Microsoft Defender til udrulning af Slutpunkt](production-deployment.md)
- [Onboard-enheder](onboard-configure.md)
