---
title: Konfigurer indstillingerne for enhedsproxy og internetforbindelse
description: Konfigurer indstillingerne for Microsoft Defender for Endpoint proxy og internet for at aktivere kommunikation med cloudtjenesten.
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
ms.openlocfilehash: 049fd7b7bcec0ebdc4690cd666bdb99ced5bf504
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873484"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Konfigurer indstillingerne for enhedsproxy og internetforbindelse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Defender for Endpoint-sensoren kræver, at Microsoft Windows HTTP (WinHTTP) rapporterer sensordata og kommunikerer med Defender for Endpoint-tjenesten. Den integrerede Defender for Endpoint-sensor kører i systemkontekst ved hjælp af LocalSystem-kontoen. Sensoren bruger Microsoft Windows HTTP Services (WinHTTP) til at aktivere kommunikation med Cloudtjenesten Defender for Endpoint.

> [!TIP]
> For organisationer, der bruger videresendelsesproxyer som en gateway til internettet, kan du bruge netværksbeskyttelse til at [undersøge forbindelseshændelser, der opstår bag fremadrettede proxyer](investigate-behind-proxy.md).

Konfigurationsindstillingen WinHTTP er uafhængig af proxyindstillingerne for Windows Internet (WinINet) (se [WinINet vs. WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). Den kan kun finde en proxyserver ved hjælp af følgende registreringsmetoder:

- Metoder til automatisk søgning:

  - Gennemsigtig proxy
  
  - WPAD (Web Proxy Auto-Discovery Protocol)

    > [!NOTE]
    > Hvis du bruger gennemsigtig proxy eller WPAD i din netværkstopologi, behøver du ikke særlige konfigurationsindstillinger. Du kan finde flere oplysninger om undtagelser for URL-adresser til Defender for Endpoint i proxyen under [Aktivér adgang til URL-adresser til Defender for Endpoint-tjenesten på proxyserveren](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- Manuel statisk proxykonfiguration:

  - Registreringsdatabasebaseret konfiguration
  
  - WinHTTP konfigureret ved hjælp af netsh-kommando: Egner sig kun til stationære computere i en stabil topologi (f.eks. en stationær computer i et virksomhedsnetværk bag den samme proxy)

> [!NOTE]
> Defender antivirus og Slutpunktsregistrering og -svar proxyer kan angives uafhængigt af hinanden.  I de efterfølgende afsnit skal du være opmærksom på disse forskelle.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Konfigurer proxyserveren manuelt ved hjælp af en registreringsdatabasebaseret statisk proxy

Konfigurer en registreringsbaseret statisk proxy for Defender for Endpoint-registrerings- og svarsensor (Slutpunktsregistrering og -svar) til at rapportere diagnosticeringsdata og kommunikere med Defender for Endpoint-tjenester, hvis en computer ikke har tilladelse til at oprette forbindelse til internettet.

> [!NOTE]
> Når du bruger denne indstilling på Windows 10, Windows 11 eller Windows Server 2019 eller Windows Server 2022, anbefales det at have følgende (eller nyere) build og kumulativ opdateringspakke:
>
> - Windows 11
> - Windows 10, version 1809 eller Windows Server 2019 eller Windows Server 2022 -<https://support.microsoft.com/kb/5001384>
> - Windows 10, version 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, version 2004 –<https://support.microsoft.com/kb/4601382>
> - Windows 10, version 20H2 –<https://support.microsoft.com/kb/4601382>
>
> Disse opdateringer forbedrer forbindelsen til og pålideligheden af CnC-kanalen (Command and Control).

Den statiske proxy kan konfigureres via gruppepolitik (GP), begge indstillinger under gruppepolitikværdier skal konfigureres til proxyserveren til brug af Slutpunktsregistrering og -svar. Gruppepolitikken er tilgængelig i Administrative skabeloner.

- **Administrative skabeloner > Windows komponenter > dataindsamling og eksempelbuilds > Konfigurer godkendt proxyanvendelse for tjenesten Tilsluttet brugeroplevelse og telemetri**.

  Angiv den til **Aktiveret** , og vælg **Deaktiver godkendt proxyanvendelse**.

  :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Statusruden Gruppepolitik setting1" lightbox="images/atp-gpo-proxy1.png":::

- **Administrative skabeloner > Windows komponenter > dataindsamling og eksempelbuilds > Konfigurer forbundne brugeroplevelser og telemetri**:

  Konfigurer proxyen.

  :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Statusruden Gruppepolitik setting2" lightbox="images/atp-gpo-proxy2.png":::


| Gruppepolitik | Registreringsdatabasenøgle | Registreringsdatabasen | Værdi |
|:---|:---|:---|:---|
| Konfigurer godkendt proxyforbrug for den tilsluttede brugeroplevelse og telemetritjenesten | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Konfigurer forbundne brugeroplevelser og telemetri | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> Eksempel: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Konfigurer en statisk proxy for Microsoft Defender Antivirus

Microsoft Defender Antivirus [cloudbaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md) sikrer næsten øjeblikkelig, automatiseret beskyttelse mod nye og nye trusler. Bemærk, at der kræves forbindelse til [brugerdefinerede indikatorer](manage-indicators.md) , når Defender Antivirus er din aktive antimalwareløsning. For [Slutpunktsregistrering og -svar i bloktilstand](edr-in-block-mode.md) har en primær antimalwareløsning, når du bruger en ikke-Microsoft-løsning.

Konfigurer den statiske proxy ved hjælp af de Gruppepolitik, der er tilgængelige i Administrative skabeloner:

1. **Administrative skabeloner > Windows Komponenter > Microsoft Defender Antivirus > Definer proxyserver til oprettelse af forbindelse til netværket**. 

2. Angiv den til **Aktiveret** , og definer proxyserveren. Bemærk, at URL-adressen skal have enten http:// eller https://. Du kan se understøttede versioner til https:// under [Administrer Microsoft Defender Antivirus opdateringer](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Proxyserveren for Microsoft Defender Antivirus" lightbox="images/proxy-server-mdav.png":::

3. Under registreringsdatabasenøglen `HKLM\Software\Policies\Microsoft\Windows Defender`angiver politikken registreringsdatabaseværdien `ProxyServer` som REG_SZ. 

   Registreringsdatabaseværdien `ProxyServer` har følgende strengformat:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> Af hensyn til robusthed og cloudbaseret beskyttelse i realtid cachelagrer Microsoft Defender Antivirus den senest kendte arbejdsproxy. Sørg for, at proxyløsningen ikke udfører SSL-inspektion. Dette ødelægger den sikre cloudforbindelse. 
>
> Microsoft Defender Antivirus bruger ikke den statiske proxy til at oprette forbindelse til Windows Update eller Microsoft Update til download af opdateringer. Den bruger i stedet en proxy for hele systemet, hvis den er konfigureret til at bruge Windows Update, eller den konfigurerede interne opdateringskilde i henhold til den [konfigurerede reserveordre](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> Hvis det er nødvendigt, kan du bruge **Administrative skabeloner > Windows Komponenter > Microsoft Defender Antivirus > Definer automatisk konfiguration af proxy (.pac)** til at oprette forbindelse til netværket. Hvis du har brug for at konfigurere avancerede konfigurationer med flere proxyer, skal du bruge **Administrative skabeloner > Windows Komponenter > Microsoft Defender Antivirus > Definer adresser** til at tilsidesætte proxyserveren og forhindre Microsoft Defender Antivirus i at bruge en proxyserver til disse destinationer. 
>
> Du kan bruge PowerShell sammen med cmdlet'en `Set-MpPreference` til at konfigurere disse indstillinger: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - Proxyserver 

> [!NOTE]
> Hvis du vil bruge proxyen korrekt, skal du konfigurere disse tre forskellige proxyindstillinger:
>  - Microsoft Defender for Endpoint (MDE)
>  - AV (Antivirus)
>  - Registrering af slutpunkt og svar (Slutpunktsregistrering og -svar)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Konfigurer proxyserveren manuelt ved hjælp af kommandoen netsh

Brug netsh til at konfigurere en statisk proxy for hele systemet.

> [!NOTE]
>
> - Dette påvirker alle programmer, herunder Windows tjenester, der bruger WinHTTP med standardproxy.</br>
> - Bærbare computere, der skifter topologi (f.eks. fra kontor til hjem), fungerer ikke korrekt med netsh-kommandoen. Brug den registreringsdatabasebaserede statiske proxykonfiguration.

1. Åbn en kommandolinje med administratorrettigheder:
   1. Gå til **Start,** og skriv **cmd**.
   1. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```command prompt
   netsh winhttp set proxy <proxy>:<port>
   ```

   For eksempel: `netsh winhttp set proxy 10.0.0.6:8080`

Hvis du vil nulstille winhttp-proxyen, skal du angive følgende kommando og trykke på **Enter**:

```command prompt
netsh winhttp reset proxy
```

Se [Netsh-kommandosyntaks, kontekster og formatering for](/windows-server/networking/technologies/netsh/netsh-contexts) at få mere at vide.

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Aktivér adgang til url-adresser til Microsoft Defender for Endpoint-tjenesten på proxyserveren

Hvis en proxy eller firewall som standard blokerer al trafik og kun tillader bestemte domæner, skal du som standard føje de domæner, der er angivet i arket, som kan downloades, til listen over tilladte domæner.

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Sørg for, at der ikke er nogen regler for firewall- eller netværksfiltrering for at nægte adgang til disse URL-adresser. Valgfrit kan det være nødvendigt at oprette en *tilladelsesregel* specifikt for dem.

<br>

|Regneark med domæneliste| Beskrivelse|
|---|---|
|Microsoft Defender for Endpoint URL-adresseliste til kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OPERATIVSYSTEM til kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx) <p> Bemærk, at Microsoft Defender for Endpoint Plan 1 og Plan 2 deler de samme URL-adresser til proxytjenesten.
| Microsoft Defender for Endpoint URL-adresseliste for Gov/GCC/DoD | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Hvis en proxy eller firewall har HTTPS-scanning (SSL-inspektion) aktiveret, skal du udelade de domæner, der er angivet i ovenstående tabel, fra HTTPS-scanning.
Åbn alle de URL-adresser, hvor kolonnen geografi er WW, i din firewall. For rækker, hvor geografikolonnen ikke er WW, skal du åbne URL-adresserne til din specifikke dataplacering. Hvis du vil bekræfte indstillingen for din dataplacering, skal du se [Bekræft datalagerplacering og opdatere indstillingerne for dataopbevaring for Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows enheder, der kører med version 1803 eller tidligere, skal bruge `settings-win.data.microsoft.com`.  <br>
>
> URL-adresser, der indeholder v20 i dem, er kun nødvendige, hvis du har Windows enheder, der kører version 1803 eller nyere. Er f.eks. nødvendig for en Windows enhed, `us-v20.events.data.microsoft.com` der kører version 1803 eller nyere, og som er onboardet til US Data Storage område.
>

Hvis en proxy eller firewall blokerer anonym trafik som Defender for Endpoint-sensor, og den opretter forbindelse fra systemkonteksten for at sikre, at anonym trafik er tilladt i de tidligere angivne URL-adresser.

> [!NOTE]
> Microsoft leverer ikke en proxyserver. Disse URL-adresser er tilgængelige via den proxyserver, du konfigurerer.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) – proxy- og firewallkrav til ældre versioner af Windows klient eller Windows Server

Oplysningerne på listen over proxy- og firewallkonfigurationsoplysninger kræves for at kommunikere med Log Analytics Agent (ofte kaldet Microsoft Monitoring Agent) for tidligere versioner af Windows, f.eks. Windows 7 SP1, Windows 8.1 og Windows Server 2008 R2*.

<br>

****

|Agentressource|Porte|Retning|Tilsidesæt HTTPS-inspektion|
|---|---|---|---|
|*.ods.opinsights.azure.com|Port 443|Udgående|Ja|
|*.oms.opinsights.azure.com|Port 443|Udgående|Ja|
|*.blob.core.windows.net|Port 443|Udgående|Ja|
|*.azure-automation.net|Port 443|Udgående|Ja|

> [!NOTE]
> *Disse forbindelseskrav gælder for den tidligere Microsoft Defender for Endpoint af Windows Server 2016 og Windows Server 2012 R2, der kræver MMA. Instruktioner til onboarding af disse operativsystemer med den nye unified løsning findes på [Onboard Windows-servere](configure-server-endpoints.md) eller migrere til den nye samlede løsning på [Server migrationsscenarier i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Ip-intervallet kan ændres som en cloudbaseret løsning. Det anbefales, at du flytter til indstillingen for DNS-løsning.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Bekræft KRAV til URL-adresse til Microsoft-overvågningsagent (MMA) 

 Se følgende vejledning for at fjerne kravet om jokertegn (*) for dit specifikke miljø, når du bruger Microsoft Monitoring Agent (MMA) til tidligere versioner af Windows.

1. Onboard et tidligere operativsystem med Microsoft Monitoring Agent (MMA) i Defender for Endpoint (du kan finde flere oplysninger under [Onboard tidligere versioner af Windows på Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2010326)- og [Onboard Windows-servere](configure-server-endpoints.md)).

2. Sørg for, at computeren rapporterer til Microsoft 365 Defender-portalen.

3. Kør værktøjet TestCloudConnection.exe fra "C:\Program Files\Microsoft Monitoring Agent\Agent" for at validere forbindelsen og for at hente de påkrævede URL-adresser til dit specifikke arbejdsområde.

4. Se listen over Microsoft Defender for Endpoint URL-adresser for at se den komplette liste over krav til dit område (se [tjenestens URL-regneark](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)).

   :::image type="content" source="images/admin-powershell.png" alt-text="Administratoren i Windows PowerShell" lightbox="images/admin-powershell.png":::

De jokertegn (\*), der bruges i \*.ods.opinsights.azure.com, \*.oms.opinsights.azure.com og \*.agentsvc.azure-automation.net URL-slutpunkter, kan erstattes med dit specifikke arbejdsområde-id. Arbejdsområde-id'et er specifikt for dit miljø og arbejdsområde. Du kan finde den i afsnittet Onboarding i din lejer på Microsoft 365 Defender portalen.

Url-slutpunktet \*.blob.core.windows.net kan erstattes med de URL-adresser, der vises i afsnittet "Firewallregel: \*.blob.core.windows.net" i testresultaterne.

> [!NOTE]
> I tilfælde af onboarding via Microsoft Defender for Cloud kan der bruges flere arbejdsområder. Du skal udføre TestCloudConnection.exe-proceduren på den onboardede maskine fra hvert arbejdsområde (for at afgøre, om der er ændringer af URL-adresserne til *.blob.core.windows.net mellem arbejdsområderne).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Bekræft klientforbindelsen til URL-adresser til Microsoft Defender for Endpoint-tjenesten

Kontrollér, at proxykonfigurationen er fuldført. WinHTTP kan derefter finde og kommunikere via proxyserveren i dit miljø, og derefter tillader proxyserveren trafik til URL-adresserne til Defender for Endpoint-tjenesten.

1. Download [værktøjet Microsoft Defender for Endpoint Klientanalyse](https://aka.ms/mdeanalyzer) til den pc, hvor Defender for Endpoint-sensoren kører. Til komplekse servere kan du bruge den nyeste prøveversion, der er tilgængelig til download [Microsoft Defender for Endpoint Client Analyzer tool Beta](https://aka.ms/BetaMDEAnalyzer).

2. Udpak indholdet af MDEClientAnalyzer.zip på enheden.

3. Åbn en kommandolinje med administratorrettigheder:
   1. Gå til **Start,** og skriv **cmd**.
   1. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

4. Angiv følgende kommando, og tryk på **Enter**:

    ```command prompt
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    Erstat *HardDrivePath* med den sti, hvor værktøjet MDEClientAnalyzer blev downloadet. Eksempel:

    ```command prompt
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. Værktøjet opretter og udtrækker den *MDEClientAnalyzerResult.zip* fil i mappen, der skal bruges i *HardDrivePath*.

6. Åbn *MDEClientAnalyzerResult.txt* , og kontrollér, at du har udført proxykonfigurationstrinnene for at aktivere serverregistrering og adgang til tjenestens URL-adresser.

   Værktøjet kontrollerer forbindelsen til URL-adresserne til Defender for Endpoint-tjenesten. Sørg for, at Defender for Endpoint-klienten er konfigureret til at interagere. Værktøjet udskriver resultaterne i *MDEClientAnalyzerResult.txt-filen* for hver URL-adresse, der potentielt kan bruges til at kommunikere med Defender for Endpoint-tjenesterne. Eksempel:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Hvis en af forbindelsesindstillingerne returnerer en (200)-status, kan Defender for Endpoint-klienten kommunikere med den testede URL-adresse korrekt ved hjælp af denne forbindelsesmetode.

Men hvis resultaterne af kontrollen af forbindelsen indikerer en fejl, vises der en HTTP-fejl (se HTTP-statuskoder). Du kan derefter bruge URL-adresserne i den tabel, der vises i [Aktivér adgang til URL-adresser til Defender for Endpoint-tjenesten på proxyserveren](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). De URL-adresser, der er tilgængelige til brug, afhænger af det område, der er valgt under onboardingproceduren.

> [!NOTE]
> Kontrol af forbindelsesanalyseværktøjets cloudforbindelse er ikke kompatibel med [blokoprettelser af attack surface reduction-processer, der stammer fra PSExec- og WMI-kommandoer](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). Du skal deaktivere denne regel midlertidigt for at køre forbindelsesværktøjet. Du kan også tilføje [ASR-udeladelser](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) midlertidigt, når du kører analysefunktionen.
>
> Når TelemetryProxyServer er angivet i registreringsdatabasen eller via Gruppepolitik, går Defender for Endpoint tilbage, og den kan ikke få adgang til den definerede proxy.

## <a name="related-articles"></a>Relaterede artikler

- [Brug Gruppepolitik indstillinger til at konfigurere og administrere Microsoft Defender Antivirus](use-group-policy-microsoft-defender-antivirus.md)
- [Onboarde Windows enheder](configure-endpoints.md)
- [Fejlfinding af problemer med Microsoft Defender for Endpoint onboarding](troubleshoot-onboarding.md)
