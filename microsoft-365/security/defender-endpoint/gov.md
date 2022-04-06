---
title: Microsoft Defender til slutpunkt for kunder inden for det amerikanske offentlige
description: Få mere at vide om de kundekrav og egenskaber, der er tilgængelige for Microsoft Defender til Slutpunkt for det amerikanske offentlige
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft Defender for Endpoint, endpoint, dod
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
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 03d4d22bdce9f18b4883437215ea5cba50b3868e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681342"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender til slutpunkt for kunder inden for det amerikanske offentlige

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Microsoft Defender til slutpunkt for kunder i det amerikanske offentlige miljø, der er indbygget i Azure US Government-miljøet, bruger de samme underliggende teknologier som Defender til slutpunkt i Azure Commercial.

Dette tilbud er tilgængeligt for GCC-, GCC High- og DoD-kunder og er baseret på den samme forebyggelse, registrering, undersøgelse og afhjælpning som den kommercielle version. Der er dog nogle forskelle i tilgængeligheden af funktioner for dette tilbud.

> [!NOTE]
> Hvis du er en GCC, der bruger Defender til slutpunkt i kommercielt, kan du se siderne med offentlig dokumentation.

## <a name="licensing-requirements"></a>Licenskrav

Microsoft Defender til Slutpunkt for kunder i det amerikanske offentlige myndigheder kræver et af følgende Microsoft-volumenlicenstilbud:

### <a name="desktop-licensing"></a>Skrivebordslicenser

<br />

****

|GCC|GCC høj|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 til GCC Høj|Microsoft 365 G5 til DOD|
|Microsoft 365 G5-sikkerheds GCC|Microsoft 365 G5-sikkerhed til GCC High|Microsoft 365 G5-sikkerhed til DOD|
|Microsoft Defender til slutpunkt – GCC|Microsoft Defender til slutpunkt for GCC High|Microsoft Defender til slutpunkt for DOD|
|Windows 10 Enterprise E5-GCC|Windows 10 Enterprise E5 til GCC Høj|Windows 10 Enterprise E5 til DOD|
|

### <a name="server-licensing"></a>Serverlicensering

<br />

****

|GCC|GCC høj|DoD|
|---|---|---|
|Microsoft Defender for Endpoint Server GCC|Microsoft Defender for Endpoint Server til GCC High|Microsoft Defender for Endpoint Server for DOD|
|Microsoft Defender til servere|Microsoft Defender til servere – Government|Microsoft Defender til servere – Government|
|

## <a name="portal-urls"></a>Url-adresser for portaler

Følgende er URL-adresserne på Microsoft Defender for Endpoint-portalen for kunder i det amerikanske offentlige:

<br />

****

|Kundetype|URL-adresse til portal|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC høj|<https://security.microsoft.us>|
|DoD|<https://security.microsoft.us>|
|
> [!NOTE]
> Hvis du er GCC-kunde og er i gang med at flytte fra microsoft Defender til slutpunkt kommerciel til GCC, https://transition.security.microsoft.com kan du bruge til at få adgang til dine kommercielle Microsoft Defender for Endpoint-data.

## <a name="endpoint-versions"></a>Slutpunktsversioner

### <a name="standalone-os-versions"></a>Enkeltstående OS-versioner

Følgende os-versioner understøttes:

<br />

****

