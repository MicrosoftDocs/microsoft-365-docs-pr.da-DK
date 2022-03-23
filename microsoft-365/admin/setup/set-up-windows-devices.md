---
title: Konfigurer Windows enheder til Microsoft 365 Business Premium brugere
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: Konfigurer Windows enheder, der Windows 10 Pro til Microsoft 365 Business Premium brugere, hvilket muliggør centraliseret styring og sikkerhedskontrolelementer.
ms.openlocfilehash: 0a6fa4178e3aeb2e77d744283bfcf671d0df1f3d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592536"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Konfigurer Windows enheder til Microsoft 365 Business Premium brugere

## <a name="before-you-begin"></a>Før du begynder

Før du kan konfigurere Windows-enheder til Microsoft 365 Business Premium-brugere, skal du kontrollere, at alle Windows-enheder kører Windows 10 Pro version 1703 (Creators Update). Windows 10 Pro er en forudsætning for udrulning af Windows 10 Business, som er et sæt af skytjenester og funktioner til administration af enheder, der supplerer Windows 10 Pro og aktiverer centraliseret styring og sikkerhedskontrol af Microsoft 365 Business Premium.
  
Hvis du har Windows enheder, der Windows 7 Pro, Windows 8 Pro eller Windows 8.1 Pro, giver dit Microsoft 365 Business Premium-abonnement dig mulighed for en Windows 10 opgradering.
  
Du kan finde flere oplysninger om, hvordan du opgraderer Windows-enheder til Windows 10 Pro Creators Update ved at følge trinnene i dette emne: Opgrader [Windows-enheder til Windows Pro Creators Update](../../business-video/upgrade.md).
  
Se [Bekræft, at enheden er forbundet til Azure AD](#verify-the-device-is-connected-to-azure-ad) for at bekræfte, at du har opgraderingen, eller for at sikre dig, at opgraderingen lykkedes.

## <a name="watch-connect-your-pc-to-microsoft-365-business"></a>Se: Forbind din pc til Microsoft 365 Business

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3yXh3] 

Hvis du synes, denne video var nyttig, kan du [se den komplette kursusserie til små virksomheder og dem, der er nye Microsoft 365](../../business-video/index.yml).
  
## <a name="join-windows-10-devices-to-your-organizations-azure-ad"></a>Deltag Windows 10-enheder i din organisations Azure AD

Når alle Windows-enheder i organisationen enten er blevet opgraderet til Windows 10 Pro Creators Update eller allerede kører Windows 10 Pro Creators Update, kan du slutte disse enheder til din organisations Azure Active Directory. Når enhederne er forbundet, opgraderes de automatisk til Windows 10 Business, som er en del af dit Microsoft 365 Business Premium abonnement.
  
### <a name="for-a-brand-new-or-newly-upgraded-windows-10-pro-device"></a>For en helt ny eller nyligt opgraderet enhed skal Windows 10 Pro enhed

Hvis du har en helt ny enhed, der kører Windows 10 Pro Creators Update, eller en enhed, der er blevet opgraderet til Windows 10 Pro Creators Update, men som ikke har gennemgået konfiguration af Windows 10-enhed, skal du følge disse trin.
  
1. Gennemgå konfigurationen Windows 10 enhed, indtil du kommer **til siden Hvordan vil du konfigurere**?. 
    
    ![På siden Hvordan vil du konfigurere skal du vælge Konfigurer for en organisation.](../../media/1b0b2dba-00bb-4a99-a729-441479220cb7.png)
  
2. Her skal du **vælge Konfigurer for en organisation og** derefter angive dit brugernavn og din adgangskode til Microsoft 365 Business Premium. 
    
