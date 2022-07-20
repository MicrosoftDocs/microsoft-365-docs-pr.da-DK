---
title: Beskyt ikke-administrerede Windows-pc'er og Macs i Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: Beskyt ikke-administrerede eller byod-enheder (bring-your-own devices) mod cyberangreb med Microsoft 365 Business Premium. Sådan konfigurerer du cybersikkerhed til Windows-pc'er og Macs.
ms.openlocfilehash: c6010661d11be2af064ddd3d5250f1cf9baacc09
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894355"
---
# <a name="protect-unmanaged-windows-pcs-and-macs-in-microsoft-365-business-premium"></a>Beskyt ikke-administrerede Windows-pc'er og Macs i Microsoft 365 Business Premium

Dette mål fokuserer på at skabe beskyttelse for alle ikke-administrerede Windows 10 pc'er og Macs, der ikke er tilmeldt Microsoft Intune. Det er meget sandsynligt, at din lille virksomhed eller kampagne kan have medarbejdere, der medbringer deres egne enheder (BYOD), og disse enheder administreres ikke. BYOD omfatter personligt ejede telefoner, tablets og pc'er.

> [!NOTE]
> BYOD-brugere skal hver især installere og køre appen Firmaportal for at tilmelde disse enheder og modtage adgang til virksomhedsressourcer.

Det er vigtigt, at du sikrer, at dine frontlinjebrugere følger disse retningslinjer, så minimumsikkerhedsfunktionerne er konfigureret på alle BYOD-enhederne.

## <a name="windows-10-or-11"></a>[Windows 10 eller 11](#tab/Windows10-11)

## <a name="windows-10-or-11"></a>Windows 10 eller 11

### <a name="turn-on-device-encryption"></a>Slå enhedskryptering til

Enhedskryptering er tilgængelig på en lang række Windows-enheder og hjælper med at beskytte dine data ved at kryptere dem. Hvis du slår enhedskryptering til, er det kun godkendte personer, der kan få adgang til din enhed og dine data. Se [Slå enhedskryptering](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) til for at få vejledning.

 Hvis enhedskryptering ikke er tilgængelig på enheden, kan du i stedet aktivere [BitLocker-standardkryptering](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) . BitLocker er ikke tilgængelig på Windows 10 Home udgave. 

### <a name="protect-your-device-with-windows-security"></a>Beskyt din enhed med Windows Sikkerhed

Hvis du har Windows 10 eller 11, får du den nyeste antivirusbeskyttelse med Windows Sikkerhed. Når du starter Windows 10 for første gang, er Windows Sikkerhed tændt og hjælper aktivt med at beskytte din pc ved at scanne efter malware (skadelig software), virus og sikkerhedstrusler. Windows Sikkerhed bruger beskyttelse i realtid til at scanne alt, hvad du downloader eller kører på din pc.

Windows Update downloader automatisk opdateringer til Windows Sikkerhed for at holde din pc sikker og beskytte den mod trusler.

Hvis du har en tidligere version af Windows og bruger Microsoft Security Essentials, er det en god idé at flytte til Windows Sikkerhed. Du kan finde flere oplysninger under [Hjælp med at beskytte min enhed med Windows Sikkerhed](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

### <a name="turn-on-windows-defender-firewall"></a>Slå Windows Defender Firewall til

Du bør altid køre Windows Defender Firewall, selvom du har en anden firewall slået til. Hvis du slår Windows Defender Firewall fra, kan det gøre din enhed (og dit netværk, hvis du har en) mere sårbar over for uautoriseret adgang. Se [Slå Windows Firewall til eller fra](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) for at få vejledning.

## <a name="next-mission"></a>Næste mission

Okay, missionen er fuldført! Lad os nu arbejde på [at beskytte mailsystemet](m365bp-protect-email-overview.md) mod phishing og andre angreb.

## <a name="mac"></a>[Mac](#tab/Mac)

## <a name="mac"></a>Mac

### <a name="use-filevault-to-encrypt-your-mac-disk"></a>Brug FileVault til at kryptere din Mac-disk

Diskkryptering beskytter data, når enheder mistes eller bliver stjålet. FileVault fuld diskkryptering hjælper med at forhindre uautoriseret adgang til oplysningerne på startdisken. Se [Brug FileVault til at kryptere startdisken på din Mac for at](https://support.apple.com/HT204837) få instruktioner.

### <a name="protect-your-mac-from-malware"></a>Beskyt din Mac mod malware

Microsoft anbefaler, at du installerer og bruger pålidelig antivirussoftware på din Mac. Se følgende artikel for at få en liste over valgmuligheder: [Bedste Mac antivirus 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Du kan også reducere risikoen for malware ved kun at bruge software fra pålidelige kilder. Indstillingerne i Sikkerhed & Indstillinger for beskyttelse af personlige oplysninger giver dig mulighed for at angive de softwarekilder, der er installeret på din Mac. Du kan få flere oplysninger under [Beskyt din Mac mod malware](https://support.apple.com/kb/PH25087).

### <a name="turn-on-firewall-protection"></a>Slå firewallbeskyttelse til

Brug firewallindstillinger til at beskytte Din Mac mod uønsket kontakt, der startes af andre computere, når du har forbindelse til internettet eller et netværk. Uden denne beskyttelse kan din Mac være mere sårbar over for uautoriseret adgang. Se [om programfirewallen](https://support.apple.com/HT201642) for at få vejledning.

## <a name="next-mission"></a>Næste mission

Okay, missionen er fuldført! Lad os nu arbejde på [at beskytte mailbrug](m365bp-protect-email-overview.md) mod phishing og andre angreb.