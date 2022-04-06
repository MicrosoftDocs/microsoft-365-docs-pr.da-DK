---
title: Sådan planlægges scanninger med Microsoft Defender for Endpoint (Linux)
description: Få mere at vide om, hvordan du planlægger en automatisk scanningstid for Microsoft Defender for Endpoint (Linux) for bedre at beskytte din organisations aktiver.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, scans, antivirus, microsoft defender for endpoint (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 706284ed0adf49c4da6357b6bb8217d5a14268e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663484"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>Planlæg scanninger med Microsoft Defender for Endpoint (Linux)

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Hvis du vil køre en scanning efter Linux, skal [du se Understøttede kommandoer](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

Linux (og Unix) har et værktøj kaldet **crontab** (svarer til Opgavestyring) for at kunne køre planlagte opgaver.

## <a name="pre-requisite"></a>Forudsætning

> [!NOTE]
> Hvis du vil hente en liste over alle tidszoner, skal du køre følgende kommando: `timedatectl list-timezones`<br>
> Eksempler på tidszoner:
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Sådan angiver du Cron-jobbet

Brug følgende kommandoer:

### <a name="backup-crontab-entries"></a>Sikkerhedskopiér crontabuleringsposter

```bash
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> Hvor 200919 == YRMMDD

> [!TIP]
> Gør dette, før du redigerer eller fjerner.

Sådan redigerer du crontabulering og tilføjer et nyt job som rodbruger:

```bash
sudo crontab -e
```

> [!NOTE]
> Standardeditoren er VIM.

Du får muligvis vist:

```outbou
0 * * * * /etc/opt/microsoft/mdatp/logrorate.sh
```

Tryk på "Indsæt"

Tilføj følgende poster:

```bash
CRON_TZ=America/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log
```

> [!NOTE]
> I dette eksempel har vi angivet det til 00 minutter, kl. 02.00. (time i 24-timers format), en hvilken som helst dag i måneden, en hvilken som helst måned, på lørdage. Det betyder, at den kører om lørdagen kl. Pacific (UTC -8).

Tryk på "Esc"

Skriv "`:wq`" uden dobbelte anførselstegn.

> [!NOTE]
> w == write, q == quit

Hvis du vil have vist dine cron-job, skal du skrive `sudo crontab -l`

:::image type="content" source="../../media/linux-mdatp-1.png" alt-text="Linux mdatp-siden" lightbox="../../media/linux-mdatp-1.png":::

#### <a name="to-inspect-cron-job-runs"></a>Sådan inspiceres kørsler af cron-job

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>Sådan inspiceres mdatp_cron_job.log*

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>For dem, der bruger Ansible, Chef eller Puppet

Brug følgende kommandoer:

### <a name="to-set-cron-jobs-in-ansible"></a>Sådan angives cron-job i Ansible

```bash
cron - Manage cron.d and crontab entries

See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.

### To set crontabs in Chef

```bash
cron resource
```bash

```
Se <https://docs.chef.io/resources/cron/> for at få flere oplysninger.

### <a name="to-set-cron-jobs-in-puppet"></a>At indstille cron job i Dukke

```bash
Resource Type: cron
```

Se <https://puppet.com/docs/puppet/5.5/types/cron.html> for at få flere oplysninger.

Automatisering med dukket: Cron-job og planlagte opgaver

Se [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/) for at få flere oplysninger.

## <a name="additional-information"></a>Flere oplysninger:

### <a name="to-get-help-with-crontab"></a>Sådan får du hjælp til crontab

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>Sådan henter du en liste over crontab-filen for den aktuelle bruger

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>Sådan henter du en liste over en crontab-fil fra en anden bruger

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>Sådan sikkerhedskopieres crontabuleringsposter

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> Gør dette, før du redigerer eller fjerner.

### <a name="to-restore-crontab-entries"></a>Sådan gendannes crontabuleringsposter

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>Sådan redigerer du crontabulering og tilføjer et nyt job som rodbruger

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>Sådan redigerer du crontabulering og tilføjer et nyt job

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>Sådan redigerer du en anden brugers crontabuleringsposter

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>Sådan fjerner du alle poster under crontabulering

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>Sådan fjernes andre brugeres crontab-poster

```bash
crontab -u username -r
```

### <a name="explanation"></a>Forklaring

+—————- minut (værdier: 0-59) (specialtegn: , \- \* /)  <br>
| +————- time (værdier: 0-23) (specialtegn: , \- \* /) <br>
| | +———- dag i måneden (værdier: 1-31) (specialtegn: , \- \* / L W C)  <br>
| | | +——- måned (værdier: 1-12) (specialtegn: , \- \* / )  <br>
| | | | +-- ugedag (værdier: 0-6) (søndag=0 eller 7) (specialtegn: , \- \* / L W C) <br>
| | | | |******kommando, der skal udføres
