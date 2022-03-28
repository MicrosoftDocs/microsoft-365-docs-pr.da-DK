---
title: Valider indstillinger for appbeskyttelse på Android- eller iOS-enheder
f1.keywords:
- NOCSH
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
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: f3433b6b-02f7-447f-9d62-306bf03638b0
description: Få mere at vide om, hvordan du Microsoft 365 Business Premium indstillingerne for appbeskyttelse på dine Android- eller iOS-enheder.
ms.openlocfilehash: 85d98a4741299327c0e88735cb9593e129fdc929
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596868"
---
# <a name="validate-app-protection-settings-on-android-or-ios-devices"></a>Valider indstillinger for appbeskyttelse på Android- eller iOS-enheder

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

Følg vejledningen i de følgende afsnit for at validere indstillingerne for appbeskyttelse på Android- eller iOS-enheder.
  
## <a name="android"></a>Android
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Kontrollér, at indstillingerne for appbeskyttelse fungerer på brugerenheder

Når du [har konfigureret appkonfigurationer for Android-enheder for](app-protection-settings-for-android-and-ios.md) at beskytte apps, kan du følge disse trin for at bekræfte, at de valgte indstillinger fungerer. 
  
Først skal du kontrollere, at politikken gælder for den app, du vil validere den i.
  
