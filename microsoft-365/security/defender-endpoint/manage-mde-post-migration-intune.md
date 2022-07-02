---
title: Administrer Microsoft Defender for Endpoint ved hjælp af Intune
description: Få mere at vide om, hvordan du administrerer Microsoft Defender for Endpoint med Intune
keywords: efter migrering, administration, drift, vedligeholdelse, udnyttelse, intune, Microsoft Defender for Endpoint, kant
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
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: 1cbaff007a5ef2839cbcf51babc7a057c7b756c0
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607449"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Administrer Microsoft Defender for Endpoint med Intune

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem), som omfatter Microsoft Intune (Intune) til at administrere organisationens trusselsbeskyttelsesfunktioner for enheder (også kaldet slutpunkter). [Få mere at vide om Endpoint Manager](/mem/endpoint-manager-overview).

I denne artikel beskrives det, hvordan du finder dine indstillinger for Microsoft Defender for Endpoint i Intune og viser forskellige opgaver, du kan udføre.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Find dine indstillinger for Microsoft Defender for Endpoint i Intune

> [!IMPORTANT]
> Du skal enten have tildelt rollen global administrator eller tjenesteadministrator i Intune for at kunne konfigurere de indstillinger, der er beskrevet i denne artikel. Du kan få mere at vide under **[Typer af administratorer (Intune)](/mem/intune/fundamentals/users-add#types-of-administrators)**.

1. Gå til Azure Portal ([https://portal.azure.com](https://portal.azure.com)), og log på.

2. Vælg **Intune** under **Azure Services**.

3. Vælg **Enhedskonfiguration** i navigationsruden til venstre, og vælg derefter **Profiler** under **Administrer**.

4. Vælg en eksisterende profil, eller opret en ny.

> [!TIP]
> Har du brug for hjælp? Se **[Brug af Microsoft Defender for Endpoint med Intune](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Konfigurer Microsoft Defender for Endpoint med Intune

I følgende tabel vises en liste over forskellige opgaver, du kan udføre for at konfigurere Microsoft Defender for Endpoint med Intune. Du behøver ikke at konfigurere alt på én gang. vælg en opgave, læs de tilsvarende ressourcer, og fortsæt derefter.

|Opgave|Ressourcer til at få mere at vide|
|---|---|
|**Administrer din organisations enheder ved hjælp af Intune** til at beskytte de enheder og data, der er gemt på dem|[Beskyt enheder med Microsoft Intune](/mem/intune/protect/device-protect)|
|**Integrer Microsoft Defender for Endpoint med Intune** som en Mobile Threat Defense-løsning <br/>*(til Android-enheder og -enheder, der kører Windows 10 eller Windows 11)*|[Gennemtving overholdelse af Microsoft Defender for Endpoint med betinget adgang i Intune](/mem/intune/protect/advanced-threat-protection)|
|**Brug Betinget adgang** til at styre de enheder og apps, der kan oprette forbindelse til dine mail- og virksomhedsressourcer|[Konfigurer betinget adgang i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**Konfigurer indstillingerne for Microsoft Defender Antivirus** ved hjælp af udbyderen af politikkonfigurationstjeneste ([Politik-CSP](/windows/client-management/mdm/policy-configuration-service-provider))|[Enhedsbegrænsninger: Microsoft Defender Antivirus](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [Politik-CSP – Microsoft Defender for Endpoint](/windows/client-management/mdm/policy-csp-defender)|
|**Hvis det er nødvendigt, skal du angive undtagelser for Microsoft Defender Antivirus** <br/><br/> *Generelt skal du ikke anvende undtagelser. Microsoft Defender Antivirus indeholder en række automatiske undtagelser baseret på kendte funktionsmåder i operativsystemet og typiske administrationsfiler, f.eks. dem, der bruges i virksomhedsadministration, databaseadministration og andre virksomhedsscenarier.*|[Anbefalinger til virusscanning for Enterprise-computere, der kører aktuelt understøttede versioner af Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [Enhedsbegrænsninger: Microsoft Defender Antivirus Exclusions for Windows 10 og Windows 11 enheder](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [Konfigurer Microsoft Defender Antivirus-undtagelser på Windows Server 2016 eller 2019 eller 2022](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Konfigurer dine regler for reduktion af angrebsoverfladen** for at målrette softwarefunktioner, der ofte misbruges af hackere <br/><br/> *Konfigurer dine regler for reduktion af angrebsoverfladen i [overvågningstilstand](/microsoft-365/security/defender-endpoint/audit-windows-defender) i første omgang (i mindst én uge og op til to måneder). Du kan overvåge status ved hjælp af Power BI ([hent vores skabelon](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules)) og derefter angive disse regler til aktiv tilstand, når du er klar.*|[Overvågningstilstand i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [Beskyttelse af slutpunkter: Reduktion af angrebsoverflade](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [Få mere at vide om regler for reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [Tech Community-blogindlæg: Afmystificerende regler for reduktion af angrebsoverfladen – del 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**Konfigurer netværksfiltrering** for at blokere udgående forbindelser fra en hvilken som helst app til IP-adresser eller domæner med lavt omdømme  <br/><br/> *Netværksfiltrering kaldes også [netværksbeskyttelse](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *Sørg for, at Windows 10 og Windows 11 enheder har de nyeste [opdateringer til antimalwareplatforme](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) installeret.*|[Beskyttelse af slutpunkter: Netværksfiltrering](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [Gennemse netværksbeskyttelseshændelser i Windows Logbog](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**Konfigurer kontrolleret mappeadgang** for at beskytte mod ransomware <br/><br/> *[Kontrolleret mappeadgang](/microsoft-365/security/defender-endpoint/controlled-folders) kaldes også antiransomware-beskyttelse.*|[Endpoint Protection: Adgang til styrede mapper](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Aktivér kontrolleret mappeadgang i Intune](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**Konfigurer beskyttelse mod udnyttelse** for at beskytte din organisations enheder mod malware, der bruger udnyttelser til at sprede og inficere andre enheder <br/><br/> *[Udnyttelsesbeskyttelse](/microsoft-365/security/defender-endpoint/exploit-protection) kaldes også Exploit Guard.*|[Beskyttelse af slutpunkter: Microsoft Defender Exploit Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [Aktivér beskyttelse mod udnyttelse i Intune](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**Konfigurer Microsoft Defender SmartScreen** for at beskytte mod skadelige websteder og filer på internettet. <br/><br/> *Microsoft Edge skal installeres på din organisations enheder. Hvis du vil have beskyttelse i Google Chrome- og FireFox-browsere, skal du konfigurere beskyttelse mod udnyttelse.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [Enhedsbegrænsninger: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [Politikindstillinger for administration af SmartScreen i Intune](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**Konfigurer Microsoft Defender Firewall** til at blokere uautoriseret netværkstrafik, der strømmer ind eller ud af organisationens enheder|[Beskyttelse af slutpunkter: Microsoft Defender Firewall](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Microsoft Defender Firewall med avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**Konfigurer kryptering og BitLocker** for at beskytte oplysninger på din organisations enheder, der kører Windows|[Slutpunktsbeskyttelse: Windows-kryptering](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [BitLocker til Windows 10 og Windows 11 enheder](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**Konfigurer Microsoft Defender Credential Guard** for at beskytte mod angreb mod tyveri af legitimationsoplysninger|Du kan finde Windows 10, Windows 11, Windows Server 2016 og Windows Server 2019 og Windows Server 2022 under [Endpoint Protection: Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> I forbindelse med Windows 7 SP1, Windows Server 2008 R2 SP1, Windows 8.1 og Windows Server 2012 R2 skal du se [Formildende pass-the-Hash-angreb (PtH) og andre tyverier af legitimationsoplysninger, version 1 og 2](https://www.microsoft.com/download/details.aspx?id=36036)|
|**Konfigurer Microsoft Defender Application Control** for at vælge, om du vil overvåge eller have tillid til apps på din organisations enheder <br/><br/> *Microsoft Defender Application Control kaldes også [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[Installer Microsoft Defender Application Control-politikker ved hjælp af Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [Endpoint protection: Microsoft Defender Application Control](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker-CSP](/windows/client-management/mdm/applocker-csp)|
|**Konfigurer enhedsstyring og adgang til eksterne USB-enheder** for at forhindre, at trusler i uautoriserede eksterne enheder kompromitterer dine enheder|[Styr USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender for Endpoint og Intune](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Konfigurer Microsoft 365 Defender-portalen

Hvis du ikke allerede har gjort det, kan du konfigurere din Microsoft 365 Defender-portal til at få vist beskeder, konfigurere funktioner til trusselsbeskyttelse og få vist detaljerede oplysninger om din organisations overordnede sikkerhedsholdning. Se [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Du kan også konfigurere, om og hvilke funktioner slutbrugerne kan se på portalen Microsoft 365 Defender.

- [Oversigt over Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Beskyttelse af slutpunkter: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Næste trin

- [Få et overblik over Håndtering af trusler og sikkerhedsrisici](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Besøg dashboardet til Microsoft 365 Defender-portalens sikkerhedshandlinger](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
