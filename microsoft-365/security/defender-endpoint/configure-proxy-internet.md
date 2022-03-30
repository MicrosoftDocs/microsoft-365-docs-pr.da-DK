---
title: Konfigurere indstillinger for enhedsproxy og internetforbindelse
description: Konfigurer proxy- og internetindstillingerne for Microsoft Defender for Endpoint for at aktivere kommunikation med skytjenesten.
keywords: konfigurer, proxy, internet, internetforbindelse, indstillinger, proxyindstillinger, netsh, winhttp, proxyserver
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d687273a3029f3de080f06f328d4d40853142353
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63599288"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Konfigurere indstillinger for enhedsproxy og internetforbindelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Defender for Endpoint-sensoren kræver Microsoft Windows HTTP (WinHTTP) for at rapportere sensordata og kommunikere med Defender for Endpoint-tjenesten. Den integrerede Defender for Endpoint-sensor kører i systemkontekst ved hjælp af LocalSystem-kontoen. Sensoren bruger Microsoft Windows HTTP Services (WinHTTP) til at aktivere kommunikation med Defender for Endpoint-skytjenesten.

> [!TIP]
> For organisationer, der bruger videresendte proxyer som en gateway til internettet, kan du bruge netværksbeskyttelse til at undersøge forbindelseshændelser, der opstår bag [fremadrettet proxyservere](investigate-behind-proxy.md).

