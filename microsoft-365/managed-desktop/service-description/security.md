---
title: Sikkerhedsteknologier i Microsoft Managed Desktop
description: Teknologier, der bruges til enhedssikkerhed, identitet og adgangsstyring, netværkssikkerhed og informationssikkerhed
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 4a6eb73a172ecfb680cbc48367851e40b1a54401
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588687"
---
# <a name="security-technologies-in-microsoft-managed-desktop"></a>Sikkerhedsteknologier i Microsoft Managed Desktop

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

Microsoft Managed Desktop bruger flere Microsoft-teknologier til at sikre administrerede enheder og data. Desuden anvender Microsoft Managed Desktop Security Operations Center forskellige [processer](security-operations.md) med disse teknologier. Mere specifikt:

| Proces | Beskrivelse |
| ------ | ------ |
| [Enhedssikkerhed](#device-security)| Sikkerhed og beskyttelse på Microsoft-administrerede stationære computere. |
| [Administration af identitet og adgang](#identity-and-access-management) | Administrer sikker brug af enheder via Azure Active Directory identitetstjenester. |
| [Netværkssikkerhed](#network-security)| VPN-oplysninger og anbefalede microsoft-skrivebordsløsninger og -indstillinger. |
| [Informationssikkerhed](#information-security)| Valgfrie tilgængelige tjenester til yderligere beskyttelse af følsomme oplysninger. |

Du kan finde oplysninger om datalagring, brug og sikkerhedspraksisser, der anvendes af Microsoft Managed Desktop, i vores whitepaper på [https://aka.ms/mmd-data](https://aka.ms/mmd-data).

## <a name="device-security"></a>Enhedssikkerhed

Microsoft Managed Desktop sikrer, at alle administrerede enheder er sikret og beskyttet og registrerer trusler så tidligt som muligt ved hjælp af følgende tjenester:

| Tjeneste | Beskrivelse |
| ----- | ----- |
| Antivirus | Microsoft Defender Antivirus er installeret og konfigureret<br>Microsoft Defender Antivirus definitioner er opdaterede. |
| Kryptering af fuld volumen | Windows BitLocker er løsningen til volumenkryptering til Microsoft-administrerede stationære computere.<br><br>Når en organisation er tilmeldt tjenesten, krypteres enheder ved hjælp af Windows BitLocker med indbygget Trust Platform Module (TPM) for at forhindre uautoriseret adgang til lokale data, når enheden er i slumretilstand eller deaktiveret.
| Overvågning | Microsoft Defender til slutpunkt bruges til overvågning af sikkerhedstrusler på tværs af alle Microsoft-administrerede skrivebordsenheder. Defender for Endpoint giver virksomhedskunder mulighed for at registrere, undersøge og reagere på avancerede trusler i deres virksomheds netværk. Du kan finde flere oplysninger [i Microsoft Defender til slutpunkt.](/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) |
| Opdateringer til operativsystem | Microsoft-administrerede stationære computere er altid sikret med de nyeste sikkerhedsopdateringer. |
| Sikker enhedskonfiguration | Microsoft Managed Desktop implementerer Microsofts grundlinje for sikkerhed. Du kan finde flere oplysninger [Windows oprindelige planer for sikkerhed.](/windows/security/threat-protection/windows-security-baselines)|

## <a name="identity-and-access-management"></a>Administration af identitet og adgang

Identitets- og adgangsstyring beskytter virksomhedens aktiver og forretningskritiske data. Microsoft Managed Desktop konfigurerer enheder for at sikre sikker brug med Azure Active Directory (Azure AD) administrerede identiteter. Det er kundens ansvar at vedligeholde nøjagtige oplysninger i deres Azure AD-lejer.

| Tjeneste | Beskrivelse |
| ----- | ----- |
| Biometrisk godkendelse | Windows Hello gør det muligt for brugerne at logge på med deres ansigt eller en pinkode, hvilket gør adgangskoderne sværere at glemme eller stjæle. Kunder er ansvarlige for at implementere de nødvendige forudsætninger for, at deres lokale Active Directory kan bruge denne tjeneste i en hybridkonfiguration. Du kan finde flere oplysninger [i Windows Hello.](/windows-hardware/design/device-experiences/windows-hello) |
| Standardbrugertilladelse | For at beskytte systemet og gøre det mere sikkert får brugeren tildelt standardbrugertilladelser. Denne tilladelse tildeles som en del Windows Autopilot-out of box-oplevelsen.

## <a name="network-security"></a>Netværkssikkerhed

Kunder er ansvarlige for netværkssikkerhed.

| Tjeneste | Beskrivelse |
| ----- | ----- |
| VPN | Kunder ejer deres VPN-infrastruktur for at sikre, at begrænsede virksomhedsressourcer kan gøres tilgængelige uden for intranettet.<br><br>Minimumskrav: Microsoft Managed Desktop kræver en Windows 10 kompatibel og understøttet VPN-løsning. Hvis din organisation har brug for en VPN-løsning, skal den understøtte Windows 10 og pakkes og implementeres via Intune. Kontakt din softwareudgiver for at få flere oplysninger.<br><br>Anbefaling:<br><ul><li> Microsoft anbefaler en moderne VPN-løsning, der nemt kan installeres via Intune til at skubbe VPN-profiler. Denne fremgangsmåde giver en altid tændt, problemfri, pålidelig og sikker måde at få adgang til virksomhedens netværk på. Du kan finde flere oplysninger [under VPN-indstillinger i Intune](/intune/vpn-settings-configure).</li><li>Tykke VPN-klienter eller ældre VPN-klienter anbefales ikke af Microsoft, når du bruger Microsoft Managed Desktop, da det kan påvirke brugermiljøet.</li><li>Microsoft anbefaler, at den udgående webtrafik går direkte til internettet uden at gå gennem VPN for at undgå problemer med ydeevnen.</li><li>Ideelt set anbefaler Microsoft brugen af appproxyen Azure Active Directory af en app i stedet for et VPN.</li></ul>

## <a name="information-security"></a>Informationssikkerhed

Du kan konfigurere disse valgfrie tjenester for at beskytte virksomhedens aktiver med høj værdi.

| Tjeneste | Beskrivelse |
| ----- | ----- |
| Datagendannelse | Oplysninger, der er gemt i nøglemapper på enheden, sikkerhedskopieres til OneDrive for Business. Microsoft Managed Desktop er ikke ansvarlig for data, der ikke er synkroniseret med OneDrive for Business.
| Windows beskyttelse af oplysninger | Til virksomheder, der kræver høj grad af informationssikkerhed, anbefaler [vi Windows Information Protection](/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) og [Azure Information Protection.](https://www.microsoft.com/cloud-platform/azure-information-protection)