3. Afslut Windows 10 konfiguration af enheden.
    
   Når du er færdig, får brugeren forbindelse til din organisations Azure AD. Se [Bekræft, at enheden er forbundet til Azure AD](#verify-the-device-is-connected-to-azure-ad) for at sikre dig. 
  
### <a name="for-a-device-already-set-up-and-running-windows-10-pro"></a>For en enhed, der allerede er konfigureret og kører Windows 10 Pro

 **Forbind brugere til Azure AD:**
  
1. På din brugers Windows-pc, der kører Windows 10 Pro, version 1703 (Creators Update) (se forudsætninger, skal du klikke på [Windows-logoet](../security-and-compliance/pre-requisites-for-data-protection.md) og derefter klikke Indstillinger-ikonet.
  
   ![Klik menuen Start ikonet Klik Windows Indstillinger under fanen Indstillinger.](../../media/74e1ce9a-1554-4761-beb9-330b176e9b9d.png)
  
2. I **Indstillinger** skal du gå til **Konti**.
  
   ![I Windows Indstillinger skal du gå til Konti.](../../media/472fd688-d111-4788-9fbb-56a00fbdc24d.png)
  
3. På **siden Dine oplysninger** skal du klikke **på Få adgang til Forbind** \> **.**
  
   ![Vælg Forbind under Adgang til arbejde eller skole.](../../media/af3a4e3f-f9b9-4969-b3e2-4ef99308090c.png)
  
4. I dialogboksen **Konfigurer en arbejds- eller skolekonto under** Alternative **handlinger skal** du vælge **Deltag i denne enhed for at Azure Active Directory**.
  
   ![Klik på Deltag i denne enhed for Azure Active Directory.](../../media/fb709a1b-05a9-4750-9cb9-e097f4412cba.png)
  
5. På siden **Lad os få dig logget på skal** du angive din arbejds- eller skolekonto \> **Næste**.
  
   På siden **Angiv adgangskode** skal du angive din adgangskode \> **Log på**.
  
   ![Angiv din arbejds- eller skolemail på siden Lad os få dig logget på.](../../media/f70eb148-b1d2-4ba3-be38-7317eaf0321a.png)
  
6. På siden **Sørg for, at dette er din organisation** skal du bekræfte, at oplysningerne er korrekte og vælge **Deltag**.
  
   På **Du er klar!** skal du vælge **Udført**.
  
   ![På skærmbilledet Sørg for, at dette er din organisation skal du vælge Deltag.](../../media/c749c0a2-5191-4347-a451-c062682aa1fb.png)
  
Hvis du har overført filer til en OneDrive for Business, skal du synkronisere dem igen. Hvis du har brugt et tredjepartsværktøj til at overføre profil og filer, skal du også synkronisere dem til den nye profil.
  
## <a name="verify-the-device-is-connected-to-azure-ad"></a>Kontrollér, at enheden er forbundet til Azure AD

For at bekræfte din synkroniseringsstatus skal du på siden **Adgang** til arbejde eller skole **i Indstillinger** vælge området **Tilsluttet _** \<organization name\> _ for at få vist knapperne **Oplysninger** og **Afbryd forbindelse**. Vælg **Oplysninger for** at få din synkroniseringsstatus. 
  
På siden **Synkroniseringsstatus skal** du vælge **Synkroniser** for at få de seneste politikker for administration af mobilenheder over på pc'en.
  
For at begynde at Microsoft 365 Business Premium-kontoen skal du gå til Windows **Start**, højreklikke på dit aktuelle kontobillede og derefter klikke **på Skift konto**. Log på ved hjælp af din organisations mailadresse og adgangskode.
  
![Klik på knappen Oplysninger for at få vist synkroniseringsstatus.](../../media/818f7043-adbf-402a-844a-59d50034911d.png)
  
## <a name="verify-the-pc-is-upgraded-to-windows-10-business"></a>Kontrollér, at pc'en er opgraderet til Windows 10 Business

Kontrollér, at dine Azure AD-Windows 10-enheder opgraderes Windows 10 Business som en del af dit Microsoft 365 Business Premium abonnement.
  
1. Gå til **Indstillinger** \> **System** \> **About**.
    
2. Bekræft, **at Edition** **viser Windows 10 Business**.
    
    ![Kontrollér, Windows udgaven er Windows 10 Business.](../../media/ff660fc8-d3ba-431b-89a5-f5abded96c4d.png)
  
## <a name="next-steps"></a>Næste trin

Hvis du vil konfigurere dine mobilenheder, [skal du se Konfigurer mobilenheder til Microsoft 365 Business Premium brugere](set-up-mobile-devices.md), 

For at øge beskyttelsen skal [du se De 10 bedste måder at sikre Microsoft 365 for business-planer](../security-and-compliance/secure-your-business-data.md).
  