1. I Microsoft 365 Business Premium [Administration skal du](https://admin.microsoft.com) gå til **Rediger politik** \> **for politikker**.
    
2. Vælg **Programpolitik til Android** for de indstillinger, du oprettede under installationen eller en anden oprettet politik, og bekræft, at den håndhæves af f.eks. Outlook brugere. 
    
    ![Skærmbillede, der viser alle de apps, som denne politik beskytter filer for.](../../media/b3be3ddd-f683-4073-8d7a-9c639a636a2c.png)
  
### <a name="validate-require-a-pin-or-a-fingerprint-to-access-office-apps"></a>Be validere Kræv en pinkode eller et fingeraftryk for at få adgang Office apps

I ruden  Rediger politik skal du vælge  Rediger ud for **adgangskontrol for Office-dokumenter**, udvide Administrer, hvordan brugere får adgang til **Office-filer** på mobilenheder og sørge for, at Kræv en pinkode eller et fingeraftryk for at få adgang til **Office-apps** er indstillet til **Til**.
  
![Sørg for, at Kræv en pinkode eller fingeraftryk for at få adgang Office apps er indstillet til Til.](../../media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. På brugerens Android-enhed skal du åbne Outlook logge på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Du vil også blive bedt om at angive en pinkode eller bruge et fingeraftryk.
    
    ![Indtast en pinkode på din Android-enhed for at få adgang Office apps.](../../media/9e8ecfee-8122-4a3a-8918-eece80344310.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Valider Nulstil pinkode efter et antal mislykkede forsøg

I ruden  Rediger politik skal du vælge  Rediger ud for **adgangskontrol for Office-dokumenter**, udvide Administrer, hvordan brugere får adgang til **Office-filer** på mobilenheder og sørge for, at  Nulstil pinkode efter et antal mislykkede forsøg er indstillet til et tal. Dette er som standard 5. 
  
1. På brugerens Android-enhed skal du åbne Outlook logge på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Angiv en forkert pinkode lige så mange gange, som angivet af politikken. Du får vist en meddelelse om, at grænsen for **pinkodeforsøg er nået** for at nulstille pinkoden. 
    
    ![Skærmbillede, der angiver, at du skal nulstille din pinkode efter for mange forkerte pinkodeforsøg.](../../media/fca6fcb4-bb5c-477f-af5e-5dc937e8b835.png)
  
3. Tryk på **Nulstil pinkode**. Du bliver bedt om at logge på med brugerens legitimationsoplysninger Microsoft 365 Business Premium, og derefter skal du angive en ny pinkode.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Valider Tving brugerne til at gemme alle arbejdsfiler på OneDrive for Business

I ruden  Rediger politik skal du vælge  Rediger ud for Beskyttelse mod mistede eller stjålne **enheder, udvide** Beskyt arbejdsfiler, når enheder er mistet eller blevet **stjålet og sørge** for, at Tving brugerne til at gemme alle arbejdsfiler på **OneDrive for Business** er indstillet til **Til**.
  
![Bekræft, at Tving brugerne til at gemme alle arbejdsfiler på OneDrive for Business er indstillet til Til.](../../media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. På brugerens Android-enhed skal du åbne Outlook logge på med brugerens logonoplysninger Microsoft 365 Business Premium indtaste en pinkode, hvis du bliver bedt om det.
    
2. Åbn en mail, der indeholder en vedhæftet fil, og tryk på pil ned ud for oplysningerne om den vedhæftede fil.
    
    ![Tryk på pil ned ud for en vedhæftet fil for at forsøge at gemme den.](../../media/b22573bb-91ce-455f-84fa-8feb2846b117.png)
  
    Du får vist **Kan ikke gemme på** enhed nederst på skærmen. 
    
    ![Advarselstekst, der angiver, at en fil ikke kan gemmes lokalt på en Android-enhed.](../../media/52ca3f3d-7ed0-4a52-9621-4872da6ea9c5.png)
  
    > [!NOTE]
    > Lagring på OneDrive for Business er på nuværende tidspunkt ikke aktiveret for Android, så du kan kun se, at lokal lagring er blokeret. 
  
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Valider Kræv, at brugeren logger på igen, Office apps har været inaktive i et angivet tidsrum

I ruden  Rediger politik skal du vælge  Rediger ud for **adgangskontrol for Office-dokumenter**, udvide Administrer, hvordan brugere får adgang til **Office-filer** på mobilenheder og sørge for, at Kræv, at brugere logger på igen, når **Office-apps** har været inaktive i er indstillet til et antal minutter. Dette er som standard 30 minutter. 
  
1. På brugerens Android-enhed skal du åbne Outlook logge på med brugerens logonoplysninger Microsoft 365 Business Premium indtaste en pinkode, hvis du bliver bedt om det.
    
2. Du bør nu kunne Outlook i indbakken. Lad Android-enheden være inaktiv i mindst 30 minutter (eller længere, længere end det, du har angivet i politikken). Enhedens lys dæmpes sandsynligvis.
    
3. Få Outlook på Android-enheden igen.
    
4. Du bliver bedt om at angive din pinkode, før du kan få adgang Outlook igen.
    
### <a name="validate-protect-work-files-with-encryption"></a>Valider Beskyt arbejdsfiler med kryptering

I ruden  Rediger politik skal du vælge  Rediger ud for Beskyttelse mod mistede eller stjålne **enheder, udvide** Beskyt arbejdsfiler, når enheder er mistet eller blevet **stjålet og sørge** for, at **Beskyt** arbejdsfiler med kryptering er slået **Til, og** Tving brugere til at gemme alle arbejdsfiler på **OneDrive for Business** er slået **Fra**.
  
1. På brugerens Android-enhed skal du åbne Outlook logge på med brugerens logonoplysninger Microsoft 365 Business Premium indtaste en pinkode, hvis du bliver bedt om det.
    
2. Åbn en mail, der indeholder nogle få vedhæftede billedfiler.
    
3. Tryk på ikonet med den nedadgående pil ud for oplysningerne om den vedhæftede fil for at gemme den.
    
    ![Tryk på pil ned for at gemme figurfilen på en Android-enhed.](../../media/08a9e21e-4022-45d5-acff-59cface651e7.png)
  
4. Du bliver muligvis bedt om at give Outlook adgang til fotos, medier og filer på din enhed. Tryk **på Tillad**.
    
5. Nederst på skærmen skal du vælge Gem **på enhed og** derefter åbne **appen** Galleri. 
    
6. Du bør få vist et krypteret foto (eller flere, hvis du har gemt flere vedhæftede billedfiler) på listen. Den kan vises på listen over billeder som en grå firkant med et hvidt udråbstegn i en hvid cirkel i midten af den grå firkant.
    
    ![En krypteret billedfil i appen Galleri.](../../media/25936414-bd7e-421d-824e-6e59b877722d.png)
  
## <a name="ios"></a>iOS
  
### <a name="check-that-the-app-protection-settings-are-working-on-user-devices"></a>Kontrollér, at indstillingerne for appbeskyttelse fungerer på brugerenheder

Når du [har konfigureret appkonfigurationer for iOS-enheder for](app-protection-settings-for-android-and-ios.md) at beskytte apps, kan du følge disse trin for at validere, om de valgte indstillinger fungerer. 
  
Først skal du kontrollere, at politikken gælder for den app, du vil validere den i.
  
1. I Microsoft 365 Business Premium [Administration skal du](https://admin.microsoft.com) gå til **Rediger politik** \> **for politikker**.
    
2. Vælg **Programpolitik for iOS** for de indstillinger, du oprettede under installationen eller en anden oprettet politik, og bekræft, at den håndhæves i Outlook for eksempel. 
    
    ![Skærmbillede, der viser alle de apps, som denne politik beskytter filer for.](../../media/842441b8-e7b1-4b86-9edd-d94d1f77b6f4.png)
  
### <a name="validate-require-a-pin-to-access-office-apps"></a>Valider Kræv en pinkode for at få adgang Office apps

I ruden  Rediger politik skal du vælge  Rediger ud for **adgangskontrol for Office-dokumenter**, udvide Administrer, hvordan brugere får adgang til **Office-filer** på mobilenheder og sørge for, at Kræv en pinkode eller et fingeraftryk for at få adgang til **Office-apps** er indstillet til **Til**.
  
![Sørg for, at Kræv en pinkode eller fingeraftryk for at få adgang Office apps er indstillet til Til.](../../media/f37eb5b2-7e26-49fb-9bd6-d955d196bacf.png)
  
1. Åbn brugerens iOS-enhed, Outlook og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Du vil også blive bedt om at angive en pinkode eller bruge et fingeraftryk.
    
    ![Indtast en pinkode på din IOS-enhed for at få adgang Office apps.](../../media/06fc5cf3-9f19-4090-b23c-14bb59805b7a.png)
  
### <a name="validate-reset-pin-after-number-of-failed-attempts"></a>Valider Nulstil pinkode efter et antal mislykkede forsøg

I ruden  Rediger politik skal du vælge  Rediger ud for **adgangskontrol for Office-dokumenter**, udvide Administrer, hvordan brugere får adgang til **Office-filer** på mobilenheder og sørge for, at  Nulstil pinkode efter et antal mislykkede forsøg er indstillet til et tal. Dette er som standard 5. 
  
1. Åbn brugerens iOS-enhed, Outlook og log på med brugerens Microsoft 365 Business Premium legitimationsoplysninger.
    
2. Angiv en forkert pinkode lige så mange gange, som angivet af politikken. Du får vist en meddelelse om, at grænsen for **pinkodeforsøg er nået** for at nulstille pinkoden. 
    
    ![Skærmbillede med advarsel om nulstilling af pinkode efter for mange forkerte forsøg.](../../media/fab5c089-a4a5-4e8d-8c95-b8eed1dfa262.png)
  
3. Tryk **på OK**. Du bliver bedt om at logge på med brugerens legitimationsoplysninger Microsoft 365 Business Premium, og derefter skal du angive en ny pinkode.
    
### <a name="validate-force-users-to-save-all-work-files-to-onedrive-for-business"></a>Valider Tving brugerne til at gemme alle arbejdsfiler på OneDrive for Business

I ruden  Rediger politik skal du vælge  Rediger ud for Beskyttelse mod mistede eller stjålne **enheder, udvide** Beskyt arbejdsfiler, når enheder er mistet eller blevet **stjålet og sørge** for, at Tving brugerne til at gemme alle arbejdsfiler på **OneDrive for Business** er indstillet til **Til**.
  
![Bekræft, at Tving brugerne til at gemme alle arbejdsfiler på OneDrive for Business er indstillet til Til.](../../media/7140fa1d-966d-481c-829f-330c06abb5a5.png)
  
1. På brugerens iOS-enhed skal du åbne Outlook logge på med brugerens legitimationsoplysninger Microsoft 365 Business Premium angive en pinkode, hvis du bliver bedt om det.
    
2. Åbn en mail, der indeholder en vedhæftet fil, åbn den **vedhæftede fil** , og vælg Gem nederst på skærmen. 
    
    ![Tryk på indstillingen Gem, når du har åbnet en vedhæftet fil for at forsøge at gemme den.](../../media/b419b070-1530-4f14-86a8-8d89933a2b25.png)
  
3. Du bør kun se en indstilling for OneDrive for Business. Hvis ikke, skal **du trykke på** Tilføj **konto og OneDrive for Business** på **skærmen Storage Tilføj** konto. Angiv slutbrugerens oplysninger om, Microsoft 365 Business Premium logge på, når du bliver bedt om det. 
    
    Tryk **på Gem**, og **vælg OneDrive for Business**.
    
### <a name="validate-require-user-to-sign-in-again-if-office-apps-have-been-idle-for-a-specified-time"></a>Valider Kræv, at brugeren logger på igen, Office apps har været inaktive i et angivet tidsrum

I ruden  Rediger politik skal du vælge  Rediger ud for **adgangskontrol for Office-dokumenter**, udvide Administrer, hvordan brugere får adgang til **Office-filer** på mobilenheder og sørge for, at Kræv, at brugere logger på igen, når **Office-apps** har været inaktive i er indstillet til et antal minutter. Dette er som standard 30 minutter. 
  
1. På brugerens iOS-enhed skal du åbne Outlook logge på med brugerens legitimationsoplysninger Microsoft 365 Business Premium angive en pinkode, hvis du bliver bedt om det.
    
2. Du bør nu kunne Outlook i indbakken. Lad iOS-enheden ikke ændres i mindst 30 minutter (eller længere, længere end det, du har angivet i politikken). Enhedens lys dæmpes sandsynligvis.
    
3. Access Outlook på iOS-enheden igen.
    
4. Du bliver bedt om at angive din pinkode, før du kan få adgang Outlook igen.
    
### <a name="validate-protect-work-files-with-encryption"></a>Valider Beskyt arbejdsfiler med kryptering

I ruden  Rediger politik skal du vælge  Rediger ud for Beskyttelse mod mistede eller stjålne **enheder, udvide** Beskyt arbejdsfiler, når enheder er mistet eller blevet **stjålet og sørge** for, at **Beskyt** arbejdsfiler med kryptering er slået **Til, og** Tving brugere til at gemme alle arbejdsfiler på **OneDrive for Business** er slået **Fra**.
  
1. På brugerens iOS-enhed skal du åbne Outlook logge på med brugerens legitimationsoplysninger Microsoft 365 Business Premium angive en pinkode, hvis du bliver bedt om det.
    
2. Åbn en mail, der indeholder nogle få vedhæftede billedfiler.
    
3. Tryk på den vedhæftede fil, og **tryk derefter på** indstillingen Gem under den. 
    
4. Åbn **Fotos** appen fra startskærmen. Du bør få vist et krypteret foto (eller flere, hvis du har gemt flere vedhæftede billedfiler), der er gemt, men krypteret. 
    

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)