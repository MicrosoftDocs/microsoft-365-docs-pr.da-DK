---
title: Fejlfinding af problemer med svar i Microsoft Defender til Endpoint live
description: Fejlfinding af problemer, der kan opstå, når du bruger live svar i Microsoft Defender til Slutpunkt
keywords: fejlfinding af live svar, live, svar, låst, fil
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 4a3bab27a4e2efd6b196167754303f35d5553de6
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63599329"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-live-response-issues"></a>Fejlfinding af problemer med svar i Microsoft Defender til Endpoint live

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Denne side indeholder detaljerede trin til fejlfinding af problemer med livesvar.

## <a name="file-cannot-be-accessed-during-live-response-sessions"></a>Du kan ikke få adgang til filen under live svarsessioner

Hvis du støder på en fejlmeddelelse, når du forsøger at gøre noget under en direkte svarsession, hvor der står, at der ikke er adgang til filen, skal du følge nedenstående trin for at løse problemet.

1. Kopiér følgende kodestykke til scriptkode, og gem det som en PS1-fil:

    ```powershell
    $copied_file_path=$args[0]
    $action=Copy-Item $copied_file_path -Destination $env:TEMP -PassThru -ErrorAction silentlyContinue

    if ($action){
         Write-Host "You copied the file specified in $copied_file_path to $env:TEMP Succesfully"
    }

    else{
        Write-Output "Error occoured while trying to copy a file, details:"
        Write-Output  $error[0].exception.message

    }
    ```

2. Føj scriptet til live-svarbiblioteket.
3. Kør scriptet med en parameter: filstien for den fil, der skal kopieres.
4. Gå til din TEMP-mappe.
5. Kør den handling, du gerne vil gøre på den kopierede fil.

## <a name="slow-live-response-sessions-or-delays-during-initial-connections"></a>Slow live response sessions or delays during initial connections

Live-svar udnytter Defender til endpoint-sensorregistrering med WNS-tjenesten Windows. Hvis du har forbindelsesproblemer med live-svar, skal du bekræfte følgende oplysninger:

1. `notify.windows.com` ikke er blokeret i dit miljø. Du kan få mere at vide under [Konfigurer indstillinger for enhedsproxy og Internetforbindelse](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).
2. WpnService (Windows Push Notifications System Service) er ikke deaktiveret.

Se nedenstående artikler for fuldt ud at forstå WpnService-tjenestens funktionsmåde og krav:

- [Windows oversigt over Push Notification Services (WNS)](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)
- [Enterprise Firewall og proxykonfigurationer til understøttelse af WNS-trafik](/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)
- [Offentlige IP-intervaller for Microsoft-pushmeddelelser (MPNS)](https://www.microsoft.com/download/details.aspx?id=44535)
