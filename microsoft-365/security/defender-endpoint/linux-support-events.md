---
title: Fejlfinding af manglende hændelser eller advarsler for Microsoft Defender til slutpunkt på Linux
description: Foretag fejlfinding af manglende hændelser eller advarsler i Microsoft Defender til slutpunkt på Linux.
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, events
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5a17f94e3d26c08c0f6e0ca358778a65189cf6a5
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63591240"
---
# <a name="troubleshoot-missing-events-or-alerts-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Fejlfinding af manglende hændelser eller advarsler for Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender til slutpunkt på Linux](microsoft-defender-endpoint-linux.md)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Denne artikel indeholder nogle generelle trin til at afhjælpe manglende begivenheder eller beskeder <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">på Microsoft 365 Defender-portalen</a>.

Når **Microsoft Defender til Slutpunkt** er blevet installeret korrekt på en enhed, _genereres en_ enhedsside i portalen. Du kan gennemse alle registrerede begivenheder på tidslinjefanen på enhedssiden eller på den avancerede jagtside. I dette afsnit foretages fejlfinding i tilfælde af, at nogle eller alle forventede hændelser mangler.
Hvis f.eks. _alle CreatedFile-hændelser_ mangler.

## <a name="missing-network-and-login-events"></a>Manglende netværks- og logonhændelser

Microsoft Defender for Endpoint brugte Framework `audit` fra linux til at spore netværks- og logonaktivitet.

1. Sørg for, at overvågningsrammer fungerer.

    ```bash
    service auditd status
    ```

    forventet output:

    ```output
    ● auditd.service - Security Auditing Service
    Loaded: loaded (/usr/lib/systemd/system/auditd.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2020-12-21 10:48:02 IST; 2 weeks 0 days ago
        Docs: man:auditd(8)
            https://github.com/linux-audit/audit-documentation
    Process: 16689 ExecStartPost=/sbin/augenrules --load (code=exited, status=1/FAILURE)
    Process: 16665 ExecStart=/sbin/auditd (code=exited, status=0/SUCCESS)
    Main PID: 16666 (auditd)
        Tasks: 25
    CGroup: /system.slice/auditd.service
            ├─16666 /sbin/auditd
            ├─16668 /sbin/audispd
            ├─16670 /usr/sbin/sedispatch
            └─16671 /opt/microsoft/mdatp/sbin/mdatp_audisp_plugin -d
    ```

2. Hvis er `auditd` markeret som stoppet, skal du starte den.

    ```bash
    service auditd start
    ```

**I SLES-systemer** er SYSCALL-overvågning `auditd` i muligvis som standard deaktiveret og kan tages i betragtning for manglende hændelser.

1. Hvis du vil validere, at SYSCALL-overvågning ikke er deaktiveret, skal du oprette en liste over de aktuelle overvågningsregler:

    ```bash
    sudo auditctl -l
    ```

    Hvis følgende linje er til stede, skal du fjerne den eller redigere den for at gøre det muligt for Microsoft Defender for Endpoint at spore bestemte SYSCALLs.

    ```output
    -a task, never
    ```

    overvågningsreglerne findes på `/etc/audit/rules.d/audit.rules`.

## <a name="missing-file-events"></a>Manglende filhændelser

Filhændelser indsamles med `fanotify` Framework. Hvis nogle eller alle filhændelser mangler, skal du kontrollere `fanotify` , at er aktiveret på enheden, og at filsystemet [understøttes](microsoft-defender-endpoint-linux.md#system-requirements).

Vis filsystemerne på computeren med:

```bash
df -Th
```
