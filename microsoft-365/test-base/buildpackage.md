---
title: Byg en pakke
description: Sådan opretter du din pakke
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
ms.openlocfilehash: db09d1b182965c0a21945b025601c21d5100212b
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952902"
---
# <a name="build-a-package"></a>Byg en pakke

En pakke er en .zip fil, der indeholder dine binære programscripts og testscripts, hvilket er en forudsætning for at bruge testbasen. Denne Hurtige introduktion hjælper dig med at bygge din første pakke, som du kan bruge til at udføre køreklar test på dit program.

- *En **OOB-test (Out-of-Box)** udfører en installation, start, lukning og fjernelse af dit program. Efter installationen gentages startlukningsrutinen 30 gange, før der køres en enkelt fjernelse. OOB-testen giver dig standardiseret telemetri på din pakke, så du kan sammenligne på tværs af Windows builds.*

Du kan eventuelt downloade vores [eksempelpakke](https://aka.ms/testbase-sample-package) , som du kan referere til og begynde med.

## <a name="create-a-folder-structure"></a>Opret en mappestruktur

Opret en mappestruktur på følgende måde på din lokale computer:

![Mappestrukturen, der bruges til at oprette pakken](Media/buildpackage1.png)

Disse mapper bruges:

- **App\bin**: Gem programmet og de binære afhængigheder.
- **App\scripts**: Gem scripts for at installere, starte, lukke og fjerne programmet.
- **App\logs**: Scripts skal sende logge til denne mappe, så kan du downloade og analysere logge, når testen er fuldført.

## <a name="copy-binary-files"></a>Kopiér binære filer

Kopiér dine programinstallationsfiler til **App\bin**. Hvis dit program har afhængigheder, skal de installeres først. Kopiér også installationsfilerne for afhængigheden til **App\bin**.

![Placering af programfil(er) i mappen](Media/buildpackage2.png)

## <a name="add-powershell-scripts"></a>Tilføj PowerShell-scripts

Hvis du vil udføre OOB-test, skal du tilføje PowerShell-scripts for at installere, starte, lukke og fjerne dit program.

> [!NOTE]
> *I OOB-test kræves der installation, start og lukning af scripts, mens fjernelsesscript er valgfrit*.

Scriptet skal føjes til mappen på følgende måde:

![Placering af powershell-scriptsfiler i mappen](Media/buildpackage3.png)

Et script indeholder normalt følgende funktionsmåder:

- **Kør kommandoerne for at installere/starte/lukke/fjerne programmet**. Hvis dit program f.eks. er en MSI-fil, skal du køre [msiexec](/windows-server/administration/windows-commands/msiexec) for at installere den.
- **Kontrollér resultatet af handlingen install/launch/close/uninstall**. Returner nul afslutningskode, hvis resultatet forventes. Testbasen markerer et script som en fejl, hvis det returnerer en afslutningskode, der ikke er nul.
- **Gem nok logge**, gem de korrekte logge til fremtidig brug.

Se følgende eksempler. Du kan blot kopiere dem til dine filer og foretage ændringer i overensstemmelse hermed.

**Eksempel på installationsscript (App\scripts\install\job.ps1)**:

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

**Eksempel på startscript (App\scripts\launch\job.ps1)**:

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

Når scripts og binære filer er forberedt, skal du komprimere mappen til en zip-fil. Højreklik på mappen App, og vælg **Komprimer til ZIP-fil**.

![Komprimer til zip-fil](Media/buildpackage4.png)

## <a name="verify-your-package-locally-optional"></a>Bekræft din pakke lokalt (valgfrit)

Når du har bygget zip-pakken, kan du uploade den til din Test Base-konto.

Det er dog bedste praksis at køre testen lokalt for at sikre, at scriptene fungerer korrekt, før de uploades. En lokal test kan hurtigt identificere problemer og fremskynde uploadprocessen. Følg nedenstående trin for at bekræfte lokalt:

1. Forbered en VM (virtuel maskine)

   Vi anbefaler, at du bruger en virtuel maskine til denne lokale test, da der i øjeblikket kræves et rent Windows miljø til hver test. Det er nemt at oprette en Windows VM på Azure ([Hurtig start: Windows virtuelle maskine](/azure/virtual-machines/windows/quick-create-portal)), du kan vælge en korrekt Windows version (billede) til din test, f.eks. *Windows 10 Pro, version 21H2.*<br>

2. Kopiér pakken til den virtuelle maskine

   Der er mange måder at kopiere pakkefilen til vm'en på. Hvis du bruger en Virtuel Azure-maskine, kan du vælge at:

     - Kopiér filen direkte i forbindelsen til Fjernskrivebord.
     - Brug Azure-filshare ([Hurtig start: Opret og administrer Azure-fil](/azure/storage/files/storage-files-quick-create-use-windows))

   Du kan oprette en bestemt mappe til denne test og kopiere pakkefilen under denne mappe. f.eks. *C:\TestBase*.

3. Test pakken

   Åbn Windows PowerShell, skift til den mappe, der indeholder pakken, f.eks. `cd C:\TestBase`, og begynd at køre dine test på pakken:

   1. Udpak pakkefilen.

      ```powershell
      Expand-Archive -LiteralPath C:\TestBase\App.zip -DestinationPath C:\TestBase
      ```

   2. Kør installationsscriptet.

      ```powershell
      C:\TestBase\App\scripts\install\job.ps1
      ```

   3. Genstart vm'en, hvis det er nødvendigt.

   4. Kør startscriptet.

      ```powershell
      C:\TestBase\App\scripts\install\job.ps1
      ```

   5. Kør luk script.

      ```powershell
      C:\TestBase\App\scripts\close\job.ps1
      ```

   6. Kør fjernelsesscriptet (hvis du har et).

      ```powershell
      C:\TestBase\App\scripts\uninstall\job.ps1
      ```

Efter hvert trin kan du kontrollere, om der er problemer med scriptet. Hvis alle scripts kører som forventet, er pakken klar til at blive overført til din Test Base-konto.

## <a name="next-steps"></a>Næste trin

[Upload en pakke](uploadApplication.md)
