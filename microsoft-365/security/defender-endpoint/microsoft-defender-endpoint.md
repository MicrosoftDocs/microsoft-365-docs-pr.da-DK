---
title: Microsoft Defender for Endpoint
description: Microsoft Defender for Endpoint er en sikkerhedsplatform til virksomhedsslutpunkter, der hjælper med at forsvare sig mod avancerede vedvarende trusler.
keywords: introduktion til Microsoft Defender for Endpoint, introduktion til Microsoft Defender for Endpoint, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, sensor til maskinel adfærd, cloudsikkerhed, analyse, trusselsintelligens, reduktion af angrebsoverflade, næste generations beskyttelse, automatiseret undersøgelse og afhjælpning, Microsoft threat experts, secure score, advanced hunting, Microsoft 365 Defender, cyber threat hunting
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: high
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.custom: intro-overview
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 9211597ec8a0e25130b010a6049832ac151840fc
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173705"
---
# <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender for Endpoint er en sikkerhedsplatform til virksomhedsslutpunkter, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler.

> [!TIP]
> Microsoft Defender for Endpoint er tilgængelig i to planer: Defender for Endpoint Plan 1 og Plan 2. I denne artikel beskrives de funktioner og egenskaber, der er inkluderet i hver plan. [Få mere at vide om Microsoft Defender for Endpoint Plan 1 og Plan 2](defender-endpoint-plan-1-2.md).
> 

<p><p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Defender for Endpoint bruger følgende kombination af teknologi, der er indbygget i Windows 10 og Microsofts robuste cloudtjeneste:

- **Sensorer til slutpunktets adfærd: Disse sensorer**, der er integreret i Windows 10, indsamler og behandler adfærdsmæssige signaler fra operativsystemet og sender disse sensordata til din private, isolerede, cloudforekomst af Microsoft Defender for Endpoint.

- **Analyse af cloudsikkerhed**: Udnyttelse af big data, enhedslæring og unik Microsoft-optik på tværs af Windows økosystem, virksomhedscloudprodukter (f.eks. Office 365) og onlineaktiver, adfærdssignaler oversættes til indsigt, registreringer og anbefalede svar på avancerede trusler.

- **Trusselsintelligens: Trusselsintelligens**: Genereret af Microsoft-jægere, sikkerhedsteams og forstærket med trusselsintelligens leveret af partnere gør trusselsintelligens det muligt for Defender for Endpoint at identificere værktøjer, teknikker og procedurer for hackere og generere beskeder, når de observeres i indsamlede sensordata.

<center><h2>Microsoft Defender for Endpoint</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="Threat & Vulnerability Management"> <br><b>Administration af sårbarheder i forbindelse med trussel &</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Reduktion af angrebsoverflade</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>Næste generations beskyttelse</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>Registrering af slutpunkt og svar</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>Automatiseret undersøgelse og afhjælpning</b></a></center></td>
<td><center><a href="#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>Microsoft-trusselseksperter</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>Centraliseret konfiguration og administration, API'er</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

<p></p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0]

> [!TIP]
> - Få mere at vide om de seneste forbedringer i Defender for Endpoint: [Nyheder i Microsoft Defender for Endpoint](whats-new-in-microsoft-defender-endpoint.md).
> - Microsoft Defender for Endpoint demonstrerede branchens førende optik- og registreringsfunktioner i den seneste MITRE-evaluering. Læs: [Insights fra MITRE ATT&CK-baseret evaluering](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).


> [!IMPORTANT]
> Funktionerne på platforme, der ikke er Windows, kan være forskellige fra dem, der gælder for Windows. Du kan få flere oplysninger om, hvilke funktioner der er tilgængelige for platforme, der ikke er Windows, [i Microsoft Defender for Endpoint for platforme, der ikke er Windows](/microsoft-365/security/defender-endpoint/non-windows).

<a name="tvm"></a>

**[Administration af sårbarheder i forbindelse med trussel &](next-gen-threat-and-vuln-mgt.md)**

Denne indbyggede funktion bruger en spilændrende risikobaseret tilgang til registrering, prioritering og afhjælpning af sårbarheder og fejlkonfigurationer af slutpunkter.

<a name="asr"></a>

**[Reduktion af angrebsoverfladen](overview-attack-surface-reduction.md)**

Reduktionssættet for angrebsoverfladen giver den første forsvarslinje i stakken. Ved at sikre, at konfigurationsindstillinger indstilles korrekt, og at der anvendes teknikker til afhjælpning af udnyttelse, modstår funktionerne angreb og udnyttelse. Dette sæt funktioner omfatter også [netværksbeskyttelse](network-protection.md) og [webbeskyttelse](web-protection-overview.md), som regulerer adgangen til skadelige IP-adresser, domæner og URL-adresser.

