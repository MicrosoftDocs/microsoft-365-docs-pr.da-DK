---
title: Microsoft Defender til Slutpunkt
description: Microsoft Defender til Slutpunkt er en virksomheds slutpunktssikkerhedsplatform, der hjælper med at beskytte dig mod avancerede permanente trusler.
keywords: Introduktion til Microsoft Defender til slutpunkt, introduktion til Microsoft Defender til slutpunkt, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, maskinfunktionssensor, skysikkerhed, analyse, trusselsintelligens, reduktion af angrebsoverfladen, reduktion af angrebsoverfladen, automatisk undersøgelse og afhjælpning, microsoft-trusselseksperter, sikker score, avanceret jagt, Microsoft 365 Defender, cybertrusler på jagt
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
ms.openlocfilehash: c4308c203093d2170cc1a6316db824ee9935363f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591935"
---
# <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender til Slutpunkt er en sikkerhedsplatform til virksomheder, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler.

> [!TIP]
> Microsoft Defender til slutpunkt bliver snart tilgængelig i to planer. I denne artikel beskrives de funktioner og funktioner, der er inkluderet i Microsoft Defender til Slutpunktsplan 2. [Få mere at vide om Microsoft Defender for Endpoint Plan 1 og Plan 2](defender-endpoint-plan-1-2.md).
> 

<p><p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

Defender til Slutpunkt bruger følgende kombination af teknologi, der er indbygget Windows 10 Microsofts robuste skytjeneste:

- **Slutpunktsfunktionsmådesensorer**: Disse sensorer, der er integreret i Windows 10, indsamler og behandler adfærdssignaler fra operativsystemet og sender disse sensordata til din private, isolerede, skybaserede forekomst af Microsoft Defender til slutpunkt.

- **Sikkerhedsanalyse** i skyen: Udnyttelse af big-data, enhedslæring og unik Microsoft-optik på tværs af Windows-økosystemet, virksomhedsskyprodukter (f.eks Office 365) og onlineaktiver, adfærdsbaserede signaler omsættes til indsigt, registreringer og anbefalede svar på avancerede trusler.

- Trusselsintelligens: Genereret af Microsoft-gerningsfolk, sikkerhedsteams og udvidet af trusselsintelligens fra partnere, gør Threat Intelligence det muligt for Defender for Endpoint at identificere hackerværktøjer, teknikker og procedurer og generere beskeder, når de observeres i indsamlede sensordata.

