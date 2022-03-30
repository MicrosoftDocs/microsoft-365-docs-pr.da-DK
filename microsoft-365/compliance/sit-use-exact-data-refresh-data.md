---
title: Opdatere kildetabelfilen for oplysninger, der svarer nøjagtigt til dine data
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Opdater kildetabelfilen med følsomme oplysninger.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 347ff88391a19cb3d8688b1142e524a163159b6f
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63598545"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Opdatere den nøjagtige datakilde, der svarer til kildetabelfilen med følsomme oplysninger 

Du kan opdatere databasen med følsomme oplysninger op til 5 gange i hver 24-timers periode. Du er nødt til at overføre din kildetabel med følsomme oplysninger.

1. Eksportér de følsomme data til en app, f.eks. Microsoft Excel, og gem filen i afgrænset .csv-, .tsv- eller pipe-format (|). Behold det samme filnavn og den placering, du brugte, da du tidligere har gemt og uploadet filen. Se Eksportér [kildedata for at få](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) en nøjagtig dataoverensstemmelsesbaseret følsom oplysningstype for at få mere at vide om at eksportere dine følsomme data og få dem i det korrekte format.

      > [!NOTE]
      > Hvis der ikke er nogen ændringer i strukturen (feltnavnene) på kildetabelfilen med følsomme oplysninger, behøver du ikke at foretage nogen ændringer i databaseskemafilen, når du opdaterer dataene. Men hvis du skal foretage ændringer, skal du sørge for at redigere databaseskemaet og regelpakken i overensstemmelse hermed. Se Administrer [dit nøjagtige data matchskema for trinnene](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) til at redigere eller fjerne et skema. Se Oprette [en pakke med følsomme oplysninger](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) , der svarer nøjagtigt til typen af følsomme oplysninger/regelpakke for trinnene til at redigere eller fjerne din EDM SIT/regelpakke.

2. Brug fremgangsmåderne i [Hash, og overfør](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) kildetabellen med følsomme oplysninger for nøjagtigt at matche følsomme oplysningstyper for at overføre din følsomme tabelkildefil med følsomme oplysninger.

2. Du kan bruge [Opgavestyring til at](/windows/desktop/TaskSchd/task-scheduler-start-page) automatisere hashtagget og overføre kildetabellen med følsomme oplysninger for nøjagtigt, [hvordan data matcher procedurer for følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . Du kan planlægge opgaver ved hjælp af flere forskellige metoder:

   |Metode|Hvad kan du gøre?|
   |---|---|
   |Windows PowerShell|Se [dokumentationen ScheduledTasks](/powershell/module/scheduledtasks/) og eksemplet [PowerShell-script](#example-powershell-script-for-task-scheduler) i denne artikel|
   |API'en Opgavestyring|Se [dokumentationen til Opgavestyring](/windows/desktop/TaskSchd/using-the-task-scheduler)|
   |Windows brugergrænsefladen|I Windows skal du **klikke på Start** og skrive Opgavestyring. Højreklik derefter på Opgavestyring på listen **over resultater,** og vælg **Kør som administrator**.|

### <a name="example-powershell-script-for-task-scheduler"></a>Eksempel på PowerShell-script til Opgavestyring 

Dette afsnit indeholder et eksempel på et PowerShell-script, du kan bruge til at planlægge dine opgaver til hashing af data og overførsel af hashtagdata:

#### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Planlæg hashing og upload i et kombineret trin

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Planlæg hashing og upload som separate trin

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```
