---
title: Administrer Skype for Business Online-politikker med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Oversigt: Brug PowerShell til at administrere dine Skype for Business Online-brugerkontoegenskaber med politikker.'
ms.openlocfilehash: 674ea6daba498279537f7c302f4bf4d791ee00f5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601609"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>Administrer Skype for Business Online-politikker med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

For at administrere mange egenskaber for brugerkonto for Skype for Business Online skal du angive dem som egenskaber for politikker med PowerShell til Microsoft 365.
  
## <a name="before-you-begin"></a>Før du begynder

Følg disse instruktioner for at konfigurere til at køre kommandoerne (spring de trin over, du allerede har fuldført):

  > [!Note]
  > Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste Teams offentlige PowerShell-udgivelse, behøver du ikke at installere Skype for Business Online Connector.

1. Installer Teams [PowerShell-modulet](/microsoftteams/teams-powershell-install).
    
2. Åbn en Windows PowerShell, og kør følgende kommandoer: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   Når du bliver bedt om det, Skype for Business din onlineadministratorkontos navn og adgangskode.
    
## <a name="manage-user-account-policies"></a>Administrere politikker for brugerkonti

Mange Skype for Business egenskaber for onlinebrugerkonti konfigureres ved hjælp af politikker. Politikker er blot samlinger af indstillinger, der kan anvendes for en eller flere brugere. Hvis du vil se nærmere på, hvordan en politik er konfigureret, kan du køre denne eksempelkommando for politikken FederationAndPICDefault:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Du bør vende tilbage til noget, der ligner dette:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

I dette eksempel bestemmer værdierne i denne politik, hvad en brug kan eller ikke kan gøre, når det drejer sig om at kommunikere med brugere, der er medlem af organisationsnetværket. Egenskaben EnableOutsideAccess skal f.eks. være indstillet til Sand, for at en bruger kan kommunikere med personer uden for organisationen. Bemærk, at denne egenskab ikke vises i Microsoft 365 Administration. I stedet angives egenskaben automatisk til Sand eller Falsk baseret på de andre valg, du foretager. De to andre interessante egenskaber er:
  
- **EnableFederationAccess angiver** , om brugeren kan kommunikere med personer fra domæner, der er medlem af organisationsnetværket.
    
- **EnablePublicCloudAccess** angiver, om brugeren kan kommunikere med Windows Live-brugere.
    
Derfor ændrer du ikke direkte sammenslutningsrelaterede egenskaber på brugerkonti (f.eks **. Set-CsUser -EnableFederationAccess $True**). I stedet skal du tildele en konto en ekstern adgangspolitik, der har de ønskede egenskabsværdier forudkonfigureret. Hvis vi ønsker, at en bruger skal kunne kommunikere med brugere i organisationsnetværket og med Windows Live-brugere, skal brugerkontoen være tildelt en politik, der tillader disse typer kommunikation.
  
Hvis du vil vide, om en person kan kommunikere med brugere uden for organisationen, skal du:
  
- Find ud af, hvilken ekstern adgangspolitik der er tildelt den pågældende bruger.
    
- Afgør, hvilke funktioner der er tilladt eller ikke er tilladt i forbindelse med denne politik.
    
Det kan du f.eks. gøre ved hjælp af denne kommando:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Denne kommando finder den politik, der er tildelt brugeren, og finder derefter de funktioner, der er aktiveret eller deaktiveret i den pågældende politik.
  
Hvis du vil Skype for Business politikker for Online med PowerShell, skal du se cmdlet'er for:

- [Klientpolitik](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Politik for møder](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Mobilpolitik](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Politik for onlinebeskeder](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Politik for talerouting](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> En Skype for Business onlineopkaldsplan er en politik på alle måder undtagen navnet. Navnet "opkaldsplan" blev valgt i stedet for f.eks. "opkaldspolitik" for at give bagudkompatibilitet med Office Communications Server og med Exchange. 
  
Hvis du f.eks. vil se alle de stemmepolitikker, der er tilgængelige for din brug, skal du køre denne kommando:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Der returneres en liste over alle de stemmepolitikker, der er tilgængelige for dig. Vær dog opmærksom på, at ikke alle politikker kan tildeles til alle brugere. Dette skyldes forskellige begrænsninger med licensering og geografisk placering. (Den såkaldte "[brugsplacering](/previous-versions/azure/dn194136(v=azure.100))"). Hvis du vil kende politikkerne for ekstern adgang og de mødepolitikker, der kan tildeles en bestemt bruger, skal du bruge kommandoer, der ligner disse: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Parameteren ApplicableTo begrænser de returnerede data til politikker, der kan tildeles den angivne bruger (f.eks. Alex Darrow). Afhængigt af begrænsninger for licenser og brugsplacering kan det repræsentere et undersæt af alle de tilgængelige politikker. 
  
I nogle tilfælde bruges egenskaberne for politikker ikke sammen med Microsoft 365, mens andre kun kan administreres af Microsofts supportmedarbejder. 
  
Med Skype for Business Online skal brugere administreres af en eller anden form for politik. Hvis en gyldig politikrelateret egenskab er tom, betyder det, at den pågældende bruger administreres af en global politik, som er en politik, der automatisk anvendes for en bruger, medmindre han eller hun specifikt er tildelt en politik pr. bruger. Da en klientpolitik ikke er angivet for en brugerkonto, administreres den af den globale politik. Du kan bestemme den globale klientpolitik med denne kommando:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Se også

[Administrer Skype for Business Online med PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)