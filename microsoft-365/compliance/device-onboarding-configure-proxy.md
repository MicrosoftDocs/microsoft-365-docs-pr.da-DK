---
title: Konfigurere indstillinger for enhedsproxy og internetforbindelse for Information Protection
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Konfigurere indstillinger for enhedsproxy og internetforbindelse for Information Protection
ms.openlocfilehash: 2d0bc6484636cffb479ccb96b3458fddf0697cd7
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63596949"
---
# <a name="configure-device-proxy-and-internet-connection-settings-for-information-protection"></a>Konfigurere indstillinger for enhedsproxy og internetforbindelse for Information Protection

Microsoft Endpoint Technologies bruger Microsoft Windows HTTP (WinHTTP) til at rapportere data og kommunikere med Microsofts slutpunktsskytjeneste. Den integrerede tjeneste kører i systemkontekst ved hjælp af LocalSystem-kontoen.

> [!TIP]
> For organisationer, der bruger videresendelsesproxyer som en gateway til internettet, kan du bruge netværksbeskyttelse til at undersøge bag en proxy. Få mere at vide under [Undersøg forbindelseshændelser, der opstår bag fremadrettet proxy.](/windows/security/threat-protection/microsoft-defender-atp/investigate-behind-proxy)

Indstillingen WinHTTP-konfiguration er uafhængig af proxyindstillingerne for Windows-internetbrowsing (WinINet) og kan kun opdage en proxyserver ved hjælp af følgende metoder til automatisk registrering:

- Gennemsigtig proxy
- WPAD (Web Proxy Auto-Discovery Protocol)

> [!NOTE]
> Hvis du bruger gennemsigtig proxy eller WPAD i din netværktopologi, behøver du ikke særlige konfigurationsindstillinger. Du kan finde flere oplysninger om udeladelse af URL-adresser for Defender for slutpunkt i proxyen i Aktivér adgang til [slutpunkt-DLP-skytjenestens URL-adresser på proxyserveren](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server).

- Manuel statisk proxykonfiguration:
  - Registreringsdatabasebaseret konfiguration
  - WinHTTP konfigureret ved hjælp af netsh-kommando – kun egnet til computere i en stabil topologi (f.eks.: en stationær computer i et firmanetværk bag den samme proxy)

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Konfigurer proxyserveren manuelt ved hjælp af en statisk proxy i registreringsdatabasen

For slutpunktsenheder, der ikke har tilladelse til at oprette forbindelse til internettet, skal du konfigurere en registreringsdatabasebaseret statisk proxy. Du skal konfigurere dette for kun at tillade Microsoft Endpoint DLP at rapportere diagnostiske data og kommunikere med Microsofts slutpunktsskytjeneste.

Den statiske proxy kan konfigureres via Gruppepolitik (GP). Gruppepolitikken findes under:

1. Åbne **administrative skabeloner > Windows komponenter > dataindsamling og eksempel builds > konfigurere godkendt proxybrug for** den forbundne brugeroplevelse og telemetritjenesten

2. Angiv den til **Aktiveret** , og **vælg Deaktiver godkendt proxybrug**:

   ![Billede af gruppepolitikindstillinger 1.](../media/atp-gpo-proxy1.png)

