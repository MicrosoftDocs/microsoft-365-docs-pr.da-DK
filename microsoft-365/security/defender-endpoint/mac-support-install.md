---
title: Fejlfinding af installationsproblemer for Microsoft Defender til Slutpunkt på Mac
description: Fejlfinding af installationsproblemer i Microsoft Defender til slutpunkt på Mac.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installér
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5f56e28d472cb3fdf8dd089effcd4beac6e42374
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63591783"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a>Fejlfinding af installationsproblemer for Microsoft Defender til Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender til Slutpunkt på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a>Installationen mislykkedes

Ved manuel installation står der "Der opstod en fejl under installationen" på siden Oversigt i installationsguiden. Installationsprogrammet stødte på en fejl, der forårsagede, at installationen mislykkedes. Kontakt softwareudgiveren for at få hjælp." For MDM-installationer vises den også som en generisk installationsfejl.

Vi viser ikke slutbrugeren en nøjagtig fejl, men vi beholder en logfil med installationsprocessen i `/Library/Logs/Microsoft/mdatp/install.log`. Hver installationssession føjes til denne logfil. Du kan kun bruge `sed` til at få output fra den seneste installationssession:

```bash
sed -n 'H; /^preinstall com.microsoft.wdav begin/h; ${g;p;}' /Library/Logs/Microsoft/mdatp/install.log
```
```Output
preinstall com.microsoft.wdav begin [2020-03-11 13:08:49 -0700] 804
INSTALLER_SECURE_TEMP=/Library/InstallerSandboxes/.PKInstallSandboxManager/CB509765-70FC-4679-866D-8A14AD3F13CC.activeSandbox/89FA879B-971B-42BF-B4EA-7F5BB7CB5695
correlation id=CB509765-70FC-4679-866D-8A14AD3F13CC
[ERROR] Downgrade from 100.88.54 to 100.87.80 is not permitted
preinstall com.microsoft.wdav end [2020-03-11 13:08:49 -0700] 804 => 1
```

I dette eksempel har den faktiske årsag præfiks med `[ERROR]`.
Installationen mislykkedes, fordi en nedgradering mellem disse versioner ikke understøttes.

## <a name="mdatp-install-log-missing-or-not-updated"></a>Installationsloggen i MDATP mangler eller opdateres ikke

I sjældne tilfælde efterlades der ingen sporing i MDATP's /Library/Logs/Microsoft/mdatp/install.log-fil.
Først skal du kontrollere, at der skete en installation. Analysér derefter mulige fejl ved at forespørge i macOS-logfiler. Det er nyttigt at gøre dette i MDM-installationer, når der ikke er nogen klientbrugergrænseflade. Vi anbefaler, at du bruger et smalt tidsvindue til at køre en forespørgsel og filtrere efter logføring procesnavnet, da der vil være en stor mængde oplysninger.

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
