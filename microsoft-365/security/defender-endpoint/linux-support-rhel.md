---
title: Fejlfinding af problemer med Microsoft Defender til slutpunkt på Linux RHEL6
ms.reviewer: ''
description: Fejlfinding af forbindelsesproblemer i skyen til Microsoft Defender til slutpunkt på Linux
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, cloud, connectivity, communication
search.appverid: met150
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 43a60d12883dc639c4ee5b831d305010cef58533
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592984"
---
# <a name="troubleshoot-issues-for-microsoft-defender-for-endpoint-on-linux-rhel6"></a>Fejlfinding af problemer med Microsoft Defender til slutpunkt på Linux RHEL6

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Denne artikel indeholder vejledning til fejlfinding af problemer, der kan opstå med Microsoft Defender til Linux på Red Hat Linux 6 (RHEL 6) eller nyere. 

Når pakken (mdatp_XXX.XX.XX.XX.x86_64.rpm) er installeret, skal du udføre de angivne handlinger for at bekræfte, at installationen blev gennemført. 


## <a name="check-the-service-health"></a>Kontrollér tjenestestilstanden

Brug følgende kommando til at kontrollere tjenestetjenestens tilstand:

```bash
mdatp health 
```

## <a name="verify-that-the-service-is-running"></a>Kontrollér, at tjenesten kører

Brug følgende kommando til at bekræfte, at tjenesten kører:

```bash
service mdatp status 
```

Forventet output: `mdatp start/running, process 4517`

## <a name="verify-the-distribution-and-kernel-version"></a>Bekræft fordelings- og kerneversionen
Distributions- og kerneversionerne skal være på den understøttede liste.

Brug følgende kommando til at hente distributionsversionen:

```bash
cat /etc/redhat-release (or /etc/system-release) 
```

Brug følgende kommando til at hente kerneversionen:

```bash
uname -r
```
## <a name="check-if-mdatp-audisp-process-is-running"></a>Kontrollér, om mdatp Audisp-processen kører 
Det forventede output er, at processen kører.

Brug følgende kommando til at kontrollere:

```bash
pidof mdatp_audisp_plugin 
```

## <a name="check-talpa-modules"></a>Kontrollér TALPA-moduler
Der bør være indlæst ni moduler. 

Brug følgende kommando til at kontrollere:

```bash
lsmod | grep talpa
```

Forventet output: Aktiveret

```bash
talpa_pedconnector       878  0 

talpa_pedevice          5189  2 talpa_pedconnector 

talpa_vfshook          32300  1 

talpa_vcdevice          4947  1 

talpa_syscall           9127  0 

talpa_core             90699  4 talpa_vfshook,talpa_vcdevice,talpa_syscall 

talpa_linux            29424  5 talpa_vfshook,talpa_vcdevice,talpa_syscall,talpa_core 

talpa_syscallhookprobe      882  0 

talpa_syscallhook      14987  2 talpa_vfshook,talpa_syscallhookprobe 
```


```bash
lsmod | grep talpa | wc -l 
```

Forventet output: 9

## <a name="check-talpa-status"></a>Kontrollere TALPA-status

```bash
cat /proc/sys/talpa/interceptors/VFSHookInterceptor/status 
```

Fejlfinding af logfiler (bortset fra "mdatp diagnostic create"-pakken) 

```bash
/var/log/audit/audit.log 

/var/log/messages 

semanage fcontext -l > selinux.log 
```
 

Ydeevne og hukommelse 

```bash
top -p <wdavdaemon pid>      

pmap -x <wdavdaemon pid> 
```

Hvor `<wdavdaemon pid>` kan du finde ved hjælp af `pidof wdavdaemon`.

