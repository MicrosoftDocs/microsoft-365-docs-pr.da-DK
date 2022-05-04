---
title: Microsoft Defender for Endpoint for US Government-kunder
description: Få mere at vide om de Microsoft Defender for Endpoint til US Government-kunders krav og funktioner, der er tilgængelige
keywords: government, gcc, high, requirements,capabilities, defender, Microsoft Defender for Endpoint, endpoint, dod
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
ms.openlocfilehash: a27cb75a9bace821e20a914bc3c63b571079f9db
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188410"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender for Endpoint for US Government-kunder

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Microsoft Defender for Endpoint til US Government-kunder, der er bygget i Azure US Government-miljøet, bruger de samme underliggende teknologier som Defender for Endpoint i Azure Commercial.

Dette tilbud er tilgængeligt for kunder med GCC, GCC High og DoD og er baseret på den samme forebyggelse, registrering, undersøgelse og afhjælpning som den kommercielle version. Der er dog nogle forskelle i tilgængeligheden af egenskaber for dette tilbud.

> [!NOTE]
> Hvis du er GCC kunde, der bruger Defender for Endpoint i Commercial, skal du se de offentlige dokumentationssider.

## <a name="licensing-requirements"></a>Licenskrav

Microsoft Defender for Endpoint til US Government-kunder kræver et af følgende Microsoft-volumenlicenstilbud:

### <a name="desktop-licensing"></a>Skrivebordslicenser

<br />

****

|GCC|GCC Høj|Dod|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 for GCC High|Microsoft 365 G5 for DOD|
|GCC Microsoft 365 G5 Security|Microsoft 365 G5 Security for GCC High|Microsoft 365 G5 Sikkerhed for DOD|
|Microsoft Defender for Endpoint - GCC|Microsoft Defender for Endpoint for GCC High|Microsoft Defender for Endpoint for DOD|
|Windows 10 Enterprise E5 GCC|Windows 10 Enterprise E5 for GCC High|Windows 10 Enterprise E5 for DOD|
|

### <a name="server-licensing"></a>Serverlicensering

<br />

****

|GCC|GCC Høj|Dod|
|---|---|---|
|GCC Microsoft Defender for Endpoint Server|Microsoft Defender for Endpoint Server til høj GCC|Microsoft Defender for Endpoint Server til DOD|
|Microsoft Defender til servere|Microsoft Defender for servers – Government|Microsoft Defender for servers – Government|
|

## <a name="portal-urls"></a>PORTAL-URL-adresser

Følgende er URL-adresserne på Microsoft Defender for Endpoint-portalen for US Government-kunder:

<br />

****

|Kundetype|URL-adresse til portal|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC Høj|<https://security.microsoft.us>|
|Dod|<https://security.apps.mil>|
|
> [!NOTE]
> Hvis du er GCC kunde og er ved at flytte fra Microsoft Defender for Endpoint kommerciel til GCC, kan du bruge https://transition.security.microsoft.com til at få adgang til dine Microsoft Defender for Endpoint kommercielle data.

## <a name="endpoint-versions"></a>Slutpunktsversioner

### <a name="standalone-os-versions"></a>Separate operativsystemversioner

Følgende operativsystemversioner understøttes:

<br />

****

Operativsystemversion|GCC|GCC Høj|Dod
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
Windows 7 SP1 Enterprise (legacy) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows 7 SP1 Pro (ældre) <sup>3</sup>|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Linux|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Macos|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Android|![Ja.](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion
Ios|![Ja.](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion|![Ja](images/svg/check-yes.svg) <br /> Offentlig prøveversion
|

> [!NOTE]
> <sup>1</sup> Programrettelsen skal installeres, før enheden onboardes, for at Defender for Endpoint kan konfigureres til det korrekte miljø.
>
> <sup>2</sup> Få mere at vide om den [samlede moderne løsning til Windows 2016 og 2012 R2](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution). Hvis du tidligere har onboardet dine servere ved hjælp af MMA, skal du følge vejledningen i [Serveroverførsel](server-migration.md) for at migrere til den nye løsning.
>
> <sup>3</sup> Når du bruger [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) , skal du vælge "Azure US Government" under "Azure Cloud", hvis du bruger [installationsguiden](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard), eller hvis du bruger en [kommandolinje](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) eller et [script](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) – angiv parameteren "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" til 1. <br /> Den mindste MMA-understøttede version er 10.20.18029 (marts 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>OS-versioner, når Microsoft Defender bruges til servere

Følgende operativsystemversioner understøttes, når [du bruger Microsoft Defender til servere](/azure/security-center/security-center-wdatp):

<br />

****

Operativsystemversion|GCC|GCC Høj|Dod
:---|:---:|:---:|:---:
Windows Server 2022|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2019|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2016|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2012 R2|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![Ja.](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>Påkrævede forbindelsesindstillinger

Hvis en proxy eller firewall blokerer al trafik som standard og kun tillader bestemte domæner via, skal du føje de domæner, der er angivet i arket, der kan downloades, til listen over tilladte domæner.

Følgende regneark, der kan downloades, viser tjenesterne og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Kontrollér, at der ikke er nogen firewall- eller netværksfiltreringsregler, der nægter adgang til disse URL-adresser, eller opret en *regel for tilladelse* , der er specifik for dem.

|Regneark med domæneliste| Beskrivelse|
|---|---|
|Microsoft Defender for Endpoint URL-adresseliste til kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OPERATIVSYSTEM til kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender for Endpoint URL-adresseliste for Gov/GCC/DoD | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Du kan få mere at vide under [Konfigurer indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md).

> [!NOTE]
> Regnearket indeholder også kommercielle URL-adresser. Kontrollér fanerne "US Gov".
>
> Når du filtrerer, skal du søge efter de poster, der er mærket som "US Gov" og din specifikke cloud under kolonnen geografi.

## <a name="api"></a>API

I stedet for de offentlige URI'er, der er angivet i vores [API-dokumentation](apis-intro.md), skal du bruge følgende URI'er:

<br />

****

|Slutpunktstype|GCC|GCC-dod med høj &|
|---|---|---|
|Login|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Defender for Endpoint API|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM REAP|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>Funktionsparitet med kommerciel

Defender for Endpoint for US Government-kunder har ikke fuldstændig paritet med det kommercielle tilbud. Selvom vores mål er at levere alle kommercielle funktioner og funktionalitet til vores us government-kunder, er der nogle funktioner, som vi endnu ikke vil fremhæve.

Dette er de kendte huller:

<br />

****

|Funktionsnavn|GCC|GCC Høj|Dod|
|---|:---:|:---:|:---:|
|Netværksvurderinger|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
|Netværksregistrering|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Rapporter: Enhedskontrol, Enhedstilstand, Firewall|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
|Filtrering af webindhold|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
  

Disse er de funktioner og kendte huller i [Mobile Threat Defense (Microsoft Defender for Endpoint på Android & iOS)](mtd.md):

<br />

****

|Funktionsnavn|GCC|GCC Høj|Dod|
|---|:---:|:---:|:---:|
|Webbeskyttelse (anti-phishing og brugerdefinerede indikatorer)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Beskyttelse mod skadelig software (kun Android)|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|![Nej](images/svg/check-no.svg) Under udvikling|
|Registrering af jailbreak (kun iOS)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Betinget adgang/betinget start|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Understøttelse af MAM|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Kontrolelementer til beskyttelse af personlige oplysninger|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
|Trussels- og sårbarhedsstyring (TVM)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|![Ja](images/svg/check-yes.svg)|
  

