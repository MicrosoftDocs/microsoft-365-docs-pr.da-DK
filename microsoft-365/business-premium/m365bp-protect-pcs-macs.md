---
title: Beskyt ikke-administrerede Windows-pc'er og Macs i Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Beskyt ikke-administrerede eller byod-enheder (bring-your-own devices) mod cyberangreb med Microsoft 365 Business Premium. Sådan konfigurerer du cybersikkerhed til Windows-pc'er og Macs.
ms.openlocfilehash: 10d8edd8a3e8106fc448fa3850590de9f6cda8df
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/04/2022
ms.locfileid: "65892576"
---
# <a name="protect-unmanaged-windows-pcs-and-macs-in-microsoft-365-business-premium"></a>Beskyt ikke-administrerede Windows-pc'er og Macs i Microsoft 365 Business Premium

Dette mål fokuserer på at skabe beskyttelse for alle ikke-administrerede Windows 10-pc'er og Macs, der ikke er tilmeldt Microsoft Intune. Det er meget sandsynligt, at din lille virksomhed eller kampagne kan have medarbejdere, der medbringer deres egne enheder (BYOD), og disse enheder administreres ikke. BYOD omfatter personligt ejede telefoner, tablets og pc'er.

>[!NOTE]
>BYOD-brugere skal hver især installere og køre appen Firmaportal for at tilmelde disse enheder og få adgang til virksomhedsressourcerne.

Det er vigtigt, at du sikrer, at dine frontlinjebrugere følger disse retningslinjer, så minimumsikkerhedsfunktionerne er konfigureret på alle BYOD-enhederne.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**Slå enhedskryptering til**<p>
Enhedskryptering er tilgængelig på en lang række Windows-enheder og hjælper med at beskytte dine data ved at kryptere dem. Hvis du slår enhedskryptering til, er det kun godkendte personer, der kan få adgang til din enhed og dine data. Se [Slå enhedskryptering](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) til for at få vejledning.

 Hvis enhedskryptering ikke er tilgængelig på enheden, kan du i stedet aktivere [BitLocker-standardkryptering](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) . (BitLocker er ikke tilgængelig i Windows 10 Home-udgaven). 

**Beskyt din enhed med Windows Security**<p>
Hvis du har Windows 10, får du den nyeste antivirusbeskyttelse med Windows Security. Når du starter Windows 10 første gang, er Windows Security slået til og hjælper aktivt med at beskytte din pc ved at scanne efter malware (skadelig software), virus og sikkerhedstrusler. Windows Security bruger beskyttelse i realtid til at scanne alt, hvad du downloader eller kører på din pc.

Windows Update downloader automatisk opdateringer til Windows Security for at hjælpe med at beskytte din pc og beskytte den mod trusler.

Hvis du har en tidligere version af Windows og bruger Microsoft Security Essentials, er det en god idé at flytte til Windows Security. Du kan finde flere oplysninger under [Hjælp med at beskytte min enhed med Windows Security](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**Slå Windows Firewall til**<p>
Du bør altid køre Windows Firewall, selvom du har en anden firewall slået til. Hvis du slår Windows Firewall fra, kan det gøre din enhed (og dit netværk, hvis du har en) mere sårbar over for uautoriseret adgang. Se [Slå Windows Firewall til eller fra](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) for at få vejledning.

## <a name="next-mission"></a>Næste mission

Okay, missionen er fuldført! Lad os nu arbejde på [at beskytte mailsystemet](m365bp-protect-email-overview.md) mod phishing og andre angreb.

## <a name="mac"></a>[Mac](#tab/Mac)

**Brug FileVault til at kryptere din Mac-disk**<p>
Diskkryptering beskytter data, når enheder mistes eller bliver stjålet. FileVault fuld diskkryptering hjælper med at forhindre uautoriseret adgang til oplysningerne på startdisken. Se [Brug FileVault til at kryptere startdisken på din Mac for at](https://support.apple.com/HT204837) få instruktioner.

**Beskyt din Mac mod malware**<p>
Microsoft anbefaler, at du installerer og bruger pålidelig antivirussoftware på din Mac. Se følgende artikel for at få en liste over valgmuligheder: [Bedste Mac antivirus 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Du kan også reducere risikoen for malware ved kun at bruge software fra pålidelige kilder. Indstillingerne i Sikkerhed & Indstillinger for beskyttelse af personlige oplysninger giver dig mulighed for at angive de softwarekilder, der er installeret på din Mac. Du kan få flere oplysninger under [Beskyt din Mac mod malware](https://support.apple.com/kb/PH25087).

**Slå firewallbeskyttelse til**<p>
Brug firewallindstillinger til at beskytte Din Mac mod uønsket kontakt, der startes af andre computere, når du har forbindelse til internettet eller et netværk. Uden denne beskyttelse kan din Mac være mere sårbar over for uautoriseret adgang. Se [om programfirewallen](https://support.apple.com/HT201642) for at få vejledning.

## <a name="next-mission"></a>Næste mission

Okay, missionen er fuldført! Lad os nu arbejde på [at beskytte mailsystemet](m365bp-protect-email-overview.md) mod phishing og andre angreb.