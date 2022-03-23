---
title: Forberede et domæne, der ikke kan rous, til katalogsynkronisering
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvad du skal gøre, hvis du har et domæne, der ikke kan kan rous, som er knyttet til dine lokale brugerkonti, før du synkroniserer dem med din Microsoft 365 lejer.
ms.openlocfilehash: bea80123c1a2db11baa07cd3344f65303cdd1084
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63594277"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Forberede et domæne, der ikke kan rous, til katalogsynkronisering

Når du synkroniserer dit lokale katalog med Microsoft 365, skal du have et bekræftet domæne i Azure Active Directory (Azure AD). Kun UPN'er (User Principal Names), der er knyttet til det lokale Active Directory-domæneservices (AD DS)-domæne, synkroniseres. Men eventuelle UPN'er, der indeholder et domæne, der ikke kan mailes, f.eks. ".local" (f.eks. billa@contoso.local), synkroniseres med et .onmicrosoft.com-domæne (f.eks.: billa@contoso.onmicrosoft.com). 

Hvis du aktuelt bruger et ".local"-domæne til dine brugerkonti i AD DS, anbefales det, at du ændrer dem til at bruge et bekræftet domæne, f.eks. billa@contoso.com, for at kunne synkronisere korrekt med dit Microsoft 365-domæne.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Hvad nu, hvis jeg kun har et lokalt ".local"-domæne?

Du bruger Azure AD Forbind til at synkronisere din AD DS til Azure AD-lejeren i din Microsoft 365 lejer. Få mere at vide under [Integration af lokale identiteter med Azure AD](/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Forbind synkroniserer dine brugeres UPN og adgangskode, så brugerne kan logge på med de samme legitimationsoplysninger, de bruger lokalt. Azure AD synkroniserer Forbind dog kun brugere til domæner, der er bekræftet af Microsoft 365. Det betyder, at domænet også er bekræftet af Azure AD, Microsoft 365 identiteter administreres af Azure AD. Med andre ord skal domænet være et gyldigt internetdomæne (f.eks. .com, .org, .net, .us). Hvis din interne AD DS kun bruger et domæne, der ikke kan rouses (f.eks. ".local"), kan det muligvis ikke matche det bekræftede domæne, du har for din Microsoft 365 lejer. Du kan løse dette problem ved enten at ændre dit primære domæne i din lokale AD DS eller ved at tilføje et eller flere UPN-suffikser.
  
### <a name="change-your-primary-domain"></a>Skift dit primære domæne

Skift dit primære domæne til et domæne, du har bekræftet i Microsoft 365, f.eks. contoso.com. Alle brugere med domænet contoso.local opdateres derefter til contoso.com. Dette er dog en proces, der er involveret, og en nemmere løsning er beskrevet i det følgende afsnit.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>Tilføje UPN-suffikser og opdatere brugerne til dem

Du kan løse problemet med ".local" ved at registrere nyt UPN-suffiks eller nye UPN-suffikser i AD DS, så det svarer til det domæne (eller de domæner), du har bekræftet i Microsoft 365. Når du har registreret det nye suffiks, skal du opdatere brugerens UPN'er, så ".local" erstattes med det nye domænenavn, så en brugerkonto f.eks. ser ud som billa@contoso.com.
  
Når du har opdateret UPN'erne til at bruge det bekræftede domæne, er du klar til at synkronisere dine lokale AD DS med Microsoft 365.
  
#### <a name="step-1-add-the-new-upn-suffix"></a>Trin 1: Tilføj det nye UPN-suffiks**
  
1. På AD DS domænecontroller skal du i Server Manager **vælge Værktøjer** \> **Active Directory-domæner og -tillidsforhold**.
    
    **Eller, hvis du ikke har Windows Server 2012**
    
    Tryk **Windows +R for** at åbne dialogboksen **Kør**, og skriv derefter Domain.msc, og vælg **OK**.
    
    ![Vælg Active Directory-domæner og -tillidsforhold.](../media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. I vinduet **Active Directory-domæner og -tillidsforhold** skal du højreklikke på **Active Directory-domæner og -tillidsforhold** og derefter vælge **Egenskaber**.
    
    ![Højreklik på Active Directory-domæner og -tillidsforhold, og vælg Egenskaber.](../media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Skriv dit **nye UPN-suffiks** eller dine nye **UPN-suffikser i feltet Alternative UPN-suffikser** under fanen UPN-suffikser, og vælg derefter **Tilføj** \> **Anvend**.
    
    ![Tilføj et nyt UPN-suffiks.](../media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Vælg **OK** , når du er færdig med at tilføje suffikser. 
    
 #### <a name="step-2-change-the-upn-suffix-for-existing-users"></a>Trin 2: Ændre UPN-suffikset for eksisterende brugere
  
1. På AD DS domænecontrolleren skal du i Server Manager **vælge Værktøjer** \> **Active Directory-brugere og -computere**.
    
    **Eller, hvis du ikke har Windows Server 2012**
    
    Tryk **Windows +R for** at åbne **dialogboksen** Kør, skriv derefter Dsa.msc, og klik derefter på **OK**
    
2. Vælg en bruger, højreklik, og vælg derefter **Egenskaber**.
    
3. Vælg det **nye** UPN-suffiks på rullelisten UPN-suffiks under fanen Konto, og vælg derefter **OK**.
    
    ![Tilføj et nyt UPN-suffiks for en bruger.](../media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Fuldfør disse trin for hver bruger.
    
   
### <a name="use-powershell-to-change-the-upn-suffix-for-all-of-your-users"></a>Brug PowerShell til at ændre UPN-suffikset for alle dine brugere

Hvis du har mange brugerkonti at opdatere, er det nemmere at bruge PowerShell. I følgende eksempel bruges cmdlet'erne [Get-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617241(v=technet.10)) og [Set-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617215(v=technet.10)) til at ændre alle contoso.local-suffikser til at contoso.com i AD DS. 

Du kan f.eks. køre følgende PowerShell-kommandoer for at opdatere alle contoso.local-suffikser til contoso.com:
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

Se [Active Directory-Windows PowerShell for at](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617195(v=technet.10)) få mere at vide om, hvordan du Windows PowerShell i AD DS.