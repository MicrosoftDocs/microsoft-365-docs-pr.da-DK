---
title: Microsoft Managed Desktop-teknologier
description: I denne artikel vises de teknologier og apps, der bruges i Microsoft Managed Desktop.
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 302666c6b29d2cffd4db641509f14ba616cfd459
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588881"
---
# <a name="microsoft-managed-desktop-technologies"></a>Microsoft Managed Desktop-teknologier

I denne artikel vises de teknologier og apps, der bruges i Microsoft Managed Desktop.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 Enterprise licensering er påkrævet for alle brugere af Microsoft-administrerede computere. Du kan finde flere oplysninger om licenskrav til tjenesten under [Forudsætninger for Microsoft Managed Desktop](../get-ready/prerequisites.md).

Denne artikel opsummerer de komponenter, der er inkluderet i de nødvendige Enterprise-licenser, og hvordan tjenesten bruger hver komponent med Microsoft Managed Desktop-enheder. Specifikke roller og ansvarsområder for hvert område er beskrevet i dokumentationen til Microsoft-administreret skrivebord.

## <a name="office-365-e3-or-e5"></a>Office 365 E3 eller E5

| Produkt | Oplysninger |
| ----- | ----- |
| Microsoft 365 Apps for enterprise (64-bit) | Følgende Office programmer leveres sammen med enheden:<br><ul><li>Word</li><li>Excel</li><li>PowerPoint</li><li>Outlook</li><li>Publisher</li><li>Access</li><li>Skype for Business</li><li>OneNote</li></ul><br>De 64-bit fulde versioner af Microsoft Project og Microsoft Visio er ikke inkluderet. Da installationen af disse programmer imidlertid afhænger af installationen af Microsoft 365 Apps til store virksomheder, oprettede Microsoft Managed Desktop standard Microsoft Intune-installationer og sikkerhedsgrupper, som du kan bruge til at udrulle disse programmer til licenserede brugere. Få mere at vide under [Installér Microsoft Project eller Microsoft Visio på Microsoft-administrerede skrivebordsenheder](../get-started/project-visio.md). |
| OneDrive | Azure Active Directory enkelt log på er aktiveret for brugere, når de første gang logger på OneDrive.<br><br>Kendte mappeomdirigering til mapperne Skrivebord, Dokument og Billeder er inkluderet. Disse mapper er aktiveret og konfigureret af Microsoft Managed Desktop. |
| Store apps | Microsoft Sway og Power BI leveres ikke sammen med enheden. Disse apps kan hentes fra Microsoft Store. |
| Win32-programmer | Teams leveres ikke sammen med enheden, men leveres som pakkes og leveres af Microsoft til Microsoft-administrerede skrivebordsenheder. Azure Information Protection Client leveres ikke sammen med enheden, men du kan få den pakket til installation. |
| Webprogrammer | Følgende webprogrammer leveres ikke sammen med enheden: <ul><li>Yammer</li><li>Office i en browser</li><li>Delve</li><li>Flow</li><li>StaffHub</li><li>Power Apps</li><li>Planner</li></ul> <br>Brugere kan få adgang til webversionen af disse programmer med en browser. |

## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Enterprise E5 eller E3 med Microsoft Defender til slutpunkt

Vi anbefaler, at dine it-administratorer konfigurerer følgende indstillinger.

> [!NOTE]
> Disse indstillinger er ikke inkluderet eller administreret som en del af Microsofts administrerede skrivebord.

| Produkt | Oplysninger |
| ----- | ----- |
| Windows Hello for Business | Du skal implementere Windows Hello for Business til at erstatte adgangskoder med stærk tofaktorgodkendelse til Microsoft-administrerede stationære enheder. Du kan finde flere oplysninger [i Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-identity-verification). |
| Programvirtualisering | Du kan installere Program Virtualization-pakker (App-V) ved hjælp af Intune Win32-appadministrationsklienten. Du kan finde flere oplysninger under [Programvirtualisering](/windows/application-management/app-v/appv-technical-reference). |
| Microsoft 365 forebyggelse af datatab | Du bør implementere Microsoft 365 forebyggelse af datatab for at overvåge de handlinger, der er foretaget på elementer, du har besluttet at være følsomme, og for at forhindre utilsigtet deling af disse elementer. Du kan finde flere oplysninger [Microsoft 365 forebyggelse af datatab](../../compliance/endpoint-dlp-learn-about.md). |

Funktioner, der er inkluderet og administreret som en del af Microsofts administrerede skrivebord:

