---
title: Beskyt ikke-administrerede Windows 10 pc'er og Mac-computere i Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Beskyt ikke-administrerede eller medbring dine egne enheder (BYOD) med Microsoft 365 Business Premium.
ms.openlocfilehash: b3d783ba498337af7ff867fe749366abe1734da5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705005"
---
# <a name="protect-unmanaged-windows-10-pcs-and-macs-in-microsoft-365-business-premium"></a>Beskyt ikke-administrerede Windows 10 pc'er og Mac-computere i Microsoft 365 Business Premium

Du kan administrere Windows 10-pc'er og Mac-computere ved at tilmelde dem i Microsoft Intune, hvilket giver dig mulighed for at sikre, at de er sunde og sikre, før du får adgang til data i dit miljø. Mange kampagner og mindre virksomheder omfatter dog medarbejdere, der bruger deres egne enheder (BYOD), som ikke administreres af organisationen. For disse ikke-administrerede pc'er og Mac-computere skal du bruge denne artikel til at sikre, at der er konfigureret minimumsikkerhedsfunktioner.

<!--A Windows 10 PC is considered managed after you have completed the following two steps:

1. You (or the admin) set up device and data protection policies in the [setup  wizard](../business/set-up.md).

2. You have [connected your computer to Azure Active Directory](../business/set-up-windows-devices.md) and use your Microsoft 365 username and password to sign in.
3. --> 

## <a name="protect-a-computer-running-windows-10-or-a-mac"></a>Beskyt en computer, der Windows 10 eller en Mac

<!--If you have a PC that is running Windows 10 that is not connected to Microsoft 365, or a Mac, the Microsoft 365 protections do not apply to it, but here are some things you can do to keep your data secure on these devices as well:
-->
Hvis din Windows 10-pc eller Mac ikke administreres af din organisation, skal du sørge for at konfigurere disse sikkerhedsfunktioner.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**Slå enhedskryptering til**<p>

Enhedskryptering er tilgængelig på en lang række Windows-enheder og hjælper med at beskytte dine data ved at kryptere dem. Hvis du slår enhedskryptering til, er det kun autoriserede personer, der vil kunne få adgang til din enhed og dine data. Se [slå enhedskryptering til for at](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) få vejledning.

 Hvis enhedskryptering ikke er tilgængelig på din enhed, kan du aktivere Standard [BitLocker-kryptering i](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) stedet. BitLocker er ikke tilgængelig i Windows 10 Home version. 

**Beskyt din enhed med Windows Sikkerhed**<p>
Hvis du har Windows 10, får du den nyeste antivirusbeskyttelse med Windows Sikkerhed. Når du starter Windows 10 for første gang, er Windows Sikkerhed tændt og beskytter aktivt pc'en ved at scanne for malware (skadelig software), virus og sikkerhedstrusler. Windows Sikkerhed bruger beskyttelse i realtid til at scanne alt, hvad du downloader eller kører på din pc.

Windows Update downloader opdateringer til Windows Sikkerhed automatisk for at beskytte din pc mod trusler.

Hvis du har en tidligere version af Windows og bruger Microsoft Security Essentials, er det en god ide at gå til Windows Sikkerhed. Du kan få mere at vide [under Beskyt min enhed med Windows Sikkerhed](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**Slå firewallen Windows til**<p>
Du bør altid køre en Windows Firewall, også selvom du har en anden firewall slået til. Hvis du slår Windows Firewall fra, kan det gøre din enhed (og dit netværk, hvis du har sådan et) mere sårbar over for uautoriseret adgang. Se [Slå Windows Firewall til eller fra](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) for at få vejledning.

## <a name="mac"></a>[Mac](#tab/Mac)

**Brug FileVault til at kryptere din Mac-disk**<p>
Diskkryptering beskytter data, når enheder er gået tabt eller blevet stjålet. FileVaults kryptering af hele disken hjælper med at forhindre uautoriseret adgang til oplysningerne på din startdisk. Se [Brug FileVault til at kryptere startdisken på din Mac](https://support.apple.com/HT204837) for vejledning.

**Beskyt din Mac mod malware**<p>
Microsoft anbefaler, at du installerer og bruger pålidelig antivirussoftware på din Mac. Se følgende artikel for at få en liste over valgmuligheder: [Bedste Mac antivirus 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Du kan også reducere risikoen for malware ved kun at bruge software fra pålidelige kilder. Indstillingerne under Indstillinger for sikkerhed og & giver dig mulighed for at angive de softwarekilder, der er installeret på din Mac. Få mere at vide under [Beskyt din Mac mod malware](https://support.apple.com/kb/PH25087).

**Slå firewallbeskyttelse til**<p>
Brug firewallindstillinger til at beskytte din Mac mod uønsket kontakt fra andre computere, når du har forbindelse til internettet eller et netværk. Uden denne beskyttelse kan din Mac være mere sårbar over for uautoriseret adgang. Se [om programfirewall for vejledning](https://support.apple.com/HT201642) .
