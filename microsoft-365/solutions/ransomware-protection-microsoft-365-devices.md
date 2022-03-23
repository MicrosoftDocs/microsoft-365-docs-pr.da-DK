---
title: Trin 4. Beskyt enheder
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: ransomware, ransomware drevet af mennesker, ransomware drevet af mennesker, HumOR, extortionsangreb, ransomware-angreb, kryptering, cryptovirologi, nultillids
description: Brug Windows Intune som MDA- og MAM-udbyder, og Windows 10 til at beskytte dine Microsoft 365 mod ransomware-angreb.
ms.openlocfilehash: 0d7b9a5e125c3f0478948340dce5677a3ae65395
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594621"
---
# <a name="step-4-protect-devices"></a>Trin 4. Beskyt enheder

Sådan beskytter du enheder (slutpunkter) mod den indledende adgangsdel af et ransomware-angreb:

- [Installér Intune](/mem/intune/fundamentals/what-is-intune) som en mdm-udbyder (mobile device management) og administration af mobilapps (MAM – mobile application management) til dine enheder, og tilmeld dine enheder, der ejes af organisationen.
- Implementer [politikkerne fælles identitet og enhedsadgang](/microsoft-365/security/office-365-security/identity-access-policies) for at validere legitimationsoplysningerne for brugerkontoen og gennemtvinge krav til enhedstilstand og overholdelse af regler og standarder.
- [Aktivér netværksbeskyttelse](/microsoft-365/security/defender-endpoint/network-protection) i Microsoft Defender for slutpunkt og Microsoft 365 Defender.
- Konfigurer [websteds- og downloadkontrol](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings) samt [app- og filkontrol](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings) i Microsoft Defender SmartScreen at blokere eller advare.
- [Aktivér Microsoft Defender Antivirus scanning af](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus) downloadede filer og vedhæftede filer.
- Angiv **sikkerhedsniveauet for Fjernskrivebord** **til TLS** i Microsoft Defender for slutpunkt og Microsoft 365 Defender.

## <a name="windows-11-or-10-devices"></a>Windows 11 eller 10 enheder

Sådan beskytter du mod den laterale bevægelsesdel af et angreb fra en Windows 11 eller 10 enhed:

- [Slå Microsoft Defender Firewall til](https://support.microsoft.com/windows/turn-microsoft-defender-firewall-on-or-off-ec0844f7-aebd-0583-67fe-601ecf5d774f).
- [Opdater Microsoft Defender Antivirus definitioner](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

Sådan reduceres effekten af angrebene:

- Brug [regler for reduktion af angrebsoverfladen og avanceret beskyttelse mod ransomware](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#use-advanced-protection-against-ransomware).

Sådan beskytter du mod en hacker, der undgår dit sikkerhedsbudget:

- Sørg [for, at cloud-leveret](/microsoft-365/security/defender-endpoint/enable-cloud-protection-microsoft-defender-antivirus) beskyttelse Microsoft Defender Antivirus slået til.
- Hold Microsoft Defender Antivirus [overvågning af funktionsmåder i](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) realtid slået til.
- Slå beskyttelse [i realtid til](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus).
- Slå beskyttelse [mod manipulation til i Microsoft Defender for Endpoint for at](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection) forhindre ondsindede ændringer af sikkerhedsindstillingerne.

Sådan beskytter du en hackers eksekveringskode som en del af et angreb:

- Slå [Microsoft Defender Antivirus til](/mem/intune/user-help/turn-on-defender-windows).
- [Bloker Win32 API-opkald Office makroer](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules#block-win32-api-calls-from-office-macros).
- Overfør alle ældre projektmapper, der Excel 4.0-makroer, til det opdaterede VBA-makroformat ved hjælp [af denne proces](https://www.microsoft.com/microsoft-365/blog/2010/02/16/migrating-excel-4-macros-to-vba/).
- [Deaktiver brug af usignerede makroer](https://support.microsoft.com/topic/enable-or-disable-macros-in-office-files-12b036fd-d140-4e74-b45e-16fed1a7e5c6). Sørg for, at alle interne makroer med forretningsmæssige behov er [](/deployoffice/security/designate-trusted-locations-for-files-in-office) signerede og udnytter pålidelige placeringer for at sikre, at ukendte makroer ikke kører i dit miljø.
- Stop skadelige XLM- eller VBA-makroer ved at sikre, at AMSI ( [Runtime](https://www.microsoft.com/security/blog/2021/03/03/xlm-amsi-new-runtime-defense-against-excel-4-0-macro-malware/) Macro Scanning Interface) er aktiveret. Denne funktion (aktiveret som standard) er slået til, hvis indstillingen **Gruppepolitik for** scanningsomfanget for makrokørsel er indstillet til Aktivér **for** alle filer eller Aktivér for filer med **lav tillid**. Hent de seneste skabelonfiler til gruppepolitik.

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og administration af ændringer

Når du implementerer disse beskyttelser, skal du foretage ændringsstyring for følgende:

- De [almindelige nultillids-identitets- og enhedsadgangspolitikker](/microsoft-365/security/office-365-security/identity-access-policies) kan nægte adgang til brugere, der har ikke-kompatible enheder.
- Overførsel af filer kan advare brugerne før overførslen, eller det kan være blokeret.
- Nogle Office, Excel 4.0-, XLM- eller VBA-makroer kører muligvis ikke længere.

## <a name="resulting-configuration"></a>Resulterende konfiguration

Her er beskyttelse mod ransomware for din lejer for trin 1-4.

![Beskyttelse mod ransomware for din Microsoft 365 lejer efter trin 4](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step4.png)

## <a name="next-step"></a>Næste trin

[![Trin 5 for beskyttelse mod ransomware med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step5.png)](ransomware-protection-microsoft-365-information.md)

Fortsæt med [trin 5](ransomware-protection-microsoft-365-information.md) for at beskytte oplysninger i din Microsoft 365 lejer. 
