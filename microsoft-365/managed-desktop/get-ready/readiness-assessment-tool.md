---
title: Bedømmelsesværktøjer til parathed
description: Beskriver de to værktøjer, de kontroller, de kører, og betydningen af resultaterne
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 8d949b13203aaeab51d2518f16650ba6df832195
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63591099"
---
# <a name="readiness-assessment-tools"></a>Bedømmelsesværktøjer til parathed

For at få den bedst mulige oplevelse, når du tilmelder dig Microsoft Managed Desktop, er der indstillinger og andre parametre, du skal angive i forvejen, og visse enheds- og netværkskrav for at overholde dem.

Ét værktøj, som åbnes via administrationsportalen til Microsoft-administreret skrivebord, kontrollerer administrationsrelaterede indstillinger. Et andet værktøj, som kan downloades, kontrollerer individuelle krav til enheder og netværksindstillinger. Du kan bruge disse værktøjer til at kontrollere disse indstillinger og modtage detaljerede trin til løsning af problemer, der ikke er rigtige.

## <a name="downloadable-readiness-assessment-checker-for-devices-and-network"></a>Kontrol af parathed til download til enheder og netværk

Hvis du vil have mere at vide om, hvordan du bruger vurderingskontrollen til parathed, der kan downloades, skal du [se Kontrol af parathed, der kan downloades](readiness-assessment-downloadable.md).

## <a name="online-readiness-assessment-tool-for-management-settings"></a>Værktøj til vurdering af onlineparathed til administrationsindstillinger