Indstillingen WinHTTP-konfiguration er uafhængig af den Windows-internetbrowsing af proxyindstillinger (se [WinINet vs. WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). Den kan kun opdage en proxyserver ved hjælp af følgende registreringsmetoder:

- Autodiscovery-metoder:

  - Gennemsigtig proxy
  
  - WPAD (Web Proxy Auto-Discovery Protocol)

    > [!NOTE]
    > Hvis du bruger gennemsigtig proxy eller WPAD i din netværktopologi, behøver du ikke særlige konfigurationsindstillinger. Du kan finde flere oplysninger om udeladelse af URL-adresser for Defender for slutpunkt i proxyen i Aktivér adgang til [Defender for Endpoint-tjenestens URL-adresser på proxyserveren](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- Manuel statisk proxykonfiguration:

  - Registreringsdatabasebaseret konfiguration
  
  - WinHTTP konfigureret ved hjælp af netsh-kommando: Kun egnet til skriveborde i en stabil topologi (f.eks.: en stationær computer i et firmanetværk bag den samme proxy)

> [!NOTE]
> Defender antivirus- Slutpunktsregistrering og -svar proxyer kan angives uafhængigt af hinanden.  I de følgende afsnit skal du være opmærksom på disse forskelle.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Konfigurer proxyserveren manuelt ved hjælp af en statisk proxy i registreringsdatabasen

Konfigurer en registreringsbaseret statisk proxy for Defender til registrering og svar (Slutpunktsregistrering og -svar)-sensor til at rapportere diagnostiske data og kommunikere med Defender til slutpunktstjenester, hvis en computer ikke har tilladelse til at oprette forbindelse til internettet.

> [!NOTE]
> Når du bruger denne indstilling på Windows 10 eller Windows 11 eller Windows Server 2019 eller Windows Server 2022, anbefales følgende (eller nyere) build og kumulativ opdateringspakke:
>
> - Windows 11
> - Windows 10, version 1809 eller Windows Server 2019 eller Windows Server 2022 –<https://support.microsoft.com/kb/5001384>
> - Windows 10, version 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, version 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10, version 20H2 -<https://support.microsoft.com/kb/4601382>
>
> Disse opdateringer forbedrer forbindelsen og pålideligheden af CnC-kanalen (kommando og kontrol).

Den statiske proxy kan konfigureres via gruppepolitik ( GP), og begge indstillinger under gruppepolitikværdier skal konfigureres til proxyserveren til brug af Slutpunktsregistrering og -svar. Gruppepolitikken findes i administrative skabeloner.

- **Administrative skabeloner > Windows komponenter > dataindsamling og eksempel builds > Konfigurere godkendt proxybrug for** den forbundne brugeroplevelse og telemetritjeneste.

  Angiv den til **Aktiveret** , og **vælg Deaktiver godkendt proxybrug**.

  ![Billede af Gruppepolitik indstilling1.](images/atp-gpo-proxy1.png)

- **Administrative skabeloner > Windows komponenter > dataindsamling og eksempel builds > Konfigurer forbundne brugeroplevelser og telemetri**:

  Konfigurer proxyen.

  ![Billede af Gruppepolitik indstilling2.](images/atp-gpo-proxy2.png)


| Gruppepolitik | Registreringsdatabasenøgle | Posten i registreringsdatabasen | Værdi |
|:---|:---|:---|:---|
| Konfigurere godkendt proxybrug for den forbundne brugeroplevelse og telemetritjenesten | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Konfigurere forbundne brugeroplevelser og telemetri | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> For eksempel: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Konfigurere en statisk proxy for Microsoft Defender Antivirus

Microsoft Defender Antivirus [skybaseret beskyttelse giver](cloud-protection-microsoft-defender-antivirus.md) øjeblikkelig, automatisk beskyttelse mod nye og fremspirende trusler. Bemærk, at forbindelsen er påkrævet for [brugerdefinerede indikatorer](manage-indicators.md) , når Defender Antivirus er din aktive antimalwareløsning. For [Slutpunktsregistrering og -svar i bloktilstand har](edr-in-block-mode.md) primær antimalwareløsning, når du bruger en løsning, der ikke er Microsoft.

Konfigurer den statiske proxy ved hjælp af Gruppepolitik der er tilgængelige i administrative skabeloner:

1. **Administrative skabeloner > Windows komponenter > Microsoft Defender Antivirus > Definer proxyserver til at oprette forbindelse til netværket**. 

2. Indstil den **til Aktiveret** , og definer proxyserveren. Bemærk, at URL-adressen skal have http:// eller https://. Du kan finde understøttede https:// i [Administrer Microsoft Defender Antivirus opdateringer](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Proxyserver for Microsoft Defender Antivirus.":::

3. Under registreringsdatabasenøglen `HKLM\Software\Policies\Microsoft\Windows Defender`indstiller politikken registreringsdatabaseværdien `ProxyServer` som REG_SZ. 

   Registreringsdatabaseværdien `ProxyServer` har følgende strengformat:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> Af hensyn til fleksibilitet og beskyttelse i realtid af skybaseret levering vil Microsoft Defender Antivirus cachelagre den senest kendte arbejdsproxy. Sørg for, at din proxyløsning ikke udfører SSL-inspektion. Dette vil bryde den sikre skyforbindelse. 
>
> Microsoft Defender Antivirus bruger ikke den statiske proxy til at oprette forbindelse til Windows Update eller Microsoft Update til at hente opdateringer. I stedet bruges en proxy for hele systemet, hvis den er konfigureret til at bruge Windows Update eller den konfigurerede interne opdateringskilde i henhold til den [konfigurerede fallback-rækkefølge](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> Hvis det er nødvendigt, kan **du bruge administrative skabeloner > Windows komponenter > Microsoft Defender Antivirus > .pac til** at oprette forbindelse til netværket i Definer automatisk konfiguration af proxy. Hvis du skal konfigurere avancerede konfigurationer med flere proxyer, skal du bruge **administrative skabeloner > Windows Komponenter > Microsoft Defender Antivirus > Definer** adresser til at tilsidesætte proxyserveren og forhindre Microsoft Defender Antivirus i at bruge en proxyserver for disse destinationer. 
>
> Du kan bruge PowerShell med `Set-MpPreference` cmdlet'en til at konfigurere disse indstillinger: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - ProxyServer 

> [!NOTE]
> Hvis du vil bruge proxyen korrekt, skal du konfigurere disse tre forskellige proxyindstillinger:
>  - Microsoft Defender til slutpunkt (MDE)
>  - AV (antivirus)
>  - Registrering af slutpunkt og svar (Slutpunktsregistrering og -svar)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Konfigurere proxyserveren manuelt ved hjælp af kommandoen Netsh

Brug netsh til at konfigurere en statisk proxy for hele systemet.

> [!NOTE]
>
> - Dette påvirker alle programmer, herunder Windows, der bruger WinHTTP med standardproxy.</br>
> - Bærbare computere, der ændrer topologien (f.eks.: fra office til privat brug), fungerer ikke korrekt med netsh-kommandoen. Brug den registreringsdatabasebaserede statiske proxykonfiguration.

1. Åbn en administrator-kommandolinje:
   1. Gå til **Start,** og skriv **cmd**.
   1. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   For eksempel: `netsh winhttp set proxy 10.0.0.6:8080`

Hvis du vil nulstille gevinstenhttps://proxy, skal du angive følgende kommando og trykke på **Enter**:

```PowerShell
netsh winhttp reset proxy
```

Se [Netsh-kommandosyntaksen, kontekster og formatering for at](/windows-server/networking/technologies/netsh/netsh-contexts) få mere at vide.

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Aktivér adgang til URL-adresser for Microsoft Defender for Endpoint-tjenesten på proxyserveren

Hvis en proxy eller firewall som standard blokerer al trafik og kun tillader bestemte domæner, skal du føje de domæner, der er angivet i arket, der kan downloades, til listen over tilladte domæner.

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Sørg for, at der ikke er nogen firewall- eller netværksfiltreringsregler for at nægte adgang for disse URL-adresser. Valgfrit, det kan være nødvendigt at oprette en *tilladelsesregel* specifikt for dem.

<br>

**** 
|Listen Regneark over domæner| Beskrivelse|
|---|---|
|URL-adresseliste for Microsoft Defender til slutpunkt for kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og operativsystem for kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| URL-adresseliste for Microsoft Defender til slutpunkt for Gov/GCC/DoD-kunder | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Hvis en proxy eller firewall har HTTPS-scanning (SSL-inspektion) aktiveret, skal du udelade de domæner, der er angivet i ovenstående tabel, fra HTTPS-scanning.
I din firewall skal du åbne alle URL-adresserne, hvor kolonnen geografi er WW. For rækker, hvor geografikolonnen ikke er WW, skal du åbne URL-adresserne til din specifikke dataplacering. Hvis du vil bekræfte indstillingen for din dataplacering, [skal du se Bekræft datalagringsplacering og opdater indstillingerne for dataopbevaring for Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows enheder, der kører med version 1803 eller tidligere behov`settings-win.data.microsoft.com`.  <br>
>
> URL-adresser, der indeholder v20 i dem, er kun nødvendige, hvis du har Windows enheder, der kører version 1803 eller nyere. Er f.eks. nødvendig for Windows enhed, `us-v20.events.data.microsoft.com` der kører version 1803 eller nyere og er onboardet til et Storage område.
>

Hvis en proxy eller firewall blokerer anonym trafik som Defender for Endpoint-sensoren, og der oprettes forbindelse fra systemkontekst for at sikre, at anonym trafik er tilladt i de tidligere angivne URL-adresser.

> [!NOTE]
> Microsoft har ikke en proxyserver. Disse URL-adresser er tilgængelige via den proxyserver, du konfigurerer.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (OVERENSSTEMMELSE) – krav til proxy og firewall for ældre versioner Windows klient eller Windows Server

Oplysningerne på listen over konfigurationsoplysninger for proxy og firewall er nødvendige for at kommunikere med agenten Log Analytics (ofte kaldet Microsoft Overvågningsagent) for tidligere versioner af Windows, f.eks. Windows 7 SP1, Windows 8.1 og Windows Server 2008 R2*.

<br>

****

|Agentressource|Porte|Retning|Tilgår HTTPS-inspektion|
|---|---|---|---|
|*.ods.opinsights.azure.com|Port 443|Udgående|Ja|
|*.oms.opinsights.azure.com|Port 443|Udgående|Ja|
|*.blob.core.windows.net|Port 443|Udgående|Ja|
|*.azure-automation.net|Port 443|Udgående|Ja|

> [!NOTE]
> *Disse forbindelseskrav gælder for den forrige Microsoft Defender til slutpunktet Windows Server 2016 og Windows Server 2012 R2, der kræver OVERENSSTEMMELSE. Instruktioner til onboarding af disse operativsystemer med den nye samlede løsning er på [Onboard Windows-servere](configure-server-endpoints.md), eller overfør til den nye samlede løsning på [Server migration scenarios i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Ip-området kan ændres som en skybaseret løsning. Det anbefales, at du flytter til DNS og løser indstillingen.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Bekræft URL-krav til Microsoft Monitoring Agent -tjenesten 

 Se følgende vejledning for at fjerne kravene til jokertegn (*) for dit specifikke miljø, når du bruger Microsoft Monitoring Agent (ÆLDRE) for tidligere versioner af Windows.

1. Onboard et tidligere operativsystem med Microsoft Monitoring Agent (VERSIONS) i Defender for Endpoint (få mere at vide under Onboard tidligere versioner af [Windows på Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2010326) og [Onboard Windows-servere](configure-server-endpoints.md)).

2. Sørg for, at maskinen rapporterer korrekt til Microsoft 365 Defender-portalen.

3. Kør værktøjet TestCloudConnection.exe fra "C:\Program Files\Microsoft Monitoring Agent\Agent" for at validere forbindelsen og for at få de nødvendige URL-adresser til dit specifikke arbejdsområde.

4. Kontrollér listen med URL-adresser for Microsoft Defender til slutpunkt for at se en komplet liste over krav til dit område (se regnearket med tjenestens [URL-adresser](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)).

    ![Billede af administrator i Windows PowerShell.](images/admin-powershell.png)

Jokertegnene (\*), \*der bruges i slutpunkterne .ods.opinsights.azure.com, \*.oms.opinsights.azure.com og \*.agentsvc.azure-automation.net URL, kan erstattes med dit specifikke arbejdsområde-id. Arbejdsområde-id'et er specifikt for dit miljø og arbejdsområde. Den findes i onboardingsektionen i din lejer på Microsoft 365 Defender-portalen.

Url-blob.core.windows.net-slutpunktet \*kan erstattes med de URL-adresser, der er vist i afsnittet "Firewallregel: \*.blob.core.windows.net" i testresultaterne.

> [!NOTE]
> I forbindelse med onboarding via Microsoft Defender til cloud kan du bruge flere arbejdsområder. Du skal udføre TestCloudConnection.exe-proceduren på onboardingmaskine fra hvert arbejdsområde (for at afgøre, om der er nogen ændringer i *.blob.core.windows.net-webadresserne mellem arbejdsområderne).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Bekræft klientforbindelsen til URL-adresser for Microsoft Defender for Endpoint-tjenesten

Kontrollér, at proxykonfigurationen er fuldført. WinHTTP kan derefter finde og kommunikere via proxyserveren i dit miljø, og derefter tillader proxyserveren trafik til URL-adresserne for Defender for Endpoint-tjenesten.

1. Download [værktøjet Microsoft Defender for Endpoint Client Analyzer](https://aka.ms/mdeanalyzer) på pc'en, hvor Defender for Endpoint-sensoren kører på. Til servere med downlevel skal du bruge den nyeste prøveversion, der kan [downloades betaversionen af Microsoft Defender til Endpoint Client Analyzer](https://aka.ms/BetaMDEAnalyzer).

2. Udtræk indholdet MDEClientAnalyzer.zip enhedens indhold.

3. Åbn en administrator-kommandolinje:
   1. Gå til **Start,** og skriv **cmd**.
   1. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

4. Angiv følgende kommando, og tryk på **Enter**:

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    *Erstat HardDrivePath* med den sti, hvor værktøjet MDEClientAnalyzer blev downloadet. Eksempel:

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. Værktøjet opretter og udtrækker den *MDEClientAnalyzerResult.zip* fil i mappen, der skal bruges i *HardDrivePath*.

6. Åbn *MDEClientAnalyzerResult.txtog* bekræft, at du har udført de proxykonfigurationstrin, der skal bruges for at aktivere serverregistrering og adgang til tjenestens URL-adresser.

   Værktøjet kontrollerer forbindelsen mellem Defender og Endpoint-tjenestens URL-adresser. Sørg for, at Defender for Endpoint-klienten er konfigureret til at interagere. Værktøjet udskriver resultaterne i *MDEClientAnalyzerResult.txtfor hver* URL-adresse, der potentielt kan bruges til at kommunikere med Defender for Endpoint-tjenesterne. Eksempel:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Hvis en af forbindelsesindstillingerne returnerer en (200) status, kan Defender til slutpunkt-klienten kommunikere korrekt med den testede URL-adresse ved hjælp af denne forbindelsesmetode.

Men hvis resultaterne af forbindelseskontrollen angiver en fejl, vises der en HTTP-fejl (se HTTP-statuskoder). Du kan derefter bruge URL-adresserne i tabellen, der vises i Aktivér adgang til [URL-adresser for Defender for Endpoint-tjenesten på proxyserveren](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). De URL-adresser, der er tilgængelige til brug, afhænger af det område, der er valgt under onboarding-proceduren.

> [!NOTE]
> Værktøjet Forbindelsesanalyses forbindelseskontroller i skyen er ikke kompatible med blokprocesoprettelser af angrebsoverfladen, der stammer fra [PSExec- og WMI-kommandoer.](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands) Du skal deaktivere denne regel midlertidigt for at køre forbindelsesværktøjet. Du kan også midlertidigt tilføje [ASR-udeladelse, når](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) du kører analyseatoren.
>
> Når TelemetryProxyServer er angivet i registreringsdatabasen eller via Gruppepolitik, vil Defender til slutpunkt falde tilbage, og den får ikke adgang til den definerede proxy.

## <a name="related-articles"></a>Relaterede artikler

- [Brug Gruppepolitik til at konfigurere og administrere Microsoft Defender Antivirus](use-group-policy-microsoft-defender-antivirus.md)
- [Onboard Windows-enheder](configure-endpoints.md)
- [Fejlfinding af onboardingproblemer i Microsoft Defender til Slutpunkt](troubleshoot-onboarding.md)
