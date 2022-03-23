---
title: Tildel pr. bruger Skype for Business Online-politikker med PowerShell til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Oversigt: Brug PowerShell til Microsoft 365 til at tildele kommunikationsindstillinger pr. bruger med Skype for Business Online-politikker.'
ms.openlocfilehash: c49d465ffe0a6f1379681be0ae4faaf9982b6ef0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594231"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>Tildel pr. bruger Skype for Business Online-politikker med PowerShell til Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Brug af PowerShell til Microsoft 365 er en effektiv måde at tildele kommunikationsindstillinger pr. bruger med Skype for Business Online-politikker.
  
## <a name="prepare-to-run-the-powershell-commands"></a>Forbered dig på at køre PowerShell-kommandoerne

Følg disse instruktioner for at konfigurere til at køre kommandoerne (spring de trin over, du allerede har fuldført):
  
  > [!Note]
   > Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste Teams offentlige PowerShell-udgivelse, behøver du ikke at installere Skype for Business Online Connector.

1. Installer Teams [PowerShell-modulet](/microsoftteams/teams-powershell-install).
    
2. Åbn en Windows PowerShell, og kør følgende kommandoer: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   Når du bliver bedt om det, Skype for Business din onlineadministratorkontos navn og adgangskode.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Opdatere indstillinger for ekstern kommunikation for en brugerkonto

Antag, at du vil ændre indstillinger for ekstern kommunikation på en brugerkonto. Du vil f.eks. tillade, at Alex kommunikerer med brugere, der er medlem af organisationsnetværket (EnableFederationAccess er lig med Sand), men ikke med Windows Live-brugere (EnablePublicCloudAccess er lig med Falsk). Hvis du vil gøre det, skal du gøre to ting:
  
1. Find en ekstern adgangspolitik, der opfylder vores kriterier.
    
2. Tildel Den eksterne adgangspolitik til Alex.
    
Hvordan afgør du, hvilken ekstern adgangspolitik Alex skal tildeles? Følgende kommando returnerer alle politikker for ekstern adgang, hvor EnableFederationAccess er angivet til Sand, og EnablePublicCloudAccess er indstillet til Falsk:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Medmindre du har oprettet brugerdefinerede forekomster af ExternalAccessPolicy, returnerer denne kommando én politik, der opfylder vores kriterier (Sammenslutning Kun). Her er et eksempel:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

Nu hvor du ved, hvilken politik du skal tildele Alex, kan vi tildele denne politik ved hjælp af [Grant-CsExternalAccessPolicy-cmdlet'en](/powershell/module/skype/Get-CsExternalAccessPolicy) . Her er et eksempel:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Det er ret nemt at tildele en politik: Du skal blot angive brugerens identitet og navnet på den politik, der skal tildeles. 
  
Og når det gælder politikker og politiktildelinger, er du ikke begrænset til at arbejde med brugerkonti én gang. Antag f.eks., at du skal bruge en liste over alle de brugere, der har tilladelse til at kommunikere med organisationsnetværkspartnere og med Windows livebrugere. Vi ved allerede, at disse brugere har fået tildelt politikken for ekstern brugeradgang FederationAndPICDefault. Da vi ved, at du kan få vist en liste over alle disse brugere ved at køre en enkelt kommando. Her er kommandoen:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Med andre ord skal du vise os alle de brugere, hvor egenskaben ExternalAccessPolicy er angivet til FederationAndPICDefault. (Og for at begrænse mængden af oplysninger, der vises på skærmen, skal du bruge Select-Object-cmdlet'en til kun at vise hver enkelt brugers viste navn. 
  
Hvis du vil konfigurere alle vores brugerkonti til at bruge den samme politik, skal du bruge denne kommando:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Denne kommando bruger Get-CsOnlineUser til at returnere en samling af alle de brugere, der er aktiveret til Lync, og sender derefter alle disse oplysninger til Grant-CsExternalAccessPolicy, som tildeler politikken FederationAndPICDefault til hver enkelt bruger i samlingen.
  
Antag, at du tidligere har tildelt Alex politikken FederationAndPICDefault, og at du nu har skiftet mening og vil have ham administreret af den globale eksterne adgangspolitik. Du kan ikke eksplicit tildele den globale politik til nogen. I stedet bruges den globale politik for en given bruger, hvis der ikke tildeles nogen politik pr. bruger til den pågældende bruger. Hvis Alex skal administreres af den globale politik, skal du derfor fjerne tildelingen af en  politik pr. bruger, der tidligere er tildelt ham. Her er en eksempelkommando:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Denne kommando angiver navnet på politikken for ekstern adgang, der er tildelt Alex til en Null-værdi ($Null). Null betyder "intet". Med andre ord er der ikke tildelt nogen ekstern adgangspolitik til Alex. Når der ikke er tildelt en ekstern adgangspolitik til en bruger, bliver den pågældende bruger administreret af den globale politik.

## <a name="managing-large-numbers-of-users"></a>Administration af et stort antal brugere

Hvis du vil administrere et stort antal brugere (1000 eller flere), skal du batchere kommandoerne via en scriptblok ved hjælp af [cmdlet'en Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .  I tidligere eksempler skal en cmdlet, hver gang den udføres, konfigurere opkaldet og derefter vente på resultatet, før den sendes tilbage.  Når du bruger en scriptblok, gør dette det muligt at køre cmdlet'er eksternt, og når det er fuldført, kan du sende dataene tilbage.

```powershell
$s = Get-PSSession | Where-Object { ($.ComputerName -like '*.online.lync.com' -or $.Computername -eq 'api.interfaces.records.teams.microsoft.com') -and $.State -eq 'Opened' -and $.Availability -eq 'Available' }

$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

Derved findes der 500 brugere ad gangen, som ikke har en klientpolitik. Det giver dem klientpolitikken "ClientPolicyNoIMURL" og politikken for ekstern adgang "FederationAndPicDefault". Resultaterne grupperes i grupper på 50, og hver batch af 50 sendes derefter til fjerncomputeren.
  
## <a name="see-also"></a>Se også

[Administrer Skype for Business Online med PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