[Onlineværktøjet kontrollerer](https://aka.ms/mmdart) indstillingerne i Microsoft Endpoint Manager (specifikt Microsoft Intune), Azure Active Directory (Azure AD) og Microsoft 365 for at sikre, at de fungerer sammen med Microsoft Managed Desktop.

Microsoft Managed Desktop bevarer de data, der er knyttet til disse kontroller, i 12 måneder efter den sidste gang, du tjekkede din Azure AD-organisation (lejer). Efter 12 måneder beholder vi den i identificeret form. Du kan vælge at slette de data, vi indsamler.

Alle med mindst den globale læser- eller Intune-administratorrolle vil kunne køre dette værktøj, men to af kontrollerne [(Politikker](readiness-assessment-fix.md#conditional-access-policies) for betinget adgang og [Multifaktorgodkendelse](readiness-assessment-fix.md#multi-factor-authentication)) kræver ekstra tilladelser.

> [!IMPORTANT]  
> Værktøjet til vurdering af onlineparathed hjælper dig med at kontrollere, om du er parat til at tilmelde dig Microsoft Managed Desktop for første gang. Hvis din organisation allerede er tilmeldt Microsoft Managed Desktop, skal du ikke bruge dette værktøj.

Bedømmelsesværktøjet kontrollerer disse elementer:

## <a name="microsoft-intune-settings"></a>Microsoft Intune indstillinger

Følgende er de Microsoft Intune indstillinger:

| Tjek | Beskrivelse |
| ------ | ------ |
| Autopilot-udrulningsprofil | Bekræfter, at tildelingen af Autopilot-installationsprofilen ikke gælder for alle enheder. <br><br> Profilen bør **ikke være** tildelt nogen Microsoft-administreret skrivebordsenheder. |
| Certifikatforbindelser | Kontrollerer tilstanden for certifikatforbindelser for at sikre, at de er aktive. |
| Betinget adgang | Kontrollerer, at politikker for betinget adgang ikke tildeles til alle brugere. <br><br> Politikker for betinget adgang **bør ikke** tildeles til Microsoft Managed Desktop-tjenestekonti. |
| Politikker for enhedsoverholdelse | Kontrollerer, at politikker for overholdelse af regler og standarder i Intune ikke tildeles til alle brugere. <br><br> Politikkerne bør **ikke tildeles** til nogen Microsoft-administreret skrivebordsenheder. |
| Enhedskonfigurationsprofiler | Bekræfter, at konfigurationsprofiler ikke tildeles til alle brugere eller alle enheder. <br><br> Konfigurationsprofiler bør **ikke** tildeles til nogen Microsoft-administreret skrivebordsenheder. |
| Begrænsninger for enhedstype | Kontrollerer, Windows 10 enheder i organisationen har tilladelse til at tilmelde sig Intune. |
| Statusside for registrering | Bekræfter, at Statusside for tilmelding ikke er aktiveret. |
| Tilmelding i Intune | Kontrollerer, Windows 10 enheder i Din Azure AD-organisation automatisk registreres i Intune. |
| Microsoft Store til Virksomheder | Bekræfter, Microsoft Store til Virksomheder er aktiveret og synkroniseret med Intune. |
| Multifaktorgodkendelse | Bekræfter, at multifaktorgodkendelse ikke anvendes på Microsoft Managed Desktop-tjenestekonti. |
| PowerShell-scripts | Kontrollerer, Windows PowerShell scripts ikke er **tildelt på** en måde, der kan målrettes mod Microsoft-administrerede desktopenheder. |
| Område | Kontrollerer, at dit område understøttes af Microsoft Managed Desktop. |
| Grundlinjer for sikkerhed | Kontrollerer, at den oprindelige sikkerhedsprofil ikke er målrettet alle brugere eller alle enheder. <br><br> Politikker for grundlinje for sikkerhed **bør ikke målrettes** nogen Microsoft-administrerede skrivebordsenheder. |
| Windows apps | Gennemse, hvilke apps du vil tildele til Microsoft-administrerede skrivebordsenheder. |
| Windows Hello for Business | Kontrollerer, Windows Hello for Business er aktiveret. |
| Windows 10 opdateringsring | Kontrollerer, at Intunes politik for "Windows 10 opdateringsring" ikke målrettes mod alle brugere eller alle enheder. <br><br> Politikken bør ikke **målrettes mod** nogen Microsoft-administrerede skrivebordsenheder. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory indstillinger

Følgende er de Azure Active Directory indstillinger:

| Tjek | Beskrivelse |
| ----- | ----- |
| "Ad hoc"-abonnementer til Enterprise State Roaming | Anbefaler, hvordan du kontrollerer en indstilling, der, hvis den er indstillet til "falsk", kan forhindre Enterprise State Roaming i at fungere korrekt. |
| Enterprise State Roaming | Anbefaler, hvordan du kontrollerer, at Enterprise State Roaming er aktiveret. |
| Licenser | Kontrollerer, at du har fået de nødvendige [licenser](prerequisites.md#more-about-licenses). |
| Multifaktorgodkendelse | Kontrollerer, at multifaktorgodkendelse ikke anvendes for alle brugere. <br><br> Multifaktorgodkendelse må ikke **ved et** uheld anvendes på Microsoft Managed Desktop-tjenestekonti. |
| Navne på sikkerhedskonto | Kontrollerer, at ingen brugernavne er i konflikt med dem, som Microsoft Managed Desktop reserverer til eget brug. |
| Sikkerhedsadministratorroller | Beskrav, at brugere med sikkerhedslæser-, sikkerhedsoperator- eller global læser-roller har fået tildelt disse roller i Microsoft Defender til slutpunkt. |
| Sikkerhedsstandardindstillinger | Kontrollerer, om din Azure AD-organisation har aktiveret sikkerhedsstandardindstillinger Azure Active Directory. |
| Selvbetjeningstjenesten til nulstilling af adgangskode | Bekræfter, at nulstilling af adgangskode via selvbetjening er aktiveret. |
| Standardbrugerrolle | Bekræfter, at brugerne er standardbrugere og ikke har lokale administratorrettigheder. |

## <a name="microsoft-365-apps-for-enterprise-settings"></a>Microsoft 365 Apps for Enterprise-indstillinger

Følgende er de Microsoft 365 Apps for Enterprise-indstillinger:

| Tjek | Beskrivelse |
| ----- | ----- |
| OneDrive for Business | Kontrollerer, OneDrive for Business bruger ikke-understøttede indstillinger. |

For hver kontrol rapporterer værktøjet et af fire mulige resultater:

| Resultat | Betydning |
| ----- | ----- |
| Klar | Der kræves ingen handling, før du har fuldført tilmeldingen. |
| Vejledning | Følg trinnene i værktøjet for at få den bedste oplevelse med registrering og for brugere. <br><br> Du *kan* fuldføre tilmeldingen, men du skal løse disse problemer, før du installerer din første enhed. |
| Ikke klar | **Din tilmelding mislykkes** , hvis du ikke løser disse problemer. <br><br> Følg trinnene i værktøjet for at løse dem. |
| Error | Den Azure Active Director-rolle (AD), du bruger, har ikke tilstrækkelige tilladelser til at køre denne kontrol. |

## <a name="after-enrollment"></a>Efter tilmelding

Når du har fuldført tilmeldingen til Microsoft Managed Desktop, skal du huske at gå tilbage og justere visse indstillinger for Intune og Azure AD. Du kan finde flere oplysninger [i Juster indstillinger efter tilmelding](../get-started/conditional-access.md).

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
2. Kør bedømmelsesværktøjer til parathed (denne artikel).
3. Køb [Firmaportal](../get-started/company-portal.md).
4. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
5. Kontrollér [netværkskonfigurationen](network.md).
6. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
7. [Forberede brugeradgang til data](authentication.md).
8. [Forbered apps](apps.md).
9. [Forbered tilknyttede drev](mapped-drives.md).
10. [Forberede udskrivningsressourcer](printing.md).
11. Navne [på adresseenhed](address-device-names.md).