OS-version|GCC|GCC høj|DoD
:---|:---:|:---:|:---:
Windows 11|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 21H1 og nyere|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 20H2 (med [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 2004 (med [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 1909 (med [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 1903 (med [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 1809 (med [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 1803 (med [KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup>)|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 10, version 1709|![Nej.](images/svg/check-no.svg) <br /> Bemærk! Understøttes ikke|![Ja](images/svg/check-yes.svg) med [KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> <br /> Bemærk! [Frarådes](/lifecycle/announcements/revised-end-of-service-windows-10-1709). Opgrader|![Nej](images/svg/check-no.svg) <br /> Bemærk! Understøttes ikke
Windows 10, version 1703 og tidligere|![Nej.](images/svg/check-no.svg) <br /> Bemærk! Understøttes ikke|![Nej](images/svg/check-no.svg) <br /> Bemærk! Understøttes ikke|![Nej](images/svg/check-no.svg) <br /> Bemærk! Understøttes ikke
Windows Server 2022|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2019 (med [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2016 (moderne) <sup>2</sup>|![Ja.](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion
Windows Server 2012 R2 (moderne) <sup>2</sup>|![Ja.](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion
Windows Server 2016 (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2012 R2 (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 8.1 Enterprise (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 8 Pro (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 7 SP1 Enterprise (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 7 SP1 Pro (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Linux|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
macOS|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Android|![Ja.](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion
iOS|![Ja.](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion
|

> [!NOTE]
> <sup>1</sup> Programrettelsen skal installeres før onboarding af enheden for at konfigurere Defender til Slutpunkt til det korrekte miljø.
>
> <sup>2</sup> Få mere at [vide om den samlede moderne løsning til Windows 2016 og 2012 R2](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview). Hvis du tidligere har onboardet dine servere ved hjælp af VEJLEDNINGEN, skal du følge vejledningen i [Serveroverførsel](server-migration.md) for at overføre til den nye løsning.
>
> <sup>3</sup> Når du bruger [Microsoft Overvågningsagent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma), skal du vælge "Azure US Government" under "Azure Cloud[", hvis](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard) du bruger konfigurationsguiden, eller hvis du [](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) bruger en kommandolinje eller et [script](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) – skal du angive parameteren "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" til 1. <br /> Den understøttede minimumsversion af  ÆLDRE er 10.20.18029 (marts 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>OS-versioner, når du bruger Microsoft Defender til servere

Følgende os-versioner understøttes, når du [bruger Microsoft Defender til servere](/azure/security-center/security-center-wdatp):

<br />

****

OS-version|GCC|GCC høj|DoD
:---|:---:|:---:|:---:
Windows Server 2022|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2019|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2016|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2012 R2|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>Påkrævede forbindelsesindstillinger

Hvis en proxy eller firewall blokerer al trafik som standard og kun tillader bestemte domæner gennem, skal du føje de domæner, der er angivet i arket, der kan downloades, til listen over tilladte domæner.

Følgende regneark, der kan downloades, viser de tjenester og de tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Bekræft, at der ikke er nogen firewall eller regler for netværksfiltrering, der vil nægte adgang til disse URL-adresser, eller opret en tilladelsesregel specifikt for dem.

|Listen Regneark over domæner| Beskrivelse|
|---|---|
| URL-adresseliste for Microsoft Defender til slutpunkt for Gov/GCC/DoD-kunder | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Få mere at vide under Konfigurer [indstillinger for enhedsproxy og Internetforbindelse](configure-proxy-internet.md).

> [!NOTE]
> Regnearket indeholder også kommercielle URL-adresser, og du skal kontrollere fanerne "US Gov".
>
> Når du filtrerer, skal du se efter de poster, der er mærket "US Gov" og din specifikke sky under kolonnen Geografi.

## <a name="api"></a>API

I stedet for de offentlige URI'er, der [er angivet i vores API-dokumentation](apis-intro.md), skal du bruge følgende URI'er:

<br />

****

|Slutpunktstype|GCC|GCC High & DoD|
|---|---|---|
|Logon|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Defender til Endpoint API|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>Funktionsparitet med kommerciel

Defender for Endpoint for kunder i den amerikanske stat har ikke fuldstændig paritet med det kommercielle tilbud. Vores mål er at levere alle kommercielle funktioner og funktionalitet til vores kunder i det amerikanske offentlige, men der er visse funktioner, som endnu ikke er tilgængelige, som vi gerne vil fremhæve.

Disse er de kendte mellemrum:

<br />

****

|Funktionsnavn|GCC|GCC høj|DoD|
|---|:---:|:---:|:---:|
|Netværksvurderinger|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
|Netværksregistrering|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Rapporter: Enhedshåndtering, Enhedstilstand, Firewall|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
|Filtrering af webindhold|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
  

Disse er de funktioner og kendte mellemrum for [Mobile Threat Defense (Microsoft Defender til Slutpunkt på Android & iOS)](mtd.md):

<br />

****

|Funktionsnavn|GCC|GCC høj|DoD|
|---|:---:|:---:|:---:|
|Webbeskyttelse (antiphishing og brugerdefinerede indikatorer)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Malwarebeskyttelse (kun Android)|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
|Jailbreak-registrering (kun iOS)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Betinget adgang/betinget start|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Understøttelse af MAM|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Kontrolelementer til beskyttelse af personlige oplysninger|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Administration af trusler og sikkerhedsrisiko (TVM)|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
|Filtrering af webindhold|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
  