3. Åbn **Administrative skabeloner > Windows komponenter > dataindsamling og eksempel builds > Konfigurer forbundne brugeroplevelser og telemetri**:

   Konfigurer proxyen

   ![Billede af gruppepolitikindstillinger 2.](../media/atp-gpo-proxy2.png)

   Politikken angiver to registreringsdatabaseværdier som `TelemetryProxyServer` REG_SZ som `DisableEnterpriseAuthProxy` REG_DWORD under registreringsdatabasenøglen `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

   Registreringsdatabaseværdien TelemetryProxyServer er i dette format \<server name or ip\>:\<port\>. Eksempel: **10.0.0.6:8080**

   Registreringsdatabaseværdien `DisableEnterpriseAuthProxy` skal være indstillet til 1.

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Konfigurere proxyserveren manuelt ved hjælp af kommandoen "netsh"

Brug netsh til at konfigurere en statisk proxy for hele systemet.

> [!NOTE]
> Dette påvirker alle programmer, herunder Windows, der bruger WinHTTP med standardproxy. - Bærbare computere, der ændrer topologien (f.eks.: fra kontor til privat) vil ikke fungere korrekt. Brug den registreringsdatabasebaserede statiske proxykonfiguration.

1. Åbn en administrator-kommandolinje:
    1. Gå til **Start,** og skriv **cmd**
    2. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   `netsh winhttp set proxy <proxy>:<port>`

   For eksempel: **netsh winhttp set proxy 10.0.0.6:8080**

3. Hvis du vil nulstille gevinstenhttps://proxy, skal du angive følgende kommando og trykke på **Enter**:

   `netsh winhttp reset proxy`

Se [Netsh-kommandosyntaksen, kontekster og formatering for at](/windows-server/networking/technologies/netsh/netsh-contexts) få mere at vide.

## <a name="enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server"></a>Aktivér adgang til slutpunkt-DLP-skytjenestens URL-adresser på proxyserveren

Hvis en proxy eller firewall blokerer al trafik som standard og kun tillader bestemte domæner gennem, skal du føje de domæner, der er angivet i arket, der kan downloades, til listen over tilladte domæner.

Dette [regneark, der kan](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Du skal sikre dig, at der ikke er nogen firewall- eller netværksfiltreringsregler, der vil nægte adgang til disse URL-adresser, eller du skal muligvis oprette en tilladelsesregel specifikt for dem.

Hvis en proxy eller firewall har HTTPS-scanning (SSL-inspektion) aktiveret, skal du udelade de domæner, der er angivet i ovenstående tabel, fra HTTPS-scanning.
Hvis en proxy eller firewall blokerer anonym trafik, da Slutpunkt DLP opretter forbindelse fra systemkontekst, skal du sørge for, at anonym trafik er tilladt i de tidligere angivne URL-adresser.

## <a name="verify-client-connectivity-to-microsoft-cloud-service-urls"></a>Bekræft klientforbindelsen til URL-adresser for Microsoft-skytjeneste

Kontrollér, at proxykonfigurationen blev gennemført, at WinHTTP kan finde og kommunikere via proxyserveren i dit miljø, og at proxyserveren tillader trafik til URL-adresserne for Defender for Endpoint-tjenesten.

1. Download værktøjet [MDATP Client Analyzer](https://aka.ms/mdatpanalyzer) på den pc, hvor slutpunktet DLP kører på.
2. Udtræk indholdet MDATPClientAnalyzer.zip enhedens indhold.
3. Åbn en administrator-kommandolinje:
    1. Gå til **Start,** og skriv **cmd**.
    1. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.
4. Angiv følgende kommando, og tryk på **Enter**:

   `HardDrivePath\MDATPClientAnalyzer.cmd`

   *Erstat HardDrivePath* med den sti, som MDATPClientAnalyzer-værktøjet blev hentet til, f.eks.

   **C:\Work\tools\MDATPClientAnalyzer\MDATPClientAnalyzer.cmd**

5. Udtræk **denMDATPClientAnalyzerResult.zip** _-fil, der er oprettet af værktøjet i den mappe, der bruges i _HardDrivePath*.

6. Åbn **MDATPClientAnalyzerResult.txtog** bekræft, at du har udført proxykonfigurationstrinnene for at aktivere serverregistrering og adgang til tjenestens URL-adresser.  Værktøjet kontrollerer forbindelsen mellem Defender for Endpoint-tjenestens URL-adresser, som Defender for Endpoint-klienten er konfigureret til at interagere med. Derefter udskrives resultaterne i **MDATPClientAnalyzerResult.txt** for hver URL-adresse, der potentielt kan bruges til at kommunikere med Defender for Endpoint-tjenesterne. Eksempel:

   ```DOS
   Testing URL: https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command-line proxy: Doesn't exist
   ```

Hvis mindst én af forbindelsesindstillingerne returnerer en (200) status, kan Defender for Endpoint-klienten kommunikere korrekt med den testede URL-adresse ved hjælp af denne forbindelsesmetode.

Men hvis resultaterne af forbindelseskontrollen angiver en fejl, vises der en HTTP-fejl (se HTTP-statuskoder). Du kan derefter bruge URL-adresserne i tabellen, der vises i Aktivér [adgang til slutpunkt-DLP-skytjenestens URL-adresser på proxyserveren](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server). De URL-adresser, du bruger, afhænger af det område, der er valgt under onboarding-proceduren.

> [!NOTE]
>
> Værktøjet Forbindelsesanalyse er ikke kompatibelt med [begrænsningsreglen for reduktion af angrebsoverfladen,](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#block-process-creations-originating-from-psexec-and-wmi-commands) blokprocesoprettelser, der stammer fra PSExec- og WMI-kommandoer. Du skal deaktivere denne regel midlertidigt for at køre forbindelsesværktøjet.
>
> Når TelemetryProxyServer er indstillet i registreringsdatabasen eller via Gruppepolitik, vender Defender til Slutpunkt tilbage til direkte, hvis den ikke kan få adgang til den definerede proxy. Relaterede emner:
>
> - Onboard Windows 10 enheder
> - Fejlfinding af problemer med Microsoft Endpoint DLP-onboarding

## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md)
- [Brug af forebyggelse af datatab på slutpunkt](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/)
- [Onboardingværktøjer og metoder til Windows 10 computere](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Enheder, der er forbundet til Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
