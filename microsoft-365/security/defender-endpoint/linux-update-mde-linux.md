---
title: Sådan planlægger du en opdatering af Microsoft Defender til slutpunkt (Linux)
description: Få mere at vide om, hvordan du planlægger en opdatering af Microsoft Defender til Slutpunkt (Linux) for bedre at beskytte din organisations aktiver.
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, scanninger, antivirus, microsoft defender til slutpunkt (linux)
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
ms.openlocfilehash: 6fb3141b33948c5c452096c83a2f02657c199575
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63597518"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>Planlæg en opdatering af Microsoft Defender til Slutpunkt (Linux)

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Hvis du vil køre en opdatering på Microsoft Defender til slutpunkt på Linux, skal du [se Installer opdateringer til Microsoft Defender til Slutpunkt på Linux](/microsoft-365/security/defender-endpoint/linux-updates).

Linux (og Unix) har et værktøj kaldet **crontab** (svarende til Opgavestyring) for at kunne køre planlagte opgaver.

## <a name="pre-requisite"></a>Forudsætninger

> [!NOTE]
> For at få en liste over alle tidszoner skal du køre følgende kommando: `timedatectl list-timezones`
>
> Eksempler på tidszoner:
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Sådan angives Cron-jobbet

Brug følgende kommandoer:

### <a name="backup-crontab-entries"></a>Sikkerhedskopiering af crontab-poster

```bash
sudo crontab -l > /var/tmp/cron_backup_201118.dat
```

> [!NOTE]
> Hvor 201118 == YYMMDD

> [!TIP]
> Gør dette, før du redigerer eller fjerner.

Sådan redigeres crontabulering, og der tilføjes et nyt job som rodbruger:

```bash
sudo crontab -e
```

> [!NOTE]
> Standardeditoren er VIM.

Du får muligvis vist:

```output
0****/etc/opt/microsoft/mdatp/logrorate.sh
```

Og

```output
02**sat /bin/mdatp scan quick>~/mdatp_cron_job.log
```

Se [Planlæg scanninger med Microsoft Defender til slutpunkt (Linux)](linux-schedule-scan-mde.md)

Tryk på "Indsæt"

Tilføj følgende poster:

```bash
CRON_TZ=America/Los_Angeles
```

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>! RHEL og varianter (CentOS og Oracle Linux)
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo yum update mdatp -y >> ~/mdatp_cron_job.log
> ```

> #<a name="sles-and-variants"></a>! SLES og varianter
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo zypper update mdatp >> ~/mdatp_cron_job.log
> ```

> #<a name="ubuntu-and-debian-systems"></a>! Ubuntu- og Ink- systemer
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo apt-get install --only-upgrade mdatp >> ~/mdatp_cron_job.log
> ```

> [!NOTE]
> I eksemplerne ovenfor indstiller vi den til 00 minutter, 06:00 (time i 24-timersformat), en hvilken som helst dag i måneden, en hvilken som helst måned, på søndage. [$(dato +\%d) -le 15] == Kan ikke køres, medmindre den er lig med eller mindre end den 15. dag (3. uge). Det vil sige, at den kører hver 3. søndag(7) i måneden kl. 06:00. Pacific (UTC-8).

Tryk på "Esc"

Skriv "`:wq`" med de dobbelte anførselstegn.

> [!NOTE]
> w == write, q == quit

Hvis du vil have vist dine cron-job, skal du skrive `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="opdater Defender til Slutpunkt på Linux.":::

Sådan undersøger du kørslen af cron-job:

```bash
sudo grep mdatp /var/log/cron
```

Sådan undersøger du mdatp_cron_job.log

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Til dem, der bruger Ansible, Chef eller Columbia

Brug følgende kommandoer:

### <a name="to-set-cron-jobs-in-ansible"></a>Sådan angives cronjob i Ansible

```bash
cron - Manage cron.d and crontab entries
```

Se <https://docs.ansible.com/ansible/latest/modules/cron_module.html> for at få flere oplysninger.

### <a name="to-set-crontabs-in-chef"></a>Sådan indstiller du crontabs i Chef

```bash
cron resource
```

Se <https://docs.chef.io/resources/cron/> for at få flere oplysninger.

### <a name="to-set-cron-jobs-in-puppet"></a>Sådan angives cronjob i Cron

Ressourcetype: cron

Se <https://puppet.com/docs/puppet/5.5/types/cron.html> for at få flere oplysninger.

Automatisering med 2010: Cron-job og planlagte opgaver

Se <https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/> for at få flere oplysninger.

## <a name="additional-information"></a>Flere oplysninger:

### <a name="to-get-help-with-crontab"></a>Sådan får du hjælp til crontab

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>Sådan får du en liste over crontabuleringsfilen for den aktuelle bruger

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>Sådan får du en liste over crontabuleringsfilen for en anden bruger

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>Sådan sikkerhedskopieres crontab-poster

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> Gør dette, før du redigerer eller fjerner.

### <a name="to-restore-crontab-entries"></a>Sådan gendannes crontab-poster

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

### <a name="to-edit-other-users-crontab-entries"></a>Sådan redigerer du andre brugeres crontab-poster

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>Sådan fjernes alle crontabuleringsposter

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>Sådan fjernes andre brugeres crontab-poster

```bash
crontab -u username -r
```

### <a name="explanation"></a>Forklaring

<pre>
+—————- minute (values: 0 - 59) (special characters: , - * /)  <br>
| +————- hour (values: 0 - 23) (special characters: , - * /) <br>
| | +———- day of month (values: 1 - 31) (special characters: , - * / L W C)  <br>
| | | +——- month (values: 1 - 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 - 6) (Sunday=0 or 7) (special characters: , - * / L W C) <br>
| | | | |*****command to be executed
</pre>
