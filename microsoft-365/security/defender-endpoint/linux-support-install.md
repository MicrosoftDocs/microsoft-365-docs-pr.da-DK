---
title: Fejlfinding af installationsproblemer for Microsoft Defender til slutpunkt på Linux
ms.reviewer: ''
description: Fejlfinding af installationsproblemer for Microsoft Defender til slutpunkt på Linux
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, installation
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
ms.openlocfilehash: a0b2a571be5f78818279a343d253709e05814908
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63597588"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Fejlfinding af installationsproblemer for Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="verify-that-the-installation-succeeded"></a>Kontrollér, at installationen er fuldført

En fejl i installationen kan resultere i en meningsfuld fejlmeddelelse fra pakkestyringen. For at bekræfte om installationen er fuldført, skal du hente og kontrollere installationslogfilerne ved hjælp af:

```bash
 sudo journalctl --no-pager|grep 'microsoft-mdatp' > installation.log
```

```bash
 grep 'postinstall end' installation.log
```

```Output
 microsoft-mdatp-installer[102243]: postinstall end [2020-03-26 07:04:43OURCE +0000] 102216
```

Et output fra den forrige kommando med korrekt dato og klokkeslæt for installationen angiver succes.

Kontrollér også [Klientkonfigurationen](linux-install-manually.md#client-configuration) for at bekræfte produktets tilstand og registrere tekstfilen EICAR.

## <a name="make-sure-you-have-the-correct-package"></a>Sørg for, at du har den korrekte pakke

Kontrollér, at den pakke, du installerer, svarer til værtsdistributionen og -versionen.

<br>

****

|pakke|fordeling|
|---|---|
|mdatp-rhel8. Linux.x86_64.rpm|Oracle, RHEL og CentOS 8.x|
|mdatp-sles12. Linux.x86_64.rpm|SUSE Linux Enterprise Server 12.x|
|mdatp-sles15. Linux.x86_64.rpm|SUSE Linux Enterprise Server 15.x|
|mdatp. Linux.x86_64.rpm|Oracle, RHEL og CentOS 7.x|
|mdatp. Linux.x86_64.deb|Ubuntu og Ubuntu 16.04, 18.04 og 20.04|
|

Ved [manuel installation](linux-install-manually.md) skal du sørge for, at den korrekte distribution og version er blevet valgt.

## <a name="installation-failed"></a>Installationen mislykkedes

Kontrollér, om Defender for Endpoint-tjenesten kører:

```bash
service mdatp status
```

```Output
 ● mdatp.service - Microsoft Defender for Endpoint
   Loaded: loaded (/lib/systemd/system/mdatp.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-03-26 10:37:30 IST; 23h ago
 Main PID: 1966 (wdavdaemon)
    Tasks: 105 (limit: 4915)
   CGroup: /system.slice/mdatp.service
           ├─1966 /opt/microsoft/mdatp/sbin/wdavdaemon
           ├─1967 /opt/microsoft/mdatp/sbin/wdavdaemon
           └─1968 /opt/microsoft/mdatp/sbin/wdavdaemon
 ```

## <a name="steps-to-troubleshoot-if-the-mdatp-service-isnt-running"></a>Trin til fejlfinding, hvis mdatp-tjenesten ikke kører

1. Kontrollér, om "mdatp"-bruger findes:

    ```bash
    id "mdatp"
    ```

    Hvis der ikke er nogen output, skal du køre

    ```bash
    sudo useradd --system --no-create-home --user-group --shell /usr/sbin/nologin mdatp
    ```

2. Prøv at aktivere og genstarte tjenesten ved hjælp af:

    ```bash
    sudo service mdatp start
    ```

    ```bash
    sudo service mdatp restart
    ```

3. Hvis mdatp.service ikke findes, når du kører den forrige kommando, skal du køre:

    ```bash
    sudo cp /opt/microsoft/mdatp/conf/mdatp.service <systemd_path> 
    ```

    hvor `<systemd_path>` er `/lib/systemd/system` for Ubuntu- og Oracle-fordelinger og /usr/lib/systemd/system' for Rhel, CentOS, Oracle og SLES. Kør derefter trin 2 igen.

4. Hvis ovenstående trin ikke virker, skal du kontrollere, om SELinux er installeret og i gennemtvingningstilstand. Hvis det er ja, skal du prøve at indstille den til ikke-begrænsende (helst) eller deaktiveret tilstand. Det kan gøres ved at indstille parameteren til `SELINUX` "permissiv" eller "deaktiveret" i `/etc/selinux/config` filen, efterfulgt af genstart. Kontrollér man-siden af selinux for at få flere oplysninger.
Prøv nu at genstarte mdatp-tjenesten ved hjælp af trin 2. Gendan konfigurationsændringen straks, men af sikkerhedsmæssige årsager efter at have prøvet den og genstartet.

5. Hvis `/opt` mappe er et symbolsk link, kan du oprette et indbind til `/opt/microsoft`.

6. Sørg for, at daemonen har eksekverbar tilladelse.

    ```bash
    ls -l /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ```Output
    -rwxr-xr-x 2 root root 15502160 Mar  3 04:47 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    Hvis daemon ikke har eksekverbare tilladelser, kan du gøre den eksekverbar ved hjælp af:

    ```bash
    sudo chmod 0755 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    og prøve at køre trin 2 igen.

7. Sørg for, at filsystemet, der indeholder wdavdaemon, ikke ermonteret med "noexec".

## <a name="if-the-defender-for-endpoint-service-is-running-but-the-eicar-text-file-detection-doesnt-work"></a>Hvis tjenesten Defender for Endpoint kører, men registrering af EICAR-tekstfilen ikke virker

1. Kontrollér filtypen ved hjælp af:

    ```bash
    findmnt -T <path_of_EICAR_file>
    ```

    Aktuelt understøttede filsystemer til aktivitet ved adgang vises [her](microsoft-defender-endpoint-linux.md#system-requirements). Filer uden for disse filsystemer scannes ikke.

## <a name="command-line-tool-mdatp-isnt-working"></a>Kommandolinjeværktøjet "mdatp" fungerer ikke

1. Hvis det at køre kommandolinjeværktøjet giver `mdatp` en fejl `command not found`, skal du køre følgende kommando:

    ```bash
    sudo ln -sf /opt/microsoft/mdatp/sbin/wdavdaemonclient /usr/bin/mdatp
    ```

    og prøve igen.

    Hvis ingen af ovenstående trin hjælper, kan du indsamle diagnostiske logfiler:

    ```bash
    sudo mdatp diagnostic create
    ```

    ```Output
    Diagnostic file created: <path to file>
    ```

    Stien til en zip-fil, der indeholder logfilerne, vises som et output. Kontakt vores kundesupport med disse logfiler.