<center><h2>Microsoft Defender til Slutpunkt</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="Threat & Vulnerability Management"> <br><b>Administration af & af sikkerhedssikkerhedsrisiko</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>Reduktion af angrebsoverfladen</b></center></a></td>
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
>
> - Få mere at vide om de nyeste forbedringer i Defender til Slutpunkt: [Nyheder i Microsoft Defender til slutpunkt](whats-new-in-microsoft-defender-endpoint.md).
> - Microsoft Defender til slutpunkt demonstrerede brancheførende optik og registreringsfunktioner i den seneste MITRE-evaluering. Læs: [Insights fra den MITRE ATT&CK-baserede evaluering](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

<a name="tvm"></a>

**[Administration af & af sikkerhedssikkerhedsrisiko](next-gen-threat-and-vuln-mgt.md)**

Denne indbyggede funktion bruger en risikobaseret tilgang til registrering, prioritering og afhjælpning af slutpunktsrisici og forkert konfigurationer.

<a name="asr"></a>

**[Reduktion af angrebsoverfladen](overview-attack-surface-reduction.md)**

Reduktionssættet af angrebsoverfladen er den første forsvarslinje i stablen. Ved at sikre, at konfigurationsindstillingerne er korrekt indstillet, og udnytte afhjælpningsteknikker anvendes, kan funktionerne modstå angreb og udnyttelse. Dette sæt funktioner omfatter [også netværksbeskyttelse](network-protection.md) og [webbeskyttelse](web-protection-overview.md), som regulerer adgangen til skadelige IP-adresser, domæner og URL-adresser.

<a name="ngp"></a>

**[Næste generations beskyttelse](next-generation-protection.md)**

For yderligere at styrke dit netværks sikkerhedsperimeter bruger Microsoft Defender til Slutpunkt næste generations beskyttelse, der er udviklet til at fange alle typer af nye trusler.

<a name="edr"></a>

**[Registrering af slutpunkt og svar](overview-endpoint-detection-response.md)**

Slutpunktsregistrering og svarfunktioner er blevet indsat for at registrere, undersøge og reagere på avancerede trusler, der kan have fået det forbi de første to sikkerhedssøjler. [Avanceret jagt](advanced-hunting-overview.md) giver et forespørgselsbaseret værktøj til trusselssporing, der proaktivt lader dig finde brud og oprette brugerdefinerede registreringer.

<a name="ai"></a>

**[Automatiseret undersøgelse og afhjælpning](automated-investigations.md)**

Sammen med at kunne reagere hurtigt på avancerede angreb tilbyder Microsoft Defender til slutpunkt automatisk undersøgelse og afhjælpning, som er med til at reducere mængden af beskeder i minutter på skala.

<a name="ss"></a>

**[Microsoft Secure Score til enheder](tvm-microsoft-secure-score-devices.md)**

Defender til Slutpunkt omfatter Microsoft Secure Score for Enheder, som kan hjælpe dig med dynamisk at vurdere sikkerhedstilstanden for dit virksomhedsnetværk, identificere ubeskyttede systemer og udføre anbefalede handlinger for at forbedre organisationens overordnede sikkerhed.

<a name="mte"></a>

**[Microsoft-trusselseksperter](microsoft-threat-experts.md)**

Microsoft Defender til Slutpunkts nye administrerede trussels-jagttjeneste leverer proaktiv jagt, prioritering og yderligere kontekst og viden, der yderligere giver Security Operation Centers (SOCs) mulighed for at identificere og reagere på trusler hurtigt og præcist.

> [!IMPORTANT]
> Defender til Endpoint-kunder skal ansøge om den Microsoft-trusselseksperter-administrerede trusselssøgningstjeneste for at få proaktive målrettede angrebsmeddelelser og samarbejde med eksperter efter behov. Eksperter efter behov er en tilføjelsestjeneste. Målrettede angrebsmeddelelser er altid inkluderet, når du er blevet accepteret til Microsoft-trusselseksperter trusselshundetjeneste.
>
> Hvis du endnu ikke er tilmeldt og gerne vil opleve fordelene ved den, kan du gå til **Indstillinger** \> **Generelle** \>  \> avancerede funktioner **Microsoft-trusselseksperter** at anvende. Når de er accepteret, får du fordelene ved Målrettede angrebsmeddelelser og starter en 90-dages prøveversion af Experts On Demand. Kontakt din Microsoft-repræsentant for at få et fuldt Ekspert on Demand-abonnement.

<a name="apis"></a>

**[Centraliseret konfiguration og administration, API'er](management-apis.md)**

Integrer Microsoft Defender til slutpunkt i dine eksisterende arbejdsprocesser.

<a name="mtp"></a>

**[Integration med Microsoft-løsninger](threat-protection-integration.md)**

Defender til Slutpunkt integreres direkte med forskellige Microsoft-løsninger, herunder:

- Microsoft Defender til skyen
- Microsoft Sentinel
- Intune
- Microsoft Defender til skyapps
- Microsoft Defender for Identity
- Microsoft Defender til Office
- Skype for Business

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

Med Microsoft 365 Defender udgør Defender til slutpunkt og forskellige Microsoft-sikkerhedsløsninger en samlet virksomhedsforbeholdspakke, der indbygget integreres på tværs af slutpunkt, identitet, mail og programmer for at registrere, forhindre, undersøge og automatisk reagere på avancerede angreb.


## <a name="training-for-security-analysts"></a>Kurser til sikkerhedsanalytikere

Med denne læringssti fra Microsoft Learn kan du forstå Defender til slutpunkt, og hvordan det kan hjælpe med at forhindre, registrere, undersøge og reagere på trusler på tværs af organisationens slutpunkter – dine enheder og systemer.

|Kursus:|Find og svar på cyberangreb med Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender kursusikon.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Defender til Slutpunkt er en sikkerhedsløsning for slutpunkter, der tilbyder håndtering af sikkerhedsrisici, slutpunktsbeskyttelse, slutpunktsregistrering og -svar, mobil trusselsbeskyttelse og administrerede tjenester på en enkelt, samlet platform.<p> 2 timer 25 min - Learning Sti - 9 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/paths/defender-endpoint-fundamentals/)
