---
title: Forbered et domæne, der ikke kan routes, til katalogsynkronisering
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Få mere at vide om, hvad du skal gøre, hvis du har et domæne, der ikke kan distribueres, og som er knyttet til dine lokale brugerkonti, før du synkroniserer dem med din Microsoft 365 lejer.
ms.openlocfilehash: 7c0fd93f327305477908fba0cfb495fa73205ebe
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096364"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Forbered et domæne, der ikke kan routes, til katalogsynkronisering

Når du synkroniserer din lokale mappe med Microsoft 365, skal du have et bekræftet domæne i Azure Active Directory (Azure AD). Kun de UPN'er (User Principal Names), der er knyttet til AD DS-domænet (Active Directory i det lokale miljø Domain Services), synkroniseres. Alle UPN'er, der indeholder et domæne, der ikke kan distribueres, f.eks. ".local" (f.eks. billa@contoso.local), synkroniseres med et .onmicrosoft.com-domæne (f.eks. billa@contoso.onmicrosoft.com). 

Hvis du i øjeblikket bruger et ".local"-domæne til dine brugerkonti i AD DS, anbefales det, at du ændrer dem til at bruge et bekræftet domæne, f.eks. billa@contoso.com, for at synkronisere korrekt med dit Microsoft 365 domæne.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Hvad gør jeg, hvis jeg kun har et ".local"-domæne i det lokale miljø?

Du kan bruge Azure AD Forbind til at synkronisere din AD DS til Azure AD-lejeren for din Microsoft 365 lejer. Du kan få flere oplysninger under [Integration af dine identiteter i det lokale miljø med Azure AD](/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Forbind synkroniserer dine brugeres UPN og adgangskode, så brugerne kan logge på med de samme legitimationsoplysninger, som de bruger i det lokale miljø. Azure AD Forbind synkroniserer dog kun brugere til domæner, der er bekræftet af Microsoft 365. Det betyder, at domænet også bekræftes af Azure AD, fordi Microsoft 365 identiteter administreres af Azure AD. Med andre ord skal domænet være et gyldigt internetdomæne (f.eks. .com, .org, .net, .us). Hvis din interne AD DS kun bruger et domæne, der ikke kan distribueres (f.eks. ".local"), kan det muligvis ikke matche det bekræftede domæne, du har til din Microsoft 365 lejer. Du kan løse dette problem ved enten at ændre dit primære domæne i AD DS i det lokale miljø eller ved at tilføje et eller flere UPN-suffikser.
  
### <a name="change-your-primary-domain"></a>Skift dit primære domæne

Skift dit primære domæne til et domæne, du har bekræftet i Microsoft 365 f.eks. contoso.com. Alle brugere, der har domænet contoso.local, opdateres derefter til contoso.com. Dette er dog en involveret proces, og en nemmere løsning er beskrevet i følgende afsnit.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>Tilføj UPN-suffikser, og opdater dine brugere til dem

Du kan løse problemet ".local" ved at registrere nyt UPN-suffiks eller suffiks i AD DS, så de svarer til det domæne (eller domæner), du bekræftede i Microsoft 365. Når du har registreret det nye suffiks, opdaterer du brugerens UPN'er, så ".local" erstattes med det nye domænenavn, så en brugerkonto ser ud som billa@contoso.com.
  
Når du har opdateret UPN'erne til at bruge det bekræftede domæne, er du klar til at synkronisere AD DS i det lokale miljø med Microsoft 365.
  
#### <a name="step-1-add-the-new-upn-suffix"></a>Trin 1: Tilføj det nye UPN-suffiks**
  
1. På AD DS-domænecontrolleren skal du i Serveradministrator vælge **Funktioner** \> **Active Directory-domæner og -tillidsforhold**.
    
    **Eller hvis du ikke har Windows Server 2012**
    
    Tryk **på Windows -tasten + R** for at åbne dialogboksen **Kør**, skriv derefter Domain.msc, og vælg derefter **OK**.
    
    ![Vælg Active Directory-domæner og -tillidsforhold.](../media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Højreklik på **Active Directory-domæner og -tillidsforhold i vinduet Active Directory-domæner og** **-tillidsforhold**, og vælg derefter **Egenskaber**.
    
    ![Højreklik på Active Directory-domæner og -tillidsforhold, og vælg Egenskaber.](../media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Skriv det nye **UPN-suffiks eller suffiks** i feltet **Alternative UPN-suffikser under fanen UPN-suffikser** , og vælg derefter **Tilføj** \> **Anvend**.
    
    ![Tilføj et nyt UPN-suffiks.](../media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Vælg **OK** , når du er færdig med at tilføje suffikser. 
    
 #### <a name="step-2-change-the-upn-suffix-for-existing-users"></a>Trin 2: Skift UPN-suffikset for eksisterende brugere
  
1. Vælg **Værktøjer** \> Active Directory-brugere og -computere i Serveradministrator på AD **DS-domænecontrolleren**.
    
    **Eller hvis du ikke har Windows Server 2012**
    
    Tryk **på Windows tasten + R** for at åbne dialogboksen **Kør**, skriv derefter Dsa.msc, og klik derefter på **OK**
    
2. Vælg en bruger, højreklik, og vælg derefter **Egenskaber**.
    
3. Vælg det nye UPN-suffiks på rullelisten UPN-suffiks under fanen **Konto** , og vælg derefter **OK**.
    
    ![Tilføj et nyt UPN-suffiks for en bruger.](../media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Udfør disse trin for hver bruger.
    
   
### <a name="use-powershell-to-change-the-upn-suffix-for-all-of-your-users"></a>Brug PowerShell til at ændre UPN-suffikset for alle dine brugere

Hvis du har mange brugerkonti at opdatere, er det nemmere at bruge PowerShell. I følgende eksempel bruges cmdlet'erne [Get-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617241(v=technet.10)) og [Set-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617215(v=technet.10)) til at ændre alle contoso.local-suffiks til contoso.com i AD DS. 

Du kan f.eks. køre følgende PowerShell-kommandoer for at opdatere alle contoso.local-suffikser til contoso.com:
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

Se [Active Directory-modulet Windows PowerShell](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617195(v=technet.10)) for at få mere at vide om brug af Windows PowerShell i AD DS.