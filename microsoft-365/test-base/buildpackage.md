---
title: Opbyg en pakke
description: Sådan opbygger du din pakke
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 02/28/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 277c185b633263a12687eec5a8eb9a1a34e1dbed
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2022
ms.locfileid: "63594749"
---
# <a name="build-a-package"></a>Opbyg en pakke
En pakke er en .zip fil, der indeholder dit programs binære scripts og testscripts, som er forudsætningen for at bruge Test Base. Denne Hurtigstarter hjælper dig med at opbygge din første pakke, som du kan udføre out of box-test på dit program med. 
  
*    *En **OOB-test (Out of Box)** udfører en installation, start, lukning og fjernelse af dit program. Efter installationen gentages start-luk-rutinen 30 gange, før en enkelt afinstallation køres. OOB-testen giver dig standardiseret telemetri på din pakke for at sammenligne på tværs Windows builds.*  
    
Du kan også downloade vores eksempelpakke [, som](https://aka.ms/testbase-sample-package) du kan henvise til og begynde med. 

## <a name="create-a-folder-structure"></a>Oprette en mappestruktur 

Opret en mappestruktur på din lokale computer på følgende måde:<br> 
![Mappestrukturen, der bruges til at oprette pakke](Media/buildpackage1.png)

Disse mapper bruges:
* **App\bin**: Gem programmet og afhængighedsplaceringerne.<br> 
* **App\scripts**: gem scripts for at installere, starte, lukke og fjerne dit program.<br> 
* **App\logs**: scripts bør få outputlogfiler til denne mappe, og derefter kan du downloade og analysere logfiler, når testen er færdig.<br> 

## <a name="copy-binary-files"></a>Kopiér binære filer
Kopiér dine programinstallationsfiler **til App\bin**. Hvis dit program har afhængigheder, skal de installeres først. Kopiér også installationsfilerne fra afhængigheden til **App\bin**.<br> 
![Placering af programfil(e) i mappen](Media/buildpackage2.png)

## <a name="add-powershell-scripts"></a>Tilføj PowerShell-scripts
For at udføre OOB-test skal du tilføje PowerShell-scripts for at installere, starte, lukke og fjerne dit program.
> [!NOTE]  
> *I OOB-test kræves der installation, start og lukning af scripts, mens fjernelse af script er valgfrit*.
    
Scriptet skal føjes til mappen på følgende måde:  
![Placering af PowerShell-scripts-filer i mappen](Media/buildpackage3.png)

Et script indeholder som regel følgende funktionsmåder:<br> 
-   **Kør kommandoerne for at installere/starte/lukke/fjerne programmet**. Hvis dit program f.eks. er en MSI-fil, skal du køre [msiexec for](/windows-server/administration/windows-commands/msiexec) at installere den. <br> 
-   **Kontrollér resultatet af handlingen Installér/start/luk/fjern**, returner nul-udgangskode, hvis der forventes et resultat. Testbase markerer en script-kørsel som fejl, hvis den returnerer en udgangskode, der ikke er nul.<br> 
-   **Spar nok logfiler**, gem de rigtige logfiler til fremtidig brug.<br> 

Se følgende eksempler. Du kan blot kopiere dem til dine filer og foretage ændringer i overensstemmelse hermed. <br>

**Eksempel på installationsscript (App\scripts\install\job.ps1)**
```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"


        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Installing TestBaseM365 Digital Clock")
        push-location "..\..\bin"
        if ([Environment]::Is64BitProcess) {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        else {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        $arguments = "/i "+$installer_name+" /quiet /L*v "+"$log_dir"+"\atp-client-installation.log"

        $installer = Start-Process msiexec.exe $arguments -wait -passthru
        pop-location

        if ($installer.exitcode -eq 0) {
            log("Installation succesful as $($installer.exitcode)")
        }
        else {
            log("Error: Installation failed as $($installer.exitcode)")
            $exit_code = $installer.exitcode
        }

        log("Installation script finished as $exit_code")
        pop-location
        exit $exit_code
```

**Eksempel på start script (App\scripts\launch\job.ps1)**
```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"

        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Launch TestBaseM365 Digital Clock")

        $PROCESS_NAME = "DigitalClock"
        $exePath = "C:\Program Files\Test Base M365\DigitalClock\DigitalClock.exe"

        Start-Process -FilePath $exePath

         if (Get-Process -Name $PROCESS_NAME) {
                log("Launch successfully $PROCESS_NAME...") 
                $exit_code = 0
         }
         else {
            log("Not launched $PROCESS_NAME...") 
            $exit_code = 1
         }

        log("Launch script finished as $exit_code")
        pop-location
        exit $exit_code 
```

## <a name="compress-to-zip-file"></a>Komprimer til zip-fil
Når scripts og binære er forberedt, skal du fortsætte med at komprimere mappen til en zip-fil. Højreklik på mappen App, og vælg **Komprimer til ZIP-fil**.<br>
![Komprimer til zip-fil](Media/buildpackage4.png)


## <a name="verify-your-package-locally-optional"></a>Bekræft din pakke lokalt (valgfrit)
Når du har opbygget postpakken, kan du uploade den til din Test Base-konto. <br>
Det er dog den bedste fremgangsmåde at køre testen lokalt for at sikre, at scripts fungerer korrekt før overførsel. En lokal test kan hurtigt identificere problemer og sætte fart på din uploadproces. Hvis du vil bekræfte lokalt, skal du følge nedenstående trin:<br>
1.  Forbered en VM (Virtual Machine)<br>
    Vi anbefaler, at du bruger en virtuel maskine til denne lokale test, da der i øjeblikket kræves et rent Windows til hver test. Det er nemt at oprette en Windows VM på Azure ([Hurtig start: Windows](/azure/virtual-machines/windows/quick-create-portal) virtuel maskine), du kan vælge en rigtig Windows-version (billede) til din test, f.eks. *Windows 10 Pro, version 21H2.*<br>

2.  Kopiér pakken til VM<br>
    Der er mange måder at kopiere din pakkefil til VM på. Hvis du bruger en Azure VM, kan du vælge at:
     -  Kopiér filen direkte i forbindelse med Fjernskrivebord. <br>
     -  Brug Azure-filshare ([Hurtig start: Opret og administrer Azure-fil](/azure/storage/files/storage-files-quick-create-use-windows))
    
    Du kan oprette en bestemt mappe til denne test og kopiere pakkefilen under denne mappe. F.eks. *C:\TestBase*.<br>
3.  Test pakken<br>
    Åbn Windows PowerShell, skift til mappen, der indeholder pakken, f.eks. cd C:\TestBase, og begynd at køre dine test på pakken:<br>
    a.  Udtræk pakkefilen.
     -  *Expand-Archive -LiteralPath C:\TestBase\App.zip -DestinationPath C:\TestBase*<br>
    
    b.  Kør installér script.  
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    c.  Genstart VM, hvis det er nødvendigt.<br>
    
    d.  Kør start script.
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    e.  Kør luk script.
     -  *C:\TestBase\App\scripts\close\job.ps1*<br>
    
    f.  Kør afinstaller script (hvis du har et).
     -  *C:\TestBase\App\scripts\uninstall\job.ps1*<br>
    
    Efter hvert trin kan du kontrollere, om der er problemer i dit script. Hvis alle scripts kører som forventet, er pakken klar til at blive overført til din Test Base-konto.


## <a name="next-steps"></a>Næste trin
[Upload en pakke](uploadApplication.md)
 
 
