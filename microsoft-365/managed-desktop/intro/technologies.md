---
title: Microsoft Managed Desktop teknologier
description: Denne artikel indeholder en liste over de teknologier og apps, der bruges i Microsoft Managed Desktop.
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: d7a7b6889451d83aaa6c2b53c1dce6ed035f9916
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945621"
---
# <a name="microsoft-managed-desktop-technologies"></a>Microsoft Managed Desktop teknologier

Denne artikel indeholder en liste over de teknologier og apps, der bruges i Microsoft Managed Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Enterprise licenser er påkrævet for alle Microsoft Managed Desktop brugere. Du kan få flere oplysninger om licenskrav til tjenesten under [Forudsætninger for Microsoft Managed Desktop](../get-ready/prerequisites.md).

I denne artikel opsummeres de komponenter, der er inkluderet i de påkrævede Enterprise-licenser, og hvordan tjenesten bruger hver komponent med Microsoft Managed Desktop enheder. Specifikke roller og ansvarsområder for hvert område beskrives i hele Microsoft Managed Desktop dokumentation.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 eller E5

| Produkt | Oplysninger |
| ----- | ----- |
| Microsoft 365 Apps for enterprise (64-bit) | Følgende Office programmer leveres sammen med enheden:<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Publisher</li><li>Access</li><li>Skype for Business</li><li>OneNote</li></ul><br>De 64-bit fulde versioner af Microsoft Project og Microsoft Visio er ikke inkluderet. Men da installationen af disse programmer afhænger af Microsoft 365 Apps til Enterprise-installationen, Microsoft Managed Desktop oprettet standardinstallationer Microsoft Intune og sikkerhedsgrupper, som du kan bruge til at installere disse programmer til brugere med licens. Du kan få flere oplysninger under [Installér Microsoft Project eller Microsoft Visio på Microsoft Managed Desktop enheder](../get-started/project-visio.md). |
| OneDrive | Azure Active Directory enkeltlogon er aktiveret for brugerne, første gang de logger på OneDrive.<br><br>Kendte mappeomdirigeringer for mapperne Desktop, Document og Pictures er inkluderet. Disse mapper aktiveres og konfigureres af Microsoft Managed Desktop. |
| Store apps | Microsoft Sway og Power BI leveres ikke med enheden. Disse apps kan downloades fra Microsoft Store. |
| Win32-programmer | Teams leveres ikke sammen med enheden, men leveres og leveres af Microsoft til Microsoft Managed Desktop enheder. Azure Information Protection Client leveres ikke sammen med enheden, men du kan få den pakket til installation. |
| Webprogrammer | Følgende webprogrammer leveres ikke sammen med enheden: <ul><li>Yammer</li><li>Office i en browser</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>Power Apps</li><li>Planner</li></ul> <br>Brugerne kan få adgang til webversionen af disse programmer med en browser. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Enterprise E5 eller E3 med Microsoft Defender for Endpoint

Vi anbefaler, at it-administratorer konfigurerer følgende indstillinger.

> [!NOTE]
> Disse indstillinger er ikke inkluderet eller administreret som en del af Microsoft Managed Desktop.

