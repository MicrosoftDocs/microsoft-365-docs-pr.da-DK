---
title: Administrer Microsoft Defender for Endpoint ved hjælp af Intune
description: Få mere at vide om, hvordan du administrerer Microsoft Defender til slutpunkt med Intune
keywords: efter overførslen, administrere, handlinger, vedligeholdelse, udnyttelse, intune, Microsoft Defender til slutpunkt, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 290d98f3f4136cfd07b5ea5abc21988ac8d9867a
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63594096"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Administrer Microsoft Defender til slutpunkt med Intune

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Vi anbefaler at [Microsoft Endpoint Manager](/mem), som omfatter Microsoft Intune (Intune), til at administrere organisationens funktioner til trusselsbeskyttelse på enheder (også kaldet slutpunkter). [Få mere at vide Endpoint Manager](/mem/endpoint-manager-overview).

I denne artikel beskrives det, hvordan du finder dine Microsoft Defender for Endpoint-indstillinger i Intune, og en liste over forskellige opgaver, du kan udføre.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Find dine Microsoft Defender for Endpoint-indstillinger i Intune

> [!IMPORTANT]
> Du skal have enten den globale administrator- eller tjenesteadministratorrolle tildelt i Intune for at konfigurere de indstillinger, der er beskrevet i denne artikel. Du kan få mere at vide **[under Administratortyper (Intune)](/mem/intune/fundamentals/users-add#types-of-administrators)**.

1. Gå til Azure-portalen ([https://portal.azure.com](https://portal.azure.com)), og log på.

2. Under **Azure Services** skal du **vælge Intune**.

3. Vælg Enhedskonfiguration i navigationsruden **til venstre**, og vælg derefter **Profiler** under **Administrer**.

4. Vælg en eksisterende profil, eller opret en ny.

> [!TIP]
> Har du brug for hjælp? Se **[Brug af Microsoft Defender til slutpunkt med Intune](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Konfigurer Microsoft Defender til slutpunkt med Intune

I følgende tabel vises forskellige opgaver, du kan udføre for at konfigurere Microsoft Defender til slutpunkt med Intune. Du behøver ikke at konfigurere alt på én gang; skal du vælge en opgave, læse de tilsvarende ressourcer og derefter fortsætte.

<br/><br/>

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Administrer din organisations enheder ved hjælp af Intune for at** beskytte disse enheder og data, der er gemt på dem|[Beskyt enheder med Microsoft Intune](/mem/intune/protect/device-protect)|
|**Integrer Microsoft Defender til slutpunkt med Intune som** en Mobile Threat Defense-løsning <br/>*(for Android-enheder og enheder, der Windows 10 eller Windows 11)*|[Gennemtving overholdelse af regler og standarder for Microsoft Defender til slutpunkt med Betinget adgang i Intune](/mem/intune/protect/advanced-threat-protection)|
|**Brug Betinget adgang til** at styre de enheder og apps, der kan oprette forbindelse til din mail og virksomhedens ressourcer|[Konfigurer Betinget adgang i Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**Konfigurere Microsoft Defender Antivirus ved hjælp** af politikkonfigurationen serviceudbyder ([CSP for politik](/windows/client-management/mdm/policy-configuration-service-provider))|[Enhedsbegrænsninger: Microsoft Defender Antivirus](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [CSP for politik – Microsoft Defender til slutpunkt](/windows/client-management/mdm/policy-csp-defender)|
|**Angiv om nødvendigt udeladelse for Microsoft Defender Antivirus** <br/><br/> *Generelt skal du ikke anvende udeladelse. Microsoft Defender Antivirus indeholder en række automatiske udeladelsesforanstaltninger, der er baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler, f.eks. dem, der bruges i virksomhedsadministration, databaseadministration og andre virksomhedsscenarier.*|[Anbefalinger til virusscanning for virksomhedscomputere, der kører aktuelt understøttede versioner af Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [Enhedsbegrænsninger: Microsoft Defender Antivirus for Windows 10 og Windows 11 enheder](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [Konfigurere Microsoft Defender Antivirus udeladelse på Windows Server 2016 eller 2019 eller 2022](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Konfigurer dine regler for reduktion af angrebsoverfladen** for at målrette softwareadfærd, der ofte misbruges af hackere <br/><br/> *Konfigurer dine regler for reduktion af [angrebsoverfladen i](/microsoft-365/security/defender-endpoint/audit-windows-defender) overvågningstilstand i starten (i mindst en uge og op til to måneder). Du kan overvåge status ved Power BI ([få vist vores skabelon](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules)), og derefter angive disse regler til aktiv tilstand, når du er klar.*|[Overvågningstilstand i Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [Slutpunktsbeskyttelse: Reduktion af angrebsoverfladen](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [Få mere at vide om regler for reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [Tech Community-blogindlæg: Afmystificere regler for reduktion af angrebsoverfladen - Del 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**Konfigurer din netværksfiltrering for** at blokere udgående forbindelser fra enhver app til IP-adresser eller domæner med dårligt ry  <br/><br/> *Netværksfiltrering kaldes også [netværksbeskyttelse](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *Sørg for, Windows 10 og Windows 11-enheder har de nyeste [opdateringer til antimalwareplatformen](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) installeret.*|[Endpoint-beskyttelse: Netværksfiltrering](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [Gennemse netværksbeskyttelseshændelser i Windows Event Viewer](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**Konfigurer styret mappeadgang for** at beskytte mod ransomware <br/><br/> *[Kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders) kaldes også antiransomwarebeskyttelse.*|[Slutpunktsbeskyttelse: Styret mappeadgang](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Aktivér styret mappeadgang i Intune](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**Konfigurere udnyttelse af** beskyttelse for at beskytte din organisations enheder mod malware, der bruger udnyttelse til at sprede og inficere andre enheder <br/><br/> *[Exploit Protection](/microsoft-365/security/defender-endpoint/exploit-protection) kaldes også for Exploit Guard.*|[Slutpunktsbeskyttelse: Microsoft Defender Exploit Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [Aktivér udnyttelse af beskyttelse i Intune](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**Konfigurer Microsoft Defender SmartScreen** at beskytte mod skadelige websteder og filer på internettet. <br/><br/> *Microsoft Edge skal være installeret på din organisations enheder. For at beskytte Google Chrome- og FireFox-browsere skal du konfigurere exploit protection.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [Enhedsbegrænsninger: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [Politikindstillinger til administration af SmartScreen i Intune](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**Konfigurer Microsoft Defender Firewall** til at blokere uautoriseret netværkstrafik, der flyder ind eller ud af organisationens enheder|[Endpoint-beskyttelse: Microsoft Defender Firewall](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Microsoft Defender Firewall med Avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**Konfigurer kryptering og BitLocker** til at beskytte oplysninger på organisationens enheder, der kører Windows|[Slutpunktsbeskyttelse: Windows kryptering](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [BitLocker til Windows 10 og Windows 11 enheder](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**Konfigurer Microsoft Defender Credential Guard for at beskytte** dig mod angreb med legitimationstyveri|Du Windows 10 du Windows 11, Windows Server 2016 og Windows Server 2019 og Windows Server 2022 under [Slutpunktsbeskyttelse: Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> For Windows 7 SP1 skal du Windows Server 2008 R2 SP1, Windows 8.1 og Windows Server 2012 R2 i Formning af [PtH-angreb (Pass-the-Hash)](https://www.microsoft.com/download/details.aspx?id=36036) og andre tyveri af legitimationsoplysninger, version 1 og 2|
|**Konfigurer Microsoft Defender Application Control for** at vælge, om du vil overvåge eller have tillid til apps på din organisations enheder <br/><br/> *Microsoft Defender Application Control kaldes også [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[Installér Microsoft Defender Application Control-politikker ved hjælp af Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [Endpoint protection: Microsoft Defender Application Control](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker CSP](/windows/client-management/mdm/applocker-csp)|
|**Konfigurer enhedsstyring og adgang til USB-enheder** for at forhindre trusler i uautoriserede eksterne enheder i at gå på kompromis med dine enheder|[Styr USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender til slutpunkt og Intune](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurere din Microsoft 365 Defender portal

Hvis du ikke allerede har gjort det, skal du konfigurere din Microsoft 365 Defender-portal for at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om organisationens overordnede sikkerhedslag. Se [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Du kan også konfigurere, om og hvilke funktioner slutbrugere kan se i Microsoft 365 Defender portal.

- [Oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Slutpunktsbeskyttelse: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Gå til Microsoft 365 Defender portalsikkerhedsdashboard](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