| Produkt | Oplysninger |
| ----- | ----- |
| BitLocker-drevkryptering | BitLocker-drevkryptering bruges til at kryptere alle systemdrev. Du kan finde flere oplysninger under [BitLocker-drevkryptering](/windows/security/information-protection/bitlocker/bitlocker-overview). |
| Windows Defender System Guard | Beskytter integriteten af systemet ved start og validerer, at systemintegriteten virkelig er blevet bevaret. Du kan finde flere oplysninger [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Windows Defender Credential Guard | Windows Defender Credential Guard bruger virtualiseringsbaseret sikkerhed til at isolere hemmeligheder, så kun systemsoftwaren har adgang til dem. Du kan finde flere oplysninger [Windows Defender System Guard](/windows/security/threat-protection/windows-defender-system-guard/system-guard-how-hardware-based-root-of-trust-helps-protect-windows). |
| Microsoft Defender til slutpunkt – Registrering af slutpunkt og svar | Microsoft Managed Desktop Security Operations reagerer på beskeder og gør noget ved hjælp af registrering og svar af slutpunkter. Du kan finde flere oplysninger [i Microsoft Defender til slutpunkt – registrering af slutpunkt og svar](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response). |
| Microsoft Defender til Slutpunkt – Trusselseksperter | Microsoft Managed Desktop integrerer med Threat Experts-indsigt og data gennem målrettede angrebsmeddelelser. Du skal give yderligere samtykke, før denne tjeneste aktiveres. Du kan finde flere oplysninger [under Microsoft Defender til Slutpunkt – Trusselseksperter](/windows/security/threat-protection/microsoft-defender-atp/microsoft-threat-experts). |
| Microsoft Defender til slutpunkt – administration af trusler og sikkerhedsrisiko | Påkrævet til fremtidig brug i Microsoft Managed Desktop-serviceabonnementet. Du kan finde flere oplysninger [i Microsoft Defender til slutpunkt – administration af trusler og sikkerhedsrisiko](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). |
| Microsoft Defender til slutpunkt – Reduktion af angrebsoverfladen | Er målrettet mod risikabel softwareadfærd, der ofte misbruges af hackere. Du kan finde flere oplysninger [under Microsoft Defender til slutpunkt – Reduktion af angrebsoverfladen](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction). |
| Microsoft Defender for Endpoint – Exploit Protection | Beskytter mod malware, der bruger udnyttelse til at inficere enheder, og spreder sig automatisk ved at anvende afhjælpningsteknikker til processer og apps i operativsystemet. Du kan få mere at vide [under Microsoft Defender for Endpoint – Exploit Protection](/windows/security/threat-protection/microsoft-defender-atp/exploit-protection). |
| Microsoft Defender til Slutpunkt – Network Protection | Udvider omfanget af netværksservere Microsoft Defender SmartScreen at blokere al udgående HTTP- og HTTPS-trafik, der forsøger at oprette forbindelse til kilder med dårligt ry. Du kan få mere at vide [under Microsoft Defender til Slutpunkt – Netværksbeskyttelse](/windows/security/threat-protection/microsoft-defender-atp/network-protection). |
| Microsoft Defender Tamper Protection | Windows Tamper Protection bruges til at forhindre, at sikkerhedsindstillinger som f.eks. antivirusbeskyttelse ændres. Du kan finde flere oplysninger [i Microsoft Defender Tamper Protection](/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection). |
| Microsoft Defender Antivirus adfærdsbaseret, heuristisk og antivirusbeskyttelse i realtid | Altid tændt for at søge efter fil- og procestrusler, der muligvis ikke registreres som malware. Du kan finde flere [oplysninger Microsoft Defender Antivirus af adfærdsbaseret, heuristisk og antivirusbeskyttelse i realtid](../../security/defender-endpoint/microsoft-defender-antivirus-in-windows-10.md). |
| Microsoft Defender Antivirus Cloud-leveret beskyttelse | Giver dynamisk, øjeblikkelig, automatisk beskyttelse mod nye og nye trusler. Du kan finde flere oplysninger [Microsoft Defender Antivirus Cloud-delivered Protection](/windows/security/threat-protection/microsoft-defender-antivirus/utilize-microsoft-cloud-protection-microsoft-defender-antivirus). |
| Microsoft Defender til slutpunkt – "Blok ved første synsfelt" | Registrering og blokering af ny malware, når Windows registrerer en mistænkelig eller ukendt fil. Du kan finde flere oplysninger [i Microsoft Defender til slutpunkt – Bloker ved første synsvidens](/windows/security/threat-protection/microsoft-defender-antivirus/configure-block-at-first-sight-microsoft-defender-antivirus). |
| Microsoft Defender Antivirus uønskede programmer | Bruges til at blokere apps, der kan få din computer til at køre langsomt, vise uventede reklamer eller i værst installere anden software, der kan være uventet eller uønsket. Du kan finde flere oplysninger [Microsoft Defender Antivirus programmer, der kan være uønskede](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus). |
| Windows Defender firewall med Avanceret sikkerhed | Host-based, two-way network traffic filtering for a device, Windows Defender Firewall blocks unauthorized network traffic flowing into or out of the local device. Du kan finde flere oplysninger [Windows Defender Firewall med Avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). |
| Kontrol af brugerkonti | Kontrol af brugerkonti skifter til Secure Desktop, når en opgave eller en handling kræver adgangstype som administratorkonto. Brugere af Microsoft-administrerede skriveborde tildeles standardbrugeradgang ved tilmelding. Du kan finde flere oplysninger [under Kontrol af brugerkonti](/windows/security/identity-protection/user-account-control/how-user-account-control-works). |

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

| Produkt | Oplysninger |
| ----- | ----- |
| Enterprise Mobility + Security E3<br><br>Azure Active Directory Premium P2 | Du kan bruge alle funktioner i Enterprise Mobility + Security E3 til at administrere MDM-enheder.<br><br>Du kan bruge Azure Active Directory Premium P2 som en valgfri funktion med Microsoft Managed Desktop. |
| Microsoft Defender til skyapps | Du kan bruge denne valgfri funktion med Microsoft Managed Desktop.
| Azure Information Protection P2  | Du kan bruge denne valgfri funktion med Microsoft Managed Desktop.