<a name="ngp"></a>

**[Næste generations beskyttelse](next-generation-protection.md)**

For yderligere at styrke sikkerhedsperimeteren på dit netværk bruger Microsoft Defender for Endpoint næste generations beskyttelse, der er designet til at fange alle typer nye trusler.

<a name="edr"></a>

**[Slutpunktsregistrering og -svar](overview-endpoint-detection-response.md)**

Der er indført funktioner til registrering af slutpunkter og svar for at registrere, undersøge og reagere på avancerede trusler, der kan have gjort det forbi de første to sikkerhedssøjler. [Avanceret jagt](advanced-hunting-overview.md) indeholder et forespørgselsbaseret værktøj til trusselsjagt, der giver dig mulighed for proaktivt at finde brud og oprette brugerdefinerede opdagelser.

<a name="ai"></a>

**[Automatiseret undersøgelse og afhjælpning](automated-investigations.md)**

Sammen med at kunne reagere hurtigt på avancerede angreb tilbyder Microsoft Defender for Endpoint automatisk undersøgelses- og afhjælpningsfunktioner, der hjælper med at reducere mængden af beskeder i minutter i stor skala.

<a name="ss"></a>

**[Microsoft Secure Score til enheder](tvm-microsoft-secure-score-devices.md)**

Defender for Endpoint indeholder Microsoft Secure Score for Devices, der hjælper dig med dynamisk at vurdere sikkerhedstilstanden for dit virksomhedsnetværk, identificere ubeskyttede systemer og udføre anbefalede handlinger for at forbedre den overordnede sikkerhed i din organisation.

<a name="mte"></a>

**[Microsoft Threat Experts](microsoft-threat-experts.md)**

Microsoft Defender for Endpoint nye administrerede trusselsjagttjeneste giver proaktiv jagt, prioritering og yderligere kontekst og indsigt, der yderligere gør det muligt for SIC'er (Security Operation Centers) at identificere og reagere på trusler hurtigt og præcist.

> [!IMPORTANT]
> Defender for Endpoint-kunder skal ansøge om den Microsoft-trusselseksperter administrerede trusselsjagttjeneste for at få proaktive meddelelser om målrettede angreb og samarbejde med eksperter efter behov. Eksperter on Demand er en tilføjelsestjeneste. Målrettede angrebsmeddelelser er altid inkluderet, når du er blevet accepteret i Microsoft-trusselseksperter administreret trusselsjagttjeneste.
>
> Hvis du endnu ikke er tilmeldt og gerne vil opleve fordelene ved det, skal du gå til **Indstillinger** \> **Generelle** \> **avancerede funktioner** \> **, Microsoft-trusselseksperter** gælder. Når du har accepteret, får du fordelene ved meddelelser om målrettede angreb og starter en 90-dages prøveversion af Eksperter on Demand. Kontakt din Microsoft-repræsentant for at få et komplet Abonnement på eksperter on Demand.

<a name="apis"></a>

**[Centraliseret konfiguration og administration, API'er](management-apis.md)**

Integrer Microsoft Defender for Endpoint i dine eksisterende arbejdsprocesser.

<a name="mtp"></a>

**[Integration med Microsoft-løsninger](threat-protection-integration.md)**

Defender for Endpoint kan integreres direkte med forskellige Microsoft-løsninger, herunder:

- Microsoft Defender for Cloud
- Microsoft Sentinel
- Intune
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity
- Microsoft Defender for Office
- Skype for Business

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

Med Microsoft 365 Defender, Defender for Endpoint og forskellige Microsoft-sikkerhedsløsninger danner du en samlet virksomhedsforsvarspakke, der er integreret før og efter sikkerhedsbrud, og som oprindeligt integreres på tværs af slutpunkter, identitet, mail og programmer for at registrere, forhindre, undersøge og automatisk reagere på avancerede angreb.


## <a name="training-for-security-analysts"></a>Oplæring af sikkerhedsanalytikere

Med dette læringsforløb fra Microsoft Learn kan du forstå Defender for Endpoint, og hvordan det kan hjælpe med at forhindre, registrere, undersøge og reagere på trusler på tværs af organisationens slutpunkter – dine enheder og systemer.

|Uddannelse:|Registrer og reager på cyberangreb med Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender træningsikon.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Defender for Endpoint er en sikkerhedsløsning for slutpunkter, der tilbyder håndtering af sikkerhedsrisici, slutpunktsbeskyttelse, slutpunktsregistrering og -svar, mobiltrusselforsvar og administrerede tjenester på en enkelt samlet platform.<p> 2 t. 25 min. - Learning sti - 9 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/paths/defender-endpoint-fundamentals/)
