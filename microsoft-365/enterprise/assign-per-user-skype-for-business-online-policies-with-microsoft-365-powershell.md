---
title: Tildel Skype for Business onlinepolitikker pr. bruger med PowerShell til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: 70120f6d296f958f44906a3526a7dcaa36b7eb04
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091385"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>Tildel Skype for Business onlinepolitikker pr. bruger med PowerShell til Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Brug af PowerShell til Microsoft 365 er en effektiv måde at tildele kommunikationsindstillinger pr. bruger med Skype for Business Online-politikker.
  
## <a name="prepare-to-run-the-powershell-commands"></a>Forbered kørsel af PowerShell-kommandoer

Brug disse instruktioner til at få konfigureret til at køre kommandoerne (spring de trin over, du allerede har fuldført):
  
  > [!Note]
   > Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste Teams offentlige PowerShell-version, behøver du ikke at installere Skype for Business Online Connector.

1. Installér [Teams PowerShell-modulet](/microsoftteams/teams-powershell-install).
    
2. Åbn en Windows PowerShell kommandoprompt, og kør følgende kommandoer: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   Når du bliver bedt om det, skal du angive navnet på og adgangskoden til din Skype for Business Online-administratorkonto.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Opdaterer indstillinger for ekstern kommunikation for en brugerkonto

Lad os antage, at du vil ændre indstillingerne for ekstern kommunikation for en brugerkonto. Du vil f.eks. tillade, at Alex kommunikerer med brugere i organisationsnetværket (EnableFederationAccess er lig med Sand), men ikke med Windows Live-brugere (EnablePublicCloudAccess er lig med Falsk). Hvis du vil gøre det, skal du gøre to ting:
  
1. Find en ekstern adgangspolitik, der opfylder vores kriterier.
    
2. Tildel den eksterne adgangspolitik til Alex.
    
Hvordan bestemmer du, hvilken politik for ekstern adgang der skal tildeles Alex? Følgende kommando returnerer alle politikker for ekstern adgang, hvor EnableFederationAccess er angivet til Sand, og EnablePublicCloudAccess er angivet til Falsk:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Medmindre du har oprettet brugerdefinerede forekomster af ExternalAccessPolicy, returnerer kommandoen én politik, der opfylder vores kriterier (FederationOnly). Her er et eksempel:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

Nu, hvor du ved, hvilken politik der skal tildeles til Alex, kan vi tildele denne politik ved hjælp af cmdlet'en [Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy) . Her er et eksempel:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Det er ret enkelt at tildele en politik: Du skal blot angive brugerens identitet og navnet på den politik, der skal tildeles. 
  
Og når det kommer til politikker og politiktildelinger, er du ikke begrænset til at arbejde med brugerkonti én gang. Lad os f.eks. antage, at du har brug for en liste over alle de brugere, der har tilladelse til at kommunikere med partnere i organisationsnetværket og med Windows livebrugere. Vi ved allerede, at disse brugere er blevet tildelt politikken for adgang til eksterne brugere FederationAndPICDefault. Da vi ved det, kan du få vist en liste over alle disse brugere ved at køre én enkel kommando. Her er kommandoen:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Med andre ord skal du vise os alle de brugere, hvor egenskaben ExternalAccessPolicy er angivet til FederationAndPICDefault. (Hvis du vil begrænse mængden af oplysninger, der vises på skærmen, skal du bruge cmdlet'en Select-Object til kun at vise hver enkelt brugers viste navn). 
  
Hvis du vil konfigurere alle vores brugerkonti til at bruge den samme politik, skal du bruge denne kommando:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Denne kommando bruger Get-CsOnlineUser til at returnere en samling af alle de brugere, der er blevet aktiveret til Lync, og sender derefter alle disse oplysninger til Grant-CsExternalAccessPolicy, som tildeler politikken FederationAndPICDefault til hver enkelt bruger i samlingen.
  
Som et yderligere eksempel kan du antage, at du tidligere har tildelt Alex politikken FederationAndPICDefault, og at du nu har ændret mening og gerne vil have, at han administreres af den globale politik for ekstern adgang. Du kan ikke eksplicit tildele den globale politik til nogen. Den globale politik bruges i stedet for en given bruger, hvis der ikke er tildelt nogen politik pr. bruger til den pågældende bruger. Hvis Vi ønsker, at Alex skal administreres af den globale politik, skal du derfor  *fjerne tildelingen*  af en politik pr. bruger, der tidligere er tildelt ham. Her er et eksempel på en kommando:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Denne kommando angiver navnet på den eksterne adgangspolitik, der er tildelt Alex, til en null-værdi ($Null). Null betyder "intet". Med andre ord er der ikke tildelt nogen politik for ekstern adgang til Alex. Når der ikke er tildelt en politik for ekstern adgang til en bruger, administreres brugeren af den globale politik.

## <a name="managing-large-numbers-of-users"></a>Administration af et stort antal brugere

Hvis du vil administrere et stort antal brugere (1000 eller flere), skal du batche kommandoerne via en scriptblok ved hjælp af cmdlet'en [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .  I tidligere eksempler skal en cmdlet konfigureres og derefter vente på resultatet, før den sendes tilbage, hver gang der udføres en cmdlet.  Når du bruger en scriptblok, gør dette det muligt for cmdlet'erne at blive udført eksternt, og når de er fuldført, skal du sende dataene tilbage.

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

Dette vil finde 500 brugere ad gangen, der ikke har en klientpolitik. Den giver dem klientpolitikken "ClientPolicyNoIMURL" og politikken for ekstern adgang "FederationAndPicDefault". Resultaterne batches i grupper på 50 og hvert batch på 50 sendes derefter til fjernmaskinen.
  
## <a name="see-also"></a>Se også

[Administrer Skype for Business Online med PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)