| Produkt | Oplysninger |
| ----- | ----- |
| Windows Hello til virksomheder | Du skal implementere Windows Hello til virksomheder for at erstatte adgangskoder med stærk tofaktorgodkendelse for Microsoft Managed Desktop enheder. Du kan få flere oplysninger under [Windows Hello til virksomheder](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| Application Virtualization | Du kan installere App-V-pakker (Application Virtualization) ved hjælp af Intune Win32-klient til appadministration. Du kan få flere oplysninger under [Program virtualisering](/windows/application-management/app-v/appv-technical-reference). |
| Microsoft Purview forebyggelse af datatab | Du skal implementere forebyggelse af datatab for at overvåge de handlinger, der udføres på elementer, du har besluttet dig for at være følsomme, og for at forhindre utilsigtet deling af disse elementer. Du kan få flere oplysninger under [Forebyggelse af datatab](../../compliance/endpoint-dlp-learn-about.md). |

Funktioner, der er inkluderet og administreret som en del af Microsoft Managed Desktop:

| Produkt | Oplysninger |
| ----- | ----- |
| BitLocker-drevkryptering | BitLocker-drevkryptering bruges til at kryptere alle systemdrev. Du kan få flere oplysninger under [BitLocker-drevkryptering](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| Windows Defender System Guard | Beskytter systemets integritet ved start og validerer, at systemintegritet virkelig er blevet vedligeholdt. Du kan få flere oplysninger under [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Windows Defender Credential Guard | Windows Defender Credential Guard bruger virtualiseringsbaseret sikkerhed til at isolere hemmeligheder, så det kun er privilegeret systemsoftware, der kan få adgang til dem. Du kan få flere oplysninger under [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Microsoft Defender for Endpoint – Registrering af slutpunkt og svar | Microsoft Managed Desktop Sikkerhedshandlinger reagerer på beskeder og reagerer på trusler ved hjælp af Registrering af slutpunkt og Svar. Du kan finde flere oplysninger [under Microsoft Defender for Endpoint – Registrering og svar af slutpunkter](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response). |
| Microsoft Defender for Endpoint – Trusselseksperter | Microsoft Managed Desktop integreres med Threat Experts-indsigt og -data via målrettede angrebsmeddelelser. Du skal give yderligere samtykke, før denne tjeneste aktiveres. Du kan få flere oplysninger [under Microsoft Defender for Endpoint – Trusselseksperter](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Microsoft Defender for Endpoint – administration af trusler og sårbarheder | Påkrævet til fremtidig brug i Microsoft Managed Desktop serviceplan. Du kan få flere oplysninger [under Microsoft Defender for Endpoint – Administration af trusler og sårbarheder](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Microsoft Defender for Endpoint – Reduktion af angrebsoverflade | Er målrettet risikable softwarefunktioner, der ofte misbruges af hackere. Du kan få flere oplysninger [under Microsoft Defender for Endpoint – Reduktion af angrebsoverflade](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Microsoft Defender for Endpoint - Beskyttelse mod udnyttelse | Beskytter mod malware, der bruger udnyttelse til at inficere enheder, og spredes ved automatisk at anvende teknikker til udnyttelse af operativsystemets processer og apps. Du kan få flere oplysninger [under Microsoft Defender for Endpoint – Beskyttelse mod udnyttelse](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection). |
| Microsoft Defender for Endpoint – Netværksbeskyttelse | Udvider omfanget af Microsoft Defender SmartScreen for at blokere al udgående HTTP- og HTTPS-trafik, der forsøger at oprette forbindelse til kilder med lavt omdømme. Du kan få flere oplysninger [under Microsoft Defender for Endpoint – Netværksbeskyttelse](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| Microsoft Defender Tamper Protection | Windows Tamper Protection bruges til at forhindre, at sikkerhedsindstillinger som f.eks. antivirusbeskyttelse ændres. Du kan få flere oplysninger under [Microsoft Defender Tamper Protection](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| Microsoft Defender Antivirus adfærdsbaseret, heuristisk og antivirusbeskyttelse i realtid | Altid klar til at scanne efter fil- og procestrusler, der muligvis ikke registreres som malware. Du kan få flere oplysninger [under Microsoft Defender Antivirus adfærdsbaseret, heuristisk og antivirusbeskyttelse i realtid](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md). |
| Microsoft Defender Antivirus Cloud-leveret beskyttelse | Giver dynamisk automatisk beskyttelse næsten øjeblikkelig mod nye og nye trusler. Du kan få flere oplysninger [under Microsoft Defender Antivirus Cloud-leveret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus). |
| Microsoft Defender for Endpoint - "Blok ved første øjekast" | Leverer registrering og blokering af ny malware, når Windows registrerer en mistænkelig eller ukendt fil. Du kan få flere oplysninger [under Microsoft Defender for Endpoint – Blok ved første øjekast](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| Microsoft Defender Antivirus potentielt uønskede programmer | Bruges til at blokere apps, der kan få din maskine til at køre langsomt, vise uventede annoncer eller i værste fald installere anden software, der kan være uventet eller uønsket. Du kan få flere oplysninger [under Microsoft Defender Antivirus potentielt uønskede programmer](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| Windows Defender Firewall med avanceret sikkerhed | Værtsbaseret, tovejsfiltrering af netværkstrafik for en enhed, Windows Defender Firewall blokerer uautoriseret netværkstrafik, der flyder ind eller ud af den lokale enhed. Du kan få flere oplysninger [under Windows Defender Firewall med avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). |
| Kontrol af brugerkonti | Brugerkontokontrol skifter til Secure Desktop, når en opgave eller handling kræver administratorkontotypeadgang. Microsoft Managed Desktop brugere tildeles Standard-brugeradgang ved tilmelding. Du kan få flere oplysninger under [Kontrol af brugerkonti](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| Produkt | Oplysninger |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory Premium P2 | Du kan bruge alle funktioner i Enterprise Mobility + Security E3 til at administrere MDM-enheder.<br><br>Du kan bruge Azure Active Directory Premium P2 som en valgfri funktion med Microsoft Managed Desktop. |
| Microsoft Defender for Cloud Apps | Du kan bruge denne valgfri funktion sammen med Microsoft Managed Desktop.
| Azure Information Protection P2  | Du kan bruge denne valgfri funktion sammen med Microsoft Managed Desktop.
