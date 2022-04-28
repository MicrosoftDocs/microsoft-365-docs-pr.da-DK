---
title: Administrer Skype for Business Online-politikker med PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Oversigt: Brug PowerShell til at administrere egenskaberne for din Skype for Business Online-brugerkonto med politikker.'
ms.openlocfilehash: 71ced77947efda0f587fe7a20af85a73dea73f6c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094344"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>Administrer Skype for Business Online-politikker med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hvis du vil administrere mange egenskaber for brugerkontoen for Skype for Business Online, skal du angive dem som egenskaber for politikker med PowerShell til Microsoft 365.
  
## <a name="before-you-begin"></a>Før du begynder

Brug disse instruktioner til at få konfigureret til at køre kommandoerne (spring de trin over, du allerede har fuldført):

  > [!Note]
  > Skype for Business Online Connector er i øjeblikket en del af det nyeste Teams PowerShell-modul. Hvis du bruger den nyeste Teams offentlige PowerShell-version, behøver du ikke at installere Skype for Business Online Connector.

1. Installér [Teams PowerShell-modulet](/microsoftteams/teams-powershell-install).
    
2. Åbn en Windows PowerShell kommandoprompt, og kør følgende kommandoer: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   Når du bliver bedt om det, skal du angive navnet på og adgangskoden til din Skype for Business Online-administratorkonto.
    
## <a name="manage-user-account-policies"></a>Administrer politikker for brugerkonti

Mange Skype for Business Egenskaber for onlinebrugerkonto konfigureres ved hjælp af politikker. Politikker er blot samlinger af indstillinger, der kan anvendes på en eller flere brugere. Hvis du vil se, hvordan en politik er konfigureret, kan du køre denne eksempelkommando for politikken FederationAndPICDefault:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Til gengæld skal du komme tilbage noget, der ligner dette:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

I dette eksempel bestemmer værdierne i denne politik, hvad en brug kan eller ikke kan gøre, når det kommer til kommunikation med brugere i organisationsnetværket. Egenskaben EnableOutsideAccess skal f.eks. være angivet til Sand, for at en bruger kan kommunikere med personer uden for organisationen. Bemærk, at denne egenskab ikke vises i Microsoft 365 Administration. Egenskaben angives i stedet automatisk til True eller False baseret på de andre valg, du foretager. De to andre interessante egenskaber er:
  
- **EnableFederationAccess** angiver, om brugeren kan kommunikere med personer fra organisationsnetværksdomæner.
    
- **EnablePublicCloudAccess** angiver, om brugeren kan kommunikere med Windows Live-brugere.
    
Derfor ændrer du ikke direkte organisationsrelaterede egenskaber på brugerkonti (f.eks. **Set-CsUser -EnableFederationAccess $True**). Du kan i stedet tildele en konto en politik for ekstern adgang, der har de ønskede egenskabsværdier forudkonfigureret. Hvis en bruger skal kunne kommunikere med brugere i organisationsnetværket og med Windows livebrugere, skal denne brugerkonto tildeles en politik, der tillader disse kommunikationsformer.
  
Hvis du vil vide, om nogen kan kommunikere med brugere uden for organisationen eller ej, skal du:
  
- Find ud af, hvilken politik for ekstern adgang der er tildelt den pågældende bruger.
    
- Find ud af, hvilke egenskaber der er tilladt af denne politik eller ej.
    
Det kan du f.eks. gøre ved hjælp af denne kommando:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Denne kommando finder den politik, der er tildelt brugeren, og finder derefter de funktioner, der er aktiveret eller deaktiveret i den pågældende politik.
  
Hvis du vil administrere Skype for Business Online-politikker med PowerShell, skal du se cmdlet'erne for at:

- [Klientpolitik](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Mødepolitik](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Mobilpolitik](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Politik for online voicemail](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Politik for stemmedistribution](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> En Skype for Business Onlineopkaldsplan er en politik i alle henseender undtagen navnet. Navnet "opkaldsplan" blev valgt i stedet for f.eks. "opkaldspolitik" for at sikre bagudkompatibilitet med Office Communications Server og med Exchange. 
  
Hvis du f.eks. vil se på alle de stemmepolitikker, der er tilgængelige til dit brug, skal du køre denne kommando:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Det returnerer en liste over alle de talepolitikker, der er tilgængelige for dig. Vær dog opmærksom på, at ikke alle politikker kan tildeles til alle brugere. Dette skyldes forskellige begrænsninger, der involverer licensering og geografisk placering. (Den såkaldte "[anvendelsesplacering](/previous-versions/azure/dn194136(v=azure.100))")." Hvis du vil vide mere om politikker for ekstern adgang og mødepolitikker, der kan tildeles til en bestemt bruger, skal du bruge kommandoer, der ligner disse: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Parameteren ApplicableTo begrænser de returnerede data til politikker, der kan tildeles til den angivne bruger (f.eks. Alex Darrow). Afhængigt af begrænsninger for licenser og anvendelsesplacering kan det repræsentere et undersæt af alle tilgængelige politikker. 
  
I nogle tilfælde bruges egenskaber for politikker ikke sammen med Microsoft 365, mens andre kun kan administreres af Microsofts supportpersonale. 
  
Med Skype for Business Online skal brugerne administreres af en eller anden politik. Hvis en gyldig politikrelateret egenskab er tom, betyder det, at den pågældende bruger administreres af en global politik, som er en politik, der automatisk anvendes på en bruger, medmindre brugeren specifikt tildeles en politik pr. bruger. Da vi ikke kan se en klientpolitik for en brugerkonto, administreres den af den globale politik. Du kan bestemme den globale klientpolitik med denne kommando:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Se også

[Administrer Skype for Business Online med PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Administrer Microsoft 365 med PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)