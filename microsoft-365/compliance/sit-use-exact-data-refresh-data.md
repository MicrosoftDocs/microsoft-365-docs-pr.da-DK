---
title: Opdater den nøjagtige datamatchtabelfil til følsomme oplysninger
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
description: Opdater din tabelfil med følsomme oplysninger.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a846f22b866b4b8adf75c44e55fde4b9d56b8ac4
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008839"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Opdater den nøjagtige datamatchtabelfil til følsomme oplysninger 

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan opdatere din følsomme informationsdatabase op til 5 gange i hver 24-timers periode. Du skal gemme og uploade din følsomme informationskildetabel igen.

1. Eksportér de følsomme data til en app, f.eks. Microsoft Excel, og gem filen i .csv, .tsv-format eller pipeformat (|) afgrænset format. Behold det samme filnavn og den placering, du brugte, da du tidligere hashkodede og overførte filen. Se [Eksportér kildedata for præcise datamatch baseret på følsomme oplysninger for](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) at få oplysninger om eksport af dine følsomme data og om at få dem til det korrekte format.

      > [!NOTE]
      > Hvis der ikke er nogen ændringer af strukturen (feltnavne) i den følsomme informationskildetabelfil, behøver du ikke at foretage ændringer i databaseskemafilen, når du opdaterer dataene. Men hvis du skal foretage ændringer, skal du sørge for at redigere databaseskemaet og regelpakken i overensstemmelse hermed. Se [Administrer det nøjagtige datamatchskema](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) for trinnene til redigering eller fjernelse af et skema. Se [Opret præcise data, der stemmer overens med typen af følsomme oplysninger/regelpakke](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) for trinnene til redigering eller fjernelse af din EDM SIT/rule-pakke.

2. Brug procedurerne i [Hash, og upload den følsomme datakildetabel for at få præcise data til at matche følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) for at uploade kildefilen til tabellen med følsomme oplysninger.

3. Du kan bruge [Opgavestyring](/windows/desktop/TaskSchd/task-scheduler-start-page) til at automatisere [hashværdien og uploade den følsomme informationskildetabel for at få præcise data til at matche følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . Du kan planlægge opgaver ved hjælp af flere metoder:

   |Metode|Sådan gør du|
   |---|---|
   |PowerShell|Se dokumentationen [til ScheduledTasks](/powershell/module/scheduledtasks/) og [eksemplet med PowerShell-scriptet](#example-powershell-script-for-task-scheduler) i denne artikel|
   |Opgavestyrings-API|Se dokumentationen til [Opgavestyring](/windows/desktop/TaskSchd/using-the-task-scheduler)|
   |Windows brugergrænseflade|Klik på **Start** i Windows, og skriv Opgavestyring. Højreklik derefter på **Opgavestyring** på listen over resultater, og vælg **Kør som administrator**.|

## <a name="example-powershell-script-for-task-scheduler"></a>Eksempel på PowerShell-script til Opgavestyring

Dette afsnit indeholder et eksempel på et PowerShell-script, som du kan bruge til at planlægge dine opgaver for hashing af data og uploade de hashkodede data:

### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Planlæg hashing og upload i et kombineret trin

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

### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Planlæg hashing og upload som separate trin

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
